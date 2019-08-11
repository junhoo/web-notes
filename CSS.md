- BFC
>  浮动元素和绝对定位元素，非块级盒子的块级容器,以及overflow值不为`visiable`的块级盒子,都会为他们的内容创建新的BFC（块级格式上下文）。

```

<p>block布局存在高度塌陷，即block布局不会考虑float元素的大小</p>
<P>float元素很大时，会出现float元素溢出容器</P>
<div id="box">
  <div id="item-1">A 触发bfc不溢出</div>
  <div id="item-2">B 触发碰到边缘</div>
</div>

#box {
  display: block;
  display: flow-root;

  width: 300px;
  border: 1px solid red;
  background: #000;
  font-size: 15px;
}

#item-1 {
  float: left;
  width: 120px;
  height: 100px;
  background: orange;
  margin-right: 10px;
}

#item-2 {
  display: flow-root;

  width: 120px;
  height: 50px;
  background: skyblue;
}
```