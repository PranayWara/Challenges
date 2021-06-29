# Challenges
World and Sakila Challenges

World Challenges

USE world;

1. "Using COUNT, get the number of cities in the USA."

SELECT COUNT(Name) from city WHERE city.CountryCode = 'USA';
Output = 274

2. "Find out the population and life expectancy for people in   Argentina."

SELECT Population, LifeExpectancy FROM country WHERE Name = 'Argentina';
Output = 
Populatuion = 37032000
Life Expectancy = 75.1

3. "Using IS NOT NULL, ORDER BY, and LIMIT, which country has the highest life expectancy?"

SELECT * FROM country WHERE LifeExpectancy = (
	SELECT LifeExpectancy FROM country ORDER BY LifeExpectancy DESC LIMIT 1
);

Output = Andora, 83.5

4. "Using JOIN ... ON, find the capital city of Spain."

SELECT city.name, country.name FROM country JOIN city ON country.capital=city.ID AND country.code=city.countryCode WHERE country.name='Spain';

Output = Madrid

5. "Using JOIN ... ON, list all the languages spoken in the Southeast Asia region."

SELECT language,region FROM countrylanguage join country on countrylanguage.CountryCode = country.Code
WHERE country.Region = 'Southeast Asia';

Output = 'All countries outputted'

6. "Using a single query, list 25 cities around the world that start with the letter F."

SELECT NAME FROM city WHERE NAME LIKE 'f%' ORDER BY NAME DESC LIMIT 25;

Output = 'All countries outputted'

7. "Using COUNT and JOIN ... ON, get the number of cities in China."

SELECT COUNT(Name) from city WHERE city.CountryCode = 'CHN';

Output = 363

8."Using IS NOT NULL, ORDER BY, and LIMIT, which country has the lowest population? Discard non-zero populations"

SELECT * FROM country WHERE Population = (
SELECT Population FROM country ORDER BY Population IS NOT NULL ASC LIMIT 1
);

Output = Aruba, 103000

9. "Using aggregate functions, return the number of countries the database contains."

SELECT COUNT(DISTINCT Name) FROM country;

Output = 239
