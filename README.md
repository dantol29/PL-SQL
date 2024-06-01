# PL/SQL
### The 'Hello World' Example
```
DECLARE 
   message  varchar2(20):= 'Hello, World!'; 
BEGIN 
   dbms_output.put_line(message); 
END;
```

### Basic structure
```
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

## Each block consists of three sub-parts

### 1. Declarations (DECLARE)

    This section starts with the keyword DECLARE. 
    It is an optional section and defines all variables, cursors, subprograms, and other elements to be used in the program.

### 2. Executable Commands (BEGIN, END)

    This section is enclosed between the keywords BEGIN and END and it is a mandatory section.
    It consists of the executable PL/SQL statements of the program. 
### 3. Exception Handling (EXCEPTION)

    This section starts with the keyword EXCEPTION. This optional section contains exception(s) that handle errors in the program.

**Every PL/SQL statement ends with a semicolon (;)**

<hr>

## Data types

<details>
<summary> <h4>NUMERIC</h4> </summary>
   
| Type | Value |
| --- | --- |
| `PLS_INTEGER` | Signed integer in range -2,147,483,648 through 2,147,483,647, represented in 32 bits |
| `BINARY_INTEGER` | Signed integer in range -2,147,483,648 through 2,147,483,647, represented in 32 bits |
| `BINARY_FLOAT` | Single-precision IEEE 754-format floating-point number |
| `BINARY_DOUBLE` | Double-precision IEEE 754-format floating-point number |
| `NUMBER(prec, scale)` | Fixed-point or floating-point number with absolute value in range 1E-130 to (but not including) 1.0E126 |
| `DEC(prec, scale)` | ANSI specific fixed-point type with maximum precision of 38 decimal digits |
| `DECIMAL(prec, scale)` | IBM specific fixed-point type with maximum precision of 38 decimal digits |
| `NUMERIC(pre, secale)` | Floating type with maximum precision of 38 decimal digits |
| `DOUBLE PRECISION` | ANSI specific floating-point type with maximum precision of 126 binary digits (approximately 38 decimal digits) |
| `FLOAT` | ANSI and IBM specific floating-point type with maximum precision of 126 binary digits (38 decimal digits) |
| `INT` | ANSI specific integer type with maximum precision of 38 decimal digits |
| `INTEGER` | ANSI and IBM specific integer type with maximum precision of 38 decimal digits |
| `SMALLINT` | ANSI and IBM specific integer type with maximum precision of 38 decimal digits |
| `REAL` | Floating-point type with maximum precision of 63 binary digits (approximately 18 decimal digits)

</details>

<details>
<summary> <h4>CHARACTER</h4> </summary>
   
| Type | Value |
| --- | --- |
| `CHAR` | Fixed-length character string with maximum size of 32,767 bytes |
| `VARCHAR2` | Variable-length character string with maximum size of 32,767 bytes |
| `RAW` | Variable-length binary or byte string with maximum size of 32,767 bytes, not interpreted by PL/SQL |
| `NCHAR` | Fixed-length national character string with maximum size of 32,767 bytes |
| `NVARCHAR2` |  Variable-length national character string with maximum size of 32,767 bytes |
| `LONG` | Variable-length character string with maximum size of 32,760 bytes |
| `LONG RAW` | Variable-length binary or byte string with maximum size of 32,760 bytes, not interpreted by PL/SQL |
| `ROWID` | Physical row identifier, the address of a row in an ordinary table |	
| `UROWID` |Universal row identifier (physical, logical, or foreign row identifier) |

</details>

<details>
<summary> <h4>DATE</h4> </summary>

| Type | Value |
| --- | --- |
| `YEAR` |	-4712 to 9999 (excluding year 0)	|
| `MONTH` | 01 to 12 |
| `DAY`	| 01 to 31 |
| `HOUR` |	00 to 23	|
| `MINUTE` |	00 to 59 |
| `SECOND` |	00 to 59.9(n) |
| `TIMEZONE_HOUR` |	-12 to 14 |
| `TIMEZONE_MINUTE`	| 00 to 59 |
| `TIMEZONE_REGION` | Found in the dynamic performance view V$TIMEZONE_NAMES	|
| `TIMEZONE_ABBR` |	Found in the dynamic performance view V$TIMEZONE_NAMES |

</details>

<details>
<summary> <h4>LARGE OBJECT</h4> </summary>
   
| Type | Value |
| --- | --- |
| `BFILE` | Used to store large binary objects in operating system files outside the database. Cannot exceed 4 GB |
| `BLOB` |	Used to store large binary objects in the database. 8 to 128 terabytes TB |
| `CLOB` |	Used to store large blocks of character data in the database.	8 to 128 TB |
| `NCLOB` | Used to store large blocks of NCHAR data in the database. 8 to 128 TB |
</details>

<hr>
<details>
<summary> <h2>Variables</h2> </summary>
   
- `variable_name [CONSTANT] datatype [:= initial_value] `

```
sales number(10, 2); 
pi CONSTANT double precision := 3.1415; 
name varchar2(25); 
address varchar2(100);
```
### SELECT INTO
- The SELECT INTO statement is used to fetch the results of a SQL query and assign them to PL/SQL variables.
- In PL/SQL, the `%TYPE` attribute is used to declare variables with the same data type as a column in a table or a previously declared variable

 <b>Example:</b>
   
```
DECLARE
  v_employee_id  employees.employee_id%TYPE := 101;  -- Variable to hold employee ID
  v_first_name   employees.first_name%TYPE;          -- Variable to hold first name
  v_salary       employees.salary%TYPE;              -- Variable to hold salary
BEGIN
  -- Select first_name and salary into PL/SQL variables
  SELECT first_name, salary
  INTO v_first_name, v_salary
  FROM employees
  WHERE employee_id = v_employee_id;
END;
```
</details>

<details>
<summary> <h2>Arrays</h2> </summary>

### VARRAY
- `varray_type_name IS VARRAY(n) of <element_type>`
- VARRAY can store a fixed-size sequential collection of elements of the same type
- In Oracle environment, the starting index for varrays is always 1.
- Varrays are one-dimensional arrays.

```
DECLARE 
   type namesarray IS VARRAY(5) OF VARCHAR2(10); 
   type grades IS VARRAY(5) OF INTEGER; 
```

</details>

<details>
<summary> <h2>Loops</h2> </summary>
   
- `EXIT` instead of `RETURN` 
```
DECLARE 
   i number(1); 
   j number(1); 
BEGIN 
   FOR i IN 1..3 LOOP 
      FOR j IN 1..3 LOOP 
         dbms_output.put_line('i is: '|| i || ' and j is: ' || j); 
      END loop inner_loop; 
   END loop outer_loop; 
END; 
```

</details>

<details>
<summary> <h2>Procedures</h2> </summary>
   
- Procedure is a program unit/module that performs a particular task. These subprograms are combined to form larger programs
- A subprogram can be created − `At the schema level`, `Inside a package` and `Inside a PL/SQL block`
     1. `At the schema level`, subprogram is a standalone subprogram. It is created with the `CREATE PROCEDURE` or the `CREATE FUNCTION` statement. It is stored in the database and can be deleted with the `DROP PROCEDURE` or `DROP FUNCTION` statement.
     2. `Inside a package`, subprogram is a packaged subprogram. It is stored in the database and can be deleted only when the package is deleted with the `DROP PACKAGE` statement.
     3.  `PL/SQL blocks` that can be invoked with a set of parameters

_How to create a procedure?_
```
CREATE PROCEDURE greetings 
AS 
BEGIN 
   dbms_output.put_line('Hello World!'); 
END; 
```

_How to execute a procedure?_
```
EXECUTE greetings;
```
_OR_
```
BEGIN 
   greetings; 
END; 
```

#### Parameter modes in PL/SQL:

| Type | Value |
| --- | --- |
| IN | lets you pass a value to the subprogram. It is a read-only parameter. Is passed by reference |
| OUT | returns a value to the calling program. Inside the subprogram, an OUT parameter acts like a variable. You can change its value and reference the value after assigning it. The parameter must be variable and is passed by value |	
| IN OUT | passes an initial value to a subprogram and returns an updated value to the caller. It can be assigned a value and the value can be read. Is passed by value |

_An example with `IN` and `OUT`_
```
DECLARE 
   a number; 
   b number; 
   c number;
PROCEDURE findMin(x IN number, y IN number, z OUT number) IS 
BEGIN 
   IF x < y THEN 
      z:= x; 
   ELSE 
      z:= y; 
   END IF; 
END;   
BEGIN 
   a:= 23; 
   b:= 45; 
   findMin(a, b, c); 
   dbms_output.put_line(' Minimum of (23, 45) : ' || c); 
END; 
```

_An example with `IN OUT`_
```
DECLARE 
   a number; 
PROCEDURE squareNum(x IN OUT number) IS 
BEGIN 
  x := x * x; 
END;  
BEGIN 
   a:= 23; 
   squareNum(a); 
   dbms_output.put_line(' Square of (23): ' || a); 
END; 
```
</details>

<details>
<summary> <h2>Functions</h2> </summary>
   
**A function is same as a procedure except that it returns a value**

- The function must contain a return statement.
- The `AS` keyword is used instead of the `IS` keyword for creating a standalone function.

_An example with `RETURN` keyword`_
```
DECLARE 
   a number; 
   b number; 
   c number; 
FUNCTION findMax(x IN number, y IN number)  
RETURN number 
IS 
    z number; 
BEGIN 
   IF x > y THEN 
      z:= x; 
   ELSE 
      Z:= y; 
   END IF;  
   RETURN z; 
END; 
BEGIN 
   a:= 23; 
   b:= 45;  
   c := findMax(a, b); 
   dbms_output.put_line(' Maximum of (23,45): ' || c); 
END;
```
</details>

<details>
<summary> <h2>String functions and operators</h2> </summary>

| Name | Description |
| --- | --- |
| `ASCII(x)` | Returns the ASCII value of the character x |
| `CHR(x)` | Returns the character with the ASCII value of x |
| `CONCAT(x, y)` | Concatenates the strings x and y and returns the appended string |
| `INITCAP(x)` | Converts the initial letter of each word in x to uppercase and returns that string |	
| `INSTR(x, find_string [, start] [, occurrence])` | Searches for find_string in x and returns the position at which it occurs |	
| `INSTRB(x)` | Returns the location of a string within another string, but returns the value in bytes |	
| `LENGTH(x)` | Returns the number of characters in x |	
| `LENGTHB(x)` | Returns the length of a character string in bytes for single byte character set |	
| `LOWER(x)` | Converts the letters in x to lowercase and returns that string |
| `LPAD(x, width [, pad_string])` | Pads x with spaces to the left, to bring the total length of the string up to width character |
| `LTRIM(x [, trim_string])` | Trims characters from the left of x |
| `NANVL(x, value)` | Returns value if x matches the NaN special value (not a number), otherwise x is returned |	
| `NLS_INITCAP(x)` | Same as the INITCAP function except that it can use a different sort method as specified by NLSSORT |
| `NLS_LOWER(x)` | Same as the LOWER function except that it can use a different sort method as specified by NLSSORT |
| `NLS_UPPER(x)` | Same as the UPPER function except that it can use a different sort method as specified by NLSSORT |
| `NLSSORT(x)` | Changes the method of sorting the characters. Must be specified before any NLS function; otherwise, the default sort will be used |
| `NVL(x, value)` | Returns value if x is null; otherwise, x is returned |
| `NVL2(x, value1, value2)` | Returns value1 if x is not null; if x is null, value2 is returned |
| `REPLACE(x, search_string, replace_string)` | Searches x for search_string and replaces it with replace_string.
| `RPAD(x, width [, pad_string])` | Pads x to the right |
| `RTRIM(x [, trim_string])` | Trims x from the right |
| `SOUNDEX(x)` | Returns a string containing the phonetic representation of x |
| `SUBSTR(x, start [, length` | Returns a substring of x that begins at the position specified by start. An optional length for the substring may be supplied |
| `SUBSTRB(x)` | Same as SUBSTR except that the parameters are expressed in bytes instead of characters for the single-byte character systems |
| `TRIM([trim_char FROM) x)` | Trims characters from the left and right of x |
| `UPPER(x)` | Converts the letters in x to uppercase and returns that string |

</details>
