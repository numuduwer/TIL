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
0.  gradle로 프로젝트 시작하기 
1.  gradle 프로젝트를 스프링부트 프로젝트로 변경 




# 1. gradle 프로젝트를 스프링부트 프로젝트로 변경

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
        buildscript {
            // ext:   build.gradle에서 사용하는 전역변수를 설정하는 키워드.
            // springBootVersion을 전역변수로 생성하고 값을 2.1.7.RELEASE로 하겠다. 
            // 즉 이놈을 의존성으로 받겠다는 의미.
            ext {
                springBootVersion = '2.1.7.RELEASE'
        }

        // repositories : 각종 의존성들을 어떤 원격 저장소에서 받을지 정해줌
        //   1. mavenCentral 2.jcenter 일단 둘다 등록
        repositories {
            mavenCentral()
            jcenter()
        }

    // dependencies : 프로젝트 개발에 필요한 의존성들을 선언하는 곳 밑에서 설명. 
    dependencies {
        classpath("org.springframework.boot:spring-boot-gradle-plugin:${springBootVersion}")
        }
    }

    // 자바와 스프링부트를 사용하려면 반드시 추가해줘야 되는 플러그인 4가지
    apply plugin: 'java'
    apply plugin: 'eclipse'
    apply plugin: 'org.springframework.boot'

    // 스프링 부트의 의존성을 관리해주는 플러그인. 
    apply plugin: 'io.spring.dependency-management'


    group 'com.jojoldu.book'
    version '1.0-SNAPSHOT'
    sourceCompatibility = 1.8

    repositories {
        mavenCentral()
    }
    // dependencies : 프로젝트 개발에 필요한 의존성들을 선언하는 곳.
    // 이 둘을 받도록 선언되어있음.  
    dependencies {
        compile ('org.springframework.boot:spring-boot-starter-web')
        testCompile('org.springframework.boot:spring-boot-starter-test')

    }
    ~~~
    
    ### 결과
    <img width="650" alt="스크린샷 2020-12-05 오후 2 45 58" src="https://user-images.githubusercontent.com/33523029/101236741-f0946f80-3716-11eb-98b3-d8f96e0d294b.png">
