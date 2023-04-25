thank you. would you include any scripts for demos you think might be helpful? 







will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "Many to Many Relationships", and the section of the course "SQL", and subsection "SQL-Relationships", as well as any demos you think would helpful to me?:



0:00
(upbeat music)
0:04
- [Instructor] Alrighty.
0:05
So at this point we've seen an example
0:07
of a one-to-many relationship.
0:09
One studio, a movie studio, has many movies,
0:12
unless they're one of my horrible chicken studios,
0:14
or cut cut cut studios, in which case they have no movies.
0:18
But they potentially have a ton of movies like Disney.
0:22
But then each particular movie belongs to one studio,
0:25
and that's just how we set it up.
0:27
Yes, there is this situation
0:28
where we could have different studios working together
0:31
to produce a movie,
0:32
but our database currently doesn't allow for that,
0:34
so just ignore that fact.
0:36
Other examples of one-to-manys
0:38
that we've talked about in passing include posts,
0:42
so a user, lets say on Reddit can have multiple posts,
0:45
but each post corresponds to exactly one user.
0:50
Same thing with comments.
0:51
We can have a relationship between users and comments,
0:54
so users can have many thousands of comments
0:58
if they're prolific,
0:59
each comment belongs to exactly one user.
1:02
Or comments in posts.
1:04
So on Reddit you can write a comment on a specific post,
1:08
so each post could have thousands of different comments
1:10
associated with it,
1:11
but each comment is only associated with exactly one post.
1:16
So one-to-many associations or relations
1:18
are really really common,
1:20
but not every relationship can be expressed that way.
1:23
For example, let's take the example of actors.
1:26
If we have this movies database, we'll keep using it.
1:30
We have movies at this point.
1:31
If we also wanted to store information
1:33
about actors and actresses
1:35
and store them in association with the movies they were in,
1:39
the different roles that they played,
1:41
a one-to-many relationship wouldn't really work for us,
1:44
because an actor can play a bunch of different roles.
1:47
They can be in 10, 20, 50, 100 different movies,
1:50
and within each given movie, you can have multiple actors.
1:55
You almost always do,
1:56
unless you are creating a very niche film,
2:00
where you have exactly one actor,
2:02
the one-to-many approach is not gonna cut it for us.
2:05
So this is an example of a many-to-many relationship.
2:09
If we hop over to a spreadsheet here,
2:11
let's think about how this could work.
2:13
We have a movies table.
2:15
I'm skipping some of these stuff around
2:17
runtime and rating and studio ID.
2:21
But let's just say we're working with movies
2:23
and we want actors.
2:25
So we could make an actors table.
2:27
Each actor will have an ID and then a name.
2:31
We could do first name, last name, it doesn't matter.
2:33
We'll just go with name, and we could just start with that.
2:38
So I know that in "Guardians of the Galaxy" ,
2:40
we'll just list some actors here.
2:43
Let's see, there's Kurt Russell is in there,
2:47
we've got Bradley Cooper,
2:52
so he'll have ID of two,
2:54
ID of three will be I guess Chris Pratt.
2:59
Okay, so all three of these actors
3:02
are in "Guardians of the Galaxy".
3:05
So with what we saw earlier with a one-to-many relationship,
3:08
just quickly add some formatting here,
3:11
what we would do is store some sort of foreign key
3:15
on the movies...
3:16
Oh that's a bit large,
3:18
on the movies table,
3:19
or we could put a movie ID on the actor's table.
3:24
But the problem with this if I were to add in actor ID,
3:29
the problem here is that I can only have one actor.
3:32
So "Guardians of the Galaxy",
3:34
let's say Kurt Russell was in it, he was,
3:37
but now what about Bradley Cooper?
3:39
He voiced the raccoon character,
3:41
what's it called? Rocket.
3:42
And then Chris Pratt was also in "Guardians of the Galaxy",
3:46
so I guess we could've done actor one ID, actor two ID,
3:51
actor three ID, and theoretically this could work
3:55
if we created 100+ different columns
4:00
for actor one, two, three, four, five,
4:01
six, seven, eight, nine,
4:02
whatever the maximum number of actors
4:04
that a single movie has, we would need that many columns.
4:08
And on a lot of these these movies, smaller cast movies,
4:12
indie films that don't have a huge cast,
4:14
"Hateful Eight" doesn't have a very large cast,
4:16
we would have tons and tons of empty columns
4:19
or empty rows in those columns.
4:21
So it really does not work to do with this way.
4:24
I could say, okay actor one is Kurt Russell
4:27
in "Guardians of the Galaxy" actor two is Bradley Cooper,
4:31
actor three is Chris Pratt, and continue with that.
4:36
But if we look at "Guardians of the Galaxy",
4:38
there is quite a large cast.
4:40
I'm not even viewing the full cast, I'm not IMDb.
4:42
Here we go.
4:44
All of these roles,
4:47
at least 100 different actors in the same film.
4:50
So that approach doesn't quite cut it,
4:53
and the same would go if we tried to do it the opposite way,
4:57
to put a movie ID here,
4:59
like movie one ID, movie two ID,
5:04
we would also have to have
5:06
some potential maximum number of movies.
5:09
Maybe 100 possible columns,
5:12
and then for actors who just haven't been in many movies,
5:15
we would have a ton of empty columns in those rows.
5:19
So neither approach here is gonna work very well.
5:22
What we would do instead, is set up a third table.
5:27
We have our movies table, we have an actors table,
5:31
we can include other information,
5:33
so first name, last name, birth date.
5:35
And then we have a third table,
5:37
and this table is technically a joint table.
5:41
It's not one we're creating in memory, it's actually stored,
5:44
it's a structured table in our database.
5:47
So we would have a third table called in this case its easy,
5:51
we would call it roles,
5:53
because each joining of an actor
5:56
and a movie is a thing in the real world, it is a role.
6:00
So inside of roles, we could have a role ID,
6:03
just a regular ID, and then movie ID, actor ID,
6:09
and we could even have other information like character.
6:15
So, lets start with "Guardians of the Galaxy",
6:18
movie ID of one, and Kurt Russell was in that,
6:23
and his character name,
6:24
I can't exactly remember right now, Ego.
6:30
And then also, in "Guardians of the Galaxy",
6:33
this is volume two I believe, not volume one,
6:36
doesn't mater really,
6:37
but we also have Bradley Cooper was in there,
6:41
and he played Rocket,
6:43
and then after that, still in "Guardians of the Galaxy",
6:46
we have Chris Pratt,
6:48
I think his character's name is Star-Lord, is that right?
6:52
Peter Quill / Star-Lord, okay. We'll go with Star-Lord,
6:56
and this allows us to have one movie
6:59
with a bunch of actors in it,
7:01
and we could also have a single actor
7:04
who's in a bunch of movies.
7:05
So a many-to-many relationship
7:07
is really just two one-to-manys back to back.
7:10
At this point, we've implemented the one-to-many,
7:13
where one movie can have many actors,
7:15
now let's add in some examples of other roles.
7:18
For example Kurt Russell was in "The Thing",
7:21
so movie ID of two, actor ID of one, Kurt Russell,
7:26
and his character's name I can't remember.
7:29
Let's see. It really doesn't matter here.
7:32
Macready, I don't know.
7:36
Like that, and he was also in "The Hateful Eight",
7:42
so that's a movie ID of three.
7:44
Actor ID is still one, for Kurt Russell,
7:47
and I can't remember his role
7:49
in "The Hateful Eight" either, let's see, John Ruth.
7:53
Okay, so that's enough of an example here for now.
7:56
We have this third table
7:58
that is joining information about movies and actors,
8:02
two foreign keys, two references to other tables,
8:06
and in this case we have some additional information
8:09
like a character name, the actual name of the role.
8:12
We could also include things like awards nominations,
8:15
although that might actually be a separate table
8:18
because you can have multiple nominations or awards,
8:21
wins, losses, for each character.
8:24
Although I don't know if any of these characters
8:26
really were nominated for anything,
8:28
these are not the typical Oscar fodder.
8:30
But sometimes we'll have tables
8:32
that don't really have an analog in the real world,
8:36
so the joining of a movie and an actor is a role.
8:41
But we may have other situations, we almost certainly will,
8:45
where we just end up joining one table
8:47
with some other table, so two foreign key references
8:50
where there's no other additional information,
8:52
and we don't have a great name for that table.
8:55
So we usually would just name it
8:56
something like movie actors, or actor movies.
9:02
But in this case role makes sense,
9:04
and we can include additional information.
9:07
So here is a nicer color-coded spreadsheet
9:10
that matches with the actual data we have in our database.
9:13
If you ran that movies that sequel file to seed our database
9:17
it created the database, created the tables,
9:19
we have four different tables.
9:21
We have movies which we've already seen,
9:24
and its color coded, so studios is a yellow table.
9:28
Whenever we see yellow somewhere else like right here,
9:30
this is a foreign key reference to the studio's table.
9:34
So each ID here has to be a valid ID in studios.
9:38
So that's what we saw with a one-to-many relationship.
9:41
But then the relationship between actors and movies
9:44
is not expressed anywhere in those two tables
9:48
like studios and movies was.
9:50
We can see the relationship is actually right here
9:52
inside of movies,
9:53
but for a many-to-many as we've already talked about,
9:56
we set up a third table joining movies and actors.
10:01
So we have two IDs, a movie ID and an actor ID,
10:05
and then the actual role ID,
10:07
which will just be automatically created for us.
10:10
So here we have, let's see,
10:12
movie ID of three is "Black Panther",
10:15
actor ID of one is Scarlett Johansonn,
10:18
and she was in "Black Panther" I think,
10:20
I'm pretty bad with those Marvel movies.
10:23
If she wasn't, then just pretend that she was.
10:27
Then we have movie ID of five,
10:29
Marvel's "The Avengers", actor ID of two Samuel L. Jackson.
10:34
I know he was in "The Avengers", or at least one of them.
10:37
So here we're joining two different references
10:39
from external tables, blue for actors, red for movies.
10:44
This is what we currently have set up in our database,
10:47
and it's what we'll play around with in the next video.
10:49
We'll start to see how we can create new movies.
10:52
We'll see how we can create new roles,
10:55
so how we insert data into the roles table,
10:58
as well as updating things, deleting things,
11:00
kind of what we did with our one-to-many example,
11:03
movies and studios,
11:04
but this time it's a many-to-many relationship.
11:07
So that's up next.
11:08
(upbeat music)