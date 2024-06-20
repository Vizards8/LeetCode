## Leetcode for Go

---

- [Leetcode for Go](#leetcode-for-go)
  - [Basic Syntax](#basic-syntax)
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
  - [ACM](#acm)

---

### Basic Syntax

[Back](#leetcode-for-go)

- 基本语法:

  ```go
  // && || ! true false
  // if / for
  if condition {
  } else if condition {
  } else {
  }

  for condition {
  }

  for i := 0; i < 10; i++ {
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

  // 正常除法：3 / 2
  a := 3.0 / 2

  // 向下取整：3 // 2
  a := math.Floor(3.0 / 2)

  // 截尾除法/向零截断：int(3 / 2)
  a := 3 / 2

  // 四舍五入：round(a / b) 并不一样！
  a := math.Round(3.0 / 2)

  // string -> int/float
  i, err := strconv.Atoi(s)
  f, err := strconv.ParseFloat(s, 64)

  // String <-> []byte
  b := []byte(s)
  s := string(b)

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

### String

[Back](#leetcode-for-go)

- Comparison:

  - strings.Builder 处理速度快但不是线程安全的

- String:

  ```go
  s := "asdefgasdefg"

  // 常用
  cs := []rune(s)
  strings.Compare("abcd", s2) == 0 // 比较两个字符串

  s[index]
  strings.Index(s, "sub")
  len(s)
  list_s := strings.Split(s, " ")
  s := strings.Join(list_s, ",")
  s := s[start:end] //[start, end)

  // 遍历
  for _, c := range s {
  }
  for i := 0; i < len(s); i++ {
      c := s[i]
  }

  // string -> int/float
  i, err := strconv.Atoi(s)
  f, err := strconv.ParseFloat(s, 64)

  // API
  s := strings.ToLower(s)
  s := strings.ToUpper(s)
  s := strings.TrimSpace(s)
  ```

- StringBuilder: 可变长字符串

  ```go
  var sb strings.Builder
  sb.WriteString("String")
  sb.WriteByte('a')
  sb.WriteRune('你')
  sb.String()

  // 遍历
  for i := 0; i < sb.Len(); i++ {
      sb.String()[i]
  }

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
// res = [0 for _ in range(n)]
arr := [100]int{}
arr := [...]int{1, 2, 3, 4}
arr2D := [...][2]int{{1, 2}, {3, 4}}

// len(arr)
len(arr)

// arr.sort()
sort.Ints(arr)

// 深拷贝
b := append([]int(nil), arr...)

// 切片
c := arr[1:4] // [start, end)

// reverse: a[::-1]
// 手动双指针 reverse 吧

// print
fmt.Println(arr)
fmt.Println(arr2D)

// int[] <-> []int
// 记不住的话，不如一个个放进去
list := []int{1, 2, 3}
arr := make([]int, len(list))
copy(arr, list)

// 填充，初始化
for i := range a {
    a[i] = "fill"
}
```

### Slice: 动态数组

[Back](#leetcode-for-go)

```go
list := []int{}
list := []int{a, b, c}
list = append(list, d)
list = append(list[:index], list[index+1:]...)
list[index] = value
value := list[index]
index := indexOf(list, value)
contains := contains(list, value)
empty := len(list) == 0
sublist := list[start:end] // [start, end)

// 二维数组
res := [][]int{}
res = append(res, []int{})
res = append(res, []int{})
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
m := make(map[int]int)
m[key] = value
v, exists := m[key]
delete(m, key)
len(m)
for k, v := range m {
}
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
