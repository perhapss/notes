set Map
===
### set
```javascript
// 去除数组的重复成员
[...new Set(array)]
//去除字符串里面的重复字符
[...new Set('ababbc')].join('')
``` 
> 向 Set 加入值的时候，不会发生类型转换，所以5和"5"是两个不同的值。 Set 加入值时认为NaN等于自身
### Set 实例的属性和方法
* Set.prototype.constructor：构造函数，默认就是Set函数。
* Set.prototype.size：返回Set实例的成员总数。

* Set.prototype.add(value)：添加某个值，返回 Set 结构本身。
* Set.prototype.delete(value)：删除某个值，返回一个布尔值，表示删除是否成功。

* Set.prototype.has(value)：返回一个布尔值，表示该值是否为Set的成员。
* Set.prototype.clear()：清除所有成员，没有返回值。

*遍历*
* Set.prototype.keys()：返回键名的遍历器
* Set.prototype.values()：返回键值的遍历器
* Set.prototype.entries()：返回键值对的遍历器
* Set.prototype.forEach()：使用回调函数遍历每个成员
### Map
Map 结构的实例有以下属性和操作方法。 
* size 属性 返回 Map 结构的成员总数。
* Map.prototype.set(key, value)  set方法设置键名key对应的键值为value，然后返回整个 Map 结构。如果key已经有值，则键值会被更新，否则就新生成该键。
* Map.prototype.get(key)  get方法读取key对应的键值，如果找不到key，返回undefined。
* Map.prototype.has(key) 返回一个布尔值，表示某个键是否在当前 Map 对象之中。
* Map.prototype.delete(key) 删除某个键，返回true。如果删除失败，返回false。
* Map.prototype.clear() 清除所有成员，没有返回值。
*遍历*
* Map.prototype.keys()：返回键名的遍历器。
* Map.prototype.values()：返回键值的遍历器。
* Map.prototype.entries()：返回所有成员的遍历器。
* Map.prototype.forEach()：遍历 Map 的所有成员。
> Map 转为数组  [...myMap]
### WeakMap
WeakMap只接受对象作为键名（null除外），不接受其他类型的值作为键名。
