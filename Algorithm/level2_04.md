# 4. 순간이동




<img width="600"  src="https://user-images.githubusercontent.com/33523029/123285269-dc478100-d547-11eb-8734-f4ca019eb443.png">
<img width="600"  src="https://user-images.githubusercontent.com/33523029/123285305-e1a4cb80-d547-11eb-84c1-a377f495ad65.png">

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
