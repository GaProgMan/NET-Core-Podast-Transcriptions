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

**Jamie**

So first of all, I just want to thank you Ed for being on the podcast. It's a great pleasure to have you on here. One of the great's in the long standing community drivers of Telerik, I guess is, is your podcast, the telric product or is it an Ed product?

**Ed**

Yeah, so I've been kind of in the community for about eight years now. And I joined Telerik about three years ago and started up the podcast as part of my job as developer advocate with Progress, or Telerik. We go by Progress now, but the brand Telerik is still there, but the company that was Telerik got absorbed by progress a few years back.

**Jamie**

Okay, so is it better if I refer to the company website or as Progress?

**Ed**

Yeah, it kind of confuses devs because we've been in the .NET space for such a long time as Telerik as a company. We got purchased three years ago my Progress and the company is no longer Telerik, but we still maintain that brand. People know it so well from us being in the industry for so long. But yeah, the actual company itself is Progress now. We've been in the space since the early early web forms days. And I actually was a customer years ago. So I kind of cut my teeth on Telerik tools is I learned my .NET skills. So it all kind of went together for me. So when I joined the company a few years ago, it really worked out was a nice fit for me.

**Jamie**

Oh, that's cool. That's cool. So if you don't mind Ed, for the incredibly small Venn diagram of people who may be listening to this podcast, but either have not heard of you or your podcast. Could you maybe introduce yourself and talk about your show a little bit?

**Ed**

Sure. My name is Ed Charbonneau. I'm a software developer, turned developer advocate a few years ago, I've been doing software dev for about 15 plus years now. Mainly in the web development space and done everything from full stack dev to, you know, UI design and all sorts of things. And now I spend my days working with the community as part of my developer advocacy with Progress. And I talk about front end web development with all of the .NET stack, and a lot of the JavaScript tools as well. So if you've seen me out in conferences and stuff, you've probably heard me talk about, you know, .NET and functional programming with .NET, and ASP .NET MVC and responsive web design and angular and all those fun web stack things that people love to use.

And currently, I have a podcast as part of my activities with Progress called "Eat, Sleep, Code." It's the official Telerik brand podcast. We don't typically have our own content on there, which is nice. It's very much a community outreach type of a show where I get to talk to awesome developers from all around the community. And we talk about the things that they're interested in and working on, rather than focusing on our own tools and things that we build. So it's a lot of fun to get to talk to those people and have them on the show.

And I'm also a Microsoft MVP for the third year now, which

**Jamie**

Oh, wow.

**Ed**

is phenomenal, because I don't, I don't feel like I deserve it. I don't know. One of those things that that just happened, and I'm very grateful to have it.

**Jamie**

Well, congratulations on three years, I guess.

**Ed**

Thank you.

**Jamie**

Definitely. I was at a local meetup to me. Last night, as we are recording this with an MVP called Ian Cooper. And he'd said, because he runs a .NET user group in London. And he'd said, something along the lines of, "I've been MVP 15 years, which means should be retiring and you'll actually be taking my place."

**Ed**

Yeah, it's amazing how fast 15 years goes by.

**Jamie**

Yeah.

**Ed**

It's like, I felt like I picked up .NET yesterday, and I'm still learning all the new things about it.

**Jamie**

Yeah, well, hopefully, this won't make you feel too old. But hopefully it doesn't anyway. But I picked up .NET when I was at university; our computer science course was in .NET, which, looking back seems a lot easier to deal with and see if it was in C++. You know, because having to learn memory management alongside how to build your basic algorithms and things like that would have I guess, been CS hardmode I guess. But yeah, it's been it's been good to me these past - my goodness, year - 15 years for me as well I guess.

**Ed**

Yeah, I had. I had the pleasure of talking about this all on the "Developer on Fire" podcast a couple weeks back, and that brought up some old school memories like I've been non professionally, I've been doing software development like my whole life, since I was able to touch keyboards and interact with computers. I've had some kind of activities that have involved programming. So it's kind of been a lifelong thing. But professionally, it's been about 15 years.

**Jamie**

Yeah, yeah, I feel like for for a lot of people, this two sort of origin stories, as it were, with development or software engineering. There's the, you know, like, I guess you or me, we've been doing it since we were, you know, wee nippers as we might say, over here in the UK. So, you know, small children. And then there's the people who come to it later in life who've maybe either had careers doing other things and decided, "no, I want to get on this technology, train." or Maybe they've just decided to do it. It makes for interesting discussions. You know, when you get someone who has a purely academic background and someone who has a purely vocational background, you can have a different exchange of ideas is really cool.

**Ed**

Yeah, it's a it's definitely a fun space to be in, you meet a lot of interesting people that cross over from other professions and get into software because it you know, they had a problem they needed to solve and they kind of like took up programming is a second hobby or something and ended up making something really cool and transitioning their entire career over.

**Jamie**

Certainly, certainly. But, unfortunately, development backstories is not what we're here to discuss today. I guess. I thought what we could do is we could discuss, talk a little bit about Blazor, if that's okay.

**Ed**

Yeah, and those backstories actually will come in very handy because Blazor will kind of bring up some of these older frameworks and languages and stuff that we've worked with before, and we can do some comparisons there. So that that should be interesting.

**Jamie**

Okay, yeah. So I guess, what we should start with is, you know, what is Blazor?

**Ed**

So Blazor is an experimental framework from the folks at Microsoft on the ASP .NET team. Mainly it is Daniel Roth as the programme manager and Steve Sanderson is the lead developer on that. And this came out of Steve's Sanderson's kind of, it's his brainchild. So Blazor is a mixture of everybody's favourite .NET templating language Razor, and it runs browser side. So Blazor is Browser plus Razor. So we get Blazor out of that. What's really interesting about that Blazor is that it is using the web assembly feature of our modern browsers to run C#, or .NET code on the local client in the browser.

**Jamie**

How does it do that then if it's in C#/.NET in the browser, I mean, I know that we can run JavaScript and I know that we can kind of, I think, is it Perl, you can kind of run in the browser, but it gets a bit wobbly. So like, how do we get from C#, "I have a DLL if I'm in .NET core world, or I have an exe if I mean .NET framework world" to running it in the browser?

**Ed**

Right. Excellent question. So what we have is web standards are moving forward. And they're now including a new target for putting our code in the browser. And that's web assembly.

So in a traditional app, we'd have our HTML or CSS and our JavaScript that all gets loaded into the browser and then the browser takes the JavaScript. And it parses through that JavaScript. And eventually, it actually turns that JavaScript into a form of bytecode. So it's doing this whether using webassembly or not, and that that bytecode gets created, and then the actual execution of the code happens. So what they've done is taken that bytecode and opened up kind of an interface there. So instead of going through this process of sending the JavaScript to the browser and having the browser do this, this just-in-time type compilation, and then turn that into bytecode. We can directly insert that bytecode into the application. And that's what webassembly is.

So what's happened is the Mono framework - that's the .NET framework that runs all over the place on many platforms. It started off as on .NET on Linux. And it also powers the Xamarin stack. So this is what we're using to do cross compilation to iOS and Android. And now Mono is targeting webassembly. So Blazor is a framework that sits on top of the web assembly, or sorry, the Mono web assembly runtime. And what we do is actually send DLLs down to the browser. So you'll actually see these coming across the wire. If you create a Blazor application. You open up your Chrome Developer Tools, and you see, literally, `netstandard.dll` flying across the wire down to the browser, which is extremely odd, because we're not used to seeing that, right? We're using these JavaScript files. But now DLLs are a static file type that we can use to send application code down to the browser.

**Jamie**

Okay, so is webassembly specific to .NET? I guess would be the next question. Do I have to have a .NET app to be able to leverage web assembly?

**Ed**

So web assembly is actually an open standard that the browsers implement. So your evergreen browsers like Chrome, Edge, Firefox, even Opera those - ah sorry, Opera may support it, not hundred percent sure. But I meant to say Safari, those things support webassembly natively. So you don't need any plugins, you don't need anything special. You just have to have a newer browser to be able to run webassembly.

**Jamie**

Just so I'm understanding that. So we have a Mono runtime which can run on webassembly. So it compiled down to webassembly, I guess. And then we we load our our apps on top of that?

**Ed**

Exactly, right. So Mono is actually compiled to run on webassembly, then our DLLs, those get loaded into mono and interpreted. And Mono is taking care of the heavy lifting.

We technically could build and compile .NET down to web assembly directly. However, that compilation step would be a complex process and take quite a bit of time. So by using the Mono runtime, instead, we're able to load those DLLs in and have a much smoother development experience because now we're just compiling down to an intermediate language and then that's being picked up by Mono and utilised. So the compilation process is much much smaller, rather than trying to go all the way directly down to webassembly. Now Daniel Roth has talked to me about this before and I think he's mentioned it at maybe build where their future roadmap they hope to be able to have a final step in their compilation process that does exactly that, and compiles the entire app down to that web assembly type of bytecode and can execute natively in the browser. But for the meantime, we're piggybacking off of Mono and using the Mono webassembly runtime.

**Jamie**

But I wonder, Is there much of a sort of operational slowdown? Converting, I guess, from .NET through Mono into webassembly, down to JavaScript?

**Ed**

Yeah. So currently, yes. So it's, you're not going to see a one to one performance, say if you compare a JavaScript operation to something that's written in .NET and running through this stack of frameworks to interact with the browser. But that doesn't mean that the application is so slow that it's impossible to use. So the performance has actually been pretty good for me so far. And then, you know, this, this project is only existed for about six months, maybe, maybe seven now. So I mean, that's very early on. So this is, you know, like I said at the beginning, it's, it's an experiment right now, it's not an official product or anything like that. So we'd expect to see, you know, beta type software behaviour out of something this new. And we're not going to see the, you know, top notch performance out of it yet, but hopefully in the future, when they start implementing some performance tweaks and possibly then, like I said, compiling the app all the way down to bytecode at the very end, that final deployment package might be able to run it at native speeds or even better.

**Jamie**

Okay, that's, that's really cool. So I guess we're, we're getting closer and closer to the .NET Anywhere. Well I mean we have .NET anywhere I guess at the moment, but I guess Blazor is one of the final pieces to get .NET to run anywhere, I guess. Because we've got, we've obviously got .NET framework on Windows devices, Mono for what sounds like pretty much everything. .NET Core for Windows, Mac and Linux, and I guess, and the cloud. So and obviously .NET framework can run on the cloud as well. So I guess in the browser, that's the final is the final runtime.

**Ed**

Well, there's always devices that are, you know, IoT devices. So there's, there's .NET on IoT, we can have it running on our Samsung televisions. Don't know if we could say that it runs _everywhere_. But I'm sure there's, you know, we're covering most of the major areas where this can run.

But the browser is a very big platform that we're kind of missing out on. You know, we've had things in the past like web forms which tried to do some abstraction on state fullness, that has kind of gone into the history books, people still write web forms apps, but I don't think there's a whole lot in brand new web form apps being written. And then we had Silverlight, which required a plug in. And I think we all know how that ended. It has ended, has ended folks like it's done.

So, you know, we've had these ideas in the past of running C#, in the web development process. And currently, we're using things like ASP .NET MVC, and .NET core, where we do server side rendering of some HTML and send that down the pipe. But at the end of the day, when we do interactions with the user, it's mostly through JavaScript.

**Jamie**

What are the differences I guess, between things like Silverlight, web forms and Blazor? Other than I guess, "Blazor is C# natively in the in the browser." I mean, is that the only difference?

**Ed**

So that's one of the main differences. So it's running client side. And, and I will have a little caveat there and say there are other ways to run Blazor. And I'll try to talk about those near the end of the conversation because it can get really confusing really fast if we try to cover all the bases at once.

But, so you can run Blazor on the, on the actual browser using C#, natively in the browser. Now of the things that we've used before, like Silverlight, required a plugin, so we had to go out and download a plugin. And then you would download your application and run it inside of that environment within Silverlight. So that kind of went outside of web standards, right? You're no longer using HTML and CSS. You're using, you know, XAML and those technologies instead. And then with something like Web Forms. You're using web technologies, but you have this weird abstraction on state. So it didn't kind of embrace the web, as a whole. It didn't, you didn't even know what type of HTTP requests were going across the pipe, it kind of was there to bridge the gap for WinForms developers to migrate their process to the web.

So with Blazor, there's no plugins that are needed download. It's fully web standard compliant. So web assembly itself is a web standard that's being targeted through Mono. And then the C# assemblies are running inside of that runtime. So there's no special plugins, you're not going to have to go to a site and download something first before you can run a Blazor webassembly application, you just visit a site like normal and the end user has - they don't know anything different. It looks just like a regular web application to them.

Now, we have the other web standard technologies to we're using HTML or using CSS. We can even choose use JavaScript if it's needed, or if we just need to fall back on it for some reason. So what's really interesting about Blazor, there's an interop layer, where we can actually talk back and forth the JavaScript modules. We can run JavaScript from within our C# code. And we can also run C# code from within our JavaScript. And we can get data and pass arguments back and forth through that layer. So that's some pretty interesting technology that we can leverage to not only fill gaps where webassembly may or may not have, say API's available, but we can also harness frameworks and technologies that already exist. I almost said "legacy." I don't want to say legacy when it's kind of putting the cart before the horse. But something like, for example, Bootstrap, we could create a layer on top of this interop that lets us write C# code that interacts with Bootstrap, but it's actually running JavaScript under the hood. And at the end of the day, the developer that's writing the application, his experience, or her experience may be just in C# without ever touching that JavaScript.

**Jamie**

Okay, would you class a Blazor application as being similar to a SPA or single page application? Or should they be classified to something completely different, do you think?

**Ed**

So Blazor actually does run as a single page application style app. So it actually takes a lot of ideas that are found in frameworks like Angular and React, and implements those ideas in our C# language. And Blazor itself has similar concepts like it has a component model, which is very easy to understand. If you take a look at Blazor code, it's very easy to get an idea of what's happening within that code.

Basically, any cshtml file - or razor markup file - gets converted into a component. So you write your markup in HTML. And then you can either write your C# code in an external file, or you can right there in the razor, the razor file the cshtml file, you can write an `@functions`, and then you write your code right there in C# to interact with that markup. And you can do client side interaction right there inside of that component. And then you can kind of package that up and reuse it throughout your application. It's very easy to understand and get running.

It also includes a routing module that has dependency injection right out of the box. And like I said, it has that, that JavaScript interop as well. So you've got this nice package of tools inside of this framework that's really easy to get up and running and understand what's happening.

And I kind of emphasise that because I've done Angular, I've done React programming as well, and the cycle of getting a new project up and running can kind of be messy. You have a lot of other technologies under the hood that you have to understand when you're doing SPA applications in JavaScript. You have things like webpack, and NPM. And you kind of have to tie these build pipelines together. And if you don't know how to configure your webpack file just the right way things don't work and you don't get a whole lot of feedback from that type of a build system when something goes wrong. Because at the end of the day it is a JavaScript system. So you end up with errors like undefined. And you're like, "Okay, I gotta go search for a missing comma or semicolon somewhere." Instead of, you know, what C# developers are used to, generally an intelligent message from the compiler that says, "check out this line of code, because your compile failed somewhere."

**Jamie**

Not just that, I guess,there's also a few of my personal projects. You know, it's so easy to just go, "oh, what's a node module to do this particular piece of functionality that I need?" Because, you know, there's a node module for everything, right? Oh, rather, shall I say, an NPM module for anything. And it's so easy just to pull down an NPM package, and then you do an `npm audit` and find out that it's, you know, three years out of date, and there's issues and stuff, you know. And then you try and reach out to the author and the author says, "oh, I deprecated this package but I forgot to tell everyone," you know. Whereas I guess if we're using the C# tools and libraries that we already know, you know, there's a there's a more, I don't know, say a more stable ecosystem. But it certainly feels like, you know, a NuGet package - at least to me, my experience being C# .NET almost exclusively, NuGet packages, if you find an issue, or if there's an outdated package reference, it seems like they can be rectified a lot quicker.

**Ed**

Yeah, that's, that's kind of been my experience as well. I feel like, you know, it's a matter of preference. And I think there's quite a few JavaScript developers that enjoy that toolset, and are very productive with it. And I don't think that it's a bad thing. I think it's great that they have something that works well for them. As a .NET developer, who's done both sides of the equation I often find myself struggling with errors and troubleshooting problems on the JavaScript side, just because there's not a lot of feedback; and it goes down to the basics of the language, right? It's not a compiled language. It just doesn't have those feedback mechanics built into it. So you get a lot of empty errors or undefined. Or I even had one situation where I added a CSS file to - or a sass file rather - to an Angular application. And that broke the build and the application literally just didn't run. So here I am trying to style an application, I haven't made any code changes, but because of webpack and how it operates, it spotted something in that sass file that threw off the JavaScript in the application and crashed it. And the output on that was, it's one of those messages that you type into your web search, and you come up with a million reasons why it could do that. And none of them have anything to do with what you're working on.

**Jamie**

Yeah, I've had a few of those in the past couple of days where I'll do a, you know, Google/Bing or whatever, for a specific error message related to some esoteric thing that I'm doing. And you know, I'm working on a Windows machine. And all of the answers are, "well if you're on a Mac, or you're on Linux, clear this directory." And I'm like, "that's lovely. But I'm on my windows, that directory doesn't exist," you know, or this version of this software doesn't write to that directory. It feels sometimes as though some of those error message can be a bit hit and miss, you know, "have you tried this? Have you tried that? Well, last time I had this error, I jumped up and down three times and clicked the button and then it's been around and he just worked."

**Ed**

Yeah, and I think it's it's also fair to say like, people have probably struggled with MS Build from time to time. The .NET tool stacks not perfect. NuGet can be imperfect as well. It's just I've had less experience, personal experience with those things. And also, if you're using C# on the client and on the server, and now you have just one tool chain to worry about. And it's, it's a little bit easier to plan for those type of problems because you don't have not only the problem of MS Build, but now you also have the problem of webpack, and they handle errors completely differently. And it just kind of doubles the complexity of what you're working on.

So now we have one tool chain that all uses the same language and build system and package management tools. And I'm sure like that .NET developers have said these things many times. Now node developers are probably going, "yeah, now you understand how we've handled things for last couple years." Because they've had that luxury for a while. So, you know, it comes full circle, I guess. I'm sure there's plenty of times where we, you know, people are using TypeScript and C# developers are going, "Yay. Now, you know, we've been handling things for quite a few years now."

**Jamie**

Yeah, exactly. But I mean, that's just how technology works, isn't it, you know. Someone comes up with a wonderful innovation and it suits a lot of people for it'll suid, a small group or a large group of people, a particular area of the tech space. And then, you know, knowledge of that will sort of start to bleed out and like you say, because, say you or I haven't had as much experience with these other build platforms. When we find errors in some, you know, because we're not used to the error messages. They seem a lot more terse. So they take a little bit more I guess, a lot more brainpower to figure out, and a lot more time to figure out what the solution is. Whereas like you say, if were working with one tool chain with one or maybe two languages, I don't know, for whichever app you're building - maybe you building the back end in F# I don't know - then you know, it simplifies it a lot. Because then I suppose the same thing can be said, like you said, the the other way around. So like, the the node folks saying, "Yeah, we used to have to put up with, you know, Apache or nginx, or I guess, IIS running some server that we have no control over. And now we have a server which runs in JavaScript, which allows us that one framework, that one language that one tool chain, for both sides of the equation."

**Ed**

Yeah, like I say it comes down to a matter of preference when these tools end up getting to where their production quality, and I can't iterate enough: it's an experiment right now. So it's not quite there, yet. But it's some really cool stuff to play with. And like one of the things that that kind of concerned me at first is, there's like this huge ecosystem built around web front end. So you know, we have a lot of frameworks that are available. And there's a lot of really helpful tooling that's out there. But what I quickly found out on the side of Blazor is that our .NET standard packages tend to work just fine in Blazor. So we also have this robust ecosystem of things that already exist that we can immediately consume with this.

So this is a really cool thing that I experimented with. And I built a small demo app called Blazedown. So I took and created an online markdown editor. And just kind of keeping with the theme of Browser plus Razor is Blazor I called it Blazedown, because Markdown plus Blazor is Blazedown, I thought it sounded kind of cool. And what I wanted to do is see if I could build a markdown, like document editor on the web. And I'm not a super genius, I don't know how to build a markdown parser. I don't know the first thing about it. But I did go to NuGet and do a quick search and found one right away. I was like, "Okay, cool. So I have a markdown parser. Now I just need to kind of wire the bits together." And I found that the markdown parser worked perfectly well on the client running in the browser. So I was running a NuGet package that has existed for I don't know how long and it's been used in, you know, desktop and other types of .NET applications. But now I was running it in the browser on the client and parsing markdown text into HTML, and displaying it in the window and I thought that was just really cool. And that I was able to just pick up bits that already existed on a NuGet and reuse those.

**Jamie**

Yeah, it is really cool when those things happen. And that is, and that's a huge thing, you know, like you say is this NuGet package that was maybe built for some desktop app or maybe built for some server side rendering of, "maybe I have a backing store that has markdown in it, and I want to send HTML to the browser." Well, now you don't have to you can just send your markdown to the browser and have the NuGet package, reformat the the markdown for con, cons, for the user to consume - that's what I was trying to say, for the user to consume so that they can see it and read it and the browser can, can render it and that is that's amazing. You know.

I mean, I don't think we can, I guess with web assembly, we could probably do that. With C++ now as well, but, you know, that's not what this podcast is about. But, you know, we take a little bit more effort, I guess. But that's amazing that you can have the same NuGet package being used on the client as well as the server because you could probably reverse that NuGet package and have HTML being sent from the client to the server converted to markdown and stored in the database. Then when the user hits refresh, and we're reading from the database, send it over the wire, convert it from markdown to HTML and display it on the page.

**Ed**

Yeah, the app that I wrote, I just left it completely client side to just kind of demonstrate that it's a nice little editor, but you could run wild with all of it and make some really cool apps.

One of the things that I found was really interesting in that process was how, first of all how simple the code was, since most of it was abstracted into that markdown library. All the work is really being done in there. A lot of the UI part of it was just kind of wiring up, you know, a textbox, to a function that calls to that external library, and, you know, handles all the processing in there. And then I get an output and just render that to the page. So I mean, the code is, you know, you can open this project up and look at it. And it's, you know, just a few lines of code here and there, and you can immediately understand how it works.

Where I actually struggled and had a problem is the age old browser problem that we experience, whether we're doing JavaScript, or we're doing any other type of web development, that's where I wanted the user to be able to click a button and download the markdown and, you know, be able to open that up on the desktop and say, continue editing in a markdown editor locally or something or, you know, download and share it however, you know, just get it out of the editor itself. So I started out with the idea of putting the download material into a data URI. So I kind of wrapped the content that was in the markdown editor in this data URI, and then when you click the button, magically, it just the browser understands this is a data URI, the payload is within the URI, and deliver that as a download. So you just click the button, and boom, you get it. And then I opened Edge. And you click the button and nothing happens. So after some research, I found out that Edge does not support data URIs. So you have to use a proprietary API that only exists on Edge. So yeah, that the same problem that you'd have you know, 10 years ago with browsers handling things differently. I guess you could say "incompatibility", for lack of a better term. But you know, that was raising its ugly head. And I ended up having to use that JavaScript interop, because there's no native browser support for doing this download functionality. You have to actually tap into this Edge API to handle it, and it's in JavaScript. So was JavaScript to writing that shim to kind of get Blazor to work in that way, and provide that download button. But I was able to get it to where it works. So the app, you can actually import from a URL, so you can import some markdown from say a GitHub resource or some other web resource, and then you can edit that document and then you can click a button and actually download a markdown file and save it. So I thought that was a pretty cool full cycle application to experiment with.

**Jamie**

Yeah, yeah. That sounds a lot cooler than the demo app that I created. We're going back a few months now. But when the Blazor, I believe it was 0.1 preview was released. I got a little excited and wrote a little blog post about, "oh, this is really cool. You should check this out." And then a bunch of people that I work with, decided, "why don't we stay behind one evening, and just have a mini sort of not really a hackathon, but see what we can create with it." So I created a template, a .NET Core `[dotnet] new` template that we used, that created you know that the base - it was essentially one of the demo apps but with most of the stuff ripped out of it just so you started with a blank slate - so that we could get up and running. And I ended up creating an app that I called [PokeBlazor](https://github.com/GaProgMan/PokeBlazor), much for the same reasons that I guess you did with your your markdown viewer and editor: in keeping with the sort of Blazor Razor Browser connection. And all the mine does is it displays a little text box and you type in, I think it's a number between one and 750. And it tells you which Pokemon that is. And it gives you a bunch of images. You type in a value and C# code on the browser, does a web request back to the server to send the ID through. The server does all the hard work of contacting an API, but then it converts what it receives to a C# POCO - so a plain old C# object - and sends that down the wire to the app. And then the app uses the POCO to update the view. Which is, you know, obviously in the past, we'd have had to convert that to I guess, JSON or something similar on the server, send it over the wire as JSON, then parse it back to JavaScript and display it.

**Ed**

Yeah, it's definitely taking a lot of ceremony out of writing a front end application. I think it's got some serious potential. And in the last release in Blazor 0.5.1, they added a new feature, which is I kind of alluded to earlier, but I didn't want to, I didn't want to muddy the webassembly conversation. Because Blazor, the framework actually does not need web assembly. So it can run without it, but it can't run client side without it.

So Blazor can actually run on the server side as well. And if you're on the server, you don't need webassembly, you're just running C# code. So it runs natively on the server. But what they've done is they've separated the UI thread to where it can run across the web, on a web request, and it uses a SignalR WebSocket. So the way that the application is actually structured is: Blazor runs on the server, you download the index file - that's the only thing you actually get from the server besides other static resources like CSS and JavaScript. But for all intensive purposes, you don't really have any HTML coming across, other than its index file. Now, the index file bootstraps a WebSocket SignalR endpoint and that connects up to the server that's running Blaser and processes all the UI across that WebSocket. So you don't actually have a client side application in that scenario. It's kind of like a thin client or a dumb terminal. And it looks and feels just like a regular web application. The end user doesn't have any idea that it's not, you know, built and structured like a normal - what we consider today a normal application where you've got lots of HTML and JavaScript being downloaded. So this thing gets this WebSocket connection. And then if you interact with the browser, it kind of does a diff. And it says, "alright, this, you know, maybe this text is changed. And we need to do some kind of update on the UI." And it sends that package of data up pipe. And it's doing this through a binary transfer even. So we're not sending JSON packets, we're actually just sending a binary diff package up to the server. And then the Blazor application, picks that change up processes, the DOM changes that need to happen and sends a diff back down. And then the browser updates the UI for us.

**Jamie**

That's amazing.

**Ed**

It's very fast. So where we were concerned about speed earlier in the conversation, that concern is completely gone. It's only sending these tiny little binary packages back and forth. When you interact with the browser, you're not sending down DLLs anymore. There's not a bunch of JavaScript flying over the pipe. It's just the Blazor, or sorry, the, the signal our client, it's spun up. It's just a few k of JavaScript. And then it hydrates kind of the view into the browser. So it sends the HTML across the wire, the application, client side picks it up, and loads that into the browser, and then you're off and running. So there's very little data transfer in that. And then the actual updates are very tiny as well. It does kind of remind me a little tiny bit of how web forms worked. But there's not as much of an abstraction around date, so it's not kind of like the stateless thing that's happening. But you're also not doing a lot of HTTP traffic either. So it's it's kind of a new thing. It's It's very cool.

So say for instance, you have a,

an a framework database kind of abstraction. Maybe you have a repository pattern, something like that. You don't have to build like a web API endpoint on top of that, you can just access it directly from your Blazor application on the server. And it runs just like a normal dotnet application. So you're not doing HTTP across the wire. And all that to do data traffic, you do all the processing on the server, and only send down the the UI diffs that you need to make the UI look the way it needs to look. So that's, that's a pretty interesting mashup of the Blazor framework and the brand new signal our system that's been built. So that's it's quite a different table. And it's still the same Blazor framework, it's just running kind of in a different mode.

**Jamie**

That is absolutely amazing. I remember when I was playing around with, like you said, you know, the the early, the earlier releases of Blazor, you know, you had to download the dotnet, standard DLLs to the browser to make them into to make them work, I guess, because you're running those DLLs those new get packages in the browser. So obviously, if you're new get package, if you unfortunately included things like Newton soft JSON, which is an amazing package. But it's, you know, in the megabytes, your page is gonna take a while to load

**Ed**

it what's really weird is when you run Blazor server side, if you open the browser developer tools, and you look at the traffic, you're interacting with the page, and you can see data being, you know, through the UI, you know, it's being updated. So say you have a data grid or something you You see data populated in the data grid, and maybe refresh that data or interact with that data, delete a record something of that nature. You don't see traffic going across, you don't see an HTTP request, like hitting an endpoint somewhere, like an AJAX request or anything. That's because it has this open pipeline, this WebSocket that it's transferring all the data through. So you don't see new requests, you just see that there's been a initial request, then you can open a tool that the company I work for actually makes and it's completely free to download and use. It's called Fiddler. So a lot of listeners, I would assume, if heard of Fiddler, it's pretty popular. But you can actually open up Fiddler and you can look at that initial request. And if you double click on it, there's a pane that opens up and shows the socket transfers. So you can actually watch the data go Across the socket, you can't understand what the data is because it's binary. But you can see that requests are being made back and forth through that WebSocket, which is kind of neat.

**Jamie**

Yeah, that is cool. I'm starting to imagine that maybe you could create a because obviously, signal r allows you to do real time bi directional communications, like you say, over over a WebSocket. So I'm thinking, you know, at the moment, I'm thinking, less a case of I create an entity and they're deleted, more a case of maybe systems monitoring. So I could have maybe an admin dashboard that talks to a bunch of servers, which are reporting on how my apps are doing. And if an app goes down, I don't have to refresh the page. I don't have to have JavaScript doing a every second or every half a second or every minute or so doing a request to the server. The server can tell me when the app goes down.

**Ed**

Yep. And you don't have to use it. Blaser to necessarily take advantage of that. So you can actually do that type of thing with just signal r itself, you could build, you could build a JavaScript only application that utilises that technology. But with this Blazor style of doing it, the entire application code itself, you know, you don't have a JavaScript spy application that's running on the client anymore, which you could have a signal our JavaScript spa application. But in the case of Blazor, you don't even have that much, you're running the entire thing on the server. And the only JavaScript that's necessary, is that, that one that kind of makes that initial connection. So the rest of the application gets fed through that, that signal, our pipe, and all the updates happen over binary transfers. It's just really cool stuff. Now obviously, the downside of that is you have to have a consistent connection. All the time. So it's not something that you can build and have working in offline mode. But as a developer that's worked in heavy manufacturing and other corporate type of industry settings. You often have, you know, machines that sit on a shop floor and they could, you know, easily take advantage of a technology like this because they, you know, that machine doesn't move. The computer that's added doesn't move. And it's usually either hardwired or has a fairly consistent wired Wi Fi connection. Whereas if you're building say, like a mobile responsive app that somebody is going to be walking around in a cornfield with limited network access, it might not be the best option.

**Jamie**

But then like you say, it's different different technology for different uses. Where we were talking about earlier on, we were talking about dotnet and we we kind of picked on NPM. I feel like it was a bit of a To pick on them. But, you know, it's it's the same thing with any kind of development, you pick the technology that fits the problem domain. Best? I guess not. Not that it will. Because let me rephrase that. There isn't one technology that solves all of the problems. But there are different technologies that solve problems in different ways, I guess. And it's picking the right one, like you say, if, if you have a someone out in the field who doesn't have a constant internet connection, you don't want to give them something that relies on a constant internet connection. But like you say, if it's a system that's inside of an office or inside of a factory where things are happening, and you can rely on that connection, then yeah, you can do that.

**Ed**

And I know in my career, I've built some very simple applications. Simple in the respect of the technology, they use your dotnet app with not a whole lot of code behind it, but it solves a really complex problem very easily. And you don't, you don't always write like the next Facebook or Netflix app, right? You don't always need Angular in, you know, 30 40,000 files that come along with, you know, a framework of that magnitude. Sometimes you just need a VB six app, or, you know, some little wind forms or web forms type app to get a whole lot of work done. Because it's just, it's simple to create an app around a process. And maybe you have some machines within that factory that are already in place, and they have a network connection. And just by adding these these small apps, you can increase productivity in that, that setting very efficiently. And I think people forget that often. And they, you know, they see a framework and they're, you know, they're like, Oh, I'm going to build the next big gigantic multi tenant, Netflix style or Facebook style application with Angular react and, you know, a couple weeks go by, and there's so much code and, and stuff in that stack that it's it's almost, you know, impossible to figure out what's going on if you didn't build it and document it all yourself. But, you know, there's that there's a lot of opportunity for big wins with small apps for very custom type of things. And I think we lose sight of that. And I think Blazor is is something that could fill that gap very easily.

**Jamie**

So because Blazor is a Microsoft experiment, is it open source, or have they closed it off? whilst they're sort of doing their experimental phase?

**Ed**

No, it's actually open source. You can find it on on GitHub. I can't remember the URL directly. I think it's GitHub slash ASP net slash Blazor. And they do accept pull requests and you can get in there and file issues which which I've done quite a few sensitivity Really very early in development, there's things that that just don't exist because it just hasn't had time to mature enough. So it helps the, the team that's working on it, decide on the roadmap if you get in there and, and raise issues or go in and kind of comment on issues and let them know what's important. And what what you'd like them to, you know, consider working on next and put in their roadmaps. That stuff's been been helpful. As far as feedback that they've given me that that's very helpful to them. Another thing that they've expressed is helpful is just kind of providing feedback on is this something I could use, like, is this is this something I'd like to see more than an experiment on? I think that would be helpful feedback to the team as well. And they actually have a survey if you download and run your Blazor app template, there's a link you can click on right in the example That'll take you to a survey where you can fill out that type of information.

**Jamie**

So I've been using a phrase where I work on officially naming an umbrella, the core technology, so dotnet, core, ASP. NET Core, EF core sigma, you know, that kind of thing. I really like that these things are in the open and that and that Microsoft are literally developing them in the open, you can see the poll requests and the commits come through. But they're much more than that. I like that they are engaging with the community and asking for likes asking for feedback. But not just that, but asking for people to vote on things. So even if you're, if you're a developer like me, I suppose I don't think I'll ever be able to have a pull request into Blazor because it's just it's way over my head. Or at least that's how I feel at the moment. But I know that I can go on there and I know that my vote matters, you know, this feature. Being able to stream files would be good. Oh, You know, being able to, whenever, you know, being able to do this feature or that feature, we'd like these, we'd like those because I guess like you say, it helps the engineers who are working on it to prioritise which features to add. Because I guess at the end of the day, they're building the technology for us to use. They're not building it for them to use, I guess.

**Ed**

Yeah. And I think it helps them get visibility into what people actually need, rather than trying to guess, and what people are intending to build with it. So it gives them more of an accurate representation of what needs to be done with it. And it's great that they've got an open dialogue going and they comment back on issues and I've seen things get worked on and implemented. One of the examples is, there was no way to render raw HTML at the beginning. If you didn't do things through their component model, then that just didn't do anything else. There was no way to They like, manipulate the DOM in any other way. So that was kind of a hurdle for something like a markdown editor that I was building, because you couldn't render that markdown out without jumping through a lot of hoops. Another issue that I brought up that's that's being addressed is, was kind of a future forward kind of idea. browsers have now implemented a standard around JavaScript modules. So if you've done any modern JavaScript development, you've probably used Webpack. Or, gosh, I'm trying to remember the other names of those tools that that kind of do the like Babel j. s, and other bundling and compilation style tools, where they they support different module patterns in JavaScript. Now that's actually a native browser thing. So you can create us import and export statements in your JavaScript and create Real JavaScript modules. And you can actually utilise those in the browser natively. So it's asking for some support on that, because of the JavaScript in our app, I think it'd be an easy way to package up your JavaScript libraries that need to go with those interrupts. So instead of having many JavaScript files and some kind of build system to create something that the browser understands, you can now just do that natively through JavaScript modules using the valid syntax. So having support for that, I think would clean up the interrupts situation a lot better and they they've actually taken notice of that issue and, and put that in their work queue. So it's really cool stuff.

**Jamie**

Yeah, it really is. I'm really interested to see where we go with Blazor in the next, say a year or so. You know, like you said, we've had a at the time of recording. We've had a few Recent 0.5 point one release, and that's only six months since the initial release. So it's going pretty rapidly. It's an experiment which is very quickly, maybe very rapidly reaching a 1.0 release.

**Ed**

And there's there's not a lot of documentation out on it right now which is again understood because of the newness of it. So if you're looking for information, you can find me on online at Ed Charbonneau Comm. I've got some blog posts that are in the works and should be live and sometime in September, these blog posts will be coming out. Not quite sure where they're going to be published yet. So if you find me at Ed Charbonneau calm or Ed Charbonneau on Twitter, I'll let you guys know when those blog posts become available and I'm doing some projects around like how All of the templates are structured and what you're going to find inside of those templates, as well as like how to work with the JavaScript interrupt. So one of those files or one of those blog posts will be published on log rocket. And then probably blogs teller comm and maybe even MSDN, we'll see, but I've got some content coming in that way. And then I've also got a channel nine video that I recorded at the Channel Nine studios that should be airing on the Visual Studio toolbox programme within say, a few weeks, so that that stuff will be out now I'll tweet about that stuff when it comes around. Just give me a follow on Twitter, or check out my website and and I'll update everyone on on where to find that stuff.

**Jamie**

Sure. So that was gonna be my next question. You know, where can people reach out to connect with you and To ask questions and find out more about yourself and maybe more about your experiments with Blazor and obviously, listen to your podcast.

**Ed**

Yeah. So the the podcast is, the easiest way to find it is to look for it on Soundcloud or iTunes and look for the eat sleep code podcast on one of those two outlets, and like are subscribed there. And we've been doing a show probably every two weeks, I'd like to get those backup every every single week. Depends on my travel schedule, though. So you might see the, the episodes come and go a little bit, but we try to get new content up there. I've got some guests lined up for the next few weeks and we've had some really great people on there in the past as well. So check out that back catalogue. actually had Daniel Roth on there talking about ASP. NET Core 2.1 not that long ago. So good. Good show there.

**Jamie**

Definitely check And wherever you can find him and listen to his podcast for sure. Did you mention where people can connect with you?

**Ed**

Twitter's probably the best way to connect with me directly and I go by my by name on Twitter. And I'll give you that for the show notes as well in case people can't spell the name. My last name is not the simplest but I go by Ed Charbonneau on Twitter. If you give me a shout on there, I'd be happy to answer questions and get in touch. So that's the best way.

**Jamie**

Fantastic. Thank you ever so much for being on the podcast. And it's a it's been a real pleasure and a real treat to learn all of these different things. You know, I'm trying to keep my my fingers in as many pies as we would say over here to do with all of the like I say that umbrella term that I use the core technologies, but sometimes with everything being released, it feels like a news release or a press release every every day. So trying to catch up with all of those is a bit difficult, but you know, hearing it from people like yourself, helps to make it a little easier to take in

**Ed**

Well, thank you for having me on and setting aside some time for me to talk about Blazor. It's it's been a lot of fun.

**Jamie**
Thank you very much.

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
