thank you. would you include any scripts for demos you think might be helpful? 







will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "Indexing", and the section of the course "SQL", and subsection "DDL and Schema", as well as any demos you think would helpful to me?:

0:03
alright we've got one more topic to talk
0:06
about around the basics of sequel it's
0:08
something called indexing in sequel we
0:11
can create a database index which is a
0:14
special think of it like a special
0:16
lookup table which makes it very
0:18
efficient for our database to retrieve
0:21
some row or multiple rows based off of
0:24
some column so if you think of the way
0:26
an index works in a book like a text
0:29
book that text book has thousands of
0:32
pages potentially if it's some sort of
0:34
medical textbook and we're trying to
0:37
find a pretend word database and we're
0:39
trying to find something that mentions
0:41
the term I don't know hip Flexer without
0:46
an index we would just flip through the
0:48
entire book looking for hip flexor is it
0:51
here is it on page two page three and go
0:54
all the way through so if we have a
0:56
thousand pages or 2,000 or 3,000 pages
0:58
we might have to look two three four
1:01
five thousand times on each page but
1:04
with an index we can flip the back of
1:06
that textbook and I can alphabetically
1:09
look for hip flexor and hopefully it
1:11
tells me oh that's on page 1687 and I
1:15
can flip right there so I still have to
1:17
do a bit of work to go to that index and
1:20
search through it to find hip flexor but
1:23
then it quickly shows me where the data
1:25
actually is where I can read about hip
1:27
flexors now if you take that concept and
1:30
we translate it to a real database an
1:32
index is very similar it is like that
1:35
index at the end of the book where we
1:37
can use some particular column some
1:39
value to quickly find a corresponding
1:42
entry now we're not actually using the
1:45
index ourself so when we create an index
1:47
it will be used by Postgres behind the
1:50
scenes but we create them to speed up
1:53
our queries so if we planned on adding a
1:56
username to a user's table and if we
2:00
thought that it would be common to look
2:02
up a user based off of a user name which
2:04
is usually pretty common a user enters
2:07
in their username to log in we're
2:09
looking them up based off of that user
2:11
name we're not using an ID we
2:13
don't ask a user please enter your ID
2:15
from our database we ask them to enter a
2:17
username and then we retrieve
2:19
information using that username so it
2:21
would make sense to place an index on
2:24
the users table using the username
2:27
column an easy way for sequel to find
2:30
the correct row based off of a user name
2:34
so it will execute faster in fact here's
2:37
how much faster there's a special data
2:39
structure that most sequel databases use
2:41
called a b-tree you don't really need to
2:44
worry about what it is how it works
2:46
it's just a data structure that is very
2:49
fast at looking things up relative to
2:52
checking every single entry by hand
2:54
so we'll learn more about Big O notation
2:56
later on but this is called linear time
2:59
o of n which is what happens when we
3:02
don't have an index if we have 10,000 or
3:05
a million users in our database and
3:07
we're asking sequel to find the one user
3:10
that has the username of Stevie chicks o
3:14
of n me and said if there's ten thousand
3:17
or a million different rows we would
3:19
potentially have to check every single
3:21
row it's like a guess and check is the
3:24
first one it know is the second one
3:25
second one Stevie checks is the third
3:27
one Stevie chicks all the way to the end
3:28
and hopefully we find it or the database
3:31
finds it for us with an index we can
3:34
improve that time to a Big O of log n
3:38
don't worry about what logarithms are if
3:40
you don't remember or if you never
3:41
learned them here is what matters if we
3:45
had a million rows and we're looking for
3:47
a single column value instead of having
3:49
to examine every single row which is
3:51
linear time that would mean a million
3:54
examinations potentially by using an
3:57
index o of log n roughly translates to
4:01
checking twenty rows to get our answer
4:03
so we can improve the speed drastically
4:06
of our queries using an index now the
4:09
downside of course is that indexes take
4:12
time they have to be built and stored
4:14
and updated it's a duplication of
4:18
information just like the index at the
4:20
back of your book of a textbook we have
4:22
an index and on a large textbook that
4:24
could be another 20 30 50 or
4:27
some of the cookbooks I have at home I'm
4:29
kind of into cooking these days some of
4:31
the really big ones have really large
4:33
indexes at the back and I really
4:35
appreciate it
4:36
being able to look something up based
4:38
off of a term like chicken parmesan or
4:41
fondue or chocolate flourless whatever
4:46
it is but if we wanted to index every
4:49
single column in a table it could get
4:52
pretty inefficient quickly because
4:53
anytime we change that table anytime we
4:56
change a row those indexes need to be
4:58
updated and updating an index is not as
5:01
simple without going into the details of
5:03
how a b-tree works and how indexes are
5:05
actually stored it's not as simple as
5:07
just changing a single column and it
5:09
takes up space so in general you only
5:11
want to add an index to a column that
5:13
you know you'll be looking up rows based
5:16
off of so in the example of users we
5:19
know on most websites will be looking up
5:21
users by their username we're not going
5:24
to look up a user by their password
5:25
we're not going to look up a user by
5:27
their City but most likely we'll look
5:29
them up by a username also another
5:32
downside of setting up an index anytime
5:34
we change our row with an insert or an
5:37
update that query becomes more expensive
5:40
because now we have to also update the
5:42
index we don't actually do anything but
5:44
sequel does it for us and it is
5:46
expensive in terms of time and space
5:49
with all that out of the way let's see
5:51
how we create an index it's pretty
5:53
straightforward we have a command called
5:55
create index and we give our index and
5:58
name generally I like to name my indices
6:01
know indexes indices with the name index
6:04
at the end so something like users user
6:08
name index or I don't know recipe foods
6:13
index whatever it is something something
6:16
or something index so we specify a name
6:19
and then the table we're adding the
6:22
index to and the name of the column that
6:25
will be used to create our index we can
6:28
also create a multi column index we
6:31
won't go into this too much at the
6:32
moment but it works in the same way but
6:36
instead of one field or one column that
6:38
we might be looking up based off of like
6:40
username
6:41
maybe we're looking users up based off
6:43
of first name and last name they don't
6:44
have user names we have first name and
6:46
last name so an index just on first name
6:49
it's not going to help us a whole lot
6:50
but if we set it up in first and last
6:52
name we just pass in two values in
6:55
parenthesis it will create a index with
6:57
two columns so in my database let's see
7:01
what we have select star from subreddits
7:04
so in my database this reddit one we've
7:07
been working with we have this
7:10
subreddits table select star from
7:13
subreddits we really don't have a lot of
7:15
data in there at all but we have an ID a
7:18
user ID a name a description and if we
7:21
think of how reddit works most of the
7:23
time when we are using a subreddit we're
7:26
going to some URL that starts with well
7:29
reddit.com slash are slash some
7:32
subreddit name it's not a subreddit ID
7:35
it's not like two three four it's slash
7:38
chickens or slash funny slash soccer
7:43
that name is going to then be used on
7:46
reddit server to look up the
7:48
corresponding subreddit information in
7:51
the database so we wouldn't want to add
7:53
an index to the ID most likely unless we
7:56
also had some reason we were looking up
7:58
subreddit to buy ID but in the context
8:00
of a reddit clone most frequently will
8:03
be looking subreddits up by their name
8:05
so we can add an index to subreddits
8:07
with this command here create index and
8:10
then a name for that index so let's do
8:13
create index subreddit name index or ID
8:19
X it doesn't really matter and then we
8:22
specify the table so on sub reddits sub
8:27
reddits and then the field or the column
8:31
name which in our case is name just like
8:34
that and we get back a little feedback
8:37
it says create index now if I try and
8:40
look at my tables I won't see anything
8:43
new if I look at the details of sub
8:48
reddits I don't see anything new here in
8:52
the actual table schema
8:55
but I do see something here indexes we
8:59
have two different indexes one we did
9:02
not create so I'll talk about in just a
9:03
moment and then one that we did create
9:06
right here subreddit name index b-tree
9:10
there are different types of indexes
9:12
that's why it says b-tree there are
9:14
other varieties that is way beyond what
9:16
we need to care about and then it's an
9:18
index on the subreddit name so this is
9:21
really the only way we can see that we
9:23
do have a subreddit that we do have an
9:25
index on subreddit we won't directly
9:28
interact with that index we don't change
9:30
anything about our queries we still just
9:32
do a select just like we would if there
9:35
was no index but it will be faster if
9:37
we're looking up based off of subreddit
9:40
names so select star from subreddits
9:43
where name equals soccer that should now
9:46
be faster especially if we had thousands
9:49
of sub reddits or millions it will be a
9:51
lot faster as we saw in this example
9:54
here instead of having to check a
9:56
million times we can do it in roughly 20
9:59
checks or sequel can do it in 20 checks
10:01
now what is this primary key subreddits
10:04
p key index it's already here when we
10:08
set something up as a primary key that
10:10
means that it can't be null and it means
10:13
that the value must be unique sequel is
10:16
going to make an index for us behind the
10:18
scenes so that I can quickly tell if
10:20
something is unique or not so it has an
10:23
index on our ID for subreddits that way
10:27
if I try and add something new in like a
10:29
new row where I specify ID manually say
10:33
ID is 5 it can quickly check its index
10:36
to see that there already is an ID of 5
10:38
or that there's not so anytime we set a
10:41
unique constraint which I think we have
10:43
on users we have user name set to unique
10:47
if we do our d / d backslash d users
10:53
under indexes we have two different
10:56
indexes I did not make either myself I
10:58
did not run create index
11:00
we've got user's primary key and users
11:03
user name key unique constraint so by
11:07
setting something as unique
11:09
that creates an index behind the scenes
11:10
so that sequel can easily check it's
11:13
much faster for it to check if something
11:15
already exists otherwise if I tried to
11:18
make a new username or a new user with a
11:20
user name of how about Stevie chicks and
11:23
I have 10 million users without that
11:26
index here Postgres would have to check
11:28
every single user name is this one
11:31
Stevie chicks is this one Stevie chicks
11:32
but with this index that was created for
11:34
me it speeds it up drastically so the
11:38
point is we can make them manually like
11:40
we did with the subreddit name but also
11:42
certain constraints like primary key and
11:44
that unique constraint will also result
11:46
in an automatically generated index
11:48
created by sequel and the last thing
11:51
we'll talk about is dropping and index
11:54
to remove one it's very easy drop index
11:57
and then the full name of the index so
12:00
our index was subreddit name index I can
12:05
do a drop index subreddit name index and
12:11
now it's gone and if I go to backslash d
12:14
sub reddits we don't see that index we
12:19
see the original primary key index that
12:21
was created for us but we don't see the
12:23
subreddit name index that we had before
12:26
okay so indexes are extremely useful
12:29
they're good for you to know about
12:31
they're kind of weird because we use
12:33
them to speed stuff up but we don't
12:35
actually interact with them we create
12:37
them we delete them but we never run
12:40
them we never select against them or
12:42
using them sequel takes care of all of
12:44
that for us so we're just setting up
12:47
some tools behind the scenes to make our
12:49
queries faster
12:52
you
