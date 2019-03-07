# 面向对象

## 语言发展历史

机器语言(面向机器) -> 汇编语言 -> 低级语言(面向过程)(C语言) -> 高级语言(面向对象)(Java, Python, Javascript) -> 模块系统 -> 框架 -> 系统接口(API)

## ES5与ES6的面向对象

1. 没有系统统一写法
2. ES6的继承更方便以及便于扩展

```javascript
//以函数的形式来写对象，同时是类也是构造函数
function Person(name, age){ //1.既是构造函数，又是类
  this.name=name;
  this.age=age;
};

//添加方法
Person.prototype.show = function(){ //2.方法独立在类之外

};
//3.没有专门的继承方法
function Worker(name, age, job){
  Person.call(this, name, age); //4.从父类继承要靠骗
  this.job=job;
};

Worker.protoype = new Person(); //5.没有专门继承父类方法的方式
worker.protoype.constructor = Worker;
```

```javascript
//ES6有单独的类的声明、构造函数声明
class Peson(){
  construction(name, age){
    this.name = name;
    this.age = age;
  }
}
```

`class`：类声明

`construct`：构造函数

```javascript
class xxx{
  constructor(){
    this.x=x
  }
}
```

`extends`：继承

`super`：父类

```javascript
class sub extends xxx{
  constructor(){
    super(xx,xx);
  }
  fn2(){

  }
}
```

------

# 模块系统

## JS模块系统

没有模块 -> CMD(Common Module )