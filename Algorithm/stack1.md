# 스택 1. 스택 뒤집기

### 출제 의도

- 스택을 알고 있는가?
- 재귀로도 생각할 수 있는가?

### 문제. 
스택을 뒤집는 코드를 작성하라.

```java
// 출력을 위한 main 메서드
public static void main(String[] args) {
        Stack<Integer> numbers = new Stack();
        numbers.push(1);
        numbers.push(2);
        numbers.push(3);

        System.out.println(numbers);
        ReverseStack reverseStack = new ReverseStack();
        Stack<Integer> reversed = reverseStack.mySolution(numbers);
        System.out.println(reversed);
    }
```

### 풀이

1. **스택을 이용해서 만들기** 

    ```java
    // 시간복잡도 : O(N)
    // 공간복잡도 : O(N)
    private Stack<Integer> solution(Stack<Integer> stack){
            Stack<Integer> newStack = new Stack<>();
            while(!stack.isEmpty()){
                newStack.push(stack.pop());
            }
            return newStack;
        }
    ```

2. **재귀 사용**

    ```java
    // 시간복잡도 : O(n^2)  
    // 공간복잡도 : O(n)
    private void solution2(Stack<Integer> stack){
            if(stack.isEmpty()) return;
            int temp = stack.pop();
            mySolution2(stack);
            insertBottom(stack,temp);
        }

        private void insertBottom(Stack<Integer> stack, int number){
            if(stack.isEmpty()) {
                stack.push(number);
                return;
            }

            int temp = stack.pop();
            insertBottom(stack, number);
            stack.push(temp);
        }
    ```
