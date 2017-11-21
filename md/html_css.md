# HTML+CSS
* HTML、XML和XHTML的联系与区别
    * 定义：都是标准通用标记语言的一个子集。
        * HTML被设计用来显示数据，其焦点是数据的外观
        * XML被设计用来传输和存储数据，其焦点是数据的内容
        * XHTML是更严格更纯净的HTML版本，是作为一种XML应用被重新定义的HTML，为取代HTML以适应网络更多需求
    * 区别：
        * 相对html，xhtml文档具有良好完整的排版，1.元素必须要有结束标签；2.元素必须嵌套；
        * html大小写混写且编码不规范，xhtml必须小写，xml是严格区分大小写的
        * html标签是预定义的；XML标签是免费的、自定义的、可扩展的
        * 在XML文档中，空白部分不会被解析器自动删除；但是html是过滤掉空格的。
<br>

* html中元素分类<br>
    * 块级元素：  1.可以设置宽和高   2.独自占据一整行<br>
    * 行级元素：  1.不可以设置宽和高  2.根据自身内容决定占据空间大小<br>
    * 行级块元素： 1.可以设置宽和高   2.根据自身内容决定占据空间大小<br>
    <br>

* meta标签属性
    * name：用于描述页面，有以下几个参数：1.keywords（关键字）2.description（描述内容）3.viewport（移动端视口） 4.author（作者）5.renderer（双核浏览器渲染方式）6.copyright（版权）
    * http-equiv：http头文件作用，可用于设置content-type（字符集），X-UA-Compatible（渲染页面所用版本）,expires（文件到期日期）,refresh（自动更新）,set-cookie（设置cookie）
    <br>

* CSS的引用方式及CSS权重值
    * 引用方式：(1)import(已弃用) 缺点：必须写在文件头，且在资源加载完以后才会加载import中的CSS文件 <br>
    (2)行间样式：标签属性中写style <br>
    (3)内部样式：head标签中的< style > <br>
    (4)< link > 标签引入<br>
    * CSS选择器：<br>(1)父子选择器(div strong{}) (2)子元素选择器(div>strong{}) <br> 
    (3)属性选择器(a[href]{})     (4)分组选择器(div,span,h1{})<br>
    (5)相邻兄弟选择器(div+p{})    (6)类选择器(.class{})<br>
    (7)ID选择器（注：1.在一个HTML文档中，ID选择器会且仅会使用一次   2.ID选择器不能结合使用）<br>
    * CSS权重值：<br>
        (1)行间样式>内部样式>引入样式 <br>
        (2) !important > 行间样式 > ID > Class(伪类) > Tagname(伪元素) > * <br>
    <br>

* 盒模型<br>
    ![](https://github.com/Meng823/Blog/blob/master/img/borderbox.png)
    ![](https://github.com/Meng823/Blog/blob/master/img/contentbox.png)
    <br>

* 层模型<br>
    * position:static： 块级元素生成矩形框，作为文档流的一部分，行内元素则会创建一个或多个行框，置于其父元素中
    * position:absolute： 被抽离到更高层面，以最近有定位的父级进行定位，否则以浏览器边框为坐标轴定位
    * position:relative： 保留其原来的位置，并相对原来的位置进行定位
    * position:fixed： 元素框的表现类似于将 position 设置为 absolute，不过其包含块是视窗本身
    * position:sticky：在屏幕范围时该元素定位相当于relative，当该元素将要移出偏移范围时，定位变成fixed
<br>

* left/right与margin-left/right的区别
    * left,right,top,bottom仅对于position:relative|absolute|fixed的元素有意义
    * margin是盒模型的外边距，在各种情况下均可使用（注意margin合并与maigin塌陷）<br>
    (注：百分数是相对于父元素的 width 计算的)
    <br>

* 清除浮动流的方式
    * 利用块级元素的属性 clear：both
    * 利用伪元素清除 ::after/before{content:''}
    * 触发bfc（块级格式化上下文：当涉及到可视化布局的时候，bfc提供了一个环境，让元素按照一定规则进行布局）
        * overflow（不为visible）
        * float（不为none）
        * position（不为static或relative）
        * display：inline-block/flex
<br>

* em，rem，px的区别
    * em：相对长度单位，相对当前对象的文本字体尺寸，没有设置则相对浏览器默认字体尺寸，em会继承父级字体大小
    * rem：相对长度单位，相对于html根元素，一般html的font-size为10px
    * px：相对于显示其屏幕分辨率，苹果的retina屏幕一个单位大概有两像素点
<br>

* display:none和visible:hidden的区别
    * display:none：不为隐藏的对象保留其物理空间，相当于此元素不存在
    * visible:hidden：使此对象隐藏，所占空间没有变化，只是看不见（像哈利波特中的隐身衣效果）
<br>

* 简述两栏式布局及三栏式布局
    * 两栏式布局实现方式很简单，一栏定宽，一栏自适应，实现方式：float + margin
    * 三栏式布局相对来说方法就会多很多了
        * 左右两栏使用float属性，中间栏使用margin属性撑开
        * 使用position定位实现，即左右两栏使用position进行定位，中间栏使用margin进行定位
        * 圣杯布局，此处不详细写了
        * flex布局(CSS3方法)
<br>

# HTML5+CSS3
* HTML5 是下一代的HTML，将成为HTML、XHTML以及 HTML　DOM的新标准。<br>
CSS3用于控制网页的样式和布局。CSS3 是最新的 CSS 标准。
<br>

* HTML5的新特性
    * 用于绘画的canvas和svg
    * 用于媒介回放的 `video` (支持ogg，MPEG4，WebM格式文件)和 `audio`(支持ogg,mp3,wav格式文件)标签
    * 对本地离线存储的更好的支持
    * 更好的语义化标签，如 article、footer、header、nav、section
    * 事件的拖放特性：drag
    * 地理位置定位API：Geolocation
<br>

* Canvas与SVG
    * SVG：利用标签进行构图。它每个元素都是可用的。可以为某个元素附加JS处理。若SVG对象的属性发生变化，浏览器则自动重现图形。
    * SVG教程（来自W3C）　　＝＞　　[传送门](http://www.w3school.com.cn/svg/index.asp)
    * Canvas：通过JS来绘制2D图形。而且一旦图形被绘制完成，就不会继续得到浏览器的关注。如果其位置发生变化，那么整个场景也需要重新绘制，包括任何或许已被图形覆盖的对象。适合图像密集型的游戏，其中的许多对象会被频繁重绘
    * Canvas参考手册（来自W3C）　　＝＞　　[传送门](http://www.w3school.com.cn/tags/html_ref_canvas.asp)
<br>

* CSS3属性（本人碰到的面试当中居然有问参数个数及参数值，所以一起整理出来）
    * 边框：
        * border-radius：边框圆角；参数：一个参数，则四个角的弧度相同；两个参数：左上右下，左下右上；四个参数分别对应：左上，右上，右下，左下；
        * box-shadow：盒阴影；六个参数：水平位移，垂直位移，模糊度，阴影尺寸，阴影颜色，阴影投射方向（outset(默认)，inset）
        * border-image：边框图片；五个参数：图片路径，边框向内偏移，边框宽度，图像超出边框的量，图像边框放置方式（平铺(repeated)、铺满(rounded)或拉伸(stretched)）
    * 背景：
        * background-size：背景尺寸；两个参数：宽度，高度
        * background-origin：背景图片的定位区域；一个参数：border-box；padding-box；content-box；
        * background-clip：背景的绘制区域；参数同上
    * 文本：
        * text-shadow：文本阴影；四个参数：水平阴影，垂直阴影，模糊距离，阴影颜色
        * text-wrap：文本换行规则；一个参数：normal(默认)；none(不换行)
        * word-wrap：长单词词进行分割并换行；一个参数：break-word(在长单词或URL地址内部进行换行) 
    * 字体：
        * @font-face：font-family：字体名字；src：字体路径；
    * 2D转换：transform
        * translate()：从当前位置移动；两个参数：水平位移，垂直位移
        * rotate()：元素顺时针旋转；一个参数：角度值
        * scale()：缩放元素的尺寸；两个参数：水平放大倍数，垂直放大倍数
        * skew()：元素翻转角度；两个参数：X轴翻转，Y轴翻转
        * matrix()：所有2D转换的组合；六个参数：水平倍数，X翻转值，Y翻转值，垂直倍数，水平位移，垂直位移
    * 3D转换：transform
        * translateX(),translateY(),translateZ(),translate3d()
        * rotateX()，rotateY()，rotateY()，rotate3d()
        * scaleX()，scaleY()，scaleZ()，scale3d()
    * 过渡：transition：四个参数，如下
        * transition-property：过渡的属性名
        * transition-duration：过渡花费的时间。默认是 0。
        * transition-timing-function：过渡的时间曲线。linear(速度不变)；ease(由慢变快又变慢)
        * transition-delay：过渡的延迟时间
    * 动画：animation：六个参数，如下
        * @keyframes+自定义名称：大括号内可为from/to，或变化的百分比
        * animation-duration：动画完成时间
        * animation-timing-function：动画速度曲线。
        * animation-delay：动画何时开始
        * animation-iteration-count：动画播放次数。默认是 1，无限播放是infinite
        * animation-direction：动画是否在下次逆向播放。默认normal，逆向播放alternate
    * 多列：
        * column-count：分隔的列数
        * column-gap：列间间隔
        * column-width：列的宽度。
        * column-span：元素横跨的列数（可用于做报纸的标题）；横跨一列是1，横跨所有列是all
<br>

…………未完待续
