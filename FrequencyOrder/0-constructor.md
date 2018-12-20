### 总结各种structure的constructor

1. hashmap
- Map<Integer, Integer> map = new HashMap<>() / Map<Integer, Integer> map = new HashMap<>(capacity) 定义capacity和load factor (可略)
- map.put(key, value);
- map.containsKey(key) / map.containsValue(value);
- map.get(key) / map.getOrDefault(key, default value);
- map.replace(key, value);

2. HashSet
- Set<Character> set = new HashSet<>();
- add() / remove()

3. queue
- Queue<Integer> neigh = new LinkedList<>();
- add()
- peek() get from front not remove
- remove() remove from front
