thank you. would you include any scripts for demos you think might be helpful? 







will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "Group By Having", and the section of the course "SQL", and subsection "SQL-Querying", as well as any demos you think would helpful to me?:

0:00
(cool upbeat music)
0:04
- Next step we've got one of the more useful
0:06
but also slightly confusing sub clauses
0:09
called Group By.
0:11
Group By will group our results, our rows
0:14
into different groups
0:16
based off of whatever we tell it to group by.
0:18
Currently in our database,
0:20
we have what, 40 different books.
0:23
And a lot of them have unique authors
0:25
but there are some authors who have created
0:27
or written multiple books.
0:29
We do select title and author from books.
0:35
This doesn't make it very clear here.
0:37
Maybe I'll revise this just to be author.
0:41
Some of those titles are quite long.
0:43
Here we go.
0:44
We've got quite a few Kyle Simpson's,
0:46
quite a few books by J.K. Rowling,
0:48
Rowling, I don't know what to say there.
0:50
And I think that's it.
0:51
Otherwise, most of the...
0:53
I think everyone else has just written one book.
0:56
Okay.
0:57
So what we can do is group our results by author
1:00
as an example, and that will automatically combine
1:04
the resulting rows for us, based off of that author.
1:08
The thing that makes it kind of confusing.
1:10
If I did SELECT * FROM books GROUP BY author:
1:20
we get this weird error saying,
1:21
column "books_id" must appear in the Group By clause
1:25
or be used in an aggregate function.
1:28
So this is why I introduced aggregate functions earlier.
1:31
We can use them in conjunction with a Group By.
1:35
When we group things,
1:36
let's say we're grouping by author,
1:38
it doesn't really make sense just to print them out,
1:40
grouped by author.
1:42
Group By is not going to place the rows together
1:45
like one row and then the next row,
1:47
and then the next row,
1:48
it combines them into a single row.
1:51
So, it wouldn't be very useful to have a single row
1:54
that contained every J.K. Rowling title
1:57
and every price and page count.
1:59
Usually we're going to group by
2:02
in order to figure something else out.
2:04
Like how many books somebody has written.
2:07
And this is where we can use aggregate functions.
2:10
So we could do something like
2:12
SELECT COUNT (*) FROM books GROUP BY author.
2:19
And what will happen here,
2:21
is that we will start with the, from books part.
2:24
So we're going to select FROM books,
2:27
not every single row on a don't instead.
2:30
I want you to group them by author.
2:32
So some of those rows
2:34
like J.K. Rowling's row
2:36
is going to contain a bunch of information
2:38
and we're going to count how many times
2:40
each author occurs.
2:42
And this is what we see.
2:44
One, one, seven, one, one, one, one, one, one, six,
2:46
not all that useful,
2:48
but we could also add in some other information
2:50
like SELECT author,
2:54
COUNT.
2:55
And now we have the author name
2:58
next to a count of how many times they occur
3:01
when we group by author.
3:03
So how many rows were there
3:05
when we grouped by J.K. Rowling?
3:07
We had seven.
3:09
How many for, who else did we have?
3:11
Kyle Simpson somewhere in here?
3:12
Yep. There we go, six.
3:15
We could also do things like GROUP BY author,
3:19
SELECT author
3:20
and instead of just count,
3:22
we can do average of page count.
3:27
Now we're grouping by author
3:29
and we're calculating the count.
3:31
How many times they occur.
3:33
So one time, one time, seven times
3:35
and the average length of their books.
3:38
So three, eight, four,
3:39
two, six, four
3:41
J K Rowling, almost 600 pages.
3:44
And then Kyle Simpson
3:46
almost 200 pages, 188.66666
3:49
and so on.
3:52
And we also have multiple duplicate publishers.
3:55
When I run SELECT publisher from books,
3:59
we have quite a few O'Reilly Media
4:02
quite a few Scholastic books.
4:04
I could use that
4:06
to form a new Group By.
4:07
SELECT publisher name, which is just publisher
4:10
and count
4:14
FROM books
4:16
GROUP BY
4:18
not author,
4:19
GROUP BY publisher.
4:22
And here we can see that
4:23
Penguin has one book.
4:24
Scholastic has seven,
4:26
HarperCollins has two
4:28
and O'Reilly Media also has seven.
4:30
We have a couple other two publishers,
4:33
and then everyone else just has one book.
4:36
Now, when we use Group By,
4:38
let's go back to this table here,
4:41
right here,
4:42
notice this order.
4:43
There's a number,
4:44
and this number actually means something.
4:46
This table shows the order
4:48
that the subclauses are performed in.
4:51
So FROM is going to run first,
4:54
sequel needs to know which table
4:56
where are we selecting From,
4:58
and then Where if president will run next,
5:01
it will decide which rows to use.
5:03
Then we have Group By
5:05
which we'll place rows into groups.
5:06
And then we have Select.
5:08
So select, which we've been using this whole time,
5:11
it's not going to run first in the example
5:15
of a little further down here,
5:18
right here, where we're selecting author
5:19
and then count from books, grouped by author.
5:23
What happens first is From,
5:25
so we're going to work with the book's table.
5:28
We are grouping by author.
5:31
That happens next.
5:33
Then, afterwards, we are going to select
5:36
I shouldn't say we,
5:37
but sequel we'll select author
5:39
and count star from that grouped books data.
5:44
So that's important to just understand
5:46
when we run these select, we're selecting author
5:49
or title or price or an aggregate function
5:53
that select happens after from, and after Group By.
5:57
So along with Group By,
5:59
a sister operator or sub clause
6:02
is called Having.
6:03
And Having allows us to whittle down
6:06
which groups we are going to select from.
6:10
So right now,
6:11
when I run SELECT author,
6:12
basically this command right here
6:15
author and COUNT (*) FROM books GROUP BY author,
6:18
we're including every single row,
6:20
even if we only have an author who's written one book.
6:24
If I want to select the authors
6:25
who have written at least two,
6:27
I could add in a Having subclause
6:31
or I could do it with publisher.
6:32
So right now I have this,
6:33
where I'm selecting all publishers
6:36
specifically the publisher name and the count,
6:39
how many times they occur
6:40
from books, group by publisher.
6:44
But I could also add in Having,
6:46
and then I could let's do
6:49
COUNT(*) > or = 2:
6:55
Now I'm only getting the groups
6:58
where count is greater than or equal to two,
7:01
meaning I'm grouping by publisher
7:03
and I only want to keep the publishers
7:06
that occur more than once,
7:08
greater than or equal to two.
7:09
And from those rows, I then want to select publisher
7:14
and their count.
7:15
So we get seven for Scholastic,
7:17
HarperCollins two,
7:18
Spiegel and Grau Group
7:20
I don't really know German, two.
7:22
And then O'Reilly Media, seven.
7:25
Let's try one more example here.
7:26
Let's select the authors,
7:28
will group them first by author,
7:31
and then we'll calculate their average page count.
7:34
And we'll only select from the authors
7:38
where their average page count is greater than 500.
7:42
So we'll select author,
7:45
and then we'll also select average page count
7:49
from books,
7:52
we group by author.
7:54
And right now,
7:56
this gives us every single author
7:58
and their average page count.
8:00
But if I only want the ones
8:01
that have a greater than how about 500 page count,
8:05
there's a couple of them here,
8:07
I could add in Having.
8:09
So having it's kind of like Where,
8:11
but it works with grouped results.
8:15
Having and then we'll do average star,
8:18
no, we want page count, not star
8:20
AVG(page_count) > 500.
8:26
And here we go.
8:27
So the first thing that happened
8:29
was selecting from books,
8:31
we have to specify which table,
8:33
group everything by author.
8:35
Then we are selecting the author name
8:38
and the average page count,
8:40
but only from those groups
8:42
where average page count is greater than 500.
8:45
And this is what we end up with.
8:47
Okay.
8:48
So that's Group By,
8:49
I know it can be a little bit trickier
8:51
than something as simple as Where
8:53
or SELECT *
8:55
It gets a little more complex
8:57
because now we're doing some aggregate operations
9:00
where we're grouping data based off of some criteria.
9:03
We're grouping by author, by publisher.
9:05
We'll get more practice with this,
9:06
if you still feel a little bit confused about it.
9:10
(cool upbeat music)