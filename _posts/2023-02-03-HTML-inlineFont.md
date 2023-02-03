---
layout: post
title: HTML) Inline Math
categories: HTML/Markdown
tags: [GitBlog, HTML]
published: true
---
## 1. Markdown inline math
<hr>
&nbsp;&nbsp;Generally, Github Markdown supprots inline math, using `$` keyword.

```html
$1 + 1 = 2$
```

<br/><br/>

## 2. MD code problem and an alternative
<hr>
&nbsp;&nbsp;However, when I write my blog, this code is not work. So, I just apply `font` tag of HTML.

```html
<font face = "Cambria Math">P(y&#124;x)</font>
```
&nbsp;&nbsp;Its result is "<font face = "Cambria Math">P(y&#124;x)</font>". `&#124` is an unicode. It works well when the used font is already installed in the local computer of the client watching the webpage. Otherwise, the default font is shown instead of what font I specify. And, in the `font` tag, some symbols make trouble because of their own function in HTML. Then, use the unicode of the symbol.

<br/><br/>

## Refers
<hr>
<a href = "https://www.tutorialspoint.com/html/html_fonts.htm"><i>tutorials point</i> </a><br/>
<a href = "https://unicode-table.com/en/sets/mathematical-signs/"><i>Unicode Character Table</i> </a><br/>