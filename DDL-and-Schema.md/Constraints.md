thank you. would you include any scripts for demos you think might be helpful? 





will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "Constraints", and the section of the course "SQL", and subsection "DDL and Schema", as well as any demos you think would helpful to me?:




Skip navigation
Search




Avatar image


0:05 / 6:08

Transcript


0:00
(upbeat music)
0:04
- [Instructor] All right, so next we'll begin
0:06
our deep dive into the syntax of SQL.
0:09
We'll start by making queries.
0:11
So when we say queries
0:12
that refers to things like
0:14
searching for information, selecting pieces of our database,
0:19
selecting all the top rated movies from 2019
0:22
or selecting the most prolific user
0:25
who has left the most reviews.
0:27
And also things like inserting and updating and deleting
0:31
particular rows into a table.
0:33
So inserting a new movie,
0:35
updating a rating for a movie,
0:37
deleting all movies,
0:38
deleting all movies from this year,
0:40
deleting all movies with an average score
0:43
of less than five out of 10.
0:45
So what we're gonna focus on first,
0:47
is technically a subset of SQL.
0:49
It's called SQL DML,
0:52
which is Data Manipulation Language.
0:54
There's also SQL DDL,
0:57
which is Data Definition Language.
0:59
And we will learn that as well.
1:01
That sounds quite intimidating,
1:02
but think of it this way,
1:03
there's two different steps to working with a database.
1:06
To get your data in a Postgres database.
1:09
We first need to define the pattern of our data,
1:11
the schema, we need to create the empty tables
1:15
that say each movie has an ID, a title, release year,
1:20
a director, and a rating.
1:22
Rating like a RPG 13, PG, that sort of thing, MPA rating.
1:27
So that is defining the structure of our data
1:31
and that's something we do through SQL.
1:33
And then after that, we can do DML stuff Data Manipulation,
1:38
where we can insert into that table
1:41
we can delete from it,
1:42
we can search within it,
1:43
we can retrieve rows that meet specific criteria.
1:46
And this is actually where we're going to start.
1:48
And the reason for that
1:49
is that it's easier.
1:51
And most of what you'll be doing
1:52
most of the time at least in a flask app
1:54
is creating new rows, deleting, rows, searching for things,
1:59
updating things
2:00
whereas the other subset, of SQL,
2:03
the Data Definition Language stuff,
2:05
creating tables and defining your schema
2:08
is something you usually do once per application.
2:11
So we will get to that, after this.
2:13
So just a couple of videos most likely,
2:15
but we're starting here.
2:17
And in order for this to work,
2:18
what I'm going to do is give you a file.
2:21
It's already attached to this lecture,
2:24
you can find it on the handout.
2:26
It's a downloadable file called library.SQL.
2:30
And if we take a look at it,
2:33
just through the command line.
2:34
It includes a lot of starter information for us.
2:37
It creates a database, it creates a table
2:39
and it adds some basic books
2:41
is what we're working with here.
2:43
And then it creates a table called employees
2:45
but it adds in a bunch of books for us.
2:47
So it's a starter file and we'll begin by running this file
2:51
that we can then work with.
2:53
So we'll create a database, we'll add a table,
2:56
we'll add some rows
2:57
and we won't have to actually write that code ourselves.
2:59
I'm giving it to you.
3:01
So then we can focus on the DML stuff, Data Manipulation.
3:05
We'll have some content to work with.
3:07
We're gonna focus on the basic CRUD operations in SQL.
3:11
CRUD is a pretty common acronym,
3:13
in web development and programming in general.
3:16
It stands for Create, Read, Update, and Delete.
3:19
Four standard operations for any entity in a database.
3:23
We want to be able to create a new movie.
3:25
How do we insert a movie into our database?
3:28
Read?
3:29
You could also think of as,
3:30
searching or finding, retrieving.
3:33
So how do we find something from the database?
3:35
Find the most recent movie,
3:37
find all movies released in 2019.
3:40
Find the lowest rated movie,
3:43
find movies that have a rating of PG 13,
3:47
updating the U, would be updating a rating for a movie,
3:52
updating the title.
3:53
If something was messed up.
3:54
Deleting would be to delete any movie from our table,
3:58
delete the most recent movie, delete all movies
4:01
below some threshold of review scores
4:04
or delete all movies directed
4:05
by Roman Polanski, for example.
4:08
So we have these different operations
4:10
Create, Read, Update, and delete very standard term.
4:13
You'll hear a lot is CRUD.
4:15
And then here is the equivalent operation,
4:17
the actual SQL command.
4:20
So to create a new movie,
4:21
the command and SQL is not create,
4:24
it's insert into, to read a movie or multiple movies.
4:29
In SQL we use select.
4:31
We use update and delete,
4:32
which both happened to match CRUD
4:35
but select and insert are slightly different.
4:38
So we're gonna go step-by-step
4:39
through each of these operations,
4:41
and within each operation, we'll see some variants.
4:44
And especially with selecting.
4:46
There are tons of ways of selecting data,
4:48
retrieving information.
4:50
It's pretty rare that you would just want to select
4:52
every movie in your database,
4:54
if we have thousands, or if we think of IMDP
4:56
I think there's at least hundreds of thousands of movies
4:59
if not, over a million who knows
5:01
actually that's probably a stretch.
5:03
if there's been a million movies made, who knows?
5:05
There's a lot of them though
5:06
and we're not viewing all of them at once on IMDV.
5:10
Usually they are retrieved based
5:12
after their rating, country, the director
5:16
if you're on an actors page, you'll see the movies
5:18
that that actor has been in.
5:20
So there's a SQL query
5:21
That's been run to select all the movies
5:23
that Leonardo DiCaprio has been in.
5:26
And then we see them showing up in the browser and HTML.
5:30
So we'll make our way through all of these commands
5:32
and we're gonna start with selecting information.
5:35
But the first thing we need to do
5:36
is get our library database up and running.
5:39
So we'll start with the R actually,
5:42
the reading of data
5:43
and we'll spend a good amount of time working with it.
5:45
But first in the next video
5:47
we'll get our database up and running.
5:49
Since we'll be using the same starter database
5:51
I've given you see data,
5:53
we'll have something to select from
5:55
without having to understand how to create a table.
5:57
Which we will do, but just not yet, Okay?
6:00
So that's next,
6:01
and then we'll focus on select.
6:02
(upbeat music).
