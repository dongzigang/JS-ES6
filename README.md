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
<h2>2.const命令</h2>
const声明一个只读的常量。一旦声明，常量的值就不能改变，除此之外用法同let<br>
ps:let不能重复声明的变量，但变量值可以改变

        const PI = 3.1415;
        PI // 3.1415
        
        PI = 3;
        // TypeError: Assignment to constant variable.

用let const class声明的变量不是全局变量 

<h2>数组的解构赋值</h2>
ES6允许按照一定模式，从数组和对象中提取值，对变量进行赋值，这被称为解构

        let [foo, [[bar], baz]] = [1, [[2], 3]];
        foo // 1
        bar // 2
        baz // 3
        
        let [ , , third] = ["foo", "bar", "baz"];
        third // "baz"
        
        let [x, , y] = [1, 2, 3];
        x // 1
        y // 3
        
        let [head, ...tail] = [1, 2, 3, 4];
        head // 1
        tail // [2, 3, 4]
        
        let [x, y, ...z] = ['a'];
        x // "a"
        y // undefined
        z // []
对象的解构赋值

        var { bar, foo } = { foo: "aaa", bar: "bbb" };
        foo // "aaa"
        bar // "bbb"
        
        var { baz } = { foo: "aaa", bar: "bbb" };
        baz // undefined
        
字符串的解构赋值

        const [a, b, c, d, e] = 'hello';
        a // "h"
        b // "e"
        c // "l"
        d // "l"
        e // "o"
        
<h3>变量解构的用途</h3>

1.交换变量的值

    [x, y] = [y, x];

2.从函数返回多个值<br>
函数只能返回一个值，如果要返回多个值，只能将它们放在数组或对象里返回。有了解构赋值，取出这些值就非常方便。

        // 返回一个数组
        
        function example() {
          return [1, 2, 3];
        }
        var [a, b, c] = example();
        
        // 返回一个对象
        
        function example() {
          return {
            foo: 1,
            bar: 2
          };
        }
        var { foo, bar } = example();

3.提取json数据

        var jsonData = 	{
        	"staff":[
                {"name":"庄三","age":18},
                {"name":"李四","age":17},
                {"name":"王五","age":16}
        	]
        	}
        for(let i=0;i<jsonData.staff.length;i++){
        	let { name, age} = jsonData.staff[i];
            console.log(name,age);
        }
        //庄三 18
        //李四 17
        //王五 16

4.遍历map结构

        var map = new Map();
        map.set('first', 'hello');
        map.set('second', 'world');
        
        for (let [key, value] of map) {
          console.log(key + " is " + value);
        }
        // first is hello
        // second is world
       如果只想获取键名，或者只想获取键值，可以写成下面这样
       // 获取键名
       for (let [key] of map) {
         // ...
       }
        // 获取键值
        for (let [,value] of map) {
          // ...
        }

















