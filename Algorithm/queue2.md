# 큐 2. LRU캐시를 구현하라.

### 출제 의도

- LRU 캐시 개념을 알고 있거나 이해할 수 있는가?
- LRU 오퍼레이션을 효율적으로 구현할 수 있는가?
- Queue와 HashSet 또는 HashMap을 활용할 수 있는가?

### 문제. 
LRU 캐시를 구현하라.

최대 n개 만큼의 가장 최근에 접근한 데이터를 캐싱하는 LRU (least recently used) 캐시를
구현하라.
입력값 number는 1부터 100까지의 숫자가 랜덤하게 입력된다. 
그 중에 최대 n (1보다 크고 9보다 작은)개 만큼의 데이터만 캐시할 수 있다. 

n개를 넘는 새로운 값이 들어오면 그 중에서
가장 오래전에 접근한 데이터를 삭제하고 number를 캐시에 추가한다.

다음 오퍼레이션을 구현하라.
● query(int number): number에 해당하는 입력값을 캐시에 추가한다.
● print() 현재 캐시하고 있는 데이터를 출력한다.

```java
// 테스트를 위한 Main메서드
public static void main(String[] args) {
        LRUCache lruCache = new LRUCache(3);
        lruCache.query(1);
        lruCache.query(2);
        lruCache.query(3);
        lruCache.query(1);
        lruCache.query(4);
        lruCache.query(5);
        lruCache.query(2);
        lruCache.query(2);
        lruCache.query(1);
        lruCache.print();
    }
```

### 풀이

**방법1** 

```java
// 시간 복잡도 O(n)
// 공간 복잡도 O(n)
private int cacheSize;
    private Deque<Integer> cache;

    public LRUCache(int cacheSize) {
        this.cacheSize = cacheSize;
        cache = new LinkedList<>();
    }
    

		// 기능 로직
    private void query(int number) {
        if(!cache.contains(number)){
            if(cache.size() == this.cacheSize){
                cache.removeLast();
            }
            cache.addFirst(number);
        }else{
            cache.remove(number);
            cache.addFirst(number);
        }
    }

    private void print() {
        System.out.println(cache);
    }
```

**방법2. 복잡도를 O(1)로 만드는 방법**

- 양방향 LinkedList와 HashMap을 이용해 O(1)의 복잡도를 구현한다.

```java
public class LRUCacheSolution2 {
	
    private int cacheSize;

    private HashMap<Integer, Node> map;
	
    private Node head, tail;

    public LRUCacheSolution2(int cacheSize) {
        this.cacheSize = cacheSize;
        this.map = new HashMap<>();
    }

    class Node<E> {
        E value;
        Node<E> next;
        Node<E> prev;
    }

    private void query(int number) {
        if (map.containsKey(number)) {
            Node node = map.get(number);
            remove(node);
            addToHead(node);
        } else {
            Node nodeToAdd = new Node();
            nodeToAdd.value = number;
            if (map.size() == this.cacheSize) {
                map.remove(tail.value);
                remove(tail);
            }
            addToHead(nodeToAdd);
            map.put(number, nodeToAdd);
        }
    }

    private void remove(Node node) {
        if (node.prev != null) {
            node.prev.next = node.next;
        } else {
            head = node.next;
        }

        if (node.next != null) {
            node.next.prev = node.prev;
        } else {
            tail = node.prev;
        }
    }

    private void addToHead(Node node) {
        node.next = head;
        node.prev = null;

        if (head != null) {
            head.prev = node;
        }

        head = node;

        if (tail == null) {
            tail = head;
        }
    }

    private void print() {
        Node current = this.head;
        while(current != null) {
            System.out.println(current.value);
            current = current.next;
        }
    }

}
```