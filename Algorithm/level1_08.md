# 8. arr 오름차순 의 사본
<img width="600"  src="https://user-images.githubusercontent.com/33523029/122941207-2564cd00-d3b0-11eb-8656-2899bef4affa.png">

### 알게된 점

- 소수 풀이
- 이 문제 풀이

### 풀이1 문제

```java
public class Level1_08 {

    public static void main(String[] args) {
        Level1_08 level = new Level1_08();

        int[] arr = level.solution(new int[]{1,5,10,2}, 5);

        for (int i = 0; i < arr.length; i++) {
             System.out.print(arr[i] + " ");
        }
    }

    private int[] solution(int[] arr, int divisor){
        int[] answer = {};
        Arrays.sort(arr);
        ArrayList<Integer> list = new ArrayList<>();

        for (int i = 0; i < arr.length; i++) {
            if(arr[i] % divisor == 0) list.add(arr[i]);
        }

        answer = new int[list.size()];

        for(int i=0; i<list.size(); i++){
            answer[i] = list.get(i);
        }

        return answer;
    }
}
```
