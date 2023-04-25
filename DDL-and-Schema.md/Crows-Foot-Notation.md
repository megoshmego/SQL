thank you. would you include any scripts for demos you think might be helpful? 







will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "Crow's Foot Notation", and the section of the course "SQL", and subsection "DDL and Schema", as well as any demos you think would helpful to me?:


Transcript


0:00
(slow upbeat music)
0:04
- [Instructor] Next up,
0:05
let's take a break from specific syntax of SQL
0:08
to talk a bit higher level about structuring our databases
0:12
and modeling or planning things out before we begin.
0:16
So with this example of the movies database
0:18
we've already worked with,
0:19
although you didn't have to define the tables,
0:21
I just gave you a file.
0:23
We had a couple different relationships that we identified.
0:26
A studio has many movies.
0:27
An actor has many roles.
0:29
A movie has many actors.
0:30
And if we wanted to include things like directors,
0:33
we'd have to decide, well,
0:35
does a movie have more than one director?
0:38
It's definitely possible.
0:40
And directors definitely have more than one movie
0:42
most of the time.
0:44
So most likely we would have a many-to-many table
0:47
or many-to-many relationship
0:49
with a third join table
0:51
like we did for roles.
0:52
And what would we call that?
0:54
Maybe movie directors or movies directors, directors movies
1:00
or you could say directing job.
1:03
And that would associate potentially multiple directors
1:06
for the single movie.
1:08
Now, when we're planning things out,
1:09
we have a couple of different ways to visualize.
1:11
We could use a spreadsheet
1:12
like I've shown you for the movie's database.
1:15
You can plan something like this,
1:18
where you type out your different columns.
1:20
You could even color code things.
1:22
And this is definitely a nice visual way of organizing
1:26
and planning your structure out.
1:28
But there's also specific diagramming tools
1:30
made for database diagrams for planning out your schema.
1:35
One popular form of notation is called Crow's Foot Notation.
1:39
It's relatively standard.
1:40
I think it's a subset of something called
1:42
ERD, entity relationship diagrams.
1:45
Anyway, it looks like this
1:47
where we have entities like our tables,
1:50
and then we can draw
1:51
and indicate a relationship
1:53
between those tables using a line with the crow's foot.
1:59
And this means we're going from one to many
2:03
or one studio has many movies,
2:07
movies have one studio.
2:10
So this indicates the relationship.
2:12
Here's some more specific details.
2:14
There's a couple for variations on the actual arrows.
2:18
So we have the crow's foot, which indicates multiple.
2:23
And then you can add in this little zero, this circle,
2:27
which indicates zero or more.
2:29
So that could mean something is optional, one or more.
2:34
And then we have a one-to-one relationship
2:36
or zero or one.
2:38
But almost always,
2:39
we'll just be using a standard crow's foot.
2:42
And when you are writing these diagrams,
2:44
there's a bunch of tools out there,
2:46
free and paid with varying degrees of beauty
2:51
and nice interfaces, ease of use.
2:54
And a lot of them require you to sign up,
2:56
which is kind of annoying.
2:57
I'll just show a couple of them.
2:59
There's one called Database Diagram Online.
3:02
This is a specific tool made for databases specifically
3:07
where you can actually draw your diagrams out visually
3:10
and then export to SQL.
3:13
So, a lot of people like these sort of tools.
3:16
We also have things like TablePlus.
3:18
This is really cool.
3:19
it's only for Mac unfortunately.
3:21
Oh no, it's now for windows.
3:23
Nevermind, this is a cool app.
3:24
It is paid.
3:26
So I definitely did not want to include it in the course,
3:28
it's something that's required.
3:30
But it's a really cool interface that allows you to actually
3:33
just interact with your database.
3:35
Visually it works it's for PostgreSQL
3:38
and we can see different databases, tables.
3:41
We can write selections
3:43
and different queries
3:44
and see what's happening.
3:46
Let's see if I can scroll down a bit
3:47
and show an example
3:49
where we can get a visual representation
3:51
of what we'll be selecting.
3:54
You can see it highlighted.
3:56
You can write SQL queries.
3:57
You can write your schema definition
3:59
and it will diagram it for you.
4:01
However, it is paid.
4:04
On the lighter side of things,
4:05
there's a tool called Gliffy
4:07
which is an online diagram maker that is not SQL specific.
4:11
It makes all sorts of diagrams.
4:14
We've also got some older looking tools.
4:17
There's this one called Vertabelo
4:20
which does what a lot of these apps do.
4:23
It allows you to type
4:24
or you can drag and drop
4:26
and manipulate your data visually
4:29
and then export to SQL.
4:32
And let's see one more.
4:34
This is a free one.
4:35
Finally, called Quick Database Diagrams, quick DBD.
4:40
And the potential downside,
4:42
which is also a potential upside for some people
4:45
is that you can't actually edit inline.
4:47
So I can't change these fields.
4:50
I can move things around
4:52
and I can manipulate relationships.
4:54
And I think I can, no, that's just zoom.
4:57
So I can't add a table here either.
4:59
The way that we add new tables
5:01
and we set the particular columns
5:04
is through text on the left-hand side.
5:07
There is a special syntax we use.
5:09
They give you a sample schema.
5:11
If I wanted to add a new table,
5:12
let's just call it a movies table.
5:15
It's not quite SQL.
5:17
it's similar,
5:19
but you'll see that we have,
5:20
let's do movies.
5:21
And then we added dash to indicate we're making
5:24
a movies table.
5:25
And then we need to add a ID.
5:27
We'll just write ID, which is a primary key, serial.
5:33
What else do we have?
5:35
Name, how about title?
5:37
Which will be text.
5:39
And other than that,
5:41
a movie will also have a rating which will be text as well.
5:46
So now we've made our table in this diagram tool.
5:49
And if we want to associate it
5:50
with some other table,
5:52
let's creates a studios table,
5:57
which will have an ID
5:58
and a studio name.
6:01
Let's just go with name, which is text.
6:06
We now have two different tables.
6:07
They are not associated in any way.
6:09
So I have a text interface to add an association,
6:13
or I can just click and drag.
6:16
So one studio can have multiple movies.
6:20
So what I'm going to do is add
6:21
a field into movies called studio_id
6:26
and then I'm gonna take this studio_id
6:28
and I can just click
6:29
and drag over to my ID on the studio table.
6:32
I did not do that correctly.
6:36
There we go.
6:37
And now we have our relationship diagrammed here.
6:39
So ignore all this other stuff.
6:42
We have studios, which corresponds to multiple movies.
6:45
A studio can have multiple movies,
6:47
but each movie has one studio.
6:49
And that's what that bar means.
6:51
Indicates a one relationship.
6:53
So we have one-to-many.
6:55
So the syntax again is not fully SQL.
6:58
We don't have comments. We don't have create table.
7:00
We don't have parentheses.
7:01
We can drag,
7:03
at least the relationships we can drag to create,
7:06
but what we can do is export
7:08
and we can choose PostgreSQL.
7:10
Hopefully it doesn't make me sign up to export
7:12
and let's see what we end up with.
7:14
Check it out.
7:15
We've got our valid SQL
7:17
that we could then just take and run.
7:20
It also includes a bunch of stuff we didn't create.
7:22
Customer, Orderline.
7:25
But we do have movies
7:26
and we do have studios
7:28
and we've got create tables.
7:29
We've got the commas in there.
7:30
We've got not null which is the default.
7:33
I think we can also specify null is okay.
7:37
But really the point here
7:38
is that there's a ton of tools out there
7:39
and it often helps to diagram your schema out
7:41
ahead of time, especially for complicated things.
7:44
Just as an example,
7:46
here is a potential schema for a discussion forum.
7:50
So we've got quite a few tables.
7:52
It's not that many,
7:53
but this is just a portion let's say of Reddit.
7:56
Reddit might have a hundred different tables.
7:59
Plus then you add in tables for tracking all sorts of user
8:01
data about clicks and ads
8:04
and what ads they have
8:05
and haven't seen
8:06
and user information that you're storing about their age
8:09
and whatever other data you can buy from other websites.
8:13
Just the reality of being a large web company these days,
8:17
it has a free product.
8:18
They're gonna have tons and tons of tables,
8:20
lots of relationships.
8:22
So, planning it out ahead of time makes a big difference.
8:25
Otherwise, if you just start with something,
8:28
just start with your forum table.
8:30
You're going to realize as you're going,
8:32
you need a lot more tables.
8:34
You need to update.
8:35
You'll need to alter those tables.
8:37
And that's fine if you're in development.
8:38
Obviously we will be changing things as we go.
8:42
It's part of the development process,
8:44
but it's always best to spend some time.
8:46
You don't have to go insane
8:48
and get it perfect.
8:49
But spend some time before you begin writing any code
8:51
before you write any create tables, just to get
8:54
some general idea of where you're going.
8:58
So this website, by the way, I think you have to buy these.
9:01
I'm not even sure.
9:02
They include schemas that you can view.
9:05
Let's say here's a survey website
9:08
or a survey data model.
9:09
So we've got a response, different types of questions,
9:12
single choice, multiple choice, data response,
9:15
text response, numeric response, yes or no questions,
9:18
choice, person, survey.
9:20
All of these are connected and look at all of these
9:22
different relationships, quite a lot going on.
9:26
So I definitely recommend you take time.
9:28
You diagram things out.
9:30
You will get some practice with this,
9:31
both through exercises,
9:33
but also on your first larger projects.
9:35
When you are working with the database,
9:37
you'll probably have a bunch of tables
9:40
and you'll need to figure out those relationships
9:42
and crow's foot notation
9:43
is one tool that you can use to help you.
9:45
You could also just whiteboard it out,
9:47
draw it on a piece of paper.
9:49
Could do a spreadsheet, whatever you feel comfortable with.
9:52
(upbeat music)
