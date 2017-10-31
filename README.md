﻿2017.10月学习html的一些笔记，学习不系统，可能比较零散

### 1 网页的基本结构
``` 
    <html>
    	<head>
	    	<title> 网页标题 </title>
	    	<meta charset="utf-8"/> <!--设定字符编码-->
	    </head>
    	<body>
        网页主体
    	</body>
    </html>
```
### 2 标签（Lablels）

#### 2.1 标题

这分别表示网页的6级标题：
```
    <h1>文字内容</h1>
      ...
    <h6>文字内容</h6>
```
#### 2.2 特殊符号

如**换行符**用`<br/>`表示，在网页中加入**水平线**用`<hr/>`, 插入**空格**一般用`&emsp;`或者`&nbsp;`，还有一些特殊符号如`&gt;`和`&lt;`分别表示“&gt;” 和“&lt;”号

引号`&quot;`；版权符号`&copy;`

#### 2.3 格式标签

##### 分组标签:
```
    <span style=" "> text </span> /*分组内容可以设置特殊格式（字体，字号，颜色，加粗等等）*/
```
##### 粗体、斜体文本：    

    <strong> 粗体文本</strong>
 
    <em> 斜体文本</em>
 
想玩点不一样的东西，可以试试`< ? style=" ">设置样式的（富）文本</>`，其中"?"代表标签内容，这里面有很多属性值得研究

#### 2.4 链接标签

##### 2.4.1 页面内部链接

先添加链接目的地的标签：

    <a name = "mark"> destnation text </a>

再对链接文本建立引用

    <a href = "mark"> link text </a>

##### 2.4.2 外部链接

    <a> href = "path" target = "_self(_blank)"</a>
    
##### 2.4.3 图片引用：

    <img src="path" alt="replace text(img url is null)" title = "promote info" width = "x" height = "y"/>
    
### 3 列表和表格

#### 3.1 列表（list）

##### 3.1.1 order-list
		<ol type="A/a/I/i/1"> /*有序列表5大排序方式，数字默认*/
			<li > content </li>
			...
			<li> content </li>
		</ol>
##### 3.1.2 disorder-list
		<ul type="disc"> /*无序列表3种排序方式，默认实心圆圈*/
			<li type="disc(default)/circle/square"> content </li>
			...
			<li> content </li>
		</ul> 
		
*在css样式中，可以设置列表的样式*

		ul{
		    list-style:none; /*取消列表前面的排序*/
		}
		
##### 3.1.3 define-list
		<dl> /*目前已知适用功能 可以控制悬挂缩进*/
			<dt> content
				<dd>
					content
				</dd>
			</dt>
		</dl>
		
#### 3.2 表格（table）

##### 3.2.1 basical format

基本格式：

		<table>
			<tr >
				<td>
				
				</td>
			</tr>
	
		</table>

基本属性：

		align="left(default)/center/right" /*水平对齐方式*/

		valign="top/middle(default)/bottom/baseline" /*垂直对齐方式*/

		rowspan="x" /*跨行*/

		colspan="y" /*跨列*/

##### 3.2.2 A typical table style code 典型的css样式列表 

		<style type="text/css"> /* 表格全局设定，优先级高于表格正文的设定 , 对现网页内所有表格生效*/
			
			table {
					width: 800px; height: 300px; 
          
					margin:0px auto; /* 顶端边距0px， 左右居中*/
          
					border-spacing: 0px; /*单元格边距调为0px，将单元格边界重合（默认不重合）*/
          
					border-collapse:collapse; /*接上个设定，将重合的单元格边界只显示一个（去掉线条颜色加深）*/ 
          
					color: black;/*设定文本颜色，优先级低，table内可以重新定义颜色*/ 
				}
			 td {
				border: 1px dashed blue; /*显示单元格边界，1px黑色虚线（实线为solid），只能在td下设置*/
        
				text-align: center; /*设定文本对齐方式，优先级高于table 内设定*/
        
				border-style:dotted; /*设定单元格边界样式，同第一个设定相同，优先级高*/
        
				border-color: black; /*设定单元格边框颜色，同第一个设定相同，优先级高*/
				
				
			}
			
			.a{
				background-color:beige; /* 设定分组a的背景颜色*/
        
				/*text-align: left; 设定分组的对齐方式*/	
			}
			
			.b{
				background-color: honeydew; /* 设定分组b的背景颜色*/
			}
		</style>
		
2 种使其生效的方法：

			1）	code it within <head> </head>
				
				<head>
					<title> title </title>
				
					<style type="text/css"> 
					
						type setting
					</style>
				</head>

			2)	firstly, creat a new .css file, and then write the 
					
					<style type="text/css">
					
						type setting
					</style>
				
				into the file;
				
				secondly,  quote the css file by using code below
				
					<link rel="stylesheet" type="text/css" href=".css"/>
          
##### 3.2.3 table nesting 表格嵌套
		
		<table>
			<tr>
				<td>
					<table>
						<tr>
							<td> content1</td>
						</tr>
						<tr>
						<tr>
							<td>content2</td>
						</tr>
					</table>				
				</td>
			</tr>
			<tr>
				<td>
					no nesting here
				</td>
			</tr>
		</table>

#### 4 表单
##### 4.1表单基本表现
```
	<form method="post/get" action=""> /* "action"表示向何处发送数据*/
		<input type="" ...>
		<select name="">  /*下拉列表框至少有一个option*/
			<option value="" selected="selected">下拉选项（选中）</option>
			...
		</selected>
	</form>

```
##### 4.2 表单的type属性
>text，指定为普通文本框 默认属性

password 指定为密码框（隐藏输入内容）

checkbox 指定为多选框

radio 指定为单选框 /*单选框属于一个类别，其name属性必须相同*/

submit 提交按钮 /*文本框和按钮在同一个form里面，按钮功能生效*/

reset 重置按钮

image 图片按钮

button 普通按钮 /*实现功能需要指定oneclick事件*/

file 文件域，用于选择上传文件

hidden 隐藏框 /*具体意义？*/

>...

##### 4.3 文本域
```
	<textarea  name="showText"  cols="x"  rows="y">文本内容 </textarea >
	/*样式设置： style="resize:none;" 可固定文本域大小*/
```
##### 4.4 fieldset 和label 标签
```
	<fieldset>
		<legend>表单名</legengd> /*用于制作带标题的边框*/
		<input type="text" >
		...
	</fieldset>
```
```
	<lable for="id">提示文本</label>
		<input type="text" name="gen" value="" id="id" > /*如果在 label 元素内点击文本，就会触发此控件。*/
 ```
>贴士：利用fieldset制作带标题的边框的时候，可以设置margin-style来设置表单名的缩进

##### 4.5 关于列表，表单，div css的综合应用，试试看看第三章练习的内容

		1.[网易邮箱登录页面](https://github.com/wangy325/html-note/blob/master/3-%E8%A1%A8%E5%8D%95/netease.html)
		是对div设计网页的一次大胆探索。
		
		网页设计的过程中对css样式的引用杂乱不堪，既有行内引用，也有基于`.css`样式的外部引用。刚开始，对css还不是很熟练。
		
		2.[阿里巴巴注册页面](https://github.com/wangy325/html-note/blob/master/3-%E8%A1%A8%E5%8D%95/alibaba.html)
		是利用div和table设计网页的代表，这里利用table较为合理地规避了提示信息和表单的对齐问题。
		
		

