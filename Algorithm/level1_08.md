# 8. arr 오름차순 의 사본

![9%20%E1%84%8E%E1%85%A6%E1%84%8B%E1%85%B2%E1%86%A8%E1%84%87%E1%85%A9%E1%86%A8%20%E1%84%8B%E1%85%B4%20%E1%84%89%E1%85%A1%E1%84%87%E1%85%A9%E1%86%AB%20045f7aaf4f044d53ba82ee2b72a0468a/_2021-06-22__4.14.27.png](9%20%E1%84%8E%E1%85%A6%E1%84%8B%E1%85%B2%E1%86%A8%E1%84%87%E1%85%A9%E1%86%A8%20%E1%84%8B%E1%85%B4%20%E1%84%89%E1%85%A1%E1%84%87%E1%85%A9%E1%86%AB%20045f7aaf4f044d53ba82ee2b72a0468a/_2021-06-22__4.14.27.png)

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