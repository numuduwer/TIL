# 큐 1. 큐 뒤집기

### 출제 의도

- 큐를 알고 있는가?
- 재귀로도 생각할 수 있는가?

### 문제. 
큐를 뒤집는 코드를 작성하라.

```java
// 출력을 위한 main 메서드
public static void main(String[] args) {
        Queue<Integer> numbers = new LinkedList<>();
        numbers.offer(1);
        numbers.offer(2);
        numbers.offer(3);

        System.out.println(numbers);
        ReverseQueue reverseQueue = new ReverseQueue();
        Queue<Integer> reversed = reverseQueue.reverse1(numbers);
        System.out.println(reversed);
    }
```

### 풀이

1. **스택으로 만들기** 

    ```java
    // 시간복잡도 : O(N)
    // 공간복잡도 : O(N)
    private Queue<Integer> reverse(Queue<Integer> numbers) {
        Stack<Integer> stack = new Stack<>();
        while(!numbers.isEmpty()){
            stack.push(numbers.poll());
        }

        while(!stack.isEmpty()) {
            numbers.offer(stack.pop());

        }
            return numbers;
    }
    ```

2. **재귀 사용**

    ```java
    // 시간복잡도 : O(n^2)  
    // 공간복잡도 : O(n)
    private Queue<Integer> reverse(Queue<Integer> numbers) {
            if(numbers.isEmpty()){
                return numbers;
            }
            
            int temp = numbers.poll();
            reverse(numbers);
            numbers.offer(temp);
            

            return numbers;
        }
    ```