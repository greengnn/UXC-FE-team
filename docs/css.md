# CSS编码风格指南

## 编码
使用UTF-8（非BOM），不需要在代码中指定编码类型。

## CSS验证

尽量使用CSS验证，除非因为修正浏览器解析差异而编写私有属性，否则都应该使用合法的CSS代码。可以使用W3C CSS validator测试你的CSS。使用合法的CSS同样是一个可被衡量的规则，它能标记出那些不起作用和可被删除的代码，并确保CSS的正确使用。

## ID和class命名

使用有意义的或通用的ID和class命名：ID和class的命名应反映该元素的功能或使用通用名称，而不要用抽象的晦涩的命名。反映元素的使用目的是首选；使用通用名称代表该元素不表特定意义，与其同级元素无异，通常是用于辅助命名；使用功能性或通用的名称可以更适用于文档或模版变化的情况。

    /* 不推荐: 无意义 */
    #yee-1901 {}
    /* 不推荐: 与样式相关 */
    .button-green {}
    .clear {}

    /* 推荐: 特殊性 */
    #gallery {}
    #login {}
    .video {}

    /* 推荐: 通用性 */
    .aux {}
    .alt {}

## ID和class命名风格

越简短越好，只要足够表达涵义。这样既有助于理解，也能提高代码效率。

    /* 不推荐 */
    #navigation {}
    .atr {}
    /* 推荐 */
    #nav {}
    .author {}
##类型选择器

避免同时使用标签、ID和class作为定位一个元素选择器；从性能上考虑也应尽量减少选择器的层级。

    /* 不推荐 */
    ul#example {}
    div.error {}
    /* 推荐 */
    #example {}
    .error {}

## 属性连写

尽量使用属性连写：CSS语法提供了大量支持连写的属性（比如font），即使只有一个值需要表达的情况，连写也能提高代码效率和可读性。

    /* 不推荐 */
    border-top-style: none;
    font-family: palatino, georgia, serif;
    font-size: 100%;
    line-height: 1.6;
    padding-bottom: 2em;
    padding-left: 1em;
    padding-right: 1em;
    padding-top: 0;

    /* 推荐 */
    border-top: 0;
    font: 100%/1.6 palatino, georgia, serif;
    padding: 0 1em 2em;

## 0与单位

属性值为0的情况下请省略单位，除非被要求加上。

    margin: 0;
    padding: 0;

## 小数点前的0

小数点前的0请省略。

    font-size: .8em;

## URL中的引号

URL中的引号（”"或”）请省略。

    @import url(//www.google.com/css/go.css);

## 十六进制

可以的情况下用3个字符来表达6个十六进制字符的信息。

    /* 不推荐 */
    color: #eebbcc;
    /* 推荐 */
    color: #ebc;

## 前缀

对ID和class使用带前缀的命名（短破折号连接），在大型项目中，可以防止命名冲突，配合查找快速定位，便于维护。

    .adw-help {} /* AdWords */
    #maia-note {} /* Maia */

## 分隔符

对ID和class使用分隔符连接单词（分隔符只能有一种，如果你选择了短破折号就不要再用下划线或者其他连字符）以便于理解和扫描。

    /* 不推荐: 没有分离单词demo和image */
    .demoimage {}
    /* 不推荐: 应使用短破折号 */
    .error_status {}
    /* 推荐 */
    #video-id {}
    .ads-sample {}

## Hacks

请不用动不动就使用浏览器检测和CSS Hacks，先试试别的解决方法吧！考虑到代码高效率和易管理，虽然这两种方法能快速解决浏览器解析差异，但应被视为最后的手段。在长期的项目中，允许使用hack只会带来更多的hack，你越是使用它，你越是会依赖它！

### 建议的hacks

使用作用域区分浏览器类型
    <!--[if lt IE 7]><html class="ie6 oldie"><![endif]-->
    <!--[if IE 7]><html class="ie7 oldie"><![endif]-->
    <!--[if IE 8]><html class="ie8 oldie"><![endif]-->
    <!--[if gt IE 8]><!--> <html> <!--<![endif]-->

区别属性：

    IE6         _property:value
    IE6/7       *property:value
    IE6/7/8/9   property:value\9
    非IE6        property//:value

区别规则：

    IE6
    * html selector { … }

    IE7
    *:first-child+html selector { … }

    非IE6
    html>body selector { … }

    firefox only
    @-moz-document url-prefix() { … }

    saf3+/chrome1+
    @media all and (-webkit-min-device-pixel-ratio:0) { … }

    opera only
    @media all and (-webkit-min-device-pixel-ratio:10000),not all and (-webkit-min-device-pixel-ratio:0) { … }

    iPhone/mobile webkit
    @media screen and (max-device-width: 480px) { … }

## 整块内容缩进

所有整块的内容都应该缩进，包括规则块和样式声明规则，利于清晰反映层次提高可读性。

    @media screen, projection {
      html {
        background: #fff;
        color: #444;
      }
    }
## 声明结束符

每个声明结束都应该带一个分号，不管是不是最后一个声明

    /* 不推荐 */
    .test {
      display: block;
      height: 100px
    }
    /* 推荐 */
    .test {
      display: block;
      height: 100px;
    }

## 属性名分隔

每个属性与属性值之间用一个空格分隔，位于冒号之后。

    /* 不推荐 */
    h3 {
      font-weight:bold;
    }
    /* 推荐 */
    h3 {
      font-weight: bold;
    }

## 选择器和声明分离

选择器和声明应各占一行，多个选择器的情况每个选择器独占一行

    /* 不推荐 */
    a:focus, a:active {
      position: relative; top: 1px;
    }
    /* 推荐 */
    h1,
    h2,
    h3 {
      font-weight: normal;
      line-height: 1.2;
    }
## 规则分离

每个声明里的规则都另起一行

    html {
      background: #fff;
    }

    body {
      margin: auto;
      width: 50%;
    }

## 区块注释

对一个代码区块注释（可选），将样式语句分区块并在新行中对其注释。

    /* Header */
    #adw-header {}

    /* Footer */
    #adw-footer {}

    /* Gallery */
    .adw-gallery {}

