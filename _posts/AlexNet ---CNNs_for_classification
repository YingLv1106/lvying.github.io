---
title: AlexNet
date: 2019-05-14 14:00:22
tags: CNNs_for_classification
categories: 
- CNNs_for_classification
---

paper: [ImageNet Classification with Deep Convolutional Neural Networks](https://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks.pdf)

We need large dataset to solve complex recognition tasks, and we need a model with a large learning capacity. Beside, model needs to have a generalization performance, not just perform well in a single dataset. Let's start our CNN tour here.

### **Contributions**
1. large cnn used in the ILSVRC-2010 and ILSVRC-2012
2. highly-optimized GPU implementation of 2D convolution and all the other operations inherent in training CNN
3. features which improve CNN's performance and reduce its training time
4. techniques for preventing overfitting

### **Pre-proccessing**
1. image's shorter side rescale to 256, then crop out the central 256x256 patch
2.  subtract the mean activity over the training set from each pixel

### **Architecture**
<div align="center">
<img src="https://saveimages.oss-cn-hangzhou.aliyuncs.com/CNNs_for_image_classification/AlexNet/AlexNet.jpg" height="80%" width="80%">
</div>
5 convolutional and 3 fc. LRN is used after the first and second convolutional layers.  

### **Features with the most important first**
1. **ReLU**: make learning faster
2. Multi GPUs training
    - one GPU's(GTX 580) memory is not enough for training 1.2 million examples
    - GPUs are able to read from and write to one another's memory directly without going through host machine memory
    - trains faster than one-GPU net and reduces top-1 and top-5 error rates by 1.7% and 1.2%
3. LRN(Local Response Normalization), while we do not use anymore, reduces top-1 and top-5 error rates by1.4% and 1.2%
4. overlapping pooling: use MaxPooling (kernel_size=3,stride=2), reduces top-1 and top-5 error rates by 0.4%and 0.3%

### **Reducing Overfitting**
1. Data augmentation
    * at train time, random crop 224x224 + horizontal reflections; at test time, crop 4 corner and 1 center patches (x5) and their horizontal reflections (x2), then average the predictions made by the network's softmax layer on the ten patches.
    * [Fancy PCA](https://deshanadesai.github.io/notes/Fancy-PCA-with-Scikit-Image), this scheme reduces the top-1 error rate by 1%
2. Dropout

### **Training Details**
1. optimizer: SGD with momentum=0.9 and weight decay=0.0005
   <div align="center"><img src="https://saveimages.oss-cn-hangzhou.aliyuncs.com/CNNs_for_image_classification/AlexNet/optimizer.jpg" height="40%" width="40%"></div>
2. initialize: a zero-mean Gaussian distribution with std=0.01, neuron biases in the second, fourth, fifth convolutional layers and fc layers with the constant 1
3. learning rate: use an equal learning rate for all layers, and divide the learning rate by 10 when validation error rate stops improving with the current lr

### **Discussion**
Depth really is important for achieving the results, the AlexNet's performance degrades if a single convolutional layers is removed.
