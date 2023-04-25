thank you. would you include any scripts for demos you think might be helpful? 






will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "ALTER TABLE", and the section of the course "SQLA", and subsection "DDL and Schema", as well as any demos you think would helpful to me?:




(upbeat music)
0:04
- [Instructor] Next up, we'll talk about
0:05
a command called alter table.
0:08
Alter table allows us to add columns, remove columns,
0:11
rename columns.
0:13
We can also add and remove and change constraints
0:16
or even data types,
0:18
although it's kind of uncommon to change data type,
0:20
but we can.
0:21
So once a table has been created,
0:23
and if we wanted to drop some column,
0:26
we could do alter table, then the name of the table,
0:30
and then the specific command
0:32
that we want to do to alter that table,
0:34
like drop column, and then the name of a column.
0:38
So right now, let's see, we've got subreddits,
0:40
select star from subreddits.
0:45
We could drop description.
0:47
So, alter table
0:51
subreddits drop, not droop, drop column
0:57
and then name of the column is description.
1:01
Description.
1:01
There we go.
1:03
Now if we select star from subreddits, it's gone.
1:07
What about if we try and drop a column
1:09
that has information in it, description was empty,
1:12
what if we drop alter table
1:14
subreddits drop column
1:16
and then is private maybe?
1:21
What happens?
1:22
Hmm, looks like it still works.
1:24
So this is definitely something to be conscientious of.
1:27
If we delete columns that do have information in them,
1:30
that data is gone.
1:31
It's not gonna warn us and say are you sure
1:33
you wanna delete that, there are rows that have values
1:36
for is private, it's just gone.
1:39
So we can also rename things.
1:41
Rename column instead of drop column.
1:44
And then we specify the column as it currently is named,
1:47
to, and then the new name.
1:50
So I have the user ID.
1:52
I could rename that to be owner.
1:55
So, alter, table, subreddits,
2:00
and then rename column user ID to owner, or owner ID.
2:10
Now, you look at subreddits and it's now
2:12
owner ID, it's not user ID.
2:15
We also can add a column.
2:17
What would I want to add to a subreddit?
2:19
How bout, actually let's do this to users.
2:24
Select, star, from users.
2:27
We've got username and password.
2:29
Let's also add in
2:33
is admin, sure.
2:35
We'll add in a field called is admin, a column.
2:38
And to make a column, we don't just specify the name,
2:41
but of course we also have to specify a type.
2:44
So is admin makes sense for it to be a Boolean,
2:47
so let's do that.
2:48
Let's do alter, table, and then the name
2:52
of the table is users, add column,
2:56
and then the name will be is admin,
3:00
or actually let's do permissions.
3:04
And instead of a Boolean, we'll have admin
3:07
mod and user, we'll just have some string there,
3:11
so we'll do text permissions.
3:13
And then we specify afterwards the data type like text.
3:19
Now if we look at users,
3:20
just rerun this command,
3:23
we now have permissions.
3:24
But what about the existing users in this case,
3:28
where we don't have a value for permissions?
3:31
Well, if I delete permissions,
3:33
so I'll just alter table, users,
3:36
and then drop column permissions,
3:42
and then remake it and after text
3:45
I add a default, I'll do default,
3:47
let's do mod, or mod, yeah mod or moderator.
3:52
Although that's probably not a good default.
3:55
We probably wanna default our permissions
3:57
for all users to be none or just standard user permissions.
4:01
But here we can add a default,
4:03
and now if we look at our users table,
4:06
moderator is the default.
4:09
So we have other things we can do within alter table.
4:12
If we look at the syntax here, there's quite a bit.
4:16
There's a lot to try and understand.
4:19
The basics are we've got rename a column,
4:22
set schema, we can add constraints,
4:25
we can drop constraints,
4:26
so if I wanna make something nullable,
4:28
I can drop the not null.
4:31
We can do other things like set the data type.
4:35
Further down there are some examples down at the end.
4:39
So we could change an integrate column to be a float column,
4:42
or we can add a column as we've already see.
4:45
Drop columns, we can change multiple types
4:48
of columns at once,
4:50
so we can have multiple alter columns.
4:53
There's a bunch of things we can do.
4:55
Honestly, you're probably not going to be altering
4:57
columns all that often.
4:59
It's pretty uncommon that you would need
5:01
to make a severe adjustment
5:03
where you're just dropping something entirely
5:05
or adding something in.
5:07
It's definitely not unheard of,
5:08
but usually you wanna plan out your database
5:11
and your columns ahead of time.
5:13
Obviously, things will change
5:15
and there are situations you can't
5:17
anticipate from the get go,
5:19
which is why we have alter table.
5:21
And that's it, alter table
5:23
and then some commands like add column,
5:25
drop column, rename column,
5:27
alter column, a lot of different things.
5:31
(upbeat music)
