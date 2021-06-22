# 10. 배열에 가운데를 구하라
<img width="600"  src="https://user-images.githubusercontent.com/33523029/122941430-59d88900-d3b0-11eb-96cb-c23a4433f736.png">


### 알게된 점

### 풀이1 문제

```java
public class Level1_10 {

    public static void main(String[] args) {
        Level1_10 level = new Level1_10();
        System.out.println(level.solution("abchde"));

    }

    private String solution(String str){
        String answer="";

        char[] chars = str.toCharArray();
        StringBuilder sb = new StringBuilder();

        if(chars.length % 2 == 0) {
            sb.append(chars[chars.length/2 -1]);
            sb.append(chars[chars.length/2]);
        }else{
            sb.append(chars[chars.length/2]);
        }

        answer = sb.toString();

        return answer;
    }
}
```
