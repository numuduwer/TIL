# 11. 더해서 만들 수 있는 모든 수 배열

![11%20%E1%84%83%E1%85%A5%E1%84%92%E1%85%A2%E1%84%89%E1%85%A5%20%E1%84%86%E1%85%A1%E1%86%AB%E1%84%83%E1%85%B3%E1%86%AF%20%E1%84%89%E1%85%AE%20%E1%84%8B%E1%85%B5%E1%86%BB%E1%84%82%E1%85%B3%E1%86%AB%20%E1%84%86%E1%85%A9%E1%84%83%E1%85%B3%E1%86%AB%20%E1%84%89%E1%85%AE%20%E1%84%87%E1%85%A2%E1%84%8B%E1%85%A7%E1%86%AF%20526be19b676f445aa13efe006e5c2daa/_2021-06-22__5.47.11.png](11%20%E1%84%83%E1%85%A5%E1%84%92%E1%85%A2%E1%84%89%E1%85%A5%20%E1%84%86%E1%85%A1%E1%86%AB%E1%84%83%E1%85%B3%E1%86%AF%20%E1%84%89%E1%85%AE%20%E1%84%8B%E1%85%B5%E1%86%BB%E1%84%82%E1%85%B3%E1%86%AB%20%E1%84%86%E1%85%A9%E1%84%83%E1%85%B3%E1%86%AB%20%E1%84%89%E1%85%AE%20%E1%84%87%E1%85%A2%E1%84%8B%E1%85%A7%E1%86%AF%20526be19b676f445aa13efe006e5c2daa/_2021-06-22__5.47.11.png)

### 알게된 점

### 풀이1 문제

```java
import java.util.ArrayList;
import java.util.Arrays;

public class Level1_11 {
    public static void main(String[] args) {
        Level1_11 level = new Level1_11();

        // [2,1,3,4,1] -> return [2,3,4,5,6,7]
        int[] arr = level.solution(new int[] {2,1,3,4,1});

        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");

        }
    }

    private int[] solution(int[] numbers){
        int[] answer = {};
        ArrayList<Integer> list = new ArrayList<>();

        for (int i = 0; i < numbers.length-1; i++) {
            for (int j = i+1; j < numbers.length; j++) {
                int temp =  numbers[i] + numbers[j] ;

                if(!list.contains(temp)){
                    list.add(temp);
                }
            }

        }

        answer = new int[list.size()];

        for(int i = 0; i< list.size(); i++){
            answer[i] = list.get(i);
        }
        Arrays.sort(answer);

        return answer;
    }
}
```