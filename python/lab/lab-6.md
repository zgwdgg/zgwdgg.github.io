# 基础练习-6

### 目标
在课堂练习的基础上，完成凯撒密码的解密程序
程序运行结果像下面这样：
```sh
C:\python\lab>python lab-6.py "guvf vf n zrffntr"
guvf vf n zrffntr 解密后为 this is a message
```
### 要求
1. 注意信息支持空格
2. 程序保存为lab-6.py

### 编程参考
关键步骤
```
参数的信息以" "包括，当作一个参数使用
解密和加密的区别在于移动的方向不同，加密是往右位移，加密后的位置是增加的。而解密相反。
```
代码结构
```python
import pyperclip
import sys
# 判断程序参数是否符合要求
if len(sys.argv) < 2:
    # 显示用法说明
    ...
    # 结束程序
    sys.exit()
# 获取需要处理的信息
message = ...
# 位移值
key = 13
# 密钥表
LETTERS = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
# 解密结果
translated = ''
# 循环信息中每个字符
for symbol in message:
    # 字符小写时
    if symbol.islower():
        # 把密钥表转换为小写
        LETTERS = LETTERS.lower()
        # 如果字符在密钥列表中
        if symbol in LETTERS:
            # 获取字符在密钥表中的位置
            num = LETTERS.find(symbol)
            # 移动密钥值的位置
            num = ...
            # 把解密后的字符放进结果中
            translated = ...
        # 不在密钥列表中
        else:
            # 把字符直接放进结果中
            translated = translated + symbol
    # 字符是大写时
    else:
        # 把密钥表转换为大写
        LETTERS = LETTERS.upper()
        # 如果字符在密钥列表中
        if symbol in LETTERS:
            # 获取字符在密钥表中的位置
            num = LETTERS.find(symbol)
            # 移动密钥值的位置
            num = ...
            # 把解密后的字符放进结果中
            translated = ...
        # 不在密钥列表中
        else:
            # 把字符直接放进结果中
            translated = translated + symbol

# 打印解密信息
...

# 复制解密信息到粘贴板
pyperclip.copy(translated)

```

### 提示信息
- 验证一下程序参数加" "和不加" "有没有区别

### 验证程序
运行程序，输入相应的信息，检查输出内容是否符合要求
注意以下几点：
- 程序能正常运行
- 验证当参数是"jryy qbar"时，解密后的文字是否是well done
- 验证当忘记写参数时，程序是否会提示用法说明

### 如何提交
在超星（学习通）平台，提交内容