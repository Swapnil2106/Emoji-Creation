# Emoji Creation using Deep Learning

## Introduction

Facial expression for emotion detection has always been an easy task for humans, but achieving the same task with a computer algorithm is quite challenging. 
With the recent advancement in computer vision and machine learning, it is possible to detect emotions from images. Computer algorithms are very sophisticated. 
Intelligent human-computer interaction is a new field aimed at enabling people to use computers naturally as tools. It is claimed that human communication skills 
are required for computers to interact with humans. One of these skills is the ability to understand a person’s emotional state. Therefore a utility that detects 
emotion from facial expressions would be widely applicable. Such an advancement could bring applications in medicine, marketing and entertainment.

## Objectives

i. To develop a CNN model for detecting facial expressions to classify them into seven emotions like Angry, Disgust, Fear, Happy, Sad, Surprise and Neutral.

ii. To develop a GUI that can convert facial expressions to personalized emoji’s at real time using face Cam.

## Problem statement

To create personalized emoji’s using Deep Learning in real time.

## Application in Societal Context

i. Website can be used to create personalized emoji's.

ii. Can be used to generate animated face for videos.

iii. Emoji's created can be used as stickers, display picture for various social media profile or even it can be used to create NFT images as the profile pictures.

## Block diagram
![image](https://github.com/user-attachments/assets/477001db-6cd5-4a2c-b97d-0c9ffe10fbf7)

After the input is fed in the form of image, the background is removed so that it cannot compromise or reduce the prediction accuracy. So, the proposed system works 
on two level of CNN framework. The first level removes the background and the second level extracts the primary expression vector (EV). The EV is generated by tracking 
down the relevant facial points of importance. Each layer consists of 4 filters. These filters detect the shapes, edges, texture and objects. The first layer uses edge, 
circle , corner detector filter to detect the face while the second layer catches the eyes, lips, ears, nose etc. Above mentioned technique is based on FACS(Facial 
Action Coding System) which leverages the relevant facial points to detect the human emotion instead of wearing sophisticated sensors.

## Implementation

### Dataset
The dataset used in this project is the FER-2013 dataset. The dataset contains approximately 30000 facial RGB images. The images are restricted for 48*48 pixels. 
The main labels of the images are divided into Angry, Disgust, Fear, Happy, Sad, Surprise and Neutral. All these categories have about 4500 images. 
This dataset is the standard dataset across the academia for facial recognition related projects. 0=Angry, 1=Disgust, 2=Fear, 3=Happy, 4=Sad, 5=Surprise, 6=Neutral are the labels of the dataset.

### Facial Action Coding System (FACS)
FACS is an anatomically based coding system that allows for the differentiation of expressions that are closely similar. FACS splits the face into two sections: upper 
and lower and further subdivides motion into action units (AUs). AUs are the unit of measurement between the muscle movements that combine to produce expressions.
The face tracking point is used to constrain the image region to process and the color probability distribution, both computed in the initialization step, is used to 
calculate the probability of a face pixel being skin so that “skin mask” of the user’s face can be created. Using this mask the system can detect, as a result of their 
nonskin-color property, the user’s eyebrows, eyes and mouth bounding boxes and due to their position related to the face tracking point, the system can label the zones. 
One problem can appear if the user has got his eyes a little bit sunk, then due to the shadow in the eyelid, most probably the eyebrow and eye will be found as a single blob. 
In that case, we divide this bounding box assuming that the eyebrow has been detected together with the eye. Finally, from the bounding boxes positions, 10 face features are extracted. 
These 10 feature points of the face will later allow us to analyze the evolution of the face parameters (distances and angles) used for expression recognition. 
Figure shows how FACS divides the input human images into different EV or expression vectors.

![image](https://github.com/user-attachments/assets/1826c3b3-9bdc-49df-9acd-f49553e9b3d6)

### CNN Model Building
The CNN Model implemented consists of 5 convolutional layers followed by a dense fully connected layer. For each layer the kernel size used is 3 x 3 pixels and 
max pooling of 2 x 2 after each layer. The activation function used is ReLU. There is one Dense layer with 200 neurons. The last output layer consists of 7 neurons corresponding to 7 emotions.

![image](https://github.com/user-attachments/assets/8a730e40-cfe6-48a0-b706-af6b56f17b09)

While implementing the CNN model we made use of the FACS method.The implemented architecture consist of 5 convolutional layers.The first layer consists of 
32 filters with kernel size of 33 filters. In the second and third layer the number of filters are increased to 64 filters with the kernel size of 33 filters. 
The fourth and fifth layer the number of filters are increased to 128 filters with the kernel size of 33 filters. The activation function used is ReLu. 
Since it increases the non-linearity in our input images and preserves lot of non-linear features like the colours, transition b/w the features etc. 
The max-pooling of 22 is done to convert 3d features to 2d features and then a dense layer of 200 nodes is implemented. The last layer consist of 7 layers 
which is equal to the number of emotions to be predicted. After training the model it gave an accuracy of 82.41% over 30 epochs. Later we saved the model in hdf5 format.

### Creating Emoji’s
Here we are making use of the python module named ‘python-avatars’. There are many attributes provided like skin colour, hair colour, clothing colour, 
hair style, clothing style, facial hair style, accessories etc.

### GUI using Django as Framework
Django is a high-level python web framework and with the help of this we can develop secure
and maintainable websites in an efficient manner. It has many built-in python libraries which
makes it suitable for both frontend and backend.
Here we created html forms which takes all the inputs which are connected to the attributes
for creating the emoji. Once the inputs are submitted, all those corresponding attributes are
used and an avatar with .svg file extension is created. The emotion prediction part from the
module 1 and the avatar generation part from module 2 are integrated.
Now, here the CNN model keep on detecting the emotions and when we click on the
generate emoji button the emotion at that point of time is converted to Emoji. Below is the
first page which is common for both genders.Figure shows gender selection.

![image](https://github.com/user-attachments/assets/9f82494c-d83d-416d-b3f5-cf82e6c3553c)

Now, based on the gender you select the respective attribute and their values will be loaded. 
Below figures show different attributes based on gender selection. If you choose Male as the gender, then you can choose different clothing type, facial hair type and accessories respectively.

![image](https://github.com/user-attachments/assets/b66d0a78-9d43-4505-8d44-83c6f3e8eab7)

![image](https://github.com/user-attachments/assets/a33446f4-9557-431d-9543-12496a67109e)

![image](https://github.com/user-attachments/assets/90ef553d-082e-4170-8128-4f502dcc7faf)


After selecting the attributes the camera turns on and user can look at the camera.

![image](https://github.com/user-attachments/assets/900bbcb2-0c2f-42ac-bc21-c36bc47b0987)

## Results
In the website, firstly the option for selecting the gender is given and then the attributes are chosen, and after choosing the attributes there is option for capturing the image, and the 
emotion of the person is detected and converted into emoji and that emoji gets downloaded.

![image](https://github.com/user-attachments/assets/b9d1f286-30d6-4c36-ad83-388b39f770a6)

![image](https://github.com/user-attachments/assets/513c270a-11f0-4482-93e8-896dd253d1d7)

![image](https://github.com/user-attachments/assets/457edaf6-81ba-4311-9f16-61aedcf98685)



## Conclusion
This project implements a simple and effective system for real-time face emotion recognition. 
Wearable detectors are frequently used in other techniques. The designed solution is based on a low-cost web camera. 
The feature extraction technology employed enables for dynamic classification of human facial expression emotions and production of personalised 
emoji in real time based on the user’s preferences utilising various variables. With an accuracy rate of 82.41%, the model produced good results. 
Future work could include evaluating the performance of our architecture on various data sets by taking training and testing samples from diverse data sets. 
Furthermore, emojis can be utilised with more customised elements like as accessories, special attire.NFTs (Non Fungible Tokens) can be utilised as a type of transaction 
in virtual worlds such as META. Additionally, by improving camera quality and hardware capability, the current system can be improved to forecast with greater accuracy while 
still using the existing architecture.




