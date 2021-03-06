# Behavioral-Cloning- P3
## Self-Driving Car Nanodegree

[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)


### Overview
The objective of this project is to clone human driving behavior by use of Convolutional Neural Network using Keras. In order to achieve this, we are going to use a udacity designed Car Simulator. During the training session, we will navigate our car inside the simulator using the keyboard or a gamepad (joystick such as PS3 or Xbox controller). While we navigating the car the simulator records training images and respective steering angles. Then we use those recorded data to train our neural network. It uses the trained model to predict steering angles for a car in the simulator given a frame from the central camera.

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

## Implementation

### How to Generate Model

You can set the folder path at line 17 in model.py make sure that your folder contains \IMG\ (generated images) folder and a csv (driving data)
- `data_dirs = ['folder_name']`

### My driving data

test1 - https://drive.google.com/file/d/0Bw2un6-T5az-V3gzZzlONG14dXM/view?usp=sharing <br>
test2 - https://drive.google.com/file/d/0Bw2un6-T5az-VTU1WENaS1BJRlE/view?usp=sharing <br>
test3 - https://drive.google.com/file/d/0Bw2un6-T5az-QktxMTEtZko4MTA/view?usp=sharing <br>
test4 - https://drive.google.com/file/d/0Bw2un6-T5az-R3JxQ1lFUDlQRzQ/view?usp=sharing <br>
Udacity test set - https://d17h27t6h515a5.cloudfront.net/topher/2016/December/584f6edd_data/data.zip <br>

### How to Run the Model

You can clone the repo and run the drive.py file with the stimulator in Autonomous mode.
- `python drive.py model.json`

## Network Architecture
The network consists of three convolutional layers. The layers are increasing in depth decreasing in size. There are three fully connected layers Dropout is employed between the fully connected layers and activation function is relu. <br>
Here is the network architecture as shown by keras

<table style="width: 42px;">
<tbody>
<tr style="height: 42px;">
<th style="width: 10px; height: 42px;">Layer (type)&nbsp;&nbsp;</th>
<th style="width: 10px; height: 42px;">&nbsp;Output Shape</th>
<th style="width: 10.2px; height: 42px;">Param #&nbsp;</th>
<th style="width: 10px; height: 42px;">&nbsp;Connected to</th>
</tr>
<tr style="height: 62px;">
<td style="width: 10px; height: 62px;">&nbsp;convolution2d_1 (Convolution2D)</td>
<td style="width: 10px; height: 62px;">&nbsp;(None, 40, 80, 32)</td>
<td style="width: 10.2px; height: 62px;">&nbsp;320</td>
<td style="width: 10px; height: 62px;">convolution2d_input_1[0][0]</td>
</tr>
<tr style="height: 42px;">
<td style="width: 10px; height: 42px;">&nbsp;maxpooling2d_1 (MaxPooling2D)</td>
<td style="width: 10px; height: 42px;">&nbsp;(None, 20, 40, 32)</td>
<td style="width: 10.2px; height: 42px;">&nbsp;0</td>
<td style="width: 10px; height: 42px;">convolution2d_1[0][0]</td>
</tr>
<tr style="height: 42px;">
<td style="width: 10px; height: 42px;">&nbsp;convolution2d_2 (Convolution2D)&nbsp;</td>
<td style="width: 10px; height: 42px;">&nbsp;(None, 10, 20, 64)</td>
<td style="width: 10.2px; height: 42px;">18496&nbsp;</td>
<td style="width: 10px; height: 42px;">maxpooling2d_1[0][0]</td>
</tr>
<tr style="height: 42px;">
<td style="width: 10px; height: 42px;">&nbsp;maxpooling2d_2 (MaxPooling2D)&nbsp;</td>
<td style="width: 10px; height: 42px;">&nbsp;(None, 10, 20, 64)</td>
<td style="width: 10.2px; height: 42px;">0&nbsp;</td>
<td style="width: 10px; height: 42px;">convolution2d_2[0][0]</td>
</tr>
<tr style="height: 22.4px;">
<td style="width: 10px; height: 22.4px;">&nbsp;convolution2d_3 (Convolution2D)&nbsp;</td>
<td style="width: 10px; height: 22.4px;">&nbsp;(None, 10, 20, 128)</td>
<td style="width: 10.2px; height: 22.4px;">73856&nbsp;</td>
<td style="width: 10px; height: 22.4px;">maxpooling2d_2[0][0]</td>
</tr>
<tr style="height: 22px;">
<td style="width: 10px; height: 22px;">&nbsp;maxpooling2d_3 (MaxPooling2D)</td>
<td style="width: 10px; height: 22px;">&nbsp;(None, 5, 10, 128)</td>
<td style="width: 10.2px; height: 22px;">0&nbsp;</td>
<td style="width: 10px; height: 22px;">convolution2d_3[0][0]</td>
</tr>
<tr style="height: 22px;">
<td style="width: 10px; height: 22px;">&nbsp;flatten_1 (Flatten)</td>
<td style="width: 10px; height: 22px;">(None, 6400)&nbsp;</td>
<td style="width: 10.2px; height: 22px;">0</td>
<td style="width: 10px; height: 22px;">maxpooling2d_3[0][0]</td>
</tr>
<tr style="height: 22px;">
<td style="width: 10px; height: 22px;">&nbsp;dense_1 (Dense) &nbsp;</td>
<td style="width: 10px; height: 22px;">&nbsp;(None, 500)</td>
<td style="width: 10.2px; height: 22px;">&nbsp;3200500</td>
<td style="width: 10px; height: 22px;">flatten_1[0][0]</td>
</tr>
<tr style="height: 22px;">
<td style="width: 10px; height: 22px;">&nbsp;dropout_1 (Dropout)</td>
<td style="width: 10px; height: 22px;">&nbsp;(None, 500)</td>
<td style="width: 10.2px; height: 22px;">&nbsp;0</td>
<td style="width: 10px; height: 22px;">dense_1[0][0]</td>
</tr>
<tr style="height: 22px;">
<td style="width: 10px; height: 22px;">&nbsp;dense_2 (Dense)&nbsp;</td>
<td style="width: 10px; height: 22px;">&nbsp;(None, 100)</td>
<td style="width: 10.2px; height: 22px;">50100&nbsp;</td>
<td style="width: 10px; height: 22px;">dropout_1[0][0]</td>
</tr>
<tr style="height: 22px;">
<td style="width: 10px; height: 22px;">&nbsp;dropout_2 (Dropout) &nbsp;&nbsp;</td>
<td style="width: 10px; height: 22px;">&nbsp;(None, 100)</td>
<td style="width: 10.2px; height: 22px;">0&nbsp;</td>
<td style="width: 10px; height: 22px;">dense_2[0][0]</td>
</tr>
<tr style="height: 22px;">
<td style="width: 10px; height: 22px;">dense_3 (Dense)&nbsp;</td>
<td style="width: 10px; height: 22px;">(None, 10)</td>
<td style="width: 10.2px; height: 22px;">1010</td>
<td style="width: 10px; height: 22px;">dropout_2[0][0]</td>
</tr>
<tr style="height: 22px;">
<td style="width: 10px; height: 22px;">dropout_3 (Dropout)&nbsp;</td>
<td style="width: 10px; height: 22px;">(None, 10)</td>
<td style="width: 10.2px; height: 22px;">0</td>
<td style="width: 10px; height: 22px;">dense_3[0][0]</td>
</tr>
<tr style="height: 22px;">
<td style="width: 10px; height: 22px;">dense_4 (Dense)</td>
<td style="width: 10px; height: 22px;">(None, 1)</td>
<td style="width: 10.2px; height: 22px;">11</td>
<td style="width: 10px; height: 22px;">dropout_3[0][0]</td>
</tr>
</tbody>
</table>

## Training Approach

- Choose Data
- Data Preprocessing
- Batch Generators
- Experiments
- Results

## Choose Data

test1 - #train =  5692 #val =  633 #test =  703 (Completed 10perc) <br>
test2 - #train =  12165 #val =  1352 #test =  1502 (Completed 40perc)<br>
test3 - #train =  12165 #val =  1352 #test =  1502 (Completed 80perc)<br>
test4 - #train =  3942 #val =  439 #test =  487 (Completed 20perc)<br>
udacity - #train =  6508 #val =  724 #test =  804 (Completed Successfully)<br>

## Data Preprocessing

There are three main steps to data preprocessing:
- Resizing the image from (320px, 160px) original size to (80px, 40px) using OpenCV resize method in line 54 `img = cv2.resize(img, target_shape)`.
- Color space conversion - the image is converted to HVS format and only the S channel
   is used. 
- Normalization - scaling the data to the range of 0-1

I choose only one channel (Satuation) as it might reduce the burden of proceessing and
inturn reduce the computational power reduired. Unlike others i havent cropped the images
because cropping might work here.but in case of a real time situation where there is a 
traffic sign or light overhead that might be missed. Making the model process whole of 
RGB is might again incur more processing power so RGB is converted to HSV in 
`img = cv2.cvtColor(img, cv2.COLOR_BGR2HLS)` line 55 model.py and only Satutation is
used `img = img[:,:,2]`

## Batch Generators

There are two multithreaded nested generators supporting train, val and test sets. The 
outer bach generator called threaded_generator which consists of producer and consumer
launches the inner batch generator called batch_generator in a separate thread and 
caches 10 output. 

To support three data types the batch generator accepts the batch size
a second parameter that selects the type such as train val or test.
Based on this parameter one of three csv file arrays are chosen. The arrays are
prepared earlier in the data loading phase where all the csv files are read.
It is also made to support multiple directory so different datasets could could be used.
and the rows are merged in one array. Then the array is split into parts train
test and val and assigned to different variable. This approach simplifies data
shuffling since the csv rows contain both features and labels and are small in 
size.

Batch Generator now randomly samples batch_size rows from the array, reads the
images from respective files, preprocesses the images and appends them to 
images array (X). The labels are appended to labels array and if three 
cameras are used the labels for left and right cameras are adjusted by 0.1
and -0.1 respectively.

## Experiments

- Based on the Cheatsheet (https://carnd-forums.udacity.com/cq/viewquestion.action?id=26214464&questionTitle=behavioral-cloning-cheatsheet) i tired keeping the epoch low as 5. But it didnt work in my case unless its 18-20 so i kept it to the max 20.

- I tried to make my model work in track 2 it was unsuccessful. Its due to my models choice. Thought its not counted for evaluation. I found that making use of all the parameters instead of only satuation might have solved this problem.

- I tried to work as simalr to the NVIDIA Model but that had 5 convolution layers, but to optimize mine i finilized to 3 convoliton layers each

## Results

In this project, we were working on a regression problem in the terms of self-driving cars. We mainly focused on finding a suitable network architecture and trained a model a dataset. According to Mean Square Error (MSE) the model worked well. Next generating new new dataset was the problem here. Additionally, we didn't fully rely on MSE when building our final model. Also, we use relatively number of training epochs (namely 20 epochs).

[![Final Output](http://img.youtube.com/vi/eQual2I0ph4/0.jpg)](https://www.youtube.com/watch?v=eQual2I0ph4)
