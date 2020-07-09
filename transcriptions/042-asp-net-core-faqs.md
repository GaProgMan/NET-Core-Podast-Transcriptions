# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie “GaProgMan” Taylor, and this is Episode 42 ASP.NET Core FAQs. In this episode we will answer some of the most frequently asked questions about ASP.NET Core. Some of the topics in this episode have already been covered in other episodes of the podcast, the transcription of this episode - available at [dotnetcore.show](https://dotnetcore.show) and linked in your podcatcher's show notes - contains links to those other episodes. So be sure to click through, in order to find out more.

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Introduction

ASP.NET Core is an rapidly evolving technology which can be used to create Web applications from SPAs (Single Page Applications) to traditional MVC (Model-View-Controller) style applications, and from Web APIs to Web Assembly based apps. As you can tell, there's a lot to learn about with respect to ASP.NET Core - even if you aren't new to .NET development.

So I thought that I'd cover a few of the most frequently asked questions that I have been asked about ASP.NET Core. These questions range from beginners topics all the way up to advanced stuff. So let's just right in.

### Question 1: So What is ASP.NET Core?

Andrew Lock - in his book [ASP.NET Core in Action](https://www.manning.com/books/asp-net-core-in-action) - says that:

> ASP.NET Core is the latest evolution of Microsoft's popular ASP.NET web framework, released in June 2016... ASP.NET Core [makes] significant architectural changes that rethink the way the web framework is designed and built.

ASP.NET Core is a rewrite of the ASP.NET web application framework using .NET Core, allowing for a more streamlined and cross platform set of APIs for creating modern web-based applications. As it is based on .NET Core, it is inherently cross platform - whereas ASP.NET was locked to Windows only.

### Question 2: Can ASP.NET Core Run on .NET Framework?

Whilst only [supported until August 21, 2021](https://dotnet.microsoft.com/platform/support/policy/dotnet-core#'lifecycle) ASP.NET Core 2.1 _can_ run on a .NET Framework base.

Usually ASP.NET Core is added as a NuGet package to a .NET Core application, however version 2.1 of the ASP.NET Core NuGet packages can be added to a .NET Framework 4.x application. The reason for this was that ASP.NET Core 2.1 was originally designed as a "stepping stone" release to allow developers who were using .NET Framework to start migrating smaller services over to .NET Core.

### Question 3: What Can You Create with ASP.NET Core?

As mentioned earlier, ASP.NET Core is a modern web application framework. The latest version of ASP.NET Core - at the time of writing this episode - has support for building:

- SPAs using Angular, React, and Vue
- Traditional MVC applications
- Static Web Sites
- Web APIs
- Web Assembly (via Blazor) applications

As you may be able to tell from the above list, ASP.NET Core supports building the majority of different web-based applications in use today. Not only that, ASP.NET Core supports both HTTP and gRPC as transports - so if you are looking at using gRPC, ASP.NET Core is worth looking into.

### Question 4: Does ASP.NET Core Use HTTP.SYS?

ASP.NET used a library called HTTP.SYS to enable HTTP communications between [IIS (Internet Information Services)](https://en.wikipedia.org/wiki/Internet_Information_Services) and an ASP.NET application running on a Windows server. However, since ASP.NET Core is cross platform, and HTTP.SYS is a Windows library, this is not available when serving an ASP.NET Core application from a Linux or Mac OS host. Microsoft have an entire support page [on docs.microsoft.com](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/servers/httpsys)

{{< pararight "check the episode transcription for a link" >}}

which explains why you may want to use HTTP.SYS, such as:

- Windows Authentication
- Port Sharing
- HTTPS with SNI
- HTTP/2 (when serving from Windows 10 or later)
- and a few more

### Question 5: Where Can ASP.NET Core Applications Be Hosted?

Whilst ASP.NET applications could only be hosted on Windows servers running IIS or on Azure, ASP.NET Core applications can be hosted on either Windows, Linux(es), or Mac OS. This allows you to host your web applications on a number of different servers, running different operating systems. For instance, any of my ASP.NET Core applications can be hosted on:

- A Windows Server with IIS, nginx, or Apache
- A Linux Server with nginx, or Apache
- A Mac OS Service with nginx, or Apache
- Cloud Infrastructure providers, like:
  - Digital Ocean
  - Linode
  - Azure
  - AWS
  - GCP
  - Netlify

Netlify is a special case as it requires a little more effort to set up, but it can be done.

{{< pararight "in fact, updated versions of my talk [Blazor - You Want To Run .NET Where?!](/post/episode-25-blazor-you-want-to-run-net-where/) include me showing how this can be done" >}}

As such, you don't necessarily need a "web server" in the traditional, on premises sense.

### Question 6: How Does Blazor Relate to ASP.NET Core?

At NDC Oslo 2017, Steve Sanderson gave a talk called "[Web Apps can’t really do *that*, can they?](https://www.youtube.com/watch?v=MiLAE6HMr10)" where he showed off an early build of a project that he'd started called: Blazor. This was actually based on an earlier open source project called [.NET Anywhere](https://github.com/chrisdunelm/DotNetAnywhere), which had been abandoned in August 31st of that same year.

For those who don't know: Blazor is a way of running .NET applications within the browser, using the browser's DOM as a UI for the application.

Blazor is actually comprised of two parts:

- Server Side Blazor
- Client Side Blazor

With server side Blazor, a SignalR connection is created between the browser and your server. When a user raises an event (i.e. the click a button, or navigate within your app) a message is sent back to the server via that SignalR connection, the server calculates the new markup, and sends a diff of the markup back to the browser. In this instance, all of the heavy lifting is done on the server and only the UI changes are sent back to the client. From a 10,000 ft viewpoint, it's similar to how RESTful APIs and MVC web applications work.

Client side Blazor is a little different, in that all code required to run the application (including the .NET code) is downloaded to the browser, and it is started in a WebAssembly build of the Mono runtime. This means that your entire application is running inside of the browser, and that there is a large amount of data required to be downloaded in order to start the application.

Putting that to one side, Blazor is as much a part of ASP.NET Core as MVC, WebAPI, and Razor are. As such, if you aren't using Blazor then it won't be included in your app's binaries.

### Question 7: Do I Have To Use ASP.NET Core For Microservices?

Because ASP.NET was tied to both the Windows operating system and the .NET Framework, using it required the presence of both of those which meant that an install for an ASP.NET application was in the gigabytes - as it was essentially a monolithic application and required the presence of that operating system. Work has been done by Microsoft to create [docker images which are as small as possible](https://hub.docker.com/_/microsoft-windows-servercore-iis), but these images are still in the hundreds of megabytes. Whereas both .NET Core and ASP.NET Core are built from the ground up to be cross platform and modular, meaning that if you're not using part of the runtime then it wont be included in the installed binaries. This means that your ASP.NET Core applications will be smaller than the .NET Framework version.

Although this sits well with the cloud native idea of being able to scale out applications as quickly, as possible by spinning up replications of key parts of those systems as microservices, ASP.NET Core doesn't require you to write your applications as microservices. In fact, many large projects like [OrchardCore](https://github.com/OrchardCMS/OrchardCore) and even [Umbraco](https://umbraco.com/) have started migrating to ASP.NET Core - and neither of those are Microservices.

A few of my open source web applications are built in ASP.NET Core, and where not designed as microservices either. Some examples are:

- [dwCheckApi](https://dwcheckapi.azurewebsites.net/) - an ASP.NET Core Web API with EF Core as a data store
- [The Discworld Disorganiser](https://discworlddisorganiser.azurewebsites.net/about) - an ASP.NET Core SPA using Angular
- [PokeBlazor](https://pokeblazor.azurewebsites.net/) - an ASP.NET Core web application using Blazor

### Wrapping Up

Those are some of the most frequent questions that I'm asked about ASP.NET Core. I hope that I've answered these questions clearly and concisely enough for you all. However, if I've missed a question that you would like answering, please don't hesitate to get in contact via Twitter (I'm [@dotnetcoreshow](https://twitter.com/dotnetcoreshow) - my DMs are open), and I'll try to answer them.

Remember to check the show notes for full transcription of this episode, links to any resources

{{< pararight "also for a discount code good for 40% off of Andrew Lock's book (or any other book released by [Manning](https://www.manning.com/))" >}}

all of which is available at [dotnetcore.show](https://dotnetcore.show) - check the show notes in your podcatcher for a direct link.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Related Episodes

- [Blazor with Ed Charbeneau](/post/episode-5-blazor-with-ed-charbeneau/)
- [ASP.NET Core](/post/episode-8-asp-net-core/)
- [.NET Core FAQs](/post/episode-16-net-core-faqs/)
- [ASP.NET Core's Middlware Pipeline with Andrew Lock](/post/episode-17-asp-net-cores-middleware-pipeline-with-andrew-lock/)
- [Microservices in .NET Core with Christian Horsdal](/post/episode-23-microservices-in-net-core-with-christian-horsdal/)
- [Migrating from ASP.NET to ASP.NET Core with Iris Classon](/post/episode-24-migrating-from-asp-net-to-asp-net-core-with-iris-classon/)
- [GRPC with Mark Rendle](/post/episode-39-grpc-with-mark-rendle/)

### Useful Links

- [ASP.NET Core in Action](https://www.manning.com/books/asp-net-core-in-action)
  - `podnetcore18` - this discount code will get you 40% off of Andrew's book, in either physical, ebook or LiveBook formats it's also good for all other books that they sell
- [.NET Core Support Lifecycle](https://dotnet.microsoft.com/platform/support/policy/dotnet-core#'lifecycle) 
- [IIS (Internet Information Services)](https://en.wikipedia.org/wiki/Internet_Information_Services)
- [HTTP.SYS](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/servers/httpsys)
- [Blazor - You Want To Run .NET Where?!](/post/episode-25-blazor-you-want-to-run-net-where/)
- [Web Apps can’t really do *that*, can they?](https://www.youtube.com/watch?v=MiLAE6HMr10)
- [.NET Anywhere](https://github.com/chrisdunelm/DotNetAnywhere)
- [ASP.NET Core Blazor Hosting Models](https://docs.microsoft.com/en-us/aspnet/core/blazor/hosting-models)
- [Windows Server Core Docker images](https://hub.docker.com/_/microsoft-windows-servercore-iis)
- [OrchardCore](https://github.com/OrchardCMS/OrchardCore)
- [Umbraco](https://umbraco.com/)
- [dwCheckApi](https://dwcheckapi.azurewebsites.net/)
- [The Discworld Disorganiser](https://discworlddisorganiser.azurewebsites.net/about)
- [PokeBlazor](https://pokeblazor.azurewebsites.net/)
