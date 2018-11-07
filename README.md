# 一个序列帧素材网站
http://www.aigei.com/  爱给网

# 实现canvas绘图区域中特定图形绕自身旋转
比如 canvas宽高600px 600px
如何实现一个长方形绕着自身左上角定点旋转 长方形 rect(100,100,200,200)

```
window.onload= function () {
  var canvas = document.getElementById('canvas');
  var ctx = canvas.getContext('2d');

  ctx.save(); // 开始保存状态 save和restore成对出现 
  ctx.fillStyle = 'red';
  ctx.fillRect(0,0,100,100); // 此长方形仅仅用于测试
  ctx.restore(); // 保存状态结束 释放状态

  ctx.save(); // 开始保存状态 save和restore成对出现 
  // 第一步移动原点至100 100位置
  ctx.translate(100, 100);
  // 第二步 然后旋转坐标轴
  ctx.rotate(Math.PI / 4);

  ctx.fillStyle = 'green';
  // 第三步 在经过移动和旋转的坐标轴上绘制长方形 注意 此时长方形的起始坐标值是0 0
  ctx.fillRect(0,0,100,100);
  ctx.restore(); // 释放控制权 释放后此次所有对坐标轴的操作都失效 回复至原始状态

}
```
