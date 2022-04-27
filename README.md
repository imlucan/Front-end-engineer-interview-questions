# 初中级前端面试题及答案

## JS 基础

1. **[简答]JS 基本数据类型 引用数据类型**

  ```JS
  // 基本数据类型 number string null undefined bool symbol
  // 引用数据类型 object function array data .... 
  ```

2. **[简答]JS 运算符**

```JS
let a = {
  i: 1,
  toString: () => a.i + 1,
};
console.log(a == "2"); // 输出是？
console.log(a === "2"); // 输出是？
// 解释一下原因
```

3. **[实践]JS 数据结构转换**

``` JS
// 原数据结构
let arr = [
  {id: 1, name: '部门1', pid: 0},
  {id: 2, name: '部门2', pid: 1},
  {id: 3, name: '部门3', pid: 1},
  {id: 4, name: '部门4', pid: 3},
  {id: 5, name: '部门5', pid: 4},
]
```

```JSON
//目标数据结构
{
    "id": 1,
    "name": "部门1",
    "pid": 0,
    "childrens": [
        {
            "id": 2,
            "name": "部门2",
            "pid": 1,
            "childrens": null
        },
        {
            "id": 3,
            "name": "部门3",
            "pid": 1,
            "childrens": [
                {
                    "id": 4,
                    "name": "部门4",
                    "pid": 3,
                    "childrens": [
                        {
                            "id": 5,
                            "name": "部门5",
                            "pid": 4,
                            "childrens": null
                        }
                    ]
                }
            ]
        }
    ]
}
```

## ES6

1. **[简答]简述var、let、const 区别**
2. **[简答]解构赋值**
   
```JS
const [a, ...b] = [1, 2, 3, 4, 5];
console.log(a);
console.log(b);

const { apple, ...fruits } = { apple: "red", orange: "orange", banana: "yellow" };
console.log(apple);
console.log(fruits);

const func(a,...args) {
  console.log(args)
}
func(1,"2","3")
```

1. **[实践]DiffArray**
   
```JS
// 两个元素均为整型的数组
const arrA = [1, 2, 3];
const arrB = [2, 4];
// 现在需要从arrA中去除等于arrB的元素，生成一个新的数组
// 期望结果 
const res = [1, 3]
// 实现它！注意参数顺序 a - b
const simpleArrayDiff = (a,b) => {
  // do sth
}

// 好 现在甲方改需求了 他说数组里面不是简单的整型了
const arrAA = [
  { id: 1, name: "Mike" },
  { id: 2, name: "Cathy" },
  { id: 3, name: "Lauran" },
  { id: 4, name: "Jack" },
];

const arrBB = [
  { id: 1, name: "Mike" },
  { id: 2, name: "Cathy" },
  { id: 5, name: "Tom" },
];

// 期望结果
const res_ =  [
  { id: 3, name: "Lauran" },
  { id: 4, name: "Jack" },
]
// 重构上面的函数吧！
const arrayDiff = (/*...*/)=>{
  // do sth
}

```

4. **[实践]Promise及异步**

```JS

const a = new Promise((resolve) => {
    setTimeout(() => {
        resolve("a")
    }, 1000)
})

const b = new Promise((resolve) => {
    setTimeout(() => {
        resolve("b")
    }, 2000)
})

const c = new Promise((resolve，reject) => {
    setTimeout(() => {
        reject("c")
    }, 3000)
})
// 以下控制台输出什么
Promise.all([a, b]).then(console.log).catch(console.log);

Promise.race([a, b]).then(console.log).catch(console.log);

Promise.all([a, b, c]).then(console.log).catch(console.log);

Promise.all([a, b])
  .then((res) => "then")
  .then(console.log)
  .catch(console.log);

Promise.all([a, b])
  .then(() => {
    throw "err";
  })
  .then(console.log)
  .catch(console.log);

Promise.all([a, b, c])
  .then(() => {
    throw "err";
  })
  .then(console.log)
  .catch(console.log);
```

## Web

1. **[简单]Http、Websocket的关系和用途**
2. **[简答]跨域问题是什么原因导致的，如何解决**
3. **[简答]实现一个div，在另一个弹性div中水平、垂直居中，列举你知道的方式**
4. **[实践]事件防抖**

```JS
//实现一个简单的事件防抖，频繁触发fn时，只会触发最后一次
const debounce=(fn,timer)=>{
  // impl
  let pre = new Date
  return function()=>{
    let func 
    let now = new Date
    if(now - pre > timer) {
      func = fn.apply(this,...args)
    }else{
      pre = now
    }
  }
}
//实现一个简单的事件节流，频繁触发fn时，一段时间内仅执行一次
const throttle=(fn,timer)=>{
  // impl
}
```

## Vue 2.X 及 相关工具

1. [简答]Vue的优缺点，以及如何解决你认为的缺点
2. [简答]简述双向绑定的实现，以及无法响应的应对措施
3. [简答]简述computed和watch异同和实践推荐
4. [简答]`<keep-alive>`的作用和用法
5. [简答][Axios]我想要确保所有请求的params中包含字段hallo，为没有这个字段的请求添加默认值"world"
6. [简答][vue-router]基本概念，实现一个简单的路由鉴权
7. [简答]
8. [简答][vuex]基本概念，最佳使用场景
9. [简答]如何实现组件与组件之间通信

