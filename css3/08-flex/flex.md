  ```
    0.flex 练习
		http://flexboxfroggy.com/

	1.flex基础点
		---要知道 什么是容器，什么是项目，什么是主轴，什么是侧轴？
		---项目永远排列在主轴的正方向上
		---flex分新旧两个版本
			-webkit-box
			-webkit-flex / flex

	2.注意点
		---我们都知道新版本的flex要比老版本的flex强大很多，有没有必要学习老版本的flex？
			移动端开发者必须要关注老版本的flex
				因为很多移动端设备内核低只支持老版本的flex
		
		---老版本的box通过两个属性四个属性值控制了主轴的位置和方向
		      新版本的flex通过一个属性四个属性值控制了主轴的位置和方向
		---老版本上是没有属性来控制侧轴的方向的
	
	3.老版本
		容器
			容器的布局方向
				-webkit-box-orient:horizontal/vertical
				控制主轴是哪一根
					horizontal：x轴，主轴为水平方向
					vertical  ：y轴，主轴为垂直方向

			容器的排列方向
				-webkit-box-direction：normal/reverse
				控制主轴的方向
					normal： 从左往右或者从上往下（正方向）
					reverse：从右往左或者从下往上（反方向）

			富裕空间的管理
				只决定富裕空间的位置，不会给项目区分配空间

			主轴的富裕空间 -webkit-box-pack   (不论主轴的方向如何)
					      
                start 富裕空间在主轴右边(主轴为水平方向)    富裕空间在主轴下边(主轴为垂直方向)
                end     富裕空间在主轴左边(主轴为水平方向)    富裕空间在主轴上边(主轴为垂直方向)  
                center  富裕空间在主轴两边(主轴为水平方向)    富裕空间在主轴两边(主轴为垂直方向)
                justify 富裕空间在项目之间      
         
				侧轴的富裕空间 -webkit-box-algin   (不论侧轴的方向如何)
		
                start   富裕空间在侧轴右边(侧轴为水平方向)    富裕空间在侧轴下边(侧轴为垂直方向)
                end     富裕空间在侧轴左边(侧轴为水平方向)    富裕空间在侧轴上边(侧轴为垂直方向)  
                center  富裕空间在侧轴两边(侧轴为水平方向)    富裕空间在侧轴两边(侧轴为垂直方向)
		项目
		    弹性空间管理
			-webkit-box-flex：弹性因子（默认值为0）
						
	4.新版本
		容器
			容器的布局方向
			容器的排列方向
				flex-direction
				控制主轴是哪一根和控制主轴的方向
					row;		 主轴为水平方向，正方向是从左往右
					row-reverse; 主轴为水平方向，正方向是从右往左
					column;		 从主轴为垂直方向，正方向是从上往下
					column-reverse;主轴为垂直方向，正方向是从下往上

			富裕空间的管理
				只决定富裕空间的位置，不会给项目区分配空间
				主轴
					justify-content
							flex-start：	   在主轴的正方向
							flex-end:		   在主轴的反方向
							center：			  在两边
							space-between：	   在项目之间
			 (老版本没有的)	 space-around：     在项目两边
							
            参考链接：https://developer.mozilla.org/zh-CN/docs/Web/CSS/justify-content

				侧轴
					align-items
							flex-start：  在侧轴的正方向
							flex-end：    在侧轴的反方向
							center：		在两边
			 (老版本没有的)  baseline       基线对齐
	     	 (老版本没有的)	 stretch	   等高布局（当项目没有高度）弹性元素被在侧轴方向被拉伸到与容器相同的高度或宽度。	

            参考链接：https://developer.mozilla.org/zh-CN/docs/Web/CSS/align-items
		
		项目
		    弹性空间管理
			  flex-grow：弹性因子（默认值为0）

    5.新版本新增的

	容器
		flex-wrap：控制的是侧轴的方向
			nowrap 不换行
			wrap   侧轴方向由上而下 			（flex-shrink失效）
			wrap-reverse 侧轴方向由下而上 	    （flex-shrink失效）
		
		align-content：多行/列时侧轴的富裕空间的管理（把多行/列看成一个整体）
		
		flex-flow：flex-direction和flex-wrap的简写属性
			本质上控制了主轴和侧轴分别是哪一根，以及他们的方向
	
	项目
		order:控制项目的排列顺序，元素按照 order 属性的值的增序进行布局。拥有相同 order 属性值的元素按照它们在源代码中出现的顺序进行布局。

		align-self：项目自身富裕空间的管理 ，align-self 会对齐当前 flex 行中的 flex 元素，并覆盖 align-items 的值，align-self属性不适用于块类型的盒模型和表格单元。如果任何 flexbox 元素的侧轴方向 margin 值设置为 auto，则会忽略 align-self。

		flex-shrink：收缩因子（默认值为1），负值是不被允许的。 flex-shrink属性生效的前提条件是：不换行且flex元素的宽度之和必须大于容器的宽度，在容器中设置flex-wrap:wrap会导致属性失效，当容器大小大于所有flex元素的宽度之后时该属性也会失效。

		flex-basis：伸缩规则计算的基准值，指定了 flex 元素在主轴方向上的初始大小（默认拿width或height的值）


	6.伸缩规则

		flex-basis（默认值为auto）,flex元素在不设置此属性时flex-basis为当前flex元素的宽度/高度

		flex-grow（默认值为0）
			可用空间 = (容器大小 - 所有相邻项目flex-basis的总和，若没有flex-basis，则使用元素的width/height代替)
			可扩展空间 = (可用空间/所有相邻项目flex-grow的总和)
			每项伸缩大小 = (伸缩基准值flex-basis + (可扩展空间 x flex-grow值))

		flex-shrink（默认值为1）

		无论如何收缩也不会导致flex元素中被占据空间的元素丢失，即flex被自动撑开的宽度不能被收缩，如果不能继续收缩的时候元素会溢出当前flex元素，若其他的flex元素没有撑满自身，则会先减去那个溢出的flex元素溢出的宽度，剩下的空间才是溢出空间，才会按照下面的公式进行计算。

			--.计算收缩因子与基准值乘的总和  
						let a = 每一项flex元素的 （flex-shrink * flex-basis ）之和
			--.计算收缩因数
						收缩因数=（项目的收缩因子*项目基准值）/ 第一步计算总和   
						let b =  (flex-shrink * flex-basis) / a
			--.移除空间的计算
							移除空间= 项目收缩因数 x 溢出的空间 
						let c =    b * 溢出的空间      

	7.侧轴富裕空间的管理（在侧轴上如何对齐）

		单行单列
			align-items
			align-self（优先级高）

		多行多列
			align-content

	8.flex的简写属性
			flex:1  (flex-basis:0% flex-grow:1 flex-shrink:1)	
			等分布局	

```