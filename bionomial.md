# Deriving e: The Binomial Expansion Method

> **Goal:** Understand how $(1 + \frac{1}{n})^n$ becomes $e = 2.71828...$ as $n \to \infty$

---

## Step 1: Discovering the Binomial Pattern

### Expand Powers of $(x+y)$ and Look for Patterns

Let's expand $(x+y)^n$ for small values of n:

$(x+y)^0 = 1$

$(x+y)^1 = x + y$

$(x+y)^2 = x^2 + 2xy + y^2$

$(x+y)^3 = x^3 + 3x^2y + 3xy^2 + y^3$

$(x+y)^4 = x^4 + 4x^3y + 6x^2y^2 + 4xy^3 + y^4$

$(x+y)^5 = x^5 + 5x^4y + 10x^3y^2 + 10x^2y^3 + 5xy^4 + y^5$

---

### Pattern 1: The Powers

Rewrite showing all powers explicitly (even when 0 or 1):

$(x+y)^0 = x^0y^0$

$(x+y)^1 = x^1y^0 + x^0y^1$

$(x+y)^2 = x^2y^0 + x^1y^1 + x^0y^2$

$(x+y)^3 = x^3y^0 + x^2y^1 + x^1y^2 + x^0y^3$

$(x+y)^4 = x^4y^0 + x^3y^1 + x^2y^2 + x^1y^3 + x^0y^4$

**Pattern:** For row $n$:

- First term: $x^n y^0$
- Each subsequent term: power of $x$ decreases by 1, power of $y$ increases by 1
- Powers always add to $n$

**General term:** $x^k y^{n-k}$ where $k$ goes from 0 to $n$

---

### Pattern 2: The Coefficients (Pascal's Triangle)

Just the coefficients:

```
n=0:                    1
n=1:                  1   1
n=2:                1   2   1
n=3:              1   3   3   1
n=4:            1   4   6   4   1
n=5:          1   5  10  10   5   1
```

**Pattern:** Each number = sum of two numbers above it

- $2 = 1 + 1$
- $3 = 1 + 2$
- $6 = 3 + 3$

---

### Why Pascal's Triangle Appears

To get next row, multiply previous row by $(x+y)$.

**Example:** From $(x+y)^2$ to $(x+y)^3$:

$(x^2 + 2xy + y^2) \times (x+y)$

Distribute $x$: $x^3 + 2x^2y + xy^2$

Distribute $y$: $x^2y + 2xy^2 + y^3$

Combine like terms:
$$x^3 + (2x^2y + x^2y) + (xy^2 + 2xy^2) + y^3$$
$$= x^3 + 3x^2y + 3xy^2 + y^3$$

The coefficient 3 comes from $2+1$ (adding adjacent coefficients)!

---

## Step 2: Understanding Binomial Coefficients

### What is $\binom{n}{k}$ (n choose k)?

**Answers:** "How many ways can we select k items from n items when order doesn't matter?"

**Formula:**
$$\binom{n}{k} = \frac{n!}{k!(n-k)!}$$

---

### Understanding Factorials

**Definition:** $n! = n \times (n-1) \times (n-2) \times ... \times 2 \times 1$

**Examples:**

- $5! = 5 \times 4 \times 3 \times 2 \times 1 = 120$
- $3! = 3 \times 2 \times 1 = 6$
- $2! = 2$
- $1! = 1$
- $0! = 1$ (by definition)

**What $n!$ represents:** Number of ways to arrange n items in order.

Example: 3 books (A,B,C) → 6 arrangements: ABC, ACB, BAC, BCA, CAB, CBA = $3!$

---

### Example: $\binom{5}{2}$ - Choose 2 from 5

**List all unordered pairs from 5 items:**

1. {1,2}
2. {1,3}
3. {1,4}
4. {1,5}
5. {2,3}
6. {2,4}
7. {2,5}
8. {3,4}
9. {3,5}
10. {4,5}

**Total: 10 pairs**

**Using formula:**
$$\binom{5}{2} = \frac{5!}{2!(5-2)!} = \frac{120}{2 \times 6} = \frac{120}{12} = 10$$

---

### Why the Formula Works

**Step 1: Count ordered selections**

If order matters (position 1 vs position 2):

- First pick: 5 choices
- Second pick: 4 choices
- Total: $5 \times 4 = 20$ ordered pairs

Using factorials: $\frac{5!}{3!} = \frac{5 \times 4 \times 3!}{3!} = 5 \times 4 = 20$

**What $(n-k)!$ does:** Cancels positions we're not filling (we pick 2 from 5, so 3 positions unused)

**Step 2: Remove duplicates**

Order doesn't matter, so (Item 1, Item 2) and (Item 2, Item 1) are the same pair.

Each pair was counted twice in our 20!

**Ways to arrange 2 items:** $2! = 2$

**Fix:** $\frac{20}{2} = 10$ unordered pairs

---

### Formula Breakdown

$$\binom{n}{k} = \frac{n!}{k!(n-k)!}$$

**What each part does:**

1. $n!$ - all arrangements of n items
2. Divide by $(n-k)!$ - cancel unused positions → ordered selections
3. Divide by $k!$ - remove duplicate orderings → unordered selections

---

## Step 3: The Binomial Theorem

### The Formula

$$(x+y)^n = \sum_{k=0}^{n} \binom{n}{k} x^k y^{n-k}$$

**Expanded:**
$$(x+y)^n = \binom{n}{0}y^n + \binom{n}{1}xy^{n-1} + \binom{n}{2}x^2y^{n-2} + ... + \binom{n}{n}x^n$$

---

### Why Coefficients Equal $\binom{n}{k}$ - The Counting Interpretation

When expanding $(x+y)^n$, we multiply:
$$(x+y)(x+y)(x+y) \cdots (x+y) \quad \text{(n copies)}$$

**To form any term:** Pick either $x$ or $y$ from each copy, then multiply.

---

### Example: $(x+y)^4$ → Getting $x^3y^1$

Need: three $x$'s and one $y$

**Question:** In how many ways can we pick $x$ from 3 copies (out of 4)?

**Answer:** $\binom{4}{3} = 4$ ways

**List all ways:**

1. Pick $x$ from copies 1,2,3 and $y$ from copy 4 → $x \cdot x \cdot x \cdot y = x^3y$
2. Pick $x$ from copies 1,2,4 and $y$ from copy 3 → $x \cdot x \cdot y \cdot x = x^3y$
3. Pick $x$ from copies 1,3,4 and $y$ from copy 2 → $x \cdot y \cdot x \cdot x = x^3y$
4. Pick $x$ from copies 2,3,4 and $y$ from copy 1 → $y \cdot x \cdot x \cdot x = x^3y$

**Coefficient is 4** because there are 4 ways to form $x^3y$!

$$\binom{4}{3} = \frac{4!}{3!1!} = \frac{24}{6} = 4$$

---

### Example: $(x+y)^4$ → Getting $x^2y^2$

Need: two $x$'s and two $y$'s

**Question:** From which 2 copies (out of 4) will we pick $x$?

**Answer:** $\binom{4}{2} = 6$ ways

**The 6 ways:**

1. Pick $x$ from copies 1,2 → $x \cdot x \cdot y \cdot y = x^2y^2$
2. Pick $x$ from copies 1,3 → $x \cdot y \cdot x \cdot y = x^2y^2$
3. Pick $x$ from copies 1,4 → $x \cdot y \cdot y \cdot x = x^2y^2$
4. Pick $x$ from copies 2,3 → $y \cdot x \cdot x \cdot y = x^2y^2$
5. Pick $x$ from copies 2,4 → $y \cdot x \cdot y \cdot x = x^2y^2$
6. Pick $x$ from copies 3,4 → $y \cdot y \cdot x \cdot x = x^2y^2$

**Coefficient is 6!**

$$\binom{4}{2} = \frac{4!}{2!2!} = \frac{24}{4} = 6$$

---

### General Pattern

For $(x+y)^n$, to get $x^k y^{n-k}$:

- Pick $x$ from exactly $k$ copies
- Remaining $(n-k)$ copies give $y$

**How many ways?** $\binom{n}{k}$ ways

**That's why the coefficient is $\binom{n}{k}$!**

---

## Step 4: Apply to $(1 + \frac{1}{n})^n$

### Set Up the Expansion

Using $x=1$ and $y=\frac{1}{n}$ in the binomial theorem:

$$(1 + \frac{1}{n})^n = \sum_{k=0}^{n} \binom{n}{k} \cdot 1^k \cdot \left(\frac{1}{n}\right)^{n-k}$$

Since $1^k = 1$:

$$(1 + \frac{1}{n})^n = \sum_{k=0}^{n} \binom{n}{k} \cdot \frac{1}{n^{n-k}}$$

**Reindex:** Replace $k$ with $(n-k)$. Using symmetry $\binom{n}{n-k} = \binom{n}{k}$:

$$(1 + \frac{1}{n})^n = \sum_{k=0}^{n} \binom{n}{k} \cdot \frac{1}{n^{k}}$$

**Expanded:**
$$(1 + \frac{1}{n})^n = \binom{n}{0} + \binom{n}{1}\frac{1}{n} + \binom{n}{2}\frac{1}{n^2} + \binom{n}{3}\frac{1}{n^3} + \cdots$$

---

### Calculate Each Term

**Term 0 ($k=0$):**
$$\binom{n}{0}\frac{1}{n^0} = 1 \cdot 1 = 1$$

**Term 1 ($k=1$):**
$$\binom{n}{1}\frac{1}{n} = \frac{n}{1} \cdot \frac{1}{n} = 1$$

**Term 2 ($k=2$):**
$$\binom{n}{2}\frac{1}{n^2} = \frac{n(n-1)}{2} \cdot \frac{1}{n^2} = \frac{n(n-1)}{2n^2}$$

Simplify:
$$= \frac{1}{2} \cdot \frac{n}{n} \cdot \frac{n-1}{n} = \frac{1}{2!}\left(1 - \frac{1}{n}\right)$$

**Term 3 ($k=3$):**
$$\binom{n}{3}\frac{1}{n^3} = \frac{n(n-1)(n-2)}{6} \cdot \frac{1}{n^3}$$

$$= \frac{1}{3!} \cdot \frac{n}{n} \cdot \frac{n-1}{n} \cdot \frac{n-2}{n} = \frac{1}{3!}\left(1 - \frac{1}{n}\right)\left(1 - \frac{2}{n}\right)$$

**Term 4 ($k=4$):**
$$\binom{n}{4}\frac{1}{n^4} = \frac{1}{4!}\left(1 - \frac{1}{n}\right)\left(1 - \frac{2}{n}\right)\left(1 - \frac{3}{n}\right)$$

**General pattern (Term $k$):**
$$\text{Term}_k = \frac{1}{k!}\left(1 - \frac{1}{n}\right)\left(1 - \frac{2}{n}\right) \cdots \left(1 - \frac{k-1}{n}\right)$$

---

### Complete Expansion

$$(1 + \frac{1}{n})^n = 1 + 1 + \frac{1}{2!}\left(1 - \frac{1}{n}\right) + \frac{1}{3!}\left(1 - \frac{1}{n}\right)\left(1 - \frac{2}{n}\right) + \cdots$$

---

## Step 5: Take the Limit as $n \to \infty$

### The Key Observation

As n gets larger and larger:

- $\left(1 - \frac{1}{n}\right) \to 1$
- $\left(1 - \frac{2}{n}\right) \to 1$
- $\left(1 - \frac{3}{n}\right) \to 1$
- All such terms approach 1

**Why?** We subtract $\frac{\text{constant}}{n}$ from 1. As $n \to \infty$, that fraction vanishes.

**Examples:**

- $n=10$: $(1-\frac{1}{10}) = 0.9$
- $n=100$: $(1-\frac{1}{100}) = 0.99$
- $n=1000$: $(1-\frac{1}{1000}) = 0.999$
- $n \to \infty$: $(1-\frac{1}{n}) \to 1$

---

### The Result

$$e = \lim_{n \to \infty}\left(1 + \frac{1}{n}\right)^n = 1 + 1 + \frac{1}{2!} + \frac{1}{3!} + \frac{1}{4!} + \frac{1}{5!} + \cdots$$

**Or:**
$$e = \sum_{k=0}^{\infty} \frac{1}{k!}$$

---

## Step 6: Compute the Value

$$e = \frac{1}{0!} + \frac{1}{1!} + \frac{1}{2!} + \frac{1}{3!} + \frac{1}{4!} + \frac{1}{5!} + \frac{1}{6!} + \frac{1}{7!} + \cdots$$

$$= 1 + 1 + \frac{1}{2} + \frac{1}{6} + \frac{1}{24} + \frac{1}{120} + \frac{1}{720} + \frac{1}{5040} + \cdots$$

**Calculate step by step:**

| Terms Added | Running Total | Decimal |
| ----------- | ------------- | ------- |
| 1           | 1             | 1.00000 |
| +1          | 2             | 2.00000 |
| +1/2        | 2.5           | 2.50000 |
| +1/6        | 2.66666...    | 2.66667 |
| +1/24       | 2.70833...    | 2.70833 |
| +1/120      | 2.71666...    | 2.71667 |
| +1/720      | 2.71805...    | 2.71806 |
| +1/5040     | 2.71825...    | 2.71825 |
| +1/40320    | 2.71828...    | 2.71828 |

**Converges to:**
$$e = 2.718281828...$$
