
# MarkDown使用教程

## 1. 常用部分

### 1.1 标题

#### [h1~h6]

```javascript
    # ~ ######
    一般 # 做为文章大标题，只有一个，###作为段落标题
```

#### 上下文标题

AAA

===

BBB

---

```javascript
    AAA
    ===
    BBB
    ---
```

### 1.2 强调

#### *斜体*

    *
    -

#### **加粗**

    **

#### ~~删除线~~

    ~~

### 1.3 代码

#### 代码块标记

```javascript
    ```
```

#### 代码块缩紧

    Tab 或四个空格

#### ```语法高亮显示```

```javascript
    ```javascript
```

#### `内联代码块`

```javascript
    `内联代码块`
```

### 1.4 表格

#### 表格

|     a     |        b        |      c       |
|:---------:|:--------------- | ------------:|
|   居中    | 左对齐           |       右对齐 |
| ========= | =============== | ============ |

```javascript
|     a     |        b        |      c       |
|:---------:|:--------------- | ------------:|
|   居中    | 左对齐           |       右对齐 |
| ========= | =============== | ============ |
```

#### 简约写法

a  | b | c  
:-:|:- |-:
    居中    |     左对齐      |   右对齐
============|=================|=============

```javascript
a  | b | c  
:-:|:- |-:
    居中    |     左对齐      |   右对齐
============|=================|=============
```

#### html表格

    http://www.tablesgenerator.com/

### 1.5. 链接

#### 内链式

[百度1](http://www.baidu.com/"百度一下"){:target="_blank"}

```javascript
[百度1](http://www.baidu.com/"百度一下"){:target="_blank"}
```

#### 引用式

[百度2][2]{:target="_blank"}
[2]: "www.baidu.com/"  "百度二下"

```[百度2][2]{:target="_blank"}
[2]: http://www.baidu.com/  "百度二下"
```

#### 邮箱链接式

<xxx@outlook.com>

```javascript
<xxx@outlook.com>
```

### 1.6 图片

#### 图片内链式

![name](./01.png '描述')

```javascript
![name](./01.png '描述')
```

#### 图片引用式

```javascript
    ![name][01]
[01]: ./01.png '描述'
```

#### 图片带有链接式

    ![name](./01.png '百度')](http://www.baidu.com){:target="_blank"}

[![name](./01.png '百度')][5]{:target="_blank"}
[5]: "www.baidu.com"

---

## 其他部分

### 2.1 序表

#### 无序

* one
* two
* three

```javascript
* one
* two
* three
+ - 可替代 *
```

#### 有序

1. one
2. two
3. three

```javascript
1. one
2. two
3. three
```

#### 序表嵌套

* one
  * two
  * three

```javascript
* one
    * two
    * three
```

### 2.2 清单

* [x] 选项一
* [ ] 选项二

```javascript
- [x] 选项一
- [ ] 选项二
```

### 2.3 引用

#### 引用

> hello world!

```javascript
> hello world!
```

#### 多层嵌套

> hello world
>> hello world
>>> hello world

```javascript
> hello world
>> hello world
>>> hello world
```

### 2.4 锚点

#### 锚点

[公式标题锚点](#1)

[需要跳转的目录] {#1}

```javascript
[公式标题锚点](#1)

[需要跳转的目录] {#1}
```

### 2.5 脚注

#### 脚注

Markdown[^1]

[^1]: Markdown是一种纯文本标记语言

```javascript
Markdown[^1]

[^1]: Markdown是一种纯文本标记语言

```

### 2.6 表情

#### github表情

:smile: :bowtie: :+1: :clap: :octocat:

```javascript
https://www.webpagefx.com/tools/emoji-cheat-sheet/
```

### 2.7 分隔符

---

---

```javascript
***
---
```