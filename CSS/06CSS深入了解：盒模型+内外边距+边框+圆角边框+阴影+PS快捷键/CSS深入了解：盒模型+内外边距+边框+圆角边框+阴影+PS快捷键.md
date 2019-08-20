# CSS深入了解：盒模型+内外边距+边框+圆角边框+阴影+PS快捷键+透明度

## 1	盒子模型（CSS重点）

> css可以归为三大模块：盒子模型、浮动、定位。其余的都是细节问题，所以这三大模块，一定要搞明白
>
> 言归正传，所谓盒子模型：把HTML页面中的布局元素看作是一个矩形的盒子，也就是一个盛装内容的容器。每个矩形都由元素的内容区域、内边距（padding）、边框（border）和外边距（margin）组成。

进入正题：

盒模型由外边距（margin），边框（border），内边距（padding），内容区域（content）四部分组成

![1564626841578](images/盒子.png)

- 所有的文档元素（标签）都会生成一个矩形框，我们成为元素框（element box），
- 它描述了一个文档元素再网页布局汇总所占的位置大小。
- 每个盒子除了有自己大小和位置外，还影响着其他盒子的大小和位置。

![1564626905282](images/盒子模型.png)

### a	盒子边框	border

​	边框就像水果皮，自己想象一下，橘子皮

```
border : border-width || border-style || border-color border : border-width || border-style || border-color 
```

边框属性—设置边框样式（border-style）

边框样式用于定义页面中边框的风格，常用属性值如下：

- none：没有边框即忽略所有边框的宽度（默认值）
- solid：边框为单实线(最为常用的)
- dashed：边框为虚线  
- dotted：边框为点线
- double：边框为双实线

### 盒子边框写法总结表

|              |                                                              |                                                              |
| ------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 设置内容     | 样式属性                                                     | 常用属性值                                                   |
| 上边框       | border-top-style:样式; border-top-width:宽度;border-top-color:颜色;border-top:宽度 样式 颜色; |                                                              |
| 下边框       | border-bottom-style:样式;border- bottom-width:宽度;border- bottom-color:颜色;border-bottom:宽度 样式 颜色; |                                                              |
| 左边框       | border-left-style:样式; border-left-width:宽度;border-left-color:颜色;border-left:宽度 样式 颜色; |                                                              |
| 右边框       | border-right-style:样式;border-right-width:宽度;border-right-color:颜色;border-right:宽度 样式 颜色; |                                                              |
| 样式综合设置 | border-style:上边 [右边 下边 左边];                          | none无（默认）、solid单实线、dashed虚线、dotted点线、double双实线 |
| 宽度综合设置 | border-width:上边 [右边 下边 左边];                          | 像素值                                                       |
| 颜色综合设置 | border-color:上边 [右边 下边 左边];                          | 颜色值、#十六进制、rgb(r,g,b)、rgb(r%,g%,b%)                 |
| 边框综合设置 | border:四边宽度 四边样式 四边颜色;                           |                                                              |

### 提一句：

表格的细线边框：

```
table{ border-collapse:collapse; }  
```

> collapse 单词是合并的意思

> border-collapse:collapse; 表示相邻边框合并在一起。

```html
<style>
	table {
		width: 500px;
		height: 300px;
		border: 1px solid red;
	}
	td {
		border: 1px solid red;
		text-align: center;
	}
	table, td {
		border-collapse: collapse;  /*合并相邻边框*/
	}
</style>
```

展示：

![1564627338900](images/table.png)

### b	内边距	padding

padding属性用于设置内边距。 **是指 边框与内容区域之间的距离。**

- padding-top:上内边距
- padding-right:右内边距
- padding-bottom:下内边距
- padding-left:左内边距



#### padding后边有几个属性值表现形式是不一样的

| 值的个数 | 表达意思                                                     |
| -------- | ------------------------------------------------------------ |
| 1个值    | padding：上下左右边距 比如padding: 3px; 表示上下左右都是3像素 |
| 2个值    | padding: 上下边距 左右边距 比如 padding: 3px 5px; 表示 上下3像素 左右 5像素 |
| 3个值    | padding：上边距 左右边距 下边距 比如 padding: 3px 5px 10px; 表示 上是3像素 左右是5像素 下是10像素 |
| 4个值    | padding:上内边距 右内边距 下内边距 左内边距 比如: padding: 3px 5px 10px 15px; 表示 上3px 右是5px 下 10px 左15px 顺时针 |

> 提一句：
>
> padding会撑开盒子大小
>
> 但是，如果没有给一个块元素指定宽度，此时，如果给这个块元素指定左右的padding，则不会撑宽盒子。



#### 内盒尺寸计算（元素实际大小）

  Element Height = height + padding + border （Height为内容高度）

  Element Width =  width + padding + border （Width为内容宽度）

  盒子的实际的大小 =   内容区域的宽度或高度 +  内边距   +  边框    



### c	外边距	margin

margin属性用于设置外边距。  margin就是控制盒子和盒子之间的距离

- margin-top:上外边距
- margin-right:右外边距
- margin-bottom:下外边距
- margin-left:左外边距

margin:上外边距 右外边距  下外边距  左外边

取值顺序跟内边距相同。

#### 外边距实现块元素居中

可以让一个块元素实现水平居中，需要满足一下两个条件：

1. 必须是块级元素。     
2. 盒子必须指定了宽度（width）
3. 然后就给**左右的外边距都设置为auto**，就可使块级元素水平居中。

实际工作中常用这种方式进行网页布局，示例代码如下：

```css
.header{ width:960px; margin:0 auto;}
```

### 文字盒子居中图片和背景区别

1. 文字水平居中是  text-align: center
2. 盒子水平居中  左右margin 改为 auto 

```
text-align: center; /*  文字居中水平 */
margin: 10px auto;  /* 盒子水平居中  左右margin 改为 auto 就阔以了 上下margin都可以 */
```

3. 插入图片 我们用的最多 比如产品展示类  移动位置只能靠盒模型 padding margin
4. 背景图片我们一般用于小图标背景 或者 超大背景图片  背景图片 只能通过  background-position

### 清除元素的默认内外边距

为了更方便地控制网页中的元素，制作网页时，可使用如下代码清除元素的默认内外边距： 

```css
* {
   padding:0;         /* 清除内边距 */
   margin:0;          /* 清除外边距 */
}
```

注意：  

- 行内元素为了照顾兼容性， 尽量只设置左右内外边距， 不要设置上下内外边距。

> 提一句：
>
> 外边距合并：使用margin定义块元素的垂直外边距时，可能会出现外边距的合并。
>
> ### 相邻块元素垂直外边距的合并
>
> 当上下相邻的两个块元素相遇时，如果上面的元素有下外边距margin-bottom，下面的元素有上外边距margin-top，则他们之间的垂直间距不是margin-bottom与margin-top之和，而是两者中的较大者。这种现象被称为相邻块元素垂直外边距的合并（也称外边距塌陷）。
>
> ![1564629053532](images/margin.png)
>
> 解决方案：  避免就好了。
>
> ### 嵌套块元素垂直外边距的合并
>
> 对于两个嵌套关系的块元素，如果父元素没有上内边距及边框，则父元素的上外边距会与子元素的上外边距发生合并，合并后的外边距为两者中的较大者，即使父元素的上外边距为0，也会发生合并。
>
> ![1564629107723](images/hebing.png)
>
> **解决方案：**
>
> 1. 可以为父元素定义1像素的上边框或上内边距。
> 2. 可以为父元素添加overflow:hidden。
>
> 待续。。。。

 盒子模型布局稳定性

开始学习盒子模型，最大的困惑就是， 分不清内外边距的使用，什么情况下使用内边距，什么情况下使用外边距？

答案是：  其实他们大部分情况下是可以混用的。  就是说，你用内边距也可以，用外边距也可以。 你觉得哪个方便，就用哪个。

但是，总有一个最好用的吧，我们根据稳定性来分，建议如下：

按照 优先使用  宽度 （width）  其次 使用内边距（padding）    再次  外边距（margin）。   

```
width >  padding  >   margin   
```

原因：

1. margin 会有外边距合并 还有 ie6下面margin 加倍的bug（讨厌）所以最后使用。 不过现在基本很少见ie6了
2. padding  会影响盒子大小， 需要进行加减计算（麻烦） 其次使用。
3. width   没有问题（嗨皮）我们经常使用宽度剩余法 高度剩余法来做。



## 2	PS快捷键

- 文件--打开 --  可以打开 我们要测量的图片
- ctrl+r 可以打开标尺  或者  视图 --  标尺
- 右击标尺，  把里面的单位改为  像素  
- ctrl+ + 键  可以 放大  视图  ctrl+ -  缩小视图
- 按住空格键，  可以 变成小手 ，拖动 ps 视图
- 工具条   窗口-工具
- 用选区 拖动  可以 测量 大小 
- ctrl+ d  可以取消选区

## 3   css3	部分属性



#### 圆角边框（css3） radius 半径（距离）

```
border-radius: 1-4 length|% / 1-4 length|%;
```

```
border-radius: 50%;   让一个正方形  变成圆圈
```

原理就是 原点到半径相同，就可以画一个圆圈。

```
div
{
border:2px solid;
border-radius:25px;
}
```

#### 盒子阴影(CSS3)

```
box-shadow: h-shadow v-shadow blur spread color inset;
```

```
box-shadow:水平阴影 垂直阴影 模糊距离（虚实）  阴影尺寸（影子大小）  阴影颜色  内/外阴影；

div
{
box-shadow: 10px 10px 5px #888888;
}
```

![1564630269147](images/shadow)

1. 前两个属性是必须写的。其余的可以省略。
2. 外阴影 (outset) 但是不能写    默认      想要内阴影  inset 



#### 透明的设置（css3） 可用作遮挡，轮播图的暗度

##### 1.rgba()   设置单颜色的透明

a代表alpha，透明范围是0-1,0可以省略掉

##### 2.opacity 设置元素整体透明

设置的是整体的透明度  范围是0-1

> 提一句：
>
> 区别：
>
> rgba（）指对设置该属性的盒子背景透明，对盒子内的内容没有影响
>
> opacity	对整体设置，盒子背景与盒子内的元素像文字等都有透明影响