router
===
```javascript
export default new Router({
  mode: 'history',
  routes: routes
})
export default () => { //需要服务器渲染时，要export一个function，不然每次export的都是同一个router会造成内存溢出
  return new Router({
    mode: 'history', //有hash和history两种模式
    routes: routes,
    base: 'base', //用vue-router跳转时都会给链接前面加一个'/base'，不强制，链接中没有也可以访问
    linkActiveClass: '', //用router-link跳转时，会给当前页面路径匹配的层级页面都加上设置的class 'router-link-active'(默认)
    linkExactActiveClass: '', //用router-link跳转时，会给当前页面路径完全匹配的标签上加上设置的class 'router-link-exact-active'(默认)
    scrollBehavior (to, from, savedPosition) { //记录之前访问过的当前页面滚动的位置
      if(savedPosition){
        return savedPosition
      }else{
        retrun {x: 0, y: 0}
      }
    },
    parseQuery (query) { //链接中的参数在query中，此方法把字符串转化为json
    
    },
    stringifyQuery (obj) { //此方法把obj转化为字符串
    
    },
    fallback: true, //默认为true, 不是所有的浏览器都支持这种'history'形式的路由方式，这时就会自动转化成'hash'的方式
  })
}
const routes = [
  {
    path: '/',
    redirect: '/login' //改变路径
  },
  {
    path: '/',
    component: 'Login',
    name: 'login', //命名
    meta: { //页面的源信息，用于SEO
      title: 'this is app',
      description: ''
    },
    children: [
      {
        path: 'details', // 要注意，以 / 开头的嵌套路径会被当作根路径。 这让你充分的使用嵌套组件而无须设置嵌套的路径。
        component: 'Details'
      }
    ]
  }
]
```
```html
  <router-link to="/login"></router-link>
  <router-link :to="{name: 'login'}"></router-link>  <!-- 给路由命名的跳转 -->
```
### 跳转路由
* this.$router.push() //跳转到不同的url，但这个方法会向history栈添加一个记录，点击后退会返回到上一个页面。
* this.$router.replace() //同样是跳转到指定的url，但是这个方法不会向history里面添加新的记录，点击返回，会跳转到上上一个页面。上一个记录是不存在的。
* this.$router.go(n) //相对于当前页面向前或向后跳转多少个页面,类似 window.history.go(n)。n可为正数可为负数。正数返回上一个页面
> 可以用一个transition标签包裹住route-view，做切换页面的动画
### 传参
```javascript
  //router
    {
      path: '/login/:id',
      // props: true, //声明后就可以在组件中用props: ['id']获取到参数
      // props: { //声明一个对象
      //   id: 123
      // },
      props: (route) => (id: route.query.a) //声明一个方法，route和在组件内部拿到的this.$toute是同一个内容
      
    }
  //html
    <router-link to="/login/123"></router-link>
  //js
  this.$route //当前路由的信息 this.$route.params.id就是我们传人的参数
  在链接中?后面跟的参数在this.$route.query中
```
> 当组件中用了this.$route时就不能作为一个公用的组件来用，只能成为router中的一个component
### 命名router-view
```javascript
  //template
    <router-view name="a" />
  //router
    {
      path: '',
      components: { //当有多个路由时(router-view)，用components
        default: '',  //没有命名的默认路由传入组件
        a: '', //命名为a的路由传入组件
      }
    }
```
### 导航守卫
```javascript
  //设置在全局
  router.beforeEach((to, from, next) => {
    //to.fullPath
    next(); //需要执行next方法才会跳转路由, next('/login'), 也可以传入一个对象，和在router里面的一样 next({path: '/login'})
  })
  router.beforeResolve((to, from, next) => {
    next();
  })
  router.afterEach((to, from) => {
    
  })
  //设置在路由配置  router
  {
    beforeEnter (to, from, next) {
      next(); //调用顺序在全局的beforeEach和beforeResolve之间
    }
  }
  //在组件内部
  beforeRouteEnter (to, from, next) {
    // next(); ////调用顺序在路由配置的beforeEnter和全局的beforeResolve之间
    //此时拿不到 组件的数据 this, 用下面方法拿到
    next( vm => {
      //vm.id
    })
  },
  beforeRouteUpdate (to, from, next) {
    next(); //同一个组件在不同的路由下面都是用这个组件去显示的时候才会触发， 例：'/app:id'，
    //如果页面数据要根据传入的id去变化时就可以在这里操作， 否则要用watch
  },
  beforeRouteLeave (to, from, next) {
    next(); //最先触发
  }
```
### 异步路由
    在首屏加载时速度会更快
```javascript
  {
    path: '/login',
    component: () => import('@/views/login/login')
  }
  //使用这种方法需要安装一个插件，npm i babel-plugin-syntax-dynamic-import -D
  //.babellic 里的plugin要添加 'syntax-dynamic-import'
```
