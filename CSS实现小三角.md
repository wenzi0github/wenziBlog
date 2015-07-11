CSS实现小三角，文章地址：[http://www.xiabingbao.com/css/2015/02/14/css-arrow](http://www.xiabingbao.com/css/2015/02/14/css-arrow/)

```html
<div style="display:block;margin:10px;width:30px;height:30px;border-style:solid;border-width:20px;border-color:#f00 #00f #0f0 #f0f;background-color:#fff"></div>
```

把div的width和height都设为0
```html
<div style="display:block;margin:10px;width:0;height:0;border-style:solid;border-width:20px;border-color:#f00 #00f #0f0 #f0f;background-color:#fff"></div>
```

4个三角形，而气泡只需要一个！怎么办？把不需要的边框设置为透明
```html
<div style="display:block;margin:10px;width:0;height:0;border-style:solid;border-width:20px;border-color:transparent #00f transparent transparent;"></div>
```

两个三角形叠在一起
```html
<div style="position:relative;display:block;width:50px;height:50px;">
    <div style="display:block;position:absolute;left:10px;top:10px;width:0;height:0;border-style:solid;border-width:20px;border-color:transparent #00f transparent transparent;"></div>
    <div style="display:block;position:absolute;left:16px;top:10px;;width:0;height:0;border-style:solid;border-width:20px;border-color:transparent #fff transparent transparent;"></div>
</div>
```
