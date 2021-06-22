# 4. char타입을 int로

<img width="600"  src="https://user-images.githubusercontent.com/33523029/122936733-58a55d00-d3ac-11eb-9736-849d92ce8fd0.png">


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
