# 배열 4. O(n) 정렬

```
1부터100까지의 숫자 중에50개의 랜덤한 숫자가 들어있는 배열이 있다.
*이 배열을O(n)의 시간 복잡도로 정렬하라.
```

### 출제 의도

- 배열의 index를 활용하는지?

**배운점**

- for(int num : numbers){}
- boolean타입의 배열은 디폴트값 false;

### 문제. 1부터100까지의 숫자 중에50개의 랜덤한 숫자가 들어있는 배열이 있다.
이 배열을O(n)의 시간 복잡도로 정렬하라.

### 풀이

1. **배열의 index를 활용한 방법**

    ```java
    // 시간복잡도 : O(n)
    // 공간복잡도 : O(n)
    private int[] solution2(int[] numbers){
             boolean[] booleans = new boolean[numbers.length];

            for (int num : numbers) {
                booleans[num] = true;
            }
            
            int index= 0;
            for (int i = 0; i < numbers.length; i++) {
                if(booleans[i]){
                    numbers[index++] = i;
                }
            }
            return  numbers;
        }
    ```