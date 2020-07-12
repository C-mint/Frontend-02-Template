## 泛用语言分类

#### 语法

- 非形式语言
  中文, 英文 ,法文 ,德文

- 形式语言

  编程语言

  ## 形式语言分类

  ### 乔姆斯基谱系  (语言的复杂程度)

  • 0型 无限制文法

   ?::=?     左右都无限制

  • 1型 上下文相关文法    

   ?<A>?::=?<B>?      只有AB可不同 一一对应        
  • 2型 上下文无关文法

  <A>::=?      右侧无限制

  • 3型 正则/正规文法(regular)

  <A>::=<A>?        (注 <A>::=?<A> ×)

上包含下 即 3属于2 属于1 属于0  反之不成立

Javascript 属于上下文无关文法  表达式多为正则文法

##### 特殊

{                                            
get a { return 1 },
get : 1
}  

上下文相关   get a  可看做关键字     get 属性

2 ** 1 ** 2       

不属于正则文法   右相关    等于2   =先1^2=1,   再2^1=2

if语句 也不属于正则文法

## 产生式

#### 一巴科斯范式     BNF

BNF是John Backus 在20世纪90年代提出的用以简洁描述一种编程语言的语言。

基本结构为：

<non-terminal> ::= <replacement>

non-terminal意为非终止符，就是说我们还没有定义完的东西，还可以继续由右边的replacement，也就是代替物来进一步解释、定义。

• 用尖括号括起来的名称来表示语法结构名
• 语法结构分成基础结构和需要用其他语法结构定义的复合结构
• 基础结构称终结符
• 复合结构称非终结符
• 引号和中间的字符表示终结符
• 可以有括号

•::=表示定义

• * 表示重复多次
• | 表示或
• + 表示至少一次

##### 举例

自定义公式表示四则运算的规则(无括号)

<MultiplicativeExpression>::=<Number>|
<MultiplicativeExpression>"*"<Number>|
<MultiplicativeExpression>"/"<Number>
<AddtiveExpression>::=< MultiplicativeExpression>|
<AddtiveExpression>"+"<MultiplicativeExpression>|
<AddtiveExpression>"-"<·MultiplicativeExpression>

 1 + 2 * 3

分析:

1+x= <ae>+<me>

​      =<me>+<number>

​     =  <number>+<number>

2*3=<me>·<number>

​      =  <number>·<number>

 终结符: number   + - * /

 非终结符:    MultiplicativeExpression      AddtiveExpression

按照优先级定义 加法表达式内包含乘法表达式  2*3 即子结构

2/4+1

分析:

const expression = {

  type: 'expression',

  children: [{

​    type: 'additiveExpression',

​    children: [{

​      type: 'multiplicativeExpression',

​      children: [{

​        type: 'multiplicativeExpression',

​        children: [{

​          type: 'number',

​          value: 2

​        }]

​      }, {

​        type: '*' //'/'

​      }, {

​        type: 'number',

​        value: 4

​      }]

​    }]

  }, {

​    type: '+',

  }, {

​    type: 'multiplicativeExpression',

​    children: [{

​      type: 'number',

​      value: 1

​    }]

  }]

}

#### 二 EBNF 

#### 三 ABNF

形式语言分类 除了按照语言的复杂程度可基于乔姆斯基谱系分为四种类型还可按其他方式

### 用途

####  数据描述语言

JSON, HTML, XAML, SQL, CSS

####  编程语言

C, C++, Java, C#, Python, Ruby,Perl, JavaScript
Lisp, T-SQL, Clojure, Haskell,  (偏声明式的函数语言)

### 表达方式

#### 声明式语言

JSON, HTML, XAML, SQL, CSS,  Lisp, Clojure, Haskell

####  命令型语言

C, C++, Java, C#, Python, Ruby,  Perl, JavaScript

## 编程语言的性质

- 图灵完备性
- 动态与静态
- 类型系统

#### 图灵完备性

一切可计算的问题都能计算，这样的虚拟机或者编程语言就是图灵完备的。

随着时间流逝 逐渐形成固定模式(两种)------两大计算机流派

• 命令式——图灵机
 goto
 if和while
• 声明式——lambda(函数)
 递归

Lambda 表达式(lambda expression)是一个[匿名函数](https://baike.so.com/doc/6895820-7113458.html)，Lambda表达式基于数学中的[λ演算](https://baike.so.com/doc/352743-373614.html)得名，直接对应于其中的lambda抽象(lambda abstraction)，是一个匿名函数，即没有函数名的函数。Lambda表达式可以表示[闭包](https://baike.so.com/doc/5623134-5835752.html)(注意和数学传统意义上的不同)。

#### 动态与静态

• 动态：
在用户的设备/在线服务器上
 产品实际运行时
 Runtime   (运行时)
• 静态：
 在程序员的设备上               如:静态类型检查
 产品开发时
•Compiletime  (编译时)

#### 类型系统

##### 动态类型系统与静态类型系统

动态类型系统  JS与静态类型系统 C++  (同动态与静态) 

注:Java 由于反射机制  ---半动态半静态

#####  强类型与弱类型

在编程语言里类型转换发生的形式 强类型语言类型转换不会默认发生 因此JS 为弱类型语言

string+number => string

string==boolean  比较运算 : Boolean=>number  再 string与number 比较大小

##### 复合类型

类型有时可为复合型

 结构体
函数签名   :参数类型+返回值类型

##### 子类型

C++

所有基于类的面向对象的语言会把类的结构关系变成类型的结构关系  类与类型二者不同

##### 泛型

泛型类 

泛型函数

泛型+子类型=> 逆变/协变

协变:

凡是能用Array<Parent>的地方，
都能用Array<Child>

逆变:

凡是能用Function<Child>的地方，
都能用Function<Parent>

## 一般命令式编程语言的设计方式

### 原子级

一个语言的最小组成单位 

包含 关键字 直接量 变量名

### 表达式

原子级等结构通过运算符,符号相连接 构成级联结构

### 语句

表达式+标识符+关键字+符号  形成特定的结构

条件语句 循环语句

### 结构化

组织代码  将其分块 分成不同的复用结构

function  class

process 过程 (PASCAL -古老语言)

namespace(C++)



组织代码 管理语言的模块与安装   在语言/辅助设施里

Program
Module
Package (Java)
Library

JS---npm   两个顶级定义  Program--实际执行的代码  Module --准备好被复用的模块



语法      语义 =>     运行时

## Number

双精度浮点数表示法:



0.1+0.2!=0.3 

三次转换+一次的精度损失  (max:3e)

### 语法:--2018标准

十进制/二进制/八进制/十六进制

##### 十进制

允许小数  小数点左右两边任意一边有数字即可  0.   .2    都是有效数字

支持科学计数法  1e3=1000   3为指数

0 .toString()   0后要加空格    因为 0. =0   

##### 二进制

只支持整数  0bxxx    其后只写0/1  无空格

##### 八进制

0oxxx    其后  0-7

##### 十六进制

0x开头  其后 0-9  A-F

## String

### Code Point 表示字符Character

• ASCII    127个字符
• Unicode   合集
• UCS   0000-FFFF
• GB
 GB2312   与Unicode 编码不一致  
 GBK(GB13000)
GB18030   最全
• ISO-8859
• BIG5   台湾

但所有的字符集都会兼容 ASCII 

##### 码点

汉字`严`的 Unicode 是十六进制数`4E25`，转换成二进制数足足有15位（`100111000100101`）

`100111000100101`即码点

##### UTF-8

UTF-8 的编码规则很简单，只有二条：

1）对于单字节的符号，字节的第一位设为`0`，后面7位为这个符号的 Unicode 码。因此对于英语字母，UTF-8 编码和 ASCII 码是相同的。

2）对于`n`字节的符号（`n > 1`），第一个字节的前`n`位都设为`1`，第`n + 1`位设为`0`，后面字节的前两位一律设为`10`。剩下的没有提及的二进制位，全部为这个符号的 Unicode 码。

按照表格 严 Unicode:4E25  即在第三行 0000 0800-0000 FFFF   按照字母顺序比大小

`严`的 Unicode 是`4E25`（`100111000100101`），根据表，可以发现`4E25`处在第三行的范围内（`0000 0800 - 0000 FFFF`），因此`严`的 UTF-8 编码需要三个字节，即格式是`1110xxxx 10xxxxxx 10xxxxxx`。然后，从`严`的最后一个二进制位开始，依次从后向前填入格式中的`x`，多出的位补`0`。这样就得到了，`严`的 UTF-8 编码是`11100100 10111000 10100101`，转换成十六进制就是`E4B8A5`。

1110xxxx  要补4位 不够 前面+0 补位

```
Unicode符号范围     |        UTF-8编码方式
(十六进制)        |              （二进制）
----------------------+---------------------------------------------
0000 0000-0000 007F | 0xxxxxxx
0000 0080-0000 07FF | 110xxxxx 10xxxxxx
0000 0800-0000 FFFF | 1110xxxx 10xxxxxx 10xxxxxx
0001 0000-0010 FFFF | 11110xxx 10xxxxxx 10xxxxxx 10xxxxxx
```

​     ### 语法



双引号字符  "abc"

单引号字符  'abc'

反引号字符  ``

\n 回车 \t  Tab键   两个\  反斜杠 \r 回到行首  \u 转义 \x 转义

正则匹配字符串表示:

"(?:[^"\n\\\r\u2028\u2029]|\\(?:['"\\bfnrtv\n\r\u2028\u2029]|\r\n)|\\x[0-9a-fA-F]{2}|\\u[0-9a-
fA-F]{4}|\\[^0-9ux'"\\bfnrtv\n\\\r\u2028\u2029])*"
'(?:[^'\n\\\r\u2028\u2029]|\\(?:['"\\bfnrtv\n\r\u2028\u2029]|\r\n)|\\x[0-9a-fA-F]{2}|\\u[0-9a-
fA-F]{4}|\\[^0-9ux'"\\bfnrtv\n\\\r\u2028\u2029])*'



| Unicode 字符值 | 转义序列 | 含义           | 类别     |
| -------------- | -------- | -------------- | -------- |
| \u0008         | \b       | Backspace      |          |
| \u0009         | \t       | Tab            | 空白     |
| \u000A         | \n       | 换行符（换行） | 行结束符 |
| \u000B         | \v       | 垂直制表符     | 空白     |
| \u000C         | \f       | 换页           | 空白     |
| \u000D         | \r       | 回车           | 行结束符 |
| \u0022         | \"       | 双引号 (")     |          |
| \u0027         | \'       | 单引号 (')     |          |
| \u005C         | \\       | 反斜杠 (\)     |          |
| \u00A0         |          | 不间断空格     | 空白     |
| \u2028         |          | 行分隔符       | 行结束符 |
| \u2029         |          | 段落分隔符     | 行结束符 |
| \uFEFF         |          | 字节顺序标记   | 空白     |

| Unicode 字符值 | 转义序列 | 含义           | 类别     |
| -------------- | -------- | -------------- | -------- |
| \u0008         | \b       | Backspace      |          |
| \u0009         | \t       | Tab            | 空白     |
| \u000A         | \n       | 换行符（换行） | 行结束符 |
| \u000B         | \v       | 垂直制表符     | 空白     |
| \u000C         | \f       | 换页           | 空白     |
| \u000D         | \r       | 回车           | 行结束符 |
| \u0022         | \"       | 双引号 (")     |          |
| \u0027         | \'       | 单引号 (')     |          |
| \u005C         | \\       | 反斜杠 (\)     |          |
| \u00A0         |          | 不间断空格     | 空白     |
| \u2028         |          | 行分隔符       | 行结束符 |
| \u2029         |          | 段落分隔符     | 行结束符 |
| \uFEFF         |          | 字节顺序标记   | 空白     |

| Unicode 字符值 | 转义序列 | 含义           | 类别     |
| -------------- | -------- | -------------- | -------- |
| \u0008         | \b       | Backspace      |          |
| \u0009         | \t       | Tab            | 空白     |
| \u000A         | \n       | 换行符（换行） | 行结束符 |
| \u000B         | \v       | 垂直制表符     | 空白     |
| \u000C         | \f       | 换页           | 空白     |
| \u000D         | \r       | 回车           | 行结束符 |
| \u0022         | \"       | 双引号 (")     |          |
| \u0027         | \'       | 单引号 (')     |          |
| \u005C         | \\       | 反斜杠 (\)     |          |
| \u00A0         |          | 不间断空格     | 空白     |
| \u2028         |          | 行分隔符       | 行结束符 |
| \u2029         |          | 段落分隔符     | 行结束符 |
| \uFEFF         |          | 字节顺序标记   | 空白     |

##### 反引号

`ab${x}abc${y}abc`

解析成=>

• `ab${
• }abc${
• }abc`

注:有反引号    格式冲突 显示出错

## boolean

true

false

## Null&Undefined

null  关键字  表示定义了 值为空

undefined  全局变量  表示未定义  最好不要赋值 用 void 0;代替

## 对象Object

任何一个对象都是唯一的，这与它本身的状态无关。
所以，即使状态完全一致的两个对象，也并不相等。
我们用状态来描述对象。
状态的改变即是行为。

对象描述: 唯一性的标识 状态 行为(改变对象状态的行为)

#### 类与原型

##### 类

类是一种常见的描述对象的方式。
”归类”和”分类”是两个主要的流派。
对于”归类”方法而言，多继承是非常自然的事情。如C++  --- 一种事物可分属不同类别

而采用分类思想的计算机语言，则是单继承结构。并且会有一个基类Object。--- 从一个大类往下细分

##### 原型

原型是一种更接近人类原始认知的描述对象的方法。
我们并不试图做严谨的分类，而是采用“相似”这样的方式去描述对象。
任何对象仅仅需要描述它自己与原型的区别即可。

如 :先认识了猫 在认识狗 认识狗这一事物是在对猫的认知基础上做出了改变和删加...

Fish Prototype=>Animal Prototype=>Object Prototype=>Nihilo (Null)

注:  我们不应该受到语言描述的干扰。
在设计对象的状态和行为时，我们总是遵循  “行为改变状态”的原则。

##### Object in JavaScript

###### 属性

描述状态 描述行为   (唯一标识:js 内存地址--内存地址的唯一性表示js对象的唯一性)

键值对表示(k v)

 K: 

- symbol (一旦创建 则需要变量来引用)  ---属性访问的权限控制
-  string(可取值 可访问)

V:

- 数据属性: 存值 类型(七种) 

  attribute: value writable enumerable configurable  即属性的特征值

  注: if  configurable  值为false 则 value writable enumerable configurable  都不可更改 

  writable : writable false时 点运算不可更改  但可通过 define property 更改(强行更改)

  描述状态 -- 数据属性中如果存储函数，也可以用于描述行为。

- 访问器属性

  get/set函数--读/写调用

  enumerable configurable

  描述行为

  ###### 原型

  原型链查找机制:当查找某对象的属性时,如果自身没有 ,则会往上一级原型对象查找...直到null

  ## Object API

   {} . [] Object.defineProperty

基本的对象机制 通过语法去创建对象 访问属性 定义新属性 改变属性的特征值(基本的面向对象能力)

 Object.create / Object.setPrototypeOf /Object.getPrototypeOf

创建/修改/获取  基于原型对象的API

基于原型的描述对象的方法  通过Object.create 可在指定原型的前提下创建对象

new / class / extends

基于分类的方式去描述对象

new / function / prototype (function.prototype)

ES3 不建议使用

## Function Object

Object
[[call]]

前面讲述了JavaScript中的一般对象。
但JavaScript中还有一些特殊的对象，比如函数对象。
除了一般对象的属性和原型，函数对象还有一个行为[[call]]。
我们用JavaScript中的function 关键字、箭头运算符或者Function构造器创建的对象，会有[[call]]这个
行为。

我们用类似 f() 这样的语法把对象当做函数调用时，会访问到[[call]]这个行为。
如果对应的对象没有[[call]]行为，则会报错。

Array
[[length]]

数组对象的长度会随着增加后的数字型的属性而变化

Object.prototype
[[setPrototypeOf]]

function.prototype所有对象的原型无setPrototypeOf 方法

## Host Object

宿主环境所定义的对象

如: 在浏览器 可直接访问 window setTimeOut   实现js语言不支持但语法支持的特性

Object
[[call]]
[[construct]]

也可通过call construct方法来实现函数的调用 和new运算