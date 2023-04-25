thank you. would you include any scripts for demos you think might be helpful? 







will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "Updating", and the section of the course "SQL", and subsection "SQL-Querying", as well as any demos you think would helpful to me?:





0:00
(upbeat music)
0:04
- [Narrator] All right, so that's inserting,
0:05
it's relatively straight forward.
0:07
We're usually not going to add any logic in here.
0:10
We're just inserting data straight up.
0:12
Next we have updating existing rows
0:15
and this can be a little more complex
0:17
because we can narrow down specific rows
0:19
that we want to update.
0:21
We're usually not going to update every single book,
0:23
but we could if we just ran UPDATE books
0:27
and then SET some column equal to something.
0:31
I could make every book,
0:32
let's say I want to make every book free.
0:34
I could do UPDATE.
0:37
And then the next piece of syntax is the table
0:40
and then SET and then some field or column.
0:43
So UPDATE books, SET price equals zero.
0:49
And here we go.
0:51
Now, let's do a SELECT price from books.
0:56
Every single price is zero.
0:58
So usually we don't want to do that.
1:00
Maybe there's a situation where you want
1:02
to mass update every single row,
1:05
but most often we will specify where we want to update.
1:09
Let's live out my fantasy,
1:11
where I actually wrote all the Harry Potter books.
1:14
So what I could do is update all
1:16
the books where author is J.K. Rowling.
1:19
So UPDATE books,
1:23
SET author to now be Colt Steele,
1:29
but I only want to do it where author is currently
1:35
J space K space Rowling like that.
1:42
And it tells us here updated seven.
1:45
Earlier, when I ran the mass update, we got 47.
1:49
Now, if I select let's just do ID and title from books.
1:57
I guess we can just do all of them.
1:59
And eventually I'll find those ones, oh, you know what?
2:02
I need to print out author as well.
2:04
So ID, title, author from books.
2:09
Eventually we'll see the books that I wrote
2:13
that used to be written by J K Rowling.
2:15
So here we go, "Harry Potter and the Sorcerer's Stone,"
2:17
"Harry Potter and the Chamber of Secrets,"
2:19
"Harry Potter, and the Prisoner of Askaban."
2:20
All of those books are now written by me.
2:24
So we can also add on other operators,
2:27
so things like, I want to update books.
2:30
How about we update the author to be Colt Steele also,
2:36
where currently ID
2:41
is in one, three or five.
2:46
And now if I select all of my books,
2:49
let's just do where ID
2:53
is in one, three and five as well.
2:58
We can see they've all been written by me.
3:00
I guess I'm a bit selfish here,
3:01
but it's a simple update to make changing the author
3:06
and that's kind of it to doing updates.
3:08
So you can update everything.
3:10
We use the keyword UPDATE and then SET.
3:13
And then we also can get more specific on what we update,
3:16
which we usually do.
3:18
Often we'll be updating something based off of an ID.
3:21
So in Flask we'll have some URL
3:24
like slash comments slash 20,
3:27
and we'll use that ID, the 20, to update
3:30
some comment in our database.
3:32
So we'll make sure we're only updating where ID equals 20,
3:36
and then we'll do something depending on what a user entered
3:38
into the update form.
3:40
And that's UPDATE.
3:41
Next step We have one last basic CRUD operation delete.
3:46
(upbeat music)