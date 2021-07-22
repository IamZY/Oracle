# Oracle

+ decode

  ```sql
  select count(*) "total",
  	count(decode(to_char(hire_date,'yyyy'),'1995',1,null)) "1995",
  	count(decode(to_char(hire_date,'yyyy'),'1996',1,null))"1996",
  	count(decode(to_char(hire_date,'yyyy'),'1997',1,null)) "1997",
  	count(decode(to_char(hire_date,'yyyy'),'1998',1,null)) "1998"
  from employees
  where to_char(hire_date,'yyyy') in ('1995','1996','1997','1998')
  ```

+ top-n分析

  ```sql
  select rn,employee_id,last_name,salary 
  from (
    select rownum rn,employee_id,last_name,salary 
    from 
    (
      select rownum,employee_id,last_name,salary
      from employees 
      order by salary desc
    )
  )
  where rn > 40 and rn <= 50
  ```

  