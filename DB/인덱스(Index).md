## 인덱스 (Index)
RDBMS의 검색 속도를 높이기 위해 Table의 컬럼을 색인화하는 기술  

> 색인화 : 특정 내용이 들어 있는 정보를 쉽게 찾아볼 수 있도록 표지 따위를 넣거나 일정한 순서에 따라 배열  
> 예시로는 책의 맨 뒷장의 색인이 있으며, 이를 통해 원하는 키워드에 대한 페이지로 바로 이동 가능하다.

<br />

#### 자료구조
B+-Tree 인덱스 알고리즘
> 일반적으로 사용되는 인덱스 알고리즘이며, B+-Tree 인덱스는 컬럼의 값을 변형하지 않고 (사실 값의 앞부분만 잘라서 관리), 원래의 값을 이용해 인덱싱하는 알고리즘이다.

Hash 인덱스 알고리즘
> 컬럼의 값으로 해시 값을 계산해서 인덱싱하는 알고리즘으로 매우 빠른 검색을 지원한다.
>
> 하지만 값을 변형해서 인덱싱하므로, 특정 문자로 시작하는 값으로 검색을 하는 등 전방 일치와 같이 값의 일부만으로 검색하고자 할 때는 해시 인덱스를 사용할 수 없다.  
> 주로 메모리 기반의 데이터베이스에서 많이 사용한다.

왜 B-Tree를 사용?
> 데이터 접근 시간 복잡도가 O(1)인 Hash Table이 더 효과적인 것처럼 보이지만, Select 질의 연산에는 부등호 (<, >) 연산도 포함된다.  
> 즉, 등호 (=) 연산에 특화된 Hash Table은 부등호 연산에서 나쁜 성능을 보이기 때문에 DB 자료구조에 적합하지 않다.

<br />
<br />

#### 상황 분석
사용하면 좋은 경우
> where 절에서 자주 사용되는 Column
>
> Join에 자주 사용되는 Column

<br />

사용을 피해야 하는 경우
> Data 중복도가 높은 Column
>
> DML이 자주 일어나는 Column

<br />

DML이 발생했을 때의 상황
> INSERT
>
> 새로운 데이터가 추가되면서 인덱스도 추가해야되고, 기존 인덱스 페이지에 저장되어 있던 탐색 위치가 수정되어야 하므로 효율이 좋지 않다.

> UPDATE
>
> 인덱스는 UPDATE를 할 수 없기 때문에 DELETE 후에 INSERT 작업 (2배의 작업) 이 발생한다.

> DELETE
>
> 테이블에서는 데이터가 지워지고, 다른 데이터가 그 공간을 사용한다.  
> 인덱스에서는 데이터가 지워지지 않고, 사용안함 표시를 해둔다.  
> 결국 인덱스는 공간을 그대로 차지하여, 실제 데이터가 10만건이지만 데이터가 100만건 있는 결과를 초래할 수 있다.

<br />
<br />

#### 컬럼 선택 기준
1. 카디널리티 (Cardinality) (높을수록 좋다.)
컬럼에 사용되는 값의 다양성 정도, 즉 중복 수치를 나타내는 지표이다.
> 중복도가 높다면 카디널리티는 낮고, 중복도가 낮다면 카디널리티는 높다.

<br />

2. 선택도 (낮을수록 좋다.)
데이터에서 특정 값을 얼마나 잘 선택할 수 있는지 나타내는 지표이며, 5 ~ 10%가 적당하다.
> 선택도는 특정 필드값을 지정했을 때 선택되는 레코드 수를 테이블 전체 레코드 수로 나눈 것입니다.

<br />

3. 활용도 (높을수록 좋다.)
해당 컬럼이 실제 작업에서 얼마나 활용되는지를 나타내는 지표이다.

<br />

4. 중복도 (낮을수록 좋다.)
중복 인덱스 여부에 대한 지표이다.

<br />
<br />

#### 종류
키에 따른 인덱스
> (1) 기본 인덱스 (Primary Index) : 기본키를 포함하는 인덱스 (키의 순서가 레코드 순서를 결정한다.)  
> (2) 보조 인덱스 (Secondary Index) : 기본 인덱스 이외의 인덱스 (키의 순서가 레코드 순서를 의미하지는 않는다.)

<br />

파일 조직에 따른 인덱스
> (1) Clustered Index : 데이터 레코드의 물리적 순서가 그 파일에 대한 인덱스 엔트리 순서와 동일하게 (또는 유사하게) 유지되도록 구성된 인덱스  
> (2) Unclustered Index : 이외의 인덱스

<br />

데이터 범위에 따른 인덱스
> (1) 밀집 인덱스 (Dense Index) : 데이터 레코드 각각에 대해 하나의 인덱스 엔트리가 만들어진 인덱스  
> (2) 희소 인덱스 (Sparse Index) : 레코드 그룹 또는 데이터 블록에 대해 하나의 엔트리가 만들어진 인덱스
