thank you. would you include any scripts for demos you think might be helpful? 







will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "Deleting", and the section of the course "SQL", and subsection "SQL-Querying", as well as any demos you think would helpful to me?:


0:00
(upbeat music)
0:05
- [Instructor] To delete rows from a table using SQL,
0:08
we use DELETE, and then FROM, and then optionally
0:12
we could use WHERE if we just did DELETE FROM books,
0:15
that will delete every row in the books table,
0:18
So I'm not gonna start with that one,
0:20
I'll do it at the end,
0:21
but we can also add in WHERE sub clause
0:24
and specify a particular set of rows that we want to delete.
0:29
So let's delete all the long books.
0:32
I could do that with DELETE FROM
0:35
books WHERE page counts is greater than 500.
0:42
And I guess if I delete this right now
0:44
we won't know how many there are with that page count.
0:47
So why don't I first do a SELECT page count
0:52
maybe title or ID page count
0:56
FROM books WHERE page count is greater than 500.
1:02
I misspelled page count.
1:04
We'll try that again.
1:05
Okay. So we've got quite a few where a page count is greater
1:08
than 500.
1:09
Let's now delete based off of that.
1:13
So DELETE FROM books WHERE page count is greater than 500.
1:22
It deleted 10 rows,
1:23
which is exactly the number that we selected earlier.
1:27
And now if I try and select again,
1:28
based after page count
1:29
greater than 500 nothing.
1:32
I could also delete based
1:34
off of some other WHERE clause so DELETE FROM books.
1:38
How about all authors that start with the letter S or T?
1:44
So the select statement would be
1:46
SELECT FROM how about author
1:50
and title FROM books WHERE author, and then I'll do I I LIKE
2:00
and we said S I think so starts with an S
2:04
or, author I LIKE, and then starts with the T
2:10
like that.
2:11
I need to make sure
2:12
I guess it doesn't matter if this is capitalized
2:14
but I like to capitalize those SQL keywords.
2:17
And now we've got four authors here
2:18
that either start with a T or an S.
2:21
So I could delete them,
2:22
I could just keep this query the same
2:24
but move to the beginning
2:26
or most of the beginning and delete this SELECT,
2:29
and instead change it to DELETE FROM
2:33
books WHERE author, case insensitive
2:36
ILIKE 'S' at the beginning or author case insensitive
2:38
ILIKE 'T' at the beginning, we deleted four
2:42
and if I try and select them again, they're gone.
2:45
So that's kind of it for deleting.
2:48
It took a while
2:49
for us to learn the select syntax, because we talked
2:52
about the different operators, the comparisons,
2:54
like greater than, like, between, Enna, all of that stuff.
2:58
And then we can use those same operators
3:01
in sub queries alongside DELETE and UPDATE as well.
3:06
So the last thing I'll do is delete every book
3:08
DELETE FROM books, with no WHERE clause
3:11
DELETE FROM books , good-bye books, and it deleted 32.
3:17
Now, if we do SELECT * FROM books , it's empty,
3:22
no more books we sold out,
3:25
or we're closing down because we're a small bookshop
3:27
and we can't compete with Amazon.
3:28
Well, let's be optimistic here.
3:30
Our community supports says
3:31
"and we sold out of every single book."
3:33
And that's it for basic credit operations in SQL.
3:38
So we saw C for credit, which is creating.
3:42
In SQL we use INSERT INTO.
3:44
We saw R incurred
3:46
which means reading, which in SQL is SELECT
3:50
plus a whole bunch of other things usually.
3:52
And then we saw updating, which is UPDATE alongside SET.
3:56
Those are the keywords, and then delete, we use DELETE and
3:59
FROM, and that's it for the basic credit operations in SQL,
4:03
there is obviously a lot more to SQL
4:06
and you can write some pretty complex queries
4:08
and we have a lot more to cover still, next step
4:11
we'll talk about how we actually create tables and set
4:14
up a schema instead of just using a seed file.
4:17
Like I gave you for this section.
4:19
(upbeat music)