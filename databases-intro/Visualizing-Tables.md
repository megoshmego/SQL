Title: Visualizing Tables
Course: SQL
Section: Databases Intro

This video is an introduction to relational databases and how they're structured. The instructor provides an example of a database for movies and users, showing how data is stored in tables with columns and rows. The example includes three tables: movies, users, and ratings. The instructor explains the concept of a relational database by demonstrating how the ratings table references both the movies and users tables.

Key terms and concepts:

Relational database: A database that uses a structure of tables with relationships between them, storing data in rows and columns.
Table: A structure in a relational database that stores data in rows and columns.
Column: A vertical structure in a table that holds a specific type of data.
Row: A horizontal structure in a table that holds a specific instance of data.
ID: A unique identifier for a specific row in a table.
Schema design: The process of designing the structure of a database, including tables and their relationships.
References: A way to link data in one table to another table using the unique identifier (ID) from the related table.
SQL (Structured Query Language): A programming language used to manage relational databases and perform operations on the data stored in them.
Demo suggestions:

Show the process of creating tables for movies, users, and ratings in a real SQL environment.
Demonstrate how to insert data into these tables.
Provide examples of SQL queries that cross-reference data from multiple tables, such as finding all ratings for a specific movie or user.
Show how to calculate average ratings for a movie using SQL.
Explain how to update and delete data in the tables.


Here are some demo scripts that you might find helpful for each of the suggested demos:

Demo 1: Creating tables for movies, users, and ratings in a SQL environment

sql
Copy code
CREATE TABLE movies (
    id INTEGER PRIMARY KEY,
    title TEXT,
    release_year INTEGER,
    runtime INTEGER,
    rating FLOAT
);

CREATE TABLE users (
    id INTEGER PRIMARY KEY,
    username TEXT,
    email TEXT
);

CREATE TABLE ratings (
    id INTEGER PRIMARY KEY,
    user_id INTEGER,
    movie_id INTEGER,
    score INTEGER,
    FOREIGN KEY (user_id) REFERENCES users (id),
    FOREIGN KEY (movie_id) REFERENCES movies (id)
);
Demo 2: Inserting data into the movies, users, and ratings tables

sql
Copy code
INSERT INTO movies (title, release_year, runtime, rating)
VALUES ('Amadeus', 1984, 160, 8.3),
       ('Parasite', 2019, 132, 8.6),
       ('Amelie', 2001, 122, 8.3),
       ('The Thing', 1982, 109, 8.1);

INSERT INTO users (username, email)
VALUES ('chicken_gal', 'tamy@gmail.com'),
       ('goose_guy', 'todd@gmail.com');

INSERT INTO ratings (user_id, movie_id, score)
VALUES (1, 1, 8),
       (1, 2, 10),
       (1, 3, 7),
       (1, 4, 5),
       (2, 1, 10),
       (2, 2, 6),
       (2, 3, 7),
       (2, 4, 9);
Demo 3: Example SQL queries to cross-reference data from multiple tables

sql
Copy code
-- Find all ratings for the movie "Amelie"
SELECT users.username, movies.title, ratings.score
FROM ratings
JOIN users ON ratings.user_id = users.id
JOIN movies ON ratings.movie_id = movies.id
WHERE movies.title = 'Amelie';

-- Find all ratings made by user "chicken_gal"
SELECT users.username, movies.title, ratings.score
FROM ratings
JOIN users ON ratings.user_id = users.id
JOIN movies ON ratings.movie_id = movies.id
WHERE users.username = 'chicken_gal';
Demo 4: Calculate average ratings for a movie using SQL

sql
Copy code
-- Calculate average rating for the movie "Amelie"
SELECT movies.title, AVG(ratings.score) as average_rating
FROM ratings
JOIN movies ON ratings.movie_id = movies.id
WHERE movies.title = 'Amelie'
GROUP BY movies.title;
Demo 5: Update and delete data in the tables

sql
Copy code
-- Update the rating for movie "Amadeus" in the movies table
UPDATE movies
SET rating = 8.5
WHERE title = 'Amadeus';

-- Delete a rating by user "chicken_gal" for movie "The Thing"
DELETE FROM ratings
WHERE user_id = (SELECT id FROM users WHERE username = 'chicken_gal')
AND movie_id = (SELECT id FROM movies WHERE title = 'The Thing');
