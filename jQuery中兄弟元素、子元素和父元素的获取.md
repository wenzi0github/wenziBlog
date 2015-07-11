jQuery中兄弟元素、子元素和父元素的获取，文章地址：[http://www.xiabingbao.com/jquery/2015/01/10/jquery-ergodic](http://www.xiabingbao.com/jquery/2015/01/10/jquery-ergodic/)

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>jQuery的元素选择</title>
	<style type="text/css">
		body{font-family: Helvetica,Arial,"Microsoft Yahei",sans-serif;}
		.clearfix:after {content: "\00A0";display: block;visibility: hidden;width: 0;height: 0;clear: both;font-size: 0;line-height: 0;overflow: hidden;}
		.selected{border:1px solid #ec2b8c !important;}
		.title{width: 1100px; margin: 20px auto;}
		.title span:nth-child(1){font-size: 20px;font-weight: bold;}
		.title span:nth-child(2){float: right;}
		.title a:hover{color: #ec2b8c;}
		.main{border: 1px solid #ccc; max-width: 1090px; padding: 10px; margin: 0 auto;}
		.manager{float: left; width: 640px;}
		.manager fieldset{margin-top: 10px;}
		.manager .list{margin: 10px;}
		.manager a{text-decoration: none;color: #aaa;border: 1px solid #ccc;padding: 4px 6px;display: block;float: left;margin: 0 10px 6px 0;}
		.manager a:hover{color: #ec2b8c;}
		.content{width: 420px; float: left; border: 1px solid #ccc; margin: 10px;}
		.content div{border: 1px solid #ccc; margin: 10px;}
		.content .list{height: 50px;}
		.content .item{width: 100px; height: 100px; float: left;}
		.content .item .s{height: 18px;}
		.content .current{text-align: center;line-height: 100px; border: 1px solid #5C2BEC;}
	</style>
</head>
<body>
<div class="title">
	<span>jQuery中兄弟元素、子元素和父元素的获取</span>
	<span><a href="http://www.xiabingbao.com/jquery/2015/01/10/jquery-ergodic/" target="_self">返回到文章</a></span>
</div>
<div class="main clearfix">
	<div class="manager">
		<fieldset>
			<legend>父节点</legend>
			<div class="list">
				<a href="javascript:;" id="parent">直接父节点</a>
				<a href="javascript:;" id="parents">所有父节点</a>
			</div>
		</fieldset>
		<fieldset>
			<legend>兄弟节点</legend>
			<div class="list">
				<a href="javascript:;" id="prev">上一个兄弟节点</a>
				<a href="javascript:;" id="prevAll">前面所有兄弟节点</a>
				<a href="javascript:;" id="next">下一个兄弟节点</a>
				<a href="javascript:;" id="nextAll">后面所有兄弟节点</a>
				<a href="javascript:;" id="siblings">所有的兄弟节点</a>
			</div>
		</fieldset>
		<fieldset>
			<legend>子节点</legend>
			<div class="list">
				<a href="javascript:;" id="children">直接子节点</a>
				<a href="javascript:;" id="childAll">所有子节点</a>
			</div>
		</fieldset>
		<fieldset>
			<legend>清除</legend>
			<div><a href="javascript:;" id="clear">清除样式</a></div>
		</fieldset>
	</div>
	<div class="content">
		<div class="bingo">
			<div class="list"></div>
			<div class="list"></div>

			<div class="current clearfix">
				<div class="item">
					<div class="s"></div>
					<div class="s"></div>
					<div class="s"></div>
				</div>
				<div class="item">
					<div class="s"></div>
					<div class="s"></div>
					<div class="s"></div>
				</div>
				<div class="item">
					<div class="s"></div>
					<div class="s"></div>
					<div class="s"></div>
				</div>
			</div>
			<div class="list"></div>
			<div class="list"></div>
		</div>
	</div>
</div>
</body>
<script type="text/javascript" src="http://code.jquery.com/jquery-2.1.2.min.js"></script>
<script type="text/javascript">
	var Common = {
		// 清除被选中的样式
		clear : function(){
			$("body div").each(function(index, el) {
				$(el).hasClass('selected') && $(el).removeClass('selected');
			});
		},

		// 为$obj添加被选中样式
		chosen : function($obj){
			this.clear();
			$obj.addClass('selected');
		}
	}

	var $current = $(".current");
	$("#clear").click(function(event) {
		Common.clear();
	});

	$("#parent").click(function(event) {
		Common.chosen($current.parent());
	});

	$("#parents").click(function(event) {
		Common.chosen($current.parents('div'));
	});

	$("#prev").click(function(event) {
		Common.chosen($current.prev());
	});

	$("#prevAll").click(function(event) {
		Common.chosen($current.prevAll());
	});
    
    $("#next").click(function(event) {
		Common.chosen($current.next());
	});
    
    $("#nextAll").click(function(event) {
		Common.chosen($current.nextAll());
	});
    
    $("#siblings").click(function(event) {
		Common.chosen($current.siblings());
	});
    
    $("#nextAll").click(function(event) {
		Common.chosen($current.nextAll());
	});

	$("#children").click(function(event) {
		Common.chosen($current.children());
	});

	$("#childAll").click(function(event) {
		Common.chosen($current.find('div'));
	});
</script>
</html>
```
