thank you. would you include any scripts for demos you think might be helpful? 







will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "Working with One to Many relationships", and the section of the course "SQL", and subsection "SQL-Relationships", as well as any demos you think would helpful to me?:

0:00
(upbeat music)
0:04
- [Tutor] Next up,
0:05
let's actually play around using SQL
0:07
with a one-to-many relationship.
0:10
So there's a file
0:11
that you can download along with these notes
0:13
with the handout called movies.sql.
0:17
Just like with the library.sql file
0:20
that I gave you previously,
0:22
movies.sql will create a new database for us.
0:25
If I just open it up
0:26
or just cut it into my command line here,
0:30
at the top you'll see that it will look for a database
0:33
called movies example,
0:34
if it does exist, it drops it.
0:36
So we're starting from scratch.
0:37
If you happen to have movies example
0:39
it will be overwritten with a new empty movies example.
0:44
Then we connect to it.
0:45
Then a couple of tables are created.
0:48
And we wanna focus on this point, studios and movies.
0:53
Once again,
0:54
we haven't talked about how we actually define our tables.
0:57
So for now, I'm just giving that to you.
0:59
If we keep going down though,
1:00
you'll see that I've also pre inserted
1:03
some studios and some movies.
1:05
There are other tables we'll come back to,
1:07
actors and roles.
1:08
We'll talk more about those
1:10
once we cover many-to-many relationships
1:12
in a couple of videos.
1:13
So all you need to do is run this file.
1:15
And if you don't remember how to do it,
1:17
there's a little comment up top,
1:19
psql movies.sql
1:22
and then connect to that database.
1:24
So I'm gonna do that now.
1:26
In the same file or the same directory,
1:28
psql less than movies.sql.
1:34
So it drops the database,
1:35
it creates it, connects to it,
1:36
it makes a bunch of tables and it insert some rows
1:39
into different tables.
1:40
Then we will connect to that database,
1:43
psql and the name of the database
1:46
that was created is movies example.
1:50
Now I'm connected.
1:52
If I do a slash dt, I can see we have four tables here
1:56
and I've already put some data in there.
1:59
If I do select star from movies,
2:03
we have five different movies in here.
2:06
So Star Wars, Avatar, Black Panther,
2:08
Jurassic world, Marvel's The Avengers.
2:10
We've got a release year, a runtime, a rating
2:14
and a studio ID.
2:16
And the studio ID is exactly what we just talked about,
2:19
is a reference, a foreign key
2:22
coming from the studios table.
2:24
So if we look at these studios table,
2:26
select star from studios, we have three different studios.
2:30
Each one has a name
2:32
and a founded in date and an ID.
2:36
This ID is the primary key for the studio.
2:39
So if I tried to insert another studio with the ID of three,
2:43
we would have trouble.
2:44
We we'd have a problem.
2:46
And it is referenced by studio ID in the movies table.
2:50
So Star Wars, Force Awakens has a studio ID of one,
2:54
which means it was put out by Walt Disney Studios
2:57
as was Black Panther and The Avengers.
3:00
Avatar was put out by 20th Century Fox
3:03
and Jurassic World has a studio ID of three.
3:05
So it was put out by Universal Pictures.
3:08
Okay.
3:09
So we've run that data or we run that file.
3:11
We now have our database created.
3:13
We have our tables, everything has been set up.
3:15
Now, again, we haven't talked about create table
3:18
and actually defining our own tables.
3:20
But I wanna highlight something,
3:22
which is this line here.
3:23
When I created this movie's table,
3:26
I said, there's an ID, there's a title
3:28
and there's a studio ID.
3:30
Studio ID references the studios table.
3:33
And the reason that this is important
3:35
is that we set up a foreign key constraint,
3:38
which means that the reference here, studio ID
3:42
must be a valid ID from some existing studio.
3:47
So if I tried to insert a new movie
3:49
that had a studio ID of 9,000, it's not going to work.
3:54
If I tried it here, insert into movies
4:01
and then I'll specify the pattern.
4:02
We'll just do title
4:04
and studio ID
4:07
and then values
4:09
will be how about good old standby,
4:13
great film Amadeus.
4:16
And then let's say studio ID of 45,
4:18
that does not exist
4:20
and I get an error.
4:22
Insert or update on table movies
4:24
violates foreign key constraint.
4:27
Studio ID 45 is not present in table studios.
4:31
So it has to be a valid reference
4:34
and this is something we'll learn to configure.
4:36
It's pretty simple as you can see here.
4:38
We just specify studio ID references, studios ID.
4:42
But again, we'll talk more about creating tables later.
4:45
For now, we can just kind of skim over that.
4:48
So we can insert studios just like normal.
4:50
As we've seen previously, we use insert into,
4:53
we specify what we're inserting and then we add our data.
4:56
We can insert into movies
4:58
as long as we also specify a valid studio ID.
5:03
So I could update this,
5:05
Amadeus,
5:05
I don't know who actually put that out.
5:08
I guess I can find that out.
5:09
Let's see, well, apparently it was put out
5:12
by a studio called Orion Pictures.
5:15
So why don't I create a new studio,
5:17
insert into studios
5:21
and then it specify name and founded in,
5:25
values,
5:26
the name is Orion
5:29
spelled with an O Pictures
5:32
and I don't know what the founded date actually is.
5:35
I'll make this up,
5:37
1980
5:39
10, 10.
5:40
Okay.
5:42
So now we have a new studio in there.
5:44
If I select star from studios, I have a Orion Pictures.
5:47
Now I can insert into movies,
5:53
I'll do title.
5:55
What else do we have?
5:55
Release year,
5:59
runtime
6:01
and rating
6:04
and then finally studio ID
6:07
and then values.
6:08
I'll just do it on a separate line so it's easier to read.
6:11
Title is Amadeus,
6:14
release year is 1984 I think.
6:17
Runtime, it's a long movie I don't know the actual runtime
6:20
but it's like three hours or so,
6:22
we'll say 180 minutes.
6:24
Rating is R
6:27
and studio ID is this new studio we just created
6:31
which is ID four.
6:33
So if I put in invalid ID we've already seen,
6:36
it's not gonna work.
6:37
If I do five, we get an error.
6:40
But if I change it to be four,
6:43
it does work.
6:44
Now if I run select star from studios,
6:48
I meant movies not studios.
6:52
We have our new movie Amadeus studio ID four.
6:56
So that's inserting into one of these movies
6:59
or into the studio table.
7:01
When we're inserting into studios, it doesn't really matter.
7:04
We don't have any constraints.
7:05
We put whatever we want in there
7:07
as long as I'm not trying to change an ID.
7:09
Now, what about deleting things?
7:11
If I want to delete a studio,
7:14
I could try deleting where ID is one
7:18
or I could try deleting based off of a title or founded in.
7:22
But let's try doing a delete
7:26
from studios
7:30
where ID equals one.
7:34
If I try this,
7:36
we get an error.
7:38
So in the past, what we saw a couple of videos ago,
7:40
this is the right syntax to delete
7:42
but we have this constraint that says,
7:45
"You're violating foreign key constraint on movies."
7:48
This key, the ID is still referenced from the table movies.
7:53
So it's getting mad at us
7:54
for trying to delete this entire studio
7:57
because we have movies in the movie table
8:00
that depend on that ID, studio ID of one.
8:04
We have three movies with that ID
8:06
so that would be a problem.
8:08
So to get around this, we have a couple of options.
8:10
The first is that we can empty out the studio ID columns.
8:14
So for any rows that reference studio ID of one,
8:18
we can set them to null and then we can delete.
8:21
Or the other option is to delete the movies first
8:25
and then delete the studio.
8:27
Now I won't run it because I want to keep my data intact.
8:30
But if you do play around with this,
8:31
you can always just reset your database.
8:33
Run that file again, the movies.sql file.
8:38
So in this approach,
8:39
we would set all studio IDs on our movies
8:43
where studio ID as one.
8:45
So here, here and here,
8:48
we would just empty it out.
8:50
Set them to null.
8:51
And we would do that
8:52
so that that reference is completely severed
8:55
and then we could delete this entire studio
8:58
like we just tried to do with that same line.
9:01
And we would do this
9:02
if there was a world where it made sense
9:04
for us to keep the movies with the studio being gone.
9:08
So if the studio is deleted,
9:11
I'm not sure how we would actually want to implement this
9:13
in a real website,
9:14
you probably wouldn't be able to delete a studio on IMDP.
9:18
Maybe its name could change.
9:20
Maybe its status if it shut down, right?
9:23
Could go from active to bankrupt
9:26
or non-existent or whatever.
9:28
But you still would probably keep that information
9:31
so that users can see historically
9:33
this movie was produced by the studio.
9:36
But this is an option.
9:38
But here's another example.
9:39
Let's say we have comments and users.
9:42
There's two different approaches.
9:43
If a user deletes their account,
9:46
one approach is to remove all of their comments
9:50
and just anything that has to do with that user,
9:52
their posts, their comments it's gone if that user is gone.
9:56
But then an example of a website like Reddit
9:59
does something different.
10:00
On Reddit if you delete your account,
10:03
your comments still show up
10:04
but they don't say who wrote them.
10:07
It says account deleted or posted by,
10:10
deleted or something like that.
10:12
So the comments are still there.
10:13
You still have a record
10:14
but the reference to a user is gone.
10:16
So two different approaches
10:18
and it really depends on what you want
10:20
and how you're using your data.
10:22
We can notify that connection sever that bond
10:26
and then delete the studio.
10:28
Or we can delete all movies first
10:30
that have studio ID of one
10:32
and then delete that studio with ID of one.
10:35
We'll learn more and talk more about this
10:37
when we talk about DDL,
10:40
I hate this acronym, DML, DDL.
10:43
DDL is data definition language.
10:46
It's what we use, the subset of SQL
10:50
to define our tables and the data types and the references.
10:53
And everything we've been using so far is DML
10:56
data modification language.
10:58
It has to do with once we have our tables,
11:01
we have our data defined
11:03
let's add it in.
11:04
So we have our structure, which I've been giving you, right?
11:07
The tables have been created for you.
11:09
Then we just insert data,
11:10
delete data, select data.
11:12
But we will be talking about DDL
11:14
how we define our structures.
11:16
And when we do that,
11:17
we'll talk more about the trade-offs
11:19
between these two approaches.
11:21
Okay, so next step we're going to talk about join tables.
11:24
(upbeat music)