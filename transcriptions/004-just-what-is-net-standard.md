# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR
- and not forgetting The .NET Core community, itself

I am your host, Jamie "GaProgMan" Taylor, and this is episode 4: Just What is .NET Standard? In this episode, I'll take you through what the .NET Standard is, why we need it, and who is in charge of it's evolution

So lets sit back, open up a terminal, type `dotnet new podcast` and let the show begin.

##### Introduction

If you're new to the podcast, then you might not know that I've been writing about .NET Core for almost two years (as I record this). And it's still quite exciting to me.

I am _not_ a Microsoft employee; I make a point of saying that at that start of each episode, by the way. But if Microsoft want to offer me a role...

In this episode, I'm going to take you through just what the .NET Standard is, why it was created, and how it relates to .NET Core.

As a reminder, I do write about .NET Core over at [https://dotnetcore.gaprogman.com](https://dotnetcore.gaprogman.com), and I've written about the .NET Standard a few times already. If, after you've listened to this episode, you want to read a little more about .NET Standard, then make sure check the show notes for links to my previous articles on the subject (along with a few other recommended urls).

If you don't know where to find the show notes, don't worry. There'll be a link in the description of this episode in your podcatcher of choice, and I'll mention the podcast website a bunch of times anyway - [https://dotnetcore.show/](https://dotnetcore.show/)

As the .NET Standard is evolving all the time, some of the minutia I cover in this episode may become out of date. I'll make a point of keeping a list of errata in the show notes, so remember to check them. I'll also, no doubt, be covering the .NET Standard in later episodes so remember to check back for more episodes on it.

Anyway, let's talk .NET Standard - right after this.

##### So What Is .NET Standard?

Everything (and I mean _everything_) that we use on a daily basis has a set of standards documents behind it. Your credit, debit, or ATM card adheres to a set of standards set up by the international banking industries - things like the physical size of the card, where the magnetic stripe is located and (if it has one) the type of chip and NFC circuit inside it.

Have you ever noticed that most doors are the same size? How about keys? What about buses and trains? Cars, too. Even things we don't see like power, water, cell phone signals, medical instruments, and the whole of BlueTooth and USB. There are standards which dictate how these things should work; some countries have their own standards for things like radio waves (which frequency bands are permitted, etc.) or slightly different versions of the international standards (whether to use AC or DC for power socket, for example).

The .NET Standard is no different.

Back when .NET Framework was first released, one of it's killer features was that it had something called the Base Class Library (or `BCL`) this allowed the .NET Framework to expose certain data types to us developers (`string`, `double`, and `int` for example). This BCL was used to communicate with the Common Infrastructure (which is a collection of compilers, linkers and runtime components). This was fantastic, because it meant that you could write entire software libraries in C#, VB.NET or even managed C++ and consume any of it using any of the other managed languages.

Then along came Mono, with it's own BCL; suddenly there were two BCLs. Then came Xamarin, and there were three. Then .NET Core, and there were four.

I don't know whether you've ever had to support two different code bases for the same app (an example would be an Android app code base in Java and an iOS app code base in Swift). If you make changes to one - to use some new feature of your web based API for instance - then you have to make that change in the other code base, too.

Imagine doing that with four separate code bases.

Then remember that each of those four technology stacks are at different maturity levels (.NET Framework is, essentially, feature completed at this point, whereas .NET Core is still evolving) and target completely different operating systems (.NET Framework targets Windows, whereas .NET Core targets Windows, MacOS and Linux).

What a nightmare! Especially since Microsoft now own all of those technology stacks. Meaning, as soon as they want to implement a new API or feature, they need to supply many times the effort required to implement them. THEN think about how all but .NET Famework are cross platform, and that they all use different underlying OS system calls.

One of the biggest points for using .NET Framework was that you could create Portable Class Libraries (or `PCL`s); this is what enabled you to create a class library in C# and have a managed C++ project consume it, and vice versa. Each of the .NET ecosystem platforms (Framework, Mono, Xamarin, and Core) had their own PCLs, so they were no longer portable.

##### Along Came The Standard

Before we go on, I just want to talk about platforms and ecosystems. In the context of .NET, we have one ecosystem (i.e the .NET Ecosystem) and many platforms (.NET Framework, .NET Core, Mono, Xamarin, Unity, etc.). Only once you get that definition straight, will the rest of the documentation and discussion around the .NET Standard start to make sense.

---

As you can no doubt tell, having four different PCLs created quite a difficult situation for Microsoft - a company which prides itself on backward compatibility. They couldn't just drop an entire platform because it was difficult to maintain (I'm not going to mention Silverlight, as this was related more to browsers and the evolution of HTML5 than anything else), so they needed a different plan.

So they decided to standardise it.

Essentially, the .NET Standard is a versioned document (at the time of recording this episode it has versions 1.0, to 1.6, and 2.0) which lists all of the APIs, types and namespaces that a platform within the ecosystem must support. Which is a long winded way of saying that it's:

> Microsoft’s attempt at standardising how the cross platform .NET APIs will work across all supported .NET platforms (including IoT and RaspberryPi support)

(that's a quote from a blog article I wrote about the [.NET Standard back in November, 2016](https://dotnetcore.gaprogman.com/2016/11/24/net-standard-what-it-is-and-how-it-applies-to-net-core/). Check the show notes for a link to it)

The idea is to replace all of the disparate, platform dependent BCLs, with One BLC to Rule Them All<sup>tm</sup>.

However, since the code which runs all of the different platforms is already out there and has been for almost 2 decades (at least, in the case of .NET Framework), it can't easily be swapped out. So what's a Multi-national Technology Company to do, other than form a committee and figure it all out?

That's where [Immo Landwerth](https://twitter.com/terrajobst) and his team come in.

It's their task to decide which APIs, types and namespaces are supported by each version of the standard, and to ensure that they are indeed supported across the different ecosystem platforms (there's that phrase again).

In the case of platforms like .NET Framework and Mono, almost all of these APIs (etc.) are supported by default. In fact, .NET Framework 4.5 was used as the basis for the first version of the .NET Standard, as it was seen to be almost feature complete anyway.

##### But the way it all works is a bit obtuse, right?

Nope.

Since you're listening to this podcast, I can assume that you are interested in development. In C# we have the idea of `interfaces`, these allow us to describe the public methods that a class will implement (by listing their signatures), and any class which implements an interface _must_ implement all of the methods listed in the interface - it can implement more methods, but the ones in the interface _must_ be implemented.

For my C and C++ developer friends, this is analogous to how header files work.

Since we know what interfaces are, we can use them as a metaphor for the .NET Standard. A version of a .NET ecosystem platform, say .NET Framework 4.5, _must_ implement everything described in the interface to .NET Standard 1.0, whereas .NET Framework 4.6.1 (for example) _must_ implement everything described in .NET Standard 2.0.

(check the show notes for a more visual example of this in the form of a code snippet. I'm not going to read it out because you don't want to hear me reading code. But check it out, because there are a bunch of interfaces that all implement each other.)

{{< highlight csharp >}}
// Again, this is an example so it isn't perfect C# code, but it's
// enough to get the point across.
interface INetStandard_1_0
{
  System;
  System.Collections;
  System.Colloections.Generic;
  /* ... */
  System.IO;
  System.Linq;
  System.RegularExpressions;
  /* etc. */
}

interface INetStandard_1_1 : INetStandard_1_0
{
  System.Collections.Concurrent;
  System.Numerics;
  /* etc. */
}

// ...

inteface INetStandard_1_6 : INetStandard_1_5
{
  System.Security.Cryptography.Algorithms;
  /* etc. */
}

interface INetStandard_2_0 : INetStandard_1_6
{
  System.Data;
  System.Data.Common;
  System.Data.SqlTypes;
  /* ... */
  System.IO.Compression;
  System.IO.IsolatedStorage;
  /* etc. */
}

public class DotNetFramework_FourPointFive : INetStandard_1_0
{
  /* Actual implementations of the APIs here */
}

public class DotNetFramework_FourPointSixPointOne : INetStandard_2_0
{
  /* Actual implementations of the APIs here */
}
{{< /highlight >}}

##### A More Concrete Example

Let's say that you work for a bank, and it's decided that the website and API for the bank needs to be re-written and modernised. It's decided that you are to going to use .NET Framework 4.6.1 to build the API, using [Domain Driven Design](https://en.wikipedia.org/wiki/Domain-driven_design), and use nodejs for the front end.

It's then decided , on the day that it's released to the public, that the bank should have both an iOS and Android app. So you decide to build one using Xamarin. During development, you copy the relevant models and business logic over to the code base for the app.

Then the bank decides that it wants to create a game, one which can be used to teach children how to save money. It's decided that the game should _not_ connect to the real API, so you start copying over the relevant parts from the API web service and build a Unity app.

{{< pararight "By the way, I'm not saying that this is how you would go about it, I'm just using an extremely contrived example to get the point across" >}}

When the Android and iOS apps and the Unity game are released, someone points out a bug in the service layer code. You scramble to fix it for the API to the website. Then you remember that the code in the Android and iOS app need to be updated, too. Just when you think the smoke has cleared, you remember that the Unity app needs to be updated as well.

{{< pararight "THEN you are told that each customer can have multiple accounts" >}}

In a previous design, it had been assumed that each of the bank's customers could only have one account. So you go back to Visual Studio and add support for multiple accounts per customer in the API; then replicate it in the Android and iOS apps, and finally the Unity app.

As you can see (or hear, as the case may be), if each of the apps that we'd written:

- API
- Android
- iOS
- Unity

used a set of common library code (in my example this was the entities and services, but in real life it wouldn't be that simple), then issuing updates would be a case of updating the relevant DLLs and importing them back into a new build of the code bases for those apps. Which is what the .NET Standard is all about.

By targeting a version of the .NET Standard rather than a specific ecosystem platform, you're ensuring that your code can run on:

- .NET Core
- .NET Framework
- Mono
- Xamarin (iOS, Android, and Windows)
- Univeral Windows Platform
- Windows Phone (as you target .NET Standard 1.0, 1.1, or 1.2)
- Or any possible future .NET ecosystem platform

However, there is a trade-off here. The higher the version of the standard, the more APIs you gain access to; however you get access to fewer .NET ecosystem platforms. For a visual of how this works, check the show notes.

Essentially, there are fewer .NET ecoysystem platforms which support .NET Standard 2.0 than there are which support .NET Standard 1.0. So the higher the value for the .NET Standard, the fewer possible platforms you can target.

Here is a table for all of you who are reading the show notes:

|.NET Standard|    [1.0] | [1.1] |   [1.2] |  [1.3] |   [1.4] |   [1.5]         | [1.6]         |         [2.0] |
|:-------------------------------------|---------:|------:|--------:|-------:|--------:|----------------:|--------------:|--------------:|
|.NET Core                             |     1.0  |  1.0  |    1.0  |   1.0  |    1.0  |    1.0          |**1.0**        |        **2.0**|
|.NET Framework                        |     4.5  |**4.5**|**4.5.1**| **4.6**|  4.6.1  |  4.6.1 |4.6.1 |      **4.6.1**|
|Mono                                  |     4.6  |  4.6  |    4.6  |   4.6  |    4.6  |    4.6          |**4.6**        |        **5.4**|
|Xamarin.iOS                           |    10.0  | 10.0  |   10.0  |  10.0  |   10.0  |   10.0          |**10.0**       |      **10.14**|
|Xamarin.Mac                           |     3.0  |  3.0  |    3.0  |   3.0  |    3.0  |    3.0          |**3.0**        |        **3.8**|
|Xamarin.Android                       |     7.0  |  7.0  |    7.0  |   7.0  |    7.0  |    7.0          |**7.0**        |        **8.0**|
|Universal Windows Platform            |    10.0  | 10.0  |   10.0  |  10.0  | **10.0**| 10.0.16299      |10.0.16299     | **10.0.16299**|
|Windows                               |     8.0  |**8.0**|  **8.1**|        |         |                 |               |               |
|Windows Phone                         |     8.1  |  8.1  |  **8.1**|        |         |                 |               |               |
|Windows Phone Silverlight             |   **8.0**|       |         |        |         |                 |               |               |

{{< pararight "The above table was taken from the [.NET Standard GitHub repo.NET Standard GitHub repo](https://github.com/dotnet/standard/blob/master/docs/versions.md) and is correct at the time of writing" >}}

This table shows the .NET ecosystem platforms as rows, and the .NET Standard versions as columns. As the .NET Standard version number increases, the platform support drops off.

Microsoft's official guideline when targeting .NET Standard is to target the lowest version of the standard that you can get away with, in order to get the widest possible ecosystem platform target area.

##### Wrapping Up

We'll leave it there, I think.

.NET Standard is a complex enough topic that both Immo and the ASP.NET team have had to think of multiple different ways to explain it. When it was first announced, members of the community started asking "How do I install .NET Standard?" and similar questions, but Immo and his team have been truly transparent about it, and he has even created a series of short YouTube videos which explain .NET Standard (check the show notes).

The .NET Standard is a point of reference for describing which APIs and namespaces are supported in the different versions of the .NET ecosystem platforms. The .NET ecosystem platforms include:

- .NET Core
- .NET Framework
- Mono
- Xamarin (iOS, Android, and Windows)
- Univeral Windows Platform

but can expand to include any new platform which adheres to the .NET Standard. Higher versions of the Standard contain more APIs, but reduce your potential ecosystem platform support.

By ensuring that your libraries target .NET Standard rather than one of the platforms, you can be sure that those libraries are consumable by the widest possible number of ecosystem platforms.

Anyway, that's going to do it for this episode. Hopefully you've found this interesting, if you did then let me know by sending me a tweet [@dotnetcoreblog](https://twitter.com/dotnetcoreblog/), or head over to the website [dotnetcore.show](https://dotnetcore.show/) and let me know what you think.

Remember to check the show notes for a link to the full transcription of this episode and links to a bunch of related websites and resources. These are available at [dotnetcore.show](https://dotnetcore.show/).

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [YouTube version of this episode](https://www.youtube.com/edit?o=U&video_id=xGFCEzNKEuM)
  - The YouTube version of this episode, if you'd prefer to listen there
- [.NET Standard – What is it and how it applies .NET Core](https://dotnetcore.gaprogman.com/2016/11/24/net-standard-what-it-is-and-how-it-applies-to-net-core/)
  - my first blog post on .NET Standard
- [.NET Core and  .NET Framework working together, Or: The magic of .NET Standard](https://dotnetcore.gaprogman.com/2017/06/01/net-core-and-net-framework-working-together-or-the-magic-of-net-standard/)
  - A blog post of mine on consuming a .NET Framework library (targeting .NET Standard) with .NET Core
- [What is .NET Core? 7 Things you should know](https://codeshare.co.uk/blog/what-is-net-core-7-things-you-should-know/)
  - A wonderful blog post by Paul Seal which includes a very succinct description of .NET Standard
- [Immo Landwerth's Youtube videos on .NET Standard](https://www.youtube.com/watch?v=YI4MurjfMn8&list=PLRAdsfhKI4OWx321A_pr-7HhRNk7wOLLY&index=1)
- [.NET Standard GitHub repo](https://github.com/dotnet/standard/blob/master/docs/versions.md)
