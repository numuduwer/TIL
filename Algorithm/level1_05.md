# 5. String을 int로 변환 가능한지?

![5%20String%E1%84%8B%E1%85%B3%E1%86%AF%20int%E1%84%85%E1%85%A9%20%E1%84%87%E1%85%A7%E1%86%AB%E1%84%92%E1%85%AA%E1%86%AB%20%E1%84%80%E1%85%A1%E1%84%82%E1%85%B3%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%E1%84%8C%E1%85%B5%203e86a6f1b7c84662a11f8feaacea9cac/_2021-06-21__12.55.36.png](5%20String%E1%84%8B%E1%85%B3%E1%86%AF%20int%E1%84%85%E1%85%A9%20%E1%84%87%E1%85%A7%E1%86%AB%E1%84%92%E1%85%AA%E1%86%AB%20%E1%84%80%E1%85%A1%E1%84%82%E1%85%B3%E1%86%BC%E1%84%92%E1%85%A1%E1%86%AB%E1%84%8C%E1%85%B5%203e86a6f1b7c84662a11f8feaacea9cac/_2021-06-21__12.55.36.png)

### 알게된 점

1. int로 형변환 가능한지?   **Character.isDisit()**

### 풀이

```java
public class Test1 {

    public static void main(String[] args) {
        Test1 t = new Test1();

        System.out.println(t.solution2("12121212234"));

    }
    private boolean solution2(String s){
        boolean answer = true;
        char[] chars = s.toCharArray();

        if(s.length() < 4 || s.length() > 6 ){
            System.out.println("길이 문제");
            answer = false;
        }

        for(int i=0; i<chars.length; i++){
            if(!Character.isDigit(chars[i])){
                System.out.println("문자열 있음");
                answer = false;
            }
        }
        return answer;
    }
```