11. 숫자함수
Round(222.45, 1) 소수점 둘째자리에서 반올림하여 첫째자리까지 출력
Round(225.67, 0) 소수점 첫째자리에서 반올림하여 정수만 출력
-1 파라미터는 1의 자리에서 반올림하여 정수를 출력
Ceil(oracle) / ceiling(SQL Server) 올림함수, 파라미터 사용법은 round와 같음
Floor 버림 함수, 파라미터 사용법은 round와 같음
12. 문자함수★
Lower, upper – 소문자로, 대문자로
Trim, ltrim, rtrim – 양쪽공백제거, 왼쪽, 오른쪽 공백제거
Lpad, rpad – 특정 자리를 정하고, 왼쪽 / 오른쪽 의 공백을 채워주는 함수
- Select lpad(‘A’, 5, ‘*’) from dual;
- ****A, rpad면 A****
Substr – SELECT SUBSTR(‘korea’, 2, 2) FROM DUAL; or 이 출력
Instr - SELECT INSTR('CORPORATE FLOOR','PO') AS idx FROM DUAL; 4 가 출력
13. 날짜함수★
To_char – 날짜형 데이터를 문자로 출력
- Select to_char(sysdate, ‘YYYY-MM-DD’) from dual;
To_date – 문자형 데이터를 날짜형으로 출력
- select to_date('2022-09-22') from dual;
sysdate (oracle), getdate() (SQL Server)
13. 조건문★
Decode
- select decode(col1,’A’,1,’B’,2,3) from dual;
- col이 A면 1, B면 2, 아니면 3
case
case when col = ‘A’ then 1
 when col = ‘B’ then 2
 else 3 end; 서로 같다
case col when ‘A’ then 1
 when ‘B’ then 2
 else 3 end;

 14. 집계함수★★
Count, min, sum, max 등
- null은 포함되지 않는다
- (1, null, 2, 3, null) 의 데이터를 기준으로 결과는 다음과 같다.
◼ Count() – 3
◼ Sum() – 6
◼ Avg() – 2
◼ Min() – 1
◼ Max() – 3
Col1 Col2 Col3
null null 1
2 3 2
1 null null
Select sum(col1 + col2 + col3) from dual;
여기에서 먼저 sum을 생각하지말고 col1 + col2 + col3 을 먼저 생각해보면 첫번째 행은 null + 
null + 1이기에 null이 반환되고, 마지막 세번째 행도 마찬가지다.
그러므로, 두번째 행의 2 + 3 + 2의 값인 7이 결과가 된다.
반대로, sum(col1) + sum(col2) + sum(col3)의 값은 3 + 3 + 3 이므로 9가 출력이 된다.
이 차이를 알아야 한다.
15. 그룹바이 group by
집약기능을 가지고 있음 (다수의 행을 하나로 합침)
Group by 절에 온 컬럼만 select 절에 올 수 있음
16. join★★
Natural join
- 반드시 두 테이블 간의 동일한 이름, 타입을 가진 컬럼이 필요하다.
- 조인에 이용되는 컬럼은 명시하지 않아도 자동으로 조인에 사용된다.
- 동일한 이름을 갖는 컬럼이 있지만 데이터 타입이 다르면 에러가 발생한다.
- 조인하는 테이블 간의 동일 컬럼이 SELECT 절에 기술 되도 테이블 이름을 생략해야 한
다.
- select department_id 부서, department_name 부서이름, location_id 지역번호, city 도시
from departments
natural join locations
where city = 'Seattle';
Using
- USING 절은 조인에 사용될 컬럼을 지정한다.
- NATURAL 절과 USING 절은 함께 사용할 수 없다.
- 조인에 이용되지 않은 동일 이름을 가진 컬럼은 컬럼명 앞에 테이블명을 기술한다

- 조인 컬럼은 괄호로 묶어서 기술해야 한다.
- select department_id 부서번호, department_name 부서, location_id 지역번호, city 도시
from departments
join locations using (location_id);
left outer join
- from table a left outer join table b
on a.col = b.col 이것과 같은 오라클 sql 문법은
- from table a, table b
where a.col = b.col(+)
join 순서
- from a,b,c
a와 b가 join 되고, 그리고 c와 join 된다
