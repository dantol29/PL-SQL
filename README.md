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

## Data types
### NUMERIC
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

### CHARACTER
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

### DATE
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

### LARGE OBJECT
| Type | Value |
| --- | --- |
| `BFILE` | Used to store large binary objects in operating system files outside the database. Cannot exceed 4 GB |
| `BLOB` |	Used to store large binary objects in the database. 8 to 128 terabytes TB |
| `CLOB` |	Used to store large blocks of character data in the database.	8 to 128 TB |
| `NCLOB` | Used to store large blocks of NCHAR data in the database. 8 to 128 TB |
