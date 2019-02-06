## Operators in SELECT Statements

>1. Write out a generic SELECT statement.

```SQL
SELECT <column name(s)>
  FROM <table name>
  WHERE <condition>
```
---
>2. Create a fun way to remember the order of operations in a SELECT statement

```SQL
SELECT, FROM, JOIN, WHERE, GROUP BY, HAVING, SELECT, ORDER BY, LIMIT
```
Suzie From Jersey With Green Horses Singing On Land

---
>3. Given this [dogs table](https://www.db-fiddle.com/f/kvD6xZQ14vRbpPe5muA92L/0), write queries to select the following pieces of data: Intake teams typically guess the breed of shelter dogs, so the breed column may have multiple words (for example, "Labrador Collie mix").

- Display the name, gender, and age of all dogs that are part Labrador.
```SQL
SELECT name, gender, age
  FROM dogs
  WHERE breed LIKE "%labrador%"
```
- Display the ids of all dogs that are under 1 year old.
```SQL
SELECT id
  FROM dogs
  WHERE age < 1
```
- Display the name and age of all dogs that are female and over 35lbs.
```SQL
SELECT name, age
  FROM dogs
  WHERE gender = 'F' AND weight > 35
```
- Display all of the information about all dogs that are not Shepherd mixes.
```SQL
SELECT *
FROM dogs
WHERE breed NOT LIKE '%shepherd%'
```
- Display the id, age, weight, and breed of all dogs that are either over 60lbs or Great Danes.
```SQL
SELECT id, age, weight
FROM dogs
WHERE weight > 60 OR breed = 'great dane'
```
---
>4. Given this [cats table](https://www.db-fiddle.com/f/55ePhx9NLn7PzdGnebFaG7/0), what records are returned from these queries?

 ```SQL
SELECT name, adoption_date
FROM cats;
```
A:    

  name    | adoption_date
----------|--------------
Mushi     |2016-03-22
Seashell  |(null)
Azul      |2016-04-17
Victoire  |2016-09-01
Nala      |(null)

```SQL
SELECT name, age
FROM cats;
```
A:

name      | age
----------|---------
Mushi     |1
Seashell  |7
Azul      |3
Victoire  |7
Nala      |1

---
>5. Given this [cats table](https://www.db-fiddle.com/f/55ePhx9NLn7PzdGnebFaG7/0) , what records are returned from these queries?

- Display all the information about all of the available cats.
```SQL
SELECT *
FROM cats
```
- Display the name and sex of all cats who are 7 years old.
```SQL
SELECT name, gender
FROM cats
WHERE age = 7
```
- Find all of the names of the cats, so you don’t choose duplicate names for new cats.
```SQL
SELECT name
FROM cats
```
---
>6. List each comparison operator and explain when you would use it. Include a real world example for each.

- `=` equal: when we need to find something in a database where the value equals exactly to 5
- `>` greater than: when you need to find all values that are greater than a 1
- `<` less than: when you need to find all values less than 10
- `>=` greater than or equal to: when you need to find a number that is greater than 5 or equal to 5
- `<=` less than or equal to: when you need to find a number that is less than 10 or equal to 10
- `!=` not equal to: when you need to find all dogs that are not pugs
- `<>` greater than or less than, not equal to: when you need to find all numbers that is not 10, in other words, all numbers that are less than or greater than 10.
---

>7. From the cats table, what data is returned from these queries?

 ```SQL
 SELECT name
 FROM cats
 WHERE gender = ‘F’;
 ```

 A:

| name     |
|----------|
| Seashell |
| Nala     |

 ```SQL
 SELECT name
 FROM cats
 WHERE age <> 3;
 ```

 A:

| name     |
|----------|
| Mushi    |
| Seashell |
| Victoire |
| Nala     |

```SQL
SELECT ID
FROM cats
WHERE name != ‘Mushi’ AND gender = ‘M’;
```

A:

| id |
|----|
| 3  |
| 4  |
