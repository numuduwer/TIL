# 7. 소수 구하기
<img width="600"  src="https://user-images.githubusercontent.com/33523029/122941093-07976800-d3b0-11eb-8605-38ba071d0503.png">


### 알게된 점

- 소수 풀이
- 이 문제 풀이

### 풀이1 문제

```java
class Solution {
    public int solution(int[] nums) {
        int answer = 0;
        
        for (int i = 0; i < nums.length-2; i++) {
            for (int j = i+1; j < nums.length-1; j++) {
                for (int k = j+1; k < nums.length; k++) {
                    int num = nums[i] + nums[j] + nums[k];
                    boolean check = true;
                    
                    for (int l = 2; l < num; l++) {
                        if (num % l == 0) {
                            check = false;
                            break;
                        }
                    }
                    
                    if (check) answer++;
                }
            }
        }

        return answer;
    }
}
```

### 풀이2. 에라스토테네스의 체

```java
public static void main(String[] args) {
        Test2 t = new Test2();
        int[] arr = new int[] {1,2,7,6,4};

        // 주어진 3가지 수를 이용해서 소수인지를 판별하는 수를 구하라
        //t.solution1(arr);
        System.out.println(t.ss2(4));

    }

    private int ss(int n){
        int answer = 0;
        int[] number = new int[n+1];

        //2부터 n까지의 수를 배열에 넣는다.
        for(int i=2; i<=n; i++) {
            number[i] = i;
        }
        //2부터 시작해서 그의 배수들을 0으로 만든다.
        //후에 0이면 넘어가고 아니면 그의 배수들을 다시 0으로 만든다.
        for(int i=2; i<=n; i++) {
            if(number[i]==0) continue;

            for(int j= 2*i; j<=n; j += i) {
                number[j] = 0;
            }
        }
        //배열에서 0이 아닌 것들의 개수를 세준다.
        for(int i=0; i<number.length; i++) {
            if(number[i]!=0) {
                answer++;
            }
        }

        return answer;
    }
```
