transition
===
### 可以给任何元素和组件添加进入/离开过渡的情形：
* 条件渲染（v-if）
* 条件展示（v-show）
* 动态组件
* 组件根节点

      添加name=""属性设置class前缀
### 过渡的类名
* v-enter
* v-enter-active
* v-enter-to
* v-leave
* v-leave-active
* v-leave-to
### 自定义过渡名
* enter-class
* enter-active-class
* enter-to-class
* leave-class
* leave-active-class
* leave-to-class
### 显性过渡持续时间
```javascript
<transition :duration="1000">...</transition>
<transition :duration="{enter: 500, leave: 800}">...</transition>
```
### JavaScript钩子
