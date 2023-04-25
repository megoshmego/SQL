thank you. would you include any scripts for demos you think might be helpful? 







will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "SELECT and FROM", and the section of the course "SQL", and subsection "SQL-Querying", as well as any demos you think would helpful to me?:





0:00
(gentle music)
0:04
- [Instructor] Alright so now that we've got
0:06
our library database up and running
0:08
from that C data file,
0:10
we can start on our first
0:11
of these CRUD operations with SQL.
0:14
We'll begin with reading.
0:15
So searching or retrieving records.
0:18
And the special command that we use in SQL is SELECT.
0:22
SELECT is probably the most commonly used
0:24
of all SQL commands.
0:25
It's extremely flexible.
0:27
It's powerful,
0:28
and it's used all over the place.
0:30
It might seem like simply reading information
0:32
out of a database is pretty straightforward.
0:35
It doesn't seem like you need anything powerful
0:37
or flexible in order to do that.
0:39
And that is true if you're simply trying
0:42
to read every movie in our database
0:44
or every movie title, or every book, or whatever it is.
0:49
But we have a lot of these subclauses we can add in.
0:53
They're kind of like modifiers
0:54
for the SELECT statement where we can narrow down
0:57
what we're selecting,
0:58
we can group results by some sort of criteria,
1:03
we can order them, so we can sort the output,
1:06
we can limit how many we get,
1:07
we can add an offset.
1:09
We'll talk about most of these
1:11
as we make some more progress here.
1:13
But there are these different subclauses we can add on
1:15
for more complicated SELECT.
1:17
In addition, eventually we'll see that we
1:19
can actually select information from multiple tables
1:23
and combine it together.
1:24
And that is where selecting gets really powerful
1:27
is when we have a hundred different tables,
1:29
and we want to get results and information compiled
1:32
from two or three or more tables all in one go.
1:36
But the most basic thing we can do with SELECT
1:39
is to select information from some table.
1:42
So right now if I connect to my database,
1:45
psql is called library.
1:48
This is the easiest way to connect,
1:50
just as a refresher.
1:51
We can see that we have a table.
1:53
There's two of them,
1:54
but the one we'll focus on is called books.
1:57
So to select all of the information,
1:59
all of the rows or entries in the books table,
2:03
I need to combine SELECT with FROM.
2:06
FROM is how I specify which table
2:09
or tables, we're not there yet,
2:11
so just one table for now,
2:12
that I want to retrieve data from.
2:15
To select all information from the books table,
2:18
SELECT star FROM books.
2:21
So let's try it.
2:22
SELCT star FROM books.
2:28
So that all caps does not technically matter
2:31
but it's a good practice to put it there,
2:33
just makes it easier to read.
2:34
And then books is the name of our table.
2:37
Now when I hit Enter here,
2:38
we're gonna see a lot of content.
2:40
And since I'm zoomed in,
2:42
it's actually kinda difficult to read.
2:44
I've made my texts larger
2:46
but if I zoom way out here, I'm not zooming,
2:49
but shrinking down my tech size,
2:53
we can start to see how it's formatted.
2:56
Alright, about there.
2:58
Now let's still, there we go.
3:01
So we get all of this output.
3:03
Each book has an ID,
3:05
a title, an author, a price, a page count, a publisher
3:08
and a publication date.
3:10
And it looks like we have 40 different books,
3:13
40 different rows here.
3:15
So, if you are zoomed in like me,
3:18
and it's difficult to read all of these
3:20
'cause I am going to zoom in
3:21
so that you can see what's going on.
3:23
The formatting does get kind of screwed up.
3:25
One option, can hit Q by the way to get out of that.
3:28
One option is to set this setting,
3:32
backslash X to be auto.
3:35
And this will, I guess it's called expanded display.
3:39
It just changes the display style.
3:40
So now if I select everything from books,
3:43
our information is displayed differently.
3:45
So we still get rows,
3:47
but instead of seeing the table itself here
3:49
in a tabular structure,
3:51
we're seeing each row one at a time, which has an ID, title,
3:56
"The Design of Everyday Things," author, Don Norman,
3:59
price 12.99, 12.92.
4:01
Page count, publisher and so on.
4:03
And that's repeated for every book.
4:05
And I can hit Enter here to keep scrolling.
4:07
And this just makes it easier to display on smaller screens
4:11
or if I'm super zoomed in, so that you guys can see my text.
4:15
So it's not gonna impact the actual information
4:17
we're getting back.
4:18
It's just how it's actually output or displayed to us.
4:21
So that selects all of the books.
4:23
So that it's going to select everything,
4:25
every piece of information, every column,
4:27
that's what the star means, from the books table.
4:31
We have a different table here called employees.
4:34
And if I SELECT star FROM employees,
4:40
I don't think there's anything in there, and there's not.
4:43
And you can see what we get back here.
4:45
Zero rows.
4:47
If I tried selecting star from some table that doesn't exist
4:50
like dogs, I'll get an error,
4:52
relation dogs does not exist.
4:54
Eventually, we'll see how we can select data
4:56
from more than one table by joining them.
4:59
This involves FROM also, the SELECT keyword.
5:02
but we're not there yet.
5:04
but we do have some other things to talk about.
5:06
at the moment we're selecting every column.
5:09
So every book has ID title, author, price.
5:13
If we wanted to specify specific columns
5:16
that we're interested in, like title,
5:19
I can modify my SELECT.
5:21
I'm just gonna zoom in here and clear my screen,
5:24
actually is it clear in here?
5:25
I don't know.
5:27
We can select title only
5:29
with this syntax, SELECT and then instead of star,
5:32
which is a placeholder for everything,
5:34
so wildcard there, we will instead select title FROM books,
5:41
and I need my semi-colon.
5:43
Now we're just getting the book titles.
5:45
Here are all of the book titles.
5:48
I could do the same thing, but instead of title,
5:51
I could do author, and we're getting all of the authors.
5:56
Now it's not going automatically condense duplicates
5:59
or anything.
6:00
It's simply going through every single book
6:02
and whatever the author column is,
6:04
it's creating a list or a result that includes that entry.
6:08
So we have a bunch of books by Kyle Simpson,
6:11
a bunch of books by J. K. Rowling,
6:14
and we do get those duplicates.
6:17
We also could select multiple things.
6:19
So SELECT title, comma, author, FROM books.
6:26
And now we're getting title and author for each column.
6:31
So we have star to get everything about a single row.
6:35
So every single column possible,
6:37
or we can specify particular columns
6:39
that we're interested in.
6:40
You can chain them together with comas.
6:42
And then we also have FROM which can be used to specify
6:46
which table we're selecting from.
6:48
And if we go back to this chart here,
6:51
this chart includes the the order
6:54
that our different subclauses are run in.
6:57
You can see that FROM is going to be the highest priority.
7:00
So if we have FROM and WHERE and GROUP BY,
7:03
the FROM is going to be executed first.
7:06
At the moment we've only been using FROM,
7:07
so it doesn't matter.
7:09
But what I wanna point out is over here, it says required.
7:13
And the only required statement or subclause is SELECT.
7:17
And technically that means
7:19
that we don't have to use FROM,
7:21
however, it's virtually required
7:22
because if you do try and SELECT star from something,
7:27
without FROM, it gives us an error.
7:29
It's not gonna work.
7:31
There is one scenario where we can use SELECT,
7:34
And it's pretty silly, without FROM,
7:37
which is if we did something like this,
7:39
SELECT two plus five.
7:41
It's going to run this code
7:43
and then select the results which is seven.
7:48
So yeah, technically it's not required.
7:51
And that's why it's not showing up in red
7:52
as yes on this chart.
7:55
But every single SELECT that we do in this course,
7:58
and that will do in any fuss gap will involve FROM.
8:02
We need to specify where we're selecting from.
8:05
Okay, so next, we're gonna take a look
8:07
at some of these other subclauses
8:09
and how we can combine them along with SELECT and FROM.
8:12
(upbeat music)