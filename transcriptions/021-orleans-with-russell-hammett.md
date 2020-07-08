# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is episode 21: Orleans with Russell Hammett. In this episode I interviewed Russell about Orleans, the actor model, and asynchrony.

Russell currently works as a Software Engineer at G2 Inc., on a government contract for the National Institute of Standards and Technology (NIST). Russell (aka Kritner) started tinkering with computers as a kid, and hasn't stopped since. He started his career in 2009, while finishing up his bachelor's degree, and has concentrated mostly on full stack development. Recently, he started working with and writing blog posts about Microsoft Orleans, which leads us here!

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Russell Hammett's Introduction

**Jamie**:
So, Russ, I just want to start by thanking you for agreeing to be on the podcast.

**Russ**:
Thanks for having me

**Jamie**:
The first thing that we should do. Because people are listening to this and they may not know who you are. I hopefully they'll know a little bit about who I am - bit I haven't interesting place for them to come into, if it's the first time hearing the podcast. So would you be able to sort of introduce yourself a little bit to the people who are listening, who may not know who you are, the kind of work you do?

**Russ**:
Sure. I would be very surprised if people knew who I am. This is the first podcast I've been on, so thank you again for having me.

My name is Russ Hammett. I've pretty much been interested in development fy whole life, started professionally developing in 2009. Mostly full stack. And I've been in a few different jobs, and currently I'm working for a company called G2 Incorporated. I work on a government contract sponsored by NIST where we get to do a lot of fun stuff. And this is where I started tinkering around with Orleans, which is what we were going to talk about a little bit today.

**Jamie**:
Fantastic. So you are the security guy then, if you work for NIST?

**Russ**:
Yeah, Kind off. More or less. I write crypto and a test harness for that crypto.

That test harness is exposed via an API and people can hit our API and get what we call test vectors, where they run basically the inputs that we're giving them against their crypto modules. They send us the answers back from their run, so to speak. And then we compare them to our answers. And that whole process is part of a cryptographic module and/or algorithm validation process, which is required for basically any government use of crypto. It has to be validated through this process in order to be used. So that's the basic of the application I'm working on. We're not quite yet at the 1.0 release, but we should be there in a few weeks or months. And we're basically replacing a much more manual process with this much more up to date API.

**Jamie**:
So when they say never roll your own crypto, you should never do it unless you work alongside NIST, I guess.

**Russ**:
Yeah, One caveat of the crypto were writing is we're not writing it necessarily to be secure because we're behind firewalls and this stuff is not exposed to the public. But were writing it for correct answers, not necessarily all of the security constraints that go into having a hardened crypto system. Some of that stuff is tested, but that's outside of the scope of the application that I'm currently working on

**Jamie**:
It's more your writing a process for taking some data, doing some magic to it and providing an answer rather than you are writing TLS 1.4 or OpenSSL or something?

**Russ**:
Well, we are writing those. They just don't necessarily have to be as hardened as, say, something like OpenSSL would be. Because people aren't actually calling our crypto within their system, they're just hitting our API which then calls into some internal process which houses our crypto. We run it, get the inputs and/or responses and send it out.

Hardening your systems is obviously very important. It's just not necessarily within the scope of what we're doing for this particular program.

### What Is Orleans?

**Jamie**:
I would love to talk crypto with you, but obviously we're not going to be talking crypto today. How about if we, like you said earlier on, how about we talk about Orleans?

**Russ**:
Sure.

**Jamie**:
Would you mind giving us a quick introduction to Orleans and maybe one or two of the problems that it aims so solve?

**Russ**:
Sure. So they describe themselves as a virtual [Actor Model](https://en.wikipedia.org/w/index.php?title=Actor_model) framework. And if you're unfamiliar with actor model, that's more or less a method of distributing compute.

So rather than being constrained to a single piece of hardware going from like the physical hardware, let's use that as the example: If you have a four core processor then your kind of constrained to those four CPUs. You can run applications on your local machine, and you can never use up more compute at any one time than those four CPUs can handle. So with a actor model framework, you basically more or less right new primitives in the form of these actors that you can stand up in a cluster of nodes. And those nodes in your cluster, you can stand up as many as you need, really. So if you had, say, ten nodes brought up with four processors each. That gives you forty processors to work with instead of the four that you have locally. So that's the basic idea behind the actor model. You bring up a cluster and you have a lot more computer available to you.

And the virtual aspect of Orleans - this could be incorrect, but from my understanding - the virtual aspect is just an abstraction for making this easier on the user. It basically handles all of the load balancing for your cluster and things like that. Yeah, that's pretty much it.

**Jamie**:
So I was recently at a talk where someone was talking about the machine learning - not their big, "Hey, this is deep learning," sort of thing, the more actual engineering side of machine learning. They were saying that what you will do as you break down your data set into the smallest possible chunks and you'll have a single, maybe a CPU or a single processing unit, act on that data point and do whatever maths it needs to do to figure out whether this is a Rose, or it's a Pikachu, or it's I don't know a PlayStation controller or something - you could tell I've been playing video games a lot recently.

So what I'm thinking is that the actor model/ Orleans could potentially help you do this. Is this right? So if I could create an actor and give it some process to run and some data, I could just sort of offload all of my heavy duty processing onto other machines, I guess other actors, to be able to do that. Is that fair enough description?

**Russ**:
Yeah, that sounds pretty close. Breaking down your problems into smaller bits is the good part of Orleans. Actually, one of the things I failed to mention earlier was Orleans is heavily dependent on asynchronous programming. Asynchronous and generally fast running programming. But I can probably get into it a little bit later, but we, as in the project I'm working on, don't use it in quite that manner. But basically everything needs to be written asynchronously and fast running, and it can just distribute and work asynchronously and respond with answers.

**Jamie**:
If the idea is to work async, is it literally just a case of `async`, `Task`, `await`, done. Or, I guess, you have to take us that back and go, "Actually, which bits can I do as an async task and which bits have to be synchronous?" is something you need to do?

**Russ**:
Everything in Orleans technically should be asynchronous. But like I mentioned earlier, we're not using it in that way.

We have a lot of tight loops where, as I mentioned earlier, we're writing a lot of crypto calls where you may do hundreds of thousands of crypto calls for a specific test of an algorithm. And those hundreds of thousands of calls are farmed out to our cluster. Now we're not writing asynchronous crypto. We're writing synchronous crypto, So we are, in effect, just wrapping synchronous code with an asynchronous wrapper.

But one of the things that we're doing, like I mentioned earlier because we didn't want to be constrained to the single four CPUs or whatever it ends up being on whatever server you have it deployed to. We're using a concept of the Orleans task scheduler to pick up all the calls, and then farm those calls out to a separate task scheduler; basically to keep the Orleans task scheduler ready for picking up more Orleans calls

So we're basically using Orleans as a means of queuing up synchronous tasks that are solved on a separate thread. So the bigger we make our cluster, the faster we can get through all these crypto calls, even though they're still synchronous.

**Jamie**:
I presume you need a network of hardware that is already provisioned, and you have a server client idea. Your main machine, I guess, being the server at each of your actors being clients?

**Russ**:
That is one way to do it, and that is the way we're doing it. There's a few different ways, actually.

There is a sort of master slave relationship, if necessary. You can also host your Orleans cluster and highly available method, where you're using something like SQL server to manage all of the silo hosts - those are the names of the nodes in the cluster. I've been going back and forth between silo host and server host and naming my projects all inconsistently, but I'm pretty sure it's silo host.

So, yes, you have the master slave, you have highly available. And this is all on-prem. But there is also a way to do this on Azure, which we can't use for my particular project. But I know that Orleans integrates very well with service fabric which I don't know a whole lot about, but they sound like they solve similar problems as well, although I think they do it a little bit differently.

If I remember correctly, Service fabric has you just use specific decorators on your class similar to the data member attributes from like WCF days. But with Orleans, you really just implement specific interfaces and/or extend specific abstract classes in order to get your code working with Orleans. It's really just basically the same thing as writing a synchronous code. Except in the way we do it, it's slightly different. But I'm hoping that I can get into some of those slight differences in the way we're using it versus how people would traditionally use Orleans in some of the blog posts I've been doing on the subject. Which I believe is how you found me. And, of course, the slack channel that were on.

I've mostly been doing the blog post so that I can learn the correct way to use Orleans, and more about the thing that I'm actually implementing at work.

**Jamie**:
So just to cover something you touched on. So we'll have links to your series off blog posts on Orleans in the notes. So if you are listening along, do click over to `dotnetcore.show`, and check out the links. Because Russ is a fantastic writer anyway, and I know next to nothing about Orleans, and I've been reading through some of the blog posts you write, and it's starting to make sense.

**Russ**:
That is very good to hear.

**Jamie**:
And yeah, you mentioned the Slack channel. So I'm gonna actually call it out directly.

So Russ and I met through the [CodingBlocks Podcast](https://codingblocks.net/) Slack Channel. If you are listening to this show but you're not listening to their's, do yourself a favor and go listen to theirs cause it's amazing.

**Russ**:
It's definitely good stuff. One of them likes getting kicked in the shins.

**Jamie**:
Yes, exactly.

Inside baseball talk here, but when [I interviewed him is part of a different podcast that I'm on](https://www.wafflingtaylors.rocks/2018/11/09/the-waffling-taylors-and-unaffiliated-jz-podcast-party/), that particular person said that, "many people have tried. But nobody has succeeded."

**Russ**:
Another podcast that you're on Jamie, and you're not going to plug it?

**Jamie**:
It doesn't cross over so I won't plug it. It's not a problem.

**Russ**:
I don't know gaming and programmers that seem to go hand in hand.

**Jamie**:
Well, yeah, maybe check the show notes. Anyway, there'll be a link.

### Why Orleans?

**Jamie**:
Have you experienced with any of the other .NET based actor model systems? Because I know there's akka, I don't know how you pronounce it. Akka there's that one, and there are a few more.

**Russ**:
I've not worked with Akka I've heard of it for sure. I think I heard of Akka from .NET Rocks!, but I think at the time it was not a free product. But I'm not positive about that.

But the big pull for Orleans was we were looking for something that seemed to relatively easy to use, that was in the .NET ecosystem. Orleans was built in .NET Core - or at least at the time I was looking at it originally, it was in the pre release for .NET Core. But it's also open source, created by Microsoft and one of the, I can't say the biggest hook because that would be a terrible thing to say, but it was created for use in the Halo franchise for some of their online play.

There are all kinds of cool examples on the [Orleans documentation](https://dotnet.github.io/orleans/) that show you more about how to use Orlean. And one of those examples is a chat program, and I can only imagine something similar was would be used for creating and joining games. And actually, it's been years since I've played Halo. I can't recall if there is chat in Halo, but maybe it could be used for something like that as well.

**Jamie**:
So what you're saying is you and your team essentially just wanted to make a video again. That's it. And you thought, "I know. I'll just pick out all of the technologies that they used to make video games and a video game will happen," right?

**Russ**:
You gotta make crypto fun, right?

**Jamie**:
Yeah. You can't gamify something without using gaming technology.

**Russ**:
Right. The game here is just to get all your crypto test factors to pass.

**Jamie**:
That's exactly it. Doesn't matter whether the tests actually pass, just putting `Assert(true)`.

**Russ**:
Yeah

**Jamie**:
That many or may not be how I write my unit test. It's not how I write my unit tests.

**Russ**:
Yeah, that wouldn't be too good of a unit test. That 100% code coverage would be pretty much useless.

**Jamie**:
I'm not going to say I haven't seen it before.

### Examples

**Jamie**:
So you've mentioned earlier on about everything really should be async and the way that you are using in your current project is it's synchronously async. Could you give us the background into the async path that you should go down and then maybe a discussion on the synchronously async/asyncly synchronous stuff?

**Russ**:
I can sure try.

The whole idea of asynchronous code is when you hit an IO portion, where you're waiting on some external resources or something like that, you can release that context in order to work on other work while waiting on the original work to come back for response. That's the whole idea of Orleans: It's constantly switching contexts, but all of that is abstracted away from you, and that allows you to not have to worry about it. You literally just write asynchronous code, you do your awaits as normal, and it all just fits together.

One of the things that was described when we were looking for something like Orleans was a Map-Reduce problem, where you break up your problem into small enough chunks - in our case, they're not especially small chunks. But you break it up into chunks, you farm it out to a server, and then it puts it all back together for you when it's done. Orleans more or less does that for us, and it's really nice because that is not something I would want to write. And it's worked great for us so far.

The method we're using it, I mentioned a little bit before, but we are taking in the calls in an asynchronous manor, immediately dispatching a new call that represents the actual crypto that needs to be run onto a separate task scheduler. And then the Orleans task scheduler immediately return in order for it to be able to process more requests.

So we are literally standing up machines throughout our little cluster, and we were just able to utilise much more of their horsepower than we would have been able to just on a single machine.

**Jamie**:
So I'm trying to think of a real world example which could kind of explain how you're doing that. And the only way I can think of is to slightly modify my stock answer for async stuff. So somebody asks me to describe basic stuff, I usually say:

So you boil a kettle, you put the water in the kettle, you swhich the kettle on and you can do one of two things. You can stand and stare at the cattle and do nothing else until it boils - that's synchronous. Or you can go, "Hey, that's boiling. I should get out my phone and go through reddit or I'll go through Facebook. I'll do something else. Whilst that's working." And that's your asynchronous.

**Russ**:
Yeah, or get your tea leaves.

**Jamie**:
Yeah, exactly. Right. So you're doing other things is what I'm getting at. I can't think of how to alter that example.

**Russ**:
So we're doing it on that level. But imagine you're creating tea for an entire group of people. And you can bring up as many kettles - putting your loose leaf tea in your brewer, I don't even know what that metal mesh thing is called, or if that's how you Englanders make your tea. I don't know. Do you do bags or do you do loose leaf mostly?

**Jamie**:
It all depends. So some people do bags, some people to loose leaf.

**Russ**:
Okay.

**Jamie**:
I tend to flit between the two. So I've had some camomile tea this evening and I've used tea bags. But if I'm drinking green tea, there's quite a complicated mug that I have where put the tea leaves in, and there's almost like a cage that they sit in, in the water. But it's really complicated.

**Russ**:
So you're tea example works. Just we're on a much larger scale of tea requirements. We need hundreds, if not thousands, of cups of tea, so we can spin up as many houses to make that tea as we need. Being constrained to our hardware, of course.

But that's the idea: you spin up resources as you need them, and all of these little actors can handle anything that gets thrown at them. So you could have one node in the cluster that is able to accomplish any portion of the tea making process. So if everything is busy making water than you get another request in,that request can either make water or get the tea ready. It doesn't really matter. That's the power of Orleans. Hopefully, that makes sense.

**Jamie**:
I mean, certainly makes sense to me. But I drink a lot of tea. So maybe a coffee drinker wouldn't really get it.

**Russ**:
Well, I'm both, so I get it. But hopefully not tea drinkers will as well.

**Jamie**:
So let's imagine that you're working on something outside of work and, you go, "I know. I'm going to use Orleans for this." What kind of project would that be? Is Orleans suited to almost anything that you can break down and send out async? Or is it more a case off, "Here's a problem domain, and it kind of fits"?

**Russ**:
I haven't had much of a chance to think about that. I mean, that's another part of the reasons I'm trying to do these blog posts to kind of understand more about how to use it, not in my business case.

There is, of course, some overhead with distributing these calls. So I would think that you would want it to be small calls that you're doing pretty often. Not necessarily just one offthings that you're doing, like one time a day. This is probably something that being hit constantly. And that, to me, seems like the ideal use case of Orleans.

Like some of the examples were that chat program. I guess that could run locally, but you can also distribute it on Orleans, as the samples show. But just lots of small little asynchronous calls that you could get some benefit out of not doing locally, I guess, would be the ideal use case.

**Jamie**:
So an example I'm thinking off is more from the Web Dev perspective. So I have maybe an API that my UI is talking to, and my UI says, "Hey, I need you to go generate this report." And the report takes seconds to create because maybe is pulling in lots of data from multiple sources. Putting it through a pre-processor are spitting out a PDF or something. I'm thinking if it takes that long, I could send a request to my API, my API could go , "Hey, Orleans, all the data, go do the thing."

**Russ**:
Yeah, Or Orleans could even, say you were getting data from multiple other APIs,you could farm out those individual API calls to say separate nodes in a cluster on Orleans and get them all accomplished at the same time rather than one at a time. I mean, granted their asynchronous anyway, ideally. So it wouldn't really be one at a time, anyway, but that's the idea of the cluster and the nodes in Orleans.

**Jamie**:
Okay, so you're fanning it out. You're one API call goes out, it hits some kind of controller and then it goes, "Hey, you fifteen clusters. Here's some things I want you all to do on let me know when you're finished and then I'll pass that aggregate response back."

**Russ**:
Yeah.

**Jamie**:
That sounds pretty useful, actually.

**Russ**:
I think one of the other guys on the Slack had mentioned - we were talking about Orleans a little bit - and he had mentioned potentially being able to farm out some image processing to Orleans.

Now, I don't know much about image processing and whether or not it's asynchronous or not. But he said he had a unique identifier that needed to be applied to every one of these hundreds or thousands of pages, whatever it was. And if that were asynchronous that would work very well out of the box with Orleans. And if it were synchronous, you could do something like the model we're using at NIST, which I don't know if I elaborated on it much with the different task manager's that we're using: we're using an [observer pattern](https://en.wikipedia.org/wiki/Observer_pattern) in order to notify the client portion of our app that the cluster has finished its processing, and that's how we get the information back.

**Jamie**:
Presumably, you're observing for the responses coming back from your Orleans clusters.

**Russ**:
Yep.

**Jamie**:
I like the idea of doing multiple image manipulationy tasks farmed out. Because, you know, if you have ten thousand images and you need to do the exact same processing on all ten thousand images, presumably you can send an image to a different cluster and say, "Hey, go and do this processing on all of these images," and then when we done maybe we zip them up and send them to the user or something,

**Russ**:
Right. The only real restrictions of it are it has to be asynchronous, at least at the entry point, and it has to be serialisable. But I mean, you can pretty much serialise everything. You could potentially even save these things out to a database and have the actual actors pull them from the database. I haven't tried that, but I don't see why that wouldn't work if you didn't want to be serialising and de-serialising that much data across the wire constantly.

**Jamie**:
So I guess you can still use the full .NET Core compatible suite of NuGet packages and libraries and things.

**Russ**:
Oh, yeah. And yeah the new release of Orleans, I mentioned it is in .NET Core, but I'm pretty sure it's also .NET Standard two. Yeah, so you can use that pretty much everywhere. We haven't tried standing up a cluster on Linux yet, but that is now an option with the 2.0 release.

**Jamie**:
Where can people go to find out more about the work you're doing with, say, Orleans or just some interesting stuff?

**Russ**:
Well, there is great Orleans documentation on the [Orleans GitHub](https://dotnet.github.io/orleans/). I have a [medium account](https://medium.com/@kritner/) - which the exact url is escaping me, but my handle is Kritner. Medium, I'm mostly on [dev.to](https://dev.to/kritner), [Twitter](https://twitter.com/RLHammett). Didn't get Kritner on Twitter. Someone stole it.

Yeah, Kritner is my gaming handle. As I heard you [discussing with Ardalis](/episode-9-designing-your-net-core-applications-with-steve-smith/) the other day, I would think that a lot of people in our line of work could have gaming handles like that. And also, if you're interested about the project I'm working on, if nothing else, to see a lot of documentation, our specifications for our API are out there on GitHub [usnistgov/acvp](https://github.com/usnistgov/acvp).

**Jamie**:
Some of the project that you're working on, I mean, obviously some of it will be NDA'd, I guess.

**Russ**:
Yeah, the actual code for the project I'm working on is not open source, but the specifications for it are.

**Jamie**:
I mean, that makes sense. If people are going to hook into your APIs, they need to know how to hook into the APIs.

You've given us and links for Medium, and Twitter, and dev.to, and stuff, so I'll make sure they go into the show notes.

**Russ**:
Sounds good.

**Jamie**:
Are there any other things about Orleans that you want to recommend to the listeners? Maybe you just want to scream out, "go check out Orleabs because it's amazing!" Or maybe you just want to go, "hey, you know, it's cool"

**Russ**:
Orleans is pretty amazing. And there are some great contributions that the .NET guys have put out on a separate repository.

One of the coolest things that I found on that repository is the [Orleans Dashboard](https://github.com/OrleansContrib/OrleansDashboard). It basically gives you metrics on how your cluster is running. It shows you like how many of your grains - which are the individual primitives that are created in Orleans - how many of those are, like, activated and working and shows error rates and graphs. Just crazy graphs. And it's always nice to be able to visualize how your system is running, and it's a very cool project and its built in React, so I know nothing about it. But what I'm doing right now, it's strictly C#. An God, I love C#. It's just it's great.

**Jamie**:
So something that should've asked earlier on, I guess, is does Orleans only support C#? Or because it's a .NET Standard package, does it support VB and Sharp if you're that way Inclined?

**Russ**:
I would imagine it supports more. I have not actually written a line of VB in probably 7 years, and I've just barely touched F#, so I can't really speak to it. But, yeah, like you said, because it's in .NET Standard, that should be the case.

**Jamie**:
So thank you ever so much for being on the podcast, Russ, and for talking to us about Orleans. Thank you ever so much.

**Russ**:
Thanks for having me.

### Wrapping Up

That was my interview with Russell Hammett. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and a full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/).

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Russell Hammett on twitter](https://twitter.com/RLHammett)
- [NIST](https://www.nist.gov/)
- [Orleans](https://dotnet.github.io/orleans/)
- [CodingBlocks Podcast](https://codingblocks.net/)
- [Getting Started with Microsoft Orleans](https://medium.com/@kritner/getting-started-with-microsoft-orleans-882cdac4307f?source=friends_link&sk=1fc3451d71a19dcb49f2c8bbeb6b079e)
  - The first in Russell's blog posts about Orleans
- [Observer Pattern](https://en.wikipedia.org/wiki/Observer_pattern) 
- [Orleans Dashboard](https://github.com/OrleansContrib/OrleansDashboard)