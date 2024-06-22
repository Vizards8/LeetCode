## Leetcode for Go

---

- [Leetcode for Go](#leetcode-for-go)
  - [Var](#var)
  - [Const](#const)
  - [Pointer](#pointer)
  - [Basic Syntax](#basic-syntax)
  - [Struct](#struct)
  - [String](#string)
  - [List: 基础数组](#list-基础数组)
  - [Slice: 动态数组](#slice-动态数组)
  - [Queue](#queue)
  - [Stack](#stack)
  - [Deque](#deque)
  - [Heap](#heap)
  - [Set](#set)
  - [Map](#map)
  - [Bit Manipulation](#bit-manipulation)
  - [Defer](#defer)
  - [Error](#error)
  - [ACM](#acm)

---

### Var

[Back](#leetcode-for-go)

```go
// 变量申明 var
// 赋初值
var a int = 10
var b string = "hello"
var l, m int = 60, 70

// 不赋初值，使用默认
var e int         // 默认值为 0
var f string      // 默认值为空字符串 ""
var n, o int

// 自动推断
var c = 20        // int 类型
var d = "world"   // string 类型
var vname1, vname2, vname3 = v1, v2, v3

// 简短申明：只能在函数内部使用，编译器会自动推断
g := 30           // int 类型
h := "hello"      // string 类型
vname1, vname2, vname3 := v1, v2, v3
```

### Const

[Back](#leetcode-for-go)

```go
// 常量申明 const
// 类型可省略，编译器会自动推断，不建议省略
const greeting [string] = "Hello, Go!"
const year [int] = 2024
const isGoFun [bool] = true

// iota 枚举，每一行 +1，可以认为是索引，有点抽象
const (
    Sunday = iota
    Monday
    Tuesday
)

fmt.Println(Sunday)   // 0
fmt.Println(Monday)   // 1
fmt.Println(Tuesday)  // 2
```

### Pointer

[Back](#leetcode-for-go)

```go
var a int = 10
var ptr *int

ptr = &a   // 获取变量 a 的指针

fmt.Println("Value of a:", a)   // 访问指针指向的值
fmt.Println("Address of a:", &a)
fmt.Println("Pointer ptr points to address:", ptr)
fmt.Println("Value at address ptr points to:", *ptr)

*ptr = 20   // 修改指针指向的值
fmt.Println("New value of a:", a)
```

### Basic Syntax

[Back](#leetcode-for-go)

- 基本语法:

  ```go
  // 运算符
  // 算数运算符，关系运算符，逻辑运算符，赋值运算符 均和 Python 一致
  
  // && || ! true false
  
  // if
  if condition {
  } else if condition {
  } else {
  }

  // for
  for i := 0; i < 10; i++ {
  }

  // for range
  numbers := []int{1, 2, 3, 4, 5}
  for index, value := range numbers {
    fmt.Printf("Index: %d, Value: %d\n", index, value)
  }

  // while
  for condition {}

  // switch...case
  // 防止 if 嵌套过多
  // 自动带 break，使用 fallthroug 取消
  switch variable {
  case value1 or condition1:
      // 执行代码
  case value2 or condition2:
      // 执行代码
  case value3, value4, value5:
      // 执行代码
  default:
      // 执行代码
  }

  // 深拷贝
  a := append([]int(nil), b...)

  // 长度
  arr := []int{1, 2, 3}
  str := "hello"
  len(arr)    // 数组和切片
  len(str)    // 字符串

  // 输出
  fmt.Println(arr)       // 1D
  fmt.Println(arr2D)     // >= 2D
  fmt.Println(arrayList) // 1D & >= 2D

  // 格式化输出，其他类似 Java
  fmt.Printf("Name: %s, Age: %d\n", name, age)

  // 正常除法：3 / 2
  res := float64(a) / float64(b)

  // 向下取整：math.floor(3 / 2)
  res := int(math.Floor(float64(a) / float64(b)))

  // 截尾除法/向零截断：3 // 2
  a := 3 / 2

  // 四舍五入：round(a / b) 并不一样！
  // 不能直接控制精度，通过 *100 /100 的方式实现
  res := math.Round(float64(a) / float64(b) * 100) / 100

  // string -> int/float
  i, err := strconv.Atoi(s)
  f, err := strconv.ParseFloat(s, 64)

  // ord()
  fmt.Println(int('a'))

  // chr()
  fmt.Println(string(97))

  // Integer 最大最小值
  numMax := math.MaxInt32
  numMin := math.MinInt32

  // 溢出问题, c = a + b
  c := int64(a) + int64(b)

  // left = stack[-1] if stack else -1
  Go 没有多目运算符

  // 交换
  a, b= b, a
  ```

- Math:

  ```go
  math.Max(float64(a), float64(b))
  math.Min(float64(a), float64(b))

  math.Floor(a) // ≤
  math.Ceil(a)  // ≥

  math.Pow(a, 2)
  math.Sqrt(a)

  rand.Float64() // [0, 1) 的随机数
  ```

  - GCD

  ```go
  func gcd(a, b int) int {
      for b != 0 {
          a, b = b, a % b
      }
      return a
  }
  ```

- Function:

  ```go
  // 常规函数
  func divide(x, y int) (int, int) {
    quotient := x / y
    remainder := x % y
    return quotient, remainder
  }

  // 函数返回值，有形参名字
  func divide(x, y int) (quotient int, remainder int) {
    quotient := x / y
    remainder := x % y
    return
  }

  // 匿名函数
  add := func(x, y int) int {
      return x + y
  }
  fmt.Println(add(3, 5)) // 使用匿名函数

  // 大写的函数名可以被包外的代码访问
  // 小写的函数名只能在包内访问
  ```

### Struct

[Back](#leetcode-for-go)

```go
// 定义结构体
type Person struct {
    FirstName string
    LastName  string
    Age       int
    City      string
}

// 访问结构体字段
fmt.Println("First Name:", person1.FirstName)

// 传的是拷贝，需要传引用需要用指针
func updateName(p *Person) {
    p.Name = "Updated"
}
```

### String

[Back](#leetcode-for-go)

```go
str := "Hello, World!"

// 常用
len(str)
greeting := "Hello, " + "Go!"
substr := str[7:12] // [start, end)
contains := strings.Contains(str, "World") // 包含
index := strings.Index(str, "World") // 查找
replaced := strings.Replace(str, "World", "Go", -1) // 替换
split := strings.Split(str, ", ") // 分割

// Python: (',').join(arr)
import "strings"
arr := []string{"apple", "banana", "cherry"}
result := strings.Join(arr, ",")

// 遍历
for index, c := range s {}
for i := 0; i < len(s); i++ {
    c := s[i]
}

// string -> int/float
i, err := strconv.Atoi(s)
f, err := strconv.ParseFloat(s, 64)

// int -> string
str := strconv.Itoa(num)

// float -> string
fstr := strconv.FormatFloat(fnum, 'f', 10, 64) // 保留10位，float64

// API
s := strings.ToLower(s)
s := strings.ToUpper(s)
s := strings.TrimSpace(s)

// string -> strings.Builder
str := "Hello, World!"
var builder strings.Builder
builder.WriteString(str)

// strings.Builder -> string
var builder strings.Builder
builder.WriteString("Hello, World")
result := builder.String()

```

- strings.Builder: 适用于需要频繁拼接字符串的情况

  ```go
  import "strings"
  var sb strings.Builder
  sb.WriteString("String")
  sb.WriteByte('a')
  sb.WriteRune('你')
  sb.String()

  // 遍历
  for i := 0; i < sb.Len(); i++ {
      sb.String()[i]
  }

  // 输出
  fmt.Println(builder.String()) 

  // Python: ().join(arr)
  sb.Reset()
  for i, v := range arr {
      if i > 0 {
          sb.WriteString(",")
      }
      sb.WriteString(strconv.Itoa(v))
  }
  s := sb.String()
  ```

### List: 基础数组

[Back](#leetcode-for-go)

```go
// 传参时需要严格匹配长度
// 传参时是值拷贝，非引用

// res = [0 for _ in range(n)]
var arr [10]int
arr := [100]int{}
arr := [...]int{1, 2, 3, 4}
arr2D := [...][2]int{
    {1, 2}, 
    {3, 4}
}
arr2 := [5]float32{1:2.0, 3:7.0} // 只初始化索引为 1 和 3 的元素

// 填充，初始化
for i := range a {
    a[i] = "fill"
}

```

### Slice: 动态数组

[Back](#leetcode-for-go)

```go
// 如果传入函数，传的是引用
slice := []int{}
slice := []int{a, b, c}
slice = append(list, d)
slice = append(list[:index], list[index+1:]...)
slice[index] = value
value := slice[index]
sublist := slice[start:end] // [start, end)

// 创建
slice := make([]int, 5) // 创建一个长度和容量都为 5 的切片
slice := make([]int, 5, 10) // 创建一个长度为 5 容量为 10 的切片

// len(arr)
len(slice)

// 判空
if slice == nil {}

// 遍历
for i, v := range slice {}
for i := 0; i < len(slice); i++ {}

// print
fmt.Println(arr)
fmt.Println(arr2D)

// 浅拷贝
shallowCopy := slice

// 深拷贝（仅限一维，二维不行）
deepCopy := make([]int, len(slice))
copy(deepCopy, slice)
copy(deepCopy, slice[:]) // [3]int -> slice

// 深拷贝（仅限一维，二维不行）
var deepCopy []int
deepCopy = append(deepCopy, slice...)
deepCopy = append(deepCopy, slice[:]...) // [3]int -> slice

// reverse: a[::-1]
// 手动双指针 reverse 吧
func reverse(slice []int) {
    for i, j := 0, len(slice)-1; i < j; i, j = i+1, j-1 {
        slice[i], slice[j] = slice[j], slice[i]
    }
}

// arr.sort()
sort.Ints(slice) // 升序排序
sort.Sort(sort.Reverse(sort.IntSlice(slice))) // 降序排序

// 自定义排序
// 升序排序
sort.Slice(slice, func(i, j int) bool {
    return slice[i] < slice[j]
})
// 降序排序
sort.Slice(slice, func(i, j int) bool {
    return slice[i] > slice[j]
})

// 二维数组
res := [][]int{}
res = append(res, []int{1, 2, 3})
sort.Slice(res, func(i, j int) bool { return res[i][0] < res[j][0] })
```

### Queue

[Back](#leetcode-for-go)

```go
queue := list.New()
queue.PushBack(1) // 添加
e := queue.Front()
if e != nil {
    value := e.Value
    queue.Remove(e) // 删除
}
```

### Stack

[Back](#leetcode-for-go)

```go
stack := list.New()
stack.PushBack(1)
e := stack.Back()
if e != nil {
    value := e.Value
    stack.Remove(e)
}
```

### Deque

[Back](#leetcode-for-go)

```go
deque := list.New()
deque.PushFront(1)
deque.PushBack(1)
e := deque.Front()
if e != nil {
    value := e.Value
    deque.Remove(e)
}
e := deque.Back()
if e != nil {
    value := e.Value
    deque.Remove(e)
}
```

### Heap

[Back](#leetcode-for-go)

```go
import "container/heap"

// 小顶堆
h := &IntHeap{}
heap.Init(h)
heap.Push(h, 1)
min := heap.Pop(h).(int)

// 大顶堆
h := &IntHeap{}
heap.Init(h)
heap.Push(h, -1)
max := -heap.Pop(h).(int)

type IntHeap []int

func (h IntHeap) Len() int           { return len(h) }
func (h IntHeap) Less(i, j int) bool { return h[i] < h[j] }
func (h IntHeap) Swap(i, j int)      { h[i], h[j] = h[j], h[i] }
func (h *IntHeap) Push(x interface{}) { *h = append(*h, x.(int)) }
func (h *IntHeap) Pop() interface{} {
    old := *h
    n := len(old)
    x := old[n-1]
    *h = old[0 : n-1]
    return x
}

```

### Set

[Back](#leetcode-for-go)

set：使用 map 实现 set

```go
set := make(map[string]struct{})
set["item"] = struct{}{}
_, exists := set["item"]
delete(set, "item")

// Set -> Slice
var list []string
for k := range set {
    list = append(list, k)
}
```

### Map

[Back](#leetcode-for-go)

map：不允许 key 为 nil

```go
// 初始化
var m1 map[string]int // 必须要 make，不然报错
m1 = make(map[string]int)
m2 := make(map[string]int)
m3 := map[string]int{
    "a": 1,
    "b": 2,
}

m[key] = value
v, exists := m[key]
delete(m, key)
len(m)
fmt.Println(m)
for k, v := range m {}
```

### Bit Manipulation

[Back](#leetcode-for-go)

```go
// 和python一样
a & b // 与
a ^ b // 异或
a | b // 或
1 << a // 左移
1 >> a // 右移
```

### Defer

[Back](#leetcode-for-go)

```go
// defer 会在当前函数返回之后执行
// Stack 栈结构，后进先出，输出 三二一
func main() {
    defer fmt.Println("第一个 defer")
    defer fmt.Println("第二个 defer")
    defer fmt.Println("第三个 defer")
    
    fmt.Println("函数体")
}
```

### Error

[Back](#leetcode-for-go)

```go
data, err := getDataFromServer()
if err != nil {
    return fmt.Errorf("获取数据失败: %w", err)
}
```


### ACM

[Back](#leetcode-for-go)

```go
// Init
reader := bufio.NewReader(os.Stdin)
scanner := bufio.NewScanner(os.Stdin)
scanner.Split(bufio.ScanWords)

// 判断是否还有下一行输入
for scanner.Scan() {
    line := scanner.Text()
}

// 获取下一个字符串
scanner.Scan()
word := scanner.Text()

// 获取下一个整数
scanner.Scan()
number, _ := strconv.Atoi(scanner.Text())

// 获取一行并分割
line, _ := reader.ReadString('\n')
parts := strings.Fields(line)
```

```go
// 模板
package main

import (
    "bufio"
    "fmt"
    "os"
    "strconv"
    "strings"
)

func main() {
    scanner := bufio.NewScanner(os.Stdin)
    scanner.Split(bufio.ScanWords)

    for scanner.Scan() {
        a, _ := strconv.Atoi(scanner.Text())
        scanner.Scan()
        b, _ := strconv.Atoi(scanner.Text())
        fmt.Println(a + b)
    }

    reader := bufio.NewReader(os.Stdin)
    for {
        line, err := reader.ReadString('\n')
        if err != nil {
            break
        }
        parts := strings.Fields(line)
        for _, part := range parts {
            num, _ := strconv.Atoi(part)
            fmt.Println(num)
        }
    }
}
```
