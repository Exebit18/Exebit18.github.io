---
layout : post
title : 'Deep Learning: Introduction'
category : ['Deep Learning',]
---


Deep learning has become an ubiquitous tool in the Machine Learning community. Today a lot of smart and intelligent applications such as self-driving cars, games engines such as Alpha-Go, face-detection & identification etc all use deep learning to achieve superhuman performance.   This technology works by arranging units called neurons in layers. Each layer takes input from the previous layer, applies some transformations on that input and feeds it to the next layer. In this post, we will cover the basics principles behind deep learning and also take a hands-on approach to write some code to classify handwritten digits.



## Biological Neuron

The human brain is essentially a network of billions of neurons that are interconnected in a complex network. A neuron is the basic functional unit of the brain. Each neuron takes inputs, in the form of electrical signals, from other neurons through the synaptic connections to the dendrites. The body of the neuron cell performs some operation (usually a simple aggregation) on these received inputs and outputs the result through the axon in form of an activation (through a spiking in potential) of the neuron. The outline of the neuron is shown below:  



![Biological neuron]({{"/images/bioneuron.jpg"}})



## Artificial Neuron

In 1943, Mcculloch and Pitts proposed a mathematical functional unit which was loosely inspired from the above neural structure. The artificial neuron was intended to be an approximation to the biological neuron. An artificial neuron takes m inputs and outputs a boolean value. Output 1 corresponds to an activation in the neuron and 0 corresponds to no activation. The unit can be mathematically represented as a weighted sum of the inputs, followed by a threshold function:

<p style="text-align: center;">
<img src="/images/signum.jpg" align="center">
</p>



![Artificial neuron]({{"/images/artificialneuron.jpg"}})



Note that using the threshold unit makes the the effective function computed non-differentiable. We need differentiable functions ideally, as they have some important properties (out of the scope of this blog) for optimising. Hence we use a simple fix. We employ a soft thresholds such as tanh or sigmoid functions which look as follows.

<p>
<img src="/images/plot2.jpg" width="300"/> <img src="/images/plot1.jpg" width="300"/>
</p>



## Artificial Neural Network

So far, we have seen how an artificial neuron works. But one neuron on it’s own is pretty limited when it comes to hard tasks like image classification etc. This is achieved by stacking these neurons in layers. The output of one layer of neurons acts as the input to the next layer, just like our brain (loosely speaking).



![Artificial neural network]({{"/images/neuralnetwork.jpg"}})



The network consists of an input layer which takes the input data, an output layer which returns the result of our algorithm, and an arbitrary number of intermediate layers called the hidden layers. Essentially, the network applies a series of transformations to the input and returns the final output. The number of neurons in the input layer is decided by the size of the input. The more number of hidden layers we have, the deeper the network. Typically using one hidden layer is sufficient for most tasks and having more will lead to a problem called over-fitting.

The structure of the final layer depends on the task at hand. In our example, we want to classify handwritten digits. There are a total of 10 digits possible: 0-9. Hence our output layer is has 10 neurons each corresponding to a digit. Each output neuron must represent the probability that the given image corresponds to that digit. Since they represent probabilities, the sum of the outputs of these neurons must be 1. This condition is imposed by using something called the softmax function (which is also differentiable).  The network is trained via a number of runs on the train data. Each run over the entire data is called an epoch. At each training instant, we batch K datapoints together for faster convergence. This is called batch size.




## Training

Remember that each neuron has a set of weights corresponding to its inputs (refer the artificial neuron diagram). These weights form an important part of the whole algorithm. If we have random weights, we are essentially computing random functions on the input which is useless. The weights have to be carefully tuned so as to achieve a desired outcome. This process is called training of the network.

During training, we take some labelled data (input x and output y). We pass the training data x to the network. We adjust the weights such that the output of the network is close to the true output y. For example, we can pass a handwritten digit of 5 to the network and make adjust weights so as to make the output of the 5th neuron 1 and all others 0. This adjustment is made by an algorithm called Back-Propagation.

Training the network using many such training examples, gives us the values of the weights of the network. Once training is completed, the network must be evaluated on test data which is not included in the training. If the network gives good performance on the test data,  it can be deployed to make real world predictions.



## Code

We now write some code in python to train our very own neural network! The task is to classify a given 28*28 images of handwritten digits into one of 10 classes. We will use a library called keras for this tutorial. For installation see this. Experiment with the hidden layer size, number of epochs and batch size.

```python
import numpy
from keras.datasets import mnist
from keras.models import Sequential
from keras.layers import Dense

# Load the MNIST data
(XTrain, YTrain), (XTest, YTest) = mnist.load_data()

# Convert 28*28 images into a 784 sized vector and normalize to 0-1 scale
XTrain = XTrain.reshape(XTrain.shape[0],784).astype('float32')/255
XTest = XTest.reshape(XTest.shape[0], 784).astype('float32')/255


# one hot encode outputs
YTrain = np_utils.to_categorical(YTrain)
YTest = np_utils.to_categorical(YTest)

model = Sequential()
# Adds one dense layer connection to input
# Hidden layer has 392 neurons.
model.add(Dense(392, input_dim=784, kernel_initializer='normal', activation='relu'))
model.add(Dense(10, kernel_initializer='normal', activation='softmax'))
# Compile model
model.compile(loss='categorical_crossentropy', optimizer='adam', metrics=['accuracy'])


model.fit(XTrain, YTrain, validation_data=(XTest, YTest), epochs=10, batch_size=200, verbose=2)
# Check for accuracy
scores = model.evaluate(XTest, YTest, verbose=0)
print("Accuracy: %.2f%%" % (scores[1]*100))
```



## Further References:
1. MOOC : [click here](https://www.coursera.org/specializations/deep-learning)
2. For latest research in deep learning: [click here](http://deeplearning.net/)
