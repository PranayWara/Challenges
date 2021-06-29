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

8. "Using IS NOT NULL, ORDER BY, and LIMIT, which country has the lowest population? Discard non-zero populations"

SELECT * FROM country WHERE Population = (
SELECT Population FROM country ORDER BY Population IS NOT NULL ASC LIMIT 1
);

Output = Aruba, 103000

9. "Using aggregate functions, return the number of countries the database contains."

SELECT COUNT(DISTINCT Name) FROM country;

Output = 239

10. "What are the top ten largest countries by area?"

SELECT * FROM country 
ORDER BY country.SurfaceArea DESC LIMIT 10;

Output = Russian Federation, Antarctica, Canada, China, United States, Brazil, Australia, India, Argentina, Kazakstan

11. "What are the top ten largest countries by area?"

SELECT Name FROM city 
WHERE CountryCode = 'JPN'
ORDER BY Population DESC LIMIT 5;

Output = Tokyo, Jokohama [Yokohama], Osaka, Nagoya, Sapporo

12. "List the names and country codes of every country with Elizabeth II as its Head of State. You will need to fix the mistake first!"

SELECT Name,Code FROM country WHERE HeadOfState = 'Elisabeth II';

Output = 'All countries outputted'

13. "List the top ten countries with the smallest population-to-area ratio. Discard any countries with a ratio of 0."

SELECT Name,Population,SurfaceArea FROM country ORDER BY Population/SurfaceArea IS NOT NULL ASC LIMIT 10;

Output = Aruba, Afghanistan, Angola, Anguilla, Albania, Andorra, Netherlands Antilles, United Arab Emirates ,Argentina ,Armenia

14. "List every unique world language."

SELECT DISTINCT Language
FROM countrylanguage;

Output = 'All distinct languages outputted'

15. "List the names and GNP of the world's top 10 richest countries."

SELECT Name,GNP FROM country ORDER BY GNP DESC LIMIT 10;

Output = United States, Japan, Germany, France, United Kingdom, Italy, China, Brazil, Canada, Spain

16. "List the names of, and number of languages spoken by, the top ten most multilingual countries."

S

Output = 

17. "List every country where over 50% of its population can speak German."

s

Output = 

18. "Which country has the worst life expectancy? Discard zero or null values."

SELECT Name,LifeExpectancy FROM country WHERE LifeExpectancy IS NOT NULL ORDER BY LifeExpectancy ASC LIMIT 10;

Output = Zambia, Mozambique, Malawi,Zimbabwe, Angola, Rwanda, Botswana, Swaziland, Niger, Namibia

19. List the top three most common government forms.


S

Output = 

20. How many countries have gained independence since records began?

s

Output = 



