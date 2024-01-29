[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/8OHy4RNn)
# RESTful-WS-Example
Simple RESTful Web Service used to illustrate the concept (based on the example by S. Subramanian on DZone.com).
Starter code for the assignment described below.

## What you have to do on this assignment:

After experimenting with this Web service (as described in the lab), extend the service (and its API) to:

a) store and update the salary of the employee;

b) check for errors, such as when trying to update information for a employee that does not exist;

c) retrieve the average salary, considering all the employees;

d) update the README with documentation of the service´s API (all its endpoints and how to use them).

## Note: Run the server and client on two separate machines in EC2

**********************************************************************************************************************************************************************************************

## Employee Database API Documentation

### Introduction

This is a simple Flask-based RESTful API for managing an employee database. The API provides endpoints to perform basic CRUD operations (Create, Read, Update, Delete) on employee records.

### Endpoints

#### 1. Get All Employees
* **Endpoint:** /empdb/employee
* **Method:** GET
* **Description:** Retrieve a list of all employees in the database.
##### Example Request:
```python
curl -X GET http://localhost:5678/empdb/employee
```
##### Example Response:
```json
{
  "emps": [
    {
      "id": "101",
      "name": "Arício Segundo",
      "title": "Technical Leader",
      "salary": "2000"
    },
    {
      "id": "201",
      "name": "Geraldo Rusmão",
      "title": "Sr Software Engineer",
      "salary": "3000"
    }
  ]
}
```
#### 2. Get Employee by ID
* **Endpoint:** /empdb/employee/[empId]
* **Method:** GET
* **Description:** Retrieve information about a specific employee by their ID.
##### Example Request:
```python
curl -X GET http://localhost:5678/empdb/employee/101
```
##### Example Response:
```json
{
  "emp": [
    {
      "id": "101",
      "name": "Arício Segundo",
      "title": "Technical Leader",
      "salary": "2000"
    }
  ]
}
```
#### 3. Update Employee Information
##### 3.1 Update Employee Details
* **Endpoint:** /empdb/employee/[empId]
* **Method:** PUT
* **Description:** Update the name and title of a specific employee.
##### Example Request:
```python
curl -X PUT -H "Content-Type: application/json" -d '{"name": "New Name", "title": "New Title"}' http://localhost:5678/empdb/employee/101
```
##### Example Response:
```json
[
  {
    "id": "101",
    "name": "New Name",
    "title": "New Title",
    "salary": "2000"
  }
]
```
##### 3.2 Update Employee Salary
* **Endpoint:** /empdb/employee/[empId]/[empSal]
* **Method:** PUT
* **Description:** Update the salary of a specific employee.
##### Example Request:
```python
curl -X PUT http://localhost:5678/empdb/employee/101/2500
```
##### Example Response:
```json
[
  {
    "id": "101",
    "name": "New Name",
    "title": "New Title",
    "salary": "2500"
  }
]
```
#### 4. Create Employee
* **Endpoint:** /empdb/employee
* **Method:** POST
* **Description:** Create a new employee record.
##### Example Request:
```python
curl -X POST -H "Content-Type: application/json" -d '{"id": "301", "name": "John Doe", "title": "Software Engineer"}' http://localhost:5678/empdb/employee
```
##### Example Response:
```json
{
  "id": "301",
  "name": "John Doe",
  "title": "Software Engineer"
}
```
#### 5. Delete Employee
* **Endpoint:** /empdb/employee/[empId]
* **Method:** DELETE
* **Description:** Delete a specific employee by their ID.
##### Example Request:
```python
curl -X DELETE http://localhost:5678/empdb/employee/301
```
##### Example Response:
```json
{
  "response": "Success"
}
```
#### 6. Average Salary
* **Endpoint:** /empdb/employee/average_salary
* **Method:** GET
* **Description:** Retrieve the average salary of all employees.
##### Example Request:
```python
curl -X GET http://localhost:5678/empdb/employee/average_salary
```
##### Example Response:
```json
{
  "average_salary": 2400.0
}
```
### Running the Application

To run the application, execute the following command in the terminal:
```bash
python your_filename.py
```
The API will be accessible at **http://localhost:5678**. Change the **"const.py"** file, putting the IP and port of your test server. In addition to placing the same port on which the server will be "listening" on line 80 of the **"EmployeeService.py"** file.
