# Networks from Independence Assumptions

## Case 1
Nodes: X, Y, Z  
Assumption: I(X, Y)

Network:  
X → Z ← Y

Prediction formula:  
P(Z | X, Y)

## Case 2
Nodes: X, Y, Z  
Assumption: I(X, Y), Not I(X, Y | Z)

Network:  
X → Z ← Y

Explanation:  
X and Y are marginally independent but become dependent given Z, indicating a collider at Z.

Prediction formula:  
P(Z | X, Y)

## Case 3
Nodes: X, Y, Z  
Assumption: I(X, Y), I(X, Y | Z), Y measured last

Network:  
Z → X  
Z → Y

Explanation:  
X and Y are independent both marginally and conditionally, implying a common cause Z.

Prediction formula (predict Y):  
P(Y | Z)

## Case 4
Nodes: X, Y, Z, W  
Assumption: I(X, Y), I(X, Y | Z), I({X, Y}, W | Z), W measured last

Network:  
Z → X  
Z → Y  
Z → W

Explanation:  
Z is a common cause of X, Y, and W. W is independent of X and Y given Z.

Prediction formula (predict W):  
P(W | Z)

## Case 5
Nodes: X, Y, Z, W  
Assumption: I(X, Y), I(Z, W), and X measured before Z and Y measured before W

Network:  
X → Z  
Y → W  

Explanation:  
Two independent causal chains. X influences Z, and Y influences W. No cross connections.

Prediction formula (predict W):  
P(W | Y)
