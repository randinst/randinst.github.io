---
title: "Disorder as a State"
excerpt: 'Our considerations center around the prescriptive methods originating from acknowledged or assumed unknowability cascades that become operationalized in spite of definitions that should not make operationalization possible.'
mathjax: true
date: 2026-06-30T15:34:30-04:00
categories:
  - POS
tags:
  - Models
---

---

*This text came to be largely as a result of the author’s concern with a perceived systematic overstatement in certain statistics claims relating to predictability and model (un)reliability across applied domains. It is intended to clarify the distinctions in terminology found both in statistics and the more informal heuristic conversations, as well as to make claims of its own to help improve definitions of state spaces that allow for forecasting. The central arguments on the matter of disorder proceed from determinism and nonlinearity on physical grounds, taking into account conservation in all forms. Sections in the second half include less common examples in an attempt to gain and use intuition about relevant bounds.* 

---

## Introduction

Given a convenient treatment of unspecified disorder as the result of states spawning outside an operational initial baseline, it can be assumed that the produced disorder inevitably becomes either a new baseline or an extension of the original baseline, deeming descriptions of states as disordered nonoperational as the initial state ceases to be a point of reference. It is the result of sustained dynamics on a system creating disorder on top of the already established disorder and continuing in infinite regress. Attempting to use such disordered states or call a state ‘disordered’ in the first place may require self-reference powerful enough to match the infinite regress where time alone will not suffice due to possible changes in the dominating scales. 

If instead, a whole system is to be described as disordered, relations to an ordered system must be made, which is more optimally achieved in fields invoking chaos, compactness, entropy, classical probability, as their versions of disorder can be successfully operationalized; we suppose that certain field syntheses and deliberate extensions of finite systems cannot. 

We additionally suggest that the definition of disorder, as colloquially understood, cannot match its underlying system if it cannot be measured, and that when measured it becomes order to the model. Operationalization demands finite rules even when the rules involve infinities, where any object having a set of parameters has not every other possible parameter. This implies that bounds cannot reveal the source of those bounds. 

Relating to terming and describing phenomena, we extend that properties of a state are not direct properties of its system, and that properties of a system are not direct properties of its environment. 

Our considerations center around the prescriptive methods originating from acknowledged or assumed unknowability cascades that become operationalized in spite of definitions that should not make operationalization possible.


## Definitions 

<em>Determinism</em>: The idea, systems approach, or philosophy that presumes all events are ‘written’ and inevitable, that a given phenomenon has only one path. It is grounded in physical law or system constraints. 

<em>Chaos</em>: A description of deterministic systems that are defined by their sensitivity to initial conditions and characterized by events being unpredictable over increasingly long periods. 

<em>Complexity</em>: Distinct from being merely complicated and not to be confused with chaos, it is a metric of a system for the number of interacting parts producing emergent behavior.

<em>Entropy</em>: The measure of the number of available microstates for a given macrostate, in its precise physical and information-theoretic definition. 

<em>Order & Disorder</em>: In a general sense, the system’s adherence to, or deviation from, expected model baselines, with the deviation potentially being from the model itself. Native to and directly operational in statistical mechanics and condensed matter physics as a property, and in clinical medicine as an entity. Other fields borrow the terms and use them largely rhetorically.

<em>Certainty & Uncertainty</em>: The observer’s states of perfect and imperfect knowledge, derived from confidence in the model.

<em>Predictability & Unpredictability</em>: The ability and inability to approximate a future state of the system. Often conflated with randomness when the observer's limitation is treated as a property of the system.

<em>Variance</em>: A statistical measure of how widely values are spread out from their mean, calculated as the average of squared deviations.

<em>Volatility</em>: The rate and magnitude of deviation from a baseline over time. In finance and risk management, it is the standard deviation of returns over a given timeframe. 

<em>Noise</em>: The variation in a signal which degrades that signal, measured by its magnitude relative to the signal rather than its origin.

<em>Randomness</em>: The absence of patterns; often the result of all possible outcomes being equally likely. Misused when projected onto systems that have merely unpredictable outcomes.

<em>Stochasticity</em>: The property of a process whose evolution is described by probability distributions over many possible paths rather than a single path. Colloquial use often conflates it with pure randomness, when in reality such processes are structured and have patterns that result from defined probabilities and rules.

## Proof 

Let $S$ be the set of admissible states, let $\Phi(M)$ denote the family of properties represented by the operative model $M$, where each $\psi \in \Phi(M)$ is a function $\psi:S\to V_\psi$, and let

$$
\Pi:S\to O
$$

be an arbitrary admissible strategy with output space $O$.
The represented properties induce an observational equivalence relation on $S$:

$$
s\sim_M s'
\iff
\forall\,\psi\in\Phi(M),\;
\psi(s)=\psi(s').
$$

**Axiom (Operational Closure)**

Every admissible strategy satisfies

$$
s\sim_M s'
\Longrightarrow
\Pi(s)=\Pi(s').
$$

**Representation Theorem**

Let

$$
q:S\to S/{\sim_M}
$$

be the quotient map sending each state to its observational equivalence class. Then every admissible strategy factors uniquely through the observational quotient. That is, there exists a unique function

$$
\widehat{\Pi}:S/{\sim_M}\to O
$$

such that

$$
\Pi=\widehat{\Pi}\circ q.
$$

*Proof.* Operational Closure implies that $\Pi$ is constant on every equivalence class of $\sim_M$. Define

$$
\widehat{\Pi}([s])=\Pi(s).
$$

This is well-defined because

$$
[s]=[s']
\Longrightarrow
s\sim_M s'
\Longrightarrow
\Pi(s)=\Pi(s').
$$

By construction,

$$
\Pi=\widehat{\Pi}\circ q.
$$

Uniqueness follows because every element of $S/{\sim_M}$ is of the form $[s]$.

*Remark*. The quotient

$$
S/{\sim_M}
$$

is the *observational state space* induced by the operative model. 

**Structural Exclusion**

A subset

$$
X\subseteq S
$$

is *observationally saturated* if it is a union of equivalence classes of $\sim_M$.
A phenomenon $X$ is *structurally excluded* if it is not observationally saturated. Equivalently,

$$
\exists\,x\in X,\;
\exists\,y\in S\setminus X
\quad\text{such that}\quad
x\sim_M y.
$$

Structural exclusion is a stronger claim than ‘unknown’ or ‘hard to identify.’

**Remark (Representation Invariance)**

If $X$ is structurally excluded, then there exist

$$
x\in X,
\qquad
y\in S\setminus X
$$

such that

$$
x\sim_M y.
$$

By Operational Closure, every admissible strategy satisfies

$$
\Pi(x)=\Pi(y).
$$

Thus admissible strategies are invariant across observationally indistinguishable states, even when those states differ in membership in a structurally excluded phenomenon.

**Corollary (No Perfect Operational Recognition)**

If $X$ is structurally excluded, then no admissible strategy can perfectly determine membership in $X$. More precisely, there exists no function

$$
g:O\to\{0,1\}
$$

such that

$$
g(\Pi(s))=\mathbf{1}_X(s)
\qquad
\forall s\in S,
$$

where $\mathbf{1}_X$ denotes the indicator function of $X$.

*Proof.* Suppose, for contradiction, that such a function $g$ exists. Since $X$ is structurally excluded, there exist

$$
x\in X,
\qquad
y\in S\setminus X
$$

such that

$$
x\sim_M y.
$$

By Operational Closure,

$$
\Pi(x)=\Pi(y),
$$

so

$$
g(\Pi(x))=g(\Pi(y)).
$$

However,

$$
\mathbf{1}_X(x)\neq\mathbf{1}_X(y),
$$

contradicting

$$
g(\Pi(s))=\mathbf{1}_X(s)
\qquad
\forall s\in S.
$$

Therefore no such function exists.

**Corollary (Representation Refinement)**

Structural exclusion is relative to the represented family of properties. Let $M^\ast$ be a refinement of $M$ satisfying

$$
\Phi(M)\subseteq\Phi(M^\ast),
$$

and let $\sim_{M^\*}$ denote the induced observational equivalence relation. 

$$
s\sim_{M^\ast}t
\Longrightarrow
s\sim_M t.
$$

Equivalently, every $\sim_{M^\ast}$-equivalence class is contained in a $\sim_M$-equivalence class.
Consequently, if a subset

$$
X\subseteq S
$$

is observationally saturated with respect to $\sim_{M^\ast}$, then $X$ is not structurally excluded relative to $M^\ast$.

*Proof.* If

$$
s\sim_{M^\ast}t,
$$

then $s$ and $t$ agree on every property in $\Phi(M^\ast)$. Since

$$
\Phi(M)\subseteq\Phi(M^\ast),
$$

they also agree on every property in $\Phi(M)$, so

$$
s\sim_M t.
$$

Hence every $\sim_{M^\ast}$-equivalence class is contained in a $\sim_M$-equivalence class. If $X$ is observationally saturated relative to $\sim_{M^\ast}$, then by definition it is not structurally excluded relative to $M^\ast$.

Consequently, no admissible strategy can systematically distinguish or respond differently to a structurally excluded phenomenon; doing so requires refining $\Phi(M)$, which changes the operative model, not just acts within it. This gives a reading of Knight's distinction between measurable risk and true uncertainty [1]: risk is represented in $\Phi(M)$ and thus operationally available; true uncertainty is structurally excluded, and stays that way until the representation changes.

Structural exclusion accordingly rules out designed or orchestrated benefit where exploiting a phenomenon requires a represented distinction to exploit, and a structurally excluded one has none. It does not imply that no benefit can arise incidentally, nor that such benefit exists. A genuine extremity may admit no compensating benefit at all.

## Deterministic Chaos

Chaos and complexity usually cannot be said to be global properties of most systems, as they emerge from the interaction between chaotic regions and stable ones. Neither in physics nor in social environments can chaotic motion fill up space uniformly, and predicting where and when chaos appears can be as difficult as predicting the chaos itself. The observer must decide which degrees of freedom are treated as active and which are averaged, held constant, or ignored, whether it is applied Navier-Stokes equations or economic agent-based models. A system that contains both mixtures and solutions cannot be treated as purely a solution due to the different divergence timeframes they operate in.

In chaotic systems governed by nonlinear wave equations, extreme outliers (such as rogue waves) can emerge from the lawful and bounded, compounding interactions of smaller waves. They are high-energy solutions to the known equations, where many stable, fast-decaying degrees of freedom can collapse into and be expressed as functions of a few dominant, unstable ones. To be surprised by them, the observer must be ignorant of the compounded interactions. Dynamical systems theory formalizes this through center manifold reduction and related structures, including slow and inertial manifolds [2]. 

In another case, a perfectly uniform matter cloud with an unstable equilibrium is bound to break by any infinitesimal density fluctuation. This creates a potential well that attracts more matter, continuously deepening the well in turn. Jeans instability effectively describes such runaway processes [3]. 

As such, we are inclined to suggest that any example of surprise by chaotic motion that we can conjure is a result of limitations in observation and not the system’s nature. If the opposite is assumed, it would imply the observer should be surprised by the system itself at all times.

A central idea inspiring classical mechanics supposes that if there existed a creature with complete knowledge of a certain moment’s every force and object, every motion and position, such a creature would have no doubts about the next or previous moment. This creature is called Laplace’s demon, after its presenter, Pierre-Simon de Laplace. 

Those equipped with the tools of chaos theory have the full equations and the knowledge that extremes are possible, sometimes inevitable, though unpredictable. Most others, including the statistician, can only afford more simplified and primitive models that often deal with averages; the extreme falls entirely outside their model’s possibility space. 

Regardless of the type of observer and the methods, a gap can be expressed that accounts for the unobserved, in the form of $s_0 \to s_n$ which expects direct cause and effect, while reality may demand intermediate steps with the true $s_0 \to (s_1 \to \cdots \to s_{n-1}) \to s_n$.

## Frame Rate 

Under the assumption of a classical, strictly deterministic reality, uncertainty does not exist as a feature of the world and can only be a description of the observer's limits. Borrowing a term from applied fields, we invoke a ‘frame rate’ as the frequency of the system’s sampling whose intervals contain the unmeasured. The higher the frame (state) rate, the more predictable the next frame (state). 

One Laplace’s demon requires no observation interval at all to predict every state. For any observer with $\Delta t > 0$, the interval gaps between observations become unknown variables, and the endstate an unsolvable unknown.
Prediction error as a function of observation gap $\Delta t$ is, in:

*Linear systems* 

$$\text{Error} \propto \Delta t$$

*Nonlinear systems* 

$$\text{Error} \propto e^{\lambda \cdot \Delta t}$$

where $\lambda$ is the Lyapunov exponent. For the Lorenz system with $\lambda \approx 0.9\ \text{day}^{-1}$, $\varepsilon(t) \approx \varepsilon_0 \cdot e^{0.9 t}$, prediction error doubles every $\approx 0.77$ days. The Taylor expansion clarifies the frame-rate dependence directly:

$$x(t + \Delta t) \approx x(t) + \dot{x}(t) \cdot \Delta t + \frac{1}{2}\ddot{x}(t) \cdot \Delta t^2 + \cdots$$

As $\Delta t \to 0$ (high frame rate), higher-order terms become negligible and with $x(t + \Delta t) \approx x(t)$, prediction is nearly perfect. As $\Delta t$ grows, nonlinear terms accumulate and chaotic divergence appears.

Ignoring the consideration for measurement of the intermediate states between the initial and the end state creates difficulty in making definitions for the unquantifiable. The describer of the system becomes an observer of the supposed unknowns the model contains.

## In Application


If measurement is forced upon hence precision loses meaning, or is of something other than assumed, the result may have no relation to the system measured and possibly even its model. Presuming educated measurements, a buildup of results is bound to display some useful patterns eventually; the limits of assumptions, expectations based on those patterns are to be discussed.

The limits enforced by conservation laws are known, with certainty, to bound all physical phenomena. It is only that such a bound is not the most useful reference when dealing with the many human-sized affairs – in terms of not fully controlled, even chaotic environments. At certain scales, universal bounds may become unhelpful, too high to concern the observer, and instead the local interactions to most define the next short term configuration. Within an active, dense medium, a part of that medium has not the ability to move arbitrarily; time-bound constraints exist due to crowding, thus at a given short timeframe the hard limit is not the binding constraint.

It remains that models require defined bounds, even where those bounds include infinities. Compactness may be used to more strictly define them. Infinities will imply known unknowns, although their points of beginning may be exactly known. A bounded and compact model within $[,]$ will imply a fully closed, 'controlled' environment whose edges are certain, and whatever is outside them would be unrelated to their insides. A bounded but not compact model of $(,)$ and variations of open intervals, we argue, will in turn be far more common in physical systems of interest: a rough base or limit may exist, but the edge remains not fully specified. 

The following proposition concerns the use of fundamentally different devices in dealing with the same underlying physical systems. A physical laws-based approach grants bounds but not baselines, while in a common statistical model built from historical data with no theoretical ceiling, there is typically an assumed baseline but no bound, unlike models with bounded support. This does not concern the deep ontological differences of their respective notions regarding states. It could then be said that in order for one to cover both bounds and baselines, the tools of statistics and physics ought to be combined. In engineering, a forced merger of this kind is used successfully, given the engineers’ ability to control, respond to closed and open environments. Outside of engineering, forcing a merger between the methods based on natural law and methods grounded in sociological observation, may be neither trivial nor fruitful. Nancy Cartwright’s *simulacrum* account of explanation suggests that fundamental and phenomenological laws, such as of physics and economics, do not mix easily; there is no guarantee they can be made consistent despite their local effectiveness [4]. 

Information and noise are foundational to all applied fields. Shannon entropy is a measure of the uncertainty within a random variable, or, applied to a channel, the uncertainty introduced by its noise [5]. A channel may constitute one of the unknown frames stated under Frame Rate, being the unobserved period in between two known states. Information theory can quantify the uncertainty and noise of a channel, but not predict the specific interference configurations within it. 

Shannon entropy only describes in practical terms the chances of a signal passing through a black box. In treating a channel as a system, to decision theory this leaves much to be desired; the evaluation of a channel even to the highest degree can only help select for optimal action based on its statistical properties but not on interference configurations. Certain filters can still be produced to search for matching signals, although when this channel-system is high in noise, the observer is left to limited devices. A special case exists within information theory where interference configurations are structured and known in advance. Through Costa’s dirty paper coding, a transmitter can pre-cancel precisely the known component before passing a signal, achieving the same capacity as if it did not exist [6]. The channel’s genuine noise remains untouched and not cancellable. In our discussion, this technique is an example of an assumed generally random system being tamed by knowledge of the behaviour of its component.

It may often seem trivial to suggest, or even insist upon the extension of model bounds where outliers have either occurred, or where the analyst is encouraged to have a hunch about them. We suppose that optimal decisionmaking cannot occur while the bounds are inflated beyond any relation to normal variance, unless utility lies entirely in the abnormal. Bounds enclose and reflect the system and its model, both of which can only exist as they are because their respective bounds exist. When bounds are turned abnormal, even if temporarily, the system is assumed different from what it is in actuality.

From a geometric and metaphorical view, given a bound that has been broken already, decisionmaking can continue with knowledge of data of concern, that is <em>(1) the area of the broken bound (2) the ‘volume’ released through the bound (3) the speed at which the ‘volume’ is released, or how far and wide it stretches.</em> Given a preventive situation instead, knowledge of how easily, or how much of the bound can possibly be broken, will be useful. 

A metric that might concern decisionmaking is the rate of change in variance, and not simply because of the decisionmaking speed presumed required to match it. The higher the rate of change, the more unusual the behavior, and the higher chance of long excursions outside established bounds. Such a case implies that the system may be susceptible to such excursions.

---

In application, it is worth remembering that a model can become more unreliable instead of credible when given more data, whether that data is used to recognize uncertainty (positive), or gets incorporated into false assumptions (negative).

### Benefitting from Disorder

To benefit from what is assumed to be disorder, we pose that the ‘disorder’ in question must be a form of variance that is not unpredictable. This variance would either need to be contained, or expected to break normal trends, in order to be fruitful. 

The issue of the ‘disorder’ definition here resurfaces, as change in volatility must be the metric to predict. Two implications can be noted. First, repeating an implication already suggested: if disorder is contained and controlled, it cannot be disorder. Secondly, any persistent analysis of the changes in volatility will inevitably result in dealings with volatility of the volatility, which in turn can have its own volatility, and so on, in infinite regress. 

$$\text{Level } 0: \text{ returns } r_t$$ 

$$\text{Level } 1: \sigma(r_t) \quad \text{(volatility of returns)}$$ 

$$\text{Level } 2: \sigma(\sigma(r_t)) \quad \text{(vol of vol)}$$ 

$$\vdots$$

To benefit from $X$, one must (1) identify $X$, (2) predict $X$, (3) position for $X$, (4) measure $X$. 

If $X$ is 'disorder' or an 'unknown unknown,' steps 1–4 are impossible by definition. If steps 1–4 can be performed, $X$ is not disorder but variance in a parameter, which is operational and modelable.

In a common scenario, an observer may expect to benefit from disorder, profiting by setup, if the system crosses a certain bound. The crossing itself becomes another dimension to operationalize. This can be negligently extended by the observer who states that once the system is out of bound, the only thing to be concerned with is that it is out of bound. A specific yet usual kind of practitioner, such as an options trader, will not accept this idea, as theta decay and general timing to act matters irrespective of any bounds crossing. The options market itself can exist precisely because it is a market that trades volatility. Using Implied Volatility (IV), ‘disorder’ has been operationalized as a traded instrument with its own model. 

Rather frequently, the notion that one can and does benefit from social disorder is heard in conversation. Our demand for strict definitions makes this another difficulty to work with, as it should be quantified so that the order/disorder distinction or scale would exist. Attempts at describing social phenomena by terms native to physics and its offspring (such as thermodynamics for ‘entropy’, materials science for ‘brittleness,’ ‘toughness,’ and others), are highly likely to fall short in practice and not be well defined or operational, as per Cartwright’s simulacrum [4]. Variables like microstates, entropy, and others cannot be specified or map onto an arbitrary social circumstance. Additionally, our observations of profits from social disorder appear to once again originate largely from proxies of disorder and not real unpredictability. The profiteer must either know the order of the alleged disorder, or trade something that responds to unpredictability.

Concavity and convexity, if assumed a universally applicable tool, must then also be property of a function over a domain. Such a function is bounded on its own terms, and other functions can act on, or compose with it. Benefiting from disorder via convexity/concavity still requires operationalization with specified behaviour and boundaries. 

At a fundamental level, any system can be viewed as information passing through a channel. With the section title taken at face value, wanting to benefit from disorder in the output would mean wanting more noise in the channel.

## Issues with Fat Tails

Fat-tailed distributions are every so often presented as grounds for claiming unknowable disorder. In such claims, the view that they should apply to many, if not most systems, may be implicit. The conclusion that fat tails are omnipresent would require it to be produced from some average of fat-tailedness across systems.

As derived from bounded uncertainty based on observation, the fat-tailed distribution also requires operationalization, including specifying bounds, parameter definitions, and model structure. Similar to volatility of volatility, a regress of uncertainty likewise requires parameterization, making its distributions fully defined at each layer of uncertainty [7]. This operationalization makes the analyzed regress no longer true uncertainty, since the model now specifies values that are meant to be unknown by definition. 

Although implied, a key detail in the fat-tailed and normal distribution distinction is often unaccounted for: the entirety of tails themselves and not the peak alone. Fat-tailed distributions’ tails decay much slower than those of other curves. Not only are abnormal events assumed to be more common, but the probabilities of different degrees of abnormality decay so slowly, flattening the line enough that moderate and extreme deviations can appear similar in likelihood. Taken literally, such similarity would suppose that events slightly outside the narrow average may have similar chances of occurring as extinction events. Continuing in this reductio: if the latter are nearly as probable as the former, yet the system continues to exist, the system appears not vulnerable but remarkably resilient.  

Fat tails can arise from basic limit theorems for sums and mixtures of random variables [8], and are not specific to actual ‘unknown unknowns.’ Claiming their general applicability would imply that most real systems share the properties of these mathematical devices used to produce fat tails, randomness being a characteristic. That would in turn suggest a general lack of patterns in the physical reality, which cannot be true. 

Complex and chaotic systems are layered across scales, potentially with different effective distributions at each one. Fat tails at one layer will not necessarily translate into fat tails at the aggregate, especially when a Gaussian layer of high model certainty dominates in the observable space.

### Infinities

Applied to a real system, the common and unaltered fat-tailed distribution would suggest the possibility of infinite variance. While the common Gaussian also allows arbitrarily large outcomes, its faster-decaying tail treats them as highly unlikely. As such, the analyst, wanting to reap the utility of the distributions while handling their limitations, truncates them in practice [9]. Another dilemma arises in deciding how the tails are to be truncated, since this effectively requires a separate model for the bounds. Truncation must treat the system as bounded and operational, which the notions of unbounded uncertainty contradict. We must recognize that truncating a distribution will fundamentally alter its properties, forming a different ‘final’ distribution.

**Power Law**

Untruncated: 

$$P(X > x) \sim x^{-\alpha}, \quad x \in (x_{\min}, +\infty)$$

Truncated: 

$$P(X > x) \sim x^{-\alpha}, \quad x \in [x_{\min}, x_{\max}]$$

where $x_{\min}$ is the minimum possible value (e.g. $-100%$) and $x_{\max}$ is the maximum possible value, both of which must be specified.

**Renormalization**

Original: $\displaystyle\int_{-\infty}^{\infty} f(x),dx = 1$

Truncated: $\displaystyle\int_{a}^{b} f(x),dx \neq 1$, so it must be renormalized: 

$$f_{\text{truncated}}(x) = \frac{f(x)}{\int_a^b f(x),dx}$$

This changes the density function.

**Moments**

Original mean: $\displaystyle E[X] = \int_{-\infty}^{\infty} x f(x),dx$

Truncated mean: $\displaystyle E[X \mid a \le X \le b]$ which is different, and likewise for variance, skewness, and all higher moments.

**Tail Behavior**

Original: $P(X > x) \sim x^{-\alpha}$ (power law)

Truncated: $P(X > x \mid X \le x_{\max})$, a different formula; near $x_{\max}$ it no longer behaves like a power law.

--- 

$x_{\max}$ must be specified, which makes for the introduction of bounds and not a persisting infinite support. 

### Scale

Applying fundamentally scale-differing phenomena to the same plane for purposes of inference, forecasting, or pattern determination, can be a slippery matter. 

In a common example, power law may without question map rather cleanly onto wealth distribution and certain biological systems: The former case makes that the wealthiest of people are in a category error from their inclusion with the minimum or average wage-earning individuals. They could be said to be different species in economic behavior. Even Everest does not look too steep among its Nepalese neighbors. The latter case and its counterparts, despite having their organizational tendency described by power law, often still do not reveal behaviours that could be used in prediction of desired metrics, or prescription of actions. 

Outliers found in historical data means that normal variance that excludes them cannot always be sufficient for bound definitions. If outliers are included, handling them as arbitrary data points will certainly not be sufficient. Given only a small number of outliers, simply extracting them and comparing them with each other may also provide no new knowledge to work with; this would depend on the system at hand, of course.

In creating a model meant to be generative and probability-worlded, making many observations of the system or its likes at different scales will be useful, as it might produce more grounded statistics to work with. As such, we posit that outliers are sometimes ignored to be able to form and keep reliable models, where a logical consistency of making operations on the model is the usual aim. 

The fat tail may be a result of scale choice and population mixing, not an intrinsic property of height. Thus, the selection itself is to be addressed more often than the outliers-as-bounds of every model. Outliers that cross bounds and are assumed unpredictable have nothing to offer to a limited observer in practice. Outliers that have a real connection to the model and can affect other data points do give the observer something to work with, which still does not mean that a category error would not result when comparing the outliers with near-averages. 

The above also signals that mixing statistics with probability theory without grounding in data source consistency may strip any real distinction between the two. Statistics can stand in for probability only when an independent theoretical or causal basis exists for separate instances governed by the same process; historical frequency alone can not establish this, with history offering only one realization of each event. The notion that outliers or ‘unknown unknowns’ repeat at a certain empirically observed rate has no logical consistency either: if it is cyclical and predictable, or at least expected, it is then not unpredictable and not unexpected.

---

---

#### References 

[1] Frank H. Knight, <em>Risk, Uncertainty, and Profit</em> (1921).

[2] Guckenheimer, J., & Holmes, P., <em>Nonlinear Oscillations, Dynamical Systems, and Bifurcations of Vector Fields</em> (1983).

[3] Jeans, J. H., “The Stability of a Spherical Nebula,” <em>Philosophical Transactions of the Royal Society A</em> (1902).

[4] Nancy Cartwright, <em>How the Laws of Physics Lie</em> (1983).

[5] Shannon, C. E., “A Mathematical Theory of Communication” (1948).

[6] Costa, M. H. M., “Writing on Dirty Paper” (1983), <em>IEEE Transactions on Information Theory</em>.

[7] Taleb, N. N., & Cirillo, P., “The Regress of Uncertainty and the Forecasting Paradox,” Risks, 13(12), 247 (2025).

[8] Gnedenko, B. V., & Kolmogorov, A. N., <em>Limit Distributions for Sums of Independent Random Variables (1954)</em>.

[9] Embrechts, P., Klüppelberg, C., & Mikosch, T., <em>Modelling Extremal Events for Insurance and Finance (1997)</em>.

