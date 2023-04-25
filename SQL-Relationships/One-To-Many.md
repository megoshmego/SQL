thank you. would you include any scripts for demos you think might be helpful? 







will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "One to Many Relationships", and the section of the course "SQL", and subsection "SQL-Relationships", as well as any demos you think would helpful to me?:


- (upbeat music)
0:04
- [ instructor] So this relationship we just saw between
0:07
the movies table and the studio's table is what's known
0:10
as a one-to-many relationship.
0:13
From the perspective of the studios table, each studio,
0:17
one studio corresponds to potentially many different movies.
0:22
So Walt Disney studios could just have one movie,
0:25
but in this world, in reality,
0:27
they have thousands of movies that have been put out.
0:30
So one studio has many movies.
0:33
On the other side of things, We've flip the perspective.
0:36
Each movie has exactly one studio that put it out.
0:41
Technically, I know that there are joint productions,
0:44
and if we want it to allow for that
0:46
for movie studios to co-produce a movie
0:48
or put one out together,
0:50
our current setup does not allow for that.
0:52
We only have one studio ID.
0:54
We could have two, we could have three,
0:57
but that's something we'll talk about later,
0:58
a many-to-many relationship.
1:00
Most of the time, the vast majority of the time,
1:02
there's one studio that's responsible
1:04
for putting out each film.
1:06
So that's the idea of a one to many relationship.
1:09
Now we need to talk about some important terminology.
1:11
There's a term in CQL called primary key.
1:15
A primary key within a single table
1:18
is a unique identifier for each row.
1:22
So traditionally almost a 100% at time,
1:26
your primary key will be the ID.
1:29
Each ID needs to be unique and that's important,
1:32
especially with our studios table,
1:35
that each idea is unique if we're going to reference
1:38
that ID in a different table.
1:40
If we had multiple studios with the idea of one,
1:44
this would be very confusing.
1:46
So star Wars, the force awakens has a studio idea of one,
1:49
but which studio has that idea?
1:52
There's two studios that's very confusing.
1:55
So a primary key is something
1:56
that is going to be unique for each row
2:00
and the easiest thing to do is just set your ID
2:03
to be the primary key.
2:05
Once we talk about creating tables,
2:07
we'll learn how we can configure a primary key,
2:09
how we can have PostgreSQL automatically increment the ID.
2:13
And create a guaranteed to be unique ID
2:16
and enforce that it is unique.
2:19
So that you can't change an ID to be two
2:22
or you can't change universal pictures ID to be one
2:25
because there already is something with ID of one.
2:28
So a primary key is that unique identifier,
2:31
most often an ID.
2:33
In this movies and studios example, in the movies table,
2:38
we have a studio ID column.
2:41
This is a reference to a primary key from a different table.
2:45
And we usually refer to that as a foreign key.
2:49
A foreign key is a key coming from a foreign table.
2:53
So studio ID coming from the studios table
2:57
is a foreign key in the movies table.
3:00
And we'll talk more about foreign key constraints.
3:03
When we create our own tables,
3:05
when we define a schema for a table.
3:08
What we can do is write some SQL code
3:11
that enforces the fact that studio ID
3:14
must be a real studio ID on the studios table.
3:19
So that I couldn't set a new movie on here
3:21
that had a studio ID of 999, which doesn't exist.
3:26
SQL will actually check, is that a real studio ID?
3:30
And if it's not, then it will give us an error
3:33
and say you can't do that, if it is then everything's great.
3:36
So we'll learn how to actually configure these tables
3:39
and set them up.
3:40
At this point, we haven't done any of that,
3:42
we haven't seen how to make a table,
3:43
we haven't talked about data types,
3:45
and constraints that is coming.
3:48
So again, one-to-many is the type of relationship here
3:51
because one studio has many movies,
3:53
but one movie has exactly one studio in our setup.
3:57
And a little bit more terminology here,
3:59
we could say that movies is the referencing table.
4:02
Movies is referencing studios
4:04
and studios is the referenced table.
4:08
Inside of our studios table there is no reference
4:11
to movies at all, this table exists on its own.
4:14
It does not have any foreign keys in it,
4:17
it's not referencing movies
4:18
or anything else.
4:19
So it is the referenced table in this one example,
4:23
and then the movies table is referencing the studios table.
4:27
So that's a one-to-many relationship in a nutshell,
4:31
there are many one to many relationships.
4:33
For example, if we were making
4:36
a website, a blog, a Reddit clone,
4:38
one user can have many posts.
4:42
If I submit a new post,
4:44
that post is going to be associated with me.
4:46
Most likely, there would be a post table
4:50
that had a user ID foreign key.
4:53
So one user can have many posts,
4:55
but one post has exactly one user who created it.
4:59
Same thing with comments.
5:01
So I can have as many comments to my name as I want
5:05
if I'm prolific I type 50 different comments
5:07
every night they're associated with me,
5:10
but each comment is only associated with one user.
5:14
So I could have hundreds of comments associated with me,
5:17
so user can have many comments, a comment has one user,
5:22
or comments to posts.
5:24
On Reddit, you comment on a particular post
5:26
so that post can have thousands of comments.
5:29
They will be associated somehow probably a post ID
5:33
would be stored on each comment,
5:35
but a comment can only be long
5:37
or be associated with one post.
5:40
So one-to-many are very common.
5:42
There's another relationship that's also common,
5:44
a many-to-many, which we'll take a look at in just a bit.
5:47
But next, let's actually take a look at some real SQL data.
5:51
I'm gonna to give you another seed file
5:53
that you can run, and we'll play around with selecting,
5:56
and inserting and updating columns
5:58
in a one-to-Many relationship.
6:00
So that's next.
6:01
(upbeat music)