# 2. LRU 캐쉬

![2%20LRU%20%E1%84%8F%E1%85%A2%E1%84%89%E1%85%B1%205bdc475c88394db4be0d30e8a7d2c8a3/_2021-06-24__1.13.56.png](2%20LRU%20%E1%84%8F%E1%85%A2%E1%84%89%E1%85%B1%205bdc475c88394db4be0d30e8a7d2c8a3/_2021-06-24__1.13.56.png)

![2%20LRU%20%E1%84%8F%E1%85%A2%E1%84%89%E1%85%B1%205bdc475c88394db4be0d30e8a7d2c8a3/_2021-06-24__1.57.32.png](2%20LRU%20%E1%84%8F%E1%85%A2%E1%84%89%E1%85%B1%205bdc475c88394db4be0d30e8a7d2c8a3/_2021-06-24__1.57.32.png)

### 알게된 점

- LRU 캐쉬란
- LinkedList method들

### 풀이1

```java
public class Level2_02 {

    static final int CACHE_HIT  = 1;
    static final int CACHE_MISS = 5;

    public static void main(String[] args) {
        Level2_02 level = new Level2_02();
        // 3, ["Jeju", "Pangyo", "Seoul", "NewYork", "LA", "Jeju", "Pangyo", "Seoul", "NewYork", "LA"]  --> 50
        // 3, "Jeju", "Pangyo", "Seoul", "Jeju", "Pangyo", "Seoul", "Jeju", "Pangyo", "Seoul"           --> 21
        System.out.println(level.solution(3,new String[] {"Jeju", "Pangyo", "Seoul", "NewYork", "LA", "Jeju", "Pangyo", "Seoul", "NewYork", "LA"}));
    }

    //  입력된 도시이름 배열을 순서대로 처리할 떄  "총 실행시간"을 출력한다.
    //  캐시 교체 알고리즘은 LRU(Least Recently Used)를 사용한다.
    //  cache hit일 경우 실행시간은 1이다.
    //  cache miss일 경우 실행시간은 5이다.
    private int solution(int cacheSize, String[] cities){
        //  cacheSize 가 0인 경우
        if (cacheSize == 0) return cities.length * 5;

        int answer = 0;

        // LRU에 사용될 LinkedList
        LinkedList<String> cache = new LinkedList<>();

        for (int i = 0; i < cities.length; i++) {
            String city = cities[i].toUpperCase();

            //cache hit
            if(cache.remove(city)){
               cache.addFirst(city);
               answer += CACHE_HIT;

            // cache miss
            } else{

                // 링크드 리스트 size
                int currentSize = cache.size();

                if(currentSize == cacheSize){
                    // LinkedList의 마지막 요소를 반환하고 제거한다.
                    cache.removeLast();
                }

                cache.addFirst(city);
                answer += CACHE_MISS;
            }
        }
        return answer;
    }
}
```