# Python基础语法
目录
- [知识点总结](#知识点总结)
    - [Hello World](#hello-world)
    - [变量](#变量)
    - [运行程序](#运行程序)
    - [基础计算](#基础计算)
- [练习](#练习)
---
# 知识点总结


### Hello World
> 用一个简单的程序比较下和C语言的不同

C语言
```c
printf("Hello World!\n");
```
Python
```python
print("你好 世界!")
```
总结：
1. 函数的用法和C语言差不多
2. 一行代码结束时不用`;`符号
3. 打印函数自带换行
4. 对中文的支持（utf-8编码）

### 变量
> Python的变量有一些不同

C语言
```c
int i=0;
printf("integer i is %i!\n",i);
```
Python
```python
i=0
print(f"integer i is {i}!")
```
总结：
1. Python的变量不用声明类型，会自动识别类型
2. 格式化打印，在打印字符串前加前缀`f`，变量放`{}`里（这种用法比较直观，但print函数还有其他的方式实现该功能）

### 运行程序
> Python是解释型语言，不需要编译后运行

保存代码文件，例如`test.py`，在命令行中运行命令`python test.py`。
```sh
C:\python>python test.py
integer i is 0!
```
总结：
1. 解释型语言不需要编译就能运行，但需要系统中有相应解释器（安装Python软件时已安装好）
2. Python代码文件的后缀名为py
3. 如果提示未找到文件，请先使用`cd`命令切换到代码文件所在的目录中，再运行。

### 基础计算
> 在Python中数字、字符、字符串的操作和大部分现代语言类似

数字：
```python
i=3+4
j=5*6
print("i的值为",i)
print("j的值为",j)
print("i除j为",i/j)
print("i除j取整为",i//j)
print("i的j次方为",i**j)
```
运行结果:
```sh
C:\python>python test.py
i的值为 7
j的值为 30
i除j为 0.23333333333333334
i除j取整为 0
i的j次方为 22539340290692258087863249
```
总结：
1. 普通的`+、-、*、/、%`等操作
2. 特殊的`**`乘方操作，`//`取整除法

字符串：
```python
print(3 * 'un' + 'ium')
print("u"+'m')
```
运行结果：
```sh
C:\python>python test.py
unununium
um
w
```
总结：
1. 字符串可以用`+`合并（粘到一起），也可以用`*`重复
2. Python中没有严格的字符概念，字符被当作字符串处理
3. 无论是`''`还是`""`都可以用做字符串的符号（他们的区别请查阅[Python 速览-字符串](https://docs.python.org/zh-cn/3/tutorial/introduction.html#id2)）

# 练习
1. 基础练习（必做，个人完成）

    - 完成[基础练习-1](python/lab/lab-1.md)

<!--暂时取消
2. 综合项目（二选一，分组完成）
    - 难度稍低[综合项目-1-查找](python/problem/problem-1-find.md)
    - 难度稍高[综合项目-1-验证合法性](python/problem/problem-1-verify.md)
-->


