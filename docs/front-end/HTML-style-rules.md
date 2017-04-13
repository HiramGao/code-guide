# HTML(beta)

## 写在前面的话

阅读此规范前，请保证你已经熟悉HTML基本应用，如果没有推荐下面网站

[https://developer.mozilla.org/zh-CN/docs/Web/HTML](https://developer.mozilla.org/zh-CN/docs/Web/HTML)

[http://www.w3school.com.cn/html/](http://www.w3school.com.cn/html/)

HTML5是下一代HTML，请务必了解。

**本文引用来源：**

[http://codeguide.bootcss.com/](http://codeguide.bootcss.com/)

[https://github.com/gionkunz/chartist-js/blob/develop/CODINGSTYLE.md](https://github.com/gionkunz/chartist-js/blob/develop/CODINGSTYLE.md)

## 语法

- 请用四个**空格**代替Tab(soft tabs)
- 嵌套元素应当缩进一次（四个空格）
- 对于属性定义，全部用双引号，**禁止**用单引号。推荐：`<img src="xx.png" alt="image">`
- 不要在自闭合元素的尾部添加斜线。推荐：`<br>`
- 不要省略可选的结束标签。例如：`</li>`,`</body>`


## 格式化规则

- 每一个**块状**元素，**列表**元素和**表格**元素开头要另起一行，结尾要加上一新**空白行**，并对其子孙元素进行缩进。
- 内联元素写在一行内。

``` html
<blockquote>
    <p><em>Space</em>, the final frontier.</p>
</blockquote>

<ul>
    <li>Moe</li>
    <li>Larry</li>
    <li>Curly</li>
</ul>

<table>
    <thead>
        <tr>
            <th scope="col">Income</th>
            <th scope="col">Taxes</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>$ 5.00</td>
            <td>$ 4.50</td>
        </tr>
    </tbody>
</table>

```



## 文档类型

推荐使用HTML5的文档类型声明：`<!DOCTYPE html>`

```html
<!DOCTYPE html>
<html>
    <head>
    </head>
</html>

```

## 语言属性

建议为html根指定lang属性，为文档设置正确的语言。

[HTML 语言代码参考手册](http://www.w3school.com.cn/tags/html_ref_language_codes.asp)

[微软的语言代码](https://msdn.microsoft.com/en-us/library/ms533052(v=vs.85).aspx)

```html
<html lang="en">
    <!-- ... -->
</html>
```

## IE兼容模式

请将以下标签添加，确定IE使用最新的渲染模式。

阅读这篇[文章](http://stackoverflow.com/questions/6771258/what-does-meta-http-equiv-x-ua-compatible-content-ie-edge-do)，可以解惑。

```html
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
```

## 字符编码

请将以下代码添加保证文档编码一致

```html
<head>
    <meta charset="UTF-8">
</head>
```


## 结构分离

保证结构、表现、行为三者分离，并尽量使三者之间没有太多的交互和联系。

- 不使用超过一到两张样式表（i.e. main.css, vendor.css）
- 不使用超过一到两个脚本（学会用合并脚本）
- 不使用行内样式（`<style>.no-good {}</style>`）
- 不在元素上使用 style 属性（`<hr style="border-top: 5px solid black">`）
- 不使用行内脚本（`<script>alert('no good')</script>`）
- 不使用表象元素（i.e. `<b>`, `<u>`, `<center>`, `<font>`, `<b>`）
- 不使用表象 class 名（i.e. red, left, center）

```html
<!DOCTYPE html>
<html>

<head>
    <!-- Concatinate your style sheets into a single one -->
    <link rel="stylesheet" href="main.css">
</head>

<body>
    <!-- Don't use style attributes but assign sensible classes and apply styles in the stylesheet -->
    <h1 class="title"></h1>
    <!-- Don't use presentational elements and assign sensible classes -->
    <div class="sub-title">I'm a subtitle and I'm bold!</div>
    <!-- Maybe your comments get centered in your presentation but that decision is up to the stylesheet -->
    <span class="comment">Dare you center me!</span>
    <!-- You wanted to make it red because it's important so then also name the class important and decide in the stylesheet
   what you want to do with it -->
    <div class="important">I'm important!</div>
    <!-- Put all your scripts into files and concatinate them into a single one -->
    <script async src="main.js"></script>
</body>

</html>

```

## 语义化

语义化对于代码重用、可访问性、代码效率有很大意义

推荐阅读[文章](http://www.html5jscss.com/html5-semantics-section.html)

## 内容实用

HTML 就应该只关注内容。

HTML 标签的目的，就是为了不断地展示内容信息。

- 不要引入一些特定的 HTML 结构来解决一些视觉设计问题
- 不要将 `img` 元素当做专门用来做视觉设计的元素

不推荐

```html
<span class="text-box">
  	<span class="square"></span>
  	See the square next to me?
</span>
```

```css
.text-box > .square {
  	display: inline-block;
  	width: 1rem;
  	height: 1rem;
  	background-color: red;
}
```

推荐

```html
<!-- That's clean markup! -->
<span class="text-box">
  	See the square next to me?
</span>
```

```css
.text-box:before {
  	content: "";
  	display: inline-block;
  	width: 1rem;
  	height: 1rem;
  	background-color: red;
}
```

## 属性顺序

HTML属性应当按照以下给出的顺序排列：

- `class`
- `id`, `name`
- `data-*`
- `src`, `for`, `type`, `href`, `value`
- `title`, `alt`
- `role`, `aria-*`

## 布尔（boolean）型属性

布尔型属性不用赋值

```html
<input type="text" disabled>
<input type="checkbox" value="1" checked>
<select>
  	<option value="1" selected>1</option>
</select>
```

## 多媒体回溯

对页面上的媒体而言，像图片、视频、canvas 动画等，要确保其有可替代的接入接口。图片文件我们可采用有意义的备选文本（alt），视频和音频文件我们可以为其加上说明文字或字幕。

```html
<img src="luke-skywalker.jpg" alt="Luke skywalker riding an alien horse">
```



## 减少标签的数量

编写 HTML 代码时，尽量避免多余的父元素。

```html
<!-- 不推荐 -->
<span class="avatar">
  	<img src="...">
</span>

<!-- 推荐 -->
<img class="avatar" src="...">
```

## JavaScript 生成的标签

通过 JavaScript 生成的标签让内容变得不易查找、编辑，并且降低性能。能避免时尽量避免。

强烈建议**不**使用：

``` javascript
document.write()
```

``` javascript
$("#result" ).load("ajax/test.html");
```

尤其反对`load`,加载跨站资源会有安全隐患，并且chrome的console会有一个简单的安全提示


## 引入CSS和JavaScript

根据HTML5规范，引入 CSS 和 JavaScript 文件时一般不需要指定 `type` 属性，因为 `text/css` 和 `text/javascript` 分别是它们的默认值。

```html
<link rel="stylesheet" href="code-guide.css">
<script src="code-guide.js"></script>
```

加载JavaScript脚本，现代浏览器中，推荐

```html
<html>
    <head>
      <link rel="stylesheet" href="main.css">
      <script src="main.js" async></script>
    </head>
    <body>
        <!-- body goes here -->
    </body>
</html>
```

所有浏览器中

```html
<html>
    <head>
      <link rel="stylesheet" href="main.css">
  </head>
  <body>
      <!-- body goes here -->
      <script src="main.js" async></script>
    </body>
</html>
```

---



## 版本更新

### version1.0 beta(2017-4-13)(高尚)

- 初始化文档，添加主要的内容

## 本页面维护者

- 高尚