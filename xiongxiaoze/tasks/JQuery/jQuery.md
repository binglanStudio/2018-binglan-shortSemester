https://code.jquery.com/jquery-3.3.1.js
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