# Employee-and-Department-Data-Analysis

## Project Overview

This project entails the analysis of employee and department data from a relational database. The main goal is to derive actionable insights regarding workforce distribution, salary structures, and departmental compositions. The analysis focuses on retrieving and manipulating employee data through SQL queries. The key operations include:

- **Data Retrieval**: Extracting records from tables such as `employees`, `departments`, `jobs`, and `locations`. This process helps in understanding key characteristics such as salary distribution, department assignment, and job roles.
  
- **Conditional Filtering**: Applying conditions to retrieve specific data sets, such as employees whose salaries are outside a specified range, or those working in certain departments. This helps narrow down the dataset for targeted insights.
  
- **Aggregate Functions**: Using functions like `AVG` to compute average salaries or `COUNT` to tally the number of employees in different categories.
  
- **Joining Data**: Combining data across different tables like `employees` and `departments` to offer a holistic view of employee distribution across the organization.

The purpose of this project is to help Human Resources and management teams make better decisions regarding salary adjustments, workforce allocation, and organizational planning by providing insights through detailed SQL analysis.

## Retrieving and Filtering Employee and Department Data

### 1. Employees with Salaries Outside $10,000 to $15,000

This query focuses on identifying employees whose salaries fall outside the specified range of $10,000 to $15,000. The purpose of this query is to highlight salary outliers that may require special attention.

```sql
SELECT
    CONCAT(FIRST_NAME, ' ', LAST_NAME) AS FULL_NAME,
    SALARY
FROM employees
WHERE SALARY NOT BETWEEN 10000 AND 15000;
```

**Explanation**:  
- The `CONCAT(FIRST_NAME, ' ', LAST_NAME)` function combines the first and last names into a single field called `FULL_NAME` for easier readability.
- The `WHERE SALARY NOT BETWEEN 10000 AND 15000` clause filters out employees whose salaries fall within the $10,000–$15,000 range, focusing instead on those with either lower or higher salaries.  
This query is useful in understanding the pay structure and identifying any employees who might be underpaid or overpaid in relation to company standards.

### 2. Employees in Departments 30 or 100

This query helps retrieve employee data based on departmental assignment, specifically focusing on employees who work in departments `30` or `100`. The results are ordered by department ID.

```sql
SELECT
    CONCAT(FIRST_NAME, ' ', LAST_NAME) AS FULL_NAME,
    DEPARTMENT_ID
FROM employees
WHERE DEPARTMENT_ID = '30' OR DEPARTMENT_ID = '100'
ORDER BY DEPARTMENT_ID;
```

**Explanation**:
- Employees are filtered by their `DEPARTMENT_ID`, showing only those in departments `30` or `100`.
- The `ORDER BY DEPARTMENT_ID` clause organizes the results in ascending order of department IDs.

This query is useful for departmental analysis, helping managers identify how many employees are allocated to key departments. It can be particularly useful in determining staffing levels and resource allocation.

### 3. Employees with Salaries Not Matching the Average

This query finds employees whose salaries deviate from the average salary within the company. By identifying those who earn more or less than the average, HR can make informed decisions about compensation adjustments.

```sql
SELECT
    CONCAT(FIRST_NAME, ' ', LAST_NAME) AS FULL_NAME,
    SALARY
FROM employees
WHERE SALARY <> (SELECT AVG(SALARY) FROM employees);
```

**Explanation**:
- The inner query calculates the average salary across all employees.
- The outer query filters employees whose salary does not equal the calculated average. This is achieved using the `<>` operator, which means "not equal to."
  
This query is crucial for salary assessments, allowing HR to quickly identify employees who may be over- or under-compensated compared to their peers.

## Using Aggregate Functions and Sorting Data

### 4. Employees by Hire Date

The following query helps analyze employee recruitment patterns by retrieving employees who were hired after a specific date (in this case, January 1, 2005).

```sql
SELECT
    CONCAT(FIRST_NAME, ' ', LAST_NAME) AS FULL_NAME,
    HIRE_DATE
FROM employees
WHERE HIRE_DATE > '2005-01-01';
```

**Explanation**:
- The `HIRE_DATE` is compared using the `>` operator to return all employees hired after January 1, 2005.
  
This query is helpful for analyzing recruitment trends and understanding the organization's growth over time. It can provide insights into periods of high or low recruitment.

### 5. Employees in Specific Job Roles

This query filters employees who work in a specific job role, such as `IT_PROG` (IT Programmers). Understanding workforce composition by job role is key to organizational planning.

```sql
SELECT
    CONCAT(FIRST_NAME, ' ', LAST_NAME) AS FULL_NAME,
    JOB_ID
FROM employees
WHERE JOB_ID = 'IT_PROG';
```

**Explanation**:
- The query filters employees based on their `JOB_ID`. In this case, it retrieves those who are IT Programmers (`IT_PROG`).

By understanding the number of employees in specific job roles, management can allocate resources more efficiently, particularly in high-demand roles like IT.

## Usage Instructions

1. **Clone the Repository**: Clone this project repository to your local machine to access the SQL files.
  
2. **Setup the Database**: Import the SQL scripts into your SQL environment (e.g., MySQL) and ensure the relevant tables (`employees`, `departments`, etc.) are available.
  
3. **Execute SQL Queries**: Run the SQL queries in this README to retrieve insights related to employee data. Each query is focused on a particular aspect of workforce analysis, such as salary, department composition, and hiring trends.
  
4. **Analyze Results**: Review the output of each query and derive actionable insights for salary adjustments, workforce planning, or recruitment strategies.

### Sample Exercise: Employees with Non-Average Salaries

**Objective**: Retrieve the names and salaries of employees whose salary does not match the company’s average salary.

```sql
SELECT
    CONCAT(FIRST_NAME, ' ', LAST_NAME) AS FULL_NAME,
    SALARY
FROM employees
WHERE SALARY <> (SELECT AVG(SALARY) FROM employees);
```

This exercise will help you understand how many employees are earning above or below the average salary, providing critical data for salary review processes.

## Recommendations

Based on the analysis of employee and department data, several recommendations can be made:

1. **Salary Adjustments**: Employees whose salaries deviate significantly from the average may require salary adjustments to ensure fairness and retain talent.
  
2. **Departmental Staffing**: Departments like `30` and `100` may require further resource allocation if staffing levels are lower than required.
  
3. **Recruitment Strategy**: Identifying recruitment trends based on hire date analysis can help HR plan future recruitment campaigns to fill key roles, particularly in job roles like IT Programmers (`IT_PROG`).

4. **Salary Benchmarking**: Employees earning significantly more or less than the defined salary range ($10,000–$15,000) should be benchmarked against industry standards to ensure competitive pay rates.

## Conclusion

This SQL analysis provides critical insights into the workforce structure, salary distribution, and department composition of an organization. By leveraging SQL queries and aggregate functions, HR and management teams can make informed decisions about salary reviews, resource allocation, and recruitment strategies.

Contributions to this repository are welcome. If you have additional SQL queries or insights, feel free to submit a pull request.
