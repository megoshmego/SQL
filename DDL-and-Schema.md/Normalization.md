thank you. would you include any scripts for demos you think might be helpful? 







will you please evaluate the following script for the key terms, concepts, and any other relevant information and definitions and include the title of the video "Normalization", and the section of the course "SQL", and subsection "DDL and Schema", as well as any demos you think would helpful to me?:


nscript


0:00
(upbeat music)
0:04
- [Narrator] To wrap up our basic SQL content here,
0:07
we'll talk a little bit about some best practices
0:09
to keep in mind, when you are designing your databases.
0:13
So the first topic we'll introduce
0:14
is a term called normalization.
0:17
Normalization is actually a relatively kind
0:20
of complex topic if you go and research it.
0:23
Database design in general really is an art,
0:25
we are scratching the surface here, but keep in mind
0:28
there are people whose entire role,
0:31
their entire job description is to architect databases
0:34
to maintain databases, to plan out how a database
0:38
will be structured, for large applications,
0:41
this stuff gets very complex.
0:43
So we're scratching the surface here and I wanna mention
0:45
this term normalization, with the caveat
0:48
that if you do go research it, it's not a bad idea
0:51
you'll run into some interesting terms like
0:54
the first normal form, the second normal form,
0:56
the third normal form.
0:58
There are different types or degrees of normalization.
1:01
So what is normalization?
1:03
It's basically a design pattern or technique, where
1:06
we reduce redundancy and dependency of data in our tables.
1:11
So we can break up a larger table into smaller tables
1:14
and link them using relationships.
1:16
And sometimes we are forced to do this,
1:19
if we wanna represent a relationship, I guess
1:21
we're never forced to do it technically, but with
1:24
what we've seen so far, it makes a lot of sense.
1:27
When we're working with things like movies and studios,
1:31
we make a separate studios table and we've referenced
1:34
that from within movies.
1:36
But here's another example, that is a little simpler.
1:39
Here we have a products table, where we have IDs,
1:43
we have a price for a product, we would have some name,
1:46
let's say we're making a Lego bricks, then we could
1:49
have colors or maybe we're making bicycles, who knows.
1:52
And some bikes come in one color like yellow,
1:55
very cheap bike by the way on the 10 bucks.
1:58
So it comes in yellow and then some other bike frames
2:00
have different varieties, we've got red and green.
2:04
With the way this is set up right now, we have
2:07
a single color column, where we could store multiple colors.
2:11
This works, we totally could do this,
2:13
we can't store multiple colors in here as
2:15
a single string as text.
2:17
The downside of course, is that it sucks, if we want
2:20
to query it, if we're looking for green, anything that comes
2:23
in color green, we would have to check
2:26
to see if the string contained green.
2:29
And that's not that bad because we can use like,
2:31
as we've seen, but if we want to fully just remove green,
2:36
we stop making that color paint, we don't have green paint
2:38
anymore for our bikes, anything that has color of green,
2:42
imagine there's thousands of different bikes we make
2:44
and a couple hundred come in green, in order to update all
2:47
of those rows to remove green, we can't just delete
2:51
the entire value, because there might be red,
2:54
there might be yellow, there might be gold or whatever.
2:56
We could have four colors listed here separated by commas,
2:59
we would have to somehow use a regular expression
3:02
or some fancy tool or technique to eliminate green
3:06
while keeping the other colors.
3:08
So a normalized example, would just have a colors table,
3:12
this colors table would have an ID
3:15
and even just a color name.
3:17
So very simple, we don't have to have a ton
3:19
of information here.
3:20
But then we can now have products that are associated
3:23
with multiple colors.
3:25
Using a product colors table or colors products,
3:29
you can name this whatever, you could call
3:31
this product color variants, it doesn't really matter.
3:35
But if you can't come up with a good name,
3:37
just first table underscore second table.
3:40
And all it does is it associates a color ID
3:43
with a product ID.
3:44
So from this table, we could see that product
3:46
with ID of one, this product comes both in red,
3:51
which is color ID of one and in green product
3:54
with an ID of two, which is this product comes
3:57
in color three, which has yellow, that's actual color name.
4:01
Now if I wanted to update, let's say our color green
4:06
has changed, it's now a slightly different shade of green,
4:09
it's all of green, I change it in exactly one place.
4:13
If I wanted to discontinue a color,
4:15
like we're discontinuing yellow, we just have stopped
4:18
I don't know our supplier who gave us yellow pigment
4:21
I guess has run out.
4:23
And we're going to get rid of any product, thousands
4:27
of products that we make anyone that uses that yellow paint,
4:30
we're not making that variation anymore.
4:32
So we'll keep the read degree in whatever.
4:35
All that we need to do is remove this color
4:38
from the colors table and then use that ID and make sure
4:41
that all of the products colors are removed
4:44
if that color is no longer available.
4:47
So then we just have this one ID
4:49
that we would use to delete.
4:51
And if we set up our on delete correctly,
4:54
when we deleted a color we could have it cascade
4:57
to delete products colors.
4:58
Here's one more example of a non normalized table,
5:02
it represents a sales team.
5:04
Let's say that we are a company that sells I don't know,
5:07
we sell wood, specifically fancy hardwood that is used
5:11
to make guitars.
5:13
So maple wood and what else do they use ash,
5:17
fancy hardwoods, whatever we sell it and we have
5:20
a sales team, we have a couple different offices and we have
5:23
a sales team table or sales people table
5:27
where each person has an ID, they have a name
5:31
and then we are storing the office where they work in.
5:33
So we have multiple offices, we are a global company,
5:37
we've got a wood facility in San Francisco and New York,
5:41
the two most expensive possible places in this country
5:43
to build a wood office, whatever the hell wood office is
5:48
our warehouse and maybe we have like 20 different
5:51
distribution centers.
5:52
Each one has a phone number, so already just with
5:55
what we've seen here, we have some duplication,
5:59
we are storing the name which we need for each salesperson.
6:03
And then if they work in San Francisco,
6:04
we put San Francisco here and then we're storing the
6:07
office phone number, San Francisco has a 415229876
6:12
and then New York has 2123455555.
6:16
Right now, just with three different rows, we already
6:19
have some duplication and then we've got customers.
6:22
So, each salesperson has let's say, at most three customers.
6:28
So because at most they have three customers,
6:31
this could work, this it's not horrible.
6:35
If we had an unlimited number of customers per salesperson
6:39
and we didn't cap them, then this would be a bad approach
6:42
because we would need to have customer four and five
6:44
and six and seven and eight.
6:45
And if we could have 100 customers per one salesperson,
6:50
this structure would not work.
6:52
But even with that said, it's still not great
6:54
because a lot of these salespeople have duplicate customers.
7:00
So Chuck Berry's main clients or customer is Fender guitars.
7:04
But Ella Fitzgerald also worked with Fender guitars,
7:08
as does James Brown.
7:10
So, customer one may be our highest priority customer two
7:13
is their second priority and customer three is like
7:15
their least important relationship for each salesperson.
7:20
So even though we could store the data this way,
7:23
we still run into problems when we want to update
7:26
a relationship with a customer.
7:28
Let's say that Fender changes their name, that's
7:30
a simple one, they change their name to something else.
7:33
Well, we would have to update it in multiple places.
7:36
If we drop Fender or more likely, they're unhappy
7:40
with our service and our customer service,
7:42
they just stopped working with us.
7:45
To remove Fender from every applicable salesperson,
7:47
we would need to write kind of annoying query versus
7:51
if we wrote a normalized structure instead,
7:54
which I've partially done here, it saves some effort.
7:59
So here's our sales team it's not complete, we have ID,
8:02
we have name.
8:03
Now we have a separate offices table and this offices table
8:07
is going to store a city and a phone number.
8:10
And we can simply reference the office ID
8:12
from within the sales team table.
8:15
This means that if we delete an office,
8:17
we close our San Francisco office, it's very easy,
8:21
we just delete this and then we could decide what to do,
8:24
were we going to move all of our customers
8:26
or all of our salespeople over to the New York office.
8:29
But we no longer have to update two fields for phone number
8:32
and office name or city for each salesperson.
8:37
Also, if we wanted to change the phone number,
8:40
with this approach, if we get a new phone line
8:42
in our office, we have to update every single mention
8:45
of our San Francisco phone number here,
8:48
we update it in exactly one place.
8:50
And all of these office IDs reference
8:53
that particular office and we can find out the phone number.
8:56
So we're distributing our data more,
8:58
but we're also reducing duplication.
9:01
Yes, it does mean extra tables, but in general more tables
9:05
is a good thing compared to the cost
9:07
of having duplicated data.
9:09
There are situations where duplication is okay.
9:12
But in general, it's always a good idea
9:14
if something can be split up and it makes sense
9:16
to actually split it up.
9:18
And then if we were to fill this out for our customers,
9:22
instead of customer one, two, and three, if we still wanted
9:25
to keep that priority and have a higher priority,
9:28
main customer, secondary and a tertiary customer.
9:32
We could just make a separate customer or client
9:36
or company table where we have Fender and an ID.
9:41
So we could have something like Fender their ID is one
9:45
and this would also allow us to store things like
9:49
I don't know their phone number, Fenders phone numbers here.
9:52
Their office address is 35345 Main Street.
9:57
So now we have more information about Fender and then we can
10:01
have our main customer, which for Chuck Berry
10:06
will be Fender and then we'll just go with our main customer
10:09
and backup customer.
10:12
And for Ella Fitzgerald, she'll take over on Fenders,
10:16
so she's the backup Fender salesperson.
10:20
So even though we still have the same columns, main customer
10:22
and backup customer or customer one, customer two,
10:26
we've eliminated three, but we could also add that in,
10:29
what we see now is that it's much easier to make changes.
10:32
If we need to change, the name of a company,
10:35
from Fender to Fender 2020 experience,
10:39
we change it in one place.
10:41
We also can store additional information
10:43
about each particular company, each customer.
10:46
And if we did have a situation where instead
10:49
of main and backup customers, we allowed each salesperson
10:53
to have as many customers as they could possibly take on,
10:56
then we would probably structure this differently,
10:59
we would have a third table or a fourth table,
11:02
probably called this is our customer table.
11:07
We probably have another table called let's say sales mode,
11:12
we call this customer relationship
11:17
or customer sales relationship or just customers sales team,
11:22
sales member customer, I don't know.
11:24
What we would have here is an ID, then we would have
11:27
a customer ID and then we'd have a salesperson
11:32
or sales team ID and then any additional information about
11:38
this relationship, like what could
11:41
we include initial contact, total deal value and now we
11:50
have more information that we store in a external table.
11:53
And then we wouldn't actually put anything
11:55
about our customer relationships with the sales team in
11:58
that sales team table.
12:00
Instead, it's just an ID, a name and an office ID.
12:04
And then let's say that we have Chuck Berry working
12:07
with Fenders, so Fender has an ID of one, Chuck Berry
12:11
has an ID of one and then we can put initial contact
12:13
in here, Feb 2020 total deal value is $30,000.
12:19
Now we have a different way of structuring our data.
12:22
And it really depends on what we're going for
12:24
and how our company works.
12:26
But in both the refactors or scenarios
12:28
that I've shown you here we have reduced the duplication
12:31
of our data and we've made it easier to update
12:34
to delete things to change names of a company,
12:38
to change office phone numbers or Cities,
12:40
we could close an office and we don't have
12:42
to update all over the place.
12:45
So as I mentioned, normalization is quite a difficult topic
12:48
to convey in like five or 10 minutes.
12:51
But all you really need to take away from this
12:53
is that it's generally best to split up any duplicated data
12:57
into a stand-alone table or some sort of joint table where
13:01
we can reduce the duplication, we can store something once
13:04
and then reference it in multiple places.
13:06
It makes it easier to update and deletes
13:08
and to do all sorts of operations with
13:11
(upbeat music)
