# 行内元素与块元素

## 一	行内元素与块级元素概括

**块级元素：div 	 p 	  form  	ul 	 li   	ol  	dl   	address	 fieldset	hr**	

**menu	table**

**行内元素：**

**span	strong	em	br	img	input	label	select	textarea	cite**

## 二	详细

行内元素： ；

a	b	big	br	cite	code	em	i	img	input	label

s	select	small	span	strong	sub	sup	textarea	u

块元素：

address	center	dir	div	dl fieldset	form	h1-h6	hr	ol	

p	table	ul	li	

三	行内元素与块元素的区别：

1	从显示效果来看

- [x] 块级元素会独占一行，其宽度自动填满父元素宽度

- [x] 行内元素不会独占一行，相邻的行内元素会排列在同一行里，知道一行排不下，

  才会换行，其宽度随元素的内容而变化

2         块级元素可以设置width，height属性，行内元素设置width，height无效

**【注意：块级元素及时设置了宽度，仍然是独占一行的】**	

​	

3	块级元素可以设置margin和padding，行内元素的水平方向的padding-left，padding-right，margin-left，margin-right都产生边距效果，但是竖直方向的padding-top，padding-bottom,margin-top，margin-bottom都不会产生边距效果。（水平方向有效，竖直方向无效）

