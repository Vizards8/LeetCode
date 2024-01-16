## Leetcode for Java

---

- [Leetcode for Java](#leetcode-for-java)
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

---

### Basic Syntax

[Back](#leetcode-for-java)

- 基本语法:

  ```java
  // && || ! true false
  // 正负0: 0.0 = -0.0
  // if / while / for
  if (condition) {} else if (condition) {}
  while (condition) {}
  for (int i = 0; i < 10; i++) {}

  // 深拷贝，Object方法，[:]
  Object b = a.clone();

  // 长度
  int[]: arr.length
  String: str.length()
  StringBuilder: sb.length()
  Collections: list.size()

  // 输出: Java 会自动调用 toString()
  System.out.println(Arrays.toString(arr); // 1D
  System.out.println(Arrays.deepToString(arr); // >= 2D
  System.out.println(arrayList); // 1D & >= 2D

  // 正常除法：3 / 2
  double a = 3 * 1.0 / 2;

  // 向下取整：3 // 2
  Math.floor(3 * 1.0 / 2);

  // 截尾除法/向零截断：int(3 / 2)
  double a = 3 / 2;

  // 四舍五入：round(a / b) 并不一样！
  Math.round(3 * 1.0 / 2)

  // String[] - String
  String s = String.join(",", list_s);

  // string -> int/long/double
  int i = Integer.parseInt(s);
  int i = Integer.parseInt(ch + "");
  long i = Integer.parseLong(s);
  double i = Double.parseDouble(s);

  // String - char[]
  char[] list_ch = s.toCharArray();

  // ord()
  System.out.println(ch - 'a');

  // Float Double Byte Character Short Integer Long
  // 最大最小值, 若溢出, 可以/2
  // 32位整数，最高位是符号位
  int numMax = Integer.MAX_VALUE; // 2^31 - 1
  int numMin = Integer.MIN_VALUE; // -2^31

  // left = stack[-1] if stack else -1
  int left = stack.isEmpty() ? -1 : stack.peek();
  ```

- Math:

  ```java
  Math.max(a, b);
  Math.min(a, b);

  Math.floor(a); // ≤
  Math.ceil(a); // ≥

  (int) Math.pow(a, 2);
  Math.sqrt(a);

  Math.random(); // random.random() [0, 1) double
  ```

  - GCD

  ```java
  public int gcd(int a, int b) {
    int temp;
    while (b != 0) {
      temp = a % b;
      a = b;
      b = temp;
    }
    return a;
  }
  ```

### String

[Back](#leetcode-for-java)

- Comparison:

  - StringBuilder 处理速度快但不是线程安全的
  - StringBuffer 处理速度比 Builder 慢但是线程安全
  - String 是字符串常量，因此处理速度最慢

- String:

  ```java
  String s = "asdefgasdefg";

  // 常用
  char[] cs = s.toCharArray();
  "abcd".equals(s2); // == 引用类型，判断的是地址
  s.charAt((int)index);
  s.indexOf('s');
  s.length();
  String[] list_s = s.split(" ");
  String s = String.join(",", list_s);
  String s = s.substring((int)start, (int)end) //[start,end)

  // 遍历
  for (char c : s.toCharArray()) {}
  for (int i = 0; i < s.length(); i++) {
    char c = s.charAt(i);
  }

  // string -> int/long/double
  int i = Integer.parseInt(s);
  int i = Integer.parseInt(ch + "");
  long i = Integer.parseLong(s);
  double i = Double.parseDouble(s);

  // API
  String s = s.toLowerCase();
  String s = s.toUpperCase();
  String s = s.trim();
  ```

- StringBuilder: 可变长字符串

  ```java
  StringBuilder sb = new StringBuilder("String");
  sb.append(String/char);
  sb.charAt((int)index);
  sb.length();
  sb.reverse();
  sb.delete((int)start, (int)end); // [start,end)
  sb.toString();
  sb.setCharAt((int)index, (char)c);

  // 遍历
  for (int i = 0; i < sb.length(); i++) {sb.charAt(i);}

  // Python: ().join(arr)
  // 直接用 StringBuilder，最后 toString
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

[Back](#leetcode-for-java)

```java
// res = [0 for _ in range(n)]
int[] arr = new int[100];
int[] arr = {1, 2, 3, 4};

// len(arr)
int len = arr.length;

// arr.sort()
Arrays.sort(arr);

// 深拷贝
int[] b = arr.clone();

// 切片
String[] c = Arrays.copyOfRange(a, 1, 4); // [start,to)

// reverse: a[::-1]
// 没办法的，手动双指针 reverse 吧

// print
System.out.println(Arrays.toString(arr));
System.out.println(Arrays.deepToString(arr));

// int[] <-> List<Integer>
// 记不住的话，不如一个个放进去
Integer[] arr = {1, 2, 3};
List<Integer> list = new ArrayList<>(Arrays.asList(arr));
Integer[] arr2 = list.toArray(new Integer[list.size()]);

// 填充，初始化
Arrays.fill(a, "fill");
```

### Collections

[Back](#leetcode-for-java)

```java
list.isEmpty();
list.size();
Collections.reverse(list);
Collections.sort(list, Collections.reverseOrder());
list.sort((a, b) -> (b - a));
```

### ArrayList: 动态数组

[Back](#leetcode-for-java)

```java
List<Integer> list = new ArrayList<>();
List<Integer> list = new ArrayList<>(Arrays.asList(a, b, c));
list.add((int)index, Object o);
list.addAll(list2);
list.get(index);
list.set(index, Integer);
list.remove(index);
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
```

### Queue

[Back](#leetcode-for-java)

```java
Queue<Integer> queue = new LinkedList<>(); // 可放null，但别放
queue.offer(1); // 添加，失败，返回 false
queue.poll(); // 删除，若为空，返回 null
queue.peek(); // 获取，不删除
```

### Stack

[Back](#leetcode-for-java)

```java
Stack<Integer> stack = new Stack<>();
stack.push(1);
stack.pop();
stack.peek();
```

### Deque

[Back](#leetcode-for-java)

```java
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

[Back](#leetcode-for-java)

```java
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

[Back](#leetcode-for-java)

- HashSet:
  ```java
  Set<String> set = new HashSet<>();
  Set<String> set = new HashSet<>(Arrays.asList(arr));
  set.add();
  set.contains();
  set.remove();
  ```
- TreeSet: Sorted
  ```java
  Set<String> set = new TreeSet<>((o1,o2)->o2-o1);
  ```

### Map

[Back](#leetcode-for-java)

- HashMap: 允许 key，value 为 null

  ```java
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

  ```java
  //按照 Key 降序排序
  Map<Integer,Integer> map = new TreeMap<>((o1,o2)->o2-o1);

  //按照 Value 升序排序：可以把 map.values() 转换为 list 排序再 sort
  Map<Integer,Integer> map = new HashMap<>()
  List<Map.Entry<Integer,Integer>> list = new ArrayList<>(map.entrySet());
  Collections.sort(list, (o1,o2)->o1.getValue()-o2.getValue());
  ```

### Bit Manipulation

[Back](#leetcode-for-java)

```java
// 和python一样
a & b; // 与
a ^ b; // 异或
a | b; // 或
1 << a; // 左移
1 >> a; // 右移
```
