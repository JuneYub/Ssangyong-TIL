24. 그룹함수
- roll up
- cube
- groupingsets
- grouping
어떤 결과가 나오고 어떤 함수를 사용 했는지에 대한 문제 기출

ROLLUP
(GROUP BY에 있는 컬럼들을 오른쪽에서 왼쪽순으로 그룹 생성)
a, b 로 묶이는 그룹의 값
a 로 묶이는 그룹의 소계
전체합계
CUBE
(나올 수 있는 모든 경우의 수로 그룹 생성)
a, b 로 묶이는 그룹의 값
a 로 묶이는 그룹의 소계
b 로 묶이는 그룹의 소계
전체합계
*rollup(A,B) != rollup(B,A), cube(A,B) = cube(B,A)
25. TCL
Commit, rollback
- Auto commit, begin transaction (commit 기능 잠시 끄기) end 
26. 윈도우 함수
- rows between and 값이 증가한다.
rows between UNBOUNDED PRECEDING and CURRENT ROW) as "직업별 합계"
rows between 1 PRECEDING and 1 FOLLOWING) as "위아래합계"
- range between and 값이 동일하다
1. UNBOUNDED PRECEDING: 최종 출력될 값의 맨 처음 row의 값(Partition by 고려)
2. CURRENT ROW: 현재 row의 값
3. UNBOUNDED FOLLOWING: 최종 출력될 값의 맨 마지막 row의 값(Partition by 고려)
- Rank 1,1,3,4….
- Dense_rank 1,1,2,3…
- Partition by, order by
Row_number() over (partition by col1 order by col2)…
27. 계층형 함수★
prior 자식데이터 = 부모데이터
부모데이터에서 자식데이터로 가면 순방향
SELECT LEVEL, *순방향
 LPAD(' ', 4 * (LEVEL-1)) || 사원 사원,
 관리자,
 CONNECT_BY_ISLEAF ISLEAF
 FROM 사원
 START WITH 관리자 IS NULL
CONNECT BY PRIOR 사원 = 관리자;
SELECT LEVEL, *역방향
 LPAD(' ', 4 * (LEVEL-1)) || 사원 사원,
 관리자,
 CONNECT_BY_ISLEAF ISLEAF
 FROM 사원
 START WITH 사원 = 'D'
CONNECT BY PRIOR 관리자 = 사원;
