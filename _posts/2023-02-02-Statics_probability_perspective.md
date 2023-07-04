---
layout: post
title: STATS) Basic Stats for AI
categories: AI
tags: [Statistics, Math, AI]
---
## 1. Statistics in AI
<hr>

<img src = "https://user-images.githubusercontent.com/80208196/216513932-a4426d31-87e2-4437-80da-327b137aa623.png">
<center><span style = "opacity:0.5">fig 1. Probability density function imitation</span></center><br/>

&nbsp;&nbsp;The goal of AI imitates a function in real world. If an AI model works well, it can predicts deterministic target. However, real world consists probability density. So, There is not always deterministic value. The true goal of AI is imitates probability density function in real world. Neural networks can model a virtual probability density function $P(\mathrm{y}\| \mathrm{x})$, and approximate a probability density function of real world.

<br/><br/>

## 2. Probability distribution
<hr>
<img src = "https://user-images.githubusercontent.com/80208196/216532809-312cf775-6022-44db-9687-81d7e3150a47.png"><center><span style = "opacity:0.5">fig 2. Probability distribution</span></center><br/>
<img src = "https://user-images.githubusercontent.com/80208196/216532912-b93d5055-8797-4ebd-8a47-0046216422ff.png"><center><span style = "opacity:0.5">fig 3. Joint probability distribution <a href = "https://en.wikipedia.org/wiki/Joint_probability_distribution">(ref. Wikipedia)</a></span></center><br/>

|:---:|:---:|
|$P(\mathrm{x}=x)$, $P(x)$|Probability that variable $\mathrm{x}$ is $x$|
|$P(\mathrm{x})$|Probability distribution (function)|
|$P(\mathrm{x}, \mathrm{y})$|Joint probability distribution|


<br/><br/>
<img src = "https://user-images.githubusercontent.com/80208196/216573347-400d1991-73b4-49cf-8d42-1ed9d4f0a66c.png"><center><span style = "opacity:0.5">fig 4. Two kinds of Probability distribution</span></center><br/>

1. Discrete Probability Distribution
    - All case $x$ is discrete.
    - $\Sigma_x{P(\mathrm{x}=x)}=1, \; where\; 0 \leq P(\mathrm{x} = x) \leq 1, \; \forall{x} \in \chi$
    - Probability Mass Function(PMF) (fig 4. left plot)

<br/>

2. Continuous Probability Distribution
    - $\int{p(x)}dx=1, \; where\; p(x) \geq 0, \forall{x} \in \mathbb{R}$
    - Probability Density Function (PDF) (fig 4. right plot)
    - Contrary to discrete probability, It is not possible to find probability about a given sample.

<br/><br/>

## 3. Conditional Probability
<hr>

$$
P(\mathrm{y}\|\mathrm{x})=\frac{P(\mathrm{x},\mathrm{y})}{P(\mathrm{x})}
$$
$$ P(\mathrm{x},\mathrm{y})=P(\mathrm{y}\|\mathrm{x})P(\mathrm{x}) $$
$$ P(\mathrm{x},\mathrm{y})=P(\mathrm{x}\|\mathrm{y})P(\mathrm{y}) $$

### Bayes Theorem
- When dataset $D$ is given, the probability of hypothesis $h$.

$$ P(h\|D)=\frac{P(D, h)P(h)}{P(D)} $$

- induction
$$ P(h\|D)=\frac{P(h, D)}{P(D)} $$
$$ P(h\|D)P(D)=P(h, D)=P(D\|h)P(h) $$
$$ P(h\|D)=\frac{P(D, h)P(h)}{P(D)} $$

## 4. Marginal Distribution
<hr>

- From joint probability distribution, get a probability function of a probability variable.

$$\begin{aligned} P(x) &= \int{P(x, z)}dz \\ &= \int{P(x\|z)P(z)}dz \end{aligned}$$

&nbsp;&nbsp;Use Bayes Theorem.

$$ \;\;\;\; = \int{P(z\|x)P(x)}dz $$

&nbsp;&nbsp;$P(x)$ is constant. The integral is about $z$, so the result of the integral is 1.

$$\begin{aligned} &= P(x)\int{P(z\|x)}dz \\ &= P(x) \end{aligned}$$

## 5. Expectation
<hr>

$$ \mathbb{E}_{\mathrm{x}\sim P(\mathrm{x})}{f(x)} $$

$\mathrm{x}\sim P(\mathrm{x})$: $x$ sampled from $P(\mathrm{x})$ 

$$ \mathbb{E}_{\mathrm{x}\sim P(\mathrm{x})}{f(x)} =\sum _{x \in \chi} P(x)*f(x) $$

- In marginal distribution

$$ \begin{aligned} P(x) &= \int{P(x,z)}dz \\ &= \int{P(x\|z)P(z)}dz \\ &= \mathbb{E}_{\mathrm{z}\sim P(\mathrm{z})}[P(x\| \mathrm{z})] \end{aligned} $$

### Monte-Carlro Method

- Sampling from probability distribution, get weighted average of $f$

$$ \mathbb{E}_{\mathrm{x} \sim P(\mathrm{x})}[f(x)] \approx \frac{1}{n} \sum _{i=1}^{n} f(x_i), \; where \; x_i \sim P(\mathrm{x})) $$


## Refers
<hr>
<a href = "https://en.wikipedia.org/wiki/Joint_probability_distribution">Wikipedia, "Joint probability distribution"</a>