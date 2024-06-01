# PL/SQL
### The 'Hello World' Example
```
DECLARE 
   message  varchar2(20):= 'Hello, World!'; 
BEGIN 
   dbms_output.put_line(message); 
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
