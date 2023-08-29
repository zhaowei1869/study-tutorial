## 爬虫时带有中文url如何处理

将URL作为参数传递，需将URL进行转义，可以使用JS中提供转义字符串和解析字符串的方法

解析字符串（decodeURIComponent）

```
let url = 'http%3A%2F%2Fm.test.com%2Flogin'
url = decodeURIComponent(url) 
console.log(url) 

// http://m.test.com/login
```

转义字符串（encodeURIComponent）

```
let url = 'http://m.test.com/login'
url = encodeURIComponent(url)   
console.log(url) 

//   'http%3A%2F%2Fm.test.com%2Flogin
```



------------------------------------------------
原文链接：https://blog.csdn.net/m0_49886030/article/details/118968592



爬虫过程中需要构建url，有的url不可避免的 出现中文字符
例如：https://baike.baidu.com/item/泰山石膏（湖北）有限公司
直接输入带有中文字符的url有可能会出现编码错误，原因是url里面不允许带有中文
这时候上网上搜索可能会查看需要使用 from urllib.parse import quote来对中文进行转换，然而整个转换url之后，显示不存在这个页面
解决方法是只把中文字符进行quote转换，然后与之前的前缀合并

下面是代码：

```
from urllib.parse import quote
url = ‘https://baike.baidu.com/item/’ + quote(name)
```

```
import urllib

rooturl = "https://baike.baidu.com/item/"
item = "爬虫"
item = urllib.parse.quote(item)
url = rooturl+item
print(url)

request = urllib.request.Request(url=url)
reponse = urllib.request.urlopen(request)
result = reponse.read()
result = str(result, encoding="utf-8")
print(result)
```



------------------------------------------------
原文链接：https://blog.csdn.net/qq_33624866/article/details/110949600





## Python如何import不同文件夹下的文件(module)

### 3.b.py在任意路径下

假设 b.py 在路径 H:\Documents\user\test 下，则需要通过如下代码将路径加入到系统路径中，然后直接导入 b.py即可。

```text
import sys
sys.path.append(r"H:\Documents\user\test")
import b
```

注意：由于python中 '\' 是转义符号，因此路径名称的字符串需要写成 r"H:\Documents\user\test" 或 "H:\\Documents\\user\\test" 。

### **1. a.py 和 b.py 在同一目录下**

直接 import 即可：

```python3
import b
```

或者

```text
from b import *
```

两者的区别是：

如果用 import b，我们在调用b.py中定义的函数fun1()或类class1()时，需要写成 b.fun1()或b.class1()；

如果用 from b import *，我们在调用b.py中定义的函数fun1()或类class1()时，可以直接写成 fun1()或class1()；

### **2. b.py 在 子目录 test下**

需要先在test目录下创建一个空文件 __init__.py。创建该文件的目的是将test目录变成一个Python包。

![img](https://pic2.zhimg.com/80/v2-11312f848d3ac760fdbfb44bd7bc702d_1440w.webp)

然后我们就可以通过如下方式 import

```text
import test.b
```

或者

```text
from test.b import *
```

- 如果test包中还有子目录 sub_test/，则**不需要**在sub_test/中创建 __init__.py 即可通过如下方式导入 sub_test/中的 c.py

![img](https://pic3.zhimg.com/80/v2-4a7b402e5e6acf2599b4d9a236e29e62_1440w.webp)

```text
import test.sub_test.c
```