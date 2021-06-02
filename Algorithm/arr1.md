# 배열 1. 중복 숫자 확인

### 출제 의도

- 배열을 조회, 순회하는 조건문, 반복문사용 경험이 있는지?
- Sorting 알고리즘을 알고 이것의 시간복잡도를 알고 있는지?
- `**Set**`  자료구조를 알고 이것의 시간복잡도를 알고 있는가?

 

### 문제. 숫자로 구성된 배열이 주어졌을 때 그 배열에 중복된 숫자가 있는지 확인하는 함수를 작성하라. 중복된 숫자가 있다면 true 없다면 false.

예) 1 2 3 4 5 6 => false

예) 1 1 2 2 3 1 => true

### 풀이

1. Set을 사용  
2. for문 2개
3. Arrays.Sort 정렬 후 확인

1. **Set을 사용**
    - 자료구조 Set을 사용. 그중 순서가 필요없는 HashSet을 사용했다.
    - Set을 사용한 이유?  이 자료구조는 중복을 허용하지 않는다.
    - HashSet을 사용한 이유?  별도의 정렬작업이 없기에 연산이 가장 빠르다.

        ```java
        // 시간복잡도 : O(n)
        // 공간복잡도 : O(n) 
        private boolean solution01 (int[] numbers){
                Set<Integer> set = new HashSet<>();
                for (int i = 0; i < numbers.length; i++) {
                    if(!set.contains(numbers[i])){
                        set.add(numbers[i]);
                    }else{
                        return true;
                    }

                }
                return false;
            }
        ```

2. **for문 2개**
    - 가장 간단한 방법이다.  but 복잡도가 가장 크다.

        ```java
        // 시간복잡도 : O(n^2)
        // 공간복잡도 : O(1) 
        private boolean solution1(int[] numbers) {
                for(int i =0; i<numbers.length; i++){
                    for(int j=i+1; j<numbers.length; j++ ){
                        if(numbers[i] == numbers[j]){
                            return true;
                        }
                    }
                }
                return false;
            }
        ```

3. **Arrays.sort() 를 사용한 방법**
    - Sort 정렬 후 같은 값이 있는지 확인하는 방법
    - 자바에서 기본적으로 제공하는 `**Arrays.Sort()**`  를 사용한다.

        ```java
        // 시간복잡도 O(NlogN)
        // 공간복잡도 O(ogN)
        private boolean solution2(int[] numbers){
                Arrays.sort(numbers);
                for(int i=0; i< numbers.length -1 ; i++){
                    if(numbers[i] == numbers[i+1]){
                        return true;
                    }
                }
                return false;
            }
        ```