# Mac에서 자바 버전 관리 (zsh)

## jdk 설치하기 

### 0. AdoptOpenJDK?
- AdoptOpenJDK는 사전의 prebuild 형태로 java binary를 제공하는 커뮤니티 크룹이다. 
- Mac뿐만 아니라 윈도우, 리눅스 환경도 제공한다. 
- [홈페이지](https://adoptopenjdk.net/)

### 1. homebrew를 사용한 AdoptOpenJDK 설치 
~~~
brew tap AdoptOpenJDK/openjdk
brew cask install <version>
~~~

version 에  원하는 버전에 맞게 넣자. 
- OpenJDK8 - adoptopenjdk8
- OpenJDK9 - adoptopenjdk9
- OpenJDK10 - adoptopenjdk10
- OpenJDK11 - adoptopenjdk11
- OpenJDK11 w/ OpenJ9 JVM - adoptopenjdk11-openj9


### 2. 설치됐는지 확인 
~~~
 /usr/libexec/java_home -V
~~~


## 버전 변경하기 (버전 관리)

### 1. 설치된 모든 JDK  확인하기 
~~~
 /usr/libexec/java_home -V
~~~

### 2. zsh에 JAVA_HOME 설정

.zshrc 설정파일 열기
~~~
vim ~/.zshrc
~~~
  

~~~
# JAVA Version Control 
javahome_usage() { 
echo "javahome - switch to different JDK version" echo "Usage: javahome [-h] [-v VERSION]" 
echo 
echo " -h : display usage" 
echo " -v : specific JDK version to switch" 
echo 
echo "Examples: " 
echo "># javahome -v 1.8 : switches to JDK8" 
echo "># javahome -v 12 : switches to JDK12" 
echo "># javahome : display all installed JDK and display 
current JDK" 
} 
javahome () { 
if [ "$1" = "-h" ] ; then 
        javahome_usage 
fi 
if [ "$#" -eq 0 ] ; then 
        /usr/libexec/java_home -V 
fi 
if [ "$#" -eq 2 ] && [ "$1" = "-v" ] ; then export JAVA_HOME=`/usr/libexec/java_home $@` 
echo "Setting JAVA_HOME:" $JAVA_HOME 
echo 
echo "Added JAVA_HOME/bin to PATH"                        PATH=$PATH:$JAVA_HOME/bin 
echo $PATH echo java -version fi 
}
~~~


### 3. 잘 적용됐나 확인

~~~
javahome
~~~

### 4. 바꾸기 (설치한 버전 입력 )
~~~
javahome -v 1.8 
~~~

### 참고 
[MAC OS에서 JAVA버전 관리하기](https://woolbro.tistory.com/2)