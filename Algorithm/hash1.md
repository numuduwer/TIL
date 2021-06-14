# hash 1. 완주못한 선수

### 배운점

- getOrDefault(Object key, V DefaultValue)

    ```java
    매개변수 :  이 메서드는 두개의 매게 변수를 허용한다. 
    Key : 값을 가져와야 하는 요소의 키
    defaultValue : 지정된 키로 매핑된 값이 없는 경우 반환되어야 하는 기본값 

    반환 값 : key가 존재하면 매핑되어 있는 값을 반환하고 , 아니면 디폴트 값이 반환 

    import java.util.HashMap; 

    // 결과 : {A=2, B=1, C=1} } 
    public class MapGetOrDefaultEx { 
    	
    public static void main(String arg[]) { 
    			String [] alphabet = { "A", "B", "C" ,"A"}; 
    			HashMap<String, Integer> hm = new HashMap<>(); 
    						
    			for(String key : alphabet) hm.put(key, hm.getOrDefault(key, 0) + 1); 
    			System.out.println("결과 : " + hm); 
    		}
    }
    ```

- map.keySet

    Map의 전체값을 출력하기 위한 메서드

### 문제.

수많은 마라톤 선수들이 마라톤에 참여하였습니다. 단 한 명의 선수를 제외하고는 모든 선수가 마라톤을 완주하였습니다.

마라톤에 참여한 선수들의 이름이 담긴 배열 participant와 완주한 선수들의 이름이 담긴 배열 completion이 주어질 때, 완주하지 못한 선수의 이름을 return 하도록 solution 함수를 작성해주세요

### 입력

```java
입력값 〉	["leo", "kiki", "eden"], ["eden", "kiki"]
기댓값 〉	"leo"
```

### 풀이

```java
import java.util.*;

class Solution {
    public String solution(String[] participant, String[] completion) {
        HashMap<String, Integer> map = new HashMap<>();
        String answer = "";
        
        for(String player : participant) map.put(player, map.getOrDefault(player, 0) + 1);
        for(String player : completion) map.put(player, map.get(player) - 1);
        
        for(String key : map.keySet()){
            if(map.get(key) != 0){
                answer = key;
            }
        }
        
        return answer;

    }
}
```