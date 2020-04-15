computed //只有当依赖的值发生变化时才会触发
methods  //页面中其他地方值发生变化时也会触发
> 在computed和watch中不要去修改任何依赖的值，否则容易出现无限循环
### watch
```javascript
  watch: {
    firstName (newName, oldName) {
        // ...
      }
  }
  watch: {
    firstName: {
      handler (newName, oldName) {
        // ...
      },
      immediate: true,  //为true时初始会执行一次，否则要当监听的firstName变化时才会执行
      deep: true  //深入观察，可以监听到对象下面的值变化，或者可以将监听对象变为这个对象的值('obj.a')
    }
  }
```
