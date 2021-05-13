# END2 Session 2 Assignment

## BackProp, Embeddings and Language Models

**Assignment**:
### 1. Rewrite the whole excel sheet showing backpropagation. Explain each major step, and write it on Github.:
  - Use exactly the same values for all variables as used in the class
  - Take a screenshot, and show that screenshot in the readme file

## Solution:
  - Screenshot of excel -

  ![alt](https://github.com/SachinDangayach/END2.0/blob/main/Session2/Images/Excel_NN.JPG)

### Excel file must be there for us to cross-check the image shown on readme (no image = no score)

## Solution:  
**[Link to excel](https://github.com/SachinDangayach/END2.0/blob/main/Session2/NN%20Training.xlsx)**

### Explain each major step

## Solution:  
![alt](https://github.com/SachinDangayach/END2.0/blob/main/Session2/Images/NN.png)
***NN parameters, activation function output and loss calculation***
h1 = w1 * i1+w2 * i2  
h2 = w3 * i1+w4 * i2  
a_h1 = σ(h1) = 1/(1+exp(-h1))  
a_h2 = σ(h2)  
o1 = w5 * a_h1+w6 * a_h2  
o2 = w7 * a_h1+w8 * a_h2  
a_o1 = σ(o1)  
a_o2 = σ(o2)  
E1 = ½ * (t1-a_o1)²  
E2 = ½ * (t2-a_o2)²  

***Partial Derivation on total loss wrt Weights of network***
1.	∂E_T/∂w5 = ∂(E1+E2)/∂w5 = ∂E1/∂w5 = (∂E1/∂a_o1) * (∂a_o1/∂o1) * (∂o1/∂w5)  ---- (1)  
Now, ∂E1/∂a_o1 = (t1 - a_o1) * (-1) = a_o1 – t1   ---- x  
∂a_o1/∂o1 = ∂(σ(o1))/ ∂o1 = σ(o1) * (1 - σ(o1)) = a_o1 * (1 – a_o1)   ---- y  
∂o1/∂w5 = ∂(w5 * a_h1+w6 * a_h2)/ ∂w5 = a_h1  ---- z  
Substituting x, y and z in (1)  
***∂E_T/∂w5 = (a_o1 – t1) * (a_o1 * (1 – a_o1)) * (a_h1)***  
Similarly -  
2.	***∂E_T/∂w6 = (a_o1 – t1) * (a_o1 * (1 – a_o1)) * (a_h2)***  
3.	***∂E_T/∂w7 = (a_o2 – t2) * (a_o2 * (1 – a_o2)) * (a_h2)***  
4.	***∂E_T/∂w8 = (a_o2 – t2) * (a_o2 * (1 – a_o2)) * (a_h1)***  
5.	∂E_T/∂a_h1 = ∂(E1+E2)/∂a_h1 = ∂E1/∂a_h1 + ∂E2/∂a_h1  ---- (1)  
∂E1/∂a_h1 = ∂E1/∂a_o1 * ∂a_o1/∂o1 * ∂o1/∂a_h1  ----l  
∂E1/∂a_o1 = a_o1 – t1   ---- m  
∂a_o1/∂o1 = a_o1 * (1 – a_o1)   ---- n  
∂o1/∂a_h1 = ∂(w5 * a_h1+w6 * a_h2) /∂a_h1 = w5   ----o  
Substituting m, n, o in l  
∂E1/∂a_h1 = (a_o1 – t1) * (a_o1 * (1 – a_o1)) * w5 --- x  
Similarly,  
∂E2/∂a_h1 = (a_o2 – t2) * (a_o2 * (1 – a_o2)) * w7  ---- y  
Substituting x, y in (1)  
***∂E_T/∂a_h1 = (a_o1 – t1) * (a_o1 * (1 – a_o1)) * w5 + (a_o2 – t2) * (a_o2 * (1 – a_o2)) * w7***  
6.	***∂E_T/∂a_h2 = (a_o2 – t2) * (a_o2 * (1 – a_o2)) * w8 + (a_o1 – t1) * (a_o1 * (1 – a_o1)) * w6***  
7.	∂E_T/∂w1 = ∂E_T/∂a_h1 * ∂a_h1/∂h1 * ∂h1/∂w1 ---- (1)  
∂a_h1/∂h1 = a_h1 * ( 1 – a_h1)  -----x  
∂h1/∂w1 = i1 ---- y  
Substituting x, y in (1)  
∂E_T/∂w1 = ((a_o1 – t1) * (a_o1 * (1 – a_o1)) * w5 + (a_o2 – t2) * (a_o2 * (1 – a_o2)) * w7) *   (a_h1 * ( 1 – a_h1)  ) * i1  
Or  
***∂E_T/∂w1 = ∂E_T/∂a_h1 * (a_h1 * ( 1 – a_h1)  ) * i1***    
Similarly,  
8.	***∂E_T/∂w2 = ∂E_T/∂a_h1 * (a_h1 * ( 1 – a_h1)  ) * i2***      
9.	***∂E_T/∂w3 = ∂E_T/∂a_h2 * (a_h2 * ( 1 – a_h2)  ) * i1***    
10.	***∂E_T/∂w4 = ∂E_T/∂a_h2 * (a_h2 * ( 1 – a_h2)  ) * i2***    

***Show what happens to the error graph when you change the learning rate from [0.1, 0.2, 0.5, 0.8, 1.0, 2.0]***  

## Solution:  
***Total Loss per epoch for Learning Rate = 0.1***

![alt](https://github.com/SachinDangayach/END2.0/blob/main/Session2/Images/lr_01.JPG)

***Total Loss per epoch for Learning Rate = 0.2***

![alt](https://github.com/SachinDangayach/END2.0/blob/main/Session2/Images/lr_02.JPG)

***Total Loss per epoch for Learning Rate = 0.5***

![alt](https://github.com/SachinDangayach/END2.0/blob/main/Session2/Images/LR_05.JPG)

***Total Loss per epoch for Learning Rate = 0.8***

![alt](https://github.com/SachinDangayach/END2.0/blob/main/Session2/Images/LR_08.JPG)

***Total Loss per epoch for Learning Rate = 1***

![alt](https://github.com/SachinDangayach/END2.0/blob/main/Session2/Images/LR_1.JPG)

***Total Loss per epoch for Learning Rate = 2***

![alt](https://github.com/SachinDangayach/END2.0/blob/main/Session2/Images/LR_2.JPG)
