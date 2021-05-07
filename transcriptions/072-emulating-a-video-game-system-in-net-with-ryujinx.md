### Episode Transcription

#### JD
 
I just have to add all of this is possible thanks to the amazing team behind the writing project. And I'm here today on behalf of the ridings project representing an amazing team of people made up of incredibly talented and smart developers. And I certainly wont and can't pretend that everything we're going to be talking about today was all achieved or discovered by myself. In fact, quite the contrary.

I'm a fairly small contributor of the project relative to some of the work done by gdkchan, who was obviously the lead developer, but also ack77 and Thog, who have both been here from pretty much the very beginning. We've got riperiperi and LDj3SNuD, emmauss, Xpl0itR and MooseHunter along with a whole array of more casual contributors to the project. But I guess I've been here pretty much from the very start. And so I think I have a fairly unique perspective to share the entire project and its progress through the years.

---

Hello everyone and welcome to _THE_ .NET Core Podcast. A podcast where we reach into the core of the .NET technology stack and, with the help of the .NET community, present you with the information that you need in order to grok the many moving parts of one of the biggest cross-platform, multi-application frameworks on the planet.

I am your host, Jamie "GaProgMan" Taylor. In this episode we chatted with JD, one of folks who works on the open source, .NET based, Nintendo Switch Emulator: RyuJinx. RyuJinx, as we'll find out, is written entirely in .NET 5 (at the time of recording, the team were starting the migration over from .NET Core). There's a wonderful moment during the conversation where JD blew my mind with talk of RyuJIT (the just-in-time compiler for .NET), and another where he mentioned some of the features we have access to in .NET 5 due to some of the work of the RyuJinx team.

So let's sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

{{< paracentre "The following is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

### Jamie

So first thing I'd like to say, JD/Josh, I don't know which you prefer. I've likely already said it in the intro. We're recording this ahead of the intro record time. So they go there. Thanks for being on the show. It's a, it's it's interesting to talk to folks who are building such amazing systems, I have to say.

### JD

No, my pleasure to be here.

### Jamie

It's a it's, it's. knowing it's not like I in my in my day to day work, right? I build stuff with .NET that's like, web applications, and business line applications and all the "boring stuff" that keeps the world moving. And I've got one or two little games with it, but like, building, like replicating an entire hardware setup in C# and .NET is, it's amazing to me, I think.

### JD

But yeah, yeah, I mean, I've come from the same background as you I do a lot of ASP .NET and stuff like that poor work. But having the ability to sort of have an outlet for that sort of applying the same stuff that I'm learning throughout the day to something that's more creative and more, sort of, not the run of the mill thing is definitely a great experience.

### Jamie

Yeah, definitely. So how about we would you mind introducing yourself to the listeners a little, bit tell us a little bit about you. Like you say, you're presumably ASP .NET Core /  .NET Core Dev by day, I guess. And RyuJinx contributor by night, I guess. What's, what's the, what's the actual...

### JD

Yeah. So I do a lot of .NET stuff during the day. I've done, on and off professionally and unprofessional, I've been probably been working with .NET for the last 10-12 years, I picked it up at a very young age. I just happened to come across a book in a store that was like "C# for beginners," or whatever it was, I picked it up. And I just read that and I was like, this is for me. So that's sort of my beginnings.

Over the time, I've just picked up things here and there. A lot of my stuff obviously, wasn't done professionally as sort of being hobby projects here and there. And it's all sort of culminated into stumbling across one day, this project that was built in C#, something that I knew, and was something that really interested me. I'm really into the low level sort of tinkering and stuff like that. And so combining those two things, my experience with both of those was something really exciting for me.

### Jamie

Awesome, awesome. Yeah. So this is something that Josh and myself have discussed before we hit record, sort off air: how we actually talk about RyuJinx without touching the slightly spiky side of what it's about. But I was wondering, before we hit that, would you mind telling us a little bit about RyuJinx and perhaps the millions of different ways to pronounce the name and what it is and what it's sort of aiming to do?

### JD

Yeah. My personal pronounciation is "RyuJinx". So that's probably what I'm going to end up calling it officially it's RyuJinx, but um, I don't know anyone who actually calls it that.

Um, so yeah, RyuJinx, I sort of came into the project about six to eight months after it was started. But it was started by an incredibly talented developer called GDKchan, who sort of just casually thought, "Oh, this is a cool new system, I thought I'd try and approach this." And he'd used C# and .NET before - .NET Core was very young att that point in time, I think we were on .NET Core one or maybe .NET Core two when that started. And so the ability to build something like that cross-platform in .NET and C# was very much a new thing. Previously, you had .NET framework. And if you wanted to build something like that in C#, "sorry, you're stuck to Windows unless you want to mess around with the beast that is Mono on Linux." And so I think this is really a novel project in that sense, in that it hasn't really been this sort of thing hasn't really been done before, at least to the sort of the level that the Nintendo Switch entails.

And so yeah, over the time, we've been through .NET Core 2.1, 3, 3.1. And now we're up to .NET five, and over time, I've definitely we've seen .NET Core evolve. And thankfully, it's evolved very much in the direction that our projects been going in. They've added in .NET Core 2.1, they added things like intrinsics, which very much leads into doing things that our emulator needs to do at the lower level. And it's been incredibly eye opening for myself as well, to see a project like this come to fruition because everyone has those pre compositions. It's like, "no, you can't build an emulator in C#. You can't build anything that needs low level access. It's not as performant as C or C++. It's just it's not possible. You can't stick to websites." But this project to me is sort of like my, "in your face sort of answer." It's like it is possible.

And so over the time, yeah we've picked up a couple of developers, there's quite a few core developers now who are working on this around the clock; we all love doing it, we all enjoy doing it. And over time, we've started sort of emulating homebrew games, and stuff like that. So sort of as a development tool for other developers who are targeting say homebrew, they want to build Tic-Tac-Toe or Space Invaders for the Nintendo Switch, or they want to port say, Doom to the Nintendo Switch. Without having development consoles, and access to logging in sort of these tools. RyuJinx has been sort of available to them to debug their application, step through it to see how it runs sort of on their desktop computer, rather than on an actual console, and then take it across to an actual console and run it.

And then from there, we've sort of expanded into being able to run commercial games, obviously. Which is, as you say, the spiky part of emulation. But yeah, in the last two and a half years of the projects been going we've gone from no commercial games, running to one commercial game running to now over almost 2000 games being in a bootable or a playable state in the emulator, which I think for an emulator of any sort of level, whether it's a C emulator or a C# emulator, anything, the speed at which this emulator, developed over the years, is pretty much unprecedented. And so that's where it leaves us today with quite a capable emulator capable of near perfect emulation of a number of sort of top level, sort of first party games for the Nintendo Switch. Yeah.

### Jamie

So that's really interesting to me, because like my background, I went to university and did games dev, we did everything in .NET. And, I mean, this was 2002 to 2004. And the lecturer was like, "yeah, you'll never get, like, near native performance out of .NET." I so wish I could track that lecture into how did you say, "Hey, in your face?"

### JD

Not only are we running a game, but we're actually emulating a game from another console, in C# on a desktop machine.

### Jamie

But then, I guess, I suppose that goes hand in hand with the, the increases in performance that's brought about by Microsoft and the .NET contributors. And I guess the sheer horsepower that we now have. Because like, if you look back at 2002, I think I had, I'd custom built a triple core machine that was running on an AMD something or other. And it likely had an ATI graphics card, because I'd heard that they were good together. But we're talking maybe two gigabytes of RAM. And that was enough, because it was Windows 7, - er not even Windows 7, Windows XP. So it's like this will do. And he ran everything I needed to run and run the games as well. But I guess because we've, just the orders of magnitude of hardware. And I suppose the compilers, and tool chains, and the frameworks have just gotten better and better. Because you know, people come along and go, "Hey, can we do SIMD?" And like you say, "Can we do intrinsics, because why not?"

### JD

Yeah, for sure. I mean, I definitely think that's part of it. But we're getting to a position where now scaling hardware vertically is starting to hit the limits of what we can do today. So it's like you have an Nintendo Switch that you want to emulate, but you can't just throw a 15 gigahertz 48 core CPU at the problem. You have to start getting smart about how you apply the technology that you've got. And that's the constant challenge for us. I mean, at the moment, yes, definitely, our emulator runs best on high end CPUs. And one of our big challenges now is, "okay, we've got something working, we've got it working on your 5.2 gigahertz 10 core Intel processors. But how do we adapt that? And how do we optimise that to bring it down to something that the more average Joe is going to have might be a quad core laptop CPU, that's only four gigahertz," and bringing that performance out is something very, well not very easy to do, but it's certainly accessible to C and C++ and native languages. But doing that within C# and a managed language is something that's always a continuing challenge. Because not only are you optimising your code, but you're also having to optimise your platform's code, and Microsoft's code, and seeing places where things could be better and reporting that back to them.

### Jamie

Sure. There's a - how do I put it? It's always best to, sort of, build what you can now. It's almost like, I don't want to end up using buzzwords but it's like the Agile-ish way of doing it. Like, "build what you can and then make it better later," add the scope. Like if the scope or the features are, "can we optimise and make it run slightly cheaper hardware?" You don't do that upfront. And I think it was Donald Knuth who said, "the root of all evil is premature optimisation," right? And so you don't want to be optimising before you've got something runnin, because you don't know whether the code actually does what you want it to yet. Optimise it later, right?

### JD

You don't know what to optimise. It's like you're just guessing. Really. "I think that code looks slow."

### Jamie

Exactly. So just to retouch on something just real quick, right, because I don't think we covered it a little bit. But just for completeness sake. I'm seeing, as an outsider, I'm seeing RyuJinx as a sort of - it's not a, "hey, go pirate your games or run them on your computer." It's more a case of, "can we do it?" Is that the case is? Or is it more a case of, "hey, go pirate the game?"

### JD

Definitely not. I mean, I can speak for myself, and I know, the other core developers of this project well enough to speak for them on this behalf. We're very much for the challenge. And because we think we can do it, so let's go try and do it. RyuJinx started off as an experimental project to see if we could emulate hardware like this, whether it may not have even been the Switch may have just been, "can we emulate an ARM CPU using C# and .NET?" And it's evolved out of that. And I think a lot of our developers, on our core team have come from sort of emulation, and from the sort of the hardware side of it, rather than the software side of it. So they're bought a lot of experience with reverse engineering, the kernels and stuff like that of these platforms. And it's very much for the research side of things. It's like, there's a challenge there, we see it, and we want to know more about this, and we want to learn about this, and the best way to learn is to do. And so, "I have these coding skills, and I have this console that doesn't have an emulator for it, how can I put the two together to not only create something," because at the end of the day, for me, at least, I find it very hard to work on something that's not going to produce something at the end that's useful to someone. And so I think having the emulator sort of as an outlet to be like, "let's work towards emulating this." It just so happens that a side effect of that is it's a commercial emulator that can that can emulate commercial games. But even if it couldn't, I think we would still be working on it, I think we would still be working towards this emulator being a great replica of the actual physical console just because it interests us. And it continues to challenge us in ways that we don't necessarily get from building ASP .NET websites on our on our day jobs.

### Jamie

Yeah, there's an argument for sort of stretching out and figuring out other things, right.

A lot of the developers I speak to on a daily basis, either through the podcast or just through, like, speaking to people on slack and Twitter and stuff. There's a lot of sort of creative energy in development. Now everyone is full of creative energy, some people are just like, "Hey, I'm going to do my nine to five, I'm going to go home and be me outside of work." And that's totally fine, too. Whichever, if you're super creative outside of work, if you're not creative outside of work, if you are somewhere in between, it's "you be you," right. But I've seen that there's a lot of creative outpouring from developers outside of their day to day work. Whereas like, you know, one of my friends, Joe, he was doing some live streaming of some Python stuff. And I love to watch other people beacuse I'm like, "I want to learn how you're doing it." And I'm sat there going, "hey, could you do this way? Could you fix that?" And it's like, being that sort of cohesive workforce. And he was building a game. And I was like, "Oh, this is amazing. I've got to tune into this," because it sort of lights up that part of my brain that wants to be creative. I'm not terribly musical, but I try. Right. And I know a lot of developers who are musical, and but like, the point I'm getting... the point I'm trying and failing to get at is that outside of work, we all need that - if you have that creative flow, as I guess we all need that. output. That way to get that out of your system, because like what you're doing is you're solving a problem, right? "We got a bunch of these chips arranged on some PCBs that we can't read, but we want to recreate it in the computer. Can we do that with something that," like I said earlier on, "that in 2002, 'you're never going to get system performance that you would out of C'". Well Guess what? There's this I've literally got my Switch here. I mean, no one can see the video, but I literally got my Switch here. Just off screen. Off camera. "Can I make that run on my computer? And why not?" Right.

### JD

Yeah. I mean, I was lucky enough to find the project happened to be in C sharp. I remember there's actually another Nintendo Switch emulator out there that's called usually that's written in C and c++. And that was the emulator that I initially stumbled upon because I was I was curious about this. console. And then to discover that there was no writings written in C sharp, this language that I'd been spending the last 12 years of my life indulged in, was just amazing to me that like, the fact that even back then, like when I was running, basically no commercial games, the fact that someone was even attempting it, and someone who had similar aspirations to me, and who's willing to try these sorts of ridiculous things, really attracted me to the project.

### Jamie

Yeah, and, like you say, being able to use the knowledge that you're gaining and practising on a daily basis. And sort of applying that or indeed, doing it the other way around here, I've got this personal project I work on in the evenings, we've just figured out how to use this particular feature. Because I mean, we were saying just off air, right? That the list of C sharp nine slash dotnet, five features is huge. And you know, a lot of a lot of the developers I speak to been saying to me, well, where am I going to use this? Where am I going to use that? And it's a case of, don't look for how you're going to use it, use it if you need to, you're not you're not duty bound? To use records or to use? What's that thing with the switch statements where you can just like inlining is pattern matching. They'll say, yeah, pattern matching and stuff like that. You don't have to do that. It's there if you need it. But then I guess if you if you or someone else on the Regenexx team have gone, hey, you know, we've used async ienumerable. Just check it out. And then you can see a real world application of that and go, actually, I could use this tomorrow when I'm at work, use this in this situation, right? It's like, because obviously, the documentation can only cover like, here is the rationale behind we, why we built it. And here's like, a trivial example is, you know, some data coming in, and here, here we are for reaching over it and yielding that, and hey, go go do it. But unless you can actually see a real world application of it, which, you know, I'm not trying to say the Regenexx uses. I, I, I think enumerable or anything like that. But, you know, being able to see those real world applications is so much better than just reading the documentation.

### JD

Yeah, I mean, we've been in the unique position where we've reported things like, hey, Microsoft, we need a way to do this. Or we've discovered a performance issue just we were talking OFF AIR about one of the issues is that the suppress in it locals, which sounds very technical, but basically, when you enter a function, the dotnet runtime will zero out basically the entire stack for the variables that are allocated or declared inside that function. But when you already know, you're going to write to all of them, or you're not going to read from all of them, then spending all the time to emit the code and execute the code to zero it all over, is pointless. And this has become more and more of a sort of a point of optimization, especially now that we have spans and that we can do a lot of sort of very verbose, memory heavy operations in C sharp safely, that we never used to be able to do before. So it wasn't really an issue. But we have discovered in lots of places where the JIT is just a meeting code that's wasting time to zero all this, this memory in a function that might be called a million times every second will, or 1000 times every frame. And we know that we don't need that code. And so we asked Microsoft for a way to solve this problem. And they gave us our suppress in locals as an attribute. And this is one of the rare situations where rather than going to find a use case for a specific feature that they've added in C sharp eight or nine, it's one of the ones where we've been like, okay, Microsoft, when, when is this going out or which language features are going to be and we basically, we upgraded to dotnet, five, as soon as it became publicly available, just because we've been waiting for these features that Microsoft have said they fixed it six months ago, or they implemented this feature six months ago. And we've been able to put it in place with a practical application. Before we even knew that it was coming becoming available in C sharp nine. So yeah, we definitely when you start delving into the depths of hardware emulation in C sharp, you start really relying on all of those new features that a lot of people go, oh, mate, I hate records records is so silly. It's so verbose. Why can't you just write it with a little bit of extra code, but it's like, you can't, you don't have to use it. It's just there if you need it. And there's a lot of features that that we make use of now at a C sharp eight and C sharp nine that, um, a lot of other people go probably go, what's the point in that, but we make use of it. And it's one of the crucial parts and making the emulator not only functional, but performant.

### Jamie

We'll come back to those points as well. But I just thought about, you know, what we're what we're talking about here we are talking about a switch emulator. But the same could be said for any other commercial platform, or indeed for chip eight, would you believe is one of those fictional systems that doesn't exist. You can write an emulator for that people have already sort of they've, they've sort of, like, in theory proved that this could work as a real system. And they've just put the specifications out there for you. And people write real games for it. So it's like, yes, we're talking about the Nintendo Switch. But this could be a gap. Or it could be, oh, my goodness, what was the this something that Knuth wrote about, in his book, The Art of computer programming, he comes up with a completely virtual machine and talks through how the entire architecture works, because all of his examples are written in a programming language for this machine that doesn't exist. So that he didn't upset anyone for writing in C, or in Fortran, or whatever. Like, he invented an entire programming language, and an entire fake computer to run it to be able to write all of his examples for and he actually, I don't think he does it now. But he used to offer bounties for if you find a bug in my implementation. Yeah, so like, you know, the, what I'm trying to get at is the scope here is for creating emulators for practically anything, you know, real system, a fake system, pretend system like Donald Knuth, champagne, whatever, right? And they're all sort of fits.

### JD

Yeah, yeah. The technologies that we use and sort of the fundamental ways that you approach emulating a hardware platform, or even a virtual hardware platform that doesn't exist, they're all very similar. And you're going to be solving the same problems. And it's nice to see Microsoft embracing some of the things that we've had. And it's nice to see C sharp and the dotnet core runtime evolving in a way that further continuously enables people to build more of these exotic solutions to problems.

### Jamie

Sure. So you said earlier on, right, the the, the the entire time that this project has been alive that you've known about. It's been built in dotnet, or specifically dotnet. Core right. Now, I want to ask a question, and I don't want it to come across as in as sort of like false like, hey, what the heck, like, Why? I mean, other than, can it be done, right? Because I remember, at one of my previous employment gigs, they were like, yeah, we're moving everything from dotnet framework and dotnet. Core, I just stuck my hand up and went, why, why it's all working, right, you get but then in this instance, if there's already one in c++, and C, D, technically, you may not have been able to contribute as much as you have for this one. But like, why dotnet? Is it just because it's now cross platform? Is it was? Is there an answer to this? Do you know? I mean, obviously, you know, hopefully, you've had a chat with the team for answering this question.

### JD

Um, so the founder of the project, if you will, GDK Chen, I spoke to him about this, and very much the reason and behind this is that he had had experience with C sharp and dotnet, before he was comfortable writing the code, he was experienced, and he was fluent in it. And so not only does it prove a challenge that this has never been done before in C sharp, but also he can reuse a lot of his knowledge that he already has, rather than trying to attempt it in a different language that he may not be as fluent with. So I think there wasn't any sort of underlying ulterior motive to use dotnet. It's sort of just been like, Well, I know, C sharp, I know dotnet. Let's see if this is even possible. And at the time, I believe the other Nintendo Switch emulator yuzu, wasn't publicly not wasn't public knowledge that they were working on that. So very much. So writings, I believe, was the first sort of switch emulator on the market, and then usually came along later. So in terms of sort of like contributing to an existing project, and I'm always of the belief that competition, if you will, is healthy. Both teams have an amazing development team behind each one. And we both thrive off of the discoveries and the learnings of each other. A lot of the code that uses implemented has been fond discoveries of bugs that we've discovered on our when they just happen to have the same bug. And we both fix it and vice versa. Some of their team members like Rodrigo, who's their sort of their lead GPU developer over there, is constantly working with our team pointing out sort of issues and stuff like that, that he's found in his code that we also have. And so I think there's a benefit to having more than one emulator as well, that's sort of touched on that point. We've definitely seen a benefit of having to and it always keeps you motivated when the other guy's booting a game that you're not burning or you're booting again, that they're not booting. And it's sort of like are now Now we need to get that game booting. Or they've got some feature that we don't have. It's it's always fun and exciting, and it keeps everything motivated. But yeah, to come back to the the point, I don't think there was a really underlying reason to pick dotnet apart from that was what JDK 10 was comfortable with and all of our teens, team members were comfortable with.

### Jamie

Cool, I mean, that makes perfect sense, right? You pick the tool that you're most productive in. There's there's a constant argument of which tool will make me the most productive and I'm like, Well, if you Really good at using Notepad. For Notepad, if you're really good at using Microsoft Word, then Microsoft Word, if you're really good at using notion or G drive or whatever, it's whatever it is that you're really productive with, like, technically, you can use a screwdriver to put a nail into a wall. But you're never going to be as productive as using a hammer, to put a nail into a wall. You know, if you're using the screwdriver, there's an argument, therefore, you can, but this is the best way, the most accepted way the the way that you are going to be better. So I'm always for when when somebody comes to me and says, Hey, we want you to build this project. And we want you to use these technologies. First thing I always ask is, why those specific technologies, right? Because it could be that you want dotnet because dotnet is one of the new hotness is right now. Or you might decide, hey, we want, you might say, yeah, we want to build it in dotnet. But we want to do loads of really low level machine learning stuff. And we'll stop that does have the machine learning libraries might be the pythons better, or it might be that our is better depends on the type of data you're working with. It's always

### JD

the right tool for the job sort of thing. Yeah. Yeah. And I think dotnet one of my gripes with over the years is that people have this preconception that dotnet isn't, you can't use it for these serious sort of workloads. And one of my goals with working on this project is to sort of show that you can dotnet Yes, it has overhead. And but over the last two years since dotnet, core has been around, the overhead is continuously shrinking. And the benefit that we have with working on dotnet is that not only do we reap the benefits of our continuous improvement on our code, but every single time we bump the dotnet core version up, we get the hundreds of 1000s of hours that marks of developers have invested in the dotnet core runtime that we can read. Just recently, the dotnet, five upgrade, there's a whole bunch of there's a performance they've they put out like a performance improvement document that sort of details, the differences between dotnet, core 3.1 and dotnet, five. And a lot of the points in there are specific things that we have noticed as being sort of performance hotspots in our code, and the improvements just from upgrading from 3.1 to 5.0, in some instances, like a 10 2030 100 times performance improvement, and some of the things and that's a benefit that we get zero cost fast, we just change a version variable in our build script. And boom, now we're building on dotnet, five, and we've just gained all this additional performance. And so I think there's a real good reason to build something like this in dotnet versus say C or c++ and other stuff like this, where there's almost two teams working on writings right now there's the Microsoft team building the dotnet core runtime, and there's us, you're optimising our application on top of that. And I think that's a really unique situation that not many other languages can sort of all platforms can sort of claim to have. You've got Java and stuff like that, which are a lot more mature and sort of foot in the market. But dotnet core is moving at very rapid pace at the moment, and the performance improvements that we've already seen in the dotnet, six, sort of bave. They're not even beta builds, but whatever the nightly releases, there's already great features that they're working on, and bringing up and I think that's really exciting when you're working on a project and you can sort of just overnight win additional performance by upgrading your platform. And

### Jamie

yeah, and that feels like it's like you say it's a mutually beneficial, not just between you, you folks working on rejects and Microsoft, but obviously, for everyone else, right? Every time you push out a build, regardless of whether there's telemetry involved or not, you get a bunch of information as to whether this is actually better or worse. And then you can take that to Microsoft and go, hey, we've got a user base, who are doing things that are performance related. It is important, it is imperative that we get the best performance we can out of our code. And so we're we're optimising it. But also we've noticed, like you said, we've noticed, hey, there's all this code that's being executed that isn't actually useful in our use case. So can is there like you said with the the zeroing out stuff, when you come into a function, it's like, well, can we disable that? Oh, yeah, sure, you can do brilliant. And then anyone else who uses that gets the benefit of that, like if I decided, Hey, I'm gonna write some software that needs to do the exact same thing. Like, I don't need to zero out my variables going into a function, because I'm going to be using them straight away. And I require them to be set to garbage values, and I'm going to reset them anyway. Well, I can use that myself. I don't have to be writing an emulator. I don't have to be trying to emulate a system real or not. To be able to actually do that. I may need to do that in some of my services, my business line app services, I may need to do that. Before I can touch My domain models, you know, there's everyone gets that benefit.

### JD

And that's exactly right. And one of the things that I've found myself doing in my day to day job now is that I learned about these sort of performance things. And there is very much premature optimization. But when you're aware of how the underlying how the JIT works, and how the dotnet core runtime works, and how it thinks internally, it creates a different way from byte code, when you're writing code, and you're understanding how it's being executed. Something just clicks in your head and you start writing code, that may not be how you would typically write code, but you write code in a way that you know is going to be well executed or, or well optimised, or II know, these little tricks that we'd never reviewed, like, I would never have researched, zero, skip zero in it, the locals for something that I was doing at work. But now I can see all these potential use cases, and just even going back over and reviewing code that I've written for work, where I can apply that and be like, Oh, man, there's an instant 5% performance win on that. Because I've been contributing to this open source project. I think, like you're saying, having a practical application for some of these features that where you can point to and go like, this is where it's useful. This is where you can use it is great. And I love to think that some of these C sharp developers that we see coming through our development channels and being wanting to get involved, are able to sort of see these things and take them away back to their jobs and grow the collective knowledge about these features and how they can use them in the day to day jobs, not just in some super niche market where you're building a Nintendo Switch emulator.

### Jamie

Yeah, it all makes sense. And it's all about that. Continuous professional development. That's the sort of the buzz word project manager type wave and management way of thinking about it. But yeah, just sort of looking around, you know, back when, when I was coming out of uni, I was asking people, hey, how do I get better as a programmer, and they went, go read source code, and I was like, really, really cannot just like, take a course, read a book, or, you know, whatever. They're like, No, no, go read source code, and it still sits, Well, today. Yeah, go read and write source code, and you will get better at it. And like you say, you know, the, the implementing these feature using these, sort of using these framework features, the time I try not to use the word framework, and I'm talking about dotnet. Because dotnet framework is a thing, right? But using the platform, features, in some kind of outside of work, I'm playing around with something to see what I can build will always like you said, they're always in first with you, Hey, I can use this in in real life, I can go and go back to my my clients, my work and my customers, my whoever, right? I'd say, right, I can actually make this code better by changing one line, right? Or maybe you don't even tell them and then they just go, hey, we've noticed somehow that we're getting 5 million extra requests going through the system. What have you done if you made it better? what was happened if you just dialled it up and vertical, vertically, horizontally, whichever way scaled? Have you done that? And you just go? No, I'm just that good of a developer.

### JD

That's exactly or you take some credit for yourself?

### Jamie

Exactly. But like you say, it's part of it. Excuse me, part of it is having that knowledge and that experience, if you if you I keep coming back to async, enumerable? Because I'm still trying to figure out how to use it in real life, right? Yeah, but zero in it, right? If you don't know that exists, like, how are you going to document that if you're Microsoft? And you're trying to document that for everyone to use? How are you going to document that? Suppose you have a method where you want to not zero everything out on the way in? Like, you can't, I can't think of a way that you could document that in a generic enough way. So that anyone reading it can go Oh, yeah, I'll just throw that out. Without obviously mentioning the pitfalls of but if you're not, if you do require everything to be zeroed out, don't have it like that. The only way to learn that is to experience it.

### JD

Yeah. Yeah. And I like to think that from my experience and learning in this, I'm able to sort of instil that in my colleagues as well be like, Hey, I saw you wrote that code the other day, you know, you can actually do it this way now with this new feature. And now they take that away, and they teach their colleagues about the feature, and we will collectively improve the code that we're writing thanks to them, just things that I've learned in my free time contributing to raging.

### Jamie

Hmm, excellent. I agree completely. So we talked about why dotnet and we've touched on a couple of the C sharp nine and dotnet features that are that you're using, that you have a real world application for. If you have any others do do please shout out. Or I was wondering because we talked about the performance as well but other any other unexpected features that you knew or unexpected advantages or benefits or even disadvantages of using dotnet to try and build up Regenexx as as Is there anything where that you know of where you or someone on the dev team have gone? Actually? That's really cool. It did that for me automatically. I don't have to have to worry about that. Right.

### JD

Yeah, I mean, I think one of the biggest highlights for this one is sort of the initial approach that was used for building the emulator. And one of the unique approaches to it was, so obviously, in a Nintendo Switch emulator, you need to emulate the CPU and the GPU and the CPU. And a Nintendo Switch in this instance, is an arm based CPU. And so we can't natively execute that on your x86 CPU in your desktop computer, because they're just not same architecture. This is the same problem Apple actually has right now within you m one based Macintosh computers is that they can't just natively execute all their existing applications, because it's not the same architecture. So they've actually built basically the same thing, we have just the other way around next 86 to arm conversion. And our initial approach to this was actually something that I'm not aware anyone's really done before is that rather than converting the arm code directly to x86 and then executing it, what we did was we converted it from arm code to MSI l or the Microsoft or CIO, I believe is what the name is these days. So we actually converted it to C, sharps, intermediate language or dotnet intermediate language, which then allowed us to utilise dotnet JIT to actually do the code yet for us. So we didn't have to build an assembler and cogeneration or all that stuff, all we did was we use reflection emit, we taken an opcode, we emit some Microsoft intermediate language set handed off to a compiler, and then let Mark soft and JIT do all the work or ryou JIT in this instance, which is actually with the name ratings control. And so that was a really novel approach that allowed us to very quickly prototype the entire emulator because we didn't have to worry about building this big complex JIT compiler, all this sort of stuff, Microsoft already had it for us. And it had the unique sort of benefits that well, any target that marks up adds to dotnet core, whether it be arm, MIPS, c, x86, whatever, that's all their work, we can just our code re targetable. Now, because we can use a cross platform completely, we don't have to rewrite our code. And this is really, really cool. And for the first year of writings being around the first commercial game boots, this is how we ran our CPU code, we converted it to MSI l or ci L and compile that through Microsoft's dotnet runtime compiler. And that was sort of an unexpected, but really cool benefit of having dotnet, you have this runtime JIT that a lot of other people don't, you want IoT you want ahead of time compilation, you don't wanna have to mess with a JIT and garbage collection, all this stuff, or is in this instance, actually helped us rapidly prototype the emulator into what it could be. Now, eventually, we ended up ditching that approach. And we now do native code generation because multiple reasons, the dotnet, it's not designed to be incredibly fast. For for co compilation, so we do, if you can imagine a standard application might have a million functions in it. And your binary compiling all of those at Dane boot takes an incredibly long time, especially in the dotnet. It's getting better over time. But there were just a lot of inherent limitations and performance gains, that when you don't have your own jet, all of a sudden, you're reliant on Microsoft to improve these issues. And our use case not necessarily aligns with everyone else's use case. And so getting a lot of these performance things tweaked for us, and pretty much US alone, because as far as I'm aware, no one else is doing this was going to be next to impossible. And so we eventually, I mean, the code still available, if anyone wants to go check out our Git repository, it's all up there. It works. It's pretty cool. But we ended up ditching that idea, but that, to me was really cool. I think that was one of the sort of unexpected HSA advantages of using dotnet. It also has a whole bunch of other benefits is that because we're effectively generating C sharp code, we're able to natively interrupt with everything else, all of our other C sharp code just sort of works. We don't have to worry about marshalling to native code and back again, the performance stuff that that incurs. So we were able to get basically a data Jail Free card really, for the first year of development. But by using this helped us rapidly, sort of develop the emulator.

### Sponsor Message

#### Russel

Rolling. Action in three, two, one

[bleep]

[phone vibration and ringtone]

#### Jay

No one calls me these days. Oh hey, what-ho Squidge.

#### Squidge

[distorted through a phone line]

Have you finished that big new feature for the website yet?

#### Jay

Absolutely.

[tpying sounds]

#### Squidge

[distorted through a phone line]

Hang on.

Ah, that's not bad, It loads pretty quickly. It has every episode on it as well.

#### Jay

Thanks

#### Squidge

[distorted through a phone line]

What's this button all about?

#### Jay

Don't push that button.

#### Squidge

[distorted through a phone line]

That aint gonna happen

#### Jay

[yelling]

NOOOOOO!

#### Squidge

[distorted through a phone line]

Nothing happened.

#### Jay

That's what _you_ think.

Waffling Taylors is a podcast all about video games and nonsense. Check us out on Apple podcasts, Google podcasts - wherever you find your podcasts - or head over to [Waffling Taylors dot Rocks](https://wafflingtaylors.rocks/).

So if you want to hear more from my brother (who may or may not be a cartoon wolf) and myself about video games and silliness, head over to [Waffling Taylors dot Rocks](https://wafflingtaylors.rocks/); or look for us wherever you listen to audio.

#### Squidge

And don’t forget that we have tonnes of guests and that we’ve covered over 1,300 games in our show so far.

#### Jay

And we have 110 episodes to choose from, too

#### Squidge

[Waffling Taylors dot Rocks](https://wafflingtaylors.rocks/)

[bleep]

#### Russell

Cut. Print

#### Jay

Was that OK Russel?

#### Russell

It was sufficient. Editing now.

[radio sounds, industrial sounds, bleeps and bloops]

---

### Jamie

I have to say that is quite possibly the smartest solution to any problem I have ever heard. Like, it already has a jet and he will already compile down to native code. So why don't we just use that instead? what's already available? That is quite possibly the smartest answer I've ever heard. Like, that is a proper engineering technique that's like, hey, why write our own for the first version? Let's just get everything working first. That is absolute and I don't use this term very often, but that is genius. I love that

### JD

it works awesome. This works surprisingly well, when you when you say I'm converting a native code execution from arm to Microsoft intermediate language, and I'm going to execute it in dotnet. State, you know how this is gonna turn out? But yeah, I mean, it just goes to show the performance improvements that that dotnet has made over the years, the dotnet framework would have been basically impossible on their own object prior to the dotnet. Core, it wouldn't have even attempted it. But big kudos to Microsoft, if you're listening to this, the team and the work that you've put into the dotnet core jet is absolutely amazing. And it's definitely made, basically the simulator possible.

### Jamie

I just, I'm genuinely blown away by that solution. Because like you say, it may have been temporary, and there may be better ways to do it. But again, like you see it, then theoretically, you could take this code and run it on any CPU architecture, he may not run performance, but it would run, right? If somebody invents a new CPU architectures tomorrow, and then Microsoft, alter their JIT compiler to target that, then you just go right build run,

### JD

don't exactly why I mean, we're already looking at this for us to target the new Macs that Apple have just bought out, we're now going to have to introduce an arm back end for our budget, which is already underway, we're already looking into it, not necessarily just to target Mac, but also it would be required for like an Android toggle and stuff like this. But Microsoft also working to bring up their own base get support for dotnet, six on Apple's new one, Max. And so if we had still been using that approach, we would be benefiting from all of that development, basically, Microsoft paying developers to work for us. It's it's very, very, very cool.

### Jamie

I agree. Where is that? That's, that's awesome. Because that, that that technique, like, like I said, Everyone, like you hinted at, it may not be performance. But But I was open the doors for? Well, guess what, I'm going to read an emulator for AIX, and it may not be a real machine. It may be a fake machine. But it runs a completely separate CPU architecture. And I will just use the jet to do the hard work for me. That's just, that's like you've got a free translator. Yeah. Why not?

### JD

And I think if you were targeting anything outside of the Nintendo Switch, which is a fairly beefy CPU, like your quad core, two gigahertz ARM CPU cores, if you're I say emulating an indo DS or like an snares or an NAS system, I think it will be entirely feasible to use that approach to emulate their CPUs, protect, perhaps even emulate their GPUs, using just a reflection of mitten running Microsoft intermediate language through their JIT and executing, I think that would be completely feasible. And definitely something off. All my books says, the long list of things that are the core things that you want to try, that gets it perpetually longer and never decreases in size. It's definitely out there. And I think a lot of other projects could definitely if you're out there, and you're looking at writing a Nintendo DS emulator, or even a chip eight emulator, as you say, it's definitely something that not many people probably have gone have put two and two together, but it's it's possible, we've proven that it is. And if you want to look at how we did it, go check out our Git repository on GitHub. That's Wow.

### Jamie

That is amazing. Wow, I'm genuinely blown away by that. So the biggest, one of the biggest things that stops people from writing things with dotnet core or dotnet, five, slash six, slash seven, at the moment, is sort of cross plat. The user interface stuff, there's lots of work happening, there's like there's an electron dotnet, which I would personally I wouldn't use because it relies opening a port to the world. But I mean, that was an early version of it. There's Steve Sanderson is working on like web UI kit inside of dotnet. There's Maui, which is coming out. Or rather, I think I should say marry dotnet. Because Maui already existed. There's some controversial,

### JD

it's very complicated.

### Jamie

There's like Xamarin, all these all kinds of things that are almost like for all first ish party solutions. But I know that you all went with GTK sharp. Now, I wasn't aware. Or at least when when we were reading this Converse, I don't know whether it's changed the senses. But I wasn't aware that GTK sharp handled, like could could could work with dotnet core. So that's really quite useful. I don't I don't know whether that's still the same thing there. But like, was there a decision that went into that other than just like, Hey, we need a window manager. And we need to be able to make a GUI because an emulator without a GUI. It's kind of useless.

### JD

I'm pretty sure I'd like this is a big, contentious thing for us at the moment. GDK sharp for all the It's great things, there's a lot of negative things for us as well. A lot of the things that we try to do not try to wring out of it is makes life difficult for us at the moment. So. But yeah, GTK sharp. I mean, I guess it's, as you say, we needed a window manager, we needed something that was cross platform inherently. And this is probably the biggest place that dotnet core and the dotnet core ecosystem and the cross platform this can improve or needs to improve really is this, there is no universal cross platform user interface, you've got the likes of avalonia, which is sort of trying to, to branch all these things together, we're using zamel, and other stuff like that. But there really isn't a solution at the moment apart from sort of binding to these other native libraries. And I guess GDK sharp was the lesser of evils, if I put it that way. So I guess someone on our team was fluent with GTK that built a GTK application before and so they sort of just went and built it. And that's what we're stuck with today. We're definitely looking to migrate away from GDK sharp, so I'm not necessarily endorsing, going for that. It's great for simple applications. But for us where we need low level access to stuff, it can become a bit of a pain point. But um, no, we just, it was available. And yeah, like you said, GDK sharp, I think it targets dotnet standard. So it's sort of dotnet framework, dotnet core, mano, sort of all that intermingling stuff that no longer exists, apparently. But yeah, so we start with that it's worked fine for us for the last year. And yeah, if anyone else is looking for cross platform, there's, you've got plenty of options, just none very mature.

### Jamie

I mean, that makes sense, right? It goes back to that conversation we had about productivity, right? If someone on the team is really productive with a GTK shop, and they want to build the GUI is old stuff, go do the thing. Totally. Right. If you're going to be able to build it in a couple of weeks, couple of months, couple of days, I don't know how long it took the team to build the GUI and be able to actually draw on screen but and that's that's greatly reducing the actual task. But if, if it takes a certain amount of time, and someone says I could do it a little bit quicker, if we change to this library for this version, you get it up and running, and then like, maybe build that around an interface or something, segregate that out, and then you can just swap it out, right? Yeah, why not.

### JD

And I'm very much of the belief that build something for this day. The great thing about code is that nothing is set in stone, if we decide to go down GDK sharp as we have, and we decide that, hey, it doesn't exactly work that great for our specific use case, then we can just go and swap it out for something in the future, when we when we have the needle that the want to do that. And I feel like a lot of developers get stuck in this cycle of, I need the perfect solution, right up front, I have to think about it for months, come up, architect it carefully build it, document all my code, right from the very start to have the perfect solution at the end, but he never gonna have the perfect solution. At the end, you're always gonna want more. And I think just getting in there building an HSA minimum viable product, getting something out there that wasn't gooey, we needed one, we didn't have one at start, we literally just rendered the game on screen, there was no menu bar, there was no games list or anything like this. And it was a barrier to entry for users of the emulator. And so we sort of just thought, how's the quickest way we can slap one of these things together, it doesn't have to be the best, it doesn't have to be the final solution. But we just need something. And that's where GDK sharp popped up out of and it's worked, it's worked pretty fine until we've started to push the limits.

### Jamie

Yeah, I think that's the point. Regardless of what people take away from any kind of learning that they do, in software development, software, engineering, computer programming, whatever you want to call, the industry that we work in, is bells and whistles last getting working first, because you don't know whether one of the things I always say to junior developers, when I work with them is the one thing you will learn and you should learn it very quickly is that the person you're building the software for doesn't know what they want, until you give them what they don't want. And you can extrapolate from that and say that, you know, we don't know what we want for the user interface for Region X, or for this service we're building or for Netflix or for whatever you're building, right? We don't know what the user interface is going to look like. But we need to get something in front of the user so they can use it and tell us right, what you've produced is great. But can this button be over here? Because the majority of the times I build software, I'm not the greatest user interface designer ever. But I'll throw something together like just slapdash like push this button and it will give you bacon or push this button and it will do the thing. They push this button for the TPS reports right? Because because it doesn't matter to me how that looks as long as you can discover the button and use the feature because on building a feature, I'm not necessarily building the interface. And like you said there, right, you needed an interface GDK shop may or may not be the best for this particular application, but it fit within that time period, get it working, get it out to people, because for all, you know, it may have may be that the code was running fantastically on your machine, because you may have a development machine with, like you say, a 15 gigahertz CPU with 48 cores, and 12, gajillion bytes of RAM or whatever, right. And it works brilliantly on your dev machine. But it's a you get into the hands of the actual users, you don't know whether what you've produced is actually useful, right?

### JD

And that's, that's exactly why we, when we started down the path of GDK, sharp, we didn't know what we knew today. And we kind of known until we attempted to do it. And so it's, it's coming back to premature premature optimization, but not just in your code. But in your approach in your architecture. You can optimise for things that you don't know about yet. And just getting in getting nitty gritty building, it doesn't have to be pretty it can all just be coding one giant class for all I care all shoved into one function. But so long as you have something working, there's always the ability to refactor to update to fix code later. You can spend, I struggle with this, as a developer, I can spend endless time thinking about things and researching and documenting and stuff like that to the point where I'll never write any code. It's just getting in there and getting started that that's 90% of the hurdle.

### Jamie

Yeah, I agree completely. Because, and like liquid sort of hinted at earlier on if you if you segregate if you separate the concerns of your obligation, regardless of whether it's an emulator or a game, a a microservices architecture, a monolithic, huge web app, whatever it is, as long as you segregate everything out, and leave those I've just finished reading clean, agile, and clean architecture by Uncle Bob. I'll leave the discretion whether I agree with his politics or not on one side, but like the points he raises in those books, I like leave the technical decisions to the last possible minute, because you don't want to build your app. So the wrong lies on those external libraries. Right. We eugenics may or may not, I don't know, we haven't had a chance to read the code properly. But it may not rely on GTK shop. And if it wrong, if it doesn't rely on that being there, just something that can accept some input and produces something on screen, then technically, you can, like you say you can swap it out for avalonia. You can swap it out for Vulcan, you can swap it out for OpenGL, heck, you can even I mean, you wouldn't be cross platform, but you could swap it out for DirectX x, you know, you could, you may end up going down a route where the system detects if windows then use direct x because Direct X is written for Windows, you know, he may go down the route of Oh, we're on. I can never remember the one that Mac OS uses. But they've got their own have they it's kind of like Vulcan, but it's got like metal or something. Yeah, yeah. Right. So you could detect, hey, if Mac OS metal, you know, and, and you just say I have an interface called a window, and I have the metal implementation, I have the GTK implementation, I have duratex implementation, as long as you leave those decisions to the last and second or segregated correctly separate those concerns out. It doesn't matter what user interface you use. And same with like database technologies, right? A lot of people don't know how it's going to be EF core. Okay, fair enough. But what about if you're to use debonair, or dapper, or any of these hundreds of other database technologies leave that decision to the last possible second? Yeah, and then build an interface. And it totally makes sense. And, and that's, that's something that you can apply. Like I said, game, emulator, business line application, whatever.

### JD

Yeah. And that's one of my goals, for writings in the end is to become is to treat it like a library, where anyone can sort of add it from you get added to your thing, and then build whatever user interface you want. On top of it. writings as a library, we bring the CPU emulator and the GPU emulator, but how you put that on the screen is completely up to you. I think that leads very well into sort of the architecture of abstracting everything away, not relying on specific technology. And we're not there yet. But it's definitely something that we're we're we're working actively working towards putting in place things like dependency injection and stuff like that. People might laugh at me thinking of adding dependency injection to something performance critical, like a game emulator, but I think it's possible. Now, I definitely want to try it, and see if we can do it. And if we can't, well, then we've learned that we can't do it.

### Jamie

Yeah, absolutely. Because then you know, like you say, You're not, you know, you've already sort of gone down that route of optimising before for performance. So we've got a performing quite well, can we use dependency injection to swap a core component now, at runtime, and does that affect it? And like you say, if you do that, and it turns out that it does affect performance, you just go well undo

### JD

Yeah, cancel this pull request.

### Jamie

Exactly right, you're not, you're not committing yourself to it has to be this way, you have those options. And that I think is what real software engineering is all about is like, I have the option to swap this out, whether I decide to or not, it doesn't matter, it means that six months time, when we decided that this particular technology that we were using, it doesn't fit our use case anymore. And that's the important thing to say it doesn't fit your use case any more. It did fit previously. And some other technology may fit a little better, or he may fit completely, and is having that option to be able to swap things out and change things around, I think is the most important thing. Like I say, regardless whether the game and emulator, a business line application, whatever it is being able to swap things out, is I think the most important thing. Yeah, definitely. So let's let's talk about the name just real quick, right? Because there was a really, really interesting tidbit that you dropped off there that we think is really great, interesting. So I know that you'd said earlier on Regenexx, the part of the name comes from the fact that you that they review JIT compiler exists, right. So just for better background, the rejet is the for those that don't know is that just in time compiler, that C sharp, F sharp, those kinds of things can use to just in time, convert your, your C sharp ml, your intermediate language code. So let's take a step backwards, you write some C sharp code, you hit compile, out pops a DLL, which is compiled to the intermediate language, which is like the step in between native code and your code. And then when you run it, the jet compiler comes in and says, write this intermediate language convert that to the the operational codes for the CPU I am running on. At least that's my understanding of it. Yes, likely, I'm greatly reducing

### JD

the overhead of them. I'm sure what that happens.

### Jamie

Yeah. And I happen to know that rejet, the name of the Microsoft JIT compiler that's used by dotnet is named rejet. Because riou is Japanese for dragon. And there is a very famous book in the computer science arena, called the Red Dragon book, which is a book on compilers. And on the front guy is a knight to fighting a dragon. And so that's kind of where that comes from. But I'm interested to know, because you dropped this knowledge off, just real quick, where the name for region comes from.

### JD

Yeah, so the name regions, it comes from what region, which is a mythical seagull, or dragon, as you say, and the name stem, sort of from the use of ryou in the name Ryo jet, which is the codename for the dotnet core users. And then nx just so happens to be the code name, the internal code name Nintendo used for the Nintendo Switch. So all their game consoles, I don't know the internal code names for them all. But they all have an internal code name and the one for the switches and x. And so it sort of sounds cool when you put it all together Ryuji annex, nor Aging's as I call it. But that's where the name comes from that sort of the combination of ro jet and an extra Nintendo Switch. I think it's fitting given that the initial implementation of the emulator have been to so heavily lend on biojet itself to do all the CPU emulation, I think it's quite fitting, and it's quite it nice. It's cool name, but it also has fundamental meaning behind it. And I think that's pretty cool.

### Jamie

I'm interested to find out and you may not be able to answer this, it may be a question for GDK. What came first, the implementation, not the name, right? Because we all know the naming things is hard. Yeah, yeah.

### JD

I'm not sure. I'll have to ask.

### Jamie

Well, if you find out we could do like a follow up or also then but yeah, that's, that's a really interesting. just name it. Like I said, naming things is hard. And it's just this wonderful, sort of this, this cross pollination of the technology uses, and a whole bunch of stuff related to like, what Nintendo calls the Nintendo Switch, turn AI, and just bringing all of these things together, and like you say, you got a cool name out of it. That's what I can't do that with any of my projects that's

### JD

I'm perpetually actually stuck in the, "what do I call my project before I release it to the public?"

### Jamie

Okay. So you touched on the fact that RyuJinx and yuzu sort of have evolved together, there's that intertwining of the teams working together and like you said, you know, competition is really important to breed innovation, because if you aren't, if you aren't trying to catch up with the other, the other team, the other people, you sort of get, I feel you get kind of lazy and lacks and you go in at work kind of works. And it's a little janky and it runs it 24 frames a second

### JD

Well that's 24 frames per second than anyone else.

### Jamie

Exactly right. But then if no one else is doing it, you end up with Well, I'll do, it's fine. And you kind of stop innovating. But if you have that competition, right, then that sort of helps. But do you know of any other open source projects that you or any of the other folks at Ryuji genex have sort of used as inspiration. So for instance, I happen to know that I, at one point wanted to write a small operating system in dotnet, to see whether it was doable. And then, like a week after I decided I'm going to do this, Scott hanselman, pour in tiny arrested on a call. So I was like, Well, I don't need to do that now.

### JD

Yeah. This in terms of direct inspiration for the project. Not really. I mean, there's a lot of great emulators out there that we can draw, that we can draw sort of inspiration from our PCs three, which is a great open source, ps3 emulator, written in C, and it's quite an, they've even got a greater challenge than we do. Because the CPU in the ps3 is so arcane, and so not normal. It's a miracle that they're even able to have an emulator for that console. So that's a really great one to sort of, they have a lot of problems that they've sold over time before that will come along. I mean, the ps3 is like a 1012. I don't know how old console probably even longer than that, because the ps4 is probably that age. So 15 year old console now. So they've had a long time sort of sought out the same problems that we're trying to sort out. And so a few things like memory management tweak tricks that we can pull on Windows, ways that we can use specific instruction sets on Intel and AMD CPUs to recur eke out extra performance, we're able to sort of go into that because our PCs three is open source. There's also seen you which is another Nintendo emulator, that's for the Wii U. It's not open source, it's closed source, but it's probably like, if you're after a the sort of the best example of an emulator done right, in terms of performance and features and stuff like that seems one of the great ones, so is dolphin. But there's also a couple of other sort of C sharp emulators that are out there. Like there's c s, PSP emu, that's available, which is sort of like a PSP emulator written in C sharp. And there's also JP CSP, which is also a PSP emulator written in Java. So it's not exactly C sharp, but it's very much the sort of the same problem. Java is very similar language to C sharp, it's got the same sort of managed architecture, you sort of run into the same problems that you'd run into on C sharp and so they we didn't draw inspiration directly from those projects. But it's nice to know that there are other products out there who are sort of trying to tackle the same problems that we are, and that there are the teams who are trying the same things that we are. And I mean, if we get stuck on certain things, it's there's always those teams that we can reach out to and chat to, and we hope that they can draw inspiration from us as well that raging says are successful. I hope I can say emulator done in C sharp and dotnet. I hope it serves as an inspiration for these projects going forward that, yes, you can write a PSP emulator and C sharp, yes, you can write a ps3 emulator and C sharp, do whatever you want. Here's an example of one that we've been able to that one we've worked on. And this has worked out for us.

### Jamie

Sure. And I guess, like, like I've been sort of saying a lot. He feels like it's a great implementation of all of those software engineering principles that were told to us at work solid, that were told to, you know, what is essentially just solid, right? Do these things, right? And do them in this way, because you will achieve great success. And I feel like a lot of a lot of the things that that get built that are big applications end up trending away from those. And then they get to a point where I mean, there's so for for reference, we're recording this on seventh of January, right? And it's looking like it's going to go out in a maple time. So I can say this and not worry about I mean, look at cyberpunk, right. I have the feeling that they hadn't properly or weren't able to properly adopt things like continuous delivery and, you know, unit testing or integration tests or any kind of testing right. And so they had to just look, today's ship day shipping works. Exactly right. I've talked about this a couple times on one of the other shows that I do well waffly tailors, they just the the idea that you reduce scope or you reduce the or you extend the time and when you're in a Business Line application you, you have to make those difficult decisions. But when you're making something as a hobby, you can go, you know what the Murphy if it doesn't ship today doesn't matter if if we have to take out this feature because it doesn't work, because we can look at it later and ship it as another feature. But I also think that the practices that you and the rest of the team might be doing, would would help other developers. And like you say you're building something that is performance, critical in the open for, essentially for free. And that means that other developers, like myself can come along and read through the code and go, Oh, that's really cool. I really like what you've done there. Like you said earlier on, you know, take this code, put it through the jet, the dotnet jet, and get it exported, so they can run on my machine. That is a wonderful solution, or albia, maybe not performance, great, but a wonderful solution to an incredibly complex problem. And that solution provided for free by Microsoft.

### JD

Yet Yeah, I think this leads good into sort of the discussion around dotnet. And its performance, if you will, dotnet. And other CLR languages aren't really knowing much for, well, no one much for their performance. But it's always like, when you compare C sharp to C or c++, it's always like, oh, but C and c++ is better because it's lower level and it's faster. But I went into this same mindset. And I think it's proven to myself that Actually, no, that's not the case. I think that's one of the biggest surprise to me and myself is that to myself, and the rest of my team, sorry, is that it is possible to build these things. And no one we didn't know if it was possible, because no one's done it before. But we hope this sort of sets up other teams and other developers who might also be interested in C sharp and also interested in consoles, and emulators and stuff like that. No, you don't have to go away and learn another language to do this sort of stuff. No, you don't have to not be involved in these projects, because you don't have any experience in these languages. Try it if you know Python, I can lead you to write as Nintendo Switch emulated in Python. Hey, it may not be possible, but who knows? I didn't think it was possible to do in C sharp before I did this. I think that's a great lesson to take away even not only for myself, but for other people is that just try it. The worst case scenario is it doesn't work. No harm, no foul, really.

### Jamie

Exactly right. And if it's in good, and it doesn't work, you can either just ditch the repository, or you could leave it there and say, Hey, if anybody knows how to fix this, go ahead and try it, right? Because if it's open source, anyone could jump in and go, right, I see what you're trying to do. I think I have a solution. Here you go. Right. And you can learn from that even the most experienced developers like, I feel like you and I have the same number of years of experience. And I would never have known where to start to build an emulator for a new I mean, I haven't even built the emulator for an old system. Right? emulating an entire CPU architecture, regardless of whether it's a real commercial product, or something that isn't real, like the chip ate like the Donald Knuth machine, or like, like you say, the rpcs three, just like taking the ps3 CPU, which does not match anything else.

### JD

It doesn't even have any public documentation. So I no idea how they manage that. I mean, we're lucky, we're lucky that arm is a well known architecture, we can just pay, we can just go to arms website and download the technical reference manual, manual. And it's short, it's 10,000 pages long, but we can gather all the information that we need from that. But rpcs theory is built on a CPU architecture that basically has no public documentation. That's, that's genius to me. Like, I don't know how they did, I would, I wouldn't know how to approach that.

### Jamie

Yeah. But like you say, you don't know until you try, right? So until you try and look into how do I figure out how a CPU architecture that is closed? That doesn't have any public documentation? How do we figure that out? How do I work out how it works? Well, I mean, it could just be, you get a CPU, what do they call them the clumps in the CPU or read all of the pin outs? But then you need to find someone who ships one of those for the ps3 CPU, or maybe you just put a bunch of probes on there and just read what's happening. Or maybe you you go down the line, I'm not advocating this, but you go down the route of let's talk to someone at Sony or talk to someone who has fallen out with Sony, can you tell me a little bit about it? Or nobody knows, right? I'm not trying to advocate any of those steps, because I'm sure every single one of those is illegal in some way. You know, you don't know how to get to the solution of the problem. Until you try, right if somebody would have told like the very first time anyone fizz bows, right? The very first time anyone does fizz bows? They have no idea. I told my brother how to do fizzbuzz on paper. He was like, Oh, that's, that's really clever. Like, the the month because I told him modular operations, you know, they're divided check the remainder. We did it on paper, I then taught him how to do it in Python. I don't even know Python. I didn't know it was possible to do it in Python. I mean, it's the same operator. But there's the same, same setup. But like, until you try. You never know whether it's possible. Yeah.

### JD

Yeah, for sure. Yeah,

### Jamie

I think that's one of the cool things to take away. Hopefully, there's loads of stuff to take away from this composition. But the the one of the cool things to take away from this conversation is that until you try to work on a solution, there's no way of knowing whether over like how you get to the end of that solution, I think that's an important thing for developers to always be curious. And always be looking and trying to figure out how do I do this, right, because I, right up until the DevOps and microservices, I'm trying to go for all the buzzword Bingo. I don't know whether you can tell. But until DevOps, and microservices, microservices became huge in the early, I want to say the mid 2000s nobody ever would have thought of, of doing that, and how they would do it. And then, you know, microservices happened. And DevOps, like continuously delivering push completely out to live constantly, is something that some companies are happy with. And some companies are not. And and until we got to that, that part, we didn't know whether a company would be happy with it, there are parts of the Microsoft tool chain that they push to live, like several times a minute, because they want the latest code out there, there are parts that they don't, don't is one of those where they don't want to push out a brand new installer every time someone adds a new semi colon or something, because it might break, but they put out a nightly build for it right, so you can try it out. Netflix is is imminently famous, or we're always pushing to live to production. But they don't tell you is that it's about 10% of their business that they push to production, because they don't want the rest of it to break.

### JD

Yeah, I mean, Netflix is is an excellent example, I encourage any developer who is interested in this sort of stuff to go and read Netflix's tech blog, because it is absolutely amazing. The stuff that you can take away from what they're doing. But the Netflix architecture is really interesting with the way that they use microservices, and they continuously testing and stuff like that. And it's it's nice to be able to read the the examples of these people who solve these problems day in and day out. And that's what I hope writing says to the next guy, he's going to write a an emulator is that here's an example of what to do, may not be right may not be wrong. But here's an example. Here's what we've done, he is asked, documenting. And that's one of the great things about open source code. And I'm so glad that it is an open source project is that the entire evolution of the project is forever, hopefully, encased in the Git repository, you can go back to the very first comment that was ever made. And you can see why every piece of code was done. And hopefully, we've documented our pull requests well enough that you can understand the why we did that performance sensitive thing and why we sacrifice code readability in this area for extracting extra performance. And I guess our code is our documentation, it's our tech blog, sort of approach to the things is that you want a good example of how to do more. I'll try to be humble here. I'm not claiming it's good. But you want an example, at least of how to do this sort of thing. don't check out the code. Have a read through it, as you say that the easiest way to learn something, it's just my mind, the easiest way to read to learn something is just to read the code.

### Jamie

Yeah, I mean, you could, you could wrote maybe a 3000 Blog Post article on why we did this one function this way. Or you can read the God and run it and go, Oh, I get it. Now. Yeah, they've done it that way. Because it reduces CPU intensity or, you know, they've used the the no zeroing. I forgotten the name of the attribute now, but then the noziroh attribute, because in this method, it needs it to not be zeroed, because they're using the the, the variables and all that good stuff immediately, and those values will be overwritten that the the garbage values will be overwritten. So we don't need to waste time zero everything out before we hit that method. totally makes sense to me. And you can get that from reading the source code. You could get that from reading a four or five page article. We can just read the method and go, Oh, I get it now. Excellent. Okay, so where we talked a lot about eugenics, eugenics, real genomics, I'm trying to make up a whole bunch of different ways to pronounce it, just to really upset all of the developers not

### JD

just making I'm sure you've hit the nail on the head for how we all pronounce it. so far. So

### Jamie

excellent. As long as I've done it once that act, what I can do is I can copy paste that out and put it throughout the conversation. If you could do that for me as well. That'd be great. Excellent. But I'll do it with my pronunciation of it so that it would be like your accent with me saying, I'll refund right. That'd be interesting. Yeah. But yeah, so how, how do people find out about like, what, where's the best places to go? You've mentioned that it's on get you mentioned that, you know, you can go get the code and you can go download it, and you can go read through, but like, Where can I find these things? Do I just literally hit Google and attempt to spell it out how I've pronounced it like, what's the best places to go?

### JD

Yeah, so our website has links to pretty much all of our things. If you I'm not going to pretend to spell it out for you. But if you can, somehow managed to get to our website raging.org. You'll all have our developers hanging out on discord, we have a Discord server for the emulator, and we're all pretty much on there fairly actively. So if you're looking to get involved, you're looking to contribute, you're just looking to support us via Patreon or just by hanging out and using our emulator and spreading the word. Hit us up on Discord. We're all there. We're all friendly. We're more than happy to step new developers through who are interested in C sharp and dotnet. showing them how they can get involved. We have on our GitHub, it's linked from our website as well we have a bunch of issues tagged is good first issue. So if you're looking for an easy one to tackle to get your you get your to get into the project, really figure out how stuff works. Go check out that list. Um, and then yeah, contact, you can contact me JD, I'm in the discord. Or you can contact any of our developers who are on line with developer Roland will give you a hand.

### Jamie

Awesome. Okay, well, maybe we'll get more people submitting code or or even just finding it and using it and being able to say, hey, my weird system, which uses a CPU from 12 years ago, and 18 bajillion gigabytes of RAM and is held together with gaffa. tape and spit doesn't run this system. How do I make it run? And you can go go buy a new computer? Yeah,

### JD

that's pretty much the answer you get. There's only so much C sharp can do okay.

### Jamie

Yeah, absolutely. Absolutely. Even if you are still using the gym. Yeah. Excellent. Well, I mean, all it really remains to say is, thank you ever so much for being on the show. God, I really appreciate it, especially since like, it's really is it's early afternoon for me, which means it must be like two o'clock in the morning for you. Right?

### JD

Almost. It's getting there.

### Jamie

Oh, my goodness. Well, time zones are hard. And I want to thank you ever so much for taking the time. And I know we've we've tried to do this a few times. And it's kind of fallen over because of time zones. Because time zones are hard.

### JD

Yes, for sure. Definitely. I'm still not quite sure what time zone you're in. But we managed to make it work.

### Jamie

Well, yeah. I mean, I'm in the UK. So it's GMT, which I think is UTC. But I don't know, too many acronyms. Hey, it worked. Right. Excellent. Well, thank you ever so much JD for being on the show. And thanks to the entire team Regenexx. Because otherwise, this whole interview, this whole episode would never have happened. Because like I kind of approached? I think it was I think I reached out directly to GDK. Jenna, what? Can I please talk to someone on the podcast about this? And just like, obviously, a compensation happened? Yeah, we've gotten here now. So yeah, thank you ever so much.

### JD

No worries, I just have to add like this project is in no way mine off. I'm compared to the amount of code that GDK Chan and everyone else on our team has written for this. I'm a very small blob. So I just have to say, but massive kudos to everyone on our team who's and every contributor to this product, who's who's managed to make it what it is today. I'm just one of many. And I think what we've been able to pull together is pretty amazing. And I'm just glad to be part of the team. It's Yeah, it's it's an amazing team. I

### Jamie

have to say I have I have talked to a few people on the discord. And I was like, hey, can can you answer this? And straightaway, hey, look, go check this out, or go read this or, or check this code or this is how it works. Just amazing bunch of people from my point of view, and eminently approachable. It's absolutely wonderful. Really, yeah. So thanks for thanks for being with us, Jenny. And no worries. Yeah, we'll we'll hopefully, maybe be able be able to catch up again, when you've implemented the next version of whatever's happening.

### JD

We will move on, we've emulated the next console that Nintendo

### Jamie

say, all right, maybe in the dotnet six timeframe on this one, we can maybe come back and say hey, what were some of the best things about, you know, what have you What have you been able to adopt now? Because you hinted earlier on, so few things in dotnet, six, which are going to make things a little easier for you, but we'll leave that for another time, perhaps I don't know. For sure,

### JD

definitely. Excellent.

### Jamie

Well, thank you for so much. JD.

### JD

Thank you very much.

{{< paracentre "The above is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

### Wrapping Up

That was my interview with JD of the RyuJinx team. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/), and there will be a link directly to them in your podcatcher.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice - head over to [dotnetcore.show/subscribe](/subscribe) for ways to do that - and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [https://ryujinx.org/](https://ryujinx.org/)
- [RyuJinx on GitHub](https://github.com/Ryujinx/Ryujinx)
- [RyuJinx on Patreon](https://www.patreon.com/ryujinx)
- [RyuJinx on Twitter](https://twitter.com/RyujinxEmu) 
