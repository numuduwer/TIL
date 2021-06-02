# 배열 3. 두수의 합

### 출제 의도

- 배열 순회 및 출력
- HashMap을 사용해 봤는지?

**배운점**

- HashMap사용
- return할때 바로 배열 선언해서 리턴하기

### 문제. 
숫자로 구성된 배열 numbers와 target 숫자 하나가 주어졌을 때 numbers 배열에 들어있는 두 수를 더해 target 숫자를 만들 수 있는 인덱스 두개를 찾는 함수를 작성하라.

예) numbers = [2, 3, 5, 7] target = 8, 8을 만들 수 있는 3과 5의 인덱스인 1, 2를 리턴해야 한다.

예) numbers = [1, 2, 6, 8] target = 9, 9를 만들 수 있는1과8의 인덱스인0, 3을 리턴해야 한다.

### 풀이

1. for문 두개 사용 (return 할때 바로 배열 만들어서 리턴)  
2. HashMap 사용

1. **for문 두개 사용 (return 할때 바로 배열 만들어서 리턴)**

    ```java
    // 시간복잡도 : O(n^2)
    // 공간복잡도 : O(1)
    private int[] solution(int[] numbers, int target) {
            for (int i = 0; i < numbers.length; i++) {
                for (int j = i+1; j < numbers.length; j++) {
                    if(numbers[i] + numbers[j] == target){
                        return new int[] {i,j};
                    }
                }
            }
            return null;
        }
    ```

2. **HashMap 사용**

    ```java
    // 시간복잡도 : O(n)  
    // 공간복잡도 : O(n)
    private int[] solution(int[] numbers, int target) {
            HashMap<Integer, Integer> map = new HashMap<>();

            for (int i = 0; i < numbers.length; i++) {
                map.put(numbers[i],i);
            }

            for (int i = 0; i < numbers.length; i++) {
                int answer = target - numbers[i];
                if(map.containsKey(target-numbers[i]) && map.get(answer) != i){
                    return new int[]{i, map.get(answer)};
                }
            }
            return null;
        }
    ```