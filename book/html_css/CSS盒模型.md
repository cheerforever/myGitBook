# CSS盒模型

##### CSS盒模型，可以认为每个html标签都是一个方块，然后这个方块又包着几个小方块，如同盒子一层层的包裹着。

> "every element in web design is a rectangular box"

##### 盒模型包括：内容(content) 、内边距(padding)、外边距(margin)、边框(border)。

![](https://user-gold-cdn.xitu.io/2017/10/25/9cb491d4bd5d326aeb16632280411283?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

##### 盒模型主要分为两种：标准盒模型(box-sizing: content-box;)、IE盒模型(box-sizing: border-box)
##### CSS3新增了一种类型：box-sizing: padding-box;

## 盒模型的区别

##### 标准盒模型content-box（默认）
布局所占宽度Width：
```
Width = width + padding-left + padding-right + border-left + border-right
```
布局所占高度Height:
```
Height = height + padding-top + padding-bottom + border-top + border-bottom
```
##### IE盒模型border-box

布局所占宽度Width：
```
Width = width(包含padding-left + padding-right + border-left + border-right)
```
布局所占高度Height:
```
Height = height(包含padding-top + padding-bottom + border-top + border-bottom)
```
##### padding-box
布局所占宽度Width：
```
Width = width(包含padding-left + padding-right) + border-top + border-bottom
```
布局所占高度Height:
```
Height = height(包含padding-top + padding-bottom) + border-top + border-bottom
```

##### 注意：宽度是不包括margin的

## 盒模型使用

##### 我们在编写页面代码时应尽量使用标准盒模型，需要在页面第一行声明DOCTYPE文档类型，就会默认使用标准盒模型了。若不声明DOCTYPE类型，IE浏览器会将盒子模型解释为IE盒子模型。

## margin叠加

外边距叠加是一个相当简单的概念。 但是，在实践中对网页进行布局时， 它会造成许多混淆。 简单的说， 当两个或更多个垂直边距相遇时， 它们将形成一个外边距。这个外边距的高度等于两个发生叠加的外边距的高度中的较大者。但是注意只有普通文档流中块框的垂直外边距才会发生外边距叠加。 行内框、 浮动框或绝对定位框之间的外边距不会叠加。

一般来说， 垂直外边距叠加有三种情况：

- 元素自身叠加 当元素没有内容（即空元素）、内边距、边框时， 它的上下边距就相遇了， 即会产生叠加（垂直方向）。 当为元素添加内容、 内边距、 边框任何一项， 就会取消叠加。
- 相邻元素叠加 相邻的两个元素， 如果它们的上下边距相遇，即会产生叠加。
- 包含（父子）元素叠加 包含元素的外边距隔着 父元素的内边距和边框， 当这两项都不存在的时候， 父子元素垂直外边距相邻， 产生叠加。 添加任何一项即会取消叠加。

## 参考资料

* [CSS盒模型详解](<https://juejin.im/post/59ef72f5f265da4320026f76>)

* [CSS Magic: The Box](<https://adamschwartz.co/magic-of-css/chapters/1-the-box/>)

