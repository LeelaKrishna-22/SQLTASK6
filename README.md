# SQLTASK6 
✅ Objective
The goal of this task is to practice and demonstrate proficiency in using subqueries and nested logic in SQL. You will work with scalar, correlated, and non-correlated subqueries, and use them in various SQL clauses like SELECT, WHERE, and FROM.

🛠 Tools Required
DB Browser for SQLite or



-- Creating tables
CREATE TABLE e1 (
    id INT,
    name VARCHAR2(10),
    salary INT
);

CREATE TABLE e2 (
    id INT,
    name VARCHAR2(10),
    salary INT
);

-- Inserting values into e1
INSERT INTO e1 VALUES (1, 'bk', 20000);
INSERT INTO e1 VALUES (2, 'lk', 30000);
INSERT INTO e1 VALUES (3, 'jk', 40000);
INSERT INTO e1 VALUES (4, 'pk', 50000);

-- Inserting values into e2
INSERT INTO e2 VALUES (1, 'lasya', 10000);
INSERT INTO e2 VALUES (5, 'leela', 20000);
INSERT INTO e2 VALUES (6, 'surya', 60000);
INSERT INTO e2 VALUES (7, 'manoj', 70000);

-- 1. Select names and salaries from e1 where id matches with e2's id
SELECT e1.name, e1.salary
FROM e1
WHERE e1.id IN (SELECT e2.id FROM e2);

-- 2. Select all columns from e1 where id matches with ANY id from e2
SELECT *
FROM e1
WHERE e1.id IN (SELECT e2.id FROM e2);

-- 3. Select all records from e2 where salary matches with any salary from e1
SELECT *
FROM e2
WHERE EXISTS (
    SELECT 1
    FROM e1
    WHERE e1.salary = e2.salary
);
