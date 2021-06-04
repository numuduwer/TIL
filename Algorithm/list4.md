# 리스트 4. 원형 링크드리스트인지 확인하기

### 출제 의도

- Set을 사용해서 풀 수있는가?
- 다른 방법도 생각할 수있는가?

### 문제.

#### 주어진 연결 리스트가 원형 연결 리스트인지 단일 연결 리스트인지 확인하는 함수를 구현하라.

예)  1 -> 2 -> 3 -> 1 => true   / 1 -> 2 -> 3 => false

### 풀이

1. **Set을 사용하는 방법**

    ```java
    // 시간복잡도 : O(N)
    // 공간복잡도 : O(N)
    private boolean setTest(){
            Set<LinkedNode> set = new HashSet<>();
            LinkedNode current = this.head;

            while(current != null){
                if(!set.contains(current)){
                    set.add(current);
                }else{
                    return true;
                }
                current = current.next;
            }
            return false;
        }
    ```

2. **서로 다른 속도로 움직이는 포인터로 찾는 방법** 

    ```java
    // 시간복잡도 : O(n)  
    // 공간복잡도 : O(1)
    private boolean hasCircle2() {
            LinkedNode slow = this.head;
            LinkedNode fast = this.head;

            while(fast != null) {
                if (fast.next == null || fast.next.next == null) {
                    return false;
                }

                fast = fast.next.next;
                if (slow == fast) {
                    return true;
                }

                slow = slow.next;
            }

            return false;
        }

    ```