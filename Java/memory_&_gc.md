# 자바의 메모리 관리 및 GC

## 1. 자바의 메모리 관리

자바는 자동 메모리 관리 기능을 제공하기 때문에 개발자가 메모리의 할당과 해제를 직접 관리하지 않아도 되는 고급 언어에 속한다. 대표적인 예시가 후술할 자바의 **가비지 컬렉션(Garbage Collection)** 으로 참조되지 않는 객체를 자동으로 정리한다.

자바의 메모리 관리는 동적으로 할당된 객체가 저장되는 **힙(heap) 영역**과 메소드 호출 및 지역 변수 등을 저장하는 **스택(stack) 영역**으로 나뉘는데 이 중 힙의 메모리 설정과 관련된 옵션으로 **Xmx**와 **Xms**가 있다.

<p align="center">
<img src="./img/1.png" alt="img1" />
</p>

### Xmx & Xms

우선 Xms는 초기 힙 메모리 크기를 지정하며, JVM이 시작될 때 할당하는 힙 메모리의 크기를 설정한다. Xmx는 최대 힙 메모리 크기를 지정하며, JVM이 앱 실행 중에 할당할 수 있는 최대 힙 메모리의 크기를 설정한다.

이 두 설정이 필요한 이유는 JVM이 기본적으로 메모리가 부족하게 되면 OS에 메모리를 추가 요청하는 방식으로 힙 사이즈를 조정하기 때문이다. 이때 GC가 발생하게 되고, JVM은 필요한 만큼 힙사이즈를 늘려가게 된다.

이렇게 조정하다가 만약 머신의 물리 메모리 사이즈를 넘어가게 되면 가상 메모리를 사용하면서 swap space로 swap in - out 을 하게 되고, 이는 추후 성능의 문제로 이어질 수 있다.

```java
java -Xms2048m -Xmx2048m -jar app.jar
```
위와 같은 명령어를 통해 `app.jar` 앱을 실행할 때, 초기 메모리 및 최대 메모리 설정을 직접 지정해줄 수 있다.

## 2. 