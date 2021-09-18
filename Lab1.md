# 嵌入式系統 - 實作1

## 1-1 在TinkerCAD開一個新的Circuit, 加上一個外部的LED, 並且ON (亮) 1秒, OFF(滅) 1秒
![image](https://user-images.githubusercontent.com/89717315/131237923-ab33f410-7b87-433b-82c7-16c6e312d5fa.png)
程式
````c
void setup()
{
  pinMode(LED_BUILTIN, OUTPUT);
}

void loop()
{
  digitalWrite(LED_BUILTIN, HIGH);
  delay(1000); 
  digitalWrite(LED_BUILTIN, LOW);
  delay(1000); 
}
````

## 1-2 在TinkerCAD開一個新的Circuit, 分別使甪R, G, B三種顏色的LED, ON (亮) 0.5秒, OFF(滅) 0.5秒
![image](https://user-images.githubusercontent.com/89717315/133887382-9a4fcbc3-5d55-4cbb-85ce-c95748bb4e7d.png)
程式
````c
void setup()
{
  pinMode(13, OUTPUT);
  pinMode(11, OUTPUT);
  pinMode(9, OUTPUT);  
}

void loop()
{
  digitalWrite(13, HIGH);
  digitalWrite(11, HIGH);
  digitalWrite(9, HIGH);  
  delay(500); 
  
  digitalWrite(13, LOW);
  digitalWrite(11, LOW);
  digitalWrite(9, LOW);  
  delay(500); 
}

````

## 1-**3 在**TinkerCAD開一個新的Circuit, 分別使甪R, G, B三種顏色的LED, 讓LED ON, OFF的順序為R >> G >> B >> G >> R .... 無限循環.
![image](https://user-images.githubusercontent.com/89717315/133887472-89113439-e3b6-4b74-8cd3-b88a8fd08bbc.png)

程式

````c
void setup()
{
  pinMode(13, OUTPUT);
  pinMode(11, OUTPUT);
  pinMode(9, OUTPUT);
}

void loop()
{
  digitalWrite(13, HIGH);
  digitalWrite(11, LOW);
  digitalWrite(9, LOW);
  delay(500); 
  
  digitalWrite(13, LOW);
  digitalWrite(11, HIGH);
  digitalWrite(9, LOW);
  delay(500);
  
  digitalWrite(13, LOW);
  digitalWrite(11, LOW);
  digitalWrite(9, HIGH);
  delay(500);   
  digitalWrite(13, LOW);
  digitalWrite(11, HIGH);
  digitalWrite(9, LOW);  
  delay(500);   
}
````
