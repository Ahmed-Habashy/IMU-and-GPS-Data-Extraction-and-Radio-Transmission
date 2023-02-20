# IMU-and-GPS-Data-Extraction-and-Radio-Transmission
This program extracts data from two sensors: SparkFun 9DoF Razor IMU M0 and SparkFun GPS-RTK-SMA Breakout - ZED-F9P. The extracted data is then combined into a single message and sent via a radio transmitter.

# Hardware Requirements
SparkFun 9DoF Razor IMU M0 board (https://www.sparkfun.com/products/16481)
SparkFun GPS-RTK-SMA Breakout - ZED-F9P board (https://www.sparkfun.com/products/16481)
Radio Transmitter

# Software Requirements
Arduino IDE

# Libraries
This program uses the following libraries:

string.h
ctype.h

# Configuration
Open the Arduino IDE.
Connect the hardware.
Open the program file.
Configure the settings.
Upload the code to the microcontroller.

# Settings
This program does not require any specific settings.

# Uploading the Code
Open the Arduino IDE.
Connect the hardware.
Open the program file.
Configure the settings.
Click the "Upload" button in the Arduino IDE to upload the code to the microcontroller.

# Running the Program
Connect the radio transmitter to the microcontroller.
Turn on the power.
The program will begin running automatically.
The program will extract data from the IMU and GPS sensors and combine the data into a single message.
The program will send the message via the radio transmitter.

# Code Summary
This code extracts IMU data from a "SparkFun 9DoF Razor IMU M0" board and GPS data from a "SparkFun GPS-RTK-SMA Breakout - ZED-F9P" board. It then creates its own message and sends it via a radio transmitter.

The code begins by including two standard C libraries: string.h and ctype.h. Then, it initializes some variables and starts the setup process. In the setup, it sets the baud rate for three serial ports, creates a random seed using analogRead(0), and initializes some more variables.

The loop function begins by checking if there is any data available from Serial1 (which should be connected to the GPS). If there is, it reads the data into a character buffer rxstream. The code then checks if the data is part of an IMU message (identified by specific header bytes). If it is, it extracts the necessary data (accelerometer readings and temperature) and sets a flag to indicate that an IMU message has been processed.

Similarly, if the data is part of an Euler message or an EKF-navigation message, the relevant data is extracted, and flags are set. Finally, if the data is part of a GPS RMC message (identified by specific header bytes), the latitude and longitude data are extracted and stored.

When all necessary data has been collected, the code creates its own message by combining the extracted data with some other information (such as a random encryption key index and a pod ID). The message is then sent via a radio transmitter.

# Variable Summary
msg_c: unsigned int, message counter
i: unsigned int, index variable for character buffer rxstream
byte_c: byte array, stores the two bytes of msg_c
y: char, unused
rxstream: char array, buffer to store incoming data
msg_tx: char array, stores outgoing message
f_euler: boolean, flag indicating that an Euler message has been processed
f_nav: boolean, flag indicating that an EKF-navigation message has been processed
f_ekf_nav: boolean, flag indicating that an EKF-navigation message has been processed
rmc_rd: boolean, flag indicating that a GPS RMC message has been processed
f_imu: boolean, flag indicating that an IMU message has been processed
indc0-indc9: int, unused
tr_angle: unsigned long, unused
ac_speed: unsigned long, unused
stringGPS: String, stores incoming GPS data
rmclat: float, stores latitude extracted from GPS RMC message
rmclong: float, stores longitude extracted from GPS RMC message
strt_lat: char pointer, unused
strt_long: char pointer, unused
filedate: unsigned long, unused
previousMillis: unsigned long, stores the last time the loop was run
interval: long, stores the interval at which to perform the loop (in milliseconds)

# Notes
The program includes comments to help explain the code.
The program was last updated in 2021, and may require updates or modifications to function properly on newer systems.
