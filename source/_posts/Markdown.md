---
title: Markdown
date: 2020-08-12 17:44:24
categories: 随笔
tags:
  - Markdown
  - tech
---

## Markdown 使用教程

### 标题

markdown 通过`#`来标识标题，有几个`#`就表示几级标题。

```
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```

---

<!--more-->

### 样式

- `**粗体**`表示**粗体**
- `*斜体*`表示*斜体*
- `~~删除线~~`表示~~删除线~~

---

### 引用

`>>和>符号表示引用`
效果如下：

> 我是引用
>
> > 我是引用

---

### 链接

```
Markdown超链接的表示为:[超链接名称](超链接地址) 例如[百度](http://www.baidu.com)

```

例如：[百度](https://www.baidu.com)

图片的表示和超链接差不多，只是在前面多加了一个！，例如![图片](http://www.acemark.net/img/icon.jpg)

---

### 列表

1. 无序列表
   `*`、`+`、`-`都可以标识无序列表，例如：

```
+ 项目一
* 项目二
- 项目三
```

- 项目一

* 项目二

- 项目三

2. 有序列表
   有序列表用过在项目前面加数字来标识。

```
1. 项目一
2. 项目二
3. 项目三
```

效果如下：

1. 项目一
2. 项目二
3. 项目三

---

### ToDo 标记

```
- [ ] 未完成
- [X] 已完成
```

- [ ] 未完成
- [x] 已完成

---

### 表格

```
｜列名1｜列名2｜列名3｜
｜---｜---｜---｜
｜单元一｜单元二｜单元三｜
｜单元四｜单元五｜单元六｜
:--- 表示左对齐
--- 表示剧中对齐
---： 表示右对齐
```

| 标题 1 | 标题 2 | 标题 3 |
| :----- | ------ | -----: |
| 内容 1 | 内容 2 | 内容 3 |
| 内容 4 | 内容 5 | 内容 6 |

---

### 数学公式

- 行内公式
  行内公式包裹在两个`$`符号之间
  $f(x)=x+x^2$
- 块级公式

```
$$
\begin{bmatrix}
A&2&3\\2&3&4\\8&9&9
\end{bmatrix}
$$
```

$$
\begin{bmatrix}
1&2&3\\2&3&4\\6&7&8
\end{bmatrix}
$$

$$
\begin{pmatrix}
\alpha&\beta&\sigma\\
\theta&\rho&\pi\\
\delta&\Gamma&\epsilon
\end{pmatrix}
$$

$$
\begin{Bmatrix}
1&2&3\\4&5&6\\7&8&9\\
\end{Bmatrix}
$$

$$
\begin{vmatrix}
a&b&c\\d&e&f\\g&h&\\
\end{vmatrix}
$$

---

### 代码

Markdown 支持几十种编程语言语法高亮

- python

```python
def fun():
    print("hello word")
```

- js

```JavaScript
function fun(){
    console.log("hello word")
}
```

- C

```C
void fun(){
printf("hello word")
}
```

- shell

```shell
a=hell word
echo "${a}"
```
