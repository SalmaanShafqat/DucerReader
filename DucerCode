
#include <LiquidCrystal.h>

//all code pertaining to the second transducer was written by me(Salmaan Shafqat)
//as well as some code for the first ducer(signified with a comment)
//All other code was written by Kelso Freidler and I do not take credit for it

// initialize the library by associating any needed LCD interface pin
// with the arduino pin number it is connected to
const int rs = 13, en = 12, d4 = 11, d5 = 10, d6 = 9, d7 = 8;
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);

const int numReadings = 30;
//ducer 1
float readings[numReadings];      // the readings from the analog input
int readIndex = 0;              // the index of the current reading
float total = 0;                  // the running total
float average = 0;                // the average

//ducer 2 - Salmaan Shafqat
float readings2[numReadings];
int readIndex2 = 0;
float total2 = 0;
float average2 = 0;

//float trueTotal = 0;              // the true total
//float totalAverage = 0;           // the total average
//float count = 0;                  // the count
float pressure = 0;  // the pressure for ducer 1
float pressure2 = 0; //the pressure for ducer 2
int inputPin = A0; //ducer 1
int inputPin2 = A1; //ducer 2


void setup() {
  lcd.begin(16, 2);
  Serial.begin(9600);
  for (int thisReading = 0; thisReading < numReadings; thisReading++) {
    readings[thisReading] = 0;
  }
  for(int thisReading2 = 0; thisReading2 < numReadings; thisReading2++){  //written by Salmaan Shafqat
    readings2[thisReading2] = 0;
  }
}


void loop() {
  //ducer 1
  lcd.clear();
  //count++;
  total = total - readings[readIndex];
  readings[readIndex] = analogRead(inputPin); //reading voltage from ducer pin
  //trueTotal = trueTotal + readings[readIndex];
  total = total + readings[readIndex];
  readIndex = readIndex + 1;

  if (readIndex >= numReadings) {
    readIndex = 0;
  }
  

  average = total / 30.0;
  //pressure = 1.0129*average-17.989; //ducer 1
  pressure = 1.4405*average-255.61; //ducer 1(tested for accuracy) - all code below written by Salmaan Shafqat
  //trueTotal/count;
  Serial.print(pressure, 1);
  Serial.println("psi");
  //Serial.println(totalAverage);
  lcd.setCursor(0, 0);
  lcd.print(pressure);

  total2 = total2 - readings2[readIndex2];
  readings2[readIndex2] = analogRead(inputPin2);
  total2 = total2 + readings2[readIndex2];
  readIndex2 = readIndex2 + 1;

  if (readIndex2 >= numReadings) {
    readIndex2 = 0;
  }

  average2 = total2 / 30.0;
  //pressure2 = 1.4405*average2-255.61; 
  pressure2 = 1.0115*average2-239.09; //ducer 2 (tested for accuracy)
  Serial.print(pressure2, 2);
  Serial.println("psi");
  Serial.print(average2, 2);
  lcd.setCursor(0,1);
  lcd.print(pressure2);
  
  
  delay(250);
}
