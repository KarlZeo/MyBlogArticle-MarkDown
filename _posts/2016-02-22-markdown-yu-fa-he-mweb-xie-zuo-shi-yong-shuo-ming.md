---
id: 303
title: Markdown 语法和 MWeb 写作使用说明
date: 2016-02-22T22:23:53+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=303
permalink: /2016/02/22/markdown-yu-fa-he-mweb-xie-zuo-shi-yong-shuo-ming/
dsq_thread_id:
  - 4618292463
views:
  - 10
categories:
  - Mac
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

## Markdown 的设计哲学 {#toc_0}

> Markdown 的目標是實現「易讀易寫」。
  
> 不過最需要強調的便是它的可讀性。一份使用 Markdown 格式撰寫的文件應該可以直接以純文字發佈，並且看起來不會像是由許多標籤或是格式指令所構成。
  
> Markdown 的語法有個主要的目的：用來作為一種網路內容的_寫作_用語言。 

<!--more-->

## 本文约定 {#toc_1}

如果有写 `效果如下：`， 在 MWeb 编辑状态下只有用 `CMD + R` 预览才可以看效果。

## 标题 {#toc_2}

Markdown 语法：

<pre class="prettyprint" ><code># 第一级标题 `&lt;h1&gt;` 
## 第二级标题 `&lt;h2&gt;` 
###### 第六级标题 `&lt;h6&gt;` 
</code></pre>

效果如下：

# 第一级标题 `<h1>` {#toc_3}

## 第二级标题 `<h2>` {#toc_4}

###### 第六级标题 `<h6>` {#toc_5}

## 强调 {#toc_6}

Markdown 语法：

<pre class="prettyprint" ><code>*这些文字会生成`&lt;em&gt;`*
_这些文字会生成`&lt;u&gt;`_

**这些文字会生成`&lt;strong&gt;`**
__这些文字会生成`&lt;strong&gt;`__
</code></pre>

在 MWeb 中的快捷键为： `CMD + U`、`CMD + I`、`CMD + B`
  
效果如下：

_这些文字会生成`<em>`_
  
<u>这些文字会生成`<u>`</u>

**这些文字会生成`<strong>`**
  
**这些文字会生成`<strong>`**

## 换行 {#toc_7}

四个及以上空格加回车。
  
如果不想打这么多空格，只要回车就为换行，请勾选：`Preferences` &#8211; `Themes` &#8211; `Translate newlines to <br> tags`

## 列表 {#toc_8}

### 无序列表 {#toc_9}

Markdown 语法：

<pre class="prettyprint" ><code>* 项目一 无序列表 `* + 空格键`
* 项目二
    * 项目二的子项目一 无序列表 `TAB + * + 空格键`
    * 项目二的子项目二
</code></pre>

在 MWeb 中的快捷键为： `Option + U`
  
效果如下：

  * 项目一 无序列表 `* + 空格键`
  * 项目二 
      * 项目二的子项目一 无序列表 `TAB + * + 空格键`
      * 项目二的子项目二

### 有序列表 {#toc_10}

Markdown 语法：

<pre class="prettyprint" ><code>1. 项目一 有序列表 `数字 + . + 空格键`
2. 项目二 
3. 项目三
    1. 项目三的子项目一 有序列表 `TAB + 数字 + . + 空格键`
    2. 项目三的子项目二
</code></pre>

效果如下：

  1. 项目一 有序列表 `数字 + . + 空格键`
  2. 项目二 
  3. 项目三 
      1. 项目三的子项目一 有序列表 `TAB + 数字 + . + 空格键`
      2. 项目三的子项目二

### 任务列表（Task lists） {#toc_11}

Markdown 语法：

<pre class="prettyprint" ><code>- [ ] 任务一 未做任务 `- + 空格 + [ ]`
- [x] 任务二 已做任务 `- + 空格 + [x]`
</code></pre>

效果如下：

<li class="task-list-item">
  <input type="checkbox" /> 任务一 未做任务 <code>- + 空格 + [ ]</code>
</li>
<li class="task-list-item">
  <input type="checkbox" checked /> 任务二 已做任务 <code>- + 空格 + [x]</code>
</li>

## 图片 {#toc_12}

Markdown 语法：

<pre class="prettyprint" ><code>![GitHub set up](http://zh.mweb.im/asset/img/set-up-git.gif)
格式: ![Alt Text](url)
</code></pre>

`Control + Shift + I` 可插入Markdown语法。
  
如果是 MWeb 的文档库中的文档，还可以用拖放图片、`CMD + V` 粘贴、`CMD + Option + I` 导入这三种方式来增加图片。
  
效果如下：

![GitHub set up](http://zh.mweb.im/asset/img/set-up-git.gif "Markdown 语法和 MWeb 写作使用说明")

## 链接 {#toc_13}

Markdown 语法：

<pre class="prettyprint" ><code>email &lt;example@example.com&gt;
[GitHub](http://github.com)
自动生成连接  &lt;http://www.github.com/&gt;
</code></pre>

`Control + Shift + L` 可插入Markdown语法。
  
如果是 MWeb 的文档库中的文档，拖放或`CMD + Option + I` 导入非图片时，会生成连接。
  
效果如下：

Email 连接： <example@example.com>
  
[连接标题Github网站](http://github.com)
  
自动生成连接像： <http://www.github.com/> 这样

## 区块引用 {#toc_14}

Markdown 语法：

<pre class="prettyprint" ><code>某某说:
> 第一行引用
> 第二行费用文字
</code></pre>

`CMD + Shift + B` 可插入Markdown语法。
  
效果如下：

某某说:

> 第一行引用
  
> 第二行费用文字 

## 行内代码 {#toc_15}

Markdown 语法：

<pre class="prettyprint" ><code>像这样即可：`&lt;addr&gt;` `code`
</code></pre>

`CMD + K` 可插入Markdown语法。
  
效果如下：

像这样即可：`<addr>` `code`

## 多行或者一段代码 {#toc_16}

Markdown 语法：

<pre class="prettyprint" ><code>```js
function fancyAlert(arg) {
  if(arg) {
    $.facebox({div:&#39;#foo&#39;})
  }

}
```
&lt;/code&gt;&lt;/pre&gt;

&lt;code&gt;CMD + Shift + K&lt;/code&gt; 可插入Markdown语法。&lt;br/&gt;
效果如下：

&lt;pre&gt;&lt;code class="language-js"&gt;function fancyAlert(arg) {
    if(arg) {
        $.facebox({div:&#039;#foo&#039;})
    }
    
}
&lt;/code&gt;&lt;/pre&gt;

&lt;h2 id="toc_17"&gt;顺序图或流程图&lt;/h2&gt;

Markdown 语法：

&lt;pre&gt;&lt;code&gt;```sequence
张三-&gt;李四: 嘿，小四儿, 写博客了没?
Note right of 李四: 李四愣了一下，说：
李四--&gt;张三: 忙得吐血，哪有时间写。
```

```flow
st=&gt;start: 开始
e=&gt;end: 结束
op=&gt;operation: 我的操作
cond=&gt;condition: 确认？

st-&gt;op-&gt;cond
cond(yes)-&gt;e
cond(no)-&gt;op
```
</code></pre>

效果如下（ `Preferences` &#8211; `Themes` &#8211; `Enable sequence & flow chart` 才会看到效果 ）：

<pre class="prettyprint" ><code class="language-sequence">张三-&gt;李四: 嘿，小四儿, 写博客了没?
Note right of 李四: 李四愣了一下，说：
李四--&gt;张三: 忙得吐血，哪有时间写。
</code></pre>

<pre class="prettyprint" ><code class="language-flow">st=&gt;start: 开始
e=&gt;end: 结束
op=&gt;operation: 我的操作
cond=&gt;condition: 确认？

st-&gt;op-&gt;cond
cond(yes)-&gt;e
cond(no)-&gt;op
</code></pre>

更多请参考：<http://bramp.github.io/js-sequence-diagrams/>, <http://adrai.github.io/flowchart.js/>

## 表格 {#toc_18}

Markdown 语法：

<pre class="prettyprint" ><code>第一格表头 | 第二格表头
--------- | -------------
内容单元格 第一列第一格 | 内容单元格第二列第一格
内容单元格 第一列第二格 多加文字 | 内容单元格第二列第二格
</code></pre>

效果如下：

| 第一格表头             | 第二格表头       |
| ----------------- | ----------- |
| 内容单元格 第一列第一格      | 内容单元格第二列第一格 |
| 内容单元格 第一列第二格 多加文字 | 内容单元格第二列第二格 |

## 删除线 {#toc_19}

Markdown 语法：

<pre class="prettyprint" ><code>加删除线像这样用： ~~删除这些~~
</code></pre>

效果如下：

加删除线像这样用： <del>删除这些</del>

## 分隔线 {#toc_20}

以下三种方式都可以生成分隔线：

<pre class="prettyprint" ><code>***

*****

- - -
</code></pre>

效果如下：

* * *

* * *

* * *

## MathJax {#toc_21}

Markdown 语法：

<pre class="prettyprint" ><code>块级公式：
$$  x = \dfrac{-b \pm \sqrt{b^2 - 4ac}}{2a} $$

\\[ \frac{1}{\Bigl(\sqrt{\phi \sqrt{5}}-\phi\Bigr) e^{\frac25 \pi}} =
1+\frac{e^{-2\pi}} {1+\frac{e^{-4\pi}} {1+\frac{e^{-6\pi}}
{1+\frac{e^{-8\pi}} {1+\ldots} } } } \\]

行内公式： $\Gamma(n) = (n-1)!\quad\forall n\in\mathbb N$
</code></pre>

效果如下（`Preferences` &#8211; `Themes` &#8211; `Enable MathJax` 才会看到效果）：

块级公式：
  
&#91; x = \dfrac{-b \pm \sqrt{b^2 &#8211; 4ac}}{2a} &#93;

&#91; \frac{1}{\Bigl(\sqrt{\phi \sqrt{5}}-\phi\Bigr) e^{\frac25 \pi}} =
  
1+\frac{e^{-2\pi}} {1+\frac{e^{-4\pi}} {1+\frac{e^{-6\pi}}
  
{1+\frac{e^{-8\pi}} {1+\ldots} } } } &#93;

行内公式： &#40;\Gamma(n) = (n-1)!\quad\forall n\in\mathbb N&#41;

## 脚注（Footnote） {#toc_22}

Markdown 语法：

<pre class="prettyprint" ><code>这是一个脚注：[^sample_footnote]
</code></pre>

效果如下：

这是一个脚注：<sup id="fnref1"><a href="#fn1" rel="footnote">1</a></sup>

## 注释和阅读更多 {#toc_23}

<!-- comment -->

<!--more-->

Actions->Insert Read More Comment _或者_ `Command + .`
  
**注** 阅读更多的功能只用在生成网站或博客时。

## TOC {#toc_24}

Markdown 语法：

<pre class="prettyprint" ><code>[TOC]
</code></pre>

效果如下：

  * [Markdown 的设计哲学](#toc_0) 
  * [本文约定](#toc_1) 
  * [标题](#toc_2) </li> 

  * [第一级标题 `<h1>`](#toc_3)</p> 
      * [第二级标题 `<h2>`](#toc_4)</p> 
          *   *   *   * [第六级标题 `<h6>`](#toc_5) 
      * [强调](#toc_6) 
      * [换行](#toc_7) 
      * [列表](#toc_8)</p> 
          * [无序列表](#toc_9) 
          * [有序列表](#toc_10) 
          * [任务列表（Task lists）](#toc_11) 
      * [图片](#toc_12) 
      * [链接](#toc_13) 
      * [区块引用](#toc_14) 
      * [行内代码](#toc_15) 
      * [多行或者一段代码](#toc_16) 
      * [顺序图或流程图](#toc_17) 
      * [表格](#toc_18) 
      * [删除线](#toc_19) 
      * [分隔线](#toc_20) 
      * [MathJax](#toc_21) 
      * [脚注（Footnote）](#toc_22) 
      * [注释和阅读更多](#toc_23) 
      * [TOC](#toc_24) 
    <div class="footnotes">
      <hr />
      
      <ol>
        <li id="fn1">
          这里是脚注信息&nbsp;<a href="#fnref1" rev="footnote">&#8617;</a>
        </li>
      </ol>
    </div>
    
    <!--wp-compress-html no compression-->
    
    <!--wp-compress-html-->