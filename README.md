# COMP8880 - Computational Methods for Network Science

# Node and degree

Total number of degrees: $L = \frac{1}{2}\displaystyle\sum^{N}_{i}{k_i}$  

# Degree Distribution in Graphs

The **degree distribution** of a graph describes how the degrees (number of connections) of nodes are distributed across the entire network.

## Definition:

For a graph $G = (V, E)$ , the  **degree distribution** $P(k)$ is the probability that a randomly chosen node has exactly k edges (degree k). It is defined as:

$P(k) = \frac{\text{Number of nodes with degree } k}{\text{Total number of nodes}}$

Types of Degree Distributions:

1. **Uniform Distribution:** Each degree value appears with roughly equal probability.
2. **Poisson Distribution (Random Graphs):** In an **Erdős-Rényi Random graph,** the degree distribution follows a **Poisson distribution**, meaning most nodes have a similar number of edges.
3. **Power-Law Distribution (Scale-Free Network):**  In **real-world networks** (e.g., social network, the internet, biological networks), a few nodes have a very high degree (hubs), while most nodes have a low degree. This follows a power-law: $P(k)∝k^{−γ}$, where γ is typically between 2 and 3.
4. **Exponential Distribution:** Seen in **small-world networks,** where most nodes have a similar degree, but a few have a slightly higher degree.

# Diameter of a Graph

The **diameter** of a graph is the longest shortest path between any two nodes in the graph. In other words, it is the greatest distance between any pair of nodes when considering shortest path between them.

## Mathematical Definition

For a graph $G = (V, E)$:

1. The shortest path (also called **geodesic distance**) between two nodes $u$ and $v$, denoted as $d(u, v)$, is the minimum number of edges needed to travel from $u$ to $v$.
2. The **diameter** of the graph is defined as: $D = \max\limits_{u, v \in V} d(u,v)$ . This means that $D$ is the maximum shortest path length among all pairs of nodes.

## Interpretation

- The **diameter** gives a measure of the graph’s **”spread”** — how far apart the two most distant nodes are.
- A **small diameter** indicates that most nodes are close together (e.g., in small-world network).
- A **larger diameter** suggest that the network is more sparsely connected or stretched out.

# Betweenness

## Betweenness Centrality (for Nodes)

Betweenness centrality quantifies how often a node acts as a bridge along the shortest paths between other others. It is calculated as:

$C_{B}(i) = \displaystyle\sum^{}_{j<k}{g_{jk}(i)/g_{jk}}$, 

where:

- $C_{B}(v)$ is the betweenness centrality of node $i$
- $g_{jk} =$ the number of shortest paths connecting $jk,$
- $g_{jk}(i) =$ the number that actor $i$ is on. (the number of those shortest paths that pass through node $i$)
- The sum runs over all pairs of nodes $(s,t)$ in the graph.

Usually normalized by:

$C’_{B}(i) = C_{B}(i)/[(n-1)(n-2)/2]$

## Edge Betweenness Centrality

Edge betweenness centrality measures how many shortest paths pass through a given edge:

$C_{B}(e)=\displaystyle\sum_{s \neq t}\frac{\sigma_{st}(e)}{\sigma_{st}}$

where $\sigma_{st}(e)$ is the number of shortest paths between $s$ and $t$ that include edge $e$.

Edges with high betweenness are important **bottlenecks**  in a network, meaning they are critical connections that facilitate efficient flow.

# Non-Random Graph

**Definition:**  A non-random graph is a graph is structed or designed in a specific way rather being generated randomly. It follows certain predefined rules, constraints, or patterns instead of being formed by a **stochastic** (random) process.

## Key Characteristics of Non-Random Graphs

1. **Deterministic Structure** - The connections (edges) between nodes follow a specific rule or pattern.
2. **Predictable Topology** - The structure is not subject to random variations but is explicitly constructed.
3. **Non-Stochastic Edge Formation** - The edges are placed according to a fixed algorithm, rule or real-world system, rather than with probability.

# Random Graph $G(n, p）$

**Stochastic** means **random or involving probability**. When something is **stochastic**, it means that it has some level of randomness or unpredictability, often governed by probability distributions.

In the context of graphs, a stochastic (random) graph is a graph where edges are formed based on probabilities. This means that the structure of the graph is not fixed but depends on chance.

1. Start with n isolated nodes
2. Connection a pair of nodes with probability p
    
    i.e. generate a random number uniformly between 0 and 1. If the random number is less than p, create a link; otherwise leave the node pair unconnected.
    
3. Repeat step 2 for each of the $\frac{n(n-1)}{2}$ node pairs

## Properties of $G(n, p)$

1. **Expected Number of Edges:** Since there are $\binom{n}{2} = \frac{n(n-1)}{2}$ possible edges, the expected number of edges in $G(n,p)$ is
    
    $$
     ⁍
    $$
    
2. **Number of edges** that a node have on average:
    
    $$
    <k> = p(n-1)
    $$
    
3. **Degree Distribution:** The degree d(v) of any vertex follows a **binomial distribution:**
    
    $$
    p_{k} = \binom{n-1}{k}p^{k}(1-p)^{n-1-k} = \frac{(n-1)!}{k!(n-1-k)!}p^{k}(1-p)^{n-1-k}
    $$
    
    $p_{k}$ : (exactly $k$ edges exist),
    
    ($k$ out of $n-1$ degrees exist) and ($n-1-k$ edges does not exist)
    
    For large $n$ and small $p$, it is often approximated by a **Poisson distribution. $n \to \infin$**
    
    $$
    \begin{align*}
    p_k &= \frac{(n-1)!}{k!(n-1-k)!} p^k (1-p)^{n-1-k} \\
        &= \frac{(n-1)^k}{k!} \left( \frac{\langle k \rangle}{n-1} \right)^k e^{-\langle k \rangle} \\
        &= \frac{\langle k \rangle^k}{k!} e^{-\langle k \rangle}
    \end{align*}
    
    $$
    

| **Features** | **Non-Random Graphs** | **Random Graphs** |
| --- | --- | --- |
| **Structure** | Highly structed, follows rules | Formed by probability distribution |
| **Predictability** | High (edges follow a pattern) | Low (edges are randomly placed) |
| **Real-World Models** | Often seen is social networks, internet topology, biological systems | Used for theoretical analysis of connectivity, emergence of properties |

# Lattice

In graph theory, a **lattice** is a partially ordered set (poset) in which any two elements have a unique **least upper bound** (supremum) and a unique **greatest lower bound** (infimum). This structure is closely related to **order theory** and **lattice theory** in mathematics.

## Definition

A **lattice** $(L, \leq)$ is a poset such that for every pair of elements $a, b \in L$, there exist:

1. **Join (Supremum, $\vee$):** The least element that greater than  or equal to both $a \text{ and } b$
2. **Meet (Infimum, $\wedge$):** The greatest element that is less than or equal to both $a \text{ and } b$. 

## Graph Representation

- A **Hasse diagram** is commonly used to represent lattices. It is a directed acyclic graph (DAG) where edge indicate order relationships.
- The **Boolean lattice** is a common example, where the elements are subsets of a set ordered by inclusion.

## Types of Lattices

1. **Complete Lattice:** A lattice in which every subset has a supremum and an infimum.
2. **Distributive Lattice:** A lattice where meet and join operations distribute over each other.
3. **Modular Lattice:** A weaker form of distributive lattices.
4. **Bounded Lattice:** A lattice with a greatest element ($\top$) and a least element ($\bot$).

# Kleinberg’s Model in Graph Theory

Kleinberg’s model is **small-world network model** introduced by **Jon Kleinberg** in 2000. It extends the **Watts-Strogatz small-world model** by adding **long-range links** in controlled probabilistic manner, allowing efficient decentralized navigation (or routing).

## Definition of the Kleinberg Model

Kleinberg’s model starts with an $n \times n$ **grid** (a **lattice**), where each node is connected to its immediate neighbors. Then additional **long-range connections** are introduced based on a probability distribution.

### Graph Construction

1. **Base Grid:** The network consists of an $n \times n$ **grid** where each node $(x, y)$ is connected to its **immediate neighbors** (north, south, east, and west).
2. **Long-Range Links:** Each node is assigned **one more random long-range links** based on a probability distribution.
3. **Probability Distribution:** The probability that a node $(x, y)$ connects to another node $(u, v)$ at distance $d$ is: 

$$
P(d) \propto d^{-r}
$$

        where:

- $d = |x-u| + |y-v|$ is the **Manhattan distance** between nodes.
- $r$ is a **clustering exponent** that controls how links are distributed.

## Importance of the Clustering Exponent $r$

- $r = 0:$ Links are assigned **uniformly at random** (no preference for closer or farther nodes).
- $r > 0$ : Closer nodes are more likely to be connected (more clustered network).
- $r = 2$ : **Optimal for decentralized routing—**greedy routing can efficiently find short paths.
- $r \gg 2$ : Links are highly localized, making long-range navigation difficult.

# PDF, CDF & CCDF

- $f(t)$ is the **probability density function (PDF)**
- $F(t)$ is the **cumulative distribution function (CDF):**

$$
F(t) = \Pr(X \le t)
$$

- $\bar{F}(t)$ is the **complementary CDF (CDF):**
    
    $$
    f(t) = \frac{d}{dt}F(t)
    $$
    

## Additional information:

- The key relationship between $f(t)$ and $F(t)$ is:
    
    $$
    \bar{F}(t) = 1- F(t) = \Pr(X > t)
    $$
    
    That is: 
    
    - $F(t)$ is the **integral** of $f(t)$, and
    - $f(t)$ is the derivate of $F(t)$.
    
    **Formally:** 
    
    $$
    F(t) = \int^{t}_{0} f(u) du \quad \text{and thus }\quad \frac{d}{dt}F(t)=f(t)
    $$
    
- The key relationship between $f(t)$ and $\bar{F}(t)$
    
    We know: 
    
    $$
    \bar{F}(t) = 1 - \bar{F}
    $$
    
    Differentiate both sides with respect to t: 
    
    $$
    \frac{d}{dt}\bar{F}(t)=\frac{d}{dt}(1-F(t))=0-\frac{d}{dt}F(t)=-f(t)
    $$
    
    Thus: 
    
    $$
    \frac{d}{dt}\bar{F}(t) = -f(t)
    $$
    

## Why logically?

- $F(t)$ = cumulative probability **up to $t$**
- $\bar{F}(t)$ = cumulative probability **after** t
- As you increase $t$, the probability of being **after $t$** goes **down**
- So the derivate of $\bar{F}(t)$ is **negative —** and it’s exactly $-f(t)$

## Summary:

| Expression | Meaning |
| --- | --- |
| $F(t) = \int^t_0 f(u) du$ | CDF is integral of PDF |
| $f(t) = \frac{d}{dt}F(t)$ | PDF is derivative of CDF |
| $\bar{F}(t) = 1-F(t)$ | CCDF is 1 minus CDF |
| $\frac{d}{dt}\bar{F}(t) = -f(t)$ | Derivative of CCDF is minus PDF |

# Supremum and infimum

## Supremum

- $\sup$ stands for **supremum**: the **least upper bound** of a set.
    - Think: the smallest number that is **greater than or equal to all** elements in the set.
- For example:
    
    If $A = \{1,2,3\},$  then $\sup A = 3$.
    
    If $B = \{1-\frac{1}{n} : n\in \mathbb{N}\}$, then $\sup B = 1$ (even though 1 is not in the set).
    

## Infimum

- $\inf$ stands for **infimum**: the **greatest lower bound.**
    - Think: the largest number that is **less than or equal to all** elements.
- For example:
    
    For $C = \{2,3,4\}, \inf C = 2$
    
    For $D = \{\frac{1}{n}:n \in \mathbb{N}\}, \inf D = 0.$
    

# Limit Superior of a sequence

$$
\limsup_{n \to \infin} x_{n} = \lim_{n \to \infin}(\sup_{m \ge n} x_{m})
$$

- $x_{n}:$ Single number at position $n$.
- $(x_{n}):$ Entire sequence.
- $\sup x_{n}:$  usually shorthand for $\sup {x_{n}: n \in \mathbb{N}}$, i.e. the supremum (least upper bound) of the values in the sequences.
- At each step $n$, take all $x_{m}$ from $m \ge n$, and take their **supremum**.
- That gives you a sequence: $s_{n} = \sup_{m \ge n} x_{m}.$
- This sequence is **non-increasing** (each time you’re taking sup over a smaller set).
- Then you take the **limit** of this new sequence — that’s the $\limsup$.

### Why is this useful?

The $\limsup$ tells you the **largest "long-run" value** the sequence approaches, even if it doesn't converge
Similarly: 

$$
\liminf x_{n} = \lim_{x \to \infin} (\inf_{m \ge n} x_{m})
$$

This tells you the **smallest value** the sequence gets arbitrarily close to, eventually.

| Concept | Math Expression | Meaning |
| --- | --- | --- |
| Supremum | $\sup A$ | Least upper bound of set $A$ |
| Infimum | $\inf A$ | Greatest lower bound of set $A$ |
| Limit superior | $\limsup x_{n} = \inf_{n} \sup_{m \ge n}x_{m}$  | Largest long-term cluster point of sequence |
| Limit inferior | $\liminf x_{n} = \sup_{n} \inf_{m \ge n}x_{m}$  | Smallest long-term cluster point |
| Usual limit | $\lim x_{n}$ exists if $\limsup = \liminf$ | True convergence to a single value |

### Example

Let:

$$
x_{n} = (-1)^{n} + \frac{1}{n} \implies (x_{n}) = (2, -0.5, 1.333, -0.75, 1.2, -0.833,...)
$$

Then:

- The **supremum $\sup x_{n} \approx 2$**
- The **infimum $\inf x_{n} \approx -1$**
- The $\limsup$ is the limit of the upper “peaks” $\to$ $\limsup x_{n} = 1$
- The $\liminf$ is the limit of the lower “valleys” $\to$ $\liminf x_{n} = -1$

# Power Law

In network science, a power law describes a type of relationship between two quantities where one varies as a power of the other. It’s often written like this:

$$
P(k) \sim k^{-\gamma}
$$

Here’s what it means in plain terms:

- $P(k):$   the probability that a node in a network has $k$ connections (degree).
- $\gamma :$  a constant exponent, usually between 2 and 3 for many real-world networks.

## Why it matters

In many **real-world networks** (like social networks, internet topology, or biological systems), most nodes have only a few connections, but a few nodes (called **hubs**) have *a huge number* of connections. That’s very different from, say, a random network where degree distribution is more uniform (like Poisson).

This "fat tail" distribution (where rare events are more common than you'd expect) is one of the defining features of **scale-free networks**.

Examples:

- In a Twitter network, most users have a few followers.
- But a few users (celebrities or news accounts) have millions — they follow a power-law degree distribution.

# Fat-tail distribution

A **fat-tail distribution** is a probability distribution where extreme events (very large or very small values) have **higher probability** than they would in a "normal" distribution (like the bell curve).

**More technically:**

Compared to a normal distribution, the tails (the ends of the curve) **decay more slowly**. That means values far from the mean aren't rare — they happen more often than you'd expect under normal assumptions.

## Why it matters in Networks

In a power-law degree distribution like:

$$
P(k)\sim k^{-\gamma}
$$

- There are many nodes with small degrees.
- There are a few **very highly connected** nodes (hubs).
- This long tail (with big degrees) is **fat** — it doesn't vanish quickly.

This is what makes networks like the Internet or airline routes *robust-yet-vulnerable* — they’re stable to random failures (most nodes are low-degree), but fragile to targeted attacks (hubs are critical).

| Feature | Normal (Thin Tail) | Power-Law (Fat Tail) |
| --- | --- | --- |
| Extreme events | Rare | Common |
| Mean and variance | Finite | May be infinite |
| Looks like | Bell curve | L-shape (log-log plot) |

If you plot a power-law distribution on a **log-log graph**, the tail becomes a straight line — a classic way to spot fat-tailed behavior.

- **All power-law distributions have fat tails.**
- So: **Power-law ⊂ fat-tail**.
- But **not all fat-tail distributions are power laws**.

# Heavy Tail (almost same as Fat Tail)

A distribution with a “tail” that is “heavier” than an Exponential 

## What is an Exponential Tail?

$$
P(x)\sim e^{-\lambda x}
$$

It drops off **very fast** as $x\to \infty$. That’s what we call **light-tailed** — large values become exponentially unlikely.

## What is a Heavy-Tailed Distribution?

A distribution is **heavy-tailed** if its tail **decays more slowly than an exponential**.

In formal terms:

A distribution $F(x)$ is **heavy-tailed** if

$$
\lim_{x \to \infin} e^{\lambda x} \cdot \bar{F}(x) = \infin, \quad \text{for all }\lambda > 0
$$

where $\bar{F}(x) = 1-F(x)$ is the tail probability.

In simpler words:

- Even when multiplied by an exponential $e^{\lambda x}$, the tail **doesn’t die off**.
- That means the tail "holds more mass" — it’s **heavier**.

| Distribution | Tail behavior | Heavy-tailed? |
| --- | --- | --- |
| Normal | $e^{-x^{2}}$ | NO |
| Exponential | $e^{-\lambda x}$ | NO |
| Log-normal | slower than exp | YES |
| Power-law | $x^{-\lambda}$ | YES |

## In Network Science:

- Heavy tails mean that **some events (e.g., node degrees, file sizes, traffic spikes)** are way more likely than under "light-tailed" assumptions.
- That’s why **power laws**, **log-normal**, and similar distributions are so important — they **model rare-but-huge** events realistically.

# Distribution Comparison

| Term | Type | Definition | Relationship |
| --- | --- | --- | --- |
| **Heavy-tailed** | Broad class | Tail decays slower than exponential | Includes power-law, log-normal… |
| Power-law | Class | $P(x)\sim x^{-\alpha}$ | Specific form of heavy tail |
| Pareto | Specific | A special case of power-law | Subclass of power-law |

## Power-Law Distribution

A **power-law distribution has the form:**

$$
P(x)\propto x^{-\alpha}\quad\text{ for } x\ge x_{\min}
$$

- $\alpha > 1$ is the exponent.
- Long tail: large values occur more often than in exponential or normal distributions
- Used to model **scale-free** systems (e.g., degrees in social networks, file sizes, wealth)

**Subset of heavy-tailed distributions**

Often analyzed via **log-log plots** (looks like a straight line)

## Pareto Distribution

A **Pareto distribution** is a **specific type of power-law** with:

$$
F(x) = 1 - (\frac{x_{\min}}{x})^{a} \quad \text{ for } x \ge x_{\min}
$$

Its **PDF:** 

$$
p(x) = \frac{\alpha x^{\alpha}_{\min}}{x^{\alpha+1}}
$$

- Commonly used in **economics** (e.g., **income distribution**)
- Also known as **Pareto Type I.**

✅ It **is a power-law**

✅ It **is heavy-tailed**

❗ It’s **not the only power-law** (other power-laws may have different normalization or support)

## Heavy-Tailed Distribution

A **heavy-tailed distribution** is one where:

$$
P(X > x) \gg e^{-\lambda x} \quad \text{ as }x \to \infin \quad \text{for any }\lambda > 0
$$

This means the tail **decays slower than exponential,** allowing large events with **non-negligible probability.**
The probability that $X$ is larger than $x$ **decays more slowly** than any exponential function.

Where:

- $X:$  A **random variable** — represents outcomes drawn from the distribution.
- $x:$ A **value** on  the number line — a specific number (threshold)
- $P(X \gg x):$ The **Probability that $X$** takes a value **** **greater than** **$x$.**
- $\lambda:$ A **positive constant —** typically used in exponential decay
- $e:$ Euler’s number (~2.718) — base of natural logarithms
- $e^{-\lambda x}:$  An **exponentially decaying function**
- $\gg:$  "Much greater than" — informal notation for **asymptotically slower decay**

✅ Includes:

- Power-law (like Pareto)
- Log-normal
- Weibull (with shape parameter <1< 1<1)
- Lévy

🚫 Does **not** include:

- Normal
- Exponential
- Poisson

## When to Use Which?

- **Use Pareto** if you're modeling classic "80/20" effects (wealth, file sizes).
- **Use power-law** if you're studying networks, cascading failures, or "scale-free" behavior.
- **Use heavy-tail** as a general label when large deviations are likely, but you’re not assuming a specific shape.

# Scale-free

A **scale-free network** is a network whose **degree distribution** follows a **power-law**:

$$
P(k)\sim k^{-\gamma}, \quad \text{ typically } 2 < \gamma < 3
$$

This means:

- Most nodes have **few connections**
- A few nodes (called **hubs**) have **very many connections**
- This distribution **doesn't have a characteristic scale**, which is where the name comes from

## Summary:

A **scale-free** network is one where the degree distribution follows a power-law, meaning there’s no "typical" degree — it’s dominated by a few massive hubs and many low-degree nodes.

# Scale invariance

**Theorem:** A distribution is scale invariant if and only if it is Pareto.

$F$ is scale invariant if there exists $x_{0}$ and a $g$ such that $\bar{F} (\lambda x) = g(\lambda)\bar{F}(x)$ for all $\lambda, x$ such that $\lambda x \ge x_{0}$.

Where:

- $\bar{F}(\lambda x):$  Change of var $x \to \lambda x$
- $g(\lambda):$  Scaled by a constant

## Example

$$
\bar{F}(\lambda x) = (\frac{x_{\min}}{\lambda x})^{\alpha} = \bar{F}(x)(\frac{1}{\lambda})^{\alpha} \quad \text{ where }(\frac{1}{\lambda})^{\alpha}=g(\lambda)
$$

Recall: 

$$
\bar{F}(x)=(\frac{x_{\min}}{x})^{\alpha}
$$

Now plug in $\lambda x:$ 

$$
\bar{F}(\lambda x) = (\frac{x_{\min}}{\lambda x})^{\alpha} = (\frac{1}{\lambda})^{\alpha}(\frac{x_{\min}}{x})^{\alpha} = \bar{F}(x) \cdot (\frac{1}{\lambda})^{\alpha}
$$

# Weibull distribution

**Weibull distribution**, which is a very flexible and widely-used distribution in **reliability**, **survival analysis**, and **network modeling**.

## Probability Density Function (PDF):

$$
f(x; \alpha, \beta) = 
\begin{cases}
\alpha \beta(\beta x)^{\alpha-1}e^{-(\beta x)^{\alpha}} & \text{if } x \ge 0, \\
0 & \text{if } x < 0.
\end{cases}
$$

## Complementary CDF (CCDF):

$$
\bar{F}(x;\alpha, \beta)=
\begin{cases}
e^{-(\beta x)^{\alpha}} &\text{if } x \ge 0,\\
1 &\text{if }x<0.
\end{cases}
$$

## Parameters and Their Meaning

1. $\alpha:$  **Shape parameter**
    - Controls **how the tail behaves** and the "steepness" of the hazard rate.
    - It governs the overall **shape** of the distribution.
    
    So: 
    
    - **Heavy-tailed** when $\alpha < 1$
    
    | $\alpha$ | Interpretation | Behavior |
    | --- | --- | --- |
    | $\alpha < 1$ | **Heavy-tailed** / Fractal decay | Failure rate decreases over time |
    | $\alpha = 1$ | Exponential distribution | Constant failure rate (memoryless) |
    | $\alpha > 1$ | Light-tailed | Failure rate increases over time |
2. $\beta:$ **Inverse scale parameter**
    - Sometimes called a "rate-like" parameter.
    - Controls the **horizontal scaling** of the distribution.
    - Bigger $\beta$ → faster decay → narrower distribution.
    - Smaller $\beta$ → slower decay → wider tail.
    
    More formally:
    
    - $\frac{1}{\beta}$ is the **scale**, so large $\beta \to$  small scale.

## Interpretation in Applications

| Field | What it models | Shape role |
| --- | --- | --- |
| Reliability | Time to failure of components | $\alpha < 1$: infant mortality, $\alpha > 1$: aging |
| Survival analysis | Lifetimes of patients or systems |  |
| Network science | Time between events, durations |  |

## Summary

- The **Weibull distribution** is **very flexible** — it can behave like:
    - **Exponential** (when $\alpha = 1$)
    - **Heavy-tailed** (when $\alpha < 1$)
    - **Thin-tailed** (when $\alpha > 1$)
- It’s one of the **few distributions that can "switch tail types"** based on parameter values.

# Catastrophe & Conspiracy

## Catastrophe (Heavy-tailed)

A distribution $F$ satisfies the **catastrophe principle** if, for $n \geq 2$ independent random variables $X_1, X_2, \dots, X_n$ drawn from $F$:

$$
\Pr\left( \max(X_1, \dotsc, X_n) > t \right) \sim \Pr\left( X_1 + X_2 + \dotsc + X_n > t \right) \quad \text{as} \quad t \to \infty
$$

Meaning:

- **The probability that the maximum exceeds $t$** behaves **asymptotically the same** as
- **The probability that the sum exceeds $t$**

✅ **"Max ≈ Sum" for very large thresholds $t$**.

## Conspiracy Principle (Light-tailed)

A distribution F over the non-negative reals is said to satisfy the conspiracy principle if, for $n\ge 2$ independent random variable $X_1,X_2...,X_n$ with distribution F.

$$
\Pr\left( \max(X_1, \dotsc, X_n) > t \right) = o\left( \Pr\left( X_1 + X_2 + \dotsc + X_n > t \right) \right) \quad \text{as} \quad t \to \infty
$$

Meaning:

- The probability that **the max exceeds $t$** becomes **negligible** compared to
- The probability that **the sum exceeds $t$**.

Formally, $o(\cdot)$ means "smaller order":

$$
\frac{\Pr( \max > t)}{\Pr( \text{sum} > t )} \to 0 \quad \text{as} \quad t \to \infty
$$

✅ **"Sum ≫ Max"** for very large $t$.

## 🧠 What does this mean intuitively?

| Principle | Rough meaning |
| --- | --- |
| **Catastrophe principle** | Big sum happens because of **one big variable** (one random $X_i$ becomes huge) |
| **Conspiracy principle** | Big sum happens because **many small variables "conspire" together** (each is moderately large) |

## 🎯 When do they happen?

- **Catastrophe principle** usually happens for **heavy-tailed distributions**:
    - Example: Pareto, Cauchy
    - Very large values happen often, and a single huge $X_i$ dominates the sum.
- **Conspiracy principle** usually happens for **light-tailed distributions**:
    - Example: Exponential, Gaussian
    - Each $X_i$ is "small" but many moderately large $X_i$ together cause a large sum.

## 📐 Visual example:

Suppose you have 100 random variables:

- If they follow a **Pareto** (heavy-tail), then when the total sum is huge, probably **one of them is gigantic** and the rest are normal.
- If they follow an **Exponential** (light-tail), then to make a huge sum, **many of them must be slightly bigger than normal together** — **they "conspire."**

## $\Pr(\max(X_1,...,X_n)>t)$ & $\Pr(X_1+...+X_n>t)$

- $\Pr( \max(X_1, \dotsc, X_n) > t )$ is $\bar{F}( \max(X_1, \dotsc, X_n) ).$
- $\Pr( X_1 + \dotsc + X_n > t )$ is $\bar{F}( X_1 + \dotsc + X_n ).$

### 🔹 1. What is $F(x)$?

F(x) is the **CDF** (Cumulative Distribution Function):

$$
F(x) = \Pr(X \leq x)
$$

It measures:

- The probability that the random variable $X$ is **less than or equal to** $x$.

### 🔹 2. What is Fˉ(x)\bar{F}(x)Fˉ(x)?

$\bar{F}(x)$ is the **CCDF** (Complementary Cumulative Distribution Function), also called the **survival function**:

$$
\bar{F}(x)=1-F(x)=\Pr(X > x)
$$

It measures:

- The probability that $X$ is **greater than** $x$.

✅ **Notice:** Whenever you are asking about "**$>t$**", you're talking about the **survival function** $\bar{F}$.

### 🔹 3. Now in your assignment:

You are studying:

- $\Pr(\max(X_1, \dotsc, X_n) > t)$
- $\Pr(X_1 + X_2 + \dotsc + X_n > t)$

Both involve "**$>t$**"!

✅ Therefore, you are naturally working with **$\bar{F}$** — the **survival function**, not the CDF $F$.

### 🔹 4. Why **not $f$** (PDF)?

$f(x)$ is the **probability density function** for continuous random variables.

- $f(x)$ is about "**how dense**" the probability is **around a small neighborhood near $x$**.
- $f(x)$ alone **does not** directly tell you the probability $X>t$.

✅ To find probabilities like $X>t$, you must **integrate** the PDF:

$$
\bar{F}(t) = \int_t^\infty f(x) \, dx
$$

Thus, **$\bar{F}(t)$ is the correct quantity** to represent "**probability greater than $t$**." 

| Symbol | Meaning |
| --- | --- |
| $F(x)$ | Probability that $X \le x$ |
| $\bar{F}(x) = 1- F(x)$ | Probability that $X > x$ |
| $f(x)$ | Probability density near $x$ (not directly probabiility $> x$) |

## ✅ Quick Summary

| Concept | Catastrophe Principle | Conspiracy Principle |
| --- | --- | --- |
| Max vs Sum | Max and Sum are almost equally likely | Max is much smaller than Sum |
| Distribution type | Heavy-tailed (e.g., Pareto) | Light-tailed (e.g., Gaussian, Exponential) |
| Cause of large sum | One giant value | Many medium values working together |

# Hazard Rate

The **hazard rate**, also known as the **failure rate**.

$$
q(t) = \frac{f(t)}{\bar{F}(t)} = \frac{\text{PDF at time t}}{\text{Probability of surviving past time }t}
$$

Where: 

- $f(t)$  is the **probability density function** — how likely failure is at exactly time $t$
- $\bar{F} = P(T > t)$  is the **probability density function** — how likely failure is at exactly time $t$

**Hazard rate $q(t)$** is the **instantaneous probability of failure at time $t$**, *given that the component has survived until time $t.$*

## Example Scenarios

| Distribution | $\alpha$ | Hazard Rate Behavior | Interpretation |
| --- | --- | --- | --- |
| Exponential | 1 | Constant: $q(t) = \lambda$ | Memoryless (always same risk) |
| Weibull($\alpha < 1$) | $< 1$ | Decreasing hazard | Early-life failures more likely |
| Weibull ($\alpha > 1$) | $> 1$ | Increasing hazard | Aging components fail more often |

## Summary

- **Hazard rate** is like the *failure speedometer* at time $t$
- It combines short-term risk $(f(t)$ with conditional survival ($\bar{F}(t)$)
- Different distributions (like Weibull) model different failure behaviors via the hazard rate

# Moments

A **moment** of a random variable is a kind of **summary statistic** that captures aspects of the distribution’s shape.

In general, the **n-th moment** of a random variable $X$ is:

$$
\mathbb{E}[X^{n}] = \text{Expected value of }X^{n}
$$

Where:

- $\mathbb{E}[\cdot]$ means **expectation** (i.e., average value)
- $X^n$ means the value of $X$ raised to the power $n$

| Moment | Symbol | Meaning |
| --- | --- | --- |
| 1st moment | $\mathbb{E}[X]$ | **Mean** (average) |
| 2nd central moment | $\mathbb{E}[(X-\mu)^{2}]$ | **Variance** (spread) |
| 3rd moment | $\mathbb{E}[(X-\mu)^{3}]$ | Skewness (asymmetry) |
| 4th moment | $\mathbb{E}[(X-\mu)^{4}]$ | Kurtosis (tail weight) |

## Moments of the Pareto distribution

### Mean (1st moment):

$$
\mathbb{E}[X] = 
\begin{cases}
\infin, &\alpha \le 1;\\
\frac{\alpha x_{m}}{\alpha -1}, &\alpha > 1.
\end{cases}
$$

### Variance (2nd moment):

$$
Var[X]=
\begin{cases}
\infin, &\alpha \in (1,2]\\
(\frac{x_{m}}{\alpha -1})^{2}\frac{\alpha}{\alpha - 2}, &\alpha > 2
\end{cases}
$$

This tells you: 

- If $\alpha \le 1$: even the **mean doesn’t exist**
- If $1 < \alpha \le 2$: mean exists, **but variance is infinite**
- If $\alpha > 2$: both mean and variance exist

### General moment:

$$
\mathbb{E}[X^{n}] = 
\begin{cases}
(\frac{\alpha x_{m}^{n}}{\alpha - n}), & n < \alpha\\
\infin, & n \leq a
\end{cases}
$$

This shows that **higher moments only exist if $\alpha$ is large enough**.  

## Summary

- **Moments describe shape** (mean, spread, skewness, etc.)
- In heavy-tailed distributions (like Pareto), **some moments may be infinite**
- That signals **extreme variability** — long tails with rare but massive values

# Residual Life

**Residual life** (or **remaining life**) is the **amount of time it is still expected to survive**, starting from now.
So the **residual life distribution** tells you:

Given that a component has lasted up to time $x$, what is the probability it fails within the next $t$ units of time?

## Mathematical definition

Let $X$ be a nonnegative random variable representing the **lifetime** of a component.

Then the **residual life CDF** is:

$$
R_{x}(t) = P(\text{fails before }x + t | \text{survived until }x) = 1-\frac{\bar{F}(x+t)}{\bar{F}(x)} \quad \text{for }t\ge0, \bar{F}(x)>0
$$

Where:

- $\bar{F} = P(X > x) =$ survival function (the CCDF)
- $R_{x}(t) =$  probability it fails **within** the next $t$ time units, **given it has lasted until $x$**

## Summary

| Concept | Interpretation |
| --- | --- |
| $R_x (t)$ | CDF of "remaining life" — prob. of failing within $t$ more units |
| $\bar{R}_{x}(t)$ | Survival function of residual life |
| Used in  | Reliability, survival, queueing, resilience analysis |
| Key property | Only exponential distributions have **memoryless** residual life |

# Mean Residual Life (MRL)

**Mean Residual Life (MRL)** — one of the most important quantities in **reliability engineering**, **survival analysis**, and even **network modeling**

## Definition:

The **Mean Residual Life (MRL)** function at time $x$ is:

$$
\text{MRL}(x) = \mathbb{E}[X - x | X > x]
$$

In words:

It's the **expected remaining lifetime** of a component, **given** that it has already survived up to time $x$.

For a nonnegative random variable X with distribution F, the mean residual life(MRL) function equals $m(x) = \mathbb{E}[X-x|X>x] \text{ (for }x\ge 0 \text{ satisfying } \bar{F}(x) > 0$). Equivalently 

$$
m(x) = \int^{\infin}_{0} \bar{R}_{x}(t)dt = \int^{\infin}_{0} \frac{\bar{F}(x+t)}{\bar{F}(\bar{x})}dt
$$

# Strong Law of Large Numbers (SLLN)

You have a sequence of **i.i.d. random variables**: 

$$
X_{1}, X_{2}, X_{3},...
$$

Each one has the **same distribution**, and all are **independent** of each other. They each have a **finite expected value**: 

$$
\mu=\mathbb{E}[X_{i}]
$$

Define the **partial sum**: 

$$
S_{n} = X_{1} + X_{2} + ⋯ + X_{n}
$$

Then look at the **sample average**: 

$$
\frac{S_{n}}{n} = \frac{X_{1}+X_{2}+X_{1}+X_{n}}{n}
$$

## What does the Strong Law say?

The **Strong Law of Large Numbers (SLLN)** says:
 

$$
\frac{S_{n}}{n} \to \mu \quad \text{almost surely (a.s.) as } n \to \infin
$$

Meaning:

With probability 1, the sample average converges to the expected value $\mu$ as you take more and more samples.
✅ It’s a **guarantee** that in the long run, your average measurement stabilizes and equals the theoretical mean — **not just "on average", but almost always**.

## What does “almost surely” mean?

**Almost surely** means:

> The probability that the convergence does not happen is zero.
> 

It doesn't mean that it *always* happens (because randomness can be weird), but that the set of "bad" outcomes has zero probability — so we can practically treat it as a certainty.

## 4. Informal formula:

$$
S_{n} =^{a.s.} \mathbb{E}[X] \cdot n + o(n)
$$

This is shorthand for saying:

> The total sum $S_{n}$ grows linearly like $\mu \cdot n$, with **small fluctuations**.
> 

Where:

- $\mu \cdot n$: the **main trend**
- $o(n)$: a "smaller-order" term (goes to zero relative to $n$), i.e., error that becomes negligible as $n \to \infty$.

## Summary

| Term / Idea | Meaning |
| --- | --- |
| $X_{i}$ | i.i.d. random variables |
| $S_{n} = X_{1}+...+X_{n}$ | Sum of samples |
| $\frac{S_{n}}{n}$ | Sample average |
| $\frac{S_{n}}{n} \to \mu$  a.s. | Sample average converges to expected value |
| “Almost surely” (a.s.) | Happens with probability 1 |
| $S_{n} = \mu n+ o(n)$ | Sum behaves like linear growth with small error |

## Extra

| Symbol | Meaning | Role |
| --- | --- | --- |
| $\mathbb{E}[X]$ | The **expected value** of random variable $X$ | **Operator** — like a function |
| $\mu$ | The **value** of $\mathbb{E}[X]$ | **Named constant** (a number) |

# Central Limit Theorem (CLT)

Given:

- A sequence of **i.i.d. random variables**: $X_{1},X_{2}, \cdots$
- Each with:
    - Finite **mean** $\mu$ = $\mathbb{E}[X]$
    - Finite **variance** $\sigma^2 = \text{Var}(X)$

Define the **sum**:

$$
S_{n}=X_{1}+X_2+X\cdots+X_n
$$

Then the CLT says: 

$$
\frac{S_n-n\mu}{\sqrt{n}} \xrightarrow{d} \mathscr{N}(0, \sigma^2) \quad \text{ as }n \to \infin
$$

$Z \sim \mathscr{N}(0, \sigma^2):$ normal(Gaussian) distribution with mean 0 and variance $\sigma^2$

## Intuition

| Concept | What it tells you |
| --- | --- |
| **LLN** | $\frac{S_{n}}{n} \to \mu:$ sample mean converges to expected value |
| **CLT** | Tells you how **fast** and in **what shape** the convergence happens |

So:

> The fluctuations of the sample mean $\frac{S_n}{n}$ around the true mean $\mu$ — when rescaled by $\sqrt{n}$ — are approximately **normally distributed**.
> 

### Why $\sqrt{n}$ ?

- The standard deviation of the **sum** $S_n$ grows like $\sqrt{n} \cdot \sigma$
- To normalize the fluctuations, we divide by $\sqrt{n}$
- This lets us **compare different $n$** and talk about convergence in distribution

### What does "converges in distribution" mean?($\xrightarrow{d}$)

It means that:

As $n \to \infty$, the distribution of the normalized sum starts to **look like** a normal (Gaussian) distribution. 

It **does not** say that the values themselves become normal — just that their **distribution shape** becomes normal.

## Summary

| Theorem | Description |
| --- | --- |
| **Law of Large Numbers (LLN)** | $\frac{S_{n}}{n} \to \mu$ — long-run average stabilizes |
| **Central Limit Theorem (CLT)** | $\frac{S_{n-n\mu}}{\sqrt{n}} \to \mathscr{N}(0,\sigma^2)$ — normalized fluctuations are Gaussian |

# Independent and Id**entically distributed random variables (I.I.d.)**

**Independent** means:

> Knowing the outcome of one random variable gives no information about another.
> 

**Identically distributed** means:

> All the random variables are drawn from the same probability distribution (same mean, variance, shape, etc.).
> 

Together, **i.i.d.** random variables are:

> "Random variables that behave the same (identical rules), and don't affect each other (independent)."
> 

## 🔍 More precisely:

| Word | Meaning |
| --- | --- |
| **Independent** | For all $i \neq j$, $P(X_{i}$ and $X_{j}) = P(X_{i})P(X_{j})$ — their probabilities **multiply** |
| **Identically distributed** | $X_{i} \sim X_{j}$— all have the **same PDF** (or CDF), same $\mathbb{E}[X_{i}]$, same $\text{Var}(X_{i})$, etc. |

## 🎯 Example:

Suppose I flip a **fair coin** multiple times:

- Each flip = random variable $X_i$ (e.g., 1 for Heads, 0 for Tails).
- Each flip has:
    - $P(\text{Heads}) = 0.5$
    - $P(\text{Tails}) = 0.5$
- Flips don't influence each other.

✅ Thus, the flips $X_1, X_2, X_3, \dots$ are **i.i.d.**

### 🧠 Why is i.i.d. important?

- **Strong Law of Large Numbers** (LLN): assumes i.i.d. variables.
- **Central Limit Theorem** (CLT): needs i.i.d. to guarantee normal convergence.
- **Simplifies calculations**: you can predict behavior of sums, averages, etc.

**Without independence**, correlations can ruin convergence.
**Without identical distributions**, different random behaviors at different times could confuse patterns.

## ✅ Quick Summary

| Term | Informal meaning | Technical meaning |
| --- | --- | --- |
| Independent | No influence between variables | Joint probability = product of individuals |
| Identically distributed | Same randomness rules | Same PDF/CDF, mean, variance, etc. |

# Deterministic sequences

A **deterministic sequence** is a sequence of numbers that is **not random** — it’s **fully predictable** and **predefined**.

It’s just a regular sequence of real numbers like $a_1, a_2, a_3, \dots$, where you know exactly what each term is, and there's no probability involved.

In 

$$
\frac{X_1+X_2+ \cdots X_n - b_n}{a_n} \xrightarrow{d} Z \quad \text{ where } a_{n} > 0 \text{ and } b_{n} \in \mathbb{R}
$$

- $X_{i}$:  random variables (i.i.d.)
- $a_n, b_n:$   **deterministic sequences**

That means:

- $a_n$ might be something like $\sqrt{n}$
- $b_n$ might be $n\mu$, where $\mu = \mathbb{E}[X]$

They **normalize** or **center** the random sum to make it converge to something meaningful (like a Gaussian or a stable variable).

# What does $\xrightarrow{d}$ mean?

It means **convergence in distribution** (also called **weak convergence**). 

$$
X_n \xrightarrow{d} X
$$

means:

> The distribution of the random variable $X_n$ **approaches** the distribution of $X$ as $n \to \infty$.
> 

So $X_n$ becomes **approximately distributed like $X$** in the limit — but it doesn’t mean the values of $X_n$themselves get close to the values of $X$, just that their **distributions** do.

# Types of convergence

| Symbol | Name | Meaning |
| --- | --- | --- |
| $\xrightarrow{d}$ | Convergence in distribution | Histogram shape matches in the limit |
| $\xrightarrow{P}$ | Convergence in probability | Random variables get close with high probability |
| $\xrightarrow{a.s.}$ | Almost sure convergence | Values converge with probability 1 (strongest) |

# Summary of survival analysis and reliability theory

| Part | Formula |  | Meaning |
| --- | --- | --- | --- |
| **PDF** | $f(x)$ | Density of failure at time $x$ | **Probability Density Function** — describes "how dense" probability is at each $x$. For continuous random variables. Think of it like: *how likely is failure exactly around $x$* (per unit time). |
| **Survival function (CCDF)** | $\bar{F}= P(X > x)$ | Probability surviving past $x$ | Probability that the system **survives past time** $x$. This is called the **complementary CDF** (CCDF). |
| **Hazard rate** | $q(t)=\frac{f(t)}{\bar{F}(t)} \ge 0$ | Instantaneous risk of failure | **Instantaneous failure rate** at time $t$, given survival up to time  $t$. (The chance of dying right now if you have survived until now.) **Note**: hazard function **does not sum to 1** — it's a rate, not a probability! |
| **Residual life survival (CCDF of remaining life)** |  $\bar{R}_{x}(t) = P(X>x+t | X > x) = \frac{\bar{F}(X+t)}{\bar{F}(X)}$ | Surviving $t$ more after $x$ | Probability that a system, **already survived up to time** $x$, will survive at least $t$ more time units. |
| **MRL (Mean Residual Life)** | $m(x)=\mathbb{E}_{x}[X-x|X>x]=\int t f(\text{residual life}) dt \\
= \int^{\infin}_{0} \bar{R}_{x}(t)dt$ | Average time left after $x$ | The **expected extra lifetime** after surviving to xxx. It's the **average of the residual life**. You can compute it either using the residual life density or directly integrating the residual CCDF. |

## Key points to notice:

- $f(x)$ tells you the **chance density** of failing exactly at time $x$.
- $\bar{F}(x)$ tells you the **chance of still surviving** past xxx.
- $q(t)$ tells you the **instantaneous risk** given survival until $t$.
- $\bar{R}_x(t)$ tells you the **chance of surviving $t$ more units**, given you made it to $x$.
- $m(x)$ tells you **on average** how much longer you’ll live after surviving to $x$.

# Spectral theorem

Let $A \in \mathbb{R}^{n \times n}$ be a symmetric matrix, then all eigenvalues of $A$ are real numbers. Furthermore, there is an orthonormal basis of $\mathbb{R}^{n}$ consisting of eigenvectors of $A$.

## Eigenvalues are real

If $\lambda$ is an eigenvalues of $A$, then: 

$$
A\mathbf{v} = \lambda\mathbf{v}
$$

for some nonzero vector  $\mathbf{v}$ (the eigenvector).

✅ For symmetric matrices:

- All eigenvalues $\lambda$ are **real numbers**.
- No complex eigenvalues.
- Even though general square matrices can have complex eigenvalues, symmetric matrices don't.

## There is an orthonormal basis of eigenvectors

- **Basis**: A set of $n$ vectors that can represent any vector in $\mathbb{R}^n$.
- **Orthonormal**:
    - Vectors are all **orthogonal** (perpendicular:$\mathbf{u}^T \mathbf{v} = 0$).
    - Each has **length 1** (**normalized**).

✅ In other words:

- You can find $n$ eigenvectors $\mathbf{v}_1, \mathbf{v}_2, \dots, \mathbf{v}_n$
- They are **orthogonal** and **unit length**.
- Together, they form a complete basis for the whole space $\mathbb{R}^n$.

✅ Extra: 

- $\mathbf{u}$ and $\mathbf{v}$ are **both eigenvectors** of the symmetric matrix $A$.
- $\mathbf{u}^T \mathbf{v}$ means the **dot product** between two vectors $\mathbf{u}$ and $\mathbf{v}$.
- If $\mathbf{u}^T \mathbf{v} = 0$, it means that **$\mathbf{u}$ and $\mathbf{v}$ are perpendicular** (also called **orthogonal**).
- **Perpendicular** = 90 degrees between them.

Orthonormal basis: A set of perpendicular unit eigenvectors spanning the space

## Why is this powerful?

Because **any symmetric matrix** can be **diagonalized** very nicely: 

$$
A= Q \Lambda Q^{T}
$$

Where:

- $Q$ is an orthogonal matrix (its columns are orthonormal eigenvectors of $A$)
- $\Lambda$ is a diagonal matrix (with the real eigenvalues on the diagonal)
- $Q^T = Q^{-1}$ (because $Q$ is orthogonal)

✅ This is called **orthogonal diagonalization**.

✅ It makes computations (like powers of $A$, exponentials of $A$) **much easier**.

# Preferential attachment

With probability $1-\alpha>0$, the newly arriving vertex uses a preferential attachment mechanism and chooses a pre-existing vertex to connect to proportionally to its in-degree; and, with probability $\alpha$, the newly arriving vertex chooses a pre-existing vertex uniformly at random. the probability that the vertex arriving at time t chooses a certain vertex with in-degree $k$ to connect to equals:

$$
\frac{\alpha}{t}+\frac{(1-\alpha)k}{2t}
$$

## 🧠 Step-by-Step Explanation

1. At time $t$, a new vertex **arrives** and wants to **attach** to an existing vertex.
2. The new vertex decides:
    - **With probability $1 - \alpha$**:
        
        Attach **preferentially** — favoring nodes that already have high in-degree $k$.
        
    - **With probability $\alpha$**:
        
        Attach **uniformly at random** — every node is equally likely, no matter degree.
        
3. The probability that a vertex with **in-degree $k$** is chosen is:
    
    $$
    \frac{\alpha}{t}+\frac{(1-\alpha)k}{2t}
    $$
    

## Breaking down the formula:

| Part | Meaning |
| --- | --- |
| $\frac{\alpha}{t}$ | Uniform attachment part: since there are $t$ nodes, probability of picking any one uniformly is $\frac{1}{t}$; multiply by $\alpha$. |
| $\frac{(1-\alpha)k}{2t}$ | Preferential attachment part: chance is proportional to node's **in-degree** $k$ (higher $k$, higher chance). The total "sum of in-degrees" is approximately $2t,$ since each new edge increases total degree by 2. |
| Add them together | Total probability of choosing a vertex with in-degree $k$. |

## Intuitive picture

- If $\alpha$ is **small** (close to 0), attachment is **mostly preferential** → popular nodes get even more popular (strong "rich-get-richer" effect).
- If $\alpha$ is **large** (close to 1), attachment is **more random** → network is more random and less heavy-tailed.

## Quick Summary

| Term | Meaning |
| --- | --- |
| $\alpha$ | Controls balance between randomness and preferential choice |
| $1 - \alpha$ | Strength of preferential attachment |
| Preferential attachment | Higher in-degree → higher chance of getting new edges |
| Uniform random attachment | Equal chance for all nodes |

Under the preferential attachment model,

$F_{t} \xrightarrow{d} F$. as $t \to \infin$, where  

$$
\bar{F}(x) \sim \beta x^{-\frac{2}{1-\alpha}} 
$$

for some positive constant $\beta$.

### 🧠 Step-by-step explanation:

### 1. $F_t$ and $F$

- $F_t$: Degree distribution at time $t$ — tells you, for example, "what fraction of nodes have degree $\leq x$" at time t.
- $F$: Limiting degree distribution as $t \to \infty$ — what the degree distribution "settles into" as the network becomes very large.

The notation: 

$$
F_{t} \xrightarrow{d} F
$$

means:

> The degree distribution of the network converges in distribution to a limiting distribution $F$ as $t \to \infty$.
> 

### 2. $\bar{F}(x)$

- $\bar{F}(x)=1−F(x)$ = **complementary cumulative distribution function (CCDF)**.
- It means:
    
    > "What fraction of nodes have degree greater than $x$?"
    > 

### 3. The asymptotic behavior:

$$
\bar{F}(x) \sim \beta x^{-\frac{2}{1-\alpha}} \quad \text{for large }x
$$

- The notation $\sim$ means **"asymptotically behaves like"** — it doesn’t mean exact equality, but "roughly proportional when $x$ is large."
- The distribution has a **power-law tail** with exponent $\frac{2}{1-\alpha}$.
- $\beta > 0$ is some constant — its exact value depends on model parameters but it's not the main focus here.

### 🔥 Why is this important?

✅ **Preferential attachment networks** develop **power-law** degree distributions:

- A **few nodes** have **very large degree** (very popular),
- **Many nodes** have **small degree**.

✅ The **power-law exponent** is controlled by $\alpha$.

If you have:

- $\alpha \to 0$ (pure preferential attachment, no randomness):
    - Exponent $\frac{2}{1-0} = 2$
    - Classic Barabási–Albert model: degree distribution $\sim x^{-2}$
- $\alpha > 0$ (some randomness):
    - Exponent $>2$
    - The tail is **less heavy**, because some links are made randomly, not preferentially.
    
    | Symbol / Term | Meaning |
    | --- | --- |
    | $F_{t}$ | Degree distribution at time $t$ |
    | $F$ | Limiting degree distribution as $t \to \infty$ |
    | $\bar{F}(x)\sim \beta x^{-\frac{2}{1-\alpha}}$ | Power-law tail behavior of CCDF |
    | $\alpha$ | Controls how random vs. preferential the attachment is |
    | $\beta$ | A positive constant depending on model parameters |

# Spectral radius

**Spectral radius** $\rho(A)$ of a matrix $A$ is the **maximum** of the **moduli** of its eigenvalues. 

## 🔍 Step-by-step explanation:

1. **Eigenvalues** of a matrix
    
    If $A$ is a square matrix, an eigenvalue $\lambda$ satisfies:
    
    $$
    A\mathbf{v} = \lambda \mathbf{v}
    $$
    
    for some nonzero vector $\mathbf{v}$ (the eigenvector).
    
    - **Eigenvalues** can be **real** or **complex** numbers.
    - A matrix can have multiple eigenvalues.
2. **Modulus** of an eigenvalue
If an eigenvalue $\lambda$ is a **real number**, the modulus $|\lambda|$ is just its absolute value.
    
    If $\lambda$ is a **complex number** (e.g., $\lambda = a + bi$), then:  
    
    $$
    |\lambda| = \sqrt{a^2 + b^2}
    $$
    
    (modulus = distance from the origin in the complex plane)
    
3. **Spectral radius $\rho(A)$**
    
    The spectral radius is defined as: 
    
    $$
    \rho(A) = \max{|\lambda| : \lambda \text{ is aneigenvalue of A}}
    $$
    
    ✅ That means:
    
    - Look at **all eigenvalues** of $A$,
    - Take their **moduli** (absolute values),
    - Pick the **largest** one.

## Simple Example

Suppose $A$ has eigenvalues: 

$$
\lambda_1 = 2,\quad \lambda_2 = -3 \quad \lambda_{3}=1+i
$$

Then:

- $|\lambda_1|=2$
- $|\lambda_2| = 3$
- $|\lambda_3| = \sqrt{1^2 + 1^2} = \sqrt{2} \approx 1.414$

Thus: 

$$
\rho(A) = 3
$$

(because 3 is the maximum among 2, 3, and $\sqrt{2}$)

# Perron–Frobenius theorem

Suppose $A \in \mathbb{R}^{n \times n}$ is a:

- **Non-negative matrix**: All entries $A_{ij} \ge 0$,
- **Irreducible matrix**: Cannot be rearranged into a block upper-triangular form (intuitively: the graph is **strongly connected** — you can reach any node from any other node).

Then:  

### 🔹Statement 1:

> The spectral radius $\rho(A)$ is an eigenvalue of $A$, and its multiplicity is one.
> 

**Meaning:**

- $\rho(A)$ = the eigenvalue with largest modulus (absolute value).
- This eigenvalue is **real and positive**.
- It appears **only once** as a root of the characteristic polynomial (multiplicity 1).
- In particular, for **real symmetric matrices** (which are automatically nice), the **largest eigenvalue** is unique and dominates everything else.

### 🔹 Statement 2:

> If $v$ is an eigenvector associated with $\rho(A)$, then:
> 
- **All entries of $v$ are nonzero**, and
- **They all have the same sign** (either all positive, or all negative).

**Meaning:**

- The eigenvector corresponding to the spectral radius **points entirely in one direction** (no sign changes across components).
- Typically, people normalize $v$ to have **all positive entries**.

## 🧠 Intuition of the theorem:

- If you think of $A$ as describing **transitions or influences** (e.g., between web pages, nodes, or population movements), then:
    - The system's **long-term dominant behavior** is governed by the eigenvalue $\rho(A)$.
    - The corresponding eigenvector tells you **relative strengths** or **steady-state** values.
- **Non-negativity** ensures that there are **no cancellations** (no positives and negatives fighting each other).
- **Irreducibility** ensures that the whole system is **connected** and cannot be broken into independent subsystems.

## 📊 Quick Summary Table

| Concept | Meaning |
| --- | --- |
| Non-negative matrix | All $A_{ij} \ge 0$ |
| Irreducible matrix | Strongly connected (cannot break apart) |
| Spectral radius $\rho(A)$ | Largest eigenvalue (positive, real) |
| Multiplicity of $\rho(A)$ | Exactly one (simple root) |
| Eigenvector of $\rho(A)$ | All entries are nonzero and same sign |

# Multiplicity

## 📘 First: What does *multiplicity* mean for an eigenvalue?

When we find eigenvalues, we solve the **characteristic equation**:  

$$
\det(A-\lambda I) = 0
$$

This is a **polynomial** in $\lambda$, usually of degree $n$ if $A$ is $n \times n$.

- **Roots** of this polynomial are the eigenvalues.
- **Multiplicity** refers to **how many times** an eigenvalue appears **as a root**.

### 📚 Two types of multiplicities

| Term | Meaning |
| --- | --- |
| Algebraic multiplicity | How many times λ\lambdaλ appears as a root of the characteristic polynomial. |
| Geometric multiplicity | How many **linearly independent eigenvectors** correspond to $\lambda$. (dimension of eigenspace) |

It is talking about the **algebraic multiplicity**:

> The eigenvalue $\rho(A)$ appears exactly once as a root of $\det(A - \lambda I) = 0$.
> 

✅ There’s **only one copy** of $\rho(A)$ in the characteristic polynomial.
✅ No repeated factors like $(\lambda - \rho(A))^2$ or higher powers.

## 📐 Simple example

Suppose: 

$$
\det(A-\lambda I) = (\lambda - 5)(\lambda-2)^2(\lambda + 1)
$$

Then:

- Eigenvalues are $5,2,−1$.
- $5$ has **multiplicity 1** (appears once).
- $2$ has **multiplicity 2** (appears twice).
- $-1$ has **multiplicity 1**.

**Spectral radius** here is $5$, and it has multiplicity 1.

## 🔵 Why is "multiplicity 1" important in Perron-Frobenius?

- Guarantees that the dominant eigenvalue $\rho(A)$ is **simple** and **isolated**.
- No ambiguity or competition — there’s a unique "most important" eigenvector associated with $\rho(A)$.
- Helps ensure nice convergence properties (like unique steady states in Markov chains, network centrality scores, etc.).

# B**ipartite graph**

A **bipartite graph** is a graph where:

> The set of vertices (nodes) can be **divided into two groups** (say, Group 1 and Group 2)
> 
> 
> such that **every edge connects a vertex from Group 1 to Group 2** — and **no edges** connect two vertices within the same group.
> 

✅ So:

- Edges only **go between groups**, never **inside** a group.

## 📐 Formal definition:

A graph $G=(V,E)$ is **bipartite** if:

- The vertex set $V$ can be split into two disjoint subsets $V_1$ and $V_2$,
- Such that every edge in $E$ connects a vertex from $V_1$ to a vertex from $V_2$.

## 🎯 Simple examples:

- **Example 1**: A graph with vertices $V = \{a, b, c, d\}$ and edges $E = \{(a,c), (a,d), (b,c)\}$.
    - We can split:
        - Group 1: $\{a, b\}$
        - Group 2: $\{c, d\}$
    - Edges only go **between groups**. ✅ Bipartite!
- **Example 2**: A triangle (3 nodes, each connected to each other).
    - No matter how you split into two groups, some edge will connect two nodes in the same group. ❌ **Not bipartite**.

## ✅ Quick Summary

| Concept | Meaning |
| --- | --- |
| Bipartite graph | Vertices split into two groups; edges only go between groups |
| No edges inside groups | Yes |
| No odd cycles | Yes |
| Two-colorable | Yes (nodes can be colored with two colors) |

# Spectrum of Bipartite Graph is Symmetric

> In a bipartite graph:
> 
> - “If $\alpha$ is an eigenvalue of the adjacency matrix $A(G)$,”
> - “Then $−\alpha$ is also an eigenvalue,”
> - “And they have the **same multiplicity** (appear the same number of times).”

---

### 🧠 What does this mean?

- The **spectrum** (the set of eigenvalues) of a bipartite graph is **symmetric about zero**.
- For every positive eigenvalue $\alpha$, there is a matching negative eigenvalue $−\alpha$.
- If $\alpha = 0$, it stays 0.

## Proof idea:

The key is the structure of the adjacency matrix $A(G)$ for a **bipartite graph**.

In a bipartite graph, the nodes can be split into two groups (say Left and Right) such that:

- Edges only go **between** groups, not **inside** a group.

Thus, if you reorder the vertices (rows and columns), the adjacency matrix looks like: 

$$
A(G)=\begin{pmatrix}
0 & B\\
B^T & 0
\end{pmatrix}
$$

where:

- $B$ is some rectangular matrix (connections from Left group to Right group),
- $0$ means there are **no edges inside** Left or Right — consistent with being bipartite.

✅ This special block structure is the key!

## 🧩 How this causes spectrum symmetry

Suppose $\begin{pmatrix}x\\y \end{pmatrix}$ is an eigenvector with eigenvalue $\alpha$, meaning: 

$$
A(G)\begin{pmatrix}
x\\y
\end{pmatrix} = \alpha 
\begin{pmatrix}
x \\y
\end{pmatrix}
$$

Expanding: 

$$
\begin{pmatrix}
0 & B\\
B^{T} & 0
\end{pmatrix}
\begin{pmatrix}
x\\
y
\end{pmatrix} = 
\begin{pmatrix}
By\\
B^{T}x
\end{pmatrix} = 
\alpha \begin{pmatrix}
x\\
y
\end{pmatrix}
$$

Thus: 

- $By = \alpha x$
- $B^T x = ay$

Now notice: 

- If you replace $(x,y)$ with $(x,-y)$
- Then

$$
A(G)\begin{pmatrix}
x\\-y
\end{pmatrix} =
\begin{pmatrix}
B(-y)\\B^Tx
\end{pmatrix} = 
\begin{pmatrix}
-By\\B^Tx
\end{pmatrix} = 
\begin{pmatrix}
-\alpha x\\\alpha y
\end{pmatrix} = -\alpha
\begin{pmatrix}
x\\-y
\end{pmatrix}
$$

✅ Therefore, $(x, -y)$ is an eigenvector for eigenvalue $-\alpha$.

Thus:

- If $\alpha$ is an eigenvalue, so is $−\alpha$.
- They have the **same multiplicity**.

## ✅ Quick Summary:

| Concept | Meaning |
| --- | --- |
| Bipartite graph | Can divide nodes into two groups with no internal edges |
| Adjacency matrix form | Block matrix with $0$ blocks and $B$, $B^T$ blocks |
| Spectrum symmetry | If $\alpha$ is an eigenvalue, so is $-\alpha$ |
| Multiplicity | Both $\alpha$ and $-\alpha$ appear equally often |

# Diagonal Degree Matrix

> Let $G = (V, E)$ be an undirected graph, where the vertices are labeled $1, 2, \dots, n$.
> 

Then:

- The **diagonal degree matrix** $D(G)$ is an $n \times n$ **diagonal matrix** where:
    - $D_{i,i} = \deg(i)$ (degree of vertex $i$)
    - All off-diagonal entries are $0$.

## Example

Suppose we have this simple graph:

- Vertex 1 connected to Vertex 2 and Vertex 3
- Vertex 2 connected to Vertex 1
- Vertex 3 connected to Vertex 1 and Vertex 4
- Vertex 4 connected to Vertex 3

**Degrees:**

- $\deg(1) = 2$ (connected to 2 and 3)
- $\deg(2) = 1$ (connected to 1)
- $\deg(3) = 2$ (connected to 1 and 4)
- $\deg(4) = 1$ (connected to 3)

Thus: 

$$
D(G) = \begin{pmatrix}
2 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & 0 & 2 & 0\\
0 & 0 & 0 & 1\\
\end{pmatrix}
$$

✅ Only the diagonal entries are nonzero, and each entry $D_{i,i}$ equals the degree of vertex $i$.

## 🎯 Why is D(G)  important?

- $D(G)$ is used in **spectral graph theory** together with the **adjacency matrix** $A(G)$.
- The most common combination is the **graph Laplacian**:

$$
L(G) = D(G) - A(G)
$$

where:

- $L(G)$ helps study **connectivity**, **spreading processes**, **random walks**, etc.

# Laplacian Matrix

Let $G$ be an undirected graph. The Laplacian matrix $L(G)$ of $G$ is defined as $L(G) := D(G) - A(G)$.

When we say the $k$-th eigenvalue of a graph, we either mean the $k$-th largest eigenvalue of the adjacency matrix or the $k$-th smallest eigenvalue of the Laplacian matrix.

# Incidence Matrix B(G) and Laplacian Matrix L(G)

## 1. What is an **edge incidence vector** $b_e$?

Suppose $e = (i, j)$ is an edge between node $i$ and node $j$. 

- Then the vector $b_e \in \mathbb{R}^{n}$ is:
    - $+1$ at position $i$
    - $-1$ at position $j$
    - $0$ at all other position

(**One edge $\to$ one vector.**)

## 2. What is the edge incidence matrix $B(G)$?

- **Each column** of $B(G)$ is a vector $b_e$ for an edge $e$.
- $B(G)$ is an $n \times m$ matrix:
    - $n$  = number of vertices
    - $m$ = number of edges

✅ So **each column** describes **one edge**, and tells you **which nodes it connects and in which direction**.

## 3. What is the edge of Laplacian $L_e$ of an edge $e$?

For an edge $e = (i,j)$: 

- $(L_e)_{i,i} = (L_e)_{j,j} = 1$
- $(L_e)_{i,j} = (L_e)_{j,i} = -1$
- All other entries are $0$.

In matrix terms: 

$$
L_e = b_e b_e^{T} \quad (\text{outer product})
$$

✅ **Outer product**: If $b_e$ is a column vector, then $b_e b_e^T$ is an $n\times n$ matrix.

## 4. What is the **graph Laplacian** $L(G)$?

The graph Laplacian is the **sum of all edge Laplacians**: 

$$
L(G) = \sum_{e \in E} L_e = \sum_{e \in E} b_e b_e^T
$$

✅ Alternatively, because matrix multiplication distributes over sums: 

$$
L(G)=B(G)B(G)^{T}
$$

- Multiply the **incidence matrix $B(G)$** with its **transpose $B(G)^T$**.
- This builds the **full Laplacian matrix** for the whole graph

## Putting it all together

| Object | Meaning |
| --- | --- |
| $b_e$ | Edge vector: +1 and -1 at endpoints |
| $B(G)$ | Matrix stacking all $b_e$ as columns |
| $L_e = b_e b^T_e$ | Small Laplacian matrix for one edge |
| $L(G) = \sum_e L_e = B(G)B(G)^T$ | Full graph Laplacian matrix |

## Small example

Suppose $G$ has 3 nodes and 2 edges: 

- $e_1 = (1, 2)$
- $e_2 = (2,3)$

Then: 

- $b_{e_{1}} = (1, -1, 0)^T$
- $b_{e_{2}} = (0, 1, 1)^T$

Thus: 

$$
B(G) = 
\begin{pmatrix}
1 & 0 \\
-1 & 1 \\
0 & -1 \\
\end{pmatrix} \quad
(3 \times 2 \text{ matrix})
$$

Now compute: 

$$
L(G) = B(G)B(G)^T
$$

Multiplying: 

$$
L(G)=
\begin{pmatrix}
1 & 0 \\
-1 & 1 \\
0 & -1 \\
\end{pmatrix}
\begin{pmatrix}
1 & -1 & 0 \\
0 & 1 & -1 \\
\end{pmatrix} = 
\begin{pmatrix}
1 & -1 & 0 \\
-1 & 2 & -1 \\
0 & 1 & -1 \\
\end{pmatrix}
$$

This $L(G)$ is the **graph Laplacian**: 

- Diagonal = degrees
- Off-diagonal = $−1$ if there’s an edge, 0 otherwise

# Smallest Eigenvalue of Laplacian Matrix

> The Laplacian matrix $L(G)$ of an undirected graph $G$ is positive semidefinite, and its **smallest eigenvalue** is **zero**,
> 
> 
> with the **all-ones vector** as a corresponding eigenvector.
> 

## Step-by-step explanation:

## 🔹 1. What does **positive semidefinite** mean?

A matrix $L$ is **positive semidefinite** if: 

$$
x^T L x \ge 0 \quad \text{for all vectors x}
$$

It means: 

- No negative eigenvalues
- All eigenvalues are $\ge 0.$

## 🔹 2. What is the **smallest eigenvalue**?

- For $L(G)$, the **smallest eigenvalue** is exactly **0**.
- It always happens for any graph Laplacian (as long as the graph is undirected).

✅ So the spectrum (set of eigenvalues) looks like: 

$$
0 = \lambda_1 \le \lambda_2 \le \lambda_3 \cdots \le \lambda_n
$$

where $\lambda_1 = 0$ is always the smallest

## 🔹 3. What is the **eigenvector** corresponding to $0$?

It’s the **all-ones vector**: 

$$
1=(1,1,1,\dots,1)^T
$$

✅ The vector of all ones is an eigenvector for eigenvalue 0.

**Reason:** When you multiply $L(G)$ by $\mathbf{1}$: 

$$
L(G)1 =0
$$

because:

- Each row of $L(G)$ sums to 0:
    - The diagonal entry is the degree,
    - The off-diagonal entries are $−1$ where edges exist.
- So when you sum the entries in any row against all-ones, you get 0.

✅ Therefore, $L(G) \mathbf{1} = 0$.

## Tiny Example

$1 --- 2$

Then: 

$$
L(G)= 
\begin{pmatrix}
1 & -1\\
-1 & 1\\
\end{pmatrix}
$$

Now: 

$$
L(G)\begin{pmatrix}
1\\
1\\
\end{pmatrix} = 
\begin{pmatrix}
(1)(1)+ & (-1)(1)\\
(-1)(1) & (1)(1)\\
\end{pmatrix} = 
\begin{pmatrix}
0\\
0\\
\end{pmatrix}
$$

✅ So $\mathbf{1}$ is an eigenvector with eigenvalue 0.

## ✅ Quick Summary

| Concept | Meaning |
| --- | --- |
| Positive semidefinite | All eigenvalues $\ge 0$ |
| Smallest eigenvalue | Always 0 |
| Corresponding eigenvector | All-ones vector $(1,1,\dotsc,1)^T$ |
| Importance | Tells about graph connectivity |

# Quadratic Form for Laplacian Matrix

> Let $L$ be the Laplacian matrix of an undirected graph $G=(V,E)$ with $V(G)=[n]$.
> 
> 
> For any vector $x \in \mathbb{R}^n$,
> 
> $$
> x^T L x = \sum_{ij \in E} (x(i) - x(j))^2
> $$
> 

## Step-by-step explanation:

## 🔹 1. What is the quadratic form $x^T L x$?

- You take a vector $x$,
- Multiply $x^T$ (transpose of $x$) times $L$ times $x$ again.

✅ Result: **A single real number**.

This number measures **how “uneven” or "unsmooth"** the vector xxx is across the edges of the graph.

## 🔹 2. What does $\sum_{ij \in E} (x(i) - x(j))^2$ mean?

It means:

- For each edge $(i, j) \in E$,
- Look at the **difference** between the values $x(i)$ and $x(j)$ at nodes $i$ and $j$,
- Square that difference,
- Then **sum over all edges**.

✅ If $x(i)$ and $x(j)$ are very different → large contribution.

✅ If $x(i) \approx x(j)$ → small contribution.

Thus, $x^T L x$ measures how "smooth" $x$ is **over the graph structure**.

## 📐 Small Example:

Suppose the graph: 

$$
1 ---2---3
$$

(three nodes connected in a line.) 

- The Laplacian $L$ is:

$$
L = 
\begin{pmatrix}
1 & -1 & 0\\
-1 & 2 & -1\\
0 & -1 & 1\\
\end{pmatrix}
$$

Suppose we choose: 

$$
x = \begin{pmatrix}
3\\2\\1
\end{pmatrix}
$$

Now:

- Edge (1,2): $(x(1) - x(2))^2 = (3-2)^2 = 1$
- Edge (2,3): $(x(2) - x(3))^2 = (2-1)^2 = 1$

Thus:

$$
x^T L x = 1 + 1 = 2
$$

✅ You can also directly calculate $x^T L x$ by matrix multiplication and get the same result!

## Why is this important?

- **Small $x^T L x$** means xxx is **smooth**: values don't change much across edges.
- **Large $x^T L x$** means xxx is **rough**: big differences across connected nodes.
- This is key in:
    - **Spectral clustering**
    - **Semi-supervised learning on graphs**
    - **Graph signal processing**

✅ Many algorithms **minimize** $x^T L x$ to find **smooth embeddings**, **communities**, etc.
