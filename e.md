---
layout: page
title: "notes for `e`"
---

{% include mathjax.html %}

# e - Euler's Constant

Jacob Bernoulli in the 17th century posed this question: if I invest £1 at 100% interest for a year, but I compound it n times throughout the year, what do I get?

**Compound once (n=1):**

- Start with £1
- After 1 year: £1 × (1 + 1) = £2

**Compound twice (n=2):**

- Start with £1
- After 6 months: £1 × (1 + 0.5) = £1.50
- After 1 year: £1.50 × (1 + 0.5) = £2.25
- Or directly: £1 × $(1 + \frac{1}{2})^2$ = £1 × $(1.5)^2$ = £2.25

Notice: more frequent compounding gives better returns!

**Compound quarterly (n=4):**

- Each quarter you get 25% interest
- £1 × $(1 + 0.25)^4$ = £1 × $(1.25)^4$ = £2.441

**General formula emerges:**
$\text{Amount} = \left(1 + \frac{1}{n}\right)^n$

As we compound more frequently:

- n=12 (monthly): $(1 + \frac{1}{12})^{12}$ = £2.613
- n=52 (weekly): $(1 + \frac{1}{52})^{52}$ = £2.693
- n=365 (daily): $(1 + \frac{1}{365})^{365}$ = £2.714
- n=10,000: $(1 + \frac{1}{10000})^{10000}$ = £2.7181

Bernoulli knew the answer was between 2 and 3, but couldn't calculate it exactly. Fifty years later, Euler worked it out: **e = 2.71828...**

Mathematically: $e = \lim_{n \to \infty} \left(1 + \frac{1}{n}\right)^n$

## How This Limit Equals 2.718... [The Binomial Expansion](./bionomial.md)

This converges to **e = 2.718281828...**

This discovery means for any rate r over time t with continuous compounding:
$V(t) = V_0 \cdot e^{rt}$

## Understanding Exponential Numbers

The key insight about exponentials: the rate of change depends on the current value itself.

**Linear processes:** Rate is constant

- Your height grows at fixed rate during childhood
- A car traveling at constant speed covers same distance each hour
- Saving $100/month adds same amount regardless of balance

**Exponential processes:** Rate depends on current value

- Money growing with interest: more money = more interest earned
- Cooling coffee: temperature difference from room determines cooling rate
- Population growth: more rabbits = more baby rabbits
- Radioactive decay: more atoms = more decay events

Think about cooling coffee:

- Hot coffee (80°C) in a cold room (20°C): cools rapidly
- Warm coffee (40°C) in same room (20°C): cools slowly
- Rate depends on $(T_{coffee} - T_{room})$

Or compound interest:

- $100 at 5%: earns $5
- $1000 at 5%: earns $50
- Rate depends on current balance

For any exponential $\text{base}^x$:

- At x=3: value = $\text{base}^3$
- At x=4: value = $\text{base}^4$
- The instantaneous rate of change: $\frac{d(\text{base}^x)}{dx} = \text{base}^x \cdot \ln(\text{base})$

The rate is always proportional to the current value. This proportionality constant $\ln(\text{base})$ is different for each base.

## Why We Needed a Standard - The Search for Equilibrium

Think about this problem: you're trying to compare different exponential processes:

- Bacteria multiplying by 2 every hour
- Investment growing at 5% monthly
- Radioactive decay halving every 1000 years

Each has a different base, different time scale. How do we compare them? How do we find a common language?

Here's an observation: if you look at different exponential bases:

For $2^x$:

- Value at any point: $2^x$
- Rate of change: $2^x \cdot \ln(2) \approx 2^x \cdot 0.693$
- The derivative is slower than the function itself!

For $3^x$:

- Value at any point: $3^x$
- Rate of change: $3^x \cdot \ln(3) \approx 3^x \cdot 1.099$
- The derivative is faster than the function itself!

So somewhere between 2 and 3, there must be an equilibrium point where the derivative exactly equals the function. This special base is e.

For any exponential $a^x$:

- Value at x: $a^x$
- Rate of change: $a^x \cdot \ln(a)$

For these to be equal, we need $\ln(a) = 1$.

Solving: $a = e$

Therefore, $$\frac{d(e^x)}{dx} = e^x$$

This is the only exponential where at any point k:

- The value is $e^k$
- The slope is also $e^k$

Geometrically: if you look at the graph of $e^x$, at any point, the height above the x-axis equals the slope of the tangent line. No correction factor needed. This makes e the "natural" base.

## Natural Logarithm: The Inverse Operation

Since $e^x$ is our natural base for exponentials, we need its inverse.

$$\ln(x) = \text{natural log} = \log_e(x)$$

This answers: "what power must e be raised to get x?"

Now we can express any exponential in terms of e:

- $2^x = e^{x \cdot \ln(2)}$
- $10^x = e^{x \cdot \ln(10)}$

## Why Mystery Constants Appear

Remember those proportionality constants? Let's understand them through the chain rule.

Consider $2^x$. We can rewrite this as:
$$2^x = e^{x \cdot \ln(2)}$$

it's just asking: "e to what power gives 2?" Answer: $\ln(2)$.

Now apply the chain rule:
$$\frac{d(2^x)}{dx} = \frac{d(e^{x \cdot \ln(2)})}{dx} = e^{x \cdot \ln(2)} \cdot \ln(2) = 2^x \cdot \ln(2)$$

That mystery constant 0.693 is just $\ln(2)$!

Similarly, for any base a:
$$a^x = e^{x \cdot \ln(a)}$$
$$\frac{d(a^x)}{dx} = a^x \cdot \ln(a)$$

## Back to Finance: Understanding Returns

Now we have two ways to think about growth:

**Simple Ratio (Multiplier):**

- If stock goes $100 to $150
- Ratio = 150/100 = 1.5
- This says "multiply by 1.5"

**Log Return (Growth Rate):**

- Same scenario: $100 to $150
- Log return = $\ln(150/100) = \ln(1.5) = 0.405$
- This says "you grew at continuous rate 40.5%"

## The Problem with Simple Returns

Stock moves: $100 → $200 → $100

Let me break this down:

- Day 1: Stock goes from $100 to $200 (it doubled)
  - Simple return: (200-100)/100 = 100% gain
  - Price multiplier: 200/100 = 2.0
- Day 2: Stock goes from $200 to $100 (it halved)
  - Simple return: (100-200)/200 = -50% loss
  - Price multiplier: 100/200 = 0.5

Using simple returns:

- Day 1: +100%
- Day 2: -50%
- Average: (100 - 50)/2 = 25%

But wait - you ended where you started ($100). How can the average be 25%?

Using log returns:

- Day 1: $\ln(200/100) = \ln(2) = +0.693$
- Day 2: $\ln(100/200) = \ln(0.5) = -0.693$
- Average: $(0.693 - 0.693)/2 = 0$

Perfect. The log returns correctly show zero net change.

## Why Log Returns Add

Prices multiply over time:

- $P_1 = P_0 \times m_1$ (where $m_1$ is first multiplier)
- $P_2 = P_1 \times m_2 = P_0 \times m_1 \times m_2$
- $P_3 = P_2 \times m_3 = P_0 \times m_1 \times m_2 \times m_3$

Taking logs:

- $\ln(P_1/P_0) = \ln(m_1) = r_1$
- $\ln(P_2/P_1) = \ln(m_2) = r_2$
- $\ln(P_3/P_2) = \ln(m_3) = r_3$

Total return:
$$\ln(P_3/P_0) = \ln(m_1 \times m_2 \times m_3) = \ln(m_1) + \ln(m_2) + \ln(m_3) = r_1 + r_2 + r_3$$

The log returns literally add because $\ln(a \times b) = \ln(a) + \ln(b)$.

## Core Finance Applications

### Why e is Central to Finance

Finance is fundamentally about rates - interest rates, growth rates, discount rates. And e is the natural language for rates.

**Present Value and Discounting:**
$$PV = FV \times e^{-rt}$$

- Tells you what future money is worth today
- The negative rate represents discounting

**Risk Management:**

- Value at Risk uses log returns because they're normally distributed
- Portfolio volatility calculated with log returns
- Multiple day returns simply add together

### What e Quickly Tells You

When you see $e^{0.05}$, you immediately know: "5% continuous growth rate"

When you calculate $\ln(1.1) \approx 0.095$, you know: "about 9.5% continuous growth happened"

**Quick Mental Math:**

- $e^{0.01} \approx 1.01$ (1% growth)
- $e^{0.1} \approx 1.105$ (10% continuous ≈ 10.5% simple)
- $e^{1} \approx 2.718$ (100% continuous ≈ 172% simple)
- $e^{-x} = \frac{1}{e^x}$ (negative rates mean decay/discount)

### The Rule of 72

Why does money double in approximately $\frac{72}{r}$ years at r% interest?

For doubling: $e^{rt} = 2$

Taking $\ln$: $rt = \ln(2) \approx 0.693$

Therefore: $t \approx \frac{0.693}{r}$

With r as percentage: $t \approx \frac{69.3}{r} \approx \frac{72}{r}$ (72 is used because it has many divisors)
