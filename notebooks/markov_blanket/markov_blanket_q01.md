```markdown id="k7v2rm"
a) Markov Blanket of Y  
Parents: X, W  
Children: Z, T  
Co-parents: Z (via T)  

In a Markov blanket, co-parents (spouses) are other parents of Y’s children.  
So we check:  

For Child Z, the parents are: W, Y. So, co-parent of Y is W (already included)  
For Child T, the parents are: Y, Z. Therefore, co-parent of Y is Z  

So Z is indeed a co-parent of Y via T; however, listing W again as a co-parent is redundant since it is already a parent.  

Markov_Blanket(Y) = {X, W, Z, T}


b) Markov Blanket of W  
Parent: X  
Children: Y, Z  
Co-parents: Y (via Z)  

Markov_Blanket(W) = {X, Y, Z}


c) Parents in Markov Blanket of Z  
Parents of Z: W, Y  

Answer: {W, Y}


d) Regression: Z on X, W, Y (excluding T)  
Only parents of Z remain significant after adjustment.  
X becomes redundant since its effect is mediated through W and Y.  

Significant variables: W, Y


e) Un-confounded effect of Y on T  
Backdoor paths:  

Path 1:  
Y ← W → Z → T  

Interpretation:  
W affects the outcome (T) via Z  
W is a confounder, it influences Y directly but influences T indirectly through Z  
Z is a mediator between W and T  


Path 2:  
Y ← X → W → Z → T  

Interpretation:  
X is a confounder, it influences Y directly and affects T indirectly through W and Z  
W acts as a mediator between X and Z, and Z mediates the effect toward T  
This creates a confounding path between Y and T through upstream variables  


To block these paths, stratify on W.  
Do not stratify on Z because it is a mediator.  

Stratify on: W  


f) Miscelleneous  

After stratifying on W, estimate:

P(T ∣ do(Y)) = ∑_w P(T ∣ Y, W = w) P(W = w)  


Example with values (for illustration):

Assume W ∈ {0, 1}  

P(W = 0) = 0.6  
P(W = 1) = 0.4  

P(T = 1 ∣ Y = 1, W = 0) = 0.30  
P(T = 1 ∣ Y = 1, W = 1) = 0.70  

P(T = 1 ∣ Y = 0, W = 0) = 0.10  
P(T = 1 ∣ Y = 0, W = 1) = 0.40  


For Y = 1:  

P(T ∣ do(Y = 1))  
= (0.30 × 0.6) + (0.70 × 0.4)  
= 0.18 + 0.28  
= 0.46  


For Y = 0:  

P(T ∣ do(Y = 0))  
= (0.10 × 0.6) + (0.40 × 0.4)  
= 0.06 + 0.16  
= 0.22  


Final causal effect  

Difference or ACE (Average Causal Effect):  
0.46 − 0.22 = 0.24  

Ratio:  
0.46 / 0.22 ≈ 2.09  


Interpretation (brief):  
Y increases probability of T by 24 percentage points (ACE = 0.24).
```
