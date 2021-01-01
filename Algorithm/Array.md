# 배열(Array) 
배열은 연속된 메모리 영역에 저장된 데이터 조회 O(1), 추가 및 삭제가 O(n)의 복잡도를 가지고 있다. 
- 즉, 조회는 빠름, 삭제 추가는 느리다 
- 자바에서 배열을 만들 때 크기를 정해야하한다. 
- 다른 자료구조를 구현하는데 사용하는 가장 기본적은 데이터구조이다. 

### 선언방법 
~~~java
   // type name[]  or  type[] name
    int intArray[];
    int[] intArray;
~~~

### 사용하기
~~~java
    int[] intArray;
    intArray = new int[20];
    
    // 혹은
    int[] intArray = new int[20];
    
    // 값까지 넣는 경우 { } 안에 값을 명시해주기 
    int[] intArray = new int[]{1,2,3,4,5};


    // new없이 만드는 경우도 있다.  
    int[]arr = {3,4,5,6,7};


    // 배열안에 값을 순회할때는 
    for(int i=0; i<intArray.length; i++){
        System.out.println(i + "번 인덱스의 값은 :" + intArray[i]);
    } 
~~~

### java.util.Arrays 클래스 
- java.util 패키지에 있는 Arrays 클래스
- 배열을 다루기 위한 메서드들이 들어있다. 

#### 1. toString(arr)
- 배열의 요소를 보여준다. 
~~~java
import java.util.*;

class Main{
    public static void main(String[] args){
        int[]arr = {3,4,5,6,7};
        System.out.println(Arrays.toString(arr));
    }
}
// 결과값 [3,4,5,6,7]
~~~

#### 2. sort(arr)
- 배열의 element를 오름차순으로 정렬
~~~java
    import java.util.*;
    
    class Main{
        public static void main(String[] args){
            int [] arr = {4,3,2,1};
            Arrays.sort(arr);
            for(int i=0; i<arr.length; i++){
                System.out.print(arr[i]+" ");
            }
        }
    }
    // 출력 >> 1 2 3 4
~~~

#### 3. binarySearch(arr,값)
- 배열에서 특정 element의 위치를 이진 검색알고리즘(O(logn)을 사용해서 찾은 후 해당 값의 인덱스를 반환한다. 
- sort()로 오른차순 정렬해야 사용가능. 
~~~java
    import java.util.*;
    
    class Main{
        public static void main(String[] args){
            int [] arr = {3,4,5,7,8,9};
            System.out.println(Array.binarySearch(arr,7));
        }
    }
// 출력 >> 3
~~~

#### 4. fill(arr,값)
- 전달받은 배열의 모든 요소를특정 값으로 초기화 

~~~java
    import java.util.*;
    
    class Main{
        public static void main(String[] args){
            int [] arr = new int[4];
            Arrays.fill(arr,7);
            
        }
    }
// 배열 arr은 [7,7,7,7]
~~~
#### 5. equals(arr1,arr2)
- 두 배열이 같은지 비교 
- boolean타입으로 리턴 
~~~java
    String[] strArr1 = {"a","b","c"};
    String[] strArr2 = {"a","c","g"};

    System.out.println(Array.equals(strArr1, srtArr2));

// 결과 >> false
~~~

#### 6.asList(arr)
- 배열로부터 고정된 크기의 리스트를 리턴한다. 

~~~java
    import java.util.*;

    class Main{
        public static void main(String[] args){
            String[] arr = {"a","b","c"};

            List<String> lst = Arrays.asList(arr);

            // 결과는 
            // ["a","b","c"]
            // ["a","b","c"]
            System.out.println(Arrays.toString(arr));
            System.out.println(lst);

            arr[0] += "99";
            lst.set(2,lst.get(2),"99");

            // 결과는 
            // ["a99","b","c"]
            // ["a","b","c99"]
            System.out.println(Arrays.toString(arr));
            System.out.println(lst);


            
        }

    }

~~~

### 참고 
- https://docs.oracle.com/javase/8/docs/api/index.html




# 리스트 (List) 
- 배열과 비슷한 자바의 자료형
- 일렬로 늘여놓는 구조를 갖는다.  
- 검색,삭제,등 편리한 기능을 가지고 있다. 
- list 자료형에는 ArrayList,Vector,LinkedList들의 list 인터페이스를 구현한 자료형이 있다. 


### 배열 vs 리스트 
- 배열은 한번 크기를정하면 그 이상의 값을 담을 수 없다. 

### ArrayList 
- List 인터페이스를 구현한 클래스 
- 설정된 저장 용량보다 많은 데이터가 들어오면 자동으로 용량이 늘어난다. 

#### 생성방법 
~~~java
    List<E>객체명 = new ArrayList<E>([초기 저장용량]);

    // E는 제레릭 타입을 의미한다. 생략하면 Object타입이 된다. 
    // Object타입은 모든 타입을 저장하지만 추가,검색시 형변환해줘야한다. 
    // 주로 동일한 데이터타입을 저장하기 떄문에 생략(Object)안하고 타입을 지정해주자. 
~~~

#### 사용하기 
~~~java
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

public class ArrayListEx01{
    public static void main(String[] args){
        List<String> list = new ArrayList<String>();

        // index에 데이터 추가 
        list.add("리스트1");
        list.add("리스트2");
        list.add("리스트3");

        // 1번 index에 "리스트4" 넣기
        // 1번 이후의 인덱스들이 하나씩 밀림  
        list.add(1,"리스트4");

        //저장된 데이텅용량 출력(마지막 인덱스 +1)
        // 결과 >> 4
        System.out.println(list.size())

        // 0번 index의 값 출력
        System.out.println(list.get(0));

        // 0번 index의 값 삭제 
        // 나머지 인덱스들 앞으로 당겨짐 
        list.remove(0);


        // Iterator() 반복자 이용 데이터 출력 
        Iterator<String> elements = list.iterator();

        // hasNext : 데이터있음 True 아니면 False
        // next() : 다음데이터 리턴 
        while(element.hasNext()){
            System.out.println(elements.next());
        }
    } 
}
~~~

#### 응용하기 
- 제네릭 타입을 클래스 타입으로 지정하고 가지고 놀아보기 
- 방법은 같다 감을 익히자. 

~~~java
class Avengers{
    String name;
    String id;
    int age;

    // 생성자 
    public Avengers(String name, String id, int age){
        this.name = name;
        this.id = id;
        this.age = age;
    }
}


// Avenger클래스를 제네릭으로 ArrayList사용
public class ArrayListEx02{
    public static void main(String[] args){
        List<Avengers>list = new ArrayList<Avengers>();

        list.add(new Avengers("토니","아이언맨",50));
        list.add(new Avengers("피터 파커","스파이더맨",23));

        for(int i=0; list.size(); i++){
            Avengers av =list.get(i);
            System.out.println("이름 : " + av.name);
            System.out.println("-----");

        }
    }
}

~~~

### Vector
- ArrayList와 동일한 구조를 갖는다. 

### Vector vs ArrayList
- Vector는 자동 동기화를 보장하므로 멀티스레드 환경에서 안정적으로 사용가능하다. 
- 단일스레드에서는 ArrayList가 더 좋다. 

#### 생성방법
- 초기용량 증가용량 생략하면 0으로 설정 
~~~java
    List<E> list = new Vector([초기용량, 증가용량]);
~~~

#### 사용방법 
- 회원정보 관리를 예시로만들기  
~~~java
import java.util.*;

class MemberInfo{
    private int no;
    private String name;
    private String phoneNumber;
    private String address;

    public int getNo(){return no;}
    public void setNo(int no){this.no =no;}

    public String getName(){return name;}
    public void setName(String name){this.name = name;}

    public String getPhoneNumber(){return phoneNumber;}
    public void setPhonNumber(String phoneNumber){
        this.phoneNumber = phoneNumber;
        }
    public String getAddress(){return address;}
    public void setAddress(String address){
        this.address = address;}
}

public class VectorEx01{
    public static void main(String[] args){
        List<MemberInfo> list = new Vector<MemberInfo>();

        do{
            Scanner sc =new Scanner(System.in);
            System.out.println("회원번호 입력");
            int no = sc.nextInt();
            System.out.println("이름 입력");
            String name = sc.next();
            System.out.println("폰번호 입력");
            String phoneNumber = sc.next();
            System.out.println("주소 입력");
            String address = sc.next();  

            MemberInfo mm = new MemberInfo();
            mm.setNo(no);
            mm.setName(name);
            mm.setPhoneNumber(phoneNumber);
            mm.setAddress(address);

            list.add(mm);

            System.out.println("계속은 y, 아니면 아무키 입력");
            String answer = sc.next();

            if(asnwer.equals("y") || answer.equals("Y")){
                continue;
            }else{
                break;
            }

        }while(true); 
        for (int i=0; i<list.size(); i++){
            MemberInfo m =list.get(i);
            System.out.println("이름 : "+ m.getName() );
            System.out.println("----")
        }
    }
}
~~~


## LinkedList
- List의 구현클래스로 사용방법은 ArrayList(), Vector()와 동일하다. 


### LinkedList vs ArrayList , Vector

- ArrayList,Vector는 인덱스로 데이터를 관리
- 사용방법은 위와 동일하다. 


|         |순차적 추가,삭제|중간에 추가,삭제|검색|
|---------|------------|------------|---|
|ArrayList| 빠름        | 느림        |느림 |
|LinkedList| 느림       | 빠름        | 느림|



### 생성방법 
~~~java
    List<E> list = new LinkedList<E>();
~~~
### 사용방법
- 위와 동일해서 생략하겠습니다. 
### 참고 
- [다른 분의 블로그](https://m.blog.naver.com/PostView.nhn?blogId=heartflow89&logNo=220991199432&proxyReferer=https:%2F%2Fwww.google.co.kr%2F)
- [점프 투 자바](https://wikidocs.net/207)
### LinkedList 직접 구현하기 
[(Live Study)LinkedList 구현하기](../Java/LiveStudy[day4][LinkedList].md)
