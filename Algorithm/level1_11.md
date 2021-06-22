# 11. 더해서 만들 수 있는 모든 수 배열

<img width="600"  src="https://user-images.githubusercontent.com/33523029/122941538-6fe64980-d3b0-11eb-96a8-74e33dc2be3a.png">



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
