object 
===
### 属性的遍历
* for...in

        for...in循环遍历对象自身的和继承的可枚举属性（不含 Symbol 属性）。
        
* Object.keys(obj)

        Object.keys返回一个数组，包括对象自身的（不含继承的）所有可枚举属性（不含 Symbol 属性）的键名。
        
* Object.getOwnPropertyNames(obj)

        Object.getOwnPropertyNames返回一个数组，包含对象自身的所有属性（不含 Symbol 属性，但是包括不可枚举属性）的键名。
        
* Object.getOwnPropertySymbols(obj)

        Object.getOwnPropertySymbols返回一个数组，包含对象自身的所有 Symbol 属性的键名。
        
* Reflect.ownKeys(obj)

        Reflect.ownKeys返回一个数组，包含对象自身的所有键名，不管键名是 Symbol 或字符串，也不管是否可枚举。
### super 关键字
        指向当前对象的原型对象。super.foo等同于Object.getPrototypeOf(this).foo（属性）
        或Object.getPrototypeOf(this).foo.call(this)（方法）。但是绑定的this却还是当前对象obj
### 属性名表达式
> ES6 允许字面量定义对象时，用方法二（表达式）作为对象的属性名，即把表达式放在方括号内。
### 方法的 name 属性
> 函数的name属性，返回函数名。对象方法也是函数，因此也有name属性。
```javascript
const person = {
  sayName() {
    console.log('hello!');
  },
};
person.sayName.name   // "sayName"
```
### 扩展运算符
(...rest)
### 链判断运算符
> ?.  直接在链式调用的时候判断，左侧的对象是否为null或undefined。如果是的，就不再往下运算，而是返回undefined。
* obj?.prop // 对象属性
* obj?.[expr] // 同上
* func?.(...args) // 函数或对象方法的调用
### Null 判断运算符
        读取对象属性的时候，如果某个属性的值是null或undefined，有时候需要为它们指定默认值。常见做法是通过||运算符指定默认值。
        只要属性的值为null或undefined，默认值就会生效，但是属性的值如果为空字符串或false或0，默认值也会生效。
> Null 判断运算符??。它的行为类似||，但是只有运算符左侧的值为null或undefined时，才会返回右侧的值。

## 对象新增的方法
### Object.is()
        相等运算符（==）和严格相等运算符（===）。它们都有缺点，前者会自动转换数据类型，后者的NaN不等于自身，以及+0等于-0。
        Object.is();不同之处只有两个：一是+0不等于-0，二是NaN等于自身。
```javascript
+0 === -0 //true
NaN === NaN // false

Object.is(+0, -0) // false
Object.is(NaN, NaN) // true
```
### Object.assign()
        Object.assign方法用于对象的合并，将源对象（source）的所有可枚举属性，复制到目标对象（target）。
        Object.assign方法的第一个参数是目标对象，后面的参数都是源对象。
* 浅拷贝
* 同名属性的替换
* 数组的处理 会把数组视为对象。
* 取值函数的处理 只能进行值的复制，如果要复制的值是一个取值函数，那么将求值后再复制。
#### 常规用途
* 为对象添加属性
* 为对象添加方法
* 克隆对象
* 合并多个对象
* 为属性指定默认值
### Object.getOwnPropertyDescriptors()
返回指定对象所有自身属性（非继承属性）的描述对象
### Object.keys() Object.values() Object.entries()
* Object.keys方法，返回一个数组，成员是参数对象自身的（不含继承的）所有可遍历（enumerable）属性的键名。
> Object.values方法返回一个数组，成员是参数对象自身的（不含继承的）所有可遍历（enumerable）属性的键值。
> Object.entries()方法返回一个数组，成员是参数对象自身的（不含继承的）所有可遍历（enumerable）属性的键值对数组。
 ### Object.fromEntries() 
 > Object.fromEntries()方法是Object.entries()的逆操作，用于将一个键值对数组转为对象。
