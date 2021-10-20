# 嵌入式系統 - 實作4: 七段顯示器, LCD 顯示器 + 超音波感測器
## Lab 4-1 用七段顯示器來顯示數字"8."
![chrome-capture](https://user-images.githubusercontent.com/89717315/138009986-ec98d2e3-3999-4622-b68d-5b23a39a3c4e.gif)
程式
````C
void setup()
{
for(int x = 1; x < 9; x++) {
pinMode(x,OUTPUT);
}
}

void seg71(int a, int b, int c, int d, int e, int f, int g, int h)
{
digitalWrite(1, a);
digitalWrite(2, b);
digitalWrite(3, c);
digitalWrite(4, d);
digitalWrite(5, e);
digitalWrite(6, f);
digitalWrite(7, g);
digitalWrite(8, h);
delay(500);
}

void loop()
{
//    a, b, c, d, e, f, g, h
seg71(0, 0, 0, 0, 0, 0, 0, 0); // OFF
seg71(1, 1, 1, 1, 1, 1, 1, 1); // 8
}
````
## Lab 4-2 如下圖的Demo, 用七段顯示器, 顯示 . →1→ ... → 9 → 0 → 全滅, 狀態改變的間隔時間為0.5秒

![chrome-capture (2)](https://user-images.githubusercontent.com/89717315/138010736-ec3fdd67-960a-490e-8f7e-3add64f49338.gif)

程式

````C
void setup()
{
  for(int x = 1; x < 9; x++)
  {
  	pinMode(x,OUTPUT);
  }
}

void seg71(int a, int b, int c, int d, int e, int f, int g, int h)
{
  digitalWrite(1, a);
  digitalWrite(2, b);
  digitalWrite(3, c);
  digitalWrite(4, d);
  digitalWrite(5, e);
  digitalWrite(6, f);
  digitalWrite(7, g);
  digitalWrite(8, h);
  delay(500);
}

void loop()
{
  //    a, b, c, d, e, f, g, h
  seg71(0, 0, 0, 0, 0, 0, 0, 0); // OFF
  seg71(1, 1, 1, 1, 1, 1, 0, 1); // 0
  seg71(0, 1, 1, 0, 0, 0, 0, 1); // 1
  seg71(1, 1, 0, 1, 1, 0, 1, 1); // 2
  seg71(1, 1, 1, 1, 0, 0, 1, 1); // 3
  seg71(0, 1, 1, 0, 0, 1, 1, 1); // 4
  seg71(1, 0, 1, 1, 0, 1, 1, 1); // 5
  seg71(1, 0, 1, 1, 1, 1, 1, 1); // 6
  seg71(1, 1, 1, 0, 0, 0, 0, 1); // 7
  seg71(1, 1, 1, 1, 1, 1, 1, 1); // 8
  seg71(1, 1, 1, 1, 0, 1, 1, 1); // 9
}
````
