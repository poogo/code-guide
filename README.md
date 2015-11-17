# 拉勾·一拍 前端代码规范

[HTML](#html)

* [语法](#html_syntax)
* [HTML5 doctype](#html_doctype)
* [lang属性](#html_lang)
* [meta标签](#html_meta)
* [引入css](#html_importCSS)
* [引入js](#html_importJS)
* [属性顺序](#html_attrOrder)
* [boolean属性](#html_booleanAttr)
* [减少标签数量](#html_reduceTagsCount)
* [正确嵌套标签](#html_nestTagCorrectly)
* [语义化](#html_semantic)
* [图片](#html_img)
* [表单](#html_formItem)
* [JS生成标签](#html_jsCreatsTag)

[CSS/LESS](#cl)

* [缩进](#cl_indent)
* [分号](#cl_semicolon)
* [空格](#cl_blankSpace)
* [空行](#cl_blankLine)
* [换行](#cl_newline)
* [引号](#cl_quotes)
* [命名](#cl_named)
* [属性声明顺序](#cl_attrOrder)
* [带前缀的属性](#cl_prefixAttr)
* [颜色](#cl_color)
* [属性简写](#cl_shortAttr)
* [媒体查询](#cl_media)
* [LESS相关](#cl_less)
* [其他](#cl_other)

[Javascript](#js)

* [缩进](#js_indent)
* [分号](#js_semicolon)
* [空格](#js_blankSpace)
* [空行](#js_blankLine)
* [换行](#js_newline)
* [引号](#js_quotes)
* [命名](#js_named)
* [单行注释](#js_singleLineComment)
* [多行注释](#js_multiLineComment)
* [文档注释](#js_documentComment)
* [函数](#js_function)
* [数组、对象](#js_arrObj)
* [括号](#js_bracket)
* [null](#js_null)
* [undefined](#js_undefined)
* [其他](#js_other)


<a name="html">
## HTML
</a>

<a name="html_syntax">
### 语法
</a>

* 缩进使用2个空格
* 所有嵌套关系均使用缩进
* 标签名必须全为小写
* 在HTML页面中出现的所有属性，均使用双引号，不可使用单引号
* 属性名全为小写，可用中划线做为分隔符
* 同一个标签内，属性名不可重复
* 自定义属性均以"data-"开头
* 自闭合标签需要加上闭合
* id属性在文档内不可重复
* id使用驼峰命名规则
* class使用中划线进行连接

```html
<!DOCTYPE html>
<html>
  <head>
    <title>demo title</title>
  </head>
  <body>
    <header id="demoHeader"></header>
    <img src="..." alt="..." title="..." />
    <h1 class="hello-world">Hello, world</h1>
    <br />
  </body>
</html>
```

<a name="html_doctype">
### HTML5 DOCTYPE
</a>
在所有页面的开头均使用 HTML文档模式：<!DOCTYPE html>，使页面在每种浏览器中均得到一致的渲染效果<br />
doctype 均使用大写

```html
<!DOCTYPE  html>
<html>
  ...
</html>
```

<a name="html_lang">
### lang属性
</a>
根据HTML5规范：
>应在html标签上加上lang属性。这会给语音工具和翻译工具以帮助，告诉它们应当怎么去发音和翻译。

在[sitepoint](http://www.sitepoint.com/web-foundations/iso-2-letter-language-codes/)上可以查到语言列表；<br />
但[sitepoint](http://www.sitepoint.com/web-foundations/iso-2-letter-language-codes/)只是给出了语言的大类，例如中文只给出了zh，但是没有区分香港，台湾，大陆。而微软给出了一份更加[详细的语言列表](https://msdn.microsoft.com/en-us/library/ms533052(v=vs.85).aspx)，其中细分了zh-cn， zh-hk，zh-tw。

```html
<html lang="zh-CN">
	...
</html>
```

<a name="html_charset">
### 字符编码
</a>
通过明确声明字符编码，能够确保浏览器快速并容易的判断页面内容的渲染方式。这样做的好处是，可以避免在 HTML 中使用字符实体标记（character entity），从而全部与文档编码一致（一般采用 UTF-8 编码）。

```html
<head>
	<meta charset="UTF-8">
</head>
```

<a name="html_meta">
### meta标签
</a>

* IE兼容模式<br />
	IE 支持通过特定的```<meta>```标签来确定绘制当前页面所应该采用的 IE 版本。除非有强烈的特殊需求，否则最好是设置为 edge mode，从而通知 IE 采用其所支持的最新的模式。如果你想要了解更多，请点击[这里](http://stackoverflow.com/questions/6771258/whats-the-difference-if-meta-http-equiv-x-ua-compatible-content-ie-edge-e)；不同doctype在不同浏览器下会触发不同的渲染模式（[这篇文章](https://hsivonen.fi/doctype/)总结的很到位）。
* Google Chrome Frame<br />
	Google Chrome Frame(谷歌内嵌浏览器框架GCF)插件可以使IE浏览器使用Google Chrome浏览器内核来渲染页面，并且支持IE6、7、8等多个版本的IE浏览器，为了能取得更好的渲染效果，请为content属性添加chrome=1的值，来让安装了此插件的IE浏览器优先选择webkit内核渲染页面。
* 优先使用webkit内核渲染页面<br />
  国内的浏览器基本都是双核浏览器，极速模式通过webkit内核渲染页面，兼容模式通过ie的Trident内核渲染页面，360浏览器实现了通过在页面添加```<meta name="renderer" content="webkit">```的[私有方案](http://se.360.cn/v6/help/meta.html)来让浏览器优先选择webkit内核渲染页面，为了能让页面获得更好的渲染效果，请添加该标签。

```html
<!DOCTYPE html>
<html>
<head>
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
  <meta name="renderer" content="webkit">
</head>
</html
```



