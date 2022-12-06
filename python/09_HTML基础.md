# HTML基础

> 在学习用 python 获取网页数据之前，需要了解一些基础知识。

## 目标

* 了解网站服务原理和协议
* 掌握 HTML 基本语法
* 练习

## 01. 启动一个网站（web）服务

在命令提示符中执行如下命令：
```sh
# 使用 cd 命令切换到网站目录
C:\Users\huanglei>cd c:\myweb
# 使用 http.server 模块启动网站服务
c:\myweb>python -m http.server 
# 窗口中显示如下信息，默认使用了 8000 端口提供服务
Serving HTTP on :: port 8000 (http://[::]:8000/) ...
```
- 该模块只是测试使用，正式的网站不会用这种方法部署

### 访问网站
打开你的浏览器，然后输入下面的URL地址：

http://localhost:8000

- URL是统一资源定位符，完整地描述Internet上网页和其他资源的一种标识方法
- 如果没有指定要访问的页面，默认会列出网站目录文件列表

## 02. 访问网页

### 设置首页
在 c:\myweb 中创建一个文本文件 index.html ，编辑里面的内容

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>我的网站</title>
    </head>
    <body>
        这是我的首页，什么内容都没有！
    </body>
</html>
```
- HTML 文件通常会以 .htm 或 .html 为扩展名
- 如果有类似 index.html 的文件，网站会把这种文件当作首页显示
- 也可以使用url地址访问指定的文件资源，http://localhost:8000/index.html

### HTML文档解析
> HTML 是一种相由不同元素组成的标记语言
```html
<!DOCTYPE html>
```
- 声明文档类型。记住现在的 HTML 网页文件都这样开头。
```html
<html>
    ...
</html>
```
- \<html\> 元素是页面的根元素
- 每个元素都用一对开始和结束`标签`包裹
- 每个标签以尖括号（<>）开始和结束

```html
<head>
    <meta charset="utf-8">
    <title>我的网站</title>
</head>
```
- \<head\>元素。这个元素是一个容器，它包含了所有你想包含在HTML页面中但不想在HTML页面中显示的内容。

```html
<meta charset="utf-8">
```
- 元素中可以有`属性`，比如 charset="utf-8" 是 \<meta\> 元素的属性，属性是对元素信息的额外描述，不会直接显示在网页中
- 一些特别的元素，可以不用结束标签

```html
<title>我的网站</title>
```
- \<title\> 元素设置网页的标题，标签之间的文本，称为`内容`

```html
<body>
    这是我的首页，什么内容都没有！
</body>
```
- \<body\>元素。包含了你访问页面时所有显示在页面上的内容，文本，图片，音频，游戏等等。

### #小练习
在网站的文件夹中，创建一个新的文件，比如 aboutme.html ，里面写上个人介绍，通过浏览器访问该页面。

### 更多的URL示例

```sh
# 网站首页，使用了https加密协议，使用了域名当作主机名
https://www.baidu.com
# 访问资源 http.server.html
https://docs.python.org/zh-cn/3/library/http.server.html
# 通过 search.html 页面传递数据给服务器，使用了3个参数：q，check_keywords，area
https://docs.python.org/zh-cn/3/search.html?q=http&check_keywords=yes&area=default
```
- 网站的默认端口一般是 80，可以忽略不写
- 现在大部分网站都是用了更安全的 https 协议
- 域名和ip地址都可以当作主机
- 动态资源可以通过传递不同的参数，获取不同的内容
- 参数都是以`?`开始，参数之间是`&`符号隔开，`=`为参数赋值

### 创建超链接
> 网页中的超链接，把不同地方的文件资源，建立了关系，通过鼠标点击就可以访问

修改首页的内容，添加到个人介绍页面的链接：
```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>我的网站</title>
    </head>
    <body>
        <a href='aboutme.html'>个人介绍</a>
    </body>
</html>
```

- \<a\> 元素是超链接
- 标签中的内容，是超链接的文字
- href 属性非常重要，属性值指向一个 URL 地址

### 插入图片
> 网页中有许多类型的多媒体，最基础的是图片

为首页增加一张图片：
```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>我的网站</title>
    </head>
    <body>
        <p>
        <a href='aboutme.html'>个人介绍</a>
        </p>
        <img src="dinosaur.jpg">>
    </body>
</html>
```
- \<p\> 元素是段落标记，放在里面的内容，是一个段落
- \<img\> 元素是一个空元素，不需要包含文本内容或闭合标签，就像之前用过的 \<meta\> 元素
- src 属性指向我们想要引入的图片的路径，可以是相对路径或绝对URL，这里的图片文件就和该网页文件在同一目录中

### #小练习
使用另外的图片，替换示例的图片，浏览器访问网页看看效果

## 03. 练习

完成超星学习通上的练习
