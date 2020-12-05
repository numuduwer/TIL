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



## 목차
1.  jetbrains Toolbox 설치, inteliJ 설치  
2.  gradle로 프로젝트 시작하기 
3.  gradle 프로젝트를 스프링부트 프로젝트로 변경 




# 3. gradle 프로젝트를 스프링부트 프로젝트로 변경

- build.gradle [변경 전]  
    ~~~java
    plugins {
        id 'java'
    }
    group 'com.jojoldu.book'
    version '1.0-SNAPSHOT'
    
    repositories {
     mavenCentral()
    }

    dependencies {
        testCompile group: 'junit', name: 'junit', version: '4.12'
    }

    ~~~
- build.gradle [변경 후]
    ~~~java
        bui
    ~~~