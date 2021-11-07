# 實作7: AI-based ES? AI? ML? DL? 要如何入門 (How To Learn)?

## Lab 7-1 在你的Google Drive建立你的第一個Colab Notebook

1. 安裝Colab
2. 新增ES2021的Folder
3. 在此Folder下, 建立你的第一個Colab Notebook (i.e. 'hello-ai'). 將你的Google Drive和Google VM (Virtual Machine)掛接
4. 在你Colab Notebook顯示以下訊息(OOO: 你的英文名字; e.g., Joe biden)
5. 新增文字儲存格 (請用你的英文名字)
### 實作成果:

<div align="center">
     <img 
      src="https://user-images.githubusercontent.com/89717315/140635004-94d40fa5-c7af-4931-82aa-daaf578a521d.png" 
      width="60%" height="50%">
    </div>

---

## Lab 7-2 十分鐘學會Python!? Really?

### 程式:
````python
# task 1: string variable
name = "YUNEN"
print(name)

# task 2: number variable
number = 26
print(number)
print(number*3)
print(number/2)
print(number + number)
print(number - number)

# task 3: function

def printName(firstName, lastName):
  print(lastName + ' ' + firstName)

printName('YUNEN', 'WEI')

# task 4: if else

def printName(firstName, lastName, isCool):
  if isCool:
    print(lastName + ' ' + firstName + ' very cool!')
  else:
    print(lastName + ' ' + firstName + ' not cool!')

# Start
printName('YUNEN', 'WEI', True)
printName('YUNEN', 'WEI', False)

# task 5: for loop

def printName(firstName, lastName, isCool, num):
  for i in range(1, num):
    if isCool:
      print(i, lastName + ' ' + firstName + ' very cool!')
    else:
      print(i, lastName + ' ' + firstName + ' not cool!')

# Start
printName('YUNEN', 'WEI', True, 10)

````

### Task 5的結果:

<div align="center">
     <img 
      src="https://user-images.githubusercontent.com/89717315/140645140-623ab7cd-a240-4700-9009-ac9ee6103eb4.png" 
      width="60%" height="50%">
    </div>
   
---



## Lab 7-3 確認Lab7完成的兩個筆記本都成功的存在你的雲端硬盤碟/ES2021目錄下↓


<div align="center">
     <img 
      src="https://user-images.githubusercontent.com/89717315/140635332-0e0efc0a-c2e9-4fd3-959a-9faab75b6d87.png" 
      width="60%" height="50%">
    </div>
    
