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
    ![](https://github.com/Meng823/Test-Blog/blob/master/img/borderbox.png)
    ![](https://github.com/Meng823/Test-Blog/blob/master/img/contentbox.png)
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

…………未完待续
