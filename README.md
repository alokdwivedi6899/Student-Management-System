# Student Management System

**Core Java Project using JDBC and Oracle Database**

---

## Description
This is a simple **Student Management System** developed in **Core Java**.  
It allows users to:

- Add new students
- View all students
- Delete a student

The project uses **Oracle Database** to store student data.

---

## Technology Stack
- Java (Core Java)
- JDBC
- Oracle Database (XE)
- NetBeans IDE

---

## Features
1. Add Student with Name, Age, and Course  
2. View all Students in a tabular format  
3. Delete Student by ID  
4. Input validation to avoid wrong entries  

---

## How to Run
1. Import the project in **NetBeans**.  
2. Make sure **ojdbc8.jar** is added in Libraries.  
3. Run the `Main.java` file.  
4. Follow the console menu to manage students.

---

## Database Setup
```sql
-- Create Table
CREATE TABLE students(
    id NUMBER PRIMARY KEY,
    name VARCHAR2(50),
    age NUMBER,
    course VARCHAR2(50)
);

-- Create Sequence
CREATE SEQUENCE stud_seq START WITH 1 INCREMENT BY 1;

-- Create Trigger to auto-generate ID
CREATE OR REPLACE TRIGGER stud_before_insert
BEFORE INSERT ON students
FOR EACH ROW
BEGIN
  IF :NEW.id IS NULL THEN
    SELECT stud_seq.NEXTVAL INTO :NEW.id FROM dual;
  END IF;
END;
/
