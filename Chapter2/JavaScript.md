# 第2节：JavaScript

一、JS的变量

## 1.变量的声明

```Js
var num=1;//使用var生命的变量属于局部变量，只在当前作用与有效。在方法外部可以运行。       
 　　　　　//可以不用声明变量，直接赋值。
num="hahahah";//不用var声明的变量，默认是全局变量，在整个JS文件中使用
```



```js
function func () {
  //    var num=1;//1.使用var定义的变量是方法里面的，不能打印
  num3=10;
}
func();
//    alert(num);//1.不能运行
alert(num3);
```

## 2.使用一行代码强调多个语句。其中b为undefined；

```js
var a=1,b,c="nu";
alert(a);
alert(b);
```

## 3.JS中变量声明的注意事项。

①JS中声明变量的关键字只有var一个，变量的类型取决于所附的值。
 如果声明时未赋值，则返回undefined类型（声明之后没有赋值的变量，不是未声明）。
 ②JS中同一个变量，可以在多次赋值中，被修改数据类型。

```js
var num=1;
num="hahahah ";
```

③变量可以使用var声明，也可以直接声明
 【区别】使用var声明的作用域为局部变量。
 ④在JS中，一个变量可以多次使用var声明，后面的声明相当于直接赋值，没有任何用处。
 ⑤JS变量区分大小写，大写和小写不是一个变量。

二、JS中的数据类型、JS中的常用数值函数、JS中常用的输入输出语句、JS中的运算符

## 1.JS中的数据类型。

①Undefined：使用var声明，但是没有赋值的变量。

②null:表示空的引用。

③Boolean：真假。

④Number：数值类型：包括整形和浮点型。

⑤Object：对象（函数数组统称为对象）。

⑥String：字符串。

## 2.常用数值函数。 

①isNaN用于检测一个变量，是不是一个非数值（Not a Number）
  isNaN在检测时，会先调用Number函数，尝试将变量转为数值类型，如果最终结果能转为数值时，则不是NaN。
 ②Number函数：用于将各种函数数据类型转为数值类型。
 》》》Undefined：无法转换，返回NaN。
 》》》null:转为0；
 》》》Boolean：true转为1，false转为0；
 》》》字符串：
 如果字符串是纯数值字符串，则可以转换。“123”->123
 如果字符串包含非数值字符，则不能转换。"123a"->NaN
 如果是空字符串转为0.""--->0 " "--->0
 ③parseInt():将字符串转为数值类型。
 》》》如果是空字符串，不能转，返回结果是NaN。
 》》》如果是纯数值类型字符串，可以转换，且小数点直接删去，不保留。
 "123"--->>123 "123.9"--->>123
 》》》如果字符串包含非数值字符，则将非数值字符前面的整数进行转换。
 "123a"--->123 "a123"-->>NaN
 ④parseInt():转换机制与parseInt()相同。
 不同的是：转换数值字符串时，如果字符串是小数则可以保留小数。
 "123.5"-->>123.5 "123"-->>123
 ⑤typeof:检测一个变量的数据类型。
 字符串-->String 数值-->number true/false-->boolean
 未定义-->Undefined 对象/null-->object 函数-->function

[     ](javascript:void(0);)

```js
var num=1;
alert(isNaN(num));//false
var num="1";
alert(isNaN(num));//false
var num="a1";
alert(isNaN(num));//true
var num="1a";
alert(isNaN(num));//true
var num="a1";
alert(Number(null));//0
var num="a1";
alert(Number(undefined));//NaN
var num="a1";
alert(Number(Boolean));//NaN
```

[     ](javascript:void(0);)

```js
var num="";
alert(num);//返回空
var num="123.9";
alert(num);//123.9
var num="123.9";
alert(Number(num));//123.9
```

[     ](javascript:void(0);)

```js
var num="123.9";
alert(parseInt(num));//123
alert(Number(undefined));//NaN
alert(Number(null));//0
alert(Number(true));//1
alert(Number("123"));//123
alert(Number("123a"));//NaN
alert(Number(""));//0
alert(parseInt("123.5"));//23
alert(parseInt(123.5));//123
alert(parseInt("123"));//123
alert(parseInt("123a"));//123
alert(parseInt("a123"));//NaN
alert(typeof("123.5"));//string
alert(typeof(123));//number
alert(typeof(true));//boolean
alert(typeof(undefined));//undefined
alert(typeof(null));//object
function func () {
num3=10;
}
alert(typeof(func()));//undefined
alert(typeof(func));
```

[     ](javascript:void(0);)

## 3.JS中常用的输入输出语句。

①.alert():弹窗输出
 ②.prompt();弹窗输入，接收两部分参数。①输入提示内容②输入框的默认文本。（两部分都可以省略）
 输入的内容默认都是字符串。
 ③.document.write();在浏览器屏幕上面打印。
 ④.console.log();浏览器控制台打印。

```js
var str =prompt("请输入一句话","你真帅");//两块都可以省略//框里显示你真帅
alert(str);//你真帅
alert(typeof(str));//类型string
var str =prompt("请输入一个数");
var str1 =prompt("请输入一个数");//4+5=9
alert(parseInt(str)+parseInt(str1));
```

## 4.JS中的运算符。

①除号：无论符号两边是整数还是小数，除完之后都将按照实际结果保留小数。
 22/10=2.2
 ++ -- + - = += *= /= %= == != 和java一样。
 ②"==="：要求等式两边的数据，类型和数值必须相同，如果类型不同，直接返回false。
 "=="：值判断两边的数据，值是否相同，并不关心等式两边是否是同一种类型。
 !=:不等。 !==：不全等。
 ③& |只能进行按位运算，如果两边不是数值类型，将转为数值运算。
  && ||进行逻辑运算。
 ^相等时为0，不等为1。

```js
console.log(22/10);//2.2
console.log(10/3);//3.3333333333333335
console.log(12.0/6);//2
```

[     ](javascript:void(0);)

```js
var j=0;
var c=0;
for(var i=0;i<100;i++){
c=j++;
}
console.log(c);//99
var j=0;
for(var i=0;i<100;i++){
j=j++;
}
console.log(j);//0
var j=0;
for(var i=0;i<100;i++){
j=++j;
}
console.log(j);//100
```

[     ](javascript:void(0);)

```js
console.log(1=="1a");//false
console.log(1=="1");//true
console.log(1==="1");//false(必须是同一种类型===)
console.log(undefined==null);//true
conole.log(undefined===null);//false
console.log(NaN===NaN);//false
console.log("1"!==1);//false
console.log("1"!=1);//true
console.log(true&12);//0
```

三、JS的分支与循环

## 1.JS中的真假判断。

①Boolean类型：true为真，false为假。
 ②数值类型：0为假，非0为真。
 ③字符串类型：""为假，非空字符串为真。
 ④null/undefined/NaN：全为假。
 ⑤Object：全为真。

[     ](javascript:void(0);)

```js
if(0.0){
console.log(true);
}else{
console.log(false);
}//0为假，其他为真
if(""){
console.log(true);
}else{
console.log(false);
}//""为假，其他为真
if(undefined){
console.log(true);
}else{
console.log(false);
}//假
```

[     ](javascript:void(0);)

## 2.switch结构的（）可以放各种数据类型；比对时，采用"==="进行判断，要求数据类型完全相等。

[     ](javascript:void(0);)

```
　　　　　　　var num=1;
            switch(num){
                case "1":
                console.log("等");
                break;
                default:
                console.log("不等");
                break;
            }//不等
            var num=1;
            switch(true){
                case num>=0&&num<10:
                console.log(1);
                break;
                case num>=10&&num<20:
                console.log(2);
                break;
                default:
                console.log(3);
                break;
            }//1
```

[     ](javascript:void(0);)

## 3.练习：

输入一个数，若是正整数返回该数倒转换的数，如果不是正整数则重新输入。

[     ](javascript:void(0);)

```
　　　　　　　var s=true;
            while(s){
                var s=prompt("请输入一个数");//输入非正整数，提示：
                var str='';//您输入的不是正整数，重新“请输入一个数”
                if(parseInt(s)==s){//输入正整数，如：12345，返回54321
                    while(s>0){
                        var a=s%10;
                          str+=a;
                        s=parseInt(s/10);
                    }
                    console.log(str);
                    s=false;
                }else{
                    console.log("您输入的不是正整数");
                    s=true;
                }
            }
```

[     ](javascript:void(0);)

四、JS中函数的声明与调用 

## 1.函数声明的格式。

```
　　　　　　function 函数名(参数一，参数二){
 　　　　　//函数体代码
　　　　　　return 返回值;
　　　　　　}
```

## 2.函数调用：

 ①直接调用：函数名（参数一，参数二）;
 ②通过事件调用，在HTML标签中，通过时间属性进行调用。

## 3.函数声明与调用的注意事项：

 ①函数中有没有返回值只取决于函数中有没有return，无需可以声明。
 在JS中有返回值可以不接收，没有返回值也可以接收，结果为undefined。
 ②JS中函数的形参列表与实参列表没有任何关联。
 即，有参数可以不赋值，没有参数也可以赋值，未赋值的参数为undefined。
 函数的实际参数个数，取决于实参列表。
 ③JS中函数是变量的唯一作用域。
 那么函数的形参是属于函数的局部变量。
 ④函数的声明与调用语句，没有先后之分，即，可以先写调用语句，在声明函数。

```
 　　　　　　func();
 　　　　　　function func(){}
```

## 4.匿名函数的声明与使用。

①匿名函数表达式：
 var func=function(){};
 调用func()；
 注意：函数的调用语句必须放在声明语句之后！！！
 ②直接将匿名函数赋值给一个事件：
 window.onload=function(){}//文档就绪函数，确保函数中代码，在HTML文档中加载完成之后执行！
 document.getlementById("id").onclick=function(){}
 ③自执行函数：
 《《《!function(){}();//开头用！表明这是自执行函数。推荐。
 《《《(function(){}());//用()将匿名函数声明与调用包裹在一起。推荐。
 《《《(function(){})();//用()将匿名函数声明语句进行包裹。

[     ](javascript:void(0);)

```
　　　　　　　!function(){//one
                alert(123);
            }();//123
 
            (function(){//two
                alert(123);
            }());//123
            
            (function(){//three
                alert(123);
            })();//123
```

[     ](javascript:void(0);)

```
　　　　　　　var func=function(){
                alert(123);
            }
            func();//不能把func();调用放在上面（匿名函数）//123
```

## 5.JS代码的执行顺序。

JS代码的执行分为两个阶段：检查编译阶段，代码执行阶段。
 检查编译阶段：主要检查语法错误，变量的声明，函数的声明等声明操作。
 代码执行阶段：变量的赋值、函数的调用等执行语句，属于代码执行阶段。

```
　　　　　　　　//检查编译阶段：执行操作
               var num;
               function fun(){}
               var func2
```

[     ](javascript:void(0);)

```
　　　　　　　　//代码执行阶段：执行操作
               console.log(num);
               var  num=1;
               func();
               func2();
               var func2=function(){}
               console.log(func2());
```