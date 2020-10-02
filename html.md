## 标题

```html
<h1>This is a heading</h1>
```

## 段落

```html 
<p>This is a paragraph.</p>
```

## 链接

```html
<a href="www.w3school.com.cn">This is a link</a>
```

## 图像

```html
<img src="w3school.jpg" width="104" height="142" />
```

## 表格

```html
<table border="1">
    <tr>
        <th>Heading</th>
        <th>Another Heading</th>
    </tr>
    <tr>
        <td>(1,1)</td>
        <td>(1,2)</td>
    </tr>
    <tr>
        <td>(2,1)</td>
        <td>(2,2)</td>
    </tr>
</table>
```

## 列表

```html
<!--无序列表-->
<ul>
    <li>Coffee</li>
    <li>Milk</li>
</ul>
<!--有序列表-->
<ol>
    <li>Coffee</li>
    <li>Milk</li>
</ol>
```

## 块

```html
<div>块元素:
    大多数 HTML 元素被定义为块级元素或内联元素。
<span>内联元素:
    内联元素在显示时通常不会以新行开始。
```

## 类

```html
<!DOCTYPE html>
<html>
<head>
<style>
.cities {
    background-color:black;
    color:white;
    margin:20px;
    padding:20px;
} 
</style>
</head>

<body>

<div class="cities">
<h2>London</h2>
<p>London is the capital city of England. 
It is the most populous city in the United Kingdom, 
with a metropolitan area of over 13 million inhabitants.</p>
</div>

<div class="cities">
<h2>Paris</h2>
<p>Paris is the capital and most populous city of France.</p>
</div>

<div class="cities">
<h2>Tokyo</h2>
<p>Tokyo is the capital of Japan, the center of the Greater Tokyo Area,
and the most populous metropolitan area in the world.</p>
</div>

</body>
</html>
<!--==============================================-->
<!DOCTYPE html>
<html>
<head>
<style>span.red {color:red;}</style>
</head>  
<body>
<h1>My <span class="red">Important</span> Heading</h1>
</body>
</html>
```

## 布局

```htm
<!DOCTYPE html>
<html>

<head>
<style>
#header {
    background-color:black;
    color:white;
    text-align:center;
    padding:5px;
}
#nav {
    line-height:30px;
    background-color:#eeeeee;
    height:300px;
    width:100px;
    float:left;
    padding:5px;	      
}
#section {
    width:350px;
    float:left;
    padding:10px;	 	 
}
#footer {
    background-color:black;
    color:white;
    clear:both;
    text-align:center;
   padding:5px;	 	 
}
</style>
</head>

<body>

<div id="header">
<h1>City Gallery</h1>
</div>

<div id="nav">
London<br>
Paris<br>
Tokyo<br>
</div>

<div id="section">
<h2>London</h2>
<p>
London is the capital city of England. It is the most populous city in the United Kingdom,
with a metropolitan area of over 13 million inhabitants.
</p>
<p>
Standing on the River Thames, London has been a major settlement for two millennia,
its history going back to its founding by the Romans, who named it Londinium.
</p>
</div>

<div id="footer">
Copyright ? W3Schools.com
</div>

</body>
</html>
```

## 音频

```html
<embed height="100",width="100" src="song.mp3" />
<object height="100",width="100" data="song.mp3"></object>
<audio controls="controls">
    <source src="song.mp3" type="audio/mp3" />
    <source src="song.ogg" type="audio/ogg" />
</audio>
```

## 视频

```html
<video width='320',height='240' controls="controls">
    <source src="movie.mp4",type="video/mp4">
    <source src="movie.ogg",type="video/ogg">
</video>
```

