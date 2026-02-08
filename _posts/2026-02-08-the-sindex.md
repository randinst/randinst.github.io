---
title: "The Sindex"
mathjax: true
date: 2026-02-01T15:34:30-04:00
categories:
  - Design 
tags:
  - Models
---

*Apologies due in advance to Dante, and a warning to the unsuspecting mind about the lack of rigor and rampant pseudomathematics of the following text.* 

The premise begins with the recognition of the ancients' ingenuity in defining human vices in religious texts with clear bounds. Certain limits appear to have existed in the sources of intent and people’s behavior, which have often led to the analysis of individual actions since, in literature as much as in the court of law. The seven deadly sins only give us a morally negative side of human behavior, and since there isn’t such a popular set of positive traits, in exploration we will constrain ourselves with sins due to their incentivizing factor. This limitation may not be a poor condition if we recognize that the list of vices, in addition to being a guide to what ought to be frowned upon and not indulged, is also a decent indicator of motivation of players in games. As we will see, in certain conditions the absence of sin in a player can sometimes be a negative harming the system. We will take into account players' levels of influence and sin (motivation), which reveal imbalances usually taken for granted in analysis but rarely quantified. The subjective nature of the archaic sin list will not allow us to build a model with variables we can fully trust, nor will it allow for falsifiability. As such, we are only to experiment with values without putting the highest confidence in them. By enumerating players by influence we assign leverage, and by adding motivation levels using sin values we try to infer who may be inclined to use it. 

## Concept 

The basic principle that will be used to map out pressure points of motivation in econopolitical scenarios involves naming the players and lining up the seven possible sins to each. Then, assigning by guesswork numerical values to every sin and summing each player's sins into totals. For sin magnitudes we will take the scale between 0 and 1. 

|  Sin     | $p_1$    | $p_2$    | $p_3$    | ...   | $p_n$    | Total |
|----------|----------|----------|----------|-------|----------|-------|
| Pride    | $s_{1,\text{Pr}}$ | $s_{2,\text{Pr}}$ | $s_{3,\text{Pr}}$ | ...   | $s_{n,\text{Pr}}$ | $\Sigma \text{Pr}$  |
| Greed    | $s_{1,\text{Gr}}$ | $s_{2,\text{Gr}}$ | $s_{3,\text{Gr}}$ | ...   | $s_{n,\text{Gr}}$ | $\Sigma \text{Gr}$  |
| Lust     | $s_{1,\text{Lu}}$ | $s_{2,\text{Lu}}$ | $s_{3,\text{Lu}}$ | ...   | $s_{n,\text{Lu}}$ | $\Sigma \text{Lu}$  |
| Envy     | $s_{1,\text{En}}$ | $s_{2,\text{En}}$ | $s_{3,\text{En}}$ | ...   | $s_{n,\text{En}}$ | $\Sigma \text{En}$  |
| Gluttony | $s_{1,\text{Gl}}$ | $s_{2,\text{Gl}}$ | $s_{3,\text{Gl}}$ | ...   | $s_{n,\text{Gl}}$ | $\Sigma \text{Gl}$  |
| Wrath    | $s_{1,\text{Wr}}$ | $s_{2,\text{Wr}}$ | $s_{3,\text{Wr}}$ | ...   | $s_{n,\text{Wr}}$ | $\Sigma \text{Wr}$  |
| Sloth    | $s_{1,\text{Sl}}$ | $s_{2,\text{Sl}}$ | $s_{3,\text{Sl}}$ | ...   | $s_{n,\text{Sl}}$ | $\Sigma \text{Sl}$  |
| Total    | $\Sigma_1$    | $\Sigma_2$    | $\Sigma_3$    | ...   | $\Sigma_n$    |       |

In this table we express:

(i) $s_{i,j}$ = sin value for player $i$, sin $j$,

(ii) $\Sigma_j = \sum_{i=1}^{n} s_{i,j}$ (row sum of sin total across all players)

(iii) $\Sigma_i = \sum_{j=1}^{7} s_{i,j}$ (column sum of player $i$'s sin values)

A scale from -1 to 1 can be used if more dimensions are desired, giving negative sins—virtues as inverses of sins, where we can imagine Diligence as the opposite of Sloth, Patience as the opposite of Wrath, and so on. It should be noted, however, that introducing more dimensions to a subjective model will make it even less reasonable and consistent. Nevertheless, considering that we are only working with the totals of sin values due to our strict interpretation, the individual sin value matters much less than the cumulative sin.

Social structures, events, and happenings may be layered (macro, micro, meso), whereby the model allows for analysis of each layer individually, possibly later taking into account the motivations emerging from lower to higher layers. Another aspect to recognize on a per-scenario basis is the nature of the happening, where the state selected for analysis may be based on linear and non-linear expectations.

We can say that the Sindex model is most reasonable when the players can directly influence each other, compete for the same or similar resources, and their motivations manifest in comparable ways. 

For visualization, it is worth ordering players by influence to standardize commonly appearing patterns. In deciding this, only the initial and not the potential influences should be taken into account. The levels of influence of some players may be so similar that it cannot be said with certainty which one has more. This will have to be tolerated, unless the motivations of one or more players become so significant that all of the values must be reset—if we want to keep them all in the same bounded system.

## Interpretation and Analysis

Applying this method to historical examples, we try for recurring patterns that may emerge in different scenarios. For the sake of demonstration, a surface-level understanding of the presented events must suffice, and it is hoped that there will not be serious misrepresentation. As with any social dynamic, nuances may be present, and extensive analysis of each event would be wasteful when only a showcase of the method is the aim. 

### The Arab Spring

A series of pro-democracy protests in the Arab world between 2010 and 2012 that resulted in the overturning of Tunisian, Egyptian, Libyan, and Yemeni governments (Blakemore, 2019).

|  Sin     | Intl. Community | Gen. Public | Protesting Public  | Military  | Regime |
|----------|-------------------------|----------------|--------------------|-----------|--------|
| Pride    | 0.2 | 0.4 | 1.0 | 0.7 | 0.8 |
| Greed    | 0.3 | 0.6 | 0.7 | 0.7 | 1.0 |
| Lust      | 0.4 | 0.5 | 1.0 | 0.4 | 0.8 |
| Envy      | 0.1 | 0.6 | 0.9 | 0.6 | 0.4 |
| Gluttony | 0.6 | 0.4 | 0.6 | 0.7 | 0.9 |
| Wrath     | 0.4 | 0.7 | 1.0 | 0.8 | 0.9 |
| Sloth      | 0.9 | 0.7 | 0.1 | 0.3 | 0.3 |
| Total    | 2.9 / 7 | 3.9 / 7 | 5.3 / 7 | 4.2 / 7 | 5.1 / 7 |

![Player motivation totals for the Arab Spring](/assets/images/arab_spring.png)

Protesters were an explosive, contagious force that could be said to have had maximum Pride based on their basic dignity demands, Lust for freedom, and Wrath against the injustices seen and experienced. While their Sloth was minimal, other sins like Greed for resources and Envy of other nations’ freedoms must too have been prevalent, and so with Gluttony, for change. 

The regime could be characterized as a rather stereotypical kleptocracy, clinging to power with high Pride in its authority and Wrath against challengers. Its Greed was maximal, as it controlled national wealth. Gluttony and Lust (for resources, power) were high, and Sloth was relatively low.

The military's motivations were pragmatic. High Greed and Envy protecting the economic empire. Its Wrath was a tool, its Pride institutional. Its mid-range Sloth reflects a preference for stable hierarchy over chaotic change.
The general public could be marked by higher Sloth that stemmed from clinging to whatever normalcy could be had. Their Gluttony and Lust at large may have been for safety and stability, not revolution; moderate Envy and Greed were for a better life, but not yet actionably so.

The international community was distant, self-interested. Its Greed was for regional stability, its Sloth a reluctance for costly intervention. Its mid-level Pride and Wrath were mostly rhetorical, and whatever Lust or Envy they had was likely more for the novelty of the events.

### Social Media and Virality

Having started off as types of mainstream internet phonebooks in the mid-to-late 2000s that stemmed from simpler online forums, social media platforms did not take long to become ecosystems with their own food chains. 

|  Sin     | Users | Content Creators | Platforms  |
|----------|---------|----------------|------------|
| Pride    | 0.9 | 1.0 | 0.8 |
| Greed    | 0.8 | 0.9 | 1.0 |
| Lust      | 0.9 | 0.8 | 0.9 |
| Envy      | 1.0 | 0.9 | 0.9 |
| Gluttony | 1.0 | 0.8 | 1.0 |
| Wrath     | 0.8 | 0.6 | 0.5 |
| Sloth      | 0.8 | 0.6 | 0.2 |
| Total    | 6.2 / 7 | 5.6 / 7 | 5.3 / 7 |

![Player motivation totals for social media](/assets/images/social_media.png)

On social platforms, the majority of users and content creators could be speculated to be moderately to highly slothful, as we can generalize from looking at both the high usage (low Sloth) and the way they publish and interact (high Sloth).

Pride, Greed, Gluttony, Envy and Lust may well be near-maximal for every player. The platforms are highly competitive with one another, engineering for time spent by users and similar metrics. Content creators depend on rather fragile income and attention streams, and users engage in both the consumption of others’ produce and showmanship of their own. It could be said these sins can manifest in public spaces as much as in private interactions.

Sins like Wrath in this and similar cases are more obscure, and it is difficult to say how much anger the players have overall. For necessity, we can say users and content creators have relatively high Wrath, while platforms have it low to moderate.

This is an example of a self-perpetuating system based on a stable high motivation equilibrium. We can speculate that rising sin values of one player tend to increase the sin values of other players, upstream influence especially.

### 2008 Housing Bubble

A primarily US-originating real estate bubble and its consequent bursting in 2008 that led to a recession and global financial crisis, the causes of which included deregulation, bond-bundling and the prevalence of mortgage-backed securities, corporate and retail greed alike, and fraud (Duignan, 2024). 

|  Sin     | Borrowers | (Inv.) Banks | Regulators  |
|----------|-------------------------|----------------|--------------------|
| Pride    | 0.8 | 1.0 | 0.7 |
| Greed    | 0.7 | 1.0 | 0.4 |
| Lust      | 0.9 | 0.8 | 0.2 |
| Envy      | 0.9 | 0.9 | 0.3 |
| Gluttony | 0.8 | 1.0 | 0.1 |
| Wrath     | 0.3 | 0.4 | 0.1 |
| Sloth      | 0.8 | 0.7 | 1.0 |
| Total    | 5.2 / 7 | 5.7 / 7 | 2.8 / 7 |

![Player motivation totals for the 2008 housing crisis](/assets/images/2008_housing_crisis.png)

It could be said that Pride played a large part in the actions of every participant where regulators had unchallenged trust in their models, the banks lended and traded MBS as if they had eliminated risk, and the borrowers may have felt they were legally exploiting gaps in the system. 

The high Greed, Envy, and Lust of the players should be self-explanatory, except for the regulators’, as it would be difficult to quantify how much was to be gained by them. As for Gluttony, if we treat information and opportunities as its objects, regulators might have had very little of it with regard to their risk data consumption. 

Prior to the collapse, there were hardly any things for the players to be angry about, so we assign low Wrath across the board. On the other hand, Sloth was arguably an important driver of each player’s negligence and attraction to low-hanging fruits. 

The 2008 financial crisis is where we first see the phenomenon of a “referee,” a player with the highest theoretical influence who, having either low overall sin levels while the less-powerful have them high or high Sloth while the others have Sloth low, is an enabler of highly motivated players to pursue their aims in systems with limited rules and consequences. This often leads to prolonged reckless behaviour.

### Bosnian War

An ethnically rooted conflict that took place between 1992 and 1995 in Bosnia and Herzegovina following the breakup of Yugoslavia, characterized by ethnic cleansing and the Srebrenica genocide, which ended with NATO intervention and the Dayton Peace Agreement (Lampe, 2025).

|  Sin     | Bosniak Leadership | Bosnian Serb Leadership | Intl. Community  |
|----------|-------------------------|----------------|--------------------|
| Pride    | 1.0 | 1.0 | 0.4 |
| Greed    | 0.9 | 1.0 | 0.4 |
| Lust      | 0.8 | 0.9 | 0.2 |
| Envy      | 0.7 | 1.0 | 0.2 |
| Gluttony | 0.5 | 0.7 | 0.7 |
| Wrath     | 1.0 | 1.0 | 0.5 |
| Sloth      | 0.1 | 0.1 | 1.0 |
| Total    | 5.0 / 7 | 5.7 / 7 | 3.4 / 7 |

![Player motivation totals for the Bosnian war](/assets/images/bosnia.png)

We see again an asymmetrically motivated system where the most influential player, a slothful referee, had the least incentive to act. If it had more, some of the atrocities may have been prevented. 

Both the Bosniak and the Bosnian Serb leaders were highly motivated, as per the latter’s “Greater Serbia” ambitions and the former’s wants to survive and preserve sovereignty, territory. This we note with high values of all sins except for Sloth. 

The international community had the inverse—little stake in general with the exception of high Sloth and some incentives slightly higher so we can signify its wishes for the status quo. Only once it intervened was progress made on stopping the events.

### The Later Roman Empire

The decline and collapse of imperial authority in the western half of the Roman Empire, traditionally dated to 476 CE, caused by a combination of internal decay, economic crisis, military overextension, and pressures from invading Germanic tribes, which fragmented the empire into kingdoms (Wasson, 2018).

|  Sin     | General Populace | Military | Senatorial Elite |
|----------|-------------------------|----------------|--------------------|
| Pride    | 0.2 | 0.7 | 1.0 |
| Greed    | 0.1 | 0.9 | 1.0 |
| Lust      | 0.3 | 0.4 | 0.8 |
| Envy      | 0.5 | 0.8 | 1.0 |
| Gluttony | 0.1 | 0.7 | 0.9 |
| Wrath     | 0.7 | 0.8 | 0.9 |
| Sloth      | 0.9 | 0.5 | 0.8 |
| Total    | 2.8 / 7 | 4.8 / 7 | 6.4 / 7 |

![Player motivation totals for the fall of Rome](/assets/images/roman_empire.png)

Pride of the elite stemmed from Rome's past glory and empty rituals, and in the Roman Army it emerged from unit identity. Pride of the general populace was being eroded by heavy taxation and corruption. While the general populace was trying to get by, the elite was squeezing the provinces and tax-farming, and the military can be said to have been largely driven by donatives, therefore we can assign high Greed values for all the players.

Lust can be said to go higher with influence, where the populace’s priorities in this sense were linked to basic security, the military’s to stable pay, and the elite’s to decadence and power. Envy was largely rampant, with rivalries between generals and senators for positions in the elite, between frontier and palace legions in the military, and the populace having an idea about the lives of the more powerful. The populace also had little capacity for Gluttony, whereas the military and the elite engaged in ever higher consumption of the empire’s wealth. 

All of the players can be said to have had high Wrath, as each was dealing with its own troubles. The Senate saw an increasing number of domestic conflicts across regions, and so did the military in its own way, with mutinies. The Sloth of each player was likely also high, as the populace could not do much about its exploitation and was demoralized as a result, the military was relying on old tactics and outsourced the fighting to mercenaries, and the elite was using old formulas for governance incompatible with the state of affairs at hand. 

This suggests that high Sloth, when found in many players at once, may signal a system’s growing vulnerability to opportunistic external entities, living or not. The total sin levels that grow with the levels of influence can also signal decay, that is, when the consumers are motivated but the producers are not.

### Southeast Asian Productivity Boom (East Asian Miracle) 

A period of rapid economic growth in eight East Asian economies from the 1960s through the 1990s, driven by a unique combination of high savings, heavy investment in human capital, export-oriented policies, and active government intervention that complemented rather than replaced markets (Stiglitz, 1996).

|  Sin     | Workforce | States & Corporations | Intl. Community  |
|----------|-------------------------|----------------|--------------------|
| Pride    | 0.9 | 1.0 | 0.3 |
| Greed    | 0.8 | 1.0 | 0.7 |
| Lust      | 0.9 | 0.9 | 0.5 |
| Envy      | 0.7 | 1.0 | 0.2 |
| Gluttony | 0.2 | 0.1 | 0.8 |
| Wrath     | 0.6 | 0.7 | 0.1 |
| Sloth      | 0.1 | 0.1 | 0.9 |
| Total    | 4.2 / 7 | 4.8 / 7 | 3.5 / 7 |

![Player motivation totals for the East Asian Miracle](/assets/images/east_asian_miracle.png)

East Asia was largely a devastated region as it entered the second half of the 20th century; its economies had a scratch to start from. The participants, being almost certainly aware that immediate and easy returns were hardly possible, must have been acting based upon longer-term plans, as displayed by the delayed gratification priorities from frugality and high savings rates. 

We might assign low Sloth and low Gluttony, high everything else to their institutions and workforce, as the two players were closely aligned. There was likely Pride in national development and Greed and Lust for wealth and infrastructure respectively, Envy and Wrath in relation to foreign states’ comforts and past domestic hardships.

The international community was eager to purchase and consume the cheap goods produced and only later started outsourcing its work; there was little interest outside of this. We can thus assign high Gluttony, Greed, Sloth, and moderate Lust to the international community, leaving low sin values for Pride, Envy, and Wrath.

This may be the inverse of the Fall of Rome. In East Asia, motivations of the ruling class and the middle class aligned instead of being based upon a hierarchy layer’s influence.

---

### Clarification on Sloth and Low Sin

A small disconnect appears when we note that all sins except Sloth relate to activity and movement. However, having forced Sloth in alongside the other sins for a sense of completion, this does not stop us from recognizing that Sloth alone may indicate some of the more nuanced features of a scenario. As per the financial bubble and the Balkans examples, high Sloth in the most powerful player can allow the less powerful to act without consequences if their Sloth happens to be low. If a pair of the less powerful players are in active competition with one another in this scenario, the warring may continue until one of the players effectively disappears from the game. With this, a social system tends to spiral out of control and ends up in a disaster. 

On the other hand, high Sloth and moderate everything else might indicate that a player does not intend to act regardless of his desires. 

Similar phenomena may be implied when we assign low sin values across the board to a player, although another distinction is possible. Depending on the player, the same low values on all sins could suggest different tendencies, so by separating low sin into active and passive we can differentiate between discipline and negligence. The monk, principled activist, or ethical judge to whom one assigns low sin values can be highly motivated without exhibiting most of the archaic sins, while much more common is a low-sin player who does not see a reason to act. It could be suggested that a sin like Lust should be used, for ethics or principles, but that still leaves only one significant motivation out of seven. One solution to simplifying this is to introduce negative sin values, which would give a two-sided scale of motivation totals that clarifies whether the motivation comes from the common vices or from their absence.

## Scale Balances

### Self-Perpetuating Equilibrium

Games in which players are equally highly motivated could be said to have the characteristics of almost perpetual continuity. Since the incentives cannot be satisfied at once and thus sin values do not decrease or become dissimilar among the players, resource availability makes it possible for them to remain with unchanging motivation levels and persist with certain behaviours. This can be vividly observed in cases of social media and markets. Changes to the structure and tools of the game can be made, but that does not mean motivation totals would become asymmetric as the players in such cases are usually very dependent on one another.  

### Unstable Systems

Players having significant differences in motivation levels can be a source of brittleness in a system. This would stop a system from continuing as-is for too long. A high-influence slothful referee is not creating or enforcing rules, while a demoralized workforce is not producing what its ruling class desires (the opposite could apply to precursors of revolutions). 

## Some Implications

### The Need for Layers

Any such table or payoff matrix that we create should always be confined to a layer. In a sociological sense, a layer can translate to a timeframe, size, intensity, and similar bounds linked to players. This could prevent us from analyzing unrelated or only seemingly relevant players and events. However, we can speculate that solving a social puzzle of a small game may give answers to a model setup of a related larger game, and vice versa. Our examples from the previous sections only referred to the highest layers, ignoring nuance for demonstration purposes.

### Sin Dynamics

There is the necessity of treating games as separate states and thus making new sin tables each time. Aside from the need for states, one reason for this is that even in games with high and similar motivation levels, or equilibriums, a player may still become significantly more motivated than the rest, which the model’s bounds will not allow unless the table is reset and normalized. 
We could also say that the rate of change in a player’s sin values can influence future sin values. Rapidly dropping overall sin scores may be saying that the game as we know it has concluded, while rapidly rising scores may say that the game is just picking up intensity. Fast-spawned high motivation equilibriums could result in establishing competition stability or a quick loss of any certainty. Individually, for example, a rapidly rising Wrath score is a possible precursor to “explosions,” while a rapidly rising Sloth might show a certain path to collapse.

## In Symbols

We define a state of the game at step $k$ as a tuple

$$T_k = (P_k, S_k)$$

where $P_k = \{p_1, p_2, \ldots, p_n\}$ is the set of players.

$S_k$ is the sin matrix, an $n \times 7$ real matrix where the entry $s_{i,j}(k) \in [0,1]$ (or $[-1,1]$) quantifies the magnitude of sin $j$ for player $p_i$ at step $k$. The columns correspond to the canonical seven sins (Pr, Gr, Lu, En, Gl, Wr, Sl).

Each of the 7 sins can have a number of possible actions associated with them. An action $\alpha$ is an event initiated by a player $p_i \in P_k$, associated with a primary motivating sin $j$. Its completion status is given by a variable $c(\alpha) \in [0,1]$. That is, to indicate that an action is complete, the node value for action could be said to be 0 or 1, or if more intricacy is desired, 0 and non-zero value up to 1 with a level of completion using fractions.

The execution of an action $\alpha$ by player $p_i$ in state $T_k$ can produce a new state $T_{k+1}$ via a transition function $\Phi$ with

$$T_{k+1} = \Phi(T_k, p_i, \alpha)$$

which updates the system by:

(i) Modifying the sin vector of the acting player: $\mathbf{s}_i(k+1) \neq \mathbf{s}_i(k)$.

(ii) Possibly modifying the sin vectors of other players: $\mathbf{s}\_\ell(k+1) \neq \mathbf{s}\_\ell(k) \text{ for } \ell \neq i$

(iii) Possibly altering the player set: $P_{k+1} \neq P_k$, where players may get added or removed from the game if some action is complete.

For each player $p_i$ at state $T_k$, we define a:

(i) Motivation total: $\Sigma_i(k) = \sum_{j=1}^{7} s_{i,j}(k)$

(ii) Influence: $I(p_i) \in \mathbb{R}^+$, ordered such that $I(p_1) \geq I(p_2) \geq \cdots \geq I(p_n)$

Patterns can emerge from the relationship between $\Sigma_i(k)$ and $I(p_i)$:

(i) Equilibrium: $
|\Sigma_i(k) - \Sigma_\ell(k)| < \varepsilon
$ for all players (high symmetry in motivation)

(ii) Instability: $\max_i(\Sigma_i) - \min_\ell(\Sigma_\ell) > \theta$ for some threshold $\theta$

(iii) Slothful Referee: $I(p_1) \gg I(p_2)$ and $\Sigma_1(k) \ll \Sigma_2(k)$

Regarding the rate of change, the difference in sin values between consecutive states indicates system variations:

$$\Delta s_{i,j} = s_{i,j}(k+1) - s_{i,j}(k)$$

Large $
|\Delta s_{i,j}|$ values indicate inflection points. For instance, rapidly rising $\Sigma_i(k)
$ can suggest escalating engagement, rapidly falling $\Sigma_i(k)$ can suggest game conclusion or player exhaustion. Sharp increase in $s_{i,\text{Wr}}$ may precede aggressive action.

Action $\alpha$ by player $p_i$ may alter sin values of player $p_j$. For example,

(i) $s_{j,\text{En}}(k+1)$ may increase if $\alpha$ benefits $p_i$

(ii) $s_{j,\text{Wr}}(k+1)$ may increase if $\alpha$ harms $p_j$

(iii) $s_{i,\text{Sl}}(k+1)$ may decrease if $\alpha$ requires significant effort

### Payoff Attribution

The sin value tables from the previous sections assume we do not know precisely what resources are available to the players to be gained or lost. If we do know what is at stake, the subjectivity of the Sindex can be replaced or accompanied by a more game theory-adjacent model like the following. 

For a given game state $T_k$, let $E = \{e_1, e_2, \ldots, e_m\}$ be the set of possible outcomes. The associated payoff matrix $\Pi_k$ is an $n \times m$ real matrix where the entry $\pi_{i,q}(k)$ quantifies the gain or loss to player $p_i$ upon the realization of outcome $e_q$. Payoffs can be denominated in a common unit like fiat currency.

|          | $p_1$        | $p_2$        | ...   | $p_n$        | $\Sigma_{\text{Event}}$     |
|----------|--------------|--------------|-------|--------------|------------------------------|
| $e_1$    | $\pi_{1,1}$  | $\pi_{2,1}$  | ...   | $\pi_{n,1}$  | $\sum_{i} \pi_{i,1}$        |
| $e_2$    | $\pi_{1,2}$  | $\pi_{2,2}$  | ...   | $\pi_{n,2}$  | $\sum_{i} \pi_{i,2}$        |
| ...      | ...          | ...          | ...   | ...          | ...                          |
| $e_m$    | $\pi_{1,m}$  | $\pi_{2,m}$  | ...   | $\pi_{n,m}$  | $\sum_{i} \pi_{i,m}$        |
| $\Sigma_{\text{Player}}$ | $\sum_q \pi_{1,q}$   | $\sum_q \pi_{2,q}$   | ...   | $\sum_q \pi_{n,q}$   |             |

For example, in USD equivalents:

| | $p_1$ | $p_2$ | $p_3$ | $\Sigma_{\text{Event}}$ |
|----------|------------|------------|-------------|---------|
| $e_1$ | 100K | \-100K | 0 | 0 |
| $e_2$ | 0 | 250K | 20K\* | 270K |
| $e_3$ | 0 | \-200K\*\* | 200K\*\* | 0 |
| $\Sigma_{\text{Player}}$ | 100K | \-50K | 220K | 270K |

\* Boat valued at \$20K

\*\* 100 Ha land at \$2K/Ha = \$200K

This can be made with the rule of progression with events ordered sequentially ($e_1 \to e_2 \to \cdots \to e_m$) where an event cannot happen unless a denoted preceding event occurs. Having an event with the same payoff that two or more players compete for may introduce urgency and thus prioritize it, as one player’s direction forces the other interested players to pursue that event simultaneously.

The sums of events’ and players’ payoffs can be treated as expected values in a game, offering a similar line of thinking to that of the sin model based on motivation totals. 

The aggregate incentive for a player $p_i$ in state $T_k$ is given by an expected value function. In its simplest form, as a sum over potential outcomes:

$$\text{EV}_i(k) = \sum_{q=1}^{m} \pi_{i,q}(k)$$

A more nuanced form weights payoffs by the probability $\rho_{i,q}(k)$ that player $p_i$ will pursue or achieve outcome $e_q$, which can be estimated from their sin vector $\mathbf{s}_i(k)$:

$$\text{EV}_i(k) = \sum_{q=1}^{m} \rho_{i,q}(k) \cdot \pi_{i,q}(k)$$

When $\rho_{i,q}(k)$ is uniform (equal probability across outcomes), $\text{EV}_i(k)$ reduces to the simple sum shown in earlier examples.

We can also introduce influence scoring for this type of modelling. Mapping totals on a plane would show how the incentives change as influence grows. 

Forced alongside the sin model, this would only address Greed if we say that Gluttony is only about consumption and Lust is about general infatuation. While it is possible to try mapping the payoffs more extensively by placing monetary values on traditionally nonmaterial things and so adding other sins, that would almost certainly not be reliable.

Not unlike the subjective sin score model, this largely ignores the rules of games and addresses only the overall player motivations we can name. It is the aim of such accounting to be able to evaluate some characteristics of a game when our knowledge of its rules is limited. Meanwhile, sin value tables assume limited knowledge about available resources. What is denoted as *strategies* in game theory aligns more to *events* in the above example’s case which assumes that the probability of some events occurring cannot be affected by the players. 

#### References

Blakemore, E. (2019, March 29). What was the Arab Spring and how did it spread? *National Geographic*. <https://www.nationalgeographic.com/culture/article/arab-spring-cause>

Duignan, B. (2024, July 3). Financial Crisis of 2007–08. *Encyclopedia Britannica*. <https://www.britannica.com/money/financial-crisis-of-2007-2008>

Lampe, J. R. (2025, November 17). Bosnian War. *Encyclopedia Britannica*. <https://www.britannica.com/event/Bosnian-War>

Stiglitz, J. E. (1996). Some lessons from the East Asian miracle. *The World Bank Research Observer, 11*(2), 151–177.

Wasson, D. L. (2018, April 12). *Fall of the Western Roman Empire*. *World History Encyclopedia*. <https://www.worldhistory.org/article/835/fall-of-the-western-roman-empire/>
