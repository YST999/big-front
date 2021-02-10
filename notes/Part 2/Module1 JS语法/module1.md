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

数据类型

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

