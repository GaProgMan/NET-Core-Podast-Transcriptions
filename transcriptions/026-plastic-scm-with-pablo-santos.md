# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is episode 26: Plastic SCM with Pablo Santos. In this episode I interviewed Pablo Santos about the cross platform source control system Plastic SCM, how it has been written entirely in .NET, was created before git, and even has it's own distributions of Mono. 

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Pablo's Introduction

**Jamie**
Pablo, thank you ever so much for being on the show. I realise you're a very busy person and we can go into that a little bit if you like her later on, but I just want to say thank you ever so much for taking the time to have a chat with me today, because it's fantastic to be connected with you and I'm really eager to learn all about the stuff we're going to talk about and for the listeners to learn about it too.

**Pablo**
Actually thank you because it's great for me to have the opportunity to be on your show!

**Jamie**
Thank you ever so much. So I guess first off, for the people who may not know about you or the company that you work for all the products that you make, I was wondering, can you give us a bit of an introduction to again you and the company in the product and things.

**Pablo**
Absolutely, well my name is Pablo Santos. I'm the founder and CTO at [Codice Software](https://www.plasticscm.com/company). We are a Spanish company. We are based in Spain. Not "Madrid or Barcelona". Just the smaller city North of Madrid, and we are crazy enough to develop a version control system. You know there are not many version control systems out there. We are in the _Git Era_, but we built one called _[Plastic SCM](https://www.plasticscm.com)_ and well we are lucky enough. Well, this is like our 14th year in business so we have been around since 2005 and we have customers all around the world. From really small teams, just two people, to huge corporations who purchased more than 3000 licences of our product so that's what we do. Our entire world is goes around version control branching and merging and all of those other things.

**Jamie**
I'll just dial back a little bit. For some of the listeners who may be also used to living in git, I'll just find point out ,obviously, there are lots of other source control systems. But I remember when we were chatting before and chatting with some of your colleagues how the first version of Plastic SCM was released ahead of git so it's a long time that it's been out. A lot of a pedigree, I guess, has gone into this. 

Can you give us a bit of a 10,000 ft overview of Plastic SCM and source control for another some people who don't use source control yet.

**Pablo**
Absolutely. Well Plastic is a version control system built around a few key concepts. We wanted to be very easy to use and we always have .NET developers in mind because we are actually .NET developers. So it is very easy to use but at the same time super powerful. I mean it's super strong with branching and merging which are normally two different, two difficult things for many developers so we are especially strong with that. 

We also develop a very strong GUIs. You know it is really related with the thing of usability and all that, but really visualization, visualizing the repositories. Having really good diagrams around all that. That's our code, right. Those are the things we do well. Then Plastic can work distributed like git does or it can also work at the same time centralised like subversion or all of these other systems which is very good for some teams. And we especially good for game developers because Plastic works quite well with super big files and big projects. We have customers with repositories that are larger than 4, 5, and 6 terabytes and that's not a problem for Plastic, a very high level perspective that's what Plastic is about.

**Jamie**
Wow ok! 4 and 5 terabytes stands that's a lot of files.

**Pablo**
Certainly big right but there is this thing especially in the gaming industry. There are some teams that wonder whether they should put the code and also the the other assets they have like you know video, audio, 3D stuff, whether they should put them all in the same system. They like to put on same system because then life is easier for them and that's why we try to handle (it). Simply, like ok put everything you wanted Plastic we will just handle it.

**Jamie**
Wow! That's amazing!

Hopefully we can get into some of that I'm just going to take some key points that you've raised there a few times. So obviously you said distributed source control and centralised source control and you talked about the SVN and some of the other competitors, I guess is the correct word, but you also said that is .NET.

So is Plastic SCM written in .NET. I know you said that you are a very much .NET developers, but is it .NET or is it something else and you, sort of hook into it with .NET.

**Pablo**
Plastic SCM is like 99% written in .NET. Our server code our client code. Like EVERYTHING is written in .NET. 

Back in the day. We started back in 2005, it was sort of a big challenge because it was like, "should be go .NET for this because mostly all version control systems are written in C or C++ because you need to be cross-platform. I mean if you want to be a professional version control system or serious version control system you need to be cross-platform so we wanted to be cross-platform. And then you need to be fast. The good news, and this is something I love about .NET is that okay you can do it, and we have many benchmarks where we are even faster than you know system written in C. So I can say yes We are written in .NET.

**Jamie**
Wow ok. I do like that that you were saying that there are parts of your system there a faster than code written in C and, as good as C, is and it's very very very powerful and its inherently cross-platform I mean we'll talk about .NET core in a moment. But you know C is inherently cross-platform and it's very fast but it's also very very dangerous. 

So I remember when was in university, from 2004 onwards, we studied computer science but we used C# and .NET in the first year to sort of for some of the newer folks to get their heads around some of the more esoteric development things. I remember when the electrode was challenged about it. Somebody said "hey why aren't we learning C like all the people in the other universities?" And he said C is very good but C is like a chainsaw. If you do it wrong you can lose a limb. You know what I mean? It is very very fast and very very dangerous. So I can totally understand that, and you know .NET isn't inherently slow. A lot of people even back .NET version 1 a lot of people said, "well it is managed so it must be slow," but it really isn't is it?"

**Pablo**
Exactly. I mean, there a few things. I mean if you do like a tight loop where you're going to calculate something, okay chances are C is going to faster. Real life to his never like that right? You have io. You have network. you have different components, and then you have the algorithm you develop or the way you chain things together. For instance, we consistently beat a git in this doing comet of a huge amount of files like 500,000 files. We are like 3x faster. And considering that in order to commit in Plastic it has to go through the network. Even if it's local, we go through the network layer and we do compression. We do a number of things that many of them they do as well. 

We do (those things) in C# and we beat them consistently. We use multi-threading for that, but of course adding multi-threading to C# applications when doing the same in C is much more difficult. are many things that are super simple to do in C# and that is why, back in the day, we decided to go in that direction. 

Of course there are also some rough edges you have to take into account when you write high performance code. Like yeah there are many mistakes like a C# developer normally will do that that a C developer wouldn't do like you know reserving too much memory. It's so easy to create a byte-array again and again and then you don't care really about what's going on underneath and then you pay the price because of the garbage collector is going to kick your butt or something like that. But at the end of the day, if you are careful enough with your code. 

Before programming in C# I did a lot of C++ and also Java and also even Delphi. I don't know if you remember that. It was after Pascal. And my first content with C# was like "Wow! It Works. It Just Works". I mean I was doing something through the network and it worked. I remember during all of my days with C++, it NEVER worked the first time. You forget this you forget that or something is missing. With C# it just worked. It was a feeling that made me think, "Wow I love this language" and the one of the key reasons why we decide to go forward with it back in 2005.

### Cross Platform From Day 1

**Jamie**
That was going to be one of my next question was. Because git is written in C and I guess SVN and other things like that will probably be written in C++ or like you so Delphi, I was interested to find out what the big challenges were with being .NET only in the early days. you know, I mean, we live in a world now with .NET Core and Mono all the other .NETs. We've effectively got cross-platform .NET. You need to do a little bit of work if you're already in framework to move cross but, back in the day, it was Windows only.

Did you have a lot of push back from your customers saying "We can't use that because we don't have a Windows machine". How did you get around that?

**Pablo**
The reason why we really went for C# and .NET is a because Mono was there. Even back in 2005 it was already there, and since it was there, we made the decision to actually go for .NET because it wasn't an option for us to go Windows only. I mean as a version control system you are sort of the operating system of development, the foundation where everything else builds upon. So we wanted to be cross-platform from day one. 

Yeah, we were happy to find that Mono was there. It was, of course there was, not as mature as it is today, and of course the worst thing that didn't work as expected, and the were lot of troubles here and there but mostly it proved to be a good decision. 

So to answer your question we never wear a windows-only system. We run on Linux and Mac from day one thanks to Mono. 

**Jamie**
So does that mean that your development process was Mono across the board? Did you I installed Mono development kits on everyone's machines regardless of what they were running in you would target that, or did you have some developers who are using Windows machines and were building against .NET Framework in our other people building against Mono and then finding the the code didn't work so well?

**Pablo**
It was much like the second choice. We had people working on Windows and we also have people working linux. We had versions of the same binaries at the same day, but we would build them in Linux and Windows and tested specifically the binaries on Windows, Linux, and on Mac from day one. 

We have our test system built round end unit which we call P-End Unit. It's a piece of code we contributed back in the day and it stands for parallel-end-unit. We wrote that to actually be able to run tests on different systems at the same time. We ran our tests on the three platforms basically from day one. Probably after just 4 months into development and after we started the company, we were already had cross-platform tests. 

So it's more like what you said. We had some environments on Windows, most of them on Windows to be honest, but then we also always had machines on Linux and Mac using Mono.


**Jamie**
So then when you were producing your builds, let's say the windows build, was that using the .NET framework and then linux and Mac OS using the Mono runtime or was it let's use Mono across all the devices so that we get the best binary compatibility?

**Pablo**
It was actually .NET for windows and then Mono on the other two. From the binary perspective, it worked could work quite well for ages. The only challenges we faced is that actually having that the Mono runtime on all the platforms was not that easy because then you have to now introduce dependencies. At the end of the day what do we ended doing is that we built our own Mono. 

It's been over 8 years or so that we have built our own Mono based on the official release. We have (an) entire setup to actually package up our own systems on different Linux flavours and that's what we have. On Mac it is much easier because there's a single distribution. On Windows it's the same with .NET, but for Linux we support like five, six, seven distributions we support and then we build our own packages. The reason why we don't use the Mono default was because in some of the platforms they were not officially maintained and stuff like that. So we became, I won't say we are like maintainers of Mono, but we actually package or own using the standard Linux packing system.

**Jamie**
That's one thing I hadn't even thought about, so I can appreciate the overhead involved in that because, at home, I Run a MacBook and a Linux desktop and a Windows laptop so I have experience with you using the majority of those different forms of operating systems and I can't even imagine how, I like you know you said that these products that you support Linux, but Linux isn't an operating system it's the kernel isn't it? It's the distributions of Linux so I can't even imagine the overhead required to support let's say Debian and I don't know Fedora, I'm just pulling these out of the air, I don't know whether these are the actual distributions that use support.

**Pablo**
Those are actually.

**Jamie**
Oh wow. Good guess.

**Pablo**
The other thing is that this very nice piece of software made by SuSe long ago called [OBS](https://build.opensuse.org/) [ed. that stands for Open Build System] that lets you basically have a build machine where you can create packages for many different distros, so that's what we do right. The funny thing, is that while Plastic itself, the binaries are cross-platform because they are just .NET binaries. They should be able to run anywhere. On Linux, as I've said before, we are actually building the Mono. So we're building one for CentOS or Debian for Fedora or SuSe and for RedHat. We basically support branch of different versions so when the customer wants to try Plastic, they just have to run their separate package manager command and then they get it and then we have the repo setup and everything. They just install it. 

It's a bit of overhead as you said. By far, Linux is the most difficult one to maintain. Because the others are just a single distro, but I mean we need to do it so that's what we do. I mean even to present-day mean I every single released we make and we make two or three official releases every week. Each of them is creating the the packages, so if you go to the Plastic SCM website you will see how to install these packages.

**Jamie**
I'm actually a totally blown away by how much how much effort I'm perceiving there is involved in that. I'm probably not even thinking. I am only scratching the surface because have not done proper cross-platform using different distributions of linux that's amazing.

So just for the listeners who are the mainly Mac OS or Windows based, like I said there you know people say "Linux" and I hope you can hear the bunny quotes I'm using. There is no "Linux". There's a linux Kernel which is the kernel of the operating system and then there are distributions of operating systems built on top of that. There families of them, and different distributions have different ways to install applications and different ways to manage the whole system and then and then on top of that you've got the desktop environments and all that kind of stuff so. So how do you manage the user interface then? So for Windows developers at that time, we had Windows forms and I guess with Mono we had something similar using GTK but what if you weren't using what I believe is GNOME, as desktop environment. What if you weren't using GNOME? Are there shims you can include or does it just work?

**Pablo**
That's acutally where the fun starts! We started developing all of our gui's using winforms and then for a while we were lucky enough to run Mono-Forms as they called it. So we had exactly the same look and feel on Windows, Mac, and linux. They were basically like Windows-forms applications running on the three systems. I love how we actually started and you're actually lasted for a few years. What was the problem? Well you know how Mac users, as you know, are quite picky about the guis they use. So a WinForms-like application running on a on a Mac, of course it didn't mean the window itself didn't look like Windows, but more like the controls and settings, so it looked pretty alien on the Mac. 

On linux it probably also looked alien but since there is not such a strong standard or the users on linus are not as demanding about the guis, so it wasn't a big issue. 

So it worked for a few years. We had a lot of issues with it because we weren't able to rely on some standard controls on Mac or linux because it didn't work perfectly there. So we ended up rewriting menu controls have to have a similar look and feel on all platforms. I can share some screenshots of that you can share with the listeners later on.
 
Then like around 2012, a few years into development we decide to rewrite the gui. We kept the Windows form one for windows and then we created a GTK# one for Linux and Xamarin Mac, XamMac as they call it, for MacOS. And that is how we run to this day. We have a shared code-base, but there are specific gui parts, or gui pieces for WinForm, GTK#, and XamMac.

**Jamie**
You've architect away, I guess, so that you you have a common code base that is sitting underneath their view and then you have, almost an MVC and MVVM pattern. So that then you have a separate view system per operating system that matches, what would I guess what people would assume that a Mac OS application would look like or a GTK application or a WinForms application.

**Pablo**
Exactly. While the actual functionality is going to be the same but there are differences in how the actual look and feel is on each platform. For instance if you go to Mac and then your "OK" and "Cancel" buttons are inverted considering what you would have on Windows box. That's a small example, but there are many other things like this that are slightly different but this way, we are free to customise each of the guis for every operating system while the core is the same. When we only had like a single gui for all of them, with the issue of them looking little bit alien, it was not that easy to customise something to look better for Mac users. There were some things that weren't duplicated but you There are things that you would have to do again and again. Like you would have to do it three times.

### High Performance .NET

**Jamie**
So if we take a step away from from the view then. I've never built a version control system but I when I'm committing into git or SVN or something I always get these hashes back. It seems like I can make a commit with loads of changes, I'll get a hash number back based something to do with them. There's some magic that happens there right? Learning how to do that now, I feel would be relatively easy.There's a lot of documentation out there and had to do it but learning how to do that back in the early 2000s. Learning how to build a distributed and centralised version control system in the early 2000s when there were no other big players, how did you guys do that?

**Pablo**
Well, I think it's a very beautiful story because you know the feeling I have a 15 years down the road is that while we were young and naive enough not to know how we were going to do it, so we just did it. If you probably know too much about all the issues you will encounter and how difficult it will be, then you won't probably do it. Like you said there wasn't much documentation about what needed to be done so we just figured out. We did it wrong sometimes. We would have to retry things and do it so many times because of the end of the day our codebases has been with us for years and we need to keep it clean. Basically, when we had some ideas we would spend some time and say "Ok, how can you do this or that? How should we store the revisions? Will it be better to hash it this way or the other way. Should we store it one way or another. 

We just went through it right? I'm sure we did a lot of things wrong especially at the beginning but it's been a very nice trip so far.

**Jamie**
I would imagine that there's like you say there's a lot of algorithm design and API design or I imagine there is a lot of number crunching or maybe cryptographic stuff. Maybe not so much a cryptographic stuff, but definitely number crunching. Did you find at all that the .NET code behaved differently to the Mono code because I know a lot of the early Mono code was a "black box" reimplementation of .NET because obviously there's lot of documentation around in the in the way of "you give `string.Format()` a bunch of inputs and it will give you an output" but there are maybe millions of different ways to to write that method. So did you find them in the early days at least .NET Framework and Mono behaved differently for different functions in different situations.

**Pablo**
Actually, the developers of Mono weren't able to actually look into the .NET code. Even disassembling the stuff, they were not allowed to do because that would break the the licence terms. As you said they had to rewrite a lot of things.

As incredible as it might sound, they did a great job! We didn't find so many places in the code where it be different. We could probably find some performance issues like something that is faster on Windows but is slower on linux or something like that. We've seen that many times, but in terms of functionality I will say we've only found a few points where they behave really different. There is one I know by heart which is "filesystem watcher". you cannot use filesystem watcher on Linux or Mac because it doesn't work well at all. They are trying to mimic windows behaviour on a system that works differently. There are few places where that happened but there are not as many as you would expect.

For instance, this piece of code that this awesome which is .NET remoting. Now it's completely deprecated but I fell in love with this when I first found it because I was an e-commerce developer before this. I used to do you distributed commerce interfaces in C++. So when I first met .NET remoting, for the younger audience, it's like Windows Communication Foundation or later like Google protocol buffers. It was like a protocol made in the early days and it worked surprisingly well. I was doing a lot of stuff and it simply worked. That is how I felt about a lot. I wrote a lot of small test client and server using remoting. Servers running on Linux working on windows and he just worked. 

I had to say that that what the Mono developers did was amazing. It wouldn't be fair if I just complained about the little things we found on the way. Yeah there are little things here and there but overall, it's amazing what they did.

**Jamie**
That leads me to a question about Mono. When you, your colleague Jordi, and I were discussing this episode and how we were going to do it. All fair I think it was Jordi who brought up the fact that because you guys used Mono a lot, Miguel de Icaza actually got involved, looking into some stuff and did a case study. Is that correct? 

**Pablo**
yeah they just recently [published a study telling a story](https://www.mono-project.com/news/2019/02/13/plastic-scm-a-full-version-control-stack-built-with-mono/) of how we use Mono over the years. 

**Jamie**
He's like the grand architect of Mono and Xamarin and everywhere that .NET is going

**Pablo**
Yeah well he's an amazing guy! I was lucky enough to meet him personally. In fact, at the first show we ever introduced Plastic was back in 2006 at TechEd Developers in Barcelona. We went there. It was the first public event that the company as a team as everything and Miguel de Icaza was there. It was a first time we met him and it was amazing. After that we met in person a few times. I tried to email him to tell him how we're doing from time to time. He is one of those amazing developers. World-class developer, one in a million. It a pleasure to have been introduced to him.

**Jamie**
I was just going to ask you since, obviously, Plastic started as a .NET Framework and .NET mono application but the subject of this podcast is .NET core. I realize it is a monumental engineering task but are you planning to or is there a plan to leverage a little bit of .NET Core or are you quite happy with Mono.

**Pablo**
yeah I mean we are super interested in .NET Core. In fact, there are parts of the system that already us it. Event parts that are in the main software, like our website [plasticscm.com](https://www.plasticscm.com/). is completely written in .NET Core currently. We just migrated last year. Of course that was not part of the main piece of the problem but it is an important piece of software for us. After that, we've made several tests especially on the server-side. 

I don't think we'll be moving the client side of things soon. Although I might be mistaken but I think the client will continue to be .NET and Mono for a while, but the server we have a plan to actually migrate it as soon as possible to Dot net core. we already ran tests for the last year and a half or even more. We ran some performance tests and were lucky enough to be in touch with a .NET Core development team. Our developers even used Plastic some benchmarks in the early days. We provided them with an environment to actually do interesting things to compare .NET and .NET Core using Plastic on linux.

To answer your question, yes, there's a plan to actually do it and my personal goal is to end the year with a official server for Plastic SCM running .NET core.

**Jamie**
That's really cool. I just want point out this is Pablo's goal. His personal goal. This is not a business goal. This is him announcing to the public that this is what he is going to do with the product. That is just a goal that he as set for himself. It's not an official thing. He is not saying there will be a version by the end of the year. It is just one of his goals. 

I hope I'm not treading on your toes there. I wanna avoid setting expectations for you there. I don't want you to have to to hold yourself up to that goal of "yes, there will be a version." Unless there IS going to be a version.

**Pablo**
I understand.

Some of our customers they don't really care what we run. They don't care whether this is C#, or C, or Java, or whatever right.

But yeah. There's something interesting is that some of our biggest servers run on linux. It's not that they are better than their windows counterparts or anything. We are super happy with the Windows servers, but many customers prefer to have super big services on Linux because that better fits their culture. Surprisingly some of them ask "Are you going to adapt .NET Core?" Before that, they never really cared if it was Mono, but I think .NET Core is doing a good job in the Linux and Mac user community, or the overall industry, because many sysadmins running a Linux servers now think .NET Core is a good thing to have.

While probably were not concerned about Mono. But now they have these views. So we've gotten a few requests.

Like you said, it's not a 100% thing that we're going to have it, but most likely will try to have with by the end of the year.

**Jamie**
Really? A super quick turnaround as well. You said that you had some tests last year and you were talking with Microsoft presumably shortly before that. Going from I have a stable very important enterprise-level system. Like you said source control systems are the operating system of development. You have this very stable, has to work, every single time, cannot fail, system and there's a new runtime that's been out for at the time of recording at least just over 2 years and you're already here ready to make the jump to port over to it.

**Pablo**
The thing is or server is built on a minimum version of .NET. It's built on .NET 4.5 or 4.6.1. What I mean yes that the code itself, since we always wanted to keep 100% compatible even with old versions of Mono just in case we have to run on a (new) different platform. We had the chance to run on Solaris for a while so we tried to keep the code as simple as possible and not really making it depend on the very latest language feature. That made the move much easier because even some things that were not supported or constructions that were not there, we simply aren't using them. And dependencies for our servers are minimal. 

One of the main concerns especially in the early days of when you would try to convert to .NET Core is that maybe my code can build but what about my dependencies. I may have a ton of dependencies that are not ready for .NET Core. Since our server is so small in terms of dependencies it was not that hard.

I mean it took a while. It probably a month worth of work tweaking the build system but what we built was a core version. It doesn't have the entire functionality, but what it does have is quite complete. For instance our Plastic SCM server, the regular one, can use SQL server or MySQL SQL or Postgres or Firebird, or a bunch of database systems as backend. So it stores the data on the database. Of course this .NET Core, we just supported the bare minimum. For instance our system is integrated with LDAP. You can get the information about users and groups. Since .NET Core build doesn't have LDAP support. That's an example of the shortcuts we made. 

But what we wanted to test was the scalability of the system. How it would perform and the important pieces. What really makes Plastic Plastic was running in that version, and it wasn't that hard because of this you know how the code is written a very small set of the dependencies.

**Jamie**
So because the dependencies are so small you can move over. That's brilliant I do remember when they're done a call first came out, like you were saying, there were a lot of NuGet packages and lot of third party libraries were not ready because they were .NET Framework 4.5 or 4.6 or something and there is no way to actually load those NuGet packages in so you had to rely on everything that Microsoft had done and then they came up with the standard and then that changed everything, but it sounds like you don't even need to .NET standard to make Plastic work.

**Pablo**
Exactly. We are happy it exists and of course now will embrace it, but we were able to build even in the very early days.

**Jamie**
ok so couple of quick questions then if you were to that say you are asked to start all over again with the technology as it stands now would you use mono still would you use .NET core or would you use framework or would you use a completely different technology? What would you, if you were to rebuild Plastic from the ground up?

**Pablo**
ok so had to do that all over again today in 2019 I would go for .NET Core. Absolutely against the way to go I think there is no doubt. I see Microsoft is really going for it. It's going to be cross-platform and officially supported by Microsoft for use a lot with of investment on making it better and also now it's really optimised for server loads. In the early days .NET was able and we actually proved that to do intense server-side calculation and processing and all that right, but it was more like a desktop or client-side technology.

Today, they are super concerned with making .NET Core a server-side technology as well. It doesn't mean just server-side. Look at all the advances in the they do the memory and they handle checks of memory and put them together all these things and how they handle the stack. All of this really makes .NET Core a really good choice for for the server. 

so yeah answering your question I will definitely go with .NET Core today there are still a few small things here and there. Like "Okay, how would you handle a gui with .NET Core. On Linux, you have to GTK#, but what would you do on Mac? There's no Xamarin Mac there, but maybe who knows maybe we would go with Electron. That's also a choice. We are thinking of what we would do today. Electron apps are well understood and would be a good choice.

**Jamie**
Because you said earlier on about separating the sort of backend code from the frontend does this mean that, if you wanted to, you could create a Xamarin frontend for an Android device or maybe maybe a tablet rather than a phone I guess.

**Pablo**
I'm thinking more in terms of desktop right now so when I mention Xamarin on MacOS more than on iPhone or anything else. But of course there are ways to. 
Having actually develop a version control system, having an app very trivial for us. We actually made one. Mostly just playing with the technology.

The magic of .NET Core and .NET in general is that its very "full-stack". You can actually do the entire thing. You can do super specialized server code. You can do code-optimizations. And then you can build a website and you can build a desktop app and then you can build a mobile app.

**Jamie**
yeah I mean you can even run it in the browser now you know because of technology like Blazor

**Pablo**
Absolutely! Yeah that's one of them some more excited to think about in the future. I am really looking into that are really eager to see what goes into it and making some tests, because I'm really excited about blazor.

**Jamie**
So I now realize, leading into a very silly question Plastic SCM in the browser?

**Pablo**
Wells not silly it all. It's something that pops up I think every second week. The entire team is thinking about whether we should go in that direction. 

We have investment right now into the desktop code. We have all these versions running. It wouldn't be super fast to move that to a browser and I would think of electron app or something like that because with version control you need something running on your computer you cannot be completely web-based because you need to access the files and you need to get them uploaded to the server but maybe a blazor thing would be a possibility. 

This is not the first time this has popped up. We've been discussing this many many times in the last few months.

**Jamie**
Fantastic ok. Just to round this up, because I realize this is bleeding into your late evening. For the listeners though we're in completely different time zones; not too dissimilar it's later for Pablo than it is for me so I can appreciate that he's had a long day so far. 

So it just a couple of questions if that's ok Pablo. If I wanted to learn more about Plastic SCM I, obviously, can go to the website, or is there a Twitter? How can I get in contact with, I don't want to say the team because I don't want to say that people should be contacting the Dev team directly, but is there an open channel or way to get in contact?

**Pablo**
The main place to learn more about Plastic is [plasticscm.com](https://www.plasticscm.com/). So you go there you'll find all the information and you can always find us on Twitter at [@PlasticSCM](https://twitter.com/plasticscm). In fact, if you want to, you'll be able you can engage with the actual developers. We are a small team after all. We are like 20 people in the whole company. We are quite a compact team. So one of the great things about a team like ours is that you know it's not difficult to engage with someone because we're not like a super big corporation or anything so yeah it's one of the fun parts.

**Jamie**
So yeah! Listeners should head over to the Plastic SCM website.

**Pablo**
So yeah I'm on Twitter and my handle is [@psluaces](https://twitter.com/psluaces). You can share it later on the website and and yeah I'm more than happy to talk about anything code related.

**Jamie**
Fantastic! And one last question then. This may be more of a marketing type question. Plastic SCM, is it for enterprises? Is it for, I know you mentioned games developers using it, but does it have to be a big company? Can a startup use it? Can people use it to do their own personal projects and what's your target market?

**Pablo**
Well, it's quite wide right? We have very small teams using Plastic. Like two people doing an indie game or something to really big corporations. 

We have for free version for individuals like if you are an individual who just want to give it a try learn about it or use it for your personal projects. And it's also free for open-source projects and non-profit organizations and then we have very affordable prices for small teams and then little bit more expensive for corporations because we have more features and so on.

**Jamie**
So if someone's after listening is checking out Plastic SCM they could maybe create a small project of their own as a personal project, and try it then maybe go to their boss and say "Hey boss, but we move away from git or SVN or TFS and start using this."

**Pablo**
Absolutely and fortunately for us that happens a lot. Individuals and developers giving it a try and then go to their company and saying "hey look I found this!" 

The other I will say about Plastic. I obviously think that the product is good I'm biased. Absolutely! Its where I put my entire work life into making it good. But the thing making it even better is our support team. We have the super responsive support team. So any questions or doubts you may have. We answer 85% of all questions in less than one hour.

**Jamie**
Wow! 85% in less than an hour. That's impressive!

**Pablo**
Yes we are lucky to have such a talented support team. They are all former developers. They work on the core of the system. They really know what they are talking about and its not like they don't know the product or will just drive you to the documentation. They really know it cover-to-cover.

**Jamie**
I guess all that really remains to say is thank you ever so much for being on the show Pablo. It's been incredibly interesting to talk to you about Plastic SCM and amazing to be connected with you today.

It is an incredibly fantastic sounding product and, just talking about it, you say that you had a core of developers using Windows and .NET and a core of developers using Linux distributions using Mono, packaging all of that up and in creating your own distributions of Mono. All of that is amazing! I may have to reach out to you again and have you on the show to talk about how you did all of that too if that's ok?

**Pablo**
That would be awesome. I had a really good time today and I'm super happy. Thank you for hosting me today here. It was really great experience. Thank you very much!

**Jamie**
It really has been incredibly interesting, and if we can connect again for another episode we can talk about the Solaris story. I'm incredibly interested to find out about that.

**Pablo**
Absolutely that will be super, so thank you very much!

**Jamie**
Thank you ever so much Pablo.

### Wrapping Up

That was my interview with Pablo Santos. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and a full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/).

My thanks go to Sean and Dan M from the #linux channel on the Coding Blocks Slack group for helping me identify [Open Build Service](https://build.opensuse.org/), and to Productivity in Tech for providing the transcription of this interview.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Sign up for the mailing list](https://buttondown.email/dotnetcoreshow/)
- [Join the Slack group](https://join.slack.com/t/thenetcoreshow/shared_invite/enQtNjIwNDY1NDk4MTE3LTM3NWZiMDAxMWVlMDQyZGU3NDAyYzgyY2EwYjk2MmZlMjU2NDI4YTNjYzVlZDc2YzYxMDExYjFhZjYzMThlMDM)
- [Support the show on Patreon](https://www.patreon.com/TheDotNetCorePodcast)
- [Pablo Santos on twitter](https://twitter.com/psluaces)
- [How Plastic SCM Uses Mono](https://www.mono-project.com/news/2019/02/13/plastic-scm-a-full-version-control-stack-built-with-mono/)
