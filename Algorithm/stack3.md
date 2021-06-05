# 스택 3. 포스트픽스 계산하기

### 출제 의도

- 문제를 이해할 수있는가
- 규칙을 찾을 수 있는가
- 스택을 활용할 수 있는가?

**배운점**

1. Character.isDisit();
2. case문을 언제사용하는지 생각해보자 , 사용방법 숙지!  

### 문제.

```java
// 포스트픽스로 주어진 식을 계산하는 코드를 작성하라. 
// 수식은 사칙연산 (+, -, *, /)만 사용한다고 가정한다.
// 예) 12+      => 3
// 예) 123+-5*  => -20
public static void main(String[] args) {
        EvaluationPostfix postfix = new EvaluationPostfix();
        System.out.println(postfix.evaluate("52+") == 7);
        System.out.println(postfix.evaluate("52-") == 3);
        System.out.println(postfix.evaluate("52*") == 10);
        System.out.println(postfix.evaluate("52/") == 2);
        System.out.println(postfix.evaluate("521+-9*") == 18);
    }
```

### 풀이

1. **일반**

    ```java
    // 시간복잡도 : O(N)
    // 공간복잡도 : O(N)
    private int mySolution(String s){
            LinkedList<Integer> numbers = new LinkedList<>();
            char[] chars = s.trim().toCharArray();
            
            for(char c:chars){
                if(Character.isDigit(c)){
                    numbers.push(Integer.parseInt(c+""));
                }else{
                    int right = numbers.pop();
                    int left  = numbers.pop();
                    
                    switch (c){
                        case '+':
                            numbers.push(left+right);
                            break;
                        case '-':
                            numbers.push(left-right);
                            break;
                        case '*':
                            numbers.push(left*right);
                            break;
                        case '/':
                            numbers.push(left/right);
                            break;                        
                    } 
                    
                }
            }
            return numbers.pop();
        }
    ```