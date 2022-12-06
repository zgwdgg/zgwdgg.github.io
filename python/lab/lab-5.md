# 基础练习-5

### 目标
假设一个怪物的战利品会掉落多个，表示为这样的字符串列表：drop_item = ['金币', '匕首', '金币', '金币', '红宝石']

写一个名为 addToInventory(inventory, addedItems) 的函数，其中 inventory 参数是一个字典，表示玩家背包中的物品清单，addedItems 参数是一个列表，表示需要添加的战利品。addToInventory()函数把传入的战利品清单，更新到玩家的背包中，并返回 inventory 字典。

再写一个名为 displayInventory(inventory) 的函数，把玩家背包里的物品列出来。

程序运行结果像下面这样：
```sh
战斗结束后，背包里有：
1个 火把
2个 血瓶
3个 金币
1个 匕首
1个 红宝石
```
### 要求
1. 掉落物品增加到背包里
2. 背包里的每个物品显示一行
3. 程序保存为lab-5.py

### 编程参考
关键步骤
```
定义函数 addToInventory
定义函数 displayInventory
调用函数 addToInventory 增加物品
调用函数 displayInventory 显示背包物品
```
代码结构
```python
# 定义函数
def addToInventory(inventory,addedItems):
    # 把addedItems的内容，添加到inventory
    ...
    # 返回inventory
    return inventory
# 定义函数    
def displayInventory(inventory):
    #循环显示背包物品
    ...

#背包物品
inventory={'火把':1,'血瓶':2}
#掉落物品
drop_item = ['金币', '匕首', '金币', '金币', '红宝石']

## 结算战利品
# 调用函数 addToInventory 添加物品
inventory=addToInventory(inventory,drop_item)
print('战斗结束后，背包里有：')
# 调用函数 displayInventory 显示物品
displayInventory(inventory)
```

### 提示信息
- 字典.items() 方法：获取字典中所有的 `键值对`

### 验证程序
运行程序，输入相应的信息，检查输出内容是否符合要求
注意以下几点：
- 程序显示正确结果
- 更改初始背包物品，结果是否正确
- 更改掉落物品，结果是否正确

### 如何提交
在超星（学习通）平台，提交内容