# Interpretable Pruning of CNNs for Scale-Covariant Features in Medical Imaging

This repository contains the code to implement layer pruning for preserving scale-covariant features during transfer laerning from ImageNet pretrained CNNs to another dataset. We use the deep learning interpretability approach of Regression Concept Vectors to analyze the layer-wise encoding of scale information in standard CNNs pre-trained on ImageNet. We show that pruning a pre-trained CNN to retain features that contain most scale information markedly improves the performance on a task of magnification prediction in histopathology images. 


<p align="center">
    <img src="results/arch.png" width=700px>
</p>

Image scale carries crucial information in medical imaging, e.g. the size and spatial frequency of local structures, lesions, tumors and cell nuclei.
With feature transfer being a common practice, scale-invariant features implicitly learned from pretraining on ImageNet tend to be preferred over scale-covariant features. The pruning strategy in this paper proposes a way to maintain scale covariance in the transferred features.

We propose to use deep learning interpretability with Regression Concept Vectors to analyze the layer-wise encoding of scale information for popular architectures such as InceptionV3 and ResNet50. The evaluation of the regression vectors with R2 is used to quantify information about scale at each layer.
We then prune off the layer where invariance to scale is learned and show that the pruned networks improve the transfer to the task in medical imaging of predicting the nuclei area and image magnification of breast histopathology images. 

## Dataset 
We use the albatross, kite and car classes from the ImageNet dataset. 
For the histopathology application, we use

## Preview of the results
We show in the following the performance of the RCVs for scale at different layers of the network, averaged over 10 repetitions and over the 3 classes. Interestingly, the covariance of scale peaks at central layers and decreases close to softmax.

<p align="center">
    <img src="results/performance0.png" width=350>
</p>

## Network pruning and transfer to histopathology
We pruned off the deep layers where scale invariance is learned (mixed 9 and 10 for Inception, for example). There are clear gains given by the pruning on the medical imaging task. 

<p align="center">
    <img src="results/table.png" width=700px>
</p>
