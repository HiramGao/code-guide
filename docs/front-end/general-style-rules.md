# 一般规范

## 文件/资源命名

- 使用`-`分隔文件名，例如`big-black-background.jpg`
- 文件字母必须全部为小写
- 为特定文件增加前后缀或特定的扩展名（比如 .min.js, .min.css），抑或一串前缀（比如 `3fa89b.main.min.css`）。这种情况下，建议使用点分隔符来区分。

## 协议

不要指定协议部分

```html
不推荐
<script src="http://cdn.com/foundation.min.js"></script>
推荐
<script src="//cdn.com/foundation.min.js"></script>
```

## 编辑器规范

请将编辑器设置成以下配置：

- 用**两个空格**代替制表符（soft-tab即为空格代表空格）
- 设置文件编码为**UTF-8**
- 在文件结尾处添加**一个空白行**

## 注释

编写自解释代码只是一个**传说**，请适当编写注释。

不要写你的代码都干了些什么，而要写你的代码为什么要这么写，背后的考量是什么。当然也可以加入所思考问题或是解决方案的链接地址。

## 代码检查

JavaScript，建议使用 [JSLint](http://www.jslint.com/) 或 [JSHint](http://www.jshint.com/)。