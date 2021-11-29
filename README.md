# Industry4.0-Prognostic-Device
The task was to interface the Vibrator Censor to the Arduino Nano (ESP8266) and get the values  from the censor. The values are received through Bluetooth module interfaced with the Arduino Nano. Then those censor values are passed through the Fast Fourier Transform algorithm which  is called using the numpy package in python. The reason to convert it into FFT is because it converts the signal data into frequency which in-turn can be used to find if there is any defect in the machine.

# Architecture Diagram
![Architecture Diagram](https://user-images.githubusercontent.com/47251253/143852006-575dc757-2005-4d40-8b23-38a57863e3d0.png)



# Working Principle
The Arduino ESP8266 board is used to interface the vibration sensor and Bluetooth module. The 
values given out by the vibration sensor is automatically sent via the Bluetooth module. A device 
such as a laptop is connected to the Bluetooth module. The values are received through a python 
script and these values are updated to a google sheet simultaneously for future reference. 
The values are updated to the google sheet using the gspread module for python. The values are 
stored via API calls which is stored under a parameter. This API is in the form of a .json file. 
Once we get the instance of the sheet via the API parameter call, the values can be read, 
manipulated and updated to the google sheet.
The values received are used as a parameter for the FFT Conversion. Fast Fourier 
Transformation is an algorithm which converts a signal from its original domain to a frequency 
domain. FFT has error when finite precision floating point arithmetic is used, but these errors are 
mostly small. It rapidly computes by factorizing the DFT matrix into a product of mostly zero 
factors, thus manages to reduce the time complexity.
Once the values are obtained after FFT Conversion using the numpy module for python using the 
function numpy.fft.fft(parameter), these values are used to plot a live graph. This is done through 
the pyqtgraph module available for python. Under this graph the, pink spectrum denotes the 
signal from its original domain, whereas the blue frequency spectrum denotes the frequency 
domain which is obtained by FFT Conversion.
A Machine Learning model is trained using sklearn package available in python. Linear 
Regression algorithm is used to train the model using previous datasets. The dataset is usually 
divided into two parts. One which is used for training the model and the other one is used for 
testing the accuracy of the model. Once the model is trained, we would be able to predict the 
next set of values for a given time interval.

# Result and Inference
![r i](https://user-images.githubusercontent.com/47251253/143852113-4f79bb05-ac26-4b71-b078-1f94c7660136.png)
