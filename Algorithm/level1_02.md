# 2. Long타입  내림차순

![2%20Long%E1%84%90%E1%85%A1%E1%84%8B%E1%85%B5%E1%86%B8%20%E1%84%82%E1%85%A2%E1%84%85%E1%85%B5%E1%86%B7%E1%84%8E%E1%85%A1%E1%84%89%E1%85%AE%E1%86%AB%2091b44f40d855472ca83a214edc625a18/Untitled.png](2%20Long%E1%84%90%E1%85%A1%E1%84%8B%E1%85%B5%E1%86%B8%20%E1%84%82%E1%85%A2%E1%84%85%E1%85%B5%E1%86%B7%E1%84%8E%E1%85%A1%E1%84%89%E1%85%AE%E1%86%AB%2091b44f40d855472ca83a214edc625a18/Untitled.png)

### 알게된 점

1. 문자열로 변환  `ValueOf(n)  / toString()` 
2. StringBuilder로 사용한 뒤집기  **Long.parseInt()**
3. Long타입으로 변환.  **new StringBuilder(new String(arr)).reverse().toString();**

### 풀이

```java
import java.util.Arrays;

public class Level1_01 {
    public static void main(String[] args) {
        Level1_01 level = new Level1_01();

        System.out.println(level.solution(118372));
    }

    private long solution(long n){
        long answer = 0;

        // 1. 문자열로 만든다.
        String nStr = String.valueOf(n);

        // 2. char타입 배열로 만들어 담는다.
        char[] chars =  nStr.toCharArray();

        // 3. 정렬
        Arrays.sort(chars);

        // 4. 뒤집기
        nStr = new StringBuilder(new String(chars)).reverse().toString();

        // 5. 타입 변환환
        answer = Long.parseLong(nStr);

        return answer;
    }

}
```