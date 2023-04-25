thank you. would you include any scripts for demos you think might be helpful? 







will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "Outer Joins", and the section of the course "SQL", and subsection "SQL-Relationships", as well as any demos you think would helpful to me?:

Transcript


0:00
(soft music)
0:03
- [Instructor] Okay, so continuing on with Joins.
0:06
We just saw an example of Inner Joining.
0:09
An Inner Join is when we take the overlap
0:12
between two tables.
0:13
So where they reference each other, in our case,
0:16
we joined based off of studio_id in the movies table
0:19
and id in the studios table.
0:22
But we also have other types of Joins.
0:24
We have Outer Joins, and within Outer Joins,
0:27
we have Left, Right and Full Joins.
0:30
Now in order for this to really make sense,
0:32
we need to have some data that does not overlap.
0:35
Right now, every single movie in our movies table,
0:39
SELECT *from movies is referencing a studio,
0:44
but let's say I put out some independent film
0:47
that does not have a studio, that's totally fine
0:50
I can put that out.
0:52
Obviously, it's fine, in the real world it's great.
0:54
Congratulations me if I'm able to put that together,
0:57
probably wouldn't be able to, terrible at organizing,
0:59
but if I was, great.
1:01
But it's also fine in the context of our table,
1:03
we don't have to add a studio_id.
1:06
We'll learn later on how we can enforce
1:09
that some field is required,
1:11
but right now this column studio_id is not.
1:14
So I'll do INSERT INTO movies
1:20
and we'll do a title, release_year, runtime and rating,
1:28
and then our VALUES.
1:31
And we'll put one in here, let's say I release a movie
1:34
called "My First Indie movie".
1:39
And that was released in 2015.
1:43
Runtime was pretty short, 90 minutes,
1:46
It didn't have a big budget.
1:47
Rating is PG-13 and that's all we have, right?
1:53
Let's insert a second movie as well,
1:56
we'll call this 'my Second Indie Movie",
2:01
and this was in 2020.
2:02
This one's slightly longer it's 110 minutes
2:05
and it's rated R.
2:08
Okay, so now I have two new entries,
2:11
two new rows into movies where there is no studio_id.
2:15
On the other end of things,
2:16
we could also create a studio, a brand new studio.
2:20
Maybe that has not yet released a movie.
2:22
There's no movies associated with it.
2:25
So if we do SELECT * FROM studios, at the moment,
2:28
every studio here has at least one movie in our movies row
2:33
or in our movies table,
2:34
but I could INSERT INTO studios name and then founded_in,
2:42
VALUES, I'll insert at least one studio,
2:46
let's go with Chickenz Pictures,
2:52
which is founded in 2020-12-12.
2:58
Now I SELECT * FROM studios and we have Chickenz pictures,
3:02
but there is no movie that Chickenz Pictures has put out.
3:05
Let's do one more example.
3:07
This is a studio that maybe it's been around for a while.
3:12
How about since 1980-10-11.
3:20
And it's called Cat Cat Cat Pictures.
3:27
Okay, so now we have two studios
3:29
that do not have any representation in the market.
3:33
There are no movies associated with them
3:35
and we have two movies that don't have studio_ids.
3:39
Now we have some data that we can use
3:41
to explore these other types of Joins.
3:44
So when we do an Inner Join, as we've seen,
3:46
we are only going to get the overlap.
3:49
So if I run this code again,
3:50
just go back to what we've already run,
3:52
up arrow a couple of times, here we go.
3:55
We are selecting title and name from movies, INNER JOIN,
3:59
or we could just write JOIN, studios where there's overlap,
4:03
movies.studio_id=studio.id, we only get the movies
4:07
that do have a studio_id.
4:10
But if I were to do a Left Join, for example,
4:13
I will get all of the rows from the first table,
4:15
the left table,
4:17
regardless as to whether there is overlap or not,
4:20
plus any of the overlapping or matching rows
4:23
from the right side.
4:25
So if I did movies first and I did a Left Join with studios,
4:30
I would get all of the overlap that I got from Inner Join
4:33
plus any movies that don't have a studio.
4:37
So if I try it here, I'll just write it from scratch.
4:41
SELECT let's do title and then name.
4:47
Why don't we give it an alias like studio name FROM movies.
4:53
So movies is my left hand side here, the orange.
4:58
LEFT JOIN, so that's a syntax instead of just JOIN
5:01
or INNER JOIN, the default Join his Inner,
5:04
we're going to specify LEFT JOIN studios ON,
5:09
the same condition, so movies.studio_id=studios.id.
5:18
This gives me the overlap that we already got
5:21
from our Inner Join plus the left-hand side.
5:24
So everything from the left-hand side, which was movies,
5:28
the left is the first table we reference.
5:31
So we have movies here and we get every single movie,
5:35
including the ones that don't have an overlap.
5:38
So we have "My First Indie Movie', 'My Second Indie Movie",
5:41
there is no studio name.
5:43
So this is a table that has joined both tables together,
5:47
but it doesn't only include the overlap,
5:49
it also includes everything from the left side.
5:52
We also have Right Joins, it's a same idea here,
5:56
except from the other side.
5:58
So I could rewrite this query to SELECT title and name
6:01
FROM movies, also notice my alias is showing up here,
6:05
studio_name, instead of just name.
6:07
If I were to use a Right Join,
6:08
keep everything else the same,
6:10
but select using RIGHT JOIN instead of LEFT,
6:15
the right hand side is studios, it came second.
6:18
So we're going to have movies, RIGHT JOIN studios,
6:22
which means I want every single studios row.
6:25
And whenever there's overlap in the middle,
6:27
I also want the movies information.
6:29
And this is what we end up with here.
6:32
On the right-hand side, every studio,
6:34
it doesn't matter if they've put a picture out or not.
6:36
And then on the left-hand side,
6:38
if they have put out a picture,
6:40
we have the movie title they correspond.
6:42
So if I actually changed my query,
6:45
instead of selecting title and name, if I SELECT *,
6:49
there's gonna be a lot and I'm gonna have to zoom out
6:52
even further, I need to get rid of my alias
6:54
in order for that to work.
6:57
This makes it a little easier to see what's going on here.
7:00
So we have every piece of information possible
7:04
from the right-hand side, the studio side.
7:08
So we have studio_id, name and founded_in,
7:12
id meaning studio-id,
7:13
not the actual studio_id from the movies table.
7:16
But right here, if we cut that in half,
7:19
it's not quite in half, but if we split it here,
7:21
everything to the right is coming from the studios table.
7:24
It's the entire table, all of the rows.
7:26
And then on the left side, whenever there is an overlap,
7:30
we ended up showing all the movies information.
7:33
So compare that to what we did with the LEFT JOIN,
7:36
I'll just revamp this slightly like that.
7:43
Now we have every single movie,
7:45
every row from the movies table
7:47
and then any overlap from the studios table.
7:51
So we could rewrite either of these queries
7:53
to get the same results if I switched the order.
7:57
So if I wanted this information here, I want every movie,
8:01
regardless as to whether they've have a studio
8:05
behind them or not.
8:06
And I want overlapping studio data.
8:09
What I did here was movies LEFT JOIN studios.
8:13
I could also do SELECT * FROM studios,
8:17
but then do a RIGHT JOIN this time
8:20
because studios is first.
8:22
I will RIGHT JOIN movies ON movies.studio_id=studios.id.
8:33
So now I get the same data,
8:34
it's just flipped in terms of left and right,
8:38
but it's the same information.
8:40
So we have all the movies,
8:42
no matter if they have a studio or not
8:44
just like we did over here and then overlapping studios.
8:49
And then we have another Join called a Full join,
8:52
which is just gonna take everything from both tables
8:55
and put it together.
8:56
If there is an overlap based off of our Join condition,
9:00
then we'll get that overlap as one row.
9:02
Otherwise we'll just have some empty rows
9:05
when there isn't overlap.
9:06
So we'll take both sides, everything.
9:08
So I could rewrite this SELECT * FROM studios
9:12
and then I'll do FULL JOIN.
9:15
Whoops, I need to add a space there, here we go.
9:18
So now we have every studio and every movie,
9:22
when they overlap, we get this nice table row
9:25
where we can see information about both.
9:28
They are connected based off of this Join condition,
9:31
movie.studio_id and studios.id,
9:34
but where there is no corresponding information,
9:37
there's no relationship, we just have movies for example,
9:40
with no studio information.
9:42
"My First Indie Movie", "My Second Indie Movie",
9:45
they are independent there's no studio.
9:47
Same thing on the studio side, Cat Cat Cat Pictures
9:51
did not produce any movies, neither did Chickenz Pictures.
9:54
We're working on improving that,
9:55
but at the moment we just can't get our funding together
9:58
so there are no corresponding movies showing up.
10:01
That is a Full Join, we took both tables,
10:04
we just put them together, whatever overlaps,
10:06
great display that overlap.
10:08
But if there is no overlap on either side left or right,
10:12
just give us a data anyway.
10:15
So out of all of these Joins,
10:16
most of the time you'll be using Inner Joins
10:19
they are the most common.
10:20
You'll often have a relationship between tables,
10:24
where you want to find the overlap.
10:26
You want this sweet spot here where you can combine the data
10:29
from two tables to cross-reference or figure something out
10:33
to get more complex data back.
10:36
Outer Joins can be helpful though.
10:38
When you're trying to find rows in a table
10:40
that don't have a reference or a match in another table,
10:44
for example, things like finding independent movies
10:47
or finding studios that have not put any films out.
10:50
But again, most of the time you will be using Inner Joins.
10:53
It's important to note that those other Joins are available
10:56
and it's not like you'll never need to use them.
10:59
It's just that the majority of the time
11:01
Inner Joins are what you're looking for,
11:02
which is why we can simply write, Join
11:05
we don't need to add the Inner.
11:07
Okay, so that's some practice with Joins.
11:10
There's one other thing I wanted to show you,
11:12
which is just that we can combine some of these Joins
11:15
with the more complex operations we've seen before.
11:18
Things like GROUP BY or limit,
11:20
and some of the aggregate functions.
11:23
So if we take this Join table that we've created,
11:26
it's an Inner Join, I just wrote JOIN,
11:28
but the same thing as INNER JOIN,
11:30
and we see that we've got eight films
11:32
each one here that's showing up has a studio.
11:35
If I wanted to figure out which studios
11:37
had released the most movies,
11:40
I want it to just get a tally account for every studio
11:43
of the number of movies they've put out.
11:46
To do this, I do need a Join table
11:49
because in the studios table,
11:50
I don't have enough information.
11:51
I just have the studio name and they're founded_in date.
11:55
So we need to figure out how many times they occur.
11:58
How many times each studio_id is referenced
12:01
in the movies table.
12:02
So we can do this Join.
12:05
But what we'll actually do is add on a GROUP BY
12:09
and then we can group by the studio's name or the studio_id.
12:14
I'll do studio name, which we could just reference as name.
12:18
We could also do studios.name.
12:22
And then when we use GROUP BY,
12:24
we do need to use some sort of aggregate function
12:27
or something based off of that grouping.
12:29
So instead of selecting *,
12:31
I could SELECT the name of the studio and the COUNT,
12:37
how many times or how many elements are in these groups.
12:42
And there we go, we have Universal Pictures.
12:45
So name and then count, one, Orion Pictures, one,
12:50
Disney Studios, three, 20th Century Fox, one.
12:53
And I could also ORDER BY, and I'll go to the beginning here
13:00
and give COUNT an alias we'll do AS total.
13:05
And then I'll go to the end of this and ORDER BY,
13:08
it's kind of hard to see here, I guess I'll just hit enter,
13:12
ORDER BY total DESC, there we go.
13:18
We now have Walt Disney studios up top with three pictures
13:22
and then everyone else just has one.
13:24
So we used the JOIN and we used GROUP BY, we used COUNT,
13:29
an aggregate function, we used ORDER BY, we used an alias,
13:32
there's a lot going on here.
13:34
But we did use a JOIN
13:35
which is the thing I wanted to point out here.
13:37
When we write these Join queries,
13:39
we often combine them with some other sub queries
13:42
and operators and functions that we've already seen.