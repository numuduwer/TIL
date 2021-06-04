# 리스트 2. 끝에서 n번째 노드 찾기

### 출제 의도

- 다양한 방법들을 생각할 수 있는가??

### 문제. 
#### 단일 연결 리스트의 끝에서 n번째에 위치한 노드를 찾는 함수를 구현하라.

예) findFromLast(1 -> 4 -> 2 -> 3, 2), 끝에서 2번째에 위치한 2를 리턴한다.

### 풀이

1. **left right 사용** 

    - n만큼의 간격을 가진 좌 우 를 만들고
    - 우가 null 나올때까지 같이 이동!

    ```java
    // 시간복잡도 : O(N)
    // 공간복잡도 : O(1)
    private LinkedNode findFromLast1(int number){

            LinkedNode left = this.head;
            LinkedNode right = this.head;
    				
    				//  number+1한 이유?? number의 수와 간격이랑은 다르다. 이거 생각해자
            while(number+1 > 0){
                right = right.next;
                number--;
            }

            while(right.next != null){
                left = left.next;
                right = right.next;
            }
            return left;
        }
    ```

2. Map사용

    ```java
    // 시간복잡도 : O(n)  
    // 공간복잡도 : O(n)
    private LinkedNode findFromLast2(int number){
            Map<Integer, LinkedNode> nodeMap = new HashMap<>();
            LinkedNode current = this.head;
            int i = 0;

            while(current != null){
                nodeMap.put(i++, current);
                current = current.next;
            }

            return nodeMap.get(nodeMap.size() - number);
        }
    ```

3. **linked List 길이구하고 답을 얻기**

    ```java
    // 시간복잡도 : O(n)  
    // 공간복잡도 : O(1)
    private  LinkedNode findFromLast3(int number){
            LinkedNode current = this.head;
            int length = 0;
            while(current != null){
                length++;
                current = current.next;
            }

            int targetIndex = length -number;
            LinkedNode targetNode = this.head;
            while(targetIndex > 0){
                targetNode = targetNode.next;
                targetIndex--;
            }
            return targetNode;

        }
    ```
