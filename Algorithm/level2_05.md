# 5. String 다루어 짝지우기 의 사본

![5%20String%20%E1%84%83%E1%85%A1%E1%84%85%E1%85%AE%E1%84%8B%E1%85%A5%20%E1%84%8D%E1%85%A1%E1%86%A8%E1%84%8C%E1%85%B5%E1%84%8B%E1%85%AE%E1%84%80%E1%85%B5%20%E1%84%8B%E1%85%B4%20%E1%84%89%E1%85%A1%E1%84%87%E1%85%A9%E1%86%AB%20b0884ff49c2c419e80a5fe027d7cf4b0/_2021-06-25__6.33.45.png](5%20String%20%E1%84%83%E1%85%A1%E1%84%85%E1%85%AE%E1%84%8B%E1%85%A5%20%E1%84%8D%E1%85%A1%E1%86%A8%E1%84%8C%E1%85%B5%E1%84%8B%E1%85%AE%E1%84%80%E1%85%B5%20%E1%84%8B%E1%85%B4%20%E1%84%89%E1%85%A1%E1%84%87%E1%85%A9%E1%86%AB%20b0884ff49c2c419e80a5fe027d7cf4b0/_2021-06-25__6.33.45.png)

### 알게된 점

- String을 바로 for문에서 사용하면서 char 꺼내기
- **String.valueof(s.charAt(i));**
- 3항 연산자  **return   x == y ? 1: 0;**

### 풀이1

```java
import java.util.Stack;

public class Level2_05 {

    // 주어진 문자열 S에서 같은 알파벳이 붙어있는것을 찾습니다.
    // 이후 이 짝을 지우고 양옆을 지웁니다.
    // 이 동작을 반복으로 문자열이 다 지워지면 1 , 아니면 0 출력하라
    public static void main(String[] args) {
        Level2_05 level = new Level2_05();

        // baabaa --> 1
        // cdcd   --> 0
        System.out.println(level.solution("cdcd"));

    }

    private int solution(String s){
        int answer = 0;

        Stack<String> stack = new Stack<>();

        for (int i = 0; i < s.length(); i++) {
            if(stack.isEmpty()) {
                stack.push(String.valueOf(s.charAt(i)));
            }else{
                String lastVal = stack.peek();
                String curVal = String.valueOf(s.charAt(i));

                if(lastVal.equals(curVal)){
                    stack.pop();
                }else{
                    stack.push(curVal);
                }
            }
        }

        return stack.size() == 0? 1: 0;

    }
}
```