# 6. 배열 중복된 값 지우기


<img width="600"  src="https://user-images.githubusercontent.com/33523029/122940879-d454d900-d3af-11eb-867b-f227070c7e73.png">

### 알게된 점

- **StringBuilder 를 사용한 방법**
- **LinkedHashSet을 이용한 방법    → 이건 1301일 경우 실패 (1이 두번)**

### 풀이1. StringBuilder

```java
public class Test1 {

    public static void main(String[] args) {
        Test1 t = new Test1();
        int[] ttt = t.solution5(new int[]{1,1,3,3,0,1,1});
        for (int i = 0; i < ttt.length; i++) {
            System.out.print(ttt[i] + " ");

        }

    }
    private  int[] solution5(int[]arr){
        int[] answer = {};
        StringBuilder sb = new StringBuilder();
        int size = arr.length;

        sb.append(arr[0]);

        for(int i=1; i<size;i++) {
            if(arr[i-1] != arr[i]){
                sb.append(arr[i]);
            }
        }

        String[] strArr = sb.toString().split("");
        size = strArr.length;

        answer = new int[size];

        for(int i =0; i<size; i++){
            answer[i] = Integer.parseInt(strArr[i]);
        }

        return answer;
    }
```

### 풀이2. **LinkedHashSet**

```java
private int[] solution4(int[] arr){
        int[] answer = {};

        LinkedHashSet<Integer> linkedHashSet = new LinkedHashSet<>();

        for(int i :arr){
            linkedHashSet.add(i);
        }

        answer = new int[linkedHashSet.size()];
        int index =0;
        Iterator iter = linkedHashSet.iterator();

        while (iter.hasNext()){
            answer[index++] = (Integer)iter.next();
        }

        return  answer;
    }
```
