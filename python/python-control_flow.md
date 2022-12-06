# 控制流
目录
- [知识点总结](#知识点总结)
    - [布尔值](#布尔值)
    - [比较操作符](#比较操作符)
    - [布尔操作符](#布尔操作符)
    - [条件判断](#条件判断)
    - [循环](#循环)
    - [导入模块](#导入模块)
- [练习](#练习)
---
# 知识点总结

### 布尔值
> “布尔”数据类型只有两种值：True 和 False。
```python
# 定义变量 x 为布尔值
x=True
print('x变量的值为：',x)
# 打印变量 x 的类型
print('x变量的类型为：',type(x))
if(x):
    print('布尔值常用于条件判断')
```
运行结果：
```sh
x变量的值为： True
x变量的类型为： <class 'bool'>
布尔值常用于条件判断
```
总结：
1. 注意首字母一定要大写
2. 布尔值的类型为 bool

### 比较操作符
> “比较操作符”比较两个值，求值为一个布尔值。

表1 比较操作符

| 操作符 | 含义     |
| ------ | -------- |
| ==     | 等于     |
| !=     | 不等于   |
| <      | 小于     |
| >      | 大于     |
| <=     | 小于等于 |
| >=     | 大于等于 |

```python
# == 等于
print('42 == 42 的值是',42 == 42)
# != 不等于
print('2 != 3 的值是',2 != 3)
# 比较字符串
print("'hello' == 'hello' 的值是",'hello' == 'hello')
print("'hello' == 'Hello' 的值是",'hello' == 'Hello')
# 比较布尔值
print('True == True 的值是',True == True)
# 比较整数和浮点数是否相等
print('42 == 42.0 的值是',42 == 42.0)
# 比较数字和字符串是否相等
print("97 == 'a' 的值是",97 == 'a')
# 比较字符串大小
print("'hello' > 'Hello'",'hello' > 'Hello')
print("'狗' > '猫' 的值是",'dog' > 'cat')
# 比较字符串和数字的大小
print("'狗' > 45 的值是",'狗' > 45)
```
运行结果：
```sh
42 == 42 的值是 True
2 != 3 的值是 True
'hello' == 'hello' 的值是 True
'hello' == 'Hello' 的值是 False
True == True 的值是 True
42 == 42.0 的值是 True
97 == 'a' 的值是 False
'hello' > 'Hello' True
'狗' > '猫' 的值是 True
Traceback (most recent call last):
  File "C:\Users\huanglei\Desktop\test1.py", line 10, in <module>
    print("'狗' > 45 的值是",'狗' > 45)
TypeError: '>' not supported between instances of 'str' and 'int'
```
总结：
1. ==和!=操作符实际上可以用于所有数据类型的值。
2. 整型和浮点型的值可以比较。
3. 数字永远不会与字符串相等。
4. 数字、字符串可以比较，但不好理解，甚至会出现错误，应避免这样使用。
5. 不用考虑c语言中字符和数字的关系，想简单点，数字和字符不一样。

### 布尔操作符
> 像比较操作符一样，"布尔操作符"将这些表达式求值为一个布尔值。
```python
# 与运算
print(True and True)
print(0 and 1)
# 或运算
print(True or 0)
# 反运算
print(not 0)
print(not not 0)
# 混合运算
print(True and not 0)
# 其他类型的值进行布尔运算
print(1 and 2)
print(2 and 1)
print(True and 2)
```
运行结果：
```sh
True
0
True
True
False
True
2
1
2
```
总结：
1. and与运算，or或运算，not取反
2. 1和0在布尔运算时，大部分情况可以当作True和False使用
3. 多种操作符可以混合使用
4. 其他数字进行布尔操作时，会很难理解，所以应避免这样使用

### 条件判断
> 条件判断主要使用if，elif，else来满足逻辑需要
#### if 语句
```python
if(True):
    print('执行 if 子句')
    print('还在 if 子句内')
print('缩进结束时，离开了 if 子句')
```
如果条件为真，执行子句中的代码。if 语句包含以下部分：
- if 关键字
- 条件（即求值为 True 或 False 的表达式）
- 冒号
- 在下一行开始，缩进的代码块(条件为**真**时执行)
- 缩进结束时, if 语句结束

#### else 语句
```python
if(False):
    print('条件为真时执行 if 子句内容')
else:
    print('if 条件为假时，执行 else 子句内容')
```
else 语句跟在 if 语句后面, else 语句不包含条件,但包含以下部分：
- else 关键字
- 冒号
- 在下一行开始，缩进的代码块(条件为**假**时执行)
- 缩进结束时, else 语句结束

#### elif 语句
```python
if(False):
    print('条件为真时执行 if 子句内容')
elif(True):
    print('if 条件为假时，并且 elif 条件为真时执行 elif 子句内容')
```
elif 语句跟在 if 语句或 elif 语句后面, elif 语句包含以下部分：
- elif 关键字
- 条件
- 冒号
- 在下一行开始，缩进的代码块
- 缩进结束时, elif 语句结束

#### 案例
```python
#旅游景点门票费用
身高=1.52
年龄=9
国籍='中国'
if(国籍!='中国'):
    print('外宾票：300元')
elif(身高<=1.4 or 年龄<=12):
    print('儿童票：60元')
elif(年龄>60):
    print('老人免费：0元')
else:
    print('成人票：120元')
```
运行结果：
```sh
儿童票：60元
```
程序的逻辑用流程图表示，如下图所示

![门票费用判断逻辑](https://uinx1983.github.io//img/control-flow-1.svg)

<div style="text-align:center">图1 费用判断流程图</div>

总结：
1. 首先用 if 语句判断是否外国人
2. 在第1步的基础上，也就是中国人的基础上，接着用 elif 语句判断是否儿童，再判断是否老人
3. 最后用 else 把前面任何情况都不满足的进行处理

### 循环
> 重复执行一段代码，主要由 for 和 while 两种循环实现

#### while 语句
```python
while(True):
    print('该内容会一直重复执行，形成死循环')
```
只要 while 语句的条件为 True，while 子句中的代码就会执行。在代码中，while 语句总是包含下面几部分：
- while 关键字
- 条件
- 冒号
- 在下一行开始，缩进的代码块(条件为**真**时执行)
- 缩进结束时, while 语句结束

#### for 循环
如果你想让一个代码块执行固定次数，可以通过 for 循环语句实现
```python
for i in range(5):
    print(f'打印第{i}次')
```
Python 中的 for 语句像以上这样，总是包含以下部分：
- for 关键字
- 一个变量名（例子中是 i ）
- in 关键字
- 一个序列（例子中是 range(5) ）
- 冒号
- 在下一行开始，缩进的代码块(执行序列元素个数的次数)
- 缩进结束时, for 语句结束

#### range() 函数
内置函数 range() 常用于遍历数字序列，配合 for 使用。
```python
range(5) #代表0，1，2，3，4 的序列，默认从0开始，增幅为1
range(0,5) #和上面等价
range(1,6) #代表从1开始的5个数
range(0,5,2) #代表0,2,4 的序列，幅度为2
```

#### break语句
break 语句和 C 中的类似，用于跳出最近的 for 或 while 循环。
```python
while True:
    response = input('输入exit退出循环：')
    if response == 'exit':
        break
    print('输入不正确，循环继续')
print('循环结束!')
```
#### continue 语句
continue 语句也借鉴自 C 语言，表示继续执行循环的下一次迭代。
```python
for num in range(2, 10):
    if num % 2 == 0:
        print("找到偶数", num)
        continue
    print("找到奇数", num)
```

总结：
1. 当不确定循环的次数时，选择 while 循环更恰当。
2. 当不小心进入死循环时，用 `ctrl+c` 快捷键终止程序。
3. Python 中的 for 循环一般用于次数固定的循环。
4. 灵活应用break、continue来优化逻辑，完成需求。

### 导入模块
> 除了内置的基本函数，比如print()、input()等，在使用 Python 提供的标注库或者第三方库之前，必须用 import 语句导入该模块。

```python
# 导入 random 模块
import random
for i in range(2):
    print(random.randint(1, 10))
# 导入 random 模块中的 randint 函数
from random import randint
for i in range(2):
    print(randint(1, 10))
# 导入 math 模块，并取名为 m
import math as m
print(m.sqrt(5))
# 导入多个模块
import random, sys, os, math
# 导入 math 模块的所有函数
from math import *
print('取对数:',log2(32))
print('最大公约数:',gcd(45, 69))
```
运行结果：
```sh
3
5
4
9
2.23606797749979
取对数: 5.0
最大公约数: 3
```
总结：
1. import random 导入整个random模块，模块里的所有函数都可以使用
2. from random import randint 导入指定的函数，使用时不用写模块名
3. 导入时，可以用as关键字取别名，方便使用
4. 可以用逗号分隔，一行导入多个模块
5. from math import * 导入math模块的所有函数，使用时不用写模块名，但大型项目中不推荐用该方式，因为可能导致函数名重复
6. 导入可以放在代码中间（解释型语言特性决定的）
7. Python 的标准库中有许多有用的模块，比如 math 模块有数学运算相关的函数，random 模块有随机数相关的函数，等等。

# 练习
1. 基础练习（必做，个人完成）

    - 完成[基础练习-2](/python/lab/lab-2.md)

2. 综合项目（二选一，分组完成）
    - 难度稍低[综合项目-1-用户登录](/python/problem/problem-1-login.md)
    - 难度稍高[综合项目-1-整除](/python/problem/problem-1-divide.md)
