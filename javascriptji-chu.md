# Javascript类型

* Number
* Boolean
* String
* Object
  Function
  Aarry
  Date
  RegExp
* Symbol\(es5 新增\)
* null\(空\)
* undefined\(未定义\)
* Error


# 数字（Number）
> JavaScript 采用“遵循 IEEE 754 标准的双精度 64 位格式”（"double-precision 64-bit format IEEE 754 values"）表示数字。据此我们能得到一个有趣的结论，和其他编程语言（如 C 和 Java）不同，JavaScript 不区分整数值和浮点数值，所有数字在 JavaScript 中均用浮点数值表示



```
0.1 + 0.2 = 0.30000000000000004
```



>  parseInt() 和 parseFloat() 函数会尝试逐个解析字符串中的字符，直到遇上一个无法被解析成数字的字符，然后返回该字符前所有数字字符组成的数字。然而如果使用运算符 "+"， 只要字符串中含有无法被解析成数字的字符，该字符串都将被转换成 NaN。可分别使用这两种方法解析“10.2abc”这一字符串，并比较得到的结果，来理解这两种方法的区别。




```
parseInt("123", 10); // 123
parseInt("010", 10); // 10
parseInt("11", 2); // 3

parseInt("hello", 10); // NaN
isNaN(NaN); // true
```



> JavaScript 还有一个类似的内置函数 parseFloat()，用以解析浮点数字符串，与parseInt()不同的地方是，parseFloat() 只应用于解析十进制数字



```
+ "42";   // 42
+ "010";  // 10
+ "0x10"; // 16
```



> JavaScript 还有两个特殊值：Infinity（正无穷）和 -Infinity（负无穷）：



```
1 / 0; //  Infinity
-1 / 0; // -Infinity

isFinite(1/0); // false
isFinite(Infinity); // false
isFinite(-Infinity); // false
isFinite(NaN); // false

isFinite(0); // true
isFinite(2e64); // true

isFinite("0"); // true
// 如果是纯数值类型的检测，则返回 false：
Number.isFinite("0"); // false

```
# Boolean

* false、0、空字符串（""）、NaN、null 和 undefined 被转换为 false
* 所有其他值被转换为 true

# 变量 let const var

> JavaScript 与其他语言的（如 Java）的重要区别是在 JavaScript 中语句块（blocks）是没有作用域的，只有函数有作用域。因此如果在一个复合语句中（如 if 控制结构中）使用 var 声明一个变量，那么它的作用域是整个函数（复合语句在函数中）。 但是从 ECMAScript Edition 6 开始将有所不同的， let 和 const 关键字允许你创建块作用域的变量。

# 控制结构
```
for (var i = 0; i < 5; i++) {
  // 将会执行五次
}

for (let value of array) {
  // do something with value 数组循环
}

for (let property in object) {
  // do something with object property 对象循环
}
```





