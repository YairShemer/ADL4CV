# Advanced Deep Learning for Computer vision (ADL4CV)

## Links:
* Course site: [https://dvl.in.tum.de/teaching/adl4cv-ss20/](https://dvl.in.tum.de/teaching/adl4cv-ss20/)
* Lectures videos: [https://www.youtube.com/playlist?list=PLog3nOPCjKBnjhuHMIXu4ISE4Z4f2jm39](https://www.youtube.com/playlist?list=PLog3nOPCjKBnjhuHMIXu4ISE4Z4f2jm39)
* Slides: [https://dvl.in.tum.de/slides/adl4cv-ss20/](https://dvl.in.tum.de/slides/adl4cv-ss20/)

## 1. [Visualization and Interpretability](https://www.youtube.com/watch?v=4M-kuW2huqU&list=PLog3nOPCjKBnjhuHMIXu4ISE4Z4f2jm39&index=2)
### Lecture outline
Four visualization tools:
* The occlusion experiment - output an importance score for each pixel of the input image by measuring the effect of an occlusion around the pixel.
* Present images patches that maximize a specific filter response.
* DeconvNet - Forward an image, zero out all filters part of a specific filter, and then apply the opposite operations.
* Gradient ascent - optimize over the input image to maximize a specific class score.

### Discussion
* It can be relevant for object detection task if apply classification setting on our objects.
* Checking classification results on objects can be useful for getting a performance bound and for training the backbone.

## 2. [Similarity Learning](https://www.youtube.com/watch?v=6e65XfwmIWE&list=PLog3nOPCjKBnjhuHMIXu4ISE4Z4f2jm39&index=3)
### Lecture outline
* Train siames network (with shared weights) and then measure the distance between features.
* Train on positive pairs and negative pairs.
* Training with triplet loss is usfull. Especially when using hard examples.
* An advntage of similarity learning over classification - don't need to train for every new calss.
* Usefull for manyy computer vision tasks. E.g. image ilignment, object recognition and object tracking.

## 3. [Auto Encoders and VAE](https://www.youtube.com/watch?v=kdVSCtgHGF8&list=PLog3nOPCjKBnjhuHMIXu4ISE4Z4f2jm39&index=4)
### Lecture outline
* Auto-Encoders (AE) - A convolutional neural network (CNN) composed of: 
  * Encoder which produces low dimensional representation of the data.  
    Architecture is similar to classification CNNs, e.g. Resnet.
  * Decoder which tries to reproduce the input  
    Built of blocks of up-sampling layers (for rough reconstruction) followed by convolutional layers (for improved reconstruction).
* 3 methods of up-sampling:
  * Simple up-sampling, corresponds to padding by zeros.
  * Interpolation, e.g. nearest-neighbor, bilinear, bicubic.
  * Deconvolution: save max pooled index location and use them for precise up-sampling. Good for precise boundaries estimation.
* UNET
  * AE with skip connections between corresponding encoder and decoder parts.
  * The skip connections help to combine low level details that were lost in the compressing process, with the high level represtation extracted by the encoder.
  * Feature combination is done by simple concatenation.
* Computer vision applications examples:
  * Unsupervised learning of data structure for good weights initialization.
  * Prediction of pixel-wise values, such as semantic segmentation or depth.
  * Super-resolution.
* Variational Auto Encoder (VAE)
  * Main idea: learn probability distribution by the encoder, sample from it, and reconstruct sample using the decoder
* Application - style transfer
  * Content loss: minimaize *features* distance between original and generated images.
  * Style loss: minimaize *Gram (inner product) Matrix* distance between original and generated images.

## 4. [Graph Neural Networks and Attention](https://www.youtube.com/watch?v=FbkE7FsHDkc&list=PLog3nOPCjKBnjhuHMIXu4ISE4Z4f2jm39&index=5)
### Lecture outline
* Introduction
  * So far we dealt with images, which are structured in a *regular* grid formation. We used *regular* convolution kernels to learn and reperesent this kind of data.
  * In this lecture we introduce ways of working with *irregular* data, such as point clouds and graphs.
  * Example for new data domain - point cloud:
    * Rich information: each points can have multiple attributes, such as 3D location, RGB, semantic, etc.
    * Permutation invariance: point order does not matter. E.g., we'd like to correctly classify a rabbit's point cloud if we start traveling it from it's head or it's tail.
    * Transformation invariance: E.g., we'd like to correctly classify a rabbit's point cloud for different rotations of the point cloud.
* Graph neural networks (GNN)
  * Simply stated, graph is a data structure composed of nodes (data points) and edges (connections between data points) - each of which is represented by a vector.
  * Key challanges when working with graphs:
    * Variable sized inputs: the size of the graph (nodes and edges) can vary.
    * Need invariance to nodes permutations - nodes in different locations on the graph should be treated the same way.
  * Main idea: iteratively update graph reperensetation using information propogation steps.  
  * Single information propogation step is usually composed of:
    * Each node (and possibly also edge) gather information of it's neigboor nodes. This updtated node representation (embedding) is used to represent this node (or edge) from now on.
    * The information gathering is done using a learnable function, which combines data embeddings from near nodes and edges.
    * After L steps each node has gathered information from nodes up to L degrees of separation from it. This volume of awareness can be thought of the node's *receptive field*.
    * An information propogation step can be thought of the as the GNN counterpart of a layer in a CNN.
  * Dealing with varible sized input is done using aggregation of data from neigboor nodes in a way that is invariant to the number of those nodes (e.g. using sum, mean and max operation).
  * Invariance to nodes permutation is achived by treating local environments in differenct location on the graph in the same way (e.g. with the same learnable function).
* Applications:
  * Tracking obejcts in Videos - *interesting, should add short explaination*
  * Video object sigmentation: the main idea is to model temporal consistency through a GNN.    

Attention:
* Mechanism that give more emphasis (i.e. assigning different weight) to some parts of the data, e.g. words in a sentence or locations on an image.
* Firstly introduced in the field of machine translation, in order to help the forgetness problem in long sentences.
* **Transformer** - an important variant of attetion, which uses *only* attention for NLP problems.
  * Simply speaking, every word is connected to all the other words by attention weights.
  * Can be viewed as a graph, where words are represented by nodes and attention weights by edges.
  * More details can be found in the original paper *[Attention Is All You Need](https://arxiv.org/pdf/1706.03762.pdf)*
* Soft vs. hard attention:
  * Soft attention: weighted sum of the (normalized) attention weights. Deterministic, gradients are easily computed. *most commonly used*.
  * Hard attention: (normalized) attention weights are treated as probability distribution, from which 1 value is sampled. Stochastic, gradients are *estimated* through Monte Carlo experiments.
* Image captioning is an example for computer vision application which uses attention.
