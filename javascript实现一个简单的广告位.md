javascript实现一个简单的广告位，文章地址：[http://www.xiabingbao.com/javascript/2015/01/31/javascript-ad](http://www.xiabingbao.com/javascript/2015/01/31/javascript-ad/)

```javascript
;(function(){
    var jumeiForU = {
        // 初始化
        init : function(_config){
            this.config = this.extend(this.config, _config);
            this.show();
        },
        // 广告展示及跳转链接
        data : [
            {'title':'九朵云祛斑霜', 'img':'http://p0.jmstatic.com/g/300x250/ht150122p854446t1.jpg', 'url':'http://www.jumeiglobal.com/deal/ht150122p854446t1.html?referer='},
            {'title':'Guerisson奇迹马油24K金面膜贴', 'img':'http://p0.jmstatic.com/g/300x250/ht150122p1293256t1.jpg', 'url':'http://www.jumeiglobal.com/deal/ht150122p1293256t1.html?referer='},
            {'title':'Its-skin晶钻蜗牛面膜', 'img':'http://p0.jmstatic.com/g/300x250/ht150122p818496t1.jpg', 'url':'http://www.jumeiglobal.com/deal/ht150122p818636t1.html?referer='},
            {'title':'九朵云美白祛斑气垫BB霜', 'img':'http://p0.jmstatic.com/g/300x250/ht150122p1293254t1.jpg', 'url':'http://www.jumeiglobal.com/deal/ht150122p1293254t1.html?referer='},
            {'title':'可莱丝NMF水库针剂睡眠面膜5片', 'img':'http://p0.jmstatic.com/g/300x250/ht150122p1312153t1.jpg', 'url':'http://www.jumeiglobal.com/deal/ht150122p1312153t1.html?referer='},
            {'title':'猪皮面膜', 'img':'http://p0.jmstatic.com/g/300x250/ht150122p1254465t1.jpg', 'url':'http://www.jumeiglobal.com/deal/ht150122p1254465t1.html?referer='},
            {'title':'奇迹马油精华套装', 'img':'http://p0.jmstatic.com/g/300x250/ht150122p1293257t1.jpg', 'url':'http://www.jumeiglobal.com/deal/ht150122p1293257t1.html?referer='},
            {'title':'九朵云美白祛斑套组', 'img':'http://p0.jmstatic.com/g/300x250/ht150122p1293255t1.jpg', 'url':'http://www.jumeiglobal.com/deal/ht150122p1293255t1.html?referer='},
            {'title':'晶钻蜗牛修护睡眠面膜', 'img':'http://p0.jmstatic.com/g/300x250/ht150122p818636t1.jpg', 'url':'http://www.jumeiglobal.com/deal/ht150122p818496t1.html?referer='},
            {'title':'skin1004僵尸面膜', 'img':'http://p0.jmstatic.com/g/300x250/ht150122p1265333t1.jpg', 'url':'http://www.jumeiglobal.com/deal/ht150122p1265333t1.html?referer='}
        ],
        // 配置
        config : {
            start : '2015/01/01 00:00',
            end : '2030/01/01 00:00',
            width : 300,
            height : 250
        },
        // 广告展示
        show : function(){
            var nowtime = (new Date()).getTime(),
                starttime = (new Date(this.config.start)).getTime(),
                endtime = (new Date(this.config.end)).getTime(),
                random = this.getRandom(),
                referer = this.getCurrentScript('referer');
            if(nowtime>=starttime && nowtime<endtime){
                document.write('<div style="position:relative; padding:0; margin:0; width:'+this.config.width+'px; height:'+this.config.height+'px"><a href="'+this.data[random].url+referer+'" target="_blank"><img src="'+this.data[random].img+'" alt="" style="width:'+this.config.width+'px; height:'+this.config.height+'px; border:0;" /></a></div>');
            }
        },
        // 返回当前需要展示的广告代号
        getRandom : function(){
            return Math.floor(Math.random()*this.data.length);
        },
        extend : function(destination, source) {
            for (var property in source) {
                destination[property] = source[property];
            }
            return destination;
        },
        // 获取referer的值
        getCurrentScript : function(name){
            var i = 0,
                result = null,
                script, scripts, url, reg, r;
            
            // firefox支持currentScript属性
            if( document.currentScript ){
                script = document.currentScript
            }
            else{
                // 正常情况下，在页面加载时，当前js文件的script标签始终是最后一个
                scripts = document.getElementsByTagName( 'script' )            
                script = scripts[ scripts.length - 1 ]
            }           
            url = script.hasAttribute ? script.src : script.getAttribute( 'src', 4 );
            reg = new RegExp("(^|&|\\?)" + name + "=([^&]*)(&|$)", "i");
            r = url.substr(1).match(reg);
            if (r !== null && r !==""){
                result = decodeURIComponent(r[2]);
            }
            return result===""? null: result;
        }
    }
    jumeiForU.init();
})(window);
```
