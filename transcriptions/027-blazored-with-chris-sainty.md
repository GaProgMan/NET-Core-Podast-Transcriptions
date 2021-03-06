# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is episode 27: Blazored with Chris Sainty. In this episode I interviewed Chris Sainty about Blazored and the sheer speed at which the Blazor project has evolved. Some of you may know Chris Sainty from his blog at [chrissainty.com](https://chrissainty.com/), or the GitHub organisation he started called "[Blazored](https://github.com/Blazored)"

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Chris' Introduction

**Jamie**:
Thank you ever so much, Chris, for being on the show. I really appreciate you taking some time out of your Sunday afternoon to talk with me because uh, you know, we're all really busy people, so thank you ever so much.

**Chris**:
An Absolute pleasure.

**Jamie**:
Brilliant. For all the folks who maybe listen to this show and maybe haven't seen some of the work you do or the blog posts you've written or anything like that. I was wondering could you give us a quick introduction, sort of who you are, what you do, that kind of thing?

**Chris**:
Yeah. Cool. Yeah, so I've been in software engineer for a little over 15 years now and most people will probably know me from my blog and I've been blogging for just over a year and a half, originally focused on .Net Core. But to be honest, I discovered Blazor and that's pretty much been the primary focus ever since I work at flagship group. So there are housing association in the east of England. I work with a great team and we're building a new Greenfield Repairs and Maintenance solution, which was going to be used by the companies within the group. And what's really cool about all that we're actually using all of the nice, new goodies. So we got all the new .Net Core Stuff, uh, including Blazor for the front end, which is interesting.

**Jamie**:
Wow. We'll have to double back and talk about that because as we're recording this, MS Build has recently happened and obviously they haven't released a 1.0 they are jumping straight to 3.0. So I can't imagine trying to get buy in from PMs and managers and project owners on, "Hey, here's this experimental technology we want to build your entire stack with."

**Chris**:
Yeah. It's, it's normally not something you're probably even try and do to be on, certainly. At other places I've been. But, uh, I'm quite lucky. Flagship's an incredibly forward-looking company. They are very much about latest technologies, latest advancements, so if anything we can do to sort of help solve the housing crisis. And I'm particularly lucky that in IT I've got a great manager who trusts me and my team to make good decisions and you know, he does buy into what we, uh, what we go with. So we talked about it. He's like, do you think it's worth the risk? I'm like, I think it's, I think it's going to be the big thing. Um, you know, yes, we're going to have to suffer some pain in the short term. Definitely. You know, there'll be some breaking APIs, and there'll be some rewrites we'll have to do here at that.

**Chris**:
But I said, you know, I think if we get on this now, this is going to put us a bit ahead of the curve. He's like, great, go make it happen. And that's what we did. So like I said, it's not without its issues. Uh, I'm quite happy to admit I spent, you know, five days doing an upgrade from preview three to preview four and it was two missing using statements. Um, but you know, with the joys of preview tooling. So like I say, I'm in a fortunate position that we can use these, these early technologies. I think that'll benefits in the long run.

**Jamie**:
Fantastic. Um, I know for myself, I haven't had a chance to play with the newer versions of Blazor. I think, um, the last version I was playing with was 0.8 I think. And um, I do a few talks every now and then about Blazor, just sort of introducing it as a technology. I show a, for an example, that I built in the 0.3 initial sort of public release and uh, making sure that I have an old version of the SDK and runtime on my machine and the global.json just to get it to run.

**Chris**:
Yeah, definitely. Yeah, it does become a bit challenging if you're trying to keep older stuff going for them. And then then the newest stuff and playing around with that and yeah, I must admit, I've been in the same boat as you a few times and then I kind of got to the point and I'm like, okay, right, I'm just upgrading everything to the latest version and I'm going to stick that now because it's slightly less painful.

**Jamie**:
Brilliant. So looking at your, your website then you said on your about page that you've been in the Microsoft tech stack since the classic ASP days of then of the late nineties and you've seen it all grow and change. Right? So this is less of a quick question about Blazor, but more a question of like the tech stack as a whole. What in your opinion have been some of the biggest innovations since classic ASP in that sort of Microsoft Tech Stack?

**Chris**:
Yeah, there's been quite a few big steps forward I think. I think the obvious one to talk about first is is .Net framework itself as an ASP net. I think without those we wouldn't have anything else we've got now. You know the other technologies from build on top of that, and I think that was really the dawn of the new tech stack. Moving obviously from classic ASP, I mean C#s, huge in the language that coming in. There's all the tooling that we've got, which I think is probably one of the biggest selling points of the dominate ecosystem. I think we probably got the best tooling of probably any assistant and we're probably a bit biased. But I think in terms of pure technologies, I think MVC for me was a huge step forward. I started out in the early days with web forms and vb.net and you know, you could, you could build out, get out occasions in web forms and um, you know, the companies I worked for, we, we did and it worked and everybody was happy management wise, things like that.

**Chris**:
But you know, we had issues with maintainability and, and you know, it was very easy with web forms to write messy applications. I think this probably, and I've certainly done that, um, you know, I think that MVC, it was the first point for me where the Microsoft stack started to actually embrace the way the web worked. So I think for me, what forms always felt a bit like we're trying to make the web behave like a desktop application. Anybody who's worked with web forms, know that you always have the view states and all of that, whereas going to MVC, you know, you had these nice separation of concerns and it really felt like programming for the web properly. Now I hope I haven't offended anyone by saying now, but for me that was probably the biggest thing that stands out for me. A sort of more obviously coming in more modern .Net Core is the obvious thing to say. You know, that ability to have side by side run time versions and the ability to, or the way that then Microsoft can innovate and have a much quicker release cycle and get features out to, to us as developers is much quicker has been fantastic. So yeah, I think they're my highlights.

**Jamie**:
So I'm always interested to know whether you think that for the younger devs. So you know, I think, I think you and I are of a similar generation, a similar age bracket for the younger Devs who are coming in now: Is it worth them in your opinion knowing that these older technologies like our web forms and classic ASP and um, you know, old school asp.net exists? Or is it just a case of it doesn't matter, just carry on with the brand new shiny, don't worry about how we got here is fine?

**Chris**:
Yeah, it's a very interesting question. That one. I think for me personally, I think it's always good to know where you've come from because I think you can understand then a bit better about where you are now. I think it's probably just a genuinely good thing to learn from your mistakes and if you don't know about them and you can't, you know, we can't let them, you can't stop yourself repeating them. So I think it's definitely worth younger devs having, I guess for want of a better way of putting it, an academic knowledge of what happens and where the evolution of the .Net stack sort of came from and how it happens. I found that, I don't know it depends how cruel you're being. I think it could be interesting to give someone some classic ASP and say go and go find me something to do this. And then I think after that you would never get any complaints about anything new and going forward. Well, it might be a bit cruel as well, so yeah, like I say I think, um, I think having an idea of where you come from and things like that is good. I think necessarily having to program it just so you can say "done it" is probably not something that's necessary. I think

**Jamie**:
I kinda mentioned the reaction on the face of someone who, who's a modern Angular or React or Vue developer being given a web forms or classic ASP app and saying, right. Yeah. Just make this talk to an API and make you do some stuff.

**Chris**:
Yes.

**Jamie**:
You know, let's change the stack. Just make it do its thing.

**Chris**:
Yes. Yeah. That would be an interesting one. I'd be interested to see how much help you didn't get from Google with some of the classic ASP stuff.

**Jamie**:
Yeah, that would be interesting.

**Chris**:
Definitely. But yeah, now you'd like to add certainly from someone coming from an Angular background or something like that. I definitely don't think that that certainly give them web forms would not be ideal.

**Jamie**:
And that's fair enough. And that's not to say that, you know, the 20 years of, 25, 30 years of applications that are still using ASP classic or a web forms, you know, they, they don't necessarily need to be in that, so you know in inverted commas, there's no “need” to upgrade or change stack, you know, as long as it works.

**Chris**:
Oh, completely. I'm certainly not believer in changing things just for the sake of it. I mean, you know, I think I'm at the end of the day, most of us, you know, we're writing software for companies. Companies are there to make money and things like that. And frankly, if the app's doing what it should do and can continue doing what it's meant to do, then why change? I think that has to be a, a reason, you know, there has to be some benefit for moving forward. And to be honest with you, I mean I certainly have in my career worked with applications, web forms applications that still going now but are that great. They do the job well and why would you want to change that but you know, years you're likely going to upgrade something and potentially you know, create bugs or issues in, in code that's highly battle tested, highly reliable, highly stable just to be on something newer. I don't think that's a good reason, personally.

**Jamie**:
Definitely. Um, I think it was in [The Phoenix project](https://www.goodreads.com/book/show/17255186-the-phoenix-project), there’s a quote is lifted from the goal by, and I'm going to get the name wrong, Eliyahu M. Goldratt or something along those lines. Um, that essentially states that a product, whether it's a physical product like a car or an ephemeral product like software, makes the company no money until it's out there with the customers using it. So flip flopping on the technology and taking something that's already, you know, has a value and swapping it out for something that may have a value in six months' time when we eventually get around to replacing it is uh, maybe not the best idea for long term survival for a company.

**Chris**:
Yes, definitely. It's always done on the idea that it will work out. And I certainly, you know, I’m talking to experience on this one I've been involved with a program that's upgraded for no other reason than to upgrade. And yeah, it was messy for awhile. You know, when I said earlier about, you know, introducing bugs, you know, we did that. We thought we were doing well, you know, we, we'd run our unit tests and we were checking everything as we went and it seemed to be all okay, but at the end of the day, every time you change something, you know there’s always a risk that you're going to get it not quite right. And you know, we had that problem partly because we didn't really understand the old applications as well as we thought we did. You know what, it's like the, you know, the sort of the old guard who had written it had moved on and you know, we were looking at thinking, oh yeah, that shouldn't be too bad and just do this in and just do that, and it'll be okay. And it just doesn't work like it.

**Jamie**:
Yeah. I think that's the biggest problem. When you have a, um, an application stack that was written by a different team or someone else and you're either maintaining it or adding something to it, you need to 100% understand exactly what it's doing. And like you say, you know, if you're not, if you're not 100% sure or if the, if the other team have moved on or if it's not really well documented, it's human nature to make mistakes in that instance because you just, there's things that you don't know.

**Chris**:
Completely, yeah. I mean it's really surprising cause you know, we as developers are always so good at documentation, you know? But yeah. Yeah. Everything you said that is completely orrect. And it's very easy to fall into the trap of thinking, you know, what something does. Even when last you were writing unit tests, problem our unit tests were correct. They just, we just didn't understand why. They would correct for what we thought at that time. So like I say, just to write a test isn't even you can ensure quality.

**Jamie**:
Oh, of course. I mean I've, I've seen in the past I've seen in actual production code bases, unit tests that simply just assert true.

**Chris**:
Yes. I'd like to say I haven't, but I have as well.

**Jamie**:
It's a good way to start. You know, like if you want to run a unit tests that tests something until that unit test asserts that something is true, it will be failing.

**Chris**:
Yes.

**Jamie**:
So it's a good way to start to make sure that your unit testing framework is still running.

**Chris**:
Yeah, very true. Very true. Just have to remember to go back and take out later on.

### What's So Great About Blazor?

**Jamie**:
That's exactly, that's exactly it. Okay. Then, um, so with Blazor, you know, you've done a lot of writing about Blazor in your own time, presumably a lot of research into Blazor, presumably in your own time, maybe work's time, I'm not sure. You've also done a lot of work with Blazor alongside Blazor, that kind of thing. Um, so in your opinion, you said earlier on about, you know, Blazor being a wonderful thing. What's so great about it?

**Chris**:
Everything. Everything.

What's so great about Blazor? Wow, this is hard to condense this down. So for me, I think it's the ability to write truly full stack applications as .NET developers, you know, for me, what sort of, using before, you know, before Blazor came on, the scene I probably did what was more traditional nowadays, which is kind of, I had a web API backends that was all C# and that was all good. And then if I wanted something whizzy at front end, I'd probably have an Angular application. So, um, you know, in a work sense that's, that's all well and good. But now I've got a team that needs to have two skill sets. They need to be able to write in javascript. They need to be able to write C#. They need to understand how those front end frameworks work. So you're having to keep up with two communities and what have you, but obviously Blazor removes all of that.

Um, some companies are even having to go to turn on your complete separate front end team because they have been totally different skillsets and things. With Blazor it C# all the way through. So now you can take and back end developers, and they can write front end code and it--and it's fine to me. That for me is probably the biggest selling point for Blazor. Obviously on top of that you've got general just development speed. I mean certainly my team found that we're churning out code very, very quickly because you know we already understand C# and how it works so we can write code much more efficiently than sort of dealing with with nuances you get with javascript and things like that. That's another big plus.

NuGet So because Blazor's C# but it's all compatible, it's all standard, and things like that, it opens up the majority of NuGet. So instead having to wait for an ecosystem to fall around a framework, we've already got one and it's massive. Now obviously there are a few things we can't use that so people see, well you know, we're still under browser sandbox so we can't go, you know, try and access the local file system or, or any of those types of things or, or try and send mail out, something like that. But you know, um, I think as a, I think Dan Roth showed in his talk at build last week, downloading a NuGet package to explore some tapping like that or out to Excel and you can just go to NuGet, download that package, and it's all in your Blazor app and off you go. That's incredible. So they're kind of the big things for me about why Blazor is so cool.

On top of that, you've got the fact it's written, you know, it's all open source, you know, with this, the new Microsoft. Yeah. This has all been developed that in the public, the team are very responsive, they, you know, they listen to the community. They take on board what people say. Well they suggest, you know, it gets discussed. You know, a great example of that, I think was the naming of Blazor. So anyone who doesn't know, you know, things start off as Blazor. And then for a short period there was kind of this naming issue where another name called Razor Components was brought into the fray, and it really just didn't and take. And the community was struggling with understanding things and what have you; and you the teams took that on board and it got renamed back, which, you know, that is very much down to the community that drove that.

Same with feature requests and things like that, and you know, that there's a lot of stuff you're taking on board the community, uh, suggested things or they're taking a lot of feedback from the community about how things should work and helping to mold and develop an experience at Blazor. You know, that's huge as well. I mean, being able to get that kind of input or at least have a discussion with, with the team about these types of things is enormously beneficial. I feel like, you know, for a that's being built this early on is to be able to help direct in and have some input I think is truly phenomenal.

**Jamie**:
You'd mentioned earlier on about a being, you know, essentially full stack .NEF. And I think that's one of the biggest things for me. So, um, for instance, uh, one of the examples that I show off when I give talks, the example I talked about the runs Blazor 0.3 uses the Pokemon API and it's all entirely in the browser. The browser puts out a request from C# side, uh, stuff to the Pokemon API, gets a json back. Deserializes it, I guess? Or sserialized? I always get serialized and deserialized the wrong way around, but it does some NetwonSoft.Json. And I get a POCO out the other end and then literally pass that same poco to the Ui. So now I, you know, I don't have a C# object that is now out of sync with my javascript or typescript object. And they also don't need to do any, um, anything at compile time enforce that. I just hit compile and the compiler, Roslyn will tell me, "hey, this POCO you're trying to use in the view doesn't have a property called ID. What are you talking about?"

**Chris**:
Yeah, definitely. I mean the ability to share between the front end, the back end is enormous. The application we're building at work, you know, that's probably been one of the biggest things for us. We use kind of a CQRS style architecture and we have our commands and query objects and we have them in shared libraries and we know we're constructing commands and in the Blazor up to go up to our API and, and that's all share code and we're not duplicating, you know like you've mentioned previously having worked with an Angular front end and an API back end, you know, you have that overhead of keeping typescript objects in, you know, in lockstep with your, your C# equivalents and there's always some point where someone forgets to add the property and typescript object or whatever and you know, you end up having a bug. It just costs you a bit of time here in that, whereas, you know, as you quite already said with Blazor, that's just, just doesn't happen. You're going to, you know, the components going to probably tell you before you, you may not even get to the point of building it for you. You know, you get an error spat out, which is, you know, that that's been all over the years.

**Jamie**:
Definitely. Yeah. I want to throw a question out yet that I always get asked when I talk about Blazor, just to see how you respond to it. And so the folks who were already at a Blazor talk that I gave a few weeks back as of recording this, we'll know the question and it is, "but Chris, what's the security implications of running a random DLL and the browser?"

**Chris**:
Yes. So security. So yeah, it's something that does come up a lot. But I think the important thing to understand is that as I mentioned earlier is that Blazor and WebAssembly that they're running a in the same sandbox that javascript does. So they're just as limited as is what Javascript is. You know, you, you're not going to be able to access the file system on the, on the, you know, the client machine and on what have you. You have all those same protections in place. So running Blazor or any WebAssembly on the client is no more or less secure than running javascript. So there's no change in risk. I think it's probably what I would say.

**Jamie**:
Fair enough. That's a little bit more detailed than the answer I give. Usually, I'll say," hey, you know that code you're running on the server, you're pulling down all those NuGet packages. Have you looked into the code for those?"

**Chris**:
Well, yeah, that's a good point. I mean we all know there's been some interesting things with I think, think I'm right in saying it's with NPM, some sort of malicious code finding its way into dependencies, things like that. And yeah, you're quite right at the end of the day if you are happy to run on your back end and obviously you'll be happy to run it on your front end.

**Jamie**:
Exactly. You know, and um, how do I put it? So what I usually say is like your assumed the Newtonsoft.json is safe and secure because millions of people are running this on their servers. Right? And you assume that it's safe and secure because James Newton King now works for Microsoft and it's now a .NET Foundation project and is developed in the, in the open. But what about that random NPM package you just pulled down? That's developed in the open by reputable people. And this is not to pick on NPM, this is just to say, you know, you can't just say, oh well it's okay to run out on the server because it's on the server and I'm not okay with running on the client, you know?

**Chris**:
Yeah, definitely. I think at the end of the day, whenever we take on a dependency into our applications, you know, if you're taking on someone else's code, you're always taking on a level of risk, you know, and it's up to use it to assess that level and go from there. I guess if you want the most secure code, you could always write everything yourself from scratch, but then we'd probably be taking a lot longer to build our applications.

### Enter: Blazored

**Jamie**:
Definitely. Definitely. And so, let's talk about Blazored then, if that's all right.

**Chris**:
Yes.

**Jamie**:
I know that Blazored is a project that you work on and I've done some digging into GitHub and had a look, but obviously some of the folks who are listening may not know about it. So could you tell us a little bit about that?

**Chris**:
Yes, so a Blazored is an org on GitHub that I set  up. To be honest, it's something I set up because I wanted some way to put Blazor packages. So I was building a few things out partly because I knew some of them we'd need at work. So I sort of doing some preemptive work for that and sort of probably a more primary reason was because I just thought that'd be really useful to people in the community. Yeah. So I sat up the Blazored org, put all these least packages there, I'm starting to develop them and put them on NuGet again and things like that and yeah, so it's basically just somewhere to house those packages and it's really just somewhere as well for anybody using the Blazor community who wants to, you know, write package or put a code somewhere and they don't necessarily want to host it on their own GitHub or have enough knowledge to do that or they just want to do it somewhere they can get some help from other people and things like that. Blazored is there, as is an option. That's how I sort of any help I can give, I will, you know, the more we can nurture the Blazor community really the better.

**Jamie**:
Okay, fantastic. So what kind of packages are available on there? Is a just like example code? Or is there something that I can pull from there and throw into a Blazor app and hey, I've got a new feature now!

**Chris**:
Yeah, so there's about six, I think six packages you've got on there now. So there's a [local storage package](https://github.com/Blazored/LocalStorage) which wraps all of the local storage APIs for the browser. So that was one of the first ones I did. And that was there because one of the current, uh, sort of shortcomings of WebAssembly is that it can't interact with browser API or manipulate the DOM directly. So in Blazor we still have to use Javascript, but we want to perform those kinds of operations. Well, the local storage library does is it wraps all of the local storage APIs. Um, so that you can just download it as a NuGet package, and it'll sort that. And then you're only dealing with C# APIs. All of that interop stuff is all hidden away. So you don't have to get your hands into any Javascript stuff.

And then on top of that there's another sort of utility package which the [localisation package](https://github.com/Blazored/Localisation), so that uses some, again, uses some interop to try and work out the client's time zone information and sort of localization stuff and sort of try and give you some information and try to help you deal with that.

And then there's three components in there as well. So got the [modal component](https://github.com/Blazored/Modal), [toast component](https://github.com/Blazored/Toast) and [menu component](https://github.com/Blazored/Menu). These are kind of driven a little bit by some of the things I thought we might be facing at work. So that kind of gave me a bit of a sort of inspiration for those. And they're also kind of things I think if you're in a front end world and you know certainly coming from Angular or React, those kinds of places. They're the kind of things that you, you know you're going to be using that you're going to expect that have. Like I've said, if you've been using Javascript. So I want to try and make sure we have the equivalent in the Blazor without having to deal with javasript to do, these things.

So uh, what's quite cool is that the modal, the toast and the menu don't use any Javascript at all. So they're generated entirely using C#. There's no abstracted hidden javascript interop going over or anything like that. And this is just using C# entirely, which as much as possible, that's what I tried to do with the components that were in Blazor is wherever possible. And not use javascript because it'd be very easy to just wrap loads and loads of javascript packages in C# APIs. But it kind of defeats the object, really. I think for me, what we're trying to do with Blazor, you know in some cases, yes there is a valid reason to do javascript interop, but I try not to make that that the default. The default is that you stay in C# and then if there's absolutely no way around it, then we'll go to interop.

The most recent initiative, which is really cool is actually a [gitter client](https://github.com/Blazored/Gitter) as well into the Blazored org. So there's a great guy in the Blazor community called [SQL-MisterMagoo](https://github.com/SQL-MisterMagoo) who is always creating loads and loads of cool wacky stuff and we in the Blazor community talk a lot on gitter channel is incredibly active. So if anybody does have any issues or questions or whatever, please go to the gitter channel because there are loads of great people in there who can help. But one of the things is we kind of that the gitter client itself, the official one, is a bit iffy, shall we say. So a few of us I think, were all kind of thinking about sort of what we could maybe write a client in Blazor, but Mister Magoo kind of actually took that and actually got it started, which I think is the big thing, I think now that does actually go from an idea to actually start to code.

Yeah. So he started that going, we're developing that in the moment and there's, you know a few people from the community getting involved and they're adding bits and picking up issues and getting it done. It's a really cool thing. You know it's, it's kind of the whole reason why we created the Blazor board, what was it to get people involved in getting the community sort all working together and things like that. Which is, which is really great. It's great to see that. You know, and I've had it with some of the other packages that I've built when, say a new version of Blazor comes out, someone pops up with a PR saying oh I've upgraded to latest version, which is, that's great. That's, that's pretty awesome because you know it's great for me because some of these learnt something when they're doing it. Probably all that, you know, saving someone else, you know, time and effort, you know, doing those upgrades.

**Jamie**:
That's cool. I like it. I shall know if SQL-MisterMagoos's [Bletris](https://sql-mistermagoo.github.io/bletris) a few times. And said, somebody said to me, "well what's Blazor useful for?" and I'm like, "well you can play Tetris in your browser using C#. What's not to love?"

**Chris**:
Exactly. Why would you want to do anything else?

**Jamie**:
Exactly. Right. Exactly. And I like that you know, you all took this idea of hey let's use gitter to communicate but the gitter client isn't brilliant so let's use this technology that we're working to build a new client for it. I really liked that.

**Chris**:
Yeah, definitely. It's really cool. But I think that's the thing, like you say, if you were dealing with the front end technology and here we are at the front end client and you know picking holes in and cool, well unless you use this technology to build something better. So hopefully we're going to a release soon.

**Jamie**:
So does this mean then since you said that a number of the, uh, the controls and packages were things that you had foreseen a need for, um, in your sort of day to day work with Blazor, does this mean then that those packages have been sort of tried and tested in a realistic environment? Or are these more sort of thought process and a thought experiments here? So we could use those messages in Blazor?

**Chris**:
Yeah. The idea is initially we're like, okay, I was thinking to myself, right, what do I want to do here? What would be useful to people? And I though the easiest way for me to work out with be okay, well we're about to start building this new app. What would we use? So I started from there and started playing around with some ideas to see how things went. And then I guess like most things really, I started off trying to just get something to work. And then once I got something to work, I tried to improve it to make it more useful. So we're now using a few of these components in our project at work. So they're in something that's going to be in production. Obviously when we find a shortcoming in one of them, we try to then improve them so that then obviously anybody else who wants to use them in the community, he can hopefully get the benefit of that. I mean that's really the whole, the whole thing of open source isn't it? And sort of try to make improvements for everybody.

So hopefully fingers crossed that, you know, certainly as time goes on as well, like they'll have more features, out. I hope you're finding more and more useful. Obviously anybody can raise any issues, they'd want any feature requests, things like that. Anyone who wants to do PRs to improve stuff they can. Again, it's all open. So that'd be great. But yeah, we were trying to battle test them at work as well. And then again, as we find things that we need that aren't there, then we'll add them as well along the way. I know we have work, we use a lot of open source stuff and certainly with this, we feel this is an opportunity to give back because I think you know, it's very easy to take from open source if you use open source a lot and not necessarily always give something back in return. I don't mean that in an nasty way. As I say, certainly at work you kind of just want to get the problem solved. Oh, they're cool. There's this package. I'll use it. With this because Blazor is certainly very new and things like that. We know we see a very, very early adopter of it. We're trying to help people who are coming behind this by sort of adding any new packages we find.

**Jamie**:
I like that. I'm like you're saying it's very easy to, not to make it sound bad for people who do this, but it's very easy to take from open source and not give back and that can be either, you know, the person who's doing it doesn't feel like that they can contribute towards or maybe they just don't have time. Like you said, maybe it's something that they need to get solved for work or I was trying to explain to someone, a friend of mine who's not in any way technologically anything, he likes to call himself a "typical end user." You know, I'm not sure what that means, but he said to me, "What's this open source thing?" Then I said, "it's everybody wins. Nobody loses. Everybody wins. Because if I use it and I spot something where maybe it could be improved slightly or maybe my journey with using it isn't brilliant and then I contribute something back and say, 'Hey folks, this doesn't feel brilliant to me. It caused me an issue when I was trying to use it, here is what I did and here's why I think it caused an issue.' That then makes that library, process, function, whatever better for everyone who uses it" or I get told "shut up, you're not using it wrong."

**Chris**:
Yeah, definitely. I mean that is the big thing and I think you touched on there as well. I think there's also a lot of people I think who would really like to contribute, but they're worried about how they can do that. For me it was "Oh my god, I going to pull my code out here and I'm just going to get slated because it's terrible or something," you know, that kind of thing. I think initially it can be quite a, I guess a bit of a daunting experience, putting your code out there so that anybody can see it and potentially critique it. But I think I'd say to anybody who's wondering, you know, I just say, I think you just want to just get involved. The open source community is fantastic. I guess like everything, there's always some negative people, but you know the majority of people aren't that, you know, certainly can say now as someone who maintains open source packages, I'm happy for any help because it's anything that can sort of save me a bit of time so I can do something else somewhere else or whatever is always welcome.

**Jamie**:
Even just reporting when something goes slightly iffy I think can really help. Like I said, here's what I did, here's the lines of code I used, here's what I expected it to do. And it didn't quite do that. And maybe it's my misunderstanding of how the system is meant to work, because even then you can feed that back into documentation. Well, okay, so we've had five users who've said they've used this library and they followed the documentation. Then it didn't quite run correctly. Maybe we need to change the documentation. Maybe we need to make it more explicit as to what to do, or maybe we need to make a change to the code because in that situation we don't want it to do that.

**Chris**:
Oh, 100% definitely. I definitely have both scenarios that you've mentioned there where it's been scenarios where the documentation I've written hasn't been quite explicit enough and it's led someone sort of into the pit of failure instead of the pit of success. And that feedback is meant, I could be much better with your documentation, which is fantastic. You know, on the other side of it, I've had someone not surprisingly, plenty of bugs in stuff that I've done as well. I, it's always great to hear about them and then, you know, being able to get them fixed. You know, the worst thing I think is sometimes where I think for me is a, as an open source maintainer is the, you write something and you put it out there and you kind of don't really hear anything and then you're like, well is it because everyone's, it works and it's fine or is it not working? And that's why no one's saying anything cause it just they download it, it doesn't work and then off they go? Um, so I think it's definitely great to get feedback either way. Even if you don't want to necessarily contribute code or anything, just, you know, that bug report is valuable.

**Jamie**:
Definitely. Or even just reaching out and looking through the issues. And so I know that the .NET team do this. They'll post issues in [CoreCLR](https://github.com/dotnet/coreclr) for instance, and to get an idea of how to prioritize these tasks, they ask for people to vote on them. So you know, leave a little a thumbs up or thumbs down on something just to say whether you would be interested in seeing this fixed in the next version. Knowing that there is an issue out there that people are having and you know, maybe you've got two issues and you're thinking, well, I really want to fix this one cause this will be fun to fix. But this other issue is one that people are actually facing.

**Chris**:
Definitely. Yeah. I mean at the end of the day there's only ever a finite amount of resource whether you're doing open source in your spare time or your company, it will be open source in public like Microsoft. Now ultimately there's only a set amount of resource and you have to prioritize my somehow. That is definitely a great way to do it.

### Version Numbers Galore

**Jamie**:
So we're recording this the weekend after Build 2019 and it was only a few weeks ago that Blazor lept. And I do think it's a proper leap from 0.9 all the way up to 3.0-preview-four. Now, I didn't check before I started recording. There may have been a preview five or even a preview six, I'm not sure. But considering that the initial public release was only a year ago, you know the initial development of Blazor has been lightening quick. It does have a bit of a pedigree doesn't it? Cause it goes back to [.NET Anywhere](https://github.com/chrisdunelm/DotNetAnywhere), which was an open source thing and that has, it's a sort of source in Silverlight and things like that. But like it has come on so quickly in the last year version numbers sometimes don't really mean anything when you go from 0.9 up to three but maybe it means a lot to go from 0.9 up to three. As someone who's been watching that really intently, has that been an exciting ride? Has that been just oh yeah, they've added this new feature or whatever? Or has it been, oh my goodness, look at this!

**Chris**:
Yeah, it's been amazing. I found Blazor think it was late January or early February, 2018 and I believe 0.1 came out. I think I'm writing something about the 22nd of March, 2018 I saw [a talk by Steve Sanderson or _the_ talk by Steve Sanderson](https://www.youtube.com/watch?v=MiLAE6HMr10) where he showed C# running in the browser using WebAssembly on the .NET Anywhere runtime. And I think he even had the jaws dropping of the owners of Microsoft and you know, by March it was into experimental and they were, you know, version [0.]1 was released. So that was a quick thing. Anyway, just to go from, I think that kind of demo. So sort of a go at one as a preview within a few months anyway. But yeah, it just hasn't relented. So you think there's been a Blazor at around once a month-ish since then. But yeah, it's just been feature after feature after feature.

So I think one of the cool, really interesting things about the way that Blazor has been developed is that you've got this concept of the Blazor engine for want of a better way of putting it, which is goal of the component model in it. So that's where you've got all your things like the routing and the component model life cycle, things like that. That's where all of that sits, but that's almost can be used on its own. It's separated from the rendering. Blazor has two rendering modes, so it's got a client side mode in a certain side mode. And in client side mode Blazor that runs on Web Assembly and you get that classic SPA running on the client. Then you've got server side Blazor, which is actually running off the server, uses a SignalR connection to the client and just does sort of deltas to update across there. So that's, that was a huge thing that I think it was Blazor 0.5 when this concept came out. So you kind of got that very big jump very early on in the architecture and then sort of going forward after that and you just have constant improvements on top of that. But because this kind of model in separate from the rendering side, it's kind of happening both rendering options at the same time, which is cool.

So these two models, the server model of this has actually been a sort of committed product for a little while now that was committed sort of towards the end of 2018 which I think is a amazing feat really to say that you know, you've kind of got this thing that was committed to that on the on early 18 roughly 19 sorry - might have screwed my dates up there, but you know within a year you've kind of already got this committed to product, which was a really big thing. And what happened there with you kind of have these two versions going on because server side Blazor will ship with .NET Core 3 that kind of took on the package versioning numbers of the .NET previews. Hence you start then having preview one, preview two.

Client side Blazor stayed experimental until literally a few weeks ago now where it was announced that that is now also going to be a committed product and will be released, albeit not with .NET Core 3 that sometime after it. When that happened Blazor was running on a different numbering system, it carried on the same version. Let's start back on the 22nd of March, 2018 you know, with 0.1 so it carried on using those version numbers at the point it became connected to the next release. They decided to put everything back together, so this is why Blazor jump from 0.9 to preview four. So they were just basically aligning those two versioning system back together again. I think for people looking from outside, it kind of looks a bit of a weird jump, but basically they've putting the two hearts of Blazor back together again with that version change.

Back to original question about the speed of development. Yeah, it's been a roller coaster. It's just been new stuff, new stuff, new stuff. Really, I think to be honest, very recently we went from preview four to preview five. Preview five released when Build started, and that's probably the first release we're having in, I think as long as I can remember really, where it was, there wasn't really anything new as such. It's more just bug fixes where you didn't have a new thing to learn and obviously I think that's because we started to get ready now for releasing the service side version of Blazor with .NET Core 3. So, there's a bit of stabilization going on.

Preview six which is the next one that's kind of back to normal Blazor feature churn out. There's going to be loads of cool stuff in there. There's going to be an authentications coming in that one which I think is something that's been anticipated by the community for quite a long time. We've kind of been able to do authentication but it's been not been anything over the official. But with version six we're getting at that, which is awesome. There's a whole plethora of other bits and bobs. We've got directive attributes coming as well. So I've got to look into those myself to be honest, about how they function and how they're gonna work. We're gonna have some multi product static content stuff. So for a while now service side Blazor hasn't been able to load static assets out of NuGet packages. So if you create a NuGet package like, some of mine have javascript in them, they don't get imported properly into service side Blazor projects. But I think the preview six actually now be fixed. So that will start working again as well. Then we'll see what the stabilization bits and bobs in there.

But yeah, it should be another good cool release with lots and lots of stuff in it. So yeah, it's just been a rapid fire of fixes, I've just, I don't think I've ever seen something evolves so quickly. But then hopefully this is, you know, the sign of the pedigree of the project have been Steve Sanderson and, and you know, the rest of the team . I just, you know, they have great, great developers.

**Jamie**:
Can you see Blazor and Web Assembly sort of taking the place of SPA frameworks and javascript or is it just gonna be, you know, here's another tool in your tool belt and if you want to use it, you can. I know you're very, maybe, evangelical and maybe not the right word, but you've come across as really excited, very into the fact that this is a new thing. But taking that, if you can, taking that hat off and just becoming like a developer rather than super excited Blazor person. Can you see it sort of taking the place of traditionally of Javascript or you know, is it something that would be more, just use it if you to?

**Chris**:
Yeah and like you said, I take the Blazor hat off for a minute. I think being real about it, I personally don't see javascript going anywhere, certainly for a good while. I think at the end of the day, there are plenty of developers out there who like working with javascript. They like working with the various javascript frameworks that already exists. And a bit like we alluded to earlier, .NER developers moving WebForms, applications forward and things like that. There needs to be a good reason to do it. And if you're not gonna get anything extra, by moving to Web Assembly. If you have a perfectly working application, it's working with Angular or with Vue. I don't think there's anything that would make you change there and then. I also think that at the moment Web Assembly is very, very new and they're still, bits that are missing. I mentioned earlier, you can't interop directly with browser APIs, you cannot manipulate the DOM, you still have to use javascript for those things. These are obviously things that are being worked on. You know, Web Assembly will be able to do those things going forward. But that's gonna take time.

In terms of general performance, you know, um, AOT and things will make a big difference to Blazors specifically. You still got better performance with Javascript than you do with Web Assembly. Um, certainly with Blazor at least.

So, yeah, I think like you say, taking the non-evangelical view of it, you know, I don't think they're going anywhere in the future. And I do see Blazor certainly being another tool in their tool belt. I don't think there will ever be anything in programming that's a silver bullet. And I think it's always the case of picking the right tool for the job. You know, I think if you're in the .NET world, then I think Blazor is something you should definitely be looking at. But yeah, I think if, yeah, you're not, you've got javascript skills and you're used to that and that's what you work in, then I don't know if I say anything that could give a good enough reason to change.

**Jamie**:
So my opinion of that is a case of it's great to know that it exists and um, you know, if you're, if you're not a .Net dev, yeah, definitely. It's worth knowing that it exists. And even if you are a .Net dev, it's worth sort of looking into just to show, hey, you know, there's this other technology that you may not be using in your production systems because you know, maybe you can't get the end of the sign off for it, but it'll be worth knowing that it exists. So then you can say, ah, so this is how they're solving this issue. Maybe I can adopt something similar.

**Chris**:
Yes, definitely my view of that very much is at the moment. I think when we're looking a year down the line, two years down the line, things are going to be changing rapidly. I mean if the pace of Blazor's development continues, you know, in another couple of years, who knows where we'll be. But Blazor also does rely on underlying things, Web Assembly being the main one. Mono well because it runs on top of the Mono runtimes, [which is] compiled to Web Assembly. So that needs development and things like that. So and now obviously since Build, we now know that we're moving back to a single framework of .Net 5. What will that bring? And how will that work? And like I said, I think for the future, I think I've really struggled to bet against it as being, you know, a real big player. But yeah, I think, um, I think to say javascript would be gone entirely is yeah. I don't think that's going to happen.

**Jamie**:
Okay. That's fair enough. So it's not going to be the Javascript killer. That's fair enough.

**Chris**:
I personally, I've used javascript for a lot years, you know, it is what it is at the end of the day and I've used it and enjoyed it and typescript, I've enjoyed using that. However, my preference would be staying C# and that's why I liked Blazor. Um, but yeah, I don't think anything really dies in IT, does it?

**Jamie**:
Know that's true.

**Chris**:
They're still COBOL applications running nowadays and things like that. So I don't think anything dies.

**Jamie**:
No, that's true gotta have that backwards compatibility.

**Chris**:
Exactly. Yeah.

**Jamie**:
So where can folks who are listening go to learn more about you and Blazored and all the different projects you're doing? Where's the best place to find out about Chris stuff?

**Chris**:
So for me personally, then you probably best go into my blog, which is [chrissainty.com]. That's where I see all my blog posts are going on there and things like that. Then you've got the [Blazored](https://github.com/Blazored) on GitHub. So if you go to my blog you can get to my GitHub,  you can get to Blazored. That should be easy to find. I think if you're just interested in learning more about Blazor overall then please come and have a chat with people in Gitter. There's loads of really knowledgeable guys in there and you can get help with anything you need in that. This really is a fantastic community. I really can't speak enough about the quality of people who devote their time and effort to help people with Blazor problems in those rooms. So yeah, outside of that, the other place you can probably get hold of me is on Twitter. So [@Chris_Sainty](https://twitter.com/Chris_Sainty).

**Jamie**:
I guess all the really remains to say, is thank you ever so much for being on the show. Like I said at the beginning, you know, we're all living really busy lives and I don't know about where you are, but where I am, it's a really nice day.

**Chris**:
Yeah. It's lovely.

**Jamie**:
So dragging you into, presumably into your house to talk about Blazor for an hour rather than letting you go outside and enjoy the sunshine is a bit mean of me, I think.

**Chris**:
No, it's always my pleasure and not, it really doesn't take a lot to get me to talk about Blazor, so, yeah.

**Jamie**:
Well, thank you so much for being on the show, Chris. Yeah. It's been a pleasure to connect with you today and talk to you about Blazor. Thank you ever so much.

### Wrapping Up

That was my interview with Chris Sainty. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and a full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/).

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Sign up for the mailing list](https://buttondown.email/dotnetcoreshow/)
- [Join the Slack group](https://join.slack.com/t/thenetcoreshow/shared_invite/enQtNjIwNDY1NDk4MTE3LTM3NWZiMDAxMWVlMDQyZGU3NDAyYzgyY2EwYjk2MmZlMjU2NDI4YTNjYzVlZDc2YzYxMDExYjFhZjYzMThlMDM)
- [Support the show on Patreon](https://www.patreon.com/TheDotNetCorePodcast)
- [Chris Sainty on twitter](https://twitter.com/Chris_Sainty)
- [Chris's website](https://chrissainty.com/)
- [The Phoenix project](https://www.goodreads.com/book/show/17255186-the-phoenix-project)
- [Blazored](https://github.com/Blazored)
  - [local storage package](https://github.com/Blazored/LocalStorage)
  - [localisation package](https://github.com/Blazored/Localisation)
  - [modal component](https://github.com/Blazored/Modal)
  - [toast component](https://github.com/Blazored/Toast)
  - [menu component](https://github.com/Blazored/Menu)
  - [gitter client](https://github.com/Blazored/Gitter)
- [SQL-MisterMagoo](https://github.com/SQL-MisterMagoo)
- [Bletris](https://sql-mistermagoo.github.io/bletris)
