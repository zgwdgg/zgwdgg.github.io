# 从 Web 抓取信息

> “Web 抓取”是一个术语，即利用程序下载并处理来自 Web 的内容。即是我们常说的 “爬虫” 程序所做的事情。

## 目标

* 掌握 HTTP 协议的基本逻辑
* 掌握 requests 模块的基本用法
* 掌握 xpath 的基本用法
* 掌握 Beautiful Soup 模块的基本用法
* 掌握 JSON 数据的操作方法
* 练习

## 01. HTTP 的 get 方法
> get 方式主要用于获取信息

我们先来看看 get 方式发起请求获取文件：
```python
import requests

# 通过 requests 模块发起网络请求，把返回的信息保存为 r 对象
r = requests.get('https://uinx1983.github.io/python/lab/lab-9.zip')

if r.status_code==200:
    downFile = open('t.zip', 'wb')
    downFile.write(r.content)
    downFile.close()
```
- 服务器返回的响应 response ，保存为一个对象
- 对象的 content 属性是获取的数据
- 数据是二进制形式

再来看看获取网页内容的情况：
```python
import requests

r = requests.get('https://bing.com')

if r.status_code==200:
    print(r.text)
```
- text 是数据的文本形式

### 小练习
把获取的网页内容，保存为一个 html 文件，并在浏览器打开

### 观察
获取的内容和浏览器中网页显示的内容一样吗？

## 02. 传递参数
> 发出请求时，还可以传递参数，来获取不同的数据

格式：URL 请求的末尾跟上一个 ' ? ' 和查询字符串。

访问如下地址：

https://www.baidu.com/s?wd=python&ie=utf-8

- 参数名=值 是参数传递的格式
- 多个参数用 & 符号隔开

### 思考？
值里有特殊符号怎么办？使用转义字符？

### url编码
> 比如我要查询的内容是 `python for循环` ，在发送请求时，url变成了什么样子？

https://www.baidu.com/s?wd=python`%20`for`%E5%BE%AA%E7%8E%AF`

- 空格变成了 %20 来表示
- 中文变成了 %E5%BE%AA%E7%8E%AF 这样的表示方法 

> python中我们要如何正确的发送参数呢？

```python
import requests

payload = {'wd': 'python for循环', 'ie': 'utf-8'}
r = requests.get('https://www.baidu.com/s', params=payload)
print(r.url)
```
- 发送的 get 请求，参数进行了传递，url也进行了正确的编码

### 讨论
去豆瓣网站，找到‘豆瓣电影分类排行榜’中某一种电影类型的get请求地址

## 03. post 方法
> post 方式主要用于提交信息，比如注册，登录等操作

下面以一个问卷填写举例 https://wj.qq.com/s2/9980513/e2e4：
```python
import requests

payload = {"survey_id":"9980513","hash":"e2e4","answer_survey":"{\"id\":\"9980513\",\"survey_type\":0,\"jsonLoadTime\":59,\"time\":1649158478,\"ua\":\"Mozilla/5.0+(Windows+NT+6.1;+Win64;+x64;+rv:72.0)+Gecko/20100101+Firefox/72.0\",\"referrer\":\"\",\"uid\":\"d36c1296-4de7-47f7-b3e0-36b33773aa0a\",\"sid\":\"d51c155b-ac7b-479f-92db-8015b345b451\",\"openid\":\"\",\"pages\":[{\"id\":\"p-1-cad5\",\"questions\":[{\"id\":\"q-1-3b67\",\"type\":\"text\",\"text\":\"dd\"},{\"id\":\"q-2-7589\",\"type\":\"text\",\"text\":\"dd\"},{\"id\":\"q-3-4802\",\"type\":\"radio\",\"options\":[{\"id\":\"o-106-1686\",\"checked\":1,\"text\":\"&lt;p&gt;以上症状都没有&lt;/p&gt;\\n\"}]},{\"id\":\"q-9-JTvq\",\"type\":\"text_multiple\",\"blanks\":[{\"id\":\"fillblank-DMlA\",\"value\":\"34\"}]},{\"id\":\"q-5-38e3\",\"type\":\"radio\",\"options\":[{\"id\":\"o-102-0b15\",\"checked\":1,\"text\":\"+否\"}]},{\"id\":\"q-7-f987\",\"type\":\"radio\",\"options\":[{\"id\":\"o-102-b548\",\"checked\":1,\"text\":\"+否\"}]},{\"id\":\"q-8-75ca\",\"type\":\"radio\",\"options\":[{\"id\":\"o-102-fac3\",\"checked\":1,\"text\":\"&lt;p&gt;否&lt;/p&gt;\\n\"}]}]}],\"latitude\":\"\",\"longitude\":\"\",\"is_update\":false}"}
r = requests.post('https://wj.qq.com/sur/collect_answer', data=payload)
print(r.text)
```
- post 传递的数据可以是字典或者 json 格式
- 现在网页设计越来越复杂，post 中经常用到了 javascript 等技术，数据交互也可能由多次完成，解析整个数据交互过程有很大难度

## 04. xpath 获取网页元素
> XPath 的意思是 XML 路径语言。HTML 是一种 XML 格式的文档，使用 XPath 可以方便的定位、获取元素

```python
import requests
from lxml import etree

# 定义网络地址:豆瓣新片榜
url='https://movie.douban.com/chart'
# 自定义请求的头部信息
#headers = {'user-agent': 'Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.75 Safari/537.36 Edg/100.0.1185.36'}
# 发起网络请求，获取内容
#html=requests.get(url,headers=headers)
html=requests.get(url)
# 强制转换编码为utf-8
#html.encoding='utf-8'
# 把获取的内容转换为xml对象
xml=etree.HTML(html.text)

# 在这个对象上应用xpath，取得标题所在的链接元素
#//*[@id="content"]/div/div[1]/div/div/table/tr/td[2]/div/a
hrefs=xml.xpath('//div[@class="pl2"]/a')
for h in hrefs:
    print(h.text)
# 获取得分所在的元素
stars=xml.xpath('//span[@class="rating_nums"]')
for s in stars:
    print(s.text)

```

- headers 定义的头部信息，有些网站必须有该内容才能正常访问
- 有些时候网页获取的内容不能正确识别编码，需要用 encoding 指定
- xpath 规则可以从浏览器工具辅助获取，但自己写的更简洁准确

### XPath 基本语法汇总
> xpath 的思想是通过 路径表达 去寻找节点。节点包括`元素`，`属性`，和`内容`

- 路径表达式
```
/   根节点，节点分隔符，
//  任意位置
.   当前节点
..  父级节点
@   属性
```
- 通配符
```
*   任意元素
@*  任意属性
node()  任意子节点（元素，属性，内容)
```
- 谓语(使用中括号来限定元素，称为谓语)
```
//a[n] n为大于零的整数，代表子元素排在第n个位置的<a>元素
//a[last()]   last()  代表子元素排在最后个位置的<a>元素
//a[last()-]  和上面同理，代表倒数第二个
//a[position()<3] 位置序号小于3，也就是前两个，这里我们可以看出xpath中的序列是从1开始
//a[@href]    拥有href的<a>元素
//a[@href='www.baidu.com']    href属性值为'www.baidu.com'的<a>元素
//book[@price>2]   price值大于2的<book>元素
```

### #小练习

完成基础练习-10

## 05. 用 BeautifulSoup 模块解析 HTML
> 使用 xpath 获取一种内容比较容易，但操作复杂的文本还是不够方便，我们试试 BeautifulSoup 模块

- 模块安装：pip install BeautifulSoup4
- 模块调用：bs4
```python
import requests,bs4

# 定义网络地址:豆瓣新片榜
url='https://movie.douban.com/chart'
headers = {'user-agent': 'Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.75 Safari/537.36 Edg/100.0.1185.36'}
# 发起网络请求，获取内容
html=requests.get(url,headers=headers)
# 强制转换编码为utf-8
html.encoding='utf-8'
# 把获取的内容转换为bs对象
bs=bs4.BeautifulSoup(html.text,'lxml')

# 使用选择器获取元素
hrefs=bs.select('div[class="pl2"]')
for h in hrefs:
    name=h.a.contents[0].strip('/ ').strip()
    rate=h.select('span[class="rating_nums"]')[0].text
    print(f'电影名：{name}，评分：{rate}')

```
- select() 方法称为选择器，通过元素的特点进行选择
- 选择器的规则比xpath简单
- 选择器获得的元素，可以方便的获取内容和属性
- 选择器获取的元素，可以进一步操作获取子元素

### #小练习
使用BeautifulSoup获取"豆瓣音乐排行榜"的歌曲名

## 06. JSON数据
> JSON 是 JavaScript 程序编写数据结构的原生方式，在当今网络中非常流行。通过 API 获取的数据大部分都是 JSON 数据。

> 很多网站都提供 JSON 格式的内容，作为程序与网站交互的方式。这就是所谓的提供“应用程序编程接口（API）”。访问 API 和通过URL 访问任何其他网页是一样的。


我们来看一个获取天气的例子：
```python
import requests
import sys

# 大部分 API 接口需要申请key才能使用
key='525bdc3a99bf80086f0cc11433a1b50d'

# 高德地图提供的天气查询接口
r = requests.get(f'https://restapi.amap.com/v3/weather/weatherInfo?city=510100&key={key}')

r.raise_for_status()

# 把响应转换为JSON数据，也就是字典类型
r=r.json()
# 查询状态正常时，进一步处理数据
if(r['status']=='1'):
    天气=r['lives'][0]['weather']
    气温=r['lives'][0]['temperature']
else:
    print('天气查询失败，请稍后再试')
    sys.exit()

print(f'今天成都 天气：{天气} 气温：{气温}')
```
- 利用 API，从网站获取原始数据，通常比通过网页解析 HTML 元素更方便
- 弄清楚数据的结构，才能准确的获取想要的数据

### #小练习
去高德地图注册开发者帐号，申请一个 web服务 的key

### 进一步
> 我们再来看看城市查询接口，优化程序

```python
import requests
import sys

key='525bdc3a99bf80086f0cc11433a1b50d'

# 使用另外的接口查询城市代码
city=input('输入你想查询的城市：')
city_r=requests.get(f'https://restapi.amap.com/v3/config/district?key={key}&keywords={city}&subdistrict=0')
city_r.raise_for_status()
city_r=city_r.json()
if(city_r['status']=='1'):
    city_code=city_r['districts'][0]['adcode']
else:
    print('城市查询失败，请稍后再试')
    sys.exit()

# 天气查询
r = requests.get(f'https://restapi.amap.com/v3/weather/weatherInfo?city=510100&key={key}')
r.raise_for_status()
r=r.json()
if(r['status']=='1'):
    天气=r['lives'][0]['weather']
    气温=r['lives'][0]['temperature']
else:
    print('天气查询失败，请稍后再试')
    sys.exit()

print(f'现在{city} 天气：{天气} 气温：{气温}')
```

### #小练习
在天气例子的基础上，添加显示接下来三天的天气预报数据

<!--## 07. 练习

完成综合项目:以小组为单位，选择一个目标网站，考虑要获取哪些内容，设计一个爬虫程序获取内容，并保存到一个文件中。
-->
