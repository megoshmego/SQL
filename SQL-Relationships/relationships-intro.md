thank you. would you include any scripts for demos you think might be helpful? 







will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "Relationships Intro", and the section of the course "SQL", and subsection "SQL-Relationships", as well as any demos you think would helpful to me?:



cript


0:00
(upbeat music)
0:04
- [Teacher] All right, so next up,
0:06
we're gonna talk about relationships in SQL.
0:09
Postgres is an example of a relational database.
0:12
Let's talk about that relational part,
0:15
we have a couple of main goals,
0:16
we wanna understand
0:17
what makes Postgres and SQL in general,
0:20
or SQL databases in general relational.
0:23
We'll talk about particular types of relationships
0:26
between tables,
0:27
specifically a one-to-many, and a many-to-many relationship.
0:31
And then we'll talk about joins,
0:33
we'll learn how to select information,
0:35
select rows from multiple tables,
0:37
where we join data together to make more complex selections.
0:41
We're gonna start with just a general conceptual overview.
0:45
So let's say we're modeling movies,
0:47
we're making a movies application, like IMDb,
0:51
we need to store movies, obviously.
0:53
So each movie at the bare minimum will have a title,
0:57
and an ID most likely.
0:59
And let's focus on one particular column,
1:01
like the movie studio that created or produced the movie.
1:06
So we have a studio column,
1:07
Walt Disney Studios Motion Pictures,
1:10
20th Century Fox, Universal Pictures,
1:13
so each movie is going to have one of these studios.
1:17
In today's movie producing environments,
1:19
there's a lot of conglomeration of movie studios,
1:24
and we have a lot of duplication.
1:26
So Walt Disney Studios is responsible
1:29
in this table for three out of five movies,
1:32
then 20th Century Fox,
1:33
let's say we had thousands of movies in here,
1:36
between these three: Universal, Disney,
1:38
and 20th Century Fox is probably going to account
1:41
for like 80% of the major releases
1:44
in the last couple of years.
1:45
So one thing that's kind of annoying here is that
1:47
we have a lot of duplication,
1:49
we would have to write 20th Century Fox over and over
1:51
or Universal or Walt Disney Studios Motion Pictures
1:54
over and over.
1:55
That's not great.
1:57
But also, most of these studios also have
1:59
other information we might want to store.
2:02
If we did go to IMDb,
2:03
and we clicked on one of the top studios,
2:06
we can see a bunch of information about those studios
2:09
like where they're headquartered,
2:10
about their financial information is,
2:12
who's the CEO,
2:14
if they're a publicly traded company,
2:16
whatever data we want,
2:18
the date the studio was founded,
2:19
any name changes over time,
2:22
a lot of them have merged,
2:23
and then broken off and merged again and change names.
2:26
So to store more information about each studio,
2:29
even just one column like studio incorporation date,
2:34
or studio creation date,
2:36
or whatever you want to call it,
2:37
we could add a column to this table called studio date,
2:41
and duplicate it every time we have Walt Disney Studios,
2:44
let's say that was created,
2:45
I have no idea, 1930 something, who knows?
2:49
But let's say that it was 1930,
2:51
we would then need to have 1930
2:53
here, and here, and here.
2:55
And any additional information would have
2:57
to be duplicated for every single movie.
3:00
And if we have a bunch of duplicate studios,
3:03
we would have a lot of redundant information
3:05
stored in our movies table.
3:07
So the better approach is to not store
3:09
studio information in the movies table.
3:12
Instead, we simply store a reference
3:15
to a separate studio table.
3:17
So we can have our movies table.
3:20
All the movies information,
3:21
in this case,
3:22
it's simply title but we could have director,
3:24
release year, runtime,
3:26
rating, average meta score,
3:28
whatever we wanna store in here,
3:30
and a reference to a studio.
3:33
So then we can have a separate standalone studio table
3:36
where we only need to write
3:37
Walt Disney Studios Motion Pictures one time,
3:40
we have one entry for Disney Studios,
3:43
and we can have as much information as needed.
3:45
So founded in, CEO, location,
3:48
all of that stuff could be stored in this table,
3:51
once per studio.
3:53
And then we just store that ID
3:54
as a reference inside the movies table.
3:58
So Star Wars: The Force Awakens was put out by
4:00
the studio with ID of one,
4:02
Walt Disney Studios Motion Pictures.
4:04
So was Black Panther.
4:05
And so it was Marvel's The Avengers.
4:08
Then we have Avatar, studio ID of two,
4:10
20th Century Fox.
4:12
Jurassic Park, or Jurassic World,
4:15
ID of three, studio ID of three,
4:18
Universal Pictures.
4:19
So there's a lot of advantages
4:21
to structuring our data this way.
4:24
First of all, we reduce duplication.
4:26
And we have more flexibility,
4:27
where we can store a lot more data
4:29
about each particular studio,
4:30
but we only have to write it one time.
4:33
The only downside is that
4:35
if we want to get information about
4:38
both movies and studios together,
4:40
like I want to figure out which movies
4:42
were put out by Universal Pictures,
4:45
or how many movies 20th Century Fox released last year,
4:49
I need to gather and combine information
4:52
from more than one table.
4:54
And that's where join queries come in.
4:56
Join tables, which is something we'll talk about shortly.
5:00
So that's just a quick conceptual overview
5:02
of this idea of referencing one table
5:05
from within another table
5:07
of having some sort of relationship between our tables.
5:10
Next we'll detail two different types of relationships
5:13
one-to-many and many-to-many