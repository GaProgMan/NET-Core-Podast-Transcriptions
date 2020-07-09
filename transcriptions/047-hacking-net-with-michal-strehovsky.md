# Sponsor Message

This episode of The .NET Core Podcast is brought to you in part by {{< sponsor-link link-text="RJJ Software" link="https://rjj-software.co.uk" >}}

RJJ Software is dedicated to helping you to realise your company's digital potential through innovative solutions using the latest technologies.

Utilising the latest in .NET and cloud technologies, we can help you build the solution to your business needs, on time and under budget.

We have world class experience in cross platform development using the latest iterations of the Microsoft technology stack. This includes .NET Core; SQL Server; and Azure. Is Azure not your thing? That's fine, because we have experience with AWS, GCP, Linode, and Digital Ocean, too.

We know what it means to have to be able to iterate quickly, and how important DevOps practises are when it comes to remaining Agile. As such, we have experts in the major build and release pipelines: from Azure DevOps to AWS, from Netlify to TravisCI, AppVeyor, and everything in between).

So get in touch today at {{< sponsor-link link-text="RJJ Software" link="https://rjj-software.co.uk" >}}, or check the show notes for a link.

# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is episode 47: Hacking .NET with Michal Strehovský. In this episode I interviewed Michal about his work with the CoreCLR, CoreRT, and some of his most recent blog posts - including one where he built and ran a .NET Core app on Windows 3.1. Some of you may know Michal from his work at Microsoft, or from his open source work on the CoreRT runtime.

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Michal's Introduction

**Jamie**

The first thing I'd like to say is thank you ever so much for taking part of your Saturday morning out and talking to me. We're all really busy these days. And I'm very aware that it's a very nice thing for you to spend some time, and talk to me. So thank you ever so much.

**Michal**

Yeah. Thank you for having me.

**Jamie**
You're very welcome. Before we get into sort of the topic at hand, I was wondering, could you give the listeners a brief introduction so that they know a little bit about you and some of the work that you do?

**Michal**

Yeah, so my name is Michal Strehovský. I am one of the engineers who work on the .NET runtime at Microsoft. I have been doing this for about seven years now. I have been with Microsoft for nine; I started working on Windows, but then I decided I wanted to do something else. Kind of most of my time in .NET I was working on ahead of time compilation technologies. So if you heard about .NET native, that's the thing that basically I joined the team to ship the v1 of and V2 as well. And now I'm mostly doing CoreCLR.

**Jamie**

You've worked on the CoreCLR, is that different to the Framework CLR? Or is it just literally what it's called? It's called CoreCLR in Framework and Core and perhaps, you know, although you may never have touched it Mono and things like that, is it the same thing?

**Michal**

So CoreCLR and CLR are very related. So CLR is the runtime that has been there since, I don't know, the year 2000 or 2001 when .NET first shipped. And it's the virtual machine that has been powering .NET ever since then. And at some point, Microsoft realised that CLR, as it is, is very tightly coupled with Windows and it would be nice to be able to use the CLR, or to use .NET, outside of Windows. And when the Silverlight project started, Sliverlight had this need that, "okay, we need to run .NET outside of Windows. How can we do that?" At that time, a lot of engineers within Microsoft looked at CLR, looked at what pieces can be reused. And they created a subset of CLR that powered Silverlight. And Silverlight was this runtime that you could run within the web browser, and it worked on Windows, and it worked on Mac OS, and Silverlight faded out. But the technology that was built for Silverlight, it didn't fade out. And that's basically what became CoreCLR. It's basically the refactor or extracted. reusable. and cross platform part of the CLR. So they removed pieces that didn't make sense outside of windows, kind of use everything else to run .NET apps elsewhere.

**Jamie**

So the core kernel part of .NET core has that heritage of Silverlight. In that Silverlight was great, and it lasted for a long time. And then a whole bunch of Silverlight developers got upset because it went away. But don't worry, because it's still kind of here, in a way?

**Michal**

Yeah. Microsoft has a lot of tradition of using technology. So kind of rebuild a lot of technology. And then we how apply it elsewhere. So this is one of those things.

**Jamie**

Sure. That makes sense. I mean, why reinvent the wheel, if you can just take the wheel and add to it, or make it faster, or something? I'm not saying that in any way that Microsoft or the folks that you work with, are using old code for the sake of using old code, but what I mean is: why recreate it, if it already works and you can do a little bit of work to maybe tighten it up or make it faster or something? Absolutely makes perfect sense.

**Michal**

And especially if you look at a project like CLR it's a huge project that has, I don't know how many lines of code but it's a huge amount. You know, all those years of bug fixes, and and all those investments like it's a solid piece of technology at this point.

**Jamie**

Absolutely. I can imagine that especially from my point of view, the projects that I've worked on, compared to CoreCLR or pretty much anything that you may have worked on, or Microsoft have created in the past, the stuff I've worked on has been tiny three months, six months of work. And a project is ready for someone and you ship it, and then no one ever touches it again. So I can't even imagine just the sheer number of lines of code that are required, just to get something that's the very basic setup so [that] you can print the words "hello world" on the screen. It just boggles my mind.

So yeah, totally makes sense. Why spend a huge amount of resource on re-implementing the exact same code again, with all of those bug fixes when it already exists?

**Michal**

Yeah, that's right.

**Jamie**

And you're not speaking directly for Microsoft. this is your experience sort of thing. At least I assume you are. I like to throw that in because I don't want you to get in trouble. I don't want the listeners to misinterpret what you're saying, this is your experience, your interpretation of the things that you've seen happen. These events and things like that, and the history of .NET and the stuff that you've worked on and things like that. So just like to throw that out there so that we don't get people saying, "well, Michal says it works this way." You know, I'm not speaking to you as a voice of the company, if that makes sense.

**Michal**

Yes, I'm definitely not talking here as a Microsoft employee. I'm just a .MET enthusiast.

### Hacking Around with the CLR

**Jamie**

Just a little background, I got into contact with yourself just after I'd read [that wonderful blog post where you made snake in .NET, and produced an eight kilobyte binary](https://medium.com/@MStrehovsky/building-a-self-contained-game-in-c-under-8-kilobytes-74c3cf60ea04). For anyone who's ever actually done `dotnet build` and had a look at their binaries and supporting files, you should see that that is absolutely amazing. Would you mind telling us a little bit about that and like what made you want to do that? Why go through the effort of seeing if you could get an eight kilobyte binary, and all of the research you'd have had to have done to get to that point?

**Michal**

I like to think about the stuff that I do in my spare time as helping C# to realise its full potential. Because when you look at C# and the language itself, it has a really great mixture of low level constructs and high level constructs. So at one side you have pointers, and you can write blocks of unsafe code, and access memory, and kind of do things that C developers normally have to do. And on the other hand, you have async and you have, I don't know, interfaces and all the other things. You have a garbage collector, that's another great thing. You have array bounds checks, and those things. You can write really safe calls and be really productive on one hand, but on the other hand if you want to go down and get the maximum out of the hardware, C# allows you to do that.

So when I'm experimenting with these things like that the snake game, I'm just trying to unlock what is already there in C#. Because often times people say that. oh, C# is not a systems programming language as Go is a systems programming language." But both languages are kind of very similar. C# is just better, C# has more stuff, but if you don't use it, you can go down to the sizes that Go has and you can go down to the memory usage that Go has. So that's kind of what I was playing with when I was in the snake game. So the reason why it was maybe so challenging is that .NET, or C#, is traditionally a VM based language. So when you compile your C# code, the result of it is something that you cannot directly run on any computer, because it's something that is called byte code: it's instructions for a processor that doesn't actually exist. It's something abstract. And in order to run, or to interpret that kind of code, you need a virtual machine. So a virtual machine takes the output of the C# compiler, and kind of makes it possible to execute the semantics that are in there, the instructions. So if you write a C# game, the output will be relatively small, but you need a huge virtual machine that has a garbage collector, that has [a] just in time compiler, that has all the class libraries that you are using. And the end result will be something that is big.

But if you say, "Okay, I don't want to use all those things that .NET is offering, I would like to restrict myself to the subset that is low level." What can be the result of that? Like, can the size be comparable to if I was writing it in C? And The result of my experiment was that, yes. Like, if you restrict yourself to that subset, the result will be really the same as if you wrote it in C. And so the question is, "okay, why would you even do that? Why would you restrict yourself to a subset of C# that is kind of like C because then you could just write your programme in C?" And the answer is, "basically, if you are a C# programmer, switching to C has overhead," like, if you switch from C# to C, then you have to start thinking, "Okay, how do I write unit tests for this thing? I know [xunit](https://xunit.net/) from C#, but what's the equivalent in C? How do I find out what is the code coverage of the game logic that I wrote? What's the tools on the C side for that?" if you stick with C# for these things, you are still using C#, it's just you're using a subset of C#. But all the tools that you have for C# language are available to you. So even though you're writing something low level, when you want to test it, you don't need to be restricted by those low level restrictions. Because you are only targeting the result, you only want the results to be small, you don't care that when you are testing the app, it has 50 megabytes or hundred megabytes because it has to carry the whole virtual machine with itself. Yeah, that's what I was trying to see. If that makes sense.

**Jamie**

That makes perfect sense. It shows the difference in the amount of knowledge and experience that you have versus what I have. In that I'd have never thought, "hey, let's reduce everything down and go to a C level thing and see if we can produce the smallest binary possible."

Reading through [the article](https://medium.com/@MStrehovsky/building-a-self-contained-game-in-c-under-8-kilobytes-74c3cf60ea04) there's talk of, "Yeah, if I use this linker and implement fake implementations of things. So like, here are a bunch of structs, which represent the built in types, which then reduces the requirement of having to pull more of the runtime and just all of that stuff." It clearly shows that you work on this on a daily basis.

**Michal**

Yeah, of course, that eight kilobyte version of the game was kind of extreme. But when I was writing the article, I tried to write it as a journey. So we started with the 65 megabyte version of the game. And then we used [IL linker](https://github.com/dotnet/core/blob/master/samples/linker-instructions.md), which is something new that is shipping with .NET. Core 3.0 that lets you remove the parts of the framework that you're not using. So kind of by default, if you build a self contained game in C#, it will include support for, let's say, WCF. The game is not using WCF, so why [are] those libraries are part of the game?

So IL Linker can look at what the app is actually using, and can remove the libraries that are not in use. So you don't use regular expressions, why ship them? You don't use Linq, why ship Linq? So that part is something that anyone can try and use right now. Like if you are a .NET Core developer, you can use IL Linker to make your app smaller. The next step of the journey was to have a look at an experimental runtime that Microsoft has. And this experimental runtime is specialised for ahead of time compilation. And it compiles only the parts of the app that are used. And that also applies to parts of the runtime. So if within the runtime you don't use, let's say reflection, you don't actually have to compile it into the app. These kind of levels of what's available to you , that's what I find pretty interesting. Because you start with all of .NET, like everything is available to, you have a really comfortable development experience. But the result might be not so small as it could be, what you're getting in return is acceptable activity. And then you can say, "Okay, what are the things that I can sacrifice to get something more?"

**Jamie**

I know that in node, there's an idea of [tree shaking](https://webpack.js.org/guides/tree-shaking/) to get rid of the API calls and the parts of the libraries you're pulling in that you're not using. And that's effectively what you're saying, isn't it? The IL Linker will go through your code and the bits of the runtime that you're relying on, and just ship the bits that you rely on. Do you know whether they extends to libraries? So for instance, if I pull in [json.net](https://www.newtonsoft.com/json), which is famously and 11 to 15 megabyte NuGet package, if I do that IL Linking and I'm only using `Deserialise<T>` will it recompile json.net? So I just get that, or is it just my code and the framework?

**Michal**

IL Linker can do that, but it's not enabled in what was shipped in .NET core 3.0. The problem with removing unused parts of apps is you can inspect an app and see all the methods that get called, all the types that get activated. And you could build a really good picture of what is used. So you would think that you can start removing methods, and you can start removing types and apps will still work. Nut the problems is that .NET has reflection, and reflection is a component of .NET value can a text string, and the text string has a type name in it. And you can call the `Type.GetType()` API with this text string, and you will get a `System.Type` instance back. And this `System.Type` instance lets you do stuff with it like, "oh, make a new instance of this thing," or, "find me method with this name and then invoke it with these parameters." The thing is that this is really difficult to analyse, because the text string could be literally downloaded from the internet. So if you are trying to remove unused parts of the programme, you don't really know which parts are unused because the app can just do reflection and take a text string and find something that was never used within the app. And if the thing was removed, this reflection call will fail. [The] .NET team has been playing with this for a really long time, and there is no good solution for this. The real problem is that that .NET has design constraint reflection. And because of that, you don't really know which parts of the app are unused.

**Jamie**

That makes sense. At runtime, your app could contact a server and the server goes, "hey, it's Tuesday, I want you to use a string." "Hey, it's Wednesday, I want you to use a linked list." "It's Thursday, I want you to use this particular type that you've downloaded from the web called Jamie's special object." And when you're compiling, you don't know that ahead of time, so I totally get that.

**Michal**

Yeah, even the very conservative way of removing unused code that is in use in .NET Core right now, if you enable IL Linker, it can still break apps. Even though really like you're not removing individual types, we are not removing individual methods, we are only removing whole assemblies. But sometimes an app will call the `Assembly.Load()1 API with a text string that specifies the assembly that it would like to operate with. And if that assembly was removed, then this call will fail.

And we have also seen this to be a problem in unexpected situations. For example, serializers: serializers are notorious for using reflection to do things. So if you would like to deserialize something, for example, you have a piece of JSON and you would like to deserialize it. That's precisely what the deserializer is doing. It will look at the text string within the JSON will try to find a property or field with the given name on some type, and then it will try to kind of reflection set the fields to the value that the JSON specifies. The serializers sometimes capture the name of the type as well. And along with the name of the type you also need to know the assembly where the type is coming from. So the serializer will use the `Assembly.Load()`, or it will call `Type.GetType()` with some name of the assembly or like assembly qualified name. And even in that very conservative situation where we only removed assemblies that we thought that are not used, this would still break. It's really hard to find the right balance where we know that we only  removed code that is not used. And you don't have to worry about your app breaking if you start doing this.

**Jamie**

Sure, I totally get that. And in a real world example, from something that I worked on the last two years, is that we had an app that would read from a message queue. It would infer certain things based on the message contents. And then it would go and actually load a binary from disk using reflection using `Assembly.Load()`. It would literally do that `Assembly.Load()`, find this DLL, find this method within it, and pass this data in and this data will conform to some object that that particular assemblie's load method would expect. So in some instances, it would pass a string in some instances it would pass an object of a specific type like a custom object. Sometimes it would just pass an integer.

And yet, as an engineer of the IL Linker, that would be impossible to predict, it's not going to be possible to figure out that, "oh, yeah, this particular app called this particular name is going to look in this particular directory for a bunch of DLL files, it's then going to use reflection to figure out where the objects within that DLL exist, and where the methods exist. It's also going to try and create a bunch of instances of those objects and call this method which you don't know whether it exists." So absolutely, I totally get that it is a difficult problem to solve. And although I have a background in computer science that is way over my head, so I totally get why that's a difficult thing to solve.

**Michal**

You can get easily to being 80% correct. You can build analysis and you can try to guess what text strings the app will use and what types it will use. And we spend a lot of time building such analysis for .NET Native. But we never got more than maybe 98% right. So even you do deep analysis, and you are very conservative, but still 2% of our billds break, and they need to disable this removal of unused things within the app.

Sometimes I feel that it's kind of unfortunate that all the developers got conditioned to the framework being always available, and to using these patterns, because then it makes it harder for us as runtime developers to make things lean and small and efficient. These patterns for example, dependency injection engines, very commonly use patterns. They will just look at all the files on the file system next to the app that you're running. And it will just open all the assemblies look at all the types. Make a catalogue of like, "Okay, this type implements this interface." And then at some point, the app would say, "Oh, I would like to instantiate the thing that implements interface IFoo." And then the output consult this catalogue, and it would create an instance of an object and implements that interface on demand. This is really hard to support even in the modes that we are thinking about adding to .NET Core or we have already added.

### Party Like it's Windows 3.1

**Jamie**

You said earlier on that some people think that C# isn't a, I think the the phrase you used was a "systems language" and you compared it to Go. Whereas if anyone ever says that to me, I always say, "hey, go check out [Scott Hanselman's operating system that he wrote in C#](https://github.com/shanselman/TinyOS)."

**Michal**

Yes, we need as many of these projects as possible so that we can shift the public opinion to have the right idea of what C# is, or what is possible with C#.

**Jamie**

Sure. A lot of the projects that I've worked In the last 10/11 years in C# have been, "hey C# as a web server, right? So let's build a web server and do the web server things." But what's great about some of the work that you've had a hand in, and the work of all of your colleagues and the whole community is that: yes, it could be a web server, or it could be a desktop application, or indeed, it can run inside of the browser. Part of that IL Linking stuff is being used, I think, in the preparation for proper client side Blazor using web assembly. Which is just, it's crazy to think that we can load all of these details these binaries into my web browser. And I have this almost common runtime. It's brilliant.

**Michal**

Yeah, the web assembly is one of the cases where the size really matters because the smaller the page is, the faster it loads, and people don't like to wait for web pages. Even though I have seen some articles that are looking at how big the popular websites are these days. And if you just open a website like I don't know, maybe [bbc.com](bbc.com), and like how many megabytes of stuff it will load before the page shows up. But it's still the size matters even there, you want to optimise for as small as possible. So even what IL Linker is doing for web assembly, it will have to do the more aggressive thing. People might need to sometimes help the linker to not remove parts of the application that they actually use, [it's] just not visible because it's being used through reflection or some entire means.

**Jamie**

Sure. Just as a sort of cheeky silly comment on "look at how much data is loaded by a website." I mean, big enterprises like that. They want to track the users, right? They're not allowed to, but they want to track the users, which is why it loads 10s of megabytes of JavaScript, just to be able to do that.

**Michal**

Yeah, you have to download all the tracking scripts, but also you have to download all that useful content. You also want to make it small so that it's not like 10 megabytes of tracking scripts and 10 megabytes of useful content. So maybe we cannot make the tracking script smaller, but maybe we can at least make the useful content smaller, to give you a good information density.

**Jamie**

Sure. There's two ways that I do it:

One [is] don't include the tracking stuff. If you go to any of the websites that I've made for this show, or some of the other shows, there's no tracking involved. Because I really don't care. Most of the time, people will collect all this information and not do anything with it. And the second one is make sure that it is completely separated, don't have a dependency for your web app, for your website, to have the scripts loaded. Because the second that they are blocked inside of a browser using ad blocking techniques, somehow maybe it's inside the browser, maybe the DNS level. Soon as you do that the website is non functional. Just a little bit of friendly advice on website content.

But you touched on something earlier when we hinted at talking about Blazor: these constrained environments. And I know that's one of the things that you kind of have a passion for. In fact, one of the other blog posts I read of yours was, "hey, let's get C# running in Windows 3.1."

**Michal**

Yes, I like to play with the technology that we built. One of the technologies that I was involved with was the [CoreRT runtime](https://github.com/dotnet/corert). So CoreRT runtime is an experimental runtime. It's similar to [CoreCLR](https://github.com/dotnet/coreclr) or Mono, it's just doing things differently. So if you look at CoreCLR and Mono, both of them are virtual machines. So they are basically pieces of software that are there to help other software to run. But you build an app in C#, and the C# app once it's compiled, it's not able to stand on its own because it needs this abstract technical environments so that it can run: it needs a garbage collector, it needs Exception Handling support, it needs a bunch of things. The VM is there to support those needs, and to make the IL that is the product of the C# compiler to execute.

CoreRT looks at it differently. CoreRT tries to take the IL that the C# compiler produces, and convert it into native code that then can call into other libraries when it needs to do something special. So the special things could be, "I would like to allocate a new object." So the native code that the CoreRT compiler produces will have machine instructions for basically everything that you set in your C# programme that you would like to do. And whenever it needs to do this special thing like allocate an object, throw an exception, or perform garbage collection. It would call into a separate library that would help it to this task.

The funny thing, once you structure a runtime this way to kind of not make it a runtime but to make it a runtime library, is that you can provide your own implementations of these things. So you can say that allocating a new object will not do the thing that .NET usually does, but it will allocate a piece of memory on the managed heap and the garbage collector will track it. But maybe it will just allocate a piece of memory with [malloc](http://www.cplusplus.com/reference/cstdlib/malloc/), and the memory will never be free. So I was playing with these things. And then I kind of realised that if I can convert the C# app into something native that sometimes needs the help of a runtime, but most of the time, it doesn't, what are all the places that I can make C# code run on? So I made this experiment where I made C# code running and Windows 3.11. Because we've restricted ourselves to something that is easy to satisfy on Windows 3.11. Like, for example, you say, "Yeah, I don't want to use garbage collector, I don't want to throw exceptions, I just want to show a message box." The code generated by the native compiler that CoreRT has, will not actually have any calls until the runtime. So the output of the C# compiler will be a binary that kind of starts right there where your C# programme starts. And it will do a [P/Invoke](https://docs.microsoft.com/en-us/dotnet/standard/native-interop/pinvoke) into the show a message box, and it will exit. And it's as if no runtime was really involved.

If you wanted to do something similar with CoreCLR. CoreCLR also has an ahead of time compiler, but the outputs of the ahead of time compiler need at runtime because the operating system doesn't know what to do with them. The EXE that the head of time compiler of CoreCLR generates it not the standard format of executables that Windows knows how to deal with.

If you have a VM, the process always starts in the VM, and the VM loads the programme and then starts executing the instructions. If you have an ahead of time compiled version of .NET, the process starts with your code. And if it needs some kind of high level runtime service, then it will call into the runtime. If that makes any sense.

**Jamie**

Yeah, it makes perfect sense to me. I'm more impressed that you found a working system with Windows 3.1 on if I'm honest.

**Michal**

I actually got some bits from my [Visual Studio subscription](https://visualstudio.microsoft.com/subscriptions/). I was really surprised that I can get legally all those bits without stealing Microsoft software.

**Jamie**

I had to do something similar for one of the places where I used to work: One of the clients that I worked with had a requirement on a Windows 95 box and we had a full Visual Studio/MSDN/whatever it is licenses. You know where get access to the entire software suite? And I was digging around on there and it was like, "okay, which version of Windows 95 do you want?" And yeah, so you can just push a button and download an ISO ready to install on a machine or something, I was tempted to see whether I could use something like, I believe there's a tool called [Rufus](https://rufus.ie/), which lets you put ISOs on to USBd to make them bootable. And I was tempted to see if I could do that with a Windows 95 or Windows 3.1, and just see if I can USB Boot into something from way back in the day. ButI  didn't have the confidence in my understanding how it all worked.

I know that there are enterprises and there are systems out there that run on these constrained environments, perhaps the older operating systems, or perhaps IoT devices, or perhaps really specifically designed constrained systems for security reasons, for backwards compatibility reasons. So yeah, being able to - I don't want to say quickly throw some things together in C#, and quickly push some buttons because clearly reading through those blog posts and listening to you describing the process there, it takes a lot of effort. But being able to throw something together that will do something in C# land, or C#-like land on those constrained environments is, it's amazing. I don't think anyone back in 1999/2000 when .NET was still on the verge of coming out, and people were trying it out. If somebody would have said, "in roughly 20 years, you'd be able to run this on 3.1, or indeed run this on Linux or Mac OS, or on these tiny little single board computers you can buy for $25." It's amazing.

**Michal**

Yeah. There is actually a company, it's not Microsoft, and they are looking into making .NET run on these microcontrollers again. So they are actually using Mono, or a stripped down version of Mono, to let you run .NET Standard 2.0 compatible software on microcontrollers: Wilderness Labs. So there is actually company that is doing these things. So what I am doing is mostly just hacks, like it's definitely not supported or anything. But if you want to do something supported there is actually someone offering that.

**Jamie**

Yeah. Is that the [Meadow](https://www.wildernesslabs.co/meadow) board?

**Michal**

Yes.

### .NET Back Then vs .NET Now vs .NET Tomorrow

**Jamie**

It is crazy that .NET has become this thing. I remember. Satya Nadella was doing a talk somewhere. And it said:

> .NET: write once, run anywhere

and it is literally true.

**Michal**

Yeah. If you look at .NET maybe, was it 10-15 years ago? There were actually three Microsoft and runtimes: one was the big CLR runtime that ran on desktop machines. Then there was the compact framework, which was for [Windows CE](https://en.wikipedia.org/wiki/Windows_Embedded_Compact), or you could use it for embedded scenarios. And then there was the micro framework which was even smaller and and it ran on microcontrollers. You basically didn't need an operating system to run .NET code because everything was kind of packaged together.

Like those two projects kind of phased out, because I guess the compact framework became less relevant when the chips started to be more smart. The middle tier became the higher tier, or kind of the higher tier became the middle tier. You can now run .NET Core on the $20 boards. You no longer need to put Windows CE and compact framework on it, because it will just run the full thing it's powerful enough for that. Yeah, the micro framework, I think there are still some people who are investing in it and are playing with it. I think that it was [open sourced](https://netmf.github.io/).

**Jamie**

That makes sense. Again, if you've spent some time and engineering power building something, and it could prove useful to someone, why not let the community take over and see if they can build something with it? Or indeed use it just to learn how to build a micro framework.

**Michal**

Yeah. Although when you are using the Micro Framework, then you also have to write the code differently because not everything is available to anymore.

**Jamie**

That makes sense.

**Michal**

But it's nice that you can write a piece of C#, and test it with xunit, and then put it on a microcontroller, and it will just work.

**Jamie**

It really is. I do remember the first time that I built and ran something on my Raspberry Pi 2. [It's] just sitting around doing nothing now, because I have a whole fleet of them. I've got so many in my house today, three or four of them are in use. But the rest are just in a drawer somewhere, as is the way. I'm sure you probably have bits of hardware that you experimented with and then sort of put to one side.

**Michal**

Yeah, my Raspberry Pi is now blocking ads. And it works as a Secure Shell server if I need to do something on Linux-y.

**Jamie**

Yeah, I've got something similar. I've got one set up connected to my router that is running [Pi-hole](https://pi-hole.net/), and it just blocks ads and tracking at the DNS level. I've got one in the living room that's a home theatre PC. I've got several across the house that are connected to speakers. And you just pull up an app that I've written - it's a very low quality Xamarin app that only works on the Wi-Fi - and [it] connects to the devices using some DNS magic that I borrowed from the internet. And you could be in the living room and push a button, and it will play Bohemian Rhapsody or something; or you can be somewhere else in the house and connect to the one in the living room ,and play Bohemian Rhapsody. So there's a level of trolling involved in my house.

But what I'm getting at is the very first time that I was able to compile something on my Mac OS laptop and push a button, and it be transferred over to the Raspberry Pi. And I had this Raspberry Pi connected to a 40 inch TV, and I had a little keyboard and I typed in `dotnet run` and it said, "Hello, World!" And that was a magical moment for me.

**Michal**

It's kind of amazing how this kind of computational power became available in such small and cheap form factors. Because if you look at the RaspberryPi like, it's a pretty powerful computer. 20/25 years ago, you would have paid like $2,000 for it, and it would be huge, take up a lot of space, a lot of electricity. And now you can have five, and it's easy to just have one to do one task and then another one to do another task.

**Jamie**

It really is. It's absolutely amazing. It's a testament to the hardware and software involved. And now that they fixed the kernel issues, the Raspberry Pi 4 is able to run as a full desktop environment with multi monitor support. You know, and that's a $25 computer.

**Michal**

Yup.

### CoreCLR is Experimental, But Creates Native EXEs

**Jamie**

We've strayed slightly off of the topic of .NET. You've mentioned CoreRT a number of times. I don't think - obviously when I come to transcribe this I'll prove myself wrong. But I'm not sure that you've mentioned that it is indeed experimental, at the time of recording.

**Michal**

Yes. I think I said it, but it's good to stress it more

**Jamie**

Sure.

**Michal**

CoreRT is an experimental runtime. It was kind of put together from multiple shipping pieces of technology that Microsoft has.

When you look at CoreRT, it's based on .NET Native. Which is something that has been powering the Universal Windows apps ever since Windows 10. They kind of couldn't make .NET Native, as it was, it was open source. Because .NET Native uses UTC as the code generator. UTC is the the backend that [the] C++ compiler uses to generate code. So when you're building a .NET Native app, it gets compiled into native code using the same code generator backend that visual C++ uses. So it applies all the crazy optimizations that C++ does. So when we were thinking about open sourcing that we knew that we wouldn't be able to open source the UTC backend.

So we looked at CoreCLR. CoreCLR has [RyuJIT](https://devblogs.microsoft.com/dotnet/ryujit-the-next-generation-jit-compiler-for-net/) as the code generator. It's a pretty solid code generator for managed code. So we took the runtime from .NET Native, and the class libraries from .NET Native, and we mixed it together with RyuJIT from CoreCLR. And that's how CoreRT came up.

It's basically the experimental ground for us to look at full ahead of time compilation. I like to use it for my side projects and for my experiments, because .NET Native executables that that generated by it are the same executable as you would get from a native compiler. So if you write a C app and compile it to native code, you get an exe that the operating system understands - like the operating system knows how to load it into memory, how to start executing instructions in it. It's different from the executables that Mono has, that kind of need a runtime to kind of load them first, and then they can start running the code that is contained in those files.

Yeah, it's a really good runtime to play with, because it has a really small core, and then it builds on top of that. So of course, you can run ASP. NET with CoreRT as well. It's just that's not the things that I play with in my spare time.

**Jamie**

You see, we've talked a lot about .NET things, obviously because it's a .NET related podcast. But I have a feeling that some of the stuff we've covered is very documentation and computer science-y related. If I wanted to play with CoreRT, is there a public branch that I can use? Is that something that I can try out? Or is it just literally, "hey, here is this thing we're working on that's not quite ready for even a public experimental phase"? Is this something I can access?

**Michal**

Yeah. So there is [the CoreRT repo on GitHub](https://github.com/dotnet/corert). And there are instructions [on] how to try daily builds. There is a feed published, and we have daily builds. And daily builds contain the ahead of time compiler and the runtime. And the way you use it is actually really simple. You just reference a NuGet package, and then you run `dotnet publish`. And magically, instead of the app getting published with [the] CoreCLR runtime, it will get compiled ahead of time with the CoreRT compiler, and packaged into the Publish directory for you.

So if you want to play with it, it's really easy.

**Jamie**

I like when things happen magically. It's always a good thing. I just push a button and it happens. The first time you do something new, you want to lower that barrier to entry as far as possible. You want to be able to just a push a button and magic happens.

You mentioned about how there's lots of technical detail as to how it works. If I want to play with it, and I want to understand a little bit more about what it's doing, do I need to know a lot of computer science-y things? Or is this more just a case of, "don't worry about it, we'll handle the minutiae of how it works?" When I was reading through your blog posts, and listening to now talk about how swapping out the runtime and implementing your own versions of things: so like with the snake game, there's a point where you say, "oh, yeah, it's fine. I'll just implement a bunch of stuff for the framework. It won't do anything. But here's a bunch of classes that represent the built-in types." How would someone go about learning all of that? Is that just because you have the actual experience of building tools and the CoreRT, and you have the experience of working with the runtime, or is that is that something that people can just learn?

**Michal**

I definitely wouldn't expect the regular .NET developer to try to do these things. The thing that I like about the CoreRT codebase is that it's pretty accessible, because most of the code there is written in C#. Okay, so if you look at Mono or CoreCLR, it's a huge C or C++ codebase with like templates and macros, and all that stuff that comes with C and C++.

The CoreRT codebase is mostly written in managed code. The pieces that are in native code is the garbage collector - because it's using the same garbage collector as CoreCLR code generator, because it's using the same code generators, CoreCLR - and then a couple small things like that supports the garbage collector. So for example, stack walking, which is something that [the] garbage collector needs to do [in order] to find out, "what are all the objects that are being used?"

But besides those things, pretty much everything is written in C#. So, if you would like to see how typecasting works, the typecasting is implemented in C#; if you want to see how Exception Handling works Exception Handling also is mostly implemented in C#. If you are a C# developer and want to get into the internals of those things, the CoreRT codebase is really accessible for that. If you want to look for it in CoreCLR or Mono then you have to understand C [and] C++; might be easier to see it on the CoreRT side.

Of course, the implementation of these things is not [in] idiomatic C# code. Because if you are implementing typecasting in C#, you obviously cannot cast types within the typecasting algorithm because you will get recursion: how will [you] cast types if you are implementing the typecasting algorithms? Or if you are the exception handling, you cannot throw exceptions because then who is going to handle those? It is still C# code and it's pretty readable.

**Jamie**

Okay. So you don't necessarily need that theoretical background. As long as you can read the C# code, and the documentation you'll get an idea of how you might go about implementing this, and how it all works. But like you say, it's not idiomatic. So there's some parts that are just, "we do this this way, because we have to do it this way. Versus you should do it this way." That kind of thing.

**Michal**

Yeah. For a long time, I was even thinking that, "oh, it would be cool to have a garbage collector written in C#." And that would have the same constraints that if you are implementing a garbage collector in C#, and you cannot allocate any managed objects from within the garbage collector codebase. Which means you can't throw exceptions because to throw an exception, you have to new it up first. You can't allocate arrays, because arrays are managed objects. The way CoreRT is structured would allow even a garbage collector to be written in C#, if we wanted to do the exercise and kind of sink lots of work into something that already exists, and it works well.

**Jamie**

It's that same point that we've brought up a few times of: why reinvent the wheel. If there's something that already works and works really, really well then why spend a bunch of engineering time on creating something that already exists? It's the same reason why we have NuGet. We mentioned [json.net](https://www.newtonsoft.com/json), and the new [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) libraries, but why implement a JSON serializer and deserializer, if one already exists?

**Michal**

Yeah. You can always find the reason to implement those things. It's just then you have to explain to management or explain to your wife why it's worth to spend time on those things.

**Jamie**

Yeah, that's always the interesting one, "hey, I could go out to dinner with you. But I've got this really great idea of: I implement this in this way, then it will be a lot faster. And I'll get loads of internet points, which are absolutely useless, but people will really like it."

**Michal**

Yeah.

**Jamie**

Because CoreRT is available on GitHub. I'm in no way smart enough to do this. But if I spot something, go, "oh, hey, I think I can maybe fix that, or maybe make that a little bit more interesting." Is it pull requestable? Can I submit issues, that kind of thing? And obviously, it's experimental. So don't submit an issue of, "I built this app using reflection. And now it doesn't work because I use CoreRT," because we've already just said, "reflection doesn't work." But is it collaborative? Can I create a pull request? Can I submit issues that kind of thing?

**Michal**

Yes definitely. We had a bunch of people trying to help with things last year, or two years ago. There were some Samsung engineers that were working on the C++ code and backend CoreRT, which is an experiment within the experiment of CoreRT.

That experiment is basically trying to translate the apps into C++ code, like C++ source code: You feed it a compiled assembly output of the C# compiler, and then the CoreRT ahead of time compiler runs it and produces C++ code that do[es] the same thing as the C# code did previously. And it will link it together with the CoreRT runtime. They were working on that a little bit. They added support for reflection. There is someone who is trying to add support for webassembly to CoreRT. So there is some community activity as well and we are trying to help if we can. Of course, CoreRT is nobody's full time project. It's kind of just a side project that we are doing at nights or over the weekend. Kind of don't expect immediate answers. But we are trying to help other people experiment with it as well.

**Jamie**

Sure, that makes perfect sense. Because if it is something that you're not working on as part of your full time thing that Microsoft are paying you for, then yeah, you're not going to be able to just drop everything you're doing and rush over to GitHub to respond to an issue or something. But like we said earlier on, it's experimental. So if it doesn't work, or if your code base doesn't work in it, then don't start complaining immediately. Because you know, it's not quite there yet.

Okay, what about yourself, then if listeners want to keep up with the work you're doing and on this particular thing, or learn a little bit more about how to get in contact with you? Is that something that you are okay with, like, is there - I know there's a Twitter and our blog, but is that the best way for folks to get in contact?

**Michal**

Yeah, I think that [Twitter](https://twitter.com/MStrehovsky) works the best. I recently got into the Twitter thing and I opened my direct messages. So it's probably the easiest way to get in touch with me. And of course, like opening an issue. either in the .NET runtime repo or CoreRT repo, depending on what is the area of interest, I might see that I look at those things.

**Jamie**

Brilliant. I mean, that's really all the questions I've got. Thank you very much for taking time to talk with me. I do want to say just one more time, though, just for listeners that whilst I am chatting to you about CoreRT and .NET stuff, and whilst you do work from Microsoft, I didn't approach you in a, "let's talk about what Microsoft are doing." I'm talking about what you are doing sort of thing. So in this discussion, you're not representing Microsoft, you're not saying anything that Microsoft, I mean, if you are saying stuff that Microsoft has told you to say it, and that's fine. But this isn't a public statement of what your employer are doing. This is what you're doing.

**Michal**

Yes. Like I said, I am here as a .NET enthusiast that happens to work at Microsoft.

**Jamie**

Sure. I know that I'm going to have to listen to this one a few times, and not just during the edit and the transcription, but to take it all in. So there's a lot of information in this episode and I thank you so very much for that because this is why I started doing the podcast: I get to speak to people who are way much more smarter than I am and figure out what I need to learn.

**Michal**

It's not about smart-ness, it's about the experience. For me, it's seven years with .NET. I know how things are implemented. So anyone can learn these things. If they spend seven years.

**Jamie**

I do remember a quote, I can't remember who it's attributed to but, "anything that can be understood by one human is understandable by another."

**Michal**

Yes.

**Jamie**

Well, like I said, thank you ever so much.

**Michal**

Yeah, thank you for the opportunity to talk about stuff that I like to do.

### Wrapping Up

That was my interview with Michal Strehovský. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/), and there will be a link directly to them in your podcatcher.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Michal Strehovský on twitter](https://twitter.com/MStrehovsky)
- [Building a self-contained game in C# under 8 kilobytes](https://medium.com/@MStrehovsky/building-a-self-contained-game-in-c-under-8-kilobytes-74c3cf60ea04)
- [xunit](https://xunit.net/)
- [Using the .NET IL Linker](https://github.com/dotnet/core/blob/master/samples/linker-instructions.md)
- [Tree Shaking in webpack](https://webpack.js.org/guides/tree-shaking/)
- [TinyOS](https://github.com/shanselman/TinyOS)
- [Michal's Twitter thread on running C# in Windows 3.1](https://twitter.com/MStrehovsky/status/1215331352352034818)
- [CoreRT Runtime](https://github.com/dotnet/corert)
- [CoreCLR](https://github.com/dotnet/coreclr)
- [malloc](http://www.cplusplus.com/reference/cstdlib/malloc/)
- [P/Invoke](https://docs.microsoft.com/en-us/dotnet/standard/native-interop/pinvoke)
- [Meadow from Wilderness Labs](https://www.wildernesslabs.co/meadow)
- [Windows CE](https://en.wikipedia.org/wiki/Windows_Embedded_Compact)
- [.NET Micro Framework](https://netmf.github.io/)
- [Pi-hole](https://pi-hole.net/)
- [RyuJIT](https://devblogs.microsoft.com/dotnet/ryujit-the-next-generation-jit-compiler-for-net/)
- [json.net](https://www.newtonsoft.com/json)
- [System.Text.Json](https://www.nuget.org/packages/System.Text.Json)
- [Michal on Twitter](https://twitter.com/MStrehovsky)
