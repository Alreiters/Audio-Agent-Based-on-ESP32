# Audio Agent Based on ESP32

HKUST (GZ) Information Hub 2025 Fall PhD Summer Camp    

@Author: X. L. GUO, Y. X. YANG, H. X. Liu, J. X. Peng

# I. Introduction
The aim of this project is to make a simple and common speech recognition device that recognizes specific words in speech to start, and recognizes and completes specific commands.

# II. Hardware Part
Hardware part includes: ESP32, microphone, speaker, LEDs

# III. Speech Recognition Model
1. Training Data
Using an open source dataset containing 36 voice categories, the audio is segmented into segments and a spectrogram is generated for each segment.

![image](https://github.com/user-attachments/assets/5fe97250-ae54-40ca-b816-23f9d55bc191)


2. Training model

A Convolutional Neural Network (CNN) is used, with two Convolutional Layers, a Max Pooling Layer, a Flatten Layer, a Dropout Layer, and multiple Dense Layers. (Dense Layers), Adam Optimizer.

![image](https://github.com/user-attachments/assets/8dbf2cdc-7eed-44a2-9e0e-8b0bd634837d)


3. Conversion to TFLite (TensorFlow Lite) models
Quantization: convert 32-bit floating point numbers to 8-bit integers, reduce the size of the model using compact parameters, define the generator function to provide representative samples of the dataset, the generator function extracts small batches of data from the complete training dataset, these samples will be supplied to the TFLite converter for calculating the conversion parameters.

# IV.Network Connected Speech Recognition Model
1.Speech Recognition using Application Program Interface (API)

Utilizing API (Application Programming Interface), the captured audio input is converted into text-based commands to take full advantage of its advanced natural language processing capabilities; 
the audio data is transferred from ESP32 to the cloud server to ensure reliable and accurate speech recognition; and the language model is customized to recognize specific voice commands.

2. Using Baidu Speech Recognition

![image](https://github.com/user-attachments/assets/e440738b-43cd-401f-a0a9-83df0d584179)

Check the wi-fi connection status, use JSON to send data and return results, send data block by block and merge data together.

Receive and parse text commands from the API, map the recognized commands to the corresponding functions in the ESP32 firmware, and trigger the corresponding ESP32 operations according to the recognized voice commands.

# V. Physical Drawing

![image](https://github.com/user-attachments/assets/c0c3571c-b574-4d8a-8db5-cf996e7fce06)

# VI. Project Summary

1. Work Content
Successfully integrate audio recognition with ESP32, and utilize API for speech-to-text conversion to realize voice-controlled intelligent functions.

2. Shortcomings
Because of the network connection timeout and ESP32 memory limitation, we can't call the speech recognition API and import the data into ESP32 in a short time.

3.Improvement
Explore and extend voice control features to include a wider range of commands, integrate with other smart home devices, and further optimize system performance and user experience.


Reference: https://github.com/atomic14/diy-alexa

