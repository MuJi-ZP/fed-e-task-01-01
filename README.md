### 1. 请说出下列执行的最终结果并解释为什么？
```javascript
var a = [];
for (var i = 0; i < 10; i++) {
  a[i] = function () {
    console.log(i)
  }
} 
a[6]()//10
```
答：   
&emsp;&emsp;最终结果为10，因为在循环中i用的var声明处于全局变量，当循环执行完成时，i变量已经在变成了10，再调用函数输出就只会是10。
  

### 2. 请说出下列执行的最终结果并解释为什么？
```javascript
var tmp = 123;

if (true) {
  console.log(tmp)
  let tmp;
}
```
答：    
&emsp;&emsp;最终执行结果为 "Uncaught ReferenceError: Cannot access 'tmp' before initialization"，因为es6中当作用域中有let时候，let声明的变量会绑定该作用域，作用域内调用该名称变量只会在内部寻找，本题中，调用在声明之前，所有报错。
  
### 3. 结合 ES6 新语法，用最简单的方法找出数组中的最小值


```javascript
var arr = [12, 34, 32, 89, 4]
``` 

答：  

```javascript
var arr = [12, 34, 32, 89, 4]
var min = Math.min(...arr)
``` 

### 4. 请说明 var，let，const 三种声明变量的方式之间的具体差别？
答：  

1. var可以作用到函数域，let只能作用于当前作用域；
2. var会变量名提升，let、const不会声明提升；
3. var可以重复声明一个变量，let、const在一个作用域下不能重复声明同一个变量；
4. const是一个常量/恒量，声明后不可修改，且声明时必须赋值；
5. const不可修改针对内存的指向，其内部属性和方法依然可以变化、增减，如对象中的值，obj.x=1;是允许的。  

### 5. 请说出下列执行的最终结果并解释为什么？

```javascript
var a = 10;
var obj = {
  a: 20,
  fn(){
    setTimeout(() => {
      console.log(this.a)
    })
  }
}
obj.fn()//20
```   
答：  
&emsp;&emsp;输出20；因为是obj调用的fn方法，所以this指向obj，a值为20，setTimeout的执行时间为0，且无其他执行项，直接调用console.log(this.a),输出20.  

### 6. 简述 Symbol 类型的用途？  
答：  
&emsp;&emsp;Symbol可以用来获取一个唯一的值，每一个Symbo数据类型都是独一无二的。可以用来作为对象的属性名，用来定义私有属性和方法，所有需要一个唯一值的地方都可以试试。

### 7.说说什么是深拷贝，什么是浅拷贝？
答：  
&emsp;&emsp;浅拷贝：对象的成员值中有对象的情况下，在复制生成新对象A后，旧对象B改变会引起A的改变就是浅拷贝，因为内存地址没有发生变动，只是指向内存地址的对象又多了一个。  
&emsp;&emsp;深拷贝：对象的成员值中有对象的情况下，在复制生成新对象A后，旧对象B改变不会引起A的改变就是深拷贝，因为内存地址发生了变动，A创建并指向了一个新的内存。 
 
### 8. 谈谈你是如何理解 JS 异步编程的，Event Loop 是做什么的，什么是宏任务，什么是微任务？
答：  
&emsp;&emsp;JS的异步编程一般通过回调函数实现的解决同步决同步代码阻止塞进程的一种编程方式，同步数据执行完后，回调函数根据执行顺序进入消息队列，调用栈依次取出并执行；  
 &emsp;&emsp;Event Loop是一种运行机制，在JS中是事件循环，用来解决JS的但行程问题；  
&emsp;&emsp;在我理解中，宏任务和微任务都是异步回调函数,不同的是微任务直接会在调用后进入调用队列的末尾，在一轮结束后调用，而宏任务则是在任务队列里排队。

### 9. 将下面异步代码使用 Promise 改进
```javascript
setTimeout(function(){
  var a = "hello";
  setTimeout(function(){
    var b = "lagou";
    setTimeout(function(){
      var a = "I ? U";
      console.log(a + b + c);
    },10)
  },10)
},10)
```
答：  

```javascript
Promise.resolve("hello").then(function (a) {
    return `${a} lagou`
}).then(function (b) {
    console.log(`${b} I ? U`)
})
```  

### 10. 请简述 TypeScript 和 JavaScript 的关系？
答：  
&emsp;&emsp;TypeScript是 Javascript 的超集，是一种在JavaScript基础上对其弱语言和动态类型进行了增强的语言，在使用时需要重新编译成JavaScript。

### 11. 请谈谈你所认为 TypeScript 的优缺点？
答：  
优点：  
&emsp;&emsp;1.类型系统实际上是最好的文档，大部分的函数看看类型的定义就可以知道如何使用了  
&emsp;&emsp;2.可以在编译阶段就发现大部分错误，这总比在运行时候出错好  
&emsp;&emsp;3.增强了编辑器和 IDE 的功能，包括代码补全、接口提示、跳转到定义、重构等   
&emsp;&emsp;4.TypeScript 非常包容，渐进式的语言降低门槛  
&emsp;&emsp;5.TypeScript 是 JavaScript 的超集，.js 文件可以直接重命名为 .ts 即可  
&emsp;&emsp;6.隐式类型推断,即使不显式的定义类型，也能够自动做出\[类型推论\]()  
&emsp;&emsp;7. 可以定义从简单到复杂的几乎一切类型  
&emsp;&emsp;8. 即使 TypeScript 编译报错，也可以生成 JavaScript 文件  
&emsp;&emsp;9. 兼容第三方库，即使第三方库不是用 TypeScript 写的，也可以编写单独的类型文件供 TypeScript 读取  
&emsp;&emsp;10.TypeScript 拥有活跃的社区  
&emsp;&emsp;11.TypeScript 拥抱了 ES6 规范，也支持部分 ESNext 草案的规范

缺点：  
&emsp;&emsp;1.有一定的学习成本，增加了很多定义，需要理解接口（Interfaces）、泛型（Generics）、类（Classes）、枚举类型（Enums）等前端工程师可能不是很熟悉的概念    
&emsp;&emsp;2.短期可能会增加一些开发成本，毕竟要多写一些类型的定义，不过对于一个需要长期维护的项目，TypeScript 能够减少其维护成本  
&emsp;&emsp;3.集成到构建流程需要一些工作量  
&emsp;&emsp;4.可能和一些库结合的不是很完美


