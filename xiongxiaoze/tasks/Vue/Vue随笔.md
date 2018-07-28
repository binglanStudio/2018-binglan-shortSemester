## v-model
- 一般放在表单元素里面（input）
- 双向数据绑定
>data里面放的是json--是大括号里面的数据用：复制--用，间隔
## v-for
- v-for=" value in arr"   {{value}}
## v-on:click/mouseover/mousout/dblclick
- this.arr.push()
    - this表示就是这个事件
- 和methods配合--在methods里面放函数 methods{
    show：funtion{

    }
- v-on: ====== @
- 事件对象-> @click ="show（$event，b）"
    show(ev){
        alert(ev.clientX)随机弹出数
        alert（b）参数以及数据顺序要对应
}
## v-show
- v-show="true/false"
## 事件冒泡
- 在点击按钮的时候出发了父级点击事件
    -  1.阻止冒泡 在按钮传入$event
    @click="show($event)"
    funtion(ev){
        ev.cancelBubble=true
    }
    - 2.@click.stop="show()"---用这个
- 阻止默认行为
    - @contextmenu（右键）="show($event)"
            funtion(ev){
                ev.preventDefault()
            }
    - @contextmenu.prevent----用这个
