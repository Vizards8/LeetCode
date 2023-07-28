## Leetcode for Java

***
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
***

### Basic Syntax
[Back](#leetcode-for-java)

* 基本语法:
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
    数组: arr.length
    字符串: str.length()
    集合: list.size()

    // 输出
    System.out.println(Arrays.toString(arr));
    System.out.println(queue.toString());

    // Python: 3/2 3//2
    double a = 1.0 * 1 / 2; // 0.5
    int a = (int) Math.ceil(1.0 * 1 / 2);
    double a = 1 / 2; // 0 建议用 ceil
  
    // String[] - String
    String s = String.join(",", list_s);

    // 强转: Python: int() - String / char - int
    int i = Integer.parseInt(s);
    int i = Integer.parseInt(ch + "");
    long i = Integer.parseLong(s);
    long i = Double.parseDouble(s);

    // String - char[]
    char[] list_ch = s.toCharArray();

    // ord()
    System.out.println(ch - 'a');

    // Float Double Byte Character Short Integer Long
    // 最大最小值, 若溢出, 可以/2
    int numMax = Integer.MAX_VALUE; // 2^31 - 1
    int numMin = Integer.MIN_VALUE;
    ```

* Math:
  ```java
  Math.max((int) a, (int) b);
  Math.min((int) a, (int) b);
  
  Math.floor(a); // ≤
  Math.ceil(a); // ≥
  
  Math.pow(a, 2);
  Math.sqrt(a);
  ```
  
  * GCD
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

* Comparison:
  * StringBuilder 处理速度快但不是线程安全的
  * StringBuffer 处理速度比Builder慢但是线程安全
  * String是字符串常量，因此处理速度最慢

* String:
  ```java
  String s = "asdefgasdefg";
  // 常用
  char[] cs = s.toCharArray();
  s.equals(s2); // == 引用类型，判断的是地址
  s.charAt((int)index);
  s.indexOf('s');
  s.length();
  String[] list_s = s.split(" ");
  String s = String.join(",", list_s);
  String s = s.substring((int)start, (int)end) //[start,end)
  // 遍历
  for (char c : s.toCharArray()) {}
  // API
  String s = s.toLowerCase();
  String s = s.toUpperCase();
  String s = s.trim(); 
  ```

* StringBuilder: 可变长字符串
  ```java
  StringBuilder sb = new StringBuilder("String");
  sb.append("");
  sb.charAt((int)index);
  sb.length();
  sb.reverse();
  sb.delete((int)start, (int)end); // [start,end)
  sb.toString();
  sb.setCharAt((int)index, (char)c);

  // Python: ().join(arr) - Any[] - String
  StringBuilder sb = new StringBuilder();
  for (int i: arr) {
    sb.append(i);
    sb.append(",");
  }
  String s = sb.toString();
  ```


### List: 基础数组
[Back](#leetcode-for-java)

```java
int[] arr = new String[100];
int[] arr = {1, 2, 3, 4};
int len = arr.length;
Arrays.sort(arr);
Arrays.sort(arr, (int) start,(int) to);

// int[] <-> List<Integer>
List<Integer> list = Arrays.asList(arr);
int[] arr = list.toArray();

// 深拷贝
int[] b = arr.clone();

// 切片
String[] c = Arrays.copyOfRange(a, 1, 4); // [start,to)

// 填充，初始化
Arrays.fill(a, "fill");
```

### Collections
[Back](#leetcode-for-java)
```java
list.isEmpty();
list.size();
list.toArray();
Collections.reverse(list);
Collections.sort(list, Collections.reverseOrder());
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
```

### Queue
[Back](#leetcode-for-java)

```java
Deque<Integer> deque = new LinkedList<>(); // 可放null，但别放
queue.offer(1); // 添加，失败，返回 false
queue.poll(); // 删除，若为空，返回 null
queue.peek(); // 获取，不删除
```

### Stack
[Back](#leetcode-for-java)
```java
Deque<Integer> stack = new LinkedList<>(); // 可放null，但别放
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
PriorityQueue<Integer> pq = new PriorityQueue<>(Collections.reverseOrder());

pq.offer(Integer); // 添加
pq.poll(); // 删除
pq.peek(); // 获取，不删除
pq.remove(Object); // 删除指定元素
```

### Set
[Back](#leetcode-for-java)

* HashSet:
  ```java
  Set<String> set = new HashSet<>();
  set.add();
  set.contains();
  set.remove();
  ```
* TreeSet: Sorted
  ```java
  Set<String> set = new TreeSet<>((o1,o2)->o2-o1);
  ```

### Map
[Back](#leetcode-for-java)

* HashMap: 允许key，value为null
  ```java
  Map<Integer, Integer> map = new HashMap<>()
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

* TreeMap
  ```java
  //按照Key降序排序
  Map<Integer,Integer> map = new TreeMap<>((o1,o2)->o2-o1);

  //按照Value升序排序：可以把map.values()转换为list排序再sort
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
```