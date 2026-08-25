# Experiment 7: PL/SQL – Variables, Control Structures and Loops

## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.


## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:
- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

# PL/SQL Programs – Steps and Expected Output

## 1. Write a PL/SQL program to find the Greatest of Two Numbers

### Steps:
- Declare two numeric variables and initialize them.
- Use an `IF` statement to compare the values.
- Display the greater number using `DBMS_OUTPUT.PUT_LINE`.
### Syntax:
```sql
DECLARE
    num1 NUMBER := 80;  -- First number
    num2 NUMBER := 50;  -- Second number
BEGIN
    IF num1 > num2 THEN
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num1);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num2);
    END IF;
END;
```

**Expected Output:**  
Greater number is: 80

### Output:

<img width="169" height="34" alt="image" src="https://github.com/user-attachments/assets/66056e30-3265-429b-a586-cfcc858f9814" />




---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

### Program:

```sql
DECLARE
    n NUMBER := 10; -- number of terms
    sum NUMBER := 0;
    i NUMBER := 1;
BEGIN
    WHILE i <= n LOOP
        sum := sum + i;
        i := i + 1;
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || ' natural numbers is: ' || sum);
END;
/

```



**Expected Output:**  
Sum of first 10 natural numbers is: 55

### Output:

<img width="269" height="37" alt="image" src="https://github.com/user-attachments/assets/1b00d7e4-5b3a-4a7f-885f-19b8c9f5ac4e" />


---

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.
### Program:
```sql
DECLARE
    n NUMBER := 7; -- number of terms
    a NUMBER := 0;
    b NUMBER := 1;
    c NUMBER;
    fib_seq VARCHAR2(1000);
BEGIN
    fib_seq := a || ', ' || b;

    FOR i IN 3..n LOOP
        c := a + b;
        fib_seq := fib_seq || ', ' || c;
        a := b;
        b := c;
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Fibonacci sequence: ' || fib_seq);
END;
/
```



**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8

### Output:

<img width="253" height="34" alt="image" src="https://github.com/user-attachments/assets/e7d42950-06e0-4d9d-a1c9-e62d477904c5" />


---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.
### Program:
```sql
DECLARE
    n NUMBER := 1535; -- original number
    temp NUMBER;
    rev NUMBER := 0;
    digit NUMBER;
BEGIN
    temp := n; -- store original value

    WHILE temp > 0 LOOP
        digit := MOD(temp, 10);          -- extract last digit
        rev := rev * 10 + digit;         -- build reversed number
        temp := TRUNC(temp / 10);        -- remove last digit
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('n = ' || n);
    DBMS_OUTPUT.PUT_LINE('Reversed number is ' || rev);
END;
/
```

**Expected Output:**  
n = 1535  
Reversed number is 5351

### Output:

<img width="222" height="66" alt="image" src="https://github.com/user-attachments/assets/d3789670-dfff-4102-afae-5334f5ac3790" />


---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

### Program:
```sql
DECLARE
    a NUMBER := 10;
    b NUMBER := 9;
    c NUMBER := 15;
    largest NUMBER;
BEGIN
    IF a >= b AND a >= c THEN
        largest := a;
    ELSIF b >= a AND b >= c THEN
        largest := b;
    ELSE
        largest := c;
    END IF;

    DBMS_OUTPUT.PUT_LINE('a = ' || a || ', b = ' || b || ', c = ' || c);
    DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || largest);
END;
/
```

**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15

### Output:
<img width="214" height="49" alt="image" src="https://github.com/user-attachments/assets/3d6be89b-cee8-4f1c-bb32-b9602c4960f1" />






## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
