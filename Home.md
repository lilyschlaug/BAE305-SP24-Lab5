
# Lab 5 - The Brain: Microcontrollers

# By: Noah Lane and Lily Schlaug
# Summary
During this lab, we used Arduino as a microcontroller to understand the basics of using microcontrollers in circuits. Arduino IDE software was used throughout the lab to compile and run open-source code for different tasks. An LED was used to ensure that circuits were built and programmed properly to achieve the desired outcome. First, we made the LED blink. Then, controlled the LED with a potentiometer. Next, we controlled the LED with a photoresistor. Finally, we used pulse width modulation (PWM) to dim the LED. The outcome of this lab was to familiarize us with Arduino IDE and the Red Board to use microcontrollers. 

# Materials
1x 330 Ω Resistor

1x 10 kΩ Resistor (SparkFun Inventor’s kit)

1x Computer running Arduino IDE

1x RedBoard (SparkFun Inventor’s kit)

1x Photoresistor (SparkFun Inventor’s kit)

1x LED (SparkFun Inventor’s kit)

2 x 10 kΩ potentiometers (SparkFun Inventor’s kit)

1x A momentary button (SparkFun Inventor’s kit)

# Assembly Procedures
**Part 1 - Blinking an LED**

1. Connect the LED and 330 Ω resistor in series on the solderless breadboard
2. Connect digital pin 13 of the redboard to the positive lead of the LED
3. Connect the resistor to ground 

![image](https://github.com/npla225/BAE305-SP24-Lab5/assets/156371043/9179e068-15c9-4099-8ed2-fafa2eac4bf0)

**Figure 1. Schematic for Blinking an LED circuit**

**Part 2 - Controlling an LED with a potentiometer**

1. Begin with the Figure 1 circuit
2. Add the potentiometer to the breadboard
3. Connect the first lead to the 5V power pin on the breadboard, the central lead to A0 and the last lead to ground 

![image](https://github.com/npla225/BAE305-SP24-Lab5/assets/156371043/7519fa72-63d9-4083-892c-11c78e1dd565)

**Figure 2. Schematic for Controlling an LED with a potentiometer circuit**

**Part 3 - Controlling an LED with a photoresistor**

1. Begin with the circuit from Figure 2
2. Replace the potentiometer with the photoresistor and a 10 kΩ resistor in series

![image](https://github.com/npla225/BAE305-SP24-Lab5/assets/156371043/823d4db5-6658-4907-90cc-b1a25ac7c3c4)

**Figure 3. Schematic for Controlling an LED with a photoresistor circuit**

**Part 4 - LED dimmer using PWM**

1. Begin with the circuit from Figure 2
2. Move digital pin 13 to digital(~PWM) pin 6

![image](https://github.com/npla225/BAE305-SP24-Lab5/assets/156371043/52452dfb-5acd-435d-a2b5-1daebca304f0)

**Figure 4. Schematic for LED dimmer using PWM circuit**
**Comment: For the purpose of this lab the RGB LED was not used. A single yellow LED was used so branches R1 and R4 can be neglected.

![IMG_7749](https://github.com/npla225/BAE305-SP24-Lab5/assets/156371043/2685149f-dcbc-42bc-b1c5-22ff780d1e96)

**Figure 5. Image of LED dimmer using PWM circuit with oscilloscope leads**

# Test Equipment
1x Oscilloscope: Tektronix TDS 2012 

# Test Procedures
**Part 1 - Blinking an LED**

1. Open the Blink program from the Arduino library located under File> Examples> Basics> Blink
2. Download the program to the Arduino and run the program

**Part 1 Code**
```c++
// the setup function runs once when you press reset or power the board
void setup() {
  // initialize digital pin LED_BUILTIN as an output.
  pinMode(LED_BUILTIN, OUTPUT);
}

// the loop function runs over and over again forever
void loop() {
  digitalWrite(LED_BUILTIN, HIGH);  // turn the LED on (HIGH is the voltage level)
  delay(1000);                      // wait for a second
  digitalWrite(LED_BUILTIN, LOW);   // turn the LED off by making the voltage LOW
  delay(1000);                      // wait for a second
}
```

**Part 2 - Controlling an LED with a potentiometer**

1. Open the Analog Read Serial program from the Arduino library located under File> Basics> AnalogReadSerial
2. Copy the code from the Blink program into AnalogReadSerial
3. Change the interval of Blink from 1000 to A0 so it will be controlled by the potentiometer

**Part 2 Code**
```c++
/ the setup routine runs once when you press reset:
void setup() {
  // initialize serial communication at 9600 bits per second:
  Serial.begin(9600);
  pinMode(LED_BUILTIN, OUTPUT);
}

// the loop routine runs over and over again forever:
void loop() {
  
digitalWrite(LED_BUILTIN, HIGH);  // turn the LED on (HIGH is the voltage level)
  delay(analogRead(A0));                      // wait for a second
  digitalWrite(LED_BUILTIN, LOW);   // turn the LED off by making the voltage LOW
  delay(analogRead(A0));                      // wait for a second

  // read the input on analog pin 0:
  int sensorValue = analogRead(A0);
  // print out the value you read:
  Serial.println(sensorValue);
}
```

**Part 3 - Controlling an LED with a photoresistor**

1. 

**Part 3 Code**
**Code for nightlight with potentiometer**
```c++
void setup() {
  // initialize serial communication at 9600 bits per second:
  Serial.begin(9600);
  pinMode(PIN5, OUTPUT);
}

// the loop routine runs over and over again forever:
void loop() {

  // read the input on analog pin 0:
  int sensorValue = analogRead(A1);
  // print out the value you read:
  Serial.println(sensorValue);

  if (sensorValue>400) //Dark
  {
  digitalWrite(PIN5,HIGH); 
  }
  else {
    digitalWrite(PIN5,LOW); 
  }
}
```

**Part 4 - LED dimmer using PWM**

1. 

**Part 4 Code**
**Code for    the last part** 
```c++
void setup() {
  // initialize serial communication at 9600 bits per second:
  Serial.begin(9600);
  pinMode(PIN5, OUTPUT);
  
}

// the loop routine runs over and over again forever:
void loop() {
int A;

  // read the input on analog pin 0:
  int sensorValue = analogRead(A1);
  // print out the value you read:
  Serial.println(sensorValue);


  A = map(sensorValue, 0, 1023, 0, 255);
  analogWrite(PIN5,A);
}
```

# Test Results

Part 1 - Blinking an LED

This was a simple program to turn the LED on for one second and off for one second so that it would appear to blink. This was to make sure that the Arduino was connected properly. The major sections of the computer program were to initialize the digital pin output. Next, the program ran a loop to turn the LED on and off for a second each until the user terminates the program. 

Part 2 – Controlling an LED with a potentiometer

Part 2 resulted in using the serial monitor tool to visualize how the count values went up and down as the potentiometer was changed. 

Part 3 – Controlling an LED with a photoresistor

For part three, we found that the minimum and maximum analog value from the photoresistor were 136 and 650 milliseconds, respectively. By using an if/else statement, we were able to create a "night light" by setting a threshold value for the light to turn on when dark. 

Part 4 – LED dimmer using PWM

For part three, the result allowed us to change the potentiometer and cause the LED to dim or brighten. This is due to changing the frequency of the PWM, which impacts the amount of voltage that is able to reach the LED. 

# Discussion

Part 1 - Blinking an LED

Your LED flashes with a delay from the uploaded code. Decrease this delay until the LED just stops blinking. That is, the point where the light is still blinking, but appears to stay constantly illuminated. 

a.	What is the value of your delay now? 

- The delay had a value of 10 milliseconds. 

b.	What field may this “persistence of vision” play a greater role in? 

- The persistence of vision is that our brain is not as fast and can not see the blink, even though we know that one is still occurring in the LED. It is an optical illusion that the LED no longer appears to blink. Essentially, the blink is so quick that our eyes merge the "on" and "off" state to form a continuous image. 

Part 2 – Controlling an LED with a potentiometer

a.	What is the difference between an analog and a digital signal?

b.	In your lab report, list a few examples of real-world examples which can be described by an analog signal. Likewise, what are the two states which can be conveyed by a digital signal?

c.	What happens to the Serial Monitor Refresh rate as you move the potentiometer to control the LED blinking time?

- As the potentiometer is moved, the blinking time gets greater or smaller, depending on the direction it is moved. 

Part 3 – Controlling an LED with a photoresistor

a.	Does the LED turn on immediately after blocking the light? What about when you remove the object blocking the light, does the LED turns of immediately?

- There is a slight delay in both situations. This is because it takes a small amount of time for the microcontroller to communicate with the software, and then send a signal back to turn on or off the LED. 

Replace the 10k resistor with another LED (negative leg to ground). 

b.	What happens when you place your finger over the photoresistor?

c.	How does this help you visualize Ohm’s Law?

Part 4 – LED dimmer using PWM

Connect the oscilloscope to the LED pin and observe and record what happens to the signal and the LED brightness when you turn the knob of the potentiometer.

- When connecting the oscilloscope, the frequency of the signal does not change. Only pulse width modulation changes as potentiometer value is changed. This changes the voltage that reaches the LED, causing it to dim. As the digital signal has a longer "off" period, the average PWM voltage reaching the LED decreases. 


![IMG_7751](https://github.com/npla225/BAE305-SP24-Lab5/assets/156371043/954841dc-4ba6-4221-ae4b-7e770a88b15f)

**Figure 6. Displayed PWM signal**

# Conclusion

# Sources 
**Figures 1-4 circuit schematic images**
 
JOEL_E_B. “Sparkfun Inventor’s Kit Experiment Guide - v4.1.” SparkFun Inventor’s Kit Experiment Guide - v4.1 - SparkFun Learn, learn.sparkfun.com/tutorials/sparkfun-inventors-kit-experiment-guide---v41/project-1-light. Accessed 13 Feb. 2024. 



**Code for Night Light**

```c++
void setup() {
  // initialize serial communication at 9600 bits per second:
  Serial.begin(9600);
  pinMode(LED_BUILTIN, OUTPUT);
}

// the loop routine runs over and over again forever:
void loop() {

  // read the input on analog pin 0:
  int sensorValue = analogRead(A0);
  // print out the value you read:
  Serial.println(sensorValue);

  if (sensorValue>400) //Dark
  {
  digitalWrite(LED_BUILTIN,HIGH); 
  }
  else {
    digitalWrite(LED_BUILTIN,LOW); 
  }
}
```