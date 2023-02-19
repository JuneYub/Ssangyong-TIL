첫번째 직원 출력 프로시저

```
CREATE OR REPLACE first_emp AS
    emp_name VARCHAR2(20);
BEGIN
    SELECT first_name || ' ' || last_name INTO emp_name
    FROM employees WHERE employee_id = 100;
    DBMS_OUTPUT.PUT_LINE(emp_name);
END;
```

서버 출력 허용

```
SET SERVEROUTPUT ON;
```

프로시저 실행
```
EXECUTE first_emp();
```

직원 정보 출력 프로시저

```
CREATE OR REPLACE PROCEDURE print_emp (
     emp_id IN EMPLOYEES.EMPLOYEE_ID%TYPE
) AS
    emp_name VARCHAR2(20); -- 프리시저에서 사용할 변수
BEGIN
    SELECT first_name || ' ' || last_name INTO emp_name-출력 결과를 변수에 넣기
    FROM employees WHERE employee_id = emp_id; - 인자를 받은 값
    DBMS_OUTPUT.PUT_LINE(emp_name);
END;
```

직원 평균 salary 출력 프로시저

CREATE OR REPLACE PROCEDURE emp_avg_salary (
    avg_salary OUT NUMBER
) AS
BEGIN
    SELECT AVG(salary) INTO avg_salary
    FROM employees
END emp_avg_salary;

프로시저 실행
```
DECLARE
    avg_salary NUMBER;
BEGIN
    emp_avg_salary(avg_salary);
    DBMS_OUTPUT.PUT_LINE(avg_salary);
END;
```

IF ELSE 문 사용 프로시저
```
CREATE OR REPLACE PROCEDURE if_salary (
    salary IN NUMBER // 파라미터
) AS
    avg_salary NUMBER; --프로시저에서 사용할 변수
BEGIN
    SELECT AVG(salary) INTO avg_salary FROM employees;  
    --쿼리는 여기서 끝났음 평균연봉은 avg_salary에 담김

    IF salary >= avg_salary THEN
        DBMS_OUTPUT.PUT_LINE('평균 이상');
    ELSE
        DBMS_OUTPUT.PUT_LINE('평균 미만');
    END IF;
END;
```

WHILE문 사용 프로시저
```
CREATE OR REPLACE PROCEDURE while_print AS
    str VARCHAR(100);
    i NUMBER;
BEGIN
    i := 1;
    WHILE (i <= 10) LOOP
        str := '반복 횟수:' || '(' || i || ')';
        DBMS_OUTPUT.PUT_LINE(str);
        i := i + 1;
    END LOOP;
END;
```


