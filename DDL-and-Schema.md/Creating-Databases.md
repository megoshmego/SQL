thank you. would you include any scripts for demos you think might be helpful? 






will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "Creating Databases", and the section of the course "SQL", and subsection "DDL and Schema", as well as any demos you think would helpful to me?:


nscript


0:00
(upbeat music)
0:04
- All ready.
0:05
Next step we're going to talk about DDL in SQL.
0:09
DDL stands for Data, Definition, Language,
0:12
everything we've been doing so far
0:13
has been under the umbrella of DML,
0:16
Data Modification Language.
0:18
I really hate those two acronyms, but you will hear them.
0:21
We've been working with tables that are pre-existing, right?
0:25
We've been running files like this movies.sql file.
0:28
It makes the database, it makes the tables for us.
0:31
We haven't actually created tables
0:33
and defined schemas from scratch.
0:36
We've only been working within existing tables.
0:39
We've been inserting, we've been deleting, updating,
0:42
and reading, or selecting information,
0:45
basic crud that all falls under DML or modifying data.
0:50
Next, we will learn how to define our own tables.
0:54
So we've a couple basic goals.
0:56
First, we wanna learn how to Create, Update
0:58
and Remove Databases and Tables.
1:01
So how do we make a new table? How do we modify a table?
1:04
Like adding in a another column
1:07
after the table has been created
1:09
and maybe it already has data in it.
1:11
What about removing databases and removing tables?
1:14
We'll talk a little bit about Basic Schema Design
1:17
as well as how to Properly Model Relational Data.
1:21
So we're gonna start
1:22
with the basics of working with databases.
1:25
We've seen how to create databases through the command line.
1:30
If I get out of PSQL or Postgres,
1:34
we've seen this before,
1:36
I can create a database with this createdb,
1:40
and I'll just call this, delete_me.
1:44
That makes us a database.
1:46
If I then open up PSQL and I list my databases,
1:50
\l I can see delete_me right here.
1:55
The other way of creating a database from within Postgres,
1:58
when I'm already inside of the Postgres terminal
2:01
or the shell, I can run, create database,
2:04
just like I would do a select from or insert into,
2:09
and then some database name. So create database.
2:13
Once again, capitalization doesn't actually matter,
2:15
but it's best to put our SQL keywords in all caps.
2:18
It's conventional, kitty_toys_db.
2:23
Oop, forgot my semi-colon and that makes us a database.
2:28
We can see it here, kitty_toys_db.
2:30
It doesn't have any tables.
2:32
We haven't added any information.
2:34
We can also drop a database,
2:36
just like we have the dropdb command,
2:39
which we can run from our bash shell.
2:41
When we're inside of SQL, we can run drop space database,
2:46
so drop database, and then let's do delete_me;
2:51
It has nothing in it.
2:53
Now it's gone. I'll also do kitty_toys_db;
2:59
And now we look at \L we don't have those databases.
3:03
We just removed two relatively straightforward.
3:07
And remember when you drop a database, it is gone.
3:11
So we can't easily. We can't undo it.
3:13
There's no command.
3:14
See here that empty database in this case delete_me
3:17
as well as kitty_toys_db.
3:19
We don't really miss them. There wasn't anything in them,
3:22
but if I were to delete my movies database
3:24
or the movies example, actually,
3:26
that's what we were working in a relatively recently,
3:29
all of those tables, all of those records are gone.
3:32
Early on, we saw how we can create a backup.
3:35
So that is one option for creating a backup.
3:38
But in general, you're not gonna be dropping databases
3:41
all that often, at least not manually in your command line
3:45
or in the SQL Postgres shell,
3:48
you will be dropping databases relatively frequently
3:51
when you are testing your applications,
3:54
when you are seeding a database,
3:56
when you're developing an app, for example,
3:59
this movies.SQL file that you ran earlier
4:02
in order to get our movies tables
4:04
and some starter data begins with a drop database.
4:08
We're cleaning the slate,
4:10
removing any existing movies and getting rid
4:12
of that database if it exists.
4:14
So we can also do drop database if exists, movies_example;
4:19
And then we create that database.
4:21
And we only do this in this scenario
4:23
where if we want to wipe the slate, clean, start over
4:26
and get fresh data, fresh tables.
4:28
We don't have to worry about whatever was in there before,
4:31
but you wouldn't do this in a real application.
4:34
Once it's in production, you have user data in there.
4:36
You don't wanna be dropping a database.
4:39
We've also seen the command \c,
4:43
which we can use to connect to a database.
4:45
So to connect to my, let's do the movies_example
4:49
that we've been working in \c movies_example.
4:54
Now my prompts changes,
4:56
and I am connected to that one database in particular.
4:59
I could change and go to how about books_db
5:03
or how about library?
5:05
Once again, the prompt changes
5:07
I'm now connected to that particular database.
5:10
And we have a command called \d well,
5:13
it's not called this, but \dt,
5:16
which will show us the tables in our database.
5:19
So right now I have books and employees
5:21
in this one database.
5:23
If I instead connect to a movies_example,
5:28
/dt I get those four tables we've seen before.
5:31
Actors, movies, roles, and studios.
5:34
And we've also seen this in passing \d or \d+
5:40
and then a name of a table in your current database.
5:44
So if I want more information about actors,
5:46
I can do \d actors.
5:48
And it tells me the different columns.
5:50
So ID first name, last name, birth date, the indexes,
5:55
something we haven't considered,
5:56
we haven't talked about it at all, but we will.
5:58
And then any foreign key constraints,
6:00
and then any references involving this table,
6:03
there's also \d+ ,
6:06
which gives us a little bit more information.
6:09
Can see we get this storage column stats,
6:11
target and description,
6:13
but we also get a huge overlap in the information
6:16
that is displayed here.
6:17
So I only am able to run this command
6:20
with the tables in my current database.
6:23
So I don't have, you know, the books table in this database.
6:27
If I tried to access it and read more about it,
6:30
it won't be found because I'm connected
6:31
to my movies_example database.
6:34
And if we look at one of these seed files i've given you,
6:38
it starts off by dropping the database if it exists,
6:41
and it creates a new database with the same name,
6:44
then it connects to it.
6:45
So when we create and drop databases,
6:49
we do not have to be connected to them.
6:51
But if we want to create tables or insert data
6:54
or do anything with our actual information in that database,
6:58
we do need to connect first.
7:00
So if you're trying to write a seed file
7:02
or a file just to create your database,
7:05
maybe for exercises or demos,
7:07
you'll want to create your database
7:09
and then \c, connect to it. Okay.
7:14
Next, we've got a lot to talk about around creating tables.
7:18
This is the meat of this section.
7:20
Very important stuff that we are currently missing.
7:22
We need to be able to make tables.
7:24
(upbeat music)
