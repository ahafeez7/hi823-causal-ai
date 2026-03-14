# Do-Operator Assignment

The following table gives the recovery rates of **700 patients** who were prescribed a drug, half of whom took the medication.

|            | Med | No Med |
|------------|-----|--------|
| **Men**    | 81 recovering (n = 87) | 234 recovering (n = 270) |
| **Women**  | 192 recovering (n = 263) | 55 recovering (n = 80) |
| **Total**  | 273 recovering (n = 350) | 289 recovering (n = 350) |

Answer the following questions:

1. What is the probability of taking medications given that the person is female?
2. What is the probability of the remission of symptoms given that the person has taken their medications and the patient is female?
3. What is the probability of the remission of symptoms given that the person has taken their medications and the patient is male?
4. Which variable is leading to a selection bias if we had observational data on these three variables and wanted to measure the impact of taking the medication?
5. What is the causal impact of taking the medication?

---

# Part (a)

The probability of taking medication given that the patient is female is computed as a conditional probability. From the table, the number of women who took the medication is 263 and the total number of women is the sum of women who took medication and those who did not take medication. Thus, the probability is calculated as the number of women taking medication divided by the total number of women.

$$
P(Med \mid Female) = \frac{\text{# of women taking medication}}{\text{# of women taking medication + # of women not taking medication}}
$$

$$
P(Med \mid Female) = \frac{263}{263+80}
$$

$$
P(Med \mid Female) = \frac{263}{343}
$$

$$
P(Med \mid Female) \approx 0.767
$$

This means that approximately **76.7% of women in the dataset took the medication**.

---

# Part (b)

The probability of remission given that the patient is female and took the medication is computed using the number of women who recovered among those who took the medication. According to the table, 192 women recovered out of the 263 women who took the medication.

$$
P(R \mid Med, Female) = \frac{\text{women recovering with medication}}{\text{women taking medication}}
$$

$$
P(R \mid Med, Female) = \frac{192}{263}
$$

$$
P(R \mid Med, Female) \approx 0.730
$$

Therefore, approximately **73.0% of women who took the medication experienced remission of symptoms**.

---

# Part (c)

The probability of remission given that the patient is male and took the medication is computed using the number of men who recovered among those who took the medication. According to the table, 81 men recovered out of the 87 men who took the medication.

$$
P(R \mid Med, Male) = \frac{\text{men recovering with medication}}{\text{men taking medication}}
$$

$$
P(R \mid Med, Male) = \frac{81}{87}
$$

$$
P(R \mid Med, Male) \approx 0.931
$$

Therefore, approximately **93.1% of men who took the medication experienced remission of symptoms**.

---

# Part (d)

The variable that creates selection bias in the observational data is **Gender**.

From the DAG, it is obvious that:

Gender → Medication  
Gender → Remission  

Therefore:

**Gender is a confounder.**

If we simply compare

$$
P(Remission \mid Med)
$$

without adjusting for gender, the estimate will be biased. In nutshell, **Gender causes selection bias (confounding bias)**.

---

# Part (e)

To estimate the causal impact of the medication, we compute the probability of remission under an intervention using the **do-operator**. Since gender is a confounder, we adjust for gender using the backdoor adjustment formula.

$$
P(R \mid do(Med)) =
\sum_g P(R \mid Med, g)P(g)
$$

First, we compute the proportion of each gender in the dataset. The dataset contains 700 patients.

$$
P(Female) = \frac{\text{# of women}}{\text{total patients}} = \frac{343}{700}
$$

$$
P(Male) = \frac{\text{# of men}}{\text{total patients}} = \frac{357}{700}
$$

Next, we compute the recovery probabilities within each gender group.

$$
P(R \mid Med, M) = \frac{\text{men recovering with medication}}{\text{men taking medication}}
$$

$$
P(R \mid Med, M) = \frac{81}{87}
$$

$$
P(R \mid Med, F) = \frac{\text{women recovering with medication}}{\text{women taking medication}}
$$

$$
P(R \mid Med, F) = \frac{192}{263}
$$

Now we compute the causal probability.

Causal probability:

$$
P(R \mid do(Med))
$$

$$
P(R \mid do(Med)) =
P(R \mid Med, M)P(M) + P(R \mid Med, F)P(F)
$$

$$
P(R \mid do(Med)) =
\left(\frac{81}{87}\right)\left(\frac{357}{700}\right) +
\left(\frac{192}{263}\right)\left(\frac{343}{700}\right)
$$

$$
P(R \mid do(Med)) \approx 0.832
$$

Next we compute the remission probability if no medication were given.

$$
P(R \mid NoMed, M) = \frac{\text{men recovering without medication}}{\text{men not taking medication}}
$$

$$
P(R \mid NoMed, M) = \frac{234}{270}
$$

$$
P(R \mid NoMed, F) = \frac{\text{women recovering without medication}}{\text{women not taking medication}}
$$

$$
P(R \mid NoMed, F) = \frac{55}{80}
$$

$$
P(R \mid do(NoMed)) =
\left(\frac{234}{270}\right)\left(\frac{357}{700}\right) +
\left(\frac{55}{80}\right)\left(\frac{343}{700}\right)
$$

$$
P(R \mid do(NoMed)) \approx 0.779
$$

---

# Final causal effect

The **Average Causal Effect (ACE)** of the medication is the difference between the probability of remission under treatment and the probability of remission without treatment.

$$
ACE = P(R \mid do(Med)) - P(R \mid do(NoMed))
$$

$$
ACE = 0.832 - 0.779
$$

$$
ACE = 0.053
$$

This result indicates that **taking the medication increases the probability of remission by approximately 5.3 percentage points after adjusting for gender**.
