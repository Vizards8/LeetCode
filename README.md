## Leetcode for Java

***
- [Leetcode for Java](#leetcode-for-java)
  - [Basic Syntax](#basic-syntax)
  - [String](#string)
  - [List: 基础数组](#list-基础数组)
  - [Collections](#collections)
  - [ArrayList: 动态数组](#arraylist-动态数组)
  - [Deque](#deque)
  - [PriorityQueue: heap](#priorityqueue-heap)
  - [Set](#set)
  - [Map](#map)
***

### Basic Syntax
[Back](#leetcode-for-java)

* 基本语法:
    ```java
    // && || !
    // if / while / for
    if (condition) {} else {}
    while (condition) {}
    for (int i = 0; i < 10; i++) {}

    // 深拷贝，Object方法
    Object b = a.clone();

    // Float Double Byte Character Short Integer Long
    // 最大最小值, 若溢出, 可以/2
    int numMax = Integer.MAX_VALUE;
    int numMin = Integer.MIN_VALUE;

    // 输出
    System.out.println(Arrays.toString(arr));
    System.out.println(queue.toString());

    // Python: 3/2 3//2
    double a = 1.0 * 1 / 2; // 0.5
    int a = (int) Math.ceil(1.0 * 1 / 2);
    double a = 1 / 2; // 0 建议用 ceil
    ```

* String - Integer && Integer - String
  ```java
  int i = 1;
  String a = Integer.toString(i);
  
  String a = "1";
  int i = Integer.parseInt(a);
  long i = Integer.parseLong(a);
  ```

* String - Character && Character - String
  ```java
  String s = "abc";
  char[] cs = s.toCharArray();
  // ().join(arr)
  char[] arr = {'a', 'b', 'c'};
  String s = String.valueOf(arr);
  ```

* Chacter - Integer && Integer - Chacter
  ```java
  int i = 1;
  char a = (char) (i + '0');
  
  char a = '1';
  int i = a - '0';
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
  s.indexOf('s');
  s.split(" ");
  s.length();
  String s = s.substring((int)start, (int)end) //[start,end)
  char[] cs = s.toCharArray();
  String s = s.toLowerCase();
  String s = s.toUpperCase();
  String s = s.trim(); 
  // 遍历
  for(int i = 0; i < s.length(); i++){
    char c = s.charAt(i);
  }
  ```

* StringBuilder:
  ```java
  StringBuilder sb = new StringBuilder("String");
  sb.append("");
  sb.reverse();
  sb.delete((int)start,(int)end); // [start,end)
  sb.deleteCharAt(int index);
  sb.insert((int)offset,"String");
  sb.toString();
  sb.setCharAt((int)index,(char)c);
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

// 切片 & 输出
String[] c = Arrays.copyOfRange(a, 1, 4); // [start,to)
System.out.println(Arrays.toString(c))

// 填充
Arrays.fill(a, "fill");
```

### Collections
[Back](#leetcode-for-java)
```java
list.isEmpty();
list.size();
list.toArray();
Collections.reverse(list);
Collections.sort(list);
```

### ArrayList: 动态数组
[Back](#leetcode-for-java)

```java
List<Integer> list = new ArrayList<>();
List<Integer> list = new ArrayList<>(Arrays.asList(a, b, c));
list.add((int)index, Object o);
list.get(index);
list.set(index, Integer);
list.remove(index);
list.indexOf(Integer);
list.lastIndexOf(Integer);
list.contains(Integer);
list.isEmpty();
list.subList(int start,int end); // [start,end);
```

### Deque
[Back](#leetcode-for-java)

* Deque: Stack / Queue / Deque
  ```java
  Deque<Integer> deque = new ArrayDeque<>();
  List<Integer> deque = new LinkedList<>(); // 可放null
  // append
  deque.addFirst(1);
  deque.addLast(1);
  // pop
  deque.removeFirst();
  deque.removeLast();
  // 获取，不删除
  deque.getFirst();
  deque.getLast();
  ```

### PriorityQueue: heap
[Back](#leetcode-for-java)
```java
// 默认小顶堆
PriorityQueue<Integer> pq = new PriorityQueue<>(); 

pq.add(Integer); // 添加
pq.peek(); // 获取，不删除
pq.poll(); // 删除
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
