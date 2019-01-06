## template

\# 904 Fruit into baskets -- medium
##### description:
描述
****************
##### 思路:
思路
time complexity
**********
##### 失误点：
失误
********
##### Code:
```
code
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
- remove()

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
- add()
- set(index, value) replace value at index
- remove(index)
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

14. Character
- character array to string: new String(array);
- character to int: Character.getNumericValue(char);

15. Array
- int[] array1 = {};
  int[] array2 = array1;
  这样的assign只是获得array1在内存中的地址，并不是hard copy，如果要copy可以使用object继承下来的clone
  int[] array2 = array1.clone();
- 将array fill为相同的数val
  Arrays.fill(arr, val);
- Boolean[] 默认fill是null {null,null,null}
boolean[] 默认fill是false {false, false, false}

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
- toString() return integer value as string
- character to int: Character.getNumericValue(char);
- string to int:
Integer.parseInt(str) -- Primitive int / Integer.valueOf(str) -- Integer object

19. random
Random r = new Random();
- nextInt() / nextInt(int bound) bound is exclusice
- nextBoolean()
- nextDouble()...
