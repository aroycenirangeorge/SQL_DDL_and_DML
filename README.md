# Experiment 5: Implementation of SQL for DDL and DML Commands

Royce Niran George A

212223060231

## Aim

To write and execute SQL commands to implement DDL (Data Definition Language) and DML (Data Manipulation Language) operations on a database and perform various operations such as creating tables, inserting, retrieving, updating, deleting, and querying data.

## Algorithm – DDL Commands

1. Start.
2. Create a database named `COLLEGE`.
3. Select the `COLLEGE` database using the `USE` command.
4. Create the `DEPARTMENT` table with primary key, unique, and not-null constraints.
5. Create the `STUDENT` table with primary key, foreign key, check, unique, and default constraints.
6. Add a `Phone` column to the `STUDENT` table using `ALTER TABLE`.
7. Add a check constraint to validate the phone number length.
8. Add a check constraint to ensure that `Student_Name` is not empty.
9. Display the structure of the tables using `DESCRIBE`.
10. Rename the `STUDENT` table to `STUDENT_DETAILS`.
11. Remove the `Phone` column using `ALTER TABLE ... DROP COLUMN`.
12. Create the `COURSE` table with appropriate constraints.
13. Remove all records from the `COURSE` table using `TRUNCATE`.
14. Permanently remove the `COURSE` table using `DROP TABLE`.
15. Stop.

## Algorithm – DML Commands

1. Start.
2. Create a database named `HOSPITAL`.
3. Select the `HOSPITAL` database using the `USE` command.
4. Create the `PATIENT` table with fields for Patient ID, Name, Age, Gender, Disease, and Fees.
5. Insert patient records into the `PATIENT` table using the `INSERT` command.
6. Display all patient records using the `SELECT` command.
7. Retrieve patients whose age is greater than 40 using the `WHERE` clause.
8. Retrieve patients suffering from Diabetes using the `WHERE` clause.
9. Increase the fees of all patients by 500 using the `UPDATE` command.
10. Update Anu's disease from Asthma to Allergy using the `UPDATE` command.
11. Delete patients whose fees are less than 3000 using the `DELETE` command.
12. Display patient records in descending order of fees using `ORDER BY`.
13. Calculate the average patient fees using the `AVG()` function.
14. Find the highest patient fees using the `MAX()` function.
15. Stop.

## Procedure for Executing the SQL Program

* Open an SQL programming environment such as MySQL Workbench.
* Create a new SQL query.
* Type or paste the given SQL commands into the editor.
* Execute the DDL commands to create and modify the database and tables.
* Execute the DML commands to create the `PATIENT` table and insert records.
* Use `SELECT` commands to retrieve and filter the required records.
* Use `UPDATE` commands to modify existing records.
* Use `DELETE` commands to remove records based on the specified condition.
* Execute sorting and aggregate queries to obtain the required results.
* Observe the database structure and output of each SQL command.

## Program

```sql
CREATE DATABASE COLLEGE;

USE COLLEGE;

CREATE TABLE DEPARTMENT (
    Dept_ID INT PRIMARY KEY,
    Dept_Name VARCHAR(30) NOT NULL UNIQUE,
    Location VARCHAR(30)
);

CREATE TABLE STUDENT (
    Student_ID INT PRIMARY KEY,
    Student_Name VARCHAR(50) NOT NULL,
    Email VARCHAR(50) UNIQUE,
    Age INT CHECK (Age >= 17),
    Dept_ID INT,
    Status VARCHAR(10) DEFAULT 'Active',
    FOREIGN KEY (Dept_ID) REFERENCES DEPARTMENT(Dept_ID)
);

ALTER TABLE STUDENT
ADD Phone VARCHAR(15);

ALTER TABLE STUDENT
ADD CONSTRAINT chk_phone
CHECK (CHAR_LENGTH(Phone) BETWEEN 10 AND 15);

ALTER TABLE STUDENT
ADD CONSTRAINT chk_student_name
CHECK (TRIM(Student_Name) <> '');

DESCRIBE DEPARTMENT;

DESCRIBE STUDENT;

RENAME TABLE STUDENT TO STUDENT_DETAILS;

ALTER TABLE STUDENT_DETAILS
DROP COLUMN Phone;

CREATE TABLE COURSE (
    Course_ID INT PRIMARY KEY,
    Course_Name VARCHAR(50) NOT NULL UNIQUE,
    Credits INT CHECK (Credits > 0),
    Dept_ID INT,
    FOREIGN KEY (Dept_ID) REFERENCES DEPARTMENT(Dept_ID)
);

TRUNCATE TABLE COURSE;

DROP TABLE COURSE;

CREATE DATABASE HOSPITAL;

USE HOSPITAL;

CREATE TABLE PATIENT (
    Patient_ID INT PRIMARY KEY,
    Patient_Name VARCHAR(50),
    Age INT,
    Gender CHAR(1),
    Disease VARCHAR(50),
    Fees INT
);

INSERT INTO PATIENT VALUES
(201, 'Kumar', 45, 'M', 'Diabetes', 5000),
(202, 'Priya', 32, 'F', 'Fever', 2000),
(203, 'Ravi', 60, 'M', 'Heart Disease', 15000),
(204, 'Anu', 28, 'F', 'Asthma', 6000);

SELECT * FROM PATIENT;

SELECT * FROM PATIENT
WHERE Age > 40;

SELECT * FROM PATIENT
WHERE Disease = 'Diabetes';

UPDATE PATIENT
SET Fees = Fees + 500;

UPDATE PATIENT
SET Disease = 'Allergy'
WHERE Patient_Name = 'Anu';

DELETE FROM PATIENT
WHERE Fees < 3000;

SELECT * FROM PATIENT
ORDER BY Fees DESC;

SELECT AVG(Fees) AS Average_Fees
FROM PATIENT;

SELECT MAX(Fees) AS Highest_Fees
FROM PATIENT;
```

## Output

### Database: COLLEGE

<img width="513" height="155" alt="image" src="https://github.com/user-attachments/assets/914e182e-d19e-4122-9f1d-6656edf70bd0" />

<img width="538" height="213" alt="image" src="https://github.com/user-attachments/assets/4ba817b6-061e-4d77-bf5c-f092eca50605" />


### Database: HOSPITAL

<img width="533" height="171" alt="image" src="https://github.com/user-attachments/assets/40ce2f49-2e36-4d30-9c0c-506bf977233f" />

<img width="531" height="120" alt="image" src="https://github.com/user-attachments/assets/e13a29bf-715e-4fdf-95c5-c0b59774c24a" />

<img width="507" height="93" alt="image" src="https://github.com/user-attachments/assets/4be1933b-4ba4-47b4-8ba2-2b677f888261" />

<img width="521" height="123" alt="image" src="https://github.com/user-attachments/assets/cddca8ed-0ea7-426f-8386-2e401e9bbdf3" />

<img width="495" height="93" alt="image" src="https://github.com/user-attachments/assets/11fa4b7f-6a16-499b-8257-f13347195eab" />

<img width="473" height="92" alt="image" src="https://github.com/user-attachments/assets/4e76ceca-2cca-42f3-8139-14785e80e960" />

<img width="520" height="126" alt="image" src="https://github.com/user-attachments/assets/8ae9abfd-4885-4f51-91a0-586893813973" />

## Result

Thus, the SQL program to implement DDL and DML commands was successfully executed. The database and tables were created and modified using DDL commands, while data was successfully inserted, retrieved, updated, deleted, sorted, and analyzed using DML commands.
