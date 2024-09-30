# <center>Python 爬虫</center>

## <font class="text-color-13" color="#ffeb3b">requests 库</font>
- Python的 `requests` 库是一个功能强大且易于使用的HTTP客户端库，用于发送HTTP请求。它使得发送HTTP请求变得简单，支持各种请求方法（GET、POST、PUT、DELETE等）和数据格式（如JSON、表单数据等）。

- 安装requests库：
	- 如果您尚未安装`requests`库，可以使用以下命令通过pip安装它：
```bash
pip install requests
```

## <font class="text-color-121" color="#ffeb3b">get</font>
- `get` 方法是 `requests` 库的一个重要函数，用于发送 HTTP GET 请求并获取服务器的响应数据
```python
requests.get(url, params=None, **kwargs)
```
**参数：**

- `url` (str)：需要请求的目标 URL 地址。
- `params` (dict, optional)：字典或字节序列，作为 GET 请求的查询参数，会附加在 URL 后面。例如：`http://example.com/resource?param1=value1&param2=value2`。
- `**kwargs`：可选的关键字参数，用于传递其他配置选项，例如请求头、身份验证等。

**返回值：** `requests.get` 方法返回一个 `Response` 对象，包含服务器响应的所有信息。你可以从这个对象中获取响应的内容、状态码、头部信息等。

- 示例
```python
import requests

# 发送一个简单的 GET 请求
response = requests.get("https://api.example.com/data")

# 获取响应内容
print(response.text)

# 获取状态码
print(response.status_code)

# 获取响应头信息
print(response.headers)

```

- **传递查询参数：** 如果你需要传递查询参数，可以通过 `params` 参数传递一个字典。这些参数会被自动添加到请求的 URL 后面。例如：
```python
import requests

query_params = {
    'key': 'your_api_key',
    'location': 'New York',
    'units': 'metric'
}

response = requests.get("https://api.example.com/weather", params=query_params)
```
- 在上述示例中，`params=query_params` 将字典 `query_params` 中的键值对转换为查询参数附加到 URL 上，从而构建了类似于 `https://api.example.com/weather?key=your_api_key&location=New%20York&units=metric` 的请求。

- **其他选项：** 除了 `params` 参数，`requests.get` 方法还接受其他可选的关键字参数，如 `headers`、`auth`、`timeout` 等。你可以使用这些参数来配置请求的头部信息、进行身份验证，以及设置超时时间等。例如：
```python
import requests

headers = {
    'User-Agent': 'CustomUserAgent/1.0'
}

response = requests.get("https://api.example.com/resource", headers=headers, auth=('username', 'password'), timeout=10)
```
- [Header 的设置](https://zhuanlan.zhihu.com/p/518788491)

- [爬虫请求头生成工具](https://curlconverter.com/)

## <font class="text-color-121" color="#ffeb3b">Beautiful Soup 库</font>
- `bs4`（Beautiful Soup 4）是Python中一个功能强大且易于使用的库，用于解析HTML和XML文档，并提供了方便的方法来提取其中的数据。`bs4` 使得解析和处理HTML或XML文档变得简单，并且支持多种解析器，包括Python标准库中的 `html.parser`、`lxml` 和 `html5lib`。

### <font class="text-color-15" color="#ff9800">安装 bs4</font>
- 如果你还没有安装 `bs4` 包，可以使用以下命令来安装：
```
pip install beautifulsoup4
```
### <font class="text-color-15" color="#ff9800">导入 bs4 库</font>
	- 在Python脚本中，首先需要导入 `bs4` 库：
```python
from bs4 import BeautifulSoup
```
### <font class="text-color-15" color="#ff9800">创建 BeautifulSoup 对象</font>
- 要使用 `bs4` 库解析 HTML 或 XM L文档，首先需要创建一个 BeautifulSoup 对象，将要解析的文档和解析器作为参数传递给它。通常情况下，我们会使用 Python 标准库中的 `html.parser` 解析器：
```python
html_doc = "<html><head><title>Example</title></head><body><p>Hello, World!</p></body></html>"
soup = BeautifulSoup(html_doc, 'html.parser')
```
### <font class="text-color-15" color="#ff9800">寻找标签</font>
- 通过创建 BeautifulSoup 对象后，我们可以使用多种方法来寻找 HTML 文档中的标签。例如，可以使用 `find` 方法找到第一个符合条件的标签：
```python
title_tag = soup.find('title')
```
- 或者使用 `find_all` 方法找到所有符合条件的标签：（返回一个列表）
```python
p_tags = soup.find_all('p')
```

### <font class="text-color-15" color="#ff9800">提取标签内容</font>
- 一旦找到了标签，我们可以使用 `.text` 属性来提取标签的文本内容：
```python
title_text = title_tag.text
```
### <font class="text-color-15" color="#ff9800">获取标签属性</font>
- 如果标签有属性，我们可以使用字典的方式来获取标签的属性值：
```python
link_tag = soup.find('a')
href_value = link_tag['href']
```

### <font class="text-color-15" color="#ff9800">遍历文档树</font>
- `bs4`还支持对文档树的遍历，可以使用 `children` 、 `descendants` 等属性来获取标签的子标签和后代标签：
```python
for child in soup.body.children:
    print(child)
```

### <font class="text-color-15" color="#ff9800">CSS选择器</font>
- `bs4` 还支持使用CSS选择器来查找标签，可以使用 `.select` 方法并传递CSS选择器作为参数：
```python
p_tags = soup.select('p')
```

### <font class="text-color-15" color="#ff9800">find 和 findAll 方法</font>
-  `find` 和 `findAll` （或 `find_all` ）方法用于查找 HTML 文档中的标签。它们可以根据标签名、属性、文本内容等条件来查找标签，并返回匹配的结果。

#### <font class="text-color-7" color="#03a9f4"> find 方法</font>
- `find` 方法用于查找第一个匹配的标签。它的基本语法为：
```python
find(name, attrs, recursive, string, **kwargs)
```
- `name`：要查找的标签名，可以是字符串或列表，例如：`'div'`、`['div', 'span']`。
- `attrs`：可选参数，用于指定标签的属性和属性值，可以是字典或关键字参数，例如：`{'class': 'content', 'id': 'post'}`
- `recursive`：可选参数，表示是否递归查找，默认为`True`。如果设置为`False`，则只在当前标签的直接子标签中查找。
- `string`：可选参数，用于匹配标签的文本内容。
- `**kwargs`：额外的关键字参数用于匹配标签的其他属性，例如：`id='post'`。

- 示例
```python
from bs4 import BeautifulSoup

html_doc = """
<html>
  <head><title>Example</title></head>
  <body>
    <div class="content" id="post">
      <p>Hello, World!</p>
    </div>
    <div class="content">
      <p>Another paragraph.</p>
    </div>
  </body>
</html>
"""

soup = BeautifulSoup(html_doc, 'html.parser')

# 查找第一个<div>标签
div_tag = soup.find('div')
print(div_tag)

# 查找class为"content"的第一个<div>标签
div_with_class = soup.find('div', class_='content')
print(div_with_class)

# 查找id为"post"的第一个<div>标签
div_with_id = soup.find('div', id='post')
print(div_with_id)
```

#### <font class="text-color-61" color="#03a9f4">findAll 方法</font>
- `findAll` 方法用于查找所有匹配的标签，并返回一个包含所有匹配结果的列表。它的基本语法与 `find` 方法类似：
```python
findAll(name, attrs, recursive, string, limit, **kwargs)
```
- 参数含义与 `find` 方法相同，除了多了一个 `limit` 参数，用于指定返回的结果数量，默认为不限制。

- 示例：
```python
from bs4 import BeautifulSoup

html_doc = """
<html>
  <head><title>Example</title></head>
  <body>
    <div class="content">
      <p>Hello, World!</p>
    </div>
    <div class="content">
      <p>Another paragraph.</p>
    </div>
  </body>
</html>
"""

soup = BeautifulSoup(html_doc, 'html.parser')

# 查找所有<div>标签
div_tags = soup.findAll('div')
for div_tag in div_tags:
    print(div_tag)

# 查找class为"content"的所有<div>标签
divs_with_class = soup.findAll('div', class_='content')
for div_with_class in divs_with_class:
    print(div_with_class)

# 查找所有<p>标签
p_tags = soup.findAll('p')
for p_tag in p_tags:
    print(p_tag)

# 只查找前两个<p>标签
p_tags_limited = soup.findAll('p', limit=2)
for p_tag_limited in p_tags_limited:
    print(p_tag_limited)
```

## <font class="text-color-121" color="#ffeb3b">爬取示例</font>
```python
import requests
from bs4 import BeautifulSoup
import re

cookies = {
   # cookies 信息 
}

headers = {
   # headers 信息
}

# 定义正则表达式
pattern = re.compile(r'】(.*?)【')

# 打开指定写入文件
with open("<path>", 'w', encoding='utf-8') as file:
    # 自定义页码
    for page in range(1, 50):
        # 获取 html 页面（发出请求）
        content = requests.get(f'<url>', cookies=cookies, headers=headers).text
        # 解析 html 页面
        soup = BeautifulSoup(content, "html.parser")
        # 按 class 查找所有 a 标签
        all_title = soup.findAll("a", attrs={"class": "<class 名字>"})
        # 写入页号
        file.write(f"- 第{page}页：\n")
        # 写入内容
        for title in all_title:
            result = pattern.search(title.string)
            if result:
                content = result.group(1)
                file.write(f"   - {content}\n")
            else:
                # file.write(f"   {title.string}\n")
                pass
        # 当前页操作完成
        print(f"第{page}页采集完成！")

# 全部操作完成
print("操作完成！") 
```




