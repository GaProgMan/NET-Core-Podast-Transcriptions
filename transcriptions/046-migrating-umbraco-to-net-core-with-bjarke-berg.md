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

I am your host, Jamie "GaProgMan" Taylor, and this is episode 46: Migrating Umbraco to .NET Core with Bjarke Berg. In this episode I interviewed Bjarke about Umbraco HQ's plans to migrate Umbraco, the CMS used by over half a million website, over to .NET Core. Some of you may know Bjarke from his work at Umbraco HQ, his talks at the many Umbraco events, or the help he gives out on the Umbraco forums and Slack channel.

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Bjarke's Introduction

**Jamie**

The first thing I'd like to say is thank you ever so much for spending your Wednesday evening - and it's a little bit later for you than it is for me. So, you know, spending part of your late Wednesday evening with me talking about what we're about to talk about. So, thank you ever so much for that.

**Bjarke**

Yes. Thank you. I appreciate you being part of the podcast that I'm actually listening to myself.

**Jamie**

Excellent. It's always good to hear that someone's listening.

**Bjarke**

I am.

**Jamie**

Fantastic okay.

For listeners who may not know of the work that you're doing at the moment or where indeed you've work for - because maybe they didn't listen to the intro: Could you give us a quick, brief introduction to yourself and the work that you're doing at the moment?

**Bjarke**

Yeah, sure.

So today, I am a senior developer at Umbraco HQ. I am part of our core team with the responsibility of our open source CMS, and some of our closed source plugins to the CMS. I'm mostly a back end developer, and currently am the project lead for the transition into .NET Core. So I spend most of my time on this project. My journey started back at the age of 10 or something, where I found interest in HTML. My Dad was a hobby programmer who could teach me a little bit. And around the age of 16, I tried ASP Classic because I needed some more dynamic websites. Then as a Master in computer science, I was introduced to real programming languages like Java, and C, and c++. My first professional job was as a Java developer, but I also learned about the MVC pattern that I used today. And the last eight years or so I have been a .NET developer, mainly on MVC and C#. And since .NET Core and release candidate six, I have been part of working on that. That's my journey so far.

**Jamie**

Wow. Okay. That's an interesting background. A little bit similar to mine, except that I didn't come into development from the web background. I had a machine that would run BASIC, and would spend my evenings just typing away, seeing if I could get something to happen. Eventually got something to happen, end then I discovered the unbridled joy of, "hey, this thing actually works and does where I want it to." And I've been hooked ever since.

**Bjarke**

Exactly. And BASIC or Visual Basic was pretty easy to get started with. That was also an ASP classic, I used Visual Basic.

**Jamie**

I haven't used Visual Basic. But this was old school BASIC: All caps, you know, with the the green screen monitors

```basic
10. PRINT "Hello World"
20. GOTO 10
```

That kind of thing

**Bjarke**

Sure. Good times.

**Jamie**

Yeah, your applications didn't require 500 gigabytes of JavaScript libraries just to get them to compile.

**Bjarke**

Exactly.

**Jamie**

Okay, so we're going to be talking a little bit about Umbraco today. Now obviously because I have a different accent, I pronounce it Umbraco [hard k sound]. But I've noticed that both you and other folks on the team say it Umbrago [softer g sound]. But I think that's just the different pronunciations.

**Bjarke**

Yeah, exactly. I don't know how to pronounce it correctly, because it's a misspelling of the Danish way to say [allen Key](https://en.wikipedia.org/wiki/Hex_key)

**Jamie**

Oh right. I did not know that. So that's interesting. I have to make a note of that. I think that's really cool.

So yeah, we're going to talk about on Umbraco today. But you could totally be a .NET developer and have not heard of Umbraco or ever used Umbrcao. So I was wondering, could you give us a quick description of what it is, and the types of problems that it solves?

**Bjarke**

Of course.

So it is a content management system. So basically some software that is used to manage the creation and modification of digital content. It is built on .NET Framework, and it's an open source project. We have around for 450 contributors on GitHub. And [during] the last [Hacktober Fest](https://hacktoberfest.digitalocean.com/) we had almost 500 PRs from 100 different countries. So pretty big open source project, I guess.

Originally, it was just a web content management system. But nowadays, it's used for everything: apps, chat bots. Yeah, even an ice cream bar managed by robot. So we are known because we are intuitive and flexible, especially for the editor experience. We are extremely extendable. And we have hundred percent freedom for the front end or the website you are building. For programmers. I'm used to just calling it, "a UI on top of MVC," because we have data types, like you have data types in C#. So a `ShortString` [in Umbraco] could be comparable to us to a `string` [in C#] with a MaxLength [attribute] . And we have drop downs, and grids of nested data types, and every kind of data type, and you can build your own. And then we have `DocumentTypes`, which is basically the same as models in MVC. And finally, we have `Templates`, which is just razor views, and it's pretty easy to get started. We have a cloud solutions with free trials or course, [at] [Umbraco.com](https://umbraco.com). And you can also just start a new empty web project and then download our NuGet package, and then you start it.

### Migrating Umbraco to .NET Core

**Jamie**

I have used Umbraco in the past for client work, for employment work, and for playing around with it. And I have to say the it's one of the easiest .NET based CMSs, I think. That just freedom, you know, you don't have to do anything other than pull down a NuGet package, and you're done. So I compare it to the experience with say [Sitecore](https://sitecore.com) were have to buy a licence, install some software, and cross your fingers, and hope that it works.

**Bjarke**

Yeah.

**Jamie**

It was my friend, [Paul Seal [from Codeshare]](https://codeshare.co.uk) who got me into Umbraco with his wonderful videos, his tutorials on, "let's set up an Umbraco website," or "lets use this particular feature or that particular feature". Interestingly, one of the things that I've done with Umbraco a while back, is I actually used it [to give a talk on Blazor](https://www.youtube.com/watch?v=ULai6sIbeAU), which is something we've talked about on [the podcast](https://dotnetcore.show/episode-25-blazor-you-want-to-run-net-where/). And it used the headless on Umbraco, which I believe is his own project. But what's interesting about that it's always been a .NET Framework application, right? But I remember I got in contact with you around the time that both yourself and [Niels](https://twitter.com/thechiefunicorn) had publicly announced plans [to] migrate to .NET Core. I was wondering whether you could give us a little bit more information on that. Is that a thing that's going forward? Is it just something that's in planning stages?

**Bjarke**

We are currently in the process of migrating to Core right now. But we do it in small iterations. So instead of a big bang approach, we aim for always having a development branch that is working. And the first step is to move our bottom layer in our architecture in to .NET Standard. But to do that, we need to break a lot of circular dependencies. We have even runtime dependencies because we have taken a community package into the project, because it was so good. But we need to break these kinds of dependencies. And we need to eliminate the usage of the `System.Web` namespace and it's pretty known by all of our assemblies. And sometimes we even need to refactor switch cases into polymorphism if some of the cases cannot be migrated. For example, SQL Compact Edition: that is not supported in .NET Standard. We also aim for having as few changes as possible, because the current version of Umbraco version eight is still under active development. And we need to merge all these features and fixes into this branch of .NET Core.

**Jamie**

That does seem to sort of echo the advice that I've been given in the past. I believe [we had Iris Classon](https://dotnetcore.show/episode-24-migrating-from-asp-net-to-asp-net-core-with-iris-classon/) on the show before, and she was talking about techniques for migrating from Framework to Core. And essentially, she said, "pick the smallest part that can easily be converted to either Standard or Core and start with that, and then sort of build up from there," rather than. like you say, "take the entire code base, scrap it all and start again," or "you don't want to start messing around with csproj files. When a project is as big as Umbraco is."

**Bjarke**

Exactly is, it will be a big [challenge] to make a big bang approach. Maybe with it will become faster done. But I doubt it.

**Jamie**

I feel like I'm the "migrating small parts of the application path," that would probably pick up speed quicker, if that makes sense. It would be more agile to do that. If you were to start again and do a full migration of the entire application, you may be looking at a couple of months of instability. Whereas right now, if you're picking parts out and going, "let's convert that let's fix this. Let's refactor that," it starts to sort of build up very quickly. It becomes almost like a snowball: you start with a small thing and add to it, and add to it.

**Bjarke**

Exactly.

**Jamie**

So we've talked about Umbraco being a full featured CMS. And as we mentioned earlier on, there's already a headless version of it. So when I used it, it was a sort of preview or beta. I haven't managed to keep up with it. So I don't know if it's still a preview or beta. But with the migration over to Core, is this going to be a full featured version of Umbraco? So aside from things like SQL Compact Edition, and certain maybe smaller features that aren't easily migratable, is it going to be a full migration of Umbraco to .NET Core? Or is it going to be just parts of it? Or are we just talking about the headless version? What was the plan? Obviously, I know that you're at the beginning of the project. So it might be a case of what you say now may not be true in say six months time, but what's the plan at the moment?

**Bjarke**

Yeah. First of all, our official headless offering is a pure SaaS product named [Umbraco Heartcore](https://umbraco.com/products/umbraco-heartcore/), and it's built on top of the CMS and it includes a lot of cloud services like CDN and storage and so on. The migration will be for both. But the users are of Umbraco Heartcore shouldn't care, because it's just a SaSS offering. But people have used the full CMS as a headless for a long time also. And these kind of versions of headless are also built on the full Umbraco, but we need to be migrated to .NET Core also.

**Jamie**

I didn't realise that [Umbraco Heartcore] was the same product, but with extra stuff added on. I thought it was perhaps a slightly different version. I say that because a friend of mine, James Studdart [a.k.a [Cynical Developer](https://cynicaldeveloper.com)], had created an almost headless version of Umbraco a few months before the first public previews of [Heartcore] were released. But then I guess if you're saying other other consumers of Umbraco have used it as a headless CMS in the past, then that kind of makes sense. So then that must mean that there is a, almost like a public API to sort of poke out for your Umbraco installations.

**Bjarke**

No it is built on top of the full framework, or the follow the CMS. So it's basically just a package on top that disable[s] some of the functionality, and add some new functionality, including a lot of cloud services. So there will be a CDN in front of all the requests. Also, if I remember correctly, we also move some of the image processing into functions. And, yeah, of course, use Cloud Storage.

**Jamie**

I hadn't realised that. So that's interesting to know. With the migration to Core as it is sort of planned out, is this perhaps just a performance thing? Or is the goal for the long term life of Umbraco? Or is it more so that you can support the cross platform story that .NET Core supports? Because you know, traditionally in Umbraco has been .NET Framework, which means it's Windows only. So is it because you want consumers to be able to host on Linux? Or is it more a case of, "hey, the future is .NET Five in November onwards, so we'd better move across." what's the big reason for moving across to Core?

**Bjarke**

So the long term goal is, of course, the cross platform support, because it opens up for a larger set of potential users and community members. But the short term goal is more about the long term life and performance. Because it's pretty easy for, or it's important for us so that it's easy to get started using Umbraco - also for no developers.And one of our dependencies, like SQL Compact Edition is not supported [on] cross platform, so we need to find alternatives to that. So the first cross platform version will likely only support SQL Server

**Jamie**

I mean, that makes sense because if it's not supported in the Runtime you are using, you have to support it some other way.

**Bjarke**

Exactly. We looked into Sqlite, but it's pretty slow compared to SQL Compact Edition. But on the other hand, we don't recommend anyone to use SQL Compact Edition for production.

**Jamie**

I do remember, again when I was talking to Paul, about getting set up with Umbraco, he was saying to me, "you can use Compact Edition if you don't have a full SQL Server licence or whatever. But yeah, don't use it for production because there's not fast enough, it doesn't the features. Just the support for it isn't there." Not in on Umbraco doesn't support it. But like Microsoft themselves, say, "Hey, you know, don't use SQL Compact for your production environments."

**Bjarke**

Exactly. Yeah, but it's a good tool to let it be easy to get started.

**Jamie**

So you've mentioned Sqlite, and how you looked into it and maybe that's not one of the future things at the moment. Are you perhaps looking into other database technologies? Or is it very much just a case of, "let's get on Umbraco .NET Core ready first, and then if there is a plan for it in the future, that's a future development. That's not something we need to worry about now."

**Bjarke**

Yeah, exactly. It will be a future development, not part of this project.

**Jamie**

In the future. If I get an Umbraco for .NET Core, I still need a SQL server somewhere?

**Bjarke**

Yes, you will do that.

**Jamie**

That's fair enough. I mean, Microsoft have ported SQL Server to Linux environments anyway. So you know, it's not like you suddenly then have this dependency on a Windows Server.

**Bjarke**

Exactly. And I used it in Docker images, and it's pretty good. I think.

**Jamie**

I remember trying to help a friend of mine get started with SQL Server in a Docker image. It took a little while because of the command line switches to get it running, and then we were running before we could walk. I don't know whether that's a metaphor that crosses the language barrier, but we were trying to get the SQL Server inside of Docker running but also trying to hide the usernames, and passwords, and credentials for setting it all up, and port numbers, and things. And this was before we knew about [Docker secrets](https://www.docker.com/blog/docker-secrets-management/). So we were trying to figure out a way of maybe encrypting that data before it goes in. And, yeah, that got a bit confusing. But once we dropped that requirement, the SQL Server inside of Docker is brilliant, and fast. It's not like Microsoft have done a part of a job in porting it, it seems like it's all there, which is useful.

**Bjarke**

I agree.

### What Issues Have You Already Planned For?

**Jamie**

So this is a potentially difficult question to answer, and perhaps a big answer. But as part of the the plan for the migration, what sort of issues have you already anticipated, going into that migration? You've got a massive code base with potentially several layers of API's which are talking to each other, and maybe API's which are no longer supported in Core but they were there in Framework. So have you any plans for tackling that issue? Is this even something you need to worry about? Was there a big planning committee of, "this API isn't supported in Core or Standard. So how do we move everything across?" What was the planning stage like?

**Bjarke**

Yeah, so we have identified some third party dependencies that [are] not .NET Standard compatible. As mentioned earlier, SQL Compact Edition will only be supported on Windows. And we also have a dependency on [Lucene .NET](https://lucenenet.apache.org/) it [is] currently only in beta for .NET Standard, and we will need to update for a new version for that anyway. And then we have a NuGet package with an implementation of a [B+ tree](https://en.wikipedia.org/wiki/B%2B_tree) and that package is not compatible with .NET Standard, but the exists forks but we will need to try these out. And of course, in the Framework itself, we use some API's, like [CallContext](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.remoting.messaging.callcontext?view=netframework-4.8) [LogicalGetData](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.remoting.messaging.callcontext.logicalgetdata?view=netframework-4.8) and [SetData](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.remoting.messaging.callcontext.logicalsetdata?view=netframework-4.8). And these are replaced today by [AsyncLocal](https://docs.microsoft.com/en-us/dotnet/api/system.threading.asynclocal-1?view=netcore-3.1), and then most of [System.Web](https://docs.microsoft.com/en-us/dotnet/api/system.web?view=netcore-3.1) namespace has changed. Yeah, and finally, we also probably need a new install process because NuGet has also changed a lot. And we, we depend on install and uninstall scripts.

**Jamie**

Potentially a lot of gotchas, a lot of issues, as you sort of enter into this project of moving across.

**Bjarke**

Yes, hopefully we have found most of them upfront, but you never know.

**Jamie**

So what was that process like? Was it a case of, "Okay, everybody go away and do a deep dive into the code base as it stands, and have a deep knowledge of Core versus Framework, and NuGet versus new NuGet" What was that process like? Was it that or was it, "everybody go off and pick an area And focus on that"?

**Bjarke**

No, actually, we have something called [Umbraco Retreat](https://our.umbraco.com/community/umbraco-retreat/) the weekend before our own conference [Code Garden](https://codegarden20.com/). And we [were] a team of four people - I guess three from HQ and one community member - that was on the .NET Core topic on that weekend. And we identified most of these things by searching the code base and looking into ways to solve this big project.

**Jamie**

So if you don't mind me saying the fact that you mentioned earlier on there are 400 to 500 active contributions towards the Umbraco project on GitHub. And there were four people actually do the planning process. That's pretty huge, from my point of view. I couldn't even imagine how that would have worked. If I'm honest.

**Bjarke**

Of course it was just the beginning of the process. But we identified a lot of stuff and we came up with ideas [for] how to do a new architecture to make it easier to move some of the code base into .NET Standard. Yeah, small iterations.

**Jamie**

Sure that makes sense. And you know, like we said earlier on, "start with the small things and build up. And it will hopefully, very quickly migrate over."

### Will the Migration be Open Source?

**Jamie**

Potentially problematic question, [but] I hope it isn't: Umbraco is famously open source is free to use unless you want to go with the SaaS option, and get support for that and things. But the whole thing is open source. I remember going to an Umbraco hackathon as part of one of the UK events and actually creating a pull request and watching that whole thing go live, you know, they had, I think it was [Sebastiaan [Janssen]](https://twitter.com/cultiv) was there

**Bjarke**

Exactly. He is our head of pull requests.

**Jamie**

And he was sitting there shouting out, "pull requests completed!", "pull request completed!", and "everyone can do a pull request!" and we all got quite excited. The general development of Umbraco is quite open,bBut what about the migration project? Is that something that is still open source? Are you doing things in a closed source area to try them out? And then sort of going, "Hey, here's our branch for creating cool. Look what we've done so far."

**Bjarke**

No. Indeed it is in the open. We are, at the time of recording, establishing a community team to help us. We plan to have bi-weekly meetings to keep everyone up to date. And hopefully, this will make the team available to help other community members and also help with some of the more advanced coding tasks. Yeah, and regarding being open, I will also communicate on the [official Umbraco blog](https://umbraco.com/blog/) when something interesting happens like we are ready with an lfl beta version. I will also attend that some of the Umbraco conferences and do a talk about the current status - for example, Umbraco Spark in the beginning of March, and hopefully also own conference called Code Garden. But I know there was a talk sumbissions, so I don't know yet.

**Jamie**

So there's lots of chances for folks to find out about the actual progress of the open source migration, even if they're not watching the GitHub account?

**Bjarke**

Yeah, there should be many options.

**Jamie**

And obviously, it's worth noting that this episode of the podcast may not go out until after Umbraco Spark has happened. And you'd mentioned earlier on about [how] maybe you'll be able to attend, maybe not because of certain things that are happening or sort of the schedule of everything. And hopefully, folks are going to those events can and will have seen your updates, but these things are not set in stone, are they?

**Bjarke**

Nope.

**Jamie**

You mentioned that about the community group that will help to work on that migration. Is that something that anyone can join? Or is that just, "you have to submitted this many requests the Umbraco source code"? Or is it just anyone could say "hey, I'd like to help it."

**Bjarke**

Yeah, everyone [is] welcome to help out. We already some up for grabs tasks on our [GitHub](https://github.com/umbraco/Umbraco-CMS). But to be honest, the biggest problem right now is to find tasks that do not have a tight deadline before we need the changes. We can't expect volunteers to make the job with tight deadlines. But we will do whatever we can to find tasks due to a massive interest from our community to help on this project. But when we are closer to the end goal, we were planning to render some hackathons or whatever.

**Jamie**

Sure, okay. Now, this is definitely a very difficult question, because I don't want to tie anyone down to any kind of deadlines or anything. And I remember mentioning it to [Niels](https://twitter.com/thechiefunicorn) at Umbraco UK Fest 2018. I've mentioned, "hey, if you guys start doing a migration to .NET Core could I have a talk with you, or maybe the person involved with it," that kind of thing. And the answer from him was, "I don't want to talk about it because I don't want to give the community the wrong impression and say something that sets expectations." But with that in mind, do you have any kind of deadlines? Or is it just a case of this will continue until the work is done?

**Bjarke**

Of course, we will continue until the work is done. But sure, we aim for having something public, like an alpha or beta in the second half of this year.

**Jamie**

Wow. Okay. That's really impressive. I just want to caveat that, because it has happened in the past where people will listen to the show, pick out a point where someone says, "Hey, this may happen, it may not," and have taken it as, "this is going to happen." So obviously, that's based on a number of internal deadlines, and it is not a fact that it will happen.

**Bjarke**

Exactly. We have estimates, and estimates are basically just guesses.

**Jamie**

So yeah, the point that I'm trying to get at there is that, although you said you're aiming to have something out by this point, doesn't mean that there will be something out by that point.

**Bjarke**

Exactly.

**Jamie**

Excellent. Because you've got to set that expectation there and you don't want to say, "we'll try and get this out," and then people start going, "My goodness, I'd better ditch my old Umbraco installation and start learning Linux," because we don't want people to do that.

**Bjarke**

No, but I expect most of the listeners to be developers who also have given estimates.

**Jamie**

Of course, yeah, so we all understand how estimates can be. How do I put it? Estimates can sometimes be way too long on way too short.

Because we've mentioned it's moving to Core, and you want the long term life of performance and cross platform. Are you going to be targeting any particular platform? Or is it just a case of, "hey, this works on our test benches for Windows and Linux? So that's fine." Are you going to be testing on particular platforms, or is it just, "we'll see what happens"

**Bjarke**

In the short term, we will only be testing on Windows. But yeah, the long term of course, we will at least test on stuff like Docker and so on, I think.

**Jamie**

Sure that makes sense. I guess the problem is if you're moving a big projects like this to a runtime which is supported on multiple operating systems, you need to have someone on board who can support that.

**Bjarke**

Yeah.

**Jamie**

One of the things that I said, I believe in 2016/2017, when .NET vNext, and .NET Core, and [dnx](https://docs.microsoft.com/en-us/dotnet/core/migration/from-dnx) were starting to become popular vernacular, I was chatting to some of my .NET friends who are Windows developers [and] there's nothing wrong with that at all - if you've only worked with Windows, and that's fine. It's an operating system that has lots of support. But I was talking to them about, "this is brilliant, I'll be able to do .NET stuff on my Linux machines." And they kind of looked at me funny, and we're like, "what's the Linux?" or they were saying, "what's the difference?"

**Bjarke**

Yeah.

**Jamie**

The scary thing is that potentially everyone I'm Umbraco HQ, and in the community, would potentially have to support an operating system that maybe they've had no experience with.

**Bjarke**

Exactly. But right now we have actually a lot of Mac users, [who] use a virtual machine to just develop on windows.

**Jamie**

Okay, what I'm trying to get at is that the team isn't just Windows users. It's multidisciplinary people?

**Bjarke**

Yeah. And the community. Of course, if Umbraco was cross platform, hopefully also a lot of Linux users will become part of the community, and Mac users and so on, and could help us at least finding issues.

**Jamie**

That's very true.

It was once described to me as Umbraco is one of the ways of democratising content creation. And once it's available on more than one operating system, the it won't matter so much about the operating system will it? It won't matter that, "hey, this is running on a Windows machine or a Linux machine." And certainly to the end user, we as developers, we will be writing code that I'm Umbraco users, but I suppose the end user, the business user, the marketing person who just wants to change the way the web page looks or to upload new copy for a page, it won't matter to them at all by that point.

**Bjarke**

Exactly. But hopefully, hosting can be cheaper on Linux distributions.

**Jamie**

Yes, that's true. I have noticed that because there is less involved in licensing and hosting is cheaper on Linux, depending on what you're doing obviously.

**Bjarke**

Yeah, of course.

**Jamie**

Because whilst you're not paying for the licence, you may have to pay to get support for, "how do I install this," or "this is broken", or "how do I get these two machines to talk to each other as if their load balanced," kind of thing.

**Bjarke**

Yeah, exactly.

### Keeping up with the Migration and Bjarke

**Jamie**

So then, for this migration to Core, what's the best way to find out what's happening? Is it just go watch the GitHub repo and watch for issues. We've already talked about the best way to help with a migration is to be involved in the GitHub account. But if I want to just keep an eye on the migration, is it watching the GitHub? Is it attempting to go to one of the events? Maybe there might be some blog posts? What is the best way to find out?

**Bjarke**

It depends on the level of detail, because the blog posts will be top level of detail mostly. "Now we are ready with a beta version," or whatever. And of course, on GitHub is specific issues. We will also create requests for comments if we are in doubt about something and need feedback from the community. And if you have questions, you can use [our official forum](https://our.umbraco.com/forum/).

**Jamie**

You mentioned that you need to keep the branch for migrating to Core in sync with an Umbraco eight because there's still development going on there. I'm just interested as to what the plan is for that, because a lot of the migrations that I've come across in the world have been "this product is now done, there is no active development, and now we need to migrate it." But then the added story of, "we need to migrate it but keep it in sync with the other branch." That must be something that is going to cause maybe a few issues, I don't know. Is there a plan for dealing with that?

**Bjarke**

The plan is just to have a task in every sprint to ensure that our branch is always up to date, because the big issue would be if we are if the branches is too different. So again, small iterations is the way to go.

**Jamie**

With those smaller iterations, you take an individual component swap it over, and then if a bug is discovered and then fixed, you can then just copy over the change, and make sure it still works, and then away you go. So it's not a case of migrate everything and then apply the changes.

**Bjarke**

Exactly.

**Jamie**

Okay. So it's slow, small and often changes rather than one big monolithic change. That makes sense.

**Bjarke**

Yeah. And then most of the changes, from the community at least, is on the front end. We do not touch the front end code for this project. The API's between the front end and back end will be the same after the migration. So all of these changes [are] easy to merge.

**Jamie**

Because the front end, it isn't a separate project, but because it's a almost like a facade. It is literally an interface. So I'm thinking this is more of a back end code, kind of you have the interface, `IUmbraco` interface. The user interface is an instance of the interface. The Umbraco. back end is the class, the instance of that interface, ie the interfaces with the database, does all the things and creates all the HTML pages and all that kind of stuff, keeping that UI and back end separate, I guess, will help with that migration.

**Bjarke**

Yeah. So today, our UI is just a single page application that uses web API's.

**Jamie**

Because we mentioned earlier on that Umbraco can be used as a headless, or it can be used with some kind of user interface on there, are there plans to in any way change the user interface or is this like is a is it completely separate?

**Bjarke**

It will be a completely separate development. But we are looking into it because right now we're using Angular JS. And it's not the most recommended technology anymore. But again, it will be a separate project.

**Jamie**

So perhaps in the future, we could see a Blazor front end for Umbraco?

**Bjarke**

I know some of my colleagues, [would] vote for Blazor. So yes.

**Jamie**

I do have a project called [UmBlazor](https://github.com/gaprogman/umblazor). So if you need open source project to steal from...

**Bjarke**

Yeah, we are an open source project. So you're free to just get it started.

**Jamie**

Exactly, exactly. We talked about keeping an eye on the migration to .NET Core. But what's the best way for listeners to get in contact, maybe to ask questions about the migration, [or] provide feedback? Is that a case of check the GitHub, watch issues, join in on conversations, that kind of thing?

**Bjarke**

Yeah. We also have a [public and private community slack workspace](http://umbracians.chat/) that you can join. There's a lot of conversation. Going going on.

**Jamie**

Okay, excellent. I'll make a point of putting the link to that in the show notes. That way if people want to join, they can.

**Bjarke**

Yeah. Cool.

**Jamie**

What about catching up with yourself then? Is it advisable for people to [follow you on Twitter?](https://twitter.com/BjarkeBerg) Do you have a blog? Or is it just the Umbraco? blog? What's the best way of keeping in contact with you? And finding out a little bit more of your input into this process?

**Bjarke**

Yeah, you can use [Twitter](https://twitter.com/BjarkeBerg) and of course, I will blog on the official Umbraco blog. I do not have a personal blog, because life is a bit busy with small kids at the moment. But I'm also available on the community slack.

**Jamie**

Sure. Okay, so there's a number of ways of keeping in contact with you. Let's say someone comes along and says, "Hey, Bjarke, here's a question for you." Can you find out the answer? Not a support question. But, "hey I have a question about the migration." Is it a case of I ask you and then maybe you say, "Oh, that's more of a question for this person," and direct people. Or is that a case of, "I'll go find out for you and come back"?

**Bjarke**

It depends on the question. And sometimes I will redirect them. And sometimes I can find the answer.

**Jamie**

What we'll do is we'll make sure to put links to all of these events. And hopefully we'll see you Umbrtaco Spark if you can make it.

What I wanted to say. Bjarke  is, thank you ever so much for taking this time out to chat with me. I realise we've been talking for about an hour now. And it's really incredibly interesting stuff. Because I'm very interested in this migration. I'm seeing a lot of bigger projects start this migration over the .NET Core. And it's always interesting finding out how other people are doing it. Because invariably, we're all going to have to do it at some point.

So yeah, thank you very much for taking the time out and answering these questions.

**Bjarke**

Yeah, of course, no problem at all.

### Wrapping Up

That was my interview with Bjarke Berg about migrating Umbraco to .NET Core. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and a full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/).

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice - head over to [dotnetcore.show/subscribe](/subscribe) for ways to do that - and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Bjarke Berg on twitter](https://twitter.com/BjarkeBerg)
- [allen Key](https://en.wikipedia.org/wiki/Hex_key)
  - Umbraco is named after a mis-spelling of the Danish word for "allen key"
- [Hacktober Fest](https://hacktoberfest.digitalocean.com/)
- [Umbraco.com](https://umbraco.com)
- [Sitecore](https://sitecore.com)
- [Paul Seal [from Codeshare]](https://codeshare.co.uk)
- [My talk on Blazor and Umbraco](https://www.youtube.com/watch?v=ULai6sIbeAU)
- [Episode 25 of the podcast](https://dotnetcore.show/episode-25-blazor-you-want-to-run-net-where/)
  - which is an edited version of that talk
- [Niels Hartvig](https://twitter.com/thechiefunicorn)
- [Episode 24 - Migrating from ASP.NET to ASP.NET Core with Iris Classon](https://dotnetcore.show/episode-24-migrating-from-asp-net-to-asp-net-core-with-iris-classon/)
- [Umbraco Heartcore](https://umbraco.com/products/umbraco-heartcore/)
- James Studdart [a.k.a [Cynical Developer](https://cynicaldeveloper.com)]
- [Docker secrets](https://www.docker.com/blog/docker-secrets-management/)
- [Lucene .NET](https://lucenenet.apache.org/)
- [B+ tree](https://en.wikipedia.org/wiki/B%2B_tree)
- [CallContext](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.remoting.messaging.callcontext?view=netframework-4.8)
- [LogicalGetData](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.remoting.messaging.callcontext.logicalgetdata?view=netframework-4.8)
- [SetData](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.remoting.messaging.callcontext.logicalsetdata?view=netframework-4.8)
- [AsyncLocal](https://docs.microsoft.com/en-us/dotnet/api/system.threading.asynclocal-1?view=netcore-3.1)
- [System.Web](https://docs.microsoft.com/en-us/dotnet/api/system.web?view=netcore-3.1)
- [Umbraco Retreat](https://our.umbraco.com/community/umbraco-retreat/)
- [Code Garden](https://codegarden20.com/)
- [Sebastiaan](https://twitter.com/cultiv)
- [The official Umbraco blog](https://umbraco.com/blog/)
- [Umbraco on GitHub](https://github.com/umbraco/Umbraco-CMS)
- [dnx](https://docs.microsoft.com/en-us/dotnet/core/migration/from-dnx)
- [Umbraco official forum](https://our.umbraco.com/forum/)
- [UmBlazor](https://github.com/gaprogman/umblazor)
- [Umbraco public community slack workspace](http://umbracians.chat/)
