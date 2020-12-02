# 목표 


# 학습할 것
1. 프리미티브 타입 종류와 깞으 범위 그리고 기본값
2. 프리미티브 타입과 레퍼런스 타입
3. 리터럴
4. 변수 선언 및 초기화하는 방법
5. 변수의 스코프와 라이프타임
6. 타입 변환, 캐스틴 & 타입 프로모션
7. 1차, 2차 배열 선언
8. 타입 추론, var


# 1. 프리미티브 타입 종류와 깞으 범위 그리고 기본값
- primitive type은 자바에서 사용하는 기본적인 data타입이고  자료형이라 부른다. 

- 자바에서 사용하는 primitive type 8가지 
    1. boolean
    2. byte
    3. char
    4. short
    5. int
    6. long
    7. float
    7. double 
- primitive type은 고정된 값과 범위를 가지고 있다. (값은 bit, byte의 개념으로 나타난다.)
- 1bit는 0과 1로 표현하는 2진수, 8bit가 1byte

|        |  타입    | 할당되는 메모리 크기 | 기본값 | 데이터 표현 범위 |
|--------|---------|-----------------|------|--------------|
|  논리형  | boolean |  1byte          |false|   true, false |
|  정수형  | byte    |  1byte          | 0   |   -128 ~ 127       |
|        | short   |  2byte          | 0   |   -32,768 ~ 32,767  |
|        | int     |  4byte          | 0   |   -21억 ~ 21억 근사값 |
|        | long    |  8byte          | 0L  |     매우 많음,,|
|  실수형  | float   |  4byte          |0.0F |  매우 많음,,|
|        | double  |  8byte          | 0.0  |(1.7 * 10^-308 ~ 1.7 * 10^308)근사값 |
|  문자형  | char    |  2byte (유니코드) | '₩u0000' | 0 ~ 65,535  |

# 2. 프리미티브 타입 레퍼런스 타입 

- 프리미티브 타입은 값을 그대로 저장하는 반면 레퍼런스 타입은 어떤 값이 저장되어 있는 주소를값으로 갖는다. 

### 프리미티브 타입
- 기본값이 있기 때문에 Null이 존재하지 않는다. 
- 실제 값을 저장하는 공간으로 Stack메모리에 저장된다. 
- 컴파일 시점에 담을 수 있는 크기를 벗어나면 에러가 발생하는 "컴파일 에러"가 발생한다. 

### 레퍼런스 타입 
- 프리미티브 타입(기본형)을 제외한 모든 타입을 레퍼런스타입(참조형)이라고 한다. 
- 빈 객체를 의미하는 null이 존재한다. 
- 값이 저장되어 있는 곳의 주소값을 저장하는 공간으로 Heap 메모리에 저장된다. 
- 문법상에는 에러가 없지만 실행시켰을 때 에러가 나는 "런타임 에러"가 발생한다.
- 배열을 null값으로 받으면 "nullpointException"이 발생, 변수 값을 넣어야 한다. 
| 타입      | 예시                    | 기본값 | 할당되는 메모리 크기  |
|----------|------------------------|------|------------------|
|배열(Array)| int[] arr = new int[5];| Null | 4byte(객체의 주소값) |
|열거(Enumeration)|                  | NUll |                   |
|클래스(Class)| String str = "test";  | Null |                   |
|           |  Student sujin = new Student();|Null|           |
|인터페이스(interface) |               |Null|                    |



# 3. 리터럴
- 리터럴은 데이터 그 자체를 뜻한다. 
- 변수에 넣은 변하지 않는 데이터를 의미하다.

### 종류 
 - 정수 리터럴 : integer
 - 부동 소수점 : floating point
 - 불리언 : boolean
 - 문자 : character
 - 문자열 : string

# 4. 변수의 선언 초기화하는 방법
- 초기화 : 변수를 선언한 후 처음으로 값을 저장하는 것
- 데이터 타입 변수명 =  타입에 맞는 리터럴 

~~~java
    // 예시
    int a = 10;
    String name = "kimshin";  
~~~

# 5. 변수의 스코프와 라이프타임
- 라이프타임:  변수 or 레퍼런스의 유효범위를 말한다. 
- 변수의 스코프 : 변수에 접근할 수 있는 프로그램 영역을 가리킨다. 
- 라이프타임은 변수가 메모리에 얼마나 유지되어있는가 정도이다. 
- 즉, 스코프와 라이프타임은 얼마나 어디에 변수가 정의되어져 있는가를 의미하는 것과 같다. 

### 1. 인스턴스 변수 
- 클래스안에 있지만 다른 메서드 밖에 선언된 변수를 말한다. 
- scope :  static method를 제외한 클래스 어디서나 사용가능 
- lifetime : 클래스 객체가 메모리에 남아있을때까지

### 2. 클래스 변수 
- 클래스안에 선언되고 static으로 선언된 변수를 클래스변수라한다. 
- scope : 클래스안에 어디서나 사용가능 
- lifetime : 프로그램 끝날때까지

### 3. 지역벼수 
- 클래스변수와 인스턴스변수가아닌 모든 변수들을 지역변수라 한다. 
- scope : 선언된 블록안에서만 사용가능 
- lifetime : 블록이 컨트롤 될 때까지

~~~java
    ublic class scope_and_lifetime {
    int num1, num2;   //Instance Variables
    static int result;  //Class Variable
    int add(int a, int b){  //Local Variables
        num1 = a;
        num2 = b;
        return a+b;
    }
    public static void main(String args[]){
        scope_and_lifetime ob = new scope_and_lifetime();
        result = ob.add(10, 20);
        System.out.println("Sum = " + result);
    }
}
~~~

참고 : 
- https://www.learningjournal.guru/article/programming-in-java/scope-and-lifetime-of-a-variable/


# 6. 타입 변환, 캐스팅 그리고 타입 프로모션 
- 타임변환 : 어떤 값이나 변수의 타입을 다른 타입으로 변경하는 것.   
- 이떄 타입은 두가지로 변환된다. 
    1. 확장 (자동형변환)
    2. 축소 (명시적 형변항)

### 1. 자동적 형변환 (타입 프로모션)
- 두 데이터 타입이 자동으로 변환되는 경우이다 2가지 조건이 있다.
    1. 두 데이어 타입은 호환가능해야한다. 
    2. 더 작은 데이터 타입을 더 큰 범위의 타입에 할당할 떄만 동작한다.

- 자바에서숫자타입은 byte -> short -> int -> long -> float -> double순서로 자동 형변환 된다. 
~~~java
    class Test 
{ 
    public static void main(String[] args) 
    { 
        int i = 100;  
          
        // automatic type conversion 
        long l = i;  
          
        // automatic type conversion 
        float f = l;  
        System.out.println("Int value "+i); 
        System.out.println("Long value "+l); 
        System.out.println("Float value "+f); 
    } 
}
~~~

### 2. 명시적 형변환(casting)
- Casting은 더 큰 범위의 타입을 더 작은 범위의 타입에 할당하기 위해 반드시 축소(casting)해줘야 한다. 

- 이것은 자동형변환할 수 없는 뎅이터 유형에 사용할 수 있다. 
- 타입을 명시해줘서 강제적으로 형변환(캐스팅)해 주는 방법.
~~~java
    //Java program to illustrate explicit type conversion 
class Test 
{ 
    public static void main(String[] args) 
    { 
        double d = 100.04;  
          
        //explicit type casting 
        long l = (long)d; 
          
        //explicit type casting  
        int i = (int)l;  
        System.out.println("Double value "+d); 
          
        //fractional part lost 
        System.out.println("Long value "+l);  
          
        //fractional part lost 
        System.out.println("Int value "+i);  
    }  
}
~~~

# 7. 1차배열 & 2차배열 

- 배열 : 고정된 타입의 값을 저장시키는 컨테이너 객체이다.
- 처음만들떄 그 길이는 고정 
- 배열의 각 item들은 요소(element)라 부르고 각 요소들은 index로 접근한다. 


### 1차배열 예시
~~~java
    // 선언하는 방법
anArray = new int[10];

// 각 element에 값을 넣는 방법 
anArray[0] = 100; // initialize first element
anArray[1] = 200; // initialize second element
anArray[2] = 300; // and so forth

// 또 다른 방법 :  선언과 동시에 값을 넣는방법
int[] anArray = { 
    100, 200, 300,
    400, 500, 600, 
    700, 800, 900, 1000
};

int[] anArray = new int[] {100, 200, 300};
~~~


### 2차배열 예시 
~~~java
// 2차배열은 String[][]names로 선언 가능하다. 
String[][] names = {
            {"Mr. ", "Mrs. ", "Ms. "},
            {"Smith", "Jones"}
        };
        // Mr. Smith
        System.out.println(names[0][0] + names[1][0]);
        // Ms. Jones
        System.out.println(names[0][2] + names[1][1]);
    }

// 출력 결과 
Mr. Smith
Ms. Jones
~~~


# 8. 타입추론 var
- 타입추론 : 코드 작ㄱ성시 타입이 정해지지 않았지만 컴파일러가 그 타입을 유추하는 것이다. 
- 자바10부터 타입 추론을 지원하는 var키워드가 추가되었다. 
- var 키워드는 local variable이면서 선언과 동시에 initializer가 필수적으로 요구된다. 
- 컴파일러는 오른쪽 초기화 값으로 타입을 유추한다. 

~~~java

// java 9 이하 
string message = "data";
// java 10 이상 
var message = " the initializer present on the right-hand side";
~~~

참고 : 
- https://velog.io/@bk_log/Java-타입-추론