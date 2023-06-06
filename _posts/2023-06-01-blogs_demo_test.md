---
title: Blogs Demo Test View
author: kuang_hl 
date: 2023-06-01 12:39:00 +0800
categories: [Blogging, Tutorial]
tags: [google analytics, pageviews]
comments: true

# 其他还有：
description: this is a demo. # 描述
toc: true # 打开目录
math: true # 加载数学功能
mermaid: true # 启用Mermaid
pin: true # 置顶帖子
---

## 标题.
```md
# h1
## h2
### h3
#### h4
```

## 字体.
```md
**粗体**
*斜体*
~~删除线~~
<u>下划线</u>
```

## 列表.
```md
# 有序列表
1. list1
2. list2
# 无序列表
- one
- two
# 任务列表
- [ ] task 1
- [x] task 2
# 描述列表\* Chirpy适用：
Sun
: the star around which the earth orbits
Moon
: the natural satellite of the earth, visible by reflected light from the sun
```

## 链接.
```md
纯URL：<https://jinhanlei.github.io/>
文字上加超链接: [jinhanlei](https://jinhanlei.github.io/)
使用链接变量（如果同一个链接使用很多遍，可以使用一个变量来定义该链接，犹如论文）：
[jinhanlei][1]
[1]:https://jinhanlei.github.io/（这句话是看不见的）
```

## 图片.
```md
![hello-world](https://huggingface.co/front/assets/huggingface_logo-noborder.svg)
在light模式下呈现阴影效果：
![Desktop View](https://huggingface.co/front/assets/huggingface_logo-noborder.svg){: .shadow}
```

## 代码.
```md
# 代码块
\```python
print("hello world")
\```
# 内联代码，一般写在正文中
`hello，world!`
```

## 表格.
```md
| Column1 | Column2 |
| ------- | ------- |
| Row1    | test    |
| Row2    | aaa     |
| Row3    | bb      |
| Row4    | cc      |
```

## 媒体资源.
```md
<iframe width="420" height="315" src="//player.bilibili.com/player.html?aid=80433022&bvid=BV1GJ411x7h7&cid=137649199&page=1" frameborder="0" allowfullscreen></iframe>
```


## 引用.
```md
> 引用
```

## 提示.
```md
> Example line for prompt.
{: .prompt-info }
(可选prompt-tip、prompt-info、prompt-warning、prompt-danger)
```

## 脚注.
```md
"never gonna give you up"——Rick[^Rick]
[^Rick]: Rick是一位著名歌手。
```

## 数学.
```md
# 内联公式
$x+y$
# 公式块
$$
\begin{Bmatrix}
   a & b \\
   c & d
\end{Bmatrix}
$$

$$
\begin{CD}
   A @>a>> B \\
@VbVV @AAcA \\
   C @= D
\end{CD}
$$
```

## Mermaid.
```md
# 横向流程图
\```mermaid
graph LR
A[方形] -->B(圆角)
    B --> C{条件a}
    C -->|a=1| D[结果1]
    C -->|a=2| E[结果2]
    F[横向流程图]
\```
```

## other.
```md
喜欢 <kbd>Ctrl</kbd> music～
```
<!--
<meting-js
	server="netease"
	type="playlist"
	id="60198">
</meting-js>
-->
<meting-js 
	server="netease" 
	type="playlist" 
	id="5393777464"
	fixed="true" 
	autoplay="true"
	loop="all"
	order="random"
	preload="auto"
	list-folded="ture"
	lrc-type="1"
	mutex="true">
</meting-js>


[more detail ref](http://jekyllcn.com/docs/posts/)
