# python框架相关
引子：主要收集记录，python的框架模板之类的信息，便于以后查找

**目录**

> [1、requests](#no1)
>
> [2、lxml](#no2)
>
> [3、系统自带模块](#system)
> >[3-1、datetime模块](#s-no1)
> >
> >[3-2、urlparse模块](#s-no2)
> >
> >[3-3、re正则匹配模块](#s-no3)
>
>
> [参考](#info)


## <a name="no1"></a>1、requests
Passing Parameters In URLs

```
	>>> payload = {'key1': 'value1', 'key2': 'value2'}
	>>> r = requests.get('http://httpbin.org/get', params=payload)
	>>> print(r.url)
	
	http://httpbin.org/get?key2=value2&key1=value1
```	

Response Content

```
	>>> import requests

	>>> r = requests.get('https://api.github.com/events')
	>>> r.text
	u'[{"repository":{"open_issues":0,"url":"https://github.com/...
```

Binary Response Content

```
	>>> r.content
	b'[{"repository":{"open_issues":0,"url":"https://github.com/...
```

eg:

	>>> from PIL import Image
	>>> from io import BytesIO

	>>> i = Image.open(BytesIO(r.content))

[更多请参考](http://docs.python-requests.org/en/latest/user/quickstart/)



## <a name="no2"></a>2、lxml

[英文资料](http://lxml.de/tutorial.html#the-xml-function)

[中文参考](http://cuiqingcai.com/2621.html)



##<a name="system"></a>3、系统自带模块
###<a name="s-no1"></a>3-1、datetime模块
时间处理相关的模块，可[参考](http://www.wklken.me/posts/2015/03/03/python-base-datetime.html)

###<a name="s-no2"></a>3-2、urlparse模块
网址信息分析截取模块，可[参考](https://my.oschina.net/guol/blog/95699)

###<a name="s-no3"></a>3-3、re正则匹配模块
正则匹配模块，和perl脚本的正则匹配很像可[参考](http://www.runoob.com/python/python-reg-expressions.html)

正则匹配的[demo](http://www.codeceo.com/article/python-regular-expressions-re-module.html)

[What is the difference between .*? and .* regular expressions](http://stackoverflow.com/questions/3075130/what-is-the-difference-between-and-regular-expressions)

It is the difference between greedy and non-greedy quantifiers.

Consider the input 101000000000100.

Using 1.*1, * is greedy - it will match all the way to the end, and then backtrack until it can match 1, leaving you with 1010000000001.
.*? is non-greedy. * will match nothing, but then will try to match extra characters until it matches 1, eventually matching 101.

All quantifiers have a non-greedy mode: .*?, .+?, .{2,6}?, and even .??.





##<a name="info"></a>参考
[系统自带库的官方文档](https://docs.python.org/2/library/index.html)
