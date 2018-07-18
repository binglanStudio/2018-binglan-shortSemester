### div溢出小点
- div写一段英文，会看成一个，则溢出，加上空格，表示文字分割（空格回车都是文字分割）
### a
- 加上target = “_blank_”跳转到新页面
- href = “#name”,给div一个name，点击a标签跳转到该div出---回到顶部
### 行级盒子VS块级盒子
- 不在行级盒子里面的文字回匿名生成行级盒子 比如：  <p>some<em>text</em></p>
- 块级盒子不能同时包含两种盒子，块级里面有块级与行级，会自动生成匿名块级盒子来包含行级盒子 比如：<div><h1>标题</h1><span>2018-07-18</span></div>
- 行级盒子包含块级盒子，会被块级盒子分割成两个部分，两部分分别北生成的匿名块级盒子包含
- display:inline-block----生成行级盒子，内容为块级盒子
### ::before 和 ::after
- before会在子元素的前面生成一个**盒子**，相应的在子元素的后面生成一个**盒子**
### BFC(Block formatting context)块级格式化上下文概念
- BFC布局规则1：内部的Box会在垂直方向，一个接一个地放置。
上文定义中提到过的块级盒：block-level box，在这里解析一波：我们平常说的盒子是由margin、border、padding、content组成的，实际上每种类型的四条边定义了一个盒子，分别是分别是content box、padding box、border box、margin box，这四种类型的盒子一直存在，即使他们的值为0.决定块盒在包含块中与相邻块盒的垂直间距的便是margin-box。

- BFC布局规则2：Box垂直方向的距离由margin决定。属于同一个BFC的两个相邻Box的margin会发生重叠

- BFC的作用4：阻止margin重叠:
当两个相邻块级子元素分属于不同的BFC时可以阻止margin重叠

操作方法：*给其中一个div外面包一个div，然后通过触发外面这个div的BFC，就可以阻止这两个div的margin重叠*

- BFC布局规则3：每个元素的margin box的左边， 与包含块border box的左边相接触(对于从左往右的格式化，否则相反)。即使存在浮动也是如此，*div里面的div、左浮是子div的左边接触父div的borderbox的左边，右浮是子div接触父div的borderbox右边*

- BFC作用3：可以包含浮动元素——清除内部浮动
给父divpar加上 overflow: hidden;

*清除浮动原理：触发父div的BFC属性，使下面的子div都处在父div的同一个BFC区域之内，此时已成功清除浮动。*

- BFC布局规则4：BFC的区域不会与float box重叠,上面aside盒子有一个浮动属性，覆盖了main盒子的内容，main盒子没有清除aside盒子的浮动。只做了一个动作，就是触发自身的BFC，然后就不再被aside盒子覆盖了。所以：BFC的区域不会与float box重叠。
<div class="aside"></div>
<div class="text">
    <div class="main"></div>
</div>

- BFC作用：自适应两栏布局。代码同上面对