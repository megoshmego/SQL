thank you. would you include any scripts for demos you think might be helpful? 







will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "Deletion Behavior", and the section of the course "SQL", and subsection "DDL and Schema", as well as any demos you think would helpful to me?:


anscript


0:00
(upbeat music)
0:04
- [Instructor] Next up, let's talk about deletion behavior
0:06
when we have references within a given table.
0:10
So currently, we have our users table,
0:13
and we have the subreddits table that has a reference
0:15
to a particular user ID.
0:18
And this ID, user ID must be a valid user ID
0:22
in the users table.
0:23
So if I were to delete one of those users,
0:27
right now, I think we have two subreddits,
0:29
they're both stupid subreddits.
0:32
But I shouldn't say stupid, chickens and waterluvers,
0:34
great subreddits, but we're missing some fields here.
0:38
We have a user ID of let's go with this user ID of two,
0:41
for this first subreddit.
0:43
So it was created by whatever user has said ID,
0:46
select star from users.
0:49
User ID of two is Stevie-chicks.
0:51
If I try and delete Stevie-chicks, delete from users where
0:57
ID equals two,
1:00
I get an error.
1:01
Update or delete on table users
1:03
violates foreign key constraint.
1:05
Key of ID equals two is still referenced
1:08
from the table subreddits.
1:10
So it's telling me I cannot delete this user,
1:13
because other tables have entries that depend
1:16
on that user information, specifically, the ID of two.
1:20
So if I were to somehow delete this,
1:23
all of a sudden, this becomes invalid.
1:26
We have that constraint on user ID that says
1:28
it must be a real user ID found in the users table.
1:32
So if it's no longer found, what is supposed to happen?
1:35
Well, we have a couple of approaches.
1:37
The first option is to add this on delete set null,
1:41
which allows us to delete the user and then replace
1:44
or update user ID with null.
1:47
We can also set it to something else, I guess,
1:49
but null is pretty standard.
1:51
We would do this in situations where we want to be able
1:54
to sever that tie,
1:56
and we want to still have our subreddit exist.
1:59
Now subreddit is kind of a difficult example.
2:02
I don't know what Reddit actually does,
2:04
if I create a subreddit, and then my account disappears.
2:08
I'm pretty sure that the subreddit continues to exist.
2:12
Especially because as a subreddit grows,
2:15
you have different owners or multiple owners, I think.
2:19
Who knows?
2:20
But let's say that that's a behavior we want.
2:22
We don't want to remove the entire subreddit
2:24
just because the original creator has left
2:28
or has been removed.
2:30
So we can add this on delete set null,
2:33
where we have our references, on delete set null.
2:40
Now there is a problem that we'll run into,
2:43
if we do on delete set null,
2:45
and we have not null as a constraint.
2:48
The delete will be attempted, the user will be deleted,
2:52
but then this on delete set null will kick in,
2:54
and it will attempt to set user ID to null,
2:57
but it can't be null.
2:59
So we'll get an error.
3:01
So we can remove not null.
3:03
And that would make sense if we want this behavior
3:06
where we can have no user ID,
3:08
the connection can be severed.
3:11
Also, I've reordered my tables so I can run this file,
3:15
because we need to define users first
3:17
in order to then reference users.
3:19
Otherwise, we'll get an error saying table users
3:22
or relation users is not defined
3:24
if we try and make subreddits first.
3:26
So I'll run this file PSQL,
3:29
and then I think it's called Reddit dot pgsql,
3:33
creates, first drops my existing database,
3:35
creates the new one, connects, makes two tables,
3:38
insert some stuff.
3:40
Now let's open it up, connect to Reddit db.
3:44
And just make sure it worked.
3:45
Select star from users
3:49
and select star from subreddits.
3:52
Okay, so let's delete the user Stevie-chicks with ID of two.
3:57
She is responsible for creating or being associated
4:00
with this subreddit, the chicken subreddit,
4:04
one subscriber user ID of two.
4:06
So let's delete from users
4:10
where ID equals two.
4:13
And this time, it looks like it worked.
4:15
If we run again, the Select star from users,
4:19
we now only have one user.
4:20
And select star from subreddits,
4:22
we still have our chicken subreddit,
4:24
but now there is no user ID.
4:27
Again, this is one option.
4:28
The other option is known as on delete cascade.
4:32
And this will cause the referencing row to also be deleted.
4:37
So one example I guess would be a post or a comment.
4:41
If we wanted that comment to just completely be deleted
4:45
if a user is deleted, we could do that using
4:49
on delete cascade.
4:51
Now I think technically on Reddit, you can have comments.
4:55
Once the user has been deleted
4:56
it just says deleted user ID or deleted username
5:00
or something.
5:01
But a lot of the times a lot of websites like Facebook,
5:04
for example, if you have a bunch of posts and comments
5:06
and your account is removed, those are gone,
5:09
they're not going to show up.
5:10
Now I'm pretty sure they still store all of that
5:12
they probably don't delete it,
5:13
they just don't show it on the webpage,
5:15
because Facebook wants to keep all that stuff.
5:18
And I think you can reactivate it any time but who knows?
5:21
Let's just go with a simple example of comments.
5:23
And we're gonna have a very, very simple comments table.
5:28
Our comments table will have an ID, serial,
5:34
primary key for each comment,
5:37
then we'll have the user ID of the person who created it,
5:41
the user who created it, which will also be an integer,
5:46
references users, and then we'll set on delete cascade.
5:51
And then we'll also add comment text,
5:54
let's just go with comment text, which will be text.
5:59
And we'll make that not null.
6:02
Alrighty, so let's run this SQL file again.
6:05
Add my semicolon in there.
6:07
So I'm gonna quit out of here.
6:10
Run that file.
6:12
And we'll open up psql, connect to Reddit db.
6:18
And then let's insert into our comments table,
6:23
a couple of comments, so insert into comments,
6:29
where we have, what do we need?
6:31
A user ID
6:33
and a comment text
6:38
values.
6:40
And we have two users at this point
6:42
because we just recreated all of this.
6:44
So the deleted user is now back.
6:47
We've got graylady and Stevie-chicks.
6:49
Let's say Stevie-chicks posts, cluck, cluck.
6:54
And what else?
6:57
Let's do one more.
6:59
Stevie-chicks also says bock bock.
7:03
And then graylady says something else.
7:08
Okay, so we hit enter here, we now have our comments,
7:11
select star from comments.
7:14
Three comments, each one has a user ID.
7:17
Now if I delete a user with the user ID of two,
7:20
so delete from users where ID
7:25
equals two.
7:27
Now we see we got one user that was deleted.
7:30
So select star from users,
7:32
we should only see one left, graylady.
7:34
And if we do select star from comments,
7:39
those two comments that had user ID of two
7:42
have now been removed, they are gone.
7:45
So that is the cascade behavior.
7:47
When the referencing table or the referencing column
7:51
has been removed, so user ID references users dot ID.
7:56
When a user with a particular ID has been removed,
7:59
any referencing comments in our case
8:02
will also be completely removed,
8:05
versus what we had with subreddits,
8:06
where we would set the user ID to null,
8:09
two different behaviors, two different approaches
8:11
depending on the needs of your application
8:14
and the type of data you're storing.
8:16
Do you want something to be thrown out when a user is gone?
8:19
Or do you want to just have it remain
8:21
and maybe give it a new value, and maybe null
8:24
or some other value?
8:26
It's totally up to you.
8:27
But now we've seen that it's a thing we can do.
8:29
We've got delete on cascade or on delete cascade
8:32
and on delete set null.
8:34
(upbeat music)
