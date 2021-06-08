# 큐 4. 큐를 사용해서 스택을 만들어라

### 출제 의도

- 큐 스택을 잘 알고 있는가?

### 문제

```java
// 주어진 배열 prices에 대한 스팬을 구하는 코드를 작성하라.
// 스팬: 당일의 주가 보다 낮거나 같았던 연속적인 일 수.
// 예) [5, 3, 2, 4, 7, 1]    =>   [1, 1, 1, 3, 5, 1]
// 예) [2, 3, 4, 5, 6, 7]    =>   [1, 2, 3, 4, 5, 6]

public static void main(String[] args) {
        Span span = new Span();
        System.out.println(Arrays.toString(span.solution(new int[]{5, 3, 2, 4, 7, 1})));
        System.out.println(Arrays.toString(span.solution(new int[]{2, 3, 4, 5, 6, 7})));
    }
```

### 풀이

1. push: O(n) /  pop : O(1) 방법

    ```java
    public class QueueStack {

        Queue<Integer> q1 = new LinkedList<>();
        Queue<Integer> q2 = new LinkedList<>();

        public static void main(String[] args) {
            QueueStack stack = new QueueStack();
            stack.push(1);
            stack.push(2);
            stack.push(3);
            System.out.println(stack.pop() == 3);
            System.out.println(stack.pop() == 2);
            System.out.println(stack.pop() == 1);

        }

        private Integer pop(){
            if(q1.isEmpty()){
                return null;
            }
            return q1.poll();
        }

        private void push(int number){
            q2.offer(number);

            while (!q1.isEmpty()){
                q2.offer(q1.poll());
            }

            Queue<Integer> temp = q1;
            q1 = q2;
            q2 = temp;
        }
    }
    ```

2.  push: O(1) /  pop : O(n) 방법

    ```java
    public class QueueStack {

        Queue<Integer> q1 = new LinkedList<>();
        Queue<Integer> q2 = new LinkedList<>();

        public static void main(String[] args) {
            QueueStack stack = new QueueStack();
            stack.push(1);
            stack.push(2);
            stack.push(3);
            System.out.println(stack.pop() == 3);
            System.out.println(stack.pop() == 2);
            System.out.println(stack.pop() == 1);

        }

        private Integer pop(){
            if(q1.isEmpty()) {
                return null;
            }
            while (q1.size() > 1) {
                q2.offer(q1.poll());
            }
            Integer value = q1.poll();

            Queue<Integer> temp= q1;
            q1= q2;
            q2 = temp;

            return  value;
        }

        private void push(int number){
                q1.offer(number);
            }
        }
    ```