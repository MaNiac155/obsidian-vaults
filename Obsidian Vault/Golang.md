#### Variables
3 ways of declare
```go
var a = "asdfg"

var b,c int = 2,5

var d = true

var e int

f:=4

// := means declaring and initializing
```
#### Constant
use `const` to replace `var`
```go
const n = 500000000
```
常数表达式可以执行任意精度的运算.
数值型常量没有确定的类型，直到被给定某个类型，比如显式类型转化。
一个数字可以根据上下文的需要（比如变量赋值、函数调用）自动确定类型。

#### for
`for` is the only looping statement.
```go
func main() {
// used the same as while
    i := 1
    for i <= 3 {
        fmt.Println(i)
        i = i + 1
    }
// used like for in C
    for j := 0; j < 3; j++ {
        fmt.Println(j)
    }
//use range to do forEach
    for i := range 3 {
        fmt.Println("range", i)
    }
// dead loop
    for {
        fmt.Println("loop")
        break
    }
}
```
#### if else
```go
func main() {
//A statement can precede conditionals; any variables declared in this statement are available in the current and all subsequent branches.
    if num := 9; num < 0 {
        fmt.Println(num, "is negative")
    } else if num < 10 {
        fmt.Println(num, "has 1 digit")
    } else {
        fmt.Println(num, "has multiple digits")
    }
}
```
#### array
An array's length is exactly set, cannot change.

By default an array is zero-valued, which for `int`s means `0`s.

Use ... to let the compiler count the number of elements.
```go
	b := [5]int{1, 2, 3, 4, 5}
	fmt.Println("dcl:", b)
	
	b = [...]int{100, 3: 400, 500}
    fmt.Println("idx:", b)
```

#### Slices
Gives a more powerful interface to sequences than arrays.
不给数字就是slice。
未初始化时等于nil，长度为0，类型根据元素类型确定。
需要用make来创建
内置的append，返回新的切片。需要接受返回值。

```go
package main
//需要import
import (
    "fmt"
    "slices"
)
func main() {

    var s []string
    fmt.Println("uninit:", s, s == nil, len(s) == 0)
// 需要用make来创建
    s = make([]string, 3)
    fmt.Println("emp:", s, "len:", len(s), "cap:", cap(s))
// cap: capacity
    s[0] = "a"
    s[1] = "b"
    s[2] = "c"
    fmt.Println("set:", s)
    fmt.Println("get:", s[2])

    fmt.Println("len:", len(s))

// 内置的append，返回新的切片。需要接受返回值。
    s = append(s, "d")
    s = append(s, "e", "f")
    fmt.Println("apd:", s)

    c := make([]string, len(s))
    copy(c, s) //copy into `c` from `s`.
    fmt.Println("cpy:", c)

//切片运算符，等于python
    l := s[2:5]
    fmt.Println("sl1:", l)

    l = s[:5]
    fmt.Println("sl2:", l)

    l = s[2:]
    fmt.Println("sl3:", l)

    t := []string{"g", "h", "i"}
    fmt.Println("dcl:", t)

//slices包里面有切片的函数
    t2 := []string{"g", "h", "i"}
    if slices.Equal(t, t2) {
        fmt.Println("t == t2")
    }

    twoD := make([][]int, 3)
    for i := 0; i < 3; i++ {
        innerLen := i + 1
        twoD[i] = make([]int, innerLen)
        for j := 0; j < innerLen; j++ {
            twoD[i][j] = i + j
        }
    }
    fmt.Println("2d: ", twoD)
}
```
#### Map
用make创建
类似C++的`unordered_map`
delete删除。 `delete(m,"key")`
clear清空
取值时可以用2个返回值，第一个是值，第二个是是否存在。 这可以用来消除 `键不存在` 和 `键的值为零值` 产生的歧义
`_,ok := m["key"]`

#### Range
