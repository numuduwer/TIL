# 목표 
자바가 제공하는 다양한 연산자를 학습하세요. 
# 학습할 것

0. 자바의 특징
1. JVM 이란? 
2. 컴파일하는 방법 & 살행하는 방법
3. 바이트 코드란?
4. JIT컴파일러란? 동작방법? 
5. JVM 구성요소
6. jdk와 jre 차이 


# 0. 자바의 특징 
### "Write One, Run Anywhere"   
자바는 JVM이 설치된 어느 기계에서든 동작할 수 있다. 
자바는 컴파일러로 바이트 코드를 만들고, 바이트 코드를 JVM을 통해 기계어(바이너리코드)로 번역하기 때문에 어느 OS든지 동작이 가능하다. 
- 이 특성을 Portability 이식성이라 함. 

# 1. JVM 이란?
### "Java Virtual Machine" 
자바 프로그램이 실행되게 런타임 환경을 제공해주는 장치이다. 

> " A Java virtual machine is a virtual machine that enables a computer to run Java programs as well as programs written in other languages that are also compiled to Java bytecode. " - Wikipedia-

## JVM의 역할 
1. 자바 프로그램을어떤 OS에서든 런타임 환경을 제공하고 실행시켜 줍니다. 
2. 자바프로그램 메모리를 효과적으로 관리합니다. 

# 2. 컴파일하는 방법 & 살행하는 방법

### 컴파일이란?
 우리가 작성한 소스코드를 컴퓨터가 이해하는 기계어(바이너리 코드)로 바꾸어 주는 과정


 ### Java의 컴파일
 - 자바 파일(.java)을 자바 컴파일러(javac.exe)를 이용하여 JVM이 이해할 수 있는 바이트 코드(.class)바꿔준다. 
 - 런타임시 바이트 코드를 바이너리코드(기계어)로 바꿔주는데 이역할을 JVM이 한다.

 ### 컴파일하는 방법
 - javac 파일명.java

 ### 실행방법 
 - java 클래스명

 # 3. 바이트 코드란?
- JVM이 이해할 수 있는 언어로 변환된  자바 소스코드를 의미한다. 
- 자바 컴파일러에 의해 변환되는 코드의 명령어 크기가 1바이트라 바이트 코드로 불림
- 바이트 코드의 확장자는 .class

# 4. JIT 컴파일러 (Just in Time compiler)
- 자바 파일(.java)을 자바 컴파일러를 이용해 JVM이 이해할수있는 바이트코드(.class)로 바꿔준다. 
- 런타임 시 이 바이트코드(.class)를 기계어로 바꿔주느데 이 역할을 JVM에서 한다. 

이때 바이트코드(.class)변환하는 방식은 두가지가 있다.
1. 인터프리터 (interpreter)
2. JIT 컴파일러(just in time compiler)

### 인터프리터 (interpreter)
사용자가 작성한 소스코드를 한 문장씩 읽고 바로 기계어로 바꿔준다. 그 후에 변환된 코드 실행 
### JIT 컴파일러 
인터프리터 방식을 사용하다가 적당할 때 바이크 코드 전체를 기계어로 바꿔주는 방식을 말한다. 

java프로그램 실행시 인터프리터방식으로 하나씩 읽고 해석하기 때문에 추가로 읽어야 할 클래스파일이 있는 경우 느려질 수 있다.   
보다 좋은 실행속도를 내기위해 번역한 내용을 캐싱 해두었다가 동일한 메소드를 실행할 경우 번역하지 않고 캐싱된 내용을 실행해주는 것이 JIT컴파일러. 

[사진 이이이] 

# 5. JVM의 구성요소

1. Class Loader
2. Runtime Data Area
3. Execution Engine
4. Garbage Collector   
[tk dkdkdk wls] 


## 1.Class Loader
- JVM의 보조장치. 자바 클래스파일을 불러오는 역할을 한다. 
- 자바 프로그램을 실행시 처음 classLoader로부터 로드되어진다. 
- 예를들면 자바에서 코딩시 a.java파일이 생성된다면,   
1. .java 파일소스를 컴파일러(javac)가 컴파일하여 .class 클래스파일(바이트 코드)로 변환해준다.   
2. Class Loader는 이러한 class파일들만 모아 JVM이 운영체제로 부터 할당받은 메모리영역인 Runtime Data Area로 적재하는 역할을 한다. 

## 2. Runtime Data Area 
- JVM의 메모리 영역.
- 자바 어플리케이션 실행시 사용되는 데이터를 적재하는 영역이다. 
- 크게 5가지가 있다. 
    1. Method Area
    2. Heap Area
    3. Stack Area
    4. PC Register
    5. Native method stack 



### 1. Method Area
- static이 붙어있는 것들의 영역
- 프로그램 실행시 먼저 생성되고, 종료할때까지 남아있는 영역이다.

[적제되는 데이터들]
- 클래스 변수의 이름, 데이터 타입, 전근제어자 같은 필드정보
- 메서드 이름, 리턴타입, 파라미터같은 메서드 정보
- interface인지 class인지 판단하는 type정보 
- Constant pool (:문자상수, 타입, 필드, 객체참조가 저장됨)

### 2. Heap Area
- new 키워드로 생성ㅇ되는 모든 것들이 있다. (배열, 객체)
- 스스로 사라지지 않고 Garbage Collector가 참조되지 않으면 제거한다. 

### 3. Stack Area
- 실행중인 메서드들이 차지하는 메모리영역. (지역변수)
- 지역변수, 파라미터, 리턴값, 연상에 사용되는 임시 값들이 생성되는 영역이다.

~~~java
int a = 10; 
//->  stack 영역에 a라는 이름의  메모리를 만들고  10인 메모리 공간을 잡아둠.

Person p = new Person();
//->  Person p 는 stack 영역에 생성되고,  new Persone()는  Heap 영역에 생성된다.  
//    Person p는 Heap area의 주소값을 가지고 있다. 
~~~

### 4. PC Register
- Thread가 생성될 때마다 생성되는 영역
- 현재 쓰레드가 실행되는 부분의 주소와 명령을 저장하는 영역이다. 


### 5. Native method stack
- 자바언어 외 다른 네이티브 코드를 위한 메모리 영역
- 보통 C/ C++들의 코드를 수행하기 위한 영역이다. 

## 3. Execution Engine
- Class Loader에 의해 클래스들이 메머리에 적재되면 기계어단위로 변결해 명령어 단위로 실행하는 역할을 한다. 
- 내부적으로 인터프리티, JIT 컴파일러, Garbage Collecter가 있다.

## 4. 그외 Java Native InterFace
- c나 c++같은 다른언어로 만든 프로그램들과 소통할 수있는 인터페이스를 제공해주는프레임워크 

# 5. jdk와 jrd 차이 

## jre 
> Java Runtime Environment의 약자로 자바프로그램을 실행시켜주는 환경을 구성해주는 도구다. 
즉 JAVA개발안하더라도 JAVA 프로그램을 실행해주려면 JRE가 필요하다. 

### JDK
> Java Development Kit의 약자로 자바 개발에 필요한 툴킷을 제공하는 도구들이다.  개발하려면 JAVA를 실행해야하기 때문에 JDK안에는 JRE가 포함되어있다. 