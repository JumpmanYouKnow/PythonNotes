---
title: "ML-DL Notes"
date: 2018-09-08
---

Notes for machine learning and deep learning models, design and training techniques
Mainly includes: CNN, RNN(LTSM)  
ensemble techniques  
activation functions  

### 1. deep learning concept
#### 1. LTSM,
a type of RNN, most successful RNNs are LTSM RNNs  
1. use a vector as cell state to record state  
2. use three gates to erase, update, output the cell state.  
  
Example: Rakuten data challenge  
Character-level tokenization  
Ensembling:  
Bidirectional training 

#### 2. Ensemble learning
1. Bagging(bootstrap aggregating):
randomly select N training sets, then vote  
example: random forest

2. Boosting
try to learn from a bunch of weak models, to learn from mistakes
example: gradient boosting, gradient boosting decistion tree

3. model stacking
training different models first, then stack them together (with different weights)


#### 3. Activation functions 
https://towardsdatascience.com/activation-functions-neural-networks-1cbd9f8d91d6
Sigmoid, R:(0,1)
Tanh, R:(-1, 1)
ReLu, y=max(0,x) R:(0, z), f(z) = 0 if z <= 0, otherwise z = z (most used, used in almost all teh convolutional neural networks)
Leaky ReLu: solve ReLu's range problem
Softplus, y=log(1+ex)
Softmax

### 2. deep learning packages:
Keras:

TensorFlow:


#### 4. Other models to be learned
Siamese network
triplet loss neural network



> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTM5NzExNzQ2OV19
-->