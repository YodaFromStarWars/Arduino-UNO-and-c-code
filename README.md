# Arduino-UNO-and-c-code
This repo contains both the ISO file for the Microcontroller code
Ultrasonic_tester is the code for the microcontroller. It was programmed using Arduino IDE and can be opened by unizpping the Ultrasonic_tester zip file and openng the ISO file with the Arduino IDE software.
For the MCU, a built in library (NewPing) is used to easily ping for the max distance measured by the sensor using the sonar.ping command.
The sensor will send an ultrasonic wave forward which will then bounce off of the nearest object and return to the receiver. The distance from the sensor (in cm) can then be measured using the sonar.convert_cm command.
This distance is recorded and presented in the serial monitor.

The code operates with a Baud Rate of 115200 bauds and continuously loops with a 0.1 second delay to prevent sensor interferance.
The sensor is rated for a maximum reading distance of 3m.
If the sensor is disconnected or not properly wired it will read an input of 0cm, therefore this exception is handled as an error in the MCU code.

The C# can be opened by unzipping the Arduino UNO Serial.zip file and selecting the Arduino UNO Serial.snl file in the folder
In the C# code, a serialport is initialized. The following properties need to be identical to their respective MCU counterparts.
 - Port Name
 - Baud Rate

An infinite loop is used to continuously read data (with a 0.1s delay) from the serial port and display it when the code is running.
The try-catch statement is used to handle errors that would occur if the MCU was disconnected from the port. The zero reading exception is handled in the Arduino IDE code.
The C# code simply imports serial data from the MCU and displays it, therefore if you want to attach additional sensors, the majority of the changes will take place in the Arduino IDE code. Additional sensors can be attached and input data can be displayed on the serial monitor. The C# code will then import and display the serial data.

In the case that you would want to add an additional MCU on a seperate port, you would then need to modify the c# code to include another SerialPort with the correct baudrate and port name and include another line within the infinite loop to display the data.
The C# program will not run if the serial monitor of the Arduino IDE is running at the same time.
The C# code can be used in any application where data is read via a sensor. The code was tested using an ultrasonic sensor (HY-SRF05) as well a temperature sensor (tmp36), but can also be used with IR sensors, humidity sensors, motion sensors etc.
