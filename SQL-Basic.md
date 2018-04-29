# SQL (MS SQL Server)

## Basic Select

### Revising the Select Query I
> SELECT * FROM CITY WHERE POPULATION > 100000 AND COUNTRYCODE = 'USA';

### Revising the Select Query II
> SELECT NAME FROM CITY WHERE COUNTRYCODE = 'USA' AND POPULATION 120000;

### Select All
> SELECT * FROM CITY;

### Select by ID
> SELECT * FROM CITY WHERE ID = 1661;

### Japanese Cities' Attributes
> SELECT * FROM CITY WHERE COUNTRYCODE = 'JPN';

### Japanese Cities' Names
> SELECT NAME FROM CITY WHERE COUNTRYCODE = 'JPN';

### Weather Observation Station 1
> SELECT CITY, STATE FROM STATION;

### Weather Observation Station 3
> SELECT DISTINCT (CITY) FROM STATION WHERE (ID % 2 = 0);

### Weather Observation Station 4
> SELECT (COUNT (CITY)) - (COUNT (DISTINCT CITY)) FROM STATION;

### Weather Observation Station 5
> SELECT TOP 1 CITY, LEN(CITY) AS L FROM STATION ORDER BY L, CITY;
SELECT TOP 1 CITY, LEN(CITY) AS L FROM STATION ORDER BY L DESC, CITY DESC;

### Weather Observation Station 6
> SELECT DISTINCT CITY FROM STATION WHERE LOWER (LEFT(CITY, 1)) IN ('a', 'e', 'i', 'o', 'u'); 

### Weather Observation Station 7
> SELECT DISTINCT CITY FROM STATION WHERE LOWER (RIGHT(CITY, 1)) IN ('a', 'e', 'i', 'o', 'u'); 

### Weather Observation Station 8
> SELECT DISTINCT CITY FROM STATION WHERE LOWER (LEFT(CITY, 1)) IN ('a', 'e', 'i', 'o', 'u') AND LOWER (RIGHT(CITY, 1)) IN ('a', 'e', 'i', 'o', 'u');

### Weather Observation Station 9
> SELECT DISTINCT CITY FROM STATION WHERE LOWER (LEFT(CITY, 1)) NOT IN ('a', 'e', 'i', 'o', 'u'); 

### Weather Observation Station 10
> SELECT DISTINCT CITY FROM STATION WHERE LOWER (RIGHT(CITY, 1)) NOT IN ('a', 'e', 'i', 'o', 'u'); 

### Weather Observation Station 11
> SELECT DISTINCT CITY FROM STATION WHERE LOWER (LEFT(CITY, 1)) NOT IN ('a', 'e', 'i', 'o', 'u') OR LOWER (RIGHT(CITY, 1)) NOT IN ('a', 'e', 'i', 'o', 'u');

### Weather Observation Station 12
> SELECT DISTINCT CITY FROM STATION WHERE LOWER (LEFT(CITY, 1)) NOT IN ('a', 'e', 'i', 'o', 'u') AND LOWER (RIGHT(CITY, 1)) NOT IN ('a', 'e', 'i', 'o', 'u');

### Higher Than 75 Marks
> SELECT NAME FROM STUDENTS WHERE MARKS > 75 ORDER BY RIGHT(NAME, 3), ID;

### Employee Names
> SELECT NAME FROM EMPLOYEE ORDER BY NAME;

### Employee Salaries
> SELECT NAME FROM EMPLOYEE WHERE SALARY > 2000 AND MONTHS < 10 ORDER BY EMPLOYEE_ID;


## Advanced Select

### Type of Triange
> SELECT CASE WHEN A + B <= C OR A + C <= B OR B + C <= A THEN 'Not A Triangle'
            WHEN A = B AND B = C THEN 'Equilateral'
            WHEN A = B OR A = C OR B = C THEN 'Isosceles'
            ELSE 'Scalene'
        END
FROM TRIANGLES;

### The PADS
> select concat(name, '(', substring(occupation, 1, 1), ')') from OCCUPATIONS order by name;
select concat('There are a total of ', count(occupation), ' ', lower(occupation), 's.') from OCCUPATIONS
group by occupation order by count(occupation), occupation;

### Occupations
**[Not Submitted]**
> SELECT Doctor_O, Professor_O, Singer_O, Actor_O
FROM
(
    SELECT
        CASE WHEN OCCUPATION = 'Doctor' THEN NAME ELSE NULL END AS Doctor_O,
        CASE WHEN OCCUPATION = 'Professor' THEN NAME ELSE NULL END AS Professor_O, 
        CASE WHEN OCCUPATION = 'Singer' THEN NAME ELSE NULL END AS Singer_O, 
        CASE WHEN OCCUPATION = 'Actor' THEN NAME ELSE NULL END As Actor_O
    FROM OCCUPATIONS
    --ORDER BY NAME
)
TEMP1
WHERE Doctor_O IS NOT NULL OR Professor_O IS NOT NULL OR Singer_O IS NOT NULL OR Actor_O IS NOT NULL
ORDER BY 1, 2, 3, 4;

### Binary Tree Nodes
> SELECT N, (
    CASE WHEN N = ANY (SELECT DISTINCT P FROM BST) AND P IS NOT NULL THEN 'Inner'
         WHEN P IS NULL THEN 'Root'
         ELSE 'Leaf'
    END
    ) NODE_TYPE
FROM BST
ORDER BY N, P;

### New Companies
> SELECT T1.company_code, T1.founder, COUNT(DISTINCT T2.lead_manager_code), COUNT(DISTINCT T3.senior_manager_code), COUNT(DISTINCT T4.manager_code), COUNT(DISTINCT T5.employee_code)
FROM company T1,
>
>(SELECT company_code, lead_manager_code
FROM Lead_Manager
GROUP BY lead_manager_code, company_code) T2,
>
>(SELECT lead_manager_code, senior_manager_code
FROM Senior_Manager
GROUP BY senior_manager_code, lead_manager_code) T3,
>
>(SELECT senior_manager_code, manager_code
FROM Manager
GROUP BY manager_code, senior_manager_code) T4,
>
>(SELECT manager_code, employee_code
FROM Employee
GROUP BY employee_code, manager_code) T5
>
>WHERE T1.company_code = T2.company_code
AND T2.lead_manager_code = T3.lead_manager_code
AND T3.senior_manager_code = T4.senior_manager_code
AND T4.manager_code = T5.manager_code
>
>GROUP BY T1.company_code, T1.founder
ORDER BY T1.company_code;


## Aggregation
> SELECT COUNT(*) FROM CITY WHERE POPULATION > 100000;

> SELECT SUM(POPULATION) FROM CITY WHERE DISTRICT = LOWER('CALIFORNIA');

> SELECT ROUND(AVG(CAST(POPULATION AS FLOAT)), 3) FROM CITY WHERE DISTRICT = LOWER('CALIFORNIA');

> SELECT ROUND(AVG(POPULATION), 2, 0) FROM CITY;

> SELECT SUM(POPULATION) FROM CITY WHERE COUNTRYCODE = LOWER('JPN');

> SELECT MAX(POPULATION) - MIN(POPULATION) AS DIFFERENCE FROM CITY;

> - SELECT  employee_id, name, months, salary, (salary * months) AS earnings FROM Employee;
>
> SELECT TOP 1 (salary * months) AS earnings, count(*) FROM Employee GROUP BY (salary * months) ORDER BY earnings DESC;

> SELECT ROUND(CAST(SUM(LAT_N) AS DECIMAL(10,2)), 2, 0) AS lat, ROUND(CAST(SUM(LONG_W) AS DECIMAL(10,2)), 2, 0) AS lon FROM STATION;

> SELECT CAST(SUM(LAT_N) AS DECIMAL(10,4)) AS sum_lat_n
FROM STATION
WHERE CAST(LAT_N AS DECIMAL(10,4)) > 38.7880
AND CAST(LAT_N AS DECIMAL(10,4)) < 137.2345;

> SELECT CAST(MAX(LAT_N) AS DECIMAL(10,4)) AS max_lat_n
FROM STATION
WHERE CAST(LAT_N AS DECIMAL(10,4)) < 137.2345;

> SELECT CAST(LONG_W AS DECIMAL(10,4)) AS lon
FROM STATION
WHERE CAST(LAT_N AS DECIMAL(10,4)) = (
    SELECT CAST(MAX(LAT_N) AS DECIMAL(10,4)) AS sum_lat_n
    FROM STATION
    WHERE CAST(LAT_N AS DECIMAL(10,4)) < 137.2345
);

> SELECT CAST(MIN(LAT_N) AS DECIMAL(10,4)) AS min_lat_n
FROM STATION
WHERE CAST(LAT_N AS DECIMAL(10,4)) > 38.7780;

> SELECT CAST(LONG_W AS DECIMAL(10,4)) AS lon
FROM STATION
WHERE CAST(LAT_N AS DECIMAL(10,4)) = (
    SELECT CAST(MIN(LAT_N) AS DECIMAL(10,4)) AS min_lat_n
    FROM STATION
    WHERE CAST(LAT_N AS DECIMAL(10,4)) > 38.7780
);

> SELECT CAST (ROUND( ABS(MIN(LAT_N) - MAX(LAT_N)) + ABS(MIN(LONG_W) - MAX(LONG_W) ), 4, 0) AS DECIMAL(10,4)) AS 'MANHATTAN DISTANCE'
FROM STATION;

> /*
A = MIN(LAT_N)
B = MAX(LAT_N)
C = MIN(LONG_W)
D = MAX(LONG_W)
P1(A, C)
P2(B, D)
- Euclidean distance = SQRT((B - A) ^ 2 + (D - C) ^ 2)
> */

> SELECT
CAST(SQRT( POWER((MAX(LAT_N) - MIN(LAT_N)), 2) + POWER((MAX(LONG_W) - MIN(LONG_W)), 2) ) AS DECIMAL(10,4)) AS 'Euclidean distance'
FROM STATION;

> WITH MY_TABLE AS
(
    SELECT 
        ROW_NUMBER() OVER (ORDER BY LAT_N) AS RowNumber, LAT_N
    FROM
        STATION
)
SELECT
    CAST(LAT_N AS DECIMAL(10,4))
FROM
    MY_TABLE
WHERE
    RowNumber = (
        SELECT
            CASE WHEN COUNT(LAT_N) % 2 <> 0 THEN (COUNT(LAT_N) + 1) / 2
            ELSE (COUNT(LAT_N)) / 2
            END
        FROM STATION
);


## Basic JOIN
### Asian Population
> SELECT SUM(CITY.POPULATION)
FROM CITY, COUNTRY
WHERE CITY.CountryCode = COUNTRY.Code
AND COUNTRY.Continent = LOWER('Asia');

### African Cities

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5MTQ1NzI5MjQsMTg1ODg2NzY4MSwtOD
U5Njk1MDUwLC0zMzQ2NTM5MzgsLTExNDE0NDk3MDMsLTkwNzU0
MTc4NywtMTE3Mjk4MjYzMywtODA4NDA0NzAsMTE5NzU3NTUyMC
wtMTI3MDg1NjIyMSwtNzA3NzA0NzI5LC0xMzgxODg2Njg3LC04
MDA4NzE3NzYsLTEzNjA0NDg0NywtNDcyOTgzMzgyLC0xNzgzMT
YyNjY0LDc0ODAyOTk2NywtMTc2NDQxNzU5NSwtMjcyNzg1NDE1
LC02NzgwNzk0MTBdfQ==
-->