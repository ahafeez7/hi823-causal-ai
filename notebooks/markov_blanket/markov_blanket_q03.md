## Question 4.1 — Markov Blanket

### (a) Markov Blanket and Multicollinearity

#### Markov Blanket of Y

Given:
- X1 and X2 are significant predictors of Y  
- X3 and X4 are not significant  
- No interaction terms are significant  

The Markov Blanket of Y is:

$$
\{X1, X2\}
$$

**Explanation:**  
The Markov blanket consists of variables that make Y independent of all others.  
Conditioning on X1 and X2 makes X3 and X4 irrelevant for predicting Y.

---

#### Relation to Multicollinearity

- Multicollinearity refers to correlation among predictors (e.g., X1 and X2).
- Markov blanket refers to variables necessary for predicting Y.

**Key distinction:**
- Markov Blanket → relevance for prediction  
- Multicollinearity → redundancy among predictors  

Even if X1 and X2 are highly correlated, both can still belong to the Markov blanket.

---

### (b) Temporal / Causal Markov Blanket

Given:
- X1 occurs before Y → potential cause  
- X2 occurs after Y → effect  

The Markov Blanket of Y is:

$$
\{X1, X2\}
$$

---

#### Causal Interpretation

- X1 is a **parent (cause)** of Y  
- X2 is a **child (effect)** of Y  

Causal structure:

$$
X1 \rightarrow Y \rightarrow X2
$$

---

#### Key Insight

- X1 explains why Y occurs (cause)  
- X2 reflects consequences of Y (effect)  
- Conditioning on both makes all other variables irrelevant  

---

### Final Summary

- (a) Markov Blanket of Y: {X1, X2}; distinct from multicollinearity  
- (b) Markov Blanket: {X1, X2}, where X1 is a cause and X2 is an effect of Y  
