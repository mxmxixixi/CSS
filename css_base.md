- 假设高度已知，请写出三栏布局，左右宽度各300px,中间自适应；
- 扩展题目：上下高度固定，中间自适应；左宽度固定，右自适应；右宽度固定，左自适应；上宽度固定，下自适应；下宽度固定，上自适应【解决方式与上面题目一样，换成对应的属性就好，优缺点也一样】
1. **浮动原理**

> 缺点 :浮动是脱离文档流的，有些时候需要清除浮动，需要很好的处理浮动周边元素的关系；

> 优点:兼容性比较好；

> 高度：必须有，否则因为浮动的原理就是左边有遮挡物，就会避开遮挡物显示文案，当发现左边没有遮挡物的时候，就会紧贴原始的边显示文案，于是就会溢出。【解决方案：浮动一定要有高。但是可以用BFC解决。】

```
    <section class="layout float">
      <style media="screen">
      .layout.float .left{
        float:left;
        width:300px;
        background: red;
      }
      .layout.float .center{
        background: yellow;
        overflow: hidden;//解决无高度问题，或者中间高度大于左右两侧高度
      }
      .layout.float .right{
        float:right;
        width:300px;
        background: blue;
      }
      </style>
      <h1>三栏布局</h1>
      <article class="left-right-center">
        <div class="left"></div>
        <div class="right"></div>
        <div class="center">
          <h2>浮动解决方案</h2>
          1.这是三栏布局的浮动解决方案；
          2.这是三栏布局的浮动解决方案；
          3.这是三栏布局的浮动解决方案；
          4.这是三栏布局的浮动解决方案；
          5.这是三栏布局的浮动解决方案；
          6.这是三栏布局的浮动解决方案；
        </div>
      </article>
    </section>
```

2. **定位**

> 缺点 :该布局脱离文档流，所以子元素也必须脱离文档流，因此可使用性比较差

> 优点 :快捷，比较不容易出问题

> 高度：左右的高度不会被撑开

```
    <section class="layout absolute">
      <style>
        .layout.absolute .left-center-right>div{
          position: absolute;
        }
        .layout.absolute .left{
          left:0;
          width: 300px;
          background: red;
        }
        .layout.absolute .center{
          left: 300px;
          right: 300px;
          background: yellow;
        }
        .layout.absolute .right{
          right:0;
          width: 300px;
          background: blue;
        }
      </style>
      <h1>三栏布局</h1>
      <article class="left-center-right">
        <div class="left"></div>
        <div class="center">
          <h2>绝对定位解决方案</h2>
          1.这是三栏布局的浮动解决方案；
          2.这是三栏布局的浮动解决方案；
          3.这是三栏布局的浮动解决方案；
          4.这是三栏布局的浮动解决方案；
          5.这是三栏布局的浮动解决方案；
          6.这是三栏布局的浮动解决方案；
        </div>
        <div class="right"></div>
      </article>
    </section>
```
3. **flex**

> 优点 :比较完美的解决了浮动和绝对定位的问题。在移动端比较常用。

> 缺点 :兼容性比较差，不兼容IE8及以下的版本。因为这个是CSS3中新增的display的属性值。

> 高度:无影响 

```
    <section class="layout flexbox">
      <style>
        .layout.flexbox{
          margin-top: 110px;
        }
        .layout.flexbox .left-center-right{
          display: flex;
        }
        .layout.flexbox .left{
          width: 300px;
          background: red;
        }
        .layout.flexbox .center{
          flex:1;
          background: yellow;
        }
        .layout.flexbox .right{
          width: 300px;
          background: blue;
        }
      </style>
      <h1>三栏布局</h1>
      <article class="left-center-right">
        <div class="left"></div>
        <div class="center">
          <h2>flexbox解决方案</h2>
          1.这是三栏布局的浮动解决方案；
          2.这是三栏布局的浮动解决方案；
          3.这是三栏布局的浮动解决方案；
          4.这是三栏布局的浮动解决方案；
          5.这是三栏布局的浮动解决方案；
          6.这是三栏布局的浮动解决方案；
        </div>
        <div class="right"></div>
      </article>
    </section>
```
4. **table**

> 缺点 :操作繁琐，当三栏中其中某一栏高度超出时，其他两栏的高度也会自动跟着调整(不符合某些场景)

> 优点 :兼容性非常好，补缺了flex布局兼容的问题

> 高度:会自动撑开

```
<section class="layout table">
      <style>
        .layout.table .left-center-right{
          width:100%;
          height: 100px;
          display: table;
        }
        .layout.table .left-center-right>div{
          display: table-cell;
        }
        .layout.table .left{
          width: 300px;
          background: red;
        }
        .layout.table .center{
          background: yellow;
        }
        .layout.table .right{
          width: 300px;
          background: blue;
        }
      </style>
      <h1>三栏布局</h1>
      <article class="left-center-right">
        <div class="left"></div>
        <div class="center">
          <h2>表格布局解决方案</h2>
          1.这是三栏布局的浮动解决方案；
          2.这是三栏布局的浮动解决方案；
          3.这是三栏布局的浮动解决方案；
          4.这是三栏布局的浮动解决方案；
          5.这是三栏布局的浮动解决方案；
          6.这是三栏布局的浮动解决方案；
        </div>
        <div class="right"></div>
      </article>
    </section>
```
5. **网格布局**

> 优点：代码比较简单。

> 缺点：兼容性比较差。

> 高度：左右高度不会被撑开

```
    <section class="layout grid">
      <style>
        .layout.grid .left-center-right{
          width:100%;
          display: grid;
          grid-template-rows: 100px;
          grid-template-columns: 300px auto 300px;
        }
        .layout.grid .left-center-right>div{

        }
        .layout.grid .left{
          width: 300px;
          background: red;
        }
        .layout.grid .center{
          background: yellow;
        }
        .layout.grid .right{

          background: blue;
        }
      </style>
      <h1>三栏布局</h1>
      <article class="left-center-right">
        <div class="left"></div>
        <div class="center">
          <h2>网格布局解决方案</h2>
          1.这是三栏布局的浮动解决方案；
          2.这是三栏布局的浮动解决方案；
          3.这是三栏布局的浮动解决方案；
          4.这是三栏布局的浮动解决方案；
          5.这是三栏布局的浮动解决方案；
          6.这是三栏布局的浮动解决方案；
        </div>
        <div class="right"></div>
      </article>
    </section>
```

- css盒模型

  -  盒模型是有两种标准的，一个是标准模型，一个是IE模型

    ![img](https://images2017.cnblogs.com/blog/1265396/201711/1265396-20171119143703656-1332857321.png)

    ![img](https://images2017.cnblogs.com/blog/1265396/201711/1265396-20171119144229156-49945808.png)

  - 设置盒模型应该是哪种模型：box-sizing:content-box(标准模型，默认值)、box-sizing:border-box(IE模型)、box-sizing:inherit(表示从父级获取box-sizing值)

  - js获取宽高

    - dom.style.width/height:这种方式只能取到dom元素内联样式所设置的宽高，也就是说如果该节点的样式是在style标签中或外联的CSS文件中设置的话，通过这种方法是获取不到dom的宽高的;
    - dom.currentStyle.width/height :这种方式获取的是在页面渲染完成后的结果，就是说不管是哪种方式设置的样式，都能获取到,但这种方式只有IE浏览器支持;
    - window.getComputedStyle(dom).width/height:这种方式的原理和2是一样的，这个可以兼容更多的浏览器，通用性好一些;
    - dom.getBoundingClientRect().width/height:这种方式是根据元素在视窗中的绝对位置来获取宽高的;
    - dom.offsetWidth/offsetHeight:这个就没什么好说的了，最常用的，也是兼容最好的。

  - 边距重叠

    - 对于行内元素 margin-top/margin-bottom对于上下元素无效，margin-left/margin-right有效，对于相邻的块级元素margin-top和margin-bottom两者叠加按照一定的规则：
      - 都是正整数margin值取两者的最大值
      - 都是负数margin值取最小值
      - 两者正负相反，margin值取两者之和

    - 解决方案：创建BFC,下面将介绍BFC具体内容

  - BFC(Block Formatting Context块级格式化上下文)

    - 定义:它是一个独立的渲染区域，只有Block-level box参与， 它规定了内部的Block-level Box如何布局，并且与这个区域外部毫不相干;

    - BFC布局规则：

      - 内部的Box会在垂直方向上，一个接一个的放置；

      - Box垂直方向的距离由margin决定，属于**同一个**BFC的两个相邻Box的margin会发生重叠；

        > 解决方案：相邻的Box中再创建BFC

        ```
        <section>
        	<style>
            *{
                margin: 0;
                padding: 0;
            }
            p {
                color: #f55;
                background: yellow;
                width: 200px;
                line-height: 100px;
                text-align:center;
                margin: 30px;
            }
            div{
                overflow: hidden;
            }
        	</style>
          <p>看看我的 margin是多少</p>
          <div>
            <p>看看我的 margin是多少</p>
          </div>
        </section>
        ```

      - 每个盒子（块盒与行盒）的margin box的左边，与包含块border box的左边相接触(对于从左往右的格式化，否则相反)。即使存在浮动也是如此;BFC的区域不会与float box重叠;

        > 自适应两列布局、三列自适应布局

        ```
        <section>
        		<style>
              *{
                  margin: 0;
                  padding: 0;
              }
              body {
                  width: 100%;
                  position: relative;
              }
        
              .left {
                  width: 100px;
                  height: 150px;
                  float: left;
                  background: rgb(139, 214, 78);
                  text-align: center;
                  line-height: 150px;
                  font-size: 20px;
              }
        
              .right {
                  overflow: hidden;
                  height: 300px;
                  background: rgb(170, 54, 236);
                  text-align: center;
                  line-height: 300px;
                  font-size: 40px;
              }
         	 	</style>
        		<div class="left">LEFT</div>
            <div class="right">RIGHT</div>
        </section>
        ```

      - BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素；反之；

      - 计算BFC的高度时，浮动元素也参与计算；

        > 当我们不给父节点设置高度，子节点设置浮动的时候，会发生高度塌陷，这个时候我们就要清楚浮动;

        ```
        <section>
        	<style>
            .par {
                border: 5px solid rgb(91, 243, 30);
                width: 300px;
                overflow: hidden;
            }
            
            .child {
                border: 5px solid rgb(233, 250, 84);
                width:100px;
                height: 100px;
                float: left;
            }
        	</style>
        	<div class="par">
            <div class="child"></div>
            <div class="child"></div>
          </div>
        </section>
        ```

    - 创建BFC方式
      - float的值不是none;
      - position的值不是static或者relative;
      - display的值是inline-block、table-cell、flex、table-caption或者inline-flex;
      - overflow的值不是visible;

- css中border渲染原理

  > div的border是有宽度和颜色的，当div的宽度比较大的时候，比如每个边100像素，颜色又不一样，浏览器怎么渲染颜色呢？经测试发现，宽度较大的border相交时：

  - 只有相邻边才会相交，对边是不可能相交的;
  - 相交区域(显然是矩形)按对角线划分成两个三角形，两个三角形分别渲染成两个边的颜色，颜色不会出现重叠的情况;
  - 调整四个边的宽度，加上中间区域的宽度，配以不同颜色和透明，各种简单多边形(举一反三)已经不在话下了

- 文本溢出显示...

  - 单行文本隐藏

    ```javascript
    overflow: hidden;//超出隐藏
    text-overflow: ellipsis;//文本超出显示...
    white-space: nowrap;//超出的空白区域不换行
    ```

  - 多行文本隐藏

    ```javascript
    //只兼容webkit内核的浏览器
    display: -webkit-box;             /*将对象转为弹性盒模型展示*/
    -webkit-box-orient: vertical;     /*设置弹性盒模型子元素的排列方式*/
    -webkit-line-clamp: 2;            /*限制文本行数*/
    overflow: hidden;                 /*超出隐藏*/
    ```

    ```javascript
    //跨浏览器兼容+伪元素定位
    .text-box3 p{
        position: relative;
        line-height: 1.4em;        /*行高和height成倍数，这里以三行文本超出隐藏举例*/
        height: 4.2em;
        overflow: hidden;
    }
    .text-box3 p::after{         /*若要兼容IE8需用:after*/
        content: "...";          /*替换内容比较灵活*/
        position: absolute;
        bottom: 2px;
        right:5px;
        padding: 0 3px;
        background:#fff;         /*颜色和文字背景保持一致*/
        box-shadow: 0 0 10px #fff;  /*边缘处理*/
    }
    ```

- 滚动条样式修改

  ```javascript
  .demo{
    //滚动条的轨道的类名
    &::-webkit-scrollbar{
      width: 8px;
    }
    //滚动条的轨道的类名
    &::-webkit-scrollbar-track {
      background-color: #1f2150;
      border-radius: 5px;
    }
   	//滚动条的滑块的类名
    &::-webkit-scrollbar-thumb {
      background-color: #2d3075;
      border-radius: 5px;
    }
  }
  ```

- 图片尺寸变形

  ```javascript
  可以对图片进行裁剪
  object-fit: cover;
  ```

  