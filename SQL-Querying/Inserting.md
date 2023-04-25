thank you. would you include any scripts for demos you think might be helpful? 







will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "Inserting", and the section of the course "SQL", and subsection "SQL-Querying", as well as any demos you think would helpful to me?:

(bright music)
0:04
- [Instructor] All right, so we spent a while
0:06
talking about selecting and all the different modifications
0:09
and the logical operators and functions we can use
0:12
to enhance our selections.
0:14
Fortunately for us, doing other things
0:17
like inserting or updating or removing is generally easier.
0:22
So we're gonna start with inserting new elements,
0:25
new rows into our tables.
0:27
We use the INSERT INTO keywords,
0:30
and then a table.
0:32
And then we need to specify
0:33
which particular columns we're going to add
0:36
or specify and in what order.
0:39
And then we add this VALUES keyword
0:42
and then the actual data.
0:43
So whatever this order is here
0:45
dictates which will be the title,
0:47
which will be the author.
0:49
If I swap these, this would be author, this would be title.
0:53
So we can try a basic insert.
0:56
Let's INSERT INTO books.
1:01
And then we need to specify
1:02
that we're going to add title and author
1:06
and maybe price for now.
1:09
And then values, and then our title will be,
1:13
how about Dogs Book?
1:18
And the author will be me and the price will be 19.99.
1:26
Now, if we do a SELECT * FROM books,
1:31
I guess that's gonna be quite a lot to read.
1:34
I probably should have just been a bit more specific
1:37
in that selection.
1:38
Let me get out of there and do SELECT * FROM books,
1:41
how about ORDER BY id DESC.
1:47
And here we go.
1:48
Dogs Book, title.
1:50
Author is called Steele, price, 19.99.
1:53
Notice that all the other columns are empty except for id.
1:59
So in SQL in general, it's pretty rare
2:02
to specify an id when you're inserting something.
2:05
If we take a look at our table,
2:07
we can get more information about it with \d
2:10
and then the name of a table like books.
2:13
You'll see under this default right here,
2:15
default is going to specify the default value
2:19
for each column if we don't pass something in.
2:21
So title, author, price,
2:23
all these columns do not have a default value, but id does.
2:27
It has this thing called nextval.
2:30
So it's going to automatically generate the next valid id
2:34
and put it in there for us.
2:35
So we don't set the id.
2:37
Now we'll learn how we configure this later on
2:40
when we talk about creating tables
2:42
and schemas and data types,
2:44
but for now just know that we didn't specify an id
2:47
and it worked.
2:48
It's still created us one.
2:49
But those other columns are just left blank.
2:52
We'll also learn how to make things required
2:54
so that we get an error if we do leave something blank.
2:58
We can also insert multiple books at once
3:01
using the same syntax, INSERT INTO some table name,
3:05
and then the format,
3:07
the order of things that will pass in.
3:09
So in this case, just title, VALUES.
3:13
And then we can separate our individual books,
3:16
our rows with commas.
3:19
So I could add onto this example, INSERT INTO books.
3:23
Let's just do title and author for now, VALUES.
3:28
And I could just hit enter
3:30
if I want to make my life a little bit easier.
3:32
Generally, typing these inserts into your terminal like this
3:36
is just not very fun.
3:38
We'll often write these in a separate file
3:40
and then run that file.
3:42
But for now, we'll just do it here.
3:43
So INSERT INTO books, title, author.
3:45
Let's come up with some titles.
3:46
How about chicken book.
3:49
That's written also by me.
3:53
And then after that, we'll have,
3:57
how about animals are cool written by Darwin.
4:09
And then one more book title.
4:11
How about learn to knit written by my grandma.
4:19
Semi-colon to tell SQL we are actually done.
4:23
And now if we do the same thing
4:25
where we select all, SELECT * FROM books,
4:28
but we'll ORDER BY id DESC.
4:31
We can now see most recently.
4:33
We have id of 44, learn to knit,
4:35
43 animals are cool, 42 chicken book.
4:39
It's a great one.
4:40
And then our earlier book, 41 Dogs Book.
4:43
And that's kind of it for inserting.
4:46
So the syntax is INSERT INTO some table.
4:49
And then inside of those parentheses,
4:51
we will specify the order of the columns
4:54
that we will be writing.
4:56
So title and author,
4:58
or just title or author then title.
5:01
Whatever pattern we set up here will be used
5:04
when we pass in our values.
5:05
So we need that VALUES keyword,
5:07
whether we're just inserting one thing or three or 50,
5:11
each line here or each entry separated by parentheses
5:15
and a comma will be parsed with this pattern
5:17
that we laid out and added as a new row to the books table.
5:22
Next up, we'll talk about updating information.
5:25
(bright music)