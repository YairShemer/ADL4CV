# Advanced Deep Learning for Computer vision (ADL4CV)

## Links:
* Course site: [https://dvl.in.tum.de/teaching/adl4cv-ss20/](https://dvl.in.tum.de/teaching/adl4cv-ss20/)
* Lectures videos: [https://www.youtube.com/playlist?list=PLog3nOPCjKBnjhuHMIXu4ISE4Z4f2jm39](https://www.youtube.com/playlist?list=PLog3nOPCjKBnjhuHMIXu4ISE4Z4f2jm39)
* Slides: [https://dvl.in.tum.de/slides/adl4cv-ss20/](https://dvl.in.tum.de/slides/adl4cv-ss20/)

## 1. Visualization and Interpretability
### Lecture outlines
Four visualization tools:
* The occlusion experiment - output an importance score for each pixel of the input image by measuring the effect of an occlusion around the pixel.
* Present images patches that maximize a specific filter response.
* DeconvNet - Forward an image, zero out all filters part of a specific filter, and then apply the opposite operations.
* Gradient ascent - optimize over the input image to maximize a specific class score.

### Discusion
* It can be relevant for object detection task if apply classification setting on our objects.
* Checking classification results on objects can be useful for getting a performance bound and for training the backbone.
