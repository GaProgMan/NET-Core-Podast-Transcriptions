# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is episode 22: The NUKE build system with Matthias Koch. In this episode of The .NET Core Podcast, I talk with Matt Koch about the NUKE build automation system, clean code, and configuration as code.. Matt describes himself as is a lover of clean code, API design and software architecture. He started with NUKE in 2017 while looking for the perfect build system for one of his open-source projects.

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Matthias' Introduction

**Jamie**: 
So thank you for being on the show, but this is it, Matthias or Matthias? Which would you prefer?

**Matthias**: 
Well, in Germany would say Matthias which sounds boring. So in English I usually prefer to be called, like, Matt or something.

**Jamie**: 
Okay.

**Matthias**: 
We have a second Matt on my team at work, which makes things more complicated.

**Jamie**: 
At my first programming job, there was already someone there called Jamie. So when I joined, I became two point zero.

**Matthias**: 
That's actually really funny because during school I never got to to meet another one called, like, me. But during university and starting there like everyone was called Matthias. I was was just crazy. I know just from that point. So anybody Matthias people.

**Jamie**: 
So I thought maybe before we begin, you could be introduced yourself to some of the listeners.

**Matthias**: 
Yeah. So my name is Matthias, and I worked as a developer advocate at [JetBrains](https://www.jetbrains.com/), usually for the .NET department. So everything about Resharper - which is an extension for visual studio - and  Rider - which is stand alone .NET IDE for cross platform basically, so not for any particular platform.

And yeah, I love my job so you can ping me whenever someone has questions about that. But today I guess we're talking more about my open source project, which is called Nuke. And I've been working on that for a couple of months. So I think I started in 2017, so last year at the beginning of last year. And that's basically my my current hobby.

**Jamie**: 
Cool. Okay, I read a little bit in your [GitHub work](https://github.com/matkoch) and, you know, on [your website](http://ithrowexceptions.com/) and things that you have also created a few other open source projects called [TestFX](https://github.com/matkoch/TestFx) and [SpecK](https://github.com/matkoch/TestFx/wiki/SpecK). I wonder whether you could talk a little through those.

**Matthias**: 
Yes. So that was, it seems like faraway, already.

TestFX was like an approach to introduce a framework for building test frameworks. Currently, those those test frameworks, they're pretty much about having methods as as isolation level. Also declare a test method, and inside you declar the test. And TestFX was sort of like a way to break through that so that you could declare test based on statements a statement level, for instance.

What's the benefit of that? That is that you have more context, right? So if you're stating the action of a test - like action in terms arrange act assert - if you state the action first, then you have a lot of context like result type and so on. And you can can build up a fluent API from that.

And that that's also the downside. Or was the downside of that because too much fluent API - that that's something I learned from that - can also be like an obstacle in getting things done because gets too complex. Yeah, that that was it about TestFX.

TestFX was basically the platform and SpecK was like like an implementation, an example implementation, for for the platform.

**Jamie**:
Interesting.

**Matthias**:
But that's fine because I was always looking for, I mean I did that over three years, and I knew there it's probably nothing to be introduced in big companies because it was like in tooling for to certain extent, is trying to work things out about that. But eventually I got into this situation where I said, OK, I want to have good build automation, then I looked at some of the available options. And, I think, like three months later or so, I started with Nuke.

**Jamie**: 
So that leads us nicely into Nuke. So could you give us a quick description of what Nuke is.

**Matthias**: 
So Nuke is a build automation system, similar to if you have heard about [Cake](https://cakebuild.net/), for instance, or [Fake](https://fake.build/). So usually they all follow this naming pattern. And build systems are aiming for automating the building of software, right? So that includes certain steps like compiling the solution and converting it into NuGet packages. For instance, I guess that's pretty common for everyone working in .NET. But also other things like uploading things to an FTP server, whatever you can think of.

So everything that you would like to automate, like with every commit to Release branch or a Master branch, whatever you can think off. That can be done with build automation systems. And they will. You just help you to put everything into the right place and call that in a convenient way.

**Jamie**: 
The idea with Nuke is to provide this service of automated build tool that can do off the things, like you said, similar to Cake and Fake

**Matthias**:
Yeah

**Jamie**:
and to package it to NuGet if you need it, and things like that.

**Matthias**: 
so it acts as a platform and provides a lot of the predefined tasks - we call it that way - so something like invoking MSBuild, for instance, as a command line tool, so MSBuild.exe, for instance, or the .NET CLI, that you can do in a very convenient way inside Nuke. And all those calls to tasks are usually encapsuled into targets. And Target is like Unit inside your build automation chain that you can call either as a single invocation or single step, or in build automation there's common thing called Dependency Model. Or the second way is to say, "OK, I have the pack target," for instance, "and in order to be able to call pack, I first need to call compile." And that's something that the build system is helping you with, because you can basically defined dependencies between those targets. And the build system will build up something called Dependency Graph based on that information, it knows which targets to invoke and which targets could be skipped.

**Jamie**: 
I've seen on the website that, I think there are two types of Nuke. There's that .NET Core global tool and you can have scripts. Is that correct? Am I reading that?

**Matthias**: 
Not exactly, no.

So there is a global tool, and so that's really the thing I guess for for your podcast also, because it's all about .NET Core. And those global tools, I was really happy reading about that when it was released because I instantly knew how this can improve the invocation of the Nuke, right?

What you have seen, those scripts: if you set up a repository with Nuke and you want to introduce Nuke as a built in system, then what it does is to create two bootstrapping scripts. Which is a PowerShell script for Windows based systems, and Bash shell script which can be executed in all Unix based operating systems. And those bootstrapping scripts are basically just taking care of the Yeah, doing the bootstrapping. What they do is, if you don't have that installed locally already than they will download the .NET Core SDK because that's a requirement for compiling the build program. So I wouldn't call it build script anymore, actually, because what it is, it's actually a built program encapsuled inside a normal C# project. That's the new thing about Nuke I guess, compared to others.

And because you have those bootstrapping scripts you can invoke the build everywhere. So even on a freshly set up Windows machine, for instance, you could check out the repository and at least the build project would compile because it knows how to download the .NET Core SDK. And the global tool, on the other side ,is just more convenient way to invoke those bootstrapping scripts.

So what you can do is compared to before, on Windows you would say PowerShell `./build.ps1`, for instance - different on Unix systems. But now you can, on both operating systems, just type `nuke` inside the repository, and it will find those bootstrapping scripts and invoke them for you.

**Jamie**: 
I really like that ability to, regardless of how I've set up my machine, I can pull the repo on the least build it. Because that's the biggest barrier to entry I feel, when you're working on a new, rather a project which is new to you, but a preexisting project, if that makes sense. So someone else is already working on it and you pull the code, "right. How do I build it?" That's the biggest barrier to entry straightaway. "What tools do I need to install to be able to actually build and run and edit this code base?" And if I could just type in `nuke` at the CLI and it just doesn't work for me, that's fantastic.

**Matthias**: 
Yeah, right. And one one small thing about that as well, is I kind of like that you can be wherever you want inside the sub-folders of your repository. So even in a very deep sub folder and you can just type `nuke` again, and it will recursively scan upwards through the directories and try to search for that certain marker file we have in place - its just called `.nuke` and that will mark the root directory - and you can execute a build just with same command. So usually if you have just those bootstrapping scripts and you're like messing around with your build and navigating somewhere, you would need to take care of the relative paths right, and go upwards or have second shell available. But there you can, yeah, just be anywhere and invoke `nuke` again. Just like that.

**Jamie**: 
I like that because I greatly simplifies, like you say, say you have to climb four or five levels deep into your subdirectories to change something, to change some file, to fix some bug. Then to rebuild, if you're not in Visual Studio or Rider, for instance, you may have to, like you say, traverse back up to the root of your project or at least to where your project file is to be able to type in `dotnet run` or `dotnet build`. Whereas Nuke allows you to, from what you've said, it will take care of all of that business for you. That's incredibly useful

**Matthias**: 
Yeah.

And just another thing that we've added about two months ago, which also incorporates the global tool, is the ability to complete parameters that you define in your build script or build program, I'm sorry.

So if you if you have ah, parameter like API Key, for instance, if you plan to push your NuGet packages to to end point. Then you can, with the Nuke CLI, you can just type `--` for the parameter, then maybe in `a` and then hit tab, and it will complete the parameter for you. And there's also completion for targets and so on. That's the reason why I said this global tool thing for .NET Core is just such a great way to avoid all those messing around with bash scripts and PowerShell scripts.

Very early in the beginning, we had the set up completely in bash and PowerShell, and that was so fragile. You always had to keep them in sync and with with those global tools, you you don't have that issue anymore. You just have your implementation in .NET. You can be sure it can be executed on both systems, and that's all you gonna need to know, right?

**Jamie**: 
I get it. Could you use a Nuke on the build server as well?

**Matthias**: 
Yeah. So on the build server, usually I would prefer to invoke the bootstrapping scripts because installing the global tool is not really of use. The two advantages I explained are, there's no use for them on the build server, right.

Although just just recently, a very big project converted to Nuke, which is [AvaloniaUI](https://github.com/AvaloniaUI/Avalonia). And, yeah, I kind of reviewed some of there approach to introducing Nuke, and they were just installing the global tool on the CI as well.

**Jamie**: 
Does Nuke help to create these bootstrapping scripts? Or do I still need to, sort of, hand roll those bootstrapping scripts?

**Matthias**: 
No.

That was one off the intentions I had initially. Because messing around, like I said, with those shell specific implementations can be really annoying, especially if you want to have a cross platform build which works on both systems. There can be a lot of work that is needed to make it work on both both systems, and those two scripts are completely or generated. But in case you have additional things, you would like to be involved there then, of course, it's also possible to just customise them.

**Jamie**: 
So looking at the documentation, there's a lot of C# stuff. So there's the global tool, which is the .NET Nuke global tool. Then there's also, you could work within your IDE to do Nuke stuff. Am I reading that correctly? So I can create a build, which is just a class, and I can add some targets and some operations to perform within those targets.

**Matthias**: 
Right. So the initial thought was also to make it as the less complex as possible. You say that, yeah, less complex?

**Jamie**: 
Yeah, that makes sense.

**Matthias**: 
The idea was to just use a C# console application, and that's what it is.

So those bootstrapping scripts are just compiling that console application, and then it's getting invoked. And the big benefit is that we get all the IDE tooling that is available already out off the box. So there's no additional work to make with refactoring work, to make debugging work. I never managed to debug an MSBuild file, right? I know it's possible, but that was always such a, even just thinking of that made me headache. And that's one thing in Nuke, dont't have to worry about that. It's nothing you need to read documentation about or anything.

We made the switch to get away from using magic strings as target names, so usually most of the other build systems, they use string declared targets. Like in MSBuild  for instance, you could say my favorite is if you have a target in initial initiative, that's a hard word.

**Jamie**:
Initialization?

**Matthias**:
Yeah, exactly. That one can be written with s or z that right? And, you can make this mistake and in Nuke however, those names are actual symbols. Because of that, the type system and the compiler can help you to spot those errors, and it won't even compile if you have such an error. Meanwhile, with other build systems, you get a runtime error.

And back to your question about the extensions: Those extensions are usually just improving the already given experience with Nuke, especially in terms of the executing the built targets. So, for instance, in Rider you can place the caret inside a target declaration and the usual way and Rider and Resharper to hit `Alt+Enter`. And if you do `Alt+Enter` inside a target declaration, you get a nice little pop up, which lets you execute the current target that your caret is positioned in. You can execute that with all the dependencies, for instance, in debug mode, if you want, or just skipping dependencies, whatever you like.

And another extension is also available for VS Code because I want to make it approachable to everyone, of course. Something for Visual Studio is planned. But the extension model is different to what I'm used to with Rider and Resharper. And we're waiting, too.

One specific thing I can maybe just explain that is the VS Code extension has code lens providers. So you can have little code lens texts of off the target, which says "Debug" and "Run". And we intended to do the same in Visual Studio but it turns out they have a different implementation for code lens, and that won't let you have a text which is bound to a command that it's just invoked. What they have for code lens is just, some kind of graphical details window where you can also leave some some comments. That's not the way how we plan to make things work. So in Visual Studio, it might take a little while to have this code lens implementation, but we're thinking about maybe having the task runner being used for that. And the task runner feels similar - for everyone who hasn't heard about that - feels similar to like the Unit Tests Runner, for instance, and then you have just all the targets as a tree available, and you can just double click them and invoke them like that?

**Jamie**: 
Sure. Yeah, I remember back when I was using gulp and grunt to do bundling and magnification two or three years ago with my MVC applications.

**Matthias**:
Yeah.

**Jamie**:
So I'm familiar with the task runner because it's the same window. Isn't like you say you have a tree with, like b`efore build`, `build` and `after build`.

**Matthias**: 
Yes. Something like that. Yeah.

So one of the major build systems out there, which is even like, cross language, I would say that thing is Gradle. They built like this big empire, right? And was also kind of inspired by that because they have very good UI tooling in say IDEs like can InteliJ, for instance. That was a goal for Nuke as well: to provide the same level of integration. Because that, we talked about that initially, about my TestFX project that was one big mistake. I would say afterwards, I kind off reflected about that, and that was a big mistake: to not integrate with tooling as soon as possible. I think it's really important to take approaches which integrate natively without doing too much magic.

**Jamie**: 
Sure, that makes sense. The quickest you can get the tool into the hands of users, and make it easier for them to use it, I suppose.

**Matthias**: 
That's also we We didn't talk about. Usually it's always something that I that I mention during the introduction when I when I do presentations is: writing scripts, build scripts was usually a thing that was dedicated to a single person. Whenever I was working in a team there was one guy who was managing the build - or one developer, let's make it this way - managing the build. And if that someone is on vacation, then you're might be lost, right? Everything is standing still, and you have invest a lot of work to continue. And having pure C# for build automation makes this step little smaller, at least.

**Jamie**: 
Especially if you're using C# to architect your application logic, and you can use the same C# to create your build steps to package of your application logic, and create a binary or a NuGet package at the end of it. It makes sense because then, like you say, that reduces that barrier to entry: you don't rely on a single person or a small team of people who know the build tools intimately, and you don't get to a point where, as you said earlier on, you're trying to debug an MSBuild script and have no idea because it's so complex.

**Matthias**: 
Yeah, right. I very much like the idea, so this is not coming from me but Gary from from the Cake team, he once said in a presentation that:

> it's a good idea to use build tool which follows the same language as the main project language. So if your doings F# project, then use Fake and so on.

And I very much agree with that, because at first I also had the idea of, "Well, that's let's use Fake and learn a little bit more about F# as well meanwhile." But in reality, this works a little bit differently because you won't always have the time, in various situations, to just sit there and learn some new things to make the building work. So I very much agree on this point.

**Jamie**: 
Yes. I've seen it too many times and by relatively short career so far where the build has failed, and the person who is in charge of making the build work is, like you say on vacation, or maybe they're out with illness. And a small team of very dedicated people essentially try their hardest by a combination of slamming their heads against the keyboard, and going to Google to find out.

**Matthias**:
Yeah, right.

**Jamie**:
Whereas, like you say, if if we're using the same language that they were writing the application in, the theory is that you know that language anyway, so you should be able to at least follow along with the build system and find out what's going on.

**Matthias**:
Yeah.

**Jamie**:
Since Nuke itself is in C#, I'm not limited to a specific IDE for creating the console application, which builds my larger application am I? I could use notepad, TextEdit, atom, Visual Studio Code, Rider; just to, sort of, type it all in?

**Matthias**:
Yeah.

**Jamie**:
But, like you say, there are plugins for Visual Studio Code and for Rider; So that I can create my Nuke build system and then presumably hit F5, and it will actually build my application.

**Matthias**: 
Well, that usually not.

Well, it depends on the IDE you're using, but it won't replace the start project configuration. You can, of course, select the build project as being executed that's possible, but it won't do that automatically. So we're just orchestrating MSBuild or `dotnet`, whatever you you need. And by the way, that's one thing many people get wrong initially when it's also hard to communicate that. But being a .NET Core project, I mean the build project, it's still able to execute MSBuild on full .NET Framework projects. So this is not limited to the .NET Core world or anything because it's orchestration. It can work with whatever projects you have.

**Jamie**: 
Does it also support Mono, or is it just .NET Framework and .NET Core?

**Matthias**: 
Mono is also supported, yeah. But I don't think there's like special support for that. We talked about the bootstrapping scripts, and we still have bootstrapping scripts for full .NET Framework and Mono, so that's also available. But in terms of the invoking MSBuild, for instance, I don't think there's a difference on Windows and Unix about the invocation, at least because MSBuild can be found on Unix systems as well - if Mono is installed - and the only thing we have custom we made there was to find the tool path so the MSBuild executable on Unix. That's one thing we made customly for Mono support. Yeah.

**Jamie**: 
I see. So a couple more questions, if that's okay.

So the modern design principles are: you will have a maybe a single solution or a number of solutions in your C# application hierarchy. And let's say that you have a single solution and you have multiple projects within that: maybe a data access library, maybe a business logic library, maybe a WebUI, and perhaps also a separate WebAPI application. Is it possible, with Nuke, to build both of those: the WebAPI and the WebUI projects with the same Nuke console application build system? Or do I have to have a separate Nuke build system for each of my WebUI and my WebAPI projects?

**Matthias**: 
No, I would expect this does into a single Nuke build project.

The idea is basically that you have one build project per git or SVN repository - or whatever you're using. And if you need separate units for building, that is again a target. So if you want to build that separately, would have a build WebUI and build - what did you say? - WebAPI or something. You just have to different targets that he can invoke separately. That's also one thing that the global tool provides and even the bootstrapping script itself, if two targets don't have a correlation terms of the dependencies, then you can just separate them with the plus sign, I think, or space, and both of those targets would be would be executed. So it's very flexible also.

**Jamie**: 
Looking back at some of the example targets that there are available on the Nuke website - I'll put a link in the show notes - the targets seem very much like: So I've been doing a lot of PowerShell build automation recently, so I've been trying to figure out how to build my PowerShell modules into PowerShell scripts recently. And there's a, it's `psake` - so p-s-a-k-e - is a tool that I've been using to create build scripts for my PowerShell scripts. And they have a very similar field of them, I think, with a task, the name of your target, and then the actions required to run them. Was that something that you are aware of, or is that just something that is a common design pattern throughout the built automation systems?

**Matthias**: 
I was first to use of Cake.

And, of course, this also kind of inspired me, because they have this fluent API for configuring a certain target a little bit more, like with dependencies. But that's not the only thing I can add to a target, for instance, what we provide in addition to that like a condition: when a target should be executed. That is checked, like at Runtime, for instance, if a certain NuGet was already built by a previous build, you could, for instance, skip the pack target as one example.

And another thing is we provide a way to add requirements. My favorite example for that is push target, which would push NuGet packages and that would, of course, require an API key being passed from the command line, for instance. And putting a call to the `requires` fluent method on the push target, you could ensure that an API key was being added to the invocation, and that is even checked pre-build. What I mean by "pre-build" is that: this happens before any invocation or execution of any other targets. So even if the push target is eventually dependent on the clean target or compile target, then those conditions are checked prior execution to them. So you have a fail fast behavior of your build. You won't wait until all those targets have been executed, and then at the push target you realize, "Oh, there was no API key being passed so that wont happen."

And aside from that, what my suggests that way at least, to make it a little bit more readable, is we tried to advocate for using static imports. I think the best example is the `math` class, which has square root methods, add, subtract, and stuff like that. And if you've writing code with that, it's kind of annoying to have that `math.` written everywhere, and with static imports you can just import that `math` class, and have all the other methods that it provides - you can just call, as if there were declared in the same class you're currently.

And that's something we also use just for the matter of reducing like noise - I would call it noise because a build script is a very nice opportunity to design things in a readable way. I really have to point that out: if you like to do things like with real C#, right, and with real C# I wouldn't import statics all over the place. But my suggested way with Nuke is to just break out of the build declaration, and have it in a separate class, and there I can just start over with a different coding style, which follows the usual approach of C# style guidelines. Like, for instance, having a private modifier and so on. Inside the build declaration inside the build class, I'm usually trying to avoid that because it makes things more readable.

**Jamie**: 
Sure, that makes sense.

A friend of mine likens that to reading a newspaper. In that you need to be able to just look down the page and understand each thing at a high level: "Oh, yes. OK, so we're calling the `dotnet restore` action, set verbosity to maximum, set NuGet sources to a private NuGet feed." Whereas you don't need to drill down into the detail to find out how it's doing it. You just need to know from that top level 10,000 feet approach, "Yes, we're calling this command. We're doing this with NuGet, we're doing this with the verbosity." You don't need to go, "but we need to set it to maximum. And we need to call this particular version of the .NET Core SDK. We need to pass in the username, or personal access token, or whatever to get a hold of the NuGet feed, or the URL for the NuGet feed.: like you say, that could be abstracted away into some static class that you're pulling in somewhere else.

**Matthias**: 
Right.

So, for instance, for our web presentation, we also use Nuke for the build automation uploading to the app server. And in that case, for instance, were building, we're using DocFX for generation off the website. But we have a custom table of contents, and that method, or that target, that build step previously at least used Mono, and at some point, even reflection to gather data from all the packages that we provide. And that is a very good example - it used even Roslyn at some certain point. And that's a very good example because we were able to do that implementation, the very same build project and have it just called fluently, so if your debugging you can just step into that. And I think that would be impossible with MSBuild, for instance, to do that I don't know, like an inline task or something - are you familiar with that? But the usual approach in that case would be to make a console application yourself and invoke it from MSBuild. I know, for instance, the NodaTime project - which is maintained by John Skeet - he's making use off those dedicated build tools a lot. So there are several console applications, basically, which do a certain job, they are in his build script. And with Nuke, you would have just everything as the normal C# project.

**Jamie**: 
Perhaps we need to figure out a way of connecting the two of you together and see if we could make a Nuke build system for NodaTime.

**Matthias**: 
Well, actually, I tried to do that because I thought it's it's good PR for the project. And a few months ago, I approached John, and we're trying to; actually we converted some of the his build scripts into Nuke and he said, "Looks promising, but it needs a little more time to figure out some stuff."

We also got some feedback about minor things. One thing specifically was he said that with Nuke it seems more cumbersome to involve commands like - I'm not even sure what this stands for - `rm` is remove, for something on Unix?

**Jamie**:
Yes.

**Matthias**:
Right and I said, "well it looks  a little bit more, more complex in Nuke to do that," but meanwhile, we tried to work around things, and in this specific case, for instance, we found the solution: and that is that you can just declare a field which is called `RM` - so the field name is `rm` - the type of that field is called tool. And it also has an attribute which is applied onto that which says, "path executable" because `rm` is only reachable through the path environment variable. And Nuke will automatically resolve that and inject a delegate into that field, and that will allow you to call `rm` like it was a method inside the targets. So he can just do `RM("` and so on, and you've write all the other arguments that you would pass to the `rm`` command.

So if someone has a crazy idea about build automation, and they're not happy with our certain things work, I'm really looking forward to get ideas. Or you can just pointers to issues, how cumbersome something must be written currently, then this is like the challenge for me, too, trying to solve that because, yeah, I really like API design and stuff like that. I like that.

**Jamie**: 
Oh, okay. It's been a fantastic conversation. I have to say.

**Matthias**: 
Yeah. Been enjoying is as well.

**Jamie**: 
Where can folks go to learn about Nuke and maybe a little bit about you and to ask you more questions about Nuke, or to find out more information about that kind of thing?

**Matthias**: 
So the idea was established for build automation towards to use domain names with something `.build`; I think this top level domain is usually for something like companies which are doing like constructing buildings and something. So it's [nuke.build](https://nuke.build/), And also we usually rely on Slack, we have this like Slack workspace which is quite busy already. I think we have, like, almost fifty members there.

**Jamie**:
OK

**Matthias**:
With lots of questions. And, of course, we're using GitHub issues for reporting bugs if there are any. But we also have a gitter channel. We have a Twitter account, which I currently don't manage to use a lot because they're some other nice things that that need work.

**Jamie**: 
Okay. What I'll do is I'll collect a bunch of those links off-air, and I'll put them in the show notes. So fewer folks want to find out about what's happening in Nuke land, they can click through and find out, maybe learn some more about how to use Nuke, how they can contribute towards it. Because, I guess it's an open source project isn't it, if it's GitHub?

**Matthias**:
Its open source, yeah.

**Jamie**:
Okay, so folks can head over to GitHub, I guess, and have a look at the source. Maybe if they want to try and help out, they could look at an issue. Maybe put a little comment saying, "hey, I am looking at this issue. Can you give me any kind of pointers? Is Is it okay for me to take this issue and run with it?" that kind of thing?

**Matthias**: 
Yeah, Right.

**Jamie**: 
Okay. Cool. What about yourself? Are you okay with people sort of contacting you over Twitter or?

**Matthias**: 
Yeah, sure. Always.

**Jamie**: 
So OK, then we'll put a link to your Twitter in the show notes and see if we can get more success stories about using nuke on their systems and say, "Hey, this made my belt system so much easier to use, quicker to use or easier to change or something"

**Matthias**: 
Yeah, that's the thing I want to hear.

**Jamie**: 
Fantastic, yeah. If there are listeners out there who have used Nuke, please get in contact with Matthias and then let him know that it's going really well.

Thank you very much for being on the podcast with us.

**Matthias**: 
Yeah, it was really a pleasure.

**Jamie**: 
It was great being connected with you today and having this wonderful conversation.

### Wrapping Up

That was my interview with Matthias Koch. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and a collection of text snippets from the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/).

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Matthias on Twitter](https://twitter.com/matkoch87)
- [Nuke homepage and documentation](https://nuke.build/)
- [NUKE on GitHub](https://github.com/nuke-build/nuke)
- [JetBrains](https://www.jetbrains.com/)
- [Matthias' GitHub](https://github.com/matkoch) 
- [Matthias' website](http://ithrowexceptions.com/)
- [TestFX](https://github.com/matkoch/TestFx)
- [SpecK](https://github.com/matkoch/TestFx/wiki/SpecK)
- [Cake](https://cakebuild.net/)
- [Fake](https://fake.build/)
- [AvaloniaUI](https://github.com/AvaloniaUI/Avalonia)
