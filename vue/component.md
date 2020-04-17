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
