## final

1. final class
해당 클래스를 다른 클래스에서 상속하지 못하도록 한다.

<br />

2. final method
해당 메소드를 오버라이딩 하지 못하도록 한다.

<br />

3. final variable
수정할 수 없는 변수 (상수) 값으로 설정된다. (Read-Only, Immutable)

<br />

4. finally
try / catch 블록이 종료될 때 항상 실행되는 코드 블록을 정의하기 위해 사용한다.
```Java
try {

} catch (Exception e) {

} finally {
    System.out.println("try / catch 문 종료");
}
```

<br />

5. finalize()
가비지 컬렉터가 더 이상 참조되지 않는 객체들을 메모리에서 삭제하겠다고 결정하는 순간 호출되는 메소드이다.
