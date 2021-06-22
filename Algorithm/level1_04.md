# 4. char타입을 int로

![4%20char%E1%84%90%E1%85%A1%E1%84%8B%E1%85%B5%E1%86%B8%E1%84%8B%E1%85%B3%E1%86%AF%20int%E1%84%85%E1%85%A9%208fa459786b7a4b0da01ea382c83b3043/_2021-06-21__12.35.38.png](4%20char%E1%84%90%E1%85%A1%E1%84%8B%E1%85%B5%E1%86%B8%E1%84%8B%E1%85%B3%E1%86%AF%20int%E1%84%85%E1%85%A9%208fa459786b7a4b0da01ea382c83b3043/_2021-06-21__12.35.38.png)

### 알게된 점

1. char 타입을 int로 바꾸려면  **Character.getNumericValue(chars);**

### 풀이

```java
public class Test1 {

    public static void main(String[] args) {
        Test1 t = new Test1();

        System.out.println(t.solution(123));
    }

    private int solution(int n){
        int answer = 0;

        // int를 String 으로
        String str = String.valueOf(n);

        // String을 chars[]로
        char[] chars = str.toCharArray();

        for (int i = 0; i < chars.length; i++) {

            // char를 int로
            answer += Character.getNumericValue(chars[i]);

        }
        return answer;
    }

}
```