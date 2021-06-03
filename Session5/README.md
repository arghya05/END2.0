
### Submission by:
1. Sachin Dangayach (sachin.dangayach@gmail.com)

***[Link for colab file](https://colab.research.google.com/drive/13-mpSe80XXG69Pz3y1SOP7HQmekAyggw?usp=sharing)***

# Objective

We aim to build a network that would:

1) Download the StanfordSentimentAnalysis Dataset. This dataset contains just over 10,000 pieces of Stanford data from HTML files of Rotten Tomatoes. The sentiments are rated between 1 and 5, where one is the most negative and 5 is the most positive.

2) Use "Back Translate", "random_swap", random_insert and "random_delete" to augment the data you are training on.

3) Train your model and achieve 60%+ validation/text accuracy. Upload your collab file on GitHub with readme that contains details about your assignment/word (minimum 250 words), training logs showing final validation accuracy, and outcomes for 10 example inputs from the test/validation data.


# Data

- StanfordSentimentAnalysis is a popular dataset used for benchmarking NLP related models. It comprises of movies reviews and sentiments associated with reviews manually labeled for nearly 25 classes. We decided to go for total five labels ["very negative", "negative", "neutral", "positive", "very positive"].
- Dataset has got train, test split of (8544, 2210). On exploring the dataset, it was found to be imbalanced dataset.



# The Network / Model - Architecture

The network we decided to build is designed as follows:
1. Two convolutions with pooling applied to feature map
2. Dropout layer
3. Six fully connected layers leading to the two outputs - recognized digit & addition result

Design choices we made while building the network:
1. The network would have 2 main components:
  a. For digit recognition
  b. For adding the digit to the random number
2. Once we have the output from component (a), we would concatenate the one-hot encoded random number to the output
3. The final output would contain:
  a. A vector of 10 number giving the probabilities of the image being 0 to 9
  b. A vector of 19 numbers giving the probabilities of the addition being 0 to 18


The summary of the network looks like this:  
![Model Summary](https://github.com/SachinDangayach/END2.0/blob/main/Session3/images/Model%20Parameters.jpg)



# The Network / Model - Loss Function

We went ahead with the Negative Log Likelihood loss as that is known to give good results for comparing outputs for classification problems like this one.

Yes, we set it up as a classification problem mainly because:
  a. Digit recognition is involved
  b. The summations are constrained within the range of 0 to 18, with the input combinations being finite



# The training

Inspired by YOLO, we wanted to train the network for digit recognition for the first few epochs and then
after it achieves certain level of accuracy, train it for the addition / summation objective

### ACCURACY ACHIEVED - 97.75%
To our surprise, the network does not take more than a few epochs to achieve an ~ 98% accuracy

Here are the loss and accuracy charts from training the network:


Training Logs  
![Training Logs Screenshot](https://github.com/sairamsubramaniam/tsai_nlp/blob/master/end_course_v2/3_nn_practice/images/training_logs.png)


Training Loss By Epochs  
![Chart - Training Losses by Epochs](https://github.com/SachinDangayach/END2.0/blob/main/Session3/images/training_loss_by_epochs.png)


Digit Recognition Accuracy By Epochs  
![Chart - Digit Recognition Accuracy by Epochs](https://github.com/SachinDangayach/END2.0/blob/main/Session3/images/test_acc_by_epochs_dra.png)


Addition Accuracy By Epochs  
![Chart - Addition Accuracy by Epochs](https://github.com/SachinDangayach/END2.0/blob/main/Session3/images/test_acc_by_epochs_aa.png)


Training Loss By Batch Iterations  
![Chart - Training Losses by Epochs](https://github.com/SachinDangayach/END2.0/blob/main/Session3/images/training_loss_by_batch_iterations.png)
