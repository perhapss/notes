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

```javascript
  props: {
    variateName: {
      type: String, //规定类型
      required: true, //规定是否必传
      default: "defaultData", //规定默认值,如果默认值是一个对象需要新建一个方法return出默认值
      validator (value) { //可以更详细的检查传入的值
        return typeof value === 'String'
      }
    }
  }
```

