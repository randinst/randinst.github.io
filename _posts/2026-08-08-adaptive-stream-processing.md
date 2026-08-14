---
title: "Adaptive Stream Processing"
date: 2026-08-08T15:34:30-04:00
mathjax: true
excerpt: 'Presented is a general streaming system for handling increasingly complex inputs and constrained observation. The system comprises distinct mechanisms a streaming reader may use as needed, including direct comparison of incom...'

categories:
  - Design
tags:
  - Algorithms
---

Presented is a general streaming system for handling increasingly complex inputs and constrained observation. The system comprises distinct mechanisms a streaming reader may use as needed, including direct comparison of incoming values, recursive comparison, heterogeneous structure handling, pattern generation, pattern pruning, selective reading, and uncertainty-aware processing.

## Stream Comparison

A stream of incoming values arriving one by one, with a reader following the most recently processed value and evaluating each new value against it. Plain numbers are used as the simplest example of a streamable input; the same reader-based process to be applied to more complex structures.

The input is a sequence $S=(s_1,s_2,\ldots,s_n)$ of numbers arriving one at a time. The reader state $r$ holds the most recently seen value. Each incoming value after the first is compared with its predecessor, producing a relation of greater than, less than, or equal to.

For each pair of consecutive elements, the comparison function is:

$$
C(s_{i-1},s_i)=
\begin{cases}
+1 & \text{if } s_i>s_{i-1}\quad\text{(increasing)}\\
0 & \text{if } s_i=s_{i-1}\quad\text{(stable)}\\
-1 & \text{if } s_i<s_{i-1}\quad\text{(decreasing)}
\end{cases}
$$

The resulting output is the sequence of comparisons between consecutive elements:

$$
R=\left(C(s_1,s_2),C(s_2,s_3),\ldots,C(s_{n-1},s_n)\right)
$$

The comparator requires $O(1)$ time for each incoming element and $O(n)$ time for the complete stream. Its reader state requires $O(1)$ space and only the most recently seen value needs to be retained, allowing each value to be processed immediately as it arrives.

For example, the input stream [5, 8, 8, 3, 10] produces the comparisons 5 < 8, 8 = 8, 8 > 3, and 3 < 10, giving the result sequence [+1, 0, -1, +1].

```text
Algorithm StreamComparison

Pre:
    A stream of values with a defined comparison relation.

State:
    reader           // most recently processed value

Procedure Process(x)
    if reader is undefined then
        reader <- x
        return

    if x > reader then
        relation <- >
        result <- +1
    else if x < reader then
        relation <- <
        result <- -1
    else
        relation <- =
        result <- 0

    record (reader, relation, x, result)
    reader <- x
```

## Recursive Comparison

The basic streaming comparator compares each incoming number with the number immediately preceding it. The same reader-based process can compare recursively nested collections as stream items.

Collections may be compared element-wise, by aggregate, by structure, by set relationship, by pattern, or by distance, and these comparisons may recurse through nested collections.

### Stateful Streaming

The reader is stateful and retains the previous item or its relevant representation for the comparisons to follow. For example, given the stream {5, 2, 9}, {8, 1, 7}, {3, 6, 4}, the reader compares the first collection with the second, then the second with the third.

There are several possible ways to compare the collections. An element-wise comparison of {5, 2 ,9} and {8, 1, 7} gives 5 < 8, 2 > 1, and 9 > 7, producing a structured mixed result rather than a single scalar relation. An aggregate comparison instead reduces each collection to a property such as its sum, maximum, or mean and then applies scalar ordering to the resulting values. Other comparisons can concern subset relationships, overlap, patterns or distributions, or distance measures such as Euclidean distance, Jaccard similarity, or cosine similarity. A distance or similarity may be recorded directly, or the selected comparison method may define a threshold or ordering that converts it into a comparison result.

The structure can be extended to arbitrary depth. A single number is level 0; a collection of numbers is level 1; a collection of collections is level 2; and so on. For example, 5 is level 0, while $\lbrace\lbrace5,2\rbrace,\lbrace9,1\rbrace\rbrace$ is level 2.

Level 0: Single number

$$5$$

Level N: Arbitrary depth

$$
\lbrace\lbrace\lbrace\cdots\rbrace\rbrace\rbrace
$$

At these deeper levels, comparison can operate on the structure as a whole, at corresponding levels, or recursively from the lower levels upward. For example, a bottom-up aggregate comparison of $\lbrace\lbrace5,2\rbrace,\lbrace9,1\rbrace\rbrace$ and $\lbrace\lbrace8,3\rbrace,\lbrace7,4\rbrace\rbrace$ reduces the inner collections to $7$, $10$, $11$, and $11$, then compares $\lbrace7,10\rbrace$ with $\lbrace11,11\rbrace$, giving $17<22$.

A structural comparison can instead compare the shapes of the structures. $\lbrace\lbrace5,2\rbrace,\lbrace9,1,3\rbrace\rbrace$ has the structure $[2,3]$, while $\lbrace\lbrace8\rbrace,\lbrace7,4\rbrace\rbrace$ has $[1,2]$; different structures may therefore be incomparable or require a structural distance. Multi-level comparison can preserve results at several levels rather than reducing them to one relation, producing mixed results such as $7<11$ at one level and $10>11$ at another.

The structures can also change between stream items. $\lbrace\lbrace5,2\rbrace,\lbrace9\rbrace\rbrace$ may be followed by $\lbrace8,3,7\rbrace$, which is flattened, and then by $\lbrace\lbrace\lbrace1\rbrace\rbrace\rbrace$, which is deepened. This raises the problem of comparing structures with different depths or shapes. Possible comparison semantics include lexicographic, component-wise, and aggregate-based comparison. When a particular comparison semantics is selected, that choice is part of the algorithm configuration and therefore must be fixed for reproducible execution; structures for which the selected semantics does not define a result are recorded as `incomparable` rather than silently coerced.

Comparison can operate directly on tree leaves, recursively on corresponding substructures, or on structural properties when the structures do not correspond.

This recursive comparison changes the reader's cost. Comparing two scalar values requires one inequality, but comparing nested structures can require traversing their contents and recursively processing their substructures. The work therefore grows with the size and depth of the structures, and the reader may begin to lag behind the incoming stream.

One approach is to reduce each nested structure to a single scalar before comparison. Each collection can be recursively reduced using an operation such as sum or product, after which the resulting scalar can be compared with the preceding scalar. With hierarchical sums, $\lbrace\lbrace5,2\rbrace,\lbrace9,1,3\rbrace\rbrace$ becomes $7$ and $13$, then $20$ at the top level. With hierarchical products, it becomes $10$ and $27$, then $270$.

The structure must still be traversed once to produce its aggregate, requiring $O(n)$ work for $n$ elements, but the resulting scalar can be compared in $O(1)$ time and retained in $O(1)$ space. The aggregation operation determines what information about the original structure is preserved.


## Nested Comparison

This comparator formalizes recursive comparison of arbitrarily nested collections in a streaming context. Each incoming structure is compared with its predecessor according to a selected comparison mode, which may operate on aggregate values, structural signatures, depth, or corresponding elements. The reader retains the previous structure and advances to the new one after recording the comparison. For element-wise comparison, the selected rules must specify how corresponding elements are identified and how unequal lengths, missing elements, and incompatible substructures are handled. For `aggregate`, `structure`, and `depth`, the resulting representations are compared according to the comparison rule selected for that mode.

```text
Algorithm RecursiveNestedCompare(mode)

Pre:
    The input is a stream of recursively nested collections.
    mode in {aggregate, structure, depth, elementwise}.

State:
    reader

Post:
    Each incoming structure has been compared with its predecessor
    according to the selected comparison mode.

Procedure Process(x)
    if reader is undefined then
        reader <- x
        return

    previous <- Evaluate(reader, mode)
    current <- Evaluate(x, mode)
    result <- Compare(previous, current, mode)
    record(reader, result, x)
    reader <- x

Procedure Evaluate(x, mode)
    case mode of
        aggregate
            recursively reduce every nested collection to a single aggregate value

        structure
            recursively construct a structural signature describing the nesting pattern

        depth
            recursively determine the maximum nesting depth

        elementwise
            retain the nested structure for recursive element-wise comparison

    return resulting representation

Procedure Compare(previous, current, mode)
    if mode = elementwise then
        recursively compare corresponding elements throughout the hierarchy
        define the result for missing elements, unequal collection lengths,
        and incompatible substructures according to the selected
        element-wise comparison rules
        return resulting comparison

    compare previous with current
    return resulting relation
```

## Aggregate Comparison

Instead of comparing nested structures directly, each incoming structure is recursively reduced to a single value in the selected aggregation domain, such as sum or product. This is one comparison mode, not a general equivalence criterion. Distinct structures may have the same aggregate because aggregation deliberately discards structural information. The structure must still be traversed to produce its aggregate, but the resulting scalar comparison is $O(1)$ once both aggregates are available.

The aggregation function is defined over the numeric aggregation domain $D$ of the selected operator. The selected operator, identity element, numeric representation, and overflow policy are part of the algorithm configuration.

The aggregation function is:

$$
A:\mathrm{NestedStructure}\to\mathrm{D}
$$

$$
A(x)=
\begin{cases}
x & \text{if }x\text{ is a number}\\
e & \text{if }x=\varnothing\\
op\bigl(A(x_1),A(x_2),\ldots,A(x_n)\bigr)
& \text{if }x=\lbrace x_1,x_2,\ldots,x_n\rbrace
\end{cases}
$$

where

$$
op\in\{+,\times\}
$$

and $e$ is the identity element of the selected aggregation operator.

For a stream $S_1,S_2,S_3,\ldots$, each structure is reduced to an aggregate $v_i=A(S_i)$. After the first input, each aggregate is compared with the aggregate of its predecessor.

For the unpruned aggregate comparator, producing the aggregate requires $O(n)$ time, where $n$ is the total number of elements in the structure, while comparison of the resulting scalars is $O(1)$. Thus the per-input cost is $O(n)$. The aggregate result itself requires $O(1)$ storage. The recursive traversal may additionally require working storage proportional to the nesting depth.

The aggregate therefore provides a fixed-value representation of an arbitrarily nested structure for purposes of comparison, at the cost of discarding structural information that the aggregate does not preserve. Sum and product also produce different comparison behavior, so the choice of aggregation operation is part of the comparator’s semantics.

```text
Algorithm AggregateNestedComparison(aggregation)

Pre:
    The input is a stream of recursively nested numeric collections.
    aggregation in {sum, product}.

State:
    previous aggregate
    comparison history

Post:
    Every incoming structure has been reduced to a scalar and
    compared with the aggregate of its predecessor.

Procedure Process(x)
    current <- Aggregate(x)

    if no previous aggregate exists then
        previous aggregate <- current
        return

    determine the relation between previous aggregate and current
    append the comparison to comparison history
    previous aggregate <- current

Procedure Aggregate(x)
    if x is a number then
        return x

    if x is empty then
        return identity element

    recursively aggregate every child of x
    combine the resulting values using the selected aggregation operator
    return the resulting scalar

Procedure Trend()
    if comparison history is empty then
        return Mixed

    if all recorded comparisons are increasing then
        return Increasing

    if all recorded comparisons are decreasing then
        return Decreasing

    return Mixed
```

## Pattern Generation

A generative pattern-based comparator extends the nested streaming comparator by allowing a recognized pattern within an incoming structure to produce a replacement numeric value or nested structure before the comparison is performed. Instead of always aggregating the structure that arrived, the reader can apply a registered pattern rule, generate a new structure from the match, and use that generated structure as the representation that is subsequently aggregated and compared with the preceding result.

The pattern match can therefore alter what the reader actually compares. A rule might recognize a particular structure, depth, or arrangement and replace it with a generated value or structure, allowing the parent level to operate on the generated result without processing the original structure in the same way. Pattern rules have a total precedence order when multiple rules match, and the first matching rule is applied. Generation is reproducible by default: a deterministic generation function is used, or a stochastic rule receives an explicit seed derived from the algorithm configuration and stream position. The generated result, rule identity, and seed are recorded with the comparison trace so that the transformation can be replayed exactly.

```text
Algorithm PatternGeneration(aggregation)

Pre:
    The input is a stream of recursively nested collections.
    A finite collection of pattern rules has been defined.

State:
    previous aggregate
    pattern library

Post:
    Each incoming structure has been compared with its predecessor.
    Structures matching registered patterns may generate a replacement value 
    or structure before comparison.

Procedure RegisterPattern(rule)
    Add rule to the pattern library.

Procedure Process(x)
    generated <- none

    for each rule in the pattern library in precedence order
        if rule matches x then
            generated <- Generate(rule, x)
            terminate the search

    if generation occurred then
        current <- Aggregate(generated)
    else
        current <- Aggregate(x)

    if no previous aggregate exists then
        previous aggregate <- current
        return

    determine the relation between previous aggregate and current
    record the comparison
    previous aggregate <- current

Procedure Generate(rule, x)
    return rule.generation(x)
```

## Pattern Pruning

Pattern pruning introduces synthetic replacement into the recursive comparison process. After pruning, the resulting structure is processed using the selected aggregation operation. When a structure at some level matches a defined pattern or condition, the reader does not continue deeper into that structure. Instead, the matched structure is replaced by a generated abstraction, such as a random or otherwise computed value, and the parent level treats that replacement as the representation of the entire matched substructure. Pattern matching can therefore terminate recursion early, and the parent does not need to know what was inside the replaced structure.

```text
Algorithm PatternPruning

Pre:
    The input is a recursively nested structure.
    A finite set of pruning rules has been defined.

State:
    previous value

Post:
    Every structure has been transformed according to the first
    applicable pruning rule before aggregation and comparison.

Procedure Process(x)
    x' <- Prune(x)
    value <- Aggregate(x')

    if no previous value exists then
        previous value <- value
        return

    compare previous value with value
    record comparison
    previous value <- value

Procedure Prune(x)
    if x is atomic then
        return x

    if a pruning rule matches x according to its defined precedence then
        generate the rule's replacement
        return replacement

    recursively prune every child of x
    return reconstructed structure
```

## Heterogeneous Graphs

Handles recursively nested structures whose elements may be scalars, vectors, references, or further nested structures. Because references can point outside the immediate tree, the resulting structure may have non-tree topology, and the comparator therefore has to define how different element types are resolved before they can participate in aggregation and comparison.

References may be resolved or treated symbolically, and vectors may be reduced, retained, or compared according to the selected comparator. Cyclic references require explicit termination handling; the algorithm uses current-path tracking. A resolved value outside the selected aggregation domain makes the affected comparison `incomparable`.


```text
Algorithm HeterogeneousGraphComparison

Pre:
    The input is a recursively nested heterogeneous structure whose
    elements may be scalar, vector, reference, or nested structure.

State:
    previous aggregate

Post:
    Each heterogeneous structure has been resolved,
    aggregated, and compared with its predecessor.

Procedure Process(x)
    value <- Aggregate(x, path = {})

    if no previous aggregate exists then
        previous aggregate <- value
        return

    compare previous aggregate with value
    record comparison
    previous aggregate <- value

Procedure Aggregate(x, path)
    if x is scalar then
        return x

    if x is vector then
        return ResolveVector(x)

    if x is reference then
        return Resolve(x, path)

    if x is a nested structure then
        if x is empty then
            return identity element
        recursively aggregate every element with the current path
        combine the results using the selected aggregation operator
        return the resulting aggregate
        
Procedure ResolveVector(x)
    return the value produced by the implementation's selected vector-resolution strategy

Procedure Resolve(ref, path)
    if ref.id in path then
        return a cycle representation

    add ref.id to path
    value <- Aggregate(dereference(ref), path)
    remove ref.id from path
    return value
```

## Depth-Limited Evaluation

The reader may be unable to inspect an arriving structure to arbitrary depth because of computational, memory, processing, or access limits. Content beyond the inspection limit is unseen. The comparator may estimate unseen content under a defined strategy or represent it as unknown; estimates carry confidence and are not treated as directly observed.

Confidence may be associated with an evaluated structure or with portions of a structure when they are evaluated separately. In the algorithm shown here, confidence is associated with each evaluated input. Confidence is represented on [0,1], with higher values indicating greater confidence in the evaluated result. Data quality is likewise represented on [0,1]. Confidence reflects certainty in the evaluated result, not data quality itself. The confidence function and child-confidence aggregation rule are implementation-defined, subject to the following constraints: confidence is non-increasing with observation depth when all else is equal, non-decreasing with data quality, and remains within [0,1]. The implementation must distinguish `unknown` from `estimated`: unknown means that the value was not obtained and no estimate was produced; estimated means that a value was produced by an explicit estimation strategy. An estimate may carry confidence, but an unknown value cannot be silently substituted with a numeric value.

```text
Algorithm DepthLimitedComparison

Pre:
    The input is a stream of recursively nested structures.
    A maximum inspection depth and a confidence function are defined.
    The confidence function satisfies the stated depth and data-quality constraints.
    An aggregation strategy and confidence-combination rule are defined.
    A data-quality value in [0,1] is available when the confidence
    function uses source-quality information.
    An estimation strategy may be defined for unseen content; if none is defined, unseen content is represented as unknown.
    A rule for combining child observation statuses is defined.

State:
    previous value
    previous confidence

Post:
    Each incoming structure has been evaluated within the
    inspection limit and compared with the previous result.

Procedure Process(x)
    current <- Evaluate(x, depth = 0)

    if no previous value exists then
        previous value <- current.value
        previous confidence <- current.confidence
        return

    compare previous value with current.value
    record comparison together with the current and previous confidence values
    previous value <- current.value
    previous confidence <- current.confidence

Procedure Evaluate(x, depth)
    if depth > max_depth then
        if an estimation strategy is defined then
            estimate the unseen portion using that strategy
            confidence <- Confidence(depth, data quality)
            return estimated value, estimated status, and confidence
        else
            return unknown value and unknown status with confidence 0

    if x is atomic then
        return value together with Confidence(depth, data quality)

    recursively evaluate every child at depth + 1
    if any child is unknown and no unknown-combination rule is defined then
        return unknown value and unknown status with confidence 0
    value, confidence <- CombineUncertainValues(
        child results,
        aggregation strategy,
        confidence rule
    )
    return aggregated value and combined status and confidence
```

## Confidence-Dependent Computation

Confidence-conditional computation attaches different computational models to a given scenario, structural level, or detected pattern according to how certain the system is about the available information. The type and complexity of processing can therefore adapt to the confidence associated with the data rather than requiring every input to be processed by the same model. Confidence may be associated with an entire input or with separately evaluated portions of a structure, allowing computation to vary within the same structure when those portions are evaluated separately.

Model selection can take into account confidence level, detected patterns, depth in the structure, data-quality indicators, and available computational resources. A high-confidence region may justify more precise computation, while a less confident region may be handled approximately or not processed. 

```text
Algorithm ConfidenceDependentComputation

Pre:
    The input is a stream of recursively nested structures.
    A collection of computational models and a model-selection policy are defined.
    The available computational resources or budget are defined as needed.

State:
    previous value
    computational budget

Post:
    Each input has been evaluated using a computational model
    selected according to confidence, detected patterns,
    available resources, and structural properties.

Procedure Process(x)
    confidence <- AssessConfidence(x)
    pattern <- DetectPattern(x)
    model <- SelectModel(confidence, pattern, remaining budget)
    value <- Compute(model, x)
    update remaining budget

    if no previous value exists then
        previous value <- value
        return

    compare previous value with value
    record comparison
    previous value <- value

Procedure SelectModel(confidence, pattern, budget)
    if the selection policy chooses a pattern-specific model then
        return that model

    return the model selected for the current confidence and available resources
```

## Selective Reading

Selective reading is to be a process that receives a stream but does not fully read every item that passes through it. Instead, it looks only for predetermined information, values, or patterns of interest and ignores irrelevant information. Its scope of inspection may also be limited: it can be lazy by design, or it can become stuck processing one item or deeply nested structure while later items in the stream wait. The result of a bounded search is tri-valued with respect to the target predicate: `match`, `no_match` after complete search within the configured domain, or `unknown` when the search budget ends before the relevant domain has been completely examined. Only `no_match` permits the reader to conclude that the item contains no target under the selected search policy.

When multiple matches are found, the selected extraction rule determines whether they are retained individually, ordered, or reduced to a single value.

```text
Algorithm SelectiveStreamFilter

Pre:
    The input is a stream of recursively nested structures.
    A finite collection of filter predicates is defined.
    Search heuristics, a maximum search depth, and a maximum processing time are defined.

State:
    previous value
    search policy

Post:
    Only information satisfying the filter predicates contributes
    to comparison. A complete search can establish `no_match`; a bounded
    incomplete search produces `unknown` and does not contribute a false
    negative result.

Procedure Process(x)

    search_status, matches <- Search(x)

    if search_status = no_match then

        discard x

        return

    if search_status = unknown then

        record unknown search result for x

        return

    value <- Extract(matches)

    if no previous value exists then

        previous value <- value

        return

    compare previous value with value

    record comparison

    previous value <- value

Procedure Search(x)

    terminate the search with status `unknown` if

        - the maximum search depth is exceeded before the searched domain is complete, or

        - the maximum processing time is exceeded before the searched domain is complete

    if x satisfies a filter predicate then

        record x

        if early termination is enabled then

            return match status and all matches found before termination

    recursively examine only those substructures that
    satisfy the search heuristics

    if the searched domain has been completely examined then
        if recorded matches are nonempty then
            return match status and all recorded matches
        return no_match status and all recorded matches

    return unknown status and all recorded matches

```