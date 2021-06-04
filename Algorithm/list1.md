# 리스트 1. LinkedList 뒤집기

### 출제 의도

- LinkedList 구조를 이해하고 있는가?
- 재귀로도 생각할 수 있는가?

**배운점**

- 재귀 순한맛

### 문제. 
#### 정렬된 연결 리스트에서 중복가 노드를 제거하는 함수를 구현하라.

예) 1 -> 1 -> 1 -> 2 -> 3 -> 3   =>   1 -> 2 -> 3

### 풀이

1. **일반 순회**

    ```java
    // 시간복잡도 : O(N)
    // 공간복잡도 : O(N)
    private void reverse1(){
            LinkedNode current =  this.head;
            LinkedNode next = null;
            LinkedNode prev = null;

    				
            // 뒤집는 코드
            while(current != null){
                next  = current.next;
                current.next = prev;
                prev = current;
                current = next;
            }
            
            // 다 뒤집었으면 클래스에 디폴드로 있는 head tail도 바꿔주자.
            this.tail = this.head;
            this.head = prev;
        }
    ```

2. **재귀 사용**
    - 재귀로 처리하는 방법 (1 → 2 → 3값있는 LinkedList를 생각해보자)
    - (1) 3 → 1  을 보게하기
    - (2)  위에게 무한루프가 안되게 끊어 주기

    ```java
    // 시간복잡도 : O(n)  
    // 공간복잡도 : O(n)
    pprivate void reverse1(){
            LinkedNode head = this.head;
            this.tail = this.head;
            this.head = recursive1(head);
        }

        private LinkedNode recursive1(LinkedNode node){
            if(node.next == null){
                return node;
            }
            LinkedNode newHead  = recursive(node.next);
    				
            node.next.next = node;     //(1) 3 → 1  을 보게하기 
            node.next = null;          //(2) 위에게 무한루프가 안되게 끊어 주기 

            return newHead;
        }
    ```

### 테스트 해보기 (전체 코드)

```python
public class LinkedList {

    private LinkedNode head;
    private LinkedNode tail;

    public static void main(String[] args) {
        LinkedList list = new LinkedList();
        list.add(new LinkedNode(1));
        list.add(new LinkedNode(2));
        list.add(new LinkedNode(3));

        list.print();
        list.reverse();
        //list.reverse1();

        list.print();
    }

    /**
     * TODO 단일 연결 리스트를 뒤집는 함수를 구현하라.
     *  예) 1 -> 2 -> 3   =>   3 -> 2 -> 1
     * @return
     */
    private void reverse(){
        LinkedNode current =  this.head;
        LinkedNode next = null;
        LinkedNode prev = null;

        // 뒤집는 코드
        while(current != null){
            next  = current.next;
            current.next = prev;
            prev = current;
            current = next;
        }
        
        // 다 뒤집었으면 클래스에 디폴드로 있는 head tail도 바꿔주자.
        this.tail = this.head;
        this.head = prev;
    }

    private void reverse1(){
        LinkedNode head = this.head;
        this.tail = this.head;
        this.head = recursive1(head);
    }

    private LinkedNode recursive1(LinkedNode node){
        if(node.next == null){
            return node;
        }
        LinkedNode newHead  = recursive1(node.next);
        node.next.next = node;
        node.next = null;

        return newHead;
    }
}

// Linked List 기능들 
    public void print() {
        LinkedNode nodeToPrint = this.head;
        while(nodeToPrint != null) {
            System.out.println(nodeToPrint.number);
            nodeToPrint = nodeToPrint.next;
        }
    }

    public void add(LinkedNode node) {
        if (head == null) {
            head = node;
            tail = node;
        } else if (tail != null) {
            tail.next = node;
            tail = tail.next;
        }
    }
    public String toString(){

        StringBuilder sb = new StringBuilder();

        // node가 없는 경우
        if(head == null){
            return "[]";
        }
        // 탐색을 시작
        LinkedNode temp = head;
        String str = "[";
        // 다음 노드가 없을 때까지 반복문을 실행합니다.
        // 마지막노드는 다음 노드가 없기 때문에 아래의 구문은 마지막 노드는 제와
        while (temp.next != null){
            str += sb.append(temp.number).append(",");
            temp = temp.next;
        }
        // 마지막 노드를 포함시킨다.
        str += temp.number;
        return str + "]";
    }
```
