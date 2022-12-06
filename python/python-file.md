# 读写文件
目录
- [知识点总结](#知识点总结)
    - [文件和路径](#文件和路径)
    - [文件读写](#文件读写)
    - [shelve模块](#shelve模块)
    - [文件管理](#文件管理)
- [练习](#练习)
---
# 知识点总结

### 文件和路径
> 文件有两个关键属性：“文件名”和“路径”

```python
# windows系统的路径示例，注意 \ 需要转义表示
path='c:\\python\\lab-1.py'
path='c:\\python\\'
# linux 和 mac os系统的路径示例
path='/home/user/lab-1.py'
# 文件名示例
filename='lab-1.py'
```
- 路径指明了文件在计算机上的位置
- windows下根目录是某个盘符，比如 c:\ ，其他操作系统一般是 / 代表根目录

#### 绝对路径和相对路径
```python
# 比如程序在c:\python\lab-1.py,那么和程序同一文件夹的文件test.text，可以如下两种表示
# 绝对路径
path='c:\\python\\test.txt'
# 相对路径
path='test.txt'
```
- “绝对路径”，总是从根目录开始
- “相对路径”，它相对于程序的当前工作目录

#### 路径的常用操作
```python
import os
path='c:\\python\\test.txt'
# 获取最后一个 \ 之前的内容，这里获取的是 test.txt 所在文件夹的路径
dirname=os.path.dirname(path)
print(dirname)
# 获取最后一个 \ 之后的内容，这里获取的是文件名
filename=os.path.basename(path)
print(filename)

```
运行结果
```
c:\python
test.txt
```
- os.path.dirname() 常用于获取文件夹部分
- os.path.basename() 常用于获取文件名

### 文件读写

```python
# 以 r+ 读写模式打开文件
file = open('filename','r+')
# 读取所有内容
text=file.read()
# 写入内容
file.write('新的内容\n')
# 关闭文件对象
file.close()
```
原filename文件内容
```sh
这是一行内容
```
写入新内容后
```sh
这是一行内容新的内容
```
基本步骤：
1. 以某种模式打开文件对象
2. 读取或者写入文件
3. 关闭文件对象

#### 文件操作主要模式
- r 只读，打开一个**已存在**的文件
- rb 只读、二进制格式，打开一个**已存在**的文件
- r+ 可读写，打开一个**已存在**的文件
- w 写入，如果文件存在则覆盖，如果不存在则创建
- w+ 可读写，如果文件存在则覆盖，如果不存在则创建
- a 追加，打开一个文件写入内容到结尾，如果文件不存在则创建
注意：一般模式用于读写文本，二进制格式用于读写一般文件，比如图片、视频等

### shelve模块
```python
import shelve
# 操作名为data的文件系统，如果不存在则创建
file = shelve.open('data')
pets = ['狗','猫','兔子','乌龟']
# 把变量pets的内容保存到文件中，取名congwu
file['congwu']=pets
# 关闭文件对象
file.close()

# 如果需要读取，把内容当作对象来操作
newfile=shelve.open('data')
pets=newfile['congwu']
print(pets)
newfile.close()
```
运行结果:
```sh
['狗','猫','兔子','乌龟']
```
- shelve 模块提供了一种方便的存储和读取文件内容的方法，可以理解为提供了一套结构化存储系统
- 使用者不用关心文件是如何操作的
- 缺点是不能手动修改存储的内容

### 文件管理
> 除了读写内容，我们经常会操作文件本身，比如新建、改名、复制、移动等

> os 和 shutil 模块常用于文件管理

#### 复制
```python
import os,shutil
# 更改当前目录
os.chdir('c:\\')
# 复制文件 源文件 --> 目的路径 ，文件名不变
shutil.copy('name.txt', 'c:\\文件')
# 复制文件，并取名
shutil.copy('name.txt', 'c:\\文件\\name1.txt')
# 复制文件夹
shutil.copytree('文件', 'c:\\文件备份')
```
- 注意测试时，需要准备一个name.txt文件
- 注意如果不是当前目录的文件，路径需要写完整，os.chdir() 在这里只是为了演示，根据实际需要可忽略该步骤
- 注意路径里的 `\` 需要转义
- 注意目的路径有没有文件名，意义不一样
- 可以复制整个文件夹，但要注意如果目的文件夹已存在，复制会失败

#### 移动和改名
```python
import shutil
# 移动文件 源文件 --> 目的路径 ，文件名不变
shutil.move('c:\\文件\\name.txt', 'c:\\文件备份')
# 移动文件到当前路径并取名，则原文件改名
shutil.move('c:\\文件备份\\name.txt', 'c:\\文件备份\\name1.txt')
# 移动文件夹，在同一目录中，则是改名
shutil.move('c:\\文件', 'c:\\文件备份1')
```
- 注意测试时，需要准备2个文件夹 '文件'和'文件备份'，1个文件 name.txt
- 注意如果目的文件已存在，移动操作会失败
- 移动和改名本质是一样的，所以 move() 方法可以实现2种操作


#### 删除
```python
import os,shutil
# 删除文件
os.remove('c:\\文件备份1\\name1.txt')
# 删除文件夹
shutil.rmtree('c:\\文件备份')
```
- 注意测试时，需要准备相应的文件和文件夹
- 注意删除是永久的，并不是删除到回收站（也有相应的方法可以做到）
- 移动和改名本质是一样的，所以 move() 方法可以实现2种操作

#### 遍历
```python
import os
# 循环遍历每个文件夹，分别获取文件夹名称-folderName，子文件名称列表-subfolders，文件列表-filenames
for folderName, subfolders, filenames in os.walk('C:\\文件夹'):
    print('当前目录是 ',folderName)
    for subfolder in subfolders:
        print('子目录有 ',subfolder)
    for filename in filenames:
        print('文件有 ',filename)
    print()
```
运行结果:
```
当前目录是  C:\文件夹
子目录有  子文件夹1
子目录有  子文件夹2
文件有  文件1.txt

当前目录是  C:\文件夹\子文件夹1
文件有  文件2.txt

当前目录是  C:\文件夹\子文件夹2
文件有  文件3.txt
```
- 测试的文件夹结构如下

![文件夹结构](https://uinx1983.github.io/img/filetree.png)

- os.walk() 函数可以对指定的目录，遍历所有的子目录和文件
- 根据需要选择使用 '文件夹名称'、'子文件夹列表'、'文件列表'

### 打包文件
> 把一系列文件或者文件夹打包成一个文件，也经常称为'压缩'或'归档'
```python
import shutil
# 指定归档压缩的目标文件，压缩类型，压缩源
shutil.make_archive('c:\\压缩文件','zip','c:\\文件夹')
```
- 输出的文件为 '压缩文件.zip'
- python自带的压缩类型有 'zip'、'tar'、'gzip' 等

# 练习
1. 基础练习（必做，个人完成）

    - 完成[基础练习-8](/python/lab/lab-8.md)

2. 综合项目（二选一，分组完成）
    - 难度稍低[综合项目-4-隐私信息处理](/python/problem/problem-4-privacy.md)
    - 难度稍高[综合项目-4-图片加水印](/python/problem/problem-4-watermark.md)



