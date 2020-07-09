# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is episode 41: Visual Recode with Mark Rendle. In this episode I interviewed Mark about Visual Recode, why you might consider using it to move your WCF applications over to gRPC, why you might _want_ to do that, and what  doing so actually provides you with. This is actually part two of the interview that I had with Mark. It was so densely packed that I wanted to split it into two episodes, so that we wouldn't overload you with all of the great stuff that Mark had to say. If you haven't heard part one, check out [Episode 39 - gRPC with Mark Rendle](https://dotnetcore.show/episode-39-grpc-with-mark-rendle/) for a little background to the topics we discuss in this episode.

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### What Is VisualRecode?

**Jamie**

So we're going to also talk about Visual, it's Visual Recode isn't it?

**Mark**

Visual Recode, yes.

So this was as I started getting into the looking and writing stuff for WCF developers going, "don't be afraid to gRPC it actually does most of the things that you want. And it does them in a very similar way, it's not that different." And I was, I idly mused on Twitter. One of the nice things about WCF is with its service contracts, and its implementations and its full contracts and its data contracts, all those attributes. Basically, there was enough metadata in those attributes and within the code itself, to generate the WSDL file. And the WSDL file is like a really, really horrible long XML schema'd, late 90s / early 2000s equivalent of the proto file. And I thought, "if you can generate a WSDL file using reflection, then I wonder if I could generate a protot file using Roslyn." And so I had a quick go. And then a quick go turned into, I think a fortnight of evenings with my wife going, "are you coming downstairs ever again?" Like, "I'm trying to code myself out of a job."

But at the end of two weeks, I got a very, very simple WCF application. And not only could I generate the proto file, to define the equivalent application in gRPC. I could also copy across all the necessary code and wire it up to... Yeah, basically I had a console application that you could run on a WCF - my test WCF application - and it would output the result. And you could run the result. And it was a gRPC application. I wrote a couple of blog posts doing my benchmark comparisons of the two. And that was actually done using a generated application. But from this, it was a console application. And it was basically custom written for this one WCF thing. And if you threw something at it, it didn't understand it would explode. And I hadn't even got as far as putting in command line arguments to say, "that solution." Never mind the fact that that solution might have 100 projects in it and you want to tell it exactly. It would have been a nightmare to use from the command line.

And speaking of open source, I have open sourced everything I've ever done. In this way things like [Simple.Data](https://github.com/markrendle/Simple.Data), which is my.. an idle experiment to see if you could do something and then ended up going nuts. But this time I thought, "if I open source this, then people are going to want to use it, which means I'm going to have to support it. I haven't got time to support it. And any way the people who have this problem and the people who are angry about Microsoft dropping support for WCF, they've got millions of lines of code. And each of those lines of code just cost them $1." So I got in touch with Kendall Miller at [Gibraltar Software](https://www.gibraltarsoftware.com/). Who is a good friend of mine. And I said, "Hey, Kendall, look what I've done." And he went, "Ooh!" And I went, "do you think I could sell that?" And he said, "I think I could sell it."

He said, "If you turn it into a Visual Studio plugin, and make it easy to use,  make it fit nicely with the Visual Studio thing that I think we've got something that that we can go to market with." And so that's what I've been working on. Literally four o'clock this afternoon, I did a push to private GitHub repository, which triggered a build in Azure DevOps. And I said, "That's preview one." Preview, which hopefully we're going to be distributing within the next couple of days; we need to get it sorted with certificates and sign the package and everything. And we're just going to send the VSIX to a few people to start off with. And so far, it does WCF request/response, but it will pretty much generate the gRPC application. And as long as everything, as long as all the code in the WCF application is valid .NET Core code, then it will just work. Otherwise, you'll have a lot of red squiggles that you have to fix. But it still does a big chunk of the work.

**Jamie**

It gets you, sort of 90%?

**Mark**

Yes. And it will vary from from person to person. And, you know, there's obviously, you've still got to then go, "where do I run the gRPC application?" Because you can't run it in IIS at the moment, you might be able to run it and IIS by the end of next year; because IIS and HTTP.sys don't support all the features of HTTP/2: response trailers, things like that. But it will, hopefully, the majority of people's valuable code is not the stuff that's decorated with data contract and data members operation contract and, and that sort of thing. Hopefully it's in some kind of layered architecture and dependency injection. But what Recode actually does is it reads your contracts, generates the proto file, copies your service contract implementation, and your data contract stuff across, sets up as your service contract to dependency injection - so then it can be injected into the gRPC service - and then maps from .NET data types to gRPC data types, and back again. But for the most part, it is just your code that has been copied across. It also detects all the dependencies, so it goes through the entire solution - so if you've got a repository, it'll pull that across. If you've got a factory, it'll pull that across - and it'll drag all these things across into a nice shiny new .NET Core three project. And it generates a report to tell you it's done it and it puts comments in various bits of the code going, "Hey, not sure what's happening here. You might want to fix this." But yeah, so first preview. Very simple. WCF to gRPC. I'm working on getting it to the duplex.

So duplex is really weird because duplex with WCF, you have a callback interface. You go, "Hey server, I have this type here which implements this interface, when you want to ask me something, call a method on this interface," and then the server then generates a kind of a stub proxy thing for that. And it's, well, you can reproduce that with bi-directional streaming in gRPC. But it's, it's quite different. So actually, what Recode is going to do is generate the gRPC stuff, but then wrap it in those interfaces. So the interface will be a kind of facade over the stream at both ends. So you're applying code, you'll be able to take that callback interface that you've already written, and just hook it into the stream. And it will carry on working exactly the same. And when I started working on that, I thought, "why don't I do that for all the client stuff?" So you generate your gRPC client in the normal way. But then I can generate you a wrapper class around that that has exactly the same API as your old WCF client. Which you can then you know, bundle those two things into a NuGet package and ship it and there's a reasonable chance that other developers who were using your WCF client can just drop it in and not even notice that anything's changed. So yeah, that's the next step. And Yeah, the aim is to have it sort of essentially feature complete by the end of the year. But once we've, we've got early preview partners, and it's going to be interesting. We've been speaking to a few people. And yeah, we're talking about people who've got solutions with hundreds of projects in a single solution. And so yeah, we're gonna throw it in the deep end, get into these guys work quite closely with them. And yeah, so it's not open source. Because my hope is that I can be doing this for a living in a year's time.

**Jamie**

Yeah, like you said, you know, you release it open source, it becomes a full time job anyway. So I why not charge a few bucks, make a little money, and support it at the same time? 

**Mark**

It's not going to be prohibitively expensive.

And for a lot of people - So you look at something like ReSharper or nCrunch, that's an ongoing expense, you need to, they are subscription based, and you buy it. And then you can stop paying the subscription and you're stuck with that version that you've got. But ReSharper is something that you are going to want to be using for the rest of your life, the rest of your professional life. Visual Recode, if it does its job properly, for a lot of people it will be, "buy this for a couple hundred dollars, whatever the price for an individual licence ends up being, run your code for once you're done." You haven't got any NuGet packages, so any supporting code we need we generate directly into your application. And yeah, for a lot of people, it's going to be, we'll just get it will run stuff through it. And once we're done, we're done and then we don't need it anymore. Thanks very much. And that's great. And then the big organisation who've got hundreds of millions of lines of code across thousands and thousands of projects, it's going to take a bit longer. And so those are the guys where we're going to be digging in for the for the long haul, and sort of reacting to their needs and feedback and reports and so on.

Judging by some of Microsoft past sort of escapades we'll probably add in functionality, maybe even in the lite version, so that when .NET five comes along, and they've changed project files, again, it'll do that for you as well. But yeah, that's the sort of thing if I can get to the point where my living costs are covered by that revenue stream plus, hopefully some consulting. So you know, I can come in and I can look at your systems and I can say, "this is that one and that one, and, yeah, no, there's no way Roslyn analyser can understand whatever that is." But also I can help people with sort of running it on Kubernetes and setting up service meshes, and load testing, and planning adoption strategies and all that sort of thing. And yet, if we can get to the point where it's generating enough revenue to be a sustainable business, then there's a very real possibility that some of the more widely usable features will be in a sort of lite version or like, like [CodeRush](https://www.devexpress.com/products/coderush/) has a free version and a paid version doesn't it? So we've discussed that as a possible model once it's paying for itself. But yeah, very excited about it. I have never worked so hard on a personal project as I have on this. I've never spent quite so much time dotting T's and crossing I's, and using the valuable lessons that I've learned from my eight year old son about testing

**Jamie**

Yes.

### The Irony of Creating New Tech To Help Older Tech

**Mark**

I'm very excited. I think it's, it's, it looks really good. It's got two modes. There's a wizard and it says, "What do you want to do?" And three of the buttons are disabled. [You say] "I want to convert a WCF application to gRPC, "and then it goes, "Okay, so open existing solution or create a new one?" and then open a project or create project, and then choose the service contract that you want to convert across. And then if it's got a callback contract it'll say, "okay, I'm sorry, I can't do that yet."

But this is the thing. I've been testing the sad path, it doesn't just kind of go, "Oh, I don't know what's happening," and crash. It actually stops you from shooting yourself in the foot. That takes you through the kind of nice step by step, and there's a progress par, and it generates it, and then there's a button that says, "open this in another Visual Studio." But once you've got started, you can actually just click a service contract, or a data contract, or any class you like in your solution explorer and drag it onto the Visual Recode window and it doesn't only bring that class across, it also brings all its dependencies across. And it it rewrites NuGet package mappings. If you've got a NuGet package reference, and it can't find .NET Standard or .NET Core version it'll put that into the report saying, "there's no .NET Core version of this. And also this NuGet package you're using hasn't been updated since 2005. Which is actually before NuGet how have you done that?"

But yeah. Visual Studio extensions are not the easiest things to write. I have a newfound respect for the ReSharper guys, and Mark Miller who does CodeRush, and Remco Mulder who does NCrunch. And anybody who writes... Mads Kristensen who just churns them out, and gives them away. And bless him for putting all the source code for all of them on GitHub, because there have been a lot of times when I go, "Oh, how do you do... hang on, I'll go and check." Yes, I think the most frustrating thing of all though - I'm pretty sure this is irony - I've been all over ASP. NET Core and .NET Core, since it was Project K, I was actually an MVP when they started working on it, which means I knew about it under NDA for about six months before they announced it to the public. And I was downloading it and doing things with it. I put a production micro service out when it was still Project K.

It did one thing: it generated GUIDs. It had an HTTP endpoint, it didn't matter what you sent to it, it would send back `text/text`, and it was just a GUID. And the only reason it existed was because node is terrible at generating UUIDs.

**Jamie**

Wow.

I think you could have left the generating UUIDs off of that sentence. Personal opinion.

**Mark**

Node is very good at some of the things that node is very good at. As long as it doesn't need to do something with the CPU, as oon as it needs to do something with the CPU that's it, everything stops. And if it takes a 10th of a second, to generate a UUID, which in JavaScript on the hardware we had was roughly how long it took. That means you can serve 10 requests a second. Which when you're writing a web bug on one of the UK's biggest websites, to track people's progress through their thing isn't really enough.

And I have blogged about it. And I've been talking about it at conferences for the last three years. And I've been, you know, with .NET Core three and C# eight, I've been sort of keeping up with it and downloading all the previews and everything. And now, the thing that I'm spending most of my spare time working on and the thing that I would dearly love to be able to do for a living .NET 4.7.2. Because that's what Visual Studio has written it. Yeah. And that's what I have to use. And I'm really really, really hoping that Visual Studio 2021 is going to be ported over to .NET five.

They're going to have to do with eventually. Yeah, but I imagine it's going to be difficult.

**Jamie**

Yes.

**Mark**

Yeah. Not gonna hold my breath. I keep typing C# 8 code, and then just getting rid squiggles, and it's going, "aarghh," because you can't. C#7.3 works with .NET 4.7.2

Bu C# 8? No. They actually changed. They changed too much. So I can't do switch expressions, and I can't turn on nullable references either. Which will be really useful.

**Jamie**

Yes

**Mark**

I'm very, very proud of it. And I'm really excited once we've got the feedback from the early preview guys, and things have stabilised a bit, then it will go on to the Visual Studio marketplace. And until we actually come out with our 1.0, what you will get from the marketplace will be the full thing. But it will explode 30 days after we've released it.

**Jamie**

Ok.

**Mark**

In the best way of all early access programmes, there's a time limit on it. But if you're cunning, and you're quick, and you've only got a little bit of WCF code, then there's a very real chance that you could probably get the whole thing done before we actually release the paid version.

**Jamie**

Well, I wouldn't recommend people do that.

**Mark**

No

**Jamie**

But I think it's a good idea to try it.

**Mark**

Absolutely.

**Jamie**

Throw your WCF code at it, if you get the chance to during that 30 day window. And just see what it can do. Because there might be things that you have done, or your team has done, or the person who wrote the WCF code that you're maintaining has done, that maybe Visual Recode doesn't know about yet, or support yet. Or [things that] it doesn't support, full stop.

At which point they could contact?

**Mark**

They could contact me, and I could go, "Oh, I could I could make it do that," or "yeah, no, just don't." Or maybe put up a message box going, "could you refactor this before you convert it, because it will make my life much easier."

**Jamie**

And indeed it might just be part of the 1%, 10%, 20% of the stuff that Visual Recode can't do, because it can do everything.

**Mark**

Yes.

**Jamie**

But it will take away the six months, painful pulling out what's left of everyone's hair, and screaming, and everyone, trying to get everything slowly moved over.

**Mark**

Yes.

**Jamie**

Whereas you can maybe do it in a half a day.

**Mark**

I'm really hoping that the stuff it can do is the boring stuff. Because nobody wants to sit there with two screens with a service contract on one of them typing the equivalent proto file on the other one, that's just, that's nuts. That is not a way anyone wants to spend the next few years. So yeah, it's not even artificial intelligence. It's just "if this, then that; if this then that; filter this; replace these," it is doing the most mindless aspect of the programming for you. So yeah, I don't think it's certainly not going to be taking anyone's jobs away or nothing. I'm kind of half thinking once I've done with this, I'm going to do COBOL.

### Everything is Legacy

**Jamie**

You say that it's not going to take anyone's job away, and it's not. But there is an argument for when a project manager comes to you and says, "We want you to take this WCF, this code base; I don't understand what it is because I'm a project manager. I want you to take this code and make it run on the new hot sexiness, because I've heard all of these keywords and all these buzzwords, and I've been to a few talks with other project managers, do it." And then you go, "it's going to take six months. Or we can spend a number of dollars," because you don't know maybe what the price is going to be yet, "download an app that will do most of it. And it'll take me a couple of weeks to sort of fix the extra bits."

I mean, it's a no-brainer. The project manager is going to go, I will get the authorization before the [end of the day]."

**Mark**

Yeah, if you say, "it would take six months,"  there's very little chance that's gonna happen at all.

**Jamie**

Exactly.

**Mark**

Whereas if you say, "$300, or $1000-$1500 for a team licence, and we can do it in six weeks, or a sprint," or whatever, you know - and this depends on your project - then it doesn't just make it quicker, it turns it into something that is going to happen.

**Jamie**

Exactly.

**Mark**

As opposed to something that's not going to happen. And, yeah, that's gotta be good.

**Jamie**

Because there's a project management technique that I know of - I'm not a project manager at all but - where you draw an x and y axis of maximum effort and maximum reward.

**Mark**

Yes.

Yes. And certainly if you're in anything in the financial sector, anything in public facing; so NHS, which is one of the biggest it organisations in the UK, anything like that; they've got developers who spend their entire careers, just keeping up with changes in regulation. And so it's not a matter of they're not willing to spend six months retooling from one technology to another. They can't, because they've got to keep changing the way the tax regulations work, or the way the SEC reporting is done, or the way patient data is, you know they've got to stay on top of this stuff. It's very easy, I think, for people who haven't worked in enterprise environments, there's some sneering, there's the "durp" thing; which is, there are some really, really smart people working in those environments, you know. WCF, we kind of go, "oh, why are you doing WCF? Well, you should have been doing ReST and hypermedia." There are people who are doing things with WCF that I didn't know it could do. And it's doing it fast. And they, you know, they're really pushing it. And so yeah, one thing I've learned over the last sort, the course of this year really is yeah, not to make assumptions about other people's situations. Yes, I have 100,000 lines of code in this thing that I've written, and it really wouldn't take very long time to change it from an MVC application to the gRPC application. But yeah, walk a mile in their shoes. If I can help people not get stuck in yet another computer legacy trap, and if I can make a bit of money while I'm doing it, then I will be very happy.

**Jamie**

Yeah, exactly. And I, you know, I try to do that with with some of the stuff I do: I try to give back. If there's something that I can do to help someone, even if it saves someone five minutes. That's five, like, the way I see it, is that five minutes of their life, they never gonna get back, you know. And like you say, if you're trapped in a situation where every couple of weeks you're having to change because of some regulation, or because of some management decision, or some decision somewhere else you have no control over, and you have to change every now and again; then you're never going to progress with whatever project you're working on. So it's taking away that, "let's not worry about progression but you do the bit that you're great at, which is the you know, without trying to reduce what you're doing the you're looking after making sure that it's you know, regulatory or whatever. And we'll just come in and just do the bit that needs to be done. Yeah. And then you You can just sort of jump back on to where you were.

**Mark**

That's it.

**Jamie**

And away you go.

**Mark**

You have your domain knowledge, you know how your business works, you know what its requirements are, you know all the other parts of your business. And you've written the ridiculously complicated algorithms and database queries and everything else that actually makes you money. I'm just going to come along and shave this exterior bit off and put this new exterior bit on for you.

And, one of the things that we'd like to be able to do is, in the same way that people that I said, you can have an MVC, so an HTTP API, and the gRPC API, running off the same code. One thing I thought would be really nice: So we'll do the thing where we can generate a client wrapper. So it looks the same at both ends. So it makes it easier to migrate. But also to be able to put notes in the generated code. So if you then change the WCF application, you can hit refresh. And it pulls the changes from the WCF application across into the gRPC application. So you can be continuing to add features on the side that you're used to, and run WCF and gRPC in parallel; and have them doing the same thing, talking to the same databases and the same back end services and everything else. Because I had, I was talking to somebody and he's kind of like, "we got a WCF thing. And  it's just doing soap. But we've got 150 utility providers of some description all talking to our API, and we can't turn around to them and say, 'Hey!' because they're external." Again, you don't know what they're going through.

And so yeah, I kind of went away and did some rough notes, and, "can we do this?" and "what would I have to do?" But yeah, to be able to come and go, "okay, so we're doing gRPC now; here's a proto file." But not have to be actively maintaining two codebases. Either by, "lets yank this out into a dual framework shared library that works with both of them." And as much as possible, I think that's the best way to go. But also just being able to go. "change the API slightly add in an extra integer parameter. So I'm just going to drag that across and put it in the parameter on this slide and so on." So, yeah. The aim is that my wife's kind of going, "so they buy it, they use it, and then that's it? How long you expecting to make a living off this for?"

**Jamie**

By the same token you will end up with customers. You don't just have one WCF stack. Like you were saying you've got hundreds of thousands of projects in one place.

**Mark**

And also, you know, a lot of them are oil tankers as well. And so yeah, there are going to be companies next year buying this and running their stuff through it. In five years, there's going to be the more conservative companies doing it. I have consulted with people in the last four years who are still running code that was written in Visual Studio 2003. And it's dotnet 1.1. And they're kind of going, "why is this slow?" And you're like, "is this a 486?" And it is, and they're going, "and guess what? We can't upgrade it."

And so yeah, like I say, in 10 years time, maybe they'll be the ones who are finally getting there. And by that point, it's going to be just seamless. 10 years of development, and I will get it working.

But other things will come along, and this is going to be an ongoing situation. And yes, you don't know what the world's going to look like in 10 years. You know, maybe I'll be kind of going, "oh, I can take your UWP application and convert it to run on HoloLens," or whatever.

**Jamie**

Yeah. I mean, you made the joke earlier about, "maybe I'll go on to COBOL next," you know, and COBOL is a language that was [created] in the 60s - maybe even earlier, my entire history of computer programming languages is a bit murky - but, you know, and it's still being used now, because those systems are bulletproof. They have to run. Our entire society, whether you know it or not requires those systems to be up and running. And if they're not: Game Over.

**Mark**

I think I'm pretty, sure ifwe go, "oh COBOL is old and dead." I'm pretty sure anybody who gets paid, and then money just appears in their bank account, one day every month. I'm 99.9% sure there's some COBOL doing that somewhere in the BACS system, or in the FIC system, or whatever these things are.

And, yeah. I think the real thing there is, if you went to the banks and said, "hey, I can rewrite all this COBOL code for you!" They'd go, "why? Why would you want to do that? It works. It's fine. IBM keep supporting the mainframes and keep selling us insanely expensive operating system licences to keep supporting AIX." But yeah, I will move with the times and kind of go, "what can I do now?" And also, you know, I spent the last half of this year writing a book; writing this thing in my spare time, and I've still got a day job. And I do conferences, and programme committees, and I have been a very busy boy.

But yeah, if I can get to the point where this is my job that will give me a little A lot more time to spend on other things. Because the other thing that maybe I could be doing in 10 years is running an independent game studio with my kids. Which would also be awesome.

**Jamie**

Yeah.

**Mark**

Because one of them's very arty and very creative. And, and yeah, he's felt tips and all this sort of stuff. And his big sister seems to have the same coding gene that I've got. She I gave her a copy of C# and she just whoosh. So Yeah, that'd be nice. Even if it's just, you know, main full time job is Visual Recode, but I've got enough time and space to make games with them and stick them on app stores and stuff that would be awesome too.

### Contacting Mark

**Jamie**

So where can folks go to learn about Visual Recode? Obviously, there is a website.

**Mark**

There is a website. It's [visualrecode.com](http://visualrecode.com/).

Which, if you've followed my product naming tendencies in the past, is probably the easiest web address that I've ever used for anything: [visualrecode.com](http://visualrecode.com/). There's information about the product there, you can sign up for updates. People who sign up to the mailing list for updates will be the second in line for the preview releases. So we've got kind of people were actually speaking to, who are going to do our very, very early testing - kind of a private beta thing - but then people on mailing list will get informed when there is public beta. And like I say, it will be full featured, but time limited. So it's not going to go, "I'm not doing this. It's a million lines of code." Because I haven't written the code to work out if it's a million lines of code.

But then you can get it and you can try it. And you can give us feedback. And I'm doing all the development work, or the lion's share of the development work. Gibralter Software, who do [Loupe](https://onloupe.com/) and [VistaDB](https://vistadb.com/), they will be doing all sales, marketing, licencing, frontline support. So this has got a proper software company that's experienced in the enterprise world and in the formal software world handling all the the business stuff so we will have a support site, we will have a knowledge base, we will have all that sort of stuff as well. Which anyone who knows me will be very grateful, responsible for that side of things. But yes, and like I say the game is to have it on the Visual Studio marketplace in November, and probably have something that we feel comfortable asking people to pay for by the end of the year.

**Jamie**

Excellent. Okay. So what about yourself and what's the best way to keep in touch with what you're up to, what you're doing, all that kind of stuff?

**Mark**

Follow me on Twitter: [@MarkRendell](https://twitter.com/markrendle), R-E-N-D-L-E. There's a [@VisualRecode](https://twitter.com/VisualRecode) on Twitter, you can follow that as well. And that's just me as well, but it's an account.

If you want to see me speak, then if you're in the UK, or Europe, and you have a user group, and you'd like [me] to come and talk about gRPC, or any of this stuff, then reaching out through Twitter. I love wandering around and talking about stuff. NDC conferences do all those. Yeah. I put myself out there.

And if you are at a conference, and you are an attendee and I know a lot of people go to conferences, and speakers hanging out with other speakers. They're kind of, it's like their own work buddies, but we only see them every three months. And so we tend to hang out in groups. And somebody told me that they, they plucked up the courage to come and talk to me. Which threw me completely because I'm quite, actually, I'm quite introverted. And I'm quite shy. And one of the reasons that I like speaking at conferences is it helps me to get over that.

I can kind of go, "I have a right to be here because I speak." But if you see me at a conference, and you want to come up and talk about stuff then, as you can probably tell from the fact that we've been recording for two hours now: I love talking, and I love talking about tech. And I love talking about other things as well: space, and quantum physics, and philosophy, and stuff. So yeah, I probably won't come up and talk to you about conference because I'm shy. But yeah, anytime anyone sees me anywhere, just come say, "hi".

**Jamie**

Yes.

Okay. Excellent. Sound Advice.

Well, that's essentially all the questions that I've got. And like you said, we have talked about stuff for two hours, but that's [ok] because I can split that across multiple episodes. So this might be the world's first .NET Core Podcast two-parter.

**Mark**

Wind me up and let me go.

**Jamie**

That's it. But yeah, so all it really remains to say is, thank you ever so much for taking the trip across the city of London, in rush hour to come to do the show. I mean, it really does mean a lot.

**Mark**

That's been a pleasure. I've really enjoyed it. And hopefully I'll be speaking to you again. Let's set it up and we'll speak in a year's time. And I can tell you what my yacht's like.

**Jamie**

That's it, right? We'll do the next episode on your yacht.

**Mark**

Or, you know, maybe when we get Club Penguin with the felt tip drawings on the app store. 

**Jamie**

Yeah. Why not?

**Mark**

I can come and talk to you about that.

**Jamie**

Yeah, I do need to talk to someone about Unity. So.

**Mark**

Oh, yeah.

**Jamie**

Well, yeah, like I said, thank you very much for taking the time. It does mean a lot.

**Mark**

Thank you for having me.

### Wrapping Up

That was part two of my interview with Mark Rendle. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and a full transcription of the interview. The show notes, as always, can be found at dotnetcore.show.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Episode 39 - gRPC with Mark Rendle](https://dotnetcore.show/episode-39-grpc-with-mark-rendle/) 
- [Mark Rendle on twitter](https://twitter.com/@markrendle)
- [Simple.Data](https://github.com/markrendle/Simple.Data)
- [Gibraltar Software](https://www.gibraltarsoftware.com/)
- [CodeRush](https://www.devexpress.com/products/coderush/)
- [@VisualRecode on Twitter](https://twitter.com/VisualRecode)
- [visualrecode.com](http://visualrecode.com/)
- [Loupe](https://onloupe.com/)
- [VistaDB](https://vistadb.com/)
