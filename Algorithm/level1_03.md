# 3.약수 구하기

![3%20%E1%84%8B%E1%85%A3%E1%86%A8%E1%84%89%E1%85%AE%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A1%E1%84%80%E1%85%B5%20c7f9f8682f39413d881e492771061e7d.png](3%20%E1%84%8B%E1%85%A3%E1%86%A8%E1%84%89%E1%85%AE%20%E1%84%80%E1%85%AE%E1%84%92%E1%85%A1%E1%84%80%E1%85%B5%20c7f9f8682f39413d881e492771061e7d.png)

### 알게된 점

1. 효율적인 약수 구하는 방법 **Math.sqrt()**

### 풀이

```java
import java.util.*;

class Solution {
    public int solution(int left, int right) {
        int answer = 0;
        
        for(int i =left; i<right+1; i++){
            int count = 0;
            
            for(int j=1; j<= Math.sqrt(i); j++){
                if(i%j == 0){
                    if(j == i/j) count+= 1; 
                    else count+= 2;  
                }
                
            }
            if(count%2 ==0) answer += i;
            else answer -= i;
            
        }
        
        return answer;
    }
}
```

### 약수를 구하는 방법 두가지

```java
// 비효율적
private int solution2(int num){
        int answer =0;

        for(int i=1; i<=num; i++){
            if(num%i == 0){
                answer++;
            }
        }
	return answer;
}

// 효율적
private int solution2(int num){

        int count  = 0;
        for(int i=1; i< Math.sqrt(num); i++){
            if(num%i == 0){
                if(num / i == i){
                    count++;
                }else{
                    count += 2;
                }
            }
        }

        return count;
    }
```