---
title: "Mean Proximity Reduction"
date: 2026-08-12T16:18:00+02:00
mathjax: true
excerpt: 'A reduction process for numerical collections based on repeated comparison of their elements with the current arithmetic mean. The process removes the item whose value is closest to that mean, records the removed item, and repeats...'
categories:
  - Design
tags:
  - Algorithms
---

A reduction process for numerical collections based on repeated comparison of their elements with the current arithmetic mean. The process removes the item whose value is closest to that mean, records the removed item, and repeats the operation on the remaining collection. The process records the items removed at each step and the resulting reduction of the collection.

---

The input is a collection $S=(s_1,s_2,\ldots,s_n)$ of numerical items. At each step, the arithmetic mean of the current collection is calculated. The item having the smallest absolute distance from that mean is selected and removed.

For a current collection $S$, its mean is:

$$
\mu(S)=\frac{1}{|S|}\sum_{x\in S}x
$$

The distance of an item $x$ from the current mean is:

$$
d(x,S)=|x-\mu(S)|
$$

The selected item minimizes:

$$
d(x,S)
$$

If the minimum distance is attained by only one distinct value, one occurrence of that value is popped from the current collection and recorded. The mean is then recalculated from the reduced collection. If multiple distinct values have exactly the same minimum distance, the process stops because the criterion cannot distinguish between them. No numerical tolerance is used for this comparison.

Duplicate occurrences of the same value do not create such ambiguity. When a value occurs more than once, one occurrence of that value is popped according to traversal order. If the current collection contains one or two items, the collection is left unchanged.

The initial collection is significant because every removal changes the collection used to calculate the next mean. The resulting pop order therefore depends on the original contents and is not merely an ordering of distances from one fixed mean. The popped items may be collected separately as:

$$
B=(p_1,p_2,\ldots,p_k)
$$

where $p_i$ is the item removed at step $i$. This collection may too be processed using the same operation if continued selection is desired.

## Representation

The arithmetic mean is the selection criterion rather than the item being sought:

$$
S=\{1,2,4,7\}
$$

has:

$$
\mu(S)=3.5
$$

and the distances from the mean are:

$$
2.5,\quad1.5,\quad0.5,\quad3.5
$$

so $4$ is the first item removed. 

Repeated application produces a reduction sequence, where $S_i$ denotes the collection remaining after $i$ removals:

$$
S_0\rightarrow S_1\rightarrow S_2\rightarrow\cdots\rightarrow R
$$

where $R$ is the first collection for which no further permitted selection is possible.

```text
Algorithm MeanProximityReduction

Pre:

    A finite collection S of numerical items.

State:

    current collection
    popped sequence

Post:

    Each uniquely closest item has been removed from the 
    current collection and recorded in popped sequence.
    Processing stops when the current collection has size <= 2
    or multiple distinct values have the same minimum distance 
    from the current mean.

Procedure Process(S)

    current <- S
    popped <- empty sequence

    while size(current) > 2

        mean <- Average(current)

        closest_distance <- infinity
        closest_item <- undefined
        tie <- false

        for each item x in current

            distance <- |x - mean|

            if distance < closest_distance

                closest_distance <- distance
                closest_item <- x
                tie <- false

            else if distance = closest_distance

                if x has a different value from closest_item
                    tie <- true
                else
                    continue

        if tie = true
            return current, popped

        remove one occurrence of closest_item from current
        append closest_item to popped

    return current, popped
```