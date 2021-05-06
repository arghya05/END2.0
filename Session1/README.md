# END2 Session 1 Assignment by Sachin Dangayach

## Background & Very Basics

**Assignment**:
### 1. Rewrite the Colab file and:
  - remove the last activation function
  - make sure there are in total 44 parameters
  - run it for 2001 epochs
### 2. You must upload your assignment to a public GitHub Repository and share the link as the submission to this assignment

## Solution:

**[Link to cloab file](https://colab.research.google.com/drive/1yQxqQXFwAdbpG_T6V-uazKC0T2WOP-7V)**

**[Link to file in git](https://github.com/SachinDangayach/END2.0/blob/main/Session1/END2_0_Session_1.ipynb)**

### 3. Add a readme file to your project and describe these things:
  - What is a neural network neuron?
  - Ans: Within an artificial neural network, a neuron is a mathematical function that model the functioning of a biological neuron.
    Typically, a neuron compute the weighted average of its input, and this sum is passed through a nonlinear function, often called activation function, such as the sigmoid.
    [neuron in a neural network](https://i.stack.imgur.com/wXL9A.png)
  - What is the use of the learning rate?
  - Ans: To reduce the training loss while training a neural network, we need to adjust the weights and for this we use SGD. The new value of weight is derived by subtracting the gradient of loss wrt weight multiplied by learning rate from old weight. Right choice of LR needed as if we chose higher values, we might get new weight values ocsillating around local minima and if we chose very small value for LR, it will  take long time before we reach the local minima resulting the optimal weight for lesser loss.
  [learning Rate](https://www.fromthegenesis.com/wp-content/uploads/2020/04/lr_12420_1-1024x384.png)
  - How are weights initialized?
  - Ans:
  - What is "loss" in a neural network?
  - Ans:
  - What is the "chain rule" in gradient flow
  - Ans:
