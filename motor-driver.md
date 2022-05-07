# motor dirver
## description
The project is to just control a dc motor with the help of motor driver.
## components used
1. arduino uno
2. Motor driver
3. Dc motor
4. connecting wires
## working
A DC motor can be controlled in two ways,by controlling the speed and controlling the direction of rotation.Here i have controlled both the cases.
### connection
Firstly the port enable 1&2 is connected to eneble the input pin 1 and 2.
now the input pin 1 and 2 are connected to the arduino board.Input 1 and 2 directly enables output 1 and 2 respectively.Output 1 and 2 are connected to the motor terminals.
### circuit
![alt text](./task 2(1).png)
### code
```sh
int ena=9;     //settingup all the connection
int in1=8;
int in2=7; 

void setup()
{
  pinMode(ena,OUTPUT);   //initialising  the default 
  pinMode(in1,OUTPUT);
  pinMode(in2,OUTPUT);
  digitalWrite(in1,LOW);
  digitalWrite(in2,LOW);
}
void loop()
{
  directionControl();
  delay(1000);
  speedControl();
  delay(1000);
}

void directionControl()
{
  analogWrite(ena,255);  //sets motor to max speed  
  digitalWrite(in1,HIGH);   //turn on the motor
  digitalWrite(in2,LOW);
  delay(2000);
  digitalWrite(in1,LOW);   //reversing the rotation
  digitalWrite(in2,HIGH);
  digitalWrite(in1,HIGH);
  digitalWrite(in2,LOW);
}
void speedControl()
{
  digitalWrite(in1,LOW);  
  digitalWrite(in1,HIGH);
  
  for(int i=0;i<265;i++)   //to accelarate the speed to maximum
  {
    analogWrite(ena,i);
    delay(20);
  }
  delay(1000);
  for(int i=255;i>=0;--i) //to decelarate to zero
  {
    analogWrite(ena,i);
    delay(20);
  }
  delay(1000);
  digitalWrite(in1,LOW);   //turn off the motor
  digitalWrite(in2,LOW);
}
```

## tinker cad
link to this project in  my tinker cad is [here](https://www.tinkercad.com/things/8f7RbHlGA3z-task-21/editel?sharecode=8WdNgfjV6O11YnyXvJ52aSbvD2Ze-mpxe1pMssSeRv0)
