# Causal Inference Problem – AI Antidepressant Advice

We analyze whether an AI system improves recovery from depression.

---

## Given Data

| Group   | Advice Followed | Advice Not Followed |
|--------|-----------------|---------------------|
| Men    | 81 / 87         | 234 / 270           |
| Women  | 192 / 263       | 55 / 80             |
| Total  | 273 / 350       | 289 / 350           |

---

## (a) Is the AI system effective for men?

- P(Recovery | Followed, Men) = 81 / 87 ≈ **0.931**
- P(Recovery | Not Followed, Men) = 234 / 270 ≈ **0.867**

✅ **Conclusion:**  
The AI system **improves recovery for men**.

---

## (b) Is the AI system effective for women?

- P(Recovery | Followed, Women) = 192 / 263 ≈ **0.730**
- P(Recovery | Not Followed, Women) = 55 / 80 ≈ **0.688**

✅ **Conclusion:**  
The AI system **improves recovery for women**.

---

## (c) Is the AI system effective overall (ignoring gender)?

- P(Recovery | Followed) = 273 / 350 ≈ **0.780**
- P(Recovery | Not Followed) = 289 / 350 ≈ **0.826**

❌ **Conclusion:**  
The AI system appears **less effective overall**.

---

## Key Insight: Simpson’s Paradox

- Within each subgroup (men and women): AI helps ✅  
- Aggregated data: AI appears harmful ❌  

👉 This is **Simpson’s Paradox**, caused by **gender as a confounder**.

---

## Causal Interpretation

To estimate the true causal effect:

\[
P(Y \mid do(A)) = \sum_{Z} P(Y \mid A, Z) P(Z)
\]

Where:
- A = Following AI advice  
- Z = Gender  

---

## Final Conclusion

- (a) Men: ✅ Effective  
- (b) Women: ✅ Effective  
- (c) Overall: ❌ Misleading  

👉 **Correct causal conclusion:**  
The AI system is effective, but confounding by gender reverses the observed association.
