VNU - University of Science

21TGMT - Image & Video Processing

21KHMT - Parallel Programming

## Summary

This repository is for storing lab and project works for two subjects. More details below:

### Lab

Located in /lab. This is the labwork for Image & Video Processing, consisting of 3 labs as follows:

1. Train and evaluate a CNN on three basic datasets, all given by PyTorch library.

2. Train or use YOLOv8 to detect objects on any video or image.

3. Fine-tune a Stable Diffusion model using LoRA technique on Google's DreamBooth dataset.

Full work has been done using Google's Colab Notebook and the provided T4 GPU, is reported by /lab/lab.pdf.

##### Work summary

Lab 1: We trained a Darknet53 model (by Joseph Redmon, pjreddie.com) on and evaluated on the three datasets. 

The model beats MNIST dataset easily but performs very poorly on FashionMNIST due to dataset complexity and poor data depth (3 vs. 1 channel of images) to make good use of a CNN model that is not supported by any kind of edge detection or related techniques.

Lab 2: We implemented YOLOv8 (by ultralytics) to detect objects in a video.

We have the model's simplicity making it useful and quick in object detection, which is a staple of CNN-based models. However, related weaknesses persist, including its low accuracy on smaller objects in the image, as well as poor precision in object classification. 

Furthermore, as a suggestion, using information relations between consecutive frames is proven to boost object classification accuracy, which YOLOv8 is used for object detection and outputs bounding boxes in order to be used by video object classification models like LSTM.

Lab 3: We fine-tuned Stable Diffusion 1.5 model (from Diffusers library, by runwayml) using LoRA technique (from PEFT library and API) on Google's DreamBooth dataset. The training process has UNet and variational autoencoder (VAE) encoder fine-tuned using Adam optimizer. 

The given results were actually quite poor expectedly, because we were supposed to fine-tune only UNet, while freezing VAE in order to keep the definitions of trained latents, destabilizing training. OOPS!

### Project

Located in /project. This project was meant to be submitted to both subjects as they shared topics, although requiring different goals. Unfortunately, we ran out of time and forfeited the project. But we still chose to keep it here and the following shall explain the legacy code:

##### Goal

We intended to replicate Unsafe-Net, an object detection and classification model for workplace safety violations, from scratch, consisting of a YOLOv4 base followed by LSTM with convolution variant.

##### Architecture

Our architecture consists of 3 main layers for multiple requirements from the two subjects:

- Function Manager (design patterns: Singleton, Factory Method, Decorator): a singleton object in order to implement different versions of low-level calculation functions (mainly between CPU, Numba-jit and Numba-CUDA GPU versions), used to track the total amount of time it takes to execute in training, in order to plan ahead for what should be optimized through parallel programming.

- Layer (design patterns: Composition, Abstract Pattern): which is the basis for other related classes, such as Convolution, Residual Blocks,  Pooling, etc. and to ensure a class of such can stack inside another (in YOLOv4: Residual Block contains 2 Convolution layers).

- Unsafe-Net: implementation of the whole project.

##### Repository

The main repository consists of two folders inside /proj:

- /papers: Research papers that assist in this project and related knowledge.

- /src: Implemented code of the project
  
  - /CSPDarknet53: Dummy implementation of CSP-enhanced Darknet53, used in YOLOv4.
  
  - /legacy: Abandoned code files, saved for possible future reuse.
  
  - /FunctionManager.ipynb: Function Manager.
  
  - /Functions_and_classes.ipynb: Implementation of the rest, currently available for only CPU calculations.

##### Results

The project has been officially abandoned on August 11th, after 5 weeks and ~120 man-hours, with 2 weeks remaining, due to insufficient amount of time and to focus on other tasks at the time.


