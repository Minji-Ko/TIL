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
- 자바의 최상위 부모 클래스, Object 클래스의 메소드는 모든 자바 객체에서 사용가능
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
- 운영체제의 일부 기능을 이용할 수 있음
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
- 바이트 배열로 변환 `getBytes()`
    - getBytes()의 메소드는 시스템의 기본 문자셋으로 인코딩 된 바이트 배열 리턴 (window > MS949)
    - getBytes(Charset charset) 메소드는 특정 문자셋으로 인코딩된 바이트 배열 리턴
    - 바이트 배열을 다시 문자열로 디코딩할 때에는 인코딩했던 문자셋으로 `String str1 = New String(bytes1 , "UTF-8")`
- 문자열 찾기 `indexOf()` `contains()`
- 문자열 길이 `length()`
- 문자열 대치 `replace()` *String은 문자열 한 번 입력하면 변경 불가
- 문자열 잘라내기 `substring(int beginIndex, int endIndex)` *int endIndex는 출력하지 않음
- 알파벳 소, 대문자 변경 `toLowerCase()`, `toUpperCase()`
- 문자열 앞뒤 공백 잘라내기 `trim()`
- 문자열 변환 `valueOf()` > 기본 타입의 값을 문자열로 변환

**Wrapper(포장) 클래스**
- 박싱: 기본 타입의 값을 내부에 두고 포장 객체로 만드는 과정
    - 포장하고 있는 기본 타입 값은 외부에서 변경할 수 없음
    - `Integer obj = new Integer(10);`, `Integer obj = Integer.valueOf(10);`
- 언박싱 : `intValue()`
- 자동박싱과 언박싱
    - 자동 박싱 > 포장 클래스 타입에 기본값이 대입될 경우 
    - 자동 언박싱 > 기본 타입에 포장 객체가 대입되는 경우
- 문자열을 기본 타입 값으로 변환 : `Integer.parseInt("1000");`  *박싱을 하지 않음
- 포장 값 비교 
    - `equals()`
    - == 과 != (번지비교) 사용하지 않는게 좋음
    ```java
    Integer obj1 = 300;
    Integer obj2 = 300;
    System.out.println(obj1 == obj2);    //false 

    Integer obj3 = 100;
    Integer obj4 = 100;
    System.out.println(obj3 == obj4);    //true > byte, short, int, char, boolean의 경우 자주 사용되므로 이전에 생성된 객체를 참조함 
    ```

**Math 클래스**
- 절대값    `Math.abs();`
- 올림값    `Math.ceil();`
- 버림값    `Math.floor();`
- 반올림값  `Math.round();`
- 가까운 정수의 실수값 `Math.rint();`

- 최대값    `Math.max(a,b);`
- 최소값    `Math.min(a,b);`
- 랜덤값    `Math.random();`


**Date 클래스**
- Date는 객체 간 날짜 정보를 주고받을 때 매개변수나 리턴타입으로 주로 사용 
- 원하는 날짜 형식의 문자열을 얻기 위해 java.text 패키지의 SimpleDataFormat 클래스와 함께 사용 `SimpleDateFormat sdf = new SimpleDateFormat("yyyy년 MM월 dd일 hh시 mm분 ss초");`
- format() 메소드 호출

**Calendar 클래스**
- 추상클래스이므로 new 연산자로 인스턴스 생성 불가
- getInstance() 메소드를 이용하여 Calendar 하위 객체 얻을 수 있음 `Calendar now = Calendar getInstance();`

    |리턴값|코드|
    |---|-------|
    |연도|`int year = now.get(Calendar.YEAR);`|
    |월|`int month = now.get(Calendar.MONTH) + 1;`|
    |일|`int day = now.get(Calendar.DATE_OF_MONTH);`|
    |요일|`int week = now.get(Calendar.DAY_OF_WEEK);`|
    |오전/오후|`int amPm = now.get(Calendar.AM_PM);`|
    |시|`int hour = now.get(Calendar.HOUR);`|
    |분|`int minute = now.get(Calendar.MINUTE);`|
    |초|`int second = now.get(Calendar.SECOND);`|


