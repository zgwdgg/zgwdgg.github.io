# 综合项目-3-维吉尼亚加密

### 目标
写一个程序实现维吉尼亚加密。
维吉尼亚密码是使用一系列`凯撒密码`组成密码字母表的加密算法，属于多表密码的一种简单形式。简单易用，同时初学者难以破解。
如下例所示：其中 pizza 是密钥，i have a dream 是需要加密的字符串
```sh
c:\python\problem>python problem-3-vigenere.py pizza "i have a dream"
i have a dream 通过密钥 pizza 加密后为 x pzue p lqdab
```

### 要求
1. 密钥不限制长度，可以超过需要明文的长度
2. 密钥值是一个由字母组成的字符串，不能有特殊字符
3. 明文可以有特殊字符，对除字母外的字符保留原始状态
4. 程序保存为problem-3-vigenere.py

### 维吉尼亚密码法简介
维吉尼亚加密法和凯撒加密法类似，除了使用多个密钥。
凯撒加密法的密钥范围是0到25。使用字母表对应字母的位移进行加密。
对于维吉尼亚加密法来说，我们不用一个数字密钥，而用一个字母密钥。字母A对应密钥0，字母B对应密钥1，依此类推，最后Z对应密钥25。
因此，维吉尼亚的密钥是一系列字母，比如一个英文单词。如果我们使用“PIZZA”作为密钥，那么第1个子密钥是P-对应字母顺序值15，第2个子密钥是I-对应值8，第3和4个子密钥都是Z-对应值25，第5个子密钥是A-对应值0。
我们将使用第1个子密钥来加密明文的第1个字母，使用第2个子密钥来加密第2个字母，以此类推。当到第6个明文时，重复使用密钥的第1个字母，以此类推，比如要加密"I have a dream"，方法如下：
```python
明文：i have a dream
密钥：p izza p izzap
位移：15 8,25,25,0 15 8,25,25,0,15
结果：x pzue p lqdab
```
### 编程参考
关键步骤
```
读取并处理程序参数，判断是否满足要求
接着处理加密过程
加密需要用到循环，对明文中的每个字符进行凯撒加密
凯撒加密需要用到：密钥值（位移），来源于从参数读取的密钥所对应的字母
```
代码结构
```python
import sys

LETTERS = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'

#凯撒加密函数，symbol参数传递需要加密的字符，key参数传递密钥值（位移值）,函数返回加密后的字符
def ceasar(symbol,key):
    LETTERS = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
    # 字符小写时
    if symbol.islower():
        # 把字母表转换为小写
        LETTERS = LETTERS.lower()
        # 如果字符在字母列表中
        if symbol in LETTERS:
            # 获取字符在字母表中的位置
            num = LETTERS.find(symbol)
            # 移动密钥值的位置
            num = num + key
            # 返回结果
            return LETTERS[num%26]
        # 不在字母列表中
        else:
            # 返回原始字符
            return symbol
    # 字符是大写时
    else:
        # 把字母表转换为大写
        LETTERS = LETTERS.upper()
        # 如果字符在字母列表中
        if symbol in LETTERS:
            # 获取字符在字母表中的位置
            num = LETTERS.find(symbol)
            # 移动密钥值的位置
            num = num + key
            # 返回结果
            return LETTERS[num%26]
        # 不在字母列表中
        else:
            # 返回原始字符
            return symbol

# 判断程序参数是否符合要求
if ...:
    # 显示用法说明
    ...
    # 结束程序
    sys.exit()
#获取密钥
key=...
#获取明文
message=...
#设置加密结果
result=''
#循环明文中每个字符
for ... in ...:
    #对字符进行加密
    ...
#打印结果
print(result)
```

### 提示信息
- find() 方法：字符串的方法，返回对象在字符串中的位置
- % 运算符：求余运算

### 验证程序
运行程序，输入相应的信息，检查输出内容是否符合要求

注意以下几点：
- 程序结果是否和例子中一致
- 密钥中如果有其他字符，程序是否会给出相应提示
- 密钥的长度比明文长时，程序是否正常运行

### 如何提交
在超星（学习通）平台，提交内容