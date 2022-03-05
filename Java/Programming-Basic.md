### Chapter 01 자바를 시작하기 전에
---
#### 1. 자바 

> **자바의 특징**
- 운영체제에 독립적
- 객체지향언어
- 비교적 배우기 쉬움
- 자동 메모리 관리 > 가비지컬렉터
- 네트워크와 분산처리 지원
- 멀티쓰레드 지원
- 동적 로딩 지원

#### 2. 자바개발환경 구축
> **JDK : 자바개발도구**
- JDK 설치
    - bin 디렉토리 > 실행파일
        - *.dll : 독립 실행 불가능 
        - *.exe : 독립 실행 가능 > javac.exe / java.exe / javadoc.exe / ...
- 환경변수 설정 : 해당 디렉토리 내 파일을 경로없이 이름만으로 사용 
    - 시스템 > 정보 > 고급 > 환경변수 
    - `Add` : JAVA_HOME, C:\ ... \jdk-11.0.2
    - `Edit` : Path > %JAVA_HOME%\bin
    
> **Eclipse**
- eclipse.ini 
    - `Edit` : -vm ... > 소규모 자바도구의 경로를 수정하여 안정성 증가
- window > preference 
    - font : 가독성 높은 고정폭 폰트 선호 
    - encoding > UTF-8
    - theme

#### 3. 자바로 프로그램작성하기

>**Hello world!!**
1. 메모장
	- 코드 작성
	- 산출물(결과물) > "Hello.java" > Source Code File
	- 소스 파일은 프로그램이 아니다. > 텍스트 파일이다.
	- 프로그래밍 코드를 작성 > 프로그램 완성 > CPU에게 명령어 전달!!
	- 어떤 언어로 구성? > 자바(X) > 사람이 쓰는 언어로 구성(인간)
	- 소스 파일의 명령어의 실행 주체 > 컴퓨터(CPU) > 이진데이터(1, 0)

2. javac.exe Hello.java
	- 1차 컴파일
	- javac.exe 파일명
	- javac.exe > Java Compiler >  사람이 작성한 코드를 컴퓨터가 이해하는 코드로 번역 하는 프로그램
	- 번역 작업 실행 > Compile
	- 산출물 > "Hello.class" > 실행 파일(클래스 파일)
	- Hello.class > 컴퓨터 실행(바이너리 코드, 이진 데이터, 기계어, Machine Code)
    - 중간언어(IL) 산출물 > 실행파일(=프로그램)
	
3. java.exe Hello
	- 2차 컴파일, 인터프리터, JIT(Just in time) 컴파일러	//java - 2번의 번역
	- java.exe > Java Compiler, Java Interpreter, 실행기
	- java.exe 클래스명 > 최종 실행                         //산출물 없음
    - 최종적으로 운영체제에 적합한 기계어로 바꿔주는 번역 작업  

<br><br>
### Chapter 02 변수
---

#### 1. RAM (메모리) 
> **주 기억장치 RAM**
- 최소 저장단위 1byte = 8bit > 0~255
- 저장범위가 이미 규정되어 있음 > 1byte, 2byte, 4byte, 8byte 
- 프로그램이 필요로 하는 공간을 '연속적으로' 할당

#### 2. 자료형

> **기본형 Primitive type; 원시형, 값형**
1. 숫자형
    - **정수형**
        - `byte`    : 1byte(=8bit)   / 2^8 / -128~127
        - `short`  : 2byte(=16bit) / 2^16
        - `int`      : 4byte(=32bit) / 2^32
        - `long`    : 8byte(=64bit) / 2^64
    - **실수형**
        - `float`  : 4byte, 무제한, 단정도형(정밀도 > 유효한 숫자 저장할 범위)
        - `double` : 8byte, 무제한, 배정도형(단정도*2 정밀도)
2. 문자형
    - **문자형**
        - `char`    : 2byte / 유니코드 지원
3. 논리형
    - **논리형**
        - `boolean` : 1byte / 명제의 참, 거짓 / true(00000001), false(00000000)

> **참조형 Reference Type**  

<br>
#### 3. 변수

> **Variable : 변수** 
- 개념 : 개발자가 명령어를 사용하여 할당받은 메모리 공간
- 목적 : 원하는 데이터를 읽거나 쓰기위한 공간

### 2-4. 변수와 시스템 입출력
The **width** (p91) specifies the minimum number of characters in the output.

**throws Exception** (p93)

**Enter** (p94)
- CR(캐리지 리턴) = 13
- LF(라인 피드) = 10
[개발 용어 : 캐리지 리턴(CR), 라인 피드 (LF) 알아보기](https://jw910911.tistory.com/90)

**Scanner** (p95)
- `System.in.read()`의 단점 : 2개 이상의 키가 조합된 한글과 통 문자열을 읽지 못함 
- 자바는 위 단점을 보완하기 위한 Scanner 클래스를 제공
- import java.util.Scanner;
- 입력된 모든 내용을 **문자열**로 읽음
- String 변수를 다른 타입으로 변환시, 기존 String 변수 외의 **새로운 변수를 선언**해야 함
```java
...
import java.util.Scanner;
...
Scanner scanner = new Scanner(System.in);
String str1 = scanner.nextLine();
// Double num1 = Double.parseDouble(scanner.nextLine()); 
...
``` 


**print** (p98)
```java
package sec04.exam06.verify;

public class Exam01 {

    public static void main(String[] args) {
        
        String name = "김자바";
        int age = 25;
        String tel1="010", tel2="123", tel3="4567";
        System.out.println("이름: " + name);     // println은 ("문자열 %", variable) 형식아님 
        System.out.print("나이: " + age + "\n");		// print는 println과 다르게 띄어쓰기포함하지 않음
        System.out.printf("전화: %s-%s-%s", tel1, tel2, tel3); //String변수인지 int변수인지 잘 보아야 함.
    }
}
```
- `shift + tap` : 들여쓰기 해제

---

### 3-1. 연산자와 연산식

 연산식의 방향과 우선순위
- 단항(++, --, ~, !), 부호(+, -), 대입(=, +=, -=,*=, /=, %=)연산자만 **"←"** 방향연산
- 산술, 비교, 논리, 대입 연산자 순으로 우선순위
- 먼저 처리해야할 연산식은 **괄호( )** 사용  

### 3-2. 연산자의 종류
- 부호 연산자의 결과는 **int타입** 
^
- 증감 연산자만 사용시 위치는 상관없음 ++i; = i++;
- 증감 연산자와 다른 연산자 함께 사용시 ++i + 10; = (++i) + 10; 이거나 i++ + 10; = ++(i+10);
- `int x = 10;  z = x++;` → z = 10, x = 11 
^
- !는 boolean타입에만 사용
^
- 나눗셈(/) 사용시 변환되는 타입 주의
- 리터럴 간 연산은 컴파일 단계에서 수행하여 타입 변환 **없음**
^
- 비교 연산자 실수 타입 `0.1 == 0.1f`의 결과값은 **false**로 산출됨
    - 원인 : 실수의 저장방식인 부동 소수점 방식이 0.1을 정확히 표현하지 않음
    - 해결 : 피연산자를 모두 float 혹은 정수 타입으로 변환하여 비교
- 문자열 비교는 == 대신 **equals()** 메소드 사용

```java
int x = 10;
int y = 20;
int z = (++x) + (y--);
System.out.println(z);  //31
```
---
### 4-1. 조건문 : if , switch
- if 조건식 : true/false값을 산출하는 연산식 혹은 boolean타입 변수
- if, else if 문에서는 가장먼저 나온 true 실행문을 실행한 후 빠져나옴.

### 4-2. 반복문(looping) : for, while, do-while
**for, while** 
- for문은 반복 횟수를 알고 있을 때, while문은 조건에 따라 반복할 때 주로 사용

**do-while**
- do-while문은 블록 내부의 실행문을 우선 실행하고 그 결과에 따라서 반복 실행을 계속할지 결정 
- do-while문에서 while() 뒤에 반드시 세미콜론(;)

**break, continue**
- 주로 if문과 함께 사용
- 중첩된 반복문에서 break문은 가장 가까운 반복문만 종료하므로 바깥쪽 까지 종료하려면 바깥쪽 반복문에 이름(라벨)을 붙이고 `break 이름;`을 사용

`System.out.println()` : `System.out.print("\n")`과 같은 효과
---
### 5-1. 참조 타입과 참조 변수
**참조타입**
기본타입은 실제 값을 변수에 저장하지만, 참조타입은 번지를 통해 객체를 참조
- 바이트 코드 파일: 자바 소스 파일을 javac명령어로 컴파일한 파일
- JVM : 자바 가상 기계(Jave Virtual Machine)는 바이트 코드 파일을 운영체제를 위한 완전한 기계어로 번역하고 실행하는 역할을 함

★
== : 같은객체참조하는지 비교 (x)
equals() : 문자비교 (o)

### 5-2. 배열

**배열 복사**
System.arraycopy(Object src, int srcPos, Object dest, int destPos, int length) : 원본배열, 인덱스, 대상배열, 인덱스, 몇개

**향상된 for문**
for(타입 변수 : 배열){};

### 5-3. 열거 타입
**열거 타입**
열거 상수(한정된 값)을 저장하는 타임
**열거 타입 선언, 저장**
```java
public enum Week { MONDAY, TUESDAY... SUNDAY }

Week today = Week.SUNDAY;
```