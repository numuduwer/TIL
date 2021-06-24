# 1. 이진법을 이용한 수

<img width="600"  src="https://user-images.githubusercontent.com/33523029/123284251-12383580-d547-11eb-9492-70f4f57de62c.png">



### 알게된 점

- 이진법 변환 : **Integer.toBinaryString(int n)**

### 풀이1 문제

```java
public class Level2_01 {

    // 자연수 n이 주어졌을때 다음 수를 구하를 solution을 만들어라

    // 조건 1. answer는 n보다 큰 자연수
    // 조건 2. n과 answer는 이진법으로 변환시 1의 갯수가 동일해야 한다.
    // 조건 3. answer는 조건 1,2를 충족하는 수중 가장 작은 수
    public static void main(String[] args) {

        Level2_01 level = new Level2_01();

        System.out.println(level.solution(78));

    }

    private int solution(int n){
        int answer = 0;

        // n 을 이진수로 만든다.
        // 1를 뽑는다.
        String n2 = Integer.toBinaryString(n);
        char[] n2Char = n2.toCharArray();
        int n2Count =0;

        for (int i = 0; i < n2Char.length; i++) {
            if(n2Char[i] == '1'){
                n2Count++;
            }
        }

        while(true){

            // n++ 를 이진수로 만든다.
            // 1를 뽑는다.
            int n3 = ++n;
            System.out.println("n3 " + n3);
            String n32 = Integer.toBinaryString(n3);
            char[] n32Chars = n32.toCharArray();
            int n32Count =0;

            for (int i = 0; i < n32Chars.length; i++) {
                if (n32Chars[i] == '1') {
                    n32Count++;
                }
            }

            if(n2Count == n32Count){
                answer = n3;
                break;
            }

        }

        return answer;
    }
}
```
