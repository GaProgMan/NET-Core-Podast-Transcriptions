# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is episode 9: Designing Your .NET Core Applications with Steve Smith. In this episode I interviewed Steve Smith about design patterns, and how you can leverage them in your ASP.NET Core application. Steve - also known as Ardalis - has been a Microsoft MVP since 2002, has published numerous courses on both PluralSight and DevIQ, and runs the Weekly Dev Tips podcast. He's an entrepreneur and offers mentoring for teams and individuals who want to develop better software.

So lets site back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Steve's Introduction

My name is Steve Smith, I go by "Ardalis" online because Steve Smith is a disturbingly difficult username to find variations of on various online sites.

I am a Microsoft Developer. I have been writing software professional for over 20 years - which means I'm old. and I've been working with .NET since the very begining - before it was released. I've been excited about .NET Core, which is sort of a rebirth of .NET.

I've contributed quite a bit to the ASP.NET Core documentation, and written some ebooks for Microsoft on architecture. And you may find me on Pluralsight where I've published a number of courses, as well as on DevIQ.

I have my own podcast called [Weekly Dev Tips](www.weeklydevtips.com/), where I have five or 10 minute long episodes that simply describe one tip that can make you a better developer.

And my main thing that I do these days is provide mentoring and coaching for individuals and teams who want to develop better software.

### ASP NET Insiders

The Microsoft ASP.NET team has had a great relationship with the developer community for decades at this point. So this group goes back for almost 20 years. And basically it has an invite-only group of folks that provide feedback to Microsoft on design direction and things that they're working on.

It's become somewhat less relevant now since Microsoft has move to open source, and GitHub, and we have Twitter. So a lot of the conversation that typically would have happened on the ASP.NET Insiders mailing list 10 years ago, today is happening on Twitter or more often on a GitHub issue.

Which I think is great, that Microsoft has become more open. But this group still remains as a group of known, trusted individuals that Microsoft can go to if they have a question on something or some feedback that they want to get from a smaller, closer group of non Microsoft people before they send some messaging out more publicly.

![Top 5 Commits to the ASP.NET Core documentation repo](/img/09-Top5DocsCommits.jpg)

### On The Strategy Pattern and Dependency Injection

**Steve**:
Now I will say that one pattern that I tend to use quite a bit, and it is assumed and built into ASP.NET Core today, is the Strategy Pattern. And you wont find very many classes which end with "Strategy" as their suffix because basically any service in ASP.NET Core can be used as a strategy, because the Strategy Pattern is basically the pattern that describes Dependency Injection.

So if you've ever used Dependency Injection, you've used the Strategy Pattern. And ASP.NET Core has Dependency Injection built in from the ground up.

So when you build apps as ASP.NET Core and you say, "I need to register this service with the service collection," and then you have some controller or something that asks for that service, you're using the Strategy Pattern. That service is being injected using the Strategy Pattern.

### Clean Architecture

**Jamie**:
Would you recommend the Clean Architecture - that clean, oniony, hexagonal architecture - for people who want to move towards ASP.NET Core, or would you recommend that developers figure out what's best for them?

**Steve**:
If you are trying to get to a point where you can write maintainable systems that are unit testable and modular, I recommend that you at least consider some type of project structure that follows the Dependency Inversion Principle.

It doesn't have to be my template, although that will get you going on the right foot if you don't have any experience doing it yourself.

There are other approaches that can be successful, another one that I see gaining traction is Mediator and using micro handlers for every little end point in your application. And if you go that route then you don't necessarily need as much separation as I tend towards. But I think either one of those can work.

What I would encourage you not to do is create one big web project, put everything in that web project, and don't have any separation of concerns or any different logical structures or projects.

And I would also encourage you not to make it so that your business rules end up having a dependency on your database, or on Entity Framework, or on Web Services, or on any other type of infrastructure. Because that's going to make it much more difficult to maintain that code into the future and very difficult to unit test that logic, which is probably the most important logic in your application.

The one place that I would say that's totally fine to just build a web app and not worry about it is if you don't really have any business logic. If you're just building a [CRUD](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete/) system: you have this internal system that has a database and doesn't get used that often, and every now and then somebody has to go and add a record to this table. Sure just build them a simple web page that lets them add and edit rows on a database table, fine.

But if you have something that has some real business logic and it has to be maintained for a while that's got critical business value to your company, you're probably going to want to architect it a little better than that.

### Wrapping Up

That was my interview with Steve Smith. We covered quite a lot of stuff in this episode, so be sure to check out the show notes for a selection of links, and a collection of text snippets from the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/).

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [YouTube version of this episode](https://www.youtube.com/watch?v=_QoIuiS1Cvo)
  - The YouTube version of this episode, if you'd prefer to listen there
- [Steve Smith on twitter](https://twitter.com/@ardalis)
- [Steve's Website](https://ardalis.com/)
- [Architecting Modern Web Applications with ASP.NET Core and Microsoft Azure](http://aka.ms/WebAppEbook)
- [Steve's Pluralsight courses](https://app.pluralsight.com/profile/author/steve-smith)
- [Weekly Dev Tips](www.weeklydevtips.com/)
- [Ditching Hourly](https://www.ditchinghourly.com/)
- [Microsoft's Open Source Documentation](https://docs.microsoft.com/)
- [ASP.NET Documentation](https://docs.asp.net/)
- [E-Shop On Web Repo](https://github.com/dotnet-architecture/eShopOnWeb/)
- [E-shop on Containers Repo](https://github.com/dotnet-architecture/eShopOnContainers/)
- [ASP.NET GitHub Repo](https://github.com/aspnet/)
- [The Importance of Deliberate Practise](https://dev.to/dotnetcoreblog/the-importance-of-deliberate-practise-3cff0/)
  - Steve and I cover deliberate pracise, and this is an article that I'd written about the importance of it.
- [Steve's Clean Architecture GitHub Repo](https://github.com/ardalis/CleanArchitecture/)
- [Dependency Inversion Prinicple](https://en.wikipedia.org/wiki/Dependency_inversion_principle/)
