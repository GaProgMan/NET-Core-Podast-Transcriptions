### Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is Episode 65: Marten DB With Jeremy Miller. In this episode I talked with Jeremy about Marten DB, what a document database is, how that differs from a relational database, and whether you should contemplate using a document database rather than a relational one.

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

{{< paracentre "The following is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

#### Jamie

So the first thing I'd like to say, Jeremy is Thank you ever so much for spending some time with with us today. I know that you know, time zones don't make things 100% easy. And I know that it's rather early in the morning for you. So thank you ever so much for wanting to spend part of your early morning with, with me and the listeners. And thank you ever so much for agreeing to be on the show as well.

#### Jeremy

Oh, thank you so much for reaching out. Any any chance to talk? Martin? We'll take it every time.

#### Jamie

Excellent stuff. Excellent. So we'll come on to what Martin is in a little bit. But I was wondering for the listeners, could you perhaps give us a brief overview of like, like a bio, like who you are the work you do that kind of thing?

#### Jeremy

Sure. So I'm Jeremy Miller. I'm a senior software architect at kalvista software and Austin. We're a custom software development shop maso, the author of several open source tools and the dotnet space, you may or may not not have heard of any. I wrote structure map that was the first IOC container and dotnet. I'm one of the lead developers and the core maintainer. So Martin, that we're going to talk about today, and a couple other things along the way.

#### Jamie

Excellent, thank you. And we're gonna talk about what we've said a bunch of times are going to talk a bit about Martin. Now, I throw my, my sort of professional career, I've only ever interacted with a sequel based database. So I know that Martin, I'm gonna let you describe it in a moment. But I know that Martin is a document based database, although I know like the theory of what, what that entails and how it all works. I have absolutely no experience of of that in real life. So I apologise in advance. In case I ask any kind of silly questions that you thinking, Oh, well, you know, you should know this do me, because I really don't know No, no,

#### Jeremy

that's okay. So in relational database that all of us have used at some point in time, most of those are probably still using today, most of us will probably be using in 10 years, because it's so entrenched. Data is organised in terms of tables have columns and rows, it is a two dimensional piece of data. And the world is much more complicated than that. So of course, you know, an order has ordered details a person has dependents has these things with these things. So then you start to pick up relationships between tables. But you're still working really hard to represent your world as tables, columns, rows, so on and so forth. That's great. It's awesome for reporting, it was fantastic for some of the early work I did in my career, like supply chain work or ordering parts, it's like that. But in the real world, when you're talking about now, the behaviour of my code, the world is hierarchical. I may have a user but I have types of user, I have parts, but I have different parts. Or, God forbid, if you get into financial software, when you represent trades, in the finance world, each kind of trade has a totally different set of set of data. But yet, you still want to try to fit that to relational database. And things get start getting really nasty as problem domains can places where maybe you have a lot polymorphism maybe have very deep hierarchies. One of the projects kalvista works on right now. Our clients problem domain is a everything relates to a top level entity, just call them a person, but that person has up to two or three dozen other kinds of related entities. And breaking that down into and mapping that to a relational database, you run into the old impedance mismatch of the way that data wants to be shaped in your code where it's all about behaviour becomes very different than how the relational database forces you to structure. So here I'm trying to prove out that relational database is not not the end all be all for some some problem domains. So in a document database, what we're trying to do is we're trying to persist that that person, basically just the way it is, and bypass a lot of this mapping. So taking the example of Martin and Martin sits right on top Oh no. We can talk about why Martin sits on top of the PostgreSQL database. But what what Martin's doing is it's taking your objects instead of mapping into individual columns, tables, whatnot. It's JSON serialised. Seeing your document and stuffing that a database somewhere. So all your mapping problems go away, as long as it's JSON serializable, you're good to go.

#### Jamie

Oh, fantastic. I do like that idea. because like you said, there are just some things that cannot be easily maintained in that sort of relational status where there are only so many foreign keys and join tables and all sorts of craziness like that until you stop pulling, at least in my instance, pulling was left of your hair out, trying to figure it out, how do I get this data and that data? And then, you know, you look at Entity Framework, and you end up pulling the entire object graph back and all you want is one piece of data and we'll get a bit. Yeah, a bit much to, to have to organise, I guess, keeping your head as well. If you've got 15 different tables, and they're all interrelated. You have to be able to keep all of that, if not in your head on a piece of paper, and explain it to someone else, right?

#### Jeremy

Yes.

#### Jamie

Excellent. Okay. So you're saying that Martin DB, I can just give it if my like you said, you know, if your object is JSON serializable I just either do a JSON serialise it or just keep it to mountain it handles.

#### Jeremy

You tell Martin, you tell Martin, I want you to store this object. And there's there's a few there's a few extra requirements, Martin has to figure out what the identity is of your object easily just as long as you have an ID property, your field. And you can override this with explosive stuff if you absolutely have to be special and different and people do. But as long as Martin can figure out what the identity is, and it can be serialised to JSON, that's it, that's enough, Martin will take care of everything else for you. Moreover, Martin, Postgres has special up cert, absurd capability, where it's very efficient to do absurd. So we don't even make you care. We don't even make you tell Martin, unless you really want to whether it's an insert or an update, it's just, I want to persist this. And Martin will get the ID for you. It'll sign it if it has to, just like you used to with the EF core, and it'll persist it to the right table. If you're working in development time. With development mode on martin No, build the necessary underlying tables by itself for you on the fly. So you can focus on getting stuff done thinking about your problem domain, evolve your, your model objects as as you need to. And don't even think about database migrations or structure or anything like that. Just go on what you're really trying to

#### Jamie

do. I really like that the amount of times when I've been interacting with a relational database and with Entity Framework, and you know, you make some change, and you'll be working for several hours to implement some new field or something, and you've implemented everything and then you hit go, and it all fell all fails falls over miserably, because you've forgotten to create a migration or because your migration failed, because maybe you're using SQL lite or MySQL, rather than Ms. SQL. And some field isn't supported somewhere. And it all goes a bit wobbly. And you're sat there for hours go, why isn't this just just write the data.

#### Jeremy

But they're done that man? Yep.

#### Jamie

Excellent. Okay. So. So let's talk about that there's a backing store then. So Martin communicates with Postgres.

#### Jeremy

Yeah. So Martin, be really clear. Mark DB is a fancy data access library. It's completely completely passive. all the heavy lifting work is done with PostgreSQL. And we do that on purpose. I'll just, I'll just step ahead to the inevitable question. Why is it on Postgres and not SQL Server? Since we are a Microsoft shop? So Postgres has some unusual JSON support for a database that that goes way beyond what everybody else does. There's a binary format, it's actually in a binary format called JSON B. So your JSON document is kind of pre parsed out in a binary format internally. So query within a document is much faster. There are a lot more operators for querying inside the JSON document that we have to use to give Martin its its link provider support. And Postgres has a lot of facilities for indexing, a JSON document for for searching. So all that kind of database indexing that you expect today of Hey, I am always querying on this one field or this combination of fields. We still have the ability within Martin because of Postgres support to give you computed or calculated indexes within that that document so everything is still fast, the way that you you're used to You're expected

#### Jamie

to be sure show that you did preempt one of my questions. And that was why Postgres? Yeah,

I can tell you've done this a lot.

#### Jeremy

We very much know that Martin could probably have much higher adoption rates, if we were able to support SQL Server. And we do pay attention to SQL servers, it's clearly improving its own JSON support. But we don't think it's quite there yet. We may try to bite the bullet with an alarm next couple of years and support subset of Martin but Martin was very purposely put on Postgres for a reason.

#### Jamie

That's fair enough. He used the what's the what's the phrase I'm looking for? Use the best tool for the job with best being in money quotes, right? Because the best available right now. Excellent. So he said that I take my I take my object in, in C sharp or dotnet. Land, we'll come on to that in a moment. You take your object in dotnet, land, your poco, or whatever. And you say, to Martin gusto this month, and then communicates with Postgres does some JSON magic, and some binary data gets dumped into the database, right?

#### Jeremy

Yes, yes. But by default, this can be replaced, but by default, it's, it's using Newton, soft JSON. What, like, almost everything else

#### Jamie

here. It's become one of those ubiquitous languages, you kind of can't do at least ASP Well, you couldn't for a while, do ASP dotnet core without using Newton soft because it was actually a dependency on I believe, ASP. NET Core two. So totally makes sense, right? It's quite easily the best JSON parser out there for dotnet. And, you know, covers even, like partially corrected JSON and stuff like that. It's kind of self healing in that aspect. Because it's had a small core team of people working on it for, I want to say about a decade now, but I don't think that's quite right. But

#### Jeremy

I think it probably is. So it is, it is definitely not the fastest serializer, we've been able to clock out, Gil jL as much faster supporting Martin. But Newton soft, has the quality of everything just works and all the other serializers, eventually you hit some some kind of problem with it.

#### Jamie

Sure. I guess from your point of view, as a sort of tools designer, you can't guarantee that the JSON pass to Martin will be standard compliant, or it won't fit into one of these corner cases where, you know, Gil can do maybe 99% of everything. And then somebody tries to store some mission critical data without ever having tested it. Jill falls over. And then you get a bunch of really nasty emails at two o'clock in the morning, my entire enterprise has fallen to pieces, because I never tested it. And it's all your fault.

#### Jeremy

So yes, exactly that. Hopefully you would test it before you got into production, though, hopefully.

#### Jamie

Fair enough. Because my other question was going to be around this sort of area is, obviously if you're storing JSON in a database, to be able to search on that you've got to either I mean, I don't know how Postgres works, but you've either got to be able to do some kind of text manipulation in the database, or, or really back out, read everything out. Hopefully, you have infinite amount of memory, pause everything, or rather deserialize everything, and then search on properties, right, but you're saying the Postgres has this ability to sort of binary if I, for one of a better word,

#### Jeremy

yes. So older, Postgres before Postgres 12. They have their own custom operators to retrieve a, you know, a single piece of data within the JSON and compare. So when you're querying against the Martin data store, most of the time, you probably looking at a document by its ID, that that's easy. But if you're saying I want to reach in, I want to find all the documents where this child child Prop, child pop child prop equals this. So we provide a a link provider on top top of Martin, that's turning parsing the link expressions, you know, doing all that munching and that's creating a sequel string that knows how to use Postgres own stuff to reach in and query within the document. We try as much as possible, we try to hide that kind of kind of detail from you, the the older Postgres operators aren't super friendly, you don't really want to use those. So for the most part, we're letting you use link with Postgres b 12. There is a new industry standard called sequel slash JSON. As more databases adopt dot JSON, it's allowing us JSON path operators to query within stored JSON documents in the database and then It gets to the point where it's user friendly enough that you could actually use it yourself. So we have some helpers that kind of straddle the line of if there's something Linc can't do for you. And in Martin, we've got a helper that lets you use SQL fragments to query within documents as well. And that's much more valuable when you hit newer versions of Postgres that supports that JSON path model.

#### Jamie

Searching. See? I say, Yeah, because that was going to be Yeah, that That, to me is an important thing. But I can actually query that data in a very performant way. Because Yeah, as good as straight text manipulation is, I don't want to have to, like, do JSON traversal. Because I'm getting flashbacks, I'm doing an XML traversal. And I'm just No, no. And

#### Jeremy

at this point, a dotnet. developer is expecting a link provider. And that's something that's been a little soft, we don't have, I mean, we're a little Rebel Alliance project, we don't have the same breath of the EF core team. But that's something ongoing, we're deep into a v4 release. And we're making a lot of improvements to the link provider to fill in the gaps of what things work and don't work. But that's what a dotnet developer expects right now. So that's what we're gonna try to get him

#### Jamie

to show that makes sense. And yeah, I guess it gives. So. Okay, so if I have a pre existing application, and it has some database technology, and let's say, I'm using Entity Framework, it's not going to be a trivial job to just swap out for MongoDB. Is it? Or is it because you said earlier, and if you're in development mode, it can do all of the database migrations for you.

#### Jeremy

And it can.

So if you were picking up strictly from if you're switching over just development, it may not be that bad to switch for me, of course, to Martin, but in the real world, you have all your existing data. And that that one I won't I won't oversold sell that you would have to write something yourself that loads all those objects in the memory. And then let's Barton persisted off the side. That was not not gonna be clean.

#### Jamie

Sure, yeah. So but let's say I'm Greenfield projects, right? I'm starting something brand new, then three days into it. And I think maybe this isn't for me, I want to swap it out for for Martin and Postgres, I can just maybe spend an afternoon a day a couple of days.

#### Jeremy

If you're comfortable with Postgres, yeah, you're gonna be able to do that. And Postgres is a much as much smaller binary footprint in SQL Server. So spinning up a Postgres Docker container just for development is like that. Yeah, you'd be able to switch over. And we finally finally got to got it together. In the last couple months, we have the pretty standard obligatory extension methods off the generic host builder. So if you're on dotnet, core, two or three, that pattern that pretty well, everybody's going to have to fall from right now extension methods right off of host builder or the service collection, to have a very similar bootstrapping. We have that now. So you can add Martin much faster to a dotnet core application than you could three or four years ago, where it was still a little bit of piecing it together, because every type of framework had a totally different bootstrapping.

#### Jamie

Okay, so let's talk about the the data that I can store, you know, we talked earlier on about you have this, maybe have a relational database, and you've got a couple of foreign keys and a join table, a one to one and a one to many, and a many to many, and all these kinds of hundreds of things. What I'm getting from what you're saying is, obviously, if I have some big complex map in a relational database, give that to Entity Framework. And I've told it, where the identity keys and stuff are, you will take that out, and it will split out and it will say, this part of the object goes into this table, this part of the object goes into that table, and it will figure all that out for me. But because I'm giving a JSON blob to Martin and it's doing some communicating with Postgres, is it literally just that JSON blob as it is goes into the database, or is there some splitting out and separating or

#### Jeremy

no, it's that JSON blob goes in and you know, it's a it's not a silver bullet Martin works best any document database is going to work best when you have the these pop level entities that are relatively isolated from each other other types of documents. We have some limited ability to we can still let you utilise foreign keys between documents. But if you're getting to the point where that kind of relationship is that important, then you probably are better off going back to it. bf with a relational database. But yeah, if if you can be thinking mostly in terms of entities that are at hierarchies that are isolated from each other, there's nothing else going on, you just give it to Martin, as long as you are JSON serializable, you're good to go.

#### Jamie

Okay, so I'm just trying to think of any examples I can come up with of data types, maybe not data types was wrong, wrong word. But like, any kind of data that I can come up with off the top of my head that I would that I would store in a document rather than a relational table, because document databases, like I say, it's still kind of new to me. So I'm just trying to think, are there any examples you can think of top of your head that are great for document versus relational

I, so any

#### Jeremy

place we have a lot of polymorphism.

So I brought up the the financial trades, getting into energy trades, where anything or financial, where different kinds of trades have, there's some properties in in, in common, but they have very different properties underneath that different child collections. Sometimes you will look at them as the same thing. Sometimes you don't, maybe there's a lot of variable in the structure, the way that we persist things with Martin, it can wallpaper over hierarchies like that very easily. there's not as much energy in creating that map to the relational, that's where something like Martin really takes off off, or any kind of any kind of operation like a system I was trying to describe. We have a work now where we have a top level entity and Entity Framework, and literally about 25 to 30 related entities that hang off of that in terms of collections, you know, what is this person doing in this year, this season, so on and so forth. And very frequently, we need some subset of that. So the amount of time you spend thinking about eager loading, lazy loading, including this document, including that we're spending a lot of time telling you, of course what to do to make it make it fast. If we were using Martin, we probably pull the whole thing. But what we'll be doing is behind the scenes, were making one query by the primary key and grabbing one quick JSON blob really fast. And then letting the optimised serializer. Bring it to us. So all that mental overhead of how do I optimise this data access as I go in this deep, deep, rich hierarchy of objects? Martin just cuts off through that and makes a lot of that worry go away? You know, for me, I would tell people in a simpler system, I don't think it matters very much. But as soon as your domain model starts to get more complicated, deep levels of this guy has a bunch of those guys, and those guys have a bunch of these these objects are there's a lot of polymorphism than a document databases is going to work much better, much faster, lower friction.

#### Jamie

Sure. That makes sense. And so then he talked earlier on about migrations can happen automatically in development mode.

What happens when I come to release them?

Yeah,

#### Jeremy

yeah, I'm just DBAs tend to not like having applications have rights to change themselves on the fly. We weird that way. This is part of Martin that was that's not not fun to work on or develop. But we have quite a few facilities to even command line support, especially now with the authentic core of Okay, this is the way the database is supposed to be these are the entities is supposed to know about things like these are the the indexes that the applications, find a foreign key relationships, just all these other things. Now compare that to this database that's running in production, if you can, or target whatever it is, and just give me a dummy out a Delta sequel file that will make the necessary updates table adds to bring the production database up to speed with where I'm supposed to be. So we built in a lot of that that work. You could run in development mode, where it just creates everything on the fly. But there's a potential that you could actually destroy things you can go down to lesser degrees of it's okay to add new things, but don't change anything that's existing, and so on and so forth, down to all the way of never make any kind of database changes on your own depend on somebody explicitly creating the migrations. So we've tried to work it that way where Martin can try to create its own migration files for you and then you plug that into One of our clients, we use Roundhouse, just as a way to tie database migrations, whatever migration tool you use, take the Up, up and down SQL files we generate and just plug it in, however you do your database migrations, and it mostly works. We have a little that something needs to get a lot better we have some support for say that you need to change your document structure. We have some support for doing transformations of document structure from another. And worst case, case scenario, Postgres supports running JSON JavaScript in the database, if you can't get away from JavaScript, so it's gonna follow you somewhere. The worst case scenario, you can write a JavaScript function, and we'll start and we'll slurp that up and use that to do the transformation inside the database.

#### Jamie

They see. They see. So there's lots of different options. And because that was, yeah, that was something I was concerned about, if I can only change the structure, the schema of the database, in, in in development mode, how's that going to work in production for you? Makes perfect sense. It just like you would with EF core, right?

#### Jeremy

Yeah, yeah.

It's the kind of thing that's kind of thing that separates us from being

Yeah, that's a cool, that's a cool development toy.

But I have to do serious grown up work. And we want Martin to be something that's very suitable for serious grown up, let's get paid for this work.

#### Jamie

Show. Yeah, you, it makes sense to go after that, rather than rather, to target that first. And then sort of be able to if you want to backpedal into let's look at this cool toy and play with it. Not to, not to, like, say the phrase, I'm looking for it not to sort of take away anything from the frameworks and libraries that are at the this is a cool toy. But obviously, you want people to be using it in production before they start, before people start playing around with it in their own free time, right? Because otherwise, if it's not ready for production, no one's ever going to use it.

#### Jeremy

Exactly. And this was built Martin was built to was built explicitly at one of my former employers, we build it explicitly to use in production.

#### Jamie

You can you can always tell, I think, at least I think you can always tell when you're using some kind of tool or framework, and it's like, if you really thought about how this is going to work in production, you know, in the real world.

#### Jeremy

Yeah. I mean, it's an open source author, the only way to really get your tool good at that, it's a little bit of a chicken and egg problem, you've got to have users that are willing to share feedback with you. And Martin spin, Martin's been a very good experience with that. margin is a feasible product to use because of how many early adopters we had and how much community feedback we've had over the last four or five years.

#### Jamie

Excellent. I do like that kidding. Almost like dogfooding it but sending ads, people ain't gonna try and build a real world application in this because if your tool only supports the sort of Hello, world, cleanroom Greenfield, we've just started a project, then you're not going to get as many people who are like, Hey, I'm supporting this thing. And I want a new way to, to communicate with his database that pre exists, the useful, but you're only supporting that I have a new database path that you're never going to get that user right

#### Jeremy

now that this is definitely correct. But at the same time, your hello world needs to be really easy and fast to get going. There were folks will not get to the grown up stuff that makes production possible.

#### Jamie

Absolutely, absolutely.

Okay, so you so we're talking at the time of recording, because there's a bit of time, machine time. Yeah, time recording, time cast pod machine, wibbly, wobbliness, to deal with, when things are recorded and when they're released. So the time of recording, you're gearing up for Martin version four. I was just wondering. So earlier on, I thought we could talk about Martin as if nobody's or other as if the listener hasn't heard of it, because I certainly haven't know of it. But now let's pretend I'm a Martin three wizard. What can I look forward to in Martin for?

Well, so

#### Jeremy

Well, let's say let's take it there's there's two main tracks of changes coming. So we've been talking about Martin is a document database. Martin also has a pretty substantial event sourcing, set of functionality. It fits very well. nicely, actually uses a lot of the same document database infrastructure. So two tracks here, what I'm what I'm personally most focused on now, and I need to, I need to get out of the way of everyone else soon, we're going through all the internals of Martin and looking for every possible place where, hey, we can reduce memory allocations, introduce dictionary lookups, generally looking for any place to simplify the internals, make it faster, making a big effort on the link provider, there are holes in the link late provider people, and people find them, you get enough people using your tool, they find the problems and the shortcomings, making a big leap and the capability of the link. There's some missing features a document database features that people expect that we haven't had in until now. But we've made some breakthroughs. And that one's on the way. The much bigger effort is the event sourcing functionality, that that's maybe unfortunately been popular. And people have a huge wish list of things they wish they supported. So we're making, I think, an order of magnitude improvement in Martin's event sourcing capability to to get ready for much more complicated scenarios, much bigger data loads, be able to scale people like the event sourcing and Martin, but they needed to be much more robust than than it has been until now. that those are the big changes.

#### Jamie

Excellent, excellent. Okay.

So Martin, Davey, brother Martin can can do event sourcing as well as be a database communication to an ORM. I mean, that's,

#### Jeremy

it's that Oh, and, you know, Martin is definitely not no RM. Okay, sorry. Nope, that's okay, that's kind of famous, I get I get touchy. So RM is a document database, and an event sourcing tool, the event sourcing part of Martin, the projected read side documents that you would expect out of sourcing, or just foreign documents. So that that was a, it was a nice little bit of synergy between the two, the two tools. But almost as a lark, honestly, we didn't need it at the time four or five years ago. But I had done a lot of experimentations at my job for using Postgres for actually a Node JS event store. And that project looked like it was all going to go completely to waste. So as irritated about it, so I just for fun, spent a couple of weeks and put basic event sourcing into Martin. Other people, the people that are now the other core contributors to Martin and community folks took that and turned that into something much, much larger than than what I had originally put in place. So that that has, surprisingly to me, I think, then what feels like the most popular part of Martin.

#### Jamie

Sure. Okay. So you're saying that you're taking the event sourcing and improving it? Is so my is it? Is it production ready at the moment? Could I would you would you know, I guess that's probably the right way

#### Jeremy

isn't production, so it better be production ready?

#### Jamie

Okay, because because my question was going to be, what should I feel confident building an event sourcing platform or platform that uses event sourcing with one DB and just go Yeah, switch or just leave it? I mean, obviously, I've got loads of tests everywhere. But

#### Jeremy

in a, in an application that doesn't have an extreme amount of events. But I've heard from at least one user that, that stores in the realm of millions of events a day and their system, a smaller to mid level system, I know that some people have had success with bigger, you know, the problem with a tool like this, and when you talk to one of the authors of a tool like that, I'm always focused on the problems, the problems in the places that need to be better. So yeah, you could do it today. But there, there are some missing things. We don't support document metadata. So for things like tracing the events to, you know, session ID or user ID, that that's coming up. Being able to do we have some support for asynchronous projections, you know, events are always flowing in and something behind the scenes is trying to catch up and rebuild the projections. With v4, we're going to make that cloud friendly. So instead of you being responsible for where is this projection building happening, you know, have things that support the do leader election to be able to work on clusters of boxes. Be able to do partition the event store. So you're looking at being able to move Martin into very, very large applications. You know, things like people say, hey, my, my retired projection and I changed it, I want to now rebuild it to this new model, which we can do. But as you want to use Martin in much bigger systems, we're kind of ways to usually optimise how that projection rebuilding goes, again, more of that grownup stuff, stuff you don't do when you're just playing with it. But when you're trying to use it for real grown up, pay me work, or growing up into that

#### Jamie

show that makes sense. I mean, everything you've said, so far makes me think that this is, and you said yourself only when you started out life as a real tool you were using. For one of your previous roles, it strikes me very much as this is something I want to make for enterprise users to use in their enterprise, or at least production users to start there. And then see what we can do to make it even more production, your enterprise II, which is refreshing. Yeah, it's a it's quite refreshing, because I see that so often, mostly in the JavaScript space, where someone will go, Oh, this great new framework is version one, and I've already deprecated it.

#### Jeremy

I'm aware, I know.

#### Jamie

Excellent. Okay. So what does the What does the future hold for Martin, and we've talked about version four. But it may be that this goes out after version four ships. It might be that this goes up before version four ships. I mean, this is more like a,

#### Jeremy

this is not this is not going to go out before.

#### Jamie

Fair enough. Okay. So like the, obviously, I want to make it very clear to any, anyone who's listening that anything, we're talking about these, like, wish list of things that you'd love for it to do. This is obviously me not tying you down to it, we'll do this. But this is like in an imaginary world where there are no time budgets, and you can write code for 72 hours straight without having to then lay down for a week. I mean, that's how I feel you feel. But if you lived in a world like that, what would be some of the things you would implement?

#### Jeremy

Sure. So I know, one of the things that the other core contributors, and I'm not the only core contributor, also a reason why Martin is turning into a grownup project, one of the things I know we would like to do, we need to find a way to make development sustainable. One way or another, it needs to produce a little bit of revenue of some kind. So that might be after v4, part of the four, it may be some paid commercial add ons, especially for things like making it cloud cloud ready, you know, here, here's an AWS recipe with support for dynamic clustering, the event sourcing leader election, stuff like that, or, you know, here's an Azure Azure compatibility, that that's one realm of things, especially as the event sourcing grows up. The other big thing, you know, we, I snuck in a, here's why we don't support SQL Server yet. At some point, Martin's probably going to have to, to keep growing, we're going to have to be able to go cross cross database and find some way to get at least a big subset of Martin running on SQL Server. There's occasion people ask us about Oracle or MySQL support, but and the dotnet space SQL Server, we know if we could support SQL server that Martin Martin user, user numbers would probably we think would explode.

#### Jamie

Sure, sure. I wonder whether in that case, they, you know, postulating theorising, whatever, if if you could probably get the the the the paid support sort of structure in place before doing the sequel. And then what his sequel support. And then everybody goes, right, I'm going to move all of my again, buzzword bingo, my macro service, event source database, things over to mother.

#### Jeremy

Yes, exactly. If you have any thoughts about how to make it, make it happen, I'm sure that we would love to.

And we do know that that

there's an issue. So Martin's older than Kosmos dB. But, I mean, we're playing into Microsoft world, and anybody who's interested in this kind of thing is paying attention to Cosmos DB right now. So we that that's a little bit of an issue. I mean, I would just say that I think Martin has easier usability and Martin will definitely have have less expensive hosting costs because of Postgres but I mean, that's something where I have to wrestle with as well.

#### Jamie

Sure. Okay.

So then is is Martin,

open source? Is it

#### Jeremy

under the, under the MIT licence?

#### Jamie

Okay, fair enough. So then if I, if I, as a developer think, oh, I've got this great idea for a feature, or I have this, I have this issue, and I want to see if I can fix it. Is it? Do you take pull requests? Or is it a case of it's open source? But if you really want to? I mean, how does that work?

#### Jeremy

So we do. So I've been involved with open source and dotnet. Since let's see, structuremap was production ready in 2004. It was on SourceForge. Nothing anybody downloaded for the first five years, but it was on SourceForge, publicly released in 2004. So I've been embracing open source a lot. But Martin is the one project I've been involved with, it's had a lot of a lot of contributors. So Martin's had over 100 contributors over the years. So people, I'm using it, I need to do this specific thing. I need to define indexes with composite keys, I want a couple little releases ago, one of our big contributors added Full Text Search. So it's very much community project. We get, we get additions and fixes at the documentation. But well, yeah, we've accepted pull requests from over 100 people

#### Jamie

now. Wow. See, that's I do know of a few. I call them I thought what I call them like a jar source, rather than open up almost like the door is slightly ajar. But like, we're open source, but we don't want anything from the community.

So that's why I kind of asked that easy.

#### Jeremy

Well, there's there's a lot of open source projects where we'd love to have contributions from the community, but nobody's interested. Martin said, that sweet spot of it's something that people have been interested wanted to and been willing to contribute to

#### Jamie

show. Excellent. So then if folks go to the

page of the jasmine framework?

#### Jeremy

Well, so the homepage for Martin it's, it's Martin db.io, but ma RT n? Because it's named after a little weasel like character, or the little weasel like animal and not Martin the person.

#### Jamie

Right? I see. Okay. So if I go to Martin DeVito, there's, I mean, I had a look, I remember there's documentation examples and links to wherever the source code is. And you can just sort of play around from there.

#### Jeremy

Exactly. And you'll also find a link to the GitHub room for Martin that that you can use that that's your getters, like slack tied to GitHub repositories, but that'll get you right to the get a room for Martin. That's where all this Hangout, so if you have any questions, conversations, suggestions, that's how you immediately get a hold of the Martin community.

#### Jamie

Sure. Okay. So then is, so I guess that's the best place to go. Because that's, that was gonna be my next question, right? where's the best place to go to learn of their man DB? That's the website that has the links to all of the things right. Yes, sir. Okay, excellent. So what about catching up with you then learning about all the other projects that you're working on? How do I how do I, as a listener, find out more about Jeremy and where you're working?

#### Jeremy

So my blog, my website? Is it Jeremy D. Miller Comm. I don't blog as much as I did back in the code, better days in the late 2000s. But I try to. So Martin was Martin's kind of an accident that it took off the way it is. But most of the open source projects I'm involved with are under the Jasper FX family projects, including Martin, which is all now part of the it's officially blessed by the dotnet foundation. We're still not sure what that really means. But we're blessed. So there's a bunch of ongoing projects that I work on a lot of which are actually used by Martin Martin itself. So I mean, do you mind if I make a quick rundown of some of the things you could find? Absolutely,

#### Jamie

please do.

#### Jeremy

Okay. So, you know, set up front that I worked on structure map, and the original author of structure map that is just once again, the oldest the original IOC container and dotnet, which means it has a lot of very old, creaky code. Lots of things passed by. people figure out how to make much faster, more resilient containers, you know, in the 15 years since freshmen came out. So there is a next generation container called Lamar, that supports a subset of structure Maps API that's meant to be a novel frode for people that are still have a lot of structuremap code, but are moving into newer technologies, that will depending on use case will be between one to two, sometimes even three orders of magnitude faster than structuremap. Completely adds to that core compliant. There is a, there's a very large framework I've been working on for years, called Jasper that has was originally meant to be a competitor things like in service bus or mass transit still is, but is a, it can be used as a any kind of command processor in memory service bus or a true asynchronous messaging framework. There's also open that small, small project that's yet another command line parser that I've used, it's been used off and on for about 10 or 12 years. But it has the interesting integration with ASP. NET Core and the generic host builder. So it's a way to add extensible command line parsing to any old dotnet core project today for things like utilities or development time pass, or it adds environment test. So that's, that's what I'm working on today.

#### Jamie

Cool. I was I was actually sort of sitting here earlier on going through the, because you inside of a small talk, you sent a few, a few links, or and I was looking through you the the the Jasper effects GitHub group, I was looking at all of the different things I don't like I wouldn't how he comes up with the names for all of his projects.

#### Jeremy

It's, it's gonna be kind of boring. Martin's got an interesting story I'll get to. So Jasper has been my passion project for about five, five to six years. It was meant to be a next generation replacement for a very large failed open source project I worked on years ago called fubu MVC. So totally an ego driven project. The smaller projects around it, so Jasper is my hometown back home. little tight, you know what we call it America. It's it's a, it's a map.on a blacktop. Right. So the other little projects to open Alba, that's an HP contract testing tool for ASP. NET Core. All of those refer to either small landmarks or other tiny little towns around the ground, my hometown. So just the same way Microsoft names things after like streams and found so that's that's where I got the idea. Martin on the other hand, I've told the story public A lot of times, but I still enjoy it. We built Martin on purpose to replace Raven dB. inside of our environment. We were having a lot of troubles with Raven dB. This is many versions of Raven ago. I know that we were doing some unwise things with Raven DB in our system. So let's make Raven a little bit blameless here. And so we had started this work of Hey, I think we could use Postgres as the foundational piece to write a drop in replacement for Raven, let's do it. I was working on it. My boss and collaborator called me and just ask, so what are you calling this thing? You're calling it something lame, like Jasper data or something like that? Right? And I look down at what I'm what I'm doing and that that's what I was calling it at the time said, No, no, not at all. So as fast as I could I googled what are the natural predators of ravens. And the Marten this weasel like animal, they will steal Raven eggs. So I said, No, we're gonna call it Martin, because they're a predator of ravens and the name stuck.

#### Jamie

like it. I like it. Cuz Yeah, we all know that naming things is difficult, right? But you've, you've gone for the almost like the rate not really a raven killer. But yeah, there. That's Yeah, I guess it is a raven killer. Yeah, let's kill the raven by creating this thing, or

#### Jeremy

I like it. That's where we're going.

#### Jamie

Excellent.

So we've talked about how folks can get in contact with you. We talked about where folks can go to get the information. And we've talked about whether name confirm, and we talked about what Martin Davies was wondering, do you know of any interesting or cool projects that you've been told of the US, Martin, where somebody's gone, you know, previously, we do this way, but we found Martin and now it's just awesome. Really just works. And it's really,

#### Jeremy

I

#### Jamie

can't talk about the specifics. That's totally fine.

#### Jeremy

Yeah. At least one commonly used government, government tool, website tool that I can't hide. Yeah,

#### Jamie

I'm sorry. I can't tell you Now that's fair enough. I mean, that's the problem. If you go after the enterprise first, you don't find out about the cool fun things that people are making. Yeah, that's totally cool. Okay. But I mean, that's effectively all the questions that I have for you today. So I just want to say thank you so much, Jeremy, for having a chat about Martin DB, I've learned not just about Martin DB, I know a lot about document databases. And that, I mean, I knew that Postgres was a thing, but I now know enough to do some more furious googling and find out a little bit more about, can I take this project and put it in there, because I've got this idea. I have this project that I built a few years ago, I'm a big fan of Terry Pratchett's Discworld books. And I decided, I'll do this really geeky thing of note down, every time a character appears in one of the 42 novels, grouped them by series. And I've done that in a relational database. And it just, it hurts my head to think about, like, This book has many series, and the series has many characters, and it's just so crazy. So if I can represent every single thing as a, as a document, with this thing has a couple of these things. And that's it. And I think that's what I'll do.

#### Jeremy

So that one might be

a graph database, something like Neo for j might might be a better fit. And then Martin, but yeah, that sounds cool. So I'm a huge if you follow me on Twitter, you know, I'm a huge fan of the Wheel of Time. And people have made massive compendiums like

that have

of being looked at, hey, I have this character, show me what chapters in which books had this character had a point of view reference to, so that the fandom of the world appreciates that kind of thing.

#### Jamie

Cool. Okay, well, I'll still try and do in mutton DB anyway, and then see how that pans out. Now maybe try and do it in, in graph qL as well. And then I can like compare all three, right?

#### Jeremy

Yeah, cool, man.

#### Jamie

Yeah, I mean, that's how I'm gonna get my my sort of my hands dirty with this, my feet work with this project to see what I can build with it. You know, you've you've said, you come from more of the enterprise level. I just want to have fun and play with something so I'm gonna have fun to play with

#### Jeremy

there are definitely more fun than any framework core.

#### Jamie

Well, I can say for sure for this project. It most definitely will. And I haven't even tried using MongoDB yet, so yeah, excellent. But yeah, thank you ever so much for spending your part of your morning with me, Jeremy. I really appreciate it. And I wish you the best of luck with Madden DB and all of the other projects you're working

#### Jeremy

on. Thank you so much. Thanks for having me on and good luck, this podcast going forward. Thank you so much.

{{< paracentre "The above is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

### Wrapping Up

That was my interview with Jeremy Miller about Marten DB. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/), and there will be a link directly to them in your podcatcher.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice - head over to [dotnetcore.show/subscribe](/subscribe) for ways to do that - and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Jeremy Miller on Twitter](https://twitter.com/jeremydmiller)
- [Marten DB on twitter](https://twitter.com/marten_lib)
- [Marten DB documentation](https://martendb.io/)
- [Marten DB source on GitHub](https://github.com/JasperFx/marten)

