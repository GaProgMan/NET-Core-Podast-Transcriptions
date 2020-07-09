# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is episode 28: memstate with Robert Friberg. In this episode I interviewed Robert about memstate, the state of database technologies, and a little about his journey as a developer. Some of you may know Robert from his work on memstate or his work at [Devrex Labs](https://devrex.se)

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Robert's Introduction

**Jamie**

So the first thing I'd like to say, Robert is a thank you ever so much for devoting some time to being on the podcast. I really appreciate it.

**Robert**

Okay. Yeah. Great. Well, I mean it's, I'm happy to do this, so it's a nice talking to you. So...

**Jamie**

For the very few people who listen to this show, but don't know of the work that you do or anything like that, I was wondering, could you give us a brief introduction so the listeners know who it is that I'm talking to? Is that okay?

**Robert**

Yeah, so I'm a, I'm a system developer and I've been doing this since 1995 professionally and I've been working as a trainer primarily. So about half of the time I do training sessions and the rest of the time I do development gigs and I've been doing this as a freelancer...since. Uh, yeah. So like I said, 1995 that's a few years, kind of started out on a, on a Commodore 64 and Basic, and then work my way through a PC and Integral Pascal, Delphi did some C, some, uh, Visual Basic. And so on. And I jumped on the .Net framework, uh, as soon as that came. And I've kind of been working with that ever since, primarily. But I've, uh, I do a lot of Linux and Pearl as well. And uh, yeah, it was kind of all over the place with different languages, but I feel that a C# is my primary language.

**Jamie**

That really is amazing. That's uh, uh, I'd love to maybe have a separate episode with you and talk about how things have changed since, you know, the mid nineties and you know, all those languages and frameworks and how essentially I think it's a James Studdart of the Cynical Developer podcasts says that what was great about .Net and C# and VB is it's kind of programming in easy mode because we don't have to worry about references and memory management and you know, all that kind of stuff. And the framework takes care of all of that for you.

**Robert**

Exactly.

**Jamie**

You've been in the trenches, you know what it's like, cause I have to de-reference pointers and, and find yourself in valid memory space and all that kind of stuff.

**Robert**

Yeah, yeah, yeah. So I did some, the most serious things I did with, with a C I built, um, the game Othello, you remember that? Over in C, remember that? The black and white,

**Jamie**

uh, oh yeah.

**Robert**

The black and white pieces that you flipped. Yeah. And so I was coding for several days before I even got to the point where it could compile. But uh, after that point you were nowhere near anything runnable right? So you had just loads of, uh, of bugs, right. Pointer bugs and so on. But, but as in, if you're working with Java or C#, when it compiles your, you're pretty near something that's, that's runable.

**Jamie**

it is crazy. Like you see, it's just a, it is just, you push a button and your app runs and you have at the very least a blinking cursor in a console and you can issue commands and watch it do stuff. Whereas, yeah, in, in low level C or whatever, you have to write everything yourself. You've got to write the engine, the framework, the models, all of that kind of stuff. It's, yeah. I don't think I could do it at this at this time anyway.

**Robert**

Yeah. And so a lot of time we don't really benefit from the extra performance so that you can, that you can have, if you, if you need it. And so it kind of doesn't really make sense to, to do the extra work.

**Jamie**

That's it. Uh, who was it? I want to say it was Donald Knuth who said the premature optimization is the root of all evil. I think it might've been Dykstra that's 50, 60, 70s. And they're, right. You know, like you say, they're eking out of that 1% of optimization in a .Net app is probably not gonna save you anything and it's probably going to take you maybe a week to do it if you're lucky.

**Robert**

Yeah. I feel, I feel a lot of people misinterpret that, that, that part about optimization. Uh, so, so that doesn't mean that you shouldn't be planning or designing or thinking about performance during the design phase right.

So you need to pick good, good algorithms and data structures and so on from the onset. And uh, if you don't do that and build a mess, then, then you won't be able to optimize that anyway. Right. So optimization is kind of, maybe you're squeezing out the last, uh, 20, 15% of something that's already going to, so by choosing poor algorithms, you, yeah, that's, so that's more important than, than the optimization bits in themselves.

**Jamie**

Definitely. You know, there's always that risk that you run when you're, uh, when you're in a large team and you worried does say Jeff, know algorithms? You know, it's so easy, like I say, with a .Net to just go, yeah, we'll just use our lists and store everything in the list. Cause contiguous memory goes on forever. Whereas actually maybe that's better being stored in a hash table or something.

**Robert**

Actually all those, all that kind of knowledge comes into play when you're doing things in memory.

**Robert**

Because like you said, uh, if we're, if we're used to using the list instead of a hash or a link list in or an arraylist and so on, but we only have 10 or a hundred items to, to work with, then it doesn't really matter. The difference won't be measurable. But if you will have all your data in memory, if you have gigabytes of memory, if you listed it contains millions of items, then it, then that comes into play, you know, so the things we learned at university, but we never use in practice because we were just moving data from the database, putting it in, in front of the user, letting them change some stuff and hit save and then pushing it back. So that's kind of what, 80% of developers do. Maybe that, that might be a bit cynical, but that's a lot of the industry that I see the information processing and uh, you, you don't really get to apply that knowledge that you've studied at University of if you did that.

**Jamie**

That's true. Yeah.

**Robert**

But it's fun. Again, by keeping it in memory, then you have to, then you get to do these things that are fun as well.

**Jamie**

That leads us on to, I guess a little bit about the topic that we're going to talk about today, if that's all right. So although it's, it's partially related, maybe, maybe 100% relates that I'm not entirely sure. Could you give us a quick introduction to memstate, um, what it is and what it's going to achieve and things like that?

**Robert**

Yeah, for sure. Okay. So memstate it's a framework that will let you keep your data in memory and it will, it will, uh, let's see. It's kind of like an event sourcing a framework where it will automatically record at the input events and uh, maintain that all the data in memory and it will allow you to restore the state, all the data in memory when it, when the system comes back up again, right?

If we start up the system, it will, it will, uh, read are the prior amounts and create an in memory model. And this model is something that you define yourself and when you issue new events or commands, these will be applied to the model after they have been appended to the log. And so so, so what it tells us is it makes you, you can run queries very quickly because all the data is in memory. And also your write transactions are pretty fast too because the limiting factor is, is taking a single command object and appending it to the log. That is the bottleneck in the transaction processing pipeline, right? And so you can, you can, you can run, you can do thousands, tens of thousands, maybe 100,000 write transactions per second and a at the same time you can, you can do millions of reads it or queries.

If the queries are simple, if you just doing a simple lookup in a, in a dictionary, then you can do millions of those. But reading a single row from, from the database, from a relational database would, would be slower. Right? And if you have a lot of ongoing write transactions at the same time, you can't get anywhere near that kind of throughput with a relational database. That's the main problem that we set out to solve because we saw a lot of systems where the transaction processing was complex, right? And and a lot of it's popular now to use an object relational framework... Object relational mapping framework like Entity framework for example. And so what you're doing there is for every business transaction, you're pulling some data from the database, right? And then you do the doing some stuff on the, on those entities, you're adding entities to the context you're, or you're, you're modifying existing your to removing and so on.

And then you're, then at the end of that transaction you need to save all these entities back to the database, right? And that's just kind of, that can become very slow and a if a, if your transactions are very complex, then it just, you can't do a single read. You might need to do multiple reads from the database and then do multiples, multiple transactions within a business transaction. So multiple database transactions for a single business transaction. Yeah. So, so I was part of a project where they were having a performance problems. So they had uh, they had a requirement that no, no transaction should take more than three seconds. So it was kind of a system where where people are working with data on the screen and then very complex relationships across the data. And when they make changes and saved then nothing could, nothing should take more than three seconds.

But things were going very slow. And a, I did some analysis and looked at the code and the code is very structured and well architectured according to the rules, a layered architecture, right? So the transactions arrive at the service or the requests arrive at the service layer and at that, at the service layer you start a transaction and then it will start pulling in some data using a components in the, in the data access layer and it will read some data and then it will write some data back. And then we'll read some more data from, from the database and write some things back. So, so the code was very structured, but there was kind of no control over how many round trips we're going back and forth to the database and the duration of the database transactions. I think since the most common transaction when we looked at them, they were, they could be doing two, three, 400 database round trips per business transaction. And that's kind of crazy because a database round trip can take over the take a number of milliseconds, right? And if you're doing hundreds of those right then, then you're over a few seconds per business transaction and then you're very close to this, a three second limit. So, so that's, that's, that's the kind of problems that we saw that we wanted to kind of work with in a different manner. Yeah. So that's, that's kind of where memstate comes from.

**Jamie**

So if I can unpack a lot of what you've said there and just sort of expand on a few things, the entire state of the application is in memory so that then you can, when your app closes or whatever, you can store that, that application state to desk in some way. And then when you start the output backup, it just sort of replays where it was to get to the sort of "now" state and as you're doing more requests and doing more business logic things is keeping a log of what you're doing and then, uh, dumping that to disc and then coming back up so that even if your app crashes, you're not having to, um, you know, recreate all of that business logic, all of those actions and everything to get back to that state where it previously had crashed, but hopefully this time it wont.

**Robert**

Yeah, that sounds kind of kind of accurate. I think maybe I got carried away a bit that we didn't explain the simple things, but yeah, that does a good explanation.

One way of sort of thinking about it is that you have an application but you don't have a database. So imagine a cache, a lot of people use a cache and the cache, it's something that you need because your database is so slow. If you're a bit cynical, that's a way to to view a cache. For example, cache everything in memory. So we have a cache, you have a dictionary and you put everything in there. And then when you want to change something, you update the cache immediately. So everything is in the cache and that means you never need to read from the actual database, right? So you're doing the transactions, the regular stuff, you're writing to your database, but at the same time you're keeping your, your cache in sync is, all of the data is in the cache.

So anything, anytime you need to query, you ask for data. It's always in the cache. It's, it's always up to date. That's one way of thinking about memstate. This is kind of like a cache, but not because it's the kind of, um, uh, cache is kind of a copy where you're keeping, so you're keeping data close because it's expensive to fetch. It's, it might be far away or it might be expensive to create or get into the shape that you need and need to work with it. But it's not a cache because it's the, it's the, it's your true source of, of data, right? The data that is in memory, that is the database, but it, but it disappears as soon as the process dies. And so you need some way to, to recreate it. And so when the system starts up, you replay all of the commands.

All the data is back in memory after that to the exact same state as when it went down. And so you really don't need a framework to do this kind of thing. But what memstate guarantees is [ACID transactions](https://en.wikipedia.org/wiki/ACID). It guarantees a concurrency. So when you were dealing with multiple transactions there won't there won't be any conflicts or concurrency conflicts. And so there's isolation between a concurrent transactions. They're automic and they're also durable. So we, uh, because they're, they're appended to the log and they're there, they're safe on disc before they're executed. Right. So we can, we have acid guarantees. Those are the four properties of transactions. You probably heard the acronym acid, right? Atomic, consistent, isolating and durable. We have those kinds of guarantees when you're updating the data in memory.

**Jamie**

So then how does that, that get persisted it back to your database or data store or something? Is that something that happens on shutdown of the app? It does a, a massive, hey, here are all of the things I need you to do database or is it more of a sort of rolling thing? So the app has been running for half an hour and there are no transactions running. Hey, quickly don't pay everything to the database or, you know, how does that all work?

**Robert**

Okay. No, that, that wouldn't work because, uh, to give a team durability for a database transaction before the memstate server tells a client, okay, we've saved this data, we've got you right? This transaction is, is safe. It needs to be stored in persistent storage before the server response to the client, right? Because otherwise if it says, okay, we got this, and then they immediately crashes, then that data is lost, right? And, and you, you can't do that, right? So you need to save it on disk first. And when that safe on disk, then you can process a transaction and then respond to the client. Right? So, so what it does is it takes each single change, which is a command. It's a command object, right? So, um, it's an object oriented model. So the changes are represented as command objects. And so, so you just, uh, you just create a command object and you execute it.

And when you execut it, the engine, the memstate engine will upend that command object to the log. And that log is, that's actually the backing store. So that could be postgres, it could be events store, it could be a file on the file system. So before it processes the transaction, it writes it to disk to persistent storage.

**Jamie**

Right. I see.

**Robert**

So each transaction is saved on the fly

**Jamie**

I think I confused myself earlier on when you were describing it. I think I thought that memstate it's between the user and the actual database on desk or as we are saying is I issue a command to say my command describes that we should find the user who's name is Jamie and change the user's name to Jeff. And before we do that add to the end memory data store. We stole the command that I issued to desk and then do it to the data store and then say it to the user. Yep, that's done. So that then the next time the app starts, it will replay all of those actions and one of those actions will be find the user who's name is Jamie and change it to Jeff. And then it's then assisted into what load it back into memory in that state of the app is reapplied there.

**Robert**

That that's a, that was a very good description.

### Using memstate

**Jamie**

Using memstate I guess requires a, a bit of rethinking as to how your app is meant to work. I mean you mentioned a few times then about using command, um, objects. So, I guess, does that mean that that memstate leans towards a command pattern or is it just a case of you can still use a standard sort of nTier or onion architecture or whatever pattern you like, even maybe a singleton pattern, please don't use singleton as a pattern for your, for your app. And then as long as it can send something that represents a command to be run on that database.

**Robert**

Yeah. Well, so, you know, the command pattern is, it's kind of forced because it's so, it's a framework. So, so your command to objects that need to inherit from a command class.

**Jamie**

Sure.

**Robert**

Okay. And, uh, some of the, some of the fields on this command class are, well, there's an id for the command, which is a GUID and that's just to guarantee that we don't execute the same command multiple times and so on. Right?

**Jamie**

Sure.

**Robert**

Yeah. So uniquely identify the commands and, uh, also with, with replication, because you can have multiple memstate servers that, uh, that have the same state in memory. And of course then you need to keep track of which commands you have executed in which are, are not executing as well. And also for correlation when, uh, when we execute a command and need to tell the client we need to, yeah, we use the id.

So there's an ID and there's a, there's a sequence number also on the, on the base class because uh, the sequence of commands is it's an unbroken sequence of commands and they're numbered, right? So, so each command has the a version property when the for the first one starts with one and so on. So it's an increasing sequence. Yeah. And so we have some dates also some timestamps.

Okay. On the base class or, so what you do is you create a subclass, and let's run with your example there. Your subclass would be called a change user name command for example. Yeah. Which inherits from command and then what you do is you, then you create two properties. One property would be the ID of the user for which we are changing the name and the other property would be a name okay? Or the new name. Okay.

So we've got two properties on the command object and then you override the execute method on the command. So there's a command pattern there. So we have, you have a command object which has an execute method and you pass that object to the engine and the engine will execute that call. The execute method within a transaction. Okay.

**Jamie**

Okay.

**Robert**

So you're handing over the command objects for execution and you can, you can actually create the command object on a client. So that could be a windows client or a inside an asp .Net web application. You can send the command object to a memstate state server. Okay. Since you're passing an object around a command object, which is executable inside executed method, there's an argument pass to the execute method and that is the entire data model, right?

So the engine has a reference to the, to the data model, which no one else has access to. You cannot access the data immediately, but you need to, you can only access it through a command object or a query object. So inside the execute method you have, you have an argument which has a reference to the model. And let's say that the model is a dictionary of int to user. So in our example of the change user name command, the inside the execute method, you would look up the user with the ID that we have as an as a, um, a property on the, on the command object and find that a user object. And then we will change that user object and then we're done. Right? So that's that that happens inside the execute method.

**Jamie**

This is the data, the, the entity I want you to find here is how to change it. Here is the field I want you to change. Go and do this thing.

**Robert**

Yeah, exactly. And it's, it's all C# or, or some other .Net language if you prefer that.

**Jamie**

Okay

**Robert**

So that's pretty cool. You write everything in C#, so there's no SQL, you don't have to type any T-SQL. You don't have to do store procedures and so on, but you can do very complex logic if you like. So you have the full power of the framework at your disposal inside the execute method. So that's pretty cool.

**Jamie**

There have been times where I've had to do some operation in SQL and I thought to myself, can I not just use or for loop and just get all of these things, you know? And, and it is possible. You just have to translate the syntax. But it's knowing that syntax and how it all works. But yeah, I guess being able to use their core CLR languages to drive your database makes it a lot simpler for, well, for everyone I guess. That's really cool.

### Gracefully Shutting Down and Restarting

**Jamie**

So then when you come to, uh, let's say you have a memstate application runnning and it has, you know, there's hundreds of users hitting it, doing stuff, things are being changed, things are being queried for, you know, things are being updated and deleted. And then after, I don't know, six months, the app clauses gracefully and then I need to start it back up again. Presumably it's going to take awhile to reapply all of those six months of commands into memory, right?

**Robert**

Well, no, not really. It's a, it sounds like that could be difficult, could take a lot of time, but it's actually pretty quick because when you're doing your reading, all these command objects from, from a sequential log on disk and out there and you can get, you can get kind of good throughput when you reading data for sequentially from disk, even spinning hard drives can be a very fast, they can, they can actually be faster than SSDs I think if you're reading sequentially. Okay. So you can get a loan. That's the bottleneck when you're rebuilding the in memory state.

Well, I have some applications that they've been running for six or seven years, right. And they're running constantly and sometimes we need to patch the machines and we need to take these, shut them down and bring them back up again. And so, uh, so, so we need to do this. Yeah. Sometimes. And let me see. Last time I checked, I think we had three or 4 million command objects. It's just a matter of minutes, 10 minutes to, uh, from when we start reading until the, the engine is online and available to respond to queries and process new transactions.

**Jamie**

Wow, okay. I guess in that aspect, your, you're limited to the amount of hard drive space and ram I guess that the server has access to.

**Robert**

Yeah, exactly. And so this pattern and uh, actually the pattern actually has a name that could, that could be good to know. And let me see. Martin Fowler, we all know who that is. He has a blog posts and where he talks about something called [memory image](https://martinfowler.com/bliki/MemoryImage.html), the memory image pattern.

So he has a blog post on that and I recommend everyone go, go read that. So Google for memory image. And uh, when you go back in time, you actually find even older references to, to the pattern. This is something that they did very early in embedded hardware for example, in, uh, in routers and switches and so on. Because you need to have a lot of data, you need to be able to route things very quickly. You can't have a relational database or read your routing tables from disk and so on, right inside a router or switch. So, so it's very common to keep the data in memory and also say changes transactionally sort of says this and this approach to persistence is actually very old. And uh, I started playing around with this all during the 90s, right. So before 2000, this is one of the earliest things I've, I did at that time. How much memory do did we have in a machine? Almost nothing here. What do you remember your first computer?

**Jamie**

Oh yeah. Now you're going back some. So, um, it was before the days of Windows I had wasn't known as an [Amstrad CPC 464](https://www.wafflingtaylors.rocks/2017/03/03/our-first-computer-amstrad-cpc-464/) right? And I'm just literally going to look it up whilst I'm talking to find out exactly how much ram it had. Uh, and it had 64k yeah, 64K of ram.

**Robert**

Seriously? Well, it wasn't an Intel machine was it with, with the...?

**Jamie**

These were released in it, the 80s as a home PC, the Commodore 64 and things like that. But the first home PC we had maybe had maybe a megabyte or two of yeah, it was an old Windows 3.1 machine.

**Robert**

Yeah, exactly. Yeah. So that's kind of crazy because we have, we have thousands of times more memory in a normal laptop today. That's kind of crazy, isn't it?

**Jamie**

Yeah.

**Robert**

So this idea wasn't really useful during the eighties or nineties because we had so little ram to play with, right? So you couldn't, you couldn't possibly fit all your data in ram at that point in time. But towards the end of the nineties, we were getting more and more memory and then it became possible to keep all the data in memory as the amount of memory increased. And then there was a bold person, a guy from Brazil, I forgot his name now, sorry about that. He said that, um, the amount of memory will increase faster than the amount of, uh, than the size of your data. Right? So, so he's, he kind of postulated that, uh, now we're home free and this is the, this is the best way to keep data and that relational databases are obsolete. And he said this already around year 2000/2001 I think. Yeah. And so, and so they built the framework in Java. That's when the Java world, they had something called [Prevayler](http://prevayler.org/) and that's the framework that, that uses the same memory image pattern. But no one believed him. They said he was crazy and now they say I'm crazy.

**Jamie**

Well, you know, they said a lot of very smart people were crazy. So, you know, maybe there's a pattern there.

**Robert**

I think we're very fond of doing things the way we always have done and it's, it's kind of comfortable to, to, to stick with what we know. But it can be very rewarding if you try to go outside of the box.

The relational database architecture itself, it's kind of a solution to this problem that we have very small amounts of ram or that we had, right. So the, the first relational database we'll say, if we look at, say Oracle. Oracle was new in the beginning of the eighties and there's an example of it running on a machine with, I think they had one megabyte of Ram, but that was a lot of memory at that point in time. And it costs, I think it costs millions of dollars, that machine, and that was because it had so much memory, a megabyte of Ram during the 80s the relational data'sarchitecture. It's a solution to that problem, right?

That we need to provide ram access to the data. But if you, if you're reading random access to a disk, a slow disk, then then you can't get any throughput. Yeah. That will be very, very slow. So you can, you can hardly build applications by caching these data pages in memory or do you, I don't know if you're familiar with, um, the architecture. If you look at SQL Server with the buffer manager and the, and the data pages and so on and how all this works is, it's kind of an amazing piece of engineering, but it's, it's, it was kind of a, it solves a problem that that doesn't exist anymore.

**Jamie**

Okay.

**Robert**

Yeah. So, so, so I would say, I would say that the architecture itself is obsolete, but the, the culture around it, of course it is not right? We had, there's a lot of, uh, knowledge invested in it. There's a lot of infrastructure. There's a lot of, uh, politics, right? This is a huge ecosystem with a relational databases and it's not really going away anytime soon, but it is obsolete. It's not the smartest way to, to work with data. So it was smart for 30 years ago because it solved a problem, but that problem doesn't exist anymore.

**Jamie**

That's a really good point. Yeah. I mean, obviously my question was, you know do you need I need all of this hard drive space and ram, but we have essentially compute on tap now you know, we can pull up and as your instance or an AWS instance or a Google instance or digital ocean, linode and whatever, you know, name your, your infrastructure as a service company and you could pull up an instance of whatever you want with as much ram and hard drive as you'd like within minutes.

**Robert**

Exactly. But you have to pay if you want to beefy, uh, that our instance on AWS, you'll have to, people have to pay a bit. And that's one of the drawbacks here because if you're keeping all their data in memory, that's good. If you need to access all of the data all of the time, right? If we're reading all of the bits of data almost all of the time, then it's, and you needed fast there, then that's a good, that's a good fit for memstate.

 But let's say that you have an instance that's with a 200 gigabytes of Ram and you're using almost all of that ram for your data, but you're only accessing five or 10% of it during the day. Yeah. Then you're kind of paying a lot for that memory and you're not really utilizing it. But if you have on prem servers and they then it's a, then the ram is cheaper. It's kind of an expensive in the cloud with uh, with the, the bigger servers with a lot of ram.

### Segmenting "Hot" and "Cold Data

**Jamie**

Does memstate allow me to almost kind of segregate the data and say, okay, this is this chunk of data here, these 5 million records are the most requested records. Let's have those and their history and memory and all that kind of thing, but have maybe a data store behind it with, you know, all of our extra data, all the rest of the data, the remaining data that we don't actually access often, is that something that memstate can do?

**Robert**

Well, there's a, there's nothing built in that will do that for you, but you, so you have to yourself. So if you have a dictionary with, uh, with things in it, say users that can be logged on users, right? And so when a user logs off, then you remove the user from the dictionary. So you kind of, uh, the size of the data would be all of the users that are logged out and maybe not all of the users that have existed for the complete history of time. Right?

**Jamie**

Yeah. I mean, you could have, like you say, if you've got a system that's been running for seven or eight years, you're going to have millions, hopefully millions of users. Um, but today you may only have 12,000 users. You only need those 12,000 users in memory, I guess today.

**Robert**

Yeah. The active users.

And maybe maybe managing users is not a good fit either because that's kind of, that's not data that you're accessing extremely quickly. So, so managing all of your users and their data, so data that you access frequently, frequently we'll be a good fit that you have many reads and a lot of updates and there's a lot of contention, right? So a lot of, uh, transactions that need access to multiple bits of data at the same time. That's a good fit for him for in memory. I would say.

For example, let's see, let's take some ecommerce, the for for example. So if I go to an ecommerce site and I put some stuff in the, in the basket, right? And then I check out. So the, the baskets in and, and my activities during the session would be a fit to keep in, in memory, right? So all of the users that are currently online or have something in a basket at this point in time, that's, that's the data that you would keep in memory. But then when they check out and place the order, then that kind of becomes history or goes into some kind of a processing system. The order processing or workflow, right. We're with, with delivery and credit checks and invoicing and payments and so on. That's a different kind of flow. But the sales process, when I'm checking out, that would be a good fit for in memory.

Also the inventory levels, right? So if we, if we have three items in stock and two people are trying to buy first and four items, yeah, you can oversell. But if you keep the all the inventory in stock, then you could capture that kind of thing. Yeah. When, when there's a conflict, when there's not enough in stock.

**Jamie**

I like it. Yeah. Cause then you don't have the round trip to go back to the data store to get the current quantity subtract by two. Oh wait, now you know Jamie and Robert have both checked out at the same time. We have to then fight to get to the database faster for Robert's transaction to go through and mine to be refused. Whereas, because it's all in memory, as soon as I had, as soon as we both hit checkout and hits the in memory store, then bounces back straight away rather than going all the way through the database and all the way back.

**Robert**

Yeah, exactly. A lot of these e-commerce sites, they have a legacy systems and they can't respond that quickly to, to, to inventory and the inventory might not be even up to date. Right? Because there might be some orders in the pipeline and, and everything just so slow and complicated, so, so it's kind of impossible to, to show online and the exact inventory. But it, I think it would, it could be a business, a benefit if you could show those, uh, the, the exact inventory at any given point in time, right. Because it's, it's not fun to make an order and you think you're getting something tomorrow, but the, then it, they didn't have it in stock and you have to wait a week. They might tell you after you place the order because they're there, they really want your order. Right. And so they'll let you place the order and then they'll tell you a little bit later that, uh, it might be delayed.

**Jamie**

I had something very similar, very recently as we're recording. So the tail end of 2018 and I ordered a custom PC. I have built them in the past. I just don't get the time in these days to put them all together myself. So I went on to a specific, very reputable website for ordering a custom PC designed the entire system. Picked out a case, picked out the motherboard, the, the specific ram and all that kind of stuff, and then hit order. And then four days later they said, oh yeah, we don't have the case or the PSU or the motherboard. So you don't have to wait an extra two days. But for me it's two days. But for someone who needs the machine right now, maybe it's an important purchase for our company. Maybe it's an emergency purchase for something, I don't know. Then yeah, it makes sense to have the most recent quantities of items being displayed to the user.

### Real World Examples

**Robert**

We did a back of the envelope of the calculation during a training course a few weeks ago where we took some examples.

I'm from Sweden, so I like to use Ikea as an example. Pretty big company, right? So they have a lot of products, right? And they have a lot of warehouses and they have a lot of online, uh, and sales, something that you have a lot of sales on-site.

So, so what we did is we kind of estimated the number of products are the number of warehouses and then kind of projected to see how much memory would we need to keep all of this in memory in a single node. And that's doable. All of Ikea's warehouses, all of the products and all of the inventory in all of the warehouses. You could easily create an object oriented model for that. Could do that in a few hours I think.

And you could use that to represent everything in just a few gigabytes of memory. I mean, data, the important data doesn't take up that much space. And you can choose what kind of data you want to keep in memory. I mean, you don't need to keep everything. You don't need to keep product descriptions that are uh, yeah, two megabytes of text and the images and so on. Right. You don't need to keep all of that in memory. You can keep the important data and do so the product ids and inventories and the names and so on, and then you can keep, so the, the other data out of bound everything doesn't need to be in memory. Having that as a backend for Ikea's e-commerce that could easily be served with just a few servers globally.

**Jamie**

That's all in memstate, then? We can do all of that rather than storing it in a relational database. Yeah. When you first say it, all of Ikea's warehouses and stock levels and you know, stores and all this kinds of stuff, it doesn't sound like a lot, but then you realize that they are a multinational.

**Robert**

Yeah. Well I think we be counted to hundreds of thousands of products and they may be hundreds or thousands of warehouses or stores are around. It's not an enormous amount of data.

Working with another company. I'm a co founder and what we do is we collect news information in environmental topics, so global warming, so and climate and a 50 other topics within the environmental field. So I'm working with the, with the journalist, we collect these news articles and we put them in an index so they're searchable. And then we do some curated newsletters and we also provide access to, to this, uh, database of articles to people that work with environmental questions. And we started in 1997 and, uh, everything from that database. So we're collecting thousands of articles every day. No, not really hundreds. I would say hundreds. So we're approaching a thousand per day. So we're collecting articles globally in English and Swedish and a few other languages.

So we using a crawler to collect all this data and push it into, we started out with relational database, but we, we switched over to keeping everything in memory and all the data. Right? So all of these articles that we've been collecting for, for 20 years and all the customers and every newsletter that we send, every time someone clicks a link in the newsletter, right? We're tracking all this, all this data fits in memory.

We're not keeping the entire body of the each article, but we're keeping all the keywords rights. We're, we're indexing all of the interesting words in all of the articles and we're also creating summaries. So every article has a title and a summary. And the summary is kind of short, could be a hundred or 200 words. And all these articles are in memory. So the summaries and the search and the search index and all the customers and everything.

And it doesn't, it doesn't take a lot of memory. What's that guy's name that does the funny stuff on Java script? He did some kind of either the video where he's mocking Javascript, Gary Bernard, Bernard? I've heard him say, give me your money and then I'll tell you that your data fits in ram, I think he had the, there was some kind of website where you can enter how much data you have and then it will say your data fits in ram.

And then kind of becomes simple, right? Because if you have your data in Hadoop or something and then you're doing, um, [MapReduce](https://en.wikipedia.org/wiki/MapReduce) queries over your data, that's extremely complex and that's great if you have petabytes of data or even more because that won't fit in ram. So, so then you need some kind of clever way to deal with the data. But if your data fits in around that, it's kind of pointless to, to use that kind of the infrastructure. And then that's kind of his point. So there are a lot of people are doing, they think they're doing big data, but they don't have as much data as they think.

So terabytes of data could fit in ram. Do you know what the biggest instance is you can get on on Azure?

**Jamie**

Well, off the top of my head? I'm not sure.

**Robert**

What do you think? What's your guess?

**Jamie**

I know that I can get a 128 core machine, but I don't know Ram wise, I'm not sure.

**Robert**

Well, I'm pretty sure it's, it's over, over a gigabyte or over a, I'm sorry, over a terabyte thousand gigabytes. Yeah. You need to look off and because a, they're updating, they're adding new new instance sizes all the time.

So if you're doing a analysis, then you could, you could spin up some of these machines, expensive machines, you, you've proven your data and then you do your analysis queries or reporting or whatever, and then you, then you throw the machines away. That's a different approach than a, for example, using a MapReduce, Hadoop and so on. If the data fits. Yeah.

**Jamie**

Well I guess the only question that I have left at the moment is where can people go to find out more about you or more about memstate or anything like that? Any of the project you're working on that kind of thing?

**Robert**

Ok yeah, so GitHub is a, is a good place to look. And uh, I think if you, if you just Google for memstate that I think I, hopefully the spelling is, uh, is obvious from, from, from the pronunciation. Yeah. That was kind of a, the most important goal when choosing a name that we could pronounce it

So memstate. And there's, we have a webpage called [memstate.io](https://memstate.io). So that's one place to go, that that's a kind of a work in progress to that website. But [memstate on GitHub](https://github.com/DevrexLabs/memstate) is probably the best place to look.

So the code is there, it's open source. If you look at the organization that memstate is a part of, we have multiple, a repository. So we have a [memstate tutorial](https://github.com/DevrexLabs/memstate-tutorial) and that's a great place to start. So the tutorial is a step by step, uh, a guide to building something similar to Twitter, right? You were building your own Twitter from scratch. And I think I have some of the domain modeling. You start with some of the domain modelling, but then you add the commands and the queries and you create the main model and so on. So it's, it's, it's, it's, it's a good way to learn, I would say. Kind of Nice.

And, uh, I'm on Twitter, [@robertfriberg](https://twitter.com/robertfriberg)

**Jamie**

I'll share that. And the um, GitHub page for memstate and the GitHub for the tutorial for building at Twitter, Twitter clone. Definitely.

**Robert**

Yeah. And so anyone, feel free to get in touch on Twitter. I like to, I like to engage. Right. If you have any questions or any feedback, that would be great.

Also, we're on [Gitter](https://gitter.im/memstate/). We chat on gitter. I think there's a link to that from, from uh, yeah, but if you want to chat with us or the team there that's building it or some other users then so we have a chat for that.

**Jamie**

Great. I'll make sure that I put all of these links into the show notes for sure.

Thank you very much, Robert, for joining us in this wonderful discussion about a memory databases and memstate and how that works. That's, it's been very educational. I really appreciated that. Thank you very much.

**Robert**

Okay, thanks.

### Wrapping Up

That was my interview with Robert Friberg. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and a full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/).

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Sign up for the mailing list](https://buttondown.email/dotnetcoreshow/)
- [Join the Slack group](https://join.slack.com/t/thenetcoreshow/shared_invite/enQtNjIwNDY1NDk4MTE3LTM3NWZiMDAxMWVlMDQyZGU3NDAyYzgyY2EwYjk2MmZlMjU2NDI4YTNjYzVlZDc2YzYxMDExYjFhZjYzMThlMDM)
- [Support the show on Patreon](https://www.patreon.com/TheDotNetCorePodcast)
- [Robert on Twitter](https://twitter.com/robertfriberg)
- [Devrex Labs](https://devrex.se)
- [Cynical Developer](https://cynicaldeveloper.com)
- [ACID transactions](https://en.wikipedia.org/wiki/ACID)
- [Memory Image Pattern](https://martinfowler.com/bliki/MemoryImage.html)
- An article I wrote about the [Amstrad CPC 464](https://www.wafflingtaylors.rocks/2017/03/03/our-first-computer-amstrad-cpc-464/)
- [Prevayler](http://prevayler.org/)
- [MapReduce](https://en.wikipedia.org/wiki/MapReduce)
- [memstate.io](https://memstate.io)
- [memstate on GitHub](https://github.com/DevrexLabs/memstate)
- [memstate tutorial](https://github.com/DevrexLabs/memstate-tutorial)
- [Gitter](https://gitter.im/memstate/)
