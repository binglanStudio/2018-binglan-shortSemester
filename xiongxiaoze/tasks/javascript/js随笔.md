## 计算器js步骤
- 1.定义当前输入的第一个数
- 2.获取当前的输入
- 3.计算输入结果
- 4.清0
- 5.后退
-----
## eavl()
- eavl（”2+3“）---直接得出5
-----
## .fcous()
- 获取焦点
---
## onfcous()
- 当获取焦点时做什么
---
## substring()
- substring(0,5)提取第0个数（或字符）到第5个数（或字符）
---
## Map和Set
- Map&Set都是键值对形成一个key：value的数组
    - var m = new Map()
        m.set('name',67)
        m.get('name')----67
- var s1 = new Set()--自动过滤重复元素
    - var s2 = new Set([1,2,3,'3'])---3与'3'不重复
---
## 函数里rest参数
- funtion fool(a,b,...rest){
    console.log("a ="+a)
    console.log("b ="+b)
    console.log(rest)
}
fool(1,2,3,4,5)
//a = 1
//b = 2
//Array[3,4,5]
>不同函数内部的变量相互独立,``JavaScript的函数在查找变量时从自身函数定义开始，从“内”向“外”查找。如果内部函数定义了与外部函数重名的变量，则内部函数的变量将“屏蔽”外部函数的变量。``
- JavaScript的函数定义有个特点，它会先扫描整个函数体的语句，把所有申明的变量“提升”到函数顶部
- 不在任何函数内定义的变量就具有全局作用域。实际上，JavaScript默认有一个全局对象window，全局作用域的变量实际上被绑定到window的一个属性：    'use strict';
    var course = 'LearnJavaScript';
    alert(course); // 'Learn JavaScript'
    alert(window.course); // 'Learn JavaScript'
- 由于JavaScript的变量作用域实际上是函数内部，我们在for循环等语句块中是无法定义具有局部作用域的变量的
- ``解构赋值``
    var array = ['hello','js','ES6']
    var [x,y,z] = ['hello','js','ES6']
    console.log('x ='+x,'y ='+y,'z ='+z)
    --赋值分别对应顺序，不写表示空着
- 对象里面的第一个方法里的this指向的就是这个对象
    - 但是方法里的函数里的this无定义
        - 解决方法是在第一个方法的定义域内定义 var that = this
- 高阶函数就是函数能够接受别的函数
- [1,2,3,4,5].reduce(f) = f(f(f(x1,x2)x3)x4)
    var arr = [1,2,3,4,5]
    arr.reduce(funtion(x,y){
        return x+y
    })//实现求和
----
## 闭包
- for (var i=1; i<=3; i++) {
        arr.push(function () {
            return i * i;
        })全部都是16！原因就在于返回的函数引用了变量i，但它并非立刻执行。等到3个函数都返回时，它们所引用的变量i已经变成了4，因此最终结果为16,返回闭包时牢记的一点就是：返回函数不要引用任何循环变量，或者后续会发生变化的变量
    - 解决方法-创建匿名函数并立即执行（funtion(x){return x*x}(3)）//9
- 实现多次方
    - function make_pow(n) {
        return function (x) {
            return Math.pow(x, n);
        }
    }
    var pow2 = make_pow(2);创将两个新函数
    var pow3 = make_pow(3);

    console.log(pow2(5)); // 25
    console.log(pow3(7)); // 343
----
## 标准对象
- number string Boolean undefined object
- 包装对象用new--var n = new Number(123)//123
    - 不要使用new Number()、new Boolean()、new String()创建包装对象
    - 用parseInt()或parseFloat()来转换任意类型到number
    - 用String()来转换任意类型到string，或者直接调用某个对象的toString()方法
    - 通常不必把任意类型转换为boolean再判断，因为可以直接写if (myVar) {...}
    - typeof操作符可以判断出number、boolean、string、function和undefined
- ``Date对象``：用来获取当前``年月日``和``时分秒``
    - var now = new Date().get__()
    - **getMonth()获取的月份少一：美国0=一月**
---
## JSON
- JXON.stringfy(xiaoming,['name','shills'],' ')
    - 1对象 2输出指定属性 3按缩进输出：有层次

- 反序列化JSON.parse()
---
##面向对象
- 原型链
    - 当我们用obj.xxx访问一个对象的属性时，JavaScript引擎先在当前对象上查找该属性，如果没有找到，就到其原型对象上找，如果还没有找到，就一直上溯到Object.prototype对象，最后，如果还没有找到，就只能返回undefined。