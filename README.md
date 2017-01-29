# Behavioral-Cloning-P3 - Deep Learning
##Self-Driving Car Nanodegree

### Overview
The objective of this project is to clone human driving behavior by use of Convolutional Neural Network using Keras. In order to achieve this, we are going to use a udacity designed Car Simulator. During the training session, we will navigate our car inside the simulator using the keyboard or a gamepad (joystick such as PS3 or Xbox controller). While we navigating the car the simulator records training images and respective steering angles. Then we use those recorded data to train our neural network. It uses the trained model to predict steering angles for a car in the simulator given a frame from central camera.

### Dependencies

This project requires **Python 3.5** and the following Python libraries installed:
- [OpenCV2] (http://opencv.org/) - https://anaconda.org/menpo/opencv
- [Keras](https://keras.io/) - https://anaconda.org/anaconda/keras
- [NumPy](http://www.numpy.org/) - https://anaconda.org/anaconda/numpy
- [Scikit-learn](http://scikit-learn.org/) -https://anaconda.org/anaconda/scikit-learn
- [Tensorflow](https://www.tensorflow.org/)

### Files in this repo
- model.py - The script used to build and train the model.
- drive.py - The script to drive the car.
- model.json - The model architecture.
- model.h5 - The model weights.
- model-test1.json model-test1.h5 - 4 Diffrent test might fail in some place while driving (These are actually genrated while experimenting with the model

### Stimulator

You can download the stimulator at https://d17h27t6h515a5.cloudfront.net/topher/2016/November/5831f3a4_simulator-windows-64/simulator-windows-64.zip

### How to Generate Model

You can set the folder path at line 17 in model.py make sure that your folder contains \IMG\ (generated images) folder and a csv (driving data)
- `data_dirs = ['folder_name']`

##My driving data
test1 - https://drive.google.com/file/d/0Bw2un6-T5az-V3gzZzlONG14dXM/view?usp=sharing
test2 - https://drive.google.com/file/d/0Bw2un6-T5az-VTU1WENaS1BJRlE/view?usp=sharing
test3 - https://drive.google.com/file/d/0Bw2un6-T5az-QktxMTEtZko4MTA/view?usp=sharing
test4 - https://drive.google.com/file/d/0Bw2un6-T5az-R3JxQ1lFUDlQRzQ/view?usp=sharing
Udacity test set - https://d17h27t6h515a5.cloudfront.net/topher/2016/December/584f6edd_data/data.zip

### How to Run the Model

You can clone the repo and run the drive.py file with the stimulator in Autonomous mode.
- `python drive.py model.json`

