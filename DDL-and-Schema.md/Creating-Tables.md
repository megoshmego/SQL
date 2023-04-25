
thank you. would you include any scripts for demos you think might be helpful? 






will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "Creating Tables", and the section of the course "SQL", and subsection "DDL and Schema", as well as any demos you think would helpful to me?:


0:00
(upbeat music)
0:04
- All right.
0:05
Next we're going to learn how to create tables.
0:08
So to create a table in SQL, it's relatively easy.
0:12
We use the syntax create, space, table.
0:15
And then the name of the table we want to create.
0:18
Usually that name is pluralized.
0:20
So books instead of book.
0:22
Although it actually doesn't matter.
0:24
It's really just semantics, but it makes more sense.
0:27
Because we are storing multiple books in this table.
0:30
It is a collection of some, something.
0:32
Some data that we're storing.
0:34
Then within parentheses, we specify kind of key value pairs
0:40
between a column name and then a data type.
0:44
And we have different data types
0:45
that we will talk more about in a separate video.
0:48
So for now, we'll work with text.
0:51
Which is kind of what it sounds like.
0:53
It's text information inside of quotes.
0:56
So I'm gonna make my table.
0:58
My first table, in a standalone file.
1:00
Usually we're not going to be typing create state,
1:03
create table statements into our terminal
1:06
because it's something you really only do once per table.
1:10
We're not going to create a table,
1:11
and then create the same table again.
1:14
Usually you set up your, your schema.
1:16
You set your tables early, and then you add data in.
1:19
So it's pretty common to define your tables in a file.
1:23
So I'm gonna make a new file here.
1:26
And why don't we work with Reddit like data.
1:31
It won't actually be a full clone of Reddit's database,
1:34
but it will be a Reddit like website.
1:36
And we can name our file dot SQL.
1:38
That is totally valid if we run it in Postgres.
1:41
However, I prefer to use PG SQL.
1:43
Postgres SQL, as our file extension.
1:47
Because in VS code, there is an extension you can get.
1:50
Postgres right here is called PostgresSql.
1:54
And it just gives us some colorization,
1:56
some snippets, some auto-complete
1:58
and it just makes our files generally easier to read.
2:01
So if I create my first table in here, create table.
2:07
We'll go with posts.
2:10
And we'll start very simple.
2:11
Our post table will have a title for each post.
2:15
And we're just gonna work with text for now.
2:17
So title is text, username of the person who created it.
2:21
Will be text, and what else should we have for a post?
2:26
How about a link?
2:28
So on Reddit, you can include links.
2:31
Link will also be text.
2:34
And if I say save first of all.
2:36
I don't like the formatting we get in a regular SQL file.
2:40
And the syntax highlighting, it's not that bad here.
2:43
It looks kind of normal.
2:44
But if I change this to be a dot PGSQL. PGSQL.
2:53
Down here, it detects
2:54
that I'm working in Postgres specifically.
2:57
And I now get some nicer syntax highlighting if I save.
3:00
So I can format it all weird on one line.
3:03
So I prefer to do that.
3:04
But that really doesn't impact the actual code.
3:07
It's still just creates a table.
3:09
It's basic SQL.
3:11
So if I run this right now,
3:13
and to keep things simple, I'm just gonna copy and paste.
3:15
Even though usually we would just run this file
3:17
and we've already seen how to run a file.
3:20
So if I create a database.
3:22
I'll call this one, Reddit DB.
3:25
Then I will connect to it.
3:29
I'm now connected to it.
3:30
We have no tables in here.
3:33
Let's run our code to create our first table.
3:34
I'm just gonna paste it in right there.
3:36
Add my semi-colon.
3:38
And it says, created a table.
3:40
Now we have one relation.
3:41
We have a table called posts.
3:44
And just like any other table we've worked with,
3:46
I can insert into posts and then we'll do our values.
3:54
Nope, not our values.
3:56
We need to specify what we're inserting.
3:58
How about title first, then username, then link.
4:05
And this should be all recap at this point.
4:07
We've seen this before.
4:09
Our post title will be LOL, look at my dog.
4:14
The username will be, dog lover.
4:19
And the link will just be some fake link, like that.
4:25
Now we can run a select star from posts.
4:29
And we've inserted our first row into this table
4:31
that we just created.
4:33
So we'll learn a lot more about these different data types
4:36
and what a primary key is.
4:38
Different constraints.
4:40
We can add on to each column when we define a table.
4:43
But for now, we've seen we can create a table.
4:46
The other thing I'll show you is that we can drop a table
4:48
with drop space table and the name of that table.
4:52
So drop table posts.
4:56
And now if I try and select star from posts,
4:58
it doesn't exist.
4:59
We run backslash D there are no tables
5:02
in our Reddit DB anymore.
5:04
Okay. So that's a taste of creating a table.
5:07
We still have a lot to talk about.
5:08
(upbeat music)
