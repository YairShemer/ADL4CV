# Advanced Deep Learning for Computer vision (ADL4CV)

## Links:
* Course site: [https://dvl.in.tum.de/teaching/adl4cv-ss20/](https://dvl.in.tum.de/teaching/adl4cv-ss20/)
* Lectures videos: [https://www.youtube.com/playlist?list=PLog3nOPCjKBnjhuHMIXu4ISE4Z4f2jm39](https://www.youtube.com/playlist?list=PLog3nOPCjKBnjhuHMIXu4ISE4Z4f2jm39)
* Slides: [https://dvl.in.tum.de/slides/adl4cv-ss20/](https://dvl.in.tum.de/slides/adl4cv-ss20/)

## 1. Visualization and Interpretability
### Lecture outline
Four visualization tools:
* The occlusion experiment - output an importance score for each pixel of the input image by measuring the effect of an occlusion around the pixel.
* Present images patches that maximize a specific filter response.
* DeconvNet - Forward an image, zero out all filters part of a specific filter, and then apply the opposite operations.
* Gradient ascent - optimize over the input image to maximize a specific class score.

### Discusion
* It can be relevant for object detection task if apply classification setting on our objects.
* Checking classification results on objects can be useful for getting a performance bound and for training the backbone.

## 2. Similarity Learning
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
  
