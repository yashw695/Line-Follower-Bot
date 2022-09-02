# Line-Follower-Bot
Robot


int IR1=3;      //Right sensor
int IR2=2;    //left Sensor
// motor one
int enA =11 ;    //Right motor
int MotorAip1=9;
int MotorAip2=6;
// motor two
int enB = 10;    //Left motor
int MotorBip1=4;
int MotorBip2=5;
void setup() 
{
  
  // put your setup code here, to run once:
  pinMode(enA, OUTPUT);
  pinMode(enB, OUTPUT);
  pinMode(IR1, INPUT);
  pinMode(IR2, INPUT);
  pinMode(MotorAip1,OUTPUT);
  pinMode(MotorAip2,OUTPUT);
  pinMode(MotorBip1,OUTPUT);
  pinMode(MotorBip2,OUTPUT);
  Serial.begin(9600);
}
void loop() 
{
   
  
   Serial.print(digitalRead(IR2));
   Serial.println(digitalRead(IR1));
   if(digitalRead(IR1)==HIGH && digitalRead(IR2)==HIGH) //IR will not glow on black line
  {
    //Stop both Motors
   
    digitalWrite(MotorAip1,LOW);
    digitalWrite(MotorAip2,LOW);
    digitalWrite(MotorBip1,LOW);
    digitalWrite(MotorBip2,LOW);
    analogWrite (enA, 0);
    analogWrite (enB, 0);
    delay(5000);
    
   
    foreward();
    delay(400);
  
    
   }
   

  else if(digitalRead(IR1)==LOW && digitalRead(IR2)==LOW)  //IR not on black line
  {
    foreward();
   
  }
  
  else if(digitalRead(IR1)==LOW && digitalRead(IR2)==HIGH)
  {
    digitalWrite(MotorAip1,HIGH);     
    digitalWrite(MotorAip2,LOW);
    digitalWrite(MotorBip1,LOW);
    digitalWrite(MotorBip2,HIGH);
    analogWrite (enA, 152);
    analogWrite (enB, 140);
    delay(100);
    
  }

  else if(digitalRead(IR1)==HIGH && digitalRead(IR2)==LOW)
  {
    digitalWrite(MotorAip1,LOW);     
    digitalWrite(MotorAip2,HIGH);
    digitalWrite(MotorBip1,HIGH);
    digitalWrite(MotorBip2,LOW);
    analogWrite (enA, 152);
    analogWrite (enB, 140);
    delay(100);
   
  }

  else
  {
    //Stop both the motors
    digitalWrite(MotorAip1,LOW);
    digitalWrite(MotorAip2,LOW);
    digitalWrite(MotorBip1,LOW);
    digitalWrite(MotorBip2,LOW);
    analogWrite (enA, 0);
   analogWrite (enB, 0);
  
  }
}
void foreward()
{
    //Move both the Motors
    digitalWrite(MotorAip1,HIGH);
    digitalWrite(MotorAip2,LOW);
    digitalWrite(MotorBip1,HIGH);
    digitalWrite(MotorBip2,LOW);
    analogWrite (enA, 152);
    analogWrite (enB, 140);
  }
