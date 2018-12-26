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

2. HashSet
- Set<Character> set = new HashSet<>();
- add() / remove()
- contains()
- isEmpty()
- clear() remove all contents

3. queue
- Queue<Integer> neigh = new LinkedList<>();
- add()
- peek() get from front not remove
- remove() remove from front

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

9. substring
s.substring(3, 9) [3,9),not include 9

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
- 没有isEmpty(),用size()判断是否为空
- add / peek(如果empty，return null) / remove(相当于pop)

13. StringBuilder
StringBuilder res = new StringBuilder();
- append()
- reverse()
- .toString()
- charAt()
- length()
- deleteCharAt(index)
- delete(int start, int end) [start, end)

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
