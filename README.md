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
