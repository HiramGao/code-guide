# CSS（BETA）

## 写在前面的话

阅读此规范前，请保证你已经熟悉CSS基本应用，如果没有推荐下面网站

[https://developer.mozilla.org/zh-CN/docs/Web/CSS](https://developer.mozilla.org/zh-CN/docs/Web/CSS)

[http://www.w3school.com.cn/css/](http://www.w3school.com.cn/css/)

CSS3 是最新的 CSS 标准。请务必了解。

**本文应用来源：**

[http://codeguide.bootcss.com/](http://codeguide.bootcss.com/)

[https://github.com/gionkunz/chartist-js/blob/develop/CODINGSTYLE.md](https://github.com/gionkunz/chartist-js/blob/develop/CODINGSTYLE.md)

[http://www.cnblogs.com/y-lin/p/5753302.html](http://www.cnblogs.com/y-lin/p/5753302.html)

## 语法

- 文件编码使用无BOM得UTF-8
- 请用四个**空格**代替Tab
- 为了代码的易读性，在每个声明块的左花括号前添加一个空格。
- 声明块的右花括号应当单独成行。
- 每条声明语句的 `:` 后应该插入一个空格。
- 为了获得更准确的错误报告，每条声明都应该独占一行。
- 所有声明语句都应当以分号结尾。
- 规则之间始终有一个空行（双换行符）分隔。

```css
/* Bad CSS */
.selector, .selector-secondary, .selector[type=text] {
  padding:15px;
  margin:0px 0px 15px;
  background-color:rgba(0, 0, 0, 0.5);
  font-family: 'Microsoft YaHei', sans-serif;
  box-shadow:0px 1px 2px #CCC,inset 0 1px 0 #FFFFFF
}

/* Good CSS */
.selector,
.selector-secondary,
.selector[type="text"] {
  padding: 15px;
  margin-bottom: 15px;
  background-color: rgba(0,0,0,.5);
  font-family: "Microsoft YaHei", sans-serif;
  box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
}
```

## 选择器

为选择器分组时，将单独的选择器单独放一行。

```css
.selector,
.selector-secondary,
.selector[type="text"] {
	...
}
```

`>`,`+`,`~`选择器两边保留一个空格。

``` css
.main > nav{
  ...
}
```

为选择器中的属性添加双引号，例如，`input[type="text"]`。

## 合理的避免使用ID

一般情况下ID不应该被应用于样式。应该始终考虑使用class，而不是id，除非只使用一次。

```css
//不推荐
#content .title {
  font-size: 2em;
}
//推荐
.content .title {
  font-size: 2em;
}
```

## 避免标签名

不要使用标签选择器。

**不推荐**

```
div.content > header.content-header > h2.title {  font-size: 2em;}
```

**推荐**

```
.content > .content-header > .title {  font-size: 2em;}
```

## 值和单位

- 文本内容必须用双引号包围。
- 对于属性值或颜色参数，省略小于 1 的小数前面的 0 （例如，`.5` 代替 `0.5`；`-.5px` 代替 `-0.5px`）。
- `url()` 函数中的路径不加引号。
- 十六进制值应该全部小写，例如，`#fff`。
- 尽量使用简写形式的十六进制值，例如，用 `#fff` 代替 `#ffffff`。
- 避免为 0 值指定单位，例如，用 `margin: 0;` 代替 `margin: 0px;`。
- 不要在 `rgb()`、`rgba()`、`hsl()`、`hsla()` 或 `rect()` 值的内部的逗号后面插入空格。
- 颜色值不允许使用命名色值。不推荐`color: lightgreen;`
- 对于以逗号分隔的属性值，每个逗号后面都应该插入一个空格（例如，`box-shadow`）。

## 文本编排

### 字体族

`font-family` 属性中的字体族名称应使用字体的英文 `Family Name`，其中如有空格，须放置在引号中。

常见字体名称如下：

| 字体        | 操作系统    | Family Name         |
| --------- | ------- | ------------------- |
| 宋体 (中易宋体) | Windows | SimSun              |
| 黑体 (中易黑体) | Windows | SimHei              |
| 微软雅黑      | Windows | Microsoft YaHei     |
| 微软正黑      | Windows | Microsoft JhengHei  |
| 华文黑体      | Mac/iOS | STHeiti             |
| 冬青黑体      | Mac/iOS | Hiragino Sans GB    |
| 文泉驿正黑     | Linux   | WenQuanYi Zen Hei   |
| 文泉驿微米黑    | Linux   | WenQuanYi Micro Hei |

 `font-family` 按「西文字体在前、中文字体在后」、「效果佳 (质量高/更能满足需求) 的字体在前、效果一般的字体在后」的顺序编写，最后必须指定一个通用字体族( `serif` / `sans-serif` )

``` css
h1 {
    font-family: "Helvetica Neue", Arial, "Hiragino Sans GB", "WenQuanYi Micro Hei", "Microsoft YaHei", sans-serif;
}
```

`font-family` 不区分大小写，但在同一个项目中，同样的 `Family Name` 大小写必须统一。下列写法是**不**允许的。

``` css
/*错误*/
body {
    font-family: arial, sans-serif;
}

h1 {
    font-family: Arial, "Microsoft YaHei", sans-serif;
}
/*正确*/
body {
    font-family: Arial, sans-serif;
}

h1 {
    font-family: Arial, "Microsoft YaHei", sans-serif;
}
```

### 字体

需要在 Windows 平台显示的中文内容，其字号应不小于 12px。由于 Windows 的字体渲染机制，小于 12px 的文字显示效果极差、难以辨认。

## 变换与动画

使用 `transition` 时应具体指定 `transition-property`不要使用`all`。

``` css
/* good */
.box {
	transition: color 1s, border-color 1s;
}

/* bad */
.box {
    transition: all 1s;
}
```

尽可能在浏览器能高效实现的属性上添加过渡和动画。

例如：可以使用`translate`来代替`left`作为动画属性。

``` css
/* good */
.box {
    transition: transform 1s;
}
.box:hover {
    transform: translate(20px); 
}

/* bad */
.box {
    left: 0;
    transition: left 1s;
}
.box:hover {
    left: 20px; 
}
```



## 声明顺序

相关的属性声明应当归为一组，并按照下面的顺序排列：

1. Positioning
2. Box model
3. Typographic
4. Visual

由于定位（positioning）可以从正常的文档流中移除元素，并且还能覆盖盒模型（box model）相关的样式，因此排在首位。盒模型排在第二位，因为它决定了组件的尺寸和位置。

其他属性只是影响组件的*内部（inside）*或者是不影响前两组属性，因此排在后面。

完整的属性列表及其排列顺序请参考 [Recess](http://twitter.github.com/recess)。

```css
.declaration-order {
  /* Positioning */
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 100;

  /* Box-model */
  display: block;
  float: right;
  width: 100px;
  height: 100px;

  /* Typography */
  font: normal 13px "Helvetica Neue", sans-serif;
  line-height: 1.5;
  color: #333;
  text-align: center;

  /* Visual */
  background-color: #f5f5f5;
  border: 1px solid #e5e5e5;
  border-radius: 3px;

  /* Misc */
  opacity: 1;
}
```

## 不要使用`@import`

不要使用`@import`!!不要使用`@import`!!不要使用`@import`

## 媒体查询（Media query）

将媒体查询放在尽可能相关规则的附近。不要将他们打包放在一个单一样式文件中或者放在文档底部。如果你把他们分开了，将来只会被大家遗忘。下面给出一个典型的实例。

```css
.element { ... }
.element-avatar { ... }
.element-selected { ... }

@media (min-width: 480px) {
  .element { ...}
  .element-avatar { ... }
  .element-selected { ... }
}
```

## 带前缀的属性

当使用特定厂商的带有前缀的属性时，通过缩进的方式，让每个属性的值在垂直方向对齐，这样便于多行编辑。

```css
.selector {
  -webkit-box-shadow: 0 1px 2px rgba(0,0,0,.15);
          box-shadow: 0 1px 2px rgba(0,0,0,.15);
}
```

## 单行规则声明

对于**只包含一条声明**的样式，为了易读性和便于快速编辑，建议将语句放在同一行。对于带有多条声明的样式，还是应当将声明分为多行。

```css
/* Single declarations on one line */
.span1 { width: 60px; }
.span2 { width: 140px; }
.span3 { width: 220px; }

/* Multiple declarations, one per line */
.sprite {
  display: inline-block;
  width: 16px;
  height: 15px;
  background-image: url(../img/sprite.png);
}
.icon           { background-position: 0 0; }
.icon-home      { background-position: 0 -20px; }
.icon-account   { background-position: 0 -40px; }
```

## 缩写属性

CSS提供了各种缩写属性（如 font 字体）应该尽可能使用，但是例如`border`,`margin`,`padding`缩写会同时设置多个值，容易覆盖不需要覆盖的字。当仅仅需要设置一个值，推荐**不**缩写。

```css
//不推荐
border-top-style: none;
font-family: palatino, georgia, serif;
font-size: 100%;
line-height: 1.6;
padding-bottom: 2em;
padding-left: 1em;
padding-right: 1em;
padding-top: 0;
margin-top: 0;
//推荐
border-top: 0;
font: 100%/1.6 palatino, georgia, serif;
padding: 0 1em 2em;
//例外
margin-top: 0;
```

## 嵌套

避免不必要的嵌套。这是因为虽然你可以使用嵌套，但是并不意味着应该使用嵌套。只有在必须将样式限制在父元素内（也就是后代选择器），并且存在多个需要嵌套的元素时才使用嵌套。

## 注释

代码是由人编写并维护的。请确保你的代码能够自描述、注释良好并且易于他人理解。好的代码注释能够传达上下文关系和代码目的。不要简单地重申组件或 class 名称。对于较长的注释，务必书写完整的句子；对于一般性注解，可以书写简洁的短语。

```css
/* Bad example */
/* Modal header */
.modal-header {
  ...
}

/* Good example */
/* Wrapping element for .modal-title and .modal-close */
.modal-header {
  ...
}
```

### 普通注释

``` css
/* 普通注释 */
```

### 区块注释

``` css
/**
 * 模块：m-detail
 * author: xxx
 * edit:   2016.5.02
 */
```



## CSS命名规范

- CSS命名中只能出现小写字符和破折号（不是下划线，也不是驼峰命名法）。破折号应当用于相关 class 的命名（类似于命名空间）（例如，`.btn` 和 `.btn-danger`）。
- 避免过度任意的简写。`.btn` 代表 *button*，但是 `.s` 不能表达任何意思。
- CSS命名应当尽可能短，并且意义明确。
- 基于最近的父 class 或基本（base） class 作为新 class 的前缀。

```css
/* Bad example */
.t { ... }
.red { ... }
.header { ... }

/* Good example */
.tweet { ... }
.important { ... }
.tweet-header { ... }
```

**命名前缀**

| 前缀   | 说明                    | 示例          |
| ---- | --------------------- | ----------- |
| g-   | 全局通用样式命名              | g-mod       |
| m-   | 模块命名方式                | m-detail    |
| ui-  | 组件命名方式                | ui-selector |
| j-   | 所有用于纯交互的命名，不涉及任何样式规则。 | j-switch    |

不允许出现以类似：`.info`， `.current`， `.news` 开头的选择器，比如：`.info{} `，推荐这样：`.m-xxx .info{}`

**命名单词**

- 不以表现来命名，而是根据内容来命名。比如：left, right, center, red, black这种以表现来定命名，不允许出现；
- 推荐使用功能和内容相关词汇的命名，如:

```
套系:package
相册:photo-album
作品:works
攻略:raiders
普通用户:normal-user 
达人:talent-user
摄影师:photographer
用户昵称:user-alias
头像:head
地区:area
关注数:follow
粉丝数:followers
互相注意:attention
标签:label
发表时间:publish-date,publish-time
标题:title
信息:info
内容:content
关于我:about
简介内容:intro-content
评论:review 
服务:service
封面:cover
流行:popular
收藏:collect
查看:view
预约:reservation
促销:sale-promotion
待补充
```

## 选择器

- 对于通用元素使用 class ，这样利于渲染性能的优化。
- 对于经常出现的组件，避免使用属性选择器（例如，`[class^="..."]`）。浏览器的性能会受到这些因素的影响。
- 选择器要尽可能短，并且尽量限制组成选择器的元素个数，建议不要超过 3 。
- **只有**在必要的时候才将 class 限制在最近的父元素内（也就是后代选择器）（例如，不使用带前缀的 class 时 -- 前缀类似于命名空间）。

```css
/* Bad example */
span { ... }
.page-container #stream .stream-item .tweet .tweet-header .username { ... }
.avatar { ... }

/* Good example */
.avatar { ... }
.tweet-header .username { ... }
.tweet .avatar { ... }
```

## 代码组织

- 以组件为单位组织代码段。
- 制定一致的注释规范。
- 使用一致的空白符将代码分隔成块，这样利于扫描较大的文档。
- 如果使用了多个 CSS 文件，将其按照组件而非页面的形式分拆，因为页面会被重组，而组件只会被移动。

```css
/*
 * Component section heading
 */

.element { ... }


/*
 * Component section heading
 *
 * Sometimes you need to include optional context for the entire component. Do that up here if it's important enough.
 */

.element { ... }

/* Contextual sub-component or modifer */
.element-heading { ... }
```

------

## 推荐BEM

来源：[http://www.w3cplus.com/css/mindbemding-getting-your-head-round-bem-syntax.html](http://www.w3cplus.com/css/mindbemding-getting-your-head-round-bem-syntax.html)

块（block）、元素（element）、修饰符（modifier）。

命名约定的模式如下：

``` css
.block{}
.block__element{}
.block--modifier{}	
```

- `.block` 代表了更高级别的抽象或组件。
- `.block__element` 代表`.block`的后代，用于形成一个完整的`.block`的整体。
- `.block—modifier`代表`.block`的不同状态或不同版本。

BEM的关键是光凭名字就可以告诉其他开发者某个标记是用来干什么的。通过浏览HTML代码中的class属性，你就能够明白模块之间是如何关联的著作权归作者所有。

``` css
/*BEM*/
.person{}
.person__hand{}
.person--female{}
.person--female__hand{}
.person__hand--left{}	

/*常规*/
.person{}
.hand{}
.female{}
.female-hand{}
.left-hand{}
```

常规CSS关系脱节。

举个html的例子

``` html
<!-- 常规 -->
<form class="site-search  full">
  <input type="text" class="field">
  <input type="Submit" value ="Search" class="button">
</form>	
<!-- BEM -->
<form class="site-search  site-search--full">
  <input type="text" class="site-search__field">
  <input type="Submit" value ="Search" class="site-search__button">
</form>
```

**什么时候使用BEM**

使用BEM的诀窍是，你要知道什么时候哪些东西是应该写成BEM格式的。因为某些东西确实是位于一个块的内部，但这并不意味它就是BEM中所说的元素。例如

``` html
<div class="content">
  <h1 class="content__headline">Lorem ipsum dolor...</h1>
</div>
```

在这个例子里，我们也许仅仅只需要另一个class，可以叫它.headline；它的样式取决于它是如何被层叠的，因为它在.content的内部；或者它只是恰巧在.content的内部。如果它是后者（即恰巧在.content的内部，而不总是在）我们就不需要使用BEM。

一切都有可能潜在地用到BEM。

BEM最难的部分之一是明确作用域是从哪开始和到哪结束的，以及什么时候使用（不使用）它。随着接触的多了，有了经验积累，你慢慢就会知道怎么用，这些问题也不再是问题。

## 版本更新

### version1.0 beta(2017-4-15)(高尚)

- 初始化文档，添加主要的内容

## 本页面维护者

- 高尚