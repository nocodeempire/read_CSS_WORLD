# read_CSS_WORLD
读css世界案例记录 部分代码来自《css揭秘》,代码中注解写法仅为了方便阅读而已,不用较真.

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
    background: #f0f0f0 no-repeat center; // 主要是这行和下面的.btn-plus
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
#### 斜45的有背景按钮
````css
.button {
  position: relative;
  /* 其他的文字颜色、内边距等样式…… */
}
.button::before {
  content: ''; /* 用伪元素来生成一个矩形 */
  position: absolute;
  top: 0; right: 0; bottom: 0; left: 0;
  z-index: -1;
  background: #58a;
  transform: skew(45deg);
}
````
直接skew文字也会倾斜, 所以用伪元素生成背景  

#### clip-path
clip-path可以参与动画，只要我们的动画是在同一种形状函数（比如这里是 polygon()）之间进行的，而且点的数量是相同的。 因此， 如果我们希望图片在鼠标悬停时平滑地扩展为完整的面积.
````css
img {
  clip-path: polygon(50% 0, 100% 50%, 50% 100%, 0 50%);
  transition: 1s clip-path;
}
img:hover {
  clip-path: polygon(0 0, 100% 0, 100% 100%, 0 100%);
}
````
#### 折角效果
````css
.box {  //单个折角
  background: #58a; //如果某些浏览器不支持 CSS渐变， 那第二行声明会被丢弃， 而此时我们至少还能得到一个简单的实色背景。
  background: linear-gradient(-45deg, transparent 15px, #58a 0);  //渐变从右下角往上
}
````
````css
background: #58a;
background:
  linear-gradient(135deg, transparent 15px, #58a 0) top left,
  linear-gradient(-135deg, transparent 15px, #58a 0) top right,
  linear-gradient(-45deg, transparent 15px, #58a 0) bottom right,
  linear-gradient(45deg, transparent 15px, #58a 0) bottom left;
background-size: 50% 50%;
background-repeat: no-repeat;
````
#### 弧形切角
````css
background: #58a;
background:
  radial-gradient(circle at top left,transparent 15px, #58a 0) top left,
  radial-gradient(circle at top right,transparent 15px, #58a 0) top right,
  radial-gradient(circle at bottom right,transparent 15px, #58a 0) bottom right,
  radial-gradient(circle at bottom left,transparent 15px, #58a 0) bottom left;
background-size: 50% 50%;
background-repeat: no-repeat;
````
#### 梯形tab栏
尽管优点多多， 但这个技巧也不是完美无缺的。 它存在一个非常大的缺点：斜边的角度依赖于元素的宽度。 因此， 当元素的内容长度不等时， 想要得到斜度一致的梯形就很伤脑筋了。 不过， 对于宽度变化不大的多个元素（比如导航菜单） 来说， 这个方法还是非常管用的。  
````css
nav > a {
  position: relative;
  display: inline-block;
  padding: .3em 1em 0;
}
nav > a::before {
  content: '';
  position: absolute;
  top: 0; right: 0; bottom: 0; left: 0;
  z-index: -1;
  background: #ccc;
  background-image: linear-gradient(
  hsla(0,0%,100%,.6),
  hsla(0,0%,100%,0));
  border: 1px solid rgba(0,0,0,.4);
  border-bottom: none;
  border-radius: .5em .5em 0 0;
  box-shadow: 0 .15em white inset;
  transform: perspective(.5em) rotateX(5deg);
  transform-origin: bottom; // bottom left直角梯形
}
````
#### box-shadow单边投影
box-shadow: 2px 3px 4px rgba(0,0,0,.5);  
(1) 以该元素相同的尺寸1①和位置， 画一个 rgba(0,0,0,.5) 的矩形。  
(2) 把它向右移 2px， 向下移 3px。  
(3) 使用高斯模糊算法（或类似算法） 将它进行 4px 的模糊处理。 这在本质上表示在阴影边缘发生阴影色和纯透明色之间的颜色过渡长度近似于模糊半径的两倍（比如在这里是 8px）。  
(4) 接下来， 模糊后的矩形与原始元素的交集部分会被切除掉， 因此它看起来像是在该元素的“后面”。  

最终的解决方案来自 box-shadow 鲜为人知的第四个长度参数。 它排在模糊半径参数之后， 称作扩张半径。 这个参数会根据你指定的值去扩大或（当指定负值时） 缩小投影的尺寸。 举例来说， 一个 -5px 的扩张半径会把投影的宽度和高度各减少 10px（即每边各 5px）。  
从逻辑上来说， 如果我们应用一个负的扩张半径， 而它的值刚好等于模糊半径， 那么投影的尺寸就会与投影所属元素的尺寸完全一致。 除非用偏移量（前两个长度参数） 来移动它， 我们将完全看不见任何投影。 因此， 如果给投影应用一个正的垂直偏移量， 我们就会在元素的底部看到一道投影， 而元素的另外三侧是没有投影的， 这正是我们一直苦苦追寻的效果：  
box-shadow: 0 5px 4px -4px black;  
<strong>上面这么多话,其实可以理解成: box-shadow第一个参数,水平阴影,正数往右;第二个参数,垂直阴影,正数往下;第三个参数,模糊距离;第四个参数,阴影尺寸,由此参数可以联想到,假设模糊距离是2px,设置阴影尺寸是-2px,则正好抵消模糊.所以水平或者垂直阴影有一个设置的大于模糊距离,而模糊距离等于负的阴影尺寸,那阴影就是单边了.</strong>  
box-shadow: 5px 0 4px -4px black, -5px 0 4px -4px black;  //左右投影
#### 滤镜filter
filter: blur() grayscale() drop-shadow();等, 空格隔开就可以了, 试了下 支持transition过渡,很好玩的. ie不支持,不过不影响使用.渐进增强.  
毛玻璃效果:  
````html
<main>
  <blockquote>
    "The only way to get rid of a temptation[...]"
    <footer>－
      <cite>
        Oscar Wilde,
        The Picture of Dorian Gray
      </cite>
    </footer>
  </blockquote>
</main>
````
````css
body, main::before {
  background: url(图片) 0 / cover fixed;
}
main {
  position: relative;
  background: hsla(0,0%,100%,.3);
  overflow: hidden; // 毛玻璃效果溢出部分隐藏
}
main::before {
  content: '';
  position: absolute;
  top: 0; right: 0; bottom: 0; left: 0;
  filter: blur(20px);
  margin: -30px; // 正值的话毛玻璃接近border区域会清晰
}
````
#### 斑马条纹
在表格中,我们可以根据nth-child(even)奇偶行来直接设置. 但如果是文字呢,大段大段的文字. 这里的思路是直接大背景用渐变实现.
````css
padding: .5em;  // 文字在盒子中是有0.5的padding的
line-height: 1.5;
background: beige; //不连写在background中是为了支持不支持渐变的远古时代浏览器,这样,起码背景色还是存在的
background-size: auto 3em;
background-origin: content-box; // 所以此处背景色是从content-box开始的
background-image: linear-gradient(rgba(0,0,0,.2) 50%, transparent 0); 
````
这个方法总体来说是十分灵活的， 唯一可能破坏效果的情况②可能就是在改变 line-height 时忘了相应地调整 background-size。

#### 用某款字体中的特定某个字
````css
@font-face {
font-family: tang;
src: local('LiSu'),  // local用于指定本地字体的名称, 这样不会像使用src一样会产生请求
    local('KaiTi'),
    local('SimHei'),
    local('Microsoft Yahei');
    unicode-range: U+5510; // unicode-range是基于“Unicode 码位”的. 
    //可以这么做"唐".charCodeAt(0).toString(16); 返回5510; 这样你就得到了字符的十六进制码位，然后需要在码位前面加上 U+ 作为前缀。 
    //如果你想指定一个字符区间， 还是要加上 U+ 前缀， 比如 U+400-4FF。实际上对于这个区间来说， 你还可以使用通配符， 以这样的方式来写：U+4??。 
    //同时指定多个字符或多个区间也是允许的， 把它们用逗号隔开即可，比如 U+26, U+4??, U+2665-2670。 
}
body {
  font-family: tang, Microsoft Yahei, SimHei;
}
````
#### 下划线的几种实现
````css
a { /* 1 */
  text-decoration: underline; 
}
a { /* 2 */
  border-bottom: 1px solid gray;
  text-decoration: none;
}
a { /* 3 这个效果是因为觉得线太靠下面 所以减小行高往上 */
  display: inline-block;
  border-bottom: 1px solid gray;
  line-height: .9;
} 
a { /* 4 */
  box-shadow: 0 -1px gray inset;
}
a { /* 5 */
  background: linear-gradient(gray, gray) no-repeat;
  background-size: 100% 1px;
  background-position: 0 1.15em;
}
a { /* 6 虚线 */
  background: linear-gradient(90deg, gray 66%, transparent 0) repeat-x;
  background-size: .2em 2px;
  background-position: 0 1em;
}
/* 未来不必这么麻烦,有新属性 
 text-decoration-color 用于自定义下划线或其他装饰效果的颜色。
 text-decoration-style 用于定义装饰效果的风格（比如实线、虚线、波浪线等）。
 text-decoration-skip 用于指定是否避让空格、字母降部或其他对象。
 text-underline-position 用于微调下划线的具体摆放位置。
*/
````
#### checkbox美化
原理其实是用label替代;
````html
<input type="checkbox" id="awesome" />
<label for="awesome">Awesome!</label>
````
````css
input[type="checkbox"] + label::before {
  content: '\a0'; /* 不换行空格 */
  display: inline-block;
  vertical-align: .2em;
  width: .8em;
  height: .8em;
  margin-right: .2em;
  border-radius: .2em;
  background: silver;
  text-indent: .15em;
  line-height: .65;
}
input[type="checkbox"]:checked + label::before {
  content: '\2713'; /* 代表是 √ */
  background: yellowgreen;
}
/* 复选框以一种不损失可访问性的方式隐藏起来。 这意味着不能使用 display: none， 因为那样会把它从键盘 tab 键切换焦点的队列中完全删除。 */
input[type="checkbox"] {
  position: absolute;
  clip: rect(0,0,0,0);
}
/* 还能更加美化效果,比如在聚焦或者禁用时改变其样式, 甚至可以用过渡或动画来让各个状态之间的切换更加平滑 */
input[type="checkbox"]:focus + label::before {
  box-shadow: 0 0 .1em .1em #58a;
}
input[type="checkbox"]:disabled + label::before {
  background: gray;
  box-shadow: none;
  color: #555;
}
````
#### 模态框(背景虚化)
````html
<main>这里将成为背景虚化的大容器</main>
<dialog>
  这是弹出框,但存在兼容性问题,实际项目建议直接用一个div代替吧.
</dialog>
<button>按钮</button>
````
````css
main {
  transition: .6s filter;
}
main.de-emphasized {  /* js为其添加类名 */
  filter: blur(3px) contrast(.8) brightness(.8);
}
````
````js
var but = document.querySelector("button");
var dialog = document.querySelector("dialog");
but.onclick = function() {
  main.className = "de-emphasized";
  dialog.showModal();
}
````
如果不需要虚化的话其实还有一种实现思路,那就是增加弹出框的outline,这样的话只需要一层标签就能实现.

#### animation动画
就摘录一个例子. 是一个正方形的容器中有一张很长的图片,鼠标悬浮上去的时候图片滚动,移开的时候暂停.
````css
@keyframes panoramic {
  to { background-position: 100% 0; }
}
.panoramic {
  width: 150px; height: 150px;
  background: url("img/naxos-greece.jpg");
  background-size: auto 100%;
  animation: panoramic 10s linear infinite alternate;
  animation-play-state: paused; /* 动画一直存在 只是一开始是暂时的 */
}
.panoramic:hover, .panoramic:focus {
  animation-play-state: running;
}
````
#### 多列等高
````html
<div class="web_width">
  <div class="left"></div>
  <div class="right"></div>
</div>
````
````css
.web_width{
  width: 100%;
  overflow: hidden;			//关键所在
}
.left{
  float: left;
  width: 20%;
  min-height: 10em;
  background: #66afe9;
  padding-bottom: 2000px;		//关键所在
  margin-bottom: -2000px;		//关键所在
}
.right{
  float: right;
  width: 80%;
  height: 20em;
  background: #f00;
}
````






















# 追求卓越的道路是永无止境的！
