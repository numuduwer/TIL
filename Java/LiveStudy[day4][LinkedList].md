# 목표 
LinkedList를 구현하세요 
# 학습할 것
- 정수를 저장하는 ListNode클래스를 구현하세요
- ListNode add(ListNode head, ListNode nodetoadd, int position)를 구현하세요
- ListNode remove(ListNode head, int positionToRenove)를 구현하세요 
- bollean contains(ListNode head, ListNode nodeTocheck)를 구현하세요


# Linked List
- 앞에 있는 노드들이 뒤에았는 노드를 가리키고 있는 자료구조를 연결리스트라 한다. 
- <strong>노드는 2가지로 구성되어있다.</strong> 
    - Data
    - 다음 노드를 가리키는 next

- <strong>LinkedList는 3가지 구조로 이루어져있다.</strong> 
    - 첫 노드를 가리키는 head
    - 마지막 노드를 가리키는 tail
    - 노드의 수를 가리키는 nodeCount 

- <strong>LinkedList의 연산은 6가지가 있다.</strong>
    1. 조회 
    2. 모든 리스트 순회
    3. 길이 얻어내기
    4. 노드 삽입
    5. 노드 삭제 
    6. 리스트 합치기 


## Node와 LinkedList
~~~java
    class CodeTest{
        public static class LinkedList{
            private Node head;
            private Node tail;
            private int size =0;

            public Node(Object input){
                this.data = input;
                this.next = null;
            }
        }

    }
~~~
## 6가지 연산
###  <strong>삽입 </strong>
1. addFirst
2. addLast
3. addd 

###  1. addFirst 
- 앞에서 추가하기
~~~java
    public void addFirst(Object input){
        // 노드를 생성합니다.
        Node newNode = new Node(input);
        // 새로운 노드의 다음 노드로 해드를 지정합니다.
        newNode.next = head;
        // 헤드로 새로운 노드를 지정합니다.
        head = newNode;
        size++;
        if(head.next == null){
            tail = head;
        }
    }
~~~

### 2. addLast
- 값을 뒤로 추가하기
~~~java
    public void addLast(Object input){
        // 노드를 생성합니다.
        Node newNode = new Node(input);
        // 리스트의 노드가 없다면 첫번째 노드를 추가하는 메소드를 사용합니다.
        if(size == 0){
            addFirst(input);
        } else {
            // 마지막 노드의 다음 노드로 생성한 노드를 지정합니다.
            tail.next = newNode;
            // 마지막 노드를 갱신합니다.
            tail = newNode;
            // 엘리먼트의 개수를 1 증가 시킵니다.
            size++;
        }
    }
~~~

### 3. add
- 값을 중간에 추가하기 

~~~java
   public void add(int k, Object input){
        // 만약 k가 0이라면 첫번째 노드에 추가하는 것이기 때문에 addFirst를 사용합니다.
        if(k == 0){
            addFirst(input);
        } else {
            Node temp1 = node(k-1);
            // k 번째 노드를 temp2로 지정합니다.
            Node temp2 = temp1.next;
            // 새로운 노드를 생성합니다.
            Node newNode = new Node(input);
            // temp1의 다음 노드로 새로운 노드를 지정합니다.
            temp1.next = newNode;
            // 새로운 노드의 다음 노드로 temp2를 지정합니다.
            newNode.next = temp2;
            size++;
            // 새로운 노드의 다음 노드가 없다면 새로운 노드가 마지막 노드이기 때문에 tail로 지정합니다.
            if(newNode.next == null){
                tail = newNode;
            }
        }
    }
~~~


### <strong> 조회 </strong>
1. 특정 노드를 조회 
2. 전체 조회 
### 1. 특정 노드 조회 
~~~java
Node node(int index) {
    Node x = head;
    for (int i = 0; i < index; i++)
        x = x.next;
    return x;
}
~~~
### 2. 전체 조회 
~~~java
    public String toString() {
        // 노드가 없다면 []를 리턴합니다.
        if(head == null){
            return "[]";
        }       
        // 탐색을 시작합니다.
        Node temp = head;
        String str = "[";
        // 다음 노드가 없을 때까지 반복문을 실행합니다.
        // 마지막 노드는 다음 노드가 없기 때문에 아래의 구문은 마지막 노드는 제외됩니다.
        while(temp.next != null){
            str += temp.data + ",";
            temp = temp.next;
        }
        // 마지막 노드를 출력결과에 포함시킵니다.
        str += temp.data;
        return str+"]";
    }    
~~~