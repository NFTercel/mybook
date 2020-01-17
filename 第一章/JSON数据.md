# 第3节：JSON数据

## JSON简介


JSON( JavaScript Object Notation,即 JavaScript对象表示法)是一种轻量级的数据交换格式。它独立于语言和平台,JSON解析器和JSON库支持不同的编程语言。
JSON具有自我描述性,很容易理解.目前大多数接口返回的数据格式为JSON,因此进行接口测试必须掌握JSON

---

## JSON语法


### 语法规则

* 数据在键/值对中
* 数据由逗号分隔
* {花括号}保存对象
* [方括号]保存数组

### JSON键/值对

JSON数据的书写格式是:key: value键值对。比如:

    “Name”："512xW"

JSON值可以是：
* 数字(整数或浮点数)
* 字符串(在双引号中)
* 逻辑值(true或 false)
* 数组(在方括号中)
* 对象(在花括号中)

### JSON数字

    "status code": 200

### JSON字符串

    "Name":"51zxw"
### JSON逻辑值

    "result" : true

### JSON数组

    "user":["51zxw","zxw2818","zXw666"]
### JSON对象

JSON对象在花括号中书写:对象可以包含多个键/值对:

  ``` { "firstName":"John","lastName":"Doe"}```
Tips:在接口测试过程中,一般都是返回JsON对象类型。



### JSON数据嵌套

比如在数组中含多个对象:

```json
{
"employees":[
{"firstName":"John","lastName":"Doe"},
{"firstName ": "Anna","lastName": Smith"},
{"firstName":"Peter","lastName":"Jones"}
]
}
```
在上面的例子中,对象" employees"是包含三个对象的数组.每个对象代表条关于某人(有姓和名)的记录。

---

## JSON数据解析


Python3中可以使用json模块来对JSoN数据进行编解码,它包含了两个方法:
*  json. dumps():将 python数据转化为Json数据
*  json. loads():将json数据类型转为 Python数据类型

JSON库官方文档<https://docs.python.org/3/library/json.html>

### json.dumps()

将 python数据转化为Json数据 json_ dumps.py

```Python
import json

 data={'id': 1, 'name':'51zxw','password':'66666'}
print (type(data))
json_str=json.dumps(data)
print(type (ison_str)
print(json_str)
```
输出结果：

    <class ’dict‘>
    <class ’str‘>
    {"password":"66666","id": 1,"name":“51Zxw")

### json.loads()

将json数据类型转为 Python数据类型 json_loads.py

```Python
import json
 json_str='{"id": 1,"name":"51zxw","password": "66666"}'
data=json.loads(json_str)
print(type(json_str))
print(type(data)
print(data)
print(data[ 'id'])
print(data['name'])
```
输出结果:   

    <class ’dict‘>
    <class ’str‘>
    {'name':'51zxw','password':'66666','id':1)
    1
     51zxw

### Json文件处理

有时我们可能需要将JSON数据写入到文件,或者从Json数据文件读取数据

```Python
#写入JSON数据到文件
with open('data. json',w) as f:
    json, dump(data, f)

#读取JSON数据文件
with open('data.json' ,'r') as f:
    data= json. load(f)
```

---
## 参考资料

* <https://www.w3school.com.cn/json/index.asp>
* <https://www.runoob.com/python3/python3-json.html>





