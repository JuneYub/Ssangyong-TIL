17. 서브쿼리★★★
Select – 스칼라 서브쿼리
From – 인라인뷰 (메인 쿼리의 컬럼 사용 가능)
Where – 중첩 서브쿼리
Group by – 사용 불가
Having – 중첩 서브쿼리
Order by – 스칼라 서브쿼리
In – 서브쿼리 출력값들 or 조건
Any/some – 서브쿼리 출력값들중 가장 작거나 큰 값과 비교
All – any/some과 반대 개념
Exists – 서브쿼리내 select 절엔 뭐가 와도 상관 없다. Row가 있으면 true, 없으면 false
18. 집합연산자★★
Union 정렬O 중복제거O 느리다
Intersect 정렬O 교집합 느리다
Minus (except) 정렬O 차집합 느리다
Union all 정렬X 중복제거X 빠르다
19. DDL★★
Truncate – drop & create, 테이블 내부 구조는 남아 있으나 데이터가 모두 삭제 됨
Drop – 테이블 자체가 없어짐 (당연 데이터도 없음)
Delete – 데이터만 삭제
Rollback, commit 이랑 항상 같이 나옴
20. DML★
Insert – 데이터 넣는 명령, insert into 테이블 (col1, col2, col3..) values (‘11’, ‘22’, ‘33’..);
- values를 기준으로 좌우의 괄호속 개수가 맞는지
update – 데이터의 특정 행의 값을 변경 (delete & insert)
- update 테이블 set col = ‘값’ where col1 = ‘조건’;
delete – 데이터의 특정 행을 삭제
- delete from 테이블 where col = ‘조건’;
merge – 특정 데이터를 넣을 때 해당 테이블 키값을 기준으로 있으면 update, 없으면 insert를 한
다. (최근 기출)
위 문제 모두 commit, rollback, savepoint 와 주로 함께 출제 된다.
21. 제약조건★★★
PK – not null + unique
- 테이블당 하나의 PK를 가질 수 있음 (하나라는게 컬럼이 아님, 복합키 가능)
Not null – 해당 컬럼에 null이 올 수 없음
Unique – 해당 컬럼에 중복값이 올 수 없음
22. DCL
Grant, revoke 문법
- GRANT 시스템 권한명 [, 시스템 권한명 ... | 롤명] TO 유저명 [, 유저명... | 롤명 ... 
|PUBLIC | [WITH ADMIN OPTION];
- REVOKE { 권한명 [, 권한명...] ALL} ON 객체명 FROM {유저명 [, 유저명...] | 롤명(ROLE) | 
PUBLIC} [CASCADE CONSTRAINTS];
- Role은 객체
23. VIEW
- 독립성, 편의성, 보안성
- SQL을 저장하는 개념