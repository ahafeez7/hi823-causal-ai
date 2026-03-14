# Do-Operator Assignment

## Problem Statement

The following table gives the recovery rates of 700 patients who were prescribed a drug, half of whom took the medication.

|            | Med | No Med |
|------------|-----|--------|
| Men        | 81 recovering (n = 87) | 234 recovering (n = 270) |
| Women      | 192 recovering (n = 263) | 55 recovering (n = 80) |
| Total      | 273 recovering (n = 350) | 289 recovering (n = 350) |

Answer the following questions:

a. What is the probability of taking medications given that the person is female?  
b. What is the probability of remission of symptoms given that the person has taken their medications and the patient is female?  
c. What is the probability of remission of symptoms given that the person has taken their medications and the patient is male?  
d. Which variable is leading to a selection bias if we had observational data on these three variables and wanted to measure the impact of taking the medication?  
e. What is the causal impact of taking the medication?

---

## Part (a)

The probability of taking medication given that the patient is female is computed as a conditional probability. From the table, the number of women who took the medication is 263 and the total number of women is the sum of women who took medication and those who did not take medication.

P(Med | Female) = 263 / (263 + 80)

P(Med | Female) = 263 / 343

P(Med | Female) ≈ 0.767

<div style="background-color:#eef6ff; border-left:6px solid #2563eb; padding:12px; border-radius:6px">

Answer: The probability that a female patient took the medication is **0.767 (76.7%)**.

</div>

---

## Part (b)

The probability of remission given that the patient is female and took the medication is computed using the number of women who recovered among those who took the medication.

P(R | Med, Female) = women recovering with medication / women taking medication

P(R | Med, Female) = 192 / 263

P(R | Med, Female) ≈ 0.730

<div style="background-color:#eef6ff; border-left:6px solid #2563eb; padding:12px; border-radius:6px">

Answer: About **73.0% of women** who took the medication experienced remission of symptoms.

</div>

---

## Part (c)

The probability of remission given that the patient is male and took the medication is computed using the number of men who recovered among those who took the medication.

P(R | Med, Male) = men recovering with medication / men taking medication

P(R | Med, Male) = 81 / 87

P(R | Med, Male) ≈ 0.931

<div style="background-color:#eef6ff; border-left:6px solid #2563eb; padding:12px; border-radius:6px">

Answer: Approximately **93.1% of men** who took the medication experienced remission of symptoms.

</div>

---

## Part (d)

The variable that creates selection bias in the observational data is Gender.

From the DAG it is clear that:

Gender → Medication  
Gender → Remission  

Therefore:

Gender is a confounder.

If we simply compare

P(Remission | Med)

without adjusting for gender, the estimate will be biased.

<div style="background-color:#eef6ff; border-left:6px solid #2563eb; padding:12px; border-radius:6px">

Answer: Gender causes selection bias (confounding bias).

</div>

---

## Part (e)

To estimate the causal impact of the medication, we compute the probability of remission under an intervention using the do-operator.

P(R | do(Med)) = Σ P(R | Med, g) P(g)

First compute the proportion of each gender in the dataset.

P(Female) = number of women / total patients = 343 / 700

P(Male) = number of men / total patients = 357 / 700

Next compute the recovery probabilities within each gender group.

P(R | Med, M) = men recovering with medication / men taking medication = 81 / 87

P(R | Med, F) = women recovering with medication / women taking medication = 192 / 263

Causal probability:

P(R | do(Med))

P(R | do(Med)) = P(R | Med, M)P(M) + P(R | Med, F)P(F)

P(R | do(Med)) = (81/87)(357/700) + (192/263)(343/700)

P(R | do(Med)) ≈ 0.832

Now compute the remission probability if no medication were given.

P(R | NoMed, M) = 234 / 270

P(R | NoMed, F) = 55 / 80

P(R | do(NoMed)) = (234/270)(357/700) + (55/80)(343/700)

P(R | do(NoMed)) ≈ 0.779

---

## Final Causal Effect

ACE = P(R | do(Med)) − P(R | do(NoMed))

ACE = 0.832 − 0.779

ACE = 0.053

<div style="background-color:#eef6ff; border-left:6px solid #2563eb; padding:12px; border-radius:6px">

Interpretation: Taking the medication increases the probability of remission by **5.3 percentage points** after adjusting for gender.

</div>
