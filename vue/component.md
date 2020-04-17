> 组件名首字母大写
```javascript
    //全局定义一个组件
    vue.component('CompOne', componentName)
```
```javascript
    //组件传值
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
### extend //继承
```javascript
    import Vue from 'vue'
    const NewHeader = Vue.extend(PageHeader)
    new NewHeader({
        el: '#root',
        propsData: { //此时需要用propsData才能拿到
          propsOne: 'xxx' 
        },
        data: {
          text: '123'
        }
    })
```
```javascript
    import PageHeader from '../../layout/page-header.vue'
    const HeaderTwo = {
        extends: PageHeader,
        props: {
          propsTest: {
            type: String,
            default: "props text"
          }
        },
        data (){
          return {
            logoText: "123"
          }
        }
    }
```
### slot
```javascript
{ //父组件
    template: `
        <comp>
          <div slot="header">this is header</div>
          <div slot="cont" slot-scope="props">this is {{props.text}}</div>
        </comp>
    `
}
{ //子组件
    data(){
        return {
          text: "cont"
        }
    },
    template: `
        <div>
          <slot name="header"></slot>
          <slot name="cont" :text="text"></slot>
        </div>
    `
}
```
        slot添加name属性成为具名插槽
        作用域插槽：组件在引用是写在里面的变量是跟随引用这个组件的父组件里面的变量值，
        若想用到子组件里面的值，则在引用组件里面加slot-scope=""指令
        
> provide用于父、祖辈组件传值给后辈组件，用inject接收
