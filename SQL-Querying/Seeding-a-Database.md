thank you. would you include any scripts for demos you think might be helpful? 







will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "Seeding a Databases", and the section of the course "SQL", and subsection "SQL-Querying", as well as any demos you think would helpful to me?:

0:00
(upbeat music)
0:04
- [Tutor] All right.
0:05
So before we dive into the syntax of Select,
0:07
we need to make sure that we're all on the same page here.
0:09
We'll be using the same database,
0:11
with the same initial seed data.
0:13
So download this file,
0:15
which is called library.sql.
0:18
These other two,
0:19
I created in previous videos,
0:21
you don't need those.
0:22
Library.sql contains all of this information here.
0:25
These are SQL commands.
0:27
It will create a new database.
0:29
First it checks to see
0:30
if there is a database called library.
0:32
It will deleted if there is,
0:34
and then it remakes a new empty database called library.
0:38
So every time I run this,
0:39
it will check to see if there is database, drop it.
0:42
If it exists, recreate it.
0:44
And then we change into it.
0:46
We connect to library.
0:48
You can kind of think of this is like seeding
0:50
into that database,
0:51
but that's not quite what happens.
0:53
It creates a table and it inserts a bunch of books.
0:56
So we'll run this,
0:58
and the way we do this,
0:59
we saw previously psql and then our less than sign
1:04
library.sql.
1:07
We need to make sure we're in the directory,
1:09
where this file is,
1:10
or you referenced the correct path to that file.
1:13
Again, you can download this along with the handouts,
1:16
make sure that you have this.
1:17
And if you are using the Postgres app,
1:20
I can see that I don't have a library database,
1:24
but now I should.
1:25
And I do, here it is.
1:27
So now I can open up psql with that library database,
1:32
and I'm connected to it.
1:34
And if I type something like \dt,
1:37
which we saw earlier,
1:38
this lists the tables in this database.
1:40
We have books and we have employees.
1:42
We did not create those manually.
1:44
We didn't type anything.
1:45
As far as the creating the tables,
1:48
we just ran a file that did it all for us.
1:50
And then you could also connect if you wanted to, this way.
1:54
Open up psql and then \c library.
1:58
And now we're good to go.
1:59
So whichever option you prefer,
2:01
I generally think it's easiest to do this.
2:03
Just psql library.
2:05
We want to connect to the database,
2:07
make sure your prompt
2:08
says library=#
2:09
and that when you run \dt,
2:11
we see those two tables.
2:13
And now we're in a place
2:14
where we can start writing Selects.
2:16
We can start writing SQL queries,
2:18
that are going to connect to this information.
2:21
There is data in that book's table.
2:24
So how do we get it out?
2:25
That's what we'll see next.
2:26
(upbeat music)