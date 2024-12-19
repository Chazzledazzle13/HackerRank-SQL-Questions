# HackerRank-SQL-Questions
A list of SQL questions that were solved on HackerRank

➡️ [HackerRank](https://www.hackerrank.com/dashboard) is a practice site for multiple computer languages including Python, R, and, of course, SQL. All questions were solved using MySQL.

## Below are some hand picked questions along with my answers:

### 1. African Cities
**Question:** Given the CITY and COUNTRY tables, query the names of all cities where the CONTINENT is 'Africa'.
Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

The CITY and COUNTRY tables are described as follows:
[City and Country Tables Info](https://www.hackerrank.com/challenges/african-cities/problem)

**Answer:** 

SELECT CITY.NAME
FROM CITY
INNER JOIN COUNTRY 
ON CITY.COUNTRYCODE = COUNTRY.CODE
WHERE COUNTRY.CONTINENT = 'AFRICA';



### 2. The PADS
**Question:** Generate the following two result sets:

Query an alphabetically ordered list of all names in OCCUPATIONS, immediately followed by the first letter of each profession as a parenthetical (i.e.: enclosed in parentheses). For example: AnActorName(A), ADoctorName(D), AProfessorName(P), and ASingerName(S).
Query the number of ocurrences of each occupation in OCCUPATIONS. Sort the occurrences in ascending order, and output them in the following format:

There are a total of [occupation_count] [occupation]s.
where [occupation_count] is the number of occurrences of an occupation in OCCUPATIONS and [occupation] is the lowercase occupation name. If more than one Occupation has the same [occupation_count], they should be ordered alphabetically.

Note: There will be at least two entries in the table for each type of occupation.

The OCCUPATIONS table is described as follows:
[Occupation Table Info](https://www.hackerrank.com/challenges/the-pads/problem)

Occupation will only contain one of the following values: Doctor, Professor, Singer or Actor.

**Answer:** 

SELECT CONCAT(NAME,'(', SUBSTR(OCCUPATION,1,1), ')') AS NAME_AND_JOB
FROM OCCUPATIONS
ORDER BY NAME_AND_JOB;

SELECT CONCAT('There are a total of ', COUNT(OCCUPATION), " ", LOWER(OCCUPATION), 's.') AS COMBO_JOB
FROM OCCUPATIONS
GROUP BY OCCUPATION
ORDER BY COMBO_JOB;


### 3. Weather Observation Station 15
Query the Western Longitude (LONG_W) for the largest Northern Latitude (LAT_N) in STATION that is
less than 137.2345. Round your answer to 4 decimal places.

The STATION table is described as follows:
[Station Info](https://www.hackerrank.com/challenges/weather-observation-station-15/problem)

**Answer:** 

SELECT ROUND(LONG_W,4) 
FROM STATION 
WHERE LAT_N = (SELECT MAX(LAT_N) FROM STATION WHERE LAT_N < 137.2345);

