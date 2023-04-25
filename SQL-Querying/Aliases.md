thank you. would you include any scripts for demos you think might be helpful? 







will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "Aliases", and the section of the course "SQL", and subsection "SQL-Querying", as well as any demos you think would helpful to me?:

0:00
(ethereal music)
0:04
- [Instructor] Next up, let's talk about
0:05
something called AS.
0:07
AS in SQL allows us to define an alias.
0:11
Basically we can re-label a column
0:13
when we are selecting data and outputting it.
0:16
So, if I did something like selector do a GROUP BY,
0:21
and I'll print out the average page counts for each author.
0:26
So select average page count from books GROUP BY author.
0:35
We get our average page count
0:37
but the column header that is printed out just says average.
0:41
So if I also wanted to get average price,
0:45
I would do the same thing, average price.
0:49
And now we just have average and average.
0:51
So one reason to use an alias,
0:53
is to make your data easier to understand,
0:56
and easier to work with.
0:57
All we do is add in AS, after we are selecting some column.
1:03
So average page count AS and then some name
1:07
like average pages and then comma,
1:13
if we want to do the same thing for average price,
1:15
we could do AS average price.
1:20
And now our output is the same
1:22
in terms of the actual columns that are printed,
1:25
but we have average pages as the header
1:27
and average price as the other column name.
1:31
So this is isn't solely about outputting your data
1:34
and making it easier to understand.
1:36
So instead of average and then average again,
1:40
we have average pages, average price.
1:42
But sometimes we want to reference one of those aliases.
1:46
For example, if I wanted to figure out
1:49
who the most prolific authors were,
1:52
based off of the number of pages that had been written,
1:55
I would do something like select,
1:57
let's do author, comma,
2:00
and then the page count.
2:03
So I'm gonna sum all their pages.
2:07
From books and then GROUP BY author.
2:13
And now we're getting the sum of all their pages.
2:16
But if I wanted to ORDER BY that sum,
2:19
I wanted to have the most prolific
2:20
down to the least prolific.
2:23
Right now, what I would need to try and do
2:26
is GROUP BY author, ORDER BY sum of page count.
2:36
And it does work as you can see here
2:38
we've got 32, 40, 96,
2:41
all the way down to J. K. Rowling, 4,157 pages,
2:46
far and away the most prolific.
2:49
But what I could also do is use an alias here.
2:52
So instead of just sum page count
2:54
I could give it a name like AS total.
2:58
And then when I'm ordering by,
3:00
it's hard to read because this is a long line,
3:02
but instead of ordering by and then doing the sum again
3:05
I can order by total.
3:08
So that is the alias I gave the sum,
3:11
and I can refer to it here and we get the same output
3:14
and I could easily change it to be descending.
3:19
And now we have the most prolific down to the least prolific
3:23
Sorry Margaret Wise Brown.
3:26
That's pretty much it for AS.
3:28
So that's pretty it for AS and aliases for now.
3:31
It will resurface once we talk about join tables,
3:34
but for now it's just a way of renaming
3:37
one of your output columns,
3:39
so that you can print it out nicer
3:40
but also so that we can reference it later on
3:44
within the same query.
3:46
(upbeat music)
