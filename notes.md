________________________________________________________
HOW TO: CREATE A DATABASE

##createdb <name_of_db>
Terminal command to create database


##psql <name_of_db>
Terminal command to open database


#######ALTERNATIVELY###########

##sudo adduser <user_name>


##sudo su - postgres
##psql
Log into the default PostgreSQL user (called "postgres") to create a database and assign it to the new user

##CREATE USER <user_name> WITH PASSWORD '<password>';
##CREATE DATABASE <name_of_database> OWNER <user_name>;

##\q
exits

##exit
##sudo su - <user_name>
Exits out of the default "postgres" user account and logs into the user you created.

##psql <name_of_database>
Signs into the database you created

##show data_directory;
To see where the data directory is, use this query.

##\list or \l:
list all databases

##\dt:
list all tables in the current database

##\c or \connect database_name
To switch databases

________________________________________________________
HOW TO: CREATE A TABLE

CREATE TABLE <new_table_name> (
	<table_column_title> TYPE_OF_DATA column_constraints,
	<next_column_title> TYPE_OF_DATA column_constraints,
	table_constraint
	table_constraint
	) <INHERITS existing_table_to_inherit_from>;

CREATE TABLE pg_equipment (
	equip_id serial PRIMARY KEY,
	type varchar (50) NOT NULL,
	color varchar (25) NOT NULL,
	location varchar(25) check (location in ('north', 'south', 'west', 'east', 'northeast', 'southeast', 'southwest', 'northwest')),
	install_date date
	);

##PostgreSQL Data Types

The data type can be any of the following:
	boolean: Use "boolean" or "bool" to declare a true or false value.
	character values
	char: holds a single character
	char (#): holds # number of characters. Spaces will be inserted to fill any extra room.
	varchar (#): holds a maximum of # number of character. Can contain less.
	integer values
	smallint: whole number between -32768 and 32767.
	int: whole number between -214783648 and 214783647.
	serial: Auto-populated integer number.
	floating-point values
	float (#): floating point number with at least # points of precision.
	real: 8-byte floating point number
	numeric (#,after_dec): real number with # number of digits, and after_dec digits after decimal
	date and time values
	date: stores a date value
	time: stores a time value
	timestamp: stores a date and time value
	timestamptz: stores a timestamp that includes timezone data
	interval: stores the difference between two timestamp values
	geometric data
	point: stores a pair of coordinates that define a point
	line: stores a set of points that map out a line
	lseg: stores data that defines a line segment
	box: stores data that defines a rectangle
	polygon: stores data that defines any enclosed space
	device specifications
	inet: stores an IP address
	macaddr: stores a device MAC address


##PostreSQL Column and Table Constraints

Column definitions can also have constraints that provide rules for the type of data found in the column. The following can be used as space-separated values following the data type:

NOT NULL: column cannot have null value
UNIQUE: column value must not be the same for any record. Null is always considered a unique value
PRIMARY KEY: combination of the above two constraints. Can only be used once per table
CHECK: ensure that a condition is true for values in the column
REFERENCES: value must exist in a column in another table
After the columns are defined, table-wide constraints may be declared. Table-wide constraints can be either UNIQUE, PRIMARY KEY, CHECK, or REFERENCES.
