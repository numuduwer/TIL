# 목표 
자바가 제공하는 다양한 연산자를 학습하세요. 
# 학습할 것

- 산술 연산자 
- 비트 연산자 
- 관계 연산자
- 논리 연산자
- instance of
- assignment(=) operator
- 화살표(->) 연산자 
- 3항 연산자
- 연산자 우선순위 
- java13. switch 연산


## 산술 연산자. 
산술 연산자는 사칙연산을 다루는 기본적인 연산자입니다. 
산술 연산자는 두 개의 피연산자를 가집니다.

### 산술 연산자 종류 

|        |                    |
|--------|------------------- |
| a + b  | 더하기               | 
| a - b  | 빼기                | 
| a * b  | 곱하기               | 
| a / b  | 나누기               | 
| a % b  | 나눈 나머지를 리턴함.   | 


### 증감 연산자?
피연산자를 1씩 증가 혹은 1씩감소시킬 때 사용하는 연산자입니다. 
|        |                    |
|--------|------------------- |
| ++x    | 피연산자 값을 1증가시킨 후에 연산.  | 
| x++    | 연산을 수행하고 나서 값을 1증가시킴. |         
| --x    | 피연산자 깞을 1감소기킨 후에 연산.  | 
| x--    | 연산을 수행하고 나서 값을 1 감소시킴.| 

참고
- http://www.tcpschool.com/c/c_operator_incAndDec

## 비트 연산자
비트 연산자는 비트(bit)단위로 연산을 할 때 사용하는 연산자입니다.   
그러므로 0과 1로 표현이 가능한 정수타입만 비트연산이 가능합니다.
비트 연산자는 기능에 따라 2가지로 구분합니다. 
1. 비트 이동연산자 (<<, >>, >>>)
2. 비트 논리연산자 (&,|, ^, ~)


### 1. 비트 이동연산자 (<<, >>, >>>)
정수데이터의 비트를 왼쪽 or 오른쪽으로 이동시키는 연산을 합니다. 

|           |                    |       |
|-----------|------------------- |-------|
| x << y    | 정수 x의 비트를 y만큼 왼쪽으로 이동 |빈자리는 0 | 
| x >> y    | 정수 x의 비트를 y만큼 오른쪽으로 이동| 빈자리는 비트정수의 최상위 부호비트 |     
| x >>> y   | 정수 x의 비트를 y만큼 오른쪽으로 이동|빈자리는 0 | 

- 예시 
~~~java
2 << 3     // case1

[0000000  00000000 00000000 00000010]    // 2
000[00000000 00000000 00000000 00010000] // 16 

// 2를 32비트로 분해한 다음 왼쪽으로 3비트를 이동시키는 연산이다.
// 왼쪽으로 3비트 이동할 때 맨왼쪽 3비트는 버려지고, 오른쪽은 0으로 채워진다.


~~~

~~~java
16 >> 3

[00000000 00000000 00000000 00010000]     // 16
[00000000 00000000 00000000 00000010]000  // 2

// 16을 32비트로 분해한다음 오른쪽으로 3비트를 이동시키는연산이다.
// 오른쪽 3비트는 밀려나서 버려지게 되고 맨 왼쪽은 동일한 값으로 채워진다.(양수라면 0 음수라면 1로 채워짐)


~~~

~~~java
-16 >>> 3

[11111111 11111111 1111111 11110000]       // 16
[00011111 11111111 1111111 11111110]000    // 536870910

// >>>연산은 오직 자바에만 있는 연산이며 >>와 기본적으로 원리는 같다.
// >> 연산꽈는 다르게 맨 왼쪽에는 최상위 부호비트와 관계없이 무조건 0으로 채워지게 된다.
// 그렇기에 무조건 양수값을 가진다. 


~~~


### 2.비트 논리연산자 (&,|, ^, ~)
비트(bit)단위로 논리 연산을 할 떄 사용하는연산자입니다. 
논리 연산할 두 값을 비트단위로 나열하고 각 자릿수를 연산. 

- 예시

~~~java
    // AND 연산(&)
    15  :   [0 0 0 0 1 1 1 1]
    25  :   [0 0 0 1 1 0 0 1]
        :   [0 0 0 0 1 0 0 1]  // 9로 계산

    // OR 연산(|)
    15  :   [0 0 0 0 1 1 1 1]
    25  :   [0 0 0 1 1 0 0 1]
        :   [0 0 0 1 1 1 1 1]  // 31로 계산

    // XOR 연산(^)
    15 :   [0 0 0 0 1 1 1 1]
    25 :   [0 0 0 1 1 0 0 1]
       :   [0 0 0 1 0 1 1 0]  // 22로 계산

    // 보수(~)
    // 보수연산은 이진수로 표현된 값을 반전(보수)시켜 표현한다.
    25  :   [0 0 0 1 1 0 0 1]  // 계산 전
    -26 :   [1 1 1 0 0 1 1 0]  // 계산 후
~~~
참고
- https://coding-factory.tistory.com/521



## 관계 연산자 
관계 연산자는 부등호와 같은 연산자입니다. 
연산결과는 boolean 자료형으로 리턴됩니다. 

|        |                    |
|--------|------------------- |
| a > b  |  왼쪽이 크면 True, 아니면 False| 
| a > b  | 왼쪽이 작으면 True, 아니면 False| 
| a >= b  |왼쪽이 크거나 같으면 True, 아니면 False| 
| a <= b  |오른쪽이 크거나 같으면 True, 아니면 False| 
| a == b  | 양쪽이 같으면 True, 아니면 False| 
| a != b  | 양쪽이 다르면 True, 아니면 False| 


## 논리 연산자
3가지 종류가 있으며 논리연산 결과는 boolean 자료형으로 리턴됩니다.
~~~java
// 논리 곱 
a && b   두 항이 모두 참이면 True, 아니면 False

// 논리 합 
a || b  두 항중 하나라도 참이면 True, 아니면 False

// 부정 
!(a>b)  결과가 참이면 False, 아니면 True
~~~

## instance of
instance of는 특정 객체가 다른 타입으로 형변환 가능한지 확인해주는 연산자 입니다.   
특정 클래스에 속해있는지 확일할 때 사용합니다.   
결과는 boolean타입으로 리턴합니다. 

예시
~~~java
class Dog extends Animal{
	public static void main(String args[]){
		Dog1 d = new Dog1();
		System.out.println(d instanceof Animal);  // True
	
	}
}
~~~


## assignment(=) operator
"=" 은 값을 변수에 할당할 때 사용합니다. 
예시 
~~~java
// int타입의 x라는 변수에 10의 값을 할당한다. 
int x = 10;
~~~

## 화살표(->) 연산자
람다 표현식이라 하고 식별자 없이 실행 가능한 함수를 표현할 때 사용됩니다.. 

### 나오게 된 배경 
- 기존 자바언어 체계에서는 함수형 언어를 지원하지 못했다. 
- java8에서 나온 람다 표현식을 통해 JAVA에서 함수형 프로그래밍 조건을 만족시킬 수 있게 되었다. 


### 람다 표현식 작성법 
~~~java
//(매개변수, ... ) -> {실행문 ... }
// 매개변수를 이용해서 중괄호 { } 바디를 실행한다는 뜻으로 해석하면 된다.
(int a, int b) -> {return a + b}
~~~

### 특징 
- 단순한 람다구문은 중괄호가 없어도 된다. 
- return이 없는 경우도 있다. 
- 매개변수에는 타입을 명시하지 않아도 된다. (타입추론)
- 컴파일럭가 람다식 문법을 익명 클래스로 변환한다. 즉 함수형 인터페이스를 컴파일러가 구현하도록 위임하는 형태라고 볼 수 있다. 

### 장점
- 코드를 간결하게 만든다. 
- 함수를 만드는 과정없이 한번에 처리하기에 코딩하는 시간이 줄어든다.
- 병렬 프로그래밍에 용이하다. 

### 단점
- 무명함수는 재사용이 불가능하다.
- 디버깅이 까다롭다.
- 지저분해질 수 있다. 
- 재귀로 만들 경우에는 부적합하다. 


### 예시 

1. 사람표현 
    ~~~java
    @FunctionalInterface
    interface Say{
	int something(int a,int b);
    }
    class Person{
	public void hi(Say line){
		int number = line.something(3,4);
	}
    }
    // 람다 사용 x 
    Person rin = new Person();
    rin.hi(new Say(){
	public int somthing(int a, int b){
		System.out.println("람다식 사용 x");
		System.out.println("number : " + a + +","+ b);
		return 7;
	}
    });

    // 람다 사용 0
    Person rin = new Person();
    rin.hi((a,b)->{
		System.out.println("람다식 사용 x");
		System.out.println("number : " + a + +","+ b);
		return 7;
        });

    ~~~
2. 숫자 더하기 
    ~~~java
    interface Compare{
	public int compareTo(int a, int b);
    }
    public class Ramda2{
	public static void exec(Compare com){
		int k = 10;
		int m = 20;
		int value = com.compareTo(k,m);
		System.out.println(value);
	}
	public static void main(Stringp[] args){
		exec((i,j)->{
			return i+j;
	});
    }
    ~~~

참고 
- http://www.tcpschool.com/java/java_lambda_concept
- https://skyoo2003.github.io/post/2016/11/09/java8-lambda-expression
- https://coding-factory.tistory.com/entry/Java-람다식Lambda-Expressions-사용법-예제
- https://dinfree.com/lecture/language/112_java_9.html

## 3항 연산자
말그대로 3개의 피연산자(항)을 갖는 연산자입니다. 
기존의 if문의 라인수를 줄여주어 가독성을 높일 수 있다. 

~~~java
//예시
// (조건문) : ? 참 : 거짓  
int a;

// 기존 if 방법
if(4<5){
	a = 40;
}else {
	a = 50; 
}
system.out.println(a); //50


// 3항 연산자 방법
int a = (4<5) ? 40 : 50; 
system.out.println(a); //5
~~~

## 연산자 우선순위 


|순위| 연산자  |  내용            |
|--|-------- |----------------------- |
|1 | (), []        |  괄호 / 대괄호      | 
|2 | ! ,~ , ++, -- |  부정 / 증감연산자   | 
|3 | * , / , %     |  곱셈 / 나눗셈      | 
|4 | +, -          |  덧셈 / 뺄셈       | 
|5 | << ,>>, >>>   |  비트 이동연산자     | 
|6 | <, <=, >, >=  |  관계 연산자        | 
|7 | ==, !=        |                  | 
|8 | &             |  비트 논리 연산자    | 
|9 | ^             |                  | 
|10| ㅣ             |                  | 
|11| &&            |  논리 곱           | 
|12| ㅣㅣ           |   논리 합          | 
|13| ? :           |  조건 연산자        | 
|14| =, +=, -=,*=,/=, <<= ,>>=,&=,^=,~=        |  대입 / 할당 연산자    | 



## java 13 switch 연산자 
java13버전부터 switch연산자를 쓸 때 ->를 써서 가독성을 높였다.   
"break"대신에 "yield"를 사용한다. 

예시 
~~~java
Day day = Day.WEDNESDAY;    
    System.out.println(
        switch (day) {
            case MONDAY, FRIDAY, SUNDAY -> 6;
            case TUESDAY                -> 7;
            case THURSDAY, SATURDAY     -> 8;
            case WEDNESDAY              -> 9;
            default -> throw new IllegalStateException("Invalid day: " + day);
        }
    );

~~~

yield를 이용해 값을 리턴한다. 
예시 
~~~java
Day day = Day.WEDNESDAY;
    int numLetters = switch (day) {
        case MONDAY:
        case FRIDAY:
        case SUNDAY:
            System.out.println(6);
            yield 6;
        case TUESDAY:
            System.out.println(7);
            yield 7;
        case THURSDAY:
        case SATURDAY:
            System.out.println(8);
            yield 8;
        case WEDNESDAY:
            System.out.println(9);
            yield 9;
        default:
            throw new IllegalStateException("Invalid day: " + day);
    };
    System.out.println(numLetters);
~~~

참고 
-https://docs.oracle.com/en/java/javase/13/language/switch-expressions.html