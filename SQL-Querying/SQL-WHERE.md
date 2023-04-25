thank you. would you include any scripts for demos you think might be helpful? 







will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "SQL WHERE", and the section of the course "SQL", and subsection "SQL-Querying", as well as any demos you think would helpful to me?:

0:00
(soft music)
0:04
- [Instructor] So the next sub-clause
0:05
we'll take a look at that we can use
0:07
in conjunction with select is where.
0:10
where allows us to whittle down
0:13
which particular rows we want to include.
0:16
So right now, when we run select star
0:18
or select title from books,
0:21
let's do title from books.
0:25
We are selecting every single row
0:27
and then just getting the title from each row.
0:31
But if I wanted to only include rows
0:33
where price was greater than some number,
0:37
or where author equaled Kyle Simpson,
0:40
or where the book title started with an E
0:43
or where a page count was between 500 and 600,
0:47
I would use the where sub-clause.
0:50
This allows us to filter.
0:52
So we use where a lot.
0:54
Well to use where to select posts,
0:57
where user ID matches the current logged in user.
1:01
That's a simple example.
1:02
So where, and then we specify some sort of condition.
1:06
And in SQL, we have almost all of the operators
1:10
that were used to
1:11
from things like Python and JavaScript.
1:13
So we have greater than, we have less than,
1:15
greater than or equal to, less than or equal to, not equal.
1:18
On the Postgres docs, you can go to functions and operators.
1:23
We can look at all the different,
1:25
these are logical operators.
1:26
So this is, and, or, and not.
1:29
So we also have those Boolean and or nots.
1:32
We have comparison operators, less than greater than,
1:35
less than or equal to, greater than or equal to,
1:37
equal is just one equal sign.
1:40
The only reason in JavaScript and Python,
1:43
that we need to use two equal signs
1:44
is because one equal sign is used for assignment
1:47
for creating a variable,
1:49
and then not equal exclamation point equal.
1:52
Or sometimes you might see this, is the same thing.
1:55
This means not equal.
1:57
So let's try a couple.
1:59
Let's select, what should we do?
2:01
Let's select title.
2:05
We'll do star from books where price is greater than $30.
2:16
And here we go.
2:17
If we look at the prices we're getting 89,
2:20
42 95, 49, and looks like that's it,
2:26
we're getting six records, 63, 112.
2:30
We could whittle that down a bit more.
2:32
We could also just select its title and price,
2:36
and now we can see it a little bit easier.
2:38
So title and price, I could revise that
2:42
to be where price is exactly how about 89.
2:48
And now we just get that one entry,
2:50
Introduction to Analytic and Probabilistic Number Theory,
2:52
price is exactly 89.
2:55
I can also do greater than or equal to 89.
2:59
And now we've got 89, 169.03 and 112.42,
3:05
same thing with less than or equal to,
3:07
I could also do where price is not equal to 89,
3:11
and that should give us what 39 books,
3:13
hope, I forgot my semi-colon,
3:16
and I think we have 40 total.
3:19
So we should get 39 rows now because as we saw,
3:22
there's only one book that has price of 89.
3:27
And we're almost there, come on, there we go, 39.
3:31
Now we also have these Boolean operators.
3:34
So logical and, and/or, and not.
3:37
To assure an example of that,
3:40
we have these page counts.
3:42
See if I can remember the name,
3:43
let's just do select star from books.
3:46
I can't remember how I named the column,
3:48
page underscore count.
3:50
So if we do select title comma page underscore count,
3:56
from books, and I want to select the long books to start.
4:01
So where page count is greater than maybe 500 pages.
4:10
And there we go, these are the long books,
4:12
but if I want a particular range,
4:14
I want the books that are between,
4:15
how about 700 and 800 pages.
4:19
I could do this, where page count is greater than
4:21
or equal to 700 and page count,
4:28
is less than or equal to 800.
4:31
semi-colon and there we go, 709, 752, 759.
4:38
So right here, we are selecting
4:41
just the title and page count
4:43
from the books table, but not every book,
4:47
only the books where page count
4:48
is greater than or equal to 700
4:50
and that same page count is less than or equal to 800.
4:54
Now there are a bunch of other operators
4:57
and different built-in functions that we can use.
4:59
We're not gonna go into a ton of detail
5:01
on them at the moment,
5:03
but just to give you an example,
5:04
we have things like In, right here.
5:08
In, is a built-in function
5:10
where we can basically test to see
5:12
if a value is in a group of other values.
5:16
So I'll give you a quick example of that.
5:18
If we select author from books,
5:24
and we can just see a list of the different authors we have,
5:26
let's say I wanted to select all of the books
5:29
who are written by Kyle Simpson, Don Norman, and who else?
5:35
Maybe what's another short name, Trevor Noah.
5:40
I could do this right here,
5:41
SELECT title, author FROM books WHERE,
5:46
and then I could write author IN.
5:50
And then I pass in a list of in this case, author names.
5:55
So, let's do something easy, like Ari Berman,
6:00
and then we have Trevor Noah somewhere.
6:05
Let's start with that.
6:08
And I need my semi-colon once again, and there we go.
6:11
We just selected every title and author
6:14
from the books table,
6:15
where author is either Ari Berman or Trevor Noah.
6:20
And we did that using the IN operator.
6:23
Technically I think it's a function in Postgres.
6:25
We could also have replicated this using equals, right?
6:29
We could have said where author equals Ari Berman
6:32
or author equals Trevor Noah,
6:35
but the nice part about IN,
6:36
so that I could easily add something else in here.
6:39
Like, who else do we have, Michael Pollan,
6:47
and now we're getting books by him as well.
6:51
So we're not going to go over
6:52
all of these different built-in functions
6:54
and these different subqueries
6:56
and operators that we have access to,
6:59
but just know that there are quite a few.
7:01
At this point, we wanna continue learning select.
7:04
And some of the other variations upon select,
7:06
we've seen where,
7:08
which allows us to narrow down where we are selecting,
7:11
which actual rows we want to work with
7:13
from within the book's table.
7:16
(soft music fades)