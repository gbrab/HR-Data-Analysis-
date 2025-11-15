The data transformations applied in the Module 4 assignment: Data Transforma Activity were as follows:
+ Created and loaded a new table called "employee_sales"
```
CREATE TABLE employee_sales
(
  Attrition string,
  Department string,
  JobSatisfaction int,
  MonthlyIncome int
);
```
+ Selected the columns: Attrition, Department, JobSatisfaction, and MonthlyIncome
```
INSERT OVERWRITE TABLE employee_sales
SELECT Attrition, Department, JobSatisfaction, MonthlyIncome
FROM employee;
```
+ Rounded the data in the MonthlyIncome column to the nearest one thousandth
```
INSERT OVERWRITE TABLE employee_sales
SELECT Attrition, Department, JobSatisfaction, ROUND(MonthlyIncome,-3)
FROM employee_sales;
```
+ Filtered the data to only include Departments that contained the word "Sales"
```
INSERT OVERWRITE TABLE employee_sales
SELECT *
FROM employee_sales
WHERE Department LIKE "%Sales%";
```
+ Ordered the data by the JobSatisfaction column from highest to lowest
```
INSERT OVERWRITE TABLE employee_sales
SELECT *
FROM employee_sales
ORDER BY JobSatisfaction DESC;
```

