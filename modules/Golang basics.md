<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Contents**

- [入门](#%E5%85%A5%E9%97%A8)
  - [导出名](#%E5%AF%BC%E5%87%BA%E5%90%8D)
  - [函数](#%E5%87%BD%E6%95%B0)
  - [变量](#%E5%8F%98%E9%87%8F)
  - [基本类型](#%E5%9F%BA%E6%9C%AC%E7%B1%BB%E5%9E%8B)
  - [类型转换](#%E7%B1%BB%E5%9E%8B%E8%BD%AC%E6%8D%A2)
  - [类型推导](#%E7%B1%BB%E5%9E%8B%E6%8E%A8%E5%AF%BC)
  - [常量](#%E5%B8%B8%E9%87%8F)
  - [数值常量](#%E6%95%B0%E5%80%BC%E5%B8%B8%E9%87%8F)
  - [for](#for)
  - [if 的简短语句](#if-%E7%9A%84%E7%AE%80%E7%9F%AD%E8%AF%AD%E5%8F%A5)
  - [switch](#switch)
  - [defer 栈](#defer-%E6%A0%88)
  - [指针](#%E6%8C%87%E9%92%88)
  - [结构体字段](#%E7%BB%93%E6%9E%84%E4%BD%93%E5%AD%97%E6%AE%B5)
  - [结构体指针](#%E7%BB%93%E6%9E%84%E4%BD%93%E6%8C%87%E9%92%88)
  - [结构体文法](#%E7%BB%93%E6%9E%84%E4%BD%93%E6%96%87%E6%B3%95)
  - [数组](#%E6%95%B0%E7%BB%84)
  - [切片](#%E5%88%87%E7%89%87)
    - [切片的默认行为](#%E5%88%87%E7%89%87%E7%9A%84%E9%BB%98%E8%AE%A4%E8%A1%8C%E4%B8%BA)
    - [切片的长度与容量](#%E5%88%87%E7%89%87%E7%9A%84%E9%95%BF%E5%BA%A6%E4%B8%8E%E5%AE%B9%E9%87%8F)
    - [用 make 创建切片](#%E7%94%A8-make-%E5%88%9B%E5%BB%BA%E5%88%87%E7%89%87)
    - [append函数](#append%E5%87%BD%E6%95%B0)
  - [Range](#range)
  - [方法](#%E6%96%B9%E6%B3%95)
  - [方法与指针重定向](#%E6%96%B9%E6%B3%95%E4%B8%8E%E6%8C%87%E9%92%88%E9%87%8D%E5%AE%9A%E5%90%91)
  - [选择值或指针作为接收者](#%E9%80%89%E6%8B%A9%E5%80%BC%E6%88%96%E6%8C%87%E9%92%88%E4%BD%9C%E4%B8%BA%E6%8E%A5%E6%94%B6%E8%80%85)
  - [接口与隐式实现](#%E6%8E%A5%E5%8F%A3%E4%B8%8E%E9%9A%90%E5%BC%8F%E5%AE%9E%E7%8E%B0)
  - [错误](#%E9%94%99%E8%AF%AF)
  - [Reader](#reader)
  - [goroutine](#goroutine)
  - [信道](#%E4%BF%A1%E9%81%93)
  - [range 和 close](#range-%E5%92%8C-close)
  - [select 语句](#select-%E8%AF%AD%E5%8F%A5)
  - [默认选择](#%E9%BB%98%E8%AE%A4%E9%80%89%E6%8B%A9)
  - [sync.Mutex](#syncmutex)
  - [references](#references)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# 入门

## 导出名

在 Go 中，如果一个名字以大写字母开头，那么它就是已导出的。例如，`Pizza` 就是个已导出名，`Pi` 也同样，它导出自 `math` 包。

`pizza` 和 `pi` 并未以大写字母开头，所以它们是未导出的。

在导入一个包时，你只能引用其中已导出的名字。任何“未导出”的名字在该包外均无法访问。

```go
package main

import (
	"fmt"
	"math"
)

func main() {
	fmt.Println(math.Pi)
}

```

vs

```go
package main

import (
	"fmt"
	_"math"
)

func main() {
	fmt.Println(11)
}

```

## 函数

函数可以没有参数或接受多个参数。

在本例中，`add` 接受两个 `int` 类型的参数。

注意类型在变量名 **之后**。

```go
package main

import "fmt"

func add(x int, y int) int {
	return x + y
}

func main() {
	fmt.Println(add(42, 13))
}
```

## 变量

`var` 语句用于声明一个变量列表，跟函数的参数列表一样，类型在最后。

就像在这个例子中看到的一样，`var` 语句可以出现在包或函数级别

```go
package main

import "fmt"

var c, python, java bool

func main() {
	var i int
	fmt.Println(i, c, python, java)
}
```

> ## 短变量声明
>
> 在函数中，简洁赋值语句 `:=` 可在类型明确的地方代替 `var` 声明。
>
> 函数外的每个语句都必须以关键字开始（`var`, `func` 等等），因此 `:=` 结构不能在函数外使用。

```go
package main

import "fmt"

func main() {
	var i, j int = 1, 2
	k := 3
	c, python, java := true, false, "no!"

	fmt.Println(i, j, k, c, python, java)
}

```

## 基本类型

Go 的基本类型有

```
bool

string

int  int8  int16  int32  int64
uint uint8 uint16 uint32 uint64 uintptr

byte // uint8 的别名

rune // int32 的别名
    // 表示一个 Unicode 码点

float32 float64

complex64 complex128
```

本例展示了几种类型的变量。 同导入语句一样，变量声明也可以“分组”成一个语法块。

`int`, `uint` 和 `uintptr` 在 32 位系统上通常为 32 位宽，在 64 位系统上则为 64 位宽。 当你需要一个整数值时应使用 `int` 类型，除非你有特殊的理由使用固定大小或无符号的整数类型。

```go
package main

import (
	"fmt"
	"math/cmplx"
)

var (
	ToBe   bool       = false
	MaxInt uint64     = 1<<64 - 1
	z      complex128 = cmplx.Sqrt(-5 + 12i)
)

func main() {
	fmt.Printf("Type: %T Value: %v\n", ToBe, ToBe)
	fmt.Printf("Type: %T Value: %v\n", MaxInt, MaxInt)
	fmt.Printf("Type: %T Value: %v\n", z, z)
}

```

> 字符串格式化: 
>
> ```go
> // 定义示例类型和变量
> type Human struct {
>     Name string
> }
> 
> var people = Human{Name:"zhangsan"}
> ```
>
> ```
> *普通占位符*
> 占位符     说明                           举例                   输出
> %v      相应值的默认格式。            Printf("%v", people)   {zhangsan}，
> %+v     打印结构体时，会添加字段名     Printf("%+v", people)  {Name:zhangsan}
> %#v     相应值的Go语法表示           Printf("%#v", people)   main.Human{Name:"zhangsan"}
> %T      相应值的类型的Go语法表示       Printf("%T", people)   main.Human
> %%      字面上的百分号，并非值的占位符  Printf("%%")            %
> 
> ```
>
> ```
> *布尔占位符*
> 占位符       说明                举例                     输出
> %t          true 或 false。     Printf("%t", true)       true
> ```
>
> ```
> *整数占位符*
> 占位符     说明                                  举例                       输出
> %b      二进制表示                             Printf("%b", 5)             101
> %c      相应Unicode码点所表示的字符              Printf("%c", 0x4E2D)        中
> %d      十进制表示                             Printf("%d", 0x12)          18
> %o      八进制表示                             Printf("%d", 10)            12
> %q      单引号围绕的字符字面值，由Go语法安全地转义  Printf("%q", 0x4E2D)        '中'
> %x      十六进制表示，字母形式为小写 a-f          Printf("%x", 13)             d
> %X      十六进制表示，字母形式为大写 A-F          Printf("%x", 13)             D
> %U      Unicode格式：U+1234，等同于 "U+%04X"    Printf("%U", 0x4E2D)        U+4E2D
> ```
>
> ```
> *浮点数和复数的组成部分（实部和虚部)*
> 占位符     说明                              举例                           输出
> %b      无小数部分的，指数为二的幂的科学计数法，
>         与 strconv.FormatFloat 的 'b' 转换格式一致。例如 -123456p-78
> %e      科学计数法，例如 -1234.456e+78        Printf("%e", 10.2)       1.020000e+01
> %E      科学计数法，例如 -1234.456E+78        Printf("%e", 10.2)       1.020000E+01
> %f      有小数点而无指数，例如 123.456        Printf("%f", 10.2)        10.200000
> %g      根据情况选择 %e 或 %f 以产生更紧凑的（无末尾的0）输出 Printf("%g", 10.20)   10.2
> %G      根据情况选择 %E 或 %f 以产生更紧凑的（无末尾的0）输出 Printf("%G", 10.20+2i) (10.2+2i)
> ```
>
> ```
> *字符串与字节切片*
> 占位符     说明                              举例                           输出
> %s      输出字符串表示（string类型或[]byte)   Printf("%s", []byte("Go语言"))  Go语言
> %q      双引号围绕的字符串，由Go语法安全地转义  Printf("%q", "Go语言")         "Go语言"
> %x      十六进制，小写字母，每字节两个字符      Printf("%x", "golang")         676f6c616e67
> %X      十六进制，大写字母，每字节两个字符      Printf("%X", "golang")         676F6C616E67
> ```
>
> ```
> *指针*
> 占位符         说明                      举例                             输出
> %p      十六进制表示，前缀 0x          Printf("%p", &people)             0x4f57f0
> ```
>
> ```
> *其它标记*
> 占位符      说明                             举例          输出
> +      总打印数值的正负号；对于%q（%+q）保证只输出ASCII编码的字符。 
>                                            Printf("%+q", "中文")  "\u4e2d\u6587"
> -      在右侧而非左侧填充空格（左对齐该区域）
> #      备用格式：为八进制添加前导 0（%#o）      Printf("%#U", '中')      U+4E2D
>        为十六进制添加前导 0x（%#x）或 0X（%#X），为 %p（%#p）去掉前导 0x；
>        如果可能的话，%q（%#q）会打印原始 （即反引号围绕的）字符串；
>        如果是可打印字符，%U（%#U）会写出该字符的
>        Unicode 编码形式（如字符 x 会被打印成 U+0078 'x'）。
> ' '    (空格)为数值中省略的正负号留出空白（% d）；
>        以十六进制（% x, % X）打印字符串或切片时，在字节之间用空格隔开
> 0      填充前导的0而非空格；对于数字，这会将填充移到正负号之后
> ```
>
> > golang没有 '%u' 点位符，若整数为无符号类型，默认就会被打印成无符号的。
> >
> >  
> >
> > 宽度与精度的控制格式以Unicode码点为单位。宽度为该数值占用区域的最小宽度；精度为小数点之后的位数。
> > 操作数的类型为int时，宽度与精度都可用字符 '*' 表示。
> >
> > 对于 %g/%G 而言，精度为所有数字的总数，例如：123.45，%.4g 会打印123.5，（而 %6.2f 会打印123.45）。
> >
> > %e 和 %f 的默认精度为6
> >
> > 对大多数的数值类型而言，宽度为输出的最小字符数，如果必要的话会为已格式化的形式填充空格。
> >
> > 而以字符串类型，精度为输出的最大字符数，如果必要的话会直接截断。



## 类型转换

表达式 `T(v)` 将值 `v` 转换为类型 `T`。

一些关于数值的转换：

```go
var i int = 42
var f float64 = float64(i)
var u uint = uint(f)
```

或者，更加简单的形式：

```go
i := 42
f := float64(i)
u := uint(f)
```

Go 在不同类型的项之间赋值时需要***显式***转换.

```go
package main

import (
	"fmt"
	"math"
)

func main() {
	var x, y int = 3, 4
	var f float64 = math.Sqrt(float64(x*x + y*y))
	var z uint = uint(f)
	fmt.Println(x, y, z)
}
```

## 类型推导

在声明一个变量而不指定其类型时（即使用不带类型的 `:=` 语法或 `var =`表达式语法），变量的类型由右值推导得出。

当右值声明了类型时，新变量的类型与其相同：

```go
var i int
j := i // j 也是一个 int
```

不过当右边包含未指明类型的数值常量时，新变量的类型就可能是 `int`, `float64` 或 `complex128` 了，这取决于常量的精度：

```go
i := 42           // int
f := 3.142        // float64
g := 0.867 + 0.5i // complex128
```

## 常量

常量的声明与变量类似，只不过是使用 `const` 关键字。

常量可以是字符、字符串、布尔值或数值。

常量不能用 `:=` 语法声明。

## 数值常量

数值常量是高精度的 **值**。

一个未指定类型的常量由上下文来决定其类型。

（`int` 类型最大可以存储一个 64 位的整数，有时会更小。）

（`int` 可以存放最大64位的整数，根据平台不同有时会更少。）

```go
package main

import "fmt"

const (
	// 将 1 左移 100 位来创建一个非常大的数字
	// 即这个数的二进制是 1 后面跟着 100 个 0
	Big = 1 << 100
	// 再往右移 99 位，即 Small = 1 << 1，或者说 Small = 2
	Small = Big >> 99
)

func needInt(x int) int { return x*10 + 1 }
func needFloat(x float64) float64 {
	return x * 0.1
}

func main() {
  //fmt.Println(Big)// overflows int
	fmt.Println(needInt(Small))//21
	fmt.Println(needFloat(Small))//0.2
	fmt.Println(needFloat(Big))//1.2676506002282295e+29
}

```

## for

Go 只有一种循环结构：`for` 循环。

**注意**：和 C、Java、JavaScript 之类的语言不同，Go 的 for 语句后面的三个构成部分外没有小括号， 大括号 `{ }` 则是必须的。

初始化语句和后置语句是可选的。

```go
package main

import "fmt"

func main() {
	sum := 1
	for ; sum < 1000; {
		sum += sum
	}
	fmt.Println(sum)
}

```

此时你可以去掉分号，因为 C 的 `while` 在 Go 中叫做 `for`。

```go
package main

import "fmt"

func main() {
	sum := 1
	for sum < 1000 {
		sum += sum
	}
	fmt.Println(sum)
}
```

## if 的简短语句

同 `for` 一样， `if` 语句可以在条件表达式前执行一个简单的语句。

该语句声明的变量作用域仅在 `if` 之内。

```go
package main

import (
	"fmt"
	"math"
)

func pow(x, n, lim float64) float64 {
	if v := math.Pow(x, n); v < lim {
		return v
	}
	return lim
}
```

##  switch

`switch` 是编写一连串 `if - else` 语句的简便方法。它运行第一个值等于条件表达式的 case 语句。

Go  只运行选定的 case，而非之后所有的 case。 实际上，Go 自动提供了在这些语言中每个 case 后面所需的 `break` 语句。 除非以 `fallthrough` 语句结束，否则分支会自动终止。 Go 的另一点重要的不同在于 switch 的 case 无需为常量，且取值不必为整数。

```go
package main

import (
	"fmt"
	"runtime"
)

func main() {
	fmt.Print("Go runs on ")
	switch os := runtime.GOOS; os {
	case "darwin":
		fmt.Println("OS X.")
	case "linux":
		fmt.Println("Linux.")
	default:
		// freebsd, openbsd,
		// plan9, windows...
		fmt.Printf("%s.\n", os)
	}
}

```

##  defer 栈

defer 语句会将函数推迟到外层函数返回之后执行。

推迟调用的函数其参数会立即求值，但直到外层函数返回前该函数都不会被调用。

推迟的函数调用会被压入一个栈中。当外层函数返回时，被推迟的函数会按照**先进后出**的顺序调用

```go
package main

import "fmt"

func main() {
	fmt.Println("counting")

	for i := 0; i < 10; i++ {
		defer fmt.Println(i)
	}

	fmt.Println("done")
}
```

## 指针

类型 `*T` 是指向 `T` 类型值的指针。其零值为 `nil`。

```go
var p *int
```

`&` 操作符会生成一个指向其操作数的指针。

```go
i := 42
p = &i
```

`*` 操作符表示指针指向的底层值。

```go
fmt.Println(*p) // 通过指针 p 读取 i
*p = 21         // 通过指针 p 设置 i
```



## 结构体字段

结构体字段使用点号来访问。

```go
package main

import "fmt"

type Vertex struct {
	X int
	Y int
}

func main() {
	v := Vertex{1, 2}
	v.X = 4
	fmt.Println(v.X)
}

```

## 结构体指针

结构体字段可以通过结构体指针来访问

```go
package main

import "fmt"

type Vertex struct {
	X int
	Y int
}

func main() {
	v := Vertex{1, 2}
	p := &v
  p.X = 1e9 // (*p).X = 1e9, 此处隐式间接引用
	fmt.Println(v)
}

```



## 结构体文法

```go
package main

import "fmt"

type Vertex struct {
	X, Y int
}

var (
	v1 = Vertex{1, 2}  // 创建一个 Vertex 类型的结构体
	v2 = Vertex{X: 1}  // Y:0 被隐式地赋予
	v3 = Vertex{}      // X:0 Y:0
	p  = &Vertex{1, 2} // 创建一个 *Vertex 类型的结构体（指针）
)

func main() {
	fmt.Println(v1, v2, v3, p)// {1 2} {1 0} {0 0} &{1 2}
}

```



## 数组

类型 `[n]T` 表示拥有 `n` 个 `T` 类型的值的数组。

```go
package main

import "fmt"

func main() {
	var a [2]string
	a[0] = "Hello"
	a[1] = "World"
	fmt.Println(a[0], a[1])
	fmt.Println(a)

	primes := [6]int{2, 3, 5, 7, 11, 13}
	fmt.Println(primes)
}
```

## 切片

类型 `[]T` 表示一个元素类型为 `T` 的切片。

切片通过两个下标来界定，即一个上界和一个下界，二者以冒号分隔, **左闭右开**

```go
package main

import "fmt"

func main() {
	primes := [6]int{2, 3, 5, 7, 11, 13}

	var s []int = primes[1:4]
	fmt.Println(s)// [3, 5, 7]
}

//切片文法
q := []int{2, 3, 5, 7, 11, 13}
	fmt.Println(q)//[2 3 5 7 11 13]
```

> ## 切片就像数组的引用
>
> 切片并不存储任何数据，它只是描述了底层数组中的一段。
>
> 更改切片的元素会修改其底层数组中对应的元素。
>
> 与它共享底层数组的切片都会观测到这些修改。

### 切片的默认行为

切片下界的默认值为 `0`，上界则是该切片的长度。

```go
package main

import "fmt"

func main() {
	s := []int{2, 3, 5, 7, 11, 13}

	s = s[1:4]
	fmt.Println(s)//[3, 5, 7]

	s = s[:2]
	fmt.Println(s)// [3, 5]

	s = s[1:]
	fmt.Println(s)//[5]
}
```

### 切片的长度与容量

切片`s`拥有 **长度** `len(s)`和 **容量**`cap(s)`。

切片的长度就是它所包含的元素个数。

切片的容量是从它的第一个元素开始数，到其底层数组元素末尾的个数。

```go
package main

import "fmt"

func main() {
	s := []int{2, 3, 5, 7, 11, 13}
	printSlice(s)

	// 截取切片使其长度为 0
	s = s[:0]
	printSlice(s)

	// 拓展其长度
	s = s[:4] // s = s[:7]  silce bounds out of range
	printSlice(s)

	// 舍弃前两个值
	s = s[2:]
	printSlice(s)
}

func printSlice(s []int) {
	fmt.Printf("len=%d cap=%d %v\n", len(s), cap(s), s)
}
```

> ##  nil 切片
>
> 切片的零值是 `nil`。
>
> nil 切片的长度和容量为 0 且没有底层数组。



### 用 make 创建切片

切片可以用内建函数 `make` 来创建，这也是你创建动态数组的方式。

`make` 函数会分配一个元素为零值的数组并返回一个引用了它的切片：

```go
a := make([]int, 5)  // len(a)=5
```

要指定它的容量，需向 `make` 传入第三个参数：

```go
b := make([]int, 0, 5) // len(b)=0, cap(b)=5
```



### append函数

- 加到切片末尾

- 当 `s` 的底层数组太小，不足以容纳所有给定的值时，它就会分配一个更大的数组。返回的切片会指向这个新分配的数组。

- 将b加到a末尾

  ```go
  a := []string{"John", "Paul"}
  b := []string{"George", "Ringo", "Pete"}
  a = append(a, b...) // equivalent to "append(a, b[0], b[1], b[2])"
  ```



## Range

`for` 循环的 `range` 形式可遍历切片或映射。

当使用 `for` 循环遍历切片时，每次迭代都会返回两个值。第一个值为当前元素的下标，第二个值为该下标所对应元素的一份副本

可以将下标或值赋予 `_` 来忽略它。

```go
for i, _ := range pow
for _, value := range pow
```

若你只需要索引，忽略第二个变量即可。

```go
for i := range pow
```

```go
func main() {
	pow := make([]int, 10)
	for i := range pow {
		pow[i] = 1 << uint(i) // == 2**i
	}
	for _, value := range pow {
		fmt.Printf("%d\n", value)
	}
}

```



##  方法

Go 没有类。不过你可以为结构体类型定义方法。

方法就是一类带特殊的 **接收者** 参数的函数。

方法接收者在它自己的参数列表内，位于 `func` 关键字和方法名之间。

在此例中，`Abs` 方法拥有一个名为 `v`，类型为 `Vertex` 的接收者。

```go
package main

import (
	"fmt"
	"math"
)

type Vertex struct {
	X, Y float64
}

func (v Vertex) Abs() float64 {
	return math.Sqrt(v.X*v.X + v.Y*v.Y)
}

func main() {
	v := Vertex{3, 4}
	fmt.Println(v.Abs())
}
```

## 方法与指针重定向

比较前两个程序，你大概会注意到带指针参数的函数必须接受一个指针：

```
var v Vertex
ScaleFunc(v, 5)  // 编译错误！
ScaleFunc(&v, 5) // OK
```

而以指针为接收者的方法被调用时，接收者既能为值又能为指针：

```
var v Vertex
v.Scale(5)  // OK
p := &v
p.Scale(10) // OK
```

对于语句 `v.Scale(5)`，即便 `v` 是个值而非指针，带指针接收者的方法也能被直接调用。 也就是说，由于 `Scale` 方法有一个指针接收者，为方便起见，Go 会将语句 `v.Scale(5)` 解释为 `(&v).Scale(5)`。

```go
package main

import "fmt"

type Vertex struct {
	X, Y float64
}

func (v *Vertex) Scale(f float64) {
	v.X = v.X * f
	v.Y = v.Y * f
}

func ScaleFunc(v *Vertex, f float64) {
	v.X = v.X * f
	v.Y = v.Y * f
}

func main() {
	v := Vertex{3, 4}
	v.Scale(2)
	ScaleFunc(&v, 10)

	p := &Vertex{4, 3}
	p.Scale(3)
	ScaleFunc(p, 8)

	fmt.Println(v, p)
}
```

同样的事情也发生在相反的方向。

接受一个值作为参数的函数必须接受一个指定类型的值：

```go
var v Vertex
fmt.Println(AbsFunc(v))  // OK
fmt.Println(AbsFunc(&v)) // 编译错误！
```

而以值为接收者的方法被调用时，接收者既能为值又能为指针：

```go
var v Vertex
fmt.Println(v.Abs()) // OK
p := &v
fmt.Println(p.Abs()) // OK
```

这种情况下，方法调用 `p.Abs()` 会被解释为 `(*p).Abs()`。

##  选择值或指针作为接收者

使用指针接收者的原因有二：

首先，方法能够修改其接收者指向的值。

其次，这样可以避免在每次调用方法时复制该值。若值的类型为大型结构体时，这样做会更加高效

```go
package main

import (
	"fmt"
	"math"
)

type Vertex struct {
	X, Y float64
}

func (v *Vertex) Scale(f float64) {
	v.X = v.X * f
	v.Y = v.Y * f
}

func (v *Vertex) Abs() float64 {
	return math.Sqrt(v.X*v.X + v.Y*v.Y)
}

func main() {
	v := &Vertex{3, 4}
	fmt.Printf("Before scaling: %+v, Abs: %v\n", v, v.Abs())//Before scaling: &{X:3 Y:4}, Abs: 5
	v.Scale(5)
	fmt.Printf("After scaling: %+v, Abs: %v\n", v, v.Abs())//After scaling: &{X:15 Y:20}, Abs: 25
}
```

##  接口与隐式实现

类型通过实现一个接口的所有方法来实现该接口。既然无需专门显式声明，也就没有“implements”关键字。

隐式接口从接口的实现中解耦了定义，这样接口的实现可以出现在任何包中，无需提前准备。

因此，也就无需在每一个实现上增加新的接口名称，这样同时也鼓励了明确的接口定义

```go
package main

import "fmt"

type I interface {
	M()
}

type T struct {
	S string
}

// 此方法表示类型 T 实现了接口 I，但我们无需显式声明此事。
func (t T) M() {
	fmt.Println(t.S)
}

func main() {
	var i I = T{"hello"}
	i.M()
}
```



## 错误

通常函数会返回一个 `error` 值，调用的它的代码应当判断这个错误是否等于 `nil`来进行错误处理。

```go
package main

import (
	"fmt"
  "strconv"
)
i, err := strconv.Atoi("42")
if err != nil {
    fmt.Printf("couldn't convert number: %v\n", err)
    return
}

fmt.Println("Converted integer:", i)
```

`error` 为 nil 时表示成功；非 nil 的 `error` 表示失败。



## Reader

`io` 包指定了 `io.Reader` 接口，它表示从数据流的末尾进行读取。

Go 标准库包含了该接口的[许多实现](https://go-zh.org/search?q=Read#Global)，包括文件、网络连接、压缩和加密等等。

`io.Reader` 接口有一个 `Read` 方法：

```go
func (T) Read(b []byte) (n int, err error)
```

`Read` 用数据填充给定的字节切片并返回填充的**字节数**和**错误值**。在遇到数据流的结尾时，它会返回一个 `io.EOF` 错误。

示例代码创建了一个 [`strings.Reader`](https://go-zh.org/pkg/strings/#Reader) 并以每次 8 字节的速度读取它的输出。

```go
package main

import (
	
	"fmt"
	"io"
	"strings"
)

func main() {
	r := strings.NewReader("Hello, Reader!")

	b := make([]byte, 8)
	for {
		n, err := r.Read(b)
		fmt.Printf("n = %v err = %v b = %v\n", n, err, b)
		fmt.Printf("b[:n] = %q\n", b[:n])
		if err == io.EOF {
			break
		}
	}
}
/*
n = 8 err = <nil> b = [72 101 108 108 111 44 32 82]
b[:n] = "Hello, R"
n = 6 err = <nil> b = [101 97 100 101 114 33 32 82]
b[:n] = "eader!"
n = 0 err = EOF b = [101 97 100 101 114 33 32 82]
b[:n] = ""
*/


```



## goroutine

goroutine是由 Go 运行时管理的轻量级线程。

```go
go f(x, y, z)
```

会启动一个新的 Go 程并执行

```
f(x, y, z)
```

`f`, `x`, `y` 和 `z` 的求值发生在当前的 Go 程中，而 `f` 的执行发生在新的 Go 程中。

Go 程在相同的地址空间中运行，因此在访问共享的内存时必须进行同步。[`sync`](https://go-zh.org/pkg/sync/) 包提供了这种能力，不过在 Go 中并不经常用到，因为还有其它的办法.

```go
package main

import (
	"fmt"
	"time"
)

func say(s string) {
	for i := 0; i < 5; i++ {
    time.Sleep(100 * time.Millisecond)//如果没有Sleep(), 输出会是5个hello.因为还没来得及启动goroutine.
		fmt.Println(s)
	}
}

func main() {
	go say("world")
	say("hello")
}
/*
world
hello
hello
world
world
hello
hello
world
world
hello
*/


```



##  信道

信道是带有类型的管道，你可以通过它用信道操作符 `<-` 来发送或者接收值。

```
ch <- v    // 将 v 发送至信道 ch。
v := <-ch  // 从 ch 接收值并赋予 v。
```

（“箭头”就是数据流的方向。）

和映射与切片一样，信道在使用前必须创建：

```
ch := make(chan int)
```

默认情况下，发送和接收操作在另一端准备好之前都会阻塞。这使得 Go 程可以在没有显式的锁或竞态变量的情况下进行同步。

以下示例对切片中的数进行求和，将任务分配给两个 Go 程。一旦两个 Go 程完成了它们的计算，它就能算出最终的结果。

```go
package main

import "fmt"

func sum(s []int, c chan int) {
	sum := 0
	for _, v := range s {
		sum += v
	}
	c <- sum // 将和送入 c
}

func main() {
	s := []int{7, 2, 8, -9, 4, 0}

	c := make(chan int)
	go sum(s[:len(s)/2], c)
	go sum(s[len(s)/2:], c)
	x, y := <-c, <-c // 从 c 中接收

	fmt.Println(x, y, x+y)
}
/*
-5 17 12
*/
```



## range 和 close

发送者可通过 `close` 关闭一个信道来表示没有需要发送的值了。接收者可以通过为接收表达式分配第二个参数来测试信道是否被关闭：若没有值可以接收且信道已被关闭，那么在执行完

```
v, ok := <-ch
```

之后 `ok` 会被设置为 `false`。

循环 `for i := range c` 会不断从信道接收值，直到它被关闭。

*注意：* 只有发送者才能关闭信道，而接收者不能。向一个已经关闭的信道发送数据会引发程序恐慌（panic）。

*还要注意：* 信道与文件不同，通常情况下无需关闭它们。只有在必须告诉接收者不再有需要发送的值时才有必要关闭，例如终止一个 `range` 循环。

```go
package main

import (
	"fmt"
)

func fibonacci(n int, c chan int) {
	x, y := 0, 1
	for i := 0; i < n; i++ {
		c <- x
		x, y = y, x+y
	}
	close(c)
}

func main() {
	c := make(chan int, 10)
  go fibonacci(cap(c), c)// cap()查看capacity
	for i := range c {
		fmt.Println(i)
	}
}

```



## select 语句

`select` 语句使一个 Go 程可以等待多个通信操作。

`select` 会阻塞到某个分支可以继续执行为止，这时就会执行该分支。当多个分支都准备好时会随机选择一个执行。

```go
package main

import "fmt"

func fibonacci(c, quit chan int) {
	x, y := 0, 1
	for {
		select {
		case c <- x:
			x, y = y, x+y
		case <-quit:
			fmt.Println("quit")
			return
		}
	}
}

func main() {
	c := make(chan int)
	quit := make(chan int)
	go func() {
		for i := 0; i < 10; i++ {
			fmt.Println(<-c)
		}
		quit <- 0
	}()
	fibonacci(c, quit)
}

```



## 默认选择

当 `select` 中的其它分支都没有准备好时，`default` 分支就会执行。

为了在尝试发送或者接收时不发生阻塞，可使用 `default` 分支：

```
select {
case i := <-c:
    // 使用 i
default:
    // 从 c 中接收会阻塞时执行
}
```

```go
package main

import (
	"fmt"
	"time"
)

func main() {
	tick := time.Tick(100 * time.Millisecond)
	boom := time.After(500 * time.Millisecond)
	for {
		select {
		case <-tick:
			fmt.Println("tick.")
		case <-boom:
			fmt.Println("BOOM!")
			return
		default:
			fmt.Println("    .")
			time.Sleep(50 * time.Millisecond)
		}
	}
}
/*
    .
    .
tick.
    .
    .
tick.
    .
    .
tick.
    .
    .
tick.
    .
    .
tick.
BOOM!
*/
```



## sync.Mutex

我们已经看到信道非常适合在各个 Go 程间进行通信。

但是如果我们并不需要通信呢？比如说，若我们只是想保证每次只有一个 Go 程能够访问一个共享的变量，从而避免冲突？

这里涉及的概念叫做 *互斥（mutual*exclusion）* ，我们通常使用 *互斥锁（Mutex）* 这一数据结构来提供这种机制。

Go 标准库中提供了 [`sync.Mutex`](https://go-zh.org/pkg/sync/#Mutex) 互斥锁类型及其两个方法：

- `Lock`
- `Unlock`

我们可以通过在代码前调用 `Lock` 方法，在代码后调用 `Unlock` 方法来保证一段代码的互斥执行。参见 `Inc` 方法。

我们也可以用 `defer` 语句来保证互斥锁一定会被解锁。参见 `Value` 方法。

```go
package main

import (
	"fmt"
	"sync"
	"time"
)

// SafeCounter 的并发使用是安全的。
type SafeCounter struct {
	v   map[string]int
	mux sync.Mutex
}

// Inc 增加给定 key 的计数器的值。
func (c *SafeCounter) Inc(key string) {
	c.mux.Lock()
	// Lock 之后同一时刻只有一个 goroutine 能访问 c.v
	c.v[key]++
	c.mux.Unlock()
}

// Value 返回给定 key 的计数器的当前值。
func (c *SafeCounter) Value(key string) int {
	c.mux.Lock()
	// Lock 之后同一时刻只有一个 goroutine 能访问 c.v
	defer c.mux.Unlock()
	return c.v[key]
}

func main() {
	c := SafeCounter{v: make(map[string]int)}
	for i := 0; i < 1000; i++ {
		go c.Inc("somekey")
	}

	time.Sleep(time.Second)
	fmt.Println(c.Value("somekey"))
}
//1000
```



## references

(TODO)

