## String vs StringBuilder vs StringBuffer

#### String
불변 (Immutable) 이라는 특징 때문에 String 객체는 한 번 생성되어 할당된 메모리 공간은 변하지 않는다.

> 기존에 생성된 문자열 객체에 +, concat 등을 통해 다른 문자열을 덧붙이는 경우  
> 기존 문자열에 붙이는 것이 아니라, 새로운 문자열 객체를 생성한 뒤 연결된 문자열을 저장하고 그 객체를 참조하도록 한다.

String 객체는 Heap 메모리 영역 (GC가 동작하는 영역) 에 생성되고, 기존 객체가 제거 되면 GC를 통해 회수한다.

<br />

##### 특징
1. 문자열 연산이 많은 경우, String 객체는 새로운 객체를 계속해서 생성하기 때문에 좋은 성능을 내지 못한다.  

2. Immutable 특성을 가지기 때문에 동기화를 생각할 필요가 없으며 (Thread-Safe), 조회 연산의 경우는 큰 장점을 가진다.

<br />
<br />

#### StringBuilder & StringBuffer
String 클래스와 다르게 문자열 연산을 수행하여 기존 객체의 공간이 부족하게 되면 버퍼 크기를 늘리며 동작한다. (Mutable)

<br />

##### 차이점

StringBuilder
> 쓰레드 동기화를 보장하지 않으며, 단일 쓰레드 환경에서는 StringBuffer보다 좋은 성능을 낸다. (동기화 관련 처리를 하지 않기 때문이다.)

StringBuffer
> 각 메소드별로 Synchronized Keyword가 존재하기 때문에 멀티쓰레드 환경에서 동기화를 지원한다.

