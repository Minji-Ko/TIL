### CHAP10

**예외**
-  에러 VS 예외 ?
    - 에러 : 컴퓨터 <u>하드웨어</u> 관련 고장으로 발생하는 응용프로그램 실행 오류
    - 예외 : 사용자의 잘못된 조작 또는 개발자의 잘못된 코딩으로 인해 프로그램 자체에서 발생하는 오류
    - 예외 발생 가능성이 높은 코드를 컴파일할 때 컴파일러는 예외 처리 유무 확인 ─> 예외 처리 프로그램 통해 정상 실행상태 유지 가능
- 일반 예외 (exception)
    - 컴파일러 체크 예외
    - 자바 소스 컴파일 과정에서 해당 예외 처리 코드가 있는지 검사
    - 예외의 상속관계
        ```mermaid
        stateDiagram
            Exception --> ClassNotFoundException 
            Exception --> InterruptedException  
            Exception --> etc
            Exception --> RuntimeException
        ```
- 실행 예외 (runtime exception)
    - 컴파일러 넌 체크 예외
    - 실행 시 예측할 수 없이 갑자기 발생하기에 컴파일 과정에서 예외처리코드 검사하지 않음
    - 실행 예외는 개발자의 경험에 의해서 예외 처리 코드를 작성해야 함
    - NullPointerException 
        - 가장 빈번하게 발생하는 실행 예외
        - 객체 참조가 없는 상태의 참조 변수로 객체 접근 연산자 도트를 사용할 경우 발생
        - `String str = null;   str.length();`
    - ArrayIndexOutOfBoundsException
        - 배열에서 인덱스 범위를 초과할 경우
        - `int[] arr ={1, 2, 3};   int result = arr[0] + arr[3];`
    - NumberFormatException
        - 문자열을 숫자로 변환하는 경우
    - ClassCastException
        - 상위 및 하위 클래스 그리고 구현클래스와 인터페이스 간 타입 변환 가능하고 그 외의 관계에서는 ClassCastException 발생


**예외 처리**
- 예외 처리 목적
    - 1) 프로그램의 갑작스러운 종료를 막고
    - 2) 정상실행을 유지할 수 있도록
- 예외 처리 코드 : 예외가 발생하고 나서 처리하는 코드
    - 자바 컴파일러는 <u>일반 예외</u>를 발생시키는 코드를 발견할 경우 예외 처리 코드를 강제로 요구
    - <u>실행 예외</u>는 컴파일러가 체크하지 않으므로 개발자가 경험으로 예외 처리 코드 작성
- try-catch-fianlly 블록
    ```java
    try {
        예외 발생가능 코드
    } catch(예외클래스 e){
        예외 처리
    } finally {
        항상 실행;
    }
    ```
    - 다중 catch : 발생하는 예외별로 예외 처리 코드를 다르게 함
    - 모든 예외는 Exception의 상속을 받음
    - 개발하는 동안에만 `e.printStackTrace();`를 사용하여 디버깅을 할 수 있음
- thorws 키워드
    - 메소드를 호출한 곳에서 다양한 방식으로 처리할 수 있도록 함
    - throws 키워드 뒤에는 떠넘길 예외 클래스를 쉼표로 구분하여 나열
    - main 메소드에 throws를 하면 JVM으로 예외를 떠넘기기에 사용자 입장에서 좋은 프로그램이 아님
