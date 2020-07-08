# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is episode 23: Microservices in .NET Core with Christian Horsdal. In this episode, we talked a lot about microservices, mediumservices, BFFs, and how you can go about testing your microservices.

Some of you may know Christian from either of his books [Microservices in .NET Core](https://www.manning.com/books/microservices-in-net-core) or [Nancy Web Development](https://www.packtpub.com/web-development/instant-nancy-web-development), or [his blog](https://www.horsdal-consult.dk) where he writes about aplication design, microservices and the training and talks that he gives.

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Christian Horsdal Introduction

**Jamie**
I just want to thank you, Christian, for being on the podcast is a great pleasure to have you on the show.

**Christian**
Thank you. I'm happy to be here to chat.

**Jamie**
It's great to be connected with you today and to have this chance to discuss microservices and all of the wonderful things about microservices because, aside from going to a few talks on microservices, I haven't really built anything using them. So I'll be interested to find out the benefits of pitfalls and things of creating them.

**Christian**
Well, it is all the rage and has been for for a while, hasn't it.

So to me, I guess the really great benefit of it is that it's so closely connected to continuous delivery, really. That's usually sort of where I start talking about microservices. And if I talk to clients about introducing microservices or not, it's usually where I go that, "there's a lot of work involved in doing microservices." So I think the motivation should really be the agility and the flexibility you can gain from continuous delivery because to my mind, at least, it's almost impossible to build microservices without doing continuous delivery and, then vice versa. It's easier to do continuous delivery with a microservice architecture than with many other architectures. So I'm not saying it's the only one that you could do continuous delivery with, but it's just one that lends itself to that kind of working.

So I think that's where really a lot of the value lies in the flexibility you can get from that. So that can enable businesses to turn around quickly, change the minds, experiment even - like putting something out quickly, just running it for for a while. See if it works, then change it a little bit, see if that works better on so on. That kind of agility and that kind of flexibility, I think, can be enabled by the microservice. And that's a huge value, at least for organisations that know how to take advantage of that. If that makes sense,

**Jamie**
Sure, that makes perfect sense. What I'd like to do before I touch on any of the points you've raised there is: could you quickly just introduce yourself? Is that okay?

**Christian**
Sure. Yes.

My name is Christian and. I live in Denmark. I work as a say consultants slash contractor. So I get to visit various companies and help them with their systems; and sort of that goes from coming into a company as a contractor and being sort of a hired hand, being a developer along with everybody else, but also doing stuff like architecture reviews or helping people set up in architecture. I've helped some startups in sort of figuring out how to set up their development=, and finding other developers, and stuff like that. So it's kind of varied.

And so relating to this to this podcast: Yeah, I wrote the book [Microservices in .NET Core](https://www.manning.com/books/microservices-in-net-core), which was published by Manning almost two years ago now. So that gave me a good excuse to really learn Core, and do a lot of work with Core before it came out. And sort of off the back of that I also run some courses and trainings on .NET Core as well as on microservices and soime other stuff. so different kinds of bits and bobs with companies here and there. And then, sort of, occasionally speaking at conferences. It's not that much, but just a few times a year. And then I would love to bring my blog back to life. But it kind of fell to the wayside while I was writing the book. And then I haven't got back into the swing, so I hope I will,

**Jamie**
Yeah, I can totally understand that for a long time, I ran three blogs myself, and then

**Christian**
Oh, wow.

**Jamie**
Yeah, they one of those blogs transitioned to be a podcast. And then I created this podcast. So, you know, the blogs have taken a back seat for a while.

**Christian**
Yeah, but the podcast much be a lot of work, too.

**Jamie**
Yeah, but I myself, am an auditory learner. So I learn best by listening

**Christian**
Right

**Jamie**
So just listening through to it and editing a few times, you know, it helps help us to really sink in, which is incredibly useful for me.

**Christian**
Yeah.

**Jamie**
Touching on microservices, then. What is a microservice?

**Christian**
That's a good question, and I believe you can find a lot of different definitions of that. The one that I tend to use when I talk about it and the one that I use in my book is that a microservices is a very narrowly focused service that has a few characteristics.

So number one is that it's a service that is responsible for a single piece of functionality. Secondly, it's something that can be individually deployed that, as in: it can be deployed without sort of deploying anything else in the system - deployed to production that is. And it owns his own data store. So it has some data that naturally belongs to it, and t is the source of truth for that data, and it owns the data store where that goes into and sort of, it's responsible for keeping that around. And then sort of a grey area as well which is around the sort of "micro" part of it.

So "micro," what does that mean? Does it have to be really small? What's that sort of about? And I don't know. It doesn't have to be that small, really. But then, on the other hand, I tend to think that sort of a typical software team around three to five persons, or something like, that should probably be able to maintain like 10 microservices. And that's definitely a grey area saying that, because that depends on how much development has to go on on the services? How many bugs do they have? How many new features do they need? And so on, so forth. But I do think it kind of gives people an idea of what we're talking about in terms of the the size I think about when you talk about microservices.

So those things are some characteristics that I tend to use in two ways. So when I go into a company and they say we're doing microservices, then I like to look at them and see if their services adhere to those characteristics or not. Sometimes its, "I don't really think what you're doing is microservices," and that's not a judgement call. It's just a a matter of recognising what it is and what isn't, because it can be absolutely fine being something else, but it's nice to being able to recognise it. And then the other way around as well. If I work for a company and we've decided that we are going to try to do microservices, then I like to keep these things in mind and keep on saying, "OK, is this still individually deployable? If it's not, it's not really microservice. And we've decided to go with microservices because off the benefits it can give us in terms of flexibility and so on. And if we lose track of that, then we lose the value." And other things like, "Is it still single responsibility? Does it only implement one business capability or is being broader than that?" So get sort of guide the design of the microservices. But it also helps in recognising what a microservice _is_, I think.

That's the definition _I_ go by. And I'm sure you can find a million different definitions on the Internet at this point.

**Jamie**
Yeah, I think that's well, both the great and horrible thing about design patterns is that everyone has their own implementation.

**Christian**
Yeah

**Jamie**
Let's say I have a Web application, and that I got a Web UI and a Web API, would that Web UI be classed as a microservice, or would I need to break that down into smaller chunks to make it into a microservice, in your definition?

**Christian**
I would probably tend to break it down into smaller chunks.

I think there's a few different ways of attacking the UI, and I think some of it has to do with where we want to compose the functionality, because I think it's also important to recognise that breaking the system down to many, many small, little microservices might be great on the back end; that might be great from developers standpoint, from a business agility standpoint. But that doesn't mean that the end users want to be confronted with that. They want a clear UI of course, they don't want to know that we've broken the system into 100 or 1,000 different microservices. Why should they care really about each of those individual ones? So at some point, we you need to make that into one coherent thing.

I think that could be all the way inside the browser. I mean, with a SPA, you can make a composite application and draw on different microservices for painting different parts of the page and showing that to the user. That moves UInto sort of having a thicker client that needs to know some or about the back end architecture, so you can also move that to something like a gateway on the backend. So a Gateway could be the thing that exposed the API to the outside world, and then behind that we have a lot of microservices. But it's just really a thin layer that just proxies onto the other microservices, but translates it a little bit into a slightly more coherent set of API where naming might follow slightly different conventions, and you have in the inside of that.

And then a third route, which I guess is a little bit in between the two and one that I think you can have actually pretty good success with is the [BFF](https://samnewman.io/patterns/architectural/bff/) - and is not best friends forever, it's "back in for front end", but I'm sure there's some tongue in cheek going on there. But a backend for front end is sort of a specialised gateway. So it's kind of like a gateway, but it doesn't expose everything. It could expose just the things needed for the front page of the website; or the things needed for the details page of the website; or the things needed for the android app or the iOS app. So it's kind of tightly coupled to the frontend, or at least part of the frontend. And then it translate to all the microservices on the backend. I think that can create kind of a nice situation where you can have the small services behind the scenes broken down by business capabilities, and those can be nice; self contained; individually deployable, all these my things. But then, when you're in the UI code, in the app code, or in one of the pages on the Web site, then you just have one API that you talk to.

And then the balance is that that API doesn't grow to become sort of the newmonolith, because I think that's a danger of the gateway approach that we also talked about it has to be really, really thin. If you start putting a little bit of functionality into that gateway it can easily become sort of the thing that attracts more and more functionality. And then you have these anemic microservices behind it, but all the real functionality is in the gateway, and then it's just just a monolith. And if you didn't set out to make a good monolith, it probably isn't a good monolith, then it's probably a bad monolith.

So those are different approaches, and I think the one that I've had the most success with has been the back and front and approach. But I'm not saying it's the only way to go, but it's the one that I've seen the most successful.

### BFFs and an Example

**Jamie**
So if I unpack that a little bit and use, say, Netflix as an example, I know that they've been pretty vocal in the past few years about "Hey, we have this wonderful testing framework and everything's a microservice; and even though our data centres went doqwn, we were still able to serve stuff." Could a backend for front end, or a BFF, API or microservice, could the UI be spread into: here is the microservice for seach; here's the microservice for displaying recommendations; here's the microservice for, I don't know, genres of films; and here's the microservice perhaps for streaming the movie or the TV show that you're watching?

**Christian**
Yes.

I don't know how Netflix have done it. I guess an approach could be that on the back end you break it down by these capabilities like search and maybe some different categorizations, and there's probably some things around the playback and stuff. There's probably a whole sort of back end stuff going on with the importing of films and getting them subtitled as well well, and I don't know. And then I guess if we were to look at that back and for front end pattern, then I would guess you could look at, say, there is the Web UI and that consists of different pages or even maybe some parts of the page like we're they're sort of the "my list" thing; and there's the continue watching; and there's the recommendations and each of those sort of lines and the UI that people might know in there in the Netflix UI. I could imagine that that could have even its own back in for front end, and then draw on more than one microservice on the back end because maybe that's the recommendation itself, but maybe I could imagine maybe sort of the picture that you see on the on the page, maybe that's from at another microservice. Maybe there's something around the language that had a third microservice involved in.

So maybe even those bits of the UI actually draws on different microservices. So you could still imagine having that back end for front end in between. So that the UI just talked to one in point and then that draws on things from different microservice either. Maybe by HTTP end points on the back end, or you could have some eventing system. You pick up the data on the back end and ready to serve. I would say there would be different ways to go and, yeah, one won a second guess how have they done it.

But those approaches the least you could see so it can be quite broken down still with this backend for front end thing. Or you could go slightly bigger and say, "Okay, I want the front page to have a back end for front end, and then I want the player to have another one and then there is somewhat bigger." But that's kind of a trade off, and I think the tradeoff there for me leans a lot towards what makes it easiest to implement the UI. So that's kind of what I want to drive how the backend for front end looks. And then I can have other things that drive how the microservices have broken down at the back end of that. And then the back end for front end is the glue between those two worlds. So that's also why I'm saying that that the backend for front end this is somewhat tightly coupled to the to the UI: because that's why it exists. It exists to serve the UI really. And to shield us from the complexity of the microservices on the on the backend

**Jamie**
So I wonder then, if I have some form of UI that requires a number of microservices to be called in order to render everything on the page, if we're talking Web development land - because obviously microservices aren't just limited to Web development, Web development I guess it's an area where we can use microservices - but as the number of microservices increases, presumably the number of web requests that you need to make increases to, I guess.

**Christian**
Well, yeah. Again, I guess that depends on how we attack that UI problem.

If we go sort of the composite UI route and have everything assembled in the browser, then, yeah, it would be a tendency towards that: that you actually see drawing from more and more places as it becomes more complex than maybe you break the page down further. So, like the left menu is from one microservice, and then there might be sort of the header from another, and the footer from a third, and then there's a few content areas in the middle, and each of those draw from different microservices.

But if we go with the gateway or the back end for front end approaches, then those are our services on the back end, and they give us a chance to sort of consolidate things for the UI. Because on the Web or with a mobile client, I mean, the rules are still the same as they always have been and making too many requests, that costs and people are sometimes on bad connexions, and you don't want to use too much bandwidth, and so on so forth. And you want your page to render fast. So it still makes sense to consolidate that into, say, "OK, the initial page request for the front end actually needs to get some data back. But that could be something that the Gateway or BFF, assembles from different microservices and then sends back to the browsers so we can actually render the first part of the page before it has to make any AJAX requests to0 get the next bit.

And I guess the same somewhat goes for those AJAX requests, that instead of making ten small calls, it's quite all right to, in the back and for front end consolidate that into one call again, because I see the back and front and as something that exists to make the UI easy to implement and perform well. So if the UI needs a certain endpoint then the BFF will implement that end point, and that might mean that the BFF goes and talks to two different microservices, and listenes to maybe events from a queue from a couple of other ones and picks up some data, combines all four or five sources like that, and then returns that to the UI. So that there's only one request going on from the browser, or from the mobile phone, back to the server. And then there's some server communication, but that's much faster of course. So that's at least one way to get around that problem of the explosion of how much UI have to talk to.

**Jamie**
In that case then, you could have almost a fuzzy metric for figuring out, "wow! We're sending off 500 requests. That's too many. How many can we sort of combine and consolidate," as you said, "in to fewer requests." Maybe do, like you said, more server side rendering of things and maybe send actual HTML down the wire. Or rather than sending data that then has to be passed and rendered, can we do some of that rendering on the server and send it through?

**Christian**
Yeah, that could definitely make sense as well to send fragments of HTML down so it just readily can be incorporated into the page.

### NancyFX

**Jamie**
So we've talked a lot about microservices so far, and I do know that in the Microservices book you made a point of using [NancyFX](http://nancyfx.org/). So I wondering if you could give us a really quick introduction to that, and maybe why you would or wouldn't use Nancy FX compared to, say, ASP.NET Core or ASP.NET.

**Christian**
Yeah.

So Nancy is a .NET and .NET Core based web framework and it has the mantra of: "giving the developer the super duper happy path." So you're supposed to as a developer, using Nancy, just naturally follow a road that leads you to success and. Just finding it easy. So Nancy tries hard to get out of your way. So there's a little syntax that you have to learn to use Nancy. But once you've learned that, it tries really hard to do what you would expect and have sensical defaults and not tie you very much to the framework. So it's quite easy to only touch Nancy in very small parts of your code, and it's very modular. So you can change out literally everything in Nancy.

So you can use it out of the box and it's great. And then if there is some corner that you want to make behave a little bit differently, you can change that out. So Nancy has a history of eight years, I want to say I'm not sure something like that. So it's definitely from a time when ASP.NET looked a lot different than ASP.NET does today. And I think, to be honest, Nancy used to have much more of an advantage over , say MVC or WebAPI, I than it does today over MVC core.

So, yeah, the book is two years old and I would probably go with MVC Core if I was writing it today. I still really, really like Nancy, but I do think the gap is a lot smaller today. I think MVC Core has a lot more sensible defaults than - well, MVC had a lot of sensible defaults as well, but I thought there were some things that I always bumped my head into, and I just don't find that as much with MVC Core and I think it is easier to get the framework out of the way as well. And I think a big thing as well, that's sort of changed with Core compared to more traditional ASPNET is I think they cleaned up the pipeline.

So Nancy all along lead you down a path using stuff like [OWIN](http://owin.org/). So it lended itself really nicely too  building upon an OWIN pipeline, and that's been the great inspiration for the middleware model that we have in ASP.NET Core today. It's not exactly the same, but it's the same set of ideas and I think that's actually really, really nice as well, and something that is just a lot simpler, and a lot more composable than the way that ASP.NET used to work. So that's also an area where I think they've closed the gap a whole lot: that instead of having something like a self hosted service using OWIN and Nancy, then today everything in ASP.NET Core is essentially self-hosted because it's essentially a console app, where you create a Web host and then you start that, and everything's go through the layers of middleware, and I think that's a nice composable, and pretty simple model. And then, sort of, at the end of that chain of middleware you have the web framework, that could be a Nancy, that could be MVC Core. I think both work really well, and Nancy works perfectly fine on Core as well. But I just don't think the gap is as big as it used to be. So I'm not completely sure, but I think if I was rewriting the book, I would go with MVC Core.

**Jamie**
Sure. So there's still a usage for Nancy, in the same way that they're still usage for any technology once a new technology has come out. But you would recommend, I guess, starting with MVC Core because I guess it's built in?

**Christian**
Yeah, I think I would, because it's already pretty widespread, and it's only growing.

So I mean, that's obviously not always the reason to do something: just because other people are using it. But as I said, since I think the gap is a lot smaller. I still think Nancy is more elegant, but there's not as much of a difference as they used to be. So I think, the argument of using the thing that is probably easier to Stack Overflow or Google, I think that wins out today .So I think I would go with MVC Core.

Another interesting project that sprang out, I guess, of Nancy, or at least is greatly inspired by Nancy is something called [Carter](https://github.com/CarterCommunity/Carter) that Jonathan Channon, who also used to work on Nancy - or still does to some extent, I guess - created. And it's a set of libraries that basically uses the same syntax as Nancy. So it's sort of meant to look as much like Nancy as they can, but it doesn't have the ties to .NET full Framework and OWIN and so on. So it's more natively in ASP.NET Core, if you will. So it's built on ASP.NET Core middleware directly. Which I guess can give it sort of a leg up going forward with ASP.NET Core because it's more native to to that stack. And then it still has the same syntax asNancy, and the simplicity of how that used to work. That's something I'm at least following and seeing where that goes. A very interesting project, so I'd recommend taking a look at that.

**Jamie**
I know there's a community version available on GitHub, so I'll make sure that there's a link to that so that people can go have a look, and check it out.

### Best Practises for Designing Microservices

**Jamie**

So without giving away too much of the secret sauce in the book, is there a best practise, or almost like a formulaic step by step for how to design a system with microservices? Or is it just a case of your system will naturally, as you are designing it will just move slowly towards the microservices architecture?

**Christian**
I think it's more of the latter than the former.

I definitely think that it's one of those things that almost impossible to get right the first time around. I know that some people that argue that you can't even start with microservices, that you sort of have to start with a monolith and then carve microservices out of that. I don't know that that's been my experience, but I mean at least sort of repeatingly with clients I see that when they start using microservices, the first one tends to sort of be something that when you look at it a year later, you look it and then you go, "It's not really micro, and I'm not even sure it's service. It's kind of a thing, and it does something, and we learned from it. And then the next one became better, and the next one became better. And then maybe the fifth one: that's really a microservice, and we're happy with that."

And so I think that just is this sort of a organisational learning curve in recognising the right size, and really recognising the importance of once you have defined that this microservice deals with one particular thing: so it could be something like the checkout flow on a Web shop - probably even less than that - but recognise that that's what the microservice deals with. Then it looks like most organisations, for the first few, they tend to sort of put a bit more into it because, "we also need this small functionality. And then we have this service right next to it already, we'll just put it in there." And then sort of at a later stage, they probably more get into the habit of saying, "No, we're not putting it in there we're spinning up a new service."

But I think that's habit there. And I think part of that is also has to do with the tooling around it that we build up as wego. So that ties back to something that I said at the top of the show: that I think one of the great benefits of microservices is how well it works together with continuous delivery. But it also kind of demands some of that, because it's kind of fine when you have a handful of services, you can sort of get along with a lot of things. But once you have 500 microservices, you really, really, really need to have some great automation around everything to do with that was microservices. Be it building them; keeping packages up to date; testing them on all the levels like, unit testing, integration testing, system level testing; deploying them to say QA environment, then the production environment; monitoring them. All those kinds of thing, you really have to have that in place.

But then I think the thing that kind of happens is that the closer you get to having all those kinds of things in place, the more you tend to sort of align on how that's done. But that also means that creating a new microservice just becomes that much easier. So I think that's part of it: that as we go along, it becomes easier to create new microservices. So it's also easier to be in the habit of not putting too much functionality into the existing ones, but just going, "I'm creating a new microservice for this."

And then, I guess, at some point really you can get to the situation where that even feels like the easiest thing to do just because then I have my own little new pristine code base that I put this functionality, and I don't have to deal with anything else. And I know that setting up all the the automation is easy because we've not only automated deployment and so on, we've automated building that pipeline. So we've sort of automated the automation, if you understand what I mean. At least that's what I see organisations do, just because you get into such large numbers that that becomes necessary.

But getting back to your question of how do you actually build these systems? I think there's sort of a whole other big area to learn in order to do this well, which is a lot less technical than much of work we've talked about now, which is the whole domain driven design area. Because I think that's at the heart of designing microservices as well: that you understand domain driven design and what a bounded context is; what a business capability is. Maybe use techniques like event storming to figure out how business flows actually work, and what happens in what sequence, and what tends to group together, because those groups are sort of potential microservices. But sort of in that whole area of thinking around DDD, or domain driven design, is also the fact that it's an exploration, and it's something that evolves over time. So you get some of it right early on, and some of it you don't, and I guess it's the same with microservices: you don't get them all right from the beginning, it's a growing thing.

I think one of the rules of thumb I like to try to apply there is that: when in doubt, I'd rather have a service be slightly bigger than it ideally would than slightly too small. Because when we can't get it exactly right, it's often because we don't know enough at that point in time. And it's easier to experiment somewhat within just one code base, one service. You can have your IDE do the refactoring, and you can move the boundaries and things. And then you can sort of figure out, "what's the right way to structure this. What are the right concepts within the code?" And then, once you've done that, you might begin to recognise that, "Ah. This microservices actually doing two different things, so we can cut it in half and make those two nice services." But if we try to do that upfront with too little knowledge, we might have, sort of, cut that the wrong way. So you had, sort of, half for one of the capabilities in one service, and half of it in the other, and all mixed together. And that means that when moving the code around is just more cumbersome, because there's not one code base, so you can't really just refactor. And there's also the matter of deployment: that you easily get into a situation where those two microservices have to move in lockstep and have to be deployed at the same time. And that's difficult to do.

So I'd rather for awhile err on the side of slightly bigger and then eventually move into these really small, really focused microservices. Just from a practical standpoint,

**Jamie**
The advice you've given there about "start with slightly bigger microservices", and "you're potentially not going to get it right the first time" is almost exactly the same advice I've been given when I've gone to talks where the subject has been "here is one of microservices, and we did it wrong."

**Christian**
It's not necessarily wrong, really. There's a learning curve. And I think every company that ventures in this has a learning curve, if for no other reason than just because their domain is unique, and learning the domain on the level that you need to do domain driven designm and to break it down like this: that's a journey, and that's a learning experience as well. So I think there's no way around the fact that there will be learning going on. If there wasn't it almost wasn't development, was it?

**Jamie**
I'd like to just touch on how you go about unit testing and integration testing microservices. Only because my understanding is obviously if I have a microservice out there, let's say I have a foo microservice and I have a bar microservice. If my foo microservice talks to my bar microservice, can I mock that communication? And if so, how do I keep that in sync for when the microservices change or grow?

**Christian**
Yeah, I would usually mock that communication.

So we can look at the kind of [traditional testing pyramid](https://martinfowler.com/bliki/TestPyramid.html) and that still mostly apply. So you have unit tests on the bottom, and those are, I guess, the same way as they would be in other systems. Then I think an interesting level of testing that I like to do with microservices is exactly what you're talking about: which I sometimes called service level testing. So testing a complete service, but with all its collaborators - the other services - mocked out. And depends on how that communication had done, that would dictate how the mocking would be done.

If we're talking about the HTTP communication, then I would actually, usually just within the test process itself. So I might have, like, an xUnit project with the test in it, then within that project I would start a `webhost` - an ASP.NET Core `webhost` - and set up mocked endpoints right there. And just write canned responses that returns and use those in the tests.

So I would use the real service, maybe run it in like a test server, so you don't have as much overhead of going down into the network stack, but then giving that a configuration that makes it think that it's collaborators are at different localhost ports; which all just point back to the test process itself, that then just have mocked endpoint.

If you're using a queue and events, then you might need to actually have that queue running in, say, a container on your localhost as well, and on your test environment as well. And then, again, set up sort of consumers and producers for the events that you need to mock. But that is a good level of testing just because you get a very complete test of the service itself, but also because itt's actually one of the areas where I think microservices can shine: because their sort of small enough that testing all of the service isn't that hard. So I think you can get a really long way with testing at that level, and then using unit tests in conjunction with that for the places where you need it.

So I like to follow an outside in approach to my TDD around these services and actually start from the outside with these tests that test the complete service, including a database, for instance. But mocking collaborators. I think that's really nice and they can be reasonably fast, and then you get really good coverage. And then when that gets too slow, or it gets too much, set up to get the service into a specific situation, then just changed gears and use unit tests, that's finest well. But I think that level of testing is really good. And then I guess the third one is to supplement that with system level tests as well that not only test one service, but tests the whole system and thereby also where the integration.

So another possibility around looking at whether mocks are still as they should be, is that you might have a set of tests that you can run against the mock, but also against the reeal collaborator, and then compare the results. What is it? [Contract testing](https://martinfowler.com/bliki/ContractTest.html) or something like that. I believe Martin Fowler calls it. He has a bliki around doing that kind of thing, where you test your mock and then test the real thing. Just to make sure that your mock behaves in a manner that matches the real one

**Jamie**
Sure, that makes perfect sense. 

Yeah, it is a contract test as Martin Fowler described it. So you would run the test on, as you said, your mockked version of the microservice and then run the same test against a live version of the same microservice, and ensure that the results are the same.

**Christian**
Yeah, or at least similar.

I think sometimes and practise it can be difficult to make them exactly the same, just because if you're testing against the real one then you might sort of have data issues. "Do you have the same data as the one that you expecting in the mock?" and so on.

But yeah, you can get around that and check that it looks like it's the same behaviour still. But ultimately, I think you also need those system level test; and by system level test, I can be testing through the UI even. So, you don't want to test every little single piece of functionality that way because it comes too heavy. But all these sort of sunshine paths I like to have tested through the US as well, because that gives you the confidence that those integrations actually still work.

**Jamie**
One of my final few questions, I do have a few more: So a lot of the talks I've been to have been very much docker and Kubernetes and microservices because they make sense. However, do microservices require that sort of containerisation and orchestration? Or is it literally just the case off "I can have an API somewhere else on the Web that just accepts a web request and returns a response?"

**Christian**
I definitely think the latter.

There's no technology that you need to do microservices. Of course, you need technology, but there's no specific technology you need. So it can be containerised and you can have orchestration. You could also do it with something serverless, so could do it in with lambda and functions, and that way go higher abstraction than containers. Or it could go the other way: You could host APIs on IIS, or Apache, or whatever.

To me, at least, that's not the important bit of doing microservices. Making good technology choices obviously has an impact, and I think just like we want to keep the services small because that means that we have some simplicity, and we have an easy code based to work with where we can actually deliver on that flexibility to the business. I think favouring simplicity in technology choices as well makes a lot of sense, and I think that makes for better microservices systems. But there's no one technology that fits that bill. Sometimes that might be deploying some WebAPIs to IIS, and other times it might be deploying some containers into kubernetes, and sometimes it might be a doing AWS lambdas.

So I think it sort of depends on what technologies you'ree familiar within your organisation; how your microservices look - the complexity of domain will probably also you read a little bit into how your microservices look, and that could sort of drive you either one way or the other. What a your performance characteristics? How are your scalability characteristics, that could also drive you sort of into looking at serverless something for you or isn't it? But it's not microservices per se, that tells you whether to do one or the other. I would say.

**Jamie**
Okay, so I guess like all design patterns, the microservice architecture is mostly technology agnostic then?

**Christian**
yes, I'l give you that well put.

**Jamie**
Would you recommend that listeners start out with a green field or a preexisting project when trying to learn microservices? Are they better to start with, "this is a completely very new project that I'm going to design from the ground up to use microservices," or should I take a pre existing monolithic application and try to break that down?

**Christian**
I wouldn't recommend one over the other, I think you can have success in both cases.

I think the thing to keep in mind that is why you want to do microservices, because it does take a lot of work. So there's the risk of getting the scope of the microservicess wrong, and then have to moving things around between them, and that's cumbersome. And there's all the automation that I talked about that you have to build, and you have to build it all of that scale if you're planning to support having several hundred microservices, so there's some definitely cost to it.

So I think really what it comes down to is: is there sufficient value in having the flexibility and the agility that you can get from these microservices? And if there isthen I think it's absolutely fine for Greenfield, and it's also fined for carving out existing and monolith and going that way. Just remember if the motivation is really there.

If we're talking Greenfield then, sort of, for obvious reasons, you won't have 100 microservices from day one; you'll probably have like two or something. But then, pretty quick you'l have three or five. At that point, I think you can think about it as microservices, but you're still growing them and they're still getting more, and more, and more, still expanding properly. But you could still sort of follow that pattern of thinking.

**Jamie**
Fantastic. Like I say, that seems to be pretty similar to all of the advice I've received it at some of these talks where they've said, "when designing from the ground up, start with almost like a monolith. Get your design right, your domain knowledge right, and break off pieces and create small, maybe not small, but sorather than creating microservices, create medium services and then maybe splinter off from there"

**Christian**
Yeah, I actually like that term "doing the medium services." Because that ties into what I said around how I do favour having them slightly too big until you have enough knowledge to get it just right. "Mediumservice," that's a good term. I'll steal that.

**Jamie**
That's fine. So long as you say that it was created on the podcast.

**Christian**
I will.

**Jamie**
You can take complete credit for it, I don't mind.

Where can people maybe connect with you and find out updates on some of maybe any of the open source projects that you're working on, if you work on them, or find out about new books that are coming out. If you write anymore, that kind of thing.

**Christian**
Well to connect with me, I guess the easiest way is through my Twitter. So that's [chr_horsdal](https://twitter.com/chr_horsdal) and Horsdal is my middle name. But then there's also my website, which is [horsdal-consult.dk](https://www.horsdal-consult.dk/). And as I said, I do want to get blog going. But there's also an about page where people can find ways to contact me, and I try to keep that page on there up to date with talks I'm giving as well.

**Jamie**
Fantastic. All that really remains to say is thank you ever so much for being on the podcast, Christian, Thank you for taking time out to talk to me about microservices.

**Christian**
Well, thanks for having me on. It was a complete pleasure. I was happy to do it.

**Jamie**
You're very welcome. Like I said, thank you ever so much for being on the show. Christine and I'll make sure to put links to all of the things that we discussed into the show nuts and thank you ever so much Thank you.

### Wrapping Up

That was my interview with Christian Horsdal. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and a collection of text snippets from the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/).

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Christian Horsdal on twitter](https://twitter.com/chr_horsdal)
- [Carter](https://github.com/CarterCommunity)
- [Nancy](http://nancyfx.org/)
- [Contract tests](https://martinfowler.com/bliki/ContractTest.html)
- [Test pyramid](https://www.mountaingoatsoftware.com/blog/the-forgotten-layer-of-the-test-automation-pyramid)
- [BFFs](https://samnewman.io/patterns/architectural/bff/)
- [Single-page BFFs](https://www.horsdal-consult.dk/2016/09/single-page-bffs.html)
- [Microservices in .NET Core](https://www.manning.com/books/microservices-in-net-core)
- [Christian's website](https://www.horsdal-consult.dk/)
- [conftalks.dev](https://conftalks.dev?utm_source=dotnetcore&utm_medium=podcast&utm_campaign=dotnetcore)
