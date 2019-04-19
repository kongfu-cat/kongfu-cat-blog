---
layout:     post
title:      "Hello My Blog"
subtitle:   "博客搭建好了, 想想有点小激动"
date:       2019-04-15
author:     "LeYe Hu"
header-img: "img/post-bg-hello-my-blog.jpg"
tags:
    - 经历
    - MarkDown
---

## 前言

> 一段时间的学习, 自身的不足愈加明显
通过写写博客, 放松的同时, 每日思考一下自己都做了些什么

## 正文

要写博客了, 使用MarkDown编写, 语法什么的还是需要了解的

本博客使用的是 **Kramdown**
> Kramdown是一个完全由Ruby语言编写的Markdown解析器
在语法上Kramdown是Markdown的一个超集, 较Markdown而言, Kramdown语法更加严谨
但基本能很好的兼容Markdown语法, 有所差异的地方是高亮部分

以下语法参考[官网文档](https://kramdown.gettalong.org/syntax.html)

目前只记录一些常用的语法, 其余需要使用时在更新

#### 转义序列

~~~
This \`is not a code\` span!
以下列出一些需要通过转义序列来原样显示的字符
\ backslash
. period
* asterisk
_ underscore
+ plus
- minus
= equal sign
` back tick
()[]{}<> left and right parens/brackets/braces/angle brackets
# hash
! bang
<< left guillemet
>> right guillemet
: colon
| pipe
" double quote
' single quote
$ dollar sign
~~~

句子与段落
* 一般而言, 单独由空格或者Tab组成的行会被视为一行空白行, 多行连续的空白行会被视为一行空白行
* 一个段落, 首行最多三个缩进, 其他行可以有任意缩进
> 块的边界问题需要注意一下, 一般可以通过`^`**EOF标记**来标识块的结束

#### 标题

标题部分Kramdown支持 *Setext* 和 *atx* 样式
> 这里我主要使用atx样式
^
* 以#开头, #前不能有空格, 任意#(包括0)来结束
* \#个数表示标题级别, 最多六级
* 中间标题首尾两端的空格会被删除
~~~
# First level header
### Third level header ###
## Second level header ######
~~~
> 
# First level header
### Third level header ###
## Second level header ######
^

* 设置头部 ID *
 ~~~ 
 # Hello # {#id} 
 ~~~
 > # Hello # {#id}

#### 段落引用 

* 使用>标记, >后的第一个空格字符无效
* 支持换行(可以通过EOB标记分割 ^)
* 可以与其他块级元素嵌套使用(包括他自己)
~~~
> This is a paragraph inside
    a blockquote.
>
> > This is a nested paragraph
    that continues here
> and here
> > and here
~~~
> This is a paragraph inside
    a blockquote.
>
> > This is a nested paragraph
    that continues here
> and here
> > and here

#### 代码块

* 可以使用四个空格或者一个Tab来标识
* 或者三个及以上~开头及结尾
~~~~~~~~~~~~
~~~~~~~~
Here comes some code.
~~~~~~~~
~~~~~~~~~~~~
* 代码中如果使用了~可以如下使用
~~~~~~~~~~~~~~~~~~~~~~~
~~~~~~~~~~~~
~~~~~~~
code with tildes
~~~~~~~~
~~~~~~~~~~~~~~~~~~
~~~~~~~~~~~~~~~~~~~~~~~
* 可以使用IAL( inline attribute list)来标记语言类型, 使用键值对的形式
~~~
  {: title="The blockquote title"}
  {: #myid}
  {: .language-ruby}  标记ruby语言, 影响高亮显示
~~~
也可以这样
~~~~~~~~~~~~~~~~~~
~~~ ruby
def what?
42
end
~~~
~~~~~~~~~~~~~~~~~~
> ~~~ ruby
> def what?
> 42
> end
> ~~~

与代码块有点类似的是**Code Spans**(不知道怎么翻译XX)
* 使用 ` 包围, 可以将代码内联到句子中
~~~
Use `<html>` tags for this.
This is a Ruby code fragment `x = Class.new`{:.language-ruby}
~~~
> Use `<html>` tags for this.
> This is a Ruby code fragment `x = Class.new`{:.language-ruby}
* 如果文本中包含\`,就使用两个\`\`包围
~~~
Here is a literal `` ` `` backtick.
And here is `` `some` `` text (note the two spaces so that one is left
in the output!).
~~~
> Here is a literal `` ` `` backtick.
And here is `` `some` `` text (note the two spaces so that one is left
in the output!).

#### 列表

* 无序列表--\*, +, - 后面接一个空格表示开始
* 有序列表--数字. 后面接一个空格表示开始
^
~~~
* kram
+ down
- now
1. kram
2. down
3. now
~~~
> * kram
+ down
- now
1. kram
2. down
3. now
^
* 可以内嵌使用, 使用方式一致
^
~~~
1. list 1 item 1
 2. list 1 item 2 (indent 1 space)
  3. list 1 item 3 (indent 2 spaces)
   4. list 1 item 4 (indent 3 spaces)
    5. lazy text belonging to above item 4
* list 1 item 1
  * nested list item 1(indent 2 space)
  * nested list item 2
* list 1 item 2
  * nested list item 1
~~~
> 1. list 1 item 1
>  2. list 1 item 2 (indent 1 space)
>   3. list 1 item 3 (indent 2 spaces)
>    4. list 1 item 4 (indent 3 spaces)
>     5. lazy text belonging to above item 4
> * list 1 item 1
>   * nested list item 1(indent 2 space)
>   * nested list item 2
> * list 1 item 2
>   * nested list item 1

#### 表格

* 使用`|`符号进行表格单元格切分, 尾部的可以忽略
^
~~~
| First cell|Second cell|Third cell
| First | Second | Third |

First | Second | | Fourth |
~~~
> | First cell|Second cell|Third cell
> | First | Second | Third |
> 
> First | Second | | Fourth |

~~~
|-----------------+------------+-----------------+----------------|
| Default aligned |Left aligned| Center aligned  | Right aligned  |
|-----------------|:-----------|:---------------:|---------------:|
| First body part |Second cell | Third cell      | fourth cell    |
| Second line     |foo         | **strong**      | baz            |
| Third line      |quux        | baz             | bar            |
|-----------------+------------+-----------------+----------------|
| Second body     |            |                 |                |
| 2 line          |            |                 |                |
|=================+============+=================+================|
| Footer row      |            |                 |                |
|-----------------+------------+-----------------+----------------|
~~~
> 
|-----------------+------------+-----------------+----------------|
| Default aligned |Left aligned| Center aligned  | Right aligned  |
|-----------------|:-----------|:---------------:|---------------:|
| First body part |Second cell | Third cell      | fourth cell    |
| Second line     |foo         | **strong**      | baz            |
| Third line      |quux        | baz             | bar            |
|-----------------+------------+-----------------+----------------|
| Second body     |            |                 |                |
| 2 line          |            |                 |                |
|=================+============+=================+================|
| Footer row      |            |                 |                |
|-----------------+------------+-----------------+----------------|
^
* 也可以这样写
^
~~~
|---
| Default aligned | Left aligned | Center aligned | Right aligned
|-|:-|:-:|-:
| First body part | Second cell | Third cell | fourth cell
| Second line |foo | **strong** | baz
| Third line |quux | baz | bar
|---
| Second body
| 2 line
|===
| Footer row
~~~
> 
|---
| Default aligned | Left aligned | Center aligned | Right aligned
|-|:-|:-:|-:
| First body part | Second cell | Third cell | fourth cell
| Second line |foo | **strong** | baz
| Third line |quux | baz | bar
|---
| Second body
| 2 line
|===
| Footer row
^

#### 水平线

* 三个连续的\*, \-或者\_

~~~
* * *
---
_ _ _ _
---------------
~~~
> 
* * *
---
_ _ _ _
---------------
^

#### 数学表达式

* 两个$$包围, 使用需要符合LaTeX语法 (需要使用 **[MathJax](https://www.mathjax.org/)** 脚本渲染)
^
~~~
$$
\begin{align*}
  & \phi(x,y) = \phi \left(\sum_{i=1}^n x_ie_i, \sum_{j=1}^n y_je_j \right)
  = \sum_{i=1}^n \sum_{j=1}^n x_i y_j \phi(e_i, e_j) = \\
  & (x_1, \ldots, x_n) \left( \begin{array}{ccc}
      \phi(e_1, e_1) & \cdots & \phi(e_1, e_n) \\
      \vdots & \ddots & \vdots \\
      \phi(e_n, e_1) & \cdots & \phi(e_n, e_n)
    \end{array} \right)
  \left( \begin{array}{c}
      y_1 \\
      \vdots \\
      y_n
    \end{array} \right)
\end{align*}
$$
~~~
> 
$$
\begin{align*}
  & \phi(x,y) = \phi \left(\sum_{i=1}^n x_ie_i, \sum_{j=1}^n y_je_j \right)
  = \sum_{i=1}^n \sum_{j=1}^n x_i y_j \phi(e_i, e_j) = \\
  & (x_1, \ldots, x_n) \left( \begin{array}{ccc}
      \phi(e_1, e_1) & \cdots & \phi(e_1, e_n) \\
      \vdots & \ddots & \vdots \\
      \phi(e_n, e_1) & \cdots & \phi(e_n, e_n)
    \end{array} \right)
  \left( \begin{array}{c}
      y_1 \\
      \vdots \\
      y_n
    \end{array} \right)
\end{align*}
$$
^
* 内联使用
^
~~~
\$$ 5 + 5 $$
~~~
> \$$ 5 + 5 $$

#### Html语句块

~~~
<div id="content"><div id="layers"><div id="layer1">
This is some text in the `layer1` div.
</div>
This is some text in the `layers` div.
</div></div>
This is a para outside the HTML block.
~~~
> 
> <div id="content"><div id="layers"><div id="layer1">
> This is some text in the `layer1` div.
> </div>
> This is some text in the `layers` div.
> </div></div>
> This is a para outside the HTML block.
^

#### 链接

* 使用尖括号包围\<\>
^
~~~
Information can be found on the <http://example.com> homepage.
You can also mail me: <me.example@example.com>
~~~
> 
Information can be found on the <http://example.com> homepage.
You can also mail me: <me.example@example.com>
^
* \[文本\]\(链接 "标题"\)
^
~~~
This is [a link](http://rubyforge.org) to a page.
A [link](../test "local URI") can also have a title.
And [spaces](link with spaces.html)!
~~~
> 
This is [a link](http://rubyforge.org) to a page.
A [link](../test "local URI") can also have a title.
And [spaces](link with spaces.html)!
^

#### 参考

~~~
The next paragraph contains a link and some text.
[Room 100]\: There you should find everything you need!
[Room 100]: link_to_room_100.html
~~~
> 
> The next paragraph contains a link and some text.
> [Room 100]\: There you should find everything you need!
> [Room 100]: link_to_room_100.html
^
#### 图片

* 和链接很像, 只需要在前面加入一个惊叹号, 也可以加入内联属性设置宽高
^
~~~
Here is an inline ![Cat]({{ site.baseurl }}/img/kongfu-cat.jpg){:height="36px" width="36px"}.
And here is a referenced ![Cat]

[Cat]: {{ site.baseurl }}/img/kongfu-cat.jpg
{: height="36px" width="36px"}
~~~
> 
> Here is an inline ![Cat]({{ site.baseurl }}/img/kongfu-cat.jpg){:height="36px" width="36px"}.
> And here is a referenced ![Cat]
> 
> [Cat]: {{ site.baseurl }}/img/kongfu-cat.jpg
> {: height="36px" width="36px"}
^

#### 强调

* 使用\*或\_包围
* 强调文本--斜体
* 强强调文本--粗体
* 没有更强的了:)
^
~~~
*some text*
_some text_
**some text**
__some text__
~~~
>
*some text*
_some text_
**some text**
__some text__
^
#### 脚注

* \[ \]内以^开头
* 在\[^ \]之前要有换行
^
~~~
This is some text.[^1]. Other text.[^footnote].

[^1]: Some *crazy* footnote definition.
[^footnote]:
    > Blockquotes can be in a footnote.
~~~
>
> This is some text.[^1]. Other text.[^footnote].
> 
> [^1]: Some *crazy* footnote definition.
> [^footnote]:
    > Blockquotes can be in a footnote.
^


## 后记

还是不怎么习惯看英文资料, 写的想吐, 欧拉欧拉 XX
由于英文水平较渣, 可能还有不少翻译上的问题, 之后遇到在修改吧

--- LeYe Hu 初记于 2019.04.15