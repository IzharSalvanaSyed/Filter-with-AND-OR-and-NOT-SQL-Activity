# Filter-with-AND-OR-and-NOT-SQL-Activity
Use the AND, OR, and NOT operators in SQL to filter for information. Use SQL to get specific information about employees, their machines, and the departments they’re in.


## Table of contents

1. [Scenario](#scenario)
2. [Retrieve after hours failed login attempts](#retrieve)
3. [Retrieve login attempts on specific dates](#dates)
4. [Retrieve login attempts outside of Mexico](#mexico)
5. [Retrieve employees in Marketing](#marketing)
6. [Retrieve employees in Finance or Sales](#sales)
7. [Retrieve all employees not in IT](#it)
8. [Conclusion](#conclusion)

## Scenario <a name="scenario">
In this scenario, you need to obtain specific information about employees, their machines, and the departments they belong to from the database.  
Your team needs data to investigate potential security issues and to update computers.  
You are responsible for filtering the required information from the database.  
Here’s how you’ll do this task: **First**, you’ll retrieve all failed login attempts after business hours. **Second**, you’ll retrieve all login attempts that occurred on specific dates. **Third**, you’ll retrieve logins that didn't originate in Mexico. **Fourth**, you’ll retrieve information about certain employees in the Marketing department. **Fifth**, you’ll retrieve information about employees in the Finance or the Sales department. **Finally**, you’ll obtain information about employees who are not in the Information Technology department.  
Common operators for working with numeric or date and time data will help you accurately filter data. These are some of the operators you'll use:

### Note: 
This is a Coursera lab; follow along with the prompts and outputs to understand what is happening.

## Retrieve after hours failed login attempts <a name="retrieve">
Your team is investigating failed login attempts that were made after business hours. You want to retrieve this information from the login activity. You’ll identify all unsuccessful attempts after 18:00.  
The `login_time` column in the `log_in_attempts` table contains information on when login attempts were made. Office hours end at `'18:00'`.  

The `success` column in the `log_in_attempts` table contains values of `TRUE` or `FALSE` to indicate whether the login was successful. MySQL stores Boolean values as `1` for `TRUE`, and `0` for `FALSE`. This means that `TRUE` is represented as `1`, and `FALSE` represented as `0` in the `success` column.

Use the `AND` operator to retrieve the failed login attempts that occurred after business hours.  
`SELECT * FROM log_in_attempts WHERE login_time > '18:00' AND success = 0;`

Note: Values of TRUE and FALSE are not placed in single quotes because they are not string data. They are Boolean data, which is another data type.

How many failed login attempts occurred after 18:00?

    +----------+----------+------------+------------+---------+-----------------+---------+
    | event_id | username | login_date | login_time | country | ip_address      | success |
    +----------+----------+------------+------------+---------+-----------------+---------+
    |        2 | apatel   | 2022-05-10 | 20:27:27   | CAN     | 192.168.205.12  |       0 |
    |       18 | pwashing | 2022-05-11 | 19:28:50   | US      | 192.168.66.142  |       0 |
    |       20 | tshah    | 2022-05-12 | 18:56:36   | MEXICO  | 192.168.109.50  |       0 |
    |       28 | aestrada | 2022-05-09 | 19:28:12   | MEXICO  | 192.168.27.57   |       0 |
    |       34 | drosas   | 2022-05-11 | 21:02:04   | US      | 192.168.45.93   |       0 |
    |       42 | cgriffin | 2022-05-09 | 23:04:05   | US      | 192.168.4.157   |       0 |
    |       52 | cjackson | 2022-05-10 | 22:07:07   | CAN     | 192.168.58.57   |       0 |
    |       69 | wjaffrey | 2022-05-11 | 19:55:15   | USA     | 192.168.100.17  |       0 |
    |       82 | abernard | 2022-05-12 | 23:38:46   | MEX     | 192.168.234.49  |       0 |
    |       87 | apatel   | 2022-05-08 | 22:38:31   | CANADA  | 192.168.132.153 |       0 |
    |       96 | ivelasco | 2022-05-09 | 22:36:36   | CAN     | 192.168.84.194  |       0 |
    |      104 | asundara | 2022-05-11 | 18:38:07   | US      | 192.168.96.200  |       0 |
    |      107 | bisles   | 2022-05-12 | 20:25:57   | USA     | 192.168.116.187 |       0 |
    |      111 | aestrada | 2022-05-10 | 22:00:26   | MEXICO  | 192.168.76.27   |       0 |
    |      127 | abellmas | 2022-05-09 | 21:20:51   | CANADA  | 192.168.70.122  |       0 |
    |      131 | bisles   | 2022-05-09 | 20:03:55   | US      | 192.168.113.171 |       0 |
    |      155 | cgriffin | 2022-05-12 | 22:18:42   | USA     | 192.168.236.176 |       0 |
    |      160 | jclark   | 2022-05-10 | 20:49:00   | CANADA  | 192.168.214.49  |       0 |
    |      199 | yappiah  | 2022-05-11 | 19:34:48   | MEXICO  | 192.168.44.232  |       0 |
    +----------+----------+------------+------------+---------+-----------------+---------+
    19 rows in set (0.001 sec)

- 19

## Retrieve login attempts on specific dates <a name="dates">
Your team is investigating a suspicious event that occurred on `'2022-05-09'`. You want to retrieve all login attempts that occurred on this day and the day before (`'2022-05-08'`).  

The `login_date` column in the `log_in_attempts` table contains information on the dates when login attempts were made.

Use the `OR` operator to retrieve the failed login attempts on the specified days.  
`SELECT * FROM log_in_attempts WHERE login_date = '2022-05-08' OR login_date = '2022-05-09';`

How many login attempts were made on these two days?

    +----------+----------+------------+------------+---------+-----------------+---------+
    | event_id | username | login_date | login_time | country | ip_address      | success |
    +----------+----------+------------+------------+---------+-----------------+---------+
    |        1 | jrafael  | 2022-05-09 | 04:56:27   | CAN     | 192.168.243.140 |       1 |
    |        3 | dkot     | 2022-05-09 | 06:47:41   | USA     | 192.168.151.162 |       1 |
    |        4 | dkot     | 2022-05-08 | 02:00:39   | USA     | 192.168.178.71  |       0 |
    |        8 | bisles   | 2022-05-08 | 01:30:17   | US      | 192.168.119.173 |       0 |
    |       12 | dkot     | 2022-05-08 | 09:11:34   | USA     | 192.168.100.158 |       1 |
    |       15 | lyamamot | 2022-05-09 | 17:17:26   | USA     | 192.168.183.51  |       0 |
    |       24 | arusso   | 2022-05-09 | 06:49:39   | MEXICO  | 192.168.171.192 |       1 |
    |       25 | sbaelish | 2022-05-09 | 07:04:02   | US      | 192.168.33.137  |       1 |
    |       26 | apatel   | 2022-05-08 | 17:27:00   | CANADA  | 192.168.123.105 |       1 |
    |       28 | aestrada | 2022-05-09 | 19:28:12   | MEXICO  | 192.168.27.57   |       0 |
    |....      |          |            |            |         |                 |         |
    +----------+----------+------------+------------+---------+-----------------+---------+
    75 rows in set (0.055 sec)

- 75     

## Retrieve login attempts outside of Mexico <a name="mexico">
Now, your team is investigating logins that did not originate in Mexico, and you need to find this information. Note that the country field includes entries with `'MEX'` and `'MEXICO'`. You should use the `NOT` and `LIKE` operators and the matching pattern `'MEX%'`.  

Run the following SQL query to retrieve login attempts that did not originate in Mexico.  
`SELECT * FROM log_in_attempts WHERE NOT country LIKE 'MEX%';`

How many login attempts were made outside of Mexico?
    
    +----------+----------+------------+------------+---------+-----------------+---------+
    | event_id | username | login_date | login_time | country | ip_address      | success |
    +----------+----------+------------+------------+---------+-----------------+---------+
    |        1 | jrafael  | 2022-05-09 | 04:56:27   | CAN     | 192.168.243.140 |       1 |
    |        2 | apatel   | 2022-05-10 | 20:27:27   | CAN     | 192.168.205.12  |       0 |
    |        3 | dkot     | 2022-05-09 | 06:47:41   | USA     | 192.168.151.162 |       1 |
    |        4 | dkot     | 2022-05-08 | 02:00:39   | USA     | 192.168.178.71  |       0 |
    |        5 | jrafael  | 2022-05-11 | 03:05:59   | CANADA  | 192.168.86.232  |       0 |
    |        7 | eraab    | 2022-05-11 | 01:45:14   | CAN     | 192.168.170.243 |       1 |
    |        8 | bisles   | 2022-05-08 | 01:30:17   | US      | 192.168.119.173 |       0 |
    |       10 | jrafael  | 2022-05-12 | 09:33:19   | CANADA  | 192.168.228.221 |       0 |
    |       11 | sgilmore | 2022-05-11 | 10:16:29   | CANADA  | 192.168.140.81  |       0 |
    |....      |          |            |            |         |                 |         |
    +----------+----------+------------+------------+---------+-----------------+---------+
    144 rows in set (0.001 sec)

- 144

## Retrieve employees in Marketing <a name="marketing">
For tasks 4, 5 and 6 you need to retrieve the information from the department and office columns in the employees table.  

You can run the following SQL query if you need to view the columns and values in the employees table:  
`SELECT * FROM employees;`

Your team is updating employee machines, and you need to obtain the information about employees in the 'Marketing' department who are located in all offices in the East building (such as `'East-170'` or `'East-320'`).  

Write a SQL query to retrieve this information from the `employees` table. Select all columns and include filters on the `department` and `office` columns to return only the needed records.   
Note: You’ll need to use the `AND` and `LIKE` operators to satisfy both of these criteria.  
`SELECT * FROM employees WHERE department = 'Marketing' AND office LIKE 'East%';`

What is the username of the first employee in the Marketing department in the East building?

    +-------------+--------------+----------+------------+----------+
    | employee_id | device_id    | username | department | office   |
    +-------------+--------------+----------+------------+----------+
    |        1000 | a320b137c219 | elarson  | Marketing  | East-170 |
    |        1052 | a192b174c940 | jdarosa  | Marketing  | East-195 |
    |        1075 | x573y883z772 | fbautist | Marketing  | East-267 |
    |        1088 | k865l965m233 | rgosh    | Marketing  | East-157 |
    |        1103 | NULL         | randerss | Marketing  | East-460 |
    |        1156 | a184b775c707 | dellery  | Marketing  | East-417 |
    |        1163 | h679i515j339 | cwilliam | Marketing  | East-216 |
    +-------------+--------------+----------+------------+----------+
    7 rows in set (0.024 sec)
    
- elarson

## Retrieve employees in Finance or Sales <a name="sales">
Now, your team needs to perform a different update to the computers of all employees in the Finance or the Sales department, and you need to locate information on these employees.  

Write a SQL query to retrieve records for employees in the `'Finance'` or the `'Sales'` department.  
Note: Even though both conditions are based on the same column, you need to write out both full conditions. This means that you must specify `department` as the column in both conditions.   
`SELECT * FROM employees WHERE department = 'Sales' OR department = 'Finance' ORDER BY department;`

What is the username of the first employee in the Sales department returned by the query?  

    +-------------+--------------+----------+------------+-------------+
    | employee_id | device_id    | username | department | office      |
    +-------------+--------------+----------+------------+-------------+
    |        1195 | n516o853p957 | orainier | Finance    | East-346    |
    |        1136 | g299h520i457 | jhawes   | Finance    | West-416    |
    |        1122 | s103t952u851 | btorres  | Finance    | West-319    |
    |        1105 | b551c837d758 | kmei     | Finance    | Central-232 |
    |        1099 | v283w690x104 | anaser   | Finance    | West-357    |
    |        1174 | s371t911u987 | eortiz   | Finance    | North-428   |
    |        1103 | NULL         | randerss | Marketing  | East-460    |
    |....         |              |          |            |             |
    |        1025 | z381a365b233 | jhill    | Sales      | North-115   |
    |        1039 | n253o917p623 | cjackson | Sales      | East-378    |
    |        1024 | y976z753a267 | iuduike  | Sales      | South-215   |
    |        1130 | a317b635c465 | tsnow    | Sales      | Central-451 |
    |        1176 | u849v569w521 | nliu     | Sales      | West-220    |
    |        1186 | e281f433g404 | sacosta  | Sales      | North-460   |
    |        1011 | l748m120n401 | drosas   | Sales      | South-292   |
    |        1169 | NULL         | mmitchel | Sales      | Central-250 |
    |        1086 | i281j129k749 | lmajumda | Sales      | West-499    |
    |        1072 | u905v920w694 | esmith   | Sales      | East-421    |
    |        1009 | NULL         | lrodriqu | Sales      | South-134   |
    |....         |              |          |            |             |
    +-------------+--------------+----------+------------+-------------+
    71 rows in set (0.001 sec)

- lrodriqu

NOTE: I am not sure what happened here, I guessed, the answer was correct even though the output does not display the answer I put.  

## Retrieve all employees not in IT <a name="it">
Your team needs to make one more update. This update was already made to employee computers in the Information Technology department. The team needs information about employees who are not in that department. You should use the NOT operator to identify these employees.  

Write a SQL query to retrieve records for employees who are not in the `'Information Technology'` department.  
`SELECT * FROM employees WHERE NOT department = 'information Technology';`

How many employees are not in the Information Technology department?

    +-------------+--------------+----------+-----------------+-------------+
    | employee_id | device_id    | username | department      | office      |
    +-------------+--------------+----------+-----------------+-------------+
    |        1000 | a320b137c219 | elarson  | Marketing       | East-170    |
    |        1001 | b239c825d303 | bmoreno  | Marketing       | Central-276 |
    |        1002 | c116d593e558 | tshah    | Human Resources | North-434   |
    |        1003 | d394e816f943 | sgilmore | Finance         | South-153   |
    |        1004 | e218f877g788 | eraab    | Human Resources | South-127   |
    |        1005 | f551g340h864 | gesparza | Human Resources | South-366   |
    |        1007 | h174i497j413 | wjaffrey | Finance         | North-406   |
    |        1008 | i858j583k571 | abernard | Finance         | South-170   |
    |        1009 | NULL         | lrodriqu | Sales           | South-134   |
    |        1010 | k242l212m542 | jlansky  | Finance         | South-109   |
    |....         |              |          |                 |             |
    +-------------+--------------+----------+-----------------+-------------+
    161 rows in set (0.001 sec)

- 161
 
## Conclusion <a name="conclusion">
You now have practical experience in using SQL to

run SQL queries to retrieve information from a database and
apply `AND`, `OR`, and `NOT` operators to filter SQL queries.
