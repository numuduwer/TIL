# 5. String을 int로 변환 가능한지?


<img width="600"  src="https://user-images.githubusercontent.com/33523029/122936982-91ddcd00-d3ac-11eb-950b-592274c40c30.png">

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
