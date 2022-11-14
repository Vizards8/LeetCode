## Leetcode for Java

***
- [Leetcode for Java](#leetcode-for-java)
  - [Basic Syntax](#basic-syntax)
  - [String](#string)
  - [List: 基础数组](#list-基础数组)
  - [Stack](#stack)
  - [Queue](#queue)
  - [ArrayList: 动态数组](#arraylist-动态数组)
  - [Deque](#deque)
  - [PriorityQueue: heap](#priorityqueue-heap)
  - [Set](#set)
  - [Map](#map)
***

### Basic Syntax
[Back](#leetcode-for-java)

* 最大最小值, 若溢出, 可以/2
    ```java
    // Float Double Byte Character Short Integer Long
    int numMax = Integer.MAX_VALUE;
    int numMin = Integer.MIN_VALUE;
    ```

* String - Integer && Integer - String
  ```java
  int i = 1;
  String a = Integer.toString(i);
  
  String a = "1";
  int i = Integer.parseInt(a);
  long i = Integer.parseLong(a);
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
  for(int i = 0; i < s.length(); i++){
    char c = s.charAt(i);
  }
  s.indexOf('s') //retrun 1
  s.indexof('s',2) //return 7
  s.lastIndexOf('s') //return 7
  s.lastIndexOf('s',6) //return 1
  string[] ss = s.split("regex");
  String s = s.substring((int)start, (int)end) //[start,end)
  char[] cs = s.toCharArray();
  String s = s.toLowerCase();
  String s = s.toUpperCase();
  String s = s.trim(); 
  String s = String.valueOf(object);
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
Arrays.sort(arr);
Arrays.sort(arr, (int) start,(int) to);

// 与list转换  List<Integer> 和 int[] 因类型不同不可直接转换
List<String> list = Arrays.asList(a);
String[] b = (String[]) list.toArray(new String[size]);

// 深拷贝
int[] b = arr.clone();

// 切片 & 输出
String[] c = Arrays.copyOfRange(a, 1, 4); // [start,to)
System.out.println(Arrays.toString(c))

// 填充
Arrays.fill(a, "fill");
Arrays.fill(a, (int) start,(int) to, "fill");
```

### Stack
[Back](#leetcode-for-java)

```java
Stack<Object> stack = new Stack<>();
stack.pop();
stack.peek();
stack.push(Object o);
```

### Queue
[Back](#leetcode-for-java)

```java
Queue<Object> queue = new LinkedList<>();
queue.offer(Object o);
queue.peek();
queue.poll();
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

* Deque:
  ```java
  Deque<Integer> deque = new LinkedList<>();
  //添加元素到队首/队尾
  deque.addFirst(1);
  deque.offerFirst(1);
  deque.addLast(1);
  deque.offerLast(1);
  //取队首/队尾元素并删除
  deque.removeFirst();
  deque.pollFirst();
  deque.removeLast();
  deque.pollLast();
  //取队首/队尾元素不删除
  deque.peekFirst();
  deque.getFirst();
  deque.peekLast();
  deque.getLast();
  ```

* LinkedList:
  ```java
  LinkedList<Integer> num = new LinkedList<Integer>();
  num.add(index);
  num.remove(index);
  num.isEmpty();
  //通过对链表头尾操作可同时当stack和queue (初始化必须用LinkedList而不是List)
  num.addFirst(Integer);
  num.addLast(Integer);
  num.getFirst();
  num.getLast();
  num.offer();
  num.offerFirst(Integer);
  num.offerLast(Integer);
  num.removeLast();
  ```

### PriorityQueue: heap
[Back](#leetcode-for-java)
```java
PriorityQueue<Integer> pq = new PriorityQueue<>(); 

//改为大顶堆
PriorityQueue<Integer> pq = new PriorityQueue<>(new Comparator<Integer>(){
    @Override
    public int compare(Integer i1, Integer i2){
        return i2-i1;
    }
}); 
//简化写法（匿名Lambda表达式）
Queue<Integer> pq = new PriorityQueue<>((n1,n2)->n2-n1); 

pq.add(Integer);
pq.offer(Integer);
pq.poll();
pq.remove()
```

### Set
[Back](#leetcode-for-java)

* HashSet:
  ```java
  Set<String> set = new HashSet<String>();
  set.add();
  set.contains();
  set.remove();
  ```
* TreeSet: Sorted
  ```java
  Set set = new HashSet((o1,o2)->o2-o1);
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
  map.keySet();
  map.values();
  map.size();
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