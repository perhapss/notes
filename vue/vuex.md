vuex
===
### store
```javascript
import Vuex from 'vuex'

import defaultState from './state/state'
import mutations from './mutations/mutations'
import getters from './getters/getters'
import actions from './actions/actions'
const isDev = process.env.NODE_ENV === 'development' //判断是否是生产环境

export default ()=>{ //做服务端渲染的话就需要每次新生成一个store,不然会有内存溢出
  return new Vuex.Store({
    strict: isDev, //禁止在component中修改state的值，只在生产环境使用这个配置
    state: defaultState,
    mutations,
    getters, 
    actions
  })
}
```
### state
```javascript
export default {
  pageIndex: 0
}
```
### mutations
```javascript
export default{
  updatePage (state, num) { //只有两个参数，若传入值为多个是转换成一个对象
    state.pageIndex = num
  }
}
```
### getters
> 生成一些可以在应用中直接使用的数据，统一
```javascript
export default{
  fullName (state) {
    return `${state.firstName} ${state.lastName}`
  }
}
```
### actions 
> 用于有异步修改数据的操作
```javascript
export default{
  updatePageAsync (store, data) { //只有两个参数，若传入值为多个是转换成一个对象
    setTimeout(() => {
      store.commit('updatePage', data.num)
    }, data.time)
  }
}
```
### component
```javascript
computed: {
  pageIndex () {
    return this.$store.state.pageIndex  //获取到store的state值，也可以在组件中直接给pageIndex赋值，但不推荐这样做
  },
  fullName () {
    return this.$store.getters.fullName  //获取到getters的fullName值
  }
}

this.$store.dispatch('updatePageAsync', { //调用store的actions中的方法
  num: 5,
  time: 2000
})
this.$store.commit('updatePage', num)  //调用store的mutations中的方法
```
### modules
```javascript
//store
modules: {
  a: {
    namespaced: true, //声明后mutation就只在当前模块，各模块之间就可以有相同的命名
    state: {
      text: 1  //this.$store.state.a.text 调用
    }，
    mutation: { 
      updateText(state， text){ //this.$store.commit('updateText', num) 默认vuex会把mutation放到全局的命名空间中
        state.text = text
      }
    },
    getters: {
      textPlus (state, getter, rootState) { 
        //第二个参数是所有的getter方法, 第三个参数是全局的state, return this.$store.getters.textPlus
        return state.text + 1
      }
    }
  },
  b: {
    state: {
      text: b
    }
  }
}
```
