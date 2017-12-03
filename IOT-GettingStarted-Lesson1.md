# Internet of Things

IOT is a term used to collectively describe the embedded devices which can communicate with each other over a network. e.g. Bluetooth speakers, Amazon Alexa, Smart watches, Apple beakons, etc.
There are several steps to begin learning the insights of IOT and programming a device.


## Computers vs Embedded systems

A computer consists of a very strong CPU and large memory (RAM) which can be programmed to do a lot of heavy tasks simultaneously. However, an embedded system is a standalone device which is programmed to do a specific task, and do it in an extremely optimized and robust way.

## Microcontrollers

A microcontroller (uC) is an integrated circuit containing CPU, RAM, buses, input-output pins etc. all in one place. So, it can be programmed to do a task. However, the computation power of its CPU is low (1-32 MHz). RAM too is very small (2-16 kiB). Hence a microcontroller cannot do heavy tasks. Examples are ATmega328P, PIC12F1572, ESP8266, nRF24L01, MSP430, etc.

### Part - 1 : Arduino
Arduino is a platform which provides an easy UI to begin programming a microcontroller, preferabally from Atmel.

Materials required:
Arduino UNO
Adruino software

Let's get started with our first program, Blink LED. 

Step - 1: Blink an LED

Code:

void setup() {
  // initialize digital pin LED_BUILTIN as an output.
  pinMode(LED_BUILTIN, OUTPUT);
}

// the loop function runs over and over again forever
void loop() {
  digitalWrite(LED_BUILTIN, HIGH);   // turn the LED on (HIGH is the voltage level)
  delay(1000);                       // wait for a second
  digitalWrite(LED_BUILTIN, LOW);    // turn the LED off by making the voltage LOW
  delay(1000);                       // wait for a second
}


Connect your Arduino to the computer. Open the Arduino software. Select the board as Arduino Genuino/Uno. Select the appropriate port in th Tools menu. Copy the above code and paste in the Arduino editor and save the file with name blink.ino. After saving, click the 'Verify' button on top to compile the code. If there are no errors, go ahead and upload the program. After a few seconds of successful upload, the inbuilt LED will start to blink.


Step - 2: USART - Communicating with other devices
A lot of times, we want to communicate with the microcontroller, maybe for debugging purposes. This is achieved using USART (Universal Synchronous Asynchronous Receiver Transmitter). To delve deep into how it works, you may contact Atmel datasheets.

Compile the code and upload it. Open the Serial Monitor and set the Baud rate to 9600.
After this code is uploaded, the microcontroller will return the same message that you sent to it.

Code:

void setup() {
  // Open serial communications and wait for port to open:
  Serial.begin(9600);
  while (!Serial) {
    ; // wait for serial port to connect. Needed for native USB port only
  }


  Serial.println("Goodnight moon!");
}

void loop() { // run over and over
  if (Serial.available()) {
    Serial.write(Serial.read());
  }
}


### Part - 2 : Raspberry Pi

Raspberry Pi (RPi) is basically a protable computer. It has USB ports, WiFi, Bluetooth, Power input, HDMI output, 3.5 mm audio jack, a camera connector, and about 40 general purpose input-output (GPIO) pins.
To begin with, a decent knowledge of linux OS is required. Since it is a computer, we can do anything. Programming can be done in Python, C, C++, Java, or whatever you like. What differentiates it from a computer is the availability of 40 GPIO pins which can be used to connect to other devices and create a more interactive device.

Download a Raspberry Pi image from this official link and follow their intructions to upload the image on a SD card. After the image is burned on the SD card, insert it into the slot on RPi, connect the HDMI output to a monitor/TV and power it up. Booting will start.

There are some user-specific configurations that need to be done after every new image is burned. These configurations make your life easier. The instructions are listed on https://gitlab.com/ashish28ranjan/raspberry-pi/blob/master/raspbian-jessie-lite.md