# sql-challenge
---
## Project Description
For this project I taken the six CSV files on employee data from the 1980s and 1990s, created tables for the data, imported the files into SQL, and analyzed the data.  

---
## Data Modeling
![image](https://github.com/Faith-Hall/sql-challenge/assets/135525815/62490812-c5e6-4063-82e0-58d34a2bceb9)

(Image generated by QuickDBD)
---
## Data Engineering
Creating schema tables and for each CSV file: specified data types, relationships, primary keys, and foreign keys

```
-- create tables
CREATE TABLE "departments" (
    "dept_no" char(4)   NOT NULL,
    "dept_name" varchar(36)   NOT NULL,
    CONSTRAINT "pk_departments" PRIMARY KEY (
        "dept_no"
     )
);

CREATE TABLE "dep_emp" (
    "emp_no" int   NOT NULL,
    "dept_no" char(4)   NOT NULL,
    CONSTRAINT "pk_dep_emp" PRIMARY KEY (
        "emp_no","dept_no"
     )
);

CREATE TABLE "dept_manager" (
    "dept_no" char(4)   NOT NULL,
    "emp_no" int   NOT NULL,
    CONSTRAINT "pk_dept_manager" PRIMARY KEY (
        "emp_no"
     )
);

CREATE TABLE "employees" (
    "emp_no" int   NOT NULL,
    "emp_title_id" char(5)   NOT NULL,
    "birth_date" date   NOT NULL,
    "first_name" varchar(20)   NOT NULL,
    "last_name" varchar(20)   NOT NULL,
    "sex" char(1)   NOT NULL,
    "hire_date" date   NOT NULL,
    CONSTRAINT "pk_employees" PRIMARY KEY (
        "emp_no"
     )
);

CREATE TABLE "salaries" (
    "emp_no" int   NOT NULL,
    "salary" int   NOT NULL,
    CONSTRAINT "pk_salaries" PRIMARY KEY (
        "emp_no"
     )
);

CREATE TABLE "titles" (
    "title_id" char(5)   NOT NULL,
    "title" varchar(20)   NOT NULL,
    CONSTRAINT "pk_titles" PRIMARY KEY (
        "title_id"
     )
);

ALTER TABLE "dep_emp" ADD CONSTRAINT "fk_dep_emp_emp_no" FOREIGN KEY("emp_no")
REFERENCES "employees" ("emp_no");

ALTER TABLE "dep_emp" ADD CONSTRAINT "fk_dep_emp_dept_no" FOREIGN KEY("dept_no")
REFERENCES "departments" ("dept_no");

ALTER TABLE "dept_manager" ADD CONSTRAINT "fk_dept_manager_dept_no" FOREIGN KEY("dept_no")
REFERENCES "departments" ("dept_no");

ALTER TABLE "dept_manager" ADD CONSTRAINT "fk_dept_manager_emp_no" FOREIGN KEY("emp_no")
REFERENCES "employees" ("emp_no");

ALTER TABLE "employees" ADD CONSTRAINT "fk_employees_emp_title_id" FOREIGN KEY("emp_title_id")
REFERENCES "titles" ("title_id");

ALTER TABLE "salaries" ADD CONSTRAINT "fk_salaries_emp_no" FOREIGN KEY("emp_no")
REFERENCES "employees" ("emp_no");
```
## Data Analysis
1. List the employee number, last name, first name, sex, and salary of each employee.
```
SELECT 
	employees.emp_no, 
	employees.last_name, 
	employees.first_name, 
	employees.sex, 
	salaries.salary
	
FROM employees
JOIN salaries
ON employees.emp_no = salaries.emp_no;
```
![Screenshot 2023-08-30 173830](https://github.com/Faith-Hall/sql-challenge/assets/135525815/284074fc-61a2-4b29-a7e4-116d50cdf601)

2. List the first name, last name, and hire date for the employees who were hired in 1986.
```

```
3. List the manager of each department along with their department number, department name, employee number, last name, and first name.
```

```
4. List the department number for each employee along with that employee’s employee number, last name, first name, and department name.
```

```
5. List first name, last name, and sex of each employee whose first name is Hercules and whose last name begins with the letter B.
```

```
6. List each employee in the Sales department, including their employee number, last name, and first name.
```

```
7. List each employee in the Sales and Development departments, including their employee number, last name, first name, and department name.
```

```
8. List the frequency counts, in descending order, of all the employee last names (that is, how many employees share each last name).
```

```
