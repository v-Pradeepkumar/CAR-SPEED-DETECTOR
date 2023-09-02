# CAR-SPEED-DETECTOR
This project employs an ATmega328P microcontroller with an IR sensor to detect car speed. It displays the speed on an LCD and activates a buzzer if the car exceeds a preset speed limit, creating a car speed detection system

#include <LiquidCrystal.h>
const int rs = 7, en = 6, d4 = 5, d5 = 4, d6 = 3, d7 = 2;
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);
int sen1=11;
int sen2=12;
unsigned long t1=0;
unsigned long t2=0; 
float velocity;
void setup()
{
  lcd.begin(16, 2);
  pinMode(sen1,INPUT);
  pinMode(sen2,INPUT);
  Serial.begin(9600);
  lcd.setCursor(0,0);
  lcd.print(" Speed Detector ");
}

void loop() 
{
  while(digitalRead(sen1));
  while(digitalRead(sen1)==0);
  t1=millis();
  while(digitalRead(sen2));
  t2=millis();
  velocity=t2-t1;
  velocity=velocity/1000;//convert millisecond to second
  velocity=(5.0/velocity);//v=d/t
  velocity=velocity*3600;//multiply by seconds per hr
  velocity=velocity/1000;//division by meters per Km
  for(int i=5;i>0;i
  {
   lcd.setCursor(3,1);
   lcd.print(velocity);
   lcd.print(" Km/hr   ");
   delay(500);
   lcd.setCursor(3,1);
   lcd.print("            ");
   delay(500);
  }  
