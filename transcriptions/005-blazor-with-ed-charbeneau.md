# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself

I am your host, Jamie "GaProgMan" Taylor, and this is episode 5: Blazor with Ed Charbeneau. In this episode I interviewed Ed about Blazor, what is it, a little background on WebAssembly, and how it all works. Some of you may know Ed from the Eat Sleep Code podcast (which is the official Progress Telerik podcast). He is also a Senior Developer Advocate at Progress and a Microsoft MVP.

So lets site back, open up a terminal, type `dotnet new podcast` and let the show begin.

### Ed's Introduction

My name is Ed Charbeneau, and I'm a software developer turned developer advocate. I've been doing software dev for about 15 plus years now, mainly in the web development space. And I've done everything from full stack dev to UI design and all sorts of things.

And now I spend my days working with the community as part of my developer advocacy with Progress. I talk about front end development with all of the .NET stack, and a lot of the JavaScript tools as well. If you've seen me out at conferences, then you've probably heard me talk about .NET; functional programming with .NET; ASP NET MVC; and responsive web design; Angular; webpack; and all of those fun things that people like to use.

And currently I have a podcast as part of my activities with Progress called "Eat, Sleep, Code", it's the official Telerik brand podcast. We don't typically have our own content on there, which is nice. It's very much a community outreach type of a show, where I get to talk to awesome developers from all around the community, and we talk about the things that they are interested in and working on rather than focussing on our own tools and things that we build. It's a lot of fun to get to talk to those people and have them on the show.

I'm also a Microsoft MVP for the third year now, which is phenominal because I don't think that I deserve it. It's one of those things that just happened and I'm very greatful for it.

### What Is Blazor?

**Ed**:
Blazor is an experimental framework from the folks at Microsoft on the ASP NET team. Mainly it is Daniel Roth, who is the Program Manager, and Steve Sanderson, who is the lead developer. This came out of Steve Sanderson's experiments and it's his brain child. 

Blazor is a mixture of everybody's favourite .NET templating language: Razor, and it runs browser side. So Blazor is Browser + Razor.

What's really interesting about Blazor is that it is using Web Assembly of our modern browsers to run C# and .NET Code on the browser.

**Jamie**:
How do we get from C# and a DLL if I'm in .NET Core world or an EXE if I'm in .NET Framework world to running it in the browser?

**Ed**:
So what we have is that web standards are moving forward, and they're now including a new target for putting our code in the browser, and that's [Web Assembly](https://en.wikipedia.org/wiki/WebAssembly/).

So in a traditional app we'd have our HTML, CSS, and Javascript, and that all gets loaded into the browser. Then the browser takes the JavaScript and it parses through that JavaScript, and eventually it turns that JavaScript into a form of byte code. So it's doing this whether you're using Web Assembly or not, and that byte code gets created and then the execution of that byte code actually happens.

So what they've done is taken that byte code and openned up an interface there. So instead of going through this process of sending the JavaScript to the browser, and having the browser do this Just-In-Time type compilation, and turn that into byte code, we can directly insert that byte code into the application.

And that's what Web Assembly is.

So what's happened is the Mono framework - that's the .NET framework that runs all over the place, on many platforms, which started off running on Linux, and it also powers the Xamarin stack. So this is what we're using to do cross compilation on iOS and Android, and now Mono is targetting Web Assembly.

So Blazor is a framework that sits on top of the Mono Web Assembly runtime, and what we do is actually do send DLLs down to the browser. And you'll actually see these coming across the wire if you create a Blazor application. If you open your browser developer tools, you'll literally see `netstandard.dll` flying across the wire, down to the browser; which is extremely odd, because we're not used to seeing that, right?

We're using to seeing JavaScript files, but now DLLs are a static file type that we can use to send application code down to the browser.

### Blazor, WebAssembly, and The Dependency

**Ed**:
Blazor is definitely taking a lot of ceremony out of writing a front-end application. I think it's got some serious potential. And in the last release in Blazor 0.5.1, they added a new feature which I alluded to earlier but I didn't want to muddy the WebAssembly conversation. 

Blazor the framework does not actually need WebAssembly. It can run without it, but it can't run client side without it. Blazor can actually run on the serverside as well. If you're on the server, you don't need WebAssembly, you're just running C# code. So it runs natively on the server, but what they've done is they've separated the UI thread ot where it can run across the web on a web request, and it uses a SignalR websocket.

The way the application is actually structured: is blazor runs on the server. You download the index file, which is the only file you get from the server besides static resources (like CSS and JavaScript). For all intents and purposes, you don't have any HTML coming across other than this index file.

Now, the index file bootstraps a web socket SignalR endpoint, and that connects up to the server running Blazor and it processes all of the UI across that web socket. So you don't actually have a client side application in that scenario, it acts like a thin client or a dumb terminal.

If you interact with the browser it does a diff and says, "alright, this text has changed, and we need to do an update on the UI". And it sends that package of data up the pipe [using the SignalR connection], and it's doing this through a binary transfer. So we're sending a binary package up to the server, and then the Blazor application picks that change up, processes the DOM changes that need to happen, and sends a diff back down. And then the browser updates the UI for us.

And it's very fast.

### Wrapping Up

That was my interview with Ed Charbeneau of Progress. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and a collection of text snippets from the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/).

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [The YouTube version of this episode](https://www.youtube.com/watch?v=tIJx2KhD1_k/)
  - The YouTube version of this episode, if you'd prefer to listen there
- [Ed Charbeneau on twitter](https://twitter.com/EdCharbeneau/)
- [Ed's blog](https://edcharbeneau.com/)
- [The Eat, Sleep, Code Podcast](https://developer.telerik.com/community/eat-sleep-code/)
- [Ed on the Developer on Fire Podcast](http://developeronfire.com/podcast/episode-363-ed-charbeneau-community-powerhouse)
- [BlazeDown](edcharbeneau.com/BlazeDown/)
  - Ed's demo Blazor utility
  - [Ed's write up of BlazeDown and how it works](https://www.telerik.com/blogs/blazedown-experiment-with-markdown-and-blazor/)
- [PokeBlazor](https://pokeblazor.azurewebsites.net/)
  - My blazor demo using the [PokemonAPI](https://pokeapi.co/)
- [Working with Blazor Javascript Interop](https://blog.logrocket.com/working-with-the-blazor-javascript-interop-3c2a8d0eb56c)
- [A Breakdown of Blazor Project Types](https://www.telerik.com/blogs/a-breakdown-of-blazor-project-types)
- [Goodbye JavaScript, Hello WebAssemby](https://www.telerik.com/blogs/goodbye-javascript-hello-webassembly)
- [Ed's new show on Blazor](https://www.twitch.tv/EdCharbeneau)
- [The Blazor repo on GitHub](https://github.com/aspnet/Blazor/)
- [Blazor.net](https://blazor.net/)
- [Learn Blazor](https://learn-blazor.com/)
