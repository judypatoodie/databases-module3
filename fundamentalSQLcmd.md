## Fundamental SQL Commands

>1. List the commands for adding, updating, and deleting data.

A:
- Adding: `INSERT INTO`, `ALTER TABLE`, `ADD COLUMN`
- Updating: `UPDATE`, `SET`, `ALTER TABLE`
- Deleting: `DELETE`, `DROP COLUMN`, `DROP TABLE`, `ALTER TABLE`
---
>2.Explain the structure for each type of command.

A:
- `INSERT INTO`: Inserts data into a table.
- `UPDATE`: Modifies existing records within a table.
- `SET`: Used with `UPDATE` to specify what data in the table to update.
- `ALTER TABLE`: Used to add, delete or modify columns in existing table
- `DELETE`: Deletes an entry from a table.
- `DROP TABLE`: Drops/deletes existing table from a database

---
>3. What are some of the data types that can be used in tables? Give a real-world example of each type.

A:
- **String**: You would use this when you need to input names of cities into a database.
- **Date**: You would use this when you need to the date to define when the employee started in the company in the HR database.
- **Time**: You would use this when you need to define what time the package arrived and put it in a database.

---
>4. Decide how to create a new table to hold a list of people invited to a wedding dinner. The table needs to have first and last names, whether they sent in their RSVP, the number of guests they are bringing, and the number of meals (1 for adults and 1/2 for children).

A:
- Which data type would you use to store each of the following pieces of information?
  - First and last name. `text`
  - Whether they sent in their RSVP. `boolean`
  - Number of guests. `integer`
  - Number of meals. `integer`
- Write a command that creates the table to track the wedding dinner
```SQL
CREATE TABLE wedding (
  firstname text,
  lastname text,
  RSVP boolean,
  guestCount integer,
  mealCount integer
)
```
- Write a command that adds a column to track whether the guest sent a thank you card.
```SQL
ALTER TABLE wedding
  ADD COLUMN thankyouCard boolean;
```
- You have decided to move the data about the meals to another table, so write a command to remove the column storing the number meals from the wedding table.
```SQL
ALTER TABLE wedding
DROP COLUMN mealCount
```
- The guests will need a place to sit at the reception, so write a command that adds a column for table number.
```SQL
ALTER TABLE wedding
  ADD COLUMN tableNum integer;
```
- The wedding is over and we do not need to keep this information, so write a command that deletes the table numbers from the database.
```SQL
ALTER TABLE wedding
  DROP COLUMN tableNUM;
```
---
>5. Write a command to create a new table to hold the books in a library with the columns ISBN, title, author, genre, publishing date, number of copies, and available copies.

```SQL
CREATE TABLE libraryBooks(
  ISBN varchar(13),
  title text,
  author text,
  genre text,
  pubDate date,
  copies integer,
  availableCopies integer
);
```
- Find three books and add their information to the table.
```SQL
INSERT INTO libraryBooks (ISBN, title, author, genre, pubDate, copies, availableCopies)
VALUES
(123-8975641236 ,'Adventures of Matilda', 'Roald Dahl', 'fiction', '1990-09-21', 30, 20),
(124-8975641237 ,'Goosebumps', 'RL Stine', 'fiction', '2015-09-21', 20, 15),
(125-8975641238 ,'Less', 'Andrew Sean Greer', 'self help', '2017-09-18', 50, 25),
```
- Someone has just checked out one of the books. Change the number of available copies to 1 fewer.
```SQL
UPDATE libraryBooks
  SET availableCopies = 19
  WHERE ISBN = 123-8975641236;
```
- Now one of the books has been added to the banned books list. Remove it from the table.
```SQL
DELETE FROM libraryBooks
  WHERE ISBN = 123-8975641236;
```


---
>6. Write a command to make a new table to hold spacecrafts. Information should include id, name, year launched, country of origin, a brief description of the mission, orbiting body, if it is currently operating, and its approximate miles from Earth. In addition to the table creation, provide commands that perform the following operations:

```SQL
CREATE TABLE spacecrafts (
  id integer,
  name text,
  launchYear integer,
  originCountry text,
  description varchar(250),
  orbitingAt text,
  inOperation boolean,
  miles integer
  )
```
- Add three non-Earth-orbiting satellites to the table.
```SQL
INSERT INTO spacecrafts(id, name, launchYear, originCountry, description, oribitingAt, inOperation, miles)
VALUES
(9875, 'Star Wars', 2012, 'United States', 'This expedition is to fight the aliens of planet Mars', 'Mars', true, 452340),
(7895, 'Space Miners', 2000, 'Africa', 'Mission to find gold in other planets', 'Jupiter', true, 987564),
(8546, 'Infinity and Beyond', 2018, 'Germany', 'Mission to search for new planets in solar system', 'Venus', true, 88745612);
```
- Remove one of the satellites from the table since it has just crashed into the planet.
```SQL
DELETE FROM spacecrafts
WHERE id = 9875
```
- Edit another satellite because it is no longer operating and change the value to reflect that.
```SQL
UPDATE spacecrafts
SET inOperation = false
WHERE name = 'Space Miners'
```
---
>7. Write a command to create a new table to hold the emails in your inbox. This table should include an id, the subject line, the sender, any additional recipients, the body of the email, the timestamp, whether or not you have read the email, and the id of the email chain it's in. Also provide commands that perform the following operations:

```SQL
CREATE TABLE emails(
  id integer,
  subject text,
  sender text,
  otherRecipients text,
  body text,
  currentTime time,
  read boolean,
  chainID integer
)
```

- Add three new emails to the inbox.
```SQL
INSERT INTO emails (id, subject, sender, otherRecipients, body, currentTime, read, chainID)
VALUES
(6545, "HR Report Needed", "John Lee", "Please send me the HR report for this month.", now(), true, 15)
(6544, "IT Inquiry", "Ruby Spice", "My computer won't turn on please help!", now(), true, 10)
(6540, "Meeting Invite", "Jacob Wills", "Please join me in the large conference room to discuss yearly initiatives", now(), true, 20)
```
- You deleted one of the emails, so write a command to remove the row from the inbox table.
```SQL
DELETE FROM emails
WHERE id = 6544
```
- You started reading an email but just heard a crash in another room. Mark the email as unread before investigating the crash, so you can come back and read it later.
```SQL
UPDATE emails
SET read = false
WHERE id = 6540
```
