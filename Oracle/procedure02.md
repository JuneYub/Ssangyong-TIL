```
CREATE OR REPLACE PROCEDURE pcd_empInfo
(p_employee_id IN number)
is
    v_employee_id number(5);
    v_ename varchar2(50);
    v_gender Nvarchar2(1);
    v_monthsal varchar2(10);
    v_age   number(3);

begin
    select employee_id
        , first_name || ' ' || last_name
        , case when substr(jubun, 7, 1) in ('1', '3') then '남' else '여' end
        , to_char( nvl(salary + (salary * commission_pct), salary), '9,999,999')
        , extract(year from sysdate) - (to_number(substr(jubun, 1, 2)) + case when substr(jubun, 7, 1) in ('1', '2') then 1900 else 2000 end ) + 1 into
        v_employee_id, v_ename, v_gender, v_monthsal, v_age

    from employees
    where employee_id = p_employee_id;

    dbms_output.put_line( lpad('-', 40, '-') );
    dbms_output.put_line('사원번호 사원명 성별 월급 나이' );
    dbms_output.put_line( v_employee_id || ' ' || v_ename || ' ' || v_gender || ' ' || v_monthsal || ' ' || v_age);
```

주민번호를 입력받아서 성별을 알려주는 funct_gender

```
create or replace function func_gender
(p_jubun in varchar2)
return Nvarchar2
is
    v_result Nvarchar2(1);
begin
    select case when substr(p_jubun, 7, 1) in ('1', '3') then '남' else '여' end into v_result
    from dual;

    return v_result;
end func_gender;
```

주민등록번호에서 나이 가져오기
```
create or replace function func_age_2
(p_jubun in varchar2)
return number
is
    v_result number(3);
begin
    v_result := extract(year from sysdate) - ( case when substr(p_jubun, 7, 1) in ('1', '2') then 1900 else 2000 end + to_number( substr(p_jubun, 1, 2) ) ) + 1;
    return v_result;
end func_age_2;
```


```
    create or replace function func_retirement_day
    (p_jubun in varchar2)
    return date
    is
        v_retirement_day date;
    begin
        select last_day( to_date( to_char( add_months(sysdate, (63 - func_age(p_jubun)) * 12 ) , 'yyyy' ) ||
        case when substr(p_jubun, 3, 2) between '03' and '08' then '-08-01' else '-02-01' end
        , 'yyyy-mm-dd') )
        into v_retirement_day
    from dual;

    return v_retirement_day;
end func_retirement_day;

```

사원번호를 입력하면 사원번호, 부서명, 사원명, 입사일자, 성별 나이가 나오도록 하는 프로시저
```

   create or replace procedure pcd_employees_info
   (p_employee_id  IN  employees.employee_id%type)
   is
      v_employee_id       employees.employee_id%type;
      v_department_name   departments.department_name%type;
      v_ename             varchar2(30);
      v_hire_date         varchar2(10);
      v_gender            Nvarchar2(1);
      v_age               number(3);
   
   begin
       WITH 
       E AS
       (
          select employee_id
               , first_name || ' ' || last_name AS ENAME
               , hire_date
               , func_gender(jubun) AS GENDER
               , func_age(jubun) AS AGE
               , department_id
          from employees
          where employee_id = p_employee_id
       )
       select E.employee_id, nvl(D.department_name, '대기발령') , E.ename, to_char(E.hire_date, 'yyyy-mm-dd'), E.gender, E.age
              INTO 
              v_employee_id, v_department_name, v_ename, v_hire_date, v_gender, v_age 
       from E LEFT JOIN departments D
       on E.department_id = D.department_id;
       
       dbms_output.put_line( lpad('-', 50, '-') );
       dbms_output.put_line( '사원번호  부서명   사원명   입사일자  성별   나이' );
       dbms_output.put_line( lpad('-', 50, '-') );
   
       dbms_output.put_line(v_employee_id || ' ' || 
                            v_department_name || ' ' || 
                            v_ename || ' ' || 
                            v_hire_date || ' ' || 
                            v_gender || ' ' || 
                            v_age);
   
   end pcd_employees_info;
```