---
title: Python学习笔记整理
abbrlink: 3a17j916
cover: https://about.gitlab.com/images/blogimages/python.jpg
tags:
  -  编程
  -  Python
  -  编程学习
  


---
## 前言

​     这个是之前自己看mosh的python教学视频做的笔记，一直留存在onenote里面，所以既然建了这个博客，就把这些笔记当时敲的基础代码发上来，记录下！！！当时只是粗略的记录下，所以只是写基本的概念！！

## Python里的术语和概念

- 矩阵

- 列表【remove insert等改变，添加或删除列表中的数字】

- 元组

- 坐标

- 字典【对象】

- 自定义函数

- 实参

- 形参

- 关键字参数

- 返回值【ruturn】

- try_exception

- 注释

- 类【class】

- 构造函数【self】

- 继承

- 模块

- package【包】

- 目录【Path】【查找路径】【glob搜寻路径中的所有特定文件，】

- 相对路径

- 绝对路径

- python网站的公开数据包

- excel表格批量处理实战 

- 机器学习【csv格式data文件】

- music机器学习项目步骤（见下面分步），推送音乐等

- 网站开发【django】

  

  ### Python机器学习的步骤

​    **1.导入数据**

​     **2.整理清洁数据删掉无用的【分为input和output】**

​     **3.创建模型和算法【决策树】**

​     **4.训练模型**

​     **5.预测数据**

​     **6.修改算法** 





## 敲的Python代码



### Pycharm里的练习

- 从hello world开始探寻世界

```python
print("hello world")
```

- input输入函数使用

```python
name = input('what is your name? ')
print('hello '+ name)

```

- 教程里的根据用户喜好推送音乐案列

```python
import pandas as pd
from sklearn.tree import DecisionTreeClassifier

music_data = pd.read_csv("music.csv")
X = music_data.drop(columns=["genre"])
Y = music_data['genre']
model = DecisionTreeClassifier()

model.fit(X, Y)
music_data

```

- 表示从p开始的所有词组，也就是完整句子

```python
course = 'python for begainners'
print(course[0:])

```

- 表示从y开始后面的所有词组

```python
course = 'python for begainners'
print(course[2:])

```

- 中括号和冒号代表和上面的字符串一模一样 

```python
course = 'python for begainners'
another = course[:]
print(another)

```

- 中括号和冒号代表和上面的字符串一模一样

```python
name = 'zhangjinhui is coder'
another_name = name[:]
print(another_name)

```

- 格式化字符串

```python
first = 'john'
last = 'smith'
message = first + ' [' + last + '] is a coder'
msg = f'{first} [{last}] is a coder'
print(msg)

```

- 把小写改成大写

```python
python = 'zhangjinhui are good'
print(python.upper())

```

- 把大写改成小写

```python
course = 'python for begainers'
print(course.upper())
print(course.lower())

```

- 找到字幕在句子中的位置

```python
course = 'python for begainners'
print(course.find('a'))

```

- 替换词语，把逗号前面的改成后面的

```python
course = 'python for begainners'
print(course.replace('begainner','abslutly begainners'))

```

### 在线软件Replit里练习

**这些代码没有中文说明，只是把代码敲了一遍而已，不是像上面一样的！** 

```python
name = ['tom' , 'lee', 'jack']
print(name[:3])

name = 'tom'
age = 18
is_new_painent = True

Number = []
Number.append(20)
Number.append(50)
Number.append('This is not fuck your business!')
print(Number)

num = 50
num += 50
print(num)

num -= 100
print(num)

num /= 100
print(num)

numbers = [1000,2000,3000,5000,1000000000]
print(numbers)

```

**同上，下面的代码也是没有中文说明，以下是刚刚开始学习mosh关于python的视频笔记的时候记录的，算是最早记录的代码了，一边看，一遍敲！也是挺长的，不知道怎么排版了，很长！！高能！！！！！以下都是在Pycharm跟着敲的练习！**

### Pycharm里的练习

#### 第一部分

```python
command = ""
started = False
while True:
    command = input("> ").lower()
    if command == "start":
        if started:
            print('the car alreay started!')
        else:
            started = True
            print('car started')
    elif command  == 'stop':
        if not started:
            print('car already stopped!')
        else:
            started = False
            print('car stoped')
    elif command == "help":
        print("""
        start to go
        stop
        quit
        """)
    elif command == 'quit':
        break
    else:
        print('sorry i cant understand!')

```

#### 第二部分

```python
prices = [10,20,30]

total = 0
for price in prices:
    total += price
print(f"total: {total}")

for x in range(4):
    for y in range(3):
        print((x,y))

numbers = [5, 2, 5, 2, 2]
for item in numbers:
    print('x'* item)

numbers = ['1', '2', '3', '4']
max = numbers[0]
for number in numbers:
    if number > max:
        max = number
print(max)

matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
for row in matrix:
    for item in row:
        print(item)

```

#### 第三部分

```python
numbers = [2, 4, 6, 8, 10]
numbers.append(30)
print(numbers)

numbers = [2, 4, 6, 8, 10]
numbers.insert(0,20)
print(numbers)

numbers = [2, 4, 6, 8, 10]
numbers.remove(10)
print(numbers)

numbers = [2, 4, 6, 8, 10]
numbers.clear()
print(numbers)

numbers = [2, 4, 6, 8, 10]
numbers.pop()
print(numbers)

numbers = [2, 4, 6, 8, 10]
print(numbers.index(10))

numbers = [2, 4, 6, 8, 10]
print(50 in numbers)

numbers = [2, 4, 6, 8, 6,  10]
numbers.sort()
numbers.reverse()
print(numbers)

numbers = [2, 4, 6, 8, 6,  10]
numbers2 = numbers.copy()
print(numbers2)

numbers = [2, 4, 6, 6, 8, 6, 10]
numbers2 = []
for number in numbers:
    if number not in numbers2:
        numbers2.append(number)
print(numbers2)

```

#### 第四部分

**可能但是有涉及后面用dj制作网站，所以跟着mosh老师一直敲，前面基础的多听几遍就还好，到后面dj搭建网站的时候，就有点听不懂了，但是代码还在跟着敲，所以就有了以下，有点乱且很长！！见谅！** 

```python
coordinates = (1, 2, 3)
x,y,z = coordinates
print(x)

coordinates = [1, 2, 3]
x,y,z = coordinates
print(x)

customer = {
    "name": "john smith",
    "age": 20,
    "is_veritify": True
}
customer["name"] = "jack smith"
print(customer["name"])

phone = input("phone: ")
digital_mapping = {
    "1": "one",
    "2": "two",
    "3": "three",
    "4": "four",
}
output = ""
for ch in phone:
    output += digital_mapping.get(ch, "!") + ""
print(output)

message = input("> ")
words = message.split(' ')
emojis = {
    "sunshine": "笑脸"
}
output = ""
for word in words:
    output += emojis.get(word, word) + " "
print(output)

def greet_user(first_name,last_name):
    print(f'hi {first_name} {last_name}!')
    print('welcome aboard')

print("start")
greet_user("john","smith")
print("finish")

def square(number):
    print(number * number)

print(square(3))

def emojis_converter(message):
    words = message.split(' ')
    emojis = {
        "sunshine": "笑脸"
    }
    output = ""
    for word in words:
        output += emojis.get(word, word) + " "
    return output

message = input(">")
print(emojis_converter(message))

try:
    age = float(input('age: '))
    print(age)
except ValueError:
    print('Invalid value')

class Point:
    def __init__(self,x,y):
        self.x = x
        self.y = y
    def move(self):
        print("move")

    def draw(self):
        print("draw")

point = Point(10,20)
print(point.x)

class Person:
    def __init__(self, name):
        self.name = name

     def talk(self):
        print(f"hi,i am {self.name}")

john = Person("john smith")
john.talk()

bob = Person("bob smith")
bob.talk()

class Mammal:
    def walk(self):
        print("walk")

class Dog(Mammal):
    def bark(self):
        print('bark')

class Cat(Mammal):
    def be ananying

dog1 = Dog()
dog1.bark()

import converters
from converters import kg_to_lbs

kg_to_lbs(80)

print(converters.kg_to_lbs(70))


def lbs_to_kg(weight):
    return weight * 0.45

def kg_to_lbs(weight):
    return weight / 0.45

def find_max(numbers):
    max = numbers[0]
    for number in numbers:
        if number > max:
            max = number
    return max

import utils
from utils import.find_max()

numbers = [10, 2, 6, 12]
max = find_max(numbers)
print(max)

numbers = [10, 2, 6, 12]
print(max)

from ecommerce import shipping

shipping.calc_shipping()

import random
for i in range(3):
    print(random.randint(80,100))

members = ['john','mary', 'bob','mosh']
leader = random.choice(members)
print(leader)

import random
class Dice:
    def roll(self):
        first = random.randint(1,6)
        second = random.randint(1,6)
        return first, second

dice =  Dice()
print(dice.roll())

from pathlib import Path

path = Path()
for file in path.glob('*'):
    print(file)

import openpyxl as xl
from openpyxl.chart import BarChart, Reference

def process_workbook(filename):

    wb = xl.load_workbook(filename)
    sheet = wb["Sheet1"]

    for row in range(2, sheet.max_row + 1):
        cell = sheet.cell(row, 3)
        correct_price = cell.value * 0.9
        correct_price_cell = sheet.cell(row, 4)
        correct_price_cell.value = correct_price

    value = Reference(sheet,
              min_row=2,
              max_row=sheet.max_row,
              min_col=4,
              max_col=4)

    chart = BarChart()
    chart.add_data(value)
    sheet.add_chart(chart, 'e2')

    wb.save(filename)

print()

i="zhangjinhui"
print(i)
print(3+15)

```



## 结语

​       这就是当时的笔记，很乱哦，可能只是供我自己看看自己过去跟着学习的样子吧，别人看估计看不懂，当然大拿肯定是能看懂的啦！！哈哈，这就是当初在B站看mosh的6小时学python的视频教程，总共记得笔记和跟着敲的代码，放上来吧，记录下！！！



**PEACE !** 
