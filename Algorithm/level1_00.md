# 1.이중배열 사용하기

![image](https://user-images.githubusercontent.com/33523029/122936056-d2891680-d3ab-11eb-82b7-21ed51ccf341.png)

### 알게된 점

1. 이중 배열 사용법
2. 배열자르기 `Arrays,copyOfRange(arr, start,end)`
3. 배열 출력하기 `Arrays.toString(arr)`

### 풀이

```java
import java.util.Arrays;

public class Arr1 {

    public static void main(String[] args) {

        int[] array = new int[] {1,5,2,6,3,7,4};
        int[][] commands = new int[][]{{2,5,3},{4,4,1},{1,7,3}};

        Arr1 a = new Arr1();
        System.out.println(Arrays.toString(a.solution(array, commands)));

    }
    public int[] solution(int[] array, int[][] commands){
        int[] answer = new int[commands.length];

        for(int i=0; i<commands.length; i++){
            int[] temp = Arrays.copyOfRange(array, commands[i][0]-1, commands[i][1]);
            Arrays.sort(temp);
            answer[i] = temp[commands[i][2]-1];
        }

        return answer;
    }
}
```
