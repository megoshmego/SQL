thank you. would you include any scripts for demos you think might be helpful? 







will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "Inner Joins", and the section of the course "SQL", and subsection "SQL-Relationships", as well as any demos you think would helpful to me?:

Transcript


0:00
(gentle music)
0:04
- [Instructor] Next step, we get to move on to a fun topic,
0:07
fun being mildly sarcastic, Join Tables.
0:11
JOIN tables are an essential part of SQL.
0:15
The term relational database
0:17
indicates that we have lots of these relationships,
0:19
one-to-many, which we've seen already
0:21
as well as many-to-many.
0:22
We also can have one-to-one relationships
0:25
but whatever the relationships are,
0:27
it's very, very common to have tables
0:29
that are connected to have lots of relationships
0:32
and without join tables, without being able to make queries
0:35
where we can join information together,
0:38
it's a multi-step process
0:40
to access data across those tables.
0:43
For example, if I had this string
0:45
Walt Disney Studios Motion Pictures
0:47
let's say it's coming from a form
0:49
or a user clicks a link on our website
0:51
and we want to show all associated movies
0:54
that Disney Studios has put out,
0:56
so with what we know right now,
0:57
this would be a multiple step process
0:59
to figure out which movies Disney Studios had put out.
1:02
We would start with a SELECT star
1:06
or we could just get the id FROM studios WHERE,
1:13
and then, I can't even remember it
1:14
it's called studio name equals
1:18
Walt Disney Studios Motion Pictures.
1:19
Then we get id of one so we could use that
1:22
SELECT star FROM movies WHERE
1:28
studio_id equals one.
1:32
And now I've selected the movies that have been put out
1:35
by the studio with id of one,
1:37
which is Walt Disney Studios Motion Pictures.
1:40
I have taken this studio name, found the correct id
1:43
and then use that id to locate
1:45
the corresponding movies in our movie table.
1:48
But there's a better way
1:50
if I wanted to combine information from related tables,
1:54
I can write a JOIN query.
1:56
So JOIN operations allow us to create a new table in memory
2:00
so it's not a real table that persists
2:02
but a table in memory that will combine information
2:05
or join it from different tables.
2:08
So data from those tables in our case movies and studios
2:12
will be matched according to some join condition.
2:15
Most commonly we'll join using a foreign key
2:18
and a primary key from another table
2:20
for example, the studio id,
2:22
which is a foreign key in the movies table.
2:26
So here is our very first example.
2:29
We could do something like this, SELECT title and name.
2:33
Remember, name is a field from studio.
2:36
Title is from movie or movies,
2:38
name is a studio name.
2:40
FROM movies, and if I just did this I'd have an error
2:44
because there is no name in movies,
2:47
but I'm going to join the two tables together.
2:50
So just to show this, if I tried this
2:53
column name does not exist.
2:55
I put a weird emphasis on that column
2:58
name does not exist, we get an error
3:01
it doesn't exist in the movies table
3:03
but if we JOIN studios,
3:06
now we're going to have all of those columns together
3:09
the columns from movies, the columns from studios
3:12
but specifically,
3:13
we're going to join on this condition right here
3:17
where in the movies table, the studio id
3:20
is the same ad the is in the studios table.
3:25
So this is the most important part here
3:26
the JOIN ON condition.
3:29
We want to join the two tables where it makes sense
3:32
where the studio id on the movies field or movies table
3:36
is referencing the id on the studios table.
3:41
So remember this, right, we have studio id on movies
3:45
and then we have just regular id on our studios.
3:49
We want to join them where they are the same
3:52
so let's try it out.
3:53
We'll SELECT title and name
3:57
title is from movies, name is from studios
4:01
FROM movies and then we're going to JOIN
4:06
oh my goodness
4:07
studios ON
4:12
and then specifically
4:13
we want movies.studio id equal to studios.id.
4:21
And there we go, we now have a new table,
4:23
which is just in memory, it's just been outputted for us
4:26
but this is not a table that has been saved to our database.
4:30
We've created it in working memory
4:32
that has title from movies and name from studios.
4:36
It combines two different tables together,
4:39
not just in an arbitrary way,
4:41
but specifically where there's overlap.
4:44
Where one of those movies had a studio id reference,
4:47
we took that studio id and then got the name of that studio
4:51
from the studios table.
4:53
So Star Wars, instead of just having studio id one
4:57
or Avatar studio id of two or whatever it is,
5:00
we now have the studio name,
5:02
Walt Disney Studios Motion Pictures,
5:05
20th Century Fox, Orion Pictures.
5:08
And if I went back to the beginning here
5:10
and selected star, let's see what happens then.
5:15
I have to zoom out a bit to make sense of it
5:18
but now we have every single column
5:20
from both of those tables combined.
5:23
So we have our movies table first,
5:25
movie id, title, release year, runtime, rating
5:28
and then we've joined the studio information
5:32
on the right hand side
5:33
studio id and then actually that's from movies,
5:36
sorry about that.
5:37
Here, we have the id from studios
5:40
and then name and founded in.
5:43
So when I'm joining tables, I can pick and choose
5:45
from these different pieces.
5:48
So if I wanted to show founded in alongside the movie title,
5:53
I could do that by revising my query,
5:57
go back to the beginning
5:58
instead of SELECT star I'll SELECT title
6:02
and then founded in, and there we go!
6:06
Title and then the year
6:08
that particular studio was founded in.
6:12
Now where it gets a little bit trickier
6:14
is they both have ids, right?
6:16
If I wanted to print the movie id and the studio id at once,
6:21
I could use star, like we just saw,
6:23
but if I want to be specific,
6:24
I only wanted those two things,
6:27
I can't just say SELECT id comma id.
6:32
It's ambiguous, both of those studios have ids
6:34
or both of those tables have ids.
6:36
So we can use the same syntax we've seen already
6:39
SELECT movies.id,studio.id
6:44
and there we go!
6:45
Now we have both of their ids together
6:47
and I could also give them an alias with as
6:50
so select movies that id as movie id, studio.id
6:54
as studio id but I just wanted to show you here
6:58
that if you do have duplicate column names,
7:00
you can reference them specifically
7:03
using the name of the table first.
7:05
Now what we just saw using this JOIN keyword
7:08
is technically a INNER JOIN.
7:11
In SQL, JOIN and INNER JOIN are going to be the same thing.
7:15
The INNER keyword is optional.
7:17
So there are different types of joins
7:18
and we'll see some more as we make more progress here,
7:21
but the most common one that you'll do most of the time
7:25
is an INNER JOIN and it's the default
7:27
if you just write JOIN
7:29
but I can just show this here.
7:31
Let's go back to title, how about title and name
7:35
from movies JOIN studios, but instead of JOIN studios,
7:39
I'll do INNER JOIN studios
7:42
we get the same results.
7:44
Another thing about these joins that we've been doing
7:47
is the order.
7:49
So we are selecting from movies
7:51
and then joining studios on
7:54
that means that on the left-hand side, like we saw here,
7:58
we have the movie information first
8:00
and then the studio information.
8:01
This doesn't really make a difference in INNER JOIN
8:04
like we have now.
8:06
So if I reversed it though,
8:08
we'll do SELECT, should we do, I'll do star,
8:10
I'll just zoom out again.
8:12
FROM studios JOIN movies ON
8:19
and then we can do studios.id equals movies.studio_id
8:28
and I'll zoom out
8:32
I'm almost there, there we go!
8:35
We end up with these studio information first
8:37
and then we've joined on the movie data as well in each row.
8:42
Okay, so those are some examples of our first joins
8:46
they are INNER JOINS but there are other types.
8:49
Next up, we'll see an OUTER JOIN
8:51
of which there's actually multiple as well,
8:53
left, right and full, that's coming up next.
8:56
(gentle music)