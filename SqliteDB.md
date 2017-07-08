# Sqlite3 Database Notes

## Why SQLite
* Lightweight database
* Lives on system
* Can easily connect to

## Tables

### CREATE 
* Create a table with specified schema (columns and what traits each value in column must have)
```
CREATE TABLE employee(
    EMPLOYEE_ID INT PRIMARY KEY NOT NULL,
    NAME CHAR(50) NOT NULL,
    );
```
* PRIMARY KEY means that value for each entry is unique (how to identify table entries)

### DROP
* Delete a table
`DROP employee`

### INSERT
* Add entry into table
```
INSERT INTO employee [EMPLOYEE_ID, NAME]
VALUES (1001, 'Super Employee');
```

```
INSERT INTO employee VALUES (1001, 'Super Employee');
```

### DELETE
* Delete entry from table
```
DELETE FROM employees WHERE EMPLOYEE_ID = 1001;
```

### SELECT
* Get specified values or columns from table
`SELECT NAME FROM employee;`

### .tables and .schema
* Shows the existing tables in the database
* Shows the layout/model of the table

## Object Relational Mapper (ORM)
* Serializes SQL data (table info) into objects
* SQLAlchemy

## Relationships
* One-to-one, one-to-many, many-to-many
* Use a junction table to for many-to-many relationships
    * Reduce the number of tables

## Models and Migrations
Knowing the basic commands and understanding what the database layout is supposed to look like helps with understanding how to create models, transfer them to the database, and map the data. Creating a table is possible through commandline `>sqlite3 Employees.db`. But within a project, models can be implemented and migrated to specified database.

Model ex.
```
db = SQLAlchemy()
app = FLASKAPI(__name__, instance_relative_config=True)
db.init_app(app)

Class Employees(db.Model):
    __tablename__ = 'employee'
    EMPLOYEE_ID = db.Column(db.Integer, primary_key=True)
    NAME = db.Column(db.String(50))

    def __init__(self, employee_id, name):
        self.EMPLOYEE_ID = employee_id
        self.NAME = name

    def get_all():
        return Employees.query.all()
```

Migrations "propagate changes" between the project model code and the database schema. One way to migrate would be to use Flask-Migrate, which is described in the RESTful API guide listed underneath Sources.

## Sources
* SQLite tutorial: https://www.tutorialspoint.com/sqlite/sqlite_create_table.htm
* Database relationships: https://stackoverflow.com/questions/7296846/how-to-implement-one-to-one-one-to-many-and-many-to-many-relationships-while-de
* "How to Build a RESTful Flask API": https://scotch.io/tutorials/build-a-restful-api-with-flask-the-tdd-way#toc-time-to-test