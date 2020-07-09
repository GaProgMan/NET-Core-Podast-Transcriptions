# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is Episode 53: The Desktop Story with Paul Michaels. In this episode I interviewed Paul about the Windows-based desktop development story when using .NET Core. You may know Paul from [his blog](https://www.pmichaels.net/), his twitter account ([@paul_michaels](https://twitter.com/paul_michaels)), or his new book [C# 8 and .NET Core 3 Projects Using Azure - Second Edition](https://www.packtpub.com/gb/web-development/c-8-and-net-core-3-0-projects-second-edition).

One thing to note about this episode is that the interview was recorded in advance of MSBuild 2020. At MSBuild, a greatly updated version of the WinForms designer was released along with things like WinUI updates and the announcement of MAUI - Multiplatform Application User Interface. As such, some of the points about the WinForms designer in this episode are based on an old version of it.

With that being said, lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Paul's Introduction

#### Jamie

So the first thing I'd like to say Paul is thank you ever so much for agreeing to be on the show. We're actually doing this on a Saturday afternoon, which, you know, if you're anything like me, then you know, Saturday afternoons kind of a lovely time to just rest up or watch TV shows. Or you spend time with family and friends. Or if you want me, you know, spend time in your basement recording an interview with someone who's pretty amazing at their job.

#### Paul

Thanks for having me on this. Great to come on. I'm a long time listener, so Yeah, Thanks for that.

#### Jamie

Your long-time listener, first-time caller as they would say.

#### Paul

Yep? Exactly. Yeah.

#### Jamie

Awesome! Okay. So for the folks who are listening in who may not know about you, could you give us a quick sort of brief introduction, to who you are and the kind of work you do. That kind of stuff.

#### Paul

Yep. So I'm Paul Michaels. I'm a lead developer. I work at a large company. Predominantly working in the web sphere, so your standard MVC type applications, a bit of React, so on and so forth. One of the things that has sort of driven me to seek you out and come on here is to talk about the upgrade to .Net Core 3 and some of the interesting things happening in the desktop sphere.

I don't tend to do a lot desktop development now, so it's quite interesting to kind of go back and and so of, I don't know if you ever saw [Bullseye](https://en.wikipedia.org/wiki/Bullseye_(British_game_show)) in the eighties, but this like "what you could have had". If this would have been around then. So, yeah, that's something that's kind of interesting me at the minute.

#### Jamie

Just for the international listeners and the youngsters among the audience, Bullseye was a quiz show but it had a twist in that they had professional darts players would play darts for you and score a bunch of points and you answer questions. But I think you hinted at that there was that the quizmaster would ask the questions a person would answer them, and if they failed or if they chose a different prize, you would say "Let's have a look at what you could have won." And it was invariably a speedboat, and they were always someone who was landlocked.

#### Paul

Yeah, I'd love to see the speedboats now and see what state they're in.

#### Jamie

There are a few at the end of my street. I don't live in a particularly wonderful neighbourhood. But there are some speedboats in, like a trash heap towards the end of my street, which is an interesting sight every day.

#### Paul

Speedboat graveyard.

#### Jamie

That's the one yeah. Okay, so we're gonna talk about .Net Core 3, desktop things, Web stuff. Perhaps if we could touch on that, it's not a problem if we don't. But what's really interesting is that, about four or five years ago, I was being interviewed for a role and they said to me, You know, "Where do you see yourself in five years?" And I said, Well, you know... Just come from a time had just come from almost like a research and development role where we were doing WinForm stuff. And I said, "you know, I want to investigate more desktop things, maybe create cross-platform desktop stuff," and they kind of looked at me and said. "What? The future is the Web, what are you talking about?"

For a number of years, it has been the Web. You know, I mean .Net itself the .Net framework is originally called NGWS, which stands for Next Gen Web service. So they knew back in the late nineties that everything was going web. But you're saying that there is a desktop story .Net Core?

#### Paul

Yeah. I mean, I think everything went web kind of for good reasons. And there's a few of them, not least of which was deployment.

You know, if you if you've ever tried to actually right a piece of desktop software that one of the biggest challenges you come across this how do you actually get from where it's been written? To so your clients machine.

And that's always been difficult to say the least. A the web just solves that because you get on chrome when you type in a url. And suddenly the software is there and it is running and and you've not got anything to install or anything to do.

And I think Microsoft is trying to solve that in the past, pretty much taking the apple model of we've got these kind of kosher apps that we know there's nothing wrong with them. You can download them from a store. I think some of the stuff that we're moving towards now with the upgrade you've got this concept of this MSIX. So essentially, it feels a bit like to take in the best pass of click once and if it's off, you know, moved over to this MSIX process and that's a really nice deployment experience.

I've been having a look at that a little bit and there's quite a lot you can do with it. And interestingly, you don't have to sort of go down the store route So you can you know, if you have private customers, you can you just package everything as MSIX, and it works really well,

#### Jamie

Okay, I kind of agree with you on that because when I was working at this research and development WinForms place they did in industrial hardware testing. So there's a standard out there Zigbee standard, which is what you're sort of like your Philips Hue lights use. And they built a bunch of hardware to test that, but to test that, you need it was a very manual process, and you would send some bytes, read the bytes back and then measure them with an oscilloscope. So we wrote some desktop applications that would essentially run the tests that would take maybe three or four hours to do manually in a number of seconds, which was amazing. And it would interpret the results and tell you whether it passed or failed and then give you the actual raw data, which was useful. But I remember having to write... I remember, it was the install shield scripting. That's what it was. And I had to write the whole script to develop the installation package and, package of all of the drivers and make sure the right version of .Net Framework was installed and then install all into the known paths. It was and took a good couple of days just to sort of get my head around how well that worked. And then invariably, someone would say, "Oh, we've been sold this software and we only run Linux at the shop. How do we use it?"

#### Paul

Yeah, it's a hard problem and there's been a few things. There's install shield and. was it WIX that that kind of cropped up at one point? They were trying to solve it as well. So it's yes, it's a difficult problem.

#### Jamie

That's before you even factor into the whole equation that different operating systems have different window managers, have different, not necessarily APIs. But the way that the UI is displayed is different, based on the window manager so my Pop!OS Linux machine in my in my office, Is based on Ubuntu, and it runs on Gnome shell, which means that everything is different on Windows, but it's a superficial difference. But it's different enough that, like a WinForms that will not work because WinForms cannot be ported to Linux or Mac OS, presumably because it's just a thin wrapper around the Windows 32 API. So everything gets a little wobbly when you try to do cross-platform desktop, right?

#### Paul

Yeah. I mean, One of the restrictions, I think when they when they upgraded to .Net Core 3, they sort of said, "Yeah, we'll run WinForms and you WPF apps, but we'll only run them on windows," kind of obviously, because it's all sort of directed at Windows.

Interesting, with the new sort off. WinUI stuff, that's coming out now, it looks like they sort of heading towards a cross-platform experience and they apparently teaming up with the at [UNO](https://platform.uno/), I don't if you come across that. I really got very sketchy knowledge of it and myself, but it looks like they're sort of using that to sort of allow you to run WinUI and it looks like the piggy-backing that onto the web assembly.

So this is me trying to predict the future, but you'll be able to kind of write a XAML application and it'll just run anywhere you want it to run by the magic of web assembly, so.

#### Jamie

That is interesting what you've said. I just want to point out, I usually do this when people start predict stuff on the podcast, that is obviously your opinion based on, you know, a bunch of stuff that you've looked into. This is not the direction that Microsoft are going, and I'm not a Microsoft Employee as far as I know Paul isn't a Microsoft Employee (Yeah).  This is just conjecture at this point. The reason I do that is because early in the show's history, someone had predicted something. And then there were blog posts about the "sky is falling!" And it got all the way to Scott Hunter who I was actually watching at a  keynote he was delivering at a conference. And he went, "Yes, I know about that podcast and yes, I know about the blog post."

So my guess is he's never going to be on the show. But that's, you know a small loss. I suppose.

#### Paul

If I had known that, I could have could have predicted something more for more ridiculous.

#### Jamie

Predict really outlandish stuff.

#### Paul

But Yeah, I have no knowledge of this, but I read a couple of things, and it seems like that's the way to go and certainly on Microsoft's GitHub site, They do sort of mention that they're working with the guys at UNO. It's conjecture, but I think the one XAML, if you like, I don't if that's the way they're gonna phrase it, but that the idea that you know you can write XAML and you could run it anywhere. That seems to be where they want to go and I'm pretty sure some guys at Microsoft say that whether they conjecting or not, I'm not sure. I mean, obviously, in this day and age, writing software that just runs in one place is kind of not cutting it.

#### Jamie

Yeah, I totally agree. I do remember there was a new experiment. It's always worth watching people like Steve Sanderson. He was experimenting with a cross platform UI based entirely on his work with Blazor. He'd managed to package in, I think it was a headless chromium or something like that into his app, which then drew a window based on the API is available for the platform that you're running. Then he he could do basic WinForm stuff because of doing Web Assembly. And I think it's probably similar to what you were saying. You know this whole let's play with Web assembly and see what we can do with it, which is it's exciting times.

#### Paul

Yeah, I think Web Assembly is definitely got some mileage in it and added Also, class, that as a form of desktop software because you know, is ultimately it's downloading stuff to your machine and running on your machine. So you still in a sandbox. But it's, you know, arguably, it is a type of desktop software.

Nobody had really say in the same breath as WinForms. And WPF. Certainly when you put stuff on your CV, you don't go. Oh yeah, I've got experience of Winforms, WPF and Web assembly. You leave the first two off.

I think they do sort of belonging in the same sort of category because you are running it locally and it does give you some sort of mileage that you don't get from if you were running is Web assembly on the server? If you really just a bog standard, you know MVC or whatever. That's all kind of going over the wire constantly. If you've got something on your machine, you can do a lot of processing. I've seen examples of games and stuff have been running Web assembly. It's quite amazing the stuff that's coming out. So yes, it impressive and it's exciting.

#### Jamie

One of my I am keen interests is video games, and web stuff and programming. And I remember, the first example that I saw of a video game using WebAssembly was [SQL-Mr.Magoo's](https://twitter.com/mistermag00) version of Tetris, using Blazor, which was called [Bletris](https://sql-mistermagoo.github.io/bletris). Which I thought, "Hey, this is pretty cool. This is a nice little diversion and you know it works cross-platform doesn't matter which browser your running on it works," but then the best one I've seen so far is. Do you remember the old PC game Diablo?

#### Paul

That now I don't.

#### Jamie

Ah right ok. This is a top down, I think my friend G from [my other podcast](https://wafflingtaylors.rocks/2019/07/26/hungry-not-hungry-horace-with-g/), described as a "top down clicky clicky looter shooter." Which is fair enough. But yeah, the entire game runs in Web Assembly. Inside of your browse it does. I think it's diablo dot, I'll get the URL and put it in the shownotes, but it's like diablo.webassembly.azurewebsites... or something like that.
### Side note

The url for Diablo in the browser is [https://d07riv.github.io/diabloweb/](https://d07riv.github.io/diabloweb/)

---

#### Jamie

You have to supply your browser with the data files from an actual, you know, proper version of the game as it were. You know, an official like maybe for GoG, from the CDs, or whatever. But yeah, you provide it with the official data files for the game and it's got the engine rewritten in WebAssembly just sat there in the browser. It's genius, that's what it is.

#### Paul

Excellent, they just need to do that for Civilizations or something and then we're going.

#### Jamie

A lot of these older games, you know, you could just run them inside the browers. The the one I'm waiting for is Age of Empires. I don't wanna have to keep rebooting into Windows to play that because I'm more of a Linux user of these days. You know a family member saying to me, "How can I run Command & Conquer on Windows 10?" and there is no way to run it on Windows 10 until somebody really smart, smarter than I, figures out how to bring it in Web assembly, which it is gonna happen. It just takes time.

#### Paul

Yeah, definitely. Yeah.

### Is The Desktop Story Only Available For Windows?

#### Jamie

So you're saying that we don't like all three you mentioned? The only one we can do. WinForms the stuff and WPF and things like that. But only on Windows, right?

#### Paul

Yep. That's right. Yeah.

#### Jamie

Okay. So I can I think I've seen it before. There's, ah, demonstration that Scott Hunter did where he... Hopefully if I say his name, enough times on the show will be on the show, right?

#### Paul

It's like if you say it three times he appears, like Beetlejuice.

#### Jamie

That's it Beetlejuice. I was gonna go with bloody Mary. But okay, Beetlejuice, that's fine. I'm sure he'll prefer that comparison than they're bloody Mary.

But Yeah, it's ah, I've seen this talk that Hunter and Hanselman gave where Hunter said, you know, here's a, I mean, it was a West Wind application, which tells you just how old it is. For those who don't know, that's, you know, the fake company that Microsoft used to use before they came up with Contoso. So this was, you know, .Net 1 stuff with WinForms, and he started up. But it took a couple of seconds to start and it wasn't very scalable. And then he went, And now I'll just changed this two or three lines of code to make it work with .Net Core 3. And wallop, there it is. And it's faster and its scales more like other stuff. So I like that it's there. I feel like it's more of a stepping stone until, like you say, until we figure out what we're gonna do with cross platform, UI desktop applications.

#### Paul

Also, the upgrade process is quite a nice a nice process. I mean, as you just described is a few ways of there in that you can sort of just changed the project that you know what, Microsoft have got some recommendations and you can do a side by side.

I mean, I think I think this is aimed at people who got, say, WinForms app and has been there since. I don't know, 2003 or something, and it's running some important software that doesn't warrant a rewrite and they only want to run it on Windows. And to be fair, if you go around the enterprise, there's a lot of people still running these kind of apps that, you know, they don't really want to touch them because they just kind of work and they've been working and everybody knows I use them.

And so everyone is just left them until now. And I think this kind of story is a really nice way to kind of bring them kicking and screaming into this 21st century. And especially, you know, with the sort of the or the little things that are going on like GRPC and so on. So, you know, if you've got an old WPF up using WCF or something like that, was it Mike Rendle was written It some library that will automatically migrate all of your WCF into GRPC.

So, yeah, it's a you know, a week's worth of work, and you can you can bring this stuff into into the 21st century and you can have you can have the speed improvements from .Net Core and that's a big factor.

#### Jamie

It certainly is. Yeah, So the tool that Mark Randel created, it's called [Visual Recode](https://visualrecode.com/).

When I interviewed him in October 2019 he was saying, "It gets you kind of 60 to 70% of the way there in your migration in some time. I can't say how far, how long, because it will depend on the complexity of your app. But it can give you 60 to 70% of the way through a migration, which is incredibly useful." I think it was Richard Campbell who said, You know, "working code has infinitely more value than experimental _I haven't written it yet_ code." Like you say in these enterprise environments, you've got these applications that are business level applications that need to be there, they are critical. You know, you can't You can't do that out of the TPS reports or whatever without this application, and nobody really understands how the code works and the original source code may have been lost, and it's just they you just run it. You feel it in your hope it doesn't throw an exception and you carry on. But then, like you say, if someone wants to bring it to .Net Core making faster or make it a little safer or anything like that, if you still have the source code, it's a case of making a few small changes and there you go.

#### Paul

Yep. And also that's all mentioned [XAML Islands](https://blogs.windows.com/windowsdeveloper/2018/11/02/xaml-islands-a-deep-dive-part-1/) at that point, because that sort of lets you changes software from the outside in so you can make a small change for, I don't know... Say you've got nuclear reactor or wherever, and a WinForms up that's running this nuclear reactor so you don't want to touch it or whatever.

So you add a form in WinForms and you add the XAML host, and then you can start adding stuff using XAML Islands written in WinUI. Then effectively you can sort of develop the application without changing it. If that makes sense,

I really do hope that there's no actual nuclear reactors that running WinForm apps.

The principle is there. You know, you're frightened to change it because it's gonna break something and you can make these changes outside of the application and then. Just see them reflected in the application. So yes it's really nice and disposable.

Was it? I can't remember. It was It may have been Martin Fowler talking about a strangling vines pattern. So he was talking about, you know, you write tests and you can sure something with tests. And then you can kind of change it from within, and the strangling vines of the test sort of hold it up. Which feels like the same sort of thing you can, you know you can make these changes inside this XAML host, and keep it running. As it did. But have this things off by the side and sort of an enhance in that way. But at the end, you might just be left with a sort of WinForms shell. But Nothin in it is left of WinForms, and it's all been migrated and at that point, it's a relatively low risk change to just go. We're going to stop using the WinForms. Now plug in a WinUI shell and we're good to go.

#### Jamie

Yeah, definitely is that [strangler pattern](https://martinfowler.com/bliki/StranglerFigApplication.html). The idea if you build an API or an interface around the working existing code, and you code against that interface until you're able to change the code underneath it. If that makes sense.

#### Paul

Yeah, absolutely.

#### Jamie

And then, like you say, you get to the point where you were able to change that code without having to worry about breaking everything else, which is incredibly useful.

### Sharing Common Code

#### Jamie

So what other elements do we have in the desktop story .Net Core. There isn't yet a fully cross-compatible UI Framework. But we're here with WinForms and the WCF stuff right? So like the way that I have understood it is being able to do WinForms of WCF on .Net Core 3. Now this is my understanding. Obviously, you know, what I have inferred from the documentation and the press release of the stuff is that it's similar to the kind of step that everyone was expected to take with .Net Core 2.1 in that ASP .Net Core 2.1 can run on either .Net Core or Framework. In that if you have something that already runs on framework, you can make a bunch of small changes and migrate either a small controller over or a small bunch of features over. Or you could just blanket move everything off it on that call which, you know, if you have that much hair to pull out than good luck to you.

#### Paul

Yeah, during the upgrade process you can. I mean, you can't do the piecemeal things. So So you kind of get on framework or you're on Core because it's the actual project that gets upgraded ultimately. You gotta change the target of the project.

What you can do is you can you can create a new .Net Core WinForms app. And you can do that, say in the same directory as the existing framework WinForms app, and then you can just point it to all the same files. So if you change one, it'll change both so you could run them side by side.

You can also, you know if you if you didn't want to do right, you could send some symbolic links across, but essentially, you're just sharing in the same code between the two environments because the idea is that both both from the same code. There's one or two exceptions to that which don't leap to mind at the minute. So I can't give you any examples. But when you do an exception, what you can do is you can put in a quick compiler directive, check. `#if whatever` and then sort of say, you know, if we're running on .Net Core, then do `x` and otherwise do `y`. Although having worked with those kind of things in C 15-20 years ago, would you don't want too many of them in your   code because it can become spaghetified?

#### Jamie

Yeah, they end up kind of like a code-smell. Don't they?

#### Paul

Yeah, one or two, you can live with, but if you see a code base that's got you know, every other line is like if we're running as this, then do X, otherwise do Y then you can't run that through in your head. It's just too many too many variables.

#### Jamie

Totally agree. I do like the idea of taking back when I was, you know, employed to do win forms applications. I was you know. So I'm noodling around with them and everything happened in the single threat and everything was in a single class and, you know, like other stuff. But if you are able to them go back and architecture applications split out you while they're from your business logic and make it almost like a NT architecture layer application and then you should then be able to just swap the UI out and it shouldn't really matter.

#### Paul

Yeah, absolutely. And arguably probably should be doing that anyway, you know, I mean a good one thing that .Net Core 3 has not done is introduced the idea that it is good to sort of separate you code into it's a sort of business logic and UI layer. It's started. UI layer.

That's always been there, so I mean, if a WPF is, I don't want to say built in, but you know it. It's quite easy to do you because you can you can solve bind. You can use data binding and then you can, you know. So use an [MVVM pattern](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93viewmodel). I want to use the term MVVM light, I don't mean the piece of software MVVM lite, But you can sort of do parts of MVVM.

With WinForms, obviously you get a bit limited. There are other patterns that you could can use with WinForms to sort of emulate that kind of binding. But you obviously don't get a smoother experience for that. But you can still separate your business logic from your UI layer. And obviously, if you've got a load of code, if you've got like, you know, you press a button on a form and it's like on click and then 5000 lines of code that do some incredibly complicated thing, then you're in trouble no matter what framework you run it on,

#### Jamie

Not gonna lie. You've given me some horrendous flashbacks just then.

But, you know, that's how we were sort of, before these end tier patterns and separating everything out and interfaces and stuff. I mean, they have always been there in computer science since, like 1991, 1992 I think since the Gang of Five. But you know, when you're throwing together, what is an MVP for an application, and it is only ever do one thing. It is doing what I call the Charles Emerson Winchester gambit. It does one thing does it very well, and then it moves on. Then, yeah, you can kind of get away with lumping all the code into the code. I don't think anyone who doesn't watch MASH would get that reference. But what I'm getting at is that you know, when you have when you're originally putting the application together, I think yet doing it that way it kind of makes sense. But then you know all the time it gets bloated, it doesn't all application code bases get bloated.

#### Paul

Yeah, every application has ever been written was only supposed to do the one thing that you just described and then suddenly they end up doing 50 different things. And nobody saw that when it was first developed. I mean, when WinForms was a classic one for being built from prototype. So you know you go out to a client And you say yeah we can do this and that was about it and press a button and it does this and then you know, eight months down the line, you've got all the code behind that button that kind of make the salesman story kind of work.

Nobody ever wants to separate it, because it's like, Well, I'm not going to be the one that's gonna re factor that. So that's how these things started isn't it?

#### Jamie

Yeah, And then you get to a point where you talking to maybe a project manager or delivery manager or someone who's more senior than you and saying this needs to be changed from the 500 line behemoth to something a little bit more scalable or a little bit, you know, needs to be moved off the UI thread and they say it's not worth it because it doesn't give us any kind of new features.

#### Paul

Yeah exactly. That's one of the issues with sprints in that in the end of it, nobody wants to see the exact thing that they saw at the start of the sprint, but you telling them now it's more maintainable.

#### Jamie

You're right. I do remember there was an actually a real world example from one of my earlier roles. I was instructed to build a demo application. Doesn't do anything. Just it starts up as a datagrid. You push a button it fake, bringing some process of dumps some random data around to the data grid on. We're gonna use that to sort of win a contract, you know? So I threw it together and maybe a few hours to architect it roughly well so that I could swap out parts as it became available. A couple hours later, I was like, "There you go boss". The boss went away and and did whatever they did and then six months later, once it had been done and dusted and I had completely forgotten about it. No one had remembered about it. I got a bug report saying that it wasn't actually running a test.

So, not only had they used it to secure some work, but they just basically handed over the executable once they'd secure the work.

Excellent.

So that you try to explain to this customer Yeah. I'll actually have to actually build the application.

#### Paul

It's not working because it's not there.

#### Jamie

But that was That was the with the great thing about WinForms is that you know, for those who haven't used it before, it's brilliant. You know, you bring up a Win Forms designer inside of visual studio, and you literally have a tool box of components. So there's a button. There's a text box. There's a A number box. There's an IP Address box. You just drag and drop them onto this. This form this window, and if you want the button to do something, you double click it and it will generate the event on tile that code together. So then you just get a method that is already existing and already tied together. You just write your code you're going in there. It's really for that rapid application development model, but in my opinion, not that great for long term survival.

#### Paul

I think you call the MVP pattern that you can you can use. The thing stands for Model View Presenter and it's sort of a way of shoehorning Winforms into a sort of, you know, for want of a better word an MVVM style of architecture.

But yea said it is. It is quick for prototyping, and I think that's sort of where it came from. It came from, you know, sort VB5, maybe 6. type ethos of Microsoft's idea of "let's just give this to accountants" or whatever and they can sort of build their own software. And off you go because it's dead simple. You just drag and drop on down. You piece of data is there and so on. Obviously, you know the price you pay for that is it's really difficult to maintain.

#### Jamie

Like you say, It's from the visual basic world on the visual basic for applications world and all that stuff where, yeah, you give the tools to the people who are they have the domain experts is making. It was that idea of trying to make development sort of democratized, I guess. That will give everyone the tools and they'll make brilliant software as long as our software that it sits on his brilliant and then you, you'd be given some kind of jumbled mess of VB code and told, Make that better and you have no idea what is doing because you know there's no there's no kind of patterns or anything that you would expect a developer to use because they weren't developers.

#### Paul

Exactly and the winforms designer has actually been I don't know if its been ported, but there is a winforms designer you can now use for .Net Core. To be honest, it's quite an early release and I may start playing with it. I think you know you. You're 15 minutes away from it just kind of crashing on you and it does quite quite nasty things. So, you know, you got a few controls on a form and then drag another one. If it doesn't like it, just kind of deletes all the controls and gives up and goes home.

So it will be good, I'm sure. But it's not now.

#### Jamie

I guess that's par for the course, isn't it? You know, it's like an early release v1 of something. There's a reason why a lot of develop a stick around for v2 of something.

#### Paul

Yeah, absolutely. It just given that you've got this sort of story, one of the one of the prices that you're gonna pay, especially if you don't know a winforms app is that in order to edit the UI You know, after go into the designer file and you know after change that stuff in code, which it's possible to do. But it's certainly not as easy to do in winforms as it is inside of WPF even and WinUI.

#### Jamie

Sure sure, I do remember talking to one of the one of my friends who is an old school Windows developer. And he said, You know, back in the day is a Windows 3.1. You essentially had to handcraft your UI and you had, like, a text file with a bunch of numbers essentially, and you changed one of the numbers and that UI stopped working and you don't know why. And then you undo do it, and it starts working again, which is a wonderful.

#### Paul

The reminds me of the time I was programming with Spectrum and you took off, writing code out from a book, and then the line wouldn't work. So you just kind of go up and delete that line because it was moaning about it and then now the next line is not working.

#### Jamie

Exactly right. You're literally hacking away to get the application running.

### New WinForms Apps in .NET Core

#### Jamie

So let's say I wanted to create a brand new let's say, winforms .Net Core 3 app. Is it relatively easy? Is it the same processes? If I was using framework, is it just filing you project inside of Visual Studio?

#### Paul

It is? Yeah. Is an easy process. Like I say, you gotta quickly come up against the the limitations of the designer because you're going to need the designer on your machine to sort of drag theses various bits and bobs on.

Very quickly. I would start playing about with it and and I managed to get about four or five controls on before it started doing strange stuff and sort of gave up and said, Right. Okay, this is causing more harm than good. But yes, they're still just File > New Project. and you've got winforms up running. It's an interesting question is to what criteria would be for creating a winforms app in 2020? There are some arguments to say that it seems to be faring better than WPF because when they fix the winforms designer problem. You still got that kind of quick drag and drop and with XAML Islands, you could arguably just run it as a shell.

But yeah, there is a question is it's whether you'd want to create a new winforms application in this day and age.

#### Jamie

You know, we talked to anyone about the enterprise, and I guess you know, the enterprise is kind of slow moving. And if somebody there say is we want to create a WinForms app, you can. Now, I guess, with the newer tools.

#### Paul

Yeah, absolutely and arguably, You can like I said run it as a shell, and then it sort satisfies the whatever policy is. That means that, you know, somebody told you create winforms app

#### Jamie

Regardless of whether that's a good thing or not, but you know. I mean, the thing is, it gets the work done, doesn't it? There? The idea is that it have said it a few times. This rad idea, rapid application development. You know this idea of quickly prototype in something in the use of MVP pattern and I thought minimum viable product pattern and that's kind of what it means.

#### Paul

Yes, it doesn't stand for that but I see what you mean. It it is a quick way to getting something running. And if all you want is a button and I've seen a few WinForms apps where they are just a button and they call out to a service somewhere and that's all they do. And then, you know, maybe that is what you want. Maybe you want no WinForms application. There's a lot to be said for running a desktop application. I mean, you know, you've got zero latency - as long as you aren't actually leaving the application - you got zero latency. You've got a really fast experience. It's running on your desktop.

No one's kind of spoofing the button that you pressing because again it is only on the desktop, you know, so that this was quite a lot of stuff that you get sort of our box to show any WinForms app or any sort of desktop application because it's running locally, you know, I can sort of say an argument for it's an applications being either of them technologies.

I'm not saying that advised generally people to go. Yeah, ditch, react and right them as a WinForms app. But you know that there are reasons for doing it. I can imagine that the and not just that you notice some strange policy that says we can only create WinForms app. It's ah, it's interesting. I did a talk, a similar sort Talk at this local user group on but the end. I was sort of saying "so how many people were creating desktop applications?" And I expected, you know, maybe one guy support his and about half the room put their hand up. I was sort saying, All right, how many people have created win forms applications and again, you know, maybe half of them. So it does happen And people are using this technology still.

#### Jamie

Like I said, the enterprise is a bit of a slow beast. It moves very slowly because, you know, it kind of has to. Because if it doesn't move slowly than you know, the code that we wrote last year and has to be rewritten and I could totally get behind that.

It's an interesting set up when you realize that you know, the majority of the world runs on incredibly old code that was kind of hacked together in the last possible minute. Like I shudder to think of how many of the behind closed doors banking how much of that industry is actually running on old COBOL. There was written by someone 30, 40, 50 years ago who is now probably since passed on but didn't document it and hasn't commented at all. And all I got the stuff is kind of crazy and scary to think about that kind of things.

#### Paul

There was an advert. I can't remember whether it might have been FORTRAN. It was they were advertising for Hubble Telescope and they were sort of same. We need, you know, a FORTRAN developer, because we had we had this guy and he's done FORTRAN and that's it and now he's retired and now we need somebody to kind of maintain this telescrope. I'm sure I would have heard about that relatively recently. And was looking for I don't know, the last the last FORTRAN developer left.

#### Jamie

Yeah, really make sense. And if you want to make loads and loads of money...

#### Paul

Yeah learn an obscure language and somebody will pay your money to keep something going.

#### Jamie

Don't use this podcast as a way of getting career advice because I don't know what I'm doing with my career. So I can't advice people on this.

### Pauls' New Book

#### Jamie

So we you know, we originally connected because we were talking about you'd written with, you know, some co-authors. A book recently. I believe it's on Packt Publishing. Did you want to tell us a little bit about that?

#### Paul

Yeah. So? Actually, I didn't write it with co-authors. I wrote the second edition of it. So there's a couple of guys that wrote the first addition, and I sort of took it and so of gutted it. It was originally written for .Net Core 2 and C#7. So the title of the Book of released is [C# 8 and .NET Core 3 Projects Using Azure](https://www.packtpub.com/gb/web-development/c-8-and-net-core-3-0-projects-second-edition).

So I've essentially upgraded it and added some new stuff. And pretty much every chapter except for the 1st one is using something on Azure. So they sort of added that in the end is a a sort of concession, but yes. So, essentially, it's just having a look at the new features in .Net Core 3 on using them. So each chapters is an independent project. So using them to create a project. So that in the first chapter, I'm sort of interestingly based on what we just talked about, creating a new WinForms app. And then I take the WinForms app that was written for the previous addition and upgrade that. And then, you know, in subsequent chapters, have a look at things like that, your logic apps and entity framework, various different bits and bobs.

So, yes, it is the first book club I've written and I would definitely encourage people, if they're so inclined and if they like writing, to write a book about tech because it's difficult. You spend a lot of time writing it and you know, it's a lot of time you could be doing other stuff. But you learn a lot. And interestingly, when you get in touch people at Microsoft and you say "I'm writing a book. Can you help me out?", I've not had a bad response. People have really put themselves out on and helped me out with all kinds of different things.

I mean Microsoft in general with the experience, even outside of the book, have been have been quite helpful. And I don't know if this has always been the case. Everyone says it's a new Microsoft, but I've never really had a bad experience with guys there, so it's a positive thing to do with it.

#### Jamie

That's cool. I like that. It does echo the sort of sentiment that I've had so far from other guests who have worked alongside Microsoft and asked for help and colleagues and clients, that I've worked with who have in the past had been in direct contact with Microsoft. There is a client that I recently worked with. You said that they were building something for summer and were in direct contact with, for instance, James Montamagno, and they had like weekly calls discussing how they were gonna make the next part off the app because it was a Xamarin app, and what they were doing was was not really supported in Xamarin. And so whilst the folks who were making the App were breaking new ground. With that, the folks who work on the Xamarin team were like "we need to create a bunch of libraries to help them do that." So it was like this really cool, collaborative process.

Yeah. A couple of the guests who have been on the show previously effect said the same thing. You know, I have been reading the spark of this series of tutorials and, you know, I had to be in touch with Microsoft, and they seem to be really open and nice about helping me out and stuff, which is It's a nice change from the previous publicity that Microsoft have had, you know, from the nineties and the early 2000s, but as it was from is the one bad report is really all you need, you know, to create that sort of negative feeling.

#### Paul

I mean, everyone is saying they changed, and to be honest, I suppose it it's ah, think part of that is it doing things a lot more in the open these days. I mean, like, so, you know, maybe they have changed. Maybe maybe everyone there before was, you know, some some kind of dragon or something. And then it's changed and they're all really nice guys now. But I have spoken to Microsoft before, you know, even prayer to 2000 You know, the guys who spoke to have always been helpful on the helpdesk and that that was pre-Twitter days when you couldn't go on Twitter and find out who's got experience of this and just kind of send them a direct message. You go, "I'm doing this. Do you have any advice". but, yeah, they are one of the guys who works on the XAML team. I was talking to him. He was extremely doubtful. He was, you know, showing me early versions of the demos that we're doing and so on and passing all that sort through.

And when I was working on chatbots. The same sort of thing I got in touch with a guy and he immediately said, "Can we hop on a call?" He taught me some things. gave me some tips. So yes, It's really useful, so I can't really say about thing about Microsoft at all.

#### Jamie

I guess there's two questions you know what kind of projects were in the book and they get more towards, "I've never used .Net Core or C# 8. And I want to know how to make an app that I could put on the web somewhere." Is that the kind of idea you're going with?

#### Paul

Yeah. So it's, um it does have quite a beginner feel to it. I'm sort of answering second question first there.

But yeah, it as sort of a beginner feel to it. So, you know, you need some basic programming experience. It's definitely going to help you if you programmed in C# before there is certainly nothing in the book that teaches you how to program and C#. But yet, you know, a sort of novice C# developer, could pick it up and run with it. The projects a supposedly real world examples. So obviously these things have not actually been requested by a client or anything, but they are sort of imagine real world examples. So, for example, we were you know, we've got a chat application using Azure SignalR just to sort of demonstrate how SignalR works with .Net Core 3 and so on.

And then, you know, Entity Framework core sort of to help you identify websites. That kind of useful things like that just trying to put it into context.

So I know one of the things that I have always found useful. Maybe not so much in IT but so in academia you generally is. You know, I was I was always a person who, in the maths class in school, wanted to know why we do in this. What is it you want to use this trigonometry for. Because until I can sort of get my head round, that just teaching me all this. This is the sum that use to calculate out, it doesn't mean anything and then interesting. You know, you you start writing games and so on. So that's what it's all for!

#### Jamie

Yeah, I like to use one of your examples, you know, SignalR is kind of useless by itself. But if you need some kind of real time bi-directional communication between an application and the server, it's wonderful for it. So yeah, that I guess The chat bot idea is kind of like a wonderful example of how the all fits together.

#### Paul

Yep And hopefully it's a useful resource for people. Like I say, it certainly helped me.

#### Jamie

Where is it best to get the book from. Visit Packt Publishing. Is it kind of get it from Amazon is it or a website? What was the best place to find out more about it?

#### Paul

So, yeah. You can get it from Packt or Packet is I've been referred into them. I don't know what pronunciation is. You can also get it from Amazon. And I can send you a link to it so you can put it in the show notes, If that's okay.

#### Jamie

Sure, we'll put the link in the show notes. Definitely. And that way, you know, we don't have to listen his own scrambling for a piece of paper or to get the phone out whilst potentially driving or something. We don't wanna be the cause of car crashes do we?

#### Paul

Definitely not no. Oh, cycling as I am normally listening to your podcast.

#### Jamie

Oh, interesting. Okay, I'm I tend to listen to one of my shows that I subscribed to when I'm doing practically anything. As long as I could be left alone by friends and family and colleagues. I just get on with it.

I'm one of these weirdos who could do the listening to podcasts and take it all in and do the work that they're doing sometime.

#### Paul

Yeah, there's not mo. I can concentrate on any one thing and then it has to be something that you know, that big concentration in there. I mean, obviously when I say not concentration of not cycling and not concentrate on the road.

#### Jamie

Is that automaticity, isn't it? You don't have to devote all of your brain power toe making the bike go and making sure that you're safe on the road. Then you factor into it that I listen to most podcasts at 1.75 times normal speed or 2 times speed or and sometimes 3 times speed. Then it usually it'll just goes in, which is - I'm a weirdo is what I'm saying.


We'll put the put the link to where to get the book from in the show notes. Is there is there a website for it? Or is it just the case of check out the book and then, like others, source code samples on Get hope and stuff like that?

#### Paul

Yeah, so? So basically, you get a book from Packet or Packt or Amazon. And then there's a GitHub repository with all of the examples and which is obviously referenced in the book so you can get everything from there.

#### Jamie

Excellent. OK, so what about yourself? If folks want to keep in touch with you or find out more about what you're sort of doing, what you're up to. Is that something that's OK, You know, Not everyone has a Twitter or a blog, But, you know, is that something you do?

#### Paul

Yes, it is so you can find me on Twitter [@Paul_Michaels](https://twitter.com/paul_michaels) So, yeah, feel free. Get in touch with me. You can find me on LinkedIn. You just search for Paul Michaels. I imagine I'll be one of the early results on I maintain a blog, which I post to relatively frequently, which is [PMichaels.net](](https://www.pmichaels.net/)).

Yeah, I think that's a that's pretty much all the ways that you can get in touch with me.

#### Jamie

So yeah, what I'll do is put links to all of those things in the in the show notes. What was the book title, again? Sorry.

#### Paul

C# 8 and .NET Core 3 Projects Using Azure.

#### Jamie

well, I mean, that's all the questions I have today. Thank you ever so much for spending part of your Saturday afternoon chatting on .NET Core and desktop technologies and WinForms and Azure and stuff with me because it's been really eye opening. There's been some stuff that they definitely didn't know going in, and now I know a lot more. So thank you ever so much for that.

#### Paul

Well, thank you for for allowing me the opportunity to uh huh. But you're and yeah, I can think of few few better ways and spend the Saturday afternoon. Then going on about tech, which probably makes me a bit for strange person as well.

### Wrapping Up

That was my interview with Paul Michaels. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/), and there will be a link directly to them in your podcatcher.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice - head over to [dotnetcore.show/subscribe](/subscribe) for ways to do that - and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Paul's blog](https://www.pmichaels.net/)
- [Paul on Twitter](https://twitter.com/paul_michaels)
- [C# 8 and .NET Core 3 Projects Using Azure - Second Edition](https://www.packtpub.com/gb/web-development/c-8-and-net-core-3-0-projects-second-edition)
- [Bullseye (British game show)](https://en.wikipedia.org/wiki/Bullseye_(British_game_show))
- [Uno](https://platform.uno/)
- [SQL-Mr.Magoo's](https://twitter.com/mistermag00)
- [Bletris](https://sql-mistermagoo.github.io/bletris)
- [Hungry Not Hungry Horace With G](https://wafflingtaylors.rocks/2019/07/26/hungry-not-hungry-horace-with-g/)
- [Visual Recode](https://visualrecode.com/)
- [XAML Islands](https://blogs.windows.com/windowsdeveloper/2018/11/02/xaml-islands-a-deep-dive-part-1/)
- [Strangler Pattern](https://martinfowler.com/bliki/StranglerFigApplication.html)
- [MVVM pattern](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93viewmodel)
