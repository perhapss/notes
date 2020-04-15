vue lifecycle
===
* beforeCreate
* created //操作和数据有关的
* beforeMount
* mounted //挂载节点  操作和dom有关的/操作数据
* beforeUpdate
* updated //更新
* activated
* deactivated
* beforeDestroy //销毁
* destroyed
    服务端渲染只调用beforeCreate和created, 服务端没有执行dom相关的环境
