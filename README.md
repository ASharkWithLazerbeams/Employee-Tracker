# EmployeeTrackerSQL
Employee Tracker SQL
ASharkWithLazerbeams/EmployeeTrackerSQL
A solution for managing a company's employees using node, inquirer, and MySQL

The command-line application allows users to:

1.Add departments, roles, employees
2.View departments, roles, employees
3.Update employee roles
4.View employees by manager
5.Delete departments, roles, employees

Clone the repo
git clone https://github.com/ASharkWithLazerbeams/Employee-Tracker.git
Install dependencies
npm install
Create the database using the officeSchema.sql and seeds.sql files.
DROP DATABASE IF EXISTS employee_db;
CREATE DATABASE employee_db;
USE employee_db;

CREATE TABLE departments(
id INT AUTO_INCREMENT PRIMARY KEY,
department_name VARCHAR(30)
);

CREATE TABLE roles (
id INT AUTO_INCREMENT PRIMARY KEY,
title VARCHAR(30),
salary DECIMAL(8,2),
department_id INT,
FOREIGN KEY(department_id) REFERENCES departments(id)
);

CREATE TABLE employees(
id INT AUTO_INCREMENT PRIMARY KEY,
first_name VARCHAR(30) NOT NULL,
last_name VARCHAR(30) NOT NULL,
role_id INT,
manager_id INT,
FOREIGN KEY(role_id) REFERENCES roles(id),
FOREIGN KEY(manager_id) REFERENCES employees(id)
);
INSERT INTO departments(department_name)
VALUES ('Management'),
('Sales'),
('Warehouse'),
('Human Resources'),
('Quality Control');

INSERT INTO roles(title)
VALUES('Regional Manager'),
('Sales Rep'),
('HR Rep');

INSERT INTO employees(first_name, last_name)
VALUES('Pam', 'Beesly'),
('Michael', 'Scott'),
('Jim', 'Halpert');

Run Server
node server.js
