# markdown结合HTML标签使用语法
[toc]
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
    <div align = "left">![img](./.img/MarkdownUse3HelloWorld.png)</div>
样例：
<center> 文字</center>
<p align = "center">文字</p>
<p align = "left">文字</p>
<p align = "right">文字</p>

<div align = "right">![img](./.img/MarkdownUse3HelloWorld.png)</div>


## 设置上下标
语法：

    H<sub>2</sub>O
    Nike<sup>TM</sup>
样例：

H<sub>2</sub>O
Nike<sup>TM</sup>

## HTML标签替代markdown
语法：

[baidu](www.baidu.com)
<a href="https://www.www.baidu.com">baidu</a>
<div align = "center">![img](./.img/MarkdownUse3HelloWorld.png)</div>
![img](./.img/MarkdownUse3HelloWorld.png)
<img src = "./.img/MarkdownUse3HelloWorld.png" width = 100 height = 100 align = >

样例：
[锚点](#i)
<a href="https://www.www.baidu.com">baidu</a>

<del>wenjian</del>
<s>del</s>
<u>underlin</u>

    <code>code</code>
<br>
<hr>
<br>
<ul>
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ul>
