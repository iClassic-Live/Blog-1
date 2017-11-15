* 类式继承模式#1——默认模式
```javascript
    function inherit(Child,Parent){
        Child.prototype = new Parent();
    }
```
    * 缺点：继承太多没用的属性方法
<br>

* 类式继承模式#2——借用构造函数
```javascript
    function Child(a,b,c,d){
        Parent.apply(this,arguments);
    }
```
    * 优点：可以获得父对象自身成员的真实副本，不存在子对象意外覆盖父对象属性的风险
    * 缺点： 无法从原型中继承任何东西，且原型也仅是添加可重用的方法及属性，并不会为每个实例重新创建原型
<br>

* 类式继承模式#3——共享原型
```javascript
    function inherit(Child,Parent){
        Child.prototype = Parent.prototype;
    }
```
    *缺点：若子对象修改了原型，它会影响到所有父对象和祖先对象
<br>

* 类式继承模式#4——临时构造函数
```javascript
    function inherit(Child,Parent){
        var Temp = function(){};
        Temp.prototype = Parent.prototype;
        Child.prototype= new Temp();
        Child.uber = Parent.prototype; 
        Child.prototype.constructor = Child;
    }
```