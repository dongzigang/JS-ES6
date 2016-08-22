# hello-ECMAScript-6
ECMAScript 6 入门笔记
ES6新增的比较常用的内容<br>
<h2>1.let命令</h2>
ES6新增了let命令，用来声明变量。它的用法类似于var，但是所声明的变量，只在let命令所在的代码块内有效。<br>

    {
      let a = 10;
      var b = 1;
    }
    
    a // ReferenceError: a is not defined.
    b // 1
    
利用let声明i,获取当前循环次数的索引<br>

用var 声明

    var a = [];
    for (var i = 0; i < 10; i++) {
      a[i] = function () {
        console.log(i);
      };
    }
    a[6](); //10
    
    这样取不到索引值，需要声明一个index
    <!DOCTYPE html>
    <html lang="en">
    <head>
      <meta charset="UTF-8">
      <title>Document</title>
       <style type="text/css">
         #main li{
             display: inline-block;
             width: 100px;
             height: 100px;
             background: #aaa;
         }
       </style>
    </head>
    <body>
      <ul id="main">
        <li>0</li>
        <li>1</li>
        <li>2</li>
        <li>3</li>
        <li>4</li>
      </ul>
    
      <script type="text/javascript">
        var main=document.getElementById("main");
        var mains=main.getElementsByTagName("li");   
        for(var i=0;i<mains.length;i++){
          mains[i].index=i;  //重点就是在这里！
          mains[i].onclick=function(){
            this.style.background="red";
            console.log(this.index);
          }
        }
    
      </script>
    </body>
    </html>

如果用let声明i     上面的js部分可以这样写

      <script type="text/javascript">
        var main=document.getElementById("main");
        var mains=main.getElementsByTagName("li");   
        for(let i=0;i<mains.length;i++){
          mains[i].onclick=function(){
            this.style.background="red";
            console.log(i);
          }
        }
    
      </script>

<h3>
    let 不存在变量提升<br>
    不允许重复声明已经声明过的变量
</h3>
<h2>const命令</h2>
const声明一个只读的常量。一旦声明，常量的值就不能改变，除此之外用法同let<br>
ps:let不能重复声明的变量，但变量值可以改变

        const PI = 3.1415;
        PI // 3.1415
        
        PI = 3;
        // TypeError: Assignment to constant variable.

用let const class声明的变量不是全局变量 
