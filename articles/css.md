# CSS3学习笔记

                                                    --张静

---

### 1、边框属性

 - border-radius 设置边框圆角
 - box-shadow   box-shadow: h-shadow v-shadow blur spread color inset;
| 值       |描述 |
| --------   | -----:  | :----:  |
| h-shadow   |   必需。水平阴影的位置。允许负值。  |
|  v-shadow  |   必需。垂直阴影的位置。允许负值。   |
| blur       |   可选。模糊距离。  |
| spread     |   可选。阴影的尺寸。  |
| color      |   可选。阴影的颜色。请参阅 CSS 颜色值。  |
| inset      |   可选。将外部阴影 (outset) 改为内部阴影  |
 -  border-image 创建图片边框

### 2、背景

 - 多重背景的设置
```
body
{ 
background-image:url(bg_flower.gif),url(bg_flower_2.gif);
}
```

### 3、文本

 - text-overflow 规定文本溢出包含元素是发生的事儿
 - text-shadow 向文本添加阴影
 - word-wrap 允许对长的不可分割的单词进行分割并换行到下一行。

### 4、2D/3D转换

 - translate()：元素根据left和top的值从当前位置移动(2D/3D)
 - rotate()：元素顺时针旋转给定的角度。允许负值，元素将逆时针旋转。(2D/3D)
 - scale()：元素的尺寸会增加或减少，根据给定的宽度（X 轴）和高度（Y 轴）参数(2D/3D)
 - skew():元素翻转给定的角度，根据给定的水平线（X 轴）和垂直线（Y 轴）参数(2D/3D)
 - matrix()(2D/3D)
 - rotate3d(x,y,z,angle)

### 5、过渡：规定希望效果添加的css属性及时长

```
body
{ 
transition-property: width;//属性名称
transition-duration: 1s;//过渡效果所花时间
transition-timing-function: linear;//过渡的时间曲线 默认“ease”
transition-delay: 2s;//过渡效果何时开始 默认0
//简写 transition: width 1s linear 2s;
/* Firefox 4 */
-moz-transition-property:width;
-moz-transition-duration:1s;
-moz-transition-timing-function:linear;
-moz-transition-delay:2s;
/* Safari 和 Chrome */
-webkit-transition-property:width;
-webkit-transition-duration:1s;
-webkit-transition-timing-function:linear;
-webkit-transition-delay:2s;
/* Opera */
-o-transition-property:width;
-o-transition-duration:1s;
-o-transition-timing-function:linear;
-o-transition-delay:2s;
}
```

### 6、动画 @keyframes规则

```
body
{ 
animation-name: myfirst; 
animation-duration: 5s;
animation-timing-function: linear;
animation-delay: 2s;
animation-iteration-count: infinite;
animation-direction: alternate;
animation-play-state: running;
//简写 animation: myfirst 5s linear 2s infinite alternate;
/* Firefox: */
-moz-animation-name: myfirst;
-moz-animation-duration: 5s;
-moz-animation-timing-function: linear;
-moz-animation-delay: 2s;
-moz-animation-iteration-count: infinite;
-moz-animation-direction: alternate;
-moz-animation-play-state: running;
/* Safari 和 Chrome: */
-webkit-animation-name: myfirst;
-webkit-animation-duration: 5s;
-webkit-animation-timing-function: linear;
-webkit-animation-delay: 2s;
-webkit-animation-iteration-count: infinite;
-webkit-animation-direction: alternate;
-webkit-animation-play-state: running;
/* Opera: */
-o-animation-name: myfirst;
-o-animation-duration: 5s;
-o-animation-timing-function: linear;
-o-animation-delay: 2s;
-o-animation-iteration-count: infinite;
-o-animation-direction: alternate;
-o-animation-play-state: running;
}
```
 - css动画手册（http://isux.tencent.com/css3/index.html） 除了基本的动画效果，还可以自定义一些动画
 - animate.css  一些现成的css动画效果

### 7、多列布局

 - column-count
 - column-gap
 - column-rule

### 8、box-sizing

### canvas 画图    fabric框架 fabricjs.com 

```
<!-- 初始化环境：引入需要的js脚本 -->
<script type="text/javascript" src="third-party/fabric_static.js"></script>

<!-- 创建一个画布  -->
<canvas id="contentCanvas" width="130" height="300"></canvas>
```
```
// 用fabric实例化画布  
var notesCanvas = new fabric.StaticCanvas('contentCanvas');

// 设置画布大小 
 notesCanvas.setWidth(canvasWidth);//设置画布的宽
 notesCanvas.setHeight(canvasHeight);//设置画布的高
 notesCanvas.calcOffset();//设置偏移量
 
//清除画布
 notesCanvas.clear();
 
// 连接两点画线
function drawLine(canvas, beginX,beginY, endX, endY, fillColor) {
    var line = new fabric.Line([beginX,beginY,endX, endY], {
        stroke: fillColor,//设置线颜色
        strokeWidth: 4,//设置线的粗细
        selectable: false //当设置为“false”时，不能选择对象进行修改（使用点按点或基于组的选择）。但事件仍在对象上。
    })          
    // 画线
    canvas.add(line);
}
//将图片设置为背景   
notesCanvas.setBackgroundImage('../assets/bkg.jpg');

//用上面的方法实现，得在画布内点击一次后，才会将图片设置为背景，原因是，在渲染画布时，图片还咩有加载完成，所以通过以下方法，在图片加载时再设置背景
function initBgImg(){
	var img = new Image();
	img.onload = function(){
		notesCanvas.setBackgroundImage(img.src, notesCanvas.renderAll.bind(notesCanvas), {
	        originX: 'left',
	        originY: 'top',
	        width: notesCanvas.width,
  			height: notesCanvas.height,
	        left: 0,
	        top: 0
	    });
	};

    img.src = '../assets/img/answer.jpg'
}

//对画布的监听（添加操作和选中）
notesCanvas.on({
	    'object:selected': function(e) {
	     
	    },
	    'object:added': function(e) {
	    }
	  });
```
 

--- 
 
 - nth-child() 可以传参  odd even 或者数字等, 用来实现隔行换色
 - [name="n"]  属性选择器, 可以是任意属性, 非常方便


 


