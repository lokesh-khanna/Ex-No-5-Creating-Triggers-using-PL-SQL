# Ex. No: 5 Creating Triggers using PL/SQL
### AIM: 
To create a Trigger using PL/SQL.
### Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
3. Create a trigger named as log_salary-update.
4. Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.
5. End the trigger.
6. Update the salary of an employee in employee table.
7. Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.
8. Display the employee table, salary_log table.
### Program:
 # Create worker table
```
CREATE TABLE worker
(
empid NUMBER,
empname VARCHAR2(10)
dept VARCHAR2(10),
salary NUMBER
);
);
```
### Create salary_log table
```
CREATE TABLE vj_log
(
log_id NUMBER GENERATED ALWAYS AS IDENTITY,
empid NUMBER,
empname VARCHAR2(10),
old_salary NUMBER,
new_salary NUMBER,
update_date DATE
);
```
### PLSQL Trigger code
```
-- Create the trigger
CREATE OR REPLACE TRIGGER log_sal_update
BEFORE UPDATE ON employed
FOR EACH ROW
BEGIN
  IF :OLD.salary != :NEW.salary THEN
    INSERT INTO sal_log (empid, empname, old_salary, new_salary, update_date)
    VALUES (:OLD.empid, :OLD.empname, :OLD.salary, :NEW.salary, SYSDATE);
  END IF;
END;
/
-- Insert the values in the employee table
insert into worker values(1,'lokesh','sales',10000);
insert into worker values(2,'khanna','manager',20000);
insert into worker values(3,'lokeshr','hr',30000);
-- Update the salary of an employee
UPDATE worker
set salary = 12000
where empid=3;
-- Display the employee table
select * from worker;
-- Display the salary_log table
select * from vj_log;
```
### Output:
![image](https://github.com/lokesh-khanna/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/119606216/8789c0c9-df96-453a-8a86-d23239ec5fad)

### Result:
Thus , the output has been successfully verified.
