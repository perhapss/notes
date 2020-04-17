binding data
===
{{data}}
### binding class
:class="{active: variableName}"

:class="[{active: variableName}]"

    绑定数据中可以用调用方法 返回值

v-text:  //绑定内容

v-html="" //banging html content

v-show="" //相当于在节点上加了"display: none"

v-if=""  //会引起页面重绘

v-else-if=""

v-else  //上一个节点必须有 v-if 或 v-else-if
```html
  <ul>
    <li v-for="(item, index) in arr" :key="item"></li>
  </ul>
  <ul>
    <li v-for="(val, key, index) in obj" :key="key"></li>
  </ul>
```
v-bind: => :

v-on: => @  //绑定事件

v-model=""  //双向绑定  用在input上

*修饰符*
v-model.number="" //会将输入的值转换成number

v-model.trim="" //去除首尾的空格

v-model.lazy="" //将input事件变为change事件

v-pre  //内容不会解析

v-cloak //现在用不到了

### $parent
```javascript
    this.$parent.$options.name //父组件的name会转化成$options里面的东西
    this.$parent.text = "xxx" //可以在子组件中改变父组件的值
    
    
```
> parent 是可以指定的，但只有在new vue({})是指定才有效，而声明一个组件，作为模板去编译是，parent是在vue渲染过程中指定的，我们无法去修改。
> 可以通过$parent在子组件中改变父组件的值，但不推荐这样做，因为在父组件中看不见是在什么地方被修改了。可以去查看，但尽量不要去修改。
```javascript
    const parent = new Vue({
        name: 'parent'
    })
    new Vue({
    parent: parent
    })
```
        

