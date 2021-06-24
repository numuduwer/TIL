# 4. 순간이동

![4%20%E1%84%89%E1%85%AE%E1%86%AB%E1%84%80%E1%85%A1%E1%86%AB%E1%84%8B%E1%85%B5%E1%84%83%E1%85%A9%E1%86%BC%208c8507cf52dd410589e951991acad07c/_2021-06-24__5.23.01.png](4%20%E1%84%89%E1%85%AE%E1%86%AB%E1%84%80%E1%85%A1%E1%86%AB%E1%84%8B%E1%85%B5%E1%84%83%E1%85%A9%E1%86%BC%208c8507cf52dd410589e951991acad07c/_2021-06-24__5.23.01.png)

![4%20%E1%84%89%E1%85%AE%E1%86%AB%E1%84%80%E1%85%A1%E1%86%AB%E1%84%8B%E1%85%B5%E1%84%83%E1%85%A9%E1%86%BC%208c8507cf52dd410589e951991acad07c/_2021-06-24__5.23.21.png](4%20%E1%84%89%E1%85%AE%E1%86%AB%E1%84%80%E1%85%A1%E1%86%AB%E1%84%8B%E1%85%B5%E1%84%83%E1%85%A9%E1%86%BC%208c8507cf52dd410589e951991acad07c/_2021-06-24__5.23.21.png)

### 알게된 점

- 음 유연한 사고?

### 풀이1

```java
// 순간이동 슈트의 최소한의 건전지 사용량을 구하는 값을 구하라
    //    ** 2  -> 사용량 x
    // k 만큼 이동 -> 사용량 k
    // ex. n = 5 > 2
    //     n = 6 > 2
   public static void main(String[] args) {

        Level2_04 level = new Level2_04();
        System.out.println(level.solution(5));
    }

    private int solution(int n ){
        int answer =0;

        while(n != 0){
            if(n % 2 == 0){
                n /= 2;
            }else{
                n--;
                answer++;
            }
        }

        return answer;
    }
```