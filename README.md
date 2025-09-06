in what language is the below code written      #include <AFMotor.h> 
//defining pins and variables 
#define lefts A0 
#define rights A1 
//defining motors 
AF_DCMotor motor1(1, MOTOR12_1KHZ);  
AF_DCMotor motor2(2, MOTOR12_1KHZ); 
AF_DCMotor motor3(3, MOTOR34_1KHZ); 
AF_DCMotor motor4(4, MOTOR34_1KHZ); 
Void setup() { 
//Setting the motor speed 
Motor1.setSpeed(180); 
Motor2.setSpeed(180); 
Motor3.setSpeed(180); 
Motor4.setSpeed(180); 
//Declaring PIN input types 
pinMode(lefts,INPUT); 
pinMode(rights,INPUT); 
//Begin serial communication 
Serial.begin(9600); 
} 
Void loop(){ 
//Printing values of the sensors to the serial monitor 
Serial.println(analogRead(lefts)); 
Serial.println(analogRead(rights)); 
//line detected by both 
If(analogRead(lefts)<=350 && analogRead(rights)<=350){ 
//Forward 
Motor1.run(FORWARD); 
Motor2.run(FORWARD); 
Motor3.run(FORWARD); 
Motor4.run(FORWARD); 
} 
//line detected by left sensor 
Else if(analogRead(lefts)<=350 && !analogRead(rights)<=350){ 
//turn left 
Motor1.run(FORWARD); 
Motor2.run(FORWARD); 
Motor3.run(BACKWARD); 
Motor4.run(BACKWARD) 
} 
//line detected by right sensor 
Else if(!analogRead(lefts)<=350 && analogRead(rights)<=350){ 
//turn right 
Motor1.run(BACKWARD); 
Motor2.run(BACKWARD); 
Motor3.run(FORWARD); 
Motor4.run(FORWARD); 
} 
//line detected by none 
Else if(!analogRead(lefts)<=350 && !analogRead(rights)<=350){ 
//stop 
Motor1.run(RELEASE); 
Motor2.run(RELEASE); 
Motor3.run(RELEASE); 
Motor4.run(RELEASE); 
} 
} 
