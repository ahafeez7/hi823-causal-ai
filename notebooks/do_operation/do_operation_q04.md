**Question 04 (Question 03 from the canvas assignment) — Propensity Scores and AI Impact on Remission**

The following table provides the **joint probability distribution** of:

- X : Clinician prescription  
- Y : Patient remission  
- Z : Artificial Intelligence (AI) recommendation  

| X (Clinician Prescription) | Y (Remission) | Z (AI Advice) | Probability |
|---|---|---|---|
| Med A | Yes | Med A | 0.116 |
| Med A | Yes | Other Med | 0.274 |
| Med A | No | Med A | 0.010 |
| Med A | No | Other Med | 0.101 |
| Other Med | Yes | Med A | 0.334 |
| Other Med | Yes | Other Med | 0.079 |
| Other Med | No | Med A | 0.051 |
| Other Med | No | Other Med | 0.036 |

Where

X = clinician prescription  
Y = patient remission  
Z = AI recommendation  

---

**Part (a) Propensity Score of Clinician Prescribing Medication**

The **propensity score** is the conditional probability of receiving treatment given covariates.

P(X | Z) = P(X,Z) / P(Z)

The propensity score represents the probability that a treatment is assigned given observed characteristics.

---

**Probability of AI Recommendation**

**AI recommends Med A**

P(Z = MedA)

0.116 + 0.010 + 0.334 + 0.051 = 0.511

**AI recommends Other Medication**

P(Z = MedOther)

0.274 + 0.101 + 0.079 + 0.036 = 0.490

---

**Propensity Scores**

**Clinician prescribing Med A when AI recommends Med A**

P(X = MedA | Z = MedA)

(0.116 + 0.010) / 0.511

= 0.126 / 0.511

= **0.2466**

---

**Clinician prescribing Med A when AI recommends Other Medication**

P(X = MedA | Z = MedOther)

(0.274 + 0.101) / 0.490

= 0.375 / 0.490

= **0.7653**

---

**Part (b) Unconfounded Impact Using Inverse Propensity Scores**

Inverse propensity weighting corrects treatment selection bias.

Weight formula

w = 1 / P(X | Z)

Weights

When Z = MedA

w = 1 / 0.2466 ≈ **4.05**

When Z = MedOther

w = 1 / 0.7653 ≈ **1.31**

Inverse probability weighting helps adjust observational data so treatment assignment behaves like a randomized experiment.

---

**Part (c) Impact of AI System on Remission**

The expected remission probability under the AI system is

P(Remission)

= Σ P(Y | Z) P(Z)

---

**Remission when AI recommends Med A**

P(Y = Yes | Z = MedA)

(0.116 + 0.334) / 0.511

= 0.450 / 0.511

= **0.8806**

---

**Remission when AI recommends Other Medication**

P(Y = Yes | Z = MedOther)

(0.274 + 0.079) / 0.490

= 0.353 / 0.490

= **0.7204**

---

**Expected Remission under AI System**

P(Remission)

= (0.8806 × 0.511) + (0.7204 × 0.490)

= 0.4499 + 0.3520

= **0.8019**

---

**Part (d) Clinician Prescription Given AI Recommendation**

**Clinician prescribing Med A when AI recommends Med A**

P(X = MedA | Z = MedA)

= **0.2466**

---

**Clinician prescribing Other Medication when AI recommends Other Medication**

P(X = OtherMed | Z = MedOther)

(0.079 + 0.036) / 0.490

= 0.115 / 0.490

= **0.2347**

---

**Final Interpretation**

Propensity scores

P(X = MedA | Z = MedA) ≈ 0.247  
P(X = MedA | Z = MedOther) ≈ 0.765  

Expected remission under AI system

≈ **0.802**

This means that **the AI recommendation system yields approximately an 80.2% remission probability**.

Inverse propensity weighting removes clinician prescription bias by reweighting the observations.
