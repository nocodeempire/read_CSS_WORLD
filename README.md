# read_CSS_WORLD
读css世界案例记录

#### 正在加载...效果
```html
正在加载中<dot>...</dot>
```
```css
dot {
  display: inline-block;
  height: 1em;
  line-height: 1;
  text-align: left;
  vertical-align: -.25em;
  overflow: hidden;
}
dot::before {
  display: block;
  content: '...\A..\A.';
  white-space: pre-wrap;
  animation: dot 3s infinite step-start both;
}
@keyframes dot {
  33% { transform: translateY(-2em); }
  66% { transform: translateY(-1em); }
}
```
 #### 凹凸效果
 ```css
.ao, .tu{
  width: 0;
  display: inline-block;
  margin: 50px
}
.tu{
  direction:rtl;
}
.ao:after{
  content: 'love 你 love';
  outline: 2px solid red;
  color: #fff
}
.tu:after{
  content: '你 love 你';
  outline: 2px solid red;
  color: #fff;
}
 ```
 #### 分隔符号 
 登录 | 注册
 ```html
<a href="">登录</a><a href="">注册</a>
```
 ```css
 a {
  padding: .25em 0;
}
a + a:before {
  content: "";
  font-size: 0;
  padding: 10px 3px 1px;
  margin-left: 6px;
  border-left: 1px solid gray;
}
 ```
#### 实心圆外面一个圈的实现效果
```css
  display: inline-block;
  width: 10px;
  height: 10px;
  padding: 1px;
  border: 1px solid;
  border-radius: 50%;
  background-color: currentColor;
  /* background-clip  设置元素的背景（背景图片或颜色）是否延伸到边框下面。 */
  background-clip: content-box;   
```
#### 三条横线实现效果
```css
/* 实现原理是高度10的一个容器,着色 上下padding10px,画上下边框线, 设置background-clip: content-box只影响内容的背景色 */
.icon-menu {
  display: inline-block;
  width: 140px; height: 10px;
  padding: 35px 0;
  border-top: 10px solid;
  border-bottom: 10px solid;
  background-color: currentColor;
  background-clip: content-box;
}
/* 方法2 */
.icon-menu {
  width: 120px;
  height: 20px;
  border-top: 60px double;
  border-bottom: 20px solid;
}
```

#### 其他
```html
我们这里的各类“尺寸”命名和对应的盒子类型全部参考自 jQuery 中与尺寸相关 API 的名称。
• 元素尺寸：对应 jQuery 中的$().width()和$().height()方法，包括 padding
和 border，也就是元素的 border box 的尺寸。在原生的 DOM API 中写作 offsetWidth
和 offsetHeight，所以，有时候也成为“元素偏移尺寸”。
• 元素内部尺寸：对应 jQuery 中的$().innerWidth()和$().innerHeight()方法，
表示元素的内部区域尺寸，包括 padding 但不包括 border，也就是元素的 padding
box 的尺寸。在原生的 DOM API 中写作 clientWidth 和 clientHeight，所以，
有时候也称为“元素可视尺寸”。
• 元素外部尺寸：对应 jQuery 中的$().outerWidth(true)和$().outerHeight
(true)方法，表示元素的外部尺寸，不仅包括 padding 和 border，还包括 margin，
也就是元素的 margin box 的尺寸。没有相对应的原生的 DOM API。
```
#### 更好的水平垂直居中的例子
```css
.son {
  position: absolute;
  top: 0; right: 0; bottom: 0; left: 0;
  width: 200px; height: 100px;
  margin: auto;
}
```
#### 图片上传图形 田---绘制
┌ ┬ ┐
├ ┼ ┤
└ ┴ ┘
```html
<a href="" class="add" title="添加图片">添加图片</a>
```
```css
.add{
    display: inline-block;
    width: 100px;
    height: 100px;
    color: #ccc;
    border: 2px dashed;
    position: relative;
    text-indent: -12em;
    overflow: hidden;
}
.add:before, .add:after {
    content: '';
    position: absolute;
    border: 2px solid;

}
.add:before {
    width: 30px;
    top: 49px;
    left: 35px;
}
.add:after {
    height: 30px;
    top: 35px;
    left: 49px;
}
.add:hover{
    color: salmon;
}
```
#### 朝下的三角 ▼
```css
div {
  width: 0;
  border-width: 10px 15px;  /* 只设置一个的话是等腰直角三角形 */
  border-style: solid;
  border-color: #f30 transparent transparent;
}
```
#### 多行文本垂直居中
```html
<div class="box">
  <div class="content">基于行高实现的...</div>
</div>
```
```css
.box {
  line-height: 120px; /* 设置line-height使得box中元素居中 */
  background-color: #f0f3f9;
}
.content {
  display: inline-block;
  line-height: 20px;
  margin: 0 20px;
  vertical-align: middle;  /* 设置vertical-align: middle使得content元素middle居中 */
}
```
#### 模态框水平垂直居中
```html
<div class="container">
    <div class="dialog">
        <div class="content">内容占位</div>
    </div>
</div>
```
```css
.container {
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    /* for IE8 */
    background: background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAABtJREFUeNpiZGBgaGAgAjAxEAlGFVJHIUCAAQDcngCUgqGMqwAAAABJRU5ErkJggg==);
    /* for IE9+ */
    background: rgba(0, 0, 0, .5), none;
    text-align: center;
    white-space: nowrap;
    z-index: 99;
}
.container:after {
    content: "";
    display: inline-block;
    height: 100%; /* 更改百分比可以灵活控制垂直居中的比例 */
    vertical-align: middle;
}
.dialog {
    display: inline-block;
    vertical-align: middle;
    border-radius: 6px;
    background-color: #fff;
    text-align: left;
    white-space: normal;
}
```
#### 获取滚动高度
在 PC 端，窗体滚动高度可以使用 document.documentElement.scrollTop 获取，
但是在移动端，可能就要使用 document.body.scrollTop 获取。

#### 滚动条问题
```text
滚动栏占据宽度的特性最大的问题就是页面加载的时候水平居中的布局可能会产生晃动，因为窗体默认是没有滚动条的，
而 HTML 内容是自上而下加载的，就会发生一开始没有滚动条，后来突然出现滚动条的情况，此时页面的可用宽度发生变化，水平居中重新计算，导致页面发生晃动，
这个体验是非常不好的. 下面css基本完美解决这个问题.
```
```css
html {
  overflow-y: scroll; /* for IE8 */
}
:root {
  overflow-y: auto;
  overflow-x: hidden;
}
:root body {
  position: absolute;
}
body {
  width: 100vw;
  overflow: hidden;
}
```
#### 滚动条样式
滚动条是可以自定义的。因为 IE 浏览器的自定义效果实在是比原生的还要难看，
倒是支持-webkit-前缀的浏览器可以说说
```css
::-webkit-scrollbar { /* 血槽宽度 */
  width: 8px; height: 8px;
}
::-webkit-scrollbar-thumb { /* 拖动条 */
  background-color: rgba(0,0,0,.3);
  border-radius: 6px;
}
::-webkit-scrollbar-track { /* 背景槽 */
  background-color: #ddd;
  border-radius: 6px;
}
```
#### 对于absolute新的认知
如果没有给其父元素设定定位,absolute其实是占据自身的位置,不写任何tlrb等,直接margin等操作,即可实现位置变换, 下面例子是文字右上角hot图标
```css
.icon-hot {
  position: absolute;
  margin: -6px 0 0 2px;
  width: 28px; height: 11px;
  background: url(hot.gif);
}
```
#### 让网页字体跟随系统字体
```css
html { font: menu; }
body { font-size: 16px; }
html { font: small-caption; }
body { font-size: 16px; }
html { font: status-bar; }
body { font-size: 16px; }
```
#### 双fixed 公司经常用 就写了个demo记录下
````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        *{
            padding: 0;
            margin: 0;
            list-style: none;
        }
        .container{
            padding: 50px 0 0 0;
        }
        .fixhead{
            width: 100%;
            height: 50px;
            background-color: pink;
            position: fixed;
            top: 0;
        }
        .bgc{
            background-color: salmon;
            width: 100%;
            height: 150px;
        }
        .nav{
            display: flex;
            line-height: 50px;
        }
        .nav a {
            flex: 1;
            background-color: #eee;
            text-align: center;
        }
        .libgc {
            width: 100%;
            height: 150px;
        }
        .libgc:nth-child(2n) {
            background-color: cyan;
        }
        .libgc:nth-child(2n+1) {
            background-color: lightblue;
        }
        .fix {
            position: fixed;
            top: 50px;
            width: 100%;
        }
        .paddingbottom{
            padding: 50px 0 0 0;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="fixhead"></div>
        <div class="bgc"></div>
        <div class="nav">
            <a href="#">导航1</a>
            <a href="#">导航2</a>
            <a href="#">导航3</a>
        </div>
        <ul>
            <li class="libgc"></li>
            <li class="libgc"></li>
            <li class="libgc"></li>
            <li class="libgc"></li>
            <li class="libgc"></li>
            <li class="libgc"></li>
            <li class="libgc"></li>
        </ul>
    </div>
</body>
<script src="../node_modules/jquery/dist/jquery.min.js"></script>
<script>
    $(document).scroll(function(){
        console.log($(document).scrollTop());
        if($(document).scrollTop() >= $('.bgc').height()){
            $('.nav').addClass('fix');
            $('ul').addClass('paddingbottom');
        } else {
            $('.nav').removeClass('fix');
            $('ul').removeClass('paddingbottom');
        }
    })
</script>
</html>
````
#### 酷炫---粘滞融合效果
http://www.zhangxinxu.com/wordpress/2017/12/svg-filter-fuse-gooey-effect/
````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .demo svg {
            position: absolute;
        }
        .target {
            height: 120px; max-width: 200px;
            filter: url("#goo");
            text-align: center;
            position: relative;
        }
        .share {
            display: block;
            width: 64px; line-height: 64px;
            background-color: #cd0000;
            color: #fff;
            border-radius: 50%;
            margin: auto;
            position: relative;
            z-index: 1;
        }
        [type="checkbox"] {
            position: absolute;
            clip: rect(0 0 0 0);
        }
        [class*="icon-share-"] {
            position: absolute;
            width: 48px; height: 48px;
            background-color: #cd0000;
            border-radius: 50%;
            transition: transform .5s;
            top: 8px; left: 0; right: 0;
            margin: auto;
            -ms-transform: scale(0.5);
            transform: scale(0.5);
        }
        [class*="icon-share-"] > img {
            display: block;
            width: 20px;
            height: 20px;
            margin: 14px auto;
        }
        :checked + .target .icon-share-weibo {
            -ms-transform: scale(1) translate(-70px, 60px);	
            transform: scale(1) translate(-70px, 60px);	
        }
        :checked + .target .icon-share-wechat {
            -ms-transform: scale(1) translate(0, 75px);	
            transform: scale(1) translate(0, 75px);	
        }
        :checked + .target .icon-share-qq {
            -ms-transform: scale(1) translate(70px, 60px);
            transform: scale(1) translate(70px, 60px);	
        }
        :checked + .target .share {
            animation: jello 1s;
        }
        @keyframes jello {
          from, 11.1%, to {
            transform: none;
          }
          22.2% {
            transform: skewX(-12.5deg) skewY(-12.5deg);
          }
          33.3% {
            transform: skewX(6.25deg) skewY(6.25deg);
          }
          44.4% {
            transform: skewX(-3.125deg) skewY(-3.125deg);
          }
          55.5% {
            transform: skewX(1.5625deg) skewY(1.5625deg);
          }
          66.6% {
            transform: skewX(-0.78125deg) skewY(-0.78125deg);
          }
          77.7% {
            transform: skewX(0.390625deg) skewY(0.390625deg);
          }
          88.8% {
            transform: skewX(-0.1953125deg) skewY(-0.1953125deg);
          }
        }
        </style>
</head>
<body>
    <div class="demo">
        <svg width="0" height="0">
          <defs>
            <filter id="goo">
              <feGaussianBlur in="SourceGraphic" stdDeviation="10" result="blur" />
              <feColorMatrix in="blur" mode="matrix" values="1 0 0 0 0  0 1 0 0 0  0 0 1 0 0  0 0 0 19 -9" result="goo" />
              <feComposite in="SourceGraphic" in2="goo" operator="atop"/>
            </filter>
          </defs>
        </svg>
        <input type="checkbox" id="share">
        <div class="target">
            <label class="share" for="share">分享</label>
            <span class="icon-share-weibo"><img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAAC9UlEQVRYR92WgVEUUQyG/1SgVCBUoFQgVqBWIFSgVuBZgViBUAFQgVCBRwVCBUIFcb6dZCf77h17zJzDjJnZudvdty9//vxJnumJzZ7Yv/4/AO7+XNIHSfxiN5KuzWzZY3vrDLj7J0nfOs4AsjCz0/ruXwDYlXRcGMDf6+L0xMyO8n7rAHo0uzugDiV9ifcjiI0BxCYfJb2K61LS115uGx1A/YWZ3bk7IH4EiDdmdjkLIBzz0UEvr2a21z7v6OBOEg6X7n4SIl2a2f6DANz9XSBORfcY3m9ZCNALSVAPY88kAQKw7PU7NtpbC8DdERKUz9kO9OYi6G/voxQBcWRmJ+5OWl4MrKwRTdI05/xC0s9IDymqTJ2HQ3LP/7ehmYW7ox8qYxXAIyKfA8f7z2Z2XBzmfZ+BRqWbOJhbQ5UQMepHT/xWDeyMKQjh/GpoTAf3kqAR5NCXliUJ/eS0tZ5AAUBbvjSzwwog81I3uYr2WZ12o46KQbgVCJVAuaGVrg0AOtQTMX2bDUcLlnBwa2awsWKlzus71r7vNa0EUKPH+UFdHNHRRqE8rTtcIqBUfQUx9IFaory0iCobA88GpeaXGwhzMlwCAA2o7pnbTfZOAAiIWsbuzWys5Q64YQ3pkcTYzXwT2SQlpdlUFoaqqA9goM7vKzMbe767szgnGHOcyIYOJumspGQlMndH6S8bkcwy0ALIXCIg/iPYXn7btMHin45GV5hKESIQevVNnW4l/8PoDAC9Nj3ZuGEucZxS9y2oBFDTMAyMcEYkOPbIO1UwyWH29yJa1tDQqqGb3bYCBhGWDzOycXYHCDakKuqxahRjUzHoB23UobRS1hMR1pumiRDp90Tt7gDJiYfiz8s7xIlYW4rppIfrmtaEgcIETmADtcMGouPiaD2UWhy5UDigGDLtaek2OumQyofsoQNJTi+c9AZNu+916AVmZmdHfjx7JoyIoZgLy2ip8zwJMXDGU9Fc1Gs18JgPt7V2Iwa25ay3z5MD+AvEbGYRoqDXHQAAAABJRU5ErkJggg=="></span>
            <span class="icon-share-wechat"><img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAACoElEQVRYR8WX4XEUMQyFnyoAKuBSAbkKgAqACshVQFIBoQKSCkgqIFcBXAWhA5IKuFQg5tuxb4zPXq/3bgb9XVl6epaevKb/bNbK7+7PJb2T9EbSIvPfSvopaWNmv1qxSt+rANydhJ9D4imxHyRdSlqbGcAm2R6AUPH3jsR5IpJ/MDOYado/ANz9VNIPSdB+qF2Z2UUryA5AJfmTpDtJAHtVCYbPjaT3kl5mPjdmthoDMQAItP8uVL6MzeXuAKEZUyP5It65u0P768xnZWYALFoEUAouM0sZosFoytTofpp1MHcv+dATJ7XGNHdntKi+ZG9jM1Wq48zAUmDxvjCq+Fyb2XkpAQCuJH0auSdoBWSuAfEIFaIBYz4PZnZSA1C6t7G+mftt109pABiggmdzo3ac211nDsA7gtRc47jCJooYlRA94WpoVHRhT64PZeAR+WXMgo4wgiSLQtbcFQCY2wNrSWch4deRJo2sUf0XM2PkdwYAxoMAPXYriXPfggL2nAUA4jRcEwCgi3ub2oixcnYGEo2NyTHXRFLYijlgg6bcRiUsKVipKhKRFP+PiQPb7y4U8yc7+IJE7g4AGIs2iFMqtbCQL5McxHWohupTG/S+EwDnlymAKc24DHefVk+g2O2wkysmhUF5Oh0R/G0KoKkHLCd3J1htNfc0I76bOQCaQHtQxCbMN+ImPDKIxbgNFQcGjindTxEA90NjMd97khma65TVXHmY9BSd+q7TFxEVNl+zhXGam5xzq+Z/QR49sEEjtka2BezRzBbdAIgaFg9jO1U9S2AG8ZoFIIDgFcxjcy6IwwAEEEwPIPKXcIt+vrMZL2czkGYIv3FxNee9EZdR/L9grPE5HoBCoyLJWzNDhvfM3bk+xvo4DEzhu+bzF2tWF6oPbpt7AAAAAElFTkSuQmCC"></span>
            <span class="icon-share-qq"><img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAYAAABzenr0AAAB+0lEQVRYR8WX4VECMRCF36tArUCpQKxAqECpQK1ArEA7UCoQOsAKhArEDrADrWCdd5PcAHe5XCCnO8Mvstkvm82+PSLBzOwYwBWAawBnAPrOfQVAvwXJWcKWYNvFZqagrwAE0WRrAA8k5232bgVgZlMAN2023FgzJjmJ+UQBzOwJwGNso8D/ysRLk28jgJkNALzvGVxu3wAuSOpaai0GsABweQCAXGckb5MBzEwV/nFgcO9+QlLZqFgwA2Y2BvCcCeCOpAo5CSBH+n3ACUkd6N8AliRV0EkAlin92mZNstcaIHMBNhZibRGamZrHfcYMaKvaphQCyFmA/hxvJKUnW1YBcOlX94uJTmqC1A1HJKWapW0BdBjcB6y05l0A0Z2nHi1xvWaGofcpAcxM/Vp6/xdWdsZNAN3R6V9Ed5NTkYUCoKN3HztLTzLtAQ4ZOmKBQv8XfcEDdPHuY2BFX6gD+OqwFn4AHDmyQqB2ATRSKxtdvYaRG+k14G5lQNNP3w8NZtbFiygl2Q076gerkBbkHMeUcaV+sNuGy2dYVy2ZR7IhSV1txUIZyN0VpQF6dpW5MKSGuabh3RMXzSeohnt0xaWT7bYCpo+UsBx7spbfgp8qLAeg+43pSO1k3PRdoM1VC3oR/oRqUjrBfPM+3We71spH6z2MILV+GirCX0O+wiEpSANxAAAAAElFTkSuQmCC"></span>
        </div>
    </div>
</body>
</html>
````
#### 图片旋转
由于rotate IE是不支持的, 所以最好的选择还是用canvas
或者插件 jQuery图片旋转插件jQueryRotate.js
````html
<canvas id="cv"></canvas>
<img id="cvImg" width="128" height="96" src="mm1.jpg" />
````
````js
window.onload = function(){
    var canvas = document.getElementById("cv");
    var oImg = document.getElementById("cvImg");
    // 旋转后canvas标签的大小
    canvas.height = 128;
    canvas.width = 96;
    // 绘图开始
    var context = canvas.getContext("2d");
    context.save();
    // 改变中心点
    context.translate(96,0);
    // 旋转90°
    context.rotate(Math.PI/2);
    // 绘制
    context.drawImage(oImg, 0, 0, 128, 96);
    context.restore();
    oImg.style.display = "none";
};
````
#### 视图 scroll offset等参数详解
http://www.zhangxinxu.com/wordpress/2011/09/cssom%E8%A7%86%E5%9B%BE%E6%A8%A1%E5%BC%8Fcssom-view-module%E7%9B%B8%E5%85%B3%E6%95%B4%E7%90%86%E4%B8%8E%E4%BB%8B%E7%BB%8D/
#### 隐藏非静音的、自动播放的 video
这是个用户
自定义样式的小技巧。避免了当页面加载时，自动播放有声音的 video 来干扰用户。如果是非静音的，就不显示 video：
````css
video[autoplay]:not([muted]) {
  display: none;
}
````
#### 逗号分隔的列表
````css
ul > li:not(:last-child)::after {
  content: ",";
}
````
#### 统一的垂直结构
在一个元素内使用通用选择器来创建一致的垂直结构：
````css
.intro > * {
  margin-bottom: 1.25rem;
}
````
#### 加载效果<img src="http://www.zhangxinxu.com/study/201305/loading-css3.gif" width="32" height="32">
````html
<div class="loading spin"></div>
````
````css
.loading {  // 需要看一下兼容性
    width: 3px; height:3px;
    border-radius: 100%;                      /* 圆角 */
    box-shadow: 0 -10px 0 1px #333,           /* 上, 1px 扩展 */
                10px 0px #333,                /* 右 */
                0 10px #333,                  /* 下 */
                -10px 0 #333,                 /* 左 */

                -7px -7px 0 .5px #333,        /* 左上, 0.5px扩展 */
                7px -7px 0 1.5px #333,        /* 右上, 1.5px扩展 */
                7px 7px #333,                 /* 右下 */
                -7px 7px #333;                /* 左下 */
}
.spin {
    animation: spin 1s steps(8) infinite;
}
@keyframes spin {
    from {transform: rotate(0deg);}
      to {transform: rotate(360deg);}
}
````
#### 图片预加载与懒加载思路
````text
预加载: 字面意思就是预先加载, 判断用户行为预先加载. 例子是:三栏切换的案例,假设用户hover到第二个tab栏了,就加载第二个tab栏中的项目,这样在hover到mouseup这段时间,数据已经加载成功了,直接展示.防止了可能出现的空白.
懒加载: 最常见的就是图片懒加载了.
参考:http://www.zhangxinxu.com/wordpress/2016/06/image-preload-based-on-user-behavior/
````
#### 千位分隔符
````html
方法一：使用正则表达式
String(Number).replace(/(\d)(?=(\d{3})+$)/g, "$1,");  // Number
方法二：使用toLocaleString()方法
Number.toLocaleString('en-US');
// 对于中文场景下，toLocaleString('en-US')中的'en-US'理论上是可以缺省的，也就是直接(123456789).toLocaleString()也是可以得到123,456,789。
// 但是如果你的产品可能海外用户使用，则保险起见，还是保留'en-US'。
// 另外，对于IE edge之前的版本，Number.toLocaleString()会自动补上两位小数，如果是不需要的，需要自己额外过滤掉。
````
#### 订单甲减的效果
````html
<a href="javascript:" class="btn btn-plus" role="button" title="增加"></a>
````
````css
.btn {
    display: inline-block;
    background: #f0f0f0 no-repeat center; // 主要是这行和下面的.
    border: 1px solid #d0d0d0;
    width: 24px; height: 24px;    
    border-radius: 2px;
    box-shadow: 0 1px rgba(100,100,100,.1);
    color: #666;
    transition: color .2s, background-color .2s;
}
.btn-plus {
    background-image: linear-gradient(to top, currentColor, currentColor), linear-gradient(to top, currentColor, currentColor);
    background-size: 10px 2px, 2px 10px;
}
.btn:active {
    box-shadow: inset 0 1px rgba(100,100,100,.1);
}
.btn:hover {
    background-color: #e9e9e9;
    color: #333;
}
````

