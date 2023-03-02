1. SQL 연산순서★★★
From
Where
Group by
Having
Select
Order by
DML
- Select, insert, update, delete
DDL
- Alter, create, modify, drop
TCL
- Rollback, commit
DCL
- Grant, revoke
2. Distinct
어떤 컬럼값들의 중복을 제거 한 결과를 출력한다.
- Select distinct col from table;
- Select distinct col1, col2 from table; 의 경우엔 col1 과 col2의 값이 모두 같지 않은 것 만
출력한다. <주의>
-
3. Alias★★
Select 절에서 사용가능, where 절에서는 사용 불가!!!
Select col as name from table; = select col name from table;
4. concat
Select col1 + col2 + col3 from table; (SQL Server)
Select col1 || col2 || col3 from table; (oracle)
Select concat(col1, col2) from table; *연산자가 2개!! 기억!!
5. 논리연산자
1) NOT - ~가 아니다
2) AND – A 그리고 B (둘다 만족)
3) OR – A 또는 B (둘중 하나만 만족해도 OK!)

6. SQL 연산자★
A between B and C – B <= A <= C
A in (1,2,3) – A = 1 or A = 2 or A = 3
A like ‘_ble*’ – A의 값중 2,3,4번째 값이 ble 인 모든 데이터 출력
7. escape
and email like '@_%' escape '@'
*아무 문자나 가능
8. rownum, top
oracle에선 where절 옆에 rownum
SQL server의 경우 select 옆에 top
9. null의 정의★★★
모르는값, 정의되지 않은값 (공백이나 0 과는 다르다)
산술연산에서 null이 들어가게 되면 null이 출력된다.
*null + 2, null * 4, null + null 모두 결과는 null
조건절에 null이 들어가게되면 false를 반환 함.
*null=null, null=2
집계함수(sum, count, min, max…) 에서 null은 데이터 대상에서 제외 된다.
정렬시에는 오라클에서는 가장큰 것이 되고, SQL Server에서는 가장 작은 값이 된다.
Nvl(col, 0) – col이 널이면 0 반환 아니면 col 반환
Nvl2(col,1,0) – col이 null이면 0 반환, 아니면 1 반환
Isnull(col,0) – col이 널이면 0 반환 아니면 col 반환
Nullif(col,0) – col이 0이면 null 반환, 아니면 col 반환
Coalesce(col1, col2, col3..) – null 아닌 첫번째 값 반환
10. 정렬★★
- 느려질 수 있다.
- 가장 마지막에 실행
- null이 어디에 오는지.. 
컬럼명으로 정렬, 앞의 기준이 같을 때 그 다음 컬럼으로 정렬
기본값은 asc(오름차순), desc는 내림차순
Order by col1, col2 des