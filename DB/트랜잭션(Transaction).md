## 트랜잭션 (Transaction)
DB의 상태를 변화시키기 위해 수행하는 작업 단위

<br />

#### 특성
1. 원자성 (Atomicity)
> 트랜잭션이 DB에 모두 반영되거나 모두 반영되지 않아야 한다.

<br />

2. 일관성 (Consistency)
> 트랜잭션의 처리 결과는 항상 일관성 있어야 한다.  
> 즉, 트랜잭션이 진행되는 동안에 데이터베이스가 변경 되더라도 업데이트된 데이터베이스로 트랜잭션이 진행되는것이 아니라, 처음에 트랜잭션을 진행 하기 위해 참조한 데이터베이스로 진행된다.

<br />

3. 격리성 (Isolation)
> 둘 이상의 트랜잭션이 실행되고 있을 때, 어떤 트랜잭션도 다른 트랜잭션 연산에 끼어들 수 없다.

<br />

4. 지속성 (Durability)
> 트랜잭션이 성공적으로 완료되었다면, 결과는 영구적으로 반영되어야 한다.

<br />
<br />

#### Commit & Rollback
Commit 
> 하나의 트랜잭션이 성공적으로 끝났고 DB가 일관성있는 상태일 때, 이를 알려주기 위해 사용하는 연산이다.

<br />

Rollback
> 하나의 트랜잭션 처리가 비정상적으로 종료되어 트랜잭션의 원자성이 깨진 경우, 트랜잭션을 처음부터 다시 시작하거나 트랜잭션의 부분적으로만 연산된 결과를 취소시키는 연산이다.