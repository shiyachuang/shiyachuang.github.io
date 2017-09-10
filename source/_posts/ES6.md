---
title: ES6 study
date: 2017-07-21 19:13:02
tags: Es6
---

-----
- #### let 块级作用域
```js
use strict

if(true) {
   let  fruit = 'apple'
}
console.log(fruit) //fruit is not defined

```
<!-- more -->

- #### const 常量
```js
const name = 'apple'
name = 'banana'
//Assignment to constant variable
const name = {foo : 'apple' }
name.foo = 'banana'
//可以正常运行
```
- ##### 解构数组
```js
let foo = ['one','two','three']
let [one,two,three] =foo
console.log(one,two,three)// one,two,three

```
- #### 解构对象
 只需保证key可以对应就行，也可只取name
```js
let obj = { name:'chuang',age:22,sex:'男'}
let {name,age,sex} = obj
console.log(name,age,sex)//chuang 22 男
```
- #### 箭头函数
```js
let add = (a,b) => { return a+b }
//当后边是表达式的时候也可以简写
let add = (a,b) => a+b
// 他们等同于
let add =function(a,b){
    return a+b
}
//在回调中也可以使用
let nums =[1,2,3]
let doublenum = num.map( i => i*2)
console.log(doublenum)//[2,3,6]

```
- #### this 在箭头函数中的作用
```js
let age =2;
let student = {
    age:1,
    grow: function() {
       setTimeout(() => {
           console.log(++this.age)
       },100)
    }
}
student.grow()//2

```
- #### 对象表达式
 ```js
 let a=1,b=2;
 let obj ={a,b}
 console.log(obj)//Object {a: 1, b: 2}
 ```

- #### Rest参数
当一个函数的最后一参数有'...' 这样的前缀，他会变成一个参数的数组
```js
funtion test(...args) {
    console.log(args)
}
test(2,3,4)//[2，3，4]
funtion test2(name,...args) {
    console.log(args)
}
test2('chuang',2,3,1)//[2,3,1]

```
- #### 展开操作符
    - 用于函数调用
```js
function test(x,y,z) {}
let args =[0,1,2]
test(..args)
```

    - 用于数字面量
```js
let arr1 =[1,2,3]
let arr2 =[4,5,6]
let arr3 =[...arr1,arr2]
console.log(arr3)//[1, 2, 3, 4, 5, 6,]
```

    - 对象的展开操作符
 ```js
 let mike = { name: 'chuang',sex: 'male'}
 mike ={...mike,age:50}
 console.log(mike)//{name: 'chuang',sex: 'male',age:50}
```

