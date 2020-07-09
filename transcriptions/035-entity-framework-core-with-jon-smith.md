# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is episode 35: Entity Framework Core with Jon Smith. In this episode I interviewed Jon about just what Entity Framework Core is, and how you can use it to speed up the development of your applications. Some of you may know Jon from his many open source libraries (including [NetCore.AutoRegisterDi](https://github.com/JonPSmith/NetCore.AutoRegisterDi)), his talks at NDC, and his book [Entity Framework Core in Action](https://www.manning.com/books/entity-framework-core-in-action)

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Jon's Introduction

**Jamie**

So the first thing I'd like to say, Jon is, thank you ever so much for being on the show. I, you know, we're all really busy people, and taking the time out to talk to me about, you know, the topic we're going to cover today is I'm very, very appreciative of it. Thank you ever so much.

**Jon**

Thank you for having me.

**Jamie**

Hey, you're very welcome. To start with, I was wondering, could you maybe Introduce yourself, give the listeners a bit of a clue as to who you are, and the kind of work you do and all that kind of stuff.

**Jon**

Okay, so my name is Jon Smith. I am a contract programmer. And I've had already had an interesting career, I was started out as a programmer went into managing technical people/programmers. And my last full time paid job was I was technical director of small to medium enterprise. But then I got called back to programming by my wife, who is a lecturer in Maths at Southampton University in the UK. And she is a specialist on health care modelling. And she's got all the maths, but then the NHS in the UK said, "Oh, could you model this?" And so I came back to programming via that route. And I've done a number of jobs with her now, but mainly now, I do web applications, particularly on the back end.

**Jamie**

I see. Excellent, I do like to meet their web application, folks, especially the server side stuff, I'm kind of falling into this camp of the full stack developer is starting to disappear. And that's not a case of fewer people doing full stack. And this is my opinion, that is shared by a lot of people that the full stack is, is becoming a term that encompasses so many things, you know, you've got just for front end, you've got Angular, and Vue, and React, and Blazer and, and, and all of these technologies, you know. And just knowing one of them enough to be productive enough to build a wonderful front end is so difficult to do. So yeah, like I say, I like to meet other other web devs and discuss where they're coming from where they're at, and which side of the silicon they like to live on. As important as the server side is the you know, the the client side is as important, you know, the server side is preparing all the CRUD and the data, the client side is doing a lot of user interaction and showing i. And that is not to, not to reduce what people do, it's just, you know, it's a completely different skill set. You know, it's like a designer and an architect, I guess, similar similar skill sets, but completely different arenas.

**Jon**

I think I agree with you, I used to call myself a full stack developer. And, but I did quite a bit around react. But with the book that I was asked to write on Entity Framework core, you know, just to get into that, in that level of detail, you just, you just can't cover the whole plethora of of things that you need, especially, I tend to work now on on larger up applications. And they, you know, there's just so much in there, that you've got to specialise, you know, your team has to specialise because you can't be doing everything. The only downside is that I'm glad I've done a lot of front end, because you don't want to as a backend person lose the context for the front end. That's, that's very important, I think,

**Jamie**

definitely, definitely, I guess it's the same as when we sit with our clients, and we get an idea of what the  business needs, we need to get an idea of what business model is. And I think that's, kind of similar, I guess for back end developers should know, the sort of inputs business model of the front end. And I feel like the front end developers should know like a "business model" in quotes of the back end, you know, that sort of API contract and how this information is going to be stored in the in the back end, or shown on the front end. And the nuances that come with that, you know, I can't give a front end developer an array with 50,000 items, and the raw GUIDs and just expect it all to work very well, in the front end, maybe I have to give, like a paged list, you know, or maybe I have to give them an API endpoint. And they can request information as and when they need it.

**Jon**

Yes, there has to be, I work at the architectural level. And and, and you have to have an overview of the whole system. And certainly, the business rules or logic or whatever you want to call it, they're spread across the whole backhand and front end. And you've got to understand what the clients trying to achieve, and then work with the other people in the team to achieve that. I think the book, you know, people now asked me to look at things that are on the back end. So that's kind of, you know, I quite like that it is big systems with lots of detail. And that, that's quite interesting. But I can't do the front end at the same time.

**Jamie**

Precisely. You know, I always think to myself, if you want to fix the pipes in your house, you get a plumber in, if you want to someone to build you a wonderful user interface, that is a breeze, a joy to use that uses whatever technology you wanted to use, then you get an expert in, you know, it's the same sort of idea. You know, I know that I could produce a usable interface. But it may not be, let's say that accessibility is a big issue. I have no idea when it comes to accessibility. So I'll get an accessibility expert to sort of run through what I've built, or maybe an accessibility expert to help me design something. Or maybe search engine optimization, gotta go to a search engine optimization expert, because I one or two things, but I don't know, you know, it's a big subject. So I completely agree, I think it's worth knowing of the problems that exist, I think in the front end. And like I said, if you're afraid that def may be knowing that the problems exist in the back end. And I think that having maybe a separate team, one that deals with the front end with some knowledge of the backend, and a team that deals with the back end with knowledge of the front end, helps maybe from a managerial point of view as well, because then you're not managing. Like you said, you don't have one person who knows the entire system back to front, all of the technologies because then that that one person has expert knowledge in all of the different areas, which for one may be more expensive to hire. But for two, what happens if that person doesn't come into work the next day?

**Jon**

Yeah.

**Jamie**

Anyway, I think we're veered off topic slightly there. But that's how the show works. I tend to sort of, like I said earlier with the pre recording, we sort of just have an informal chat. And you see where it goes.

**Jon**

Yeah.

### The Book and Entity Framework Core

**Jamie**

So you've mentioned the book a few times. So I was wondering, could you talk to us a little bit about the book, what the books about?

**Jon**

Yes.

**Jamie**

Whether it's aimed at back end developers, front end developers, whether is aimed at developers who have so you know, not to give the game away a little bit. But you've mentioned it already. It's about Entity Framework core. So is it aimed at developers is aimed at DBAs? Is it aimed at someone in between?

**Jon**

Yes, so I was approached by Manning publications. And they have a very - well, there was a lot of discussion at the beginning about who this book was for. And at one point, they were wanted to make it for starters, that didn't really know much and go from there. As we talked about the problem, and the library, which is a very comprehensive and large library, we decided in the end that we would focus on intermediate to expert. And the book tries to bring you in; the first five chapters of a very friendly for people that have never seen anything to do with Entity Framework before. But then, as you go in, it does get more complicated, just to try and get the coverage that you need. I think people like to have something which is detailed and deals with the real problems. And what I try to do in the book and what I tried doing the any articles I write on my own blog site.

**Jamie**

Sure, it totally makes sense. You know, we learn best from examples, regardless of how it is that a person learns. So like, I think I mentioned to you earlier on that I'm an auditory learner, so I kind of have to hear it to really take it in, I can take some information in via reading, but it tends to not sort of stick around. So even though let's say I wanted to go learn about Entity Framework, I need an example. I can't just be told, this is what this command does. And this is what this command does. And this is what this command does, it's not going to be as easy to sort of glue it all together to make an application, just knowing that there is a `SaveChanges`, or that there is a `DbContext`, you know, not just knowing these things isn't going to help me to build an application. Whereas knowing that I would use a `DbContext` for this thing, or this is how would you `SaveChanges`, or this is how I would use this, this is how I use that. Knowing that the ideas of how to glue things together kind of helps more than just knowing that they are there, at least when you're starting out. And that's my opinion that could be could be completely wrong, you know, because we all have opinions, you know.

**Jon**

Yeah, I think I chose to write a kind of super, super simple Amazon site selling books. And it's very simple, but it's a real problem. So you know, you can list the books, you can sort them by votes, and price and all those sorts of things. And then you can buy a book, and etc. And I thought that we're all familiar with an e-commerce site, and buying things. So there was a, it was easy for people to understand what I was trying to do. And then I, in the first five chapters, I built it up through different stages. And then in later chapters, I performance tuned the application, you know, we fed in 100,000 books, and sort by everything with four stars or more. And that gets challenging. And so and that that seemed to work. And with the book, there is a GitHub application, and which has got a branch per chapter, so that you can go to a branch, and it will run as the book describes at that point. And then as you go on, and you get to the point where you're, I've performance June, you can then run it when it's performance tuned. And I think that helped people.

**Jamie**

So we've talked a little bit about the book. And we've mentioned Entity Framework or a few times and I mentioned a few of the key words to do within the framework or but before we talk about what Entity Framework Core is, and what it aims to sort of solve those kind of areas. Obviously, you can use something like ORM, object relational mapping, which is kind of what Entity Framework is. Or you could use ADO.NET and SQL commands and run everything manually and parse everything out using data tables and item arrays and all that kind of stuff. So where does an ORM sit in that sort of hierarchy? Are we talking directly to the database? Are we talking to a thing that talks to the database? How does that all that? Is that something that's out of the context of the book?

**Jon**

No, no, in the book I right in, in chapter one, I have some diagrams of what happens inside Entity Framework when you read things, or when you update things, and I'm very visual, so I got about 100 diagrams in the book, because it's that's my way of learning is seeing images.

So I started with, you know, SQL and ADO.NET. And I've been through various forms as they came along. I tend to work in the Microsoft .NET area, so I tried LINQ SQL, and then I used Entity Framework. The one that runs on the NET Framework is called Entity Framework. And then this book was about the new version, Entity Framework core, which runs on .NET. Core. So I had come up through this whole going from SQL to not having to write SQL, and there are some lots of good things about it.

So with Entity Framework, if you want to read something for the database, you use the language called LINQ. So Language INtegrated Query, which I think most C# developers will be familiar with, because it's been around for a while. And you often use it for querying data inside your code. But what Entity Framework does is it captures the expression tree, which is what the LINQ queries where you write things like where price is less than 10. And I don't know, published date was before 1999, or something. So it takes that whole link query. And it will then turn that into database access commands to do the query. At the moment, that's SQL databases, a whole range of them, SQL Server, SQLite, I can never say the name

**Jamie**

is a Postgres

**Jon**

Postgres, that's it? Yep. And mySQL and all sorts of things. So that's turns it into SQL Server. What is very interesting for me, and for most people, is that in version three of Entity Framework Core coming out in September 2019, it will support NoSQL databases as well. The first one will be CosmosDB. And I think that's a very interesting thing, to have this whole SQL and NoSQL. together. And certainly in performance tuning in chapter 14, I used to CQRS database structure where I had the writes going to SQL, and then the reads came from a NoSQL database. And it will be lovely to be able to do that all inside Entity Framework Core when version three comes out.

**Jamie**

Wow, there's a lot of information there. That's, that's wonderful. I do like the idea of NoSQL databases. I haven't had a chance to play with any of them yet. I've seen lots of wonderful demos with CosmosDB, though. I think I saw a demo, I want to say MS Ignite, or Tech Summit, where they essentially showed the entirety of all of the characters across the entire Marvel Universe on one screen, and the person showing it off was just, "literally click on that and the information is there, click on that information is there it's not click and wait and spend and wait and wait. Because it's a big SQL query was just click, click click, click here comes the data."

And you mentioned the Entity Framework is the version that runs on .NET. And it's different .NET Core is the version that runs on .NET Core, could I use Entity Framework or .NET Core? Or can I use Entity Framework with .NET framework or am I just limited to if I'm writing an application with .NET Framework, do I have to use Entity Framework or if I'm using .NET Core, or as it will soon be renamed .NET, am I locked to EF Core? Can I can I sort of mix and match?

**Jon**

You can I've just done something for a client who had something which was using, was developed under the NET Framework. It's been built over many years. And I added a section of it using Entity Framework Core running on Cor - because that's faster. But you can mix and match these things. Because they're trying to keep, trying to do this with Entity Framework Core. You should be able to run either version on either NET Framework or .NET Core. My feeling is that the performance tuning that is coming in with .NET Core and, you know some of the performances you getting out of that is well worth it, which is why when my client, there was a performance issue. So this section of their big application is now running .NET Core part inside a .NET Standard application. And you can do that. And I did that so that the Entity Framework Core would run as quickly as possible. And we got very good performance out of that.

**Jamie**

I like the you can sort of mix and match if you need to. Because, you know, I know a few developers who were thinking "oh, well, Core is specifically for Core. And classic, as it were, is for Framework," you know. But knowing that I can if I need to use, you know, maybe I have some legacy Entity Framework stuff. And for some reason, something in Entity Framework or is not supported, I know that even though I'm building something with .NET Core, I can still kind of talk to it. That's that's useful to know, useful to know.

**Jon**

They're not doing it with ASP .NET Core that will only run on Core. I think ASP .NET, the web application is a more complex thing. And its performance is very important. And they've got fantastic performance on that. So I think they're going to keep that only running on Core. But I'd have to check all the - I don't want to absolutely say but I believe you can. I've done this thing where you can mix and match. And I believe that they're trying to keep Entity Framework Core so that it will run on Standard.

You know, don't don't believe me. Look, look it up.

**Jamie**

Sure. What we'll do is we won't call you on it. We'll leave it as an exercise to the listener to go and sort of double check whether they can or not. That's I think that's a better idea.

**Jon**

Yeah.

**Jamie**

And yeah, I do know that the the ASP .NET Core, as of version three will only run on .NET. Core. There was for a short time talk of ASP .NET Core 2.1, I believe, working with Framework, but that was more a case of getting people over the sort of huge jump iof, "I need to now write all of my applications with Core rather than Framework." There was kind of like a bit of a helper helping hand I think.

**Jon**

Yeah.

### Entity Framework or Entity Framework Core?

**Jamie**

So we've talked about what EF Core is a little, I guess this one may be a bit of a leading question. But let's say I have Entity Framework Core in one hand, because I mean, all of programming is using different tools. So we have different .NET Core in one hand, and ADO.NET or raw SQL Reader that kind of thing in the other hand. At what point would I want to shift from using one to the other? And the I guess vice versa? You know, is it a case of an argument of, say, C++ versus assembly? Or is it two completely different sets of tools for two completely different setups, two different problems as they were?

**Jon**

I think the reason why people use Entity Framework and any ORM is, because... there's two reasons:

One you can normally write database access that is quicker, you can develop quicker. It also opens up database accesses to developers who maybe don't know about SQL. So Entity Framework and Entity Framework Core are very complex underneath, but it makes it seem very simple to use on top. You just have classes that are mapped to the database, and you can put these LINQ commands in and it all magically works. And so that's why I think people use Entity Framework.

I can tell you, I'm very interested in performance. So I've really drilled down into what you can do with Entity Framework Core. And it's very good, but it's not perfect. And in the book, I you know, I try and then I use Dapper, which is a micro ORM where you have to write the SQL yourself. So there are places where you can find that Entity Framework may not produce exactly the best SQL, in some instances, normally complex instances. And and there is a point where if you want to tune it, then you could use SQL directly. And actually, it's very easy to use Entity Framework Core and Dapper together. It's very easy. And that's what I recommend to people is, "don't be afraid of Entity Framework. But make sure that your database access is a very clearly defined." And I use something called query objects, but you want them in in a very clear place because you've built this thing and then you find something is too slow, then you need to go get down to it and decide what you do.

People use this because it will make them faster at writing database access code. And it's also more amenable to general C# developers who don't really know all the ins and outs of a database.

**Jamie**

That makes perfect sense. I think it was Julie Lermon who once said that, she will do some things within Entity Framework and then maybe show it off to a DBAand say, "Is this the best way to do it?" I'd say maybe eight times out of 10 I guess it would be but like you said there will be those edge cases those corner cases where because Entity Framework is taking the SELECT statements, the WHERE statements, the filtering, all that kind of stuff, the LINQ queries that you've given it, and it's trying to do its best based on how all of these objects are all mapped together. So it can only do as good a job as you have done I guess. So yeah, I guess yeah, it's useful in that it's, they will make your your code faster in that creating the code will be faster. Because like you say, you know, you're not having to write raw SQL. So if I want to do raw SQL, or maybe call a stored procedure, or something like that, can I do that within Entity Framework, or am I better off using a micro ORM to achieve that?

**Jon**

There are commands in Entity Framework Core for doing... to allow you put raw SQL in there, they're fine. But I find dapper, very easy to use. And if I wanted to use raw SQL, I'm most likely use dapper for doing that, because I'm fairly happy with. I'm not an expert, but I've written quite a lot of SQL before. So that's the way I would do with it.

The other thing is couple of things in EF Core, which is very good, they give you a little bit more control over things in your, some of the SQL like it, you can have a default value for a column. And the big one for me is you can call user defined functions very easily. And those are like little methods of SQL that you can put in your database. And that that I find, if there's just a little bit where it's not quite doing the right thing, rather than just... Well, the example I gave in the book was, it's not very good when I want to get all the authors for a book, because there might be multiple authors, and I want them as a list to show on the screen. And because it has to go off and get all these multi things, it's not so efficient. But I found on Stack Overflow, a nice little bit of SQL that would take the names and put you know, with commas between them and send them back. So I could turn that into a user defined function, put it in, and that made things go a lot faster. So it's this mix mixing and matching.

And you do need to be a bit more aware of what's going on in your your database. And I think that's the danger. It's another topic I'm kind of segue into that thing I worry about Entity Framework core is it hides the database so well, that people just start using the classes that are mapped to the database as if it's just any old class that they have anywhere. And, you know, going through, you know, thousands of them in memory is nothing but if you want to go through 1000 there on your database, it's going to cost you. So I think there is knowing a little bit about what Entity Framework colour is doing underneath, and realising that you need to think a little bit more about your queries than just doing something that you would have done in your code. That's what I recommend to people.

And one of the things that this is a kind of a specific thing, but it's worth talking about it in the old version, Entity Framework last version was EF6 are referred to as EF6. If you wrote a LINQ command that it couldn't translate into SQL, it would have an exception and say, "I can't do that on the database," and bit of a pain, but it meant you had to think about it and and get it right. In EF Core, they wanted to be more friendly. And so they they put in something called client versus server evaluation. And so what it will do is it will look at the query that you've created, and it will go, "what can I do in the database? And what can I do in memory in the client," and it will automatically do that for you. The problem is, if your code is very inefficient, you'll think, "oh, Entity Framework is really terrible, it's really bad." And there are ways you could capture it, and make sure it gave you the exception, that was a real worry to me, because it's very easy to write incredibly bad queries.

And it's really nice to see in in the changes they're making in version three, they have picked up a lot of little things like that, and then changed it now, it won't do really bad queries, it will stop you from doing that. And I think that's a very good move, because you as a learning programmer, you might write a LINQ query, which is not very efficient and doesn't, and you put it in the wrong place, or whatever, and it runs. But it's terrible. And that can be a real problem. Because it's very easy to write these things, you run your little unit tests with kind of 10 items, and it all works fine. And you think, "oh fine," then it goes to production. And it's terrible. So this is the whole thing why I was using the diagrams and why I was trying to explain what's happening underneath because a little bit more knowledge will make the queries and the database access is more performant. And certainly there is some anti patterns that if you build your whole thing using the wrong pattern, you'll just have overall, it'll all be a bit slow. And it will be very hard to get it out. So I give you some guidelines on how to build your queries and how to build your updates. So that you will generally start from a good place, because I've get asked to look at databases and performance and things like that. And there are lots of things where you think, "I know what to look for. And it's very obvious. And if they hadn't have done it that way, they would be in a better state, you know, they still might need tuning a bit. But it would, the whole application would be faster."

### Performance

**Jamie**

I mean, I've seen things out in the wild. I'm reluctant to do this, because this is difficult to sort of visualise. But I feel like as you're a visual learner, you're getting a little more, I have done an episode before I've talked about Entity Framework. And I've read out some entity relationships, and people haven't really gotten it. But I have seen an example before, and I've changed the data types to make it fit. But I've seen an example where let's say you have one University has many Colleges, one College has many Courses, one Course as many Tutors, one Course has many Students, and one Student can have many Grades, and I've seen code before, where it's worked from the bottom up to find all of the average grades for each university based on the colleges and the students and you know, it's gone, grades upwards, so find the best university going up. So obviously, you're you're traversing that entire relationship diagram, all the way up to the top, which if you have it in memory, not such a big problem.

Obviously, that SQL query gets huge and super complex. And, you know, just attacking that problem from the other way around, you know, find me all of the grades for this university, brilliant store that somewhere. You know, rather than going get me all of the grades throughout the system, and then figure out where they are, which University, which costs which student which student, you know, working from the top down, or maybe not even doing that taking a small slice of the data, and working on that and taking another small slice.

There was a an application that I worked on in the past that did things with date times, and we'll breeze past the fact that the date times weren't stored with an offset or any kind of timezone indication. And it was a, you know, multinational company that asked us built this thing. But the date times were stored, and they were pulled back out, converted to a string for some reason. And then manipulated, converted back to an date time and then sorted. Yeah, I can totally understand that you can you can end up writing lots of queries that just are bonkers. I'll put it that way "bonkers". And yeah, attacking it from a different angle or rethinking it perhaps, because yeah, it's so easy, like you say to think of it is because the database is hidden away from you, you don't have to think about that. You just think, "I have this, there's a list of objects, this collection of objects in memory, I just interact with them, like I would with a LINQ, and it will all be fine." But in actual fact, they don't exist on the server at all.

**Jon**

Yep

**Jamie**

Just to explain that a little bit, I guess, I guess you can go into more detail, hopefully. But it's different Mark has this idea of a `Queryable`. So you build up a query. And it's when you say, `ToList`, or when you say, a certain operation that the query is built, as SQL query, sent down the pipe, to the SQL Server or MySQL, Postgres, whatever, and then brought back and it's during that bringing back process that all of the objects are then brought into memory. So knowing that, that is the thing, I guess, really helps to really help you come up with better queries. Because, like you say, if you think of it all, is just all of my records are in memory, then yeah, you're gonna have about time, I guess,

**Jon**

Yeah, what I would recommend, if you go to the Manning site, in chapter one, it's free, you could, that's a free chapter. And it has some diagrams in there, that just lays out what's happening inside Entity Framework Core when it's going through things. And I hope that is useful to people, it just gives you an idea of what's going on underneath. And that makes you more aware of what's happening and what you should be careful about.

Can I say one thing as well, one thing that if you've never come across SQL before, and you're a bit worried about it, then in Entity Framework six, EF6, the old one, it is the older one. When it outputs, its SQL, which you could capture, it was efficient, but it was very, very hard to understand it, it was written all in the kind of like a computer wrote, it was just horrible. And it was really hard to understand. EF6, they actually output SQL in a format that is almost like someone would write, even with the indents in it, and it is a beautiful to look at. So I often in my unit tests, I capture the SQL that's coming out and have a look at it, and go, "oh, that's interesting." And you you start to learn what it's doing. And also you're learning. If you don't know SQL, that's a good way to learn what's happening underneath it, what what it's producing. And I really recommend that. I have a library, which helps people when they're unit testing with Entity Framework Core, it's an open source library, it's on my GitHub page, you will find it on there. And I describe it in the book, but there's full information. And in that you can capture the logging, which contains the SQL, and just put it out to your screen. And so you can take run your little test and see what SQL it produces. And I find that very helpful.

**Jamie**

I like that because then like you say, if you don't know SQL, or maybe you just want to level up your SQL knowledge. You can read a query, fire it enough to Entity Framework Core and see what it's doing to your series will LINQ statements, your LINQ statements, LINQ objects, LINQ to SQL, whatever. You can see how it's converting that and then go, "ah yes." like you said, "ah yes. That's how I would do enumerating, you know, this is how I would write a where clause," or "this is how I tell the database to give me all of the properties for this table or something." I'll have to get a link about that in the show notes. That's, that sounds like it's something that I at the very least I'd be interested in. should give that a go myself. You know, I'm competent with SQL, but I feel like, I feel like I'm at the level where I'm competent enough to be dangerous.

**Jon**

Yes. So if you download the project, called it EF Core in Action, and you run something like branch chapter five, if you run that gives you this very simple, there's only 50 books in it, but it will build it all for you and put it on your screen using SQL Server and it gives you you can click something at the top called logs, and it will show you the SQL that was produced. And then you can try saying, "okay, I want to sort by price. Okay, what does that do? And then I want to filter by four stars or better." And you can see how the SQL changes. And then I go in chapter 13, I performance tune the thing go through three stages. And again, you can look at the logs and see what's happening. And it's it's very helpful.

### Migrations And Top Tips

**Jamie**

So what about changes to the database then. So I know from personal experience, that when, _when_ a database changes, because they all do is not wrong when your database model changes. And the client says, You need to capture these things as well as these things. And we need to map them together and somehow do some magic and display it on the screen. So that's a change to the database. Obviously, in the past, we've had to them manually script to write, add that table, add this column, this foreign key over here, add this primary key over there, add some constraints, that kind of thing. Is this something that Entity Framework Core can help with?Bbecause obviously, a lot of folks who haven't used Entity Framework are thinking, "well, I don't have a database, and I'm going to build it up as I go along. Can I change the database? Can I alter the structure of the database with a different model?"

**Jon**

Yes, you can, let me tell you what Entity Framework Core has is similar to what EF Six had, but a little bit better. The first thing to say if you have an existing database, there's a thing called reverse engineering or scaffolding, which will read your database and build you all the classes, then all the setup that you need to access that database. So that's, that's quite useful. And I've used that with my clients. But if you are starting with Entity Framework Core, and you've gotten a new project, then you can use something called migrations.

So what happens is, so you build your first thing. So in by chapter three, I, you know, you could put up books and list them and all that sort of stuff, but you couldn't buy them. And then in chapter four, I added business logic to allow you to buy a book. And so I had to add an order and a line item table to the database. And what happens is you could you add the classes that you represent that and then you can say to it, add a migration it goes and it looks at all, what was there at the beginning. And what you've added, it goes "ooh. There's two new classes that go to these oh", and it will then build the commands to take your database from chapter three, where there were no order and line items, and it will add the order and line items to it.

And so that that's a really good thing. But I'm going to put a big but here, database migrations like that are great, especially for small systems, and things that you're, you know, just trying out. But when it comes to production systems, I don't use that, I use another method. And I will send you the link to it. But I written two very long [articles about how you can create a migration](https://www.thereformedprogrammer.net/handling-entity-framework-core-database-migrations-in-production-part-1/) and then [how you can apply a migration to a database](https://www.thereformedprogrammer.net/handling-entity-framework-core-database-migrations-in-production-part-2/). And if you've got a production database, and you have to update it, it's a scary thing, right. So if you've really got an e commerce site, and you've got, even if you want to take it down and stop it while you do the update, you don't want to mess anything up. If you want to update it, while people are still using it, it's even more hard.

So I've found that I just database migrations take me so far, but I do it by building my own SQL scripts that update the database, and I have a tool, which can tell me whether my scripts will create a database that matches the classes that I've changed in the software. So and that's really important because you, if you try to manually update it, you might not quite get it the way that Entity Framework thinks it should look. And so you know, that's what I use. Again, I, the thing about this, the SQL it produces is, is very nice. So I often get it to in a unit test, I'll say, "okay, create me the database with everything in," and then I look at what it does and copy out the bits that I need to put in my migration. So I go through all of that in the book. But I also on my, my site, I've got two very long, detailed articles that covers a this whole thing,

**Jamie**

What I'll have to do is we'll have to get some links to those and put those in the show notes. And I have to go read those myself. I'm always interested to find out how something is actually working underneath the covers. Because you know, like you say it's okay, knowing that Entity Framework exists. But you know, getting an understanding of even just a basic understanding of here's what Entity Framework does for you, and here's how it does, it kind of helps you to understand, maybe there's a better way to write the query that you're thinking about, or maybe, you know, maybe you're going about it in a less optimal way. Or maybe you are doing it the best way. And maybe Entity Framework just doesn't really support what you're trying to do.

**Jon**

Yes, people do use migration in real applications, you know, that Entity Framework migrations. I just want people to stop and think about what they're doing when they update a production database, because you really don't want to get that wrong.

**Jamie**

Most definitely, most definitely, I can remember a time when, for one project I was working on, I was asked by the client to "It's okay, just go into the database and change this value." And I don't even have to tell you the rest of the story for you to know. This was very early on in my career at a point where I didn't really like to say no. And at the time, like I say, very early on in my career, I wasn't aware of transactions being a thing.

**Jon**

Yeah, I got in contact with the Microsoft development team, way back in EF6, because I wrote a long article saying, I had an e-commerce site that I was working on. And I just said, "I just can't trust the migration system that's built into Entity Framework. And this is what I've done." And we there was some stuff backward and forward, they were very interested, you know, they wanted to hear why and and understand what I was was talking about. And they have been more careful in Entity Framework Core. In EF6, by default, if you didn't tell it not to it would try and migrate any database when it started. And that was by default. In EF Core, it's not by default, you have to trigger it. And they give you very clear guidelines on what to do, especially when you're running a web application, which has got multiple instance running. You've got to be careful.

**Jamie**

I remember when I think I was reading an interview with I want to say was Julie Lerman again, I'm not sure I'm a bit hazy as to exactly who said it. But essentially, the let EF at the time, but it's now EF Core, obviously, let EF come up with a migration. And then we'll go to an actual DBA and say, "here's my entity relationships. Here's what I want. And here's what I've given it. What should it have done?"

**Jon**

Yeah

**Jamie**

But I guess it you know, if you don't have a DBA on the team, the thing that he they're the migrations, I guess that EF creates, are good enough

**Jon**

Yes. And early on, if you're, you know, some of these things take a while that they, so you might want to use migrations at the beginning. You know, with that, that's fine. It's just when you get to the production, you've got to think, "do I trust this to do this in the right way?" And in most cases, it will. And the Microsoft recommendation is you get the migration, and there's a command where you can turn it into a script, a SQL script, which you then apply to the database using some tool that is appropriate for your database. So that's the recommended way of doing it. And then you can check things and go, "oh, yeah, didn't really mean that," because sometimes I look at he SQL, for the migration that EF Core  and I go, "oh, I forgot that. I didn't set that one is not nullable. And that's my mistake." But by looking at the SQL, I knew that this string should be not now. And it shows a fault in my code, because I've forgotten to mark it with required attribute on the property,

**Jamie**

I've always felt that it can lead to those kind of constraints, you know, you you recognise where there's constraints should be versus what is detected. So obviously, when you add a new column, so one of the things that migrations will do is unless you say so when a new column is added, it will be mark it as nullable, because obviously, the previous records won't have a value. But you can then say to it, "ah, right, okay. I want to be non-nullable. And I want you to go do some extra logic with the records that already exist. Maybe put a default value in there or something."

**Jon**

Yep.

**Jamie**

Okay. Well, that's mainly the questions that I have for today, I know that I'm going to be going away scratching my head and rethinking about EF Core, if I'm honest. Because it's something that I've, in my in my recent projects, I had the opportunity to walk away from using an ORM and try sort of "SQL hard mode", using SQL connections and calling stored procedures directly from .NET. And I think it's given me the opportunity to sort of see it from the other side and understand how it's all actually glued together from a 10,000 foot view, anyway. I'm looking forward to looking back into EF Core, because the majority of the stuff that I've done with EF Core in the past has been, "here's little silly demo app or a web API that I've built just for some kind of talk or a demo just to show something off." But I'm looking forward to getting back into it.

**Jon**

Yeah, one of the clients I work for they they had 300 databases. And they were using sharding and multi tenant. And I built a system using Entity Framework Core, and ASP .NET. Core, obviously, with a web API out to an Angular front end. And that was all using Entity Framework Core. We did some performance tests. But you know, we didn't have enough data at that stage while I was involved. But my experience is that in a web application, you get tonnes and tonnes of admin commands or things that need to be done, that are not very important. And then you get, maybe, I don't know, it depends on the application. But it could be between 20 or 20%, or could be just just 5% of the queries or the updates, that really matter. And you want to spend your time on that. So by building with Entity Framework Core, you're going to build it quickly. If you build it well, such that all your queries are nicely isolated, when you have a problem, you can go and go to that isolated part, and then tune that up. But you've saved all the time on all these boring; you know, I've built applications, there's so much boring admin stuff isn't there, that some of them that they used very rarely. And they just want to get it done. So that you can then focus on the few things that really matter. And if you have to rewrite all that bit in SQL, or do something clever with Redis, and caches and all that sort of stuff, that's fine, that that that's part of the job, but you don't want to be always working with SQL across the whole thing, and have really fast admin commands that we're going to be fast anyway. So that's my, my approach anyway.

**Jamie**

Yeah, you're right, Entity Framework, well Entity Framework classic, I guess, and core both allow you to really just sort of speed through the, again, not to reduce what DBAs do, but the sort of the crud of getting everything up and running. Because I think I've said it before that there's a quote somewhere in the Phoenix Project, and a book called The Goal which essentially says that until the product is in the customers hands, so the customer, the customers of your client, until the product is in their hands, it's making no money for anyone. Except for you, I suppose.

**Jon**

Yeah.

**Jamie**

And you know, we need to get out. That's why we have things like Agile and, you know, DevOps and things like that: to try and get the working software out as quickly as possible. Get as much feedback as quickly as possible. And you know, this way, you don't have to sit and read the sort of boilerplate. Okay, so I'm going to do a SQL command. Okay, so I'm going to be using SQL command, command equals new command, we're going to do connection first or opposite connection. The generate teh, command put all the parameters in fill the data set coming back out. Now with a data set. And now I'm going to go data set or data tables, do they exist? Is it not null? Do I have the right amount? Okay, now, give me the rows right now, for each through the rules. Brilliant. Now I've got to convert because it comes back as an object, you've got to string it, and then pull it out as an indoor and then pull it out as a bool. And that's just for one row.

**Jon**

Yeah

**Jamie**

Maybe that one row represents a single object, you've got to then populate the rest of the objects. So yeah, I think you're right, it really does help with sort of getting you up to speed and started very quickly.

**Jon**

Yeah, let me also tell you about one feature that you may not realise it's there. But if you had, well let's take our order with our line items, so you have an order, and you have one too many line items, you know, so you bought this book, this price, and you bought this book at that price, okay. And when you do that, in SQL, you have to write one out to get the primary key to fill in the foreign key in the line item. So you write the order out, you get that and then you can fill in the line items. Yes?

**Jamie**

Yes.

**Jon**

So this is the typical thing that you're doing. So if you have complex sets of things, you have to put them all out in the set the right order, and then move the keys, the keys and foreign keys around. Entity Framework has something called navigational properties. So I have an order with a collection of line items. And if I just fill all those in using those navigational properties, when I save it, Entity Framework goes, "oh I need to save that and then copy that over," and it does all the foreign keys and primary key setups for you. And in that particular thing, the order with the line it that's fairly easy, but you have something big, and I had a client who already uses EF Core and he says, "oh we got to write them in out in the right order to get the primary keys and foreign keys right." I said, "no Entity Framework does that at all. You just build up this, all these things linked together. And Entity Framework will go 'all carefully go through it and find out all that one was you read from the database, this one you updated this one, you created a new one,' and it a look at it all sort it all out and push it out to the database in one transaction and do it right." That is such a saviour, saving a time, such a same time of development time.

**Jamie**

It really is here with us all the questions and topics I think we should really cover in this in this episode. Anyway, I mean, I've kept you sort of gives you around for over an hour at this point. And I realise you know, we're in the evening, it's time for you to go and do some chill out stuff, whatever it is that you do in your evening. So I just want to say thank you ever so much, Jon for taking the time to talk to me today about Entity Framework and just how magically wonderful it is.

**Jon**

I am a fan. So thank you for giving me the opportunity to spread some good news.

**Jamie**

Thank you very much. I really do enjoy talking about these kinds of technologies with people just to partially to broaden my own knowledge, but also to give an expert like yourself the chance to say, "this is really cool. And here is why."

**Jon**

Yeah, thank you.

**Jamie**

Thank you so much.

### Wrapping Up

That was my interview with Jon Smith about Entity Framework Core. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and a full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/).

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Jon Smith on twitter](https://twitter.com/thereformedprog)
- [Jon's blog](https://www.thereformedprogrammer.net)
  - [Handling Entity Framework Core database migrations in production – Part 1](https://www.thereformedprogrammer.net/handling-entity-framework-core-database-migrations-in-production-part-1/)
  - [Handling Entity Framework Core database migrations in production – Part 2](https://www.thereformedprogrammer.net/handling-entity-framework-core-database-migrations-in-production-part-2/)
- [NetCore.AutoRegisterDi](https://github.com/JonPSmith/NetCore.AutoRegisterDi)
- [Entity Framework Core in Action](https://www.manning.com/books/entity-framework-core-in-action)
