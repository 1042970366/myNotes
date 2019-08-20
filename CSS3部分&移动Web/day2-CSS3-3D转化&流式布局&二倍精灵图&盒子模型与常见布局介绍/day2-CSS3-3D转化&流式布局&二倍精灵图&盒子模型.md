# day2-CSS3-3D转化&流式布局&二倍精灵图&盒子模型

## 一	3D转化

### 1	3d位移转化

```css
/* transform: translateX(200px); */
/* transform: translateY(100%); */
/* transform: translateZ(100px); */
/* Z轴没有厚度，设置%不生效 */
/* transform: translateZ(100000000000%); */
/* 简写 */
transform: translate3d(100px, 100px, 100px);
```

### 2	视距

语法：

```css
perspective: 1000px;
```

- 加在谁上面：

  - 加在body：下面所有子元素，形成统一的透视感；
  - 加在各自父亲上：管理下面的子元素形成各自的透视感；

- 值的大小：值越小，变化越剧烈；

  



### 3	旋转

语法：绕着哪个轴，左手工具：一定要把大拇指朝向自己眼睛，其他手指弯曲的方向就是顺时针方向 

```cs
  /* 左手工具*/
  /* transform: rotateX(45deg); */
  /* transform: rotateY(45deg); */
  /* transform: rotateZ(45deg); */
  /* 自定义轴线 */
  transform: rotate3d(1, 1, 0, 45deg);
```
### 4	3D呈现

语法：

```css
transform-style: preserve-3d;
```

- 区别：
  - 视距：
    - **近大远小**，透视感；
    - body所有的子元素、各自父亲；观测角度不同；
  - 3D呈现：
    - **亲生子元素3D转化，可呈现出来**
    - **父亲上加；**



### 5	3D缩放

```css
      /* transform: scaleX(2); */
      /* transform: scaleY(0.5); */
      /* Z轴方向没有厚度，不生效 */
      /* transform: scaleZ(10000); */
      /* 合起来简写 */
      transform: scale3d(2, 2, 10000000);
```





## 二	流式布局

### 1	介绍

- 内核：webkit

- 屏幕分辨率：碎片化；

  



### 2	viewport

```css
<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
/*
width=device-width：设置HTML宽度为设备宽度；
user-scalable=no是否允许用户自定义缩放
initial-scale=1.0初始化缩放比
maximum-scale=1.0, minimum-scale=1.0 最大最小缩放比
*/
```

### 3	屏幕尺寸+物理像素点+屏幕分辨率

- 屏幕尺寸：绝对单位，到哪都不会变的单位；

- 物理像素点：客观存在的点，可以发光；做的越来越小，画面越来细腻；一个萝卜一个坑；

- 屏幕分辨率：水平和垂直方向上物理像素点的个数；

  



### 4	图片分辨率 CSS像素

- 图片分辨率：水平和垂直颜色点；
- CSS像素：
  - 设置200px，在每个屏幕显示都是一样大；
  - 在640分辨率，自动算出需要提供400个物理像素点；



### 5	二倍图命名

UI命名：

- 图名1@2x.png：二倍图
- 图名1@3x.png：三倍图





### 6	background-size

```css
  /* 图片没有设置大小，会按照自己的分辨率显示 */
      background: url('./imgs/dog.jpg') no-repeat;

      /* 两个参数设置背景图片大小 ,按照设置进行显示，不一定保证比例*/
      /* background-size: 100px 100px; */
      /* 一个固定值px，设置宽度，高度自适应 */
      /* background-size: 400px; */
      /* % :相对于当前盒子的宽度*/
      /* background-size: 50%; */

      /* 关键字 cover:覆盖，绝对不留白*/
      /* background-size: cover; */
      /* contain:包含,绝对要显示全我的图片 */
      /* background-size: contain; */
```

### 7	二倍精灵图的使用

- 步骤：

  - 先等比所小图的一半，在缩小的的图内进行图标位置测量；
  - 引入图，按照刚才的测量，写入图标的坐标；
  - 设置 图片大小：按照缩小一半后的宽高 进行 设置的；

- 注意：**测量完成后，图片不需保存；**

  



### 8	CSS3盒子模型

```css
/* 传统：盒子的宽度 = CSS中设置的width + border + padding */
box-sizing: content-box;

/* CSS3盒子模型:盒子的宽度=就是设置的width，宽度里面包含了 border 和 padding  怪异盒模型 IE盒模型*/
box-sizing: border-box;/*简单说，不随border和padding来改变盒子宽度*/
```

