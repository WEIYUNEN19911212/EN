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
