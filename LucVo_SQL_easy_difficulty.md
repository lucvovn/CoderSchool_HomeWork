## Revising the Select Query I
Submitted Code

```sql=1
SELECT * FROM CITY WHERE population > 100000 AND CountryCode LIKE "USA"
```
## Revising the Select Query II
Submitted Code

```sql=1
SELECT NAME FROM CITY WHERE COUNTRYCODE LIKE "USA" AND POPULATION >  120000
```
## Select All
Submitted Code

```sql=1
SELECT * FROM CITY 
```
## Select By ID
Submitted Code

```sql=1
SELECT * FROM CITY WHERE ID = 1661
```
## Japanese Cities' Attributes

```sql=1
SELECT * FROM CITY WHERE COUNTRYCODE LIKE "JPN"
```
## Japanese Cities' Names
Submitted Code

```sql=1
SELECT NAME FROM CITY WHERE COUNTRYCODE LIKE "JPN"
```
## Weather Observation Station 1
Submitted Code

```sql=1
SELECT CITY, STATE FROM STATION 
```
## Weather Observation Station 3
Submitted Code

```sql=1
SELECT DISTINCT CITY FROM STATION WHERE MOD(ID,2)=0
```
## Weather Observation Station 4
Submitted Code

```sql=1
SELECT NUMBERCITY - NUMBERCITYDIST 
FROM 
    (SELECT COUNT(CITY) AS NUMBERCITY FROM STATION) AS A,
    (SELECT COUNT(DISTINCT CITY) AS NUMBERCITYDIST FROM STATION) AS B
```
## Weather Observation Station 5
Submitted Code

```sql=1
select CITY,char_length(CITY) as lencity
from station 
where char_length(CITY) = (SELECT MIN(CHAR_LENGTH(CITY))   FROM STATION)
ORDER BY CITY ASC
LIMIT 1;

select CITY,char_length(CITY) as lencity
from station 
where char_length(CITY) = (SELECT MAX(CHAR_LENGTH(CITY))   FROM STATION)
ORDER BY CITY ASC
LIMIT 1;
```
## Weather Observation Station 6
Submitted Code
```sql=1
SELECT DISTINCT CITY
FROM STATION 
WHERE LEFT(CITY,1) IN ('a','e','i','o','u') 
```
## Weather Observation Station 7
```sql=1
select distinct city 
from station 
where right(city,1) in ('a', 'e', 'i', 'o', 'u')
```
## Weather Observation Station 8
```sql=1
select distinct city
from station
where left(city,1) in ('a', 'e', 'i', 'o', 'u') and right(city,1) in ('a', 'e', 'i', 'o', 'u')
```
## Weather Observation Station 9

```sql=1
select distinct city
from station
where left(city,1) not in ('a', 'e', 'i', 'o', 'u') 
```
## Weather Observation Station 10
```sql=1
select distinct city
from station
where  right(city,1) not in ('a', 'e', 'i', 'o', 'u')
```
## Weather Observation Station 11

```sql=1
select distinct city
from station
where  right(city,1) not in ('a', 'e', 'i', 'o', 'u') or left(city,1) not in ('a', 'e', 'i', 'o', 'u')
```
## Weather Observation Station 12

```sql=1
select distinct city
from station
where  right(city,1) not in ('a', 'e', 'i', 'o', 'u') and left(city,1) not in ('a', 'e', 'i', 'o', 'u')
```
## Higher Than 75 Marks

```sql=1
select name
from STUDENTS
where marks > 75
order by right(name,3) asc,id asc
```

## Employee Names

```sql=1
select name from Employee order by name asc
```

## Employee Salaries

```sql=1
select name
from employee
where salary > 2000 and months < 10 
order by employee_id asc
```

## Type of Triangle

```sql
SELECT 
IF (( (A+B)>C AND (A+C)>B AND (B+C)>A), 
    IF((A=B AND A=C AND B=C),"Equilateral",
        IF((A=B OR A=C OR B=C),"Isosceles","Scalene")), "Not A Triangle")
FROM TRIANGLES 
```

## Revising Aggregations - The Count Function

```sql=1
select count(Name) from CITY where population > 100000
```

## Revising Aggregations - The Sum Function

```sql=1
select sum(population) from CITY where district like "California"
```

## Revising Aggregations - Averages

```sql=1
select AVG(population) from city where district like "California"
```

## Average Population

```sql=1
select floor(AVG(population)) from city
```

## Japan Population

```sql=1
select sum(population) from city where COUNTRYCODE like "JPN"
```

## Population Density Difference

```sql=1
select max(population) - min(population) from city
```

## The Blunder

```sql=1
select CEILING( AVG(salary) - AVG(cast(replace(cast(salary as CHAR),0,'') as SIGNED)))from EMPLOYEES;
```

## Top Earners

```sql=1
select salary*months as totalearn, count(employee_id)
from Employee
group by totalearn
order by totalearn desc
limit 1
```
## Weather Observation Station 2

```sql=1
select round(sum(LAT_N),2) ,round(sum(LONG_W ),2) from STATION 
```

## Weather Observation Station 13

```sql=1
select Truncate(sum(LAT_N),4) from station where LAT_N > 38.7880 and LAT_N<137.2345
```
## Weather Observation Station 14

```sql=1
select Truncate(max(LAT_N),4) from station where LAT_N<137.2345
```

## Weather Observation Station 15

```sql=1
select round(long_w,4) from station where LAT_N = (select max(LAT_N) from station where LAT_N < 137.2345);
```
## Weather Observation Station 16

```sql=1
select round(min(LAT_N),4) from station where LAT_N > 38.7780
```
## Weather Observation Station 17

```sql=1
select round(LONG_W,4) from station where LAT_N = (select min(LAT_N) from station where LAT_N > 38.7780)
```
## Asian Population

```sql=1
select sum(city.population) from city left join country on city.countrycode = country.code where CONTINENT  like "asia"
```

## African Cities

```sql=1
select city.name from city left join country on city.countrycode = country.code where CONTINENT  like "africa"
```

## Average Population of Each Continent

```sql=1
select country.continent,floor(avg(city.population)) from country join city  on city.countrycode = country.code group by country.continent
```
## Draw The Triangle 1

```sql=1
DECLARE @i INT = 20
WHILE (@i > 0) 
BEGIN
   PRINT REPLICATE('*', @i) 
   SET @i = @i - 1
END
```

## Draw The Triangle 2

```sql=1
DECLARE @i INT = 0
WHILE (@i <= 20) 
BEGIN
   PRINT REPLICATE('* ', @i) 
   SET @i = @i + 1
END
```
