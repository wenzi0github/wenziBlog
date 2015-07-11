```html

<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>一个简单的transition样例</title>
	<style type="text/css">
		ul li{list-style: none;}
		#footer_links {
		    height: 165px;
		}

		#footer_links ul {
		    width: 156px;
		    height: 143px;
		    padding-left: 16px;
		    float: left;
		    zoom:1;overflow: hidden
		}

		#footer_links .linkse {
		    width: 118px
		}

		#footer_links ul li {
		    font-size: 12px;
		    white-space: nowrap;
		    overflow: hidden
		}

		#footer_links ul li a {
		    height: 22px;
		    line-height: 22px;
		    color: #666;
		    display: block;
		    text-decoration: none;
		    transition: transform .4s linear;
		    -moz-transition: transform .4s linear;
		    -webkit-transition: transform .4s linear;
		    -o-transition: transform .4s linear;
		    -ms-transition: transform .4s linear
		}

		#footer_links ul li a:hover {
		    color: #ea1d5d;
		    text-decoration: none;
		    transform: translateX(10px);
		    -moz－transform: translateX(10px);
		    -webkit-transform: translateX(10px);
		    -o-transform: translateX(10px);
		    -ms-transform: translateX(10px)
		}
		#footer_links .links {
		    color: #666;
		    font-size: 14px;
		    font-weight: 700;
		    margin-bottom: 10px;
		    overflow: hidden
		}
	</style>
</head>
<body>
<h2>鼠标放上去试试</h2>
<div id="footer_links">
	<ul class="linksb png">
	    <li class="links">使用帮助</li>
	    <li><a href="#" target="_blank" rel="nofollow">新手指南</a></li>
	    <li><a href="#" target="_blank" rel="nofollow">常见问题</a></li>
	    <li><a href="#" target="_blank" rel="nofollow">帮助中心</a></li>
	    <li><a href="#" target="_blank" rel="nofollow">用户协议</a></li>
	    <li><a href="#" target="_blank" rel="nofollow">企业用户团购</a></li>
	</ul>
</div>
</body>
</html>
```
