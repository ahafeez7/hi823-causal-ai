## Causal Inference Problem – AI Antidepressant Advice

We analyze whether an AI system improves recovery from depression

### Given Data

| Group  | Advice Followed | Advice Not Followed|
|--------|-----------------|---------------------|
| Men    | 81 / 87         | 234 / 270           |
| Women  | 192 / 263       | 55 / 80             |
| Total  | 273 / 350       | 289 / 350           |

### Part (a) Is the AI system effective for men?

- P(Recovery | Followed, Men) = 81 / 87 ≈ 0.931  
- P(Recovery | Not Followed, Men) = 234 / 270 ≈ 0.867  

Conclusion:  
The AI system improves recovery for men.


### Part (b) Is the AI system effective for women?

- P(Recovery | Followed, Women) = 192 / 263 ≈ 0.730  
- P(Recovery | Not Followed, Women) = 55 / 80 ≈ 0.688  

Conclusion:  
The AI system improves recovery for women.


### Part (c) Is the AI system effective overall (ignoring gender)?

- P(Recovery | Followed) = 273 / 350 ≈ 0.780  
- P(Recovery | Not Followed) = 289 / 350 ≈ 0.826  

Conclusion:  
The AI system appears less effective when gender is ignored.

### Explanation

Within each subgroup (men and women), the AI system improves recovery.  
However, when the data are aggregated, the AI system appears to reduce recovery. This is in accordance with the Simpson's Paradox

This reversal is an example of Simpson’s paradox and is caused by gender acting as a confounder.

### Causal Interpretation

To estimate the causal effect, adjustment for gender is required:

$$
P(Y \mid do(A)) = \sum_{Z} P(Y \mid A, Z)\, P(Z)
$$

Where:
- \(A\): Following AI advice  
- \(Z\): Gender  

$$
P(\text{Recovery} \mid do(\text{Following AI advice})) =
P(\text{Recovery} \mid \text{Following AI advice}, \text{Men}) \cdot P(\text{Men}) +
P(\text{Recovery} \mid \text{Following AI advice}, \text{Women}) \cdot P(\text{Women})
$$

$$
= (0.931 \cdot 0.51) + (0.730 \cdot 0.49)
$$

$$
= \left(\frac{81}{87}\cdot\frac{357}{700}\right) +
\left(\frac{192}{263}\cdot\frac{343}{700}\right)
\approx 0.833
$$

---

$$
P(\text{Recovery} \mid do(\text{Not Following AI advice})) =
P(\text{Recovery} \mid \text{Not Following AI advice}, \text{Men}) \cdot P(\text{Men}) +
P(\text{Recovery} \mid \text{Not Following AI advice}, \text{Women}) \cdot P(\text{Women})
$$

$$
= (0.867 \cdot 0.51) + (0.688 \cdot 0.49)
$$

$$
= \left(\frac{234}{270}\cdot\frac{357}{700}\right) +
\left(\frac{55}{80}\cdot\frac{343}{700}\right)
\approx 0.780
$$


In nutshell, AI is Effective for men as well as for women. The AI system actually helps patients recover. However, when gender is ignored and the data are aggregated, it appears that the AI system is less effective. This occurs due to confounding by gender, which distorts the comparison between groups.
