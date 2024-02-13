Welcome to the BAE305-SP24-Lab5 wiki!

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
Provide basic summary of steps performed in lab (Do not copy and paste from lab assignment.) The important part here is to provide detail that you had to develop in the lab which will be more important in later labs.
You must include Schematics, Engineering Drawings, and Programming if appropriate in this section.
1. This is step 1.
2. This is step 2.
3. This is step 3.
I am now including an image as an example: 
![](https://github.com/joedvorak/BAE305-Sp19-Lab1/blob/master/Repository%20Creation.png)
# Test Equipment
1x oscilloscope (Brand info????) 
List multimeters and other equipment used for testing and creating results.
# Test Procedures
How did you test the system to get your results
# Test Results
What are your results?
# Discussion

Part 1 - Blinking an LED 
Your LED flashes with a delay from the uploaded code. Decrease this delay until the LED just stops blinking. That is, the point where the light is still blinking, but appears to stay constantly illuminated. 

a.	What is the value of your delay now? 10

b.	What field may this “persistence of vision” play a greater role in? brain is not as fast 

c.	Discuss this further in your lab report.

d.	Delays are in milliseconds 

Part 2 – Controlling an LED with a potentiometer

a.	What is the difference between an analog and a digital signal?

b.	In your lab report, list a few examples of real-world examples which can be described by an analog signal. Likewise, what are the two states which can be conveyed by a digital signal?

c.	What happens to the Serial Monitor Refresh rate as you move the potentiometer to control the LED blinking time?

ci.	As the potentiometer is moved, the blinking time gets greater or smaller, depending on the direction it is moved. 

Part 3 – Controlling an LED with a photoresistor

a.	Does the LED turn on immediately after blocking the light? What about when you remove the object blocking the light, does the LED turns of immediately?

Replace the 10k resistor with another LED (negative leg to ground). 

b.	What happens when you place your finger over the photoresistor?

c.	How does this help you visualize Ohm’s Law?

Part 4 – LED dimmer using PWM

Connect the oscilloscope to the LED pin and observe and record what happens to the signal and the LED brightness when you turn the knob of the potentiometer.

- Frequency does not change, only pulse width changes when potentiometer is changed 

Did you make any design decisions that had an impact on the results? How did they impact the results? What do the results mean?
# Conclusion

**Code for Potentiometer and LED**
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