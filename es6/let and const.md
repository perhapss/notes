### let
* let声明的变量，只在let命令所在的代码块内有效
* 不存在变量提升，所以要在声明之后使用
* 暂时性死区，声明后不受当前快外部的影响
* 不能重复用let声明同一个变量

### const
* const声明一个只读的常量。一旦声明，常量的值就不能改变。
  > 但对于复合类型的数据（主要是对象和数组），变量指向的内存地址，保存的只是一个指向实际数据的指针，const只能保证这个指针是固定的（即总是指向另一个固定的地址），至于它指向的数据结构是不是可变的，就完全不能控制了。
  
### 声明变量的6种方法
> es5: var, function

> es6: let, const, import, class

### 顶层对象属性
> 顶层对象，在浏览器环境指的是window对象，在Node中指的是global对象。ES5之中，顶层对象的属性与全局变量是等价的。