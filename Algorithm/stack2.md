# 스택 2. 괄호 짝 맞추기

### 출제 의도

- 스택으로 이런것도 생각할 수 있는가

### 문제. 
주어진 수식의 괄호짝이 맞는지 확인하는 코드를 작성하라.

```java
//예) [{1 + 2 * (2 + 2)} - (1 - 3)]   => true
//예) [{1 + 2 * (2 + 2)} - [1 - 3)]   => false
public static void main(String[] args) {
        CheckingBrackets checkingBrackets = new CheckingBrackets();
        System.out.println(checkingBrackets.myCheck("[{1 + 2 * (2 + 2)} - (1 - 3)]"));
        System.out.println(checkingBrackets.myCheck("[{1 + 2 * (2 + 2)} - [1 - 3)]"));
        System.out.println(checkingBrackets.myCheck("((())"));
        System.out.println(checkingBrackets.myCheck("(()))"));
        System.out.println(checkingBrackets.myCheck("{{()}}"));
    }
```

### 풀이

**스캔 전 준비**

- char[] arr 로 스캔할 문자열을 담는다.
- 체크항목인 괄호 답안지를 opening / closing로 구분둬서 List로 만든다.

**스캔시작** 

- 스캔하때 Opening괄로가 스캔되면 스택에 담는다.
- 스캔할때 Closing 괄호가 스캔되면, 스택에서 pop해서 변수로 담고 같은지 비교한다.

    pop한놈의 opening 답안지에서의 index위치   /  스캔된 closing 괄호의 index위치. 

```java
// 시간복잡도 : O(N)
// 공간복잡도 : O(N)
private boolean myCheck(String str){
        Stack<Character> brackets = new Stack<>();
        char[] chars = str.toCharArray();
        List<Character> openingBrackets = Arrays.asList('(','{','[');
        List<Character> closingBrackets = Arrays.asList(')','}',']');

        for(char c:chars){
            if(openingBrackets.contains(c)){
                brackets.push(c);
            }else if(closingBrackets.contains(c)){
                if(brackets.isEmpty()){
                    return false;
                }
                char openingBraket = brackets.pop();
                if(closingBrackets.indexOf(c) != openingBrackets.indexOf(openingBraket)){
                    return false;
                }
            }
        }
        return brackets.isEmpty();
    }
```