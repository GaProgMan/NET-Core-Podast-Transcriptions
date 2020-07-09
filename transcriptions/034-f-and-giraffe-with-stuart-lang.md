# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is episode 34: F# and Giraffe with Stuart Lang. In this episode I interviewed Stuart about F#, Giraffe, the SAFE stack, and whether you should contemplate using a functional paradigm for web development. Some of you may know Stuart from his work on his website at [stu.dev](https://stu.dev), or the events [DDD southwest.com](https://dddsouthwest.com/), [F# Bristol](https://www.meetup.com/FSharpBristol/) and [.NET Southwest](https://www.meetup.com/dotnetsouthwest/) - all of which he helps to run.

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Stuart's Introduction

**Jamie**

Thank you ever so much for being on the podcast Stuart.

**Stuart**

No, thanks for having me on. I very much appreciate being on the show.

**Jamie**

Fantastic. You're very welcome. very welcome. I always like to hear from as many people in the community as possible, because, I mean, we're about to talk about something today that I have no idea.

**Stuart**

Yeah.

**Jamie**

Previously would I've talked to people it has been, "oh yeah, I have, I have an idea what Xamarin is, and I know what ASP.NET Core is, and I know what the middleware pipeline is," but I have almost no idea when it comes to F#, functional programming, or Giraffe or any of these things. So you're going to be my expert today.

**Stuart**

Cool.

**Jamie**

Excellent. Okay. So I just thought before we sort of start, I w as wondering could you sort of introduce yourself to the listeners, so we know you know a little bit about you and what you're all about?

**Stuart**

Yeah, sure. So, my name is **Stuart**


**Jamie**

Fantastic. That's a lot of stuff going on there. I can totally appreciate how busy that must be. I've only ever sort of partially attended meetups and a couple of DDD North events and the sheer amount of work that goes into organising those things. It's beyond my comprehension. So yeah, I really appreciate that potentially takes up a lot of your time.

**Stuart**

Yeah, thanks. I feel like on the DDD South West front, I sort of I owe it to the community because it was at that event that I kind of got my previous job. So this is just me sort of paying it back. So I've got so much out of and these podcasts as well. So anywhere I can sort of pay it back by do my bit. Yeah.

**Jamie**

I like it, it's it's so important to sort of pay back to the community and attempt to sort of help the people who are maybe just coming into the community, sort of get them up to speed or give them any kind of helping hand, or I totally agree with you on that one. It's very important to do that.

**Stuart**

Yeah.

**Jamie**

Excellent. Okay. So we're going to talk about F# and a little bit about Giraffe. I mean, I kind of hinted at them earlier on. But like I said earlier on, I have no idea when it comes to F# and functional programming. I mean, I know that there are Monads and that nobody knows what they are.

And I know that is it functional programming where you can't affect the global state, or you can't affect the state of variables and things like that? I mean, that's about the extent of my knowledge.

**Stuart**

Yet, there's a bit of a running joke with the whole Monad thing. And I won't try and explain it because in honesty, I don't fully understand it. But F#'s quite a pragmatic programming language in that there's different paradigms. So you can still do, you know, imperative programming and object oriented programming, but it's more focused on functional, you know, all the sort of academic things about Monads, and all that sort of thing to kind of get going with it.

**Jamie**

Okay, okay. So I can have say, I guess it would work similarly to C#, I guess. The syntax is a little different but I have an object, I call a function, I get a response.

**Stuart**

Exactly. Yeah. So I think a lot of people have that misconception, they, they think that F# is possibly some like Haskell or something where it's in a different kind of space, but really is just like C# and sense that it's multi paradigmed. So nothing stops you implementing interfaces. And sometimes, for example, if you're, if you're giving people a library, actually having interfaces and having classes, which are just a bit more easier to iterate on in terms of an API surface, sometimes that makes sense. But the wonderful thing is you you don't have to, you know, you can use whatever makes sense, you can use a functional style, or you can use an object oriented style if you need to

**Jamie**

Okay, so there's a possibility that I could be using or consuming a functional library, and I just don't realise because it's hidden behind an interface inside of a NuGet package for instance

**Stuart**

Yeah, exactly. So there's a couple ways like so I just explained as well, you can actually just, you know, have a mixed solution where you have C# projects sat alongside of actual projects. And yeah, you might have some people do it two ways, you can have a C# project, there's a very thin wrapper around your F# core code. Or you can kind of write your F# in a way that's exposed in a more C#, friendly way. And you can do it either way, the way you'd know is, if you look at the dependencies in your NuGet package, you'd probably have a dependency on `fsharp.core`. But that would be pretty much it would, you know, from consuming it, and there are libraries out there, which I can't think off the top my head. But there are libraries out there that are written in F#, but consumed in C#.

**Jamie**

Okay. I think that's one of the beauties, I guess, of the the base class libraries, as they were called in .NET Framewoork, the sort of Common Language Runtime is that you can have multi language projects and solutions, I guess, solutions rather than projects. I remember, at the time, there was a lot of C# and VB together. But I guess the lingua franca now would be C# and F#.

**Stuart**

Yeah. And sometimes I wish you could could just make it a little bit, you know, easier, just in the project be able mix in C# and F# files. But yeah. Nom, you can certainly mix solutions together, for sure.

**Jamie**

Well, maybe that's the future, maybe some, boffin at Microsoft will come up with a way of combining it all together. And we'll be good to go.

**Stuart**

Yeah.

### What is Giraffe?

**Jamie**

So we've talked a little bit about F# and functional programming. And how you don't really need to know that much about functional programming really to use F#. But when we said that we were going to talk about Giraffe as well. So I was wondering, could you give us a brief overview of what Giraffe is?

**Stuart**

Yeah, sure. So today, if you did to create a .NET core application, or an ASP. NET Core application, I should say. So if you say `dotnet new` and look at all the templates, you'll see that you have the F# templates there. So F# comes out of the box with .NET Core SDK. And you've got options there for like ASP. NET Core MVC, for example. So if you say `dotnet new --lang fsharp mvc`, you'll get a new MVC application all written in F#, and that's great. But It'd be a shame to, to want to build a web application and not take advantage of all the things that F# offers. And so that's where there are web frameworks built in F# for F#. And that's where those fit in. So that's what Giraffe is.

Giraffe is an open source, web application framework. And it sits on top of ASP. NET Core very much like MVC does. And it has a different composition model, which it borrows from Suave, which is another F# web framework. And it's really quite nice. So if I would describe how a Giraffe application works, you, you can put your application out these things called HTTP Handlers. And you sort of compose them all together. And a HTTP Handler is effectively, the way I would say it to C# developers, it's a sort of ASP NET Core middleware on steroids. So it's very similar, if you look at the signature of a, an ASP NET Core middleware. And it only varies in a subtle way. That means that when you compose them together, rather than with middleware, you can only compose them one big sort of line, you can only say, you know, invoke with this one, and then the next and the next, you're going to this singular pipeline. In Giraffe, the handlers themselves can signal whether they succeeded or aborted. And that way, you can compose them in more interesting ways. You can say, if this one succeeded, then do this next thing. For example, if the user is authenticated, then show the admin only web page. But you can break it down even further than that you can have a handler just to check it as a GET request, and add another check that it is for certain, you know, route with the application. And then can also combine these handlers and say, if this route doesn't, doesn't succeed, and abort, then try the next one, the next one. So you've got this really kind of powerful way of expressing application by putting together what effectively are very high performing lightweight, HTTP middleware. But with a really sort of expressive model. That makes sense. It's hard to see without code on the screen. But yeah, that's kind of in essence, what what Giraffe is.

**Jamie**

Okay, I think, I think I get the ide. In my head that I have like a, maybe a finite state machine design. And each one of the nodes, I guess, could be one of the HTTP handlers, and request comes in. Is it valid for this one? No. Okay. Is it valid for that one? Yes. But now that we've done that, let's do some other function, maybe take the request and send it over to that HTTP handler as well. And then when that's done, if that fails, right, now, we can't do that. So let's go over in a different direction.

**Stuart**

Yeah, exactly. And what's really nice as well, is that the, the signature for the handler, so, you know, it's, it's relatively simple. And it's very easy to write. So it's just coding against the `HttpContext`, which, you know, most ASP. NET core developers know quite well already. So it's very easy just to, you know, use the context and do things like look at headers and headers and just kind of reuse the knowledge you already know. What's really nice as well is this Giraffe plugs in as you know, itself as a HTTP middleware. So everything else in the ASP. NET Core ecosystem, you can still take advantage of. So the team I'm in at the moment, we have identity server, and we can plug in all the authentication middleware like you would in a an MVC application, we can take advantage of all that stuff. And but still write everything in and compose thing in the way we like with F#.

**Jamie**

I like that. I like that being able to sort of mix and match, I guess, you know, the, there's this part of maybe MVC, that I that I would like to be able to do something in my app. But I also want to use Giraffe to handle of the HTTP handlers. I like that.

**Stuart**

Another area where it's quite nice is that because it's just like ASP .NET Core middleware, it does really well in benchmarks, so it performs just like middleware. When you got MVC in the mix it's doing a little bit more under the hood. So when you look at the [Tech Empower](https://www.techempower.com/benchmarks/) benchmarks, Giraffe comes out on top of MVC, which was quite impressive. And it'll be exciting to see when ASP .NET, Core 3 comes along, there's some massive performance gains that have been put in there in the last few months. And it should - everybody, including Giraffe, will get the benefit of that. So good to see.

**Jamie**

I like that too, when when the sort of base system gets improved, and you can leverage that in whatever your apps are really like when that happens.

**Stuart**
Yeah.

**Jamie**

So you mentioned a few things there. You talked about Suave, and how that's, I guess, another F# based - I don't want to say MVC, because I don't think he uses MVC does it?

**Stuart**

No, it's it's just so Suave is, it was an existing - so it's actually, it's a web framework and a server. So the history behind it is the guy who, who initially built Giraffe is called Dustin Morrison, and he built an extension to Suave that allowed it to be served on top of ASP .NET. Core. And he then realised, actually, there's an opportunity to make a whole new framework that kind of borrows the best bits from both worlds, and takes the kind of the composition model that's really nice in Suave, but use all the fantastic engineering of, you know, the ASP. NET Core team have done in ASP .NET Core. And kind of fuse those two worlds together.

**Jamie**

Okay. I like taking, like, like we said earlier, and taking the best of both worlds and sort of growing it together and making a better product.

**Stuart**

Yeah.

### SAFE?

**Jamie**

You mentioned off stream when we were sort of communicating beforehand, that there's this thing called SAFE. And I was wondering, could you talk about that and what the acronym means.

**Stuart**

So there's a stack called SAFE stack. So this is like a web, I guess it's a web stack acronym. So you know, there's [LAMP stack](https://en.wikipedia.org/wiki/LAMP_(software_bundle)), which is like - let's see if I can remember these - you know, Linux, Apache, MySQL, PHP. And you've got [MEAN stack](https://en.wikipedia.org/wiki/MEAN_(software_bundle)) for Mongo, and node and whatever else. There's out of the F# sort of ecosystem has emerged this SAFE stack.

So I'll start, I'll start confusing me with the A, which is for Azure, although you can deploy to other clouds. So that's really about the tooling that comes with SAFE stack. So I should say it comes, you can store it as a .NET Core template as well. And you can kind of pick and choose the bits you want. But by default, you'll get it will deploy to Azure.

And the F part stands for a project called [Fable](https://fable.io/). And this is a F# to JavaScript transpiler. And it's called Fable, because it basically is Babel, and it uses the F# compiler services to take your F# code and take the sort of typed abstract syntax tree and translate it into the syntax tree that the Babel uses. So then people actually use the thing that writes out the JavaScript. And so Babel means that you can write F# code and have it transpiled to JavaScript. So you can, you can have code on the server with .NET Core. But also you can share that code for client side. So you can have your models for example, being shared.

The E part of safe is, stands for [Elmish](https://elmish.github.io/elmish/), which is kind of built on top of Fable, because it's it's kind of you write your code and F#, but again, it runs in the browser. So Elmish comes from this architecture that was made popular by Elm, which is a client side web framework. And Elm made popular this, this more and more up and coming trend of this UI architecture of Model View Update. And the the idea with this is you, you have your model, which is basically the kind of state of your UI, you have an update function that takes a model and takes a message which could be is, you know, dispatched by the user doing some action. So you can think of as an event, maybe the user clicked on something. And it takes the model and it takes this message, and it produces a new model. So it's a very functional style of programming and that you're not mutating anything, you're creating a new model each time, and finally got the view part, which stands for the view. And that just takes the model and turns into a view. And depending on what sort of application model you're you're building for whether it's in this case, it's for the web. So what the framework will do for you is it will have some sort of virtual DOM implementation. So you know, in Elmish if you take the model and you map it to view, it will use a virtual DOM to figure out what the diff is and do that an efficient way. And under hood, it uses React for that. This is also made recently popular by another F# library called [Fabulous](https://fsprojects.github.io/Fabulous/Fabulous/), which is a Xamarin forms library, it does the same thing. And basically, when you get to the view part, you kind of map it to this virtual - I say virtual DOM, but it kind of looks a lot like the XAML markup of Xamarin forms. And it will, under the hood, figure out what the diff needs to be. And it will make the changes for you under the hood and kind of a stretch away from that and get to the really nice sort of functional model. And it's interesting to see that, I think Apple at their recent developer conference showed Swift UI, which seems like it's going down the same a similar style up but kind of a declarative UI, and a more sort of functional UI kind of paradigm. And so that that Elmish.

So you've got AFE and the S at the front stands for a web framework called [Saturn](https://saturnframework.org/), and Saturn is basically another framework on top of Giraffe. So Giraffe kind of makes ASP NET Core a bit more usable, for F# users. Saturn also adds a layer on top of that in terms of, it's a little bit more opinionated, a bit more structured, it gives you a bit more out of the box. But I personally haven't had much experience using Saturn, I know people like it, there's differences.  But in my experience I primarily use Giraffe. And but when you create a SAFE that template, you can kind of pick and choose what you want. If you don't want to use you know, Azure, for example, you don't want use - you have to pick between Saturn and Giraffe. So you can kind of pick what you want. And it's a really nice framework. It was on the on the [ThoughWorks Tech Radar](https://www.thoughtworks.com/radar). So it was under their assess ring a few months back now. So yeah, it's quite impressive. It has commercial support as well. So I think they called Composition IT offer commercial support for it. So it's not a sort of play thing. It's a really mature stack, you can kind of build really rich applications completely an F# end to end. It's really quite nice.

**Jamie**

You were saying that you could take the SAFE stack using the template and sort of swap parts out?

**Stuart**

Yeah, yeah. So when you do `dotnet new` and after you've installed the template and and you pick the SAFE site template - I forget the name of it. But yeah, it has a little wizard where it's like, oh, would you like to use Assassin or Giraffe? And it actually a few other questions. And it just you know, so you can take your pick.

**Jamie**

I see. So I could end up with - I'm just trying to work out the acronym now, just buying time - so you end up with a GAFE?

**Stuart**

Yeah, exactly. Yeah. And Christoph, who's the the guy who who built Saturn. He knew what he was doing, because before it was Saturn it was it was Suave. But for reasons, they decided they wanted to take a different framework. So he deliberately created it with a name starting with the letter S. But yeah, you could pick GAFE, and it wouldn't sound quite quite as good.

**Jamie**

I mean, we all know that naming things in development is hard, right? So why not start with something you already know?

**Stuart**

Yeah.

**Jamie**

I have heard of MVU and Elmish before but only in the context of Fabulous. So it was nice to get a slightly clearer description of what Elmish and MVU architecture are. Because, like I say, they've been sort of mentioned to me in passing. So it's nice to know that it comes from a from Elm and exactly the idea behind MVU, because I haven't had a chance to try it. But I think I might think I might see if I can create something that uses the MVU architecture.

---

### Sponsor Message

This episode is sponsored by {{< sponsor-link link-text="Rider from JetBrains" link="https://www.jetbrains.com/rider/promo/?utm_source=netcoreshow&utm_medium=cpc&utm_campaign=rider" >}}.

Have you heard about Rider, a cross-platform .NET IDE developed by JetBrains and based on IntelliJ Platform and ReSharper? If not, it's time to give it a try! Develop .NET, ASP.NET, .NET Core, Xamarin, or Unity applications on Windows, Mac, or Linux. Get Rider today at {{< sponsor-link link-text="RiderIDE.net" link="https://www.jetbrains.com/rider/promo/?utm_source=netcoreshow&utm_medium=cpc&utm_campaign=rider" >}} and try it free for 30 days!

---

### what About The Client Side?

**Jamie**

I'm interested about the Fable aspect. So I create my F# code to run on the server. And I have some kind of view model perhaps. And I could just during that build process, the stack knows magically that or maybe not magically. But the stack knows somehow that this particular F# model needs to be converted to JavaScript, or do I need to say, these models are JavaScript and will run on the client? Or am I mistaking what's happening there.

**Stuart**

So on the client side, there's certain code you can't run to be clear. So you can't just from your F# reference any arbitrary .NET DLL.

So it works at a language level. So it will take the F# code, and it will see when you're calling things from `fsharp.core` things like you know, all the primitive types, things like `DateTime` and the Fable of re-implemented in JavaScript, all of the sort of F# functionality you find just using kind of out of the box, F# code. There's other libraries, like for example, I think big int, or big integer, there's bits that people kind of commonly use that they've re-implemented. But you can't just go and grab some arbitrary DLL. There are libraries out there that are deliberately written so that work in both full framework or .NET Core and, Fable. For example, there's a serialistation library, I forget the name of it. But it means that you can use it in either setting, and it will just work. You want to use it for composing application and for dealing with you models and things like serialisation and HTTP calls.

That's kind of as far as it goes to some degree, you can kind of, if you call something in a third party library, and you you do want to kind of say, you want to get into the sort of Fable transpilation, say when you encounter this function, this method, rewrite it into this JavaScript, you can do that, but but generally, you know, you kind of moving out of the sweet spot of where that tool works.

**Jamie**

That makes sense. I like that, though, that you can almost automagically have part of your your code transpiled to JavaScript, because that's, you know, that's the bane of least from my point of view, if I'm doing something C# on the back end, and JavaScript on the front end of keeping those view models in sync is is always a pain.

**Stuart**

Yeah, yeah. And there are tools to do that stuff. And it'll be interesting with with Blazor and seeing how that changes things up. But from my understanding at the moment is that Blazor will kind of add a burden in terms of how much you're sending assemblies down the wire, and this kind of thing. So there's still is room for this sort of thing where you are delivering JavaScript that's been transpiled via by you know, somebody like TypeScript or some other thing, for example, F#. And the MVU acrhitecture is neally nice and quite addictive, once you got to grips and got into the pattern of adapting it, it's really quite nice. And you know, it's quite an addictive paradigm it and it's hard to move away from it's very testable as well.

So I didn't mention is that because it's very functional. The update function, for example, is a pure function, in that it doesn't touch anything else, it just takes a model and a message and gives you another model. So you know, a lot of unit testing, when you're doing object oriented code is getting classes into the right state to be able to exercise the right code and right way. But here you've got something where you just hand it the model when it's, you know, the original state, and then check the output once you've put it for your update function. So that's really, really nice. And a lot of these frameworks as well allow you to test the virtual DOM layer that they implement. So the same is true for Fable you can - there's in the samples, so you can see how you can test it in a more thicker, just under the surface kind of way, which you sort of miss out on I think we don't use this paradigm.

**Jamie**

There's something you've said there that I really like, that you don't have to get, like you said, get your C# objects into the right state to begin with. Because with MVU, you're just literally saying, hey, model is the update function. Give me the model back. I like that.

**Stuart**
Yeah

**Jamie**

You see that was going to be one of my questions about the SAFE stack if you swapped Saturn for Giraffe, and Fable for Blazor, you would get the GABE stack.

**Stuart**

That would work that would work. Yeah, that could have been quite nice. I actually have a little project that I'm working on that I haven't done anything with that is using Blazor with F#, and it's using Giraffe. So that would be a GABE stack. If I hosted in Azure, so yeah, there we are.

**Jamie**

Yeah, because I was going to ask Blazor worked with it because I mean, you said earlier on how Giraffe allows you to just take the bits from ASP. NET Core MVC, if you need them. And I guess, you know, Blazor is now part of ASP .NET, so you could just hook it up, do whatever wizardry you need to, like I say F# is not my forte. So you do whatever it is you need to do to bring in Blazor. And then it just runs on the front end, I guess.

**Stuart**

Yeah. And so the thing that ASP. NET Core team are working on Blazor, there's nothing in there that inherently doesn't work with F#. But I think there's some effort that has to go in, just to make it consumable. There's a library out there. I can't remember the name of it. That kind of does that and kind of makes it accessible to you in F#, and it works fantastically. So yeah, it's exciting times, definitely for a.net, developer C# or F#, you know.

**Jamie**

Definitely, I was talking to a friend of mine the other day about building some applications to deal with audio in the browser. And we said, Hey, why don't you just use web assembly and pull in a well known C library for doing all of that stuff and just build a wrapper around it?

**Stuart**

Yeah, that's the crazy thing. And that would that would absolutely work. So yeah, when you think of the possibilities. It's pretty mind blowing.

**Jamie**

It really is considering you can get almost anything to web assembly transpilers now.

**Stuart**

Yes. Yeah.

**Jamie**

I wouldn't be surprised if there was a Rockstar to WebAssembly.

**Stuart**

Yeah.

**Jamie**

So from what you've said, so far, it makes sense to me that maybe a functional viewpoint, or maybe using Giraffe fits really well, with web dev. At least web dev you know, I don't know about functional with everything else, because I've never really talked about it. But for you, is it a good fit? Is it something that you like, if somebody says to you, you can use whatever technology you want, are you torn between C# and ASP .NET MVC? versus F# and Giraffe? Are you happy to just go? We'll mix a match will do this and this and pull this thing in? And how does that fit with you?

**Stuart**

Yeah, I mean, for me, F# feels like a really good fit for the web. In particular, because the web is inherently functional: With HTTP request and response that's naturally a function. And that's kind of how ASP .NET Core models it. So it is a very functional. So that kind of, for me, it's a kind of a no brainer for the web side of things.

But in the other spaces, what's really fascinated me as I would never thought that the UI architecture, functional pattern or functional architecture would make any sense. But it you know, turns out with what Elm's proved, and then from Elm React, and and now everyone's jumping on it: this sort of model view update pattern is really a very nice fit. And no one, I don't think anyone really saw it coming: that sort of functional UI architecture would work so well. But definitely for the web. I would say, I've given talks before, and some people take a sort of from the C# or a defensive viewpoint of So you're telling me to rewrite my code, and rewrite everything in F#? Absolutely not, like I'm just enthusiastic about it. And I hope I can rub my enthusiasm off on people. Really forcing these sorts of technical language change top down, you know, within your team just won't work. You know, you need to build your applications and whatever your your team is excited about.

I would say that the team I've joined, the website that's built is built in Giraffe. And it was built by two developers who predominantly they were Java developers, and they've never touched .NET before; they've never touched ASP. NET before and an F# before. And with minimal guidance, they've done a fantastic job, and that they've just made it work. And it's not a trivial site, either. It's talking to a headless CMS, and, you know, putting in doing caching and putting in security headers and, and all this sort of gnarly real world stuff. And they, they just got on with it. And so often this is another thing people say is, oh, I'm, I don't want to make it harder to find developers, I have a hard enough time as finding C# developers. But I think more and more today, it's it's more of a case that you're just looking for good developers. And it's less and less about, I need a language x developer,

**Jamie**

Yeah, I think that's going to be one of the big things that sort of unifies, I know we mentioned .NET, and MVC, and all that kind of stuff, and Giraffe and all these things together. But I think one of the things that's going to happen over the next year or so when everything is unified to being .NET, rather than there being a .NET Framework, a .NET Core, a Mono, a Xamarin. And all of these hundreds of things when the unified to .NET: that's one of the steps that we can take to simplify everything. Like you say, you won't _have_ to say I need a developer with this language or with this technology will just be I want a developer who can do this.

**Stuart**

Yeah, absolutely. I was really happy to see them make that announcement actually. A little bit of me was sad, because it's really nice to be able to search for .NET Core. And your shows not .NET Core right?

**Jamie**

Yeah.

**Stuart**

So it has a knock on effect to the whole ecosystem. But I think it's an important message. Because right before the announcement, it kind of felt like Microsoft kind of almost abandoned the customers that I would say stuck with it - yeah, stuck with full framework. I know that really, it's mostly a marketing thing. And it's just .NET Core, but with enough functionality that they can stand up and say this is something you should move to from .NET. But I think it's an important one, I think a lot of the large enterprises were holding off and I think this is really the sign saying no, this is it. This is the way forward.

**Jamie**

Yeah, it makes a lot of sense. Like you say, for big enterprises where your work rate as a little less speedy, your cadence of putting out new features isn't as fast because maybe your IT department has to support the devices with older operating systems. And, you know, these are perhaps companies where they have a policy of, okay, IT installs the Windows updates, then checks the network to make sure everything's still running nicely. And then they'll roll it out to everyone else. And a lot of the places where I've worked as a developer, the development team have been admins throughout the system, which is not great. But you know, in enterprise, you can't do that. And it makes sense that the Microsoft are maybe signalling to the big enterprises, you know, now is the time, don't worry about it too much. And we'll sort of help you with the transition over. And I guess it makes it easier for looking for experts. Like I said earlier on about, you know, you don't have to advertise for a .NET Core developer or a .NET Framework developer, you just advertise for a .NET Developer?

**Stuart**

Yes. Yeah, exactly.

### Why F# over C#?

**Jamie**

I think we already covered this, but I'm going to ask anyway. So in your opinion, what are some of the maybe benefits and pitfalls of using F# over a C# in that sort of web space? Or other any? I mean, I don't know.

**Stuart**

Well, I think if you bought into F#, and you decide that's what you want to do, and one of the big compelling reasons to use F# is for domain modelling and, and the kind of correctness it gives you that and the, kind of, everything around that. And this fantastic book by Scott Wilson, called Making Domain Modelling Functional, that really sells this really well. And he F# code throughout, and probably the best advertisements for building applications in F#. But if you if you bought into I'm going to use F#, that's when you're going to want to say, you know, I want to build my web application with it, you know, not just your domain model. But there's nothing wrong with C#. I mean, I love C#. I'm quite excited by the features that are coming. So I didn't see them as replacements. And I want to say I don't see them as competing, but they are a bit, you know, in my heart for sure. Yeah.

**Jamie**

Okay. So would you agree, it's fair to say that it's just a case of: it's another tool in your tool belt, I guess. Another way of solving whatever problem. It could be that, you know, some of the code that I'm working on would be better served as a functional application rather than a declarative one, or maybe I'm not so good at C#, but I'm really good at F#, and I don't really need to do in a functional manner.

**Stuart**

I would say that, as you said, the tools in your tool belt. And I think don't know that, especially with web development, I don't know that there's a scenario where a lot of people says, oh, I'll use it when, when the problem comes up, that solves it, but it's like, you're building line of business applications. So it solves that problem. You know, it's it's a general purpose language like C# is, so I don't know that there's sort of a case for here and a case for that there.

I will say more, just more broadly speaking, sometimes it's nice just to have to follow the mainstream, right, the trodden path, because if you're using C# and MVC, you're going to have so much more resources out there immediately, you know, there's something to be said about copy-paste from Stack Overflow. Whereas, you know, you may find less examples in F#, for example, although they're out there. And you know, I'm pretty fluent in both. So it's easy for me to translate between those two things. But But some people prefer the trodden path.

Another sort of case around that particular framework is that with MVC, and this is inerrant to kind of the way that they're architected: MVC, because it's convention based, it's easy for them to be able to generate Swagger, for example. And so you know, you've got Swashbuckle, and you've got NSwag that you can plug in, and they will generate you either at build time or runtime Swagger - or open API, I should say - spec files, so that you can, you know, generate clients on the other side and whatever language you want. Whereas in Giraffe, that is one thing that's missing, the moment is, there isn't something you can just plug into and say, give me the Swagger for this thing I built, because of the architecture of it. It's not convention based. There's no kind of way of introspecting that the code is built to say, and what is this what is it mapped to in terms of routes, and sort of types, your inputs and outputs?

And that is something being looked at. And what we do in the team on working in is we we go with a contract first approach. So we start by defining our API's in Swagger with then build our Giraffe API's to that definition. And there is actually, in if you look at the Swagger Gen repo, there's actually a template for Giraffe. So you can just actually generate your server straight from the Swagger. We don't do that, but you can do it. And then we generate a client off of the Swagger file. And we use that to end to end test the application we built. And if it pops for any reason, we know that we haven't added to that Swagger. So we kind of use that contract, we kind of go contract first. And we treat it as the source of truth for the how the API is designed. And you can also doesn't have to be an end to end test to take advantage of that. You can, you can have it so that you generate that and you use test server and you use your type client and you inject your HTTP client, from your test service, everything's in memory, if you know what I'm talking about there.

You can kind of have it so that you're kind of proving that everything's lining up. But with a completely memory test, and you're completely functionally testing applications, that's really nice pattern.

**Jamie**

I like that. Maybe that's another thing for me to try: a contract based API.

**Stuart**

Yeah. But you know, we have found in places to be painful, and sometimes I wish that, you know, we make a change to the code and the Swagger comes off the back of it. But you know, it does require a bit more discipline and rigour to go contract first, because it's too easy in an MVC application, just a tweak the signature something, and suddenly the Swagger is now different. But maybe nobody really noticed, you know, you have to have measures in place, you know, or thorough code reviews to make sure you're not accidentally making breaking changes,

**Jamie**

I see. And, again, that's where your unit tests based on that contract with sort of step in and say actually, you've you've submitted a pull request, which breaks the contract, because you already have this suite of tests based on an older version of a contract.

**Stuart**

Yeah, exactly. Yeah, you just get, you know, it would just blow up with some serialisation error or, you know, how any consumer of your API would experience it.

**Jamie**

Okay, it's a lot better than some of the unit tests I've seen for some MVC stuff. And, like you're saying is because it's so easy to just change it, and then nobody knows until they run the front end. Oh, wait, your method is broken, because you were accepting an iun and now you're accepting a GUID or something?

**Stuart**

Yeah, yeah. It happens a lot.

**Jamie**

So where are the best places to go, in your opinion, where are the best places to go to learn a little bit more about Giraffe and the SAFE stack and things like that the sort of things we've covered today?

**Stuart**

Giraffe is... you can find it on on GitHub under [giraffe-fsharp/Giraffe](https://github.com/giraffe-fsharp/Giraffe). So there's an org there with a bunch of other sort of related plugins to it and different view engines and, and all sorts in there. But yeah, the Giraffe project is there. And it has a really good documentation markdown file. So it has one big file with all the documentation in which sounds odd, but it's actually really, really good. It's really concise well written. And if you just want to kind of get a flavour of what Giraffe is what it can do for you, if you just read that, and scan through the bits, you know, into the detail, but the first opening few sections, and that really kind of give you an idea about what it's all about. SAFE stack, there is a website for that, which is [safe-stack.github.io](https://safe-stack.github.io/). And if you just Google it, you know `SAFE stack` you'll find it.

**Jamie**

Okay, excellent. So what about yourself? Where can people go to find out a little bit more about you is, is Twitter a thing?

**Stuart**

Yeah, I'm on a few things. But if you go to [stu.dev](https://stu.dev), all my various links, for example, Twitter, they're all on there. So you can you can find me there.

**Jamie**

Okay, fantastic. So if they're open source projects, there's a GitHub link. And you know, people can contact you on Twitter?

**Stuart**

Yeah, I don't do as much as I should in the open source space. So I always feel a bit guilty. But yeah, I've got a couple of kids. So you know, they keep me busy. And yeah, it's hard to find the spare time.

**Jamie**

Oh definitely, definitely. I was just saying to a couple of my friends - James Studdart who runs the [Cynical Developer podcast](https://cynicaldeveloper.com) and Paul Seal, who runs [codeshare.co.uk](https://codeshare.co.uk) - I was saying to them earlier on today that they are building some wonderful side projects. I'm sitting here going, I have 17 hours of audio to get through before I could do anything. But you know, I do it for the love, you know.

**Stuart**

Well you're doing a great job.

**Jamie**

Thank you very much.

So I, you know, I completely understand how, you know, there's not much time in life, I guess, to do as much open source development as, you know, we may feel like we need to, or we should do, because it's all about the amount of time that you have the you can spare for your passion project. You know, that's the always the way I've seen it. If I have 10 minutes to go and learn Hugo, I'll spend the happily spend that 10 minutes going and learning Hugo. I mean, I'll build anything, but I may just end up reading through documentation. Or I might build something with Blazor and just throw it out there for people to look at and go this is how Blazor worked back in 0.3. Or this is how this works, or this is how that works, you know.

**Stuart**

Yeah.

**Jamie**

I think there's less to worry about at contributing to the community, especially for you because you're running these these events, you know, the DDD Southwest, and all of these different places that you're sort of helping to run an organise, and get people together with. So don't ever feel bad about not doing any kind of open source work.

**Stuart**

Yeah.

**Jamie**

So speaking of those just real quick before we end, then where can people go to find out about the events that you put on them? Like, like I said, it was DDD Southwest, wasn't it?

**Stuart**

Yeah. DDD Southwest, and that's [DDD southwest.com](https://dddsouthwest.com/). And there's [F# Bristol](https://www.meetup.com/FSharpBristol/) and [.NET Southwest](https://www.meetup.com/dotnetsouthwest/), which on meetup.com.

**Jamie**

Excellent. So just to confirm, then, the DDD events aren't domain driven design, are they? They're developer developer developer events.

**Stuart**

Yeah. Which causes a lot of confusion. I feel like I should qualify that every time I say it. But yeah, unfortunately, that is a loaded term now. Yeah, developer developer developers. There is like a DDD confor Europe, like DDD Europe conf or something like that. I always think, well, if they've done a Europe now, and then I'm like, oh no wait, that's the actual domain driven design thing.

**Jamie**

Yeah, that's the problem with acronyms. There's too many of them. We need to have fewer of them, which means we'll end up with more of them. Right?

***Stuart**

Yeah.

**Jamie**

Well, thank you ever so much for being on the podcast. I've learned a lot today about F#, and Giraffe. And like I said earlier about being able to understand what the MVU architecture is, and what Elmish meant. Because people kept saying to me is Elmish, I'm like, well, what's Elm? And they'd go, "go speak to that person."

**Stuart**

Yeah, no, thank you very much. I really, really appreciate it.

**Jamie**

Appreciate it. Thank you ever so much. Like I say it's, it's hard to spend time just talking to someone for an hour about something that you're passionate about, especially when you say you've got some little ones running around and, you know, so I really appreciate you taking the time out to talk to me.

**Stuart**

No worries. Thanks so much.

### Wrapping Up

That was my interview with Stuart Lang. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and a collection of text snippets from the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/).

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Stuart Lang on twitter](https://twitter.com/stuartblang)
- [Stuart's Website](https://stu.dev)
- [DDD southwest.com](https://dddsouthwest.com/)
- [F# Bristol](https://www.meetup.com/FSharpBristol/)
- [.NET Southwest](https://www.meetup.com/dotnetsouthwest/)
- [LAMP stack](https://en.wikipedia.org/wiki/LAMP_(software_bundle))
- [MEAN stack](https://en.wikipedia.org/wiki/MEAN_(software_bundle))
- [Fable](https://fable.io/)
- [Elmish](https://elmish.github.io/elmish/)
- [Saturn](https://saturnframework.org/)
- [ThoughWorks Tech Radar](https://www.thoughtworks.com/radar)
- [Tech Empower](https://www.techempower.com/benchmarks/)
- [Fabulous](https://fsprojects.github.io/Fabulous/Fabulous/)
- [Giraffe on GitHub](https://github.com/giraffe-fsharp/Giraffe)
- [safe-stack.github.io](https://safe-stack.github.io/)
- [Cynical Developer podcast](https://cynicaldeveloper.com)
- [codeshare.co.uk](https://codeshare.co.uk)
