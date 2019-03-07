# 异步操作

异步操作： 同时进行多个操作，用户体验好；代码混乱
同步操作： 一次只能进行一个操作， 用户体验不好；清晰

------

### 融合异步、同步

#### Promise

Promise —— 封装异步操作

```javascript
let p = new Promise(function(resolve, reject){
  // 异步...
  // resolve - 解决
  // reject - 拒绝
  $.ajax({
    url: 'data/1.txt',
    dataType: 'json',
    success(arr){
      resolve(arr);
    },
    error(res){
      reject(res);
    }
  })
});
p.then(function(arr){
  alert('success')
}, function(res){
  alert('failed')
})
```