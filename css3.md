## css动画：[css动画](https://www.w3school.com.cn/css3/css3_animation.asp)
### flex布局

> Flex布局以后，子元素的float、clear和vertical-align属性将失效。
- 容器的属性：

1. flex-direction属性决定主轴的方向（即项目的排列方向）flex-direction: row | row-reverse | column | column-reverse
2. flex-wrap属性定义，如果一条轴线排不下，如何换行。flex-wrap: nowrap | wrap | wrap-reverse
3. flex-flow属性是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap；flex-flow: <flex-direction> <flex-wrap>
4. justify-content属性定义了项目在主轴上（相当于y轴）的对齐方式。justify-content: flex-start | flex-end | center | space-between | space-around
align-items属性定义项目在交叉轴（相当于x轴）上如何对齐。align-items: flex-start | flex-end | center | baseline | stretch
5. align-content属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。align-content: flex-start | flex-end | center | space-between | space-around | stretch

> 项目的属性：

1. order属性定义项目的排列顺序。数值越小，排列越靠前，默认为0；order: <integer>;
2. flex-grow属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。如果所有项目的flex-grow属性都为1，则它们将等分剩余空间（如果有的话）。如果一个项目的flex-grow属性为2，其他项目都为1，则前者占据的剩余空间将比其他项多一倍。
3. flex-shrink属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小；如果所有项目的flex-shrink属性都为1，当空间不足时，都将等比例缩小。如果一个项目的flex-shrink属性为0，其他项目都为1，则空间不足时，前者不缩小。
4. flex-basis属性定义了在分配多余空间之前，项目占据的主轴空间（mainsize）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小，可选值："auto"、"inherit" 或一个后跟 "%"、"px"、"em" 或任何其他长度单位的数字。
- flex 属性是 flex-grow、flex-shrink 和 flex-basis 属性的简写属性。
- flex: 100 200 300px;➡️flex-grow: 100; flex-shrink: 200;flex-basis: 300px;//赋给3个值
- flex: auto;➡️flex-grow: 1; flex-shrink: 1; flex-basis: auto;//赋值为auto
- flex: none;➡️flex-grow: 0;flex-shrink: 0;flex-basis: auto;//赋值为none
- flex: 1;➡️flex-grow: 1; flex-shrink: 1;flex-basis: 0%;// 赋值为非负数，该数字为 flex-grow 值，而flex-shrink 的值取 1，flex-basis 取 0%：
- flex: 0%;➡️flex-grow: 1;flex-shrink: 1;flex-basis: 0%// 赋值为一个长度或百分比，长度或百分比设为 flex-basis 值，而flex-grow 取 1，flex-shrink 取 
- flex: 10 20;➡️flex-grow: 10;flex-shrink: 20;flex-basis: 0%//赋值为两个非负数，两个数字分别设为 flex-grow 和 flex-shrink 的值，而flex-basis 取 0%；
- flex: 10 100px;➡️flex-grow: 10;flex-shrink: 1;flex-basis: 100px;//赋值为一个非负数和一个长度或百分比，非负数字和 长度或百分比 分别设为 flex-grow 和 flex-basis 的值，flex-shrink 取 1

### 表格布局

> 为什么不用table系表格元素？

> 目前，在大多数开发环境中，已经基本不用table元素来做网页布局了，取而代之的是div+css，那么为什么不用table系表格元素呢？

1. 用DIV+CSS编写出来的文件k数比用table写出来的要小，不信你在页面中放1000个table和1000个div比比看哪个文件大
2. table必须在页面完全加载后才显示，没有加载完毕前，table为一片空白，也就是说，需要页面完毕才显示，而div是逐行显示，不需要页面完全加载完毕，就可以一边加载一边显示
3. 非表格内容用table来装，不符合标签语义化要求，不利于SEO
4. table的嵌套性太多，用DIV代码会比较简洁

>表格属性

1. table：指定对象作为块元素级的表格。类同于html标签`<table>`,对应元素的padding会失效；表格前后带有换行符；
2. inline-table：指定对象作为内联元素级的表格。类同于html标签`<table>`，表格前后没有换行符
3. table-caption：指定对象作为表格标题。类同于html标签`<caption>`
4. table-cell：指定对象作为表格单元格。类同于html标签`<td>`, 对应元素的margin会失效;不要与float,position: absolute;等改变布局的属性同时使用，作用会被破坏
5. table-row：指定对象作为表格行。类同于html标签`<tr>`,对应元素的padding、margin会失效；
6. table-row-group：指定对象作为表格行组。类同于html标签`<tbody>`
7. table-column：指定对象作为表格列。类同于html标签`<col>`
8. table-column-group：指定对象作为表格列组显示。类同于html标签`<colgroup>`
9. table-header-group：指定对象作为表格标题组。类同于html标签`<thead>`
10. table-footer-group：指定对象作为表格脚注组。类同于html标签`<tfoot>`

> 使用场景

1. 高度不固定的元素垂直居中(不用设置高)
```
    <section class="layout table">
      <style>
        .vertical-center{
          width: 100%;
          height: 200px;
          display: table;
        }
        .vertical-center div{
          display: table-cell;
          vertical-align: middle;
          text-align: center;
        }
      </style>
      <h1>动态垂直居中</h1>
      <article class="vertical-center">
        <div>
          <p>动态垂直居中</p>
          <p>动态垂直居中</p>
          <p>动态垂直居中</p>
          <p>动态垂直居中</p>
          <p>动态垂直居中</p>
          <p>动态垂直居中</p>
          <p>动态垂直居中</p>
          <p>动态垂直居中</p>
        </div>
      </article>
    </section>
```
2. 动态水平居中(不用设置宽)
```
    <section class="layout table">
      <style>
        .vertical-center ul{
          display: table;
          margin: auto;
        }
        .vertical-center ul li{
          float: left;
          <!--display: table-cell;-->使用这个margin会失效
          margin-right: 10px;
        }
      </style>
      <h1>动态水平居中</h1>
      <article class="vertical-center">
        <ul>
          <li>动态水平居中</li>
          <li>动态水平居中</li>
          <li>动态水平居中</li>
          <li>动态水平居中</li>
          <li>动态水平居中</li>
        </ul>
      </article>
    </section>
```
3. 两列、三列向自适应布局
```
两列自适应
    <section class="layout table">
      <style>
        .layout.table .left-right{
          width:100%;
          display: table;
        }
        .layout.table .left{
          width: 300px;
          display: table-cell;
          background: red;
        }
        .layout.table .right{
          background: blue;
        }
      </style>
      <h1>自适应布局</h1>
      <article class="left-right">
        <div class="left">left</div>
        <div class="right">right</div>
      </article>
    </section>
三列自适应在"css常见样式"文件中
```
4. 等高布局
```
    <section class="layout height">
      <style>
        .layout.height .same-height{
          width:100%;
          display: table-row;
        }
        .layout.height .same-height div{
          width:200px;
          display: table-cell;
        }
      </style>
      <h1>等高布局</h1>
      <article class="same-height">
        <div class="left">left</div>
        <div class="right">
          <p>等高</p>
          <p>等高</p>
          <p>等高</p>
          <p>等高</p>
        </div>
      </article>
```
### 网格布局
> 网格布局（grid）是一个二维的布局，可以创建任意行列的布局。

- 容器属性

    -  display: grid/inline-grid;:指定一个容器采用网格布局;
    - grid-template-columns:属性定义每一列的列宽;
      - 可以使用px或百分比；`repeat()`接受两个参数，第一个参数是重复的次数，第二个参数是所要重复的值【grid-template-columns:repeat(3, 33.33%)】repeat()`重复某种模式也是可以的【grid-template-columns:repeat(2, 100px 20px 80px);】
      - auto-fill:有时，单元格的大小是固定的，但是容器的大小不确定。如果希望每一行（或每一列）容纳尽可能多的单元格【grid-template-columns:repeat(auto-fill, 100px);】
      - fr：为了方便表示比例关系，网格布局提供了`fr`关键字（fraction 的缩写，意为"片段"）。如果两列的宽度分别为`1fr`和`2fr`，就表示后者是前者的两倍。【grid-template-columns:1fr 2fr】
      - minmax():`minmax()`函数产生一个长度范围，表示长度就在这个范围之中。它接受两个参数，分别为最小值和最大值。【grid-template-columns:1fr 2fr minimal(1fr,2fr)】
      - `auto`关键字表示由浏览器自己决定长度。
    - grid-template-rows:属性定义每一行的行高;可以使用px或百分比；`repeat()`接受两个参数，第一个参数是重复的次数，第二个参数是所要重复的值【repeat(3, 33.33%)】repeat()`重复某种模式也是可以的【repeat(2, 100px 20px 80px);】
    - grid-gap :`grid-gap`属性是`grid-column-gap`和`grid-row-gap`的合并简写形式;`grid-row-gap`属性设置行与行的间隔（行间距），`grid-column-gap`属性设置列与列的间隔（列间距）
    - grid-template-areas
    - grid-auto-flow: dense | row(default) | column
    - justify-items: start|end|center|stretch(default) 
    - align-items: start|end|center|stretch(default)
    - justify-content  // 网格容器内的网格的`行`轴对齐方式
    - align-content  // 网格容器内的网格的`列`轴对齐方式
    - grid-auto-columns:
    - grid-auto-rows  // 隐式网格轨道的大小
    - grid-auto-flow  // grid item 排列方式
    - grid // 缩写形式，具体看下面内容

- 项目属性

    - grid-column-start属性：左边框所在的垂直网格线；
- grid-column-end属性：右边框所在的垂直网格线；
    - grid-row-start属性：上边框所在的水平网格线；
    - grid-row-end属性：下边框所在的水平网格线
    - grid-column  // grid-column-start + grid-column-end简写形式；
    - grid-row // , 和 grid-row-start + grid-row-end 简写形式；
    - grid-area属性：指定项目放在哪一个区域或 grid-column-start + grid-column-end + grid-row-start + grid-row-end 简写形式；
    - justify-self  // 沿着`行`轴对齐grid item 里的内容，start | end | center | stretch;
    - align-self  // 沿着`列`轴对齐grid item 里的内容，start | end | center | stretch;
    - place-self属性是align-self属性和justify-self属性的合并简写形式。



## [CSS 变换](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Transitions)

- 定义

  > transition 属性是一个简写属性，用于设置四个过渡属性transition-property、transition-duration、transition-timing-function、transition-delay

- 默认值

  > 请始终设置 [transition-duration](https://www.w3school.com.cn/cssref/pr_transition-duration.asp) 属性，否则时长为 0，就不会产生过渡效果。

  ```css
  transition:all 0 ease 0
  ```

- 详情介绍

  - transition-property:代表要设置动画效果的css属性名称，默认为all，可以设置width，height等；
  - transition-duration:属性规定完成过渡效果需要花费的时间（以秒或毫秒计）,默认值为0，可以设置0.5s,500ms等
  - transition-timing-function:属性规定过渡效果的速度曲线,默认值:ease
    - linear:规定以相同速度开始至结束的过渡效果（等于 cubic-bezier(0,0,1,1)
    - ease:规定慢速开始，然后变快，然后慢速结束的过渡效果（cubic-bezier(0.25,0.1,0.25,1)）
    - ease-in:规定以慢速开始的过渡效果（等于 cubic-bezier(0.42,0,1,1)）
    - ease-out:规定以慢速结束的过渡效果（等于 cubic-bezier(0,0,0.58,1)）
    - ease-in-out:规定以慢速开始和结束的过渡效果（等于 cubic-bezier(0.42,0,0.58,1)）
    - cubic-bezier(*n*,*n*,*n*,*n*):在 cubic-bezier 函数中定义自己的值。可能的值是 0 至 1 之间的数值
  - transition-delay:定义过渡效果何时开始，值以秒或毫秒计，默认为0

