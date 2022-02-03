This implementation targets a limited implementation of database management. 
	It allows you to write SQL commands in order to create and manage tables.

There are 3 accepted data types: text, integer, float

There are 2 files in SqlProject folder that should be named: comenzi.txt and comenzi2.txt
Here you can place commands just like you would in console. comenzi.txt can receive only CREATE TABLE commands
comenzi2.txt can receive any type of commands
Note that you must give them as command line arguments
	Example: Set to Visual Studio Code arguments comenzi.txt comenzi2.txt

DISCLAIMER 1: If the project will give compile errors, make sure you disable SDL checks. The compile error may appear from strcpy function.
DISCLAIMER 2: It still has plenty of bugs. It's a practice project, its purpose was to learn OOP concepts.

1. Accepted commands:
- CREATE TABLE table_name ((Column1_name, type, dimension, default_value), (Column2_name, type, dimension, default_value),..)
	Working example: 
		CREATE TABLE STUDENT((Height, integer, 5, 190), (Faculty, text, 25, CSIE))
Observations:
	a) Default_Value can't have white spaces. Example: John Smith must be written John_Smith
	b) dimension means => for type =  integer, the number of figures must be <= dimension
		Example: if we have dimension = 5 => 123456 will not be allowed. 12345 will be allowed
			=> same goes for type = text
		Example: If we have dimension = 5 => CSIETX will not be allowed. CSIEX will be allowed
	c) You can't create 2 tables with the same name
	d) This command will create a binary file named TABEL_table_name

-  DROP TABLE table_name => this command will delete the given table and the corresponding binary file

- DISPLAY TABLE table_name => this command will print the given table, currently, is equivalent to SELECT ALL FROM table_name
	Observation: These 2 commands will create a text file named SELECT_x, where x is a number
	which contains the output from the console

-  INSERT INTO table_NAME VALUES(..) => this command will insert into the given table values
	Working example: INSERT INTO STUDENT VALUES (172, MAN)
	Observations:
	- Values types must match the column ORDER and type. 
		Example: INSERT INTO STUDENT VALUES (MAN, 172) will not work
		because MAN type is text and column's type is integer. Same goes for 172
 - DELETE FROM table_name WHERE Column_Name = Value
	This command will delete all rows matching the desired pattern
	Working example: DELETE FROM STUDENT WHERE HEIGHT = 172

- UPDATE table_name SET Column_Name = VALUE Where Column_Name = Value
	Working example: UPDATE STUDENT SET HEIGHT = 180 WHERE HEIGHT = 172

- MENU option

- If you write: --showdatabase it will output all of the existing tables

- IMPORT option => imports data into a table from a csv file
	- Import is based on a set of 2,3,4.. depends on the number of columns of the given table
   Importing is done in steps ( for example, for a 2 column Table, it inserts two by two values)
   Hence, if one value in the set of 2 doesn't match the column's type, the 2 values will not get imported.
   However, it proceeds to the next values.

	Working example: Import student csvfile.csv
	Observations:
	- Only "," ( comma) separator is allowed. 
	- No other characters allowed, such as:   :/.;[]()*&^%$#@!`?<>-_+=
	- The number of values inserted must be multiple of table's number of columns. 
	Example: If the table has 3 columns, you can't have 2 values or 4 values or so on. 
	You must have either 3, either 6, either 9 and so on
	 


