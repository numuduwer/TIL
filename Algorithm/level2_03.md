# 3. 동적 프로그래밍이중 배열 정사각형


<img width="600"  src="https://user-images.githubusercontent.com/33523029/123284841-85da4280-d547-11eb-8cde-1af09eae944a.png">
<img width="600"  src="https://user-images.githubusercontent.com/33523029/123284853-88d53300-d547-11eb-8914-1a3e783c7447.png">


### 알게된 점

- 동적 프로그래밍
- 이중 배열 값 출력 :`Arrays.deepToString(board);`

### 풀이1

```java
//1과 0으로 채워진 board가 주어지고
    //이 board에서 1로 이루어진 가장 큰 정사각형의 넓이를 구하여라
    public static void main(String[] args)  {
        Level2_03 level = new Level2_03();

        // 0 1 1 1
        // 1 1 1 1
        // 1 1 1 1
        // 0 0 1 0
        // -> return  9
        System.out.println(level.solution(new int[][]{{0, 0, 1, 1},{1, 1, 1, 8}}));

    }

    private int solution(int[][] board){
        int answer = 1;

        //{0, 1, 1, 1},{1, 1, 1, 1}, {1, 1, 1, 1},{0, 0, 1, 0}
        for (int i = 1; i < board.length; i++) {
            for (int j = 1; j < board.length; j++) {

                if(board[i][j] == 1){

                    if(board[i-1][j-1] > 0 && board[i-1][j] > 0  && board[i][j-1] > 0){
                        board[i][j] = i+1;
                        answer = board[i][j] * board[i][j];
                    }
                }
            }
        }
        System.out.println(Arrays.deepToString(board));

        return answer;
        }
}
```
