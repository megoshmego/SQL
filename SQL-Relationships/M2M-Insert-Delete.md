thank you. would you include any scripts for demos you think might be helpful? 







will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "Many to Many Insert and Delete", and the section of the course "SQL", and subsection "SQL-Relationships", as well as any demos you think would helpful to me?:








(upbeat music)
0:04
- [Instructor] All right, so let's work
0:06
with our movies table, which already exists
0:08
and our actors table, which also already exists
0:11
although we haven't been using it.
0:13
So if we come over to our Postgres window
0:16
and we do a backslash DET
0:20
you'll see that actors was created for us as was roles,
0:23
just like movies and studios was created
0:25
or were created for us when we ran that seed file
0:29
the movies.sql file that we executed at the beginning.
0:34
So if we take a look at one of those tables,
0:36
like how about movies?
0:41
All right, we've already seen this.
0:42
We've got an ID title release here,
0:44
runtime, rating and studio ID.
0:47
And if we look at actors
0:51
very simple, first name, last name and birth date.
0:55
And then if we look at roles,
0:57
I'll make this a bit larger here.
0:59
It's quite simple.
1:00
It's just a movie ID and an actor ID
1:03
as well as the automatically created ID, the primary key.
1:07
Both of these are references.
1:09
They are references to other tables, right,
1:11
to the movies table and to the actors table.
1:14
And just like before,
1:15
with our one to many relationship with studios and movies,
1:18
we can't create a role where we have a movie ID
1:22
that doesn't exist in the movies table.
1:24
And same thing with actors,
1:26
we can't set an actor ID of 9,000
1:29
if we don't have an actor with that ID.
1:32
And we'll see how we actually set up those constraints
1:35
but I can give you a quick preview here.
1:38
We set up this integer references,
1:41
movies, references actors.
1:43
So movie ID and actor ID in Postgres
1:47
are set up so that they have an explicit reference
1:50
a binding, a tie to the movies table
1:53
and the actors table respectively.
1:55
And SQL will enforce that
1:57
we're actually adding in valid IDs for both of those.
2:01
So at the moment, there are some roles,
2:04
some actors and some movies.
2:06
If we do select star from movies,
2:09
we know there are some movies in there.
2:10
We added some in as well.
2:12
If we do select star from actors,
2:15
there are three actors that have been added in.
2:17
And if we do select star from roles,
2:21
that seed file also added some roles in.
2:24
However, I think most of them are actually nonsense.
2:26
They're not real roles.
2:28
For example, we've got Star Wars movie ID of one
2:32
and actor ID of one is Scarlett Johannson.
2:36
I actually didn't see the latest Star Wars
2:38
but I don't know if she's in that.
2:40
So why don't we go ahead and add some real roles?
2:43
We'll add a new movie first.
2:44
We'll get some more practice.
2:46
So inserts into movies
2:50
and we'll skip some of the stuff that doesn't really matter.
2:53
Let's just do title and release here.
2:56
None of these are required.
2:57
Runtime, rating and studio ID,
2:59
we've already seen that with studio ID.
3:01
We can leave that off.
3:03
So we'll do title release here
3:07
and I guess let's just do those two,
3:11
just keep it simple.
3:13
And then we add our values
3:16
and I think I'll do a couple of movies at once.
3:18
First we'll add in guardians.
3:22
Let's just do guardians 2
3:24
so that my table doesn't get super wide
3:27
when I print it out.
3:28
Instead of guardians the galaxy volume two,
3:30
which is quite long.
3:31
And I think that was 2017.
3:33
We'll also add in another movie the thing
3:39
which I can't remember when that came out, I don't know.
3:42
Let's just say 1982, I don't know if that's correct or not.
3:46
And we'll hit Enter here with our semi-colon.
3:49
So that now has added new movies in for us.
3:52
So if we select star from movies again,
3:56
we now have two more movies.
3:58
Now let's add in a couple actors.
4:00
So inserts into actors
4:05
and in actors, we actually do have some required fields.
4:09
If we scroll up here,
4:11
if you see under nullable, it says not null.
4:14
What this means, again,
4:15
this is something we'll learn very soon.
4:18
But at this point I set the table up for us.
4:20
Not null means you can't leave first name blank,
4:23
and birth date also can't be blank.
4:26
So insert into actors.
4:28
We'll do first name, last name and birth dates.
4:33
Just make sure that it's birth date.
4:36
One word, where are you?
4:38
Birth, underscore date.
4:39
Okay, so I would have messed that up.
4:43
Great, and then values.
4:46
We'll add in a couple actors.
4:47
So the first one will be Kurt Russell
4:53
and I have no idea what his birth date was.
4:55
I'm not even gonna try and get it right.
4:58
In 1970, oh, maybe we'll just make this up.
5:02
Okay, and then another actor was Bradley Cooper
5:10
and we'll make up his birth dates 1985.
5:16
No idea if that's accurate
5:18
and one more,
5:20
who else did we have in there, oh yeah, Chris Pratt.
5:26
And once again, no clue and we'll do 04-02.
5:31
Okay, so I'm gonna hit Enter here.
5:34
And now, if we look at our actors table,
5:39
we have three new actors, great.
5:41
Now let's add some roles in.
5:43
So if I wanted to add in, let's see.
5:47
Let's take Kurt Russell, who was in a couple of movies.
5:52
He was in guardians 2 and the thing.
5:54
Let's add in a row for him, for guardians 2.
5:58
And if we look at the roles table right here
6:00
it's just a movie ID and an actor ID.
6:03
So insert into roles, movie ID,
6:10
comma actor ID, and then values.
6:15
And we'll knock a couple out at once.
6:17
So for the first movie we'll do which has guardians 2,
6:20
that has an ID of 11.
6:22
So we'll add in 11.
6:24
And then Kurt Russell was in it.
6:25
Actor ID, Kurt Russell is four.
6:30
Then we'll add another one in.
6:32
We'll do a couple more for guardians of the galaxy.
6:35
So 11 still, Bradley Cooper was in that.
6:38
He has an ID of five right there.
6:41
And Chris Pratt was also in that.
6:43
So we'll add in 11 comma six.
6:47
And then we also have our next movie, the thing.
6:50
So movie ID of 12 and Kurt Russell was in that.
6:54
So he is four right there.
6:57
We'll hit Enter.
6:58
And if we select star from roles,
7:02
just scroll through these.
7:03
Now we have seven total rows.
7:06
Now when I try and insert something that is invalid,
7:08
so insert into roles movie ID.
7:13
Let's see what the other way around
7:14
just so you can see it really doesn't matter.
7:17
Actor ID first, and then movie ID, values.
7:21
Let's do an actor ID for Kurt Russell,
7:25
actually that's to Bradley Cooper,
7:27
five, that's his actor ID.
7:29
And then movie ID will be 72.
7:33
There is no movie with that ID.
7:35
The last one is 12.
7:37
So if I try this, we get an error,
7:39
just like we did when we tried to set an invalid studio ID
7:43
in our one to many relationship.
7:45
Key movie ID of 72 is not present in table movies.
7:49
So there is a foreign key constraint,
7:51
which means that the movie's ID has to be a real ID
7:55
in our movies table.
7:57
Same thing if I did it the other way around.
8:00
So an actor ID that doesn't exist like 100,
8:02
but a movie that does exist, I think 11 exists.
8:05
Yes, 11 is guardians 2.
8:07
Same thing, But this time actor ID is the error.
8:11
Actor ID of 100 is not present in the table actors.
8:16
Now you might be thinking,
8:18
this is kind of a lot of work
8:19
to add these join table references in.
8:23
So we have to know the ID of the actor or the actor,
8:26
and then the movie.
8:28
And we have to keep track of that 12 and four.
8:31
And as you saw there, this would be very difficult to do
8:35
if we didn't have the tables up in front of us.
8:37
If I wasn't able to quickly reference what is
8:41
Kurt Russell's ID it's four,
8:43
what is Guardian's ID, it's 11 or the things ID, it's 12.
8:47
But the reality of how we usually are inserting data,
8:51
into our database is through a application,
8:54
like let's say a flask app
8:56
where we have data coming in from some sort of request,
9:00
a user is submitting information.
9:01
What we actually do is we create the movie
9:06
or the actor all at once, along with the role
9:10
that we're going to assign.
9:11
And we can do it using Python code, where we have variables.
9:15
We can store those IDs and variables.
9:18
We'll see some tools, something called an ORM
9:21
that will help us create and work with our SQL data
9:24
without having to manually reference,
9:27
you know what is the things ID
9:29
or what is a Kristen Wiigs actor ID.
9:33
This is just us doing it from the command line.
9:36
But things will get a little smoother
9:38
once we actually work on a real application
9:41
where we integrate a database.
9:42
Lastly, let's talk about deleting.
9:45
So the real meaty topic we're about to get to
9:47
in the next video is joining.
9:49
And how do we join multiple tables in this case?
9:52
Not just two, but we've got movie information,
9:55
actor information, and roles information.
9:57
We need to join it all together.
9:59
That is coming up next.
10:00
But first, a quick note about deleting.
10:03
If you remember, we ran into some trouble
10:06
with the studios example, studios and movies.
10:09
If we do select star from movies, let's do studios.
10:16
If I were to delete one of these studios
10:19
like Orion pictures, which has an ID of four,
10:22
and if we go to our movies table,
10:24
we can see Amadeus has set referenced studio ID of four.
10:28
We ran into trouble when I tried to do delete from studios
10:33
where ID equals four.
10:36
It should be easy enough to delete one row
10:39
like this row right here.
10:41
However, we have this foreign key reference
10:44
in our movies table where that ID is being used.
10:48
So when I delete that,
10:49
we get this error update or delete on table studios
10:52
violates foreign key constraint.
10:54
That ID of four is still referenced from the movies table.
10:58
So the approaches that we talked about included
11:00
first deleting the movie and then the studio
11:04
or setting the studio ID to null.
11:08
Now I've actually set things up differently
11:10
with this roles table.
11:12
If we run backslash D to get more information about roles,
11:18
at the bottom you'll see this on delete cascade,
11:21
on delete cascade.
11:23
I won't go into detail about how this works exactly
11:27
but we will see it very shortly as well.
11:30
But all you should know at this point is that
11:32
when I delete, let's say an actor or I delete a movie
11:37
any of those references are also going to be deleted
11:39
from the roles table.
11:41
Let's say I wanted to get rid of Scarlett Johannson.
11:45
Grid actress nothing against her,
11:47
but I did list her incorrectly.
11:49
She has an ID of one actor ID of one.
11:53
It says that she's in black Panther,
11:55
the movie with ID of one.
11:57
Where's my movies right here.
11:59
Oh no, it says she's in Star Wars, the force awakens.
12:02
And I'm pretty sure she's not
12:04
haven't seen it, but I'm pretty sure she's not.
12:06
So if I just delete her entirely,
12:09
which I guess is a drastic action to take.
12:11
But if I were to delete her,
12:13
because I've set up my table differently,
12:16
let's just try it.
12:17
Delete from actors where ID equals one.
12:24
She has idea of one.
12:25
Let me just verify that, Scarlett Johannson ID of one.
12:29
Let's see what happens.
12:31
Hmm, seemed like it worked fine.
12:33
So let's take a look, select star from actors she's gone.
12:38
And what about our roles?
12:39
Select star from roles.
12:44
If you notice, we now only have seven or six roles actually.
12:49
The first role that was listed is now gone.
12:52
Now, this is very different
12:53
than what happened with studios and movies.
12:55
When I tried to delete a studio
12:57
if a movie was referencing it, we saw that error.
13:00
But because I configured this table differently
13:03
this thing called onto the cascade,
13:06
when we delete an actor in this case,
13:09
if they have roles in the roles table,
13:11
and we can see this earlier.
13:14
The very first role had ID of one.
13:16
It had movie ID of one, which was Star Wars,
13:19
the force awakens
13:20
and actor idea of one, which has Scarlett Johannson.
13:23
We deleted her.
13:24
And that means that this entire row was also deleted.
13:28
As soon as this actor ID no longer existed
13:32
SQL or Postgres, it got rid of this row as well.
13:36
So a different approach.
13:37
I just wanted to highlight this.
13:39
We could set up either version.
13:41
I could make it so that this wouldn't happen
13:43
and we don't get this automatic delete.
13:45
I could also have done
13:47
with the one one-to-many many example, studios and movies.
13:50
I could have added on delete cascade as well.
13:53
But anyway, what we've seen so far
13:55
is simply inserting information into our join table.
14:00
This is a join table that exists as part of our database.
14:04
It's not in memory,
14:05
like we saw earlier with our joining of studios and movies.
14:09
This table is technically a join table
14:11
because it's joining information from multiple tables.
14:14
And to insert all that we need to know
14:17
is a valid movie ID and a valid actor ID.
14:20
And if we try to use invalid,
14:22
either of those invalid movies, invalid actor IDs,
14:25
it will not work.
14:27
And then when we delete something
14:28
we delete a movie or we delete an actor,
14:31
it will cascade and remove any rows
14:33
that are referencing that movie or that actor.
14:37
So next step, the meaty stuff, what about joint?
14:41
(upbeat music)
