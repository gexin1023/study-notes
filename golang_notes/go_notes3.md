## golang笔记_基本数据类型

在golang中，数据类型有四种：

+ 基础类型：数值类、字符串、布尔变量
+ 组合类型：数组、结构体
+ 引用类型：指针、slice、map、function、channel
+ 接口类型：第七章会讨论

### 3.1 整数类型

Golang的数值类型中包括以下几类：整数、浮点数、复数。

Golang支持有符号和无符号整形变量，如下所示

```go
// signed integers
int8, int16, int32, int64, int

// unsigned integers
uint8, uint16, uint32, uint64, uint
```

有两个类型没有指明占用的位数，`int`和`uint`，它们可能是32位也可能是64位，这取决于编译器实现。

`rune`类型是`int32`的同义词，暗示值是一个Unicode编码的，这两个类型可以互换使用。

`byte`是`uint8`的同义词，暗示这是原始数据，而非数值。

`uintptr`类型的宽度没有指定，但是足够容纳指针值得所有位。该数据类型只有在低级别编程上会用到，比如C库或者系统层编程时。

有符号类型中的负数采用二进制补码类型，即按位取反再加1，如下所示：

```go
x int8 = 3  // 按位表示为：0b0000 0011
y int8 = -3 // 先将3按位取反，为0b1111 1100，然后加1得到0b1111 1101，这就是-3
```

Golang的二元操作符按照优先级降序排列如下：

```go
*   /   %   <<  >>  &   &^
+   -   |   ^
== !=   <   <=  >   >=
&&
||
```
涉及到优先级问题的，最好用括号，这样可读性更好。

在Golang中的`%`操作，得到的余数时钟与被除数的符号保持一致，如下所示：
```go
-5 % 3      // -2
-5 % -3     // -2
5%(-3)      // 2
5%(3)       // 2
```

不管是有符号还是无符号的运算，如果运算结果超出了变量的位数（溢出），高位超出的会被舍弃。

