# Challenges
World and Sakila Challenges
1. SELECT COUNT(ID) FROM city;
2. SELECT Population, LifeExpectancy FROM country WHERE Name = 'Argentina';
3. SELECT * FROM country WHERE LifeExpectancy = (
	SELECT LifeExpectancy FROM country ORDER BY LifeExpectancy DESC LIMIT 1
);
4. SELECT city.name, country.name FROM country JOIN city ON country.capital=city.ID AND country.code=city.countryCode WHERE country.name='Spain';
5. SELECT language,region FROM countrylanguage join country on countrylanguage.CountryCode = country.Code
WHERE country.Region = 'Southeast Asia';