Cocos学习笔记
=====
* 资源：
    * 资源管理器中的资源和文件管理器中资源同步，所有assets路径下的资源都会生成一份资源配置文件，提供该资源在项目中的唯一标识以及配置信息，若在文件系统中修改资源文件，必须同步处理相应meta文件<br>
    * SpriteFrame是核心渲染组件sprite所使用的资源，设置或替换Sprite组件中的spriteframe属性，就可以切换显示的图像，添加sprite方式：直接在节点上添加，属性检查器里的`添加组件`，然后从`添加渲染组件`中Sprite，就可添加到节点上
    <br>图集资源：游戏开发中常见的一种美术资源。在制作序列帧动画时，会用TexturePacker工具将序列帧打包成图集<br>
        *可优化性能：1.合成图集时会进行各种优化，减少游戏包体和内存占用；2.多个Sprite如果渲染的是来自同一张图集，可减少CPU的运算时间，提高运行效率（文件中的碎图会自动生成图集资源，只有构建项目才会真正生成图集到项目中，以AutoAtlas-xx.png结构命名）<br>
    * 预制资源（Prefab）：<br>
        * 编辑好节点后，直接将节点从'层级管理器'拖到'资源管理器'<br>
        * 注意在属性检查器中保存资源，并且在修改预制实例之后还可以`回退`,将预制对象还原为资源中的状态<br>
        * 自动同步：不同于手动同步，场景中的预制根节点自身的name，active，position属性不会自动同步，如发生修改，会询问是撤销还是更新资源；而且无法引用该预制资源外的其他对象，引用组件和子节点<br>
<br>

* 代码相关问题：
    * cc.Class用于声明cocos Creater中的类，与es6中的class相类似，以键值对的方式设定类型参数，以'方法名：function()'的形式声明方法，可用instanceof进行类型判断
    * name声明的是class名，ctor为构造函数，用extends实现继承，继承后，CCClass会统一自动调用父类的构造函数，不需要自己调用
    * 在properties中声明属性，这些属性可随意设置初值，因为可以在属性选择器中修改；
        * 当声明的属性具备类型时，可在声明处填写他们的构造函数来完成声明，如
```javascript
properites:{
    target:cc.Node,  //代表是cocos的节点（不知道理解的对不对）
    pos:cc.Vec2,   //position简写，代表有二维向量的坐标
}
```
        * 当声明的属性继承自`cc. ValueType`(注：所有值类型的基类，静态方法，有clone，equals，toString等方法)时，除了使用构造函数，还可以用实例作为默认值
```javascript
properites:{
    pos:new cc.Vec2(2,2),
    color:new cc.Color(225,225,225,128), //CCColor值用rgba 
    }
```
> 当声明属性是一个数组时，可在声明处填写他们的构造函数
```javascript
properites:{
    any:[],  //不定义具体类型的数组
    bools:[cc.Boolean],
    string:[cc.String],
    ints:[cc.Integer],
    float:[cc.Float],
    values:[cc.Vec2],
    nodes:[cc.Node],
    frames:[cc.SpriteFrame],
}
```
> 注：除以上几种情况，其他类型我们都需要使用`完整声明`的方式进行书写
>> 常用参数：
>>>default:设置属性默认值，默认值仅在组建第一次添加到节点上才会用到，数组的default必须设为[]<br>
>>>type:限定属性的数据类型<br>
>>>visible:设为false则不再`属性检查器`面板中显示该属性<br>
>>>serializable:设为false，则不保存该属性<br>
>>>displayName:在`属性检查器`面板中显示成指定名字<br>
>>>tooltip:在`属性检查器`面板中添加属性的Tooltip<br>
<br>

* 节点和组件<br>
> 获得组件所在的节点：类似js中的this，不同的是此处使用的是this.node;<br>
> 获得其他组件：类似js中的getElementsByTagName(),此处使用的是this.getComponent();<br>
> 查找子节点：类似原生js的childNodes，此处使用`this.node.children`或者使用子节点名字获取元素`getChildByName()`<br>
> 查找较深层次子节点，可以使用`cc.find("",this.node)`，第一个参数是逐级查找的路径，当忽略第二节节点时，从场景根标签进行查找<br>
> 声明全局变量也和原生有所差别，cocos中只能使用`window.变量名 = {}`声明，默认严格模式，window必须写<br>
> 跨文件操作：利用`require("文件名")`的方式进行跨文件使用（文件中为`module.exports`模块）<br>
<br>

* 常用节点和组件接口
> this.node.childrenCount：返回节点的子节点数量
> 改变节点位置：<br>
1.分别对x轴和y轴坐标赋值：`this.node.x/y`;<br>
               2.使用setPosition方法：`this.node.setPosition(x,y)`,`this.node.setPosition(cc.v2(x,y))`;<br>
               3.设置position变量: `this.node.position = cc.v2(x,y)` <br>
>更改节点旋转：`this.node.rotation = 角度`;`this.node.setRotation(角度)`；<br>
>更改节点旋转：`this.node.scaleX/Y`;`this.node.setScale()`<br>
>更改节点尺寸：`this.node.setContentSize(x,y)`;`this.node.setContentSize(cc.v2(x,y)`或`this.node.width/height`<br>
>更改节点锚点位置：`this.node.anchorX/Y';<br>
>常用组件接口：cc.Component是所有组件的基类（类似原型链的头object），任何组件都包括如下常见接口(this代表此组件)<br>
>>this.node：该组件所属的节点实例；<br>
>>this.enabled：是否每帧执行该组件的`update`方法，同时也用来控制渲染组件是否显示<br>
>>update(dt)：作为组件的成员方法，在组件的`enabled`属性为true时，其中的代码会每帧执行<br>
>>onLoad()：组件所在节点进行初始化时（节点添加到节点树时）执行<br>
>>start()：会在组件第一次`update`之前执行，通常用于需要在所有组件的`onLoad`初始化完毕后执行<br>
<br>

* cocos生命周期回调函数
    * onLoad：在组件首次激活时触发，比如所在场景被载入，或者所在节点被激活的情况下，保证可获取到场景中的其他节点及关联的资源数据<br>
    * start：在组件第一次激活前，即`update`前触发，通常用于初始化中间状态的数据，这些数据可能在update时改变，并被频繁的enable和disable<br>
    * update：每一帧渲染前更新物体的行为操作<br>
    * lateUpdate：`update`更新后的额外操作<br>
    * onEnable：当组件`enable`属性从false变为true时，或者所在节点的`active`从false变为true时，会激活`enable`，如果节点第一次被创建且`enable`为true，则会在`onLoad`之后，`start`之前被调用<br>
    * onDisable：当组件的`enable`属性从true变成false，或所在节点`active`从true变false时，被激活<br>
    * onDestory：当组件或者所在节点调用了`destory()`，则会调用`onDestory`并当帧结束时统一回收组件<br>

* 创建和销毁节点
    * 创建节点：new cc.node；向节点中添加组件：addComponent();
    * 克隆已有节点：cc.instantiate()
    * 创建预制节点：与克隆已有节点相似，需要先设置一个预制(Prefab)并通过cc.instantiate生成节点
    *       4000020020
    