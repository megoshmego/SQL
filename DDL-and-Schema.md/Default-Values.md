
thank you. would you include any scripts for demos you think might be helpful? 





will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "Default Values", and the section of the course "SQL", and subsection "DDL and Schema", as well as any demos you think would helpful to me?:

0:00
(upbeat music)
0:04
- [Instructor] Next up, let's set up
0:05
some default values for our columns.
0:08
So it doesn't make sense to have a default name
0:11
for a subreddit.
0:12
Maybe a default description could make sense,
0:15
like no description or not specified,
0:18
but definitely for subscribers count,
0:20
we could have it default to one.
0:23
All we do is add DEFAULTS
0:25
and then some value, like DEFAULT 1.
0:28
Same thing for is_private:
0:30
by default on Reddit, when you make a subreddit,
0:32
it will be public,
0:34
So is_private could default to false
0:39
and username password don't really make sense
0:41
to have default values, so let's leave it at that.
0:44
As we've seen already, by default
0:47
if we don't specify something like for description,
0:50
the default value is going to be null.
0:53
So that's a standard behavior in Postgres
0:56
and SQL in general,
0:57
if something does not have the NOT NULL constraint,
1:01
meaning that null is not allowed
1:03
and we don't pass in a value,
1:05
it will default to null,
1:06
but we can change that default value.
1:08
So let's update our file here
1:11
just to DROP DATABASE reddit_db
1:15
CREATE DATABASE reddit_db
1:22
and then connect to reddit_db.
1:25
Because now I can just copy and paste all of this at once,
1:28
I don't have to delete my tables.
1:31
And first I'm going to disconnect from the reddit_db.
1:34
So I'll connect to anything else, how about library.
1:38
Now I'm going to paste my code in and
1:40
hopefully it dropped reddit_db, created it, it connected,
1:44
we are connected to it and it made our two tables.
1:49
Now let's just focus on subreddits.
1:51
Let's make a new subreddit and specify a name,
1:54
no description, no subscribers and no is_private.
1:58
So we'll just specify a name. So INSERT INTO subreddits,
2:03
and we'll just do name, VALUES, 'backyardchickens'.
2:11
And we'll start with that as our one subreddit.
2:15
Ah, value too long. Okay.
2:17
Well how about 'backyardchicks'?
2:20
Okay. Let's do a SELECT * FROM subreddits
2:26
and here we go.
2:26
You can see that is_private defaulted to false,
2:30
subscribers defaulted to one,
2:32
description defaulted to null,
2:35
because we didn't pass anything in and it does not have a
2:37
NOT NULL, it does not have a default,
2:40
has no constraints aside from this type,
2:42
which is, I guess in a way it is a constraint,
2:45
although text is the most flexible,
2:47
the most forgiving of these data types.
2:49
We could add a number in, it'll turn it into text.
2:52
Another example of a default value is SERIAL.
2:55
When we create a new subreddit,
2:57
we don't pass in an ID, it's not defaulting to null,
3:01
SERIAL is a way of creating a default value
3:04
that will increment.
3:06
And we can do that manually,
3:08
although it's pretty rare to do that,
3:09
you usually would just use SERIAL;
3:11
but let's say you were trying to create, I don't know,
3:13
unique product numbers and these product numbers needed to
3:17
follow a format instead of just a serial integer,
3:20
starting from one they needed to be five numbers
3:23
or 10 digits or whatever it is:
3:25
you can set up a default value
3:27
that will generate a number for you.
3:29
But for now this works great.
3:31
We can set a default for false, a default for one,
3:34
a default, for some string.
3:37
We can do whatever we want with default values.
3:39
(upbeat music plays)
