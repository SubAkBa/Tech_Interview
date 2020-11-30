## JPA

#### JPA (Java Persistence API) 란?
자바 ORM (Object Relational Mapping) 기술 표준이다.

> JPA 인터페이스를 구현한 대표적인 오픈소스 프레임워크가 Hibernate이다.

<br />
<br />

#### JPA를 사용하는 이유?
(1) SQL 중심 개발의 경우 비즈니스 로직이 RDBMS에 의존하게 된다. JPA를 사용하면 자바 객체 중심으로 코드를 작성할 수 있어 생산성을 높일 수 있다.

(2) JPQL로 SQL을 추상화하고 DB Dialect를 지원하기 때문에 RDBMS 종류에 관계없이 동일한 쿼리를 작성하여 동일한 동작을 기대할 수 있다.