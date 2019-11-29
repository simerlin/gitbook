

## Python 基本数据类型

### 字符串

> 引号包括单引号 ' ' ，双引号 " " 和 三引号 ''' ''' ，比如 'abc' ，"123" '''三个引号的字符串'''。



```
 str1 = "双引号里面可以放个'单引号"
 
 str2 = '单引号可以放"双引号'  
 
 str3 = '''奇葩还有个三引号里面可以放些连七八糟的·
         支持格式换行'''
 
 str4 = '也可以用常规的方法 \" \' 反斜杠转义字符'                
         
 
```

### python 算术运算符

| 运算符 | 意义 |例子|
| :--- | :--- |:---|
| + | 加 |2 + 1 结果 3|
| - | 减 |2 - 1 结果 1|
| * | 乘 |2 * 2 结果 4|
| / | 除 |4 / 2 结果 2|
| % | 取模 - 取余数部分 | 5 % 2 结果 1 |
| ** | 幂 - x的y次方 | 2 ** 3  结果8|
| // | 整除 - 相除取整数部分 | 9//2 结果4 |


> Python2.7 和 Python3.1 差异 



```
# 2.7下结果是0 val 数据类型还是int 3.x 下是0.5 数据类型是float

val = 1 / 2
```

### 浮点型(float)



```
print(0.55 + 0.41)

print(0.55 + 0.4)

print(0.55 + 0.411)

# window10 Python2.7 输出结果

0.96
0.95
0.961

# window10 Python3.7.3 输出结果

0.96
0.9500000000000001
0.9610000000000001

```

### 布尔值 

> True/False 请注意大小写!!

1. and 运算是与运算，只有所有都为 True，and 运算结果才是 True。

2. or 运算是或运算，只要其中有一个为 True，or 运算结果就是 True。

3. not 运算是非运算，它是一个单目运算符，把 True 变成 False，False 变成 True。


### Python 空值 用None来标识

```
empty_val = None

```

### Python 编码 



### list Python 内置的一种有序集合数据类型

1. 定义

```
name = ['张三','李四','陈五','王刘','马七']
```

2. 读取

```
print(name[0])
print(name[0:2])
print(name[:])

```

3. 修改

```
name[1] = 'laozhang'

print(name)

name.append('追加')

print(name)
```

4. 删除

```
del name[3]

print(name)
```

5. list 运算符

```
len(name)

```

6. 衔接

```
[1,2,3] + [4,5.6]
```

7. 复制

```
['复制我把！']*5
```

8. 是否存在

```
3 in [1,2,3,4]
```

9 迭代

```
for x in [7,8,9,1,2,3]: 
     
      print(x)
```

10.  List 相关函数和方法

|函数&方法|说明|
|:---|:---|
|len(list)|列表元素个数|
|max(list)|返回列表元素最大值|
|min(list)|返回列表元素最小值|
|list(Tuple)|将元组转换成列表|
|list.append(obj)|在列表尾部追加对象|
|list.count(obj)|统计某元素出现次数|
|list.extend(seq)|在列表尾部一次追加另一个序列的多个值|
|list.index(obj)|列表中某值第一个匹配到的索引位置|
|list.insert(index,obj)|将对象插入列表|
|list.pop(obj=list[-1])|移除列表中的元素默认最后一个并返回其值|
|list.reverse()|反向列表元素|
|list.sort([func])|对列表进行排序|



### Tuple 元组也是有序列表但是定义之后不能被更改

```
tuple0 = ()

# 一个元素需要在后面加逗号 如果只有一个元素时，你不加逗号，计算机就根本没法识别你是要进行整数或者小数运算还是表示元组。

tuple1 = ('t1',)

tuple2 = ('t1','t2','t3')

# 删除只能删除整个元组 无法删除里面元素

del tuple0 

## tuple(seq) 将列表转换成元组


## 更新只可以更新 元组里元素 对象操作
```



### 字典Dict 和 set



































































