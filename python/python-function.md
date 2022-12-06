# 函数
目录
- [知识点总结](#知识点总结)
    - [自定义函数](#自定义函数)
    - [参数](#参数)
    - [返回值](#返回值)
    - [异常处理](#异常处理)
- [练习](#练习)
---
# 知识点总结

### 自定义函数
> 函数的一个主要目的就是将需要多次执行的代码放在一起，方便重复使用。函数的定义使用 def 关键字。
```python
# 定义一个名为hello的函数
def hello():
# 函数内部代码
    print('你好!')
    print('你好!!')
    print('你好!!!')
# 调用hello函数
hello()
```
运行结果：
```sh
你好!
你好!!
你好!!!
```
总结：
1. def 定义一个函数
2. 函数的内部代码，必须缩进
3. 在代码中调用函数
4. 函数如果不被调用，函数内部代码不会被执行
5. 函数可以被重复调用

### 参数
> 参数使得函数功能性更强，函数支持任意数量的参数。
```python
# 定义一个名为hello的函数，并定义2个参数name和times
def hello(name,times):
# 循环times的次数
    for i in range(times):
        # 打印name的值
        print(f'你好，{name}!')
# 调用hello函数，按顺序传递参数
hello('张三',3)
```
运行结果：
```sh
你好，张三!
你好，张三!
你好，张三!
```

#### 默认值参数
> 为参数指定默认值，可以在调用函数时不传该参数的值
```python
# 定义一个名为hello的函数，并定义普通参数name和times参数的默认值
def hello(name,times=3):
# 循环times的次数
    for i in range(times):
        # 打印name的值
        print(f'你好，{name}!')
# 调用hello函数，times参数有默认值，可以省略
hello('张三')
```
运行结果：
```sh
你好，张三!
你好，张三!
你好，张三!
```

#### 关键字参数
> 如果想不按顺序传递参数值，可以使用关键字参数
```python
# 定义一个名为hello的函数，并定义普通参数name和times参数的默认值
def hello(name,times=3):
# 循环times的次数
    for i in range(times):
        # 打印name的值
        print(f'你好，{name}!')
# 调用hello函数，使用参数的名称指定值
hello(times=2,name='张三')
# 以下使用方式是错误的，有歧义
#hello(times=2,'张三')
```
运行结果：
```sh
你好，张三!
你好，张三!
```

总结：
1. 参数可以有多个，调用时要注意顺序
2. 默认值参数调用时可以省略
3. 默认值参数不能放在普通参数之前，否则调用时有歧义
4. 使用关键字参数进行传值时，可以不按函数定义的参数顺序
5. 如果混合使用普通参数和关键字参数，关键字参数不能在普通参数之前

### 返回值
> return 关键字用于函数返回值

```python
def get():
    x=1
def getNone():
    return
def get0():
    return 0
def get_sum(x,y):
    return x+y
#调用get
print(get())
#调用getNone
print(getNone())
#调用get0
print(get0())
#调用get_sum
print(get_sum(1,2))
```
运行结果：
```sh
None
None
0
3
```
总结：
1. 默认所有函数都有返回值，如果不指定则为 None
2. 只写 return ，不写特定返回值，返回值为 None 
3. return 后面写表达式，可以返回表达式的值
4. 函数代码对应过程，返回值对应结果

### 异常处理
> 当不想让程序错误影响程序运行时，我们会用到该机制

```python
#一些代码可能会出现意料之外的情况，比如用户输入时
import sys
#尝试运行正常代码
try:
    num = int(input('请输入一个整数:'))
#代码出异常时
except:
    print('出问题时，执行except的代码！')
    #退出程序
    sys.exit()
#无论如何都要执行的代码
finally:
    print('finnally的代码无论是否有异常，都会执行')
#异常处理外的其他代码
print('这里的代码，异常后不会执行，因为前面出现异常时使用sys.exit()退出了程序')
```
异常时运行结果：
```sh
请输入一个整数:e
出问题时，执行except的代码！
finnally的代码无论是否有异常，都会执行
```
无异常时运行结果：
```sh
请输入一个整数:1
finnally的代码无论是否有异常，都会执行
这里的代码，异常后不会执行，因为前面出现异常时使用sys.exit()退出了程序
```
总结：
1. 把有可能出异常的代码块，放在 try 关键字范围内，并配合 except 关键字处理异常情况
2. 处理异常时，至少是 try 和 except 配对出现，其他关键字可选
3. finnally 里的代码，就算前面有退出的代码，也不能阻止其执行
4. 注意不要为了偷懒，把所有代码都放到 try except 里处理，会影响效率，并且出了问题不能准确定位

# 练习
1. 基础练习（必做，个人完成）

    - 完成[基础练习-3](/python/lab/lab-3.md)

