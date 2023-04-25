thank you. would you include any scripts for demos you think might be helpful? 







will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "More Operators / LIKE", and the section of the course "SQL", and subsection "SQL-Querying", as well as any demos you think would helpful to me?:

0:00
(upbeat music)
0:04
- [Instructor] Next step, we'll talk a little bit more
0:06
about some built-in SQL Operators.
0:08
We've already seen a couple of them,
0:10
like in, we've seen and,
0:12
and or.
0:13
There are a few others I'd like to introduce,
0:15
but let's just recap in to start.
0:18
In allows us to select data where we're matching
0:21
some sort of let's say a column like ID,
0:24
and instead of matching specifically ID of one,
0:28
I could match an ID of one, two or three.
0:31
Using in, I can write this,
0:33
like this,
0:34
select, let's do ID
0:36
and title
0:38
from books
0:40
where ID
0:42
in,
0:43
and then I can pass in within those parentheses
0:46
multiple values, like one, seven
0:48
and nine.
0:51
And this gives me the books
0:52
where ID is in this collection.
0:55
It's in this row of arguments one, seven
0:58
or nine.
1:00
I could have rewritten that as where ID
1:03
equals one.
1:05
Or,
1:06
ID equals seven,
1:08
or ID
1:10
equals nine,
1:11
and we get the same results.
1:13
But clearly using in is easier.
1:16
We also have not in,
1:18
where I just add a not in front of that
1:21
and we get the opposite.
1:23
So we get everything
1:24
where ID is not
1:26
one, seven or nine.
1:27
The first one we get back has an ID of two, three,
1:30
four, five, six
1:31
We skip seven, eight
1:33
skip nine, 10,
1:34
and then everything is
1:36
we get the rest all the way up to ID of 40.
1:39
So that's in and not in.
1:41
We also have between.
1:43
Between, it's an easy way of selecting
1:45
based off of a range.
1:47
So why don't I select the books with IDs between
1:51
how about 20 and 25?
1:53
I could do it this way.
1:54
Select let's just do ID and title again
1:59
from books where
2:01
ID is greater than
2:03
or equal to
2:04
20
2:05
and
2:07
ID is less than or equal to 25.
2:11
So I could do that and I get 20 to 25,
2:14
or I could say where ID
2:17
between
2:19
20
2:19
and
2:22
25.
2:24
And I get the same thing
2:25
20 to 25.
2:27
And then we have our or and and operators,
2:31
which we've already been using those work very similar
2:34
to how the logical and, and logical or operators work
2:37
in Python or in JavaScript.
2:39
We also have not just regular not,
2:42
which we can add on to things like between.
2:45
So I could say where ID,
2:48
not
2:49
between 20 and 25.
2:53
And now I get one all the way through
2:56
hopefully 19.
2:59
And then we jump to 26.
3:02
I can also combine things like where ID
3:07
between,
3:08
let's go with
3:11
30
3:11
and
3:13
35
3:16
and
3:17
ID.
3:19
Or how about instead of just ID
3:20
and price is greater than 20.
3:23
It doesn't look like we have any,
3:25
how about prices greater than 10?
3:27
Let's also display the price
3:29
so we can verify.
3:30
So we'll select ID, title,
3:33
let's do ID and then price
3:35
and then title.
3:37
And there we go.
3:37
Our prices are 13, 11, 11.55,
3:40
12, 19.
3:42
So if I revise this to be
3:44
prices that are greater than how about 12.
3:48
Now we're only getting the books
3:50
where the IDs are between 30
3:52
and 35 and price is greater than 12.
3:56
So we get three total rows
3:59
so we can combine multiple operators
4:01
as we've just seen.
4:03
Another operator I'll mention now
4:05
that we haven't seen before
4:06
is called like.
4:08
Like is useful when you're trying to match text,
4:11
but you don't have an exact match.
4:14
So if I wanted to see which books started
4:16
with a T character
4:18
or th,
4:19
at the beginning of their title or authors,
4:22
that had a first name that started
4:24
with R,
4:26
I could use like right now,
4:28
if I just try and match things
4:30
like select
4:33
star
4:34
or let's do ID and author
4:37
from books instead of star.
4:40
Where author
4:43
equals R
4:44
that's only going to be an exact match
4:47
for lowercase R.
4:49
And we don't have any authors
4:50
with the name lowercase R
4:52
so to do more of a search, a pattern search,
4:55
I can use, like.
4:57
The way that like works
4:58
is that we have these specific, special characters,
5:01
these escape characters,
5:03
that mean things
5:05
to help us match patterns.
5:06
So we have a percent sign and a percent sign
5:09
is going to match any sequence of zero
5:12
or more characters.
5:14
So right here,
5:16
we're asking for something that starts with A,
5:18
and then any number zero or more characters afterwards,
5:22
it doesn't matter what they are.
5:24
We also have these underscores and underscores represent one
5:29
and exactly one character.
5:31
So here underscore B underscore will only match strings
5:35
where we have some character then B and then
5:37
one other character, but not more.
5:40
So in these examples
5:41
where we have ABC
5:43
like A
5:44
percent sign,
5:45
we get true because this just means A
5:48
and then something else, nothing else,
5:51
multiple characters, one character.
5:52
It doesn't matter. This is a match.
5:54
When we have ABC, like underscore B underscore
5:58
we also get true
5:59
because we have one character.
6:01
That's what underscore means, then B and then one character.
6:06
So if I wanted to find all of the books
6:09
that started with a capital T
6:12
the title of the book.
6:13
I could do select
6:15
ID,
6:16
title
6:17
from
6:19
books,
6:20
where title
6:22
like,
6:23
and then if I just did a capital T,
6:26
that will only match books with that title
6:28
of T.
6:29
But if I then put a percent sign after
6:31
I'm now matching
6:32
anything that starts with a capital T
6:35
and there we go
6:36
"The Design of Everyday Things."
6:37
"The Omnivore's Dilemma."
6:38
"The wind-up Bird Chronicle."
6:41
I could also put a percent sign in front of that.
6:45
And now I'm matching any book title
6:46
that has a capital T anywhere in it.
6:50
So we get things like
6:51
"The Design of Everyday Things."
6:53
"You Don't Know JS: Types and Grammar"
6:55
types has a capital T
6:57
JavaScript, "The Good Parts" capital T.
7:00
If I wanted to find all book titles
7:02
that contained a colon in them,
7:04
I could do select,
7:06
ID, title,
7:08
from books
7:10
where title
7:11
like,
7:13
and then not just a colon,
7:15
that will be an exact match.
7:16
Just like if I had done where title equals colon,
7:20
instead we want where title,
7:22
like,
7:23
and then percent, colon, percent.
7:28
And here we go,
7:29
"Design of Everyday Things," colon,
7:31
"Flatland," colon.
7:33
"You Don't Know JS."
7:35
And a couple more examples.
7:37
There we go.
7:38
If I wanted to count how many books had colons in them,
7:42
then instead of selecting ID and title,
7:44
I could select count
7:47
star.
7:50
And we have 19 books that have colons in them.
7:53
Now, an important note about how like works.
7:56
If we were trying to implement a search form,
7:59
let's say on a website, we have a flask app.
8:02
We have a form for a user to enter a query.
8:05
They type something in like Harry, Harry Potter.
8:08
They're looking for Harry Potter books, I assume,
8:10
or any book that includes Harry in the title,
8:13
but they don't capitalize it correctly.
8:16
So they just type Harry like this.
8:19
If we use this term
8:20
directly from our user,
8:22
it's coming from a form
8:23
and we perform a SQL query to go find books that match,
8:26
we're not going to find anything.
8:28
And that's because like, is case sensitive.
8:31
But fortunately in PostgreSQL, at least
8:34
we have a different operator.
8:36
Ilike,
8:37
I meaning case insensitive,
8:39
and this will ignore case.
8:41
This is actually something that is not in the SQL standard.
8:44
So be aware of that,
8:45
but it does exist in PostgreSQL.
8:47
So if I revise this
8:48
and just put I in front of like,
8:52
we now get matches that include capital H's,
8:55
even though the actual string we were looking for
8:57
is lower cased,
8:59
let's do one more example.
9:01
How about we find books that end with,
9:03
or how about author names
9:04
that end with the letter G.
9:07
So to specify that they must end with it
9:10
rather than just containing a G.
9:12
We could do select,
9:14
let's do just author for now,
9:16
from
9:18
books
9:19
where
9:20
and then author.
9:23
Ilike
9:25
and if we just did percent,
9:27
G percent
9:29
like that.
9:30
We'll get any author that includes a G somewhere
9:34
in their name.
9:35
So,
9:36
Gerald Tenenbaum,
9:38
Douglas, there's a G,
9:40
J.K. Rowling.
9:41
But if I only want
9:43
authors that end with a G.
9:45
I could change it to look like this
9:49
percent G and this will match any number of characters
9:53
and then a G at the end.
9:55
And there we go.
9:56
Rowling, Rowling, Rowling, blah, blah, blah.
9:58
And then Ellenberg.
10:01
What about if I wanted to select
10:02
authors that had three names
10:04
like Margaret Wise Brown, Margot Lee Shetterly
10:08
there might be another one,
10:10
well JK Rowling, I guess technically
10:12
you could say that's three words
10:14
or three names because we have spaces there.
10:18
I'm sure. I think JK is actually just one name who knows?
10:23
I don't know. I actually have no idea.
10:25
I'm talking about something, I don't know.
10:27
What we could do here
10:28
is look for any number of characters with percent
10:31
and then a space,
10:32
then any number of characters
10:34
and then another space
10:35
and any number of characters.
10:37
And there we go.
10:38
We're now matching any author name
10:41
that has two spaces in it,
10:43
but not just two spaces together.
10:45
They have to be separated by some number of characters,
10:48
some characters, some characters.
10:50
So Edwin A. Abbott, Mark Z.Danielewski,
10:56
Margaret Wise Brown, Margot Lee Shetterly.
10:58
All right.
10:59
So that is like,
11:00
and Ilike as well as a bit of a review
11:02
of things like in,
11:04
not and or, between,
11:06
and then we used a couple of them in conjunction as well.
11:09
So we could easily negate this
11:12
where author not, Ilike that.
11:15
And now we get all the authors
11:17
that don't have two spaces,
11:19
so we can use these together.
11:21
You could also combine them
11:23
where author, Ilike let's say an author starts
11:27
with a letter
11:29
J,
11:30
so J at the beginning,
11:31
and then percent sign
11:33
or author
11:36
Ilike,
11:37
how about
11:39
J maybe K
11:42
so K at the beginning,
11:43
and then some characters.
11:44
Now we have all the authors who begin
11:46
with a K or a J.
11:49
Okay.
11:50
So those are some useful operators in PostgreSQL.
11:53
(upbeat music)