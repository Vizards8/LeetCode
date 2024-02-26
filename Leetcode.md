# Leetcode Java 语法默写

- [Leetcode Java 语法默写](#leetcode-java-语法默写)
    - [Basic Syntax](#basic-syntax)
    - [String](#string)
    - [List: 基础数组](#list-基础数组)
    - [Collections: 数组，队列，栈，双端队列](#collections-数组队列栈双端队列)
    - [ArrayList: 动态数组](#arraylist-动态数组)
    - [Queue](#queue)
    - [Stack](#stack)
    - [Deque](#deque)
    - [PriorityQueue: heap](#priorityqueue-heap)
    - [Set](#set)
    - [Map](#map)
    - [Bit Manipulation](#bit-manipulation)

### Basic Syntax

[Back](#leetcode-java-语法默写)

- 基本语法:

  ```java
  // and or not True False

  && || ! true false

  // if / while / for

  if (condition) {} else if (condition) {}
  while (condition) {}
  for (int i = 0; i < 10; i++) {}

  // 深拷贝？
  // a = b[:]

  Object b = a.clone();

  // 长度：int[] arr

  arr.length

  // 长度：String

  str.length()

  // 长度：集合 Collections

  list.size()

  // 输出
  // Java 会自动调用 toString()

  System.out.println(Arrays.toString(arr));
  System.out.println(Arrays.deepToString(arr));
  System.out.println(arrayList);

  // 正常除法：3 / 2

  double a = 3 * 1.0 / 2;

  // 向下取整：3 // 2

  Math.floor(3 * 1.0 / 2);

  // 截尾除法/向零截断：int(3 / 2)

  int a = 3 / 2;

  // 四舍五入：round(a / b) 并不一样！是 +0.5 向下取整

  Math.round(3 * 1.0 / 2)

  // ','.join(arr)

  StringBuilder sb = new StringBuilder();
  for (int i : arr) {
      if (sb.length() > 0) {
          sb.append(",");
      }
      sb.append(i);
  }
  String s = sb.toString();

  // string -> int/long/double

  int i = Integer.parseInt(s);
  int i = Integer.parseInt(ch + "");
  long i = Integer.parseLong(s);
  double i = Double.parseDouble(s);

  // String - char[]

  char[] list_ch = s.toCharArray();

  // char[] - String

  String s = new String(list_ch);

  // ord()

  System.out.println(ch - 'a');

  // chr()
  
  System.out.println((char) myInt); // 直接强转

  // Float Double Byte Character Short Integer Long
  // 最大最小值, 若溢出, 可以/2

  int numMax = Integer.MAX_VALUE; // 2^31 - 1
  int numMin = Integer.MIN_VALUE;

  // 溢出问题, c = a + b
  
  long c = (long) a + b;
  
  // left = stack[-1] if stack else -1

  int left = stack.isEmpty() ? -1 : stack.peek();
  ```

- Math:

  ```java

  // max(a, b)

  Math.max(a, b);

  // min(a, b)

  Math.min(a, b);

  // a ** b

  Math.pow(a, 2);

  // sqrt(a)

  Math.sqrt(a);

  // random.random()
  
  Math.random(); 
  ```

### String

[Back](#leetcode-java-语法默写)

- String:

  ```java

  // s = 'aaa';

  String s = "asdefgasdefg";

  // string -> char[]

  char[] cs = s.toCharArray();

  // char[] -> String

  String s = new String(list_ch);

  // s1 == s2

  s.equals(s2); // == 引用类型，判断的是地址

  // s[0]

  s.charAt((int)index);

  // len(s)

  s.length();

  // 遍历

  for (int i = 0; i < s.length(); i++) {
    char c = s.charAt(i);
  }

  // list_s = s.split(' ')

  String[] list_s = s.split(" ");

  // s[0:2]

  String s = s.substring((int)start, (int)end) //[start,end)

  // ''.join(list_s) -> 建议直接用 StringBuilder

  String s = String.join(",", list_s);
  ```

- StringBuilder: 可变长字符串: list_s = list(s)

  ```java

  // StringBuilder 定义

  StringBuilder sb = new StringBuilder("String");

  // 遍历

  for (int i = 0; i < sb.length(); i++) {sb.charAt(i);}

  // s.append('a')

  sb.append("");

  // s[0]

  sb.charAt((int)index);

  // len(s)

  sb.length();

  // s[::-1]

  sb.reverse();

  // 转成 String

  sb.toString();

  // s[1] = 'a'

  sb.setCharAt((int)index, (char)c);

  // ','.join(arr)

  StringBuilder sb = new StringBuilder();
  for (int i : arr) {
      if (sb.length() > 0) {
          sb.append(",");
      }
      sb.append(i);
  }
  String s = sb.toString();
  ```

### List: 基础数组

[Back](#leetcode-java-语法默写)

```java

// res = [0 for _ in range(n)]

int[] arr = new int[100];
int[] arr = {1, 2, 3, 4};
int[][] arr = {{1, 2}, {3, 4}};

// len(a)

int len = arr.length;

// a.sort()

Arrays.sort(arr);

// int[] <-> List<Integer>

List<Integer> list = new ArrayList<>(Arrays.asList(arr));
Integer[] arr = list.toArray(new Integer[0]);

// a[1:3]，深拷贝仅限一维，二维/对象都不行

String[] c = Arrays.copyOfRange(a, 1, 4); // [start,to)

// reverse: a[::-1]
// 没办法的，手动双指针 reverse 吧

// print

System.out.println(Arrays.toString(arr));

// 填充，初始化
// a = [1 for _ in range(n)]

Arrays.fill(a, "fill");
```

### Collections: 数组，队列，栈，双端队列

[Back](#leetcode-java-语法默写)

```java

// if list

list.isEmpty();

// len(list)

list.size();

// list = list[::-1]

Collections.reverse(list);

// list.sort()

Collections.sort(list, Collections.reverseOrder());
list.sort((a, b) -> (b - a));

// bisect.bisect_left(arr, target)

// find: id >= 0, insert: -id - 1
Collections.binarySearch(arr, target);
```

### ArrayList: 动态数组

[Back](#leetcode-java-语法默写)

```java

// 初始化 一维

List<Integer> list = new ArrayList<>();
List<Integer> list = new ArrayList<>(Arrays.asList(a, b, c));

// 初始化 二维
List<List<Integer>> res = new ArrayList<>();
res.add(new ArrayList<>());
res.add(new ArrayList<>());

// list.append(1)

list.add(1);
list.addAll(list2);

// list[0]

list.get(index);

// list[0] = 1

list.set(index, Integer);

// list.index(1)

list.indexOf(Integer);

// if list

list.isEmpty();

// list[2:4]

list.subList(int start,int end); // [start,end);

// ArrayList -> Set

Set<Integer> set = new HashSet<>(arrayList);
```

### Queue

[Back](#leetcode-java-语法默写)

```java

// 初始化

Queue<Integer> queue = new LinkedList<>(); // 可放null，但别放

// append / popleft / [-1]

queue.offer(1); // 添加，失败，返回 false
queue.poll(); // 删除，若为空，返回 null
queue.peek(); // 获取，不删除
```

### Stack

[Back](#leetcode-java-语法默写)

```java

// 初始化

Deque<Integer> stack = new LinkedList<>();

// append / pop / [-1]

stack.push(1);
stack.pop();
stack.peek();
```

### Deque

[Back](#leetcode-java-语法默写)

```java

// 初始化

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

[Back](#leetcode-java-语法默写)

```java

// 小顶堆

PriorityQueue<Integer> pq = new PriorityQueue<>();

// 大顶堆

PriorityQueue<Integer> pq = new PriorityQueue<>((a, b) -> b - a);

// append, pop, heap[0]

pq.offer(Integer); // 添加
pq.poll(); // 删除
pq.peek(); // 获取，不删除

// 放tuple?
// a[0] ↑，a[1] ↓

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

[Back](#leetcode-java-语法默写)

- HashSet:

  ```java

  // 初始化

  HashSet<String> set = new HashSet<>();

  // int[] -> Set 初始化

  HashSet<String> set = new HashSet<>(Arrays.asList(arr));

  // add

  set.add();

  // a in set

  set.contains();

  // remove

  set.remove();

  // Set -> ArrayList

  List<Integer> list = new ArrayList<>(set);
  ```

### Map

[Back](#leetcode-java-语法默写)

- HashMap: 允许 key，value 为 null

  ```java

  // 初始化

  HashMap<Integer, Integer> map = new HashMap<>()；

  // map[0] = 1

  map.put(key, value);

  // a = map[0]

  map.get(key);

  // a in map

  map.containsKey(key);

  // if not map

  map.isEmpty();

  // len(map)
  
  map.size();

  //遍历
  //按键遍历

  for (int key: map.keySet())

  //按值遍历

  for (int value: map.values())

  //按照Value升序排序
  //可以把 map.values() 转换为 list 排序再 sort

  Map<Integer,Integer> map = new HashMap<>()
  List<Map.Entry<Integer,Integer>> list = new ArrayList<>(map.entrySet());
  Collections.sort(list, (o1,o2)->o1.getValue()-o2.getValue());
  ```

### Bit Manipulation

[Back](#leetcode-java-语法默写)

```java

// 与

a & b;

// 异或

a ^ b;

// 或

a | b;

// 左移

1 << a;

// 右移

1 >> a;

```
