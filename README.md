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

##2.IE6 absolute与float相邻，absolute元素消失bug

结构

	<div class="demo">
		<div class="pa">absolute</div>
		<div class="fl">float:left;one</div>
		<div class="fl2">right</div>
	</div>

样式

	<style type="text/css">
		.demo{position:relative;z-index:1;background-color:#09c;height:320px;width:800px;margin:0 auto;}
		.demo .fl{ float:left;width:300px;height:20px;background-color:red;}
		.demo .fl2{width:500px; height:20px; background-color:#00F; float:left}
		.demo .pa{position:absolute;width:100px;height:100px;top:32px;right:0;background-color:red;color:#999;}
	</style>

网上看到最多的就是上面的例子。当时我自己也写过类似的结构，但是没有重现这个bug。于是就开始分析，为什么我写的代码不能重现，与上面的例子有什么区别，后来终于找到了。那就是，如果父元素.demo的宽度与里面向左浮动子元素宽度之差，小于3px时（子元素的padding、margin与border存在，请加上），就会消失。

demo地址：ie6absolute-float.html