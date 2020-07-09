# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR
- and not forgetting The .NET Core community, itself

I am your host, Jamie "GaProgMan" Taylor, and this is episode 1: A Brief History of .NET Core. In this episode, I'll take you through an incredibly brief history of .NET Core; talk a little on how it relates to .NET Framework; and cover the important events from Microsoft's recent history.

So lets open a terminal, type `dotnet new podcast` and let the show begin

##### Introduction

Essentially, I have been writing about .NET Core (at the time of recording) for almost two years. And I'm a bit, kind of obsessed with it, really. I really like .NET Core. I really like .NET Framework, but .NET Core is the way to be, I think - it's the future, I feel.

I am _not_ a Microsoft employee, I just want to say that right off the bat. I'm just a person in the .NET Core community who is passionate about .NET Core and wants to spread the knowledge.

The reason that I started this podcast is because back when I was getting into .NET Core there was hardly anything out there. I mean, Microsoft have been fantastic at setting up [docs.microsoft.com](https://docs.microsoft.com). You can go there and learn all about .NET Core. You can go to the [Microsoft Virtual Academy](https://mva.microsoft.com), they've got loads and loads of course that you can take for free - where you sit and watch the videos and do the "multiple guess" questions at the end. There's a massive community for .NET Core if you search on Twitter for [#netcore](https://twitter.com/search?q=%23netcore) or [#aspnetcore](https://twitter.com/search?q=%23aspnetcore).

Definitely go do a Google-Bing search and check it out.

However, most of these resources weren't around when I started my journey in .NET Core (which, incidentally, is the name of my blog [dotnetcore.gaprogman.com](https://dotnetcore.gaprogman.com/)). I had to learn .NET Core, ASP.NET Core and the others the hard way - that is: I'm an auditory learner, so I don't take as much in when I'm reading documentation, compared to when I"m listening to someone speaking about the same thing.

But what I thought I'd do for the first episode is talk a little bit about the history of both .NET Framework and .NET Core. So, I'm not going to be as detailed as, say Richard Campbell - who is, at the time of recording this episode, reportedly writing a book on the history of .NET. This is just going to be a brief overview to get you around the idea of:

- What's .NET Core?
- How does it relate to .NET Framework?
- What's this thing called .NET Standard?

And all these kinds of common questions.

As a reminder, I do write about .NET Core over at [https://dotnetcore.gaprogman.com](https://dotnetcore.gaprogman.com), and I've already written an article on the history of .NET Core. So if you want to read a long form version of this podcast, then please head over there and take a look.

Here's a direct link for anyone who is reading along: [.NET Core History](https://dotnetcore.gaprogman.com/2018/02/23/net-core-history/)

As with a lot of the stuff I write on that blog, it's a bit of a long post (it currently stands at 1762 words, and that's the short version), and there's a lot of information on there. I'll put a link in the show notes (along with everything else I mention), so remember to check them.

Anyway, let's get started on a brief history of .NET Core

##### The .NET Framework and Mono

In around 2000 to 2002, Microsoft released version 1 of the .NET Framework. The .NET Framework was a wonderful collection of APIs, designed to help with [rapid application development](https://en.wikipedia.org/wiki/Rapid_application_development) that were specific and applicable to the Windows operating system only. I'll quote Wikipedia's article on RAD:

> Rapid-application development (RAD) is both a general term, used to refer to adaptive software development approaches, as well as the name for James Martin's approach to rapid development. In general, RAD approaches to software development put less emphasis on planning and more emphasis on an adaptive process. Prototypes are often used in addition to or sometimes even in place of design specifications.

So the idea is that you rapidly create a prototype, using existing libraries of code to help you fill in the gaps. This can help you to get from a basic design up to a working application as quickly as possible. You'd generally go back and refactor parts of the system once you have it up and running enough that it satisfies the business needs.

In order to do RAD, you have to have a library which can facilitate database connectivity, and it has unit testing frameworks built in, and can do XML serialisation, and a whole bunch of other shopping list items. Well that's that the .NET Framework does. It was, and still is, amazing.

The current stable release of .NET Framework (as I record this in July 2018) is version 4.7.2, and it is fantastic. If you have a Windows server, you can write an application in .NET Framework 4.7.2, throw it at that server, and the server will run it without a problem.

But what about people like me who use Ubuntu and Apple hardware? (that is, I have a PC running Ubuntu Mate and a MacBook Air). What do we do?

Well, in around 2004 a very, very smart engineer called Miguel de Icaza - I've probably butchered the pronunciation of his name, I do apologise. Anyway, he started a project called [Mono Project](https://www.mono-project.com/). This was an attempt at making a cross platform, [black box](https://en.wikipedia.org/wiki/Black_box) reimplementation of the .NET Framework specifically for Linux devices.

A block box reimplementation of something is when you don't see the actual source code, but you re-implement the source code from the available documentation. For instance you might have some documentation which says:

> This method, called "Add", takes in a number and gives you a different number out.

So you might throw a 3 at this method and get out the number 7, and you give it a 9 and you get 13 out. So you sit and think about what the method could possibly be doing to the inputs to get to the outputs. In my horribly contrived example, the core thing that the "Add" method is doing is that it's adding 4 to whatever value you give it. So my reimplementation of this method might take a value, add 4 to it and return the new value.

And that's essentially what Miguel and his team did, but with the entire .NET Framework. And they built an entire open source, black box reimplementation of the .NET Framework, in C++, for the Linux kernel, and they they ported it to MacOS and Windows. Which was interesting because you could have the .NET Framework and Mono installed on your Windows machine and get different performance stats out of your app, depending on whether you ran it on .NET Framework or on Mono.

Now the important thing to remember here is that, at this point, the .NET Framework was written in C and C++, but was primarily aimed at the developers who used C# and VB.NET (and later F#).

Then Miguel started another project called [Xamarin](https://visualstudio.microsoft.com/xamarin/). This was an attempt at making a cross platform UI framework based on [XAML](https://en.wikipedia.org/wiki/Extensible_Application_Markup_Language). So XAML is a standard which adds functionality to XML, and can be used to describe a user interface, and Miguel and his team decided to try and make a single framework which would allow you write your user interface in XAML and have it cross compiled, at build time, to the native format for your target.

As an example, you can have a Xamarin project which contains multiple XAML files, each representing a different slice of the UI for both an Android and iOS app. At build time, Xamarin would take the XAML and the C# code that you had written and produce a binary for Android and a binary for iOS. And then you have one code base to rule them all - make a change, and re-compile for both formats.

And that was pretty cool. It used .NET Framework (if you were building on Windows) or Mono (if you weren't) on the back-end, and you would have an app built specifically for both Android and iOS, but from the same code base. If you're unaware, iOS uses Objective-C and Swift, whereas Android uses Java. So having that ability to cross compile a single code base for both of those formats was amazing.

##### Enter: Satya Nadella

Then, of course, along came Satya Nadella - Satya Nadella essentially started Microsoft's big push towards cloud computing, especially through the Azure platform.

In 2013, when Steve Balmer announced that he was retiring from Microsoft, Bill Gates set up a committee to pick the next CEO of Microsoft, and they chose Satya Nadella. And shortly after he became CEO, Microsoft started working more closely with their competitors. I mean, who could forget the "Microsoft ♥ Linux" slide?

![Microsoft-x-Linux](/img/01-Microsoft-x-Linux.jpg)
**[source for the above image](https://cloudblogs.microsoft.com/uploads/prod/2018/03/ms_loves_linux.png)**

When you think about it a lot of Microsoft's past has been about closed source software. Some of it has been open sourced, though. For instance, certain Microsoft partners were given access to the source code for the .NET Framework; Microsoft created their own Linux distribution (it was called SONIC, which was based on Debian); and if that last one was shocking to you, then you'll be beside yourself to find out that there are Microsoft employees who have committed source to the Linux Kernel.

When Satya started working for Microsoft, he realised that the entire future of the company relied on the cloud. I mean, there will always be a large number of users who demand Windows on the desktop, but the future for apps and services (and especially enterprise) is the cloud. Ask almost any project manager what their application does and they will, invariably, say "the cloud" - they'll also say things like "block chain", "machine learning", or whatever the buzz word of the day is. In fact, it's become so ubiquitous, that it's assumed that the application will run in the cloud.

So what Satya Nadella did was he redirected a lot of the engineering talent at Microsoft over to the cloud. He also decided that it would be a good idea to open source the .NET Framework. As I said earlier, part of the .NET Framework had already been open sourced to certain Microsoft partners, and this made sense because a lot of the NT kernel uses .NET Framework code.

The first part of the .NET Framework to be open sourced was the [Dynamic Language Runtime](https://en.wikipedia.org/wiki/Dynamic_Language_Runtime) - which provided, amongst other things, the `dynamic` keyword. This was actually open sourced before Satya Nadella became CEO.

The DLR was announced in 2007, but not released until 2010. There was an alpha in 2008, but it wasn't released proper until 2010. When the first stable version was released, it was adopted "as is" into the Mono Project. So then everything started being more open, and the ASP.NET team started doing their "[Community Standups](https://live.asp.net/)"

On September 2nd, 2014 Scott Hanselman, Scott Hunter, Damien Edwards, David Fowler, and John Galloway got together and did a live stream of what they were calling the "ASP.NET Community Standup" meeting. It was during this video that they introduced ASP.NET vNext. vNext was then codename for ASP.NET Core.

During the meeting they talked about all sorts of cool things - stuff which was still in the development and planning stages at that point, too. Things like project.json, in place of the older csproj (although, this would later be replaced in .NET Core 1.1 by a much simpler csproj). But the big thing that they wanted to push was Azure, and they even made a point of saying during this call (and I'll put a link to it in the show notes) that the target platform for ASP.NET vNext was, essentially, Azure. And this was massive, because Azure had only really started picking up popularity a few years before.

So the fact that Microsoft had gone all in with the cloud tells you where they where head and where they still are heading today.

##### ASP.NET vNext and Standups

At the time, the ASP.NET vNext team had introduced a thing called Kestrel. This was their next generation web server, and was designed to replace `http.sys`. In the first "standup" (which they all did sitting down), it was mentioned that Kestrel ran in `libuv` which is the cross platform networking stack which is used by nodeJs. The goal was to have C# code talking directly to `libuv`, and that they were going to let developers put `nginx` or `Apache` in front of it.

If you think about it, the .NET Framework had always been a C++ technology, written in C++, for developers who were using C/C++, VB.NET, C#, and F# (although support for that would come later). At this point, they had re-written the entire thing in C# - just like they had done with the compiler for .NET languages (`Rosyln`) a few years prior. This gave them the ability to see where the C# developer experience could be improved, specifically for .NET Core.

One of those improvements is the modularity of .NET Core; it allows you to include "just enough" of .NET Core (or ASP.NET Core) in order to run your app. For instance, during that first meeting Scott Hunter had said actually said these words:

> DAMIEN: Um. But this isn't just about being you able to develop ASP.NET on a Mac
> HANSELMAN: I See
> DAMIEN: We're looking beyond that.
> HANSELMAN: Ok, so for now...
> HUNTER: I want you to host apps on Linux Servers, that's my
> DAMIEN: You heard it from our boss
> HUNTER: That's my goal, is I want you to be able to host ASP.NET app on a Linux server as easily as you can on a Windows server

He even want on to say that you could use `Docker` containers, if you wanted. And that was huge, just think about that. Docker had only just come out - with it's initial release date having happened in March of 2013. So they were already looking at the different technologies that developers would want to leverage in order to host their ASP.NET Core apps on Linux servers.

Shortly after that standup, .NET Core 1.0 was released to manufactures (that's usually shortened to RTM). This means that the initial stable release was finally available, it was no longer an alpha, beta, or release candidate. It was the actual release that developers could start writing production applications with. And developers flocked to it.

It didn't take long for developers to start seeing barriers to entry. The initial release of .NET Core didn't have support full support for XML, and it didn't have `System.Drawing`. Most developers responded to Microsoft with:

> What can we do with this? We can't use this.

Then Microsoft announced that they'd been working on a thing called the `.NET Standard`. We'll cover this in greater detail in a later episode, but you can think of .NET Standard as an `interface`, but in document form. It describes all of the APIs, classes, and types that a version of a platform within the .NET ecosystem MUST support. So .NET Standard version 1.0 says that all platforms (.NET Framework, .NET Core, Xamarin, Mono, for instance) MUST have `System.Linq` and `System.Collections.Generic`, for instance. .NET Standard 2.0 with the Windows Compatibility Pack gives developers access to `System.Drawing`, but only if they target Windows.

##### But Why?

A lot of developers asked:

> Why should I port my application to .NET Core if it doesn't have all of these APIs?

And the answer back from the community was along the lines of:

> Take all of those methods which are .NET Framework specific, wrap them in a micro service (or a number of micro services) and put them somewhere. Then you can re-implement your application stack in .NET Core, making it smaller and faster. This will allow you to adhere to SOLID principles much easier, and allow you to only include the parts of the runtime that you need. And you'll be able to host them on cheap Linux servers, or cheap Windows servers, or wherever you want.

I'm paraphrasing, of course.

And that's what developers working on [Brownfield applications](https://en.wikipedia.org/wiki/Brownfield_(software_development)) did. By re-writing parts of the applications and, essentially, using dependency inversion for the parts of the applications which required .NET Framework specific APIs, they were able to make their applications smaller, faster, and cheaper to host. And as a result, we've seen a massive spike in ASP.NET Core applications and .NET Core applications.

One key thing to remember (if you take nothing else from this episode) is that .NET Core and ASP.NET Core are two separate technologies. They have a similar relationship to each other as the one between .NET Framework and ASP.NET - except that it's perfectly possible to run ASP.NET Core on a .NET Framework base (something that I call a FrankenHack).

Anyway, since then Microsoft have had a huge amount of support from the community, with people checking in features and bug fixes. This is because ASP.NET Core, .NET Core, EF Core and SignalR are all open source. You can head over to GitHub and read through the entire source code for these projects.

If you'll allow me a little hyperbole: can you imagine that? If you traveled back in time to around 20 years ago and told Microsoft not to worry, and that a large amount of their code would be open sourced within 20 years, they've have called you crazy. Maybe not crazy, but they would have said that it was impossible.

##### Wrapping Up

So essentially, that's my brief history of the .NET Framework, .NET Core and how it all fits together. I would say that if you want a slightly more in-depth version of this history, you should head over to my blog at [dotnetcore.gaprogman.com](https://dotnetcore.gaprogman.com/), I have a post on there called .NET Core History and I'll link it in the show notes. If you want more information about the history of .NET, I would take a look at a talk called "The History of .NET" by Richard Campbell, as he is putting together a book on the History of .NET - and that talk is, essentially, the highlights for that book.

You should totally have a look at the GitHub repositories for .NET Core, as you can see a literal history of the entire runtime as it's being built up in the commits. And I'd always recommend that developers read source code by other developers.

Anyway, that's going to do it for this episode. My goal was to keep this one short, and it's been me talking at you for 20 minutes so far. Hopefully you've found this interesting, if you did then let me know by sending me a tweet [@dotnetcoreblog](https://twitter.com/dotnetcoreblog/) on Twitter, or head over to the website [dotnetcore.show](https://dotnetcore.show/) and let me know what you think.

Remember to check the show notes for a link to the full transcription of this episode, which is available at [dotnetcore.show](https://dotnetcore.show/).

I will see you again some time soon. See you later folks.

### Useful Links

- [YouTube version of this episode](https://www.youtube.com/watch?v=oJQ2KrI9_DQ)
  - The YouTube version of this episode, if you'd prefer to listen there
- [https://www.youtube.com/watch?v=1rLbT6pBtak](https://www.youtube.com/watch?v=1rLbT6pBtak)
  - ASP.NET Community Standup - Sept 2nd, 2014 - Introduction to ASP.NET vNext, how and why?
- [The History of .NET with Richard Campbell](https://tv.ssw.com/7218/the-history-of-net-richard-campbell)
- [docs.microsoft.com](https://docs.microsoft.com)
  - The shiny new Microsoft documentation site
- [Microsoft Virtual Academy](https://mva.microsoft.com)
  - A wonderful place full of free training on all of Microsoft's products
- [.NET CORE HISTORY](https://dotnetcore.gaprogman.com/2018/02/23/net-core-history/)
  - A blog post of mine which formed the basis for this episode
- [ASP NET Community Standups](https://live.asp.net/)
  - A weekely (sometimes bi-weekly) live call hosted by Scott Hanselmen, John Galloway, and Damien Edwards
- [https://thedotnetcorepodcast.libsyn.com/](http://thedotnetcorepodcast.libsyn.com/)
  - The official libsyn page for the podcast
- [https://twitter.com/dotnetcoreblog](https://twitter.com/dotnetcoreblog)
