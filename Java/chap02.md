2-4
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
- 입력된 모든 내용을 문자열로 읽음

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
- *`shift + tap` : 들여쓰기 해제*

---

### 3-1. 연산자와 연산식

#### 1) 연산식의 방향과 우선순위
- 단항(++, --, ~, !), 부호(+, -), 대입(=, +=, -=,*=, /=, %=)연산자만 **"←"** 방향연산
- 산술, 비교, 논리, 대입 연산자 순으로 우선순위
- 먼저 처리해야할 연산식은 **괄호( )** 사용  

### 3-2. 연산자의 종류
- 부호 연산자의 결과는 **int타입** 
- 증감 연산자만 사용시 위치는 상관없음 ++i; = i++;
- 증감 연산자와 다른 연산자 함께 사용시 ++i + 10; = (++i) + 10; 이거나 i++ + 10; = ++(i+10);
- `int x = 10;  z = x++;` → z = 10, x = 11 

- !는 boolean타입에만 사용

- 리터럴 간 연산은 컴파일 단계에서 수행하여 타입 변환 **없음**
- 비교 연산자 실수 타입 `0.1 == 0.1f`의 결과값은 **false**로 산출됨
    - 원인 : 실수의 저장방식인 부동 소수점 방식이 0.1을 정확히 표현
    - 해결 : 피연산자를 모두 float 혹은 정수 타입으로 변환하여 비교

- 문자열 비교는 == 대신 **equals()** 메소드 사용

```java
    int x = 10;
	int y = 20;
	int z = (++x) + (y--);
	System.out.println(z);
```