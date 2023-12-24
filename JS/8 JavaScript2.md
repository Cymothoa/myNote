# JavaScript

[TOC]

## -循环语句

### -	for

> 格式：
>
> for（初始化变量；判断条件；执行表达式）{...}
>
> 当条件满足时，执行循环；条件不满足，跳出循环

```js
for(var i=0;i<5;i++)
{
    console.log("当前值为：" + i);
}
```

### -	while

> 格式：
>
> while（判断条件）{...执行表达式}

```js
while(a<15)
{
    document.write(a);
    a++;
}
```

### -	do while

> 格式：
> do{...表达式} while（判断条件）
>
> 无论条件成立与否 都会先执行一次循环

```js
do
{
    console.log(a,'do while');
    a++;
}while(a<20)
```

### -	break

> 跳出该层循环

### -	continue

> 继续下次循环，结束该次循环
>
> （下例中continue导致只输出 a=值 的句子，略过了n）

```js
while(a<15)
{
    console.log("a=" + a);
    a++;
    continue;
    for(var n=0;n<5;n++)
    {
        console.log("n=" + n);
    }
}
```

## -函数

> 格式：
>
> 函数
>
> function  函数名() {... ...}
>
> 函数调用
>
> 函数名()  ;
>
> 函数名命名规则与变量命名规则相同

```js
var sum=1;
function f1()
{
    console.log(sum,"开始"); //sum = 1
    console.log("这是第一个函数");
}
f1();

function f2()
{
    document.write("这是第二个函数");
}
f2();

function f3(a,b){
    sum=a+b;
    console.log(sum,"sum");
}
console.log(sum,"最后"); //sum = 1
f3(10,5); //sum = 15
```

### -	全局变量

> 可以在整体页面使用

### -	局部变量

> 是在局部声明使用的变量 全局读不到

## -数组

> 长度 length
>
> 下标 位数-1

### -生成空数组的方法

> 1.
>
> var arr3 = []; 
>
> arr3[0] = '我'; 
>
> arr3[1] = '你';
>
> 2.
>
> var arr1 = new Array();
>
> arr1[0] = 'eeee';

```js
var arr3 = [];
arr3[0] = '我';
arr3[1] = '你';
console.log(arr3);
var arr = [1,2,3,4,5,6,7];
console.log(arr);
// 长度 length
console.log(arr.length);
// 生成一个空数组
var arr1 = new Array();
console.log(arr1,'arr1');
var arr2 = [1,'3232','动画设计师',48,9,true];
console.log(arr2,'arr2');
console.log(arr2[2]);
// 下标 名称[下标第几个]
console.log(arr2[5]);

for(var i=0;i<arr.length;i++)
{
    console.log("下标:"+ i)
}
```

### -数组的方法

#### -push pop shift unshift

> - push：向数组最后一个位置添加元素
> - unshift：向数组第一个位置添加元素
> - pop：删除数组最后一个元素
> - shift：删除数组第一个元素

![](C:\Users\Strobo\Desktop\WEB\图片\arr.png)

```js
var arr=["1","2","3","4","5"];
arr.push("最后");
console.log(arr);
arr.pop();
console.log(arr);
arr.unshift("第一个");
console.log(arr);
arr.shift();
console.log(arr);
```

#### -join

> 将数组转换成用逗号隔开的**字符串**
>
> join（）-->改变括号中的内容可替换逗号

```js
console.log(arr.join('(._.)'),'join');
```

#### -concat

> 连接数组
>
> 格式：
>
> var 数组3名字 = 数组1名字 . concat (数组2名字) ；

```js
var burgey = ["kfc","mc","burgeyking"];
var list = arr.concat(burgey);
console.log(list,'list');
```

#### -splice

> - 2个值：splice（从哪个**下标**开始删除，删除的元素个数）
> - 多个值：splice（从哪个**下标**开始删除，删除的元素个数，添加的替换内容）
>
> *可改变原数组 例子如下
>
> del为删除掉的内容
>
> list为剩下的内容
>
> list的值splice前后发生改变   =>  可知splice可改变原数组

![](C:\Users\Strobo\Desktop\WEB\图片\splice.png)

```js
var del = list.splice(2,4,'eat','131');
console.log(del,'del');
console.log(list,'list');
```

#### -slice

> 删除掉数组的前n个元素
>
> 对原数组没有影响
>
> - 1个值：截取到索引位置后的全部值
> - 2个值：截取到第二值 索引位置的前一个 不包含第二个索引位置

![](C:\Users\Strobo\Desktop\WEB\图片\slice.png)

```js
var newList = list.slice(2);
console.log(list,'list')
console.log(newList,'newList');
```

#### -reverse

> 倒序（顺序上）

```js
var bb = list.reverse();
console.log(bb,'bb');
```

#### -toString

> 强制转换成字符串
>
> 转换成由,（逗号）分割的字符串

```js
var cc = list.toString();
console.log(cc,'cc');
```

#### - + ” “    字符串 =>数组转字符串

> 强制转换成字符串
>

```js
list += " ";
console.log(list,"转字符串");
```

#### -sort

> sort排序  按照Unicode编码排序
>
> tips：
>
> 1. 升序排列 a-b
> 2. 降序排列 b-a

```js
//例子：利用sort排序实现数组的升序排序

var newArr = [23,5,76,199,32,2,78,10];
newArr.sort(function(c,d) {
    // return 返回值
    return c-d;
})
console.log(newArr,'newArr')
```

## -对象

> 格式：
>
> var obj1 = {};
>
> var obj = {
>
>   name: '麦当劳',
>
>   sex: '女',
>
>   age: '香辣鸡腿堡'
>
> }

### -生成空对象的方法

> **1.**
>
> var obj3 = {}; 
>
> obj3[0] = '我'; 
>
> obj3[1] = '你';
>
> **2.**
>
> var obj1 = new Object();
>
> obj1[0] = 'eeee';

### -对象的声明

> *对象名.属性名 = 属性值*
>
> console.log(obj.name);

### -对象的使用

> *对象名.属性名 = 属性值*
>
> console.log(obj.name);

### -混淆点

> 下例中new的x y z类型为**object**
>
> 注意：
>
> console.log( x,'x1');    //String {''} 'x1'
>
> 这里''外面有 **{ }** 对象

```js
console.log(typeof arr);//Object
console.log(typeof obj);//Object

var x = new String();        // 把 x 声明为 String 对象
var y = new Number();        // 把 y 声明为 Number 对象
var z = new Boolean();       //	把 z 声明为 Boolean 对象
// 请避免字符串、数值或逻辑对象。他们会增加代码的复杂性并降低执行速度。

var aa = 1;
console.log(typeof aa);

console.log(typeof x,'x');
console.log(typeof y,'y');
console.log(typeof z,'z')
console.log( x,'x1');//String {''} 'x1'
console.log( y,'y1');//Number {0} 'y1'
console.log( z,'z1');//Boolean {false} 'z1'
```

## -Date

```js
// Date对象 
var date = new Date(); 
console.log(date.getFullYear(),'当前的年份'); 
console.log(date.getMonth()+1,'月份') 
console.log(date.getDate(),'日') 
console.log(date.getHours(),'小时') 
console.log(date.getMinutes(),'分钟') 
console.log(date.getSeconds(),'秒') 
console.log(date.getMilliseconds(),'毫秒') 
console.log(date.getDay(),'星期') 
console.log(date.getTime(),'获取当前时间的时间戳，也就是毫秒')
```

## -字符串

### -toUpperCase()

> 将字符串中所有的字母转为**大写**

```js
var a = "This is my name";
var b = a.toUpperCase();
console.log(b,'toUpperCase')
```

### -toLowerCase()

> 将字符串中所有字母转为**小写**

```js
var c = b.toLowerCase();
console.log(c,'toLowerCase')
```

### -concat

> 连接字符串

```js
var d = c.concat("你好",a,b);
console.log(d,'concat');
```

### -trim

> 消除字符串中**前后**的空格

```js
var ff = '    hello,world   wo   ';
var ee = ff.trim();
console.log(ee,'trim');
```

### -indexOf

> 字符串中指定字符串**首次出现**的索引下标位置

```js
var str = "Endymion in Latmos";
console.log(str,"原字符串");
str.indexOf("m");
console.log(str.indexOf("m"));  //4
//显示原字符串中第一个m的下标
```

### -lastIndexOf

> 字符串中指定字符串**最后出现**的索引下标位置

```js
var str = "Endymion in Latmos";
console.log(str,"原字符串");
str.lastIndexOf("m");
console.log(str.lastIndexOf("m"));  //15
//显示原字符串中最后一个m的下标
```

### -slice

> - 一个值 截取当前索引下标位置到最后的内容
>
> - 两个值 截取当前索引下标位置到第二个索引下标位置（ 不包含第二个索引下标 ）
>
> 不会改变原字符串

```js
var aa = str.slice(-12,-6);
console.log(aa,'slice方法');
```

### -substring

> - 一个值 截取当前索引下标位置到最后的内容
>
> - 两个值 截取当前索引下标位置到第二个索引下标位置（ 不包含第二个索引下标 ）
>
> 不会改变原字符串

```js
var bb = str.substring(3);
console.log(bb,'substring方法')
```

#### -slice与substring的区别

> slice **允许负数截取** 从后往前**-1**开始 从前往后0开始
>
> （截取负数时，绝对值上 大数在前 小数在后）

### -substr

> 有两个值：
>
> - 第一个值 截取下标的起始索引位置 
> - 第二个值 截取的长度 
>
> 不会改变原字符串

```js
var cc = str.substr(3,12);
console.log(cc,'substr方法')
```

### -replace

> 替换方法
>
> 用于指定字符串替换
>
> 不会改变原字符串
>
> str.replace("原字符串要替换的",'用于替换的字符');

```js
var dd = str.replace("Endymion",'Strobo');
console.log(dd,'replace方法')
console.log(str,'字符串1');
```

### -split

> 字符串转数组
>
> 字符串  =>  数组
>
> tips：
>
> 括号里可以不写东西 
>
> 这里写了逗号，原字符串里若有一个逗号，则转成数组后将按照逗号前后将原字符串变成两个数组的元素

```js
var ff = str.split(",");
console.log(ff,"split方法")
```

### -charAt

> 返回指定下标的字符

```js
var gg = str.charAt(14);
console.log(gg,'chatAt方法')  //t
```

### ![string](C:\Users\Strobo\Desktop\WEB\图片\string.png)
