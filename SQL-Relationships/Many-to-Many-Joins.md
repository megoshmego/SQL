thank you. would you include any scripts for demos you think might be helpful? 







will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "Many to Many Joins", and the section of the course "SQL", and subsection "SQL-Relationships", as well as any demos you think would helpful to me?:



0:00
(upbeat music)
0:04
- [Narrator] Okay, onto the main event here.
0:06
Let's talk about joined with many-to-many relationships.
0:10
So we saw how to do to a join with a one-to-many,
0:13
all we needed to do was join two tables together.
0:16
Movies and studios.
0:18
The current table we have called roles
0:21
is technically a join table ,
0:23
or an associative table or a mapping table,
0:26
alternate terms, where we've connect two tables,
0:29
that's all that a join table is.
0:31
We have at least two tables connected in some way.
0:34
In the case of the roles table,
0:36
we have two foreign key columns
0:38
referencing an actor ID and a movies ID.
0:42
In this case also,
0:44
roles is an easy name, it makes sense.
0:47
That is the relationship.
0:49
It's a nice name and entity for what the association
0:53
between a movie and an actor actually is.
0:56
But we won't always have a nice name like roles,
1:00
for example, we could have studios and movies,
1:04
as we've talked about.
1:05
We could write that as a many-to-many relationship
1:09
because technically, we could have multiple studios
1:12
teaming up together to create or produce
1:14
or distribute or whatever their responsibilities are,
1:18
one movie, so we could have multiple studios
1:21
teaming up on a single movie,
1:22
right now, we're only allowing four.
1:24
One studio per movie.
1:26
It's a one-to-many relationship
1:28
and that means that we just embed the data
1:31
directly inside of our movies table.
1:34
But if we wanted to have a join table,
1:36
a third table, where we could associate a studio ID
1:39
and a movie ID,
1:41
so that we could have partnerships
1:42
where multiple studios were working together,
1:45
co-operating on a single movie,
1:47
what would we call that table?
1:49
I don't know, maybe there's a nice term for it.
1:54
Produce studio relationships, I don't know,
1:58
usually what we do in those scenarios
2:00
is we name our join table, that third table,
2:03
table one, underscore, table two.
2:05
So we could call it movies underscore studios.
2:08
Or studios underscore movies,
2:10
but in the case of movies underscore actors,
2:13
or actors underscore movies,
2:15
it makes sense just to call it roles.
2:17
It's a real thing.
2:19
Okay, so let's talk about joining our information.
2:22
Right now we have our roles table,
2:24
let's zoom in a tad.
2:25
Select star from roles.
2:28
If we wanted to join information,
2:30
let's say from the actors table,
2:34
we wanted to get the first name and last name
2:36
for each actor and put it alongside each role,
2:39
we already know how to do that,
2:41
it's just a join of two tables,
2:43
the roles table and the actors table.
2:46
So we could do select star from roles
2:50
and then join actors
2:55
on, where are we joining?
2:57
On roles dot actor ID equals
3:03
actors dot ID.
3:05
Now we've taken the information
3:07
where there's an overlap between actors and roles.
3:11
So we have all of our roles,
3:13
still see 'em here, these three columns,
3:16
and then we've taken each actor
3:18
based off of this actor ID
3:19
and added in their first name, last name
3:21
and birth date.
3:23
So if we just wanted to know,
3:25
I don't know, the name of each one of these actors
3:28
based off of the actor ID,
3:30
we could do a single join like we have here.
3:33
But at the moment, we have no information
3:35
that corresponds to the movies,
3:37
other than movie ID.
3:40
Now, I could use a single join like this
3:42
to calculate maybe the most prolific actors,
3:46
or just how many roles each actor has been in.
3:49
So instead of select star, I could do select first name
3:54
comma last name comma count star
3:59
and then I would need to group by,
4:02
group by and we'll group by actor ID.
4:08
And that's supposed to be actors ID,
4:10
not actor ID, need to specify the table
4:13
and we have this information here
4:15
that tells us Kurt Russell has two roles,
4:17
Chris Pratt has one,
4:19
Samuel L Jackson has two,
4:20
Bradley Cooper has one
4:22
and I just realized we do have a movie in our table,
4:25
select star from movies,
4:27
that Chris Pratt has been in.
4:29
He was in, what is it,
4:32
he was in Avengers, wasn't he,
4:34
and Jurassic World.
4:36
So I could very quickly add him in as well,
4:38
just so we have more data,
4:40
let's just get our actors here.
4:42
And then we'll do an insert into roles,
4:46
we'll do actor ID and then movie ID,
4:52
values and Chris Pratt's actor ID is six
4:57
and he was in Jurassic World,
4:59
which has an ID of four
5:01
and then his ID is six again
5:03
and he was in The Avengers,
5:06
so that's an ID of five.
5:08
Okay, so now we just have a couple more roles for him.
5:11
So when I rerun this query,
5:13
where we're joining actors alongside roles,
5:17
we're not involving movies at all.
5:18
We just wanna know the names of the actors
5:22
for each role and then regrouping by actors that ID
5:26
and we're counting,
5:27
we now can see Kurt Russell two,
5:29
Chris Pratt now has three.
5:31
So I could do an order by,
5:34
the easiest way to do that would be to give my count
5:38
a name here.
5:39
So count star as total roles
5:44
and then jump to the end.
5:45
Order by total roles.
5:49
And let's do descending. Desc.
5:53
Okay, so now we know the most prolific actors
5:56
in our database.
5:57
We have Chris Pratt, he's been in three movies.
6:00
Now obviously, some of these actors
6:02
have been in a lot more movies.
6:03
Probably Samuel L Jackson,
6:05
he's been around the longest,
6:06
I'm imagining he's been in the most,
6:08
but since we only have, what ten roles or something,
6:11
or fewer, seven, whatever it is,
6:14
this is good enough.
6:16
So at the moment, this is a double join
6:18
just between two tables.
6:19
A regular join like we've seen with a one-to-many.
6:21
But we also have the movies table.
6:24
So what if I just wanted to get each movie name
6:28
alongside an actors name?
6:30
Let's do first name and last name with the movie title.
6:33
We need to go through the roles table,
6:35
that's where that information is stored.
6:38
So the simplest thing we could do
6:39
is a select star from roles
6:44
join actors on and the same thing we just did,
6:48
roles dot actor ID equals actors dot ID,
6:55
then we can do another join, this time with movies.
6:59
On roles table dot movie ID equals movies dot ID.
7:09
And we've got a lot of information here.
7:12
I'll just zoom out.
7:14
We can see that we now have joined three tables together.
7:18
So we still have all the roles table stuff at the beginning,
7:22
which we probably don't need.
7:23
We definitely don't actually
7:25
because it's only going to give us the movie ID
7:27
and the actor ID, but we already have that
7:30
because we joined on all actors.
7:32
So he's our ID for an actor
7:34
and we joined on all movies.
7:36
So here's our movie ID.
7:37
Right, so we have movie ID of one,
7:39
it's just duplicated here.
7:41
So we probably don't need that.
7:43
But we can see we have now joined all movies
7:46
and actors where they intersect
7:49
using the roles table.
7:51
If we compare that to just select star from roles,
7:56
it's the same number of rows.
7:58
We have eight rows, eight rows here,
8:00
but we've now just put in the relevant actor information,
8:04
where it matches, based off of that actor ID
8:07
and the relevant movie information,
8:09
based off of that movie ID.
8:11
So if I wanted to slim this down a bit,
8:13
let's say I just want a movie title
8:16
and I want first name and last name from an actor.
8:19
I don't want any of this role stuff,
8:21
I don't want the ID's, I don't want birth date,
8:23
run time, ratings, studio ID,
8:25
none of that,
8:26
we can just rewrite our query
8:28
where instead of selecting star,
8:31
go back to the beginning,
8:32
we'll just select title,
8:35
first name and last name.
8:39
And there we go.
8:41
We now have each of our roles,
8:43
but the roles information is not being selected,
8:46
but that roles table is at the core
8:49
of this actual selection.
8:50
It is what we are using to join the two other tables.
8:54
So in each part of this join, each on,
8:57
we're referencing roles dot actor ID
8:59
equal to a real actors ID in that table
9:02
and then we also have on roles dot movie ID
9:06
equals movies dot ID.
9:09
So we can see Guardians of the Galaxy 2,
9:12
Kurt Russell was in that,
9:13
Bradley Cooper was in that,
9:14
Chris Pratt was in that.
9:16
The thing, Kurt Russell.
9:17
Jurassic World, Chris Pratt
9:19
as well as Marvels:The Avengers
9:21
and then Samuel L Jackson,
9:22
I don't think he was in either of these movies.
9:24
I know he was in an older Star Wars,
9:26
but in our fantasy reality here,
9:28
he is in Black Panther and Star Wars, The Force Awakens.
9:33
Now one thing that gets kind of annoying
9:35
is typing roles dot actor ID,
9:39
roles dot movie ID, movies dot ID,
9:42
actors dot ID.
9:44
Fortunately, we have a syntax where we can use this
9:48
alias short hand.
9:50
So I'll zoom in here.
9:51
We can specify when we write our from clause,
9:55
movies and then M
9:57
and M will now refer to the movies table.
10:00
So I can select M dot title.
10:03
Technically we don't need M dot title
10:04
because we only have title from the movies table,
10:08
but it's always best practice to specify
10:10
which table because we could have a lot of situations
10:13
where maybe a role has a title.
10:17
The title of the role, the character name.
10:19
So if we didn't have M dot title,
10:22
sequel would get confused.
10:24
So movies, M, roles, R
10:26
and we can then use M and R,
10:29
the same thing for actors, A.
10:31
So let's try this again.
10:33
Select and we'll do movie dot,
10:37
so M, we'll assume, that's the alias we'll give it,
10:41
dot title and then actor dot first name,
10:46
actor dot last name,
10:49
from roles,
10:53
join movies, or we can join actors,
10:57
doesn't matter which one we do first.
10:59
It does matter in terms of the order
11:00
that it will show up here,
11:02
but we'll get the same matches,
11:04
that same overlap.
11:05
We're only doing inter joins right now,
11:07
and that's usually what you're doing with many-to-many,
11:10
but I'll show a quick example of an outer join
11:12
at the end here.
11:13
So from roles and actually,
11:16
I meant to add, R, which I can still do.
11:20
I wanted to say from roles, R,
11:25
join and then we'll do movies, M
11:30
on R, which is our roles, dot movie ID
11:36
equals M dot ID.
11:39
M is the movie table, R is the roles table.
11:43
And if I just did this,
11:45
I would have an error
11:45
because I'm referencing A dot first name
11:47
and A dot last name,
11:49
so we also need to join again,
11:52
actors, A on role, which is R dot actor ID
11:59
equals actor dot ID and there we go.
12:05
So we have our movie title,
12:07
our first name and our last name
12:09
and we use this alias short hand to reference M
12:12
for the movies table, R for roles
12:14
and A for actors.
12:15
Just makes it slightly easier in my opinion,
12:17
instead of having to do actors dot X,
12:20
roles dot X, movies dot X.
12:22
Let's do one more example.
12:24
Let's add on a where clause.
12:27
So right now, if we look at our movies,
12:30
select star from movies.
12:32
Oh, what just happened, where'd you go?
12:35
I don't know what just happened.
12:36
Let's try that again.
12:37
Select star from movies.
12:40
We have movies that have been released for the most part,
12:44
after the year 2000.
12:46
But if we wanted to figure out the actor,
12:48
let's say actors first name and last name,
12:51
who have been in movies before the year 2000,
12:55
which I don't think we have very many,
12:57
but I know, who do we even have here?
12:59
The Thing, Kurt Russell was in The Thing
13:01
and that has a release year before 2000.
13:05
So we would need to do a join,
13:07
so I'll write our join.
13:09
So let's begin by selecting, I'll zoom in a bit,
13:12
make this easier to see hopefully,
13:14
it's a constant balance between zooming in and out.
13:17
In so you can see my text, out so you can see the output
13:19
and not have it all garbled and messed up
13:22
on multiple lines.
13:23
Let's select M dot title,
13:25
so we'll know which movie this role is in,
13:28
or the, if we have more than one role,
13:30
which titles, which movies
13:32
and then also actor, which we'll call A dot first name
13:37
and A dot last name.
13:41
From and let's start with movies this time,
13:45
which we'll call M.
13:46
We already referenced M there.
13:49
Join, we'll join roles, R on
13:55
M dot ID equals R dot movie ID
14:01
and after that, I can't enter,
14:04
of course, because we're referencing A
14:06
so we're just joining movies and roles,
14:09
then we need to add another join.
14:11
Join actors, A on A dot ID equals R, roles,
14:20
dot actor ID and if we just start with that,
14:24
we've already seen this before,
14:26
we're just getting every role with the movie title
14:28
and the first name and last name of the actor
14:30
in that movie.
14:32
But we can go further, let's add in our where.
14:36
So I reran this query,
14:39
but I removed the semi-colon.
14:40
It looks kind of odd because I'm getting the prompt again,
14:43
but we're still writing the same query,
14:45
where and then we'll do movie, M,
14:49
dot release year, I think it was one or two words
14:56
with an underscore, we can always check,
14:57
release year is less than 2000.
15:03
And all we get here is Kurt Russell's role
15:06
in The Thing.
15:08
So he is the only, or that's the only role
15:10
in a movie pre 2000.
15:13
Could also do it the other way around,
15:15
let's do after 2016.
15:20
And we get Black Panther, Guardians of the Galaxy 2,
15:24
but we're not getting Jurassic World,
15:26
we're not getting The Avengers,
15:28
we're not getting Star Wars, The Force Awakens,
15:31
I think that was 2015.
15:32
So we're only getting the movies
15:34
and the corresponding actors who are in each movie
15:38
after the year 2016.
15:40
We're not using any of the,
15:41
we're not outputting any other information from roles,
15:44
like the actor ID or the movie ID,
15:46
all we wanted was the title and actor first name
15:49
and last name.
15:51
Okay. We also could add in an order by,
15:54
if we wanted to.
15:55
So I'm gonna go back to the beginning of the query.
15:57
Let's also print out the movie dot release date.
16:05
So M dot release date and then I'll go to the end,
16:08
by the way, those shortcuts are control E and A,
16:12
to go to the beginning and end.
16:14
So let's add an order by.
16:16
Order by, and we'll do M dot release date.
16:22
So now we should display the release date
16:24
and we're also going to order by it.
16:26
Oh, what does it not like.
16:28
Oh man, it's not release date,
16:30
it's release year, isn't it?
16:32
Okay, well I'll quickly fix that.
16:34
Release year, go back to the beginning.
16:37
M dot release year.
16:40
Usually, we'll be writing our queries in a file
16:43
and it's much easier to make those changes
16:45
and here we go,
16:46
we've ordered them by release year, 2017,
16:49
2017, 2017.
16:50
If I were to change this,
16:53
where release year is now just greater than the year 2000.
16:57
Now we can truly see the order here,
16:59
2012, 2015, 17 and then 18
17:03
and we're showing you the movie title
17:04
as well as the first name and last name
17:06
of that particular role.
17:08
The association, the many-to-many association
17:11
between a movie and an actor.
17:14
And let's just complicate it even more,
17:17
ever so slightly, let's also order by after
17:21
the release year.
17:22
We have a couple movies, well it's just one,
17:25
Guardians of the Galaxy 2,
17:27
we have multiple actors,
17:29
let's sort them by first name.
17:31
So Bradley, then Chris, the Kurt.
17:34
So I'll recall my query
17:36
and then just add in a comma, actor dot first name.
17:42
So now whenever there's a tie
17:44
after we've sorted by release year,
17:45
or ordered by release year,
17:47
we now get alphabetized first names.
17:50
So that only comes into play here
17:52
on Guardians 2 and we have Bradley,
17:54
then Chris, then Kurt.
17:57
All right, so everything we've done so far here
17:59
has been inter joined.
18:00
In the next video, I'll show a quick example
18:03
of outer joins on this roles table
18:06
where we're joining three different tables together.
18:09
Again, it's not as common as doing an inter join,
18:11
but it's worth seeing.
18:13
(upbeat music)