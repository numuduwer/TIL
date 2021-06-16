# 수박수박수

### 문제.

길이가 n이고, "수박수박수박수...."와 같은 패턴을 유지하는 문자열을 리턴하는 함수, solution을 완성하세요. 예를들어 n이 4이면 "수박수박"을 리턴하고 3이라면 "수박수"를 리턴하면 됩니다.

### 풀이

```java
class Solution {
    public String solution(int n) {
        String answer = "";
        int num = n/2;
        
        while(num >0){
            answer+="수박";
            num--;
        }
        
        
        if(n%2 == 1){
            answer+="수";
        }
        
        return answer;
    }
}
```

### 다른 풀이

```java
class Solution{
	public String solution(int n) {
		String answer = "수박";
		int multi = n/2;
		if (n%2==0) {
			answer = answer.repeat(multi);
		}else {
			answer = answer.repeat(multi) + "수";
		}
		return answer;
	}
}
```