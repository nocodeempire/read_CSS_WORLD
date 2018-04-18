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
