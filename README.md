bugcollections
==============

Record the problems I encountered. 


## 1.IE6、7浮动的一个Bug

简单说明一下我遇到的这个Bug。

结构
	
	<ul class="demo">
		<li>国内酒店</li>
		<li>首页</li>
	</ul>

当ul.demo向右浮动，li也向右浮层时，IE6、7中，ul.demo的宽度会自适应到父级的宽度（可以把ul li的结构修改为div div的结构）。

样式

	.demo{float:right;background-color:#090;margin:0;padding:0;}
	.demo li{float:right;list-style:none;background-color:#f00;margin-left:10px;}
	/* demo & demo li向右浮动，会导致ul宽度计算错误(ie67:100%)。跟zoom:1;没有半毛钱关系 */

demo地址：ie67-float-bug.html