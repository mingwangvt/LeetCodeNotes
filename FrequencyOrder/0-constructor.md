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






## 总结各种structure的constructor

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

6.
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

9. substring
s.substring(3, 9) [3,9),not include 9