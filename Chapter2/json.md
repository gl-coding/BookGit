# 第1节：通信数据格式Json

##Json

JSON：JavaScript 对象表示法（JavaScript Object Notation）。**

**JSON 是存储和交换文本信息的语法。类似 XML。**

**JSON 比 XML 更小、更快，更易解析。**

## 每一章中用到的实例

```json
{
    "employees":[
        {
            "firstName":"Bill",
            "lastName":"Gates"
        },
        {
            "firstName":"George",
            "lastName":"Bush"
        },
        {
            "firstName":"Thomas",
            "lastName":"Carter"
        }
    ]
}
```

这个 employee 对象是包含 3 个员工记录（对象）的数组。



## 什么是 JSON ？

- JSON 指的是 JavaScript 对象表示法（*J*ava*S*cript *O*bject *N*otation）
- JSON 是轻量级的文本数据交换格式
- JSON 独立于语言 *
- JSON 具有自我描述性，更易理解

\* JSON 使用 JavaScript 语法来描述数据对象，但是 JSON 仍然独立于语言和平台。JSON 解析器和 JSON 库支持许多不同的编程语言。



### JSON 语法规则

- 数据在名称/值对中
- 数据由逗号分隔
- 花括号保存对象
- 方括号保存数组

### JSON 名称/值对

JSON 数据的书写格式是：`{Key:Value}`、`{Key:Array}`。

`{Key:Value}`，前面是键，中间是英文的“:”（冒号），然后是值。但是注意的是如果是字符串，严格来说都是英文双引号引起来的

如：`{"Key":"Value"}`

```
{"name" : "鹿晗"}
```

这很容易理解，等价于这条 JavaScript 语句：

```
name = "鹿晗"
```

### JSON 值范围

- 数字（整数或浮点数）
- 字符串（在双引号中）
- 逻辑值（`true` 或 `false`）
- 数组（在方括号中）
- 对象（在花括号中）
- `null`

### JSON 对象

JSON 对象在花括号中，对象可以包含多个名称/值对，如下代码所示：

```
{    "name": "鹿晗",    "age": 26,    "birthday": "1990年4月20日",}
```

这一点也容易理解，与这条 JavaScript 语句等价：

```
name = "鹿晗";age = 26;birthday = "1990年4月20日";
```

### JSON 数组

JSON 数组在方括号（"[]"）中书写，数组可包含多个对象，如下“star_male”描述

```
{    "star_male": [        {            "name": "鹿晗",            "age": "26"        },        {            "nickname": "李易峰",            "age": "29"        },        {            "nickname": "陈赫",            "lastName": "31"        }    ]}
```

在上面的例子中，对象 "star_male" 是包含三个对象的数组。每个对象代表一条关于一个明星（姓名和年龄）的记录。

### 常见的 JSON 格式

- `{"key":"value"}`，最简单的JSON 格式。
- `{"key1":"value1","key2":"value2"}`，一个JSON中有多个键值对的表达方式。
- `{"key":["a","b","sojson.com"]}`，value是一个Array 的JSON格式。
- `{"sojson":["5年","JSON在线解析","sojson.com",true,1,null]}`，value是一个Array 的JSON格式，并且这个数组中有多重类型的元素，有String，Boolean，Number，null。
- `{"key":{"json":"json for javascript"}}`，value 是JSONObject的JSON格式。

JSON && XML

### JSON

- JSON 是纯文本
- JSON 具有“自我描述性”（人类可读）
- JSON 具有层级结构（值中存在值）
- JSON 可通过 JavaScript 进行解析
- JSON 数据可使用 AJAX 进行传输

### JSON && XML不同之处

- 没有结束标签
- 更短
- 读写的速度更快
- 能够使用内建的 JavaScript eval() 方法进行解析
- 使用数组
- 不使用保留字

### 为什么使用 JSON？*JSON 的优点*

- 更短
- 读写的速度更快
- 能够使用内建的 JavaScript eval() 方法进行解析
- 使用数组
- 不使用保留字
- ... ...

对于 AJAX 应用程序来说，JSON 比 XML 更快更易使用。

### 使用 XML

- 读取 XML 文档
- 使用 XML DOM 来循环遍历文档
- 读取值并存储在变量中

### 使用JSON

- 读取 JSON 字符串
- 用 eval() 处理 JSON 字符串

# Python JSON

本章节我们将为大家介绍如何使用 Python 语言来编码和解码 JSON 对象。

JSON(JavaScript Object Notation) 是一种轻量级的数据交换格式，易于人阅读和编写。

------

## JSON 函数

使用 JSON 函数需要导入 json 库：**import json**。

| 函数       | 描述                                     |
| :--------- | :--------------------------------------- |
| json.dumps | 将 Python 对象编码成 JSON 字符串         |
| json.loads | 将已编码的 JSON 字符串解码为 Python 对象 |

------

## json.dumps

json.dumps 用于将 Python 对象编码成 JSON 字符串。

### 语法

```
json.dumps(obj, skipkeys=False, ensure_ascii=True, check_circular=True, allow_nan=True, cls=None, indent=None, separators=None, encoding="utf-8", default=None, sort_keys=False, **kw)
```

### 实例

以下实例将数组编码为 JSON 格式数据：

```
#!/usr/bin/python
import json

data = [ { 'a' : 1, 'b' : 2, 'c' : 3, 'd' : 4, 'e' : 5 } ]

json = json.dumps(data)
print json
```

以上代码执行结果为：

```
[{"a": 1, "c": 3, "b": 2, "e": 5, "d": 4}]
```

使用参数让 JSON 数据格式化输出：

```
>>> import json
>>> print json.dumps({'a': 'Runoob', 'b': 7}, sort_keys=True, indent=4, separators=(',', ': '))
{
    "a": "Runoob",
    "b": 7
}
```

python 原始类型向 json 类型的转化对照表：

| Python           | JSON   |
| :--------------- | :----- |
| dict             | object |
| list, tuple      | array  |
| str, unicode     | string |
| int, long, float | number |
| True             | true   |
| False            | false  |
| None             | null   |

------

## json.loads

json.loads 用于解码 JSON 数据。该函数返回 Python 字段的数据类型。

### 语法

```
json.loads(s[, encoding[, cls[, object_hook[, parse_float[, parse_int[, parse_constant[, object_pairs_hook[, **kw]]]]]]]])
```

### 实例

以下实例展示了Python 如何解码 JSON 对象：

```
#!/usr/bin/python
import json

jsonData = '{"a":1,"b":2,"c":3,"d":4,"e":5}';

text = json.loads(jsonData)
print text
```

以上代码执行结果为：

```
{u'a': 1, u'c': 3, u'b': 2, u'e': 5, u'd': 4}
```

json 类型转换到 python 的类型对照表：

| JSON          | Python    |
| :------------ | :-------- |
| object        | dict      |
| array         | list      |
| string        | unicode   |
| number (int)  | int, long |
| number (real) | float     |
| true          | True      |
| false         | False     |
| null          | None      |

#JavaScript JSON

##JSON.parse()

`JSON.parse()`是Javascript中一个常用的 JSON 转换方法，`JSON.parse()`可以把JSON规则的字符串转换为JSONObject，`JSON.parse()`很方便，并且几乎支持所有浏览器。

### JSON.parse() 语法

```
JSON.parse(text[, reviver])//text:需要被转换的字符串。//[, reviver] : 可选参数，可以是一个回调方法。
```

返回值是一个 [JSONObject](https://www.sojson.com/json/json_object.html)。

### JSON 解析实例

我们得到的数据如下：

```
'{"domain" : "sojson.com","author":"soso"}'
```

外面被引号包裹起来了，证明它就是个字符串，而不是JSON对象，那么我们要转换，这个时候`JSON.parse()` 就可以派上用场了。

```
var json = JSON.parse('{"domain" : "sojson.com","author":"soso"}');
```

如果抛出语法错误（Uncaught SyntaxError），正确会返回一个JSONObject，我们来输出一把，获取“domain”。

```
var json = JSON.parse('{"domain" : "sojson.com","author":"soso"}');alert("json.domain = " + json.domain);//alert(json['domain']);//或者这样也可以
```



##JSON.stringify()

`JSON.stringify()`是Javascript中一个常用的内置 JSON 转换方法，`JSON.stringify()`可以把JSONObject 转化为 JSON 规则的字符串转换为，`JSON.stringify()`很方便，并且几乎支持所有浏览器。

### JSON.stringify() 语法

```
JSON.stringify(value[, replacer[, space]])
```

### JSON.stringify() 参数说明

| 参数     | 参数说明                                                     | 备注 |
| :------- | :----------------------------------------------------------- | :--- |
| value    | 将要序列化成 一个JSON 字符串的值。                           | 必选 |
| replacer | 如果是一个function，那么每个序列化成JSON的value都会经过这个function，如果是一个Array，那么序列化后的JSON字符串中的Key在这个数组中才会加入到返回的JSON 字符串中去。 | 可选 |
| space    | 用于美化JSON字符串，如果是一个Number类型，代表的就是多少个空格。如果是0或者小于0，那么就是没有空格（和不填此项没有区别），如果是字符串，那么直接填充。 | 可选 |

### JSON.stringify() 返回值说明

返回值是一个 JSON字符串，如：`"{"domain":"sojson.com"}"`。

### JSON.stringify() JSON To String

测试样例如下：

```
var json = {"domain" : "sojson.com","author":"soso"}
```

它就是一个正常的JSON对象，我们需要把它转换成字符串，这个时候`JSON.stringify()` 就可以派上用场了。

```
var json = {"domain" : "sojson.com","author":"soso"}alert(JSON.stringify(json));
```