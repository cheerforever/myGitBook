# CSS动画

##### CSS Transition 

###### 在CSS 3引入Transition（过渡）这个概念之前，CSS是没有时间轴的。也就是说，所有的状态变化，都是即时完成。

- 指定状态变化所需要的时间

  ```css
  img{
      height:15px;
      width:15px;
  }
  
  img:hover{
      height: 450px;
      width: 450px;
  }
  /*当鼠标移动到img上，图片会立刻放大*/
  
  img{
      /*指定图片放大的过程需要1秒*/
      transition: 1s;  
  }
  
  img{
      /*还可以指定transition适用的属性，比如只适用于height*/
      transition: 1s height;  
  }
  ```

- transition-delay（同一行transition语句中，可以分别指定多个属性）

  delay指定了动画发生的顺序，使得多个不同的transition可以连在一起，形成复杂效果。

  ```css
  img{
      /*width在1秒之后，再开始变化，也就是延迟（delay）1秒*/
      transition: 1s heigth, 1s 1s width;
  }
  ```

- transition-timing-function  

  transition的状态变化速度（又称timing function），默认不是匀速的，而是逐渐放慢，这叫做ease

  ```css
  img{
      transition: 1s ease;
  }
  ```

  属性：

  - ease:逐渐放慢（默认值）
  - linear:匀速
  - ease-in:加速
  - ease-out:减速
  - cubic-bezier函数：自定义速度模式，自定义网站：[工具网站](<https://cubic-bezier.com/#.17,.67,.83,.67>)

  ```css
  img{
      transition: 1s height cubic-bezier(.83,.97,.05,1.44);
  }
  ```

- transition常用钩子

  - transitionend会在transition结束后触发

- transition的各项属性

  ```css
  img{
      /*简写形式*/
      transition: 1s 1s height ease;
  }
  
  img{
      /*各个属性单独定义*/
      transition-property: height;
      transition-duration: 1s;
      transition-delay: 1s;
      transition-timing-function: ease;
  }
  ```

- transition的使用注意

  - IE10都已经支持无前缀的transition
  - 不是所有的CSS属性都支持transition，查看[具体效果](<http://leaverou.github.io/animatable/>)

- transiton的局限性

  - transition需要事件触发，所以没法在网页加载时自动发生

  - transition是一次性的，不能重复发生，除非一再触发

  - transition只能定义开始状态和结束状态，不能定义中间状态

  - 一条transition规则，只能定义一个属性的变化，不能涉及多个属性

    ###### CSS Animation就是为了解决这些问题而提出的

##### CSS Animation

- CSS Animation需要指定动画一个周期持续的时间，以及动画效果的名称

  ```css
  div:hover {
    /*使用名称为rainbow的动画效果*/
    animation: 1s rainbow; 
  }
  /*需要用keyframes关键字，定义rainbow效果*/
  @keyframes rainbow{
    0% { background: #c00; }
    50% { background: orange; }
    100% { background: yellowgreen; }
  }
  ```

  加入infinite关键字，可以让动画无限次播放

  ```css
  div:hover {
    animation: 1s rainbow infinite;
  }
  ```

  也可以规定动画播放次数

  ```css
  div:hover{
    /*播放三次*/
    animation: 1s rainbow 3;
  }
  ```

- animation-fill-mode

  动画结束后会立刻从结束状态调到起始状态。如果想保持在结束状态，需要使用animation-fill-mode属性

  ```css
  div:hover{
      animation: 1s rainbow forwards;
  }
  ```

  - forwards: 动画停留在结束状态
  - none: 默认值，回到动画还没开始的状态
  - backwards: 让动画回到第一帧的状态
  - both: 根据animation-direction轮流应用forwards和backwards规则

- animation-direction

  动画循环播放时，每次都是从结束状态跳回到起始状态，再开始播放。animation-direction属性，可以改变这种行为。

  ```css
  div:hover {
      /*animation-direction默认值为normal*/
    animation: 1s rainbow 3 normal;
  }
  ```

  animation-direction可以取normal、alternate、reverse、alternate-reverse等值。它们的含义见下图（假定动画连续播放三次）

  ![](https://www.ruanyifeng.com/blogimg/asset/201402/bg2014021401.png)

  浏览器对其他值的支持情况不佳，应该慎用。

- animation的各项属性

  ```css
  div:hover {
    animation: 1s 1s rainbow linear 3 forwards normal;
  }
  ```

  ```css
  div:hover {
    animation-name: rainbow;
    animation-duration: 1s;
    animation-timing-function: linear;
    animation-delay: 1s;
    animation-fill-mode:forwards;
    animation-direction: normal;
    animation-iteration-count: 3;
  }
  ```

- keyframes的写法

  keyframes关键字用来定义动画的各个状态，0%可以用from代表，100%可以用to代表

  ```css
  @keyframes rainbow {
    0% { background: #c00 }
    50% { background: orange }
    100% { background: yellowgreen }
  }
  ```

  等同于下面的写法

  ```css
  @keyframes rainbow {
    from { background: #c00 }
    50% { background: orange }
    to { background: yellowgreen }
  }
  ```

  如果省略某个状态，浏览器会自动推算中间状态，所以下面都是合法的写法

  ```css
  @keyframes rainbow {
    50% { background: orange }
    to { background: yellowgreen }
  }
  
  @keyframes rainbow {
    to { background: yellowgreen }
  }
  ```

  浏览器从一个状态向另一个状态过渡，是平滑过渡。steps函数可以实现分步过渡。举个[栗子](<http://dabblet.com/gist/1745856>)

  ```css
  div:hover {
    animation: 1s rainbow infinite steps(10);
  }
  ```

- animation-play-state

  有时，动画播放过程中，会突然停止。如果想让动画保持突然终止时的状态，就要使用animation-play-state属性。

  ```css
  div {
    animation: spin 1s linear infinite;
    /*没有鼠标没有悬停时，动画状态是暂停*/
    animation-play-state: paused;
  }
  
  div:hover {
    /*一旦悬停，动画状态改为继续播放*/
    animation-play-state: running;
  }
  ```

- 浏览器前缀

  IE 10和Firefox（>= 16）支持没有前缀的animation，而chrome不支持，所以必须使用webkit前缀

  实际运用中，代码必须写成下面的样子。

  ```css
  div:hover {
    -webkit-animation: 1s rainbow;
    animation: 1s rainbow;  
  }
  
  @-webkit-keyframes rainbow {
    0% { background: #c00; }
    50% { background: orange; }
    100% { background: yellowgreen; }
  }
  
  @keyframes rainbow {
    0% { background: #c00; }
    50% { background: orange; }
    100% { background: yellowgreen; }
  }
  ```


## 参考资料

[CSS动画简介](<https://www.ruanyifeng.com/blog/2014/02/css_transition_and_animation.html>)