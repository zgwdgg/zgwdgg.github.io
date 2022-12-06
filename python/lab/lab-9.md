# 基础练习-9

### 目标
参照如下网页，自己设计栏目和内容，完成一个新的网页：

![示例网页](https://uinx1983.github.io/img/lab9-sample.png)

### 要求
1. 主题自己选择，不能和示例一样
2. 内容不要求多，关键是东西都要有
3. 网页保存为 lab-9.html

**示例素材[下载](https://uinx1983.github.io/python/lab/lab-9.zip)**


### 编程参考
网页代码结构
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>二次元俱乐部</title>
    <link href="style.css" rel="stylesheet"><!-- 网页的样式文件，href指向文件路径 -->
  </head>

  <body>
    <header> <!-- 本站所有网页的统一主标题 -->
      <h1>聆听电子天籁之音</h1>
    </header>

    <nav> <!-- 本站统一的导航栏 -->
      <ul>
        <li><a href="#">主页</a></li>
        <!-- 共n个导航栏项目，省略…… -->
      </ul>

      <form> <!-- 搜索栏是站点内导航的一个非线性的方式。 -->
        <input type="search" name="q" placeholder="要搜索的内容">
        <input type="submit" value="搜索">
      </form>
    </nav>

    <main> <!-- 网页主体内容 -->
      <article>
        <!-- 此处包含一个 article（一篇文章），内容略…… -->
      </article>

      <aside> <!-- 侧边栏在主内容右侧 -->
        <h2>相关链接</h2>
        <ul>
          <li><a href="#">这是一个超链接</a></li>
          <!-- 侧边栏有n个超链接，略略略…… -->
        </ul>
      </aside>
    </main>

    <footer> <!-- 本站所有网页的统一页脚 -->
      <p>© 2050 某某保留所有权利</p>
    </footer>
  </body>
</html>

```

### 提示信息
- \<\!\-\- 注释的内容 \-\-\> 标签里的是注释，HTML里不能用 # 进行注释
- 样式文件，也称为css文件，用于调整网页内容的外观，使得页面更美观和个性化

### 验证程序
在浏览器访问网页，检查显示的内容是否符合要求
注意以下几点：
- 内容是否显示美观，和示例一样
- 文字是否按照自己设计的主题进行了修改
- 链接是否能正确点击，链接到了正确的页面

### 如何提交
在超星（学习通）平台，提交内容