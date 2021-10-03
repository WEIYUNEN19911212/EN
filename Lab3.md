## Lab 3-1: Ultrasonic Sensor (3-pin) + 測距 (以公分顯示即可) + RS232 Output, [Video] 
### 利用 pinMode() 設定編號 7 腳位( SIG )為數位輸出，設定為 LOW (i.e., digitalWrite(tPin, LOW);) 維持 2us，目的為將超音波模組設定 **RESET**。

將編號 7 腳位 (SIG) **設定為 HIGH，並維持10us，觸發超音波模組**。最後將編號7腳位 (SIG) 設定為 LOW (此時仍為OUTPUT )後，接著將編號 7 腳位設定為 INPUT 準備接收模組回傳的脈波訊號。
![chrome-capture (1)](https://user-images.githubusercontent.com/89717315/134792940-9567075a-f27d-4516-83c5-adea2780e365.gif)
## 電路圖
![chrome-capture (2)](https://user-images.githubusercontent.com/89717315/134793213-73276d75-e857-46ad-9054-44687e207a30.gif)
## 程式
````c

int inches = 0;

int cm = 0;

long readUltrasonicDistance(int triggerPin, int echoPin)
{
  pinMode(triggerPin, OUTPUT);
  digitalWrite(triggerPin, LOW);
  delayMicroseconds(2);
 
  digitalWrite(triggerPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(triggerPin, LOW);
  pinMode(echoPin, INPUT);
 
  return pulseIn(echoPin, HIGH);
}

void setup()
{
  Serial.begin(9600);

}

void loop()
{
 
  cm = 0.01723 * readUltrasonicDistance(7, 7);
  inches = (cm / 2.54);
  Serial.print(inches);
  Serial.print("in, ");
  Serial.print(cm);
  Serial.println("cm");
  delay(100); 
}
````
## Lab 3-2: 超音波感測器 + LED (紅色LED:亮<70cm, 緑色LED: 亮>270cm, 藍色LED:亮, 介於70cm ~ 270cm之間) + RS232 Output
![chrome-capture (3)](https://user-images.githubusercontent.com/89717315/134793587-4666d207-890e-407a-97d8-13a50b78970b.gif)
## 程式
````c
const int Red = 13;
const int Green = 10;
const int Blue = 11;

int inches = 0;

int cm = 0;

long readUltrasonicDistance(int triggerPin, int echoPin)
{
  pinMode(triggerPin, OUTPUT); 
  digitalWrite(triggerPin, LOW);
  delayMicroseconds(2);
  
  digitalWrite(triggerPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(triggerPin, LOW);
  pinMode(echoPin, INPUT);
  return pulseIn(echoPin, HIGH);
}

void changColor(int type){
  analogWrite(Red,0);
  analogWrite(Green,0);
  analogWrite(Blue,0);
  switch (type){
    case 1:
    analogWrite(Red,255);
    analogWrite(Green,0);
    analogWrite(Blue,0);
    break;
    case 2:
    analogWrite(Red,0);
    analogWrite(Green,255);
    analogWrite(Blue,0);
    break;
    case 3:
    analogWrite(Red,0);
    analogWrite(Green,0);
    analogWrite(Blue,255);
    break;
  }
}

void setup()
{
  Serial.begin(9600);

}

void loop()
{
  
  cm = 0.01723 * readUltrasonicDistance(7, 7);

  if(cm <70)
  {
    changColor(1);
  }
  else if(cm>= 270)
  {
    changColor(2);
  }
  else if(cm>= 70&& cm<270)
  {
    changColor(3);
  }
  
  inches = (cm / 2.54);
  Serial.print(inches);
  Serial.print("in, ");
  Serial.print(cm);
  Serial.println("cm");
  delay(100); 
}
````
## Lab 3-3: Arudino常用的C語言程式介紹與實作
##### 請使用Arudino, 通過Serial印出9X9乘法表, 計算時亮紅色LED, 綠色LED慢慢變亮亮完成時全亮, 並且紅色LED OFF, 細節可參考以下Demo作法:
![chrome-capture (1)](https://user-images.githubusercontent.com/89717315/135738556-52093680-92af-496e-ab8b-7bc4637def1f.gif)
## 程式
````c
/*
 Lab 3-3, Embedded System, VNU
 Date: 2021/09/26
*/
int RLED = 13;
int GLED = 11;


int result, result2, result3;
String d0 = "****** 9X9 Table ******";
String d1, d2, d3;
void setup()
{
  pinMode(RLED, OUTPUT);   // Configure PIN13
  pinMode(GLED, OUTPUT);   // Configure PIN11
  
  Serial.begin(9600);

}

void loop()
{
  int aa = 0;

  Serial.println(d0); 
  
  digitalWrite(RLED, HIGH);
  analogWrite(GLED, aa); 
  
  for (int i=1;i<=9; i=i+3){
    for (int j=1;j<=9; j++){
      
      result = i*j;
      result2 = (i+1)*j;
      result3 = (i+2)*j;
      
      d1 = String(String(i) + "X" + String(j) + "=" + String(result));
      d2 = String(String(i+1) + "X" + String(j) + "=" + String(result2));
      d3 = String(String(i+2) + "X" + String(j) + "=" + String(result3));
      
      Serial.println(d1 + ", " + d2 + ", " + d3);


       
      aa+=1;
      
      delay(100);
    } // loop j
    analogWrite(GLED, aa*3); 
    Serial.println("");
  } // loop i

  digitalWrite(RLED, LOW);
  analogWrite(GLED, 255); 
  delay(2000);	
  analogWrite(GLED, 0);
}
````
