# 리스트 3. 중복 노드 지우기

### 출제 의도

- 재귀도 사용할 수있는가?

### 문제. 
#### 정렬된 연결 리스트에서 중복가 노드를 제거하는 함수를 구현하라.

예) 1 -> 1 -> 1 -> 2 -> 3 -> 3 => 1 -> 2 -> 3

### 풀이

1. **일반**

    ```java
    // 시간복잡도 : O(N^2)
    // 공간복잡도 : O(1)
    private void removeDuplicates1() {
            LinkedNode current = this.head;
            while (current != null){
                LinkedNode temp = current;
                while (temp != null && temp.number == current.number){
                    temp = temp.next;
                }

                current.next = temp;
                current = current.next;
            }
    ```

2. **재귀 사용**

    ```java
    // 시간복잡도 : O(n)  
    // 공간복잡도 : O(n)
    private void removeDuplicates2() {
           recursive(this.head);
        }

        private LinkedNode recursive (LinkedNode node){
            if(node == null){
                return null;
            }
            if(node.next != null){
                if(node.number == node.next.number){
                    node.next = node.next.next;
                    recursive(node);
                }else{
                    recursive(node.next);
                }
            }
            return node;
        }

    ```
