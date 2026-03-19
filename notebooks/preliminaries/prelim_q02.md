## Manual Solution

### Step 1: Total Number of Voters

$$
N = 20,539 + 30,756 + 52,013 + 29,641 = 132,949
$$

### (a) Probability of being 18–29 years old

$$
P(18\text{–}29) = \frac{20,539}{132,949} \approx 0.1545
$$

**Answer:** 0.155 (≈ 15.5%)

### (b) Probability of being 30–44 given that age $\geq 29$

Since age groups are given in intervals, “at least 29” is approximated as all individuals **excluding the 18–29 group**.

$$
P(30\text{–}44 \mid \text{age} \geq 29) = \frac{30,756}{132,949 - 20,539}
$$

$$
= \frac{30,756}{112,410} \approx 0.2736
$$

**Answer:** 0.274 (≈ 27.4%)

### (c) Expected Value of Age

Use midpoints for each age group:

| Age Group | Midpoint |
|----------|---------|
| 18–29 | 23.5 |
| 30–44 | 37 |
| 45–64 | 54.5 |
| 65+ | 75 (assumed) |

$$
E[X] = \frac{\sum ( \text{midpoint} \times \text{count} )}{N}
$$

$$
E[X] = \frac{(23.5 \times 20,539) + (37 \times 30,756) + (54.5 \times 52,013) + (75 \times 29,641)}{132,949}
$$

$$
E[X] \approx 50.23
$$

**Answer:** Expected age ≈ **50.2 years**
