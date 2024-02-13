Welcome to the BAE305-SP24-Lab5 wiki!

# Lab 5 - The Brain: Microcontrollers

# By: Noah Lane and Lily Schlaug
# Summary
Lab goal; summary of work performed; summary of outcome
Lab 1 will be somewhat different since this is an introduction to the equipment.
# Materials
List materials used in the lab (not the testing equipment, but that used to build the lab project)
# Assembly Procedures
Provide basic summary of steps performed in lab (Do not copy and paste from lab assignment.) The important part here is to provide detail that you had to develop in the lab which will be more important in later labs.
You must include Schematics, Engineering Drawings, and Programming if appropriate in this section.
1. This is step 1.
2. This is step 2.
3. This is step 3.
I am now including an image as an example: 
![](https://github.com/joedvorak/BAE305-Sp19-Lab1/blob/master/Repository%20Creation.png)
# Test Equipment
List multimeters and other equipment used for testing and creating results.
# Test Procedures
How did you test the system to get your results
# Test Results
What are your results?
# Discussion
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