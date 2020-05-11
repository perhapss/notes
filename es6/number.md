number
===
### 二进制和八进制表示法
    二进制和八进制数值的新的写法，分别用前缀0b（或0B）和0o（或0O）表示。
### Number.isFinite(), Number.isNaN()
        如果参数类型不是数值，Number.isFinite一律返回false。
        如果参数类型不是NaN，Number.isNaN一律返回false。
> 它们与传统的全局方法isFinite()和isNaN()的区别在于，传统方法先调用Number()将非数值的值转为数值，再进行判断，而这两个新方法只对数值有效
### Number.parseInt(), Number.parseFloat()
> 与全局方法parseInt()和parseFloat()的行为保持不变
### Number.isInteger()
> 用来判断一个数值是否为整数
### Number.EPSILON
### 安全整数和 Number.isSafeInteger()
### Number.EPSILON
* Math.trunc方法用于去除一个数的小数部分，返回整数部分。
* Math.sign方法用来判断一个数到底是正数、负数、还是零。对于非数值，会先将其转换为数值。无法转换时返回NaN
* Math.cbrt()方法用于计算一个数的立方根。
* Math.clz32()方法将参数转为 32 位无符号整数的形式，然后返回这个 32 位值里面有多少个前导 0。
* Math.imul()方法返回两个数以 32 位带符号整数形式相乘的结果，返回的也是一个 32 位的带符号整数。
* Math.fround()
* Math.hypot方法返回所有参数的平方和的平方根。

### 指数运算符（**）

> 指数运算符可以与等号结合，形成一个新的赋值运算符（**=）。
```javascript
let b = 4;
b **= 3;
// 等同于 b = b * b * b;
```
