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
---
## DOM查找方式
- 包括五种方式
    - 1.按id查找
    - 2.按标签名查找：var elems = parent.getElementsByTagName('');
    - 3.按class属性查找:var elems = parent.getElementsByClassName('class')
    - 4.选择器选择querySelector()选一个和querySelectorAll()选所有
        ![querySelector()](https://images2015.cnblogs.com/blog/1151772/201704/1151772-20170422212749306-764470900.png)
        ![querySelectorAll()](https://images2015.cnblogs.com/blog/1151772/201704/1151772-20170422212846009-1259116040.png)
### 更新DOM
- 拿到一个DOM节点后，我们可以对它进行更新。
  可以直接修改节点的文本，方法有两种：
   - 一种是修改innerHTML属性，这个方式非常强大，不但可以修改一个DOM节点的文本内容，还可以直接通过HTML片段修改DOM节点内部的子树：// 获取<p id="p-id">...</p>
    var p = document.getElementById('p-id');
    // 设置文本为abc:
    p.innerHTML = 'ABC'; // <p id="p-id">ABC</p>
    // 设置HTML:
    p.innerHTML = 'ABC <span style="color:red">RED</span> XYZ';
    // <p>...</p>的内部结构已修改
    - 第二种是修改innerText或textContent属性，这样可以自动对字符串进行HTML编码，保证无法设置任何HTML标签：// 获取<p id="p-id">...</p>
    var p = document.getElementById('p-id');
    // 设置文本:
    p.innerText = '<script>alert("Hi")</script>';
    // HTML被自动编码，无法设置一个<script>节点:
    // <p id="p-id">&lt;script&gt;alert("Hi")&lt;/script&gt;</p>
    - 修改CSS也是经常需要的操作。DOM节点的style属性对应所有的CSS，可以直接获取或设置。因为CSS允许font-size这样的名称，但它并非JavaScript有效的属性名，所以需要在JavaScript中改写为驼峰式命名fontSize：/ 获取<p id="p-id">...</p>
    var p = document.getElementById('p-id');
    // 设置CSS:
    p.style.color = '#ff0000';
    p.style.fontSize = '20px';
    p.style.paddingTop = '2em';
---
## 操作表单
- 文本框，对应的<input type="text">，用于输入文本；
    口令框，对应的<input type="password">，用于输入口令；
    单选框，对应的<input type="radio">，用于选择一项；
    复选框，对应的<input type="checkbox">，用于选择多项；
    下拉框，对应的<select>，用于选择一项；
    隐藏文本，对应的<input type="hidden">，用户不可见，但表单提交时会把隐藏文本发送到服务器
- 获取值input.value
---
## jQuery--版本库
- $著名的jQuery符号。$本质上也是一个函数
- 使用jQuery
    - 使用jQuery只需要在页面的<head>引入jQuery文件即可：
        <html>
        <head>
            <script src="//code.jquery.com/jquery-1.11.3.min.js"></script>
            ...
        </head>
        <body>
            ...
        </body>
        </html>
    - https://code.jquery.com/jquery-3.3.1.js
      >官网下载的jQuery
        - jQuery严格控制顺序，先定义，后调取
        - 提取value $('#test').val
        - jQuery返回的是一个jQuery对象
        - jQuery能够绑定的事件主要包括：
            鼠标事件
            click: 鼠标单击时触发；
            dblclick：鼠标双击时触发；
            mouseenter：鼠标进入时触发；
            mouseleave：鼠标移出时触发；
            mousemove：鼠标在DOM内部移动时触发；
            hover：鼠标进入和退出时触发两个函数，相当于mouseenter加上mouseleave
        - 键盘事件
            键盘事件仅作用在当前焦点的DOM上，通常是<input>和<textarea>。

            keydown：键盘按下时触发；
            keyup：键盘松开时触发；
            keypress：按一次键后触发
        - focus：当DOM获得焦点时触发；
            blur：当DOM失去焦点时触发；
            change：当<input>、<select>或<textarea>的内容改变时触发；
            submit：当<form>提交时触发；
            ready：当页面被载入并且DOM树完成初始化后触发
- 选择器是jQuery的核心，一个选择器写出来类似%('#dom-id')
    - jQuery的选择器就是帮助我们快速定位到一个或多个DOM节点
    - 如果某个DOM节点有id属性，利用jQuery查找如下：
      // 查找<div id="abc">:
      var div = $('#abc');
      - 注意，#abc以#开头。返回的对象是jQuery对象。
        什么是jQuery对象？jQuery对象类似数组，它的每个元素都是一个引用了DOM节点的对象，假如存在返回的[<div id= "abc">...</div>]
        不存在，返回[]
      - 总之jQuery的选择器不会返回undefined或者null，这样的好处是   你不必在下一行判断if (div === undefined)
      - jQuery对象和DOM对象之间可以互相转化：
        var div = $('#abc'); // jQuery对象
        var divDom = div.get(0); // 假设存在div，获取第1个DOM元素
        var another = $(divDom); // 重新把DOM包装为jQuery对象
        - 按ID查找
        如果某个DOM节点有id属性，利用jQuery查找如下：

        // 查找<div id="abc">:
        var div = $('#abc');
        - 按tag查找
        按tag查找只需要写上tag名称就可以了：

        var ps = $('p'); // 返回所有<p>节点
        ps.length; // 数一数页面有多少个<p>节点
        - 按class查找
        按class查找注意在class名称前加一个.：

        var a = $('.red'); // 所有节点包含`class="red"`都将返回
        // 例如:
        // <div class="red">...</div>
        // <p class="green red">...</p>
        - 通常很多节点有多个class，我们可以查找同时包含red和green的节点：

        var a = $('.red.green'); // 注意没有空格！
        // 符合条件的节点：
        // <div class="red green">...</div>
        // <div class="blue green red">...</div>
        - 按属性查找
        一个DOM节点除了id和class外还可以有很多属性，很多时候按属性查找会非常方便，比如在一个表单中按属性来查找：

        var email = $('[name=email]'); // 找出<??? name="email">
        var passwordInput = $('[type=password]'); // 找出<??? type="password">
        var a = $('[items="A B"]'); // 找出<??? items="A B">
        - 组合查找
        组合查找就是把上述简单选择器组合起来使用。如果我们查找$('[name=email]')，很可能把表单外的<div name="email">也找出来，但我们只希望查找<input>，就可以这么写：

        var emailInput = $('input[name=email]'); // 不会找出<div name="email">
        同样的，根据tag和class来组合查找也很常见：

        var tr = $('tr.red'); // 找出<tr class="red ...">...</tr>