# markdown结合HTML标签使用语法

[toc]

## 链接自动转换

语法：

    <www.baidu.com>

样例：

<https://www.baidu.com>
## 设置字体

语法：

    <font face="华文新魏" color="red" size = 60>测试数据</font>
    注：
        face：字体
        color:颜色
        size：字体大小（1~7）

样例：

    <font face="宋体" color="purple" size = 7  id = "a">这是数据</font>


## 设置文件背景色

语法：

    <table><tr><td bgcolor = "red" size = 60>特别标注 </td></tr></table>
    注:
        单独标注出也可以使用``，例如：特别`标注`
样例：
<table><tr><td bgcolor = "pink" >denghuo </td></tr></table>

特别`标注`

## 设置文字、图片位置

语法：

    <center> 文字</center>
    <p align = "center">文字</p>
    <p align = "left">文字</p>
    <p align = "right">文字</p>

样例：

<center> 文字</center>
<p align = "center">文字</p>
<p align = "left">文字</p>
<p align = "right">文字</p>

## 设置上下标

语法：

    H<sub>2</sub>O
    Nike<sup>TM</sup>
样例：

H<sub>2</sub>O
Nike<sup>TM</sup>

## HTML标签替代markdown
###标题

语法：

    <h1>标题</h1>
    <h2>标题</h2>
    <h3>标题</h3>
    <h4>标题</h4>
    <h5>标题</h5>
    <h6>标题</h6>


样例：

<h1>标题</h1>
<h2>标题</h2>
<h3>标题</h3>
<h4>标题</h4>
<h5>标题</h5>
<h6>标题</h6>

### 文字格式

语法：

    <em>斜体</em>
    <i>斜体</i>
    *斜体*
    _斜体_
    <strong>加粗</strong>
    <b>加粗</b>
    **加粗**
    __加粗__


样例：

<em>斜体</em>

<i>斜体</i>

*斜体*

_斜体_

<strong>加粗</strong>

<b>加粗</b>

**加粗**

__加粗__

### 引用

语法：

    <q>李商隐说:庄生晓梦迷蝴蝶。望帝春心托杜鹃。</q>
    <blockquote>李商隐说:庄生晓梦迷蝴蝶。望帝春心托杜鹃。</blockquote>
    > 李商隐说:庄生晓梦迷蝴蝶。望帝春心托杜鹃。

样例：

<q>李商隐说:庄生晓梦迷蝴蝶。望帝春心托杜鹃。</q>
<blockquote>李商隐说:庄生晓梦迷蝴蝶。望帝春心托杜鹃。</blockquote>

> 李商隐说:庄生晓梦迷蝴蝶。望帝春心托杜鹃。

### 线

语法：

    <del>This is strikethrough</del>
    <s>This is strikethrough</s>
    ~~This is strikethrough~~
    <ins> This is strikethrough</ins>
    </u>This is strikethrough</u>
    <hr/>
    ---
    ***
    <br/> 注：换行

样例：

 <del>This is strikethrough</del>
<s>This is strikethrough</s>
~~This is strikethrough~~
<ins> This is strikethrough</ins>
</u>This is strikethrough</u>

---

***
<br/>

### 代码
+ 单行代码

    语法：
        
        <code> cout<<"Hello World!"<<endl; </code>
        ` cout<<"Hello World!"<<endl; `
    样例：

    <code> cout<<"Hello World!"<<endl; </code>
    ` cout<<"Hello World!"<<endl; `

+ 多行代码

    语法：

        <pre>
        public static void main(){
            System.out.println("输出数据！");
        }
        </pre>

        ```java
        public static void main(){
            System.out.println("输出数据！");
        }
        ```
    样例：

    <pre>
    public static void main(){
        System.out.println("输出数据！");
    }
    </pre>
    
    ```java
        public static void main(){
            System.out.println("输出数据！");
        }
    ```
### 列表

语法：

    <ol start = 3 >
        <li>list </li>
        <li>list </li>
        <li>list </li>
    </ol>
    1. list
    2. list
    3. list
    <ul>
        <li>list </li>
        <li>list </li>
        <li>list </li>
    </ul>
    + list
    + list
    + list

样例：

<ol start = 3 >
    <li>list </li>
    <li>list </li>
    <li>list </li>
</ol>

1. list
2. list
3. list
<ul>
    <li>list </li>
    <li>list </li>
    <li>list </li>
</ul>

 + list
 + list
 + list

### 链接

语法：

    [baidu](www.baidu.com)
    <a href="https://www.www.baidu.com">baidu</a>

样例：

[baidu](www.baidu.com)
<a href="https://www.www.baidu.com">baidu</a>

### 图片

语法：

    <img src = "https://github.com/images/modules/contact/heartocat.png" alt = "github" width = 50 height = "50" align = "center">
    ！[github](https://github.com/images/modules/contact/heartocat.png)

样例：

<img src = "https://github.com/images/modules/contact/heartocat.png" alt = "github" width = 100 height = "100">

![github](https://github.com/images/modules/contact/heartocat.png)

### 图片嵌入链接

语法：

    <a href = "https://www.github.com"><img src = "https://github.com/images/modules/contact/heartocat.png" width = 50 heigth = 50/></a>
    [![github](github.com/images/modules/contact/heartocat.png)](www.github.com)
样例：

<a href = "https://www.github.com"><img src = "https://github.com/images/modules/contact/heartocat.png" width = 50 heigth = 50/></a>

[![github](https://github.com/images/modules/contact/heartocat.png)](www.github.com)

### 表格

语法：

    <table border = 1 summary = "2014 score">
        <caption> 2014 score </caption>
        <tr>
            <th>班级</th>
            <th>学生数</th>
            <th>平均成绩</th>
        <tr>
        <tr>
            <td>一班</td>
            <td>30</td>
            <td>89</td>
        </tr>
        <tr>
            <td>二班</td>
            <td>35</td>
            <td>85</td>
        <tr>
    </table>

    |班级|学生数|平均成绩|
    |:---:|:---:|:---:|
    |一班|30|89|
    |二班|35|85|


样例：
<table border = 1 summary = "2014 score">
    <caption> 2014 score </caption>
    <tr>
        <th>班级</th>
        <th>学生数</th>
        <th>平均成绩</th>
    </tr>
    <tr>
        <td>一班</td>
        <td>30</td>
        <td>89</td>
    </tr>
    <tr>
        <td>二班</td>
        <td>35</td>
        <td>85</td>
    </tr>
</table>


|班级|学生数|平均成绩|
|:---:|:---:|:---:|
|一班|30|89|
|二班|35|85|

