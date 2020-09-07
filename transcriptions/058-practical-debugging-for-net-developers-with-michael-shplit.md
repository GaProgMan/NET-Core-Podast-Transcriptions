### Episode Transcription

### Sponsor Message

Today's show is sponsored by {{< sponsor-link link-text="Datadog" link="https://datadoghq.com/dotnetcore" >}}.

Datadog, a monitoring and analytics platform combining metrics, distributed traces, and logs in one place.

Datadog helps leading companies migrate to the cloud, transform to a microservices architecture, or transition from .NET to .NET core. With interactive and drag and drop dashboards, see a high-level overview of your .NET applications alongside the health and performance metrics from the application's underlying Azure VMs.

Give it a try with a 14-day free trial today and Datadog will send you a free T-shirt!

---

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is Episode 58 - Practical Debugging for Net Developers With Michael Shplit. In this episode I talked with Michael about the fact that most developers aren't taught a great deal about debugging other than "set a breakpoint and inspect values", we also talk about some practical advice that he has for debugging applications regardless of the technology stack used, and we talk about his new book "Practical Debugging for .NET Developers".

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

{{< paracentre "The following is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

#### Jamie

So first thing I'd like to say, Michael is Thank you ever so much for spending the time with me today to talk about this. Everyone knows hope you can hear the bunny course everyone knows debugging, right? They know that. I'll put a breakpoint in and just that debugging or I'll do as a print statement, or I'll create loads of logs that I'll never look at. Right? That's that's how we do debugging, right. But it's interesting to be able to talk to an expert about how we go about from instead of using the tools and like, here's a breakpoint, here's a stopwatch. Here's the watch window, how we go from that to actually solving the problem. So I really appreciate you coming on and talking to me about that. Could you first give a little introduction to yourself for the listeners?

#### Michael

Sure. So thanks for having me, Jamie. My name is Michael spelt. I've been programming for about 20 years and in the .NET universe for about 10 years now. I work in AWS code, which is a company that's dedicated to debugging for .NET developers. I also maintain a blog. And then now I'm in the final stages of my book and the video course about debugging. Excellent. So

#### Jamie

there's a lot going on there. Like I said earlier, and everybody thinks that they know Well, everybody knows about debugging. And that's, like I said, you put a breakpoint in, you step over you step in sorted. Excellent. But I think when I talk to your colleague, oma, we talked about how debugging, like as a platform agnostic technique as a tool agnostic technique of actually figuring out where the problem is, how to solve the problem, how to put the fix in place, isn't really covered. I went through the the university computer science, but that's my background is Computer Science at university. And we definitely didn't do anything on actual practical problem solving. So I'm, I'm really looking forward to this conversation and reading your book when it comes out. Because, you know, as much as I've been doing it for a while, I don't think anyone's really codified how to actually solve problem or best practices or any kind of tips on how to do that, you know, I'll sit there with a piece of paper and I'll be like, I'll pass in three, and it came out seven, but it was actually expecting it to give me a six. So it's added one. Okay, so I'll practice in a four, but now it's giving me 10. That's, but is that the best way to do it? Is that not the unit tests? Maybe, maybe. But before we get to the book, I do know that you've been writing over on your blog, Michaels coding spot for a long time, pretty much four years now, right? Is that just debugging or is that all manner of programming stuff? Is it just C# .NET? Is it c++,

#### Michael

it's not just debugging. It's all .NET actually started at first with WP F, because they did a lot of knowledge about that. But then it quickly moved to C# language. I read a lot about memory, write a lot about performance, performance optimizations and investigations of performance problems. I write a lot about debugging actually. Literally

#### Jamie

Okay, so it's a broad range of topics Anyway, you know, you're not just the debugging person, you you're talking about performance, you're talking about all sorts of other stuff. And I do find that starting a blog on a specific topic as you start to learn more about it, like you said that you started on WP F, right? So that's a great way to sort of solidify your knowledge and then be able to because I found out solve a problem. And then three weeks later, I'll be sat there going, how did I solve that problem? And I'll go back. And if I've written it down and put a blog post about it, and go, Oh, great. There's this public repository that I've created if the solutions to this problem, and then I don't have to spend the three hours figuring out how to do it, I just literally I have my step by step guide on how to do it, which is how I started writing about stuff. I think it's a good way for people to sort of get into that. As soon as you solve a problem, write it down, publish it somewhere, even if just put it on WordPress or Hugo or something, blogspot, whatever it is, even if it's just a markdown file in the get repository. Again, out there, because in two weeks time, you're gonna have the same problem, you're gonna have forgotten about it, right?

#### Michael

Absolutely. So actually the researchers that say when you explain something, then you get it yourself much better. And when you put it in writing for the public, like in a blog post or a YouTube video, then you sort of feel obligated to do the best job and to do their research. And if you don't, then you're gonna have nasty comments and bad comments on Reddit and in the blog. So definitely, writing a blog is very educational for the writer as well.

#### Jamie

Absolutely. It's a great way to sort of learn how to communicate, you've got a paragraph of information and really, you can maybe drop that down to two sentences, because you've got lots of filler words and stuff. Oh, yeah. Is there a better way to put this, I wrote a blog article, backwards. .NET core first came out about the ASP NET Core middleware pipeline, and they were really horrendous diagram. Just squares with arrows and then I think So that Andrew Luck had done essentially the same thing, but in a much better way. It was much more detailed, had like a summary and a conclusion. And the diagrams that he created for it were gorgeous. And I'm like, oh, maybe I should have done that. Looking at it from another person's point of view as well. It really helps.

#### Michael

Definitely, yeah, it's really important to write briefly and concisely. It's an art, I guess. I edit my everything that I write about 10 times and I'm never happy, I can edit it 10 more times, make everything shorter, shorter is better people understand short content. That's my same philosophy with the book, make things further and it will be understood.

#### Jamie

Absolutely. And that's a nice little segue. So we've mentioned the book a few times and you have one coming out called practical debugging in .NET. Could you tell us a little bit what was the decision that went into our ran a book on debugging is it there are no books on debugging was it just because You're an expert was the impetus I guess behind it,

#### Michael

experts is a big word. So there are several reasons that went into writing a book about debugging. One of them that I'm working for a company is called, which is dedicated to making debugging better for .NET developers. And we have a lot of knowledge for that both to try and to debug the debugger to try to debug ourselves. It really presents a lot of challenges. And the other thing is that I wanted to write a book. Because I was writing a blog for a long time I really enjoyed it. I thought, hey, went write a book. That's a decision that lived to regret. Don't write a book. But also the topic fascinates me. Because I think of debugging as solving problems, which is not just placing breakpoints in code. A problem might be a performance issue or a crash or a Hank, it can be anything that you need to resolve in software. There are a lot of books about technology, about SP .NET, and WTF Entity Framework. And so on. There are a few books about debugging, but they mostly talk about interactive debugging with Visual Studio. And in debug, I wanted to write a book about problem solving. So that was sort of the incentive for the book.

#### Jamie

Right? I see. It's called practical debugging to catch people with a hit. You can learn how to do the debugging, but it is really practical problem solving. But then if you call it problem solving, people are going to be like, Oh, well, I know how to build an ASP. net website. That's the problem solved. So I totally get why you've called it that. That makes a lot of sense.

#### Michael

Yeah. I actually thought about it. I wasn't sure I wanted to change it several times. But I ended up for the debugging.

#### Jamie

That's fair enough. So you've said that you want to move away from the interactive debugging the place the breakpoint, the look at the watch window, the the interactive, the actual tools used. So does that mean that the book is tool agnostic? like can I take the information that you have in that book and apply it to say Ryder from JetBrains Or Visual Studio code? Or as I'm just using notepad and I've opened the source code, can I do it that way as well? Or is it, hey, you're gonna need this suite of tools to be able to do what I'm doing.

#### Michael

The walk is definitely not tool agnostic. I talk a lot about tools. And interactive debugging is certainly part of it. But they also talk about the tools for performance and the memory profiling, and production debugging. And they're solving issues in the cloud in Azure. And they also have a big chapter about the tool agnostic about strategies for debugging principles that you can use in any language in any technology, like the divide and conquer principle, where you have an issue and you divide it into two parts. See which part of the issue comes from then keep dividing until the whole mean, it's both about tools and not about tools.

#### Jamie

Okay, so it kind of covers the whole suite. I guess for like a performance thing. You're going to need some kind of tool to Love the performance and then to work on the performance, right? You can't just say, Oh, yeah, well, what are you going to do is you're going to vaguely do this wizardry over here. And it's just going to work, you're going to need some kind of tool to help you. All right. So in the pragmatic programmer, they talk about how we are crafts people, right? We need the right tools to help us do the job. You need a hammer and a screwdriver and drill and things like that. It doesn't talk about the brand. But it talks about you need these things in order to go from journeyman to sort of wizard, as it were, in our business. We use the word wizard. I'll have to stop using. Yeah, you're gonna need some tools along the way. But yeah, that totally makes sense because he can't talk about performance debugging, or production debugging, without actually say, Well, if you use this tool, it's kind of helpful. And these are the steps that you would go through, right?

#### Michael

Yeah, you definitely need tools. Adding stopwatches in your code is not going to cut it. And then .NET we have a very rich ecosystem for we have a lot of tools that can help buss for performance, for example, with performance counters, which are these overall metrics in windows that dealt with the application health, CPU usage, memory usage, things like that. We have various performance profilers, Visual Studio has an integrated performance profiler, JetBrains redgate. We have at W events, which is a sort of built in logon system. And you can do performance profiling with that with a tool called perfu. A lots and lots of very good tools on Windows and some not so good tools on Linux.

#### Jamie

Maybe that makes sense. Your .NET is kind of not new to Linux because of things like mono, but like especially .NET core or as it will soon be renamed at the time of recording .NET five, when they bring mono and Xamarin and .NET core together. That whole tool set is new, the whole thing combined together is new. So it makes sense that the debugging tools aren't particularly there. And you know, we talk about Linux, but it isn't really like So not the machine that I'm using to record but my daily driver for all of my development, it runs pop OS, which is a distribution of Ubuntu, it has the Linux kernel. So we talked about Linux. But we don't actually mean Linux when we say, yeah, I'm running Linux. Well, you are, but you're running other things on top of it. Because there are so many different distributions, I can imagine that it would be very difficult to write one debugging tool for one language that just works across all of them. Right. I know, I know very little about the actual moving parts in distributions. But I can imagine their distribution based on Debian with the GPT package manager versus a distribution that runs on arch, which is which has the Yum, package manager, there's going to be huge differences there. Right. It's almost like Windows and Mac, right. The different the underlying differences will be will be great. That is difficult to build the tools across all of those that will just work.

#### Michael

Yeah, I guess the filmmakers the JetBrains of the world, and Microsoft I guess they have a lot of trouble with that. But now we have some better tools. With Ryder. I know you had a guest some time ago that talked about that was from the JetBrains rider team. And so we have a cross blood from .NET ID that can now we can debug code on Linux. And also with .NET. Core three, Microsoft added some very needed tools. With the .NET core three SDK, we now finally have good tools for them files on Linux, for collecting performance snapshot. And for performance counters. We kind of had those tools before in some variations. Like we could use the native Linux dump files, which are called core dumps, nothing to do with .NET core. And we had them like sort of an equivalent performance counters, but now Microsoft created tools they recognise that there's a problem that if you don't have diagnostics or some troubleshooting tools, then companies will hesitate to deploy Linux servers. So they fill that gap, sort of with those tools that are starved, and we'll see where it goes.

#### Jamie

And that's what we need. We need companies to come forward and go, here's a tool, try and use it. And in some instances, we'll make it open source. And then you can submit any fixes or whatever, and then other companies can then go, Oh, cool. I totally see how you've done that. Let me see if we can improve it and make it better, right, because it's just better for everyone. If someone comes up with some big first, you know, and then someone else comes out with a competing product. I mean, that's what the free enterprise is about. Right? competition breeds innovation.

#### Michael

Absolutely. Now JetBrains has their performance profiling support with dot race on Linux tomorrow, and we'll do the same and so on. Absolutely.

#### Jamie

Yeah. It all comes down to it being better for us developers, for us tech people, wherever you are in that tech stack in that company, it is better for you because that you get the information you need.

#### Michael

Yeah, it's all good for the customer in the end. And you know, Microsoft has a huge investment in that. Because I think they told I think a couple of years ago that 50% of the servers on Azure is Linux, something like that. And I guess it's more now, because Linux is cheaper and faster. So if they want people to use .NET, on Linux, so they use Azure, and they'll do anything, they'll invest any kind of effort into that,

#### Jamie

I believe. Oh, absolutely. I mean, it was just this week at Microsoft build, which dates the recording of this. I think they're still wrapping up at the moment as we record I'm not sure where it started late Wednesday evening for me and it was 48 hours so I'm expecting it to still be going on as we as we were recording, but the first thing that they showed us was is Windows subsystem for Linux, like Windows now ships with a Linux kernel. And you could just attack that. And it's running Linux on your machine, right. And then they're exposing the actual windowing system. So you can instal, say the canoe image manipulation programme on your Linux kernel that is running on Windows and then call it from the CLA and it will draw what it should look like on the distribution that you are running inside of windows, which is just it's amazing right there exposing that. So so then you can see as a developer, what your app will look like, and how your app will behave because it's got a real, because I think Ws l one was a translation layer. So if you did, I don't know, LS Ws l terminal, it would translate that to dir which is LS is less than dir is directory just to show the files in the directory, right? And it was doing this translation layer. Yeah, they've just sort of bitten the bullet and you know what, let's just ship it with it or enable it or something. And just, it's Hold on Windows, because then it's easier, because then you've got a real system. And it's amazing. And yeah, if you are going to be shipping your software to run on a specific format, he should be able to make sure it runs there.

#### Michael

It is amazing. Yeah, definitely.

#### Jamie

So I've talked in the past to your colleague oma, he was talking to me about a product that I was going to make that helps with debugging in production. But one of the things that we sort of talked about is that debugging as the problem solving aspects, not as the here are the tools. Here's a breakpoint is logging is printed to the console. But as a actual topic of the practical aspects of it. We both came to the conclusion that this has been sort of left out of the majority of like, training and boot camps and university courses. Do you have any sort of opinions as to why you think this might be like from my point of view, it'd be where I went to University, the University of Microsoft were very friendly. So we got you know, all of the Microsoft tools for free the operating systems for free, anything we needed. Microsoft got it for free. There may be a little bit of politics involved in that. But we were also doing a lot of .NET. So it kind of makes sense for them to join together. But from your point of view, why do you think debugging is kind of pushed to the side? Is it because we write perfect code every time and it never fails?

#### Michael

That's probably not the reason. Yeah, debugging is definitely pushed to the side. They don't teach that in university, at least not when I learned, but they kind of understand why then they don't teach debugging. And the reason is that beyond the basic functionality of debugging, where you place breakpoints, and you investigate variables, you either teach tools, or you teach principles. And the tools are very technology specific. For example, in .NET, if you're going to teach debugging, you're going to have to talk about symbols and code optimization, and the garbage collector. But then you have JavaScript which is You don't have any of those, you have a single thread. So you don't have to do any multi threading stuff, you run in a sandbox. Those are different things. And the Python is a third entity, it's different. So teaching tools is I'm sure that's the best for the time. And the principles. Well, let's talk about the principles. You have things like I already mentioned, divide and conquer, you can like there's the principle of do just one thing at a time, where you guess that certain fix will solve the problem. Or, say you have three fixes. Will we apply all three at once? Or will you apply one at a time, and in almost all cases, you will want to apply just one at a time because they might negate each other, or they might cause side effects which you won't know. And these principles are hard to teach when you're just starting out. This You developed the intuition of a software developer with a few years experience now about boot camps, you know, maybe they should have debugging boot camps. I think they should have I don't know if they have them. I didn't. I've never encountered one.

#### Jamie

I've never been to a boot camps. I don't know what's actually involved. I do know, some people who run them. And some people who teach them, I get the feeling that it's like, because you do essentially eight hours of training to do development every single day is kind of you're expected to go from nothing to graduating in about three months to six months. From what I've been told you're guaranteed to get a job at the end of it. Well, that means I don't know, right?

#### Michael

Said boot camps. I meant workshops for experienced developers. Maybe I don't know they have workshops for debugging, but I think they should. I think it's debugging is just a huge part of your time as a developer, you're either solving bugs, which is debugging by definition. Or you're developing new features, and then you encounter problems all the time. And then you do debugging?

#### Jamie

Definitely, I can say that around 60% of my time when working on a project is maybe 10 15% of it is designed. 5% is writing tests. 2% is writing the code. The rest is debugging, right? Because throughout your career, you're gonna spend more time maintaining and debugging code than actually writing brand new features, because I joked about earlier on but nobody writes perfect code. I've seen live demos with some pretty big names in the business where they messed it all up as they were doing it because they're doing it live, right. But the same thing will happen when you're working at your workstation, or you're working on your open source project or something, you're going to get something wrong. So just accept that and realise that yes, you are going to spend some time debugging whatever it is that went wrong.

#### Michael

Absolutely. We're not perfect. Nobody writes perfect code. And that's it. If you work in a team, which most of us do, that's multiplied that exponential, because you don't know what the other person is doing. Or at least you don't know, 100%. And you're going to step on each other's toes, you're going to make bugs. And then it's going to be more difficult to debug someone else's code. And you know what, it's going to be difficult to debug your own code. After six months a year, I read my own code. And for everybody who I don't recognise that I was the one who wrote it. Yeah, debugging is a huge part of development.

#### Jamie

Absolutely. I completely agree. Maybe there should be training and workshops for developers, and maybe they should not be agnostic. So like, here's a training session for .NET developers on debugging. Here's a training session for Python developers on debugging because, like you said, with experienced developers, if you are working in a specific language or framework or toolset, you're gonna want to be able to be as easy a lot of people throw around the word productive. I tend to use the word effective, you want to be as effective with your time rather than productive sometimes I found that For some developers productive just means I've moved this ticket from here to here, you know, it's gone from in development to QA or I don't know, whatever. That's all they care about is moving that ticket. But you may pick up a ticket that is create a Hello World app. And you may pick up another ticket that is craft an entire microservices architecture that does logging and uses event sources and publish it to as your and get the user using it like, which one of those is more effective for the business. So I tend to use the word effective. But if you are using a specific tool set or framework or whatever, you need to figure out the most effective way to do your job. And if we're spending 5060 70% of our time doing these problem solving activities, where we're looking at code that doesn't necessarily do what it's supposed to do. Or rather, there is an edge case in the code, and you need to solve the problem of not having that edge case happened, which we call debugging, rightly or wrongly, maybe we should have training courses where it's like oh, Okay, so first thing, two hours on the garbage collector, here is what that does Now, another hour on, here's what async actually does and how you're getting it wrong, you know, maybe someone should do that. So yeah, so we've talked about how we can use the tools, the breakpoints, stepping through the code, logging to disk and never reading those logs, analytics, all that kind of stuff, printing to screen, a friend of mine always used to do this. He was a, he's a front end developer. When he has a bug, he actually puts in, like in the JavaScript code, he literally to do his sort of divide and conquer. Rather than using debugger statements. He puts alerts everywhere, and then slowly starts to remove them until he gets to the line of code that still has the alert. He's like, Ah, that's where the problem is.

#### Michael

Also that

#### Jamie

there's nothing wrong with that. Yeah. It's a great way of doing it, isn't it? Yeah. Then you don't have to have the dev tools open. It's just literally appearing on screen. Alert, alert, alert. All right, cool. That's where it is right? Remove all of these and rerun but aside from you In the tool specific stuff without giving away the content of the book, obviously, what are some of the ways that folks can effectively figure out where the problem is and maybe solve the problem?

#### Michael

So I don't mind given some of the content. There's a lot of content. So yeah, there are a lot of things. That depends if your bug is a logical bug, like your bug can be a crash, right? But let's say it's a logical book. So if it's a logical bug, that reproduces on your development machine, your situation is great. You're in gravy. But it's not always the case. Sometimes it's in production. And placing a breakpoint in production is not always available. It's a problem. Because if you stop on a breakpoint, even if you succeed, even if you remotely attach a debugger to to the cloud, then your server will stop. It will stop serving requests and that's not something you can afford. So there are ways to do production debugging. For example, if you have a failed request, and it ends with an exception, there are techniques to get that the information of what happened without attaching a debugger. One of them is to create a dump file when an exception happens, not when a crash happens when an exception happens. And then you can get that dumb file, copy to your local development machine open in Visual Studio and see the problem. There are other techniques. You mentioned, log files, log files are great. They're very useful for logical bugs. There is also the issue of optimised code versus not optimised code, which is when you debug something in production, then it's usually almost always you're going to deploy optimise code because it's faster. Right and debugging. optimise code is a problem. Because when code is optimised it in lines methods, and I'm getting a bit technical here, but sometimes breakpoints won't stop and you wants to local variables. So there are ways to restart your process. And even though it was compiled to be optimised, you tell it Don't be optimised. Right and then reproduce the problem and then place breakpoints or whatever.

#### Jamie

I think this is where especially for .NET devs, like yourself and like me, learning what the symbols file does, I think that should be before you learn about the tools and the techniques and how to divide and conquer. Symbols files, right? Because I remember at my university course, it was almost entirely done in C#, we did a lot of c++ but the basic stuff that we did like programming one on one, the very first course we did was, is C# is Notepad. There's the compiler, we didn't even touch Visual Studio for months, right? And then when we did touch Visual Studio, it was like, okay, right, let's talk about symbol files. And they talked about how they, how they work, what they are, what they do, but I feel like a lot of the trading doesn't talk about those kind of ancillary, these connected things like the simple fast get deployed to your server as well. So then you can get that debug information. But hardly anybody uses them. Right? I've worked with many teams and they've gone okay, right? Where's the symbols? What do you mean? Where's the symbols touch? Show me the debug information. What debug information?

#### Michael

Yeah, symbol files, not everybody deploys the symbol files. But even if you do deploy the symbol files, you need the exact source code for the version that it was compiled for. And then if you don't have like a mechanism where you save that information somewhere, and there are technologies for that, I'm not going to get into it, but you can do it automatically. So even if you don't do that, and even if you don't deploy the symbols, there is a way to debug with decompiled code. There are several ways I mentioned just one which is there's an amazing tool called dn spy. It was created by an anonymous user, an open source project, where you can debug a process without symbols. It will show you decompiled code which is very simple. Similar to the original code, usually, and you can stop on breakpoints, you can investigate variables, you can do anything. So that's one option to the

#### Jamie

Absolutey.

### Sponsor Message

This episode is sponsored by {{< sponsor-link link-text="ConfigCat" link="https://configcat.com" >}}

ConfigCat is a feature flag service.

- It has a central dashboard where you toggle your flags visually.
- Hide or expose features in your application without redeploying code.
- Set targeting rules to allow you to control who has access to new features.

Easily use flags in your code with ConfigCat libraries for .NET and 9 other platforms. Get builds out faster, test in production, and do easy rollbacks. Release new features with less risk, and release more often.

With ConfigCat's simple API and clear documentation, you'll have your initial proof of concept up and running in minutes. Also, train new team members in minutes and don't pay extra for team size.
With the simple UI, even product managers can use it effectively.

You can try it out with their forever free plan. Or get 50% off any paid plan with code `NETCORESHOW`

Release features faster with less risk with ConfigCat. Check them out at today at {{< sponsor-link link-text="configcat.com" link="https://configcat.com" >}}

---

#### Jamie

We talked about how it's difficult to talk about debugging without talking about the tools. But I think it's worth potentially a course on debugging in .NET, a course on debugging in Python that goes on debugging and JavaScript, all of those courses will be completely different. But they'll have the same practical applications, the techniques, right. But because of the tools, they'll be different. I think it's worth noting that if you do want to learn debugging, for .NET, debugging, for Python debugging, for C debugging for go whatever language it is, whatever to react, Angular, whatever, you're going to need to learn the tools, right? You can't just go and now put a breakpoint in and that would be my problem solved. because like you said, What if it's a performance issue, what if it's only recreated on the server? What if you've gotten into some weird corner case where it only happens because this one is haphazard. happened in the past? I know if this there's a bug in an old version of OpenOffice. I think it's version two of OpenOffice. We're in writer, which is an application for creating documents on a Tuesday afternoon on certain systems you can't print because the printer is just not available, the set of situations to bring such a corner case that it was difficult to debug, right? What if in your line of business application, maybe a microservice, maybe a monolith, maybe whatever it is, you've entered into this weird corner case where Yeah, it will not work because something is wrong with the framework or the platform or the code or the garbage collector or any of these things, right? So it's totally worth learning the tools to be able to get yourself out of that corner case, because 90% of the time is going to be I forgot to parameterize my SQL hopefully, you're parameterizing SQL all the time, but maybe it's I expected my strings to be four characters or less someone sent in five characters drag, right? Okay, so I have to do a check for that. Or sometimes it's the database time now, it's relatively easy things to solve, but maybe you need a tool to do it.

#### Michael

Yeah, the tools are, make our lives easier. Those are there for us. And the problem is that if you don't know a tool exists, there is a good chance you can still solve the problem with the tools you do have, but it will be less effective. It will take a long time and you will be frustrated. And the the problem of you don't know what you don't know, is a huge deal in debugging. Because debugging is the game of extracting information. If you know it's not how to fix the bug. It's to find the bug, find the root cause of the problem. And the tools are, are for that tools. There are tools that help you get the most information, extract the root cause, and then you can fix the bug.

#### Jamie

Absolutely. I mean, you just think about the example that's been playing through my mind is like a crime scene. You Don't have an investigator go in or a detective go in and solve the issue. They've got to bring in effectively their tools. They bring in forensics, they bring in ballistics. They bring in experts, they bring in witnesses, and they piece all the information together. So that's what we should do. We should know that these forensics, ballistics, can you tell it'd be really good crime novels, right? But you, you bring in all of these things to help you solve the problem, right. And that's, that's essentially what we need to do. We need to learn that these tools exist. Yeah. And learn what the framework provides for us out of the box. Because, yeah, a lot of people, like we said, at the top of, like I've said about 400 times so far, is the debugging tool a lot of people is I'll just put a breakpoint in just f 11, f 11. f 11. out, there's the problem. And that's not always the case. Like you said, What if it's a performance issue? Yeah. How would you conduct an investigation into like a performance issue or a memory issue or crash, then assuming that you've got all the tools you need, and let's say you've written an app and it's running on a Windows environment. Right, just to make it easier because a large portion of .NET developers are from the windows ecosystem, how would you go about doing that?

#### Michael

So you know, you know, that joke about the buggin? How it's a mystery game where you're the detective victim, and also the murder. So how would you conduct the investigation? Okay, so it depends on the problem. Of course, if it's a crash, for example, then we have several tools. In Windows several crashes registered into the Windows Event Viewer, so you can easily like the easiest thing is to open the event viewer and you see a log of all the crashes and you can see the call stack and exception message exception details that caused the crash. Also, you can configure windows to create dump files automatically. And dump files is a representation of the process memory at a certain time, and you can open that damn file in Visual Studio, or there's some other programmes like when But Visual Studio is really the most convenient one, open the dump file. And you can see as if you were running it in Visual Studio, you can see the exact point of the exception and code that causes the crash course you'll see the code only if you have symbols and source files. Now performance, we also have some great tools. First, we can use performance counters. Performance Counters is a bunch of metrics in windows that you can find out about any process you can see like CPU usage and memory and an exception rate and the number of garbage collections, many things so you can deduct if it's CPU bound, or I O bound, like if it was along the network request, or if it was a lock contention, because you had one thread waiting for another thread because of locks. Or maybe it's a CPU usage, supers is probably going to be the easiest to solve. You don't have to start with that you can start straight with the big tools like with the performance profiler. There are several. But like the the concept is that you record the snapshot with the performance problem in, that happens. And then you can see in the performance profilers, which took what time? Which methods took the longest? What happened in those methods? What kind of code? Was it a network request? Was it a GC pressure, like a huge amount of problems are happening because of memory, because the garbage collector is not optimised. And a big percentage of the time is taken by garbage collection execution. And you can see that immediately in the performance profiler. It's very easy. And then if it's a CPU problem, then you can see which method caused that problem. And you can even set it up to see which lines of the method cause the issue. And for memory, there are a total there's memory profilers, and memory leaks are a huge deal for memory, that we have those for everything.

#### Jamie

So then let's change it up. Right We talked about there's a bunch of tools to help you and we Talking about is Windows, you can look at the event viewer, but what about if I'm on a Linux environment? Right? We talked earlier on about a lot of people are publishing to Linux, because maybe it's cheaper or maybe it's more convenient or whatever the reason, maybe some process requires the ability to use some kind of Linux system, right? Well, if I published a Linux, I don't have the windows of MPR anymore, right? And I don't have automatic audience. So what happens that

#### Michael

yes, and Linux things with less dulling things are a bit more difficult. So one option with Linux, if it's in the cloud is to use the commercial APM tools, application performance monitors, they act as a performance profiler, but also they show things like crashes and request failures and a bunch of stuff. That's sort of the easy way out, but it costs a lot of money. And also there's a performance overhead. Now, suppose you don't want to use an APM and you want to find out about crashes. One way Linux does have dump files, so you can use them Sort of the Linux native dump files. But that's going to be a bit difficult, because then you'll have to debug them with Linux is native debugger, common land debugger, which is equivalent to when debug, some of the listeners probably remember it. It's a common line. So Linux has an equivalent to that with its own comments. So for .NET developer, it means they'll have to learn a new technology. But as of .NET, core three, there was a tool called .NET dump from a mistaken in London called freeze decay. And then you can attach the process into create them files. And then you can debug it on Linux with the same interface like when debug, so you'll know the commands and you'll see you'll have all the stuff for managed code, which is something that developers are used to, in case of a performance issue on Linux, and .NET. Core three as the K also has a tool called .NET. Collect or you can Record the snapshot, copy to Windows machine open with perfu, which is an open source performance profiler, also by by Microsoft by Vince Morrison, which is one of the chief architects in there. It's not easy. It's not an easy tool, but it gets the job done. It's very powerful. And in case of memory memory still, like memory profiling is still a problem on Linux later. I hope some of the, like JetBrains I hope they support dot memory. On Linux, some,

#### Jamie

there isn't a solution yet. So there's a number of tools and we're ripe for innovation, right? There's a number of tools that require you to learn another system. Or maybe you could bring in a Linux expert and say, Look, my app has died. I've got this dump file, can you have a look and just debug it? Or like you said, pull it over to Windows and do it that way? Either way, you're gonna have to learn a debugging tool that when debug or the Linux equivalents, right, you can have to learn to read these core dumps, I guess So that makes sense. So we've talked about Windows, we talked about Linux, that's fine. But what about if it's in production? Because usually, like you said earlier on, you deploy to production. And perhaps your code has already been optimised or so one of the big things and I think .NET core three is that your code gets rejected each time around. So then essentially, it can be re optimised and re optimised and re optimised. So you may have had 15 requests go through only three of them succeeded because every time through it's rejected it and change the code. And then what about we live in a world that uses and playing a lot of buzzword bingo today, we live in a world of continuous deployment, right? Keep pushing all the changes to production constantly, because we're apparently Netflix and we want to use that route. Well, what if the version on production is five steps behind your local dev or maybe 20 steps behind your local Dev, and you can't debug because the source code has changed, not just on the server because it's been rejected rejecting time compiled. But it's also the source code that was done to there is 15 steps behind what the source code on your machine is. Yeah, right. What's how in the heck do you do that.

#### Michael

So there are a couple of technologies, where you can automatically in the symbol files, save a link to the source code, the exact commit. And this way, Visual Studio support this, when you open and say a dump file, then in the symbol file, it will automatically pull that source code from geek or from CFS FEC or whatever, and it will connect them it will match the symbols and source files, and it will work. But that's just part of the problem. You mentioned optimization that doesn't solve the optimization. Also, it's a solution that you're gonna have to make a lot of effort to implement. It's not that easy. You have to set it up. You have to set up it in Azure DevOps or whatever pipeline that you're using. It's not that easy. Now, the code optimization. It means that when you do open when you do debug whether you attach to the process or when you open a dump file, some local variables won't be seen. And the cost x will be partial, because code optimization also in lines methods, it makes one method and be part of experiment methods. So one way is not to deal with that is to get partial information. And maybe that's enough. Another way is that you can tell the JIT compiler don't optimise in runtime. And then you restart the process. It's not going to be optimised it's going to be a bit slower, but then you can debug and find information. Another way which about the symbols is, don't bother with everything with the sim don't bother with the symbols is to use the Inspire or dot pick with dot because a decompiler by JetBrains that can act as a symbol server with decompiled code. What that means is that you can attach process that without source code and symbols, see the decompiled code stop on breakpoints, and so on. So maybe don't bother.

#### Jamie

The more that we've discussed this, it seems that deploying code with the ability to debug it requires a lot more than just push it to the server and hope for the best. Which To be fair, a number of people that I've worked alongside have in the past have done that they just push it to the server will get an error report and won't be able to figure it out. Don't worry about it.

#### Michael

That's one way to approach things. Again, it's not so easy that if it was easy, there was no need to write a book about it. There are a lot of subtleties.

#### Jamie

Okay, so we've got framework and we've got core and obviously mono and all the other platforms and stuff but are there differences in how to do debugging in framework and debugging in core? Now obviously, it's the same tools you may be using Eastern maybe still using Visual Studio maybe still using roadie and maybe still be using dump files and stuff but what else The differences or is there a difference between debugging framework and debugging? Cool?

#### Michael

Yeah. So under the hood, it's a different debugging engine. But Visual Studio when you attach the process or open a dump file, it automatically recognises if it's .NET core or .NET. framework, and it uses the right debugging engine. In almost all cases, you don't have to worry in such cases, you do have to know this. And you're going to have to tell Visual Studio when attaching use this debugging engine. Most tools on Windows to support both .NET core and .NET framework, like the various profilers and the debuggers. When debug and all those tools, everything is supported for .NET. Core, as well.

#### Jamie

So from a user interacting with Visual Studio, there's no real difference. It just does the things behind the scenes to actually allow you to continue your journey.

#### Michael

Yeah, there are similar screens completely seamless.

#### Jamie

Let's say I've got my app ready. I've got my system really I got rekt apply to is your deploy to AWS or deploy to, I don't know, Stevens code system on cloud or whatever, I deployed to some cloud deployment system because I want my app to be infinitely scalable and always on all of these wonderful things. And then a crash happens. And then like, you know, if it's on prem, I could go on to the server, I can remote to the server and do what I need to do and get the files out, but it's on some other system and I can't get access to it. What do I do that,

#### Michael

so if it's a virtual machine, maybe you can remote desktop to that machine. And it's not always virtual machine, but if it's a virtual machine from remote desktop, and then you can open Windows Event Viewer and see the cost of the exception, or you can set it up to create dump files, then you can copy to the development machine, open the dump, file and investigate. If it's an Azure App Service, then you can't remote to that. You have common land access. In that case, there are many tools were in common line you can create them files automatically when a crash happens. One of those tools is the programme. It's part of the system ternal suite. It's already pre installed on any Azure App Service. And you can tell programmes to attach to that process, monitor it when a crash happens, generated them, copy the development machine open in Visual Studio, and investigate.

#### Jamie

So there's a command line app, it's always running that you can say, get that thing and tell me if something goes wrong. Now, we talked about Dev, we talked about Ops, when we say how that everyone should be like DevOps, everyone should have access to what they need to get. only a very small team of people should have access to the live server, right? I shouldn't, as a developer be able to access a live system that I shouldn't have access to. So what happens if I'm one of the many people who don't have access to that server? I can't get permission to get probed and running what happens in

#### Michael

so you can bet case you can use the US code.

Let's go to it has the feature of Personally Identifiable Information, it redirects private information sensitive information. And when a crash happens, you'll be able to see in a sort of ID in the browser of the code without a credit card and stuff like that. But that's a problem because the dump file contains sensitive information, and not everybody should be allowed to access to it.

#### Jamie

Absolutely. Okay. That was my main worry, right? You took a dump of the memory for that process, right? Let's say you're dealing with credit card transactions, and for some reason, you have a customer's name, address, social security number, credit card number orders, how much they've spent on this what they're actually buying, that's really confidential information.

#### Michael

Yeah. It's going to be in memory and valuable content that information.

#### Jamie

Exactly right. And and you know, there's there's all sorts of new laws coming into place. Now. We talked about GDPR. We talked about, there's one for California I keep forgetting the name of and each jurisdiction each country will have its own privacy and data will So, taking that dump of information, if someone's real, a real transaction in process, and just, it's fine, I'll just put it on my computer. And I'll look through it. That's a big problem.

#### Michael

Yeah, it's a huge problem.

#### Jamie

So then things like the stuff that AWS code does, I think data don't do something similar. But let's say tool agnostic, right? You need to have some tool that sits there and watches the code and gets that memory dump. And you mentioned that I was going to make a tool that will do that, and then scrub the personally identifiable information. Okay, so I've done that I've never called dump or I can then put that into Visual Studio and just go Oh, right. Yeah, I can see that then. Then I can apply the techniques, right, that you talked about in the book.

#### Michael

Yeah. So with the US code, it's not you don't actually get the dump file, because God saves that from you. Instead, you see say there was a crash or an exception. You can see in the browser and add, like there's a studio within the browser, where you can see the code you can see the call stack that led to the exception and the person information will be scrapped. Yeah, then you look at that, hopefully the personal information is not needed to solve the problem. You've tried to figure out okay, there was a divide by zero exception. There you go. Yeah. In some cases, with Oscar with a dumb file, you can take, suppose there was a request, were eventually caused to an exception, and something that reproduces just in production. And in which case, you can take the payload that lead the request, place it in your local environment in your development machine, and try to reproduce locally. That's a good technique to solve a box.

#### Jamie

That makes sense, because if it's the input that's causing the issue, you need that input. Yeah. My silly example from earlier on, I have a method, I pass three into it, I get five, I pass four into it, I get 10. I need to know why it's getting into that state. Or maybe it's the data coming in, right. Or maybe once the data is coming in, it's doing some transformation on it and then it's passing it on without having that data. I won't know whether the transformation In this correct or not, whether or not we do test driven development or not, we talk about having unit tests, integration tests, full suite of tests. But who tests the tests? Who ensures that the tests cover enough of the system and enough input data and enough stuff to guarantee that it always works? No one can write we talked earlier on about we write buggy code, as developers doesn't matter where you are in your career, you're gonna write buggy code. If that's true, then it must then follow that you potentially wrote buggy tests, right? So you can't always rely on the tests, you have to rely on the actual state of play in production, to actually give you information about what went wrong. Yes, you can use that information to then create a test which tests if I give the system bad data, does it crash or does it heal itself? Or does it log something, raise an exception and tell the user you've been a Wally? You've given me the wrong data. But without that information, you can't build the test to ensure that it doesn't fail again. Yeah,

#### Michael

that Sir, not a magic solution to all your problems, you're going to keep having bugs, probably, you need to test correctly. And you're probably not going to cover all the cases. And you're definitely not going to cover the scale and the that you get in production. And also, if you have tests and they fail, for example, just in the build server, that's a whole new problem that you need to debug the test the film The build server. So it introduces new problems as well.

Unknown Speaker  
Absolutely.

#### Jamie

And I think that, for instance, I'm going to play buzzword Bingo One more time. If you're moving from a monolith to 100,000 micro services, that's gonna be a pain to debug, because in the past, you've had one lump of code on one server in one process that you can debug easily. But if you've got service a call service B, call service equals service D, and service c fails, what happens that that becomes harder to debug. And I think that just relying on tests and logging and I talk about logging. But let's just pretend that logging doesn't exist, right? Because a, you never log in of data. And B, when you have logged in of data, you're never going to look at it. And see, all that does is it slows the server down because there's 100 million gigabytes of logs that you never look at.

#### Michael

Yeah, definitely logs is always a problem. Because when you do need them, just the exact log that he wanted, isn't there, then you need to add lobes the plugin, wait for the bug to happen again, get the right logs and see. And micro services is a huge problem to deploy micro services has a lot of downsides. And one of the downsides is the ability to debug it's harder. So you can give like a correlation ID to each request. And whenever it moves between microservices is going to have the same correlation ID. Then when you investigate those logs, you will look for that correlation Id get the output from all the services and actually asked God what we're doing is When there is a problem in a request, when it failed, or when we place a breakpoint, we track all the micro services that the request passed through. And we will show you the path of between the micro services with the payloads and the entire information. Without those cordia you're gonna have to rely on logs in there. It's not it has its problems, then you throw into the mix

#### Jamie

async Yeah, you've got an async event queue. And then everything goes completely wobbly because well, what if the Event Queue dies? Or what if it feels very much like my own personal experience? Right, so this is personal experience of me, Jamie the person. I've seen microservices implemented wonderfully. There's redundancy, there's logging. The problem is that your three line microservice then becomes 2550 or 100 150 lines just because it's got all of this redundancy in case something falls over. And then I've seen microservices where it's just been added, throw it out there and see what happens. We'll throw all the code on the wall and see what happens. You Got a three line microservice talking to a three line microservice, talking to one event queue that then dies and you lose 100,000 transactions and your business goes under, right. So it's like, it's finding that happy balance between the two is almost impossible. And I think maybe the future is installing tools like AWS code or data dog or whatever, you know, all these hundreds of tools that help you figure out what's going on. Because I kind of joked earlier on where where I said, you know, what, we're clearly as big as Netflix, we'll just throw everything at the cloud and see what happens. And the problem with that is, of course, you want Netflix, you don't have 100 million customers, you don't have 100,000 servers. You have one server, you have three customers as a plan to scale out definitely. But don't start with we have to scale to a million servers because it's going to take you years to get there.

#### Michael

Yeah, don't do any premature optimization. Exactly.

#### Jamie

Was it that I think that was wasn't that was that Dykstra enough That's right. Donald Knuth. premature optimization is the root of all evil. So the books and practical debugging in .NET,

#### Michael

practical debugging for .NET developers?

#### Jamie

Sorry for .NET developers. That's it. What's the target audience? Do you aim to teach debugging as a hero tools? This is a process or is it more a case of give us an introduction to the book?

#### Michael

Sure. The target audience. It's a it's intermediate and experienced developers. So in the book, there's sort of three parts to it to teaching how to debug. One part of it is the tools. I showed the tools, I explained what information these tools can give you. The second part is we go from instead of focusing on the tools, we focus on the problem types, and then say we have a memory problem. So I explain what kind of problem we have. What's the investigation process, when dealing with that problem? Which tools should you have And then the final part is common patterns that lead to problems and common solutions. Because in most cases, not all cases, but in most cases, you're going to have, like the 80% of problems will be similar will be of common patterns, common patterns or common ways to recognise those issues. And also proven fixes for those problems. So and the book, it explains all of those, I also decided somewhere in the start of the book to create a video lessons as well, because some of the tools are not very easy. They're okay if you know a little about the tool and then explain it in the book, kind of understand the missing pieces. But if you don't know the tool at all, unless you instal it and write screenshots and the book is not enough, so I decided also to do video lessons. And there are about five hours of video lessons to company in the book. Yeah, so that's about it.

#### Jamie

It's difficult to describe either in words or in audio, how our visual system is put together, right? So, you know, rather than say we've got a file and then new within take this thing, you know, go to this tool menu and click that button and what if the user interface changes in audio, that's a huge problem in video, you can kind of go well, this is where it is in this version, and later versions may change we need to we don't know. But at least then you can see roughly where on the screen those tools used to be. which then means you can search for them or you can look at the change logs or whatever. I can appreciate that as a as a developer having some kind of video to fall back on as well. I've read the book I get the point I get the information. But now I want to see in actual use because it's easier to see them in use. Right. That's why Pluralsight is huge. That's why Demi's huge wireless way. live coding is huge. That's why YouTube has a whole bunch of video tutorials on how to do stuff because it's easier to be walked through the user interface click this button, click this button. type this command in even if it's a command line system, type this command in and you can see it happening, right? It's like it's animated, animated videos of how the process work easier to follow. Then read this paragraph now read this paragraph now read this paragraph, right? Because eventually you're going to stop breathing.

#### Michael

Yeah, that's how people learn to the people learn a lot from videos. And the book also has a lot of advantages, because in the book, you can, well its first its reference, right? If you forget something, go to that book. You don't need to see the video all the way from the start, and then stop a trade the right minute. Also, you can skim through stuff that you already know in a book. And what I think a lot of more effort goes into a book. Because you sort of work on each sentence on each word and you I think the quality of books is higher than that of videos, almost by definition. Yeah, so books aren't replaced yet. laughing in my videos,

#### Jamie

so we're recording this a little ahead of time. And there's still some effort required to sort of finish to finalise the book. There's still a few stages left. And I think we were talking off a I think you'd said there isn't quite, you don't know quite where it's going to be published yet. I think you said it was going to be self published. I'm just thinking, working folks find out more about it when it does come out. Is there a plan for that yet? Or is it still still in the planning stages?

#### Michael

Yeah, so it's going to be published on Amazon. But also, I have a website, practical debugging .NET where you can get an ebook and the videos and the printed version is on Amazon.

#### Jamie

Okay, excellent. So um, when you're listening, check the show notes in your podcast player or click through to the full website. I was better transcription up there as well. So if there's a part where I fumble through and you're not quite following what I'm saying, scroll through and you can actually what's great about that is if you want a quote or something, it's right there. You can Ctrl F and search through text. You can't do that through audio right? So make sure you go through to the shownotes. Because when I put this together, I'll reach out to Michael again and get a bunch of links to maybe on Amazon and maybe the E book page and stuff like that all of the information that you need will be in the show notes. So definitely check through to those. So what about catching up with yourself and Michael, what was the best way to do that? Is Twitter a thing? Or is it more a case of just checking the blog or swords? What's the process for that? I'm mostly active on the blog can also catch me on twitter at Michael spelt. Excellent. So we'll make sure to drive people towards the website. So check that out. Because honest opinion. I want to learn more about debugging. You know, I know a little bit about symbols and I know that a lot of people that I've worked with in the past I don't know whether it's coincidence or not. They don't really get debugging. It's just a case of well, I still hear it today. Well, it works on my machine. That's not the point is broken in production. go fix it. Yeah, but it works here. I don't care. It should not be it works here. So I stopped working. You know should be who works here, but it doesn't work there. That's a huge problem. That should be your first step.

#### Michael

Yeah, responsibility you're responsible for your code. And it works on my machine is is not an excuse.

#### Jamie

Exactly right. It shouldn't be because like I said, if it works on your machine, but it doesn't work in production, then that's a huge problem. Because there's some kind of disconnect. Or if it works on your machine doesn't work in QA, but it works on production. We'll skip over how it got to production after QA failed it. But if it works on your machine fails at QA, but works in production, then there's something in the middle of that needs to change. I can see why this is one of the reasons why people use containerization, Docker, Kubernetes, whatever. Because then you don't have to have the works on my machine. It doesn't work over here because your entire development, test, user acceptance, whatever you call these stages. Each of those stages is running the exact same operating system, the same tools the same, everything.

#### Michael

Yeah. As professional software developers, we should have a code of ethics Or something like, Uncle Bob Martin talks about this or we should be responsible for the code. Right?

#### Jamie

Exactly. And it should be a case of if there's a problem with the code, we should all come together and go, right. Okay, how can I help? Is there a way for me to help? If it's code that someone else has written? Well, it's not necessarily their code. It's the team's code, right? So the team needs to get together and say, right, what can we do to fix this? How can I help? Is there anything I can do? Or should I just leave you to it? Or you know, what's, what's the problem? Yeah, definitely. Thank you for having the chat with me today, Michael, I'm eagerly awaiting the book, I have to say, and I'll make sure that there's a link for people to click through to check that book out. Because I think it's going to be an interesting read. And like I say, I think there's a definite gap in the skills. Maybe Maybe you can start doing courses on how to debug in .NET. What is a symbol file? What is this? How does this work? Maybe Maybe I'm just making work.

#### Michael

Thanks for having me Jamie. Hello. Have fun.

#### Jamie

No worries. Thank you ever so much.

{{< paracentre "The above is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

### Wrapping Up

That was my interview with Michael Shpilt about debugging. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/), and there will be a link directly to them in your podcatcher.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice - head over to [dotnetcore.show/subscribe](https://dotnetcore.show/subscribe) for ways to do that - and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Michael on TWitter](https://twitter.com/michaelshpilt)
- [Michael's Coding Spot](https://michaelscodingspot.com/)
- [Practical Debugging for .NET Developers](https://practicaldebugging.net/)
