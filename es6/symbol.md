symbol
===
> 新的原始数据类型Symbol，表示独一无二的值。
可以转换成字符串和布尔值
```javascript
let sym = Symbol();
String(sym) // 'Symbol(My symbol)'
sym.toString() // 'Symbol(My symbol)'
Boolean(sym) // true
!sym  // false
```
### Symbol.prototype.description
> 返回symbol 的描述，sym.description
### 作为属性名的 Symbol
Symbol 值作为对象属性名时，不能用点运算符。
### Symbol.for()，Symbol.keyFor() 
它接受一个字符串作为参数，然后搜索有没有以该参数作为名称的 Symbol 值。如果有，就返回这个 Symbol 值，否则就新建一个以该字符串为名称的 Symbol 值，并将其注册到全局。
