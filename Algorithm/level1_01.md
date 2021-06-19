# 2. Long타입  내림차순

![Long_타입_내림차순](https://user-images.githubusercontent.com/33523029/122646258-32d44a00-d159-11eb-9dbf-90809fa46d1c.PNG)


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
