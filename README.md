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




















