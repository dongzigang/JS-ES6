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
