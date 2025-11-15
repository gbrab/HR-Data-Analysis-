### The data aggregations applied in the Module 5 assignment: Data Aggregation Activity were as follows:
+ Created two tables; one showing the number of salespeople with attrition and one showing the number of salespeople without attrition.
```
CREATE TABLE attrition_yes
(
  Attrition string,
  Department string,
  MonthlyIncome int
);
```
```
INSERT OVERWRITE TABLE attrition_yes
SELECT Attrition, Department, ROUND(MonthlyIncome,-3)
FROM employee
WHERE Attrition LIKE "%Yes%" AND Department LIKE "%Sales%";
```
```
CREATE TABLE attrition_no
(
  Attrition string,
  Department string,
  MonthlyIncome int
);
```
```
INSERT OVERWRITE TABLE attrition_no
SELECT Attrition, Department, ROUND(MonthlyIncome,-3)
FROM employee
WHERE Attrition LIKE "%No%" AND Department LIKE "%Sales%";
```
+ Created 3 statistics tables displaying the monthly income for all salespeople, salespeople with attrition, salespeople without attrition.
```
SELECT Department, AVG(MonthlyIncome) AS average_monthly_income, MIN(MonthlyIncome) AS min_monthly_income, MAX(MonthlyIncome) AS max_monthly_income
FROM employee
GROUP BY Department;
```
```
SELECT Department, AVG(MonthlyIncome) AS average_monthly_income, MIN(MonthlyIncome) AS min_monthly_income, MAX(MonthlyIncome) AS max_monthly_income
FROM attrition_yes
GROUP BY Department;
```
```
SELECT Department, AVG(MonthlyIncome) AS average_monthly_income, MIN(MonthlyIncome) AS min_monthly_income, MAX(MonthlyIncome) AS max_monthly_income
FROM attrition_no
GROUP BY Department;
```
+ Created 2 tables displaying the count of salespeople with each monthly income. One table for those with attrition and one table for those without attrition.
```
SELECT MonthlyIncome AS monthlyincome, COUNT(MonthlyIncome) AS count
FROM attrition_yes
GROUP BY MonthlyIncome;
```
```
SELECT monthlyincome AS monthlyincome, COUNT(monthlyincome) AS count
FROM attrition_no
GROUP BY MonthlyIncome;
```
