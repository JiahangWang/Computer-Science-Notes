# <center>HTML</center>

## <font class="text-color-13" color="#ffeb3b">概述</font>
* HTML代表超文本标记语言（Hypertext Markup Language）。它是一种用于创建和呈现Web页面的标记语言。HTML使用标记来描述Web文档中的各个部分，例如标题、段落、列表、链接和图像等。它还提供了一种用于创建网页结构和布局的标准方式。Web浏览器解析HTML代码并将其呈现为可视化的Web页面。HTML也可以与其他技术（如CSS和JavaScript）结合使用，以增强Web页面的外观和功能。

* HTML 由World Wide Web Consortium（W3C）制定。W3C是一个国际性组织，致力于推动Web技术的发展和标准化，由Web的发明者Tim Berners-Lee于1994年创立。

* HTML最初的版本是在1991年由Tim Berners-Lee和他的团队开发的，主要用于创建Web页面和在页面之间创建超链接。随着Web技术的不断发展和演变，HTML也不断更新和改进，至今已经发展到了HTML5版本。HTML5引入了一系列新的特性和API，包括多媒体支持、本地存储、Web组件、Canvas等，使得Web应用程序可以更加丰富、复杂和实用。

* 除了HTML外，W3C还制定了许多其他的Web标准和技术规范，例如CSS、XML、DOM、Web服务等，这些标准和规范为Web开发提供了统一的编程模型和开发工具，使得Web应用程序能够更加可靠、可维护和可扩展。

* <a href=https://www.runoob.com/html/html-tutorial.html>HTML菜鸟教程</a>

### <font class="text-color-15" color="#ff9800">b/s和c/s架构</font>
#### <font class="text-color-7" color="#03a9f4">b/s 架构</font>
* b/s架构代表浏览器/服务器架构（Browser/Server architecture）。这种架构的基本思想是将应用程序的处理分为客户端和服务器端两部分，通过网络进行交互。浏览器是客户端，负责向服务器发送请求并接收响应，而服务器则负责处理请求并返回响应。通常使用的语言有HTML、CSS、JavaScript和服务器端的语言如PHP、Java、Python等。

* b/s架构的优点：

	1. 跨平台性好，因为Web浏览器可以在各种操作系统和设备上运行。
	2. 管理和维护相对简单，因为只需要维护服务器端的应用程序。
	3. 更好的安全性，因为客户端只是浏览器，无法访问服务器端的代码和数据。
	4. 更新和部署更容易，因为只需更新服务器端的应用程序即可，客户端无需任何操作。
	
* b/s架构的缺点：

	1. 受限于Web浏览器的功能，无法实现高级的用户界面和交互体验。
	2. 对于大规模并发请求，服务器端的负载可能会变得非常高，导致性能瓶颈。

#### <font class="text-color-61" color="#03a9f4">c/s 架构</font>
* c/s架构代表客户端/服务器架构（Client/Server architecture）。在这种架构中，客户端和服务器之间存在一个网络连接，客户端发送请求，服务器响应请求，并向客户端提供所需的服务。与b/s架构不同，c/s架构在客户端上运行本地应用程序，而不是使用Web浏览器。这种架构通常使用的语言有C、C++、Java、C#、Python等。

* c/s架构的优点：

	1. 可以实现更复杂的用户界面和交互体验，因为客户端可以直接访问本地计算机的资源。
	2. 对于高性能和大规模的应用程序，c/s架构比b/s架构更为适用。
	3. 可以通过客户端缓存来减轻服务器端的负载，提高性能。

* c/s架构的缺点：

	1. 跨平台性较差，因为客户端应用程序必须为特定的操作系统和设备编写。
	2. 管理和维护较为复杂，因为需要管理和维护客户端和服务器端的应用程序。
	3. 安全性较差，因为客户端应用程序可以访问本地计算机的资源，可能会受到恶意软件和攻击的威胁。
	4. 更新和部署相对困难，因为需要在所有客户端上安装新版本的应用程序。

## <font class="text-color-13" color="#ffeb3b">语法</font>
* html 不区分大小写，语法松散
* 结构分为：根，标题，主体
```html
<!--1.
    这是html的注释
    下面第一行表示 html5 语法，去掉就表示 html4
-->
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">  <!--设置浏览器打开文件使用的字符集-->
    <title>网页的标题</title>
  </head>
  <body>
  网页的主题内容
  </body>
</html>
```
* HTML可以被视为一棵树形结构，其中每个元素都是一个节点，而文本和其他内容则是节点的子节点。树的根节点是HTML文档本身，而树的分支是由HTML标记形成的。每个标记都包含一个开始标记和一个结束标记，它们之间包含了其他标记或文本节点。这种树形结构的表示方式使得我们可以轻松地遍历HTML文档的内容，访问和修改其中的元素和属性。

## <font class="text-color-13" color="#ffeb3b">基本标签</font>

### <font class="text-color-141" color="#ff9800">元数据信息 meta</font>
* `<meta>` 是一个HTML元素，它用于提供有关网页的元数据信息，如网页的描述、作者、关键字和字符集等。这些信息通常被浏览器和搜索引擎使用，以帮助它们更好地理解和呈现网页内容。

* 例如：
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="description" content="这是一个网页描述">
    <meta name="keywords" content="HTML, CSS, JavaScript">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="author" content="John Doe">
    <meta name="robots" content="index,follow">
    <title>我的网页</title>
</head>
<body>
    <h1>欢迎来到我的网页</h1>
    <p>这是一个演示用的网页</p>
</body>
</html>

```

* 常用的 `<meta>` 属性：

| 属性      | 描述                                                                                                 |
|-----------|------------------------------------------------------------------------------------------------------|
| charset   | 定义网页使用的字符集。例如：<meta charset="UTF-8">表示使用UTF-8字符集。                             |
| name      | 定义元数据的名称。例如：<meta name="description" content="这是一个网页描述">表示定义网页的描述。     |
| content   | 定义元数据的值。例如：<meta name="keywords" content="HTML, CSS, JavaScript">表示定义网页的关键字。   |
| http-equiv| 模拟HTTP头部信息，例如：<meta http-equiv="refresh" content="5;url=http://example.com">表示让浏览器在5秒后跳转到example.com网站。|
| viewport  | 定义网页在移动设备上的视口，例如：<meta name="viewport" content="width=device-width, initial-scale=1.0">表示让网页在移动设备上适应屏幕宽度，并以原始比例缩放。 |
| author    | 定义网页的作者，例如：<meta name="author" content="John Doe">表示定义网页的作者为John Doe。           |
| robots    | 定义搜索引擎如何处理网页，例如：<meta name="robots" content="index,follow">表示让搜索引擎索引该网页并跟踪其中的链接。|


### <font class="text-color-15" color="#ff9800">段落标记 p</font>
```html
<!doctype html>
<html>
    <head>
        <title>html基本标签</title>
    </head>
    <body>
        <!--段落标记 <p> -->
        <p>
            Tim Berners-Lee（蒂姆·伯纳斯-李）是英国的一位计算机科学家，也是Web的发明者之一。他于1989年在瑞士的欧洲核子研究中心（CERN）创建了第一个Web服务器，并开发出了第一个Web浏览器和Web服务器软件，从而创造了现代Web的基础。
        </p>
        <p>
            Berners-Lee出生于1955年，曾在英国牛津大学学习物理学和计算机科学，毕业后曾在CERN工作多年。他的Web发明是基于解决科学研究机构之间共享信息的需求，为了方便这些机构之间的信息交流而开发的一种系统。
        </p>
    </body>   
</html>
```
### <font class="text-color-141" color="#ff9800">标题字 h</font>
```html
<!doctype html>
<html>
    <head>
        <title>html基本标签</title>
    </head>
    <body>
        <!--标题 <h> -->
        <h1>一级标题</h1>
        <h2>二级标题</h2>
        <h3>三级标题</h3>
    </body>   
</html>
```
### <font class="text-color-141" color="#ff9800">居中 center</font>
```html
<!doctype html>
<html>
    <head>
        <title>html基本标签</title>
    </head>
    <body>
        <center>haha</center>
    </body>   
</html>
```

### <font class="text-color-141" color="#ff9800">换行 br</font>
* \<br> 标记属于独目标记
```html
<!doctype html>
<html>
    <head>
        <title>html基本标签</title>
    </head>
    <body>
        <!--换行 <br> -->
        Hello<br>World!
    </body>   
</html>
```
### <font class="text-color-141" color="#ff9800">横线 hr</font>
```html
<!doctype html>
<html>
    <head>
        <title>html基本标签</title>
    </head>
    <body>
        <!-- 横线 <hr> -->
        Hello World!
        <hr>
        hi
        <hr align="left" size="2" width="50%" color="black">
        你好
    </body>   
</html>
```
* HTML的\<hr>标签（水平线标签）可以设置以下属性：

| 属性名 | 描述 | 取值 |
| ------ | ------ | ------ |
| `align` | 指定水平线的对齐方式 | `left`, `center`, `right`, `justify`（默认值：`center`） |
| `color` | 指定水平线的颜色 | 颜色名称、十六进制值或RGB值 |
| `size` | 指定水平线的高度 | 数字或百分比值（默认值：`1`） |


### <font class="text-color-141" color="#ff9800">预留格式 pre</font>
* 按照预留格式输出
```html
<!doctype html>
<html>
    <head>
        <title>html基本标签</title>
    </head>
    <body>
        <!-- 预留格式 <pre> -->
        <pre>
            for (int i = 0; i < 10; i++) {
                System.out.println("i is " + i);
            }
        </pre>
    </body>   
</html>
```
### <font class="text-color-141" color="#ff9800">字的格式</font>
```html
<!doctype html>
<html>
    <head>
        <title>html基本标签</title>
    </head>
    <body>
        <!-- 字的格式 -->
        <del>删除字</del>
        <ins>插入字</ins>
        <b>粗体字</b> 
        <i>斜体字</i>
        10<sup>2</sup> <!-- 右上角加字 -->
        10<sub>m</sub> <!-- 右下角加字 -->
        <font color="blue" face="Times New Roman" size="5">Hello, World!</font>

    </body>   
</html>
```
* \<font>标签，可以设置以下属性：

| 属性名 | 描述 | 取值 |
| ------ | ------ | ------ |
| `color` | 设置文本颜色 | 颜色名称、十六进制值或RGB值 |
| `face` | 设置字体 | 字体名称、字体族名称或字体的完整名称 |
| `size` | 设置字体大小 | 数字1-7、相对于父元素的百分比值 |
| `style` | 设置CSS样式属性 | 可以设置CSS样式属性，例如font-style、font-weight、text-decoration等，建议使用CSS样式表来控制样式 |


### <font class="text-color-141" color="#ff9800">实体符号</font>
| 实体符号 | 对应字符 |
| ------ | ------ |
| `&lt;` | `<` |
| `&gt;` | `>` |
| `&amp;` | `&` |
| `&nbsp;` | 空格 |
| `&quot;` | `"` |
| `&apos;` | `'` |
| `&copy;` | © |
| `&reg;` | ® |
| `&trade;` | ™ |
| `&times;` | × |
| `&divide;` | ÷ |
| `&cent;` | ¢ |
| `&pound;` | £ |
| `&yen;` | ¥ |
| `&euro;` | € |
* 举例
```html
<!doctype html>
<html>
    <head>
        <title>html基本标签</title>
    </head>
    <body>
        23 &lt; 55 &gt; 11
        <!-- 23 < 55 > 11 -->
    </body>   
</html>
```

## <font class="text-color-13" color="#ffeb3b">表格</font>
* HTML表格由以下几个元素组成

| 标签        | 描述                                                         |
| ----------- | ------------------------------------------------------------ |
| \<table>    | 定义一个表格。                                               |
| \<caption>  | 定义表格的标题。                                             |
| \<tr>       | 定义表格中的行。                                             |
| \<th>       | 定义表格中的表头单元格。                                     |
| \<td>       | 定义表格中的数据单元格。                                     |
| \<thead>    | 定义表格的表头部分。                                         |
| \<tbody>    | 定义表格的主体部分。                                         |
| \<tfoot>    | 定义表格的页脚部分。                                         |
| \<col>      | 定义表格中某一列的属性，如宽度、颜色等。                     |
| \<colgroup> | 定义表格中一组列的属性，可以在其中包含多个 \<col> 元素。       |
| \<style>    | 定义表格的样式。                                             |

* \<div> 和 \<span> 等元素也可以用于在表格中实现更复杂的布局效果。
* 这些元素都可以添加属性，具体参见：<a href=https://www.runoob.com/html/html-tables.html>html表格</a>

* 例如：
```html
<!doctype html>
<html>
    <head>
        <title>html表格</title>
    </head>
    <body>

        <center>
        <!--表格-->
        <table border="1" width="50%" height="150">
            <!--第1行-->
            <tr align="center">
                <!--单元格-->
                <td>a</td>
                <td>b</td>
                <td>c</td>
            </tr>
            <!--第2行-->
            <tr align="center">
                <!--单元格-->
                <td>d</td>
                <td>e</td>
                <td>f</td>
            </tr>
        </table>
        </center>

    </body>   
</html>
```
### <font color="orange">合并单元格</font>
* row 合并的时候，规定删除下面的单元格
* col 合并对删除哪个没有要求
```html
<!doctype html>
<html>
    <head>
        <title>html表格</title>
    </head>
    <body>
        <!-- 合并单元格 -->
        <table border="1" width="50%">
            <tr>
                <td>1</td>
                <td>2</td>
                <td rowspan="2">3</td>  <!-- 行合并 -->
            </tr>
            <tr>
                <td>4</td>
                <td>5</td>
            </tr>
            <tr>
                <td colspan="2">6</td>  <!-- 列合并 -->
                <td>8</td>
            </tr>
        </table>
    </body>
</html>
```
### <font color="orange">表头</font>
* 表格第一行用 \<th> 表示表头，会居中和加粗
```html
<!doctype html>
<html>
    <head>
        <title>html表格</title>
    </head>
    <body>
        <!-- 表格 -->
        <table border="1" width="50%" align="center" style="text-align:center">
            <tr>
			<!-- 表头 -->
                <th>Title1</th>
                <th>Title2</th>
                <th>Title3</th>
            </tr>
            <tr>
                <td>1</td>
                <td>2</td>
                <td>3</td>
            </tr>
            <tr>
                <td>4</td>
                <td>5</td>
                <td>6</td>
            </tr>
        </table>
    </body>
</html>
```

### <font color="orange">thead tbody tfoot 标签</font>
* thead tbody tfoot 标签在 table 中不是必须的，但是这样做便于 JS 代码的编写
* 示例
```html
<!doctype html>
<html>
    <head>
        <title>html表格</title>
    </head>
    <body>
        
        <table border="1" width="50%" align="center" style="text-align:center">
            <thead>
              <tr>
                <th>名称</th>
                <th>价格</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>苹果</td>
                <td>$1.99</td>
              </tr>
              <tr>
                <td>橙子</td>
                <td>$2.99</td>
              </tr>
              <tr>
                <td>香蕉</td>
                <td>$0.99</td>
              </tr>
            </tbody>
            <tfoot>
              <tr>
                <td>总计</td>
                <td>$5.97</td>
              </tr>
            </tfoot>
          </table>
          
    </body>   
</html>
```

## <font color="#ffeb3b">颜色 、图片、超链接</font>

### <font class="text-color-15" color="#ff9800">背景颜色和图片</font>

* bgcolor 属性被用于设置一个 HTML 元素的背景颜色，它可以被用于 \<body> 元素、\<table> 元素、\<tr> 元素、\<td> 元素等元素上。该属性的取值可以是颜色名称、颜色

* background 属性用于设置一个 HTML 元素的背景图片，它可以被用于 \<body> 元素、\<table> 元素、\<div> 元素等元素上。该属性的取值是一个图片的 URL 地址
	
```html
<!doctype html>
<html>
    <head>
        <meta charset="utf-8">
        <title>html表格</title>
    </head>
    <body bgcolor="#f5f5f5" background="image/pic1.png"> <!--设置背景颜色和背景图片-->
        Hello, world!
    </body>
</html>
```

### <font class="text-color-15" color="#ff9800">图片 img</font>
* 设置图片宽度和高度的时候，只设置宽度，高度会进行等比例缩放
* \<image> 的属性

| 属性名 | 描述 |
| ------ | --- |
| src | 指定图片的 URL 地址。 |
| alt | 指定图片的替代文本，在图片无法加载或者用户使用辅助设备（如屏幕阅读器）访问网页时，这个文本会被展示。 |
| title | 指定图片的标题，这个属性的值会在用户将鼠标指针移动到图片上时展示。 |
| width | 指定图片的宽度，单位可以是像素（px）或百分比（%）。 |
| height | 指定图片的高度，单位可以是像素或百分比。 |
| loading | 指定图片的加载方式，可以是 lazy、eager 或 auto。其中，lazy 表示延迟加载，eager 表示立即加载，auto 则表示让浏览器自动选择。 |
| sizes | 指定不同屏幕尺寸下的图片尺寸，格式为一个或多个以逗号分隔的字符串，例如 "(min-width: 900px) 50vw, 100vw"。这个属性可以帮助浏览器在不同设备上展示合适的图片尺寸，以提高页面性能。 |
| srcset | 指定不同分辨率下的图片 URL 地址和对应的宽度，格式为一个或多个以逗号分隔的字符串，例如 "image-320w.jpg 320w, image-480w.jpg 480w, image-800w.jpg 800w"。这个属性也可以帮助浏览器在不同设备上展示合适的图片尺寸，以提高页面性能。 |
| usemap | 指定一个图片热区的名称，该名称与一个 \<map> 元素中的 name 属性对应，用于定义图片上的链接区域。 |

### <font class="text-color-15" color="#ff9800">超链接</font>
* 超链接（Hyperlink）是在网络中链接文档、网页、图片、视频等资源的一种技术。它可以让用户通过点击一个链接跳转到另一个网页或者打开另一个文档，从而实现不同资源之间的互相连接。超链接是实现网页浏览和导航的重要技术之一，也是互联网的核心技术之一。

* 超链接的原理是通过 HTML （超文本标记语言）中的链接标签 ```<a>``` 来实现。当用户点击链接时，浏览器会读取链接标签中的 href 属性（即链接地址），然后将用户导向该地址指向的网页或文档。

* ```href``` ：hot reference 热引用，href 后面一定是一个资源地址（可以是绝对路径也可以是相对路径，可以是网络中某个资源的路径，也可以是本地资源的路径）
```html
<!doctype html>  
<html>  
<head>  
<meta charset="utf-8">  
<title>html 测试</title>  
</head>  
<body> <!--超链接、热链接-->  
<center>  
<!--文字超链接-->  
	<a href="https://www.baidu.com/" target="_self">百度</a>  
	<a href="https://tieba.baidu.com/" target="_blank">百度贴吧</a>  
	<a href="https://www.youtube.com/">油管</a>  
<!--图片超链接-->  
	<a href="https://tieba.baidu.com/f?ie=utf-	8&kw=%E6%98%8E%E6%97%A5%E6%96%B9%E8%88%9F&fr=search">  
	<img src="image/pic1.png" width="60">  
	</a>  
</center>  
</body>  
</html>
```

* taget 属性：

| 值 | 描述 |
| --- | --- |
| `_self` | 默认值。链接将在当前窗口或标签页中打开。 |
| `_blank` | 链接将在新窗口或标签页中打开。 |
| `_parent` | 链接将在父级窗口或标签页中打开。 |
| `_top` | 链接将在最顶层的窗口或标签页中打开。 |
| 自定义名称 | 链接将在名称与该名称相同的窗口或标签页中打开。这个自定义名称可以在页面中的其他地方使用，比如在JavaScript代码中。 |

* 通过超链接可以从浏览器向服务器发送请求。
	浏览器向服务器发送数据（请求 B -> S：request）
	服务器向浏览器发送数据（响应 S -> B：response）

* B/S 结构的系统每一个请求都会对应一个响应

## <font class="text-color-13" color="#ffeb3b">列表</font>
### <font class="text-color-15" color="#ff9800">无序列表</font>
```html
<!doctype html>
<html>
    <head>
        <meta charset="utf-8">
        <title>html 测试</title>
    </head>
    <body> <!--无序列表-->

        <ul type="circle">
            <li>fruit
                <ul type="disc">
                    <li>apple</li>
                    <li>banana</li>
                    <li>pear</li>
                </ul>
            </li>
            <li>toy
                <ul type="square">
                    <li>gun</li>
                    <li>doll</li>
                    <li>chess</li>
                </ul>
            </li>
            <li>car</li>
        </ul>

    </body>
</html>
```
* type 属性，用于指定列表项目的标记类型。

| 值      | 描述           |
| ------- | -------------- |
| circle  | 空心圆         |
| disc    | 实心圆（默认）|
| square  | 实心方块       |

### <font class="text-color-141" color="#ff9800">有序列表</font>
```html
<!doctype html>
<html>
<head>
  <meta charset="utf-8">
  <title>html 测试</title>
</head>
<body> <!--有序列表-->

  <ol>
    <li>fruit
      <ol type="A">
        <li>apple</li>
        <li>banana</li>
        <li>pear</li>
      </ol>
    </li>
    <li>toy</li>
    <li>tool</li>
  </ol>

</body>
</html>
```
* 对于有序列表 `<ol>`，type 属性有以下几种取值：

| 值 | 描述         |
|---|-------------|
| 1 | 阿拉伯数字（默认值） |
| A | 大写字母      |
| a | 小写字母      |
| I | 大写罗马数字  |
| i | 小写罗马数字  |

## <font class="text-color-13" color="#ffeb3b">表单</font>
* 表单 ```<form>``` 是一个用户界面元素，用于收集用户输入数据，并将其发送到服务器进行处理。表单通常包括多个输入字段 ```<input>``` ，例如文本框、单选框、多选框、下拉框等，还可以包括文件上传、验证码、提交按钮等。

* 表单的主要作用是将用户输入的数据提交到服务器端进行处理，以便服务器端能够根据这些数据进行下一步的业务处理。例如，在一个注册表单中，用户可以输入用户名、密码、电子邮件地址等个人信息，这些数据可以通过表单提交到服务器上进行验证，然后将用户信息保存到数据库中。表单还可以用于搜索、订阅、留言、评论等场景，以便用户能够提交自己的意见和反馈。

* form 标签有一个 ```action``` 属性，这个属性用来指定服务器地址
	action 属性和超链接中的 href 属性一样，都可以向服务器发送请求（request）
	
* form 的 ```method``` 属性指定用于提交表单数据的HTTP请求方法。它可以是GET或POST，也可以是PUT，DELETE，HEAD等HTTP请求方法之一（method 属性不指定或者指定 get，都会是采用 get 方式）

|方法|描述|
|---|---|
|GET|通过URL将表单数据发送到服务器。适用于数据较少，安全性要求不高的情况。采用get方法提交的时候，用户提交的信息会显示在地址栏上。|
|POST|通过HTTP请求正文将表单数据发送到服务器。适用于大量数据和安全性要求高的情况，如提交密码、个人资料等。采用post方法提交的时候，用户提交的信息不会显示在地址栏上。|

 
	
### <font class="text-color-141" color="#ff9800">跳转按钮</font>
```html
<!doctype html>
<html>
<head>
  <meta charset="utf-8">
  <title>html 测试</title>
</head>
<body> <!--表单-->
<center>
  <form action="https://www.baidu.com/" target="_blank">
    <input type="submit" value="百度">
  </form>

  <form action="https://translate.google.com.hk/?hl=zh-CN&sourceid=cnhp" target="_blank">
    <input type="submit" value="谷歌翻译">
  </form>
</center>
</body>
</html>
```
### <font class="text-color-141" color="#ff9800">提交数据</font>
* 表单提交数据的格式
	如：```action``` = ```http://localhost:8080/ao/login```
	提交数据的格式：```action?name=value&name=value&name=value...```
	
* 表单项写了 ```name``` 属性的一律会提交给服务器（没写不会提交）

* 当 ```value``` 没有写的时候，value 的默认值是空字符串""，会将空字符串提交给服务器

* 登录表单例子：
```html
<!doctype html>
<html>
<head>
  <meta charset="utf-8">
  <title>html 测试</title>
</head>
<body> <!--表单-->
<center>
  <form action="http://localhost:8080/ao/login">
    <table border="2">
      <tr>
        <td>用户名</td>
        <td><input type="text" name="username"></td>
      </tr>
      <tr>
        <td>密码</td>
        <td><input type="password" name="password"></td>
      </tr>
      <tr>
        <td>确认密码</td>
        <td><input type="password"></td>
      </tr>
      <tr>
        <td>性别</td>
        <td>
          <!--单选框，单选按钮的value必须手动赋值-->
          <input type="radio" name="gender" value="1" checked>男
          <input type="radio" name="gender" value="0">女
        </td>
      </tr>
      <tr>
        <td>编程技能</td>
        <td>    <!--多选框-->
          <input type="checkbox" name="skill" value="java">java
          <input type="checkbox" name="skill" value="mips">mips
          <input type="checkbox" name="skill" value="ocaml">ocaml
        </td>
      </tr>
      <tr>
        <td>学历</td>
        <td>
          <select name="education">   <!--下拉列表-->
            <option value="Undergraduate">专科</option>
            <option value="Graduate" selected>本科</option>
            <option value="Master">硕士</option>
            <option value="Doctor">博士</option>
          </select>
        </td>
      </tr>
      <tr>
        <td>个人经历</td>
        <td>  <!--文本域，没有value属性，填写的内容就是value-->
          <textarea rows="20" cols="60" name="experience"></textarea>
        </td>
      </tr>
      <tr>
        <td colspan="2" align="center">
          <input type="submit" value="登录">
          &nbsp;&nbsp;&nbsp;&nbsp;
          <input type="reset" value="清空">
        </td>
      </tr>
    </table>
  </form>
</center>
</body>
</html>
```
#### <font class="text-color-7" color="#03a9f4">下拉列表支持多选</font>
* ```<select>``` 下拉列表添加 multiple 属性后，按 Ctrl 可以支持多选。
* size 属性设置显示几条
* selected 属性表示默认选中
```html
<!doctype html>
<html>
    <head>
        <meta charset="utf-8">
        <title>html 测试</title>
    </head>
    <body> <!--无序列表-->

        <select multiple="multiple" size="4">
            <option>中国</option>
            <option>美国</option>
            <option>英国</option>
            <option>法国</option>
            <option>德国</option>
        </select>

    </body>
</html>
```


* input 的属性：

| 属性         | 描述                                                                                                                                 |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------ |
| type         | 指定输入字段的类型，如文本输入、密码输入、复选框等等。常见的类型有：text、password、checkbox、radio、submit、reset、file、number等。 |
| name         | 输入字段的名称，用于标识输入字段并在表单提交时将其值与其他表单数据一起发送到服务器。                                                 |
| value        | 输入字段的值。对于文本输入和密码输入，它指定默认文本；对于单选按钮和复选框，它指定选定状态；对于文件输入，它指定默认文件名。         |
| placeholder  | 输入字段的占位符文本，显示在用户输入之前，为用户提供输入提示。                                                                       |
| required     | 指定输入字段是否必填，如果为真，则表单不能提交，直到该字段被填写。                                                                   |
| readonly     | 指定输入字段是否只读，如果为真，则用户不能编辑该字段的值。                                                                           |
| disabled     | 指定输入字段是否禁用，如果为真，则用户不能与该字段交互。                                                                             |
| size         | 输入字段的大小，以字符为单位。对于文本输入和密码输入，它指定显示的字符数；对于单选按钮和复选框，它指定显示的按钮数。                 |
| maxlength    | 输入字段的最大长度，以字符为单位。                                                                                                   |
| min 和 max   | 对于类型为 number 的输入字段，指定允许输入的最小和最大值。                                                                           |
| step         | 对于类型为 number 的输入字段，指定增加或减少值时的步长。                                                                             |
| autocomplete | 指定输入字段的自动完成设置，以便浏览器可以为用户填充预测值。常见的值有：on、off、name、email、tel等等。                              |
| pattern      | 对于类型为 text 和 password 的输入字段，指定输入值的正则表达式模式，用于验证用户的输入。                                             |
| multiple     | 对于类型为 file 的输入字段，指定是否允许选择多个文件。                                                                               |
|         checked     |                 用于指示该复选框（checkbox）是否被选中。当设置 `checked` 属性为 `true` 时，复选框会默认为选中状态，否则默认为未选中状态。                                                                                                                     |

* 注：超链接会以 get 方式提交数据（固定的），如：
```html
<a href="http://localhost:8080/ao/login?username=david&password=123">按钮</a>
```
## <font class="text-color-13" color="#ffeb3b">input 相关控件</font>
### <font class="text-color-15" color="#ff9800">file 控件</font>
* HTML中的`<input type="file">`用于创建一个文件上传控件。它允许用户从本地文件系统中选择文件，并将其上传到服务器。
```html
<!doctype html>
<html>
<head>
    <meta charset="utf-8">
    <title>html 测试</title>
</head>
<body> <!--表单-->
<center>
    <input type="file">
</center>
</body>
</html>
```
* file 控件常用属性

| 属性      | 描述                                        |
|-----------|---------------------------------------------|
| accept    | 指定允许上传的文件类型，多个类型之间用逗号隔开。 |
| capture   | 指定从哪个设备捕获文件，如相机或麦克风。       |
| multiple  | 允许上传多个文件。                           |
| name      | 指定表单元素的名称，用于表单提交时识别该控件的值。|
| required  | 指定该控件是否必须填写，如果设置了此属性且用户没有选择文件，则表单无法提交。|

### <font class="text-color-15" color="#ff9800">hidden 控件</font>
* HTML中的hidden控件用于在表单中传递信息，但是这些信息不应该被用户看到或者修改。hidden控件通常被用来传递一些额外的数据，例如验证令牌或者其他服务器端需要的数据。

* 在HTML中，使用 ```<input type="hidden">``` 标签创建hidden控件。hidden控件没有任何用户界面，只有在查看HTML源代码时才能看到。

* hidden控件可以像其他表单元素一样使用name和value属性，以便在提交表单时将数据传递给服务器。例如：
```html
<form action="submit.php" method="post">
  <input type="hidden" name="token" value="abc123">
  <input type="text" name="username">
  <input type="submit" value="Submit">
</form>
```
* 在这个例子中，hidden控件传递了一个名为"token"的值为"abc123"的验证令牌。当用户提交表单时，"token"和"username"的值都会被发送到submit.php脚本进行处理。

### <font class="text-color-15" color="#ff9800">readonly 和 disabled 属性</font>
* `<input>` 标签有 `readonly` 和 `disabled` 两个属性，它们的作用如下：
	1. `readonly` 属性：使输入框只读，即用户不能编辑输入框中的内容，但是可以复制内容和选择内容。
	2. `disabled` 属性：使输入框被禁用，即输入框不能被编辑，也不能被复制或选择。

* 区别在于 `readonly` 属性仍然可以获取输入框的值，而 `disabled` 属性禁用了整个输入框，不会被提交到服务器。通常情况下，如果需要将输入框的值提交到服务器，但不希望用户进行修改，可以使用 `readonly` 属性；如果不希望将输入框的值提交到服务器，可以使用 `disabled` 属性。
```html
<form>
  <label for="readonly-input">Read-only Input:</label>
  <input type="text" id="readonly-input" name="readonly-input" readonly value="This input is read-only">
  <br>
  <label for="disabled-input">Disabled Input:</label>
  <input type="text" id="disabled-input" name="disabled-input" disabled value="This input is disabled">
</form>
```

### <font class="text-color-141" color="#ff9800">maxlength属性</font>
* `maxlength` 是 `<input>` 标签的一个属性，用于限制用户在该输入框中输入的字符数量。

* 例如，以下代码会创建一个只能输入最多 10 个字符的文本框（如果用户在文本框中输入超过 10 个字符的文本，那么多余的字符将不会被显示，也不会被提交到服务器。）：
```html
<input type="text" name="username" maxlength="10">
```
## <font class="text-color-13" color="#ffeb3b">id 属性</font>
* HTML的`id`属性是用于为元素定义唯一标识符的属性。每个`id`值必须是唯一的，并且该值可以在文档内用作超链接目标、JavaScript的变量名或CSS样式表的选择器。`id`属性通常与JavaScript一起使用，以便根据标识符获取元素并对其进行操作，也可以在CSS中用作样式选择器，以根据标识符对元素进行样式化。

* 在HTML中，`id`属性可以应用于几乎所有元素，例如`div`、`p`、`a`、`img`等。`id`属性的值必须以字母开头，只能包含字母、数字、连字符或下划线。例如，可以将一个`div`元素的`id`属性设置为“myDiv”，然后在CSS样式表中使用该选择器，或者在JavaScript中使用`document.getElementById("myDiv")`获取该元素。

* 示例
```html
<p id="my-paragraph">这是一个段落。</p>
```

### <font class="text-color-141" color="#ff9800">dom 树</font>
* DOM树（Document Object Model Tree）是指一个HTML或XML文档在内存中的表现形式，是由一组节点（node）组成的树形结构，用于表示文档的结构和内容。每个节点表示文档中的一个元素、属性或文本。DOM树的根节点是文档对象（document object），代表整个文档。

* 在DOM树中，每个元素都是一个节点，节点之间的关系体现在它们的父子关系上。每个节点都有自己的类型、名称、属性和文本内容。HTML中的节点类型包括元素节点、文本节点、注释节点等。

* 通过操作DOM树，可以对HTML或XML文档进行增删改查的操作。例如，可以通过JavaScript脚本获取文档中的某个元素节点，修改该节点的属性或文本内容，向文档中插入新节点等。通过DOM树，开发者可以很方便地对文档进行操作和控制，实现动态效果和交互功能。

## <font class="text-color-13" color="#ffeb3b">div 和 span</font>
* 最早的网页确实是使用table布局的，这是因为在早期的HTML版本中，table标签是用来布局网页的主要方式。但是随着HTML和CSS标准的不断更新，div布局逐渐成为了一种更加灵活和可扩展的布局方式。在现代网页中，div布局已经成为了最常用的布局方式之一。这是因为div元素可以自由组合和嵌套，同时可以通过CSS样式表来控制其样式和位置。相比之下，table布局相对较为笨重，不够灵活，容易导致页面结构混乱、代码冗余等问题。

* 在网页布局中，图层指的是一种分层的概念，类似于图像处理软件中的图层。每个图层都可以独立控制其样式、位置和大小等属性，从而实现网页的灵活布局和美化效果。

* 在HTML中，div和span标签可以用来创建图层。**div通常用于创建块级元素，span则用于创建行内元素**。这些标签创建的图层可以通过CSS样式表来控制其样式和位置。

* 当需要在网页中进行定位时，可以使用CSS的position属性来实现。其中，通过设置position属性为"absolute"，可以将图层定位到其父元素的相对位置上，并通过设置left和top属性来指定其左上角的x轴和y轴坐标。这种方式通常用于实现精确的布局效果。

* 因此，div和span标签可以看做是网页布局中的图层，可以用来创建盒子，实现网页的分层布局，同时也可以通过CSS的定位属性来实现定位效果。

* 简单例子：
```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
	<title>Example of div and span tags without CSS</title>
</head>
<body>
	<!-- 一个包含div和span标签的容器 -->
	<div style="background-color: lightblue; padding: 10px;">
		<div style="font-size: 24px; font-weight: bold; color: white;">这是一个标题</div>
		<p>这是一个段落，其中包含一些<span style="background-color: yellow;">突出显示</span>的内容。</p>
	</div>
</body>
</html>
```
## <font class="text-color-13" color="#ffeb3b">iframe</font>
* iframe（内联框架）是一种HTML元素，允许在当前HTML页面中嵌入另一个HTML文档。它通常用于在一个页面中显示来自其他域的内容，或者将一个长页面分为多个区域，以便可以独立地滚动其中的每个区域。

* 在HTML中，可以使用如下代码添加iframe：
```html
<iframe src="path/to/external/file.html" width="600" height="400"></iframe>
```
* 其中 `src` 属性指定了要在iframe中加载的HTML文件的路径，`width` 和 `height` 属性则分别指定了iframe的宽度和高度。

* iframe元素可以与JavaScript一起使用，以便动态地更改它的内容、样式和属性。可以使用JavaScript来获取和设置iframe的内容，例如：
```javascript
// 获取iframe元素
var myFrame = document.getElementById("myFrame");

// 获取iframe中的文档对象
var myDoc = myFrame.contentDocument || myFrame.contentWindow.document;

// 在iframe中插入一段HTML代码
myDoc.body.innerHTML = "<h1>Welcome to my website!</h1>";

// 更改iframe的CSS样式
myFrame.style.border = "2px solid red";
```
* 这里的 `myFrame` 是指代iframe元素的变量，`contentDocument` 和 `contentWindow.document` 是获取iframe中的文档对象的两种方法。


