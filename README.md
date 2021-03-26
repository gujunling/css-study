## CSS2

### CSS选择器

#### 属性选择器

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>属性选择器</title>
    <style>
        /* 
        [属性名] 选择含有指定属性的元素
        [属性名 = 属性值]   选择含有指定属性和属性值的元素
        [属性名 ^= 属性值]  选择属性值中以指定值开头的元素
        [属性名 $= 属性值]  选择属性值中以指定值结尾的元素
        [属性名 *= 属性值]  选择属性值中含有某个值的元素

         */
        /* p[title] {
            color: yellowgreen;
        } */
        /* p[title=firsesest] {
            color: yellowgreen;
        } */
        /* p[title ^=se] {
            color: yellowgreen;
        } */
        /* p[title $=six] {
            color: yellowgreen;
        } */
        p[title *=se] {
            color: yellowgreen;
        }

    </style>
</head>

<body>
    <p title="firsesest">111111</p>
    <p>222222</p>
    <p title="secondsix">333333</p>
    <p>444444</p>
    <p title="five">555555</p>
    <p title="sesesixsix">666666</p>
</body>

</html>
```

#### 伪类选择器

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>伪类选择器</title>
    <style>
        /* 将ul中的第一个li设置为红色 */

        /* 伪类（不存在的类，特殊的类） 
        伪类用来描述一个元素的特殊的状态
           比如：第一个元素 、被点击的元素、鼠标移入的元素等
        伪类一般情况下都是使用:开头
            :first-child    第一个子元素
            :last-child     最后一个子元素
            :nth-child(n)   选中第n个子元素
                        n          直接写n，表示第n个，范围为0- 正无穷
                        2n或even   表示选择偶数位的元素
                        2n+1或odd  表示选中奇数位的元素
                    以上这些伪类都是根据第一个子元素来进行排序的

            :first-of-type
            :last-of-type
            :nth-of-type()
                   这几个伪类的功能和上述的类似，不同点是它们是在同类型元素中进行排序的

            :not()     否定伪类
                --将符合条件的元素从选择器中去除

        */

        /* ul>li:first-child {
            color: red;
        } */

        /* ul中除了第三个li之外的其他的li都要变成红色 */
        ul>li:not(:nth-of-type(3)) {
            color: red;
        }
        /* 
        :link       用来表示没访问过的链接（正常的链接）
        :visited    用来表示访问过的链接

                 由于隐私的原因，visited这个伪类只能修改链接的颜色，一般不建议修改     

        */

        a:visited {
            color: #bbffaa;
        }

        a:link {
            color: #000000;
        }
        /* :hover 用来表示鼠标移入的状态 */
        a:hover {
            color: orange;
        }

        /* :active   表示鼠标点击的状态 */
        a:active{
            color: green;
        }

    </style>
</head>

<body>
    <!-- <ul>
        <li>第零个</li>
        <li>第一个</li>
        <li>第二个</li>
        <li>第三个</li>
        <li>第四个</li>
        <li>第五个</li>
    </ul> -->

    <!-- 
        1.没有访问过的链接
        2.访问过的链接
    -->
    <a href="https:www.baidu.com">访问过的链接</a>
    <br>
    <br>
    <a href="https:www.baidu123.com">未访问过的链接</a>
</body>

</html>
```

#### 伪元素选择器      


```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>伪元素选择器</title>
    <style>
        p {
            font-size: 20px;
        }

        /* 伪元素，表示页面中一些特殊的并不真实的存在的元素（特殊的位置）
        伪元素使用 :: 开头

        ::first-letter   表示第一个字母
        ::first-line     表示第一行
        ::selection      表示选中的内容
        ::before         元素的开始位置    
        ::after          元素的最后位置
        before和after必须结合content属性来使用
        */
           /* 需求：首字母下沉 */
        p::first-letter {
            font-size: 50px;
        }

        /* 需求：第一行背景颜色为黄色 */
        p::first-line {
            background-color: yellow;
        }

        /* 需求：鼠标选中后背景颜色变为黄绿色 */
        p::selection {
            background-color: yellowgreen;
        }

        /* 需求：在div标签的Hello之前添加一些字符并修改颜色为红色 */
        div::before {
            content: 'hahaha';
            color: red;
        }

        /* 需求：在div标签的最后位置之后添加一些字符并修改颜色为绿色 */
        div::after {
            content: '111111';
            color: green;
        }
    </style>
</head>

<body>

    <div>Hello Are You Ok?</div>

    <p>
        hahahha布局的传统解决方案，基于盒状模型，依赖 display 属性 + position属性 + float属性。它对于那些特殊布局非常不方便，比如，垂直居中就不容易实现。
        2009年，W3C 提出了一种新的方案----Flex布局，可以简便、完整、响应式地实现各种页面布局。目前，它已经得到了所有浏览器的支持，这意味着，现在就能很安全地使用这项功能。
    </p>
</body>

</html>
```



#### 样式的继承

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>样式的继承</title>
    <style>
        /* 样式的继承

            为一个元素设置的样式同时也会应用到它的后代元素中

            继承只会发生在某个元素的后代元素上
            继承是发生在祖先元素和后代元素之间的

            继承的设计是为了方便我们的开发，
                 利用继承可以将一些通用的样式统一设置到共同的祖先元素上，这样只需要设置一次即可让所有的元素都具有该样式。

            但是，并不是所有的样式都会被继承
                 例如：背景相关的，布局相关等的这些样式都不会被继承
        */

        p {
            color: red;
        }

        div {
            color: yellowgreen;
        }
    </style>
</head>

<body>
    <!-- p元素内部不能放块级元素，可以放行内元素 -->
    <p>
        这是一个p元素啊 啊啊
        <span>
            p元素中的span啊啊啊
        </span>
    </p>
    <span>p元素外部的span</span>
    <div>
        这是div元素啊
        <span>
            这是div元素中的span元素啊 啊
            <em>
                这是span元素中的em元素
            </em>
        </span>
    </div>
</body>

</html>
```

#### 选择器权重

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>选择器的权重</title>
    <style>
        div {
            color: yellowgreen;
        }

        /* #box1 {
            color: red;
        } */
        .div1 {
            color: black;
        }

        * {
            font-size: 50px;
        }

        div {
            font-size: 20px;
        }


        /* 
        css选择器并没有优先级，平常说的css优先级实际上是css声明的优先级
        样式的冲突：
             当我们通过不同的选择器，选中相同的元素，并且为相同的样式设置不同的值,此时就发生了样式的冲突

             发生样式冲突时，应用哪个样式由css声明的优先级来决定。
             当重要声明与非重要声明冲突时，永远是重要声明起作用，即 !important 作用的样式生效，不需要考虑声明的优先级
             当重要声明之间发生冲突时，则在重要声明所组成的组中，对规则中非重要声明的优先级进行比较，优先级高的样式起作用
        
        例如：
        div{ background:pink !important;}    div .test{background:yellow !important}   
        //此时背景色被渲染成黄色，（div 和 .test选择的是同一个元素）
        
         可以在某一个样式的后边添加  !important  ，此时表示为重要声明，则此时该样式会优先被使用，甚至超过内联样式，在开发中要慎用（甚至使用js都无法修改此样式），但标志为 !important 的声明并没有特殊的特殊性值，不过要于非重要声明分开考虑，其虽然会导致样式被修改，但并不能改变css声明的优先级

        css声明的优先级（从高到低）（非重要声明）：  
             内联样式          （行内样式）      1,0,0,0
             ID选择器            （#）          0,1,0,0
             类和伪类选择器       （.）          0,0,1,0
             元素和伪元素选择器 （元素标签名）     0,0,0,1
             通配选择器           （*）          0,0,0,0
             继承的样式            没有优先级，0优先级也比没有优先级要高。通配符内部的样式会比继承来的样式优先级高，通配符的样式会优先继承的样式来生效。
     比较优先级时，需要将所有的css声明的优先级进行相加计算，最后优先级越高，越优先显示（分组选择器是单独计算的（例如：div,p,span{}））
     选择器的累加不会超过其最大的数量级，即 类选择器再高也不会超过ID 选择器
                
     如果优先级计算后相等。此时则优先使用css样式中靠下的样式，即下面的样式的值会覆盖上面的同样的样式的值
        
来源
   css样式的来源大致有三种
	 创作人员（开发人员）
	 读者（用户）
	 用户代理 （浏览器），用户代理不存在重要声明
		 
 来源的权重（由高到低）：
	 读者的重要声明（Chrome，火狐等浏览器都没有把读者的重要声明暴露出来，即在这些浏览器中没法定义读者的重要声明，但ie浏览器可以设置）
     创作人员的重要声明 （在浏览器的Elements中的element.style中写的带 !important 的样式，等同于写的内联样式中的重要声明，依旧属于开发人员的重要声明）
	 创作人员的正常声明
	 读者的正常声明
	 用户代理的声明
        
层叠样式表的最终的渲染样式顺序：
		1.找出所有相关的规则，这些规则都包含一个选择器
	    2.计算声明的优先级
	           首先按来源排序
	          （当声明的来源相同时，）在按选择器的特殊性排序
	          （当选择器的特殊性相等时，）最终按顺序展示样式（谁的样式在下面被定义，谁的样式被显示）
       
         */
    </style>
</head>

<body>
    <div id="box1" class="div1">
        hahahhahahdiv的啦啦啦啦
        <span>这是div中的span元素</span>
    </div>
</body>

</html>
```

### 背景

```html
<!DOCTYPE html>
<html lang="en">
 <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>背景图片练习</title>
    <style>
        .box1 {
            width: 500px;
            height: 500px;   
      /* 
         background-color:设置背景颜色
         background-image:设置背景图片
                可以同时设置背景颜色和背景图片，这样背景颜色将会成为图片的背景色
                如果背景图片小于元素，则背景图片会自动在元素中平铺，将元素铺满
                如果背景图片大于元素，将会有一部分背景无法完全显示
                如果背景图片和元素一样大，则会正常显示
        background-repeat:设置背景的重复方式
              可选值：
                  repeat  默认值 背景会沿着x轴和y轴双向重复
                  repeat-x  沿着x轴方向重复
                  repeat-y  沿着y轴方向重复
                  no-repeat  不重复
         background-position:用来设置背景图片的位置
            设置方式：
               1.通过top、left、right、bottom、center等几个表示方位的词来设置背景图片的位置(实际上相当于是一个九宫格，通过其中的方位词设置位置)
                   使用方位词时必须要同时指定两个值，如果只写一个，则第二个默认就是center
               2.通过偏移量来指定背景图片的位置
                   水平方向的偏移量 垂直方向的偏移量（第一个水平、第二个垂直方向）
        
        background-clip:设置背景的范围
               可选值： 
                     border-box  默认值  背景会出现在边框的下边，边框下也会有背景
                     padding-box   背景不会出现在边框，只出现在内容区和内边距
                     content-box   背景只会出现在内容区
        
        background-origin: 背景图片计算的偏移量的原点
            可选值：
               padding-box   默认值，background-position从内边距处开始计算
               content-box   原点在内容区，背景图片的偏移量从内容区处开始计算
               border-box    背景图片的偏移量从边框处开始计算
        
        background-size: 设置背景图片的大小
             第一个值表示宽度
             第二个值表示高度
               如果只写一个，则第二个值是auto，表示等比例缩放，可能出现显示不全或拉伸
            cover 表示图片的比例不变,将元素铺满
            contain  表示图片比例不变，将图片在元素中完整显示
        
        background-attachment:设置背景图片是否跟随元素移动
            可选值
                 scroll  默认值  背景图片会跟随元素移动
                 fixed   表示背景图片会固定在页面中，不会随元素移动
    
        background 背景相关的简写属性，所有背景相关的样式都可以通过该样式来设置，并且没有顺序要求，也没有必须要写的属性
              background: #bfa  url("../img/000.jpg") center center/contain no-repeat
            但是注意： background-size一定要写到 background-position的后面,并通过/来分割，不能单纯的使用size属性的值来设置样式，示例：center center/contain
                       background-clip和 background-origin的属性可选值值是一样的，但是此时 background-origin必须写在前面， background-clip在后面

         */
        background-color: #bfa;
        background-image: url("../img/000.jpg");
        background-repeat: no-repeat;
        background-size: 500px 500px;
        background-attachment: fixed;
        /* background-clip: border-box;
        background-origin: padding-box; */
        /* background-position: 100px 100px; */
        /* background-position: right bottom; */
    }
  </style>
</head>
<body>

</body>

</html>
```


### 布局

#### 块级元素盒子模型

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>块级元素的盒子模型</title>
    <style>
        .box1 {
            /* 
            内容区 （content），元素中的所有的子元素和文本内容都在内容区中排列
            内容区的大小由width和height两个属性来设置

             */
            background: #aabbff;
            width: 200px;
            height: 200px;
            /* 
            边框（border）：边框属于盒子边缘，边框里属于盒子内部，出了边框就都是盒子的外部
            边框的大小会影响整个盒子的大小
            设置边框，需要至少设置三个样式，但width和color是有默认值的，border-style的默认值为none，如果不写则默认为none,即不显示
            边框宽度：border-width，可以用来指定四个方向的边框的宽度（上、右、下、左）
                四个值：上、右、下、左
                三个值：上、左右、下
                两个值：上下、左右
                一个值：上下左右均为此值

               默认值 ，一般都是三个像素，但建议都写，不同浏览器可能默认值不同

             除了border-width还有一组border-xxx-width， 用来指定某一个边的宽度
                  xxx可以是top、right、bottom、left
             边框颜色：border-color
                 如果省略不写，则默认使用color的值，如果没有指定color的值，color值的默认值为黑色
                 
             边框样式：border-style
                        solid:表示实线
                        dotted:点状虚线
                        dashed:虚线
                        double：双线，双线的宽度等于 border-width 的值。
                        none 默认值
             简写属性：border 
                通过该属性可以同时设置边框所有的相关样式，并且没有顺序要求
             */

            border: 10px #bdbdbd solid;
           /* 
            内边距：(padding) 内容区和边框之间的距离是内边距，一共有四个方向的内边距
               内边距的设置会影响盒子的大小，背景颜色会延伸到内边距上
           */

            padding: 50px;
           /* 
            外边距（margin）外边距不会影响盒子可见框的大小，但外边距会影响盒子的位置，会影响到盒子实际占用空间
                一共有四个方向的外边距
                 margin-top
                    上外边距，设置一个正值，元素会向下移动，设置负值，元素会向上移动，其余的外边距同理
                    但默认情况下设置margin-right不会产生任何效果

              元素在页面中是按照自左向右的顺序排列的，所以默认情况下如果我们设置的左和上外边距会移动元素自身，而设置下和右边距会移动其他的元素

           */
            margin: 10px;
              }

        .inner {
            width: 100%;
            height: 100%;
            background: #bbffaa;
        }

        .box3 {
            width: 200px;
            height: 200px;
            background: orange;

        }

        .box4 {
            width: 100px;
            height: 100px;
            background: pink;
            position: relative;
            top: 100px;
        }
    </style>
</head>

<body>
    <!-- 
    盒模型、盒子模型、框模型（box model）
           CSS将页面中所有的元素都设置为了一个矩形的盒子
           将元素设置为矩形的盒子之后，对页面的布局就变成将不同的盒子摆放到不同的位置
        每一个盒子都是由以下几个部分组成：
            内容区（content）
            内边距（padding）
            边框（border）
            外边距（margin）
     一个盒子的可见框的大小，由内容区、内边距 和边框共同决定
        所以在计算盒子大小时，需要将这三个区域的大小加到一起
    -->
    <!-- 

        元素的水平方向的布局
           元素在其父元素中水平方向的位置由以下几个属性共同来决定
             margin-left
             border-left
             padding-left
             width
             padding-right
             border-right
             margin-right

        一个元素在其父元素中，水平方向必须要满足以下的等式
        margin-left + border-left + padding-left + width + padding-right + border-right + margin-right = 其父元素内容区的宽度（是必须满足的）
        以上等式必须成立，如果相加结果使等式不成立则称为过渡约束，则等式会自动调整。
           调整的情况：
              如果这七个值中没有为auto的情况，则浏览器会自动调整margin-right的值，促使等式满足
              这七个值中有三个值可以设置为auto
                 width    width的值默认为auto，如果不写，则使用默认值
                 margin-left
                 margin-right
              如果某个值为auto，则会自动调整为auto的那个值以使等式成立

              如果将一个宽度和一个外边距设置为auto，则宽度会调整到最大，设置为auto的外边距会自动为0
              如果三个值都设置为auto，则外边距都是0，宽度最大
              如果将两个外边距设置为auto，宽度为固定值，则会将为auto的两个外边距设置为相同的值，经常用来使该元素在其父元素中水平居中

     -->

    <!-- 子元素是在父元素的内容区中排列的，如果子元素的大小超过了父元素，则子元素会从父元素中溢出
        可以在父元素中使用overflow属性来设置父元素如何处理溢出的子元素
        overflow
           可选值：
              visible  默认值，子元素会从父元素中溢出，在父元素外部的位置显示
              hidden   溢出的内容将会被裁减不会显示
              scroll   生成两个滚动条，通过滚动条来查看完整的内容
              auto     根据需要生成滚动条，不会生成多余的滚动条

        overflow-x: 处理水平方向的溢出
        overflow-y：处理垂直方向的溢出
    -->

    <!-- 
        垂直方向外边距的重叠（折叠）
        相邻的垂直方向的外边距会发生重叠现象

        兄弟元素：
             兄弟元素间的相邻垂直外边距会取两者中的较大的那个值（两者都是正值）
             特殊情况，如果相邻的外边距一正一负，则取两者的和
             如果相邻的外边距都是负值，则取两者中绝对值较大的值

        兄弟元素之间的外边距的重叠，对于开发是有利的，不需要进行处理

        父子元素：
           父子元素间相邻的外边距，子元素的值会传递给父元素（上外边距）
           父子外边距的折叠会影响到页面的布局，必须要进行处理

                    1. 可以给父元素设置外边框，但要注意边框也是有宽度和高度的，需要将父元素的高度减小边框的大小，子元素的外边距也要减去父元素的边框的大小,但这样比较麻烦（不推荐使用）
                    2. 可以通过子元素使用相对定位来解决
                    3. 可以通过为子元素开启BFC来解决

     -->
       <!-- <div class="box1">
        <div class="inner"></div>
    </div> -->
    <div class="box3">
        <div class="box4"></div>
    </div>
 </body>

</html> 
```



#### 行内元素的盒子模型

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>行内元素的盒子模型</title>
    <style>
        .span1 {
            /* width: 100px;
            height: 100px; */
            visibility: visible;
        }
    </style>
</head>

<body>
    <!-- 
        行内元素的盒子模型
           行内元素不支持设置宽度和高度
           行内元素可以设置padding，但是垂直方向的padding不会影响页面的布局
           行内元素可以设置border，但是垂直方向的border不会影响页面的布局
           行内元素可以设置margin，但是垂直方向的margin不会影响页面的布局

      display:用来设置元素显示的类型 
        可选值：
           inline:将元素设置为行内元素
           block:将元素设置为块级元素
           inline-block：将元素设置为行内块级元素
                既可以设置宽度和高度，又不会独占一行（一般不建议使用）
           table ： 将元素设置为一个表格
           none:元素不在页面中显示
           
      visibility 用来设置元素的显示状态
         可选值：
            visible  默认值，元素在页面中正常显示
            hidden   元素在页面中隐藏，不显示，但是依然占据页面中的位置
     -->

    <span class="span1">
        span元素的啊啊啊啊
    </span>
</body>

</html>
```



#### 浏览器的默认样式

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>浏览器的默认样式</title>
    <!-- <link rel="stylesheet" href="./normalize.css"> -->
    <!-- <link rel="stylesheet" href="./reset.css"> -->
    <!-- 

    重置样式表：专门用来对浏览器的样式进行重置的

    reset.css:直接去除了浏览器的默认样式

    normalize.css  对浏览器的默认样式进行了统一，所有的浏览器的样式都设置为一样的了、

    二者一般不会同时使用

     -->
    <style>
        /* 
        默认样式：
           通常情况下，浏览器都会为元素设置一些默认样式

            默认样式的存在会影响到页面的布局，不同的浏览器的默认样式也不一定相同，通常情况下，编写网页时要去除浏览器的默认样式（主要是PC端页面）
        list-style 简写属性在一个声明中设置所有的列表属性。
        list-style:none;   去除列表的属性
        */

        * {
            margin: 0;
            padding: 0;
        }

        .box1 {
            width: 200px;
            height: 200px;
            background: #bbffaa;
        }
    </style>
</head>

<body>
    <div class="box1">

    </div>
    <p>这是一个段落啊 啊啊 啊</p>
    <p>这是一个段落啊 啊啊 啊</p>
    <p>这是一个段落啊 啊啊 啊</p>
    <p>这是一个段落啊 啊啊 啊</p>

    <ul>
        <li>列表111</li>
        <li>列表222</li>
        <li>列表333</li>
        <li>列表444</li>
        <li>列表555</li>
    </ul>
</body>

</html>
```

### 定位（position）

相对定位参照与元素本来的位置来进行定位。

绝对定位参照与元素的包含块来定位的。

固定定位参照与浏览器的视口来进行定位的。

没有定位就是参照的包含块进行排列的。

初始包含块是一个视口大小的矩形，但不等于视口。

定位的默认值为auto，即`left:auto;right:auto;top:auto;bottom:auto;，不可被继承`，

width和height的默认值也是auto，不可被继承，margin和padding的默认值为0，

border-width的默认值为中等大小，如果不存在border-style，则没有border-width这个说法。

width的百分比参照与包含块的width，height参照与包含块的height，left参照与包含块的width，top参照与包含块的height

margin和padding中的百分比参照的是当前元素的包含块的width的值。


```html
 <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>相对定位练习</title>
    <style type="text/css">
        body {
            font-size: 36px;
        }
    .box1 {
        width: 200px;
        height: 200px;
        background-color: #bfa;
    }

    .box2 {
        width: 200px;
        height: 200px;
        background-color: orange;
        /* 
        定位（position）
             定位是一种更加高级的布局手段
                 通过定位可以将元素摆放到页面的任意位置
                 使用position属性来设置定位
                 可选值：
                       static: 默认值，元素是静止的，没有开启定位
                       relative:开启元素的相对定位
                       absolute：开启元素的绝对定位
                       fixed：开启元素的固定定位
                       sticky：开启元素的粘滞定位 
        */
       
        position: relative;
        left: 200px;
        /* top: -200px; */
        bottom: 200px
    }

    .box3 {
        width: 200px;
        height: 200px;
        background-color: yellow;
    }
</style>
</head>

<body>
    <div class="box1">1</div>
    <div class="box2">2</div>
    <div class="box3">3</div>
    <script>
    </script>
</body>

</html>
```

#### 相对定位

     /* 
                   相对定位：当元素的position属性值设置为relative时则表示开启了元素的相对定位
                     相对定位的特点：
                       1.元素开启相对定位以后，如果不设置偏移量则元素不会发生任何变化
                       2.相对定位是参照元素在文档流中的位置（原来的位置）进行定位的
                       3.相对定位会提升元素的层级
                       4.相对定位不会使元素脱离文档流
                       5.相对定位不会改变元素的性质，块还是块，行内还是行内
                       
                  偏移量（offset）：
                       当元素开启了定位以后，可以通过偏移量来设置元素的位置
                       top   -定位元素和定位位置的上边的距离
                       bottom  -定位元素和定位位置的下边的距离
    
                      -定位元素垂直方向的位置由top和bottom两个属性来控制
                      通常情况下只会使用其中之一，
                      top值越大，定位元素越向下移动
                      bottom值越大，定位元素越向上移动
    
                       left    -定位元素和定位位置的左边的距离
                       right   -定位元素和定位位置的右边的距离
    
                       -定位元素水平方向的位置由left和right两个属性来控制，通常情况下只会使用其中之一，
                              left值越大，定位元素越向右移动
                              right值越大，定位元素越向左移动
                              
     */


#### 绝对定位

     /* 
                绝对定位: 当元素的position属性值设置为absolute时，则开启了元素的绝对定位
                      绝对定位的特点：
                        1.开启绝对定位后，如果不设置偏移量元素，则元素的位置不会发生变化
                        2.开启绝对定位后，元素会从文档流中脱离
                        3.绝对定位会改变元素的性质，行内变成块，块的宽高被内容撑开
                        4.绝对定位会使元素提升一个层级
                        5.绝对定位元素是相对于包含块进行定位的
    
                包含块（containing block）：
                  正常情况下：包含块就是离元素最近的祖先块元素
                  <span>是行内元素，不算包含块
                    
                绝对定位的包含块：包含块就是离它最近的开启了定位的祖先元素，如果所有的祖先元素都没有开启定位，则根元素就是它的包含块，则相对于根元素（html元素，即当前页面，即页面左上角为原点（0,0））进行定位
                html（根元素、初始包含块）
             
     */


#### 固定定位

     /* 
           固定定位：将元素的position属性设置为fixed则开启了元素的固定定位
           
           固定定位也是一种绝对定位，所有固定定位的大部分特点都和绝对定位一样，唯一不同的是固定定位永远参照于浏览器的视口进行定位
     */


#### 粘滞定位

     /* 
        粘滞定位
               当元素的position属性设置为sticky时，表示元素开启了粘滞定位
               粘滞定位和相对定位的特点基本一致，不同的是粘滞定位可以在元素到达某个元素时将其固定
    */
     /* 
        粘滞定位兼容性不太好，使用需谨慎
    */

#### 绝对定位的布局

     /* 
      没有开启定位时的水平布局：
         margin-left + border-left + padding-left + width + padding-right + border-right + margin-right = 其包含块的内容区的宽度
      开启了绝对定位以后的水平布局：
         left + margin-left + border-left + padding-left + width + padding-right + border-right + margin-right + right = 其包含块的内容区的宽度
    */

### JS滚轮事件


    // 火狐浏览器中支持DOMMouseScroll事件     ev.detail   向上为负,向下为正
     // 非火狐浏览器才支持onmousewheel事件    ev.wheelDelta   向上为正，向下为负

```html
 <!DOCTYPE html>
 <html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>01_滚轮事件</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
   #wrap {
        width: 200px;
        height: 200px;
        background: pink;
        position: absolute;
        left: 0;
        right: 0;
        top: 0;
        bottom: 0;
        margin: auto;

    }
</style>
</head>

<body>
    <div id="wrap"> </div>
</body>
<script>
    window.onload = function () {
        var wrapNode = document.querySelector("#wrap");
        if (wrapNode.addEventListener) {
             // 火狐浏览器中支持DOMMouseScroll事件
        wrapNode.addEventListener("DOMMouseScroll", function (ev) {
            ev = ev || event;
            console.log(ev.detail);
            // ev.detail   向上为负,向下为正
        })
    }

    // 非火狐浏览器才支持onmousewheel事件
    wrapNode.onmousewheel = function (ev) {
        ev = ev || event;
        console.log(ev.wheelDelta);
        // ev.wheelDelta   向上为正，向下为负
    }

}
</script>

</html>
```

#### 滚轮事件练习


```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>滚轮事件练习</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }

        #wrap {
            width: 100%;
            height: 200px;
            background: pink;
            }
     </style>
   </head>   
    <body>
        <div id="wrap">
   </div>
</body>
<script>
    window.onload = function () {
        var wrapNode = document.querySelector("#wrap");
        if (wrapNode.addEventListener) {

            // 火狐浏览器中支持DOMMouseScroll事件
            wrapNode.addEventListener("DOMMouseScroll", fn)
        }

        // 非火狐浏览器才支持onmousewheel事件
        wrapNode.onmousewheel = fn;

        var dir = "";
        function fn(ev) {
            ev = ev || event;
            if (ev.wheelDelta) {
                dir = ev.wheelDelta > 0 ? "向上滚动" : "向下滚动";
            }
            if (ev.detail) {
                dir = ev.detail > 0 ? "向下滚动" : "向上滚动";
            }
            switch (dir) {
                case "向上滚动":
                    wrapNode.style.height = wrapNode.offsetHeight - 10 + "px"
                    break;
                case "向下滚动":
                    wrapNode.style.height = wrapNode.offsetHeight + 10 + "px"
                    break;

            }
            // 禁止事件的默认行为
            // 火狐浏览器,dom2
            if (ev.preventDefault) {
                ev.preventDefault();
            }
            // 非火狐浏览器 dom0
            return false;
        }

    }
</script>

</html>
```


### DOM相关api

```html
<!DOCTYPE html>
<html lang="en" id="html">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>parentNode</title>
    <style>
        #inner2 {
            position: absolute;
        }
        #wrap {
        position: relative;
    }
</style>
</head>

<body id="body">
    <div id="wrap">
        wrap
        <div id="inner1">
            inner1
            <div id="inner2">
                inner2
            </div>
        </div>

     </div>
 </body>
 <script type="text/javascript">
    /*
        js方面的兼容性问题
        ev  || event
        鼠标滚轮  （火狐浏览器兼容性问题较大）
        事件绑定
        offsetParent
           1.父级是否有定位（4种）
           2.本身是否有定位（4种）
           3.浏览器不一样（5大PC浏览器 + IE(6 7 8)）
           共128种
     IE7以上：          
         不论父级有没有定位，只要本身定位为fixed
               ==》 offsetParent:null（ie7以上（不是火狐）  ）
                ==》 offsetParent:body（火狐）
          本身定位不为fixed（IE7以上的浏览器包括火狐）
             父级没有定位：
                   ==》 offsetParent:body
             父级有定位：
                  ==》 offsetParent:定位父级
        如果body和html之间的margin被清掉了。IE7以下与IE7以上的结论相同

    IE7以下，如果当前元素的某个父级触发了haslayout,那么offsetParent就会指向到这个触发了layout特性的父节点上（最常见的触发haslayout的属性就是  overflow: hidden;）
    
     ### 注意点
        
     1.分清parentNode和offsetParent的区别
        parentNode：直接父级
               parentNode表示直接父级，不论包含块是怎样，都表示的是当前元素的直接父级  
       
        offsetParent：类似于CSS的包含块

    2.offsetParent的作用：
       offsetLeft和offsetTop是参照于offsetParent的内边距边界的

    3.dom里所有的元素都是有offsetLeft和offsetTop的，只要有offsetParent

    */

    window.onload = function () {
        var inner2 = document.querySelector("#inner2");
        // parentNode表示直接父级，不论包含块是怎样，都表示的是当前元素的直接父级
        console.log(inner2.parentNode.id);
    }
</script>

</html>

```


#### offsetparent

     // offsetLeft&offsetTop是所有元素共有的，只要有offsetParent 
    /*
     IE7以上：
     
       不论父级有没有定位，只要本身定位为fixed
               ==》 offsetParent:null（ie7以上（不是火狐）  ）
                ==》 offsetParent:body（火狐）
      本身定位不为fixed（IE7以上的浏览器包括火狐）
             父级没有定位：
                   ==》 offsetParent:body
             父级有定位：
                   ==》 offsetParent:定位父级
                                
     如果body和html之间的margin被清掉了。IE7以下与IE7以上的结论相同
    
     IE7以下，如果当前元素的某个父级触发了haslayout,那么offsetParent就会指向到这个触发了layout特性的父节点上（最常见的触发haslayout的属性就是  overflow: hidden;）
    */


#### 获取元素的绝对位置，相对位置和视口尺寸

            // 获取元素在页面中的位置
            // 绝对位置：到body的距离
            // 相对位置：到视口的距离
    
            // 可以通过element对象的getBoundingClientRect（）方法来获取元素的四个角的相对位置，返回值为一个对象，对象中的值为：height、width、left、top、right、bottom
            // getBoundingClientRect+滚动条滚动时元素滚动的距离   -----》元素的绝对位置
    
            // 代表元素border-box 的尺寸
            //  height
            //  width
    
            // 代表元素左上角的相对位置
            //  left
            //  top
    
            // 代表元素右下角的相对位置
            //  right
            //  bottom
            
            // document.documentElement.clientWidth并不是根标签的可视区域，就是视口的大小
            // document.documentElement.offsetWidth才是根标签的border-box的大小


```html
/* 获取元素的绝对位置，相对位置和视口尺寸 */
<!DOCTYPE html>
<html lang="en" id="html">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>05_获取元素的绝对位置</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }

        html,
        body {
            overflow: hidden;
            height: 100%;
        }

        #wrap {
            position: absolute;
            background: pink;
            left: 200px;
            top: 200px;
        }

        #inner1 {
            position: absolute;
            background: deeppink;
            left: 150px;
            top: 150px;
        }

        div {
            width: 200px;
            height: 200px;
        }
    </style>
</head>

<body id="body">
    <div id="wrap">
        wrap
        <div id="inner1">
            inner1

        </div>

    </div>
</body>
<script type="text/javascript">
    window.onload = function () {
        // 获取元素在页面中的位置
        // 绝对位置：到body的距离
        // 相对位置：到视口的距离

        // 可以通过element对象的getBoundingClientRect（）方法来获取元素的四个角的相对位置，返回值为一个对象，对象中的值为：height、width、left、top、right、bottom
        // getBoundingClientRect+滚动条滚动时元素滚动的距离   -----》元素的绝对位置

        // 代表元素border-box 的尺寸
        //  height
        //  width

        // 代表元素左上角的相对位置
        //  left
        //  top

        // 代表元素右下角的相对位置
        //  right
        //  bottom

        var inner1 = document.querySelector("#inner1");

        // point即为inner1的绝对位置
        var point = getPointAb(inner1);
        console.log(point);
        // 如果存在border和margin存在会影响函数的取值
        function getPointAb(node) {
            // while循环叠加offsetParent的offsetLeft和offsetTop
            var x = 0;
            var y = 0;
            while (node) {
                x += node.offsetLeft;
                y += node.offsetTop;
                node = node.offsetParent;
            }
            return { x: x, y: y };
        }
         // document.documentElement.clientWidth并不是根标签的可视区域，就是视口的大小
        // document.documentElement.offsetWidth才是根标签的border-box的大小
        var w = document.documentElement.clientWidth;
        var h = document.documentElement.clientHeight;
    }
</script>

</html>
```

### 文档流

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>文档流</title>
    <style>
        .box1 {
            width: 100px;
            background: #bbffaa;
        }
        .box2 {
        width: 100px;
        background: #000000;
    }

    span {
        background: #bdbdbd;
    }
</style>
</head>

<body>
<!-- 
    文档流（normal flow）
     网页是一个多层的结构，一层摞着一层，通过css可以分别为每一层设置样式，作为用户只能看到最顶上的一层，这些层中，最底下的一层称为文档流。文档流是网页的基础。
     我们所创建的元素默认都是在文档流中进行排列的。
     对于我们来说，元素主要有两个状态：
                    --在文档流中
                    --不在文档流中（脱离文档流）

    元素在文档流中的特点：
       块元素：
           --块元素会在页面中独占一行（自上向下垂直排列）
           --默认宽度是父元素的全部（会把父元素撑满）
           --默认高度是被内容撑开（子元素撑开）,元素有多少，高度就是多少
       行内元素
            --行内元素不会独占页面中的一行，只占自身的大小
            --行内元素在页面中自左向右水平排列，如果一行之中不能容纳所有的行内元素，则元素会换到第二行继续自左向右排列（和习惯的书写顺序一致）
            --行内元素的默认宽度和默认高度都是被内容撑开

   脱离文档流的特点：

       块级元素：
           1.块元素不在独占一行
           2.脱离文档流后，块级元素的宽度和高度默认都会被内容撑开

       行内元素：
             行内元素脱离文档流后会变成块级元素，其特点和块级元素相同。

       脱离文档流后，就不需要再区分块级元素和行内元素了。

 -->
 <div class="box1">div1</div>
<div class="box2">div2</div>
<span>
    span1
</span>
<span>
    span2
</span>

</body>

</html>
```

### 长度单位


```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>单位</title>
    <style>
        .box1 {
            /* 
            长度单位：
                像素   
                    屏幕（显示器）实际上是由一个个发光的小点点构成的
                    不同屏幕的像素大小是不同的，像素越小的屏幕显示的效果就越清晰，所以同样的200px在不同的设备下显示的效果是不一样的。
                百分比
                   -也可以将属性值设置为相对于其父元素属性的百分比
                   设置百分比可以使子元素跟随父元素的改变而改变
                em
                    em是相对于元素的字体大小来计算的，是相对于自身的字体大小
                    1em = 1font-size
                    em会根据字体大小的改变而改变

                rem
                    rem是相对于根元素（html）的字体大小来计算的
         */
        width: 200px;
        height: 200px;
        background: orange;
    }

    .box2 {
        width: 10em;
        height: 10em;
        background: yellow;
    }
</style>
</head>

<body>
    <div class="box1">
    </div>
    <div class="box2">

    </div>
</body>

</html>
```

### 颜色（RGB、hsl）


```html
 <!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .box1 {
            width: 100px;
            height: 100px;
            /* 
             颜色单位：
                 在css中可以直接使用颜色名来设置各种颜色，例如red、yellow、green、blue等等
                    但是在css中直接使用颜色名是非常不方便的

                RGB：
                  RGB是通过三种颜色的不同浓度来调配处不同的颜色，RGB为光的三原色。
                  R:red，G：green，B：blue
                  每一种颜色的范围在0-255（0% - 100%）之间。
                  语法：rgb(红色，绿色，蓝色)
                  rgb(0,0,0)为黑色
                  rgb(255,255,255)为白色

                rgba:就是在RGB的基础上增加了一个a表示不透明度，1表示不透明，0表示全透明
                需要四个值，前三个和rgb一样，第四个表示不透明度，取值在0-1之间

                16进制的RGB值
                语法：#红色绿色蓝色
                颜色浓度通过00-ff表示
                如果颜色两位重复可以进行简写 
                #aabbcc ==>#abc
                但#aabbcd 就不能使用简写

                hsl值
                  H:色相（0-360）
                  S:饱和度 颜色浓度（0%  - 100%）
                  L:；亮度颜色亮度（0% - 100%）

                hsla值
                a为不透明度，其余的同hsl值一样
             */
            background: red;
        }
    </style>
</head>

<body>
    <div class="box1"></div>
</body>

</html>
```



### 浮动

#### 浮动的定义及其特点

       /* 
                  通过浮动可以使一个元素向其父元素的左侧或右侧移动
                    使用float属性来设置元素的浮动
    
                    float 可选值：
                        none:  默认值 ，不浮动
                        left：元素向左浮动
                        right：元素向右浮动
    
                    元素设置浮动以后，水平布局的等式便不需要强制成立了
                    元素设置浮动以后，会完全从文档流中脱离，不在占据文档流中的位置，所以元素下边的还在文档流中的元素会自动向上移动
                                    浮动的特点：
                         1.浮动元素会完全脱离文档流，不再占据文档流中的位置
                         2.设置浮动后，元素会向父元素的左侧或右侧移动
                         3.浮动元素默认不会从父元素中移出
                         4.水平方向上，浮动元素向左或向右移动时，不会超过它前面的其他的浮动元素
                         5.如果浮动元素的上边是一个没有浮动的块级元素，则浮动元素将无法上移
                         6.在垂直方向上，浮动元素不会超过它前面的浮动的兄弟元素，最多是和它一样高
                         7.浮动元素不会盖住文字，文字会自动环绕在浮动元素的周围，所以可以利用浮动来设置文字环绕图片的效果
                         8.元素设置浮动以后，将会从文档流中脱离，从文档流中脱离后，元素的一些特点也会发生变化
                                           
               浮动会提升元素的层级，会提升半个层级，一个元素分为两层，上层是文字相关的，下层是盒模型相关的。
         
                脱离文档流的特点：
                        块级元素：
                               1.块元素不在独占一行
                               2.脱离文档流后，块级元素的宽度和高度默认都会被内容撑开。
        
                       行内元素：
                               行内元素脱离文档流后会变成块级元素，其特点和块级元素相同。
        
                  脱离文档流后，就不需要再区分块级元素和行内元素了。
            */

#### 高度塌陷

       /* 
              高度塌陷问题
    
                 在浮动的布局中，父元素的高度默认是被子元素撑开的。
                 
                 当子元素浮动后，其会完全脱离文档流，子元素从文档流中脱离，将会无法撑起父元素的高度，导致父元素的高度丢失，出现高度塌陷问题
    
                 父元素高度丢失以后，其下的元素会自动上移，导致页面的布局混乱。高度塌陷问题是浮动布局中比较常见的一个问题，这个问题必须要进行处理。
     */


#### BFC

         /*
            BFC（Block Formatting Context）块级格式化环境，它是一个独立的渲染区域，只有Block-level box 参与，它规定了内部的Block-level Box如何布局，并且与这个区域外部毫不相干。
            
            BFC是CSS中的一个隐含的属性，可以为一个元素开启BFC，开启BFC的元素会变成一个独立的布局区域。
            
            BFC布局规则：
                1. 内部的Box会在垂直方向，一个接一个地放置。（块级元素独占一行）
                2. BFC的区域不会与float box重叠。（可设计实现两列布局）
                3. 内部的Box垂直方向的距离由margin决定，属于同一个BFC的两个相邻Box的margin会发生重叠。
                4. 计算BFC的高度时，浮动阿匀速也会参与计算（清除浮动 haslayout）
                5. BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素，反之也是如此。
            
            BFC什么时候出现（哪些元素会生成BFC？）
                  根元素
                  float属性不为none
                  position为absolute或者fixed
                  overflow不为visible
                  display为inline-block、table-cell、table-caption、flex、、inline-flex
    
               元素开启BFC后的特点：
                   1.开启BFC的元素不会被浮动元素所覆盖
                   2.开启BFC的元素子元素和父元素的外边距不会发生重叠
                   3.开启BFC的元素可以包含浮动的子元素
                   
              可以通过一些特殊的方式来开启元素的BFC(所有的开启BFC的方式都会有一些副作用)
                       1. 设置元素的浮动。（副作用：下方元素会自动上移）（不推荐使用）
                       2. 将元素设置为行内块元素。 （副作用：宽度没有了，而且行内块不适合作为外部的布局容器）（不推荐使用）
                       3. 将元素的overflow设置为一个非visible（非默认值）的值。（副作用较小，是一个临时的解决方式）
                            常用的方式，为元素设置 overflow: auto; 或overflow: hidden;来开启BFC,使其可以包含浮动元素
                       4. 也可以通过设置绝对定位为absolute或者固定定位fixed来解决高度塌陷问题，但是并不推荐，也会造成父元素的高度丢失问题
                       5. 为父元素添加一个空的div标签，设置div标签的样式为（clear:both;）但这样会添加一个多余的div元素，造成代码冗余
                       6. 完美的解决方案：父元素通过after伪元素来解决问题
                                    父元素::after{
                                        content: '';
                                        display: block;
                                        clear: both;
                                    }
          */

##### 通过BFC实现两列布局

左边固定，右边自适应。

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记-两列布局</title>
    <style>
    /* BFC的区域不会与float box重叠。（可设计实现两列布局） */
      /* 通过开启BFC实现两列布局 */
      * {
        margin: 0;
        padding: 0;
      }
      body {
        min-width: 600px;
      }
      div {
        height: 200px;
      }
      .left {
        width: 200px;
        background: #bfa;
        float: left;
      }
      .right {
        /* 开启BFC即可 */
        overflow: hidden;
        background: pink;
      }
    </style>
  </head>
  <body>
    <div class="left">左侧区域</div>
    <div class="right">右侧区域</div>
  </body>
</html>
```

##### BFC实现商品列（两列布局的应用）

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记-两列布局应用-商品列</title>
    <style>
      * {
        margin: 0;
        padding: 0;
      }
      .container {
        width: 300px;
        border: 1px solid;
        margin: 50px auto; /* 在浮动或者定位的时候如此设置会失效 */
      }
      .left {
        float: left;
        width: 100px;
        height: 100px;
        background: url("./img/111.png") no-repeat;
        background-position: -50px -50px;
      }
      .right {
        padding-left: 30px;

        /* 让溢出的文字显示省略号,这四个缺一不可 */
        display: block;
        white-space: nowrap;
        text-overflow: ellipsis;
        overflow: hidden;
      }
    </style>
  </head>
  <body>
    <div class="container">
      <div class="left"></div>
      <div class="right">
        哈哈哈哈哈哈，清仓大甩卖了啊啊啊啊啊啊啊啊啊啊
        哈哈哈哈哈哈，清仓大甩卖了啊啊啊啊啊啊啊啊啊啊
        哈哈哈哈哈哈，清仓大甩卖了啊啊啊啊啊啊啊啊啊啊
      </div>
    </div>
  </body>
</html>
```

##### margin叠加

margin重叠出现的前提： 内部的Box垂直方向的距离由margin决定，属于同一个BFC的两个相邻Box的margin会发生重叠，即同一个BFC，相邻的Box,只需要破坏这个前提就可以解决margin重叠的问题。

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记-margin叠加</title>
    <style>
      /* 内部的Box垂直方向的距离由margin决定，属于同一个BFC的两个相邻Box的margin会发生重叠 */
      * {
        margin: 0;
        padding: 0;
      }
      .up,
      .down {
        width: 200px;
        height: 200px;
        background: pink;
        margin: 50px;
      }
    </style>
  </head>
  <body>
    <div class="up">upupupupupupupupup</div>
    <!-- 若不想要margin出现重叠，只需要让两个元素不直接相邻即可，即破坏两个box的相邻
    但只是单纯的加一个空的div是不行的，因为div很干净 ，空的span也不行，br元素默认有21px的高度，也不适用，
    建议在外层在包一层div，并设置样式为overflow:hidden-->
    <div style="overflow: hidden">
      <div class="down">downdowndowndowndowndowndown</div>
    </div>
  </body>
</html>
```

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记-margin叠加2</title>
    <style>
      * {
        margin: 0;
        padding: 0;
      }
      .wraper {
        width: 300px;
        height: 300px;
        background: pink;
        margin: 50px;
        /* 开启BFC,使两个元素不属于同一个BFC即可,即破坏margin重叠的前提条件 */
        overflow: hidden;
      }
      .wraper .inner {
        width: 100px;
        height: 100px;
        background: purple;
        margin: 50px;
      }
    </style>
  </head>
  <body>
    <div class="wraper">
      <div class="inner"></div>
    </div>
  </body>
</html>
```



#### 清除浮动clear

    <!DOCTYPE html>
    <html lang="en">
    
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>clear</title>
        <style>
            div {
                font-size: 50px;
            }
    
            .box1 {
                width: 200px;
                height: 200px;
                background: #bbffaa;
                float: left;
            }
    
            .box2 {
                width: 400px;
                height: 400px;
                background: green;
                float: right;
            }
    
            .box3 {
                width: 200px;
                height: 200px;
                background: orange;
                clear: left;
            }
    
            /* 
               由于box1的浮动，导致box3位置上移，也就是说box3受到了box1浮动的影响，位置发生了改变
    
               如果我们不希望某个元素因为其他元素浮动而受到影响而改变位置，可以通过设置clear属性来清除浮动元素对当前元素产生的影响
            
               clear  作用：清除浮动元素对当前元素产生的影响
                      可选值：
                             left  清除左侧浮动元素对当前元素产生的影响
                             right 清除右侧浮动元素对当前元素产生的影响
                             both  清除两侧中最大影响的那一侧
                         原理：设置清除浮动以后，浏览器会自动为元素添加一个上外边距，以使其位置不受其他元素的影响
    
             */
        </style>
    </head>
    
    <body>
        <div class="box1">1</div>
        <div class="box2">2</div>
        <div class="box3">3</div>
    </body>
    
    </html>

#### after伪元素解决高度塌陷问题

         /* 
             解决高度塌陷问题的最好的方式：
             使用::after伪元素，
                子类元素设置浮动以后，父元素通过使用::after伪元素来设置父元素的样式，
                首先，通过content属性设置after后的字符为空，其次通过clear属性设置清除子元素的浮动的影响，最后设置父元素的after伪元素为块级元素即可完美解决高度塌陷问题。
                    父元素::after {
                        content: '';
                        display: block;
                        clear: both;
                    }
                
              */

#### clearfix

    <!DOCTYPE html>
    <html lang="en">
    
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>clearfix</title>
        <style>
            .box1 {
                width: 200px;
                height: 200px;
                background: purple;
    
            }
    
            /* .box1:before {
                content: '';
                display: table;
            } */
    
            .box2 {
                width: 100px;
                height: 100px;
                background: #bbffaa;
                margin-top: 100px;
            }
    
            /* 此样式可以同时解决外边距重叠问题和由于浮动导致的高度塌陷问题 */
            .clearfix::before,
            .clearfix::after {
                content: '';
                display: table;
                clear: both;
            }
        </style>
    </head>
    
    <body>
        <div class="box1 clearfix" >
            <div class="box2"></div>
        </div>
    </body>
    
    </html>

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记-清除浮动</title>
    <!-- 
       清除浮动：
           让浮动的子元素可以撑开父元素的高度

           1. 直接给父级加高度（扩展性不好）
           2. 父级元素开启BFC（float、position、 overflow、 display四种属性均可）
                 浮动盒子的特点和定位盒子的特点：宽高都由内容撑开
                    （页面中所有的元素都加浮动，margin左右自动失效）
           3. 空标签清除浮动（但不符合工作中 结构、样式、行为三者分离的要求）,
                             <br clear="all" />(clear是HTML标签的的一个属性)
                             或者 <div style="clear:both"></div>（此时的clear是HTML标签的style属性的css样式）
           4. after伪元素清除浮动，建议使用此种方式
     -->
    <style>
      * {
        margin: 0;
        padding: 0;
      }
      .wraper {
        border: 1px solid;

        width: 600px;
      }
      .inner {
        float: left;
        width: 200px;
        height: 200px;
        background: pink;
      }
      .clearfix:after {
        display: block;
        content: "";
        clear: both;
      }
    </style>
  </head>
  <body>
    <div class="wraper clearfix">
      <div class="inner"></div>
      <!-- <br clear="all" /> -->
      <!-- <div style="clear: both"></div> -->
    </div>
  </body>
</html>
```



### 常见的布局

位置的变动通过定位的left和top，调整边界用margin，盒模型通过margin、border、width来控制，只是改变了盒模型的大小等，实际上元素的位置并没有变动，只是盒模型的被改变的地方没有任何样式而已，没有填充背景和边框等。

#### 三列布局

* 1. 两边固定，中间自适应。
* 2. 中间项的内容要完整显示。
* 3. 中间项要优先加载

##### 通过定位实现三列布局

通过定位实现三列布局，缺点是缩小到一定距离后，即使小于最小宽度了，会出现滚动条，但中间的内容依旧会丢失，故不推荐使用。

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记</title>
    <style>
      * {
        margin: 0;
        padding: 0;
      }
      body{
          /*最小宽度的取值为： (2 * left )+ right 或者 left + (2 * right) */
          min-width: 600px;
      }
      div {
        height: 100px; 
      }
      .left,
      .right {
        width: 200px;
        background: #bfa;
      }
      .left {
        position: absolute;
        left: 0;
        top: 0;
      }
      .right {
        position: absolute;
        right: 0;
        top: 0;
      }
      .middle {
        padding: 0 200px;    /* 解决中间内容区的内容不能完整显示的方法 */
        background: pink;
      }
    </style>
  </head>
  <body>
    <!-- 
        1. 两边固定，中间自适应。
        2. 中间项的内容要完整显示

        通过定位实现三列布局，缺点是缩小到一定距离后，即使小于最小宽度了，会出现滚动条，但中间的内容依旧会丢失，故不推荐使用
     -->

    <div class="left">left</div>
    <div class="middle">
      middle 11111 middle middle middle middle middle middle middle middle
    </div>
    <div class="right">right</div>
  </body>
</html>
```

##### 通过浮动实现三列布局

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记</title>
    <style>
      * {
        margin: 0;
        padding: 0;
      }
      body {
        /*最小宽度的取值为： (2 * left )+ right 或者 left + (2 * right) */
        min-width: 600px;
      }
      div {
        height: 100px;
      }
      .left,
      .right {
        width: 200px;
        background: #bfa;
      }
      .middle {
        background: pink;
      }
      .left {
        float: left;
      }
      .right {
        float: right;
      }
    </style>
  </head>
  <body>
    <!-- 
        1. 两边固定，中间自适应。
        2. 中间项的内容要完整显示
        3. 中间项要优先加载

        通过浮动实现三列布局，缺点是在网速较慢的情况下会先加载左右两侧的内容，最后在慢慢加载中间的内容区的内容，用户体验感不好
         即使是将中间项放到最上面也不行，中间项放到最上面，左右两侧就浮动不上去了，因为块级元素优先独占一行，默认独占一行。
       
       
         块级元素特点(设置display:block就是将元素显示为块级元素)：

          1、每个块级元素都从新的一行开始，并且其后的元素也另起一行。（一个块级元素独占一行）
          2、元素的高度、宽度、行高以及顶和底边距都可设置。
          3、元素宽度在不设置的情况下，是它本身父容器的100%（和父元素的宽度一致），除非设定一个宽度。
     -->

    <div class="left">left</div>
    <div class="right">right</div>
    <div class="middle">
      middle 11111 middle middle middle middle middle middle middle middle
    </div>
  </body>
</html>
```

#### 圣杯布局

圣杯布局中其实还是使用了相对定位，通过定位来实现布局确实不太好，所以圣杯布局也确实是有点缺点的，就是使用了定位来进行布局，可能会影响页面中三列布局中的各种元素的位置，不希望提升层级和改变文档流。

* 1. 两边固定，中间自适应。
* 2. 中间项的内容要完整显示。
* 3. 中间项要优先加载。

元素与元素之间是有边界的，这个边界就是由margin来控制的，margin是盒模型的最外层。
为了解决下面的左右两侧的元素上不去的情况，则给中间的内容区也设置样式为浮动，并使用 clearfix 来清除浮动，（浮动元素在高度上是撑不开父级的，浮动元素的宽高是由内容区撑开的）

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记-圣杯布局</title>
      <style type="text/css">
      * {
        margin: 0;
        padding: 0;
      }
       body{
          min-width: 600px;
      }
      .header,
      .footer {
        height: 80px;
        text-align: center;
        border: 1px solid;
        background: #bfa;
      }
      .content {
        padding: 0 200px;
 /*  注意，设置了content元素的padding后，此时的内容区宽度已经变小了，若想让左右两侧的元素出来则需要通过给左右两侧元素设置相对定位，使其出来即可。 */
      }
      .content .middle {
        float: left;
        width: 100%;
        background: pink;
        /* padding: 0 200px;  */
        /* 此时不能如此设置，因为此时的width已经设置过了，再设置padding就相当于是给middle元素的左右增加了200px ，应该给content容器增加200px的左右padding*/
      }
      .content .left {
        float: left;
        width: 200px;
        /* margin为负值，只改变元素的边界，不改变元素的位置 */
        /* 设置左边元素的边界为向左移动一个content宽度，但注意，这样只是改变了边界，元素的位置并没有改变，
        虽然元素上去了，这是因为left的边界改变了，content元素自动向下拓展了，此时的margin-left值必须要和content元素的width值完全相同 */
        margin-left: -100%;
        background: bisque;
        position: relative;
        left: -200px;
        top: 0;
      }
      .content .right {
        float: left;
        width: 200px;
        margin-left: -200px;
        background: green;
        position: relative;
        right: -200px;
        top: 0;
      }
      /* 清除content元素的浮动产生的影响 */
      .clearfix:  {
        content: "";
        display: block;
        clear: both;
      }
    </style>
  </head>
  <body>
    <!-- 
        1. 两边固定，中间自适应。
        2. 中间项的内容要完整显示。
        3. 中间项要优先加载。

        圣杯布局技术点总结：

           浮动：搭建完整的布局框架
           margin为负值：调整旁边两列的位置（使三列布局显示到一行上）
           使用相对定位：调整旁边两侧的位置（使两侧元素的位置调整到两头，暴露出来）
     -->
    <div class="header">
      header
      每个块级元素都从新的一行开始，并且其后的元素也另起一行。（一个块级元素独占一行）
    </div>
    <div class="content clearfix">
      <div class="middle">
        finally()
        方法返回一个Promise。在promise结束时，无论结果是fulfilled或者是rejected，都会执行指定的回调函数。这为在Promise是否成功完成后都需要执行的代码提供了一种方式。
        这避免了同样的语句需要在then()和catch()中各写一次的情况。
      </div>
      <div class="left">left</div>
      <div class="right">right</div>
    </div>
    <div class="footer">
      footer
      元素宽度在不设置的情况下，是它本身父容器的100%（和父元素的宽度一致），除非设定一个宽度。
    </div>
  </body>
</html>
```

```
//注意，此时的元素的高度只是被默认撑开，左右两侧和中间内容区不会等高，可以通过伪等高布局来设置，但注意，伪等高布局的overflow需要设置为hidden，如果需要使用overflow的其他值的时候就不适合使用伪等高布局了。
修改的css样式如下：
    <style type="text/css">
    
      .content {
        padding: 0 200px;
        overflow: hidden;
     /*  注意，设置了content元素的padding后，此时的内容区宽度已经变小了，若想让左右两侧的元素出来则需要通过给左右两侧元素设置相对定位，使其出来即可。 */
      }
      /* 设置伪等高布局，保证中间的三列布局是等高的，不会出现一个高一个低的现象 */
      .content .middle,
      .content .left,
      .content .right {
          padding-bottom: 10000px;
          margin-bottom: -10000px;
      }
    </style>
```

#### 双飞翼布局

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记-双飞翼布局</title>
    <style>
      * {
        margin: 0;
        padding: 0;
      }
      body {
        min-width: 600px;
      }
      /* 伪等高布局样式 */
      .content .middle,
      .content .left,
      .content .right {
        padding-bottom: 10000px;
        margin-bottom: -10000px;
      }
      /* 隐藏多余的超出边界范围的元素 */
      .content {
        overflow: hidden;
      }
      /* 其他样式 */
      /* 头部和尾部样式 */
      .header,
      .footer {
        height: 80px;
        border: 1px solid;
        background: gray;
        text-align: center;
      }
      /* 双飞翼布局样式 */
      .content .middle {
        width: 100%;
        background: pink;
        float: left;
      }
      /* 与圣杯布局的不同之处，需要在html中多加了一个元素标签  */
      .content .middle .m-inner {
        padding: 0 200px;
      }
      .content .left,
      .content .right {
        background: greenyellow;
        width: 200px;
        text-align: center;
        float: left;
      }
      .content .left {
        margin-left: -100%;
      }
      .content .right {
        margin-left: -200px;
      }
      .clearfix::after {
        content: "";
        display: block;
        clear: both;
      }
    </style>
  </head>
  <body>
    <div class="header">
      <h4>Header</h4>
    </div>
    <div class="content clearfix">
      <div class="middle">
        <div class="m-inner">middle<br /></div>
      </div>
      <div class="left">
        left<br />
        left<br />
      </div>
      <div class="right">
        right <br />
        right <br />
      </div>
    </div>
    <div class="footer">
      <h4>Footer</h4>
    </div>
  </body>
</html>
```

两者的不同之处：

1. 两种布局方式都是把主列放在文档流最前面，使主列优先加载。

2. 两种布局方式在实现上也有相同之处，都是让三列先进行浮动，然后通过负外边距形成三列布局。

3. 两种布局方式的不同之处在于如何处理中间主列的位置：

   ​       圣杯布局是利用父容器的左、右内边距+两个丛列相对定位。

   ​       双飞翼布局是把主列嵌套在一个新的父级块中，利用主列的左、右外边距进行布局调整（没有使用到定位）。

```
如果HTML和body的样式中均写了`overflow属性`，则HTML的滚动条依旧作用给文档流，而body上的滚动条则会作用给自己，即body上是否出现滚动条取决于body上的overflow属性值。

如果HTML或body其中一个的样式写了`overflow属性`，则滚动条会出现在文档流上。
```

#### 禁止系统的默认滚动条

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记-禁止系统默认滚动条</title>
    <style>
      /* 禁止系统的默认滚动条 */
      html,
      body {
        height: 100%; /* 让body继承HTML的大小，HTML的大小又继承与浏览器视口的大小，即body的大小就是浏览器视口的大小 */
        overflow: hidden;
      }
    </style>
  </head>
  <body>
    <div style="height: 1000px"></div>
  </body>
</html>
```

#### 使用绝对定位模拟固定定位

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记-使用绝对定位模拟固定定位</title>
    <style>
        /* 使用绝对定位模拟固定定位，移动端使用较多 */
      * {
        margin: 0;
        padding: 0;
      }
      html {
        overflow: hidden; /* 隐藏文档流的滚动条，即系统默认的滚动条 */
        height: 100%; /* 继承于初始包含块（文档流）的height的大小  */
      }
      body {
        overflow: auto; /* 作用给自己 让body出现滚动条，实现禁止系统默认滚动条，通过元素的绝对定位模拟元素的固定定位 */
        height: 100%; /* 继承于HTML元素的height的大小  */
      }
      .test {
        position: absolute;
        left: 50px;
        top: 50px;
        width: 100px;
        height: 100px;
        background: fuchsia;
      }
    </style>
  </head>
  <body>
    <div class="test"></div>
    <div style="height: 1000px"></div>
  </body>
</html>
```

#### 粘连布局（footer布局）

经典的“粘连布局”，我们有一块内容区<  main>，当< main>的高度足够长的时候，< footer>应该紧跟在< main>元素的后面；当< main>元素比较短的时候（比如小于屏幕的高度时），我们期望这个< footer>元素能够“粘连”在元素的底部。

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta
      name="viewport"
      content="width=device-width, initial-scale=1.0, user-scalable=no"
    />
    <title>前端小记-粘连布局</title>
    <style>
      * {
        margin: 0;
        padding: 0;
      }
      html,
      body {
        height: 100%;
      }
      .container {
        min-height: 100%;
        background: pink;
      }
      .container .main {
        padding-bottom: 50px;
        /* 当main内容区域的元素过多，导致屏幕出现滚动条时，通过设置此属性来防止main内容区域和footer内容区域重叠，
        此时虽然依旧有重叠，但重叠区域中main内容区没有元素，对整体没有太大影响 */
      }
      .footer {
        height: 50px;
        line-height: 50px;
        background: #bfa;
        text-align: center;
        margin-top: -50px;
      }
    </style>
  </head>
  <body>
    <div class="container">
      <div class="main">
        main主体内容区域<br />
        main主体内容区域<br />
      </div>
    </div>
    <!-- footer布局要求元素必须要放在容器的外部， 不能放在container内部（main的下面）-->
    <div class="footer">footer内容区域</div>
  </body>
</html>
```

###  元素的垂直水平居中

#### 已知宽高的元素的垂直水平居中

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记-已知宽高的元素的垂直水平居中</title>
    <style>
      * {
        margin: 0;
        padding: 0;
      }
      .wrap {
        position: relative;
        width: 400px;
        height: 600px;
        background: pink;
        margin: 0 auto;
      }
      .inner {
        position: absolute;
        left: 50%;
        top: 50%;
        /* 必须要手动计算margin-left和margin-top的值，让元素的边界向左上移动当前元素的一半 */
        margin-left: -50px;
        margin-top: -50px;
        width: 100px;
        height: 100px;
        background: deepskyblue;
      }
    </style>
  </head>
  <body>
    <div class="wrap">
      <div class="inner">
        哈哈哈哈哈哈，inner<br />
        哈哈哈哈哈哈，inner<br />
       
      </div>
    </div>
  </body>
</html>
```

方式二：

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记-已知宽高的元素的垂直水平居中方式二</title>
    <!-- 
        绝对定位盒子的特性：
           宽高由内容撑开
           水平方向上：left + right + width + padding + margin = 包含块padding区域的尺寸。
           垂直方向上：top + bottom + height + padding + margin = 包含块padding区域的尺寸。
     -->
    <style>
      * {
        margin: 0;
        padding: 0;
      }
      .wrap {
        position: relative;
        width: 400px;
        height: 600px;
        background: pink;
        margin: 0 auto;
      }
      .inner {
        position: absolute;
        /* left、top、right、bottom四个元素均为0，margin必须为auto，缺一不可 */
        left: 0;
        top: 0;
        right: 0;
        bottom: 0;
        margin: auto;
        width: 100px;
        height: 100px;
        background: deepskyblue;
      }
    </style>
  </head>
  <body>
    <div class="wrap">
      <div class="inner">
        哈哈哈哈哈哈，inner<br />
        哈哈哈哈哈哈，inner<br />
      </div>
    </div>
  </body>
</html>
```

#### 未知宽高的元素的垂直水平居中

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记-未知宽高的元素的垂直水平居中</title>
    <style>
      * {
        margin: 0;
        padding: 0;
      }
      .wrap {
        position: relative;
        width: 400px;
        height: 600px;
        background: pink;
        margin: 0 auto;
      }
      .inner {
        position: absolute;
        left: 50%;
        top: 50%;
        /* 此属性中的百分比参照的元素自身的宽高，让其在x轴上向左平移自身的一半宽度，在y轴上向上平移自身的一半高度，z轴上不动 */
        /* 但此属性的兼容性不太好，可能会存在兼容性问题 */
        transform: translate3d(-50%, -50%, 0);
        background: fuchsia;
      }
    </style>
  </head>
  <body>
    <div class="wrap">
      <div class="inner">
        哈哈哈哈哈哈，inner<br />
        哈哈哈哈哈哈，inner<br />
      </div>
    </div>
  </body>
</html>
```

#### 单行文本垂直居中

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记-单行文本垂直居中</title>
    <style>
      * {
        margin: 0;
        padding: 0;
      }
      /* 将行高设置的和元素的高度一致即可实现单行文本的垂直居中 */
      .container {
        height: 200px;
        line-height: 200px;
        background: pink;
      }
    </style>
  </head>
  <body>
    <div class="container">哈哈哈哈哈哈哈哈哈哈哈哈哈哈</div>
  </body>
</html>
```

#### 图片的垂直水平居中

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记-图片垂直水平居中</title>
    <style>
      /* 此方式只对inline-block的元素有效,例如 img、input等，浮动，定位的元素都是不可以这样做的 */
      * {
        margin: 0;
        padding: 0;
      }
      /* 在容器中通过after伪元素创建一个可以撑满列的元素（宽度为0，高度为100%），
      设置display为inline-block，并设置vertical-align为middle，这样，容器下的图片就有了参照，
      再设置容器下的img标签样式为vertical-align:middle，让两者的对其方式按照after伪元素的对其方式对齐，即可实现图片的垂直水平居中 */
      .wrap {
        height: 400px;
        width: 400px;
        border: 1px solid;
        margin: 0 auto;
        text-align: center;
      }
      .wrap::after {
        content: "";
        width: 0px;
        height: 100%;
        display: inline-block;
        vertical-align: middle;
      }
      .wrap img {
        vertical-align: middle;
      }

 /* 
  vertical-align： 用来指定行内元素（inline）或表格单元格（table-cell）元素的垂直对齐方式。只对行内元素、表格单元格元素生效，不能用它垂直对齐块级元素。
                      初始值：baseline   不可被继承
                      使用最多的是img和input元素，参照于行框中行内框最高的元素进行定位
      参考链接：https://developer.mozilla.org/zh-CN/docs/Web/CSS/vertical-align
*/
    </style>
  </head>
  <body>
    <div class="wrap">
      <img src="./img/0000.png" width="200" alt="哈哈" />
    </div>
  </body>
</html>
```

### 字体相关的属性

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记-字体相关属性</title>
    <style>
      * {
        margin: 0;
        padding: 0;
      }
      /*
      font-size : 指定字体的大小，该属性的值会被用于计算em长度单位。
                  默认值：medium (Chrome下为16px，最小为12px，当这个值小于12px时均渲染成12px，当这个值为负数时，则会渲染成默认值16px)，可继承,
             取值有很多种形式，但暂时只关注的三种值 
             px:像素
             em:em的值的大小是动态的，当定义font-size属性时，1em等于元素的父元素的字体大小
             % ： 参照父元素的字体大小        

        */
      /* 
        font-style : 选择font-family字体下的italic或oblique样式
                     默认值： normal  可继承
                  
                  可选值：
                  normal：选择font-family的常规字体
                  italic: 选择斜体
                  oblique：选择倾斜体

         */
      /* 
         font-weight :指定了字体的粗细程度，一些字体只提供了normal和bold两种值
                     默认值:normal  可继承

                     可选值：
                     normal：正常粗细，与400等值
                     bold:加粗 与700等值
                     lighter：比从父元素继承来的值更细
                     bolder：比从父元素中继承来的值更粗
                     100,200,300,400,500,600,700,800,900  数值化的规定字体粗细程度的方式，提供了除normal和bold之外更多的值
          */

      /* 
          font-family:允许通过给定一个有先后顺序的，由字体名或者字体族名组成的列表来为选定的元素设置字体。属性的值用逗号隔开。
                      默认值：depends on user agent 可继承
           */

      /* 
           font:简写属性,属性值书写顺序有要求，font-style 和font-weight必须在font-size的前面，font-family必须早font-size的后面

            推荐形式：font:font-style font-weight font-size/line-height font-family

            不建议使用此简写属性，可维护性太差，而且顺序不对的话，属性不会生效
            */
      .wrap {
        font-size: 30px;
        font-style: normal;
        font-weight: bold;
        font-family: "Times New Roman", Times, serif;
      }
    </style>
  </head>
  <body>
    <div class="wrap">哈哈哈</div>
  </body>
</html>
```

### 文本相关的属性

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记-文本相关的属性</title>
    <style>
      * {
        margin: 0;
        padding: 0;
      }
      /* 
          行高：指上下文本行的基线间的垂直距离，
          行距：指一行底线到下一行顶线的垂直距离
          行距 = 行高 - 字体大小
          内容区：底线和顶线包裹的区域
          行内框：默认等于内容区域

          如果要处理大量的文本，建议把行高设置的要比字体大
       */

      /* 
       行高的使用：单行文本垂直居中
      */

      /* 
        color: 前景色（字体颜色）
        text-align:控制文本的居中形式，只对内联元素或行内元素有效
        text-indent:控制首行缩进
        text-decoration:underline用来画下划线
        letter-spacing:控制字母与字母之间的间距
        word-spacing:控制单词与单词之间的间距
        white-space:控制文本是否换行（英文之间没有空格的是不会换行的）
        
      */
      .wrap {
        height: 200px;
        line-height: 200px;
        background: hotpink;
      }
    </style>
  </head>
  <body>
    <div class="wrap">哈哈哈哈哈哈哈哈哈</div>
  </body>
</html>
```

## CSS3

### 基础概念

```
 /*
 1.css全称是什么？
 2.样式表是什么，是由什么组成的？
 3.浏览器读取编译css的顺序是从左往右还是从右往左？
 */
 
 /* 
    css全称：Cascading Style Sheets，层叠样式表
*/

/* 
    1. 样式表
    2. 样式表是由规则来组成的 （每一个style标签内部的所有规则组成的就是一个样式表，即 <style type="text/css"></style>包括其内部的所有规则就是一个样式表）
    3. 规则是由选择器+声明块来组成的（例如 *{} 整体上是一个规则，.test{}也是一个规则）
    4. 声明块则是由声明来组成的 （例如：*后面的{}、.test选择器后面的{}）
    5. 声明则是由css属性+css属性值所组成的键值对组成（例如：margin: 0;）
*/

 /* 
    浏览器读取编译css选择器的顺序是从右往左匹配的，这样效率更高。
 */
```

### css声明的优先级

```
css选择器并没有优先级，平常说的css优先级实际上是css声明的优先级
        样式的冲突：
             当我们通过不同的选择器，选中相同的元素，并且为相同的样式设置不同的值,此时就发生了样式的冲突

             发生样式冲突时，应用哪个样式由css声明的优先级来决定。
             当重要声明与非重要声明冲突时，永远是重要声明起作用，即 !important 作用的样式生效，不需要考虑声明的优先级
             当重要声明之间发生冲突时，则在重要声明所组成的组中，对规则中非重要声明的优先级进行比较，优先级高的样式起作用
        
        例如：
        div{ background:pink !important;}    div .test{background:yellow !important}   
        //此时背景色被渲染成黄色，（div 和 .test选择的是同一个元素）
        
         可以在某一个样式的后边添加  !important  ，此时表示为重要声明，则此时该样式会优先被使用，甚至超过内联样式，在开发中要慎用（甚至使用js都无法修改此样式），
         但标志为 !important 的声明并没有特殊的特殊性值，不过要于非重要声明分开考虑，其虽然会导致样式被修改，但并不能改变css声明的优先级

        css声明的优先级（从高到低）（非重要声明）：  
             内联样式          （行内样式）      1,0,0,0
             ID选择器            （#）          0,1,0,0
             类和伪类选择器       （.）          0,0,1,0
             元素和伪元素选择器 （元素标签名）     0,0,0,1
             通配选择器           （*）          0,0,0,0
             继承的样式            没有优先级，0优先级也比没有优先级要高。通配符内部的样式会比继承来的样式优先级高，通配符的样式会优先于继承的样式来生效。
     比较优先级时，需要将所有的css声明的优先级进行相加计算，最后优先级越高，越优先显示（分组选择器是单独计算的（例如：div,p,span{}））
     选择器的累加不会超过其最大的数量级，即 类选择器再高也不会超过ID 选择器
                
     如果优先级计算后相等。此时则优先使用css样式中靠下的样式，即下面的样式的值会覆盖上面的同样属性的属性值
        
  来源
    css样式的来源大致有三种
        创作人员（开发人员）
        读者（用户）
        用户代理 （浏览器），用户代理不存在重要声明
            
  来源的权重（由高到低）：
	 读者的重要声明（Chrome，火狐等浏览器都没有把读者的重要声明暴露出来，即在这些浏览器中没法定义读者的重要声明，但ie浏览器可以设置）
   创作人员的重要声明 （在浏览器的Elements中的element.style中写的带 !important 的样式，等同于写的内联样式中的重要声明，依旧属于开发人员的重要声明）
	 创作人员的正常声明
	 读者的正常声明
	 用户代理的声明
        
  层叠样式表的最终的渲染样式顺序：
		1.找出所有相关的规则，这些规则都包含一个选择器
	    2.计算声明的优先级
	           首先按来源排序
	          （当声明的来源相同时，）在按选择器的特殊性排序
	          （当选择器的特殊性相等时，）最终按顺序展示样式（谁的样式在下面被定义，谁的样式被显示）
```

### css选择器

#### 基本选择器

```
基本选择器包括：
        通配符选择器    *
        id选择器       #
        类选择器       .
        元素选择器     元素标签名
        后代选择器     空格
        分组选择器      ，（结合符）
```

#### 子元素选择器

```
 >  子元素选择器（直接后代选择器）,使用时需要考虑css属性是否是可继承的
 
 //例如：
  .wrap > li {
        border: 1px solid;
  }
```

#### 相邻兄弟选择器

```
+  相邻兄弟选择器，只会匹配紧跟着的兄弟元素，必须是紧跟着的元素，若紧跟着的兄弟元素不是希望匹配到的选择器所对应的元素,即匹配不到，则不会修改样式。

//例如：
 .wrap .first +.inner{
          color: pink;
  }
```

#### 通用兄弟选择器

```
使用 ~ 连接两个元素时，它会匹配第二个元素及其后面的元素，
        条件是 : 希望被匹配的元素必须跟（不一定是紧跟）在第一个元素之后，且他们都有一个共同的父元素
        
 //例如：
     .wrap {
        margin: 50px;
      }
   .wrap .first ~ .inner {
        border: 1px solid;
        width: 600px;
      }     
```

#### 属性选择器--存在和值选择器

```
存在和值属性选择器（css2）	
          [attr]：该选择器选择包含 attr 属性的所有元素，不论 attr 的值为何。
          [attr=val]：该选择器仅选择 attr 属性被赋值为 val 的所有元素。
          [attr~=val]：表示带有以 attr 命名的属性的元素，并且该属性是一个以空格作为分隔的值列表，其中至少一个值为val。
        
子串值属性选择器
          [attr|=val] : 选择attr属性的值是val（包括val）或以val-开头的元素,(只有以val 开头且和其他值有分割的时候和以val-开头时，才能匹配上)。(css2)
          [attr^=val] : 选择attr属性的值以val开头（包括val）的元素。(css3)
          [attr$=val] : 选择attr属性的值以val结尾（包括val）的元素。(css3)
          [attr*=val] : 选择attr属性的值中包含字符串val的元素。(css3)

//例如：
div[name~="haha"] {
        border: 1px solid;
 }
```

#### 伪类选择器--链接伪类

```
 链接伪类（link visited）只对a标签有用 ，而且缓存中的数据会对结果有影响
          :link：表示作为超链接，并指向一个未访问的地址的所有锚  
          由于a标签的:link和:visited可以覆盖了所有a标签的状态，所以当:link，:visited，:hover，:active同时出现在a标签
            身上时,使用的时候需要遵循一个顺序   link visited hover active
            
   注意， :link，:visited，:target是作用于链接元素的！
            :link		表示作为超链接，并指向一个未访问的地址的所有锚
            :visited	表示作为超链接，并指向一个已访问的地址的所有锚
            :target 	代表一个特殊的元素，它的id是URI的片段标识符
            
 //例如：
  a {
      text-decoration: none;
    }
  a:visited {
      color: deeppink;
   }
 .test:link {
    background: pink;
   }
```

####  链接伪类target练习

```
//需求：通过点击页面上不同的某个按钮显示不同的对应的信息。

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记-链接伪类target</title>
    <style type="text/css">
      * {
        margin: 0;
        padding: 0;
      }
      a {
        text-decoration: none;
        color: hotpink;
      }
      div {
        width: 200px;
        height: 200px;
        background: pink;
        display: none;
        text-align: center;
        font: 50px/200px "微软雅黑";
      }
      :target {
        display: block;
      }
    </style>
  </head>
  <body>
    <a href="#div1">div1</a>
    <a href="#div2">div2</a>
    <a href="#div3">div3</a>
    <div id="div1">div1</div>
    <div id="div2">div2</div>
    <div id="div3">div3</div>
  </body>
</html>  
```

#### 伪类选择器--动态伪类

```
  注意, :hover，:active基本可以作用于所有的元素！
          :hover		表示悬浮到元素上
          :active		表示匹配被用户激活的元素（点击按住时）
          
  隐私与    :visited ,只有下列的属性才能被应用到已访问链接。
        允许使用的 CSS 属性为color, background-color, border-color, border-bottom-color, border-left-color,
                           border-right-color, border-top-color, column-rule-color, 和outline-color。
       参考链接：https://developer.mozilla.org/zh-CN/docs/Web/CSS/:visited
       
  //例如：
     .wrap:hover {
        color: pink;
      }
      .wrap:active {
        color: yellow;
      }
      .wrap:visited {
      color: blue;
      }
```

#### 伪类选择器--表单伪类

```
表单相关伪类
      :enabled	匹配可编辑的表单
      :disable	匹配被禁用的表单
      :checked	匹配被选中的表单
      :focus	匹配获得焦点的表单
      
//例如：
      input:enabled {
        background: red;
      }
      input:disabled {
        background: yellowgreen;
      }
      input:checked {
        width: 200px;
        height: 200px;
      }
      input:focus {
        background: #bbb;
      }
```

#### 伪类选择器--结构性伪类

```
    index的值从1开始计数！
      index可以为变量n(只能是n，n的取值为0到正无穷，但是只是n=0时不起作用，2n+1（n=0），这是是可以起作用的，即括号内的最终的值不能为0，但n的取值可以为0)
        index可以为even odd
				#wrap ele:nth-child(index)		表示匹配#wrap中第index的子元素 这个子元素必须是ele
				#wrap ele:nth-of-type(index)	表示匹配#wrap中第index的ele子元素
				除此之外:nth-child和:nth-of-type有一个很重要的区别！！
						nth-of-type以元素为中心！！！
						
			:nth-child(index)系列			
				:first-child
				:last-child
				:nth-last-child(index)
				:only-child	(相对于:first-child:last-child 或者 :nth-child(1):nth-last-child(1))
			:nth-of-type(index)系列
				:first-of-type
				:last-of-type
				:nth-last-type(index)
				:only-of-type	(相对于:first-of-type:last-of-type 或者 :nth-of-type(1):nth-last-of-type(1))
				
			:not		
			:empty(内容必须是空的，有空格都不行，有attr没关系)
			
//例如：
 /* .wrap li:nth-child(1) 找到wrap下的所有子元素，并且选中第一个子元素，并且这个子元素必须为li标签 */
 
      .wrap li:nth-child(1) {
        color: yellowgreen;
      }
      
/* .wrap li:nth-child(1) 找到wrap下的所有子元素，并且选中第一个li标签的子元素 */
      .wrap li:nth-of-type(1) {
        color: yellowgreen;
      }
 
/* div下的最后一个a标签元素不设置此样式 */ 
div >a:not(:last-of-type){
   color:red;
}   
```

#### 伪元素选择器

```
 伪元素使用 : 和 ::  均可，但建议使用 ::(注意是英文状态下的)

    ::first-letter   表示第一个字母
    ::first-line     表示第一行
    ::selection      表示选中的内容
    ::before         元素的开始位置    
    ::after          元素的最后位置
    before和after必须结合content属性来使用

//例如：
      .wrap {
        margin: 50px;
      }
      .wrap::before {
        content: "*";
        color: red;
        display: inline-block;
        margin: 50px 2px 0 0;
      }
    
```

### 文本新增样式

#### 自定义字体

```
css3自定义字体：  @font-face，可以消除用户对电脑自身字体的依赖，但是不能放到选择器的内部，需要和选择器在同级下定义
font-family:'haha' ，haha为自己定义的字体名字
src: url(./font/BAUHS93.TTF); 为自己定义的字体的url地址

最后在自己需要使用此样式的元素上通过font属性或者font-family属性来使用自己定义的字体即可

自定义字体最后会在服务器上存放，用户使用到的时候去服务器上下载，确保每个用户都可以使用此字体，但坏处是会增加网络负担。

//例如：
      @font-face {
          font-family: "haha";
          src: url(./font/BAUHS93.TTF);
      }
      .wrap{
          font: 50px "haha";
      }
```

#### 文字阴影

```
text-shadow为文字添加阴影。可以为文字与 text-decorations 添加多个阴影，阴影值之间用逗号隔开。每个阴影值由元素在X和Y方向的偏移量、模糊半径和颜色值组成。
             默认值： none  可以被继承
             参考链接：https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-shadow
      
      //例如：
      .wrap{
          text-align: center;
          line-height: 200px;
          margin: 200px auto;
          border: 1px solid;
          font: 100px/200px "微软雅黑";
          text-shadow: rgba(42, 120, 69, .5) 10px 10px 10px,pink 20px 20px 20px;
      }
```

#### 文字模糊（text-shadow练习）

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记-文字模糊</title>
    <style type="text/css">
    /* 当鼠标悬浮到元素上方时，元素会逐渐模糊，直至消失 */
      * {
        margin: 0;
        padding: 0;
      }
      .wrap {
        font: 100px/200px "微软雅黑";
        color: black;
        text-align: center;
        margin: 200px auto;
      }
      .wrap:hover{
          color: rgba(0, 0, 0, 0);
          text-shadow: black 0 0 300px;
          /* 1s之后在变化，避免显得太突然 */
          transition: 1s;
      }
    </style>
  </head>
  <body>
    <div class="wrap">啊哈哈哈哈哈哈哈</div>
  </body>
</html>
```

#### 模糊背景

```
  filter CSS属性将模糊或颜色偏移等图形效果应用于元素。滤镜通常用于调整图像，背景和边框的渲染。
            默认值： none 不可被继承
            参考链接： https://developer.mozilla.org/zh-CN/docs/Web/CSS/filter

 <style>
      * {
        margin: 0;
        padding: 0;
      }
      .wrap {
        position: relative;
        height: 200px;
        background: rgba(105, 105, 45, 0.5);
      }
      .wrap .bg {
        position: absolute;
        left: 0;
        top: 0;
        right: 0;
        bottom: 0;
        z-index: -1;
        background: url(./img/0000.png) no-repeat;
        background-size: 100% 100%;
        /* 模糊则通过filter来实现 */
        filter: blur(20px);
      }
      img {
        margin: 24px 0 0 24px;
      }
    </style>
```

#### 文字排版

```
CSS属性 direction 用来设置文本、表列水平溢出的方向。  rtl 表示从右到左 (类似希伯来语或阿拉伯语)， ltr 表示从左到右 (类似英语等大部分语言).
                          初始值	ltr   可继承
                          direction 属性和 unicode-bidi 属性不受 all 属性影响。
         参考链接：https://developer.mozilla.org/zh-CN/docs/Web/CSS/direction

//例如：
  .wrap{
            width: 200px;
            height: 200px;
            border: 1px solid;
            margin:  200px auto;
            /* rtl :right to left 从右向左读，注意，必须要配合unicode-bidi使用，此属性才能生效 */
            direction: rtl;
            unicode-bidi: bidi-override;
        }
```

#### 文字溢出显示省略号

```
      .wrap {
        width: 200px;
        height: 200px;
        border: 1px solid;
        /* 一行文本溢出显示省略号必须要写下面四个属性，这四个属性缺一不可 */
        /* display: block;
        white-space: nowrap;
        text-overflow: ellipsis;
        overflow: hidden; */

         /* 让两行以后溢出的文字显示省略号 */

        /*  -webkit-line-clamp 是一个 不规范的属性（unsupported WebKit property），
        它没有出现在 CSS 规范草案中。限制在一个块元素显示的文本的行数。 为了实现该效果，它需要组合其他外来的WebKit属性。
            display: -webkit-box; 必须结合的属性 ，将对象作为弹性伸缩盒子模型显示 。
            -webkit-box-orient 必须结合的属性 ，设置或检索伸缩盒对象的子元素的排列方式 。
            text-overflow，可以用来多行文本的情况下，用省略号“...”隐藏超出范围的文本 。
        */
        display: -webkit-box;
        /* 注意，此时不能设置display: block; ，设置为块级元素会导致下面的配置失效 */
        text-overflow: ellipsis;
        overflow: hidden;
        white-space: normal;
        /* -webkit-line-clamp: 行数;   */
        -webkit-line-clamp: 2;
        -webkit-box-orient: vertical;
      }   
```

### 盒子模型

#### 盒模型阴影

```
          box-shadow   用于在元素的框架上添加阴影效果。你可以在同一个元素上设置多个阴影效果，并用逗号将他们分隔开。
                       该属性可设置的值包括阴影的X轴偏移量、Y轴偏移量、模糊半径、扩散半径和颜色。
                       默认值：none   不可被继承
              可选值：
                inset :默认阴影在边框外，使用inset后，阴影在边框内

           参考链接：https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-shadow
 
 //例如：
       .wrap {
        position: absolute;
        left: 0;
        top: 0;
        right: 0;
        bottom: 0;
        margin: auto;
        width: 200px;
        height: 200px;
        text-align: center;
        line-height: 200px;
        border: 1px solid;
        background: pink;
        box-shadow: inset 10px 10px 10px 10px black ; 
      }
```

#### box-sizing

```
 /* 需求：输入框的宽度为200px，并且需要让input在输入和显示的时候，光标左右的padding为50px*/
 
若不加下面的box-sizing属性，则会导致整个input框的宽度变成300px，因为padding会直接加在内容区上，
    加上box-sizing: border-box;则可以避免出现此类现象，让整个内容区的宽度为200px，即使设置了padding，也只会导致里面的内容显示区域变小，内容区整体大小是不会改变的 
           
     box-sizing： 默认值content-box，不可被继承
                  可选值：
                     content-box ：默认值，标准盒子模型。 width 与 height 只包括内容的宽和高， 不包括边框（border），内边距（padding），外边距（margin）。注意: 内边距、边框和外边距都在这个盒子的外部，此时元素上设置的width和height表示的是content-box的尺寸。
                      border-box： width 和 height 属性包括内容，内边距和边框，但不包括外边距。这是当文档处于 Quirks模式 时Internet Explorer使用的盒模型，此时元素上设置的width和height表示的是border-box的尺寸。

       input{
           width: 200px;
           padding: 0 50px;
           box-sizing: border-box;
           /*  outline: 0; 去掉聚焦事件时的黑色边框 */
           outline: 0;
       }

```

### 新增UI样式

#### 圆角

```
border-radius 允许设置元素的外边框圆角。
该属性是一个 简写属性，
是为了将这四个属性 border-top-left-radius、border-top-right-radius、border-bottom-right-radius，和 border-bottom-left-radius 简写为一个属性。
         
border-radius 默认值为0，不可被继承
             可选值：
               <length> 定义圆形半径或椭圆的半长轴，半短轴。负值无效。
              <percentage>使用百分数定义圆形半径或椭圆的半长轴，半短轴。水平半轴相对于盒模型的宽度；垂直半轴相对于盒模型的高度。负值无效。
              
参考链接：https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-radius
```

#### 圆角练习-风车

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记-风车示例</title>
    <style>
      * {
        margin: 0;
        padding: 0;
      }
      .wrap {
        width: 400px;
        height: 400px;
        position: absolute;
        left: 0;
        top: 0;
        right: 0;
        bottom: 0;
        margin: auto;
        transition: 4s;
      }
      .wrap > div {
        margin: 10px;
        width: 180px;
        height: 180px;
        background: #bfa;
        float: left;
        box-sizing: border-box;
        border: 1px solid;
      }
      .wrap > div:nth-child(1),
      .wrap > div:nth-child(4) {
        border-radius: 0 60%;
      }
      .wrap > div:nth-child(2),
      .wrap > div:nth-child(3) {
        border-radius: 60% 0;
      }
      .wrap:hover{
          transform: rotate(360deg);
      }
    </style>
  </head>
  <body>
    <div class="wrap">
      <div></div>
      <div></div>
      <div></div>
      <div></div>
    </div>
  </body>
</html>
```

#### 边框图片

```
border-image-source 定义一张图片来代替边框样式，如果为none，则仍然使用border-style定义的样式
                  默认值：none  不可被继承
    参考链接：https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-image-source
    
 通过border-image-source 引用边框图片后，border-image-slice属性会将图片分割为9个区域：四个角，四个边（edges）以及中心区域。四条切片线，从它们各自的侧面设置给定距离，控制区域的大小。
 参考链接：https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-image-slice

      .wrap {
        height: 200px;
        width: 200px;
        border: 30px solid;
        border-image-source: url(./img/border-image.png);
        border-image-slice: 33.3333333333333% ;
        border-image-repeat: repeat;
        border-image-width: 20px;
        border-image-outset: 10px;
      }
```

#### css2背景

```
      .wrap {
        height: 400px;
        width: 400px;
        background-color: pink;  /* 平铺整个border-box */
        background-image: url(./img/0000.png); /* 默认从padding-box开始绘制，从border-box开始裁剪 css3中有多背景，默认绘制时尺寸是自己的位图像素 */
        /* background-position 百分比的参照值：参照尺寸为背景图片定位区域的大小减去背景图片的大小 */
        background-position: -100px -10px; /* 控制背景图片在背景区域中的位置，可以是px值，也可以是百分比，百分比参照的是背景区域减去背景图片的位图像素值 */
        background-repeat: no-repeat; /* 控制是否平铺 */
        background-attachment: scroll; /* scroll：默认值，背景图不会随着元素滚动条的滚动而滚动，fixed：背景图铺在视口中，相当于是固定定位了 */
      }
```

#### css3背景

```
      .wrap {
        width: 800px;
        height: 800px;
        border: 1px solid;
        /* 默认情况下背景图片是从padding-box开始绘制的，从border-box开始裁剪 */
        background-image: url(./img/0000.png);
        background-repeat: no-repeat;
        /* css3新增属性有以下： */
        background-origin: content-box; 
        background-clip: padding-box;
        background-size: 100% 100%; /* 需要注意的是，图片是自适应的，如果需要铺满，则要设置为100% 100%  */
      }
```

### 渐变

#### 线性渐变

```
      .wrap {
        width: 1000px;
        height: 200px;
        border: 1px solid;
        margin: 0 auto;
        /* 基础的红黄绿三色渐变 */
        /* background-image: linear-gradient( red,yellow,green); */
        /* 改变方向的 */
        /* background-image: linear-gradient(to top, red,yellow,green); */
        /* 控制角度的渐变 */
        /* background-image: linear-gradient(45deg, red,yellow,green); */
        /* 控制颜色节点的渐变 */
        /* background-image:linear-gradient(90deg,red 10%,orange 15%,yellow 20%,green 30%,blue 50%,indigo 70%,violet 80%); */
        /* 透明度的渐变 */
        /* background-image:linear-gradient(90deg,rgba(25,25,0,.2) 40%,rgba(255,0,0,0.5) 70%,rgba(255,0,0,1) 850%); */
        /* 重复渐变 */
        background: repeating-linear-gradient(90deg, rgba(0,0,0,0) 10%, rgba(0,0,0,1) 30%);
      }
```

#### 径向渐变

```
radial-gradient() CSS函数创建了一个图像，该图像是由从原点发出的两种或者多种颜色之间的逐步过渡组成。
              它的形状可以是圆形（circle）或椭圆形（ellipse）。这个方法得到的是一个CSS<gradient>数据类型的对象，其是 <image> 的一种。
         
参考链接：https://developer.mozilla.org/zh-CN/docs/Web/CSS/radial-gradient()

  .wrap {
        width: 400px;
        height: 300px;
        border: 1px solid;
        margin: 0 auto;
        background-image: radial-gradient( farthest-corner circle , yellow, green 50%);
      }
```

#### 渐变练习-发廊灯

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记-发廊灯实例</title>
    <style>
      * {
        margin: 0;
        padding: 0;
      }
      html,
      body {
        height: 100%;
        overflow: hidden;
      }
      .wrap {
        margin: 300px auto;
        width: 40px;
        height: 400px;
        border: 1px solid;
        overflow: hidden;
      }
      .wrap > .inner {
        height: 900px;
        background: repeating-linear-gradient(
          135deg,
          black 0px,
          black 10px,
          white 10px,
          white 20px
        );
      }

      .wrap:hover .inner {
        margin-top: -400px;
      }
    </style>
  </head>
  <body>
    <div class="wrap">
      <div class="inner"></div>
    </div>
  </body>
  <script type="text/javascript">
    let inner = document.querySelector(".wrap > .inner");
    let flag = 0;
    setInterval(function () {
      flag++;
      if (flag === 300) {
        flag = 0;
      }
      inner.style.marginTop = -flag + "px";
    }, 1000 / 120);
  </script>
</html>
```

#### 渐变练习-光斑动画

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记-实例光斑动画</title>
    <style>
      * {
        margin: 0;
        padding: 0;
      }
      html,
      body {
        height: 100%;
        overflow: hidden;
        background: black;
        text-align: center;
      }
      .wrap {
        margin: 100px 0 0 0;
        display: inline-block;
        color: rgba(255, 255, 255, 0.3);
        font: bold 80px "微软雅黑";
        background: linear-gradient(
          120deg,
          rgba(255, 255, 255, 0) 100px,
          rgba(255, 255, 255, 1) 180px,
          rgba(255, 255, 255, 0) 260px
        );
        -webkit-background-clip: text;
        background-repeat: no-repeat;
      }
    </style>
  </head>
  <body>
    <div class="wrap">哈哈哈哈，俺来也</div>
  </body>
  <script type="text/javascript">
    let wrap = document.querySelector(".wrap");
    let flag = -160;
    setInterval(function () {
      flag += 20;
      if (flag === 800) {
        flag = -160;
      }
      wrap.style.backgroundPosition = flag + "px";
    }, 40);
  </script>
</html>
```

### 过渡

#### 过渡属性&周期

```
过渡只关心元素的初始状态和结束状态，没有方法可以获取元素在过渡中每一帧的状态

transition 属性可以被指定为一个或多个 CSS 属性的过渡效果，多个属性之间用逗号进行分隔。
transition 提供了一种在更改css属性时控制动画速度的方法，其可以让属性变化为一个持续一段时间的过程，而不是立即生效。
transition  属性是 transition-property，transition-duration，transition-timing-function 和 transition-delay 的一个简写属性。
  默认值：transition-delay: 0s  transition-duration: 0s  transition-property: all  transition-timing-function: ease ，不可被继承
 
transition-property  指定应用过渡属性的名称。
                  默认值 all 不可被继承
                  可选值：（可以指定多个property）
                        none：没有过渡动画
                        all：所有可被动画的属性都表现出过渡动画。
                              可被动画的属性参考链接：https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_animated_properties
                        IDENT: 属性名称（可指定多个）。
 参考链接：https://developer.mozilla.org/zh-CN/docs/Web/CSS/transition-property
 
 
transition-duration 属性以秒或毫秒为单位指定过渡动画所需的时间。默认值为 0s ，表示不出现过渡动画。
可以指定多个时长(时长之间用逗号隔开)，每个时长会被应用到由 transition-property 指定的对应属性上。
如果指定的时长个数小于属性个数，那么时长列表会重复。如果时长列表更长，那么该列表会被裁减。两种情况下，属性列表都保持不变。

transition-duration 属性的默认值为0s ，不可被继承
                    属性值：
                    time:以秒或毫秒为单位的数值
                    <time> 类型。表示过渡属性从旧的值转变到新的值所需要的时间。如果时长是 0s ，表示不会呈现过渡动画，属性会瞬间完成转变。不接受负值。
                          一定要加单位（不能为0,一定要写0s 1s 100ms等）
 参考链接：https://developer.mozilla.org/zh-CN/docs/Web/CSS/transition-duration
```

#### 过渡运动形式&延迟

```
CSS属性受到 transition effect的影响，会产生不断变化的中间值，而 CSS transition-timing-function 属性用来描述这个中间值是怎样计算的。
实质上，通过这个函数会建立一条加速度曲线，因此在整个transition变化过程中，变化速度可以不断改变。

transition-timing-function 属性：  初始值	ease  不可被继承
参考链接：https://developer.mozilla.org/zh-CN/docs/Web/CSS/transition-timing-function
    属性值：
        1、ease：（加速然后减速）默认值，ease函数等同于贝塞尔曲线(0.25, 0.1, 0.25, 1.0).
        2、linear：（匀速），linear 函数等同于贝塞尔曲线(0.0, 0.0, 1.0, 1.0).
        3、ease-in：(加速)，ease-in 函数等同于贝塞尔曲线(0.42, 0, 1.0, 1.0).
        4、ease-out：（减速），ease-out 函数等同于贝塞尔曲线(0, 0, 0.58, 1.0).
        5、ease-in-out：（加速然后减速），ease-in-out 函数等同于贝塞尔曲线(0.42, 0, 0.58, 1.0)
        6、cubic-bezier： 贝塞尔曲线
        7、step-start：等同于steps(1,start)
            step-end：等同于steps(1,end)
            steps(,[,[start|end]]?)
                    第一个参数：必须为正整数，指定函数的步数
                    第二个参数：指定每一步的值发生变化的时间点（默认值end）

transition-delay 属性规定了在过渡效果开始作用之前需要等待的时间。
  值以秒（s）或毫秒（ms）为单位，表明动画过渡效果将在何时开始。取值为正时会延迟一段时间来响应过渡效果；取值为负时会导致过渡立即开始。
  可以指定多个延迟时间，每个延迟将会分别作用于你所指定的相符合的css属性（transition-property）
  
  初始值	0s ，不可被继承

  可以指定多个延迟时间，每个延迟将会分别作用于你所指定的相符合的css属性。如果指定的时长个数小于属性个数，那么时长列表会重复。
  如果时长列表更长，那么该列表会被裁减。两种情况下，属性列表都保持不变

  属性值
  值以秒（s）或毫秒（ms）为单位，表明动画过渡效果将在何时开始。取值为正时会延迟一段时间来响应过渡效果；取值为负时会导致过渡立即开始。
 
       .wrap {
        width: 200px;
        height: 200px;
        background: pink;
        text-align: center;
        font: 50px/200px "微软雅黑";
        position: absolute;
        left: 0;
        top: 0;
        right: 0;
        bottom: 0;
        margin: auto;
        transition-property: width;
        transition-duration: 3s;
        transition-timing-function: linear;
        transition-delay: 1s;
        }
```

#### 过渡完成事件

```
      let bodyNode = document.querySelector("body");
      let wrapNode = document.querySelector(".wrap");
      // dom0事件
      bodyNode.onmouseover = function () {
        wrapNode.style.width = "100px";
        wrapNode.style.height = "100px";
      };
    // dom2事件
    //   当过渡完成时触发一个事件，在符合标准的浏览器下，这个事件是 transitionend, 在 WebKit 下是 webkitTransitionEnd
    //   每一个拥有过渡的属性在其完成过渡时都会触发一次transitionend事件
    // 在transition完成前设置 display: none，事件同样不会被触发
      wrapNode.addEventListener('transitionend',function(){
          alert('over')
      });
```

#### 过渡中的坑

```
过渡只关心元素的初始状态和结束状态，没有方法可以获取元素在过渡中每一帧的状态 
 
transition 在元素首次渲染还没有结束的情况下是不会被触发的，即页面整体的首次渲染时并不会执行transition
```

#### 过渡简写属性

```
css 过渡由简写属性transition  定义是最好的方式，可以避免属性值列表长度不一 ，节省调试时间
在transition属性中，各个值的书写顺序是很重要的：第一个可以解析为时间的值会被赋值给transition-duration（过渡时间），第二个可以解析为时间的值会被赋值给transition-delay(延迟时间)
  
  推荐书写顺序
      过渡时间（transition-duration）  过渡属性名称（transition-property ）  过渡形式（transition-timing-function）  延迟时间 , 过渡时间  过渡属性名称  过渡形式  延迟时间 , 。。。。。。
```

### 2D变换

#### 旋转rotate

```
transform属性允许你旋转，缩放，倾斜或平移给定元素。这是通过修改CSS视觉格式化模型的坐标空间来实现的，transform属性只对 block 块级元素有效。
rotate 属性值允许你单独设置transform的旋转属性。
      默认值为 none 不可被继承
      只能设单值。正数表示顺时针旋转，负数表示逆时针旋转
 参考链接：https://developer.mozilla.org/zh-CN/docs/Web/CSS/rotate
 
//例如：
      .test {
        width: 200px;
        height: 200px;
        background: #bfa;
        text-align: center;
        font: 40px/200px "微软雅黑";
        border-radius: 50%;
        position: absolute;
        left: 0;
        top: 0;
        right: 0;
        bottom: 0;
        margin: auto;
        transition: 2s;
      }
      .wrap:hover .test {
        transform: rotate(180deg);
      }
```

#### 平移translate

```
translate 属性 允许你单独声明平移变换，并独立于 transform 属性。
          默认值 none  不可被继承

X方向平移:transform:  translateX(tx)
Y方向平移:transform:  translateY(ty) 
二维平移：transform:  translate(tx[, ty])； 如果ty没有指定，它的值默认为0。
可设单值，也可设双值。
      正数表示XY轴正向位移，负数为反向位移。设单值表示只X轴位移，Y轴坐标不变，
      例如transform: translate(100px);等价于transform: translate(100px,0);
```

#### 倾斜skew

```
skew() 函数定义了一个元素在二维平面上的倾斜转换。它的结果是一个<transform-function> 数据类型 

这种转换是一种剪切映射(横切)，它在水平和垂直方向上将单元内的每个点扭曲一定的角度。每个点的坐标根据指定的角度以及到原点的距离，进行成比例的值调整；
因此，一个点离原点越远，其增加的值就越大。

  skew() 函数指定一个或两个参数，它们表示在每个方向上应用的倾斜量。参数值以deg为单位 
  skew(ax, ay) ax 表示用于沿横坐标扭曲元素的角度,X方向倾斜，代表与y轴之间的角度。
              ay 表示用于沿纵坐标扭曲元素的角度,Y方向倾斜，代表与x轴之间的角度。如果未定义，则其默认值为0，导致纯水平倾斜，在Y轴上没有倾斜。

        skew(45deg,15deg):参数值以deg为单位 第一个参数代表与y轴之间的角度
                                          第二个参数代表与x轴之间的角度
        单值时表示只X轴扭曲，Y轴不变，如transform: skew(30deg);等价于transform: skew(30deg, 0);
        考虑到可读性，不推荐用单值，应该用transform: skewX(30deg);。skewY表示 只Y轴扭曲，X轴不变  
          正值:拉正斜杠方向的两个角
          负值:拉反斜杠方向的两个角
```

#### 缩放scale

```
scale 属性 允许你可以分别且独立地指定CSS属性 transform 缩放的比例。这更好地映射到典型的UI（用户界面）用法中，并免去了在指定变换值时必须记住变换函数的精确顺序的麻烦。
单一数值
    单一的数值即指定了一个缩放系数，同时作用于X轴和Y轴让该元素进行缩放，相当于指定了单个值的scale()(2D缩放)函数。
两个长度/百分比值
    两个数值即分别指定了2D比例的X轴和Y轴的缩放系数，相当于指定了两个值的scale()（2D缩放）函数。
三个长度/百分比值
    三个数值即分别指定了3D比例的X轴、Y轴和Z轴的缩放系数. 相当于一个scale3d()函数。
none
    指定不进行缩放。

    默认值为none 不可被继承

    transform:scale(2);
      X方向缩放:transform:  scaleX(sx); 
      Y方向缩放:transform:  scaleY(sy);
      二维缩放 :transform:  scale(sx[, sy]);  (如果sy 未指定，默认认为和sx的值相同)  
      要缩小请设0.01～0.99之间的值，要放大请设超过1的值。
      例如缩小一倍可以transform: scale(.5);
          放大一倍可以transform: scale(2);
    如果只想X轴缩放，可以用scaleX(.5)相当于scale(.5, 1)。
    同理只想Y轴缩放，可以用scaleY(.5)相当于scale(1, .5)
    正值:缩放的程度
      负值:不推荐使用（有旋转效果）
      单值时表示只X轴,Y轴上缩放粒度一样，如transform: scale(2);等价于transform: scale(2,2);
```

#### 基点变换transform-origin

```
transform-origin 属性让你更改一个元素变形的原点。原点的改变对平移不会产生影响，平移是参照与原来的位置进行的平移
默认值 50% 50% 0   不可被继承

transform-origin属性可以使用一个，两个或三个值来指定，其中每个值都表示一个偏移量。 没有明确定义的偏移将重置为其对应的初始值。

如果定义了两个或更多值并且没有值的关键字，或者唯一使用的关键字是center，则第一个值表示水平偏移量，第二个值表示垂直偏移量。

一个值：
    必须是<length>，<percentage>，或 left, center, right, top, bottom关键字中的一个。
两个值：
    其中一个必须是<length>，<percentage>，或left, center, right关键字中的一个。
    另一个必须是<length>，<percentage>，或top, center, bottom关键字中的一个。
三个值：
    前两个值和只有两个值时的用法相同。
    第三个值必须是<length>。它始终代表Z轴偏移量。
```

#### 矩阵

```
CSS函数 matrix() 指定了一个由指定的 6 个值组成的 2D 变换矩阵。这种矩阵的常量值是隐含的，而不是由参数传递的；其他的参数是以列优先的顺序描述的。

角度转换为弧度
Math.PI = π
角度 * π / 180

.wrap:hover .test {
 /* transform: matrix(1, 0, 0, 1, 200, 0); */  /* 平移200px*/
 transform: matrix(0.7071067811865476, 0.7071067811865475, -0.7071067811865475, 0.7071067811865476, 0, 0);   /* 旋转45度*/
}
```

#### 变换组合

```
变换在组合的时候计算方向是从右往左进行计算的，所以在组合的时候需要注意，变换的底层就是矩阵的计算
```

#### 2D变换练习-扇形导航

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记-2D变形-扇形导航练习</title>
    <style>
      * {
        margin: 0;
        padding: 0;
      }
      html,
      body {
        height: 100%;
        overflow: hidden;
      }
      .wrap {
        width: 50px;
        height: 50px;
        /* border: 1px solid; */
        position: absolute;
        right: 20px;
        bottom: 20px;
      }
      .wrap > .inner {
        height: 100%;
      }
      .wrap > .inner > img {
        position: absolute;
        left: 0;
        top: 0;
        margin: 4px;
        border-radius: 50%;
      }
      .wrap > .home {
        position: absolute;
        left: 0;
        top: 0;
        z-index: 1;
        height: 100%;
        width: 100%;
        background: url("./img/home.png") no-repeat;
        border-radius: 50%;
        transition: 2s;
      }
    </style>
  </head>
  <body>
    <div class="wrap">
      <div class="inner">
        <img src="./img/clos.png" />
        <img src="./img/full.png" />
        <img src="./img/open.png" />
        <img src="./img/prev.png" />
        <img src="./img/refresh.png" />
      </div>
      <div class="home"></div>
    </div>
  </body>
  <script type="text/javascript">
    // 1. 在元素首次渲染还没有完成的情况下，是不会触发过渡的
    // 2. 在绝大多数变换样式切换中，如果变换组合的位置或个数不一样时，也是不会触发过渡的
    window.onload = function () {
      let homeEle = document.querySelector(".home");
      var imgs = document.querySelectorAll(".wrap > .inner > img");
      let flag = true;
      let c = 140;
      homeEle.onclick = function () {
        if (flag) {
          this.style.transform = "rotate(-720deg)";
          for (let i = 0; i < imgs.length; i++) {
            imgs[i].style.transition = " 1s " + i * 0.1 + "s";
            imgs[i].style.transform = "scale(1) rotate(-720deg)";
            imgs[i].style.left =
              -getPoint(c, (90 * i) / (imgs.length - 1)).left + "px";
            imgs[i].style.top =
              -getPoint(c, (90 * i) / (imgs.length - 1)).top + "px";
          }
        } else {
          this.style.transform = "rotate(0deg)";
          for (let i = 0; i < imgs.length; i++) {
            imgs[i].style.transition =
              " 1s " + (imgs.length - i - 1) * 0.1 + "s";
            imgs[i].style.transform = "scale(1) rotate(0deg)";
            imgs[i].style.left = 0 + "px";
            imgs[i].style.top = 0 + "px";
          }
        }
        flag = !flag;
      };

      //已知一个直角三角形中的斜边和其中一个角，求另外两边的长度
      function getPoint(c, deg) {
        let xx = Math.round(c * Math.sin((deg * Math.PI) / 180));
        let yy = Math.round(c * Math.cos((deg * Math.PI) / 180));
        return { left: xx, top: yy };
      }

      // 点击图片放大
      for (let i = 0; i < imgs.length; i++) {
        imgs[i].onclick = function () {
          this.style.transition = "1s";
          this.style.transform = "scale(2) rotate(-720deg)";
          this.style.opacity = 0.4;

          this.addEventListener("transitionend", fn);
        };
      }
      function fn() {
        this.style.transition = "0.2s";
        this.style.transform = "scale(1) rotate(-720deg)";
        this.style.opacity = 1;

        this.removeEventListener("transitionend", fn);
      }
    };
  </script>
</html>
```

#### 2D变换练习-时钟

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记-2D变形-时钟练习</title>
    <style type="text/css">
      * {
        margin: 0;
        padding: 0;
      }
      ul {
        list-style: none;
      }
      .wrap {
        width: 200px;
        height: 200px;
        border: 1px solid;
        border-radius: 50%;
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate3d(-50%, -50%);
      }
      ul > li {
        position: absolute;
        left: 99px;
        top: 0;
        width: 2px;
        height: 10px;
        background: black;
        transform-origin: center 100px;
      }
      ul > li:nth-child(5n + 1) {
        height: 20px;
      }
      .wrap > .hour {
        position: absolute;
        left: 97px;
        top: 70px;
        width: 6px;
        height: 30px;
        background: black;
        transform-origin: center bottom;
      }
      .wrap > .min {
        position: absolute;
        left: 98px;
        top: 50px;
        width: 4px;
        height: 50px;
        background: gray;
        transform-origin: center bottom;
      }
      .wrap > .second {
        position: absolute;
        left: 99px;
        top: 30px;
        width: 2px;
        height: 70px;
        background: red;
        transform-origin: center bottom;
      }
      .wrap > .icon {
        position: absolute;
        left: 90px;
        top: 90px;
        width: 20px;
        height: 20px;
        border-radius: 50%;
        background: pink;
      }
    </style>
  </head>
  <body>
    <div class="wrap">
      <ul></ul>
      <div class="hour"></div>
      <div class="min"></div>
      <div class="second"></div>
      <div class="icon"></div>
    </div>
  </body>
  <script>
    window.onload = function () {
      let hourNode = document.querySelector(".wrap >.hour");
      let minNode = document.querySelector(".wrap >.min");
      let secondNode = document.querySelector(".wrap >.second");

      let ulNode = document.querySelector(".wrap > ul");
      //   重新创建一个style标签，用于为多个li添加样式
      let cssStyleNode = document.createElement("style");
      let liHtml = "";
      let cssText = "";
      for (let i = 0; i < 60; i++) {
        liHtml += "<li></li>";
        cssText +=
          " ul > li:nth-child(" +
          (i + 1) +
          ") {transform: rotate(" +
          i * 6 +
          "deg);}";
        //   注意不能使用单引号，使用单引号会出错
      }
      ulNode.innerHTML = liHtml;
      cssStyleNode.innerHTML = cssText;
      document.head.appendChild(cssStyleNode);

      move(); // 防止每次刷新页面时页面需要停顿一下，在定时器setInterval之前先调用一次move函数
      setInterval(move, 1000);
      function move() {
        let date = new Date();
        let s = date.getSeconds();
        let m = date.getMinutes() + s / 60; //为了保证拿到的值是精确地,指针的转动角度需要更加精确
        let h = date.getHours() + m / 60;
        hourNode.style.transform = "rotate(" + 30 * h + "deg)";
        minNode.style.transform = "rotate(" + 6 * m + "deg)";
        secondNode.style.transform = "rotate(" + 6 * s + "deg)";
      }
    };
  </script>
</html>

```

### 3D变换

#### 景深perspective

```
景深 让3D场景有近大远小的效果（肉眼距离屏幕的距离）
方式一：perspective: 800px;

        perspective属性 指定了观察者与 z=0 平面的距离，使具有三维位置变换的元素产生透视效果。 z>0 的三维元素比正常大，而 z<0 时则比正常小，大小程度由该属性的值决定。
                默认值为none  不可被继承，但它可以作用于后代元素（不是作用于本身的）
                且景深属性需要设置给外层元素，相当于给内层需要变换的元素提供一个舞台
        参考链接：https://developer.mozilla.org/zh-CN/docs/Web/CSS/perspective
    

方式二：transform: perspective(depth);  此时作用于本身，若使用perspective()函数，那么他必须被放置在transform属性的首位，如果放在其他函数之后，则会被忽略
          depth的默认值是none，可以设置为一个长度值，这个长度是沿着Z轴距离坐标原点的距离。1000px被认为是个正常值
          这种方式因为限制有点多，不太常用。


        景深的原理：
                    景深越大，灭点越远，元素变形更小
                    景深越小，灭点越近，元素变形更大
                    
      景深叠加会导致出现问题，应该尽可能避免叠加，每个浏览器的叠加的规则是不同的，只能尽可能避免


    perspective-origin 指定了观察者的位置，用作 perspective 属性的消失点。
                        默认值为	50% 50% 百分比参照于盒模型  不可被继承

                perspective-origin 用于控制 x y轴上的基点
                perspective 用于控制 z 轴上的基点
```

#### 平移translate

```
translateZ 不能写百分比，其没有参照，translateX translateY 可以写百分比，参照的是盒模型的宽高

      .wrap:hover .inner {
        /* transform: translateX(100px); */
        /* transform: translateY(100px); */
        /* transform: translateZ(100px); */
        transform: translate3d(50%, 50%, 0);
      }
```

#### 旋转rotate

```
CSS函数定义一个变换，它将元素围绕固定轴移动而不使其变形。运动量由指定的角度定义; 如果为正，运动将为顺时针，如果为负，则为逆时针。 

      .wrap:hover .inner {
        /* transform: rotateX(360deg); */
        /* transform: rotateY(360deg); */
        /* transform: rotateZ(360deg); */
        /* transform: rotate3d(1, 0, 0, 90deg); */
        transform: rotate3d(1, 2, -1, 192deg);
      }
```

####  缩放scale

```
.wrap:hover .inner {
  /* transform: scaleZ(2); */
  /* transform: scaleX(2) translateZ(100px); */
  /* transform: scaleY(2) translateZ(100px); */
  /* transform: scaleZ(2) translateZ(100px); */
  transform: scale3d(2,2,2) translateZ(100px);
}
```

#### transform-style

```
transform-style 属性 设置元素的子元素是位于 3D 空间中还是平面中。如果选择平面，元素的子元素将不会有 3D 的遮挡关系。
                    初始值	flat   不可被继承（但作用于子元素）

                  可选值：
                        flat   设置元素的子元素位于该元素的平面中。
                        preserve-3d   指示元素的子元素应位于 3D 空间中。
```

#### 3D变换练习-立方体

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记-3D变换-入门Demo立方体</title>
    <style>
      * {
        margin: 0;
        padding: 0;
      }

      .wrap {
        position: absolute;
        left: 50%;
        top: 50%;
        width: 500px;
        height: 500px;
        border: 1px solid;
        margin-left: -250px;
        margin-top: -250px;
        perspective: 200px;
        transform-style: preserve-3d;
      }
      .wrap > .inner {
        position: absolute;
        left: 0;
        top: 0;
        right: 0;
        bottom: 0;
        margin: auto;
        width: 100px;
        height: 100px;
        /* background: pink; */
        transition: 3s;
        transform-style: preserve-3d;
        transform-origin: center center -50px;
      }
      .wrap > .inner > div {
        position: absolute;
        width: 100px;
        height: 100px;
        background: #bfa;
        text-align: center;
        font: 40px/100px "微软雅黑";
      }
      .wrap > .inner > div:nth-child(5) {
        transform-origin: bottom;
        transform: rotateX(90deg);
        top: -100px;
      }
      .wrap > .inner > div:nth-child(6) {
        transform-origin: top;
        transform: rotateX(-90deg);
        bottom: -100px;
      }
      .wrap > .inner > div:nth-child(3) {
        transform-origin: right;
        transform: rotateY(-90deg);
        left: -100px;
      }
      .wrap > .inner > div:nth-child(4) {
        transform-origin: left;
        transform: rotateY(90deg);
        right: -100px;
      }
      .wrap > .inner > div:nth-child(2) {
        transform: translateZ(-100px) rotateX(180deg);
      }
      .wrap > .inner > div:nth-child(1) {
        z-index: 1;
      }
      .wrap:hover .inner {
        transform: rotate3d(1, 1, 1, 720deg);
      }
    </style>
  </head>
  <body>
    <div class="wrap">
      <div class="inner">
        <div>前1</div>
        <div>后2</div>
        <div>左3</div>
        <div>右4</div>
        <div>上5</div>
        <div>下6</div>
      </div>
    </div>
  </body>
</html>

```

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记-3D变换-立方体-主流版本</title>
    <style>
      * {
        margin: 0;
        padding: 0;
      }

      .wrap {
        position: absolute;
        left: 50%;
        top: 50%;
        width: 400px;
        height: 400px;
        border: 1px solid;
        margin-left: -200px;
        margin-top: -200px;
        perspective: 200px;
        background: #bfa;
      }
      .wrap > .inner {
        position: absolute;
        left: 0;
        top: 0;
        right: 0;
        bottom: 0;
        margin: auto;
        width: 100px;
        height: 100px;
        transition: 3s;
        transform-style: preserve-3d;
        transform-origin: center center -50px;
      }
      .wrap > .inner > div {
        position: absolute;
        width: 100px;
        height: 100px;
        background: pink;
        text-align: center;
        font: 40px/100px "微软雅黑";
        transform-origin: center center -50px;
        backface-visibility: hidden;
      }
      .wrap > .inner > div:nth-child(6) {
        transform: rotateX(270deg);
      }
      .wrap > .inner > div:nth-child(5) {
        transform: rotateX(90deg);
      }
      .wrap > .inner > div:nth-child(4) {
        transform: rotateY(90deg);
      }
      .wrap > .inner > div:nth-child(3) {
        transform: rotateY(270deg);
      }
      .wrap > .inner > div:nth-child(2) {
        transform: rotateY(180deg) rotate(180deg);
      }

      .wrap:hover .inner {
        transform: rotateX(360deg);
      }
    </style>
  </head>
  <body>
    <div class="wrap">
      <div class="inner">
        <div>前1</div>
        <div>后2</div>
        <div>左3</div>
        <div>右4</div>
        <div>上5</div>
        <div>下6</div>
      </div>
    </div>
  </body>
</html>
```

#### 3D变换练习-三棱柱

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记-3D变换-三棱柱</title>
    <style>
      * {
        margin: 0;
        padding: 0;
      }
      /* 
      n边形的外角和为360度，每个外角为 360/n
      n边形的每个内角为 (180 - 360/n)
       */

      .wrap {
        position: absolute;
        left: 50%;
        top: 50%;
        width: 400px;
        height: 400px;
        border: 1px solid;
        margin-left: -200px;
        margin-top: -200px;
        perspective: 200px;
        background: #bfa;
      }
      .wrap > .inner {
        position: absolute;
        left: 0;
        top: 0;
        right: 0;
        bottom: 0;
        margin: auto;
        width: 100px;
        height: 100px;
        transition: 3s;
        transform-style: preserve-3d;
        transform-origin: center center -28.867513459481287px;
      }
      .wrap > .inner > div {
        position: absolute;
        width: 100px;
        height: 150px;
        background: pink;
        text-align: center;
        font: 40px/150px "微软雅黑";
        transform-origin: center center -28.867513459481287px;
        backface-visibility: hidden;
      }

      .wrap > .inner > div:nth-child(3) {
        transform: rotateY(240deg);
      }
      .wrap > .inner > div:nth-child(2) {
        transform: rotateY(120deg);
      }
      .wrap:hover .inner {
        transform: rotateY(360deg);
      }
    </style>
  </head>
  <body>
    <div class="wrap">
      <div class="inner">
        <div>1</div>
        <div>2</div>
        <div>3</div>
      </div>
    </div>
  </body>
</html>
```

#### 3D变换练习-多棱柱

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>前端小记-3D变换-多棱柱</title>
    <style>
      * {
        margin: 0;
        padding: 0;
      }
      /* 
      n边形的外角和为360度，每个外角为 360/n
      n边形的每个内角为 (180 - 360/n)
       */
      html,
      body {
        height: 100%;
        overflow: hidden;
      }

      .wrap {
        position: absolute;
        left: 50%;
        top: 50%;
        width: 400px;
        height: 400px;
        /* border: 1px solid; */
        margin-left: -200px;
        margin-top: -200px;
        perspective: 500px;
      }
      .wrap > .inner {
        position: absolute;
        left: 0;
        top: 0;
        right: 0;
        bottom: 0;
        margin: auto;
        width: 300px;
        height: 400px;
        transition: 5s transform;
        transform-style: preserve-3d;
        /* transform-origin: center center -28.867513459481287px; */
      }
      .wrap > .inner > div {
        position: absolute;
        width: 300px;
        height: 400px;
        background: pink;
        text-align: center;
        font: 40px/400px "微软雅黑";
        /* transform-origin: center center -28.867513459481287px; */
        backface-visibility: hidden;
      }
      .wrap:hover .inner {
        transform: rotateY(-360deg);
      }
    </style>
  </head>
  <body>
    <div class="wrap">
      <div class="inner"></div>
    </div>
  </body>
  <script type="text/javascript">
    window.onload = function () {
      createPrism(10);
    };
    //创建多棱柱， n表示多棱柱的棱数
    function createPrism(n) {
      // 每一个外角
      let outDeg = 360 / n;
      // 每一个内角
      let inDeg = 180 - 360 / n;
      let innerNode = document.querySelector(".wrap > .inner");
      let styleNode = document.createElement("style");

      let cssText = "";
      let text = "";
      for (let i = 0; i < n; i++) {
        text += "<div>" + (i + 1) + "</div>";
        cssText +=
          ".wrap > .inner > div:nth-child(" +
          (i + 1) +
          ") {transform: rotateY(" +
          i * outDeg +
          "deg);}";
      }
      innerNode.innerHTML = text;
      let innerDivNode = document.querySelector(".wrap > .inner > div");
      // 棱长
      let prismLength = innerDivNode.offsetWidth;
      cssText +=
        ".wrap > .inner {transform-origin: center center -" +
        (prismLength / 2) * Math.tan(((inDeg / 2) * Math.PI) / 180) +
        "px;}";
      cssText +=
        ".wrap > .inner >div {transform-origin: center center -" +
        (prismLength / 2) * Math.tan(((inDeg / 2) * Math.PI) / 180) +
        "px;}";

      styleNode.innerHTML = cssText;
      document.head.appendChild(styleNode);
    }
  </script>
</html>
```

### 动画

#### animation基础属性

```
  animation-name属性指定应用的一系列动画，每个名称代表一个由@keyframes定义的动画序列。
                初始值：none  不可被继承

  参考链接：https://developer.mozilla.org/zh-CN/docs/Web/CSS/animation-name
```

```
animation-duration属性指定一个动画周期的时长。
                      注意，必须带单位，单位为秒(s)或毫秒(ms),负值无效，浏览器会忽略该声明，但是一些早起的带前缀的声明会将负值当作0s

                  默认值为0s，表示无动画。不可被继承。

   参考链接：https://developer.mozilla.org/zh-CN/docs/Web/CSS/animation-duration
```

```
  animation-timing-function属性定义CSS动画在每一动画周期中执行的节奏。可能值为一或多个 <timing-function>。
                            初始值	ease 不可被继承

  对于关键帧动画来说，timing function作用于一个关键帧周期而非整个动画周期，即从关键帧开始开始，到关键帧结束结束。

定义于一个关键帧区块的缓动函数(animation timing function)应用到该关键帧；另外，若该关键帧没有定义缓动函数，则使用定义于整个动画的缓动函数。

   参考链接：https://developer.mozilla.org/zh-CN/docs/Web/CSS/animation-timing-function
```

```
animation-delay 属性定义动画于何时开始，即从动画应用在元素上到动画开始的这段时间的长度。
                初始值	0s    不可被继承
0s是该属性的默认值，代表动画在应用到元素上后立即开始执行。否则，该属性的值代表动画样式应用到元素上后到开始执行前的时间长度；
定义一个负值会让动画立即开始。但是动画会从它的动画序列中某位置开始。例如，如果设定值为-1s，动画会从它的动画序列的第1秒位置处立即开始。
如果为动画延迟指定了一个负值，但起始值是隐藏的，则从动画应用于元素的那一刻起就获取起始值。

参考链接：https://developer.mozilla.org/zh-CN/docs/Web/CSS/animation-delay
```

```
animation-iteration-count 属性定义动画在结束前运行的次数 可以是1次 无限循环。重复的是关键帧

animation-iteration-count 属性可以指定一个或多个以逗号分隔的值。如果指定了多个值，每次播放动画时，将使用列表中的下一个值，在使用最后一个值后循环回第一个值。

infinite :  无限循环播放动画。
<number> ： 动画播放的次数；默认值为1。可以用小数定义循环，来播放动画周期的一部分：例如，0.5 将播放到动画周期的一半。不可为负值。

参考链接：https://developer.mozilla.org/zh-CN/docs/Web/CSS/animation-iteration-count
```

#### animation-fill-mode

```
animation-fill-mode 属性 设置CSS动画在执行之前和之后如何将样式应用于其目标。
none
    当动画未执行时，动画将不会将任何样式应用于目标，而是已经赋予给该元素的 CSS 规则来显示该元素。这是默认值。
forwards
    目标将保留由执行期间遇到的最后一个关键帧计算值。 最后一个关键帧取决于animation-direction和animation-iteration-count的值。to之后的状态的与to的状态一致。
backwards
    动画将在应用于目标时立即应用第一个关键帧中定义的值，并在animation-delay期间保留此值。 第一个关键帧取决于animation-direction的值。from之前的状态与from的状态保持一致
both
    动画将遵循forwards和backwards的规则，从而在两个方向上扩展动画属性。
```

#### animation-play-state

```
animation-play-state 属性定义一个动画是否运行或者暂停。可以通过查询它来确定动画是否正在运行。另外，它的值可以被设置为暂停和恢复的动画的重放。

                      恢复一个已暂停的动画，将从它开始暂停的时候，而不是从动画序列的起点开始在动画。

                      默认值：running   不可被继承

                      可选值：
                            running
                                当前动画正在运行。
                            paused
                                当前动画已被停止。
  参考链接：https://developer.mozilla.org/zh-CN/docs/Web/CSS/animation-play-state
```

#### animation-direction

```
animation-direction 属性指示动画播放的方向。反转的是关键帧和animation-timing-function
                    初始值：normal  不可被继承
        可选值：
              normal
              每个循环内动画向前循环，换言之，每个动画循环结束，动画重置到起点重新开始，这是默认属性。
              alternate
              动画交替反向运行，反向运行时，动画按步后退，同时，带时间功能的函数也反向，比如，ease-in 在反向时成为ease-out。计数取决于开始时是奇数迭代还是偶数迭代
              reverse
              反向运行动画，每周期结束动画由尾到头运行。
              alternate-reverse
              反向交替， 反向开始交替
              动画第一次运行时是反向的，然后下一次是正向，后面依次循环。决定奇数次或偶数次的计数从1开始。
   
若希望元素在做动画时是从from ==》 to ==》from ==》to ==》from，不再一直都是from==》 to 之后直接回到from的位置在做动画运动到to

只需要设置 animation-direction的值为alternate即可。
若想从一开始就想从to开始到from则需要设置animation-direction的值为alternate-reverse即可。
```

#### 关键帧@keyframes

```
关键帧 @keyframes at-rule 规则通过在动画序列中定义关键帧（或waypoints）的样式来控制CSS动画序列中的中间步骤。
和 转换 transition 相比，关键帧 keyframes 可以控制动画序列的中间步骤。

要使用关键帧, 先创建一个带名称的 @keyframes 规则，以便后续使用 animation-name 属性将动画同其关键帧声明匹配。
每个 @keyframes 规则包含多个关键帧，也就是一段样式块语句，每个关键帧有一个百分比值作为名称，代表在动画进行中，在哪个阶段触发这个帧所包含的样式。
可以按任意顺序列出关键帧百分比；它们将按照其应该发生的顺序来处理。

其他情况参考链接：https://developer.mozilla.org/zh-CN/docs/Web/CSS/@keyframes


@keyframes move {
  0% {
    transform: translateY(-100px);
  }
  50% {
    transform: translateY(50px);
  }
  100% {
    transform: translateY(100px);
  }
}
```

