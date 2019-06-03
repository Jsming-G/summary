# 常用的方法

[canvas API 参考地址](https://developer.mozilla.org/zh-CN/docs/Web/API/Canvas_API)

```javascript
var canvas = document.getElementById(‘canvas');
var ctx = canvas.getContext(‘2d’)
// 矩形
ctx.fillRect(100,100,200,60);
// 圆形 弧形
ctx.beginPath();
ctx.arc(100,75,50,0, 2*Math.PI)
ctx.stroke();
ctx.closePath();
// 笔触 描边
ctx.strokeStyle = 'red'; // 红色边框
ctx.strokeRect(100,100,200,60);
ctx.fill();
// 线  多边形
ctx.beginPath();
ctx.moveTo(100,100);
ctx.lineTo(300,300);
ctx.closePath(); // 闭合
ctx.strokeStyle = 'blue';
ctx.stroke(); // 划线
ctx.fillStyle = 'red'; // 填充颜色
ctx.fill();
// 清屏
ctx.clearReact(x,y,w,h);
// 贝塞尔曲线
ctx.beginPath();
ctx.moveTo(x,y);
ctx.quadraticCurveTo(x1,y1,x2,y2);
// ctx.quadraticCurveTo(x1,y1,x2,y2,x3,y3);
ctx.stroke();
// 画图片
ctx.drawImage(image,x,y); // 更多参考API
ctx.drawImage(image,x,y,w,h,x1,y2,w1,h1);// 图片裁剪位置大小,和画布中显示的位置大小

ctx.save(); // 保存
ctx.translate(x,y); // 坐标原点发生改变 平移
ctx.rotate(1); // 坐标原点发生改变 旋转
ctx.restore(); // 复原

```

> 1px的线条很粗的问题 <br>
> 如:画(3,1）到（3,5）会出现模糊,解决办法是在定位的时候平移半个像素就可以; <br>
> 所以改为:(3.5,1）到（3.5,5）就不会模糊了
