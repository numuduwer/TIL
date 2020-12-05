# [Ch.1] 인텔리제이로 스프링 부트시작하기

## 개발환경 
- JVA : jdk 1.8 
- inteliJ : Community 2020.2 
- springBoot : 2.1.7.RELEASE
- gradle :  4.10.2  (default 6버전 나중에 변경)


## 막힌 부분. 
1. 맥에서 인텔리제이 자동완성 불가 해결방법.
2. gradle 버전 다운그레이드 
3. JAVA_HOME 설정 



## Chapter1 목차
0. gradle로 프로젝트 시작하기 
1. gradle 프로젝트를 스프링부트 프로젝트로 변경 
2. github 연동 & gitignore




# 2. github 연동 & gitignore

## github 연동하기 

1.  맥기준 command + shift + A으로 action 검색창 열기 
2.  검색창에 github입력, "share project on github" 선택
3.  github 로그인하면 자동으로 github Repository 생긴다. 

4. .idea  디렉토리 파일을 제외한 파일을 커밋한다. 
5.  자동으로 push단계까지 거치면 내 github에서 확인 


## git ignore 

용도 : .ignore에 기입한 파일들은 깃에서 관리하지 않는다.

- .ignore 파일에 다음과 같이 입력
    ~~~git
    # Project exclude paths
    /.gradle/
    /.idea/
    ~~~

- 변경한 내용 반영하기 
    - command + K
- 내용 푸쉬하기 
    - command + Shift + K 

- 성공적으로 반영됐는지 github에서 확인하자. 

