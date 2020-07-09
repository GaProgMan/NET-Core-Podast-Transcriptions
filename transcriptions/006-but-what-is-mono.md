# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR
- and not forgetting The .NET Core community, itself

I am your host, Jamie "GaProgMan" Taylor, and this is episode 6: But What Is Mono? In this episode, I'm going to introduce the .NET ecosystem platform Mono, talk about how it's related to .NET Core, and where you might already by using it.

So lets sit back, open up a terminal, type `dotnet new podcast` and let the show begin.

##### Introduction

I'll just take a moment to introduce myself to anyone who is new to the podcast:

I've been using .NET Core since the first 1.0 release to manufacturer build, and I've been writing about it over at [https://dotnetcore.gaprogman.com](https://dotnetcore.gaprogman.com) for almost as long. At the time of recording this episode, that accounts for almost 2 years.

I'm not a Microsoft employee, just a person in the community who really digs .NET Core.

In fact, it's the reason why I started this podacast. For a fuller introduction to me, why I started this podcast, and what I'm hoping to achieve with it, you should check out episode 0 (I'll leave a link in the show notes, so be sure to check your podcatcher).

The show notes for this episode will include a full transcription and some useful links, so don't forget to check them out.

In this episode we'll cover a little about Mono and how it relates to .NET Core. I've mentioned Mono on the podcast before, back in episode one (which was a brief history of .NET Core). This episode will be a little more involved than the brief mention it got in episode 1, though. That's because you may end up leveraging Mono at some point as you start working with .NET Core.

Mono, as we'll see, is an evolving product in the .NET ecosystem as such we'll probably revisit it a few times over the course of the podcast.

Let's talk about Mono - right after this.

##### So What Is Mono?

Back in episode one, I introduced Mono by saying:

> in around 2004 a very, very smart engineer called Miguel de Icaza - I've probably butchered the pronunciation of his name, I do apologise. Anyway, he started a project called [Mono Project](https://www.mono-project.com/). This was an attempt at making a cross platform, [black box](https://en.wikipedia.org/wiki/Black_box) reimplementation of the .NET Framework specifically for Linux devices.

Which is both a tl;dr (that's "too long; didn't read") and a pretty accurate explanation of what happened. Although, I did get one crucial part wrong: it wasn't an open source implementation of the .NET Framework per se. It was an open source implementation of the Common Language Infrastructure (which included .NET Framework).

As a quick reminder, the Common Language Infrastructure is the part of the tool chain which takes your IL compiled code and runs it on the Common Language Runtime. The Common Language Infrastructure includes:

- Common Type System
  - you can think of these as the Base Class Libraries
  - have a listen to the previous episode for a little information on those
- Meta data about your code
- Common Language Specification
- Virtual Execution System
  - this is (effectively) what runs your compiled application

All of that is an extremely brief overview of some of the things that Common Language Infrastructure includes. It has been standardised by both ISO as ["ISO/IEC 23271:2012"](https://www.iso.org/standard/58046.html), and by ECMA as ["ECMA-335"](http://www.ecma-international.org/publications/standards/Ecma-335.htm).

[Wikipedia](https://en.wikipedia.org/wiki/Common_Language_Infrastructure) describes it as:

> The Common Language Infrastructure ... describes executable code and a runtime environment that allows multiple high-level languages to be used on different computer platforms without being rewritten for specific architectures.

As the CLI (not to be confused with Command Line Interface. I'm not going mention the command line interface in this episode) is designed to be platform (in this case operating system) agnostic, it was only a matter of time before someone decided to create an open source implementation for Linux.

##### A Little More On Mono

Mono gained a lot of attention in the open source and Linux development communities, especially seeing as Miguel de Icaza was already pretty well known in the Linux community. If you've ever used the GNOME desktop environment on a Linux distribution, then you've used one of his projects. Both Miguel and Federico Mena released the initial version of GNOME in 1999.

Miguel formed a company (initially named Helix Code, but later renamed to Ximian), and it was through that company that he announced the Mono project. It gained so much traction that a whole year before version 1 of Mono was released, the company was bought by Novell.

The first publicly available version of Mono was released in June 2004. It had full support for C# 1.0 - which had only been standardised via both ISO and ECMA the year before. It was soon followed by version 1.1 (in September 2004) which had full support for C# 1.1.

It would only take a further 2 years for Mono to align with the API and C# versions that .NET Framework supported. Effectively, they were being developed and released at the same time. Along the way, the Mono team added their own APIs to the Mono stack too (Mono.Cecil, Mono.Cairo and Mono.Posix for example).

In January 2009, Mono 2.2 was released; one of the biggest features of Mono 2.2 was the inclusion of Static Compilation. This was their implementation of [ahead of time compilation](https://en.wikipedia.org/wiki/Ahead-of-time_compilation). This allowed developers to take their Mono projects, usually written in C# or VB and compile their project down to native code for their format.

This allowed Miguel to say the following (in a [blog post from 2008](https://tirania.org/blog/archive/2008/Nov-05.html)):

> Another nice piece of technology that we showed at the PDC was static compilation, the feature behind allowing Mono to run on the iPhone in a fully legit way (no jail-breaking)

At that point in time (as it still is now) the iOS platform was a "walled garden" meaning that you could only develop for iPhones or iPads using Apple hardware and the Apple approved developer toolchain. But Miguel's team had gotten around this with their nascent platform.

It was around this time that the Mono team announced the [C# Compiler as a Service](https://tirania.org/blog/archive/2010/Apr-27.html) which had support for C# 5.0 a full 7 years before it was standardised by ECMA, and 3 years before Microsoft released support for it in the form of Visual Studio 2012.

I would recommend giving both of those blog posts a read, as they are fascinating (check the show notes for links to them).

##### What Happened Next?

The development of new features for Mono continued at a meteoric trajectory. That is until Attachmate came along.

In early May of 2011, Ximian's parent company Novell was acquired by Attachmate. Shortly after the acquisition, Attachmate started making layoffs. Some of those layoffs were key personel in the Mono project, and the Internet went wild with speculation as to the future of Mono.

Steven J. Vaughan-Nichols [writing for zdnet](https://www.zdnet.com/article/is-mono-dead-is-novell-dying/) said:

> De Icaza, who is usually very outspoken, has also not tweeted nor written on his blogs about the fate of Mono and his own future with Novell. My understanding is that all of the Mono team, approximately 30-individuals, have been let go.

Miguel kept quiet until mid-May, at which point [he announced a new company called Xamarin](https://tirania.org/blog/archive/2011/May-16.html). Xamarin would be a commercial entity and would produce tools which would enable developers to create applications on iOS and Android using Mono. He also announced that:

> We have been trying to spin Mono off from Novell for more than a year now. Everyone agreed that Mono would have a brighter future as an independent company, so a plan was prepared last year.
> To make a long story short, the plan to spin off was not executed. Instead on Monday May 2nd, the Canadian and American teams were laid off; Europe, Brazil and Japan followed a few days later. These layoffs included all the MonoTouch and MonoDroid engineers and other key Mono developers. 
> ...
> So, with a heavy dose of motivation from my music teacher, we hatched a plan.
> Now, two weeks later, we have a plan in place, which includes both angel funding for keeping the team together, as well as a couple of engineering contracts that will help us stay together as a team while we ship our revenue generating products.

Shortly after this, [Attachmate allowed the Xamarin team a perpetual license to use Mono and all related technologies that were created at Novell](https://tirania.org/blog/archive/2011/Jul-18.html):

> Xamarin obtained a perpetual license to all the intellectual property of Mono, MonoTouch, Mono for Android, Mono for Visual Studio and will continue updating and selling those products.

Miguel and his team could do whatever they wanted with Mono. And they did.

It didn't take long for Xamarin to start creating new tools for developers, including Xamarin.Mac in 2012 which was a plugin for MonoDevelop. In 2013, Xamarin Studio was released (this was a re-branding of MonoDevelop) along with integration into Visual Studio, allowing Windows users to write .NET Framework code and have it compiled for Android and iOS.

In 2016 Xamarin was acquired by Microsoft for an undisclosed amount. This allowed Microsoft to ship Xamarin as a free tool with Visual Studio, and to offer it as part of their new cross platform tooling. Mono was also re-licensed as MIT.

##### Why Do I need .NET Core When I Could Use Mono?

That is a very valid question, indeed it's a question that a lot of people asked when .NET Core had it's first alpha releases (as both `dnu` and `dnx`).

Well, for starters Mono was originally designed to be binary compatible with .NET Framework. This means that, whilst some of the underlying implementation details may be different, Mono is (from a 10,000 feet view) the same as the .NET Framework.

Whereas to quote Dustin Metzgar's book [.NET Core in Action](https://www.manning.com/books/dotnet-core-in-action):

> .NET Core's modular design means that you only include the dependencies that you need, and all of those dependencies go into the same folder as your application. Deploying an application is now as simple as copying a folder.

(I'd definitely recommend his book, by the way)

So if you only need to include `System.IO` and `System.Collections.Generics` (for instance), then your code wont need the entirety of .NET Core to be installed or included with your application. Whereas Mono requires the entire platform to be installed globally.

Anyone who has ever had to maintain legacy servers with low hard drive capacity (around 100GB) will know the pain of having to install multiple versions of the .NET Framework in order to support newer applications. Especially if the other applications on the server required earlier versions of the .NET Framework. You can _very quickly_ run low on hard drive space.

Of course, none of us have to support such servers in the age of the cloud.

However, if you get into using Blazor (which we'll talk about in a later episode) you'll invariably end up using Mono - even if you don't know it. And the same can be said for Xamarin and Unity 3D. Because of that it's worth knowing about, at the very least.

##### Wrapping Up

We'll leave it there, I think.

We've covered a lot of ground here, and most of it was unrelated to .NET Core.

The Mono project has a wonderful history, and its worth knowing about it if you are serious about developing with the .NET ecosystem. Even if you don't know the history, its will be worth knowing that Mono exists and how we went from it to Xamarin.

We covered what the Common Language Infrastructure is, how that is related to .NET Framework, what Mono is, and how it came to be.

You've probably used Mono and not realised it, especially if you've used Blazor (again, we'll cover that in a later episode), Xamarin, or Unity 3D.

Anyway, that's going to do it for this episode. Hopefully you've found this interesting, if you did then let me know by sending me a tweet [@dotnetcoreblog](https://twitter.com/dotnetcoreblog/), or head over to the website [dotnetcore.show](https://dotnetcore.show/) and let me know what you think.

Remember to check the show notes for a link to the full transcription of this episode and links to a bunch of related websites and resources. These is available at [dotnetcore.show](https://dotnetcore.show/).

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [YouTube version of this episode](https://www.youtube.com/watch?v=KqmrdOEJX4A/)
  - The YouTuve version of this episode in case you'd prefer to listen there.
- [Episode 3 - What Is .NET Standard?](https://dotnetcore.show/episode-3-just-what-is-net-standard)
  - This episode of the podcast includes a description of what the Base Class Libraries are and how they're used
  - A wonderful interview with Steve Sanderson, on Scott Hanselman's podcast
- ["ISO/IEC 23271:2012"](https://www.iso.org/standard/58046.html)
- ["ECMA-335"](http://www.ecma-international.org/publications/standards/Ecma-335.htm)
- [Static Compilation in Mono](https://tirania.org/blog/archive/2008/Nov-05.html)
- [Blazor brings .NET to Web Assembly with Steve Sanderson](https://hanselminutes.com/642/blazor-brings-net-to-web-assembly-with-steve-sanderson)
