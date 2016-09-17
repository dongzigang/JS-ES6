<h3>prpmise对象</h3>

为了使异步操作更优雅

对象的状态不受外界影响。Promise对象代表一个异步操作，

有三种状态：Pending（进行中）、Resolved（已完成，又称Fulfilled）和Rejected（已失败）

<h3>基本用法</h3>

ES6规定，Promise对象是一个构造函数，用来生成Promise实例。

下面代码创造了一个Promise实例。

```
var promise = new Promise(function(resolve, reject) {
  // ... some code

  if (/* 异步操作成功 */){
    resolve(value);
  } else {
    reject(error);
  }
});
```
resolve, reject这两个参数是两个函数

resolve函数的作用是，将Promise对象的状态从“未完成”变为“成功”（即从Pending变为Resolved），在异步操作成功时调用，并将异步操作的结果，作为参数传递出去；

reject函数的作用是，将Promise对象的状态从“未完成”变为“失败”

Promise实例生成以后，可以用then方法分别指定Resolved状态和Reject状态的回调函数。

then方法可以接受两个回调函数作为参数。第一个回调函数是Promise对象的状态变为Resolved时调用，第二个回调函数是Promise对象的状态变为Reject时调用。其中，第二个函数是可选的，不一定要提供。这两个函数都接受Promise对象传出的值作为参数。
```
promise.then(function(value) {
  // success
}, function(error) {
  // failure
});
```
example1

```
function timeout(ms) {
  return new Promise((resolve, reject) => {
    setTimeout(resolve, ms, 'done');
  });
}

timeout(100).then((value) => {
  console.log(value);
});
```


```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>hello world</title>
	<style>
		.ball{
			width: 40px;
			height: 40px;
			border-radius: 50%;
			
		}
		.ball1{
			background-color: red;
		}
		.ball2{
			background-color:green; 
		}
		.ball3{
			background-color: blue;
		}
	</style>
</head>
<body>
    <div class="ball ball1" style="margin-left:0px;"></div>
    <div class="ball ball2" style="margin-left:0px;"></div>
    <div class="ball ball3" style="margin-left:0px;"></div>
	<script>
	    var ball1=document.querySelector('.ball1');
	    var ball2=document.querySelector('.ball2');
        var ball3=document.querySelector('.ball3');
		function Animate(ball,distance){
			return new Promise((resolve,reject)=>{
							function _animate(){
								setTimeout(()=>{
									var marginLeft=parseInt(ball.style.marginLeft,10)						
									if(marginLeft==distance){
										resolve();
										console.log("resolve")
									}
									else{
										if(marginLeft<distance){
											console.log("+++")
											marginLeft++
										}
										else{
											marginLeft--
										}
									ball.style.marginLeft=marginLeft+'px';
									_animate()
									}
								},13)
							}
				_animate()
			})
		}
		Animate(ball1,100)
		.then(()=>Animate(ball2,200))
		.then(()=>Animate(ball3,300))
		.then(()=>Animate(ball3,150))
		.then(()=>Animate(ball2,150))
		.then(()=>Animate(ball1,150))
	</script>
</body>
</html>
```
