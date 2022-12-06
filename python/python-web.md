# 从 web 获取数据
目录
- [知识点总结](#知识点总结)
    - [requests模块](#requests模块)
    - [xpath](#xpath)
    - [BeautifulSoup模块](#BeautifulSoup模块)
- [练习](#练习)
---
# 知识点总结

## requests模块
> python 中进行网络访问，使用 requests 模块是一种好的选择

### 发送网络请求
```python
# 导入模块
import requests

# 使用 get 方式访问网页，其中 r 是网页的回复信息（也称为响应）,后续操作都使用该对象
r = requests.get('https://api.github.com/events')

# 如果要使用 post 方式发送数据，可以如下操作，其中数据是键值对形式
r = requests.post('https://httpbin.org/post', data={'key': 'value'})
```
- get 和 post 是网页访问使用最多的两种方式，除此之外还有put、delete、head、options等方式
- get 方式主要用于请求数据
- post 方式主要用于提交数据

### 通过 url 传递参数
> 请求信息时，可以传递参数，比如URL地址：httpbin.org/get?key=val，也是以键值对的形式跟在`?`后面

```python
# 这种方式一般是 get 请求使用，为了方便参数的传递，通过变量来设置
payload = {'key1': 'value1', 'key2': 'value2'}
r = requests.get('https://httpbin.org/get', params=payload)
# 确保返回了正常的响应
r.raise_for_status()
# 可以打印出 URL 看看，是这个样子 https://httpbin.org/get?key1=value2&key2=value2
print(r.url)
```
- 当然也可以直接把参数写入 URL 地址，发送 get 请求

### 响应信息

```python
import requests

r = requests.get('https://api.github.com/events')
r.raise_for_status()
# r 是网络的响应信息，r.text 是信息的文本形式，打印出来看看
print(r.text)
# 大部分情况下程序能自动处理编码问题，但你可以看看响应的编码是什么
print(r.encoding)
# 也可以通过设置强制使用其他编码来处理文本信息，如下面把编码改为了 utf-8
r.encoding = 'utf-8'
```

### 二进制形式读取原始数据
> 网络上并不只是文本，还有文件、图片、视频等内容，使用文本读取不能正确处理这些数据

```python
from PIL import Image
from io import BytesIO
import requests

r = requests.get('https://uinx1983.github.io/img/image-20211219140759903.png')
r.raise_for_status()

# 把二进制内容保存为图片文件，注意使用二进制模式
imgFile = open('test.png', 'wb')
# 可以直接写入文件，但不推荐该方式
#imgFile.write(r.content)
# 最好是采用如下循环的方式，一部分一部分的写入，因为网络资源有可能很大，一次写入会占用大量的内存
for chunk in r.iter_content(128):
    imgFile.write(chunk)
# 也可以通过二进制形式读取出来，当作图片打开
i = Image.open(BytesIO(r.content))
# 显示图片
i.show()

```
- r.content 是二进制形式数据

### 处理JSON格式数据
> 现在网络资源有很多通过API访问，JSON格式是主要使用的格式，Python能方便的帮你进行转换

```python
import requests

r = requests.get('https://api.github.com/events')

r.raise_for_status()

# 获取JSON类型的响应
j=r.json()

# 获取其中的id值
print(j["id"])
```
- r.json() 是JSON格式数据，操作方式和字典类似

## xpath
它是一种用来确定XML文档中某部分位置的语言。关于xpath的资料，可以参考[百度百科](https://baike.baidu.com/item/XPath)的内容

## BeautifulSoup模块
Beautiful Soup 是一个可以从HTML或XML文件中提取数据的Python库。可以参考[官方中文文档](https://www.crummy.com/software/BeautifulSoup/bs4/doc.zh/)

# 练习
1. 基础练习（必做，个人完成）

    - 完成[基础练习-10](/python/lab/lab-10.md)


