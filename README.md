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

SELECT COUNT(city.Name) FROM city JOIN country ON city.CountryCode = country.code WHERE country.Code = 'CHN';

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

UPDATE country
SET HeadOfState = 'Elizabeth II'
WHERE HeadOfState = 'Elisabeth II';

SELECT Name,Code FROM country WHERE HeadOfState = 'Elizabeth II';

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

SELECT CountryCode, COUNT(CountryCode) AS `value_occurrence` 
FROM countrylanguage GROUP BY CountryCode ORDER BY `value_occurrence` DESC LIMIT 10;

Output = 
CHN	12
IND	12
CAN	12
USA	12
RUS	12
TZA	11
ZAF	11
NGA	10
IRN	10
KEN	10

17. "List every country where over 50% of its population can speak German."

SELECT CountryCode,Percentage FROM countrylanguage WHERE Percentage >= 50 and Language = 'German' ORDER BY Percentage DESC;

Output = AUT, DEU, LIE, CHE

18. "Which country has the worst life expectancy? Discard zero or null values."

SELECT Name,LifeExpectancy FROM country WHERE LifeExpectancy IS NOT NULL ORDER BY LifeExpectancy ASC LIMIT 10;

Output = Zambia, Mozambique, Malawi,Zimbabwe, Angola, Rwanda, Botswana, Swaziland, Niger, Namibia

19. "List the top three most common government forms."

SELECT GovernmentForm, COUNT(GovernmentForm) AS `value_occurrence` 
FROM country GROUP BY GovernmentForm ORDER BY `value_occurrence` DESC LIMIT 3;

Output = Republic, Constitutional Monarchy, Federal Republic

20. "How many countries have gained independence since records began?"

SELECT COUNT(IndepYear) From country WHERE IndepYear IS NOT NULL;

Output = 192


Sakila Challenges

USE sakila;

1. "List all actors."

SELECT * FROM actor;

Output = 'All Actors in list'

2. "Find the surname of the actor with the forename 'John'."

SELECT first_name,last_name FROM actor WHERE first_name = 'John';

Output = JOHN SUVARI

3. "Find all actors with surname 'Neeson'."

SELECT first_name,last_name FROM actor WHERE last_name = 'Neeson';

Output = CHRISTIAN NEESON, JAYNE NEESON

4. "Find all actors with ID numbers divisible by 10."

SELECT first_name,last_name,actor_id FROM actor 
WHERE actor_id % 10 = 0;

Output = 
CHRISTIAN	GABLE
LUCILLE	TRACY
SANDRA	PECK
JOHNNY	CAGE
NATALIE	HOPKINS
HENRY	BERRY
MICHELLE	MCCONAUGHEY
RALPH	CRUZ
SEAN	GUINESS
SPENCER	DEPP
SUSAN	DAVIS
PENELOPE	MONROE
GRETA	KEITEL
WHOOPI	HURT
JAYNE	NOLTE
CHRIS	DEPP
MENA	HOPPER
JEFF	SILVERSTONE
AUDREY	BAILEY
THORA	TEMPLE

5. "What is the description of the movie with an ID of 100?"

SELECT film_id,title FROM film WHERE film_id = '100';

Output = BROOKLYN DESERT
A Beautiful Drama of a Dentist And a Composer who must Battle a Sumo Wrestler in The First Manned Space Station

6. "Find every R-rated movie."

SELECT title,rating FROM film WHERE rating = "R";

Output = 'All films printed'

7. "Find every non-R-rated movie."

SELECT title,rating FROM film WHERE rating != "R";

Output = 'All films printed'

8. "Find the ten shortest movies."

SELECT title,length FROM film ORDER BY length ASC LIMIT 10;

Output:
RIDGEMONT SUBMARINE
IRON MOON
ALIEN CENTER
LABYRINTH LEAGUE
KWAI HOMEWARD
DOWNHILL ENOUGH
HALLOWEEN NUTS
HANOVER GALAXY
DIVORCE SHINING
HAWK CHILL

9. "Find the movies with the longest runtime, without using LIMIT."


SELECT title,length FROM film ORDER BY length DESC;

Output = 'All films printed'

10. Find all movies that have deleted scenes.

SELECT title,special_features FROM film WHERE special_features = 'Deleted Scenes';

Output = 'All films printed'

11. "Using HAVING, reverse-alphabetically list the last names that are not repeated."


S

Output = 

12. "Using HAVING, list the last names that appear more than once, from highest to lowest frequency."

S

Output = 

13. "Which actor has appeared in the most films?"

SELECT actor.actor_id, actor.first_name, actor.last_name, COUNT(actor_id) as film_count
FROM actor JOIN film_actor USING (actor_id) GROUP BY actor_id ORDER BY film_count DESC LIMIT 1;

Output = GINA	DEGENERES	42

14. "When is 'Academy Dinosaur' due?"

SELECT rental_date,rental_date + INTERVAL(SELECT rental_duration FROM film WHERE film_id = 1) 
day AS due_date FROM rental WHERE rental_id = (SELECT rental_id FROM rental ORDER BY rental_id DESC LIMIT 1);

Output = 2005-08-29 22:50:12

15. "What is the average runtime of all films?"

SELECT AVG(length) FROM film;

Output = 115.272

16. "List the average runtime for every film category."

SELECT category.Name, AVG(length) FROM film JOIN film_category USING (film_id)  JOIN category USING (category_id)
GROUP BY category.name ORDER BY AVG(length) DESC;

Output = 'All average length of each category'

