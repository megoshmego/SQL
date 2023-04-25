thank you. would you include any scripts for demos you think might be helpful? 







will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "ORDER BY LIMIT OFFSET", and the section of the course "SQL", and subsection "SQL-Querying", as well as any demos you think would helpful to me?:


Transcript


0:00
(upbeat music)
0:04
- [Instructor] Next up we have Order By,
0:06
which allows us to select an output order,
0:09
basically a sort for our results.
0:12
So the syntax is order space by,
0:15
and then some criteria, a column name like author.
0:19
And we can specify ascending or descending.
0:22
So why don't we select about title and author from books.
0:31
Actually, title was quite long,
0:33
we get a lot of messy multiple lines,
0:37
if we use titles, because some of those titles are long.
0:39
So let's select author,
0:41
from books just to start.
0:44
And here we go, we're getting all the authors.
0:47
We could also select an ID in there.
0:50
So select ID, comma, author.
0:54
And that's what the default sort is
0:56
that ID of the book, one two three four five, and so on.
0:59
Now, if I want to order instead
1:01
by the name of the author,
1:04
select ID comma author from books order by author.
1:09
Now we get them in alphabetical order.
1:12
When we are working with strings,
1:14
we'll learn more about different data types
1:16
in sequel later on,
1:17
but we have text like this author name,
1:20
and this author name,
1:21
which is different than what we have here
1:23
or than price which is a number.
1:26
The sort between text
1:28
is going to be an alphabetical sort
1:30
and the default will be an ascending order.
1:33
So lowercase or lowest a, all the way up
1:36
to what do we have at the end here, a W.
1:40
I could change that by passing in desc.
1:43
I think it's we're descending.
1:45
There we go.
1:46
Now it's descending, I can never remember
1:48
if it's dsc, deesc.
1:50
And then we have ascending, which is asc.
1:55
And now we got the same thing we had before,
1:57
which is the default behavior.
1:59
But we can also sort based off of other things,
2:02
or we could order by other things.
2:03
So instead of just the ID and the author,
2:06
we can also include the price of each book
2:12
like that from books,
2:15
and now we get our price, we can order by price
2:23
and the default when working with numbers
2:25
will be a numerical sort from lowest to highest.
2:28
And I could reverse that,
2:32
by adding in, descending.
2:35
And now we have 169 is the most expensive book,
2:38
all the way down to I think 299.
2:41
What's interesting is we can also sort by multiple things.
2:44
We can order first by author
2:47
and then sort by something else.
2:50
So I'm going to write a new query,
2:52
we'll just select title and author
2:54
or author and title from books.
3:00
Well, you can see here that there is no sort at the moment.
3:04
It's based off of the ID which are not even printing,
3:07
but now if I order by author, that works great.
3:12
We've got Ari Berman, up top c d.
3:16
But then when we have duplicates,
3:17
like JK Rowling, we could also further sort them
3:21
based off of some other criteria like the book title.
3:25
So "Harry Potter and the Goblet of Fire,"
3:26
"Harry Potter and the Deathly Hallows."
3:28
Notice that these are not alphabetized by title,
3:31
they're only ordered in the main order
3:34
based off of the author name.
3:36
But if I were to add on a comma,
3:39
and then title as the next thing I wanted to sort by.
3:42
So order by author name first
3:45
and then whenever there's a tie,
3:47
break the tie using title.
3:49
This is what we get.
3:50
It looks the same at first, Ari Berman,
3:52
Kathy O'Neill, Don Norman, keep going down
3:55
and we hit JK Rowling.
3:57
And now these are alphabetized,
3:59
"Harry Potter and the Chamber of Secrets."
4:01
They all start with "Harry Potter and the,"
4:03
so we have C, D, G, H, and then O, and then P, and S.
4:11
So that's really it for order by.
4:13
We also have another sub query called limit,
4:17
which we can use to specify how many rows we want back.
4:21
So I could just change this on to what I just did here,
4:24
limit the first five.
4:26
And now we only get five records.
4:28
So they're still sorted.
4:30
They're ordered by alphabetical order of authors.
4:33
So it starts right here, might be hard to see,
4:36
I'll add more spacing.
4:38
Do it again, there we go one, two, three, four, five.
4:44
We could change limit to one.
4:47
We could select star from books limit two,
4:54
and now we get the first two matching results.
4:56
The first two columns,
4:58
but of course we can add in a lot more,
5:00
we could do things like select star from books.
5:03
Where price is greater than 500
5:07
order by author limit two.
5:16
Okay, well, we don't have anything,
5:18
our price is greater than, is that true?
5:21
Oh yep, not price I meant page count.
5:24
Page counts is greater than 500 limit two.
5:30
And here are the first two, we didn't order them,
5:32
so it's using the default IDs.
5:35
But we've got page count greater than 500,
5:37
here's 692, here's 709.
5:40
So why don't we also do
5:42
select star from books where page count greater than 500,
5:45
order by page count limit two.
5:52
Now we're getting the top two longest books.
5:56
So page count out, well, actually,
5:58
we ordered in the wrong direction, didn't we?
6:02
Let's change that order by page count to be descending.
6:07
Now we have the top two longest books, 1072 pages,
6:11
"Discrete Mathematics and Its Application Seventh Edition."
6:14
It's a great one, and then we've got 896
6:17
for "Harry Potter And The Order of The Phoenix,"
6:19
also a great one, maybe not as exciting
6:21
as discrete mathematics, but it does have more magic.
6:25
So that's limit.
6:26
And then one other thing that we have,
6:27
it's pretty quick, is offset.
6:30
Offset allows us to skip some number of rows.
6:34
This is commonly used to perform pagination.
6:37
So if we wanna find groups of five or 10 books at a time,
6:41
and then on the next page,
6:42
if a user were to click the next button,
6:44
we wanna find 10 more, but we want to start
6:47
at the 10th or the 11th and go into the 20th,
6:51
and then next time around we want 21 to 30
6:53
or whatever it is, we can add an offset.
6:57
So I'll make some space here.
6:59
Let's select, we'll just do ID,
7:02
Should we do select ID comma, author from books.
7:11
I'm just ignoring the title because it's so long,
7:13
and it changes my formatting here.
7:14
So we've got our IDs,
7:16
and I can limit it to be about five,
7:23
and we get the first five.
7:25
But then I could also do offset five.
7:30
Now we get six to 10.
7:32
And then if I do offset 10, we get 11 to 15
7:36
and we can keep going.
7:39
And this is how we would perform pagination,
7:41
if we wanted to give a user a response
7:43
that included five pages or five books at a time rather,
7:48
and each time they click the button to go next,
7:50
we would wanna get the next five,
7:52
but we still only want to retrieve five at a time,
7:54
we can use offset.
7:56
So we saw three different sub queries here.
8:00
We started with order by which we can use to sort,
8:02
we can specify ascending or descending,
8:05
we can also order by multiple criteria, multiple columns,
8:09
then we saw limit to limit the number of rows we get back
8:12
and we saw offset which we can use to specify an offset
8:16
for the results that we get back.
8:18
So there is a lot more to selecting,
8:20
but this is a good start.
8:22
Selecting is it can be an art,
8:24
especially when we get to more complex data structures
8:27
with multiple tables that have relations,
8:29
and there's different connections
8:31
and we need to talk about join tables.
8:33
It can get quite messy.
8:35
It can be pretty fun though, challenging,
8:37
but we've seen a pretty good number of sub queries
8:40
and different functions and operations that we can use,
8:43
to select particular pieces of data from a table.
8:47
Next, we're going to talk more about the rest of crud,
8:50
like updating or inserting records or deleting records.
8:54
They're definitely gonna be much faster
8:56
because we don't have as much to talk about.
8:58
(upbeat music)