# 목표 
자바가 제공하는 제어문을 학습하세요. 
# 학습할 것
1. 선택문 
2. 반복문 

## 과제 
0. JUnit 5 학습하세요.
1. live-study 대시 보드를 만드는 코드를 작성하세요. 
2. LinkedList를 구현하세요.
3. Stack을 구현하세요.
4. 앞서 만든 ListNode를 사용해서 Stack을 구현하세요.
5. Queue를 구현하세요. 





# 제어문 

- 코드의 실행 흐름을 제어하는 구문. 
- 주어진 조건에 따라 명령을 수행하도록 하는 실행문이다. 3종류가 있다. 
- 1. 선택문 (switch / case)
- 2. 조건문 (if /else)
- 3. 반복문 (for/ while)


## 1. 선택문 (switch / case)

- 모든 값, 범위를 기반으로 하는 if조건문과 달리 열거돤 값 또는 문자, 문자열을 사용할 수 있다. 

- 예시
    ~~~java
        int num = 0;
        switch(num){
            case 1:
                System.out.println("Mac");
                break;
            case 2:
                System.out.println("Window");
                break;
            default:
                system.out.println("Linux")
        }
    ~~~

## 2. 조건문 (if / else)
- 특정 범위의 조건안에서 실행하는 제어문
- 예시 
    ~~~java
    if(num == 1){
        System.out.println("Mac");
    }else if(num == 2){
        System.out.println("Window");
    }else{
        system.out.println("Linux")
    }
    ~~~

## 3. 반복문 
- 블록안에 코드를 조건만큼 반복하는 실행문
- while 문
- do/ while 문
- for 문 
- for each문 



### while 문 예시
~~~java
    int i = 0;
    while(i<5){
        System.out.println(i);
        i++;
    }
~~~

### do / while문 예시
~~~java
    int i = 0;
    do {
        System.out.println(i);
        i++;
    }
    while(i<5);
~~~

### for 문 
~~~java
    for(int i =0; i<5; i++){
        System.out.println(i);
    }
~~~

### for each 문
- 배열에서 특정 index값을 구할때 쓴다. 
- 가독성이 더 좋다. 
~~~java
String [] number = {"one","two","tree"};

//기존 for문 예시 
for (int i =0; i<number.length; i++){
    System.out.println(number[i]);
}

//for each 문
for (String number: numbers){
    System.out.println(number);
}
~~~


# 과제 
## 0. JUnit 5 학습하세요.
## 1. live-study 대시 보드를 만드는 코드를 작성하세요. 
## 2. LinkedList를 구현하세요.
[LinkedList 공부중](https://github.com/numuduwer/TIL/tree/main/Java/LiveStudy[day4][LinkedList].md)
## 3. Stack을 구현하세요.
## 4. 앞서 만든 ListNode를 사용해서 Stack을 구현하세요.
## 5. Queue를 구현하세요. 