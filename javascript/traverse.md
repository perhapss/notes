遍历的方法
===
* continue: 中断本次循环
* return 和 break: 直接跳出循环
````javascript
  // for
  var arr = [1, 2, 3]
  for(let i = 0, len = arr.length; i < len; i++) { // 这里的i是代表数组的下标
    console.log(i); // 0, 1, 2 
  };　

  // for...of...
  for(var i of arr) {
      console.log(i); // 1, 2, 3
  };

  // for...in..
  for(var i in arr) {
      //do something
  };

  // forEach()
  arr.forEach((item, index, arr) => {
    console.log(item); // 1, 2, 3
    console.log(index); // 0, 1, 2
    console.log(arr); // [1, 2, 3]
    //不能被中断
  });

  // map()
  arr.map((value,index,array) => {
    //do something
  });
````
#### some()
````javascript
  var arr = [1, 2, 3];
  arr.some((item, index, arr) => { // item为数组中的元素，index为下标，arr为目标数组
    console.log(item); // 1, 2, 3
    console.log(index); // 0, 1, 2
    console.log(arr); // [1, 2, 3]  
  })
````
> some作为一个用来检测数组是否满足一些条件的函数存在，同样是可以用作遍历的函数签名同forEach，有区别的是当任一callback返回值匹配为true则会
直接返回true，如果所有的callback匹配均为false，则返回false。
* 如果有一个元素满足条件，则表达式返回true , 剩余的元素不会再执行检测
* 如果没有满足条件的元素，则返回false。

#### every()
````javascript
var arr = [1, 2, 3];
  arr.every((item, index, arr) => { // item为数组中的元素，index为下标，arr为目标数组
    return item > 0; // true
    return index == 0; // false
  })
````
* 如果数组中检测到有一个元素不满足，则整个表达式返回 false ，且剩余的元素不会再进行检测。
* 如果所有元素都满足条件，则返回 true。

#### for...in...
````javascript
  var arr = [1, 2, 3]
  for(var item in arr) { // item遍历数组时为数组的下标，遍历对象时为对象的key值
    console.log(item); // 0, 1, 2
  };
````
> for...in更多是用来遍历对象，很少用来遍历数组， 不过 item 对应与数组的 key值，建议不要用该方法来遍历数组，因为它的效率是最低的。

#### filter
````javascript
  var arr = [1, 2, 3];
  arr.filter(item => { // item为数组当前的元素
    return item > 1; // [2, 3]
  })
````
> filter() 方法创建一个新的数组，新数组中的元素是通过检查指定数组中符合条件的所有元素。

#### map
````javascript
  var arr = [1, 2, 3];
  arr.map(item => { // item为数组的元素
    console.log(item); // 1, 2, 3
    return item * 2; // 返回一个处理过的新数组[2, 4, 6]
  })
````
> map() 方法返回一个新数组，数组中的元素为原始数组元素调用函数处理后的值。
> map() 方法按照原始数组元素顺序依次处理元素。
> 这种方式也是用的比较广泛的，虽然用起来比较优雅，但实际效率还比不上foreach

