# HTML代码编码风格指南

## 协议

省略嵌入资源的协议：对于图像、媒体文件、样式表、脚本文件等，除非该资源请求无法对http：和https:同时可用，否则省略协议部分。URL地址变成相对地址，也节省了文件字节数。

	<!-- 不推荐 -->
	<script src="http://www.google.com/js/gweb/analytics/autotrack.js"></script>
	<!-- 推荐 -->
	<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
	/* 不推荐 */
	.example {
	  background: url(http://www.google.com/images/example);
	}
	/* 推荐 */
	.example {
	  background: url(//www.google.com/images/example);
	}
## 缩进

使用2个空格,而不使用tab或者混用空格+tab作为缩进

	<ul>
	  <li>Fantastic
	  <li>Great
	</ul>
	.example {
	  color: blue;
	}

## 大小写

所有代码只使用小写：适用于元素名，选择器，（样式和标签的）属性及属性值（text/CDATA例外，作为内容时例外）

	<!-- 不推荐 -->
	<A HREF="/">Home</A>
	<!-- 推荐 -->
	<img src="google.png" alt="Google">
## 编码
### UTF-8
使用UTF-8（非BOM），在HTML中指定UTF-8编码。

	<meta charset="utf-8">

### GB2312
文档保存为ANSI编码，在HTML中指定GB2312编码。
	<meta charset="gb2312">

## 注释

根据需要，在可能的情况下给代码做注释：这块实现了什么功能，它的目的是什么，为什么这种方案更好？（注释代码不是强制要求，视乎项目性质和复杂程度）

## 文档类型

使用HTML5，首选`<!DOCTYPE html>`：推荐使用HTML（text/html）而非XHTML（application/xhtml+xml），原因一是浏览器基础支持缺失，二是优化空间比HTML更小

## HTML合法性

使用合法的HTML标签，除非你更在意那一点点节省的文件体积；使用工具如W3C HTML验证；使用合法的HTML标签是可被衡量的规范，有助于编码者学习的技术要求和限制，并保证代码质量。

	<!-- 不推荐 -->
	<title>Test</title>
	<article>This is only a test.
	<!-- 推荐 -->
	<!DOCTYPE html>
	<meta charset="utf-8">
	<title>Test</title>
	<article>This is only a test.</article>
## 语义化

符合本义地使用元素（标签），比如在头部区域使用heading元素，使用p元素表示段落，使用a元素表示链接等；语义化地使用HTML有助于网页的可访问性，复用性，和优化代码效率。

	<!-- 不推荐d -->
	<div>All recommendations</div>
	<!-- 推荐 -->
	<a href="recommendations/">All recommendations</a>
	
## 多媒体备选内容

为多媒体元素（图像、视频音频、cavas创建的动态对象）提供替代内容，对图像来说可以在alt中加上有意义的文本内容，对视频音频来说可以加上描述性的元素。提供多媒体的替代内容在网页可访问性上是重要的：一个盲人用户可以通过alt线索得知关于这个图像的信息，或者其他用户在无法理解图像内容的时候有用。对于不是在css中引用的非内容图就不要使用alt描述了。

	<!-- 不推荐 -->
	<img src="spreadsheet.png">
	<!-- 推荐 -->
	<img src="spreadsheet.png" alt="Spreadsheet screenshot.">
## 行为、呈现与结构分离

保持结构（标记）、呈现（样式）、和行为（脚本）严格分离，并最小化三者的相互作用。HTML文件中只包含结构代码，样式语句放在样式表文件中，行为语句放在脚本文件中，在HTML文档中去引用样式表和脚本文件。分离的重要性在于，如果你要在HTML文档中更改样式和行为，你付出的成本会更高。

	<!-- 不推荐 -->
	<title>HTML sucks</title>
	<link rel="stylesheet" href="base.css" media="screen">
	<link rel="stylesheet" href="grid.css" media="screen">
	<link rel="stylesheet" href="print.css" media="print">
	<h1 style="font-size: 1em;">HTML sucks</h1>
	<p>I’ve read about this on a few sites but now I’m sure:
	  <u>HTML is stupid!!1</u>
	<center>I can’t believe there’s no way to control the styling of
	  my website without doing everything all over again!</center>

	<!-- 推荐 -->
	<title>My first CSS-only redesign</title>
	<link rel="stylesheet" href="default.css">
	<h1>My first CSS-only redesign</h1>
	<p>I’ve read about this on a few sites but today I’m actually
	  doing it: separating concerns and avoiding anything in the HTML of
	  my website that is presentational.
	<p>It’s awesome!
## 省略可选的标签

为了代码文件的可读性和体积的优化，可以考虑省略可选的标签。HTML5 specification定义了哪些标签是可以被省略的。（由于网站开发人员的技术背景差异，应用这种方法需要一段足够的缓冲期；基于一致性和简单的原则，最好是省略所有的可选标签，而不只是一两个。

	<!-- 不推荐 -->
	<!DOCTYPE html>
	<html>
	  <head>
	    <title>Spending money, spending bytes</title>
	  </head>
	  <body>
	    <p>Sic.</p>
	  </body>
	</html>

	<!-- 推荐 -->
	<!DOCTYPE html>
	<title>Saving money, saving bytes</title>
	<p>Qed.

## 引用类型

省略样式表和脚本文件的引用类型，（除非你引用的不是CSS或者JavaScript）。HTML5默认使用text/css和text/javascript，因此声明引用类型不是必要的，这对于较老的浏览器也适用。

	<!-- 不推荐 -->
	<link rel="stylesheet" href="//www.google.com/css/maia.css" type="text/css">
	<!-- 推荐 -->
	<link rel="stylesheet" href="//www.google.com/css/maia.css">
	<!-- 不推荐 -->
	<script src="//www.google.com/js/gweb/analytics/autotrack.js" type="text/javascript"></script>
	<!-- 推荐 -->
	<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>

## 通用格式化

为下一个block元素、list元素或者table元素使用另起一行，并缩进此类的每个子元素。如果因为list元素中的空格占位问题而把list元素放置在同一行中也是可以接受的，对此语法检查器应该警告而不是提示错误。

	<blockquote>
	  <p><em>Space</em>, the final frontier.</p>
	</blockquote>
	<ul>
	  <li>Moe
	  <li>Larry
	  <li>Curly
	</ul>
	<table>
	  <thead>
	    <tr>
	      <th scope="col">Income
	      <th scope="col">Taxes
	  <tbody>
	    <tr>
	      <td>$ 5.00
	      <td>$ 4.50
	</table>