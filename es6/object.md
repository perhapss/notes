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