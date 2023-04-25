thank you. would you include any scripts for demos you think might be helpful? 







will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "Aggregate Functions", and the section of the course "SQL", and subsection "SQL-Querying", as well as any demos you think would helpful to me?:

Transcript


0:00
(soft music)
0:04
- Next up.
0:05
We'll take a look at
0:06
something called Aggregate Functions in
0:08
PostgreSQL.
0:09
So these are functions that
0:10
will compute a single value or
0:12
single result from some set of inputs.
0:16
The most common one
0:18
that you'll see in a lot of tutorials is count
0:20
We can use count,
0:21
in the simplest way just to count how
0:24
many rows we have in total.
0:25
We can do select, count,
0:28
star
0:30
from books.
0:32
This will select all book rows,
0:34
and then we're just gonna count
0:36
how many there are.
0:37
And that's all we print out.
0:38
The only output is 40.
0:40
Now we have other aggregate functions
0:43
like average.
0:45
What else do we have?
0:46
Max and min.
0:48
We have sum,
0:49
why don't we start with max and min
0:52
so I can select
0:53
mean
0:54
let's do price.
0:55
So instead of just price,
0:58
from books,
0:59
this will give me every single price
1:01
I could instead select mean price
1:04
(keyboard keys clicking)
1:08
From books.
1:09
And there we go 2.99.
1:11
I also could add in
1:13
max
1:16
And there we have
1:17
169.03,
1:19
it's expensive book THERE
1:20
must be a textbook.
1:22
We also have average,
1:24
so we could do something like
1:25
select average,
1:27
page,
1:28
underscore count
1:29
from books.
1:32
And there we go. That's the average
1:34
371.6500000000000
1:37
pages.
1:39
And we'll do one more. How about sum,
1:41
we could sum
1:41
the price of all of our books
1:48
from books,
1:48
select sum price from books.
1:50
And that is the price of all
1:52
the books added together.
1:54
We could also do something where we combine
1:56
one of these functions,
1:57
these Aggregate Functions with a WHERE clause.
2:00
So why didn't I select all books
2:03
by J.K Rowling and find the
2:05
average price? So select,
2:08
average,
2:09
actually, maybe page count is more interesting
2:13
from books
2:15
WHERE
2:17
author, equals.
2:18
And then I do have to write this exactly the same
2:22
J period space K period Rowling
2:28
And the average page count,
2:30
of course for Harry Potter books is quite high,
2:32
almost 600 pages
2:34
later on, We'll see how we can do a more
2:37
effective search, a fuzzier matching
2:40
instead of exactly J.K Rowling with the
2:42
right spaces and the periods and capitalization.
2:45
Because if I were to change this one thing,
2:47
like delete that space
2:48
or change this 'R' to a lowercase 'R' we
2:51
don't have any matches.
2:53
later on
2:54
We'll see how we can use something called,
2:55
LIKE, to help us out. But for now,
2:57
we're not really focused on that
2:59
So we have to type it
3:00
exactly as it appears in our table.
3:03
Okay.
3:04
So those are
3:05
a couple different Aggregate Functions.
3:07
There are other ones
3:08
you may use some of these
3:11
most often,
3:12
I end up using counts.
3:13
At least when I'm teaching,
3:15
we're going to use it in the next video.
3:17
Min, Max, sum, average
3:19
average can be useful too.
3:21
They return a single value based
3:23
off of multiple inputs.
3:26
(soft music)