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

## 1. Write a PL/SQL Procedure to Find the Square of a Number

### Steps:
    1.Create a procedure named find_square.
    2.Declare a parameter to accept a number.
    3.Inside the procedure, compute the square of the input number.
    4.Use DBMS_OUTPUT.PUT_LINE to display the result.
    5.Call the procedure with a number as input.

PL/SQL
```
CREATE OR REPLACE PROCEDURE FIND_SQUARE (num IN NUMBER) IS square NUMBER;
 BEGIN
  square := num * num;
  DBMS_OUTPUT.PUT_LINE('Square of ' || num || ' is ' || square);
  END;
  BEGIN
     FIND_SQUARE(6);
  END;
  /
```

**Expected Output:**  
Square of 6 is 36

Output:
![image](https://github.com/user-attachments/assets/ea943908-4126-4e3d-8353-8a11e15b7a9c)

---

## 2. Write a PL/SQL Function to Return the Factorial of a Number
### Steps:
1.Create a function named get_factorial.
2.Declare a parameter to accept a number.
3.Use a loop to calculate the factorial.
4.Return the result using the RETURN statement.
5.Call the function using a SELECT statement or in an anonymous block.

PL/SQL query
```
CREATE OR REPLACE FUNCTION GET_FACTORIAL(n IN NUMBER)
RETURN NUMBER
IS
    result NUMBER := 1;
BEGIN
    IF n < 0 THEN
        RAISE_APPLICATION_ERROR(-20001, 'Input must be a non-negative number');
    END IF;

    FOR i IN 1..n LOOP
        result := result * i;
    END LOOP;

    RETURN result;
END;
DECLARE
    num NUMBER := 5;
    fact NUMBER;
BEGIN
    fact := GET_FACTORIAL(num);
    DBMS_OUTPUT.PUT_LINE('Factorial of ' || num || ' is ' || fact);
END;
/
```

**Expected Output:**  
Factorial pf 5 is 120

Output:
![image](https://github.com/user-attachments/assets/11fe1e34-8264-45c9-a79b-e16d96c5cf76)


---

## 3. Write a PL/SQL Procedure to Check Whether a Number is Even or Odd

### Steps:
1.Create a procedure named check_even_odd.
2.Accept an input parameter.
3.Use the MOD function to check if the number is divisible by 2.
4.Display whether it is Even or Odd using DBMS_OUTPUT.PUT_LINE

PL/SQL query
```
CREATE OR REPLACE PROCEDURE check_even_odd(num IN NUMBER) IS
BEGIN
    IF MOD(num, 2) = 0 THEN
        DBMS_OUTPUT.PUT_LINE(num || ' is Even');
    ELSE
        DBMS_OUTPUT.PUT_LINE(num || ' is Odd');
    END IF;
END;
SET SERVEROUTPUT ON;
BEGIN
    check_even_odd(12);
END;
/
```
**Expected Output:**  
12 is Even 

Output:
![image](https://github.com/user-attachments/assets/5fea5774-f06d-4b7e-87a6-281aa82e8c82)

---

## 4. Write a PL/SQL Function to Return the Reverse of a Number
### Steps:
1.Create a function named reverse_number.
2.Accept an input number as parameter.
3.Use a loop to reverse the digits of the number.
4.Return the reversed number.
5.Call the function and display the output.

PL/SQL query
```
CREATE OR REPLACE FUNCTION reverse_number(n IN NUMBER)
RETURN NUMBER
IS
    rev NUMBER := 0;
    num NUMBER := n;
BEGIN
    WHILE num > 0 LOOP
        rev := (rev * 10) + MOD(num, 10);
        num := TRUNC(num / 10);
    END LOOP;

    RETURN rev;
END;
SET SERVEROUTPUT ON;
DECLARE
    input_num NUMBER := 1234;
    reversed_num NUMBER;
BEGIN
    reversed_num := reverse_number(input_num);
    DBMS_OUTPUT.PUT_LINE('Reversed number of ' || input_num || ' is ' || reversed_num);
END;
/
```
**Expected Output:**  
Reversed number of 1234 is 4321

Output:
![image](https://github.com/user-attachments/assets/8f454230-a385-4ee8-9f6a-81b184686293)


---

## 5. Write a PL/SQL Procedure to Display the Multiplication Table of a Number
### Steps:
1.Create a procedure named print_table.
2.Accept an input number.
3.Use a loop from 1 to 10 to multiply the input number.
4.Display the multiplication results using DBMS_OUTPUT.PUT_LINE.

PL/SQL query
```
CREATE OR REPLACE PROCEDURE print_table(num IN NUMBER) IS
BEGIN
    DBMS_OUTPUT.PUT_LINE('Multiplication table of ' || num || ':');
    FOR i IN 1..10 LOOP
        DBMS_OUTPUT.PUT_LINE(num || ' x ' || i || ' = ' || (num * i));
    END LOOP;
END;
SET SERVEROUTPUT ON;
BEGIN
    print_table(5);
END;
/
```
**Expected Output:**  
Multiplication table of 5:
5 x 1 = 5
5 x 2 = 10
5 x 3 = 15
...
5 x 10 = 50

Output:
![image](https://github.com/user-attachments/assets/62725263-5e36-4b4d-b7fc-cb779003d125)


## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.

