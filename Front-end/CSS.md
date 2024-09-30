# <center>CSS</center>

## <font class="text-color-13" color="#ffeb3b">概述</font>
* CSS是Cascading Style Sheets（层叠样式表）的缩写，它是一种用于网页排版和样式设计的标记语言。通过CSS，开发者可以为HTML和XML等文档添加样式、布局和效果，使网页内容更加美观、易于阅读和交互。CSS可以控制文本样式、字体大小、颜色、间距、背景图像、布局等方面，而不需要改变HTML代码结构。同时，CSS具有层叠性、继承性和优先级等特点，可以实现灵活而精确的样式控制。

* <a href="https://www.runoob.com/css/css-tutorial.html">CSS菜鸟教程</a>

### <font class="text-color-15" color="#ff9800">CSS 与 HTML 的关系</font>
* CSS与HTML是紧密相关的两种技术。HTML用于创建网页结构和内容，而CSS用于控制网页的样式和布局。

* 具体来说，HTML定义了网页的内容、结构和语义，它使用标签和属性来标记不同的元素和文本。而CSS定义了网页的样式，包括颜色、字体、大小、位置、布局等方面。使用CSS，开发者可以将样式与HTML文档分离，通过样式表将网页的外观和风格统一起来。

* 通过将HTML和CSS相结合，开发者可以创建出功能丰富、易于维护和美观的网页。HTML和CSS的配合使用也为Web开发带来了更大的灵活性和可扩展性。

## <font class="text-color-13" color="#ffeb3b">内联定义</font>
* CSS的内联定义是指将样式直接写在HTML元素的style属性中，而不是将样式放在外部的样式表文件或在HTML文档中使用 `<style>` 标签定义样式。

* 语法格式：
```html
<element style="property1: value1; property2: value2; ...">
```
* 其中，`element` 代表要应用样式的HTML元素，`style` 是元素的style属性，属性值是由分号分隔的一组样式属性和值，每个样式属性和值都由冒号分隔。

* 例如，下面的代码将文本颜色设置为红色，字体大小设置为16像素：
```html
<p style="color: red; font-size: 16px;">这是一个段落</p>
```
* 使用内联样式可以为单个元素定义样式，方便、快捷，不需要额外的CSS文件，但是会增加HTML代码的复杂度和维护难度。此外，内联样式也会影响到网页的性能，因为它们无法被浏览器缓存，每次加载页面时都会重新解析。因此，通常建议使用外部样式表来定义CSS样式，可以提高网页的性能和可维护性。

* <a href=https://www.runoob.com/cssref/css-reference.html>CSS所有属性</a>

* 内联定义画div块
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>内联定义方式</title>

</head>
<body>

    <!--布局样式（none表示隐藏，block表示显示）-->
    <div style="width: 300px; height:300px; background-color:coral; display:block;
border-color: aqua;border-width: 5px;border-style: solid">
    </div>
    <br><br><br>
    <div style="width: 300px; height:300px; background-color:darkseagreen; display:block;
border: medium dashed green;">
    </div>

</body>
</html>
```

## <font class="text-color-121" color="#ffeb3b">内部样式块对象</font>
* CSS的内部样式块是一段嵌入在HTML文档中的样式定义，可以通过 `<style>` 标签在文档头部或元素的 `style` 属性中定义。内部样式块适用于需要为文档中的特定元素或元素组设置样式的情况。

* 内部样式块的优点是可以让开发者在同一个HTML文档中定义多个样式，不需要创建额外的CSS文件。同时，它也比内联样式更易于维护，因为可以集中定义一个元素或元素组的样式。但是，它也存在一些缺点，例如样式定义会与HTML文档的结构混杂在一起，导致代码可读性降低。

* 语法格式：（selector 代表网页中的元素）
```html
<!DOCTYPE html>
<html>
<head>
	<title>示例</title>
	<style>
		selector {
			property1: value1;
			property2: value2;
			...
		}
	</style>
</head>
<body>
	<!-- HTML元素 -->
</body>
</html>
```

* 例子：
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>css 测试</title>
    <style>
        h1, h2, h3 {
            color: blue;
        }

        p, span {
            font-size: 16px;
        }
    </style>
</head>
<body>
    <h1>一级标题</h1>
    <h2>二级标题</h2>
    <h3>三级标题</h3>
    <p>这是一个段落</p>
</body>
</html>
```
### <font class="text-color-15" color="#ff9800">选择器类型</font>
1. 标签选择器： `标签{...}`
2. id 选择器： `#id{...}`
3. 类选择器：`.类名{...}`
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>css 测试</title>
    <style>
        /*
        id 选择器
         */
        #message1{
            color:firebrick;
            font-size: 20px;
        }
        /*
        标签选择器
         */
        div{
            background-color: chartreuse;
            width:50px;
            height:60px;
            border-color: black;
            border-bottom-style: dotted;
            border-size: 3px;
        }
        /*
        类选择器
         */
        .myclass1{
            border: 2px solid red;
            width:300px;
        }
    </style>
</head>
<body>
    <span id="message1">今天天气真不错</span>

    <br><br><br><br>

    <div></div>
    <div></div>
    <div></div>

    <br><br><br><br>
    <input type="text" class="myclass1">
    <br>
    <select class="myclass1">
        <option>apple</option>
        <option>pear</option>
        <option>banana</option>
    </select>
</body>
</html>
```


## <font class="text-color-121" color="#ffeb3b">链入外部样式表文件</font>
* CSS的链入外部样式表文件是通过使用 `<link>` 标签来实现的。外部样式表是一种独立的CSS文件，可以被多个HTML页面共用。样式定义和HTML文档分离，可以使得页面的样式和内容更加清晰明了，并且可以提高代码的重用性和维护性。（最常用）

* `<link>` 标签应该放在HTML文档的 `<head>` 标签中，并指定外部样式表文件的路径。例如，下面的代码将一个名为 `styles.css` 的外部样式表文件链接到HTML文档中：
```html
<!DOCTYPE html>
<html>
<head>
	<title>示例</title>
	<link rel="stylesheet" type="text/css" href="styles.css">
</head>
<body>
	<!-- HTML元素 -->
</body>
</html>
```
* 其中，`rel` 属性指定了链接类型为样式表（`stylesheet`），`type` 属性指定了文件的MIME类型为CSS文件（`text/css`），`href` 属性指定了样式表文件的路径。样式表文件的路径可以是相对路径或绝对路径，根据实际情况来选择。

* 在外部样式表文件中，可以像内部样式块一样定义多个选择器和多个样式属性。例如，`styles.css` 文件中的代码如下：
```css
h1 {
	color: blue;
}

p {
	font-size: 16px;
}
```
 
 ## <font class="text-color-13" color="#ffeb3b">常用 CSS 属性</font>
 ### <font class="text-color-15" color="#ff9800">cursor</font>
* span 的 cursor 属性可以改变鼠标移动到它上面的光标显示
* <a href=https://www.runoob.com/cssref/pr-class-cursor.html>具体 cursor 属性设置</a>
* 例如
```html
<!DOCTYPE html>
<html>
  <head>
    <title>示例</title>
    <style>
      .clickable {
        cursor: pointer;
      }
    </style>
  </head>
  <body>
    <p>这是一个普通的段落，其中包含了一个<span class="clickable">可点击的元素</span>。</p>
  </body>
</html>
```

### <font class="text-color-15" color="#ff9800">position</font>
* `position` 属性是 CSS 中非常常用的属性，用于指定 HTML 元素的定位方式。
* <a href=https://www.runoob.com/cssref/pr-class-position.html>position具体属性值</a>
* 例子
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>css test</title>
    <style type="text/css">
        .container1{
            background-color: royalblue;
            border: 1px black solid;
            width: 300px;
            height: 300px;
            position: absolute; /*绝对定位*/
            left: 200px; /*把块的左边缘设置在其包含元素左边缘向右200像素的位置*/
            top: 200px; /*把块的上边缘设置在其包含元素上边缘之下5像素高的位置*/
        }
    </style>
</head>
<body>
    <div class="container1"></div>
</body>
</html>
```
