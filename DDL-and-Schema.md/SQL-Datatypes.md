
thank you. would you include any scripts for demos you think might be helpful? 




will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "SQL Datatypes", and the section of the course "SQL", and subsection "DDL and Schema", as well as any demos you think would helpful to me?:


0:00
(soft music)
0:04
- [Instructor] Next.
0:05
Let's talk more about specific data types
0:07
that we can use for individual columns
0:09
when we create or define a table.
0:12
So, within Postgres,
0:13
there's actually quite a few different data types
0:16
on the documentation.
0:18
If you could just go to the main docs homepage,
0:21
click on data types
0:24
and scroll down. There's a nice little summary table
0:27
of the different available types
0:29
that we can use when we create individual columns
0:32
or when we define our columns
0:34
and they range from pretty standard ones
0:36
like, booleans true or false values,
0:40
dates, integers, right?
0:42
Whole numbers. We've got floats,
0:44
but we also have some pretty specific things
0:46
like, I've never used circle
0:48
but it represents a circle on a plane.
0:50
Or we have box a rectangular box on a plane.
0:54
Things like, I have no idea what this is.
0:57
Media Access Control address. E-U-I 64 format,
1:02
currencies, polygons on a plane. We've got a lot of them
1:07
but most of what we work with,
1:09
I've included some of the most common ones at least,
1:11
I've included in the slides. Things like integers.
1:14
So, integer is a valid type. It's also alias.
1:18
There's a shortcut,
1:19
which is just int if I can find it on here, integer,
1:22
here we go. We can use the term int instead.
1:26
We also have float,
1:28
which are floating-point numbers so we can have decimals
1:31
and you can specify the precision.
1:33
We have texts, which we've been using.
1:36
Text is a string of variable length.
1:39
So, that means we could have, you know, a username.
1:42
If it's text that is 10 characters or 50 characters,
1:46
although we may not want usernames
1:48
that are actually that long.
1:49
We also have varchar or varchar.
1:52
It's variable character.
1:54
If you try and find it on this table,
1:56
it's not under V it's not in varchar, varchar,
2:00
varchar is just a alias for character varying.
2:04
And we can pass in a maximum length
2:07
for our string for the text.
2:10
And you'll see how that works in just a moment.
2:14
We also have other types like booleans, dates.
2:17
So, the default date type does not include time.
2:20
It's not a date time. It's just date.
2:22
We have timestamps, which are dates and times.
2:25
And then we have this thing called serial
2:27
that we'll see in a moment,
2:28
which gives us auto incrementing numbers,
2:31
which we usually use to define a primary key,
2:34
most commonly an ID.
2:36
So, you've probably noticed when we are inserting data
2:39
into our movies table, the actor's table, the book's table,
2:42
we never specify the ID we want to add
2:45
that has done for us because of this serial data type.
2:49
So, let's define a new table in SQL,
2:53
by the way, we do have comments. They're kind of annoying.
2:56
If you have to type them manually, it's just two dashes
3:00
but thanks to VS-code we have a nice shortcut,
3:04
you can just toggle comments
3:05
like we would in any other language.
3:07
Let's create a new table.
3:09
If we're going with a modeling, Reddit,
3:12
let's create a table for subreddits.
3:15
So, if you don't know Reddit,
3:16
a subreddit is like a category on Reddit
3:20
where people can submit posts.
3:21
So, I can go to the soccer subreddit.
3:24
I can go to the NFL subreddit or to videos
3:29
or funny videos
3:30
or cat pictures or whatever different categories.
3:33
So, we'll create our table subreddits
3:35
and we'll start by giving the subreddit a name.
3:39
Name will be, we could do text
3:42
or we could do a varchar.
3:45
And the reason we might do that
3:46
is if we wanted to enforce some limit,
3:49
we don't want a subreddit that's a hundred characters name,
3:51
a hundred characters long.
3:53
So, let's limit it at maybe 15 characters.
3:59
We can also add in a description, D-E-S-C description,
4:05
which we'll keep as text.
4:07
And let's also add in subscribers,
4:11
the number of subscribers to our subreddit,
4:14
which will be an INT.
4:18
And we'll do the long name integer,
4:21
just so I get my syntax highlighting, although INT is valid.
4:24
We'll also add in, how about a field called is private.
4:28
So, on Reddit, you can make private subreddit,
4:30
someone has to be invited to we'll make that a boolean.
4:34
And then why don't we also add in an ID
4:37
which will set to that serial type that I mentioned,
4:40
which will give us an auto incrementing ID.
4:44
So, I'm going to save, which I don't actually have to
4:47
'cause we're not running this from the file.
4:49
I'm just gonna copy it,
4:50
paste it over into my Reddit database,
4:53
hit enter and it looks like it worked.
4:55
If we run \d, we see we now have a table called subreddits.
5:00
And now if I want to insert into subreddits,
5:03
we'll do INSERT INTO subreddits.
5:10
What is the pattern we'll go with?
5:11
let's do name,
5:15
descriptions. Description is kind of a long...
5:18
Maybe, I should have gone with just D-E-S-C or something,
5:21
but description, subscribers.
5:23
I probably should have gone with this sub count
5:25
and then is private.
5:29
Okay. So, we've got four fields. One, two, three, four,
5:31
the ID should be automatic and then we need values.
5:35
This should be review at this point
5:37
but now we'll see that these types matter.
5:40
So, let's just do something
5:41
where we're playing by the rules first.
5:43
So, we'll add a name for our subreddit.
5:46
Let's go with a chicken
5:50
pics
5:52
Sure.
5:53
And then a description, your home.
5:58
Your fav page to see chicken
6:03
pictures.
6:05
Jeez! Can't spell here.
6:07
And then we've got subscribers.
6:09
Let's say it starts out at 10 subscribers
6:13
and then is private, which is a boolean.
6:16
I need to close my quote here by the way.
6:18
And we'll say that it is not private.
6:20
It's a public subreddit and let's hit enter.
6:24
It looked like it works.
6:25
Let's do SELECT * FROM subreddits.
6:31
Okay. So, we have an idea of one automatically generated.
6:34
We have name chickenpics, description, subscribers
6:37
and is private set to F so we can just do T and F
6:42
for our booleans or we can write false and true.
6:44
Next let's try and insert some stuff
6:47
that doesn't conform to these data types we've set up.
6:51
So, first of all, we don't have any required fields.
6:54
We haven't seen how to do that yet.
6:56
Everything is going to be optional here.
6:58
So, let's just save time and do insert into subreddits.
7:04
And why don't we start with...
7:07
What do we have? Subscribers.
7:09
Let's try doing subscribers where we insert a new subreddit
7:15
where we don't do an integer.
7:16
We instead do hello as our subscribers count,
7:20
which is supposed to be an integer.
7:22
And here we go, we get an error,
7:24
invalid input syntax for type integer hello.
7:27
That is not a valid integer.
7:29
What if we did something like 10.5.
7:34
It seems to have worked. Let's see what happened.
7:36
SELECT * FROM subreddits.
7:40
You'll see that it was rounded up to 11.
7:43
So, even though it didn't give us an error,
7:45
it did change our data to become an integer.
7:48
What about name? If you remember, we set up this varchar,
7:52
varchar of 15 and I said that was different than texts.
7:58
Let's try inserting into subreddits
8:00
but we'll only insert name this time.
8:04
And we'll insert a very long name.
8:08
Like that. And I hit enter.
8:11
Value too long for type character varying,
8:14
too long for varchar where I said 15 characters max.
8:19
So, we can have shorter subreddits, like cats.
8:25
And if I select star, it has been added successfully.
8:28
But if I try and insert something that is too long,
8:31
we hit that limit.
8:32
You'll also see that my ID is automatically incrementing.
8:36
You might be wondering where two went.
8:38
Well, I had a little mistake in my recording
8:41
and I had to edit that out and delete it and start over.
8:45
So, we have one, two is missing three and four
8:49
but I assure you two was there but then I deleted it.
8:52
And that serial, that auto incrementing number
8:56
continues to go up. Even if you delete something,
8:59
like if I delete four the next ID is still going to be five.
9:03
We also have this boolean.
9:05
So, if we do an insert into subreddits
9:09
and we're inserting is private.
9:11
Is private and we try and insert...
9:15
Why not, just cats will get this error.
9:19
Once again, invalid input syntax for type boolean.
9:22
Cats is not a boolean.
9:24
So, these types matter,
9:25
sometimes it might seem like they don't matter.
9:29
Like in the case of subscribers
9:30
where we didn't get an error.
9:32
But as we saw, when we tried to add a float,
9:34
something with a decimal as the subscribers count,
9:37
which is an integer type, it does force it into an integer.
9:41
Also with description, which is text.
9:44
Technically,
9:46
if we tried to add in something that was a number,
9:50
like description here, values and I don't add in quotes
9:54
and I just type a long number here.
9:57
It's still going to work.
9:58
It just ends up adding it in as text.
10:02
So, it does treat it as text, even though it's a number.
10:06
That's a basic survey
10:07
of some of the data types you have access to in Postgres.
10:10
Remember there are quite a few others
10:12
but most of the time, we're just working with text,
10:15
maybe varchar, floats,
10:18
booleans,
10:19
serial definitely.
10:21
It's very common that we need to have
10:22
an auto incrementing ID.
10:25
Most often we use serial with an ID,
10:27
but you can have some other things that auto increment
10:29
and then date and timestamp.
10:32
So, date we haven't worked with
10:33
but it's pretty straightforward.
10:36
So, is timestamp.
10:38
Okay.
10:39
Next, we're gonna talk about particular constraints
10:41
we can add on.
10:42
Things like requiring a name or a subscribers counter,
10:47
or description. Right now, those can all be blank.
10:50
As you see here.
10:51
Here is a subreddit with no name,
10:53
no description and no is private.
10:56
We'll also see how to do things like set default values.
10:59
And we'll talk more about primary keys coming up.
11:02
(soft music)
