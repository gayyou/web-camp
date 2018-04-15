### 符号 &lt;a&gt; 的用法  
  
	<a href="语句1"title="语句2">语句3 </a>
语句1 可以是相对路径（相对于我们打开的这个html文件）或者绝对路径，还可以是一个网页 如 https://www.google.com  要加https:// 让网页知道这不是一个本地链接

	<a target="_ blank" href="http://www.baidu.com"
	title ="去百度">213</a>
这里的加不加target="_ blank"的区别是另外开一个新窗口而不是直接跳转。
 
语句2 是提示，就是鼠标移动到那里会有提示，一般提示点下去会去那个网站这些除了&lt;a&gt;以外有很多标记可以用的  
  
语句3 浏览器用特殊效果显示短语“语句二”（通常是带下划线的蓝色文本） 还可以是一张图片，点进去就是进入到语句一所指向，如下面

	<a href="123.html">
	<img src="图片的链接">
	</a>
还可以具体定位到某个网页的某一处，用#+标志点（类似于C语言中的goto），#前不加任何语句就是本网页的 标志点处，标志点处则用id="标志"。

	<a href="#ding"
	title="goto the html 123 ">123.html</a>
	<p id="ding">...</p>
但是，如果是URL末尾的话要先加/再加#，因为浏览器会帮你在URL后面加斜线，可能取代id引用
***
#### 处理图像的元素 &lt;img&gt; 
	<img src="images/drinks.gif">
可知&lt;img&gt;是一个void型元素（&lt;br&gt;一样），内联元素（记得前后换行，不然足够大的时候前后两张图就会并排！）。
html是的页面是纯文本的，图像是绝对无法作为页面的一部分。

	<img src="123.png""width="48"height="100"
	alt="the tu is meoyong">
如果没法加载图片123.png的话，会在下面生成一段alt元素的文字，这就是候选格式，无法加载图像时对图像的解释。width.height可以强制转换图片的长度和宽度。（后面的数字是像素来着）    



### CSS  
CSS的元素专门放在一个css文件中，以便模块化设计，改动简单些；
在&lt;head&gt;中用

	<link type" text/css" rel="stylesheet" href=""
调用这个css文件；

---

	p {
		background-color:red;
	}
p->&lt;p&gt;元素，css的元素不需要加括号  想要设置的属性在大括号中间；  
CSS中的代码可以放在&lt;style&gt;与&lt;/style&gt;中间，对各种元素进行属性的分配等。   
##### 覆盖继承  
如body定义的属性，em元素中有，若要求别的style，可以对em重新定义属性。  
##### !important的用处  
一个元素的属性设定后，后面加这个!important后，这个属性就不能再被改变了  
	
	p {
		color: red
	!important;
	}
	p {
		color:yellow;		//尽管这个属性是在最后面的，但是前面有!importtant定义，不能改变元素的颜色
	}
##### 自定义语句的颜色  
	<style>
		p.green {			//p前面可以叠加不同的元素，两个元素间用，隔开
			color : green;  
		}
	</style>
	<p class="green">绿色</p>
则p中打印出的字体会变成绿色的。这是一种自定义，只有在p元素内加上class并提供类属性名，才可以显示绿色段落。  
  
##### 常用的CSS词汇  
	font-size:14px   //字体大小
	color：silver    //字体颜色
	font-weight      //字体粗细light -> normal -> bold -> bolder 由细到粗 
	text-decoration：underline    //很夺种装饰，包括字体的上下划线等等
	font-family web字体的属性详细见head the first html 的314页  
	background-color：#xxxxxx   //分别是十六进制的数，可以去查表查询要的颜色、。
	line-height：xxem           //行间距
	
  
##### 调整web字体大小的方法  
用  font-size：xx%  表示这个字体是原来的百分之几。

	body {
		font-size:14px;		//px必须紧跟着像素数后面，中间不能有空格
		font-size:90%/0.9em;  //一般默认的标准字体大小为16px，直接这样用是
		//还可以用关键字来定义字体大小，xx-small,x-small,small,medium,large,x-large,xx-large(老版的浏览器可能不支持像素定义)
	}
	h1 {
		font-size:150%;   //则h1中的字体是14的1.5倍
		font-size:1.2em   //类似于百分号，1.2倍
	}

---
#### html元素的边距，边框调整  
	.guarantee {}     //.后加元素定义的是类，没有特指的话是所有元素都可以用。
	#标志的是id  特指。

##### 简写模式  
	padding:0px 10px 20px 30px; 		//分别是上右下左的内边距
	margin也具有同样的性质，外边距；若四个数字相同，则只需输入一个；
	border: xx xx xx;    //三个属性可以乱序，分别是width，style,color.少写也行
	background 也有这种用法；
	font：font-style font-variant font-weight font-size/line-height font-family
	这个特殊一点，前三个可选的，也可以互相换位置。必须指定字体大小。
	line-height是可选的，但是如果要的话必须在size后面加个"/"才行
	font-family元素之间需要逗号隔开

### div 
div可以内嵌div，但是要遵循有用的最简化原则，多用不是好事，但是用的恰当确实最好的。  
保留

----

### 关于布局  
块元素是从上往下流布局，而内联元素总体上是从左上方流向右下方（根据屏幕变换，从左向右流，超过屏幕的话换行继续，随屏幕宽度变换）  
但是，关于2个相邻元素的边距的话，内联元素和块元素还是有区别的。  
内联元素：相邻元素的外边距会叠加（A的外边距是10px，B是20px，则这两个元素的距离是30px。）
块元素：相邻外边距会只取大的，父子块元素也是这样。（当为父子元素时候，即将外边距看做一个平面集合，取2个边距的并集）。  
  
##### float类型  
	p#amam {
		width:200px;
		float:right;
	}
这个作用有两步，第一步，把这个元素(p id="amam")整个从流中摘掉，然后放在页面的最右端，宽度为200px，下面的元素会顶替上来这个元素本来的位置。  
虽说是不在这个流中，但是其他元素内联会避开这个浮动的位置  

流体布局的话，有个叫叫做中缝。即左边div的右边距大于右边的大小，右边用float。但是要注意页面底部可能会与float属性的div重合，所以需要clear：right；
流体设计很重要，但是冻结布局也很重要。
凝胶布局的话，一般要用到左右边距是一个自动的变量。可以做到随屏幕宽度的变化页边距随之变化。
  
position 的四个属性  
static （静态）  默认属性，这个元素放进流中  
fixed   （固定）  随着屏幕的移动而移动，出现在试窗的固定位置  
relative  （相对） 正常流入画面，然后按指定的量偏移，从而流出他们原来所在的位置。
absolute  （绝对） 这个相似于float但是，流是检测不到它的存在的，所以流中的内联元素不会跟着它走。

---
#### html5
######&lt;header&gt;&lt;footer&gt;  
这是头和尾，虽然用div可以表示（只是加个id啥的），但是对于浏览器也好，维护人员的话会更快知道这是头尾，更好修改。   
######section  (区块)  
section不是通用容器元素。如果仅仅是用于设置样式或脚本处理，应用div元素。一条简单的准则是，只有元素内容会被列在文档大纲中时，才适合用section元素。

至于何时使用，基本上可以这两点： 
section 不是一个专用来做容器的标签，专用的是 div 
section 里应该有 标题（h1~6），但文章中推荐用 article 来代替 
我们可以理解为一个非文章段落，有明确 id 的一个特殊模块容器（不是专用以包住块的容器）。

也就是说，一般情况下作为元素容器，使用div而不是section，那么section就没有用了吗？图样图森破。 
这种情况下使用section就比div要好 
section，顾名思义就是一个章节，比如：  

	<section>
	<h1>WWF</h1>
	<p>The World Wide Fund for Nature (WWF) is....</p>
	</section>
至于为什么要用，是为了语义化，有section、article、dl看这多舒服，人也好理解，计算机也好理解，比满眼的div好多了。  

######aside
这个是侧栏，同样div可以做到，但是如果在一个屏幕宽度有限的移动设备上打开这个网页的时候，就会出现跟div的区别，这个aside的会在主显示的下面，会有主次之分，而div却没有。  

###### video  
	<video  controls	可以有也可以没有，浏览器会为其增加内置控件
			autoplay	加载完后自动播放，不要自动播放的话去掉
			preload 	提前加载，根据带宽决定提前加载的数量
			loop		循环播放
			width="512" height="480"	设置宽高
			src="video.mp4"				寻找目标视频
			poster="images.jpg"			未点击播放时的封面，没有此条属性的话默认是第一帧
			id="video">
			<source src="....." type='video/mp4; codecs="avc1.42e01e, mp4a.40.2"'>
			<source src="....." type='video/mp4; codecs="avc1.42e01e, mp4a.40.2"'>
			<source src="....." type='video/mp4; codecs="avc1.42e01e, mp4a.40.2"'>
			//假设上面三个不同，这些是备用选项，从上到下	（需要删除上面那个src）	
			<p>.....</p>		如果都没有就显示这条p
	</video>

###### table
		<table>
			<caption>
				the title    //默认的在表格上方的题目
			</caption>
			<tr>			
				<th>A5343</th>	//表头   注意看是th
			</tr>
			<tr>
				<td>A</td>	//表身
			</tr>
		</table>
可以实现合并行。

	<td rowspan="2">跨行</td>   这个会跨行，即将下面的那行与这一行合并（合并两行
	solspan 是合并列，合并与右边相邻的列

	border-collapse //是针对表格的，允许将单元表格边框合并成一个边框，使外观简洁
	nit-child  伪类可以指定行改色；  
	list-style-type  list-style-image  改变ol中的li的顺序图标属性。 
