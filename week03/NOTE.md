

## 运算符与表达式

#### 语法树与优先级

同BNF

1. +-

2. */

3. ()

   优先计算的在底下 之后计算的在上面

   #### Member 运算

   典型:

   a.b   点运算

   ##### 成员访问

    a.b a[b]  其中 a[b] 支持字符串形式

   ##### 反引号

   模板字符串: `字符串${fn()}`   (`不显示)

   ##### super关键字  

   属于member 运算

   class 继承里使用

   super关键字用于访问和调用一个对象的父对象上的函数。

   `super.prop`和`super[expr]`表达式在[类](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)和[对象字面量](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Object_initializer)任何[方法定义](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Method_definitions)中都是有效的。

   super.b     super['b']

   举例:

   class A {

   ​      dd = 1;

   ​      get a() {

   ​        return "a";

   ​      }

   ​      aa() {

   ​        return "aa";

   ​      }

   ​    }

   

   ​    class B extends A {

   ​      haha() {

   ​        console.log(super.aa);

   ​        console.log(super.a);

   ​        console.log(super.dd);

   ​        return super.a;

   ​      }

   ​    }

   ​    const b = new B();

   ​    console.log(b.haha());

   输出的结果:

   function  aa()  {}  // aa函数没有调用 如果调用 则是 super.aa()

   a  //之所以输出a 是因为 get 函数执行了a函数

   undefined //dd  未传参 也不是方法

   a 

   补充: 

   get语法将对象属性绑定到查询该属性时将被调用的函数。

   const obj = {
     log: ['a', 'b', 'c'],
     get latest() {
       if (this.log.length === 0) {
         return undefined;
       }
       return this.log[this.log.length - 1];
     }
   };

   console.log(obj.latest);
   // expected output: "c"

   ```javascript
   {get prop() { ... } }
    prop 要绑定到给定函数的属性名。
   ```

   ##### new.target

   在构造器中，`new.target` 指向[`new`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/new)调用的构造器。

   ##### new Foo()

   注:以上 优先级均相同

   #### new Foo

   比上面的优先级低

   ....................................................................

   ## reference

   通过a.b访问的属性  显示出来的是一个引用类型 不是属性的值 而是一个引用 即reference

   引用类型 ---标准中的类型 非语言中的 7种类型

   reference 分为两个部分

   object

   key: string /symbol

   ## 类型转换

   ==    不推荐  ===   推荐

   ![image-20200719121859707](C:\Users\samsu\AppData\Roaming\Typora\typora-user-images\image-20200719121859707.png)

#### 拆箱转换

+/number:  value Of()

属性名/string: toString()

#### 装箱转换

number  string  boolean  可通过new 转为复杂类型 

symbol 特殊:  new Object(Symbol("a"))        Symbol("a")  

## 语句

#### 简单语句

表达式语句------控制计算

空语句 ;

调试语句   ----debugger语句   debugger关键字+分号   断点

抛出异常语句  ----ThrowStatement

continue/break语句------循环

return语句-----函数内

流程控制 : throw continue break return

#### 复合语句

块语句

块语句（或其他语言的复合语句）用于组合零个或多个语句。该块由一对大括号界定 

{ StatementList }    ----完成语句树状结构的基础设施

条件语句----if

多分支语句------switch   不推荐

循环语句 

while /do while /for ;/for in /for of  /for await( of) -异步

withstatement----不推荐

with 语句用于设置代码在特定对象中的作用域

```JavaScript
var sMessage = "hello";
with(sMessage) {
  alert(toUpperCase());	//输出 "HELLO"
}
```

label语句 ?

标记语句可以和 [`break`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/break) 或 [`continue`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/continue) 语句一起使用。标记就是在一条语句前面加个可以引用的标识符（identifier）

trystatement   ?

包含三个结构  :try catch finally 

不同于块语句  {}不可省   如果里面有return 其后的语句还是会执行

#### 声明

注:此分类与js标准不一致

函数声明

generator声明 ---------- function*   xxx(){....}

异步函数声明----------async function

异步产生器声明----------async function*   xxx(){....}

变量声明

以上 几种声明   作用范围: 函数体

--------------------------------------------------------------------------------------------------------------------------

推荐:

class声明

const/let声明---------lexicaldeclaration

##### 预处理机制

##### 作用域

## 运行时

#### completion record

语句完成状态的一种记录

type: normal continue break return throw

value:  break return throw 发生时 会产生值

target: label (在语句前加上标识符或者冒号)   continue break

## 结构化程序设计

#### 宏任务与微任务

#### 事件循环

#### 函数调用

 1 2 6  7  



