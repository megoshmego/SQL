thank you. would you include any scripts for demos you think might be helpful? 








will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "Null", and the section of the course "SQL", and subsection "DDL and Schema", as well as any demos you think would helpful to me?:


0:00
(gentle music)
0:04
- [Instructor] Next up, let's talk
0:05
about the concept of null in Postgres.
0:08
So null is a special value in SQL,
0:11
and it means something is blank or unknown.
0:14
So it's the lack of a value for a given column,
0:17
which is very different than zero or an empty string.
0:22
We've been seeing null,
0:23
I'm doing air quotes around seeing, when we create rows
0:26
in a table and we are leaving certain fields blank.
0:30
So if I SELECT * FROM my subreddits table,
0:34
we have a name column, we have chickenpics and cats,
0:37
but then we have two subreddits that do not have any name,
0:41
so their name is not set to empty string,
0:44
their name is null.
0:46
The unfortunate thing is that if we wanted to try
0:48
and select based off of that,
0:50
so SELECT * FROM subreddits
0:54
WHERE name = NULL,
0:58
it's not gonna work for us.
0:59
Instead, we need to use a special syntax IS NULL.
1:03
So SELECT * FROM subreddits
1:07
WHERE name IS NULL.
1:11
And now we get the two columns where there is no name.
1:15
So again, that's different than an empty string,
1:17
that's different than zero for subscribers.
1:20
Null is the lack of a value, an unknown value
1:23
for a given column.
1:25
Usually we want to avoid null.
1:28
Sometimes it's all right to have, but a lot
1:30
of the time we either want a default value
1:33
or we wanna force a row to contain a value for that column.
1:37
So you must provide a subreddit name.
1:40
If you're trying to make a subreddit,
1:41
we're storing subreddits for Reddit,
1:44
it doesn't make sense to have an empty name.
1:46
So in the next video, we'll talk
1:48
about constraints and how we can require different fields.
1:51
And we'll also see additional constraints,
1:54
like making things unique.
1:56
You must make a unique subreddit name,
1:58
we can't have a duplicate.
2:00
So that's coming up next.
2:01
This was a very quick video on null,
2:03
which is a special value in SQL
2:05
that represents no value,
2:07
the lack of a value or an unknown value.
2:10
(gentle music)
