### Databases: Introduction Assignment

>1. What data types do each of these values represent?

"A Clockwork Orange"
- A: String

42
- A: integer

09/02/1945
-  A: DATE

98.7
-  A: float

$15.99
-  A: float

---     

>2. Explain when a database would be used. Explain when a text file would be used.

- A: A database would be used when we need to store, add, modify, search and manage data. In addition, we would need the database to be accessible by multiple applications.  You would use a text file when updating/ modifying the data is only required on rare occasions and the data is simple, straight forward, and human readable.

---
>3. Describe one difference between SQL and other programming languages.

 - A: SQL is declarative,  which means the query you write reads like a sentence describing the goal or result you want to achieve. With the query you wrote, the database engine would then figure out the most efficient way to return that data.  Most other languages are imperative procedural/ object oriented, etc. In these languages you would need to figure out an algorithm on how to tell the program step by step on how the database should find your data. The data in the DB is stored in specialized structures that allow the DB to quickly read and change data. When you make requests for data, Databases display data similar to a table structure.
---
>4. Explain how the pieces of a database system fit together at a high level.

- A:
  On a high level, the database application will allow users to manage data through an interface. The interface might be accessed via the command line or a GUI. You can also set up a database as an app on a server so other machines can send requests through the server to et data.
---
>5. Explain the meaning of table, row, column, and value.

- A: **Table**: this is made up of columns and rows that contain the database's data. **Row**: represents a complete conceptual unit. **Column**: the label that define what the data represents

---
>6. List three data types that can be used in a table.

- A:
  - objects
  - integers
  - strings
---
>7. Given this payments table, provide an English description of the following queries and include their results:

```SQL
 SELECT date, amount
     FROM payments;
```

- A: Select and return the date and amount columns from the payments table.

| date        | amount |
| ------------|:------:|
| 2016-05-01 | 1500.00 |
| 2016-05-10 | 37.00   |
| 2016-05-15 | 124.93  |
| 2016-05-23 | 54.72   |

```SQL
SELECT amount
     FROM payments
     WHERE amount > 500;
```
- A: Select and return the amount columns that are greater than 500 from the payments table.

| amount |
|:------:|
|1500.00|

```SQL
SELECT *
     FROM payments
     WHERE payee = 'Mega Foods';
```
- A: Return all columns (date, payee, amount, and memo) from the payments table where the payee column equals Mega Foods

| date        | payee | amount | memo |
|:-----------:|:------:|:------:|:------:|
| 2016-05-15 | Mega Foods | 124.93  | Groceries |

---
>8. Given this users table, write SQL queries using the following criteria and include the output:

A:  
- The email and sign-up date for the user named DeAndre Data.
    ```SQL
    SELECT email, signup
         FROM users
         WHERE name = 'DeAndre Data';
    ```

| email        | signup |
|:-----------:|:------:|
| datad@comcast.net | 2008-01-20 |

   - The user ID for the user with email 'aleesia.algorithm@uw.edu'.
    ```SQL
    SELECT userid
         FROM users
         WHERE email = 'aleesia.algorithm@uw.edu';
    ```

| userid      |
|:-----------:|
| 1 |

- All the columns for the user ID equal to 4.
    ```SQL
    SELECT *
         FROM users
         WHERE userid = 4;
    ```

| userid | name          | email    | signup |
|:------:|:-------------:|:--------:|:------:|
| 4      | Brandy Boolean | bboolean@nasa.gov |1999-10-15 |
