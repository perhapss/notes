变量的解构赋值
===

### 数组的解构赋值
````javascript
let [foo, [[bar], baz]] = [1, [[2], 3]];
foo // 1
bar // 2
baz // 3
````
> 如果解构不成功，变量的值就等于undefined

#### 默认值
> 解构赋值允许指定默认值
````javascript
  let [foo = true] = [];
  foo // true
  let [x, y = 'b'] = ['a']; // x='a', y='b'
  let [x, y = 'b'] = ['a', undefined]; // x='a', y='b'
````
* ES6 内部使用严格相等运算符（===），判断一个位置是否有值。所以，只有当一个数组成员严格等于undefined，默认值才会生效。

### 对象的解构赋值
````javascript
  let { bar, foo } = { foo: 'aaa', bar: 'bbb' };
  foo // "aaa"
  bar // "bbb"

  let { baz } = { foo: 'aaa', bar: 'bbb' };
  baz // undefined
````
* 对象的解构与数组有一个重要的不同。数组的元素是按次序排列的，变量的取值由它的位置决定；而对象的属性没有次序，变量必须与属性同名，才能取到正确的值。
* 如果解构失败，变量的值等于undefined。

#### 默认值
````javascript
  var {x, y = 5} = {x: 1};
  x // 1
  y // 5
````
* 默认值生效的条件是，对象的属性值严格等于undefined。

### 字符串的解构赋值
> 字符串也可以解构赋值。这是因为此时，字符串被转换成了一个类似数组的对象。
> 类似数组的对象都有一个length属性，因此还可以对这个属性解构赋值。
````javascript
  const [a, b, c, d, e] = 'hello';
  a // "h"
  b // "e"
  c // "l"
  d // "l"
  e // "o"

  let {length : len} = 'hello';
  len // 5
````

### 数值和布尔值的解构赋值
> 解构赋值时，如果等号右边是数值和布尔值，则会先转为对象。
````javascript
  let {toString: s} = 123;
  s === Number.prototype.toString // true

  let {toString: s} = true;
  s === Boolean.prototype.toString // true
````
> 数值和布尔值的包装对象都有toString属性，因此变量s都能取到值。
````javascript
  let { prop: x } = undefined; // TypeError
  let { prop: y } = null; // TypeError
````
> 解构赋值的规则是，只要等号右边的值不是对象或数组，就先将其转为对象。由于undefined和null无法转为对象，所以对它们进行解构赋值，都会报错

### 用途
* 交换变量的值
* 从函数返回多个值
* 函数参数的定义
* 提取 JSON 数据
* 函数参数的默认值
* 遍历 Map 结构
* 输入模块的指定方法
