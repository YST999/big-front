# JavaScript

#### JS应用场景：

1. 网页特效
2. 服务端开发(Node.js)
3. 命令行工具(Node.js)
4. 桌面程序(Electron)
5. App（Cordova）
6. 控制硬件--物联网
7. 游戏开发

#### JavaScript是什么：

* 是一种运行在客户端的脚本语言，最早在HTML网页上使用，用来给html网页增加动态功能。
* 浏览器就是一种运行JavaScript脚本的客户端，JavaScript的解释器被称为JavaScript引擎，。

#### JavaScript的组成：

+--------------------------------------------------------------+
|                     JavaScript                                       |
|                                                            		|
|                                                             		 |
|                                                              		|
|    +------------------+  +---------------+   +-------------+ |
|    |         	       |  |               |   |             | |
|    |                        |  |               |   |             | |
|    |    ECMAScript |  |    DOM        |   |    BOM      | |
|    |                 			 |  |               |   |             | |
|    |                  	|  |               |   |             | |
|    +------------------+  +---------------+   +-------------+ |
|                                                              |
|                                                              |
|                                                              |
+--------------------------------------------------------------+

DOM：文档对象模型

BOM：浏览器对象模型

### 操作系统

#### 软件：

应用软件：浏览器、QQ、Word

系统软件：Windows、Linux

#### 硬件：

三大件：CPU、内存(临时存储)、硬盘(永久存储)

输入设备：鼠标、键盘、手写板、摄像头等

输出设备：显示器、打印机、投影仪等



### 书写语法

#### 书写位置

1. 行内
2. script标签内
3. 写在外部js文件中并引入

注意：

引入外部js文件的script标签中不可以写JavaScript代码，需要书写在另一个新的script标签中。

prompt()语句

弹出一个对话框，内部有一个提示语句和输入框，可以在输入框中输入任意内容。

可以传递两个参数，用，分隔，一般为字符串类型。

#### 字面量

表示固定量

##### 整数字面量

八进制：

1. 以0、 0o、0O开头，每位最大不超过7.

十六进制：

1. 0X，0x开头
2. 0-9，a-f

有不符合规范的写法出现时，会强制忽略前面的0，将后面的数字当做十进制计算。

如：八进制中，出现如下写法：0129

##### 浮点数字面量

0<浮点数<1时，0可以省略不写。

科学计数法：

1.0e4  表示10000

浮点数精度问题：

浮点数值的最高精度是17位小数，但在算术计算时其精确度远远不如整数。

如：0.1+0.2结果为0.3000000000004

特殊数字字面量：

Infinity

意为无穷。它本身就是一个数字。最小值：Number.MIN_VALUE；最大值：Number.MAX_VALUE

NaN

表示不是一个正常的数，但还是一个Number类型的数。

NaN与任何值都不相等，包括它本身。

isNaN():判断一个数是不是NaN

##### 字符串字面量

转义字符  ----  \

\n 换行  \t  tab

也可将特殊字符转为普通字符：\ '      \ "   \ \

#### 变量

可以方便的获取或修改内存中的数据。

变量声明--

变量在使用前必须先定义，如果没有定义，会出现引用错误。

定义方法： var a;

变量的命名规则和规范

规则：

1. 由字母、数字、_、$组成，不能以数字开头。
2. 字母区分大小写。
3. 不能是关键字和保留字。

规范：

1. 变量名必须有意义
2. 驼峰命名

变量定义后，没有赋值，内部有一个默认存储的值叫undefined(未定义)

通过=赋值，一次定义，多次赋值。

一个var可以同时定义多个变量;逗号分隔，分号结尾。

```javascript
var a = 1,b = 3,c = 5;
```

#### 数据类型

* Number 数字类型

* String 字符串类型

* Boolean 

* undefined

* Null 

  null本身是一个数据

  从逻辑角度，null值表示一个空对象指针

  如果定义的变量准备在将来用于保存对象，最好将该变量初始化为null

检测数据类型(typeof())

```javascript
        // 检测字面量的数据类型
        //法1
        console.log(typeof(12));
        console.log(typeof(NaN));
        console.log(typeof(undefined));
		// 法2 做关键字使用
		console.log(typeof 67);
		
```

数据类型转换

转成字符串：

1.数据.toString()

2.String()；有的值没有toString()方法，可以使用String().如undefined和null

3.+拼接字符串方式，和""拼接，会先转成字符串，再返回该字符串值

```javascript
        // 转字符串
        console.log(true.toString());
        console.log(String(undefined));
        console.log(String(null));
        console.log(true + "");
        console.log(23 + "");
```

转成数值类型

Number()

```javascript
        // 转数字
        console.log(Number("123")) // 123
        console.log(Number(""))    // 0
        console.log(Number("    "))// 0
        console.log(Number("123sgf")) //NaN 
        console.log(Number(true)) // 1
        console.log(Number(false)) // 0
        console.log(Number(undefined)) // NaN
        console.log(Number(null)) // 0
```

parseInt()

字符串转整数的方法

作用：

1. 对浮点数进行取整操作
2. 将字符串转为整数数字，也包含取整功能

注意：字符串中，必须是纯数字字符串或者数字字符开头的字符串，才能转换为正常数字，且只取整数部分，如果不是数字打头的字符串，会转换成NaN。

```javascript
        // 字符串转数字
        console.log(parseInt(122.34)); // 122
        console.log(parseInt("122.35abc")); // 122
        console.log(parseInt("122.34")); // 122
		console.log(parseInt("a122.34")); // NaN
```

parseFloat()

字符串转浮点数

将字符串转为浮点数。

要求：满足浮点数字符必须再字符串开始，如果不在开始则返回值都是NaN。

Boolean()

将其他类型值转为boolean类型值

false:NaN、0、""  空字符串、null、undefined

true：非0 非NaN数字、非空字符串

```javascript
        // 转为boolean
        // false
        console.log(Boolean(""));
        console.log(Boolean(0));
        console.log(Boolean(null));
        console.log(Boolean(NaN));
        console.log(Boolean(undefined));
		// true
        console.log(Boolean(123));
        console.log(Boolean("  "));
        console.log(Boolean(Infinity));
```

#### 操作符(operator)

##### 算术运算符

+- * / %

正常情况：数字与数字进行运算

非正常情况1：有特殊字面量参与运算

1. 有NaN参与时，结果为NaN
2. 有Infinity参与时，结果视情况而定

```javascript
        // NaN参与的运算，结果都是NaN
        console.log(NaN + 5);
        console.log(NaN - 5);
        console.log(NaN * 5);
        console.log(NaN / 5);
        console.log(NaN % 5);
        // Infinity参与的运算 视情况而定
        console.log(Infinity + 5);
        console.log(Infinity - 5);
        console.log(Infinity * 5);
        console.log(Infinity / 5);
        console.log(Infinity % 5); // NaN 
        console.log(1 + Infinity);
        console.log(1 - Infinity); // -Infinity
        console.log(1 * Infinity);
        console.log(1 / Infinity); // 0
        console.log(1 % Infinity); // 1
        console.log(-Infinity + 5);
        console.log(-Infinity - 5);
        console.log(-Infinity * 5);
        console.log(-Infinity / 5);
        console.log(-Infinity % 5);  // NaN 
```

非正常情况2：

其他类型的数据参与数学运算。

1. 有字符串参与的+运算：转为字符串拼接
2. 隐式转换：参与运算的其他数据类型会隐式转换为数字类型。结果与用Number()转出的相同

##### 比较运算符

>  <  >  <=  >=  ==  !=  ===  !==
>
> 比较后返回一个boolean值
>
> ==： 只判断值是否相等
>
> ===：判断值和数据类型是否相等

非正常情况1：NaN参与，除!=和!==之外，其他返回值均为false

​			Infinity参与，结果如下：

非正常情况2：有其他数据类型参与，其他数据类型也会隐式转换为数字类型进行比较。

* null的判断较特殊。null与0比较时，值为false，>=和<=判断为true
* null==undefined

非正常情况3：字符串与字符串的比较

* 不会发生隐式转换为数字，而是比较两个字符串的Unicode编码顺序。
* 字符编码顺序：从前往后0-9，A-Z，a-z，前面的小于后面的
* 比较时，从第一个字符开始比较，依次往后顺延比较，直到比较出大小，就不再往后比较。
* 比较顺序：从前往后比较，前面的结果与后面进行比较。如：3>2>1 // false

##### 逻辑运算符

常用于布尔类型值之间，当操作数都是boolean值时，返回值也是boolean值。

&&   ||    ！

&&：都真才真，有假则假

|| ： 有真就真，都假才假

！：非真即假，非假即真  运算结果只能是true或false

非正常情况：有其他数据类型参与逻辑运算，其他数据类型也会隐式转换为布尔类型参与判断。最终结果为原来的某个位置的数据。

​		      并不是所有逻辑运算返回结果都是布尔值，其他数据参与得到的就是数据本身。

运算顺序：非与或

##### 赋值运算符

必须有变量参与运算

赋值运算符参与两件事情：

1. 将变量中原始值参与对应数学运算，
2. 将运算结果重新赋值给变量

= +=  -=  *=  /=  %=  ++  --

##### 一元运算符

只有一个操作数的运算符。++  --  ！

a++： 先使用，后自加

++a:先加后用

##### 运算优先级

优先级从高到低排列为：

1. ()
2. 一元运算符 ++  --  !
3. 算术运算符 先*  /  %  后+  -
4. 关系运算符  >  >=   <  <=
5. == ！=  ===  !==
6. 逻辑运算符  先&&  后||
7. 赋值运算符

#### 表达式

一个表达式可以产生一个值，有可能是运算、函数调用、字面量。表达式可以放在任何需要值的地方。

特点：先执行出一个结果，再参与运算。

#### 语句

行为。如循环、判断。给计算机一个指令，执行这段代码。

#### 流程控制语句

通过一些特殊的结构，可以让js加载时，跳过一部分不加载或循环加载一段代码。

包括条件分支语句、循环语句。

##### 条件分支语句

###### if语句

通过指定的判断条件，决定执行哪个分支的代码。
```js{cmd=node}
var s = parseFloat(prompt("请输入成绩","80"));
if (s >= 60) {
        alert('您已合格');
} else {
        alert('不及格');
}
```

if语句可以不写else：条件成立就执行后面的结构体，条件不成立，直接跳出if语句不执行。

if语句中结构体为单行时，可以省略{ } 

if只能控制自己内部的流程，结束后都要执行if语句后面的其他语句。



**多分支if语句**

包含多个判断条件，对应多个分支。

注意事项：

1. else分支只能有一个，必须出现在最后。也可以不写，表示直接跳出，不走任何分支。
2. 跳楼现象：从上往下依次验证，如果满足某个条件，会立即执行后面的结构体，然后跳到后面的程序。

**if嵌套**

if语句的结构体可以是任意代码，甚至是另外一组if语句。

###### 三元表达式

必须有三个操作数参与的运算。

**操作符号**： **？ ：**

**表达式**：在参与js程序时，都必须先计算出表达式结果，才能参与后续程序。

由于三元表达式具备了一些选择的效果，所以也是一种条件分支语句。

**语法**：

boolean_expression?true_value:false_value;
```js{cmd=node}
console.log(true?true:false);// true
```

**优点**

1. 二选一情况下，结构更加简单。
2. 三元表达式作为一个表达式参与程序时必须运算出结果才能参与，可以利用这个特点，将二选一结果赋值给一个变量。
```js{cmd=node}
// 给变量赋值，根据条件二选一
var a = 3;
var b = a >= 5 ? 1 : 0;
console.log(b);
```

###### switch语句

开关语句

表达式计算得出的值与case后面的值进行**全等**匹配，不止值要相等，数据类型也要相等。

break：用于打断结构体，直接跳出程序，模拟跳楼现象。

default：前面的情况都不匹配时，执行default。

注意事项：

1. default可以不写
2. break：根据结构需要必须再每个case后面写break，为了模拟跳楼现象，如果不写break，对应的case后面的语句执行之后，不会跳出结构体，会继续执行其他case后面的语句，直到遇到一个break。
3. 可以利用break不写的情况制作一些特殊的案例。

eg.输入月份，输出对应的天数。
```js{cmd=node}
var month  = parseInt(prompt("请输入月份"));
switch (month) {
        case 1:
        case 3:
        case 5:
        case 7:
        case 8:
        case 10:
        case 12:
                alert("31天");
                break;
        case 2:
                alert("28天或29天");
                break;
        default:
                alert("30天");
                break;
}

```

##### 循环语句

###### for循环