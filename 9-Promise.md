```
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
