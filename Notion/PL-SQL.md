## TP1:

**Exercise 1:**

```SQL
DECLARE
  a NUMBER := 1;
  b NUMBER := 2;
  temp NUMBER;
BEGIN
  temp := a;
  a := b;
  b := temp;
END;
```

**Exercise 2:**

```SQL
DECLARE
  a NUMBER := 10;
  factorial NUMBER := 1;
BEGIN
  FOR i IN 1..a LOOP
    factorial := factorial * i;
  END LOOP;
  DBMS_OUTPUT.PUT_LINE('The factorial of ' || a || ' is ' || factorial);
END;
```

**Exercise 3:**

```SQL
DECLARE
  max_id NUMBER;
BEGIN
  SELECT MAX(id) INTO max_id FROM DEPARTMENTS;
  INSERT INTO DEPARTMENTS (id) VALUES (max_id + 10);
  COMMIT;
END;
```

**Exercise 4:**

```SQL
DECLARE
  max_service_number NUMBER;
BEGIN
  SELECT MAX(service_number) INTO max_service_number FROM DEPARTMENTS;
  DBMS_OUTPUT.PUT_LINE('Max service number is: ' || max_service_number);
END;
```

**Exercise 5:**

```SQL
DECLARE
  new_department DEPARTMENTS%ROWTYPE;
BEGIN
  SELECT * INTO new_department FROM DEPARTMENTS WHERE id = (SELECT MAX(id) FROM DEPARTMENTS);
  DBMS_OUTPUT.PUT_LINE('New department id is: ' || new_department.id);
END;
```

**Exercise 6:**

```SQL
DECLARE
  rows_updated NUMBER;
BEGIN
  UPDATE DEPARTMENTS SET location_id = 2500 WHERE id = (SELECT MAX(id) FROM DEPARTMENTS);
  rows_updated := SQL%ROWCOUNT;
  DBMS_OUTPUT.PUT_LINE('Rows updated: ' || rows_updated);
  COMMIT;
END;
```

**Exercise 7:**

```SQL
DECLARE
  last_name EMPLOYEES.last_name%TYPE := '&last_name';
  manager_id EMPLOYEES.manager_id%TYPE;
BEGIN
  SELECT manager_id INTO manager_id FROM EMPLOYEES WHERE last_name = last_name;
  DBMS_OUTPUT.PUT_LINE('Manager id is: ' || manager_id);
EXCEPTION
  WHEN NO_DATA_FOUND THEN
    DBMS_OUTPUT.PUT_LINE('No employee found with last name: ' || last_name);
END;
```

**Exercise 8:**

```SQL
DECLARE
  CURSOR emp_cur IS
    SELECT * FROM EMPLOYEES ORDER BY hire_date DESC FETCH FIRST 10 ROWS ONLY;
  emp_rec emp_cur%ROWTYPE;
BEGIN
  OPEN emp_cur;
  LOOP
    FETCH emp_cur INTO emp_rec;
    EXIT WHEN emp_cur%NOTFOUND;
    DBMS_OUTPUT.PUT_LINE('Employee: ' || emp_rec.first_name || ' ' || emp_rec.last_name);
  END LOOP;
  CLOSE emp_cur;
END;
```

## TP2:

Exercise 1:

```SQL
DECLARE
    v_department VARCHAR2(50) := 'Executive';
BEGIN
    FOR emp IN (SELECT * FROM employees WHERE department = v_department) LOOP
        DBMS_OUTPUT.PUT_LINE('Employee ID: ' || emp.employee_id || ', Name: ' || emp.employee_name || ', Salary: ' || emp.salary);
    END LOOP;
END;
```