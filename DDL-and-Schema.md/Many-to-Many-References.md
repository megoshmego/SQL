thank you. would you include any scripts for demos you think might be helpful? 







will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "Many to Many", and the section of the course "SQL", and subsection "DDL and Schema", as well as any demos you think would helpful to me?:

0:00
(upbeat music)
0:04
- [Instructor] So far, we've been writing tables
0:06
that do have relationships, but right now it's just been
0:09
a one to many relationship.
0:11
Users to comments is one to many.
0:14
A comment has exactly one user or user ID.
0:17
A user can have multiple comments.
0:20
A subreddit has one owner,
0:22
one user ID who created the subreddit,
0:24
but a user can create multiple subreddits.
0:27
But what about many to many's?
0:28
Well, we use the exact same syntax.
0:30
We'll use the example of the roles,
0:33
actors and movies table, tables.
0:36
So here is the potential tables we could create,
0:38
the create table statements.
0:40
We would start with making movies,
0:42
which does not have any references, just an ID,
0:45
which is a primary key title,
0:47
which we're saying is required, not null.
0:50
Release year integer, runtime integer, rating, text,
0:53
all of them required.
0:55
Then we create actors.
0:56
Same thing, no references involved.
0:59
We just have our ID.
1:00
First name text, last name text.
1:03
First date is a date.
1:05
And for some reason we've decided last name is not required.
1:07
Maybe for some of those actors or actresses
1:09
who go by a single name, like a Awkwafina.
1:13
She just goes by Awkwafina.
1:14
And then we have our roles table.
1:17
The roles table is the joining,
1:19
it represents an actor and a movie matched together
1:23
in a particular role.
1:24
So we do have an ID, primary key, serial.
1:28
And then we have movie ID, which is a reference to movies.
1:32
And I've added on delete cascade
1:34
because it really doesn't make sense to store
1:37
anything about a role, if the movie has been removed
1:40
or the actor has been removed,
1:42
because all that a role is, is a movie ID and an actor ID.
1:46
So without a movie ID or without an actor ID,
1:49
we're just storing one ID.
1:51
It doesn't really do anything for us.
1:54
Unlike say a comment on Reddit or a subreddit,
1:57
where if you remove that user ID, you can make it null,
2:01
we still have context, we still have information.
2:04
The actual comment, text a subreddit name or whatever.
2:07
With a role there's really nothing to keep around.
2:10
So we add on delete cascade.
2:12
And if either the movie ID or the actor ID correspond
2:16
to a row that has been deleted from actors or from movies,
2:20
then the entire role, or as many roles as match, that ID,
2:25
will be removed.
2:26
So same stuff, exactly what we've already seen.
2:29
But in this case, we have a third table
2:31
with two different references instead of a single reference
2:35
embedded within the comments table or the subreddits table.
2:39
(upbeat music)
