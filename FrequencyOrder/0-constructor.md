## template

\# 904 Fruit into baskets -- medium
##### description:
描述
****************
##### 思路:
思路
time complexity
**********
##### 失误点/难点：
失误
********
##### Code:
```java
//code
```
##### 改进：
改进

*********






## 总结各种structure

1. hashmap
- Map<Integer, Integer> map = new HashMap<>() / Map<Integer, Integer> map = new HashMap<>(capacity) 定义capacity和load factor (可略)
- map.put(key, value);
- map.containsKey(key) / map.containsValue(value);
- map.get(key) / map.getOrDefault(key, default value);
- map.replace(key, value);
- map.values(); 以collections的形式返回所有map里的values ！！！
- keySet()
- size()
- remove(key) / remove(key, value)
- map1.equals(map2) 判断两个hashmap相等

2. HashSet
- Set<Character> set = new HashSet<>();
- Set<String> set = new HashSet<>(Collections<String>); build set with existing Collections
- add() / remove()
- contains()
- isEmpty()
- clear() remove all contents

3. queue
- Queue<Integer> neigh = new LinkedList<>();
- add()
- peek() get from front, not remove
- remove() remove from front
- poll() remove from front, if empty return null
- isEmpty()
- size()

4. stack
- Stack<Character> stack = new Stack<Character>();
- push() / pop() / peek()
- boolean empty()

5. switch
multiple conditions
```
switch(c) {
                case '(':
                case '{':
                case '[':
                    stack.push(c);
                    break;
```

6. if-elseif
- result = ((i1.start < i2.start)? -1 : 1);
- (i1.start < i2.start)? -1: (i1.start == i2.start)? 0 : 1;

7. Comparator
```
//自定义comparator
class IntervalComparator implements Comparator<Interval> {
    public int compare(Interval i1, Interval i2) {
        return (i1.start < i2.start)? -1: (i1.start == i2.start)? 0 : 1;
    }
}

IntervalComparator comparator = new IntervalComparator()

//sort list, do not need to assign to list again
collections.sort(list, comparator);
```
两种comparator initiate 方法
```
Arrays.sort(intervals, new MeetingComparator());
PriorityQueue<Integer> minHeap = new PriorityQueue<>(intervals.length, new Comparator<Integer>() {
    @Override
    public int compare(Integer a, Integer b) {
        return a - b;
    }
});
```

8. List
```
List<Integer> a = new ArrayList<>();
List<Integer> b = new LinkedList<>();
List<Integer> c = new Vector<>();
List<Integer> d = new Stack<>();
```
- get(index)
- add(object)
- add(index, object) 相当于insert
- set(index, value) replace value at index
- remove(index)
- remove(object)
- isEmpty()
- size()
- array to list & list to array
  - Arrays.asList(int[]) return list
  - String[] y = x.toArray(new String[size]);
  - int[] intArr = list.stream().mapToInt(Integer::intValue).toArray();

9. String
- s.substring(3, 9) [3,9),not include 9
- String is immutable, cannot change char at specific index. Use StringBuilder
- str.split();
  - str.split("")有一下特殊符号需要注意
  there are 12 characters with special meanings: the backslash `\`, the caret `^`, the dollar sign `$`, the period or dot `.`, the vertical bar or pipe symbol `|`, the question mark `?`, the asterisk or star  `*`, the plus sign `+`, the opening parenthesis `(`, the closing parenthesis `)`, and the opening square bracket `[`, the opening curly brace `{`, These special characters are often called "metacharacters".
  if you want to split on e.g. period/dot `.` which means "any character" in regex, use either backslash `\` to escape the individual special character like so `split("\\.")`
- indexOf(str/char) 寻找str/char在string中的位置, -1如果不包含这个str or char

10. for each -- java
for (type var: array) {}

11. sort
- Collections.sort()
- Arrays.sort()
- 都可自定义comparator
- 如果要sort为descending order：Arrays.sort(arr, Collections.reverseOrder());但是这个只能用于Integer array,不能用于int array，需要进行int和Integer之间转换,需自己implement
- 只sort array中一部分：Arrays.sort(arr, frontIndex, endIndex); [frontIndex,endIndex)

12. heap
```
PriorityQueue<Object> heap = new PriorityQueue<>();
```
- 本身是minheap
- 如果要自定义comparator，格式：
PriorityQueue<>(initialCapacity, comparator)
- isEmpty()
- size()
- add / peek(如果empty，return null) / remove或者用poll()

13. StringBuilder
StringBuilder res = new StringBuilder();
StringBuilder res = new StringBuilder("string");
- append()
- reverse()
- .toString()
- charAt()
- length()
- deleteCharAt(index)
- delete(int start, int end) [start, end)
- setCharAt(index, char)
- length();
- StringBuilder + StringBuilder 用append：`builder1.append(builder2)`

14. Character, String, Integer互相转换
- charact to ...
  - character array to string:
  new String(array);
  - to int:
   Character.getNumericValue(char);
  - to String:
  String.valueOf(char);
- Integer to ...
  - to String:
    - toString() return integer value as string
    - String.valueOf(int);
- string to ...
  - to int:
Integer.parseInt(str) -- Primitive int (可以直接parse 负数)
Integer.valueOf(str) -- Integer object

15. Array
- int[] array1 = {};
  int[] array2 = array1;
  这样的assign只是获得array1在内存中的地址，并不是hard copy，如果要hard copy可以使用object继承下来的clone
  int[] array2 = array1.clone();
- 将array fill为相同的数val
  Arrays.fill(arr, val);
- Boolean[] 默认fill是null {null,null,null}
boolean[] 默认fill是false {false, false, false}
- copy array一部分内容可以使用：`Arrays.copyOfRange(arr, start, end)` [start, end)

16. == vs equals
== 判断是否为同一个object，包括相同的地址
equals 则只要满足相等判断即可

17. Pair class
- 用Pair class一定要`import javafx.util.*;`
- Pair<String, Integer> p = new Pair<>("a",4);
- getKey/getValue
- equals

18. Integer
- toBinaryString(int i) return the integer as an unsigned integer in base 2
- toHexString(int i) return integer as unsigned integer in base 16
- toOctalString(int i) ... in base of 8

19. random
Random r = new Random();
- nextInt() / nextInt(int bound) bound is exclusice
- nextBoolean()
- nextDouble()...

20. Character判断
- Character.isDigit(char)
- Character.isLetter(char)
- Character.isLowerCase(char)
- Character.isUpperCase(char)
- Character.toLowerCase(char)
- Character.toUpperCase(char)

21. constant variable
- static final int DAYS_IN_WEEK = 7;

22. [regular expression](http://www.vogella.com/tutorials/JavaRegularExpressions/article.html)
[regular expression 2](http://tutorials.jenkov.com/java-regex/pattern.html)

23. array default:
- For type byte, the default value is zero, that is, the value of (byte)0.
- For type short, the default value is zero, that is, the value of (short)0.
- For type int, the default value is zero, that is, 0.
- For type long, the default value is zero, that is, 0L.
- For type float, the default value is positive zero, that is, 0.0f.
- For type double, the default value is positive zero, that is, 0.0d.
- For type char, the default value is the null character, that is, '\u0000'.
- For type boolean, the default value is false.
- For all reference types (§4.3), the default value is null. (like string, object)
