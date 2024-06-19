## Leetcode for Go

---

- [Leetcode for Go](#leetcode-for-go)
  - [Basic Syntax](#basic-syntax)
  - [String](#string)
  - [List: 基础数组](#list-基础数组)
  - [Collections](#collections)
  - [ArrayList: 动态数组](#arraylist-动态数组)
  - [Queue](#queue)
  - [Stack](#stack)
  - [Deque](#deque)
  - [PriorityQueue: heap](#priorityqueue-heap)
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

### Collections

[Back](#leetcode-for-go)

```go
list.isEmpty();
list.size();
Collections.reverse(list);
Collections.sort(list, Collections.reverseOrder());
list.sort((a, b) -> (b - a));
// bisect.bisect_left(arr, target)
// find: id >= 0, insert: -id - 1
Collections.binarySearch(arr, target);
```

### ArrayList: 动态数组

[Back](#leetcode-for-go)

```go
List<Integer> list = new ArrayList<>();
List<Integer> list = new ArrayList<>(Arrays.asList(a, b, c));
list.add((int)index, Object o);
list.addAll(list2);
list.get(index);
list.set(index, Integer);
list.remove(index);
list.remove(Integer.valueOf(3));
list.indexOf(Integer);
list.lastIndexOf(Integer);
list.contains(Integer);
list.isEmpty();
list.subList(int start,int end); // [start,end);

// 二维数组
List<List<Integer>> res = new ArrayList<>();
res.add(new ArrayList<>());
res.add(new ArrayList<>());
Collections.sort(res.get(0));

// ArrayList -> Set
Set<Integer> set = new HashSet<>(arrayList);
```

### Queue

[Back](#leetcode-for-go)

```go
Queue<Integer> queue = new LinkedList<>(); // 可放null，但别放
queue.offer(1); // 添加，失败，返回 false
queue.poll(); // 删除，若为空，返回 null
queue.peek(); // 获取，不删除
```

### Stack

[Back](#leetcode-for-go)

```go
Deque<Integer> stack = new LinkedList<>();
stack.push(1);
stack.pop();
stack.peek();
```

### Deque

[Back](#leetcode-for-go)

```go
Deque<Integer> deque = new LinkedList<>(); // 可放null，但别放
// append，若不能添加，返回 false
deque.offerFirst(1);
deque.offerLast(1);
// pop，若空返回 null
deque.pollFirst();
deque.pollLast();
// 获取，不删除， 若空返回 null
deque.peekFirst();
deque.peekLast();
```

### PriorityQueue: heap

[Back](#leetcode-for-go)

```go
// 小顶堆
PriorityQueue<Integer> pq = new PriorityQueue<>();
// 大顶堆
PriorityQueue<Integer> pq = new PriorityQueue<>((a, b) -> (b - a));

pq.offer(Integer); // 添加
pq.poll(); // 删除
pq.peek(); // 获取，不删除
pq.remove(Object); // 删除指定元素

// 放tuple? 想一想，java 可以自定义比较，必须要放tuple吗？
// a - b 升序 / b - a 降序
// return 1 -> a > b -> a 在后面
PriorityQueue<int[]> pq = new PriorityQueue<>((a, b) -> {
  if (a[0] == b[0]) {
    return b[1] - a[1];
  } else {
    return a[0] - b[0];
  }
});
pq.offer(new int[] {1, 2});
```

### Set

[Back](#leetcode-for-go)

- HashSet:

  ```go
  Set<String> set = new HashSet<>();
  Set<String> set = new HashSet<>(Arrays.asList(arr));
  set.add();
  set.contains();
  set.remove();

  // Set -> ArrayList
  List<Integer> list = new ArrayList<>(set);
  ```

- TreeSet: Sorted
  ```go
  Set<String> set = new TreeSet<>((o1,o2)->o2-o1);
  ```

### Map

[Back](#leetcode-for-go)

- HashMap: 允许 key，value 为 null

  ```go
  HashMap<Integer, Integer> map = new HashMap<>();
  map.put(key, value);
  map.getOrDefault(key, default);
  map.get(key);
  map.containsKey(key);
  map.remove(key);
  map.remove(key, value);
  map.clear();
  map.isEmpty();
  map.size();
  map.keySet();
  map.values();
  map.entrySet();
  //遍历
  //按键遍历
  for (int key: map.keySet())
  //按值遍历
  for (int value: map.values())
  //按Entry遍历
  for (Map.Entry<Integer,Integer> entry: map.entrySet()){
      entry.getKey();
      entry.getValue();
  }
  ```

- TreeMap

  ```go
  //按照 Key 降序排序
  Map<Integer,Integer> map = new TreeMap<>((o1,o2)->o2-o1);

  //按照 Value 升序排序：可以把 map.values() 转换为 list 排序再 sort
  Map<Integer,Integer> map = new HashMap<>()
  List<Map.Entry<Integer,Integer>> list = new ArrayList<>(map.entrySet());
  Collections.sort(list, (o1,o2)->o1.getValue()-o2.getValue());
  ```

### Bit Manipulation

[Back](#leetcode-for-go)

```go
// 和python一样
a & b; // 与
a ^ b; // 异或
a | b; // 或
1 << a; // 左移
1 >> a; // 右移
```

### ACM

[Back](#leetcode-for-go)

```go
// 注意：scanner.next() 和 scanner.nextLine() 不要混用

// Init
Scanner scanner = new Scanner(System.in);

// 判断是否还有下一个输入
while(scanner.hasNext()) {}

// 判断是否还有下一个输入(数字格式)
while(scanner.hasNextInt()) {}
while(scanner.hasNextLong()) {}
while(scanner.hasNextDouble()) {}
while(scanner.hasNextFloat()) {}

// 判断是否还有下一行输入
while(scanner.hasNextLine()) {}

// 获取下一个 String 格式
String word = scanner.next();

// 获取下一个 数字 格式
int number = scanner.nextInt();
long number = scanner.nextLong();
double number = scanner.nextDouble();
float number = scanner.nextFloat();

// 获取下一行并分割
String[] line = scanner.nextLine().split(" ");
```

```go
// 模板
import java.util.*;

public class Main {
    public static void main (String[] args) {
        Scanner scanner = new Scanner(System.in);

        while (scanner.hasNext()) {
            int a = scanner.nextInt();
            int b = scanner.nextInt();
        }

        while (scanner.hasNextLine()) {
            String[] line = scanner.nextLine().split(" ");
        }

        int T = scanner.nextInt();
        for (int i = 0; i < T; i++) {
            String[] line = scanner.nextLine().split(" ");
        }
    }
}

```
