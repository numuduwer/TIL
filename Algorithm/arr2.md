# 배열 2.문자열 뒤집기

### 출제 의도

- 배열을 for 문에서 잘 사용하는지
- StringBuilder API를 알고 있는지?

### 문제 
#### 주어진 문자열을 거꾸로 뒤집은 문자열을 만드는 함수를 작성하라.

예) hello => olleh /  happy new year => reay wen yppah

### 풀이

1. **for문 사용한 거꾸로 순회**

    ```java
    // 시간복잡도 : O(n)
    // 공간복잡도 : O(n)
    public char[] solution01(char[] chars){
          char[] answer = new char[chars.length];

          for (int i = chars.length-1 ; i>=0; i--) {
              answer[i] = chars[i];
          }
          return answer;
      }
    ```

2. **for문에서 공간 복잡도를 더 줄이는 방법**

    ```java
    // 시간복잡도 : O(n)  -> 이것도 1/2으로 준다.  
    // 공간복잡도 : O(1)
    public char[] solution01(char[] chars){

          for (int i = 0; i < chars.length/2; i++) {
              char temp = chars[i];
              chars[i]  = chars[chars.length-1-i];
              chars[chars.length-1-i] = temp;
          }
          return chars;
      }
    ```

3. **Stack을 사용한 방법**
    - **`Stack`**은 **Last In Fast Out (pop)**의 성격을 이용하는 방법

    ```java
    // 시간복잡도 O(n)
    // 공간복잡도 O(n)
    public char[] solution01(char[] chars){
            Stack<Character> stack = new Stack<>();

            for (int i = 0; i < chars.length; i++) {
                stack.add(chars[i]);
            }

            for (int i = 0; i < chars.length; i++) {
                chars[i] = stack.pop();
            }
            return chars;
        }
    ```

4. **String Builder를 사용한 방법 (번외)**

    ```java
    public String solution01(String chars){
            StringBuilder sb = new StringBuilder(String.valueOf(chars));
            String reverse = sb.reverse().toString();
            return reverse;
        }
    ```
