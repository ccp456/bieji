# ES6 语法特性

## 变量

### 新的声明方法

`let`：不可重复声明

```javascript
let a = 1;
let a = 2;
var b = 1;
var b = 2;
console.log('a'); // 报错
console.log('b'); // 2
```

`const`： 常量

### 解构赋值

1. 等号左右结构一样
2. 右边必须是合法的东西
3. 赋值和结构同时完成

```javascript
jason = {a: 1, b: 2};
let {a, b} = jason; // a=1, b=2
let arr[a,b] = jason; // 报错
let {a, b}= {1, 2}; //报错

arr = [1,2,3];
let [x,y,z] = arr; // x=1 y=2 z=3
```

### 块级作用域

## 函数

### 箭头函数

`()=>{...}` 等同于 `function (){...}`

```javascript
let arr = [1,43,3,6,7]

arr.sort(function (n1,n2){
  return n1 - n2;
  }) // 输出 [1, 3, 6, 7, 43]

arr.sort((n1,n2)=>{return n1-n2}) // 输出 [1, 3, 6, 7, 43]
arr.sort((n1,n2)=>n1-n2) // 输出 [1, 3, 6, 7, 43]
```

> * 如果有且仅有一个参数，()可以省略
> * 如果又且仅有一个语句并且是return，{}及return可以省略

```javascript
arr.sort((n1,n2)=>n1-n2);
```

> * 固定this， 取决在哪声明此函数

```javascript
let json = {
  a: 12,
  fn: () => {
    alert(this.a); // defined
    console(this); // Window
  }
}
```

### 参数、数组、json扩展

`...`
> 收集剩余参数
> 展开参数

```javascript
function show(a,b,...c){
  console.log(a,b,c);
}
show(1,32,4,5,3,2,4,5,6,3) // 1,32,(8)[...]

let arr1 = [12,3,4,5];
let arr2 = [3,4,5,6,];
let arr = [...arr1, ...arr2] // 12,3,4,5,3,4,5,6

let json = {a: 1, b: 2}
alert(...json);// 报错
let json1 ={
  ...json,
  c:3
}
console.log(json1) // a:1, b:2, c:3
```

### 原生对象扩展

#### Array扩展

> map 映射：一一对应

```javascript
let arr = [31,64,56,95,48];
let arr2 = arr.map(item=>item>=60?'及格':'不及格';);
console.log(arr2);//  ["不及格", "及格", "不及格", "及格", "不及格"]
```

> reduce n=>1

```javascript
let arr = [31,64,56,95,48]; //  求平均数
let result = arr.reduce(function (tmp, item, index){
  // alert(index+'次'+tmp+'，'+item)
  if(index===arr.length-1){
    return (tmp+item)/arr.length;
  }else{
    return (tmp+item);
  }
})
console.log(result);
```

> filter 过滤

```javascript
let arr = [31,64,56,95,48,43,77,98,56]; // 将偶数提入数组
let arr2 = arr.filter(item=>item%2==0);
console.log(arr2);
```

> forEach 遍历

```javascript
let arr = [31,64,56,95,48,43,77,98,56]; // 将偶数提入数组
arr.forEach((item, index)=>{
  alert(`第${index+1}个：${item}`);
})
```

### 模板字符串

```javascript
let arr = [31,64,56,95,48,43,77,98,56]; // 将偶数提入数组
arr.forEach((item, index)=>{
  alert(`第${index+1}个：${item}`);
})
```

### Json

> JSON.stringify({a:12,b:5}) => '{"a":12, "b":5}'
> JSON.parse('{"a":12, "b":5}') => {a:12,b:5}

```javascript
let json={a:12, b:5, name: 'blue'};
console.log(JSON.stringify(json)); // {"a":12,"b":5,"name":"blue"}

let str = '{"a":12, "b":5}';
let json1 = JSON.parse(str);
console.log(json1); // {a: 12, b: 5}
```
