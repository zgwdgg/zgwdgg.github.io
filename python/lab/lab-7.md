# 基础练习-7

### 目标
利用正则表达式，来判断用户输入的密码是否符合复杂度要求。
你需要完成一个函数，用于在用户注册的程序中，判断密码是否符合要求。
程序运行结果像下面这样：
```sh
#####欢迎来到Python学习平台注册程序#####
请输入用户名：huanglei
请输入密码：
请再次输入密码：
密码太简单，必须包含大小写字母和数字，至少8位，请重新输入！
请输入用户名：huanglei
请输入密码：
请再次输入密码：
注册成功！
当前系统用户有：['zhangsan', 'lisi', 'huanglei']
```
### 要求
1. 只需要完成密码复杂度检查函数的代码，程序其他部分已提供
2. 必须使用正则表达式来完成
3. 密码复杂度要求为：必须包含大小写字母和数字，至少8位
4. 程序保存为lab-7.py

### 编程参考
代码结构
```python
import getpass
import re
# 判断用户名合法性函数，字母、下划线、数字组成，至少4位，最多20位长
def userValid(username):
    nameRe = re.compile(r'[a-zA-z_]\w{3,20}')
    if(nameRe.match(username)):
        return True
    else:
        return False

# 判断密码复杂度函数，必须包含大小写和数字，至少8位
def passValid(password):
    # 待完成
    ...

# 用户数据库，预置了2个用户帐号信息 帐号：密码
users={'zhangsan':'123456','lisi':'qwerty'}
# 注册过程
# 欢迎信息
print('#####欢迎来到Python学习平台注册程序#####')
while True:
    # 用户输入
    username=input('请输入用户名：')
    password1=getpass.getpass('请输入密码：')
    password2=getpass.getpass('请再次输入密码：')
    # 处理注册信息
    if(users.get(username)):
        print('用户已存在，请重新输入！')
    elif(userValid(username)):
        if(password1==password2):
            if(passValid(password1)):
                users[username]=password1
                print('注册成功！')
                print(f'当前系统用户有：{list(users.keys())}')
                break
            else:
                print('密码太简单，必须包含大小写字母和数字，至少8位，请重新输入！')
        else:
            print('密码不一致，请重新输入！')
    else:
        print('用户名只能由字母、下划线开头，并且不能包含特殊符号,请重新输入！')

```

### 提示信息
- 可以尝试自己写规则，更方便的是网上找现成的规则
- 如果找到的规则不是完全符合任务的要求，也可以先使用试试

### 验证程序
运行程序，输入相应的信息，检查输出内容是否符合要求
注意以下几点：
- 程序运行没有错误
- 验证当注册的用户名已经存在时，输出什么结果
- 验证当注册的用户名包含特殊字符时，输出什么结果
- 验证当输入的密码太简单时，输出什么结果
- 验证当输入的2次密码不一致时，输出什么结果
- 验证当正确输入符合要求的帐号和密码时，是否注册成功

### 如何提交
在超星（学习通）平台，提交内容