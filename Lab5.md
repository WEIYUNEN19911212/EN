# 嵌入式系統 - 實作5: Servo伺服馬達, 溫度感應器 + LCD 顯示器,  (W10)
### Lab 5-1 請使用兩個**伺服馬達同步從 0 度逐步掃描到 180 度之後再逐步掃描回0度, 每步的間隔時間為50ms (0.05秒), 細節請參考以下Demo.
![chrome-capture (1)](https://user-images.githubusercontent.com/89717315/138579699-63faf6a3-30f7-47c1-8d16-f4788499217c.gif)
### 程式
````C
// Developed for Embedded Sytem, VNU, Fall 2021

#include <Servo.h>

int pos = 0;

Servo servo_9;
Servo servo_8;

void setup()
{
  servo_9.attach(9, 500, 2500);
  servo_8.attach(8, 500, 2500);
  
}

void loop()
{
// 從 0 到 180 度逐步掃描伺服, 1度/步
  for (pos = 0; pos <= 180; pos += 1) {

    servo_9.write(pos);
    servo_8.write(pos);
       

    delay(50); // 等50ms (0.05秒)
  }
  
  for (pos = 180; pos >= 0; pos -= 1) {
// 從 180 到 0 度逐步掃描伺服, 1度/步
    servo_9.write(pos);
    servo_8.write(pos);
        

    delay(50); // 等50ms (0.05秒)
  }
}
````
### Lab 5-2 LCD顯示溫度感應器的溫度;若溫度<38 綠LED亮; 若大於38度, 紅色LED亮, 細節請參考以下Demo
![chrome-capture (3)](https://user-images.githubusercontent.com/89717315/138580186-19b1f3e3-be59-4087-b4c7-b4d67db89c93.gif)
### 程式
````C
// For Embedded System course, VNU, Fall 2021 

#include <LiquidCrystal.h>

LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

void setup() {
  lcd.begin(16, 2);
  Serial.begin(9600);	
  pinMode(A1, INPUT); // Read analog voltage (2^10)

}

void loop() {
  int reading = analogRead(A1);  // read analog level (2^10)
  lcd.setCursor(0,0);  
  lcd.print("TMP Sensor Demo");

  float voltage = (reading/1024.0) * 5.0; // Convert to voltage
  
  // converting from 10mv per degree with 500mV offset  
  float tempC = (voltage - 0.5) * 100.0; 
  lcd.setCursor(0,1);
  lcd.print("Tmp:");
  lcd.print(tempC);
  lcd.print(" C");
  delay(500);
  lcd.clear();
  Serial.println(reading);
  Serial.println(voltage);  
}
````
## Plus LED Control
![chrome-capture (4)](https://user-images.githubusercontent.com/89717315/138580742-423b6858-5df6-4b68-a41f-5b47a3ec0c94.gif)

