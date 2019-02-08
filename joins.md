## Joins
>1. How do you find related data held in two separate data tables?

A: You would use the `JOIN`  method to combine data from two or more tables in a database based on attributes that are shared between the tables.

---
>2. Explain, in your own words, the difference between an INNER JOIN, LEFT OUTER JOIN, and RIGHT OUTER JOIN. Give a real-world example for each.

A:
- **INNER JOIN** returns only rows that share attributes defined in the query.
- **LEFT OUTER JOIN**: returns rows that match the shared attributes defined in the query and all rows from the left table. The left table is defined in your FROM statement. Columns that do not match the condition defined in the join will return as null.
- **RIGHT OUTER JOIN**: returns rows that match the shared attributes defined in the query (inner join) and ALL rows of the right table. The right table is defined at the word JOIN. Columns that do not match the condition defined in the join will return as null.

---
>3. Define primary key and foreign key. Give a real-world example for each.

A:
- **Primary key**: A unique identifier for each row in the immediate database table.
Ex. In my employees table, I have a primary key, the employee number which uniquely identifies each employee in the employee table
- **Foreign key**: The foreign key in a table refers to the primary key of another table.
Ex. I want to view data from my employees table and emails table, to do this I will take my primary key, employeeNumber from my employees table and link it to the foreign key, employeeNumber in my emails table.

---
>4. Define aliasing.

A:
- Table Alias: Aliasing is when you abbreviate your table names when calling it with column names, this occurs in the FROM statements.
- Column Alias: when you abbreviate your columns, this occurs in your SELECT statement.

---
>5. Change this query so that you are using aliasing:
```SQL
SELECT professor.name, compensation.salary,
compensation.vacation_days
FROM professor
JOIN compensation
ON professor.id = compensation.professor_id;
```

A:
```SQL
SELECT p.name, c.salary, c.vacation_days
FROM professor AS p
JOIN compensation AS c
ON p.id = c.professor_id;
```

---
>6. Why would you use a NATURAL JOIN? Give a real-world example.

A:  
- It automatically joins all columns that tables have in common with each other. The default is inner join for Natural joins, but they can be right outer joins and left outer joins as well. Ex. I want to view all employees on the employees table with emails  that has the same employeeID as the emails table.

---
>7. Using this Employee schema and data, write queries to find the following information:

- List all employees and all shifts.
```SQL
SELECT e.name, s.date, s.start_time, s.end_time
FROM employees AS e
JOIN shifts AS s
ON e.id = s.id
```
---
>8. Using this Adoption schema and data, please write queries to retrieve the following information and include the results:

- Create a list of all volunteers. If the volunteer is fostering a dog, include each dog
```SQL
SELECT v.first_name AS volunteer_firstname, v.last_name AS volunteer_lastname, d.id AS dog_id, d.name AS dog_name, d.breed
FROM volunteers AS v
LEFT OUTER JOIN dogs AS d
ON d.id  = v.foster_dog_id
```

- The cat's name, adopter's name, and adopted date for each cat adopted within the past month to be displayed as part of the "Happy Tail" social media promotion which posts recent successful adoptions.
```SQL
SELECT c.name AS cat_name, a.first_name, a.last_name, ca.date AS adopted_date
FROM cats AS c
JOIN cat_adoptions AS ca ON c.id = ca.cat_id
JOIN adopters AS a ON a.id = ca.adopter_id
WHERE ca.date >= (CURRENT_DATE - INTERVAL '30 DAYS');
```
- Create a list of adopters who have not yet chosen a dog to adopt.
```SQL
SELECT a.first_name, a.last_name
FROM adopters AS a
LEFT OUTER JOIN dog_adoptions as da
ON a.id = da.adopter_id
WHERE da.adopter_id IS NULL;
```
- Lists of all cats and all dogs who have not been adopted.
```SQL
SELECT dogs.name
FROM dogs
LEFT OUTER JOIN dog_adoptions ON dogs.id = dog_adoptions.dog_id
WHERE dog_adoptions.dog_id IS NULL;
SELECT DISTINCT cats.name AS cat_name
FROM cats
LEFT OUTER JOIN cat_adoptions ON cat_adoptions.cat_id = cats.id
WHERE cat_adoptions.cat_id IS NULL;
```

- The name of the person who adopted Rosco.
```SQL
SELECT adopters.first_name, adopters.last_name
FROM adopters
JOIN dog_adoptions ON dog_adoptions.adopter_id = adopters.id
```
---
>9. Using this Library schema and data, write queries applying the following scenarios and include the results:

- To determine if the library should buy more copies of a given book, please provide the names and position, in order, of all of the patrons with a hold (request for a book with all copies checked out) on "Advanced Potion-Making".
```SQL
SELECT patrons.name, holds.rank
FROM patrons
JOIN holds ON patrons.id = holds.patron_id
WHERE isbn = '9136884926';
```

- List all of the library patrons. If they have one or more books checked out, list the books with the patrons.
```SQL
SELECT DISTINCT patrons.name,
(SELECT checkedout.title AS "books checked out"
 FROM
   (SELECT transactions.patron_id, transactions.checked_in_date, books.title
    FROM transactions LEFT OUTER JOIN books ON books.isbn = transactions.isbn
    WHERE transactions.checked_in_date IS NULL) AS checkedout
WHERE checkedout.patron_id = patrons.id)
 FROM patrons
 LEFT OUTER JOIN transactions ON transactions.patron_id = patrons.id
 LEFT OUTER JOIN books on books.isbn = transactions.isbn;
```
