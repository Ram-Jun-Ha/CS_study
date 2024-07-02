1. Error
    - 일반적으로 프로그램에서 복구할 수 없는 심각한 문제를 나타내는 시스템 수준의 오류
    - 종류
        1. 논리적 에러(logical error)
            - 실행은 되지만 의도와 다르게 동작하는 에러
            - 이른바 버그로, 실제 동작은 하지만 개발자의 의도와 다르게 동작하여 서비스 운영에 지장을 줄 수 있음
        2. 컴파일 에러(compile error)
            - 컴파일 시 컴파일러가 발견하는 에러
            - 대표적인 예로는 문법 구문 오류가 있음
        3. 런타임 에러(runtime error)
            - 실행 시 발견하는 에러로 프로그램이 비정상적으로 작동함
            - 런타임 에러의 예로는 StackOverflowError, OutOfMemoryError 등이 있음
2. Exception
    - 프로그램 실행 중 발생하는 예외적인 상황을 처리하기 위해 사용되는 복구 가능한 오류
    - 예외 처리(exception handling)
        - 프로그램 실행 시 발생할 수 있는 예기치 못한 예외의 발생에 대비한 코드를 작성하는 행위
        - 예외에 대한 대비코드를 미리 만들어 놓음으로 써 비정상적인 동작과 종료를 대비할 수 있음
      ![img_6.png](img%2Fimg_6.png)
   >Throwable class 
   > - error 와 exception 클래스의 부모 클래스
    >- 오류나 에러에 대한 메세지를 담는 것이 역할
   >- 대표적인 메서드로는 getMessage() 와 printStackTrace() 가 있음
- RuntimeException : 프로그래머의 실수로 발생하는 에러
    - NullPointerException : null 참조변수를 사용하여 객체의 메서드나 속성에 접근하려고 할 때 발생
    - ArrayIndexOutOfBoundsException : 배열의 범위를 벗어난 인덱스에 접근하려할 때 발생
    - ArithmeticException : 수학적 연산 오류시 발생
    - ClassCastException : 객체를 잘못된 타입으로 캐스팅 시 발생
    - IllegalArgumentException : 메서드에 잘못된 인자를 전달했을 때 발생
    - IllegalStateException : 메서드가 객체의 상태와 맞지 않은 호출을 했을 때 발생
    - NumberFormatException : 문자열을 숫자로 변환시 문자열이 올바를 형식의 숫자가 아닌 경우 발생
    - IndexOutOfBoundsException : 인덱스 범위가 벗어날 때 발생
    - UnsupportedOperationException : 호출된 메서드가 지원하지 않은 연산을 할 때 발생
    - ConcurrentModificationException : 컬렉션 수정 시 반복자가 잘 못 사용될 때 발생
    - NegativeArraySizeException : 배열의 크기를 음수로 지정할 때 발생
    - SecurityException : 보안 관리자에 의해 허용되지 않는 동작을 수행하려 할 때 발생
    - TypeNotPresentException : 컴파일 타임에 결정된 타입이 런타임에 사용할 수 없을 때 발생
    - EnumConstantNotPresentException : 열거형 타입에 정의되지 않은 열거형 상수를 사용시 발생
- Checked Exception vs Unchecked Exception
    - ‘반드시 에외처리를 해야하는가’ 의 여부로 구분

  |  | Checked Exception | Unchecked Exception |
      | --- | --- | --- |
  | 예외 처리 필수 여부 | O | X |
  | 확인 시점 | 컴파일 | 런타임 |
  | 예외종류 | RuntimeException을 제외한 예외들 | RuntimeException의 하위 예외들 |
    - Checked Exception은 try-catch문으로 감싸 예외처리를 해야하나 Unchecked Exception로 바꿔주면 예외처리를 하지 않아도 됨
  
``` JAVA
class MyCheckedException extends Exception { ... } // checked excpetion

public class Main {
    public static void main(String[] args) {
            install();
    }

    public static void install() {
        throw new RuntimeException(new IOException("설치할 공간이 부족합니다."));
        // Checked 예외인 IOException을 Unchecked 예외인 RuntimeException으로 감싸 Unchecked 예외로 변신 시킨다
    }
}
```