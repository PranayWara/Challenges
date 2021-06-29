# Challenges
World and Sakila Challenges

World Challenges

USE world;

1. "Using COUNT, get the number of cities in the USA."

SELECT COUNT(Name) from city WHERE city.CountryCode = 'USA';

2. "Find out the population and life expectancy for people in   Argentina."

SELECT Population, LifeExpectancy FROM country WHERE Name = 'Argentina';

3. "Using IS NOT NULL, ORDER BY, and LIMIT, which country has the highest life expectancy?"

SELECT * FROM country WHERE LifeExpectancy = (
	SELECT LifeExpectancy FROM country ORDER BY LifeExpectancy DESC LIMIT 1
);

4. "Using JOIN ... ON, find the capital city of Spain."

SELECT city.name, country.name FROM country JOIN city ON country.capital=city.ID AND country.code=city.countryCode WHERE country.name='Spain';

5. "Using JOIN ... ON, list all the languages spoken in the Southeast Asia region."

SELECT language,region FROM countrylanguage join country on countrylanguage.CountryCode = country.Code
WHERE country.Region = 'Southeast Asia';

6. "Using a single query, list 25 cities around the world that start with the letter F."

SELECT NAME FROM city WHERE NAME LIKE 'f%' ORDER BY NAME DESC LIMIT 25;

7. "Using COUNT and JOIN ... ON, get the number of cities in China."

s

8."Using IS NOT NULL, ORDER BY, and LIMIT, which country has the lowest population? Discard non-zero populations"

SELECT * FROM country WHERE Population = (
SELECT Population FROM country ORDER BY Population IS NOT NULL ASC LIMIT 1
);
