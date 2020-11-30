## JDK 8

##### 1. 람다 표현식 (Lambda Expression)
메소드를 하나의 식으로 표현한 것.
> 즉, 식별자 없이 실행할 수 있는 함수 표현식을 의미하며, 익명 함수 (Anonymous Function) 라고도 부른다.

<br />

메소드를 람다 표현식으로 표현하면 객체를 생성하지 않아도 메소드를 사용할 수 있다.
또한, 람다 표현식은 메서드의 매개변수로 전달될 수도 있고, 메소드의 결과값으로 반환될 수도 있다.

``` Java
Comparator<int[]> comp = new Comparator<>(){
    (a, b) -> Integer.compare(a[0], b[0]);
};
```

<br />
<br />

##### 2. 스트림 API (Stream API)
자바에서는 배열 또는 컬렉션을 이용하여 많은 양의 데이터를 저장한다.  
또한, 이렇게 저장된 데이터에 접근하기 위해 반복문이나 반복자 (Iterator) 를 사용한다.

하지만, 이렇게 작성된 코드는 단점이 존재한다.
> (1) 코드의 길이가 길어 가독성이 떨어진다.
>
> (2) 코드 재사용이 거의 불가능하다.
>
> (3) DB Query와 같이 정형화된 처리 패턴을 가지지 못해 데이터마다 다른 방법으로 접근해야 한다.

<br />

스트림 API는 위 문제점을 극복하기 위해 나온 것으로,  
데이터를 추상화하여 다루기 때문에 다양한 방식으로 저장된 데이터를 읽고 쓰기 위한 공통된 방법을 제공한다.
> 즉, 배열이나 컬렉션 뿐만 아니라 파일에 저장된 데이터도 모두 동일한 방법으로 다룰 수 있다.

```Java
List<Integer> list = new ArrayList<>();
list.forEach(i -> System.out.println(i + " "));
```

<br />
<br />

##### 3. java.time Package
JDK 1.1부터 제공된 Calendar 클래스는 날짜와 시간 정보를 얻을 수 있지만 일부 문제점이 있다.
> (1) Calendar 객체는 불변 객체가 아니라서 (Mutable) 값이 수정될 수 있다.
> 
> (2) 윤초와 같은 특수한 상황을 고려하지 않는다.  
> 윤초 (a leap second) : 세계가 공통으로 사용하는 세계협정시(UTC)의 토대가 되는 원자시계와 지구자전에 따른 태양시계의 오차를 맞추기 위해 더하거나 빼는 1초
>
> (3) 월 (Month) 을 나타낼 때, 1월 ~ 12월을 0 ~ 11로 표현해야 하는 불편함이 있다.

<br />
<br />

##### 4. Optional
null이 될 수도 있는 객체를 Wrapper로 감싸서 NPE (Null Pointer Exception) 를 예방하는 Wrapper 클래스이다.  
메소드의 반환 값이 절대 null이 아니라면 Optional을 사용하지 않는 것이 성능저하가 적다.
> 즉, Optional은 메소드의 결과가 null이 될 수 있고, 클라이언트가 이 상황을 처리해야 할 때 사용하는 것이 좋다.

<br />
<br />

##### 5. Interface 클래스에 구현체 작성
Interface가 변경되면 Interface를 구현하는 모든 클래스들이 해당 메소드를 구현해야 하는 문제가 발생하는데,  이러한 문제점을 해결하기 위해 등장했다.

default와 static 키워드를 사용해서 구현 메소드를 interface에 작성할 수 있다.

```Java
public interface Test {
    default int plus(int a, int b) {
        return a + b;
    }

    public static int multi(int a, int b) {
        return a * b;
    }
}
```

<br />
<br />

##### 6. 나즈혼 (Nashorn)
JVM에서 JS (JavaScript) 를 실행할 수 있게 해주는 JS 엔진인 나즈혼 (Nashorn) 은 기존에 사용되어 온 엔진인 리노에 비해 성능과 메모리 관리 면에서 크게 개선된 스크립트 엔진이며, jdk 8버전에 도입됐다.