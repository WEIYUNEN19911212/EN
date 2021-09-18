# 嵌入式系統 - 實作2:會呼吸的RGB LED,  按鍵控制, 狀態輸出 
## 實作2-1, analogWrite(): 並且觀查LED亮度變化是否有像"呼吸的效果"和示波器的波形有什麼關連性? (互動1), (2021-09-05)
![image](https://user-images.githubusercontent.com/89717315/132973524-db9f4e77-5f3b-4eb6-8588-56b1f3148900.png)
程式
````c
void setup()
{
  pinMode(13, OUTPUT);
}

void loop()
{
  digitalWrite(13, HIGH);
  delay(1000); 
 
  digitalWrite(13, LOW);
  delay(1000); 
}
````

## B2 實作2-2, RGB LED燈全彩模組, 分別讓LED輪流表現正紅、正綠、正藍，三個顏色，時間間隔1秒鐘。並且觀查LED顏色和波形或是電壓有什麼關連性? 可將個人說明在更新GitHub時一起加入. (互動2), (2021-09-05)
![image](https://user-images.githubusercontent.com/89717315/133887021-cf40fa51-8278-4591-8cc2-725ad38681e7.png)
程式
````c
int R = 9;
int G = 10;
int B = 11;

void setup()
{
  pinMode(R, OUTPUT);
  pinMode(G, OUTPUT);
  pinMode(B, OUTPUT);  
}

void loop()
{
	analogWrite(R, 255);
	analogWrite(G, 0);
	analogWrite(B, 0);
  	delay(1000);
	analogWrite(R, 0);
	analogWrite(G, 255);
	analogWrite(B, 0);
  	delay(1000);
	analogWrite(R, 0);
	analogWrite(G, 0);
	analogWrite(B, 255);
  	delay(1000);  
}
````

## 實作2-3, 讓你的RGB LED燈全彩模組也可會"呼吸", LED顏色變化是否有像"呼吸的效果"和示波器的波形有什麼關連性?
![image](https://user-images.githubusercontent.com/89717315/133887114-5b19045f-34ed-4c5a-a17b-5cd22b8a3567.png)
程式
````c
int brightness = 0;
int Red = 9;
int Blue = 11;
int Green = 10;
void setup()
{
  pinMode(Red, OUTPUT);
  pinMode(Blue, OUTPUT);  
  pinMode(Green, OUTPUT);  
  
  Serial.begin(9600); 
}
void loop()
{
  Serial.println("START");

  for (brightness = 0; brightness <= 255; brightness += 5) {
    analogWrite(Red, brightness);
    delay(50); 
  }
  for (brightness = 255; brightness >= 0; brightness -= 5) {
    analogWrite(Red, brightness);
    delay(50); 
  }
  delay(1000); 
  

  for (brightness = 0; brightness <= 255; brightness += 5) {
    analogWrite(Blue, brightness);
    delay(50); 
  }
  for (brightness = 255; brightness >= 0; brightness -= 5) {
    analogWrite(Blue, brightness);
    delay(50); 
  }  
  delay(1000); 
  

  for (brightness = 0; brightness <= 255; brightness += 5) {
    analogWrite(Green, brightness);
    delay(50); 
  }
  for (brightness = 255; brightness >= 0; brightness -= 5) {
    analogWrite(Green, brightness);
    delay(50); 
  }  
  delay(1000);   
  Serial.println("END");  
}
````


## 實作2-4 analogRead(), 1024解析度 (i.e.,10-bit): 可變電阻 + 序列監視器與輸出; 當你改變可變電阻的阻值(e.g., 10K-ohm)時，序列監視器輸出的數值有什麼改變? 數值又有什麼意義呢?
![image](https://user-images.githubusercontent.com/89717315/133887939-9e50f790-7499-4777-8c9f-5bc3c597e26c.png)
程式
````c
void setup() {
  Serial.begin(9600);
}

void loop() {
  // read the input on analog pin 0:
  int sensorValue = analogRead(A0);
  // Convert the analog reading (which goes from 0 - 1023) to a voltage (0 - 5V):
  float voltage = sensorValue * (5.0 / 1023.0);
  // print out the value you read:
  Serial.println(voltage);
}
````
