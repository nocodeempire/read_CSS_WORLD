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
  content: '...\A..\A.';4.1 深入理解 content 61
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
.father {
  width: 300px; height:150px;
  position: relative;
}
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













