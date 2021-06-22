# 10. 배열에 가운데를 구하라

![10%20%E1%84%87%E1%85%A2%E1%84%8B%E1%85%A7%E1%86%AF%E1%84%8B%E1%85%A6%20%E1%84%80%E1%85%A1%E1%84%8B%E1%85%AE%E1%86%AB%E1%84%83%E1%85%A6%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A1%E1%84%85%E1%85%A1%20ecd173308e744d9fa8cdc04e0f05ff69/_2021-06-22__5.38.14.png](10%20%E1%84%87%E1%85%A2%E1%84%8B%E1%85%A7%E1%86%AF%E1%84%8B%E1%85%A6%20%E1%84%80%E1%85%A1%E1%84%8B%E1%85%AE%E1%86%AB%E1%84%83%E1%85%A6%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A1%E1%84%85%E1%85%A1%20ecd173308e744d9fa8cdc04e0f05ff69/_2021-06-22__5.38.14.png)

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