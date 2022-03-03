### CHAP11
**java.lang**
- java.lang 패키지는 자바 프로그램의 기본적인 클래스를 담은 패키지이다.
- java.lang 패키지의 클래스와 인터페이스는 import없이 사용할 수 있음

|클래스|용도|
|------|---|
|Object|자바 클래스의 최상위 클래스로 사용|
|System|시스템|
|Class|클래스를 메모리로 로딩할 때 사용|
|String|문자열을 저장하고 여러 가지 정보를 얻을 때 사용|
|Wrapper|기본 타입의 데이터를 갖는 객체를 만들 때 사용|
|Math|수학 함수를 이용할 때 사용|

**자바 API**
- 자바 라이브러리 
- 프로그램 개발에 자주 사용되는 자바에서 제공하는 클래스 및 인터페이스 모음
- API 도큐먼트를 통해 사용방법을 확인할 수 있다.
    - [Oracle help center](https://docs.oracle.com/en/java/javase/)
    - Eclipse 단어선택 후 F1
- Deprecated 가급적 사용하지 말 것

**Object 클래스**
- 객체 비교 `equals()`
    - equals() 메소드의 매개 타입은 Object로, 모든 객체가 매개값으로 대입될 수 있음
    - Object 클래스의 equals() 메소드는 비교 연산자인 ==와 동일 결과 리턴
    - equals() 메소드 재정의하는 경우
        - <u>두 객채의 필드값이 같은 동등 객체인지 비교하기 위해</u>
        - 두 객체의 필드가 모두 같으면 true를, 그렇지 않으면 false 리턴
        - equals() 메소드는 매개값이 기준 객체와 동일 타입 객체인지 먼저 확인 필요
- 객체 해시코드 `hashCode()`
    - 객체를 식별하는 하나의 정수값
    - Object 클래스의 객체 해시코드 메소드는 객체 메모리 번지 이용하여 만듦 => 객체마다 다른 값 
    - hashCode를 재정의 하는 경우
        - 두 객체가 동등한지 비교할 때 필요
- 객체 문자 정보 `toString()`
    - Object 클래스의 toString() 메소드는 객체의 문자정보 리턴 
        - 기본적으로 '클래스이름@16진수해시코드`로 구성된 문자 정보
        - println에 객체값을 주면 toString을 자동적으로 호출해서 그 결과를 출력함
            - `System.out.println(myPhone.toString())` = `System.out.println(myPhone)`
    - toString() 메소드를 재정의 하는 경우
        - 유익한 정보를 리턴하기 위해

**System 클래스**
- System 클래스의 모든 필드와 메소드는 정적 필드 및 메소드로 구성
- 프로그램 종료 `exit()`
    - exit() 메소드를 호출하여 JVM을 강제 종료
    - exit() 메소드가 지정하는 int 매개값을 종료 상태값이라 함
    - `exit();` VS `break;` for문만 빠져나옴
- 현재 시각 읽기 `currentTimeMills()`, `nanoTime()`
    - currentTimeMills() : 1/10^3단위 long값 리턴
    - nanoTime() : 1/10^9단위 long값 리턴

**Class 클래스**
- 자바는 클래스와 인터페이스의 메타 데이터를 Class 클래스로 관리
    - 메타 데이터 : 타입 이름, 파일 경로 정보, 필드 정보, 생성자 정보, 메소드 정보
- Class 객체 얻기
    - `Class clazz = 클래스이름.class`
    - `Class clazz2 = Class.forName("패키지..클래스이름");`
    - `Class clazz3 = 참조변수.getClass();`
- Class 경로 활용하여 리소스 절대 경로 얻기 `getResource()`
    - Class 객체는 파일 경로 정보를 가지고 있어 이 경로 활용해 다른 리소스 파일의 경로 얻을 수 있음

**String 클래스**
- 직접 String 객체 생성
- 문자추출 `charAt()`
- 문자열 비교 `equals()`