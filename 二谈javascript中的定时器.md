二谈javascript中的定时器，文章地址：[http://www.xiabingbao.com/javascript/2015/04/20/javascript-timer](http://www.xiabingbao.com/javascript/2015/04/20/javascript-timer/)

时间间隔为0时
```javascript
function get(){
	var timer = null;
	var date = null;
	var diff = 0;
	var last = 0;
	var now = 0;
	var nums = 0;
	var color = '#000';
	var process = document.getElementById("process");
	timer = setInterval(function(){
		date = new Date();
		now = date.getTime();
		diff = now-last; // 前后两个时间差
		last = now;
		nums++;
		color = diff===0?'#f00':'#000';
		process.innerHTML += '<p>'+now+' (<span style="color:'+color+'">'+diff+'</span>)</p>';

		if(nums>=100){
			clearInterval(timer);
		}
	}, 0);
}
get();
```

标签页处于可见和不可见状态时的时间间隔：
```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>js中的定时器</title>
    <style type="text/css">
        .title{width: 500px; margin: 20px auto;}
        .title span:nth-child(1){font-size: 20px;font-weight: bold;}
        .title span:nth-child(2){float: right; margin-top: 4px;}
        .title a{color: #00f; font-size: 16px;}
        .title a:hover{color: #ec2b8c;}
        .content{border: 1px solid #aaa;width: 468px;padding: 14px;margin: 0 auto;position: relative;}
        .content .stop{position: absolute; top: 12px;right: 20px; z-index: 2;}
        .content .stop input{padding: 4px 14px;}
        .process{ max-height: 600px;overflow: auto;}
    </style>
</head>
<body>
<div class="title">
    <span>二谈javascript中的定时器</span>
    <span><a href="/javascript/2015/04/20/javascript-timer/" target="_self">返回到文章</a></span>
</div>
<div class="content">
    <div class="stop"><input type="button" id="stop" value="停止"></div>
    <div id="process" class="process"></div>
</div>
</body>
<script type="text/javascript">
    function get(){
        var timer = null;
        var date = null;
        var diff = 0;
        var last = 0;
        var now = 0;
        var nums = 0;
        var color = '#000';
        var process = document.getElementById("process");
        timer = setInterval(function(){
            date = new Date();
            now = date.getTime();
            diff = now-last;
            last = now;
            nums++;
            color = diff===0?'#f00':'#000';
            process.innerHTML += '<p>'+now+' (<span style="color:'+color+'">'+diff+'</span>)</p>';

            if(nums>=100){
                clearInterval(timer);
            }
        }, 0);
    }
    // get();

    // 标题闪动
    function blinkTile(title, timeout){
        var self = this;
        var timer = null;
        var backup = document.title;
        var last = 0;
        var process = document.getElementById("process");

        self.init = function(title, timeou){
            if(title != undefined){
                self.title = title;
            }
            self.timeout = timeout == undefined? 500: timeout;
        }

        self.start = function(){
            self.stop();

            function blink(){
                document.title = document.title == backup? self.title : backup;
                self.check();
            }
            blink();
            timer = setInterval(blink, self.timeout);
        }



        self.stop = function(){
            if(timer != null){
                document.title = backup;
                clearInterval(timer);
                timer = null;
            }
        }


        // 打印时间差，同时让滚动条在最下边
        self.check = function(){
            var date = new Date();
            var now = date.getTime();
            var diff = now-last;
            last = now;
            process.innerHTML += '<p>'+now+' ('+diff+')</p>';
            process.scrollTop = process.scrollHeight;
        }

        self.init(title, timeout);
    }
    var blink = new blinkTile('【新消息】', 500);
    blink.start();

    // 标签页的可见状态
    var hidden, state, visibilityChange;
    if (typeof document.hidden !== "undefined") {
        hidden = "hidden";
        visibilityChange = "visibilitychange";
        state = "visibilityState";
    } else if (typeof document.mozHidden !== "undefined") {
        hidden = "mozHidden";
        visibilityChange = "mozvisibilitychange";
        state = "mozVisibilityState";
    } else if (typeof document.msHidden !== "undefined") {
        hidden = "msHidden";
        visibilityChange = "msvisibilitychange";
        state = "msVisibilityState";
    } else if (typeof document.webkitHidden !== "undefined") {
        hidden = "webkitHidden";
        visibilityChange = "webkitvisibilitychange";
        state = "webkitVisibilityState";
    }

    var process = document.getElementById("process");
    var stop = document.getElementById('stop');
    // 添加监听器，在title里显示状态变化
    document.addEventListener(visibilityChange, function() {
        if(document[state]=="hidden"){
            process.innerHTML += '<p style="color:#f00;">====== 离开  ======</p>';
        }else{
            process.innerHTML += '<p style="color:#f00;">++++++ 回来  ++++++</p>';
        }
    }, false);

    stop.addEventListener('click', function(){
        if(this.value == '停止'){
            blink.stop();
            this.value = '开始';
        }else{
            blink.start();
            this.value = '停止';
        }
        
    })
</script>
</html>
```
