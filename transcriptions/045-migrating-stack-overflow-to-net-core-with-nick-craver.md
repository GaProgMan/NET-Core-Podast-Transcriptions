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

I am your host, Jamie "GaProgMan" Taylor, and this is episode 45: Migrating Stack Overflow to .NET Core with Nick Craver. In this episode I interviewed Nick about the process of migrating Stack Overflow over to .NET Core, some of the pitfalls in such a migration, what it's meant for one of the biggest web applications in the world, and a few of the things which cause Stack Overflow to fall over. Some of you may know Nick from his work as the architecure lead over at Stack Overflow, his tweets about the migration process, or from his early work in the Q&A space.

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Nick's Introduction

**Nick**

I have to get some work stuff in a little earlier, and statcounter shuts down for the holidays, too - the week of Christmas. We just kind of turned everything off. Well, not the website. But

**Jamie**

I don't think _anyone_ would notice if the website went down over Christmas.

**Nick**

Well, there's a fun fact that I don't tell most people but at a New Year's what we do with a reputation system, we have on the user page, you can go to a [slash users](https://stackoverflow.com/users). And we show top rep for day, week, month, quarter year, yeah. And what we do is a very, very simple job. At UTC midnight, we reset the columns that should be reset to zero. So in a quarter changes, it's quarter, and maybe week and day, right. If it's the week, it's a week and the day day always resets right. And year reflects a lot of rows. It always bombs out. There's just too many users for to succeed on Stack Overflow. So you'll find me on Stack Overflow about 12:01am every New Years, fixing it manually, because it's just not worth automating. It's like once a year you go in and run the thing you're like is it's just not worth it.

So if youre rep is off slightly. That's what happens.

**Jamie**

So does that happens several times throughout the day, like as different geo locations step into the new year or, like, only when you notice.

**Nick**

Oh, so we decided to not care about time zones very early on. We largely considered time zones to be a mistake. Daylight Savings Time was definitely a mistake. So everything is UTC on StackOverflow. We do not screw around with local time. We're just like, "you know what? UTC. That's it." It's just so much simpler. We don't have to worry about anything.

One of the things that's always fun trivia to me is Google has I don't know how many million servers now some number they don't publish, right. They're in Pacific time.

**Jamie**

Oh.

**Nick**

Because it's too big to fix. There's like, "yeah, we can't change it now. There's too many servers." So we decided UTC on and everything goes by that. We do in your browser, if you click some of the pop up windows in the top bar, you'll see what your local time is and wat time that is UTC - we do a little offset calculation. But that's entirely clientside. Everything back end, servers, database, UTC all the time - makes life so much easier. I highly recommend doing that if you're going to run infrastructure.

**Jamie**

That's incredibly interesting, because it wasn't so long ago that I [interviewed Jon Skeet](/episode-40-noda-time-with-jon-skeet).

**Nick**

Oh, yeah.

**Jamie**

And he essentially said, "don't do UTC."

**Nick**

So you can store UTC with timezone information. But if you're going to run infrastructure, you want to have everything on the same page, right? So if you're viewing, if you're debugging an error, so one of the things we do at Stack [Overflow] that; we've done a lot of things that over time turn out to be very good decisions. And we've got some that have been very bad decisions, too. But one of the good decisions is, so when you come in and do a request, we have something `current.Time`, and it's not actually the current time, it's the first time you access that property on a request. And so we kind of hardened that time as a `RequestItem` in the context, and then we'll use it for everything downstream.

So for example: You go up vote, and you up vote someone and that we need to record a vote, and we need to change their Rep. And we need to maybe record something in history, whatever things that are involved in this action, right? All of them have the exact same timestamp. So when we go into database to correlate things later, they're all exact match, not like, "oh, did this happen?" Because if you use like, `getUtcDate`, the tics will be slightly off, right? By lining all of that up and using it for the rest of the request its immensely helpful. It helped us debug and even backfill so many things that may have gone sideways or go wrong or figure out a problem. So bits like that are helpful.

And kind of along the same lines, if you have an issue and you want to go digging in logs, everything being in the same time zone is kind of like needed for your sanity. You know, you want to be converting everywhere. We have this product. I won't mention the name and if I can, but it was an expensive product for network monitoring. And it had the UI in your local timezone, and it was in Flash. So if you're a sysadmin you may be able to figure out what I'm talking about. But it was a really annoying because everything's in UTC and you're trying to deal with it and especially if your remote team you can't even communicate if you're not in the same... like it was it this time like okay, let me go convert that from Queens hours to freedom hours or whatever. Right? And some of the jokes in chat, there's a lot of country-isms in there about how messed up it is. So yeah, we just said, "you know, pump the problem. Everybody, we're on this." When we schedule a meeting, we just kind of put it in and like trust Google Calendar, or whatever it says goes. Like, "we're not screwing with time"

**Jamie**

"Let someone else deal with the difficult calculations of time zone stuff is not our problem," sort of thing. I like it.

**Nick**

Yeah, if you want to do some stuff client side great. Other people have to, right? You're dealing with plane tickets in local time and when you're landing and... Yeah, sometimes you have to. For us, we don't so we don't, if you don't have to do something. Don't do it. It's not like from a, "if you want to be nice and charitable, and do these things and do these features," that's great. If you don't need to do something from a complexity standpoint, don't that's basically how we scale is you don't do the things: you don't need to do simplify and go that route, right? It's just all the little paper cuts, that of doing things you don't need to deal with. There's complexity that just builds over time. You got to stay on top of that and keep it from happening. And then 10 years later, you've got something you can work on. You don't have a quagmire of, you know, spaghetti and things. So it's a principle base of advice. I mean, it sits with kiss, doesn't it?

**Jamie**

base of advice. I mean, it sits with [KISS](https://en.wikipedia.org/wiki/KISS_principle), doesn't it?

**Nick**

Yeah, that's exactly how we state it.

**Jamie**

That makes sense.

We've been talking now for roughly eight minutes, and I'm not even introduced to yet. So could you perhaps give us a quick introduction to some of the work you do when you are developing and when you are infrastructuring?

**Nick**

Yeah. So I am Nick Craver. I'm the... currently My title is the architecture lead at Stack Overflow. I run a team that's a little bit of a wild card. So we help design things, build things, debug things. We kind of bounce around the system as a support team for other teams, so it's kind of a lot of domain knowledge and this kind of stuff, but how things interact. And we help maintain the shared services as well, right? When reporting on the context of this to .NET Core, you know, we're kind of leading the charge on that and getting it in place. So all the other teams can use it and benefit from it.

Personally, I've been there, it'll be about nine years, in a couple weeks. So Stack Overflow has been great the whole time. We're mostly remote company. So I'm out of North Carolina, my team is in UK and Slovenia. So we're, you know, very distributed, most of our engineers are. And the things we work on are Stack Overflow, as you know, and we also build a lot of open source [Marc Gravell](https://github.com/mgravell) and I, also my team, we do a lot of pairs on projects: [Dapper](https://github.com/StackExchange/Dapper), [Stack Exchange.Redis](https://github.com/StackExchange/StackExchange.Redis). I maintain [miniprofiler](https://github.com/MiniProfiler/dotnet), [Exceptional](https://github.com/NickCraver/StackExchange.Exceptional), [opserver](https://github.com/opserver/Opserver) some of these things. So if you've used open source and .NET, there's a decent chance you've touched something worked on. And yeah, we're just here to help make developer lives better if we can. That's something a lot of people believe in. You know,

**Jamie**

And obviously, if you've ever used Stack Overflow, then you've something that Nick has worked on.

**Nick**

Yeah, I've had hands in probably most of the features of Stack Overflow over the years in one way or another. It's just, I think every startups like that, right? People have been around a very long time, I've probably touched something one way or another. [If] it's a bug. It's probably mine.

**Jamie**

As a strange question, do you ever like see developers out in the wild using Stack Overflow and go, "Ah. I helped to make that," or do you just kind of nonchalantly walk away and just ignore them sort of thing?

**Nick**

It's neat to see out in the world, for sure. I don't see it as much as you would think just because I work from home right? You know, a lot of people have their reasons for their work. I just tell people, "someone touched my monitor once and I work from home you know," just I don't know I like it. You might trip on a cat on the computer, that's it. There's no traffic jams, there's no yelling. But because of that I don't see as much out in the world, and I'm in a little more rural area so. But when we go to company meetups or cities or traveling, you know when I'm on campus, at Microsoft or anything like that, that's fun as well to see people use it and, and get a lot of joy out of it,  yeah.

Or saving time, right? I strongly believe that time is the one thing that we all have a limited amount of. The best gift you can give someone is time. If I can make their life more efficient, their job easier, their tasks faster, that's giving them time. And you can't get that, right. Everyone's can't get any more of that. So that's why I really do believe in, you know, saving people time.

**Jamie**

That's cool. I like that.

### Migrating Stack Overflow to .NET Core

**Jamie**

So you mentioned earlier on about porting stuff to [.NET] Core. We had a really brief conversation off air about how you essentially just finished putting something together today even.

**Nick**

Yeah.

**Jamie**

That's a huge thing, like beause I remember reading through some documentation somewhere - maybe a discussion with you maybe a discussion with one of the other architects - and just the amount of stuff that goes into presumably just the Stack Exchange stuff. I mean, is Stack Exchange separate to Stack Overflow? I'm seeing one as an implementation of the other, or are they completely separate things?

**Nick**

Yeah, good question. So this is certainly confusing to people. And we've only changed the brand like three or four times now - so that really helped.

So Stack Overflow was the first Q&A site of you know, Joel and Jeff got together - [Joel Spolsky](https://www.joelonsoftware.com/), and [Jeff Atwood](https://blog.codinghorror.com/) - and they said, "Hey, we need to fill this gap," right. the original devs. And they're still around, which is a [Jared Dixon](https://twitter.com/jarrod_dixon), Jeff dogus - love those guys. They're the first two devs [of] Stack Overflow, they built this thing from the ground up.

They built Stack Overflow to answer programing questions. We didn't know what other areas would be in - so like [Super User](super user stack exchange) and [server fault](server fault on stack exchange) came along after for power users and sysadmins, right. And then [meta](https://meta.stackexchange.com) and then the rest of the network kind of grew from there. So Stack Overflow was the first site and the other ones grew beside it as siblings.

Now later, in Stack Exchange 1.0 everything was a separate site. 2.0, it's part of a network. So the Stack Exchange network to the users is usually presented as the separate domains besides Stack Overflow. They're really part of the same network, you have one account and you have a user on each site, or you might not right - you may be on some sites, not on others. But it's all one thing.

Architecturally it's one app. So it's one app pool that handles all this. So when you come into our server - any of our web servers - it's one app pool, one exe runs the whole thing, and you get the site, and database, and styles, and all based on the host header - like that which domain you're visiting. And we break it up at that point, but it's all a [multi tenant type of architecture](multi tenant architecture). So on the front end, it looks a little different, but you'll notice it's mostly just styling, and that's what it is. On the back end, it's all the same. Each site has a database or schema with it. And they share accounts and things but mostly it's a copy of the same thing. Think of it as... the parallel I draw is WordPress. You think of a WordPress site they all have the same schema: posts and yada yada in them, you're just running 100 customers. It's not different when you think about it, you know, sort of the similar kind of setup.

**Jamie**

Wow. Okay. Presumably a big chunk of that is .NET Framework stuff? Or is it myriad different technologies? Obviously, I don't want to reveal all of the secret sauce and stuff like that. But is it all .NET?

**Nick**

It's all Python. No, it is [.NET].

So we built on ASP. NET MVC beta. Before it was out. They started on the beta

**Jamie**

Oh wow!

**Nick**

So this was about 2008 timeframe, right? August 2008, I think was the launch. Someone is gonna kill me if I mess up all the dates, but or ish, right? We'll just say ish cover ourselves.

So it was .NET from the beginning. And people ask, "why .NET? Why not node? it would be faster in node, right?" That's my favorite debate because I'm just like, "Okay, why?" Like, I don't like argue, I'm just like, "show me why like, what, what data do you have, because I'd love this data." Of course, no one has the data. Because you have to go do it right. You'd have to the only way to figure that out is to go do it and run the same load and see what happens and you'd have pros and cons. Everything has pros and cons, everything has trade offs. But we went .NET for one simple reason: The people who started it - Jeff Atwood, Jeff dogus, Jared Dixon - it's what they knew. And they're most productive in it. So they use .NET, right?

That's it. That is a big factor in what a startup uses, "what do the founders know?" It's worked out great. So there's no reason to change. So we're still on .NET; we're moving to .NET Core, which we'll get into, for reasons not related to perf at all. It's just applied benefit. With .NET stuff,it's a co tenant web tier, we have some other apps running on there there beside q&a, like the jobs product - we call Talent. There's [an] insights little site, which runs the dev survey and some things, or a portal to it - essentially, run by a third party. So these kind of things are running beside in their own .NET Framework still, but it's all .NET Framework. And some of them have been ported to the .NET Core, our socket server, stack snippets - which is where when you click a thing and run JavaScript inside a page, and you can execute it, and test it for like answering questions and demoing, right, that's on a .NET Core - Stack Exchange website. The the top level domain, [stackexchange.com](https://stackexchange.com), not the q&a just the top level site, is a different app. That's ported, that's live. [api.stackexchange](https://api.stackexchange.com): by the time anyone listens to this podcast, it will be live because it will probably go next week.

So after API goes out, the last one to port is StackOverflow proper, which we call Stack Overflow, which [is] really any q&a site, that multi tenant app, right. The two things that run in our enterprise product are the multi tenant app and the API. So the API is done. But the reason we don't upgrade to like .NET [Framework] 4.8 or above is because an enterprise customer is able to run it on their own infrastructure, right. Their own servers. Now right now, that's a Windows install with .NET on it, and it's a little bit of hand holding to upgrade. So you don't want to incur that unless you need to. And there's no real big wins in newer versions of .NET. So we don't require it. We can upgrade to and run on it, but we don't target it.

What we're doing there, and one of the reasons to port [to] .NET Core is we're moving that to an appliance, which is way easier to maintain, right: we give you a VM and a license key. This is the goal, this is what we're working on, [there's] still a lot of pieces to put in place to get there. But .NET Core running on Linux, and being able to run in a container means our options to deploy in a appliance type model are really numerous. So that's one of the reasons to port to .NET Core.

**Jamie**

Sure.

**Nick**

So that's the state of things right now. And then testing is the other really big one. The things you can do with testing are kind of crazy. And I think a lot of people aren't necessarily fully aware of all the things you can do.

So for example, when we're porting the API, the API has an API result, which we need to send and make sure it serializes correctly, that it has the content length header correct for some old clients, that it compresses correctly, and handles all these permutations of things, right. So one of the things you can do is take it controller in the test project, you can inherit from a controller, you can add routes to it in the test project. So if you have a controller and it's got like protected things in it, you can inherit from it, add new routes is like test controller that inherits from your base, right? It can add routes have access that protected stuff. And you can run the Kestrel test server and hit them and return them. You can walk through a five step wizard with five posts or whatever you want to do. It's very powerful. And you can see the state from the client and the server the whole way through.

That's crazy compared to what you couldn't do in .NET MVC 5, right? It's just not really testable. So that's one of the big reasons we're moving testability is humongous. It's just it's so much better.

**Jamie**

Wow, that's amazing.

**Nick**

I love it. It's really cool. Watching some of the things coming in from the devs here like, "what?! I didn't know you could do some of these things that [Samo Prelog](https://twitter.com/m0sa) on my team has been working on .NET Core more than anybody. It's very cool to see some of the stuff as it comes through. You just like, "this is great because we're experimenting with this," and then you know as we get it in place; all the devs can hop in and add more tests.

**Jamie**

Well that's it, isn't it? You know, the reason we have unit tests is - and not to get political, but because there are some places out there that don't believe in unit tests or integration tests or end to end tests. But it's essentially, like you said, it gives you confidence that your code that you have written, does what you think it does. Less a case of "what it's supposed to do," more a case of, "it does what you think it does," because there's always going to be that disconnect of what it is supposed to do, and what you think it does may end up being completely different things.

**Nick**

Yeah.

And it's not that we didn't like testing here, we didn't have as much testing as we would like. Although I think most people don't have as much testing as they would like, even people who are fanatical about testing. If you don't, if you have 99.9% code coverage, you still want more, but it was so hard to test in MVC 5. still one of the best ways to test is [Phil Haack's simulator](https://haacked.com/archive/2007/06/19/unit-tests-web-code-without-a-web-server-using-httpsimulator.aspx/) from like 2011. Like that says a lot about how testable that framework was, it was just not built with in mind. And .NET Core ou know, when they revamped it, they learned a lot of lessons and really factored those into when they rebuilt the thing.

You know, it's some areas are painful to port from .NET to .NET Core, some areas are very easy when you go outside the box is when it gets hard, right. I think that's true with any product upgrades. And the things that are hard, it's interesting because the things we've hit the past week or two. We have some areas, for example,there's two basic string types in old and new MVC, they changed right because .NET Core is a port of the API's that largely are one to one or they poured over. ASP. NET Core, I think a lot of people that haven't gone through it, that is a rewrite. The primitives are different, HTTPContext is like completely different, request is different, right. If you're off the beaten path with those, you need to port some things.

So when you have some bits like that, that don't come over immediately, some of the things we've hit are like: So in the old world, you had something called an [HtmlString](https://docs.microsoft.com/en-us/.NET/api/system.web.htmlstring?view=netframework-4.8). It's an interface and it says, "I am going to write out some content and it's already HTML encoded. You don't need to encode it again," this is razor's signal of, "I need to write this or I need to encode it while I write it to be safe," right? This is injection attacks, this kind of stuff. [Barry Dorrans](https://twitter.com/blowdart) is a great follow there. If you want to see some crazy injection attacks from like SQL and back, some of them you're like, "what?!" Very cool stuff.

You have `IHtmlString` in the old world. In the New World, it's called an `IStackHtmlContent` right? So one of the things you can do in the old world, MVC 5, is you could call `ToHtmlString()`, and it would take the thing and it would render it out to a string, it would kind of realize it or materializer, minimalize it whatever and call it like actually made the string. Before that, it's a thing that generates a string. And that may sound the same, but they're very different, right one, say for example, I do localization. This is matters to us, we actually do our own localization. This is Samo builds. It's called [Moonspeak](https://nickcraver.com/blog/2016/05/03/stack-overflow-how-we-do-deployment-2016-edition/#step-3-finding-moonspeak-translation). If you feed it a string that says, "You have five inbox messages," simple example, right? There's three parts of that string in English. It's "you have," and then that "five" is a variable, and then "inbox messages," is pluralized. Now the plural can actually go anywhere. Don't make any assumptions based on your language. Which I found out; like languages are crazy, and Japan has no spaces, Japanese has no spaces.

**Jamie**

Yeah, I know that. I'm a Japanese speaker.

**Nick**

Okay, so it makes Elastic Search that tokenized based on space, really fun, right? We've learned that localization is interesting and sometimes painful.

So with Moonspeak, you've got those three portions. In English, the last portion is going to be "inbox message" or "messages" depending on the one or zero, so there's some pluralisation involved. But what you want to do when you right that, is you want to write the first part: you want to write the number and even write the third part. You don't need to make that string in between because that's garbage. You need to make and then collect, right? So these are things you want to avoid. So IHtmlString, that's what it does it right? When you go to realize it, it realizing it to a writer, and it's writing the three parts out, that's okay. It's an interface, you choose how you want to do it.

So the new version of that is called [IHtmlContent](https://docs.microsoft.com/en-us/.NET/api/microsoft.aspnetcore.html.ihtmlcontent). And it has a `WriteTo` method and you output it. So that's the equivalent in ASP. NET Core roughly. The other is [MvcHhtmlString](https://docs.microsoft.com/en-us/.NET/api/system.web.mvc.mvchtmlstring) in the old world, and it's [HtmlString](https://docs.microsoft.com/en-us/.NET/api/System.Web.HtmlString) in the new world. This is, "I have a string, it's built, it's already HTML encoded. Just use it, just put it in the page verbatim as it is," right? The old world, that `ToHtmlString()` that existed on the IHtmlContent, which is like, "take that, you know, nice, neat, I can write parts version and make a string out of it." That actually doesn't exist in the new world, because performance wise, it's terrible. So they removed it for perf reasons, but it actually subtly enforces good behavior on your side. You can't very easily - this is something was apparent to us, until we get into porting - we cannot very easily take an HTML encoded string and use it as a string. You don't want to, right? That should be flagged type wise the whole way through the tree that, "this is encoded." I don't want to move back and forth, that's an opportunity to trip on yourself and put an unencoded thing in the page or vice versa, or double encoded, right. So the fact that they've taken bits out of this out for performance actually really enforces good behavior. In our case, it was painful because we were doing the wrong thing. So it's like, it's an interesting artifact of the port that we didn't learn until like, 80% of the way through when we got the Stack Overflow, and this was all over the place. We were like, "man, we really shouldn't have been doing that." And it's odd, but it's very cool stuff like that, that I think are some of the neatest lessons out of the migration.

I just love it.

**Jamie**

It's interesting because I was talking with, I think, Iris Classon before about [migrating stuff from framework to Core](https://dotnetcore.show/episode-24-migrating-from-asp-net-to-asp-net-core-with-iris-classon/) and I feel like perhaps she hadn't run into these situations because she wasn't using IHtmlString and doing localization in that manner. So it's interesting to hear different people's approaches to different things; like how migrating to a new runtime with slightly different API surfaces and parts of it have been rewritten. And how all of that kind of messes different people up and forces them to work a little smarter about how you're doing things.

**Nick**

I want to stress to people that this is not the normal experience. Stack Overflow is big. It's huge. It's, you know, one of the top 50 websites, we started back in beta MVC. Some things we worked around have long since been solved in the framework, we just never changed them because they're working. And you don't change a working thing unless there's a benefit to doing so, right? You know, what works. You know, you're the state you're in, you move to an unknown, it's an unknown: you could break things.

So some of those things have been solved. Some of those things like how we do routing, and how we make routing performant in the URLs. Well, they fixed routing. They're [B-trees](https://en.wikipedia.org/wiki/B-tree) now, they're not loops in the old framework. So that's kind of stuff is just all for free, we can just remove the workaround. The way we matched routes can just be removed, it's just built in. There's a lot of those. I would say in general, the more you are kind of vanilla or in-box, like you're using controllers the way most people use controllers, you use x the way it's kind of in the docs, your upgrade is pretty quick. It's where you went off the beaten path that we've hit any kind of fun. So I think that's true of anything. Any time you customize a product and you go out of the box, that's not stuff that was necessarily considered when they were designing the next, you know.

**Jamie**

It kind of flies in the face of something that Steve McConnell said in Code Complete 2, and that was :

> Don't program around the framework program into the framework.

But the problem there is, like you say, when you come to grade or replace the framework, and the framework is your dependency in that instance. You swap out the framework and everything goes wobbly.

**Nick**

It is and I think one of the things to really differentiate here is, historically the framework ship very slowly. If you wanted to fix something, okay, like you need to fix it, it wasn't getting fixed in the framework for some time. .NET Core, we could pull it and build it today, if we needed to do a custom build to a web server, I could do it in a matter of minutes to hours. That's amazing. Before you had to work around the framework, because there was no other choice. Now we can upstream a fix and get it in a reasonable time-frame. And even if we have to do an emergency build. That's a fantastic vision to be in. The open sourcing of .NET is hugely beneficial. And it totally changes around how you think about working around a problem, right? We would much rather upstream a fix because again, the company mission is to make developers lives better, right? And well really anyone in tech we can, or anyone in general for me. So if we can upstream a fix for everybody? Yeah, that's the default. Alright, so we'll open an issue or file a thing.

Some of the things that we're really good at Stack Overflow, that we have the skill sets, right? I'm happily brag about my team is we're really good at debugging. It's one of the things that just is a very good set of skills that the team has. So if we can just file issues about, "here's what the cause is," even if you don't have a fix, right. Just filing an issue of, "here's the thing, here's the cause," that's hugely helpful. A lot of the trouble in software or really dealing between two companies at all is: finding the right person, and communicating correctly the problem. After that, fixing it is usually pretty quick. You know, that's, I mean, there's cases where it's contentious, but generally, that's most of the problem, right? And open source is lowering that barrier tremendously.

### Debugging and other Important Skills

**Jamie**

Debugging is one of the most important skills for a developer, because aside from if you're migrating like you to a new runtime, the majority of your time is going to be spent maintaining code. And like you said, existing code has infinitely more value than code which doesn't exist, because the existing code works. So keeping that code working is the most important thing. Keep it working, make sure it's still doing the thing, even if it's still doing it in a roundabout way now, and if it's incredibly badly optimized, and if it takes an hour to process the results, or whatever, it's still working. So yeah, I think you're right. I think debugging is one of the most important skills.

**Nick**

Yeah. And we try and help this out a little bit, right. When we realize this early on, there were some gaps in .NET. I think a lot of frameworks have a lot of gaps, otherwise there would be no open source ecosystem, right? We open sourced [StackExchange.Exceptional](https://github.com/NickCraver/StackExchange.Exceptional): you can log your errors to SQL, or JSON files, or Mongo, or wherever. You can, you can log all these things. That's one thing we do. [Opserver](https://github.com/opserver/Opserver)'s a way to see these errors. [MiniProfiler](https://github.com/MiniProfiler/.NET), you can put in your page and see where the slowness is. These are things that we had to build for ourselves.

So we open source[d] them, and this is all along the lines of debugging, right? "Where's my slowness? How do I see this in production?" Getting to what is slow on a page in production is way harder than it needs to be. That's where MiniProfiler aims to help. Right? That's one of the things that I maintain. How do you lower that barrier, lower the bar for users to be able to access that kind of information developers, right? Reproducing a production bug is way harder than it needs to be in a lot of places. And I think .NET Core helps that a little bit because you can run more stuff locally and things, but there's some tooling that needs to exist outside of the core framework for that kind of stuff, you know. The more that's built in the better. I mean, it's great. They're doing some event stuff that [ETW](https://docs.microsoft.com/en-us/windows/win32/etw/about-event-tracing) bits are being replaced - or not replaced, I guess there's like another path being added to .NET Core. Because ETW is Windows - that's event tracing for Windows - I don't know what it stands for. But it's all these events, right? Like "A thing happened", "garbage collection happened", "a thing was allocated," whatever events, right. These are ETW system. So when you, like [perfview](https://github.com/microsoft/perfview) that you hear people talking about; this is where you're tracing an app, and seeing what happened, and getting kind of a running debug log - it's not a snapshot. It's like a chronological log as to what happened. That only works on Windows. So they're porting that, I think it might be in 3.0, to work on Linux tend to work on stuff, right. And it's the kind of stuff that we haven't gotten to yet: when we run on Linux, we're gonna have to figure out how you do memory profiling, because some of that tooling is not there. It's matured on Windows over 20 years. So some of that stuffs got to catch up a little bit. And that's part of the adventure we haven't gotten into yet. It'd be fun.

**Jamie**

I suppose that's one of the big scary things for the majority of .NET, folks: is that primarily .NET has been a Windows technology. I know a lot of .NET developers who are Windows and Microsoft stack all the way - and there's nothing wrong with that. Myself, I run a couple of Linux boxes and Mac box and a Windows box in my house for a bunch of different reasons. But I'm a little more comfortable jumping between the operating systems. But now we're in a world where you could have a developer who is a very strong .NET developer, but doesn't know a thing about how Linux works. So that whole debugging story that you were talking about, they maybe wouldn't know where to start. Maybe perhaps they start with Stack Overflow, but they really wouldn't know where to start.

**Nick**

Yeah it's very, we live in strange times, right? We hop into different areas of, you know, performance, debugging and profiling with Windows, because that's where the tooling has matured. But there are other areas, you know, you use what's practical, I've always been a fan of, "use the tool that makes the most sense." And that doesn't mean just like, "Hey, this is good for this specific use case, use it." That's not what I'm saying. What I'm saying is, "use the tool that makes the most sense all things considered, or as many things as as reasonable consider right." For your team, what are you using? Are you using a tool that does 95% of what another tool does. One tool that's 95% good for two cases is way better than two tools that are 100% good for that and heavily overlap. You know, that racks up. Complexity has a cost. It really does.

So for the .NET we're running containers and Linux and stuff. We can link to [my blog post if you want on show notes or something](https://nickcraver.com/blog/2016/02/17/stack-overflow-the-architecture-2016-edition/). The architecture hasn't changed that much I list what OSs we're using for everything. So example we'd run:

- Elastic Search on Linux
- HA Proxy or load balancer on Linux
- Redis is on Linux
- SQL server is on Windows
- IIS on Windows
- Our service boxes, which run some out of process stuff on Windows.

That's actually a pretty cool thing to to cover. If users aren't aware, there's something called [IHostedService](https://docs.microsoft.com/en-us/dotnet/api/microsoft.extensions.hosting.ihostedservice) in ASP. NET Core, which is a very simple interface. It's just like here's a service, you fire it up. And then it gets a cancellation token basically, so when the app gets torn down, we stop the service, right. And what we can do with that is, so Stack Overflow is an interesting use case. I talked about the deployments a little bit earlier, right? Where we deploy in [enterprise](https://stackoverflow.com/enterprise), we also have [teams](https://stackoverflow.com/teams), I can talk about that if you want. But Stack Overflow for teams is a something launched last year, which is where you can have your own little private area of Stack Overflow. That actually runs in another app pool behind in a secure zone. So there's actually four ways we deploy the app:

1. Public
1. Teams
1. Enterprise
1. Enterprise self hosted

All of them are very similar but different scales, right? So for Stack Overflow, if you're dealing with 20 million questions then the tag engine, which is what [Marc Gravell](https://twitter.com/marcgravell) writes, it does bit math and crazy things that make your brain melt, or at least my brain melt, in memory to do things very, very fast and quick, right? Faster, quicker, same word.

So this is something that him and [Sam Saffron](https://twitter.com/samsaffron) built way back in the day, near when we started. That thing is something that needs to run very, very fast to find the Java tags and the C# tags, or the combinations of those, ore the combinations of those written by this person last week; all these criteria, right. We outgrew SQL for this a long time ago. That needs to run at scale on Stack Overflow in a pretty big way, and it can hammer a core when it updates or hammer a socket really, right. So we need to run it separately. Just because a) we don't need to run it nine times and keep nine versions of it - we run nine production web servers, we can still run on one or two. But we we keep nine for redundancy at like 10% CPU. When that thing is running, we don't need a lot of duplication. It's heavy. And you want it to persist across app restarts and be in memory because a decent chunk of memory: a gig and a half right now. That thing is running a separate box for Stack Overflow scale. It doesn't need to, for the other deployment scenarios, right. Teams is getting to [the] scale [which] needs that. But for enterprise, you don't need another box, you don't need another app. Again, complexity has cost, right.

So what we do with that, and our mail service. and our scheduler service; so [Dean Ward](https://twitter.com/deanward81) on my team, he writes the scheduler and some other things. That piece, it runs inside the single app pool we talked about for all those deployments. And it runs on a separate server for the Stack Overflow deployment, but it's the same code.

Okay, so if you have an `IHostedService`. It's just this thing. It's like, "hey, I'm firing you up, do what you do. And you get a config, and you get a token to run. But that's it," you just run. Where you're running doesn't really matter. So for us, I consider it like Lego blocks, right? You might have to bleep it out for trademark. So the Lego blocks are, "I can build it one way and use it in multiple ways." So when you talk about our tag server, our tag server is like a little wrapper that runs this `IHostedService` and exposes some status routes. That's all it does, right? Our scheduler, same thing, our stack mail instance, the mail sender, same thing. And in enterprise, we just run they're just NuGet packages for both right? So it's a - it's in the same project - but in the core product it's a NuGet package that either goes across HTTP - we will be gRPC later - but it goes across HTTP to hit the service and get a response back, like a JSON thing, and we share an SDK like a signature payload, right? Your JSON, your POCO definitions basically, right? Or you run it in process.

So we feed an object, and we either go across the wire or we go in local memory. And that mechanism is what we use to deploy things at scale separately on so, or completely in the box in one app pool for enterprise. So that means on Stack Overflow, we have stack mail is an app on the service tier scheduler, tag engine - these are apps and the main app pool: that's for apps total. In enterprise it's one app. It's a lot of simpler to maintain, a lot simpler to deploy, right? If you're a local dev -  most people forget this - like people design their infrastructure that I've seen, at least initially, once you run it, and your devs try to develop on, it reality hits really fast and they let you know about it. Devs really aren't, they don't keep their opinions to themselves too much, right? At least around here.

So when you're doing this locally, like okay, "we'll build a container, we'll run it in Docker to debug everything," okay? But when you're making a JavaScript change, and you got to build Docker, and run the image and fire it up, and that takes five minutes every time, you're going to hear about it really quickly. That's not very practical for a tight dev-loop, right? So I think it's very important whenever you're designing, .NET Core or anything, consider, "what does your local dev story look like?" Because that's really important to get, right. Because if that's slow, then everything else is going to suffer. So I consider the local dev story to be like the fifth deployment mode. What does that look like? And the ability to run services in the app like we do an enterprise, that's really more for local dev for me, than for enterprise. It just happens to work for both. Any time you have one thing that solves three use cases: awesome, right? That's the way you should design it. But it's something to think about and I think it doesn't get enough attention early on in the design process. What does the devs machine look like? Because honestly, they're the first ones going to try it doesn't matter what your final looks like if you don't get past step one. Anyway. So `IHostedService` definitely check it out. Yeah, very cool.

**Jamie**

I like it. Simple always trumps complex. Always.

**Nick**

Absolutely. Simplicity is just simpler to debug, simpler to reason about. I did a talk on this at a conference a couple weeks ago. Months ago? I don't, I'm getting old. Simplicity is: people like to simplify code, devs like to refactor. And when you can, some jobs don't allow it. Some jobs have too much time for it. But refactoring is always a good thing, right? You always hate the code that you wrote yesterday, or a lot of times you do. So simplifying the code is great. But a lot of times, that's like, way too late in the process. You need to be simplified when a spec comes in, and it says, "hey, we've got ABCD and E." Like, "okay, ABC and E are the same thing. D is kind of this weird thing. 10% of the effort and 90% of the win are in ABC and E, right? Let's do that and separate out D. And maybe I can ship faster." That's the basis of Agile right? And it's just simpler to reason about. If you can simplify it up-front, challenge assumptions up-front. Do it when you're writing the spec, then everything else is going to be easier. It's easier to build. It's easier to debug. It's easier to test. It's easier to even replace later, if you need to, right. Simplicity, is I wish people put more time into it, I really do. I think it would save a lot of time overall, if it was done up front more. So, of course, I only have my you know, anecdotal experience to see this. But I think it's valuable I really do.

**Jamie**

Anecdotal experience running one of the biggest services on the planet, essentially.

**Nick**

Except when it goes down. More than a couple outages here have been caused by HA [Proxy], and complexity in HA [Proxy] causing an outage which is just irony in and out, right. Always the case.

### Onboarding New Devs to Stack Overflow

**Jamie**

It's interesting that you said that you did that as part of a talk because, like anything relating to Stack Overflow is that interesting. It could be a talk in itself. Like maybe a 10,000 foot view of, "this is how we go about onboarding a new person." Because that in itself, I mean, you talk about simplicity, but how do I as a developer clone the code and get it all running on my machine?

**Nick**

Yeah. So actually, a lot of people want us to open source that. We had this problem early on. I'm not sure, I'm guessing a lot of people have had this problem at their company, right? How do you get a new dev spun up? This is like a case that [would] actually be worth doing a blog post about probably -, I've had a lot of blog posts in queue. I've got this Trello board of them, I just need to take time. I'm taking a sabbatical at some point next year, they're telling me I really need to, haven't really had one in nine years.

So the onboarding a dev is interesting here, because what do you need to set up stuff as much like production as you can, Right? And this is interesting to me, because you had told you enterprise is, "you run an app in a, like, a very simple way because it doesn't need to run a huge scale." It is much like a developer local experience, right? It's so much like that, that the script we use to set up local devs was the first version of the enterprise install script. It was the same thing was actually reused, because they were like, "wow, this is just about what we need."

So we have a PowerShell Script. This has been worked on over the years in various forms. I think Matt Sherman was a dev manager here, great guy. He worked on it for a while. I'm forgetting who all had hands in it. And then at some point, I rewrote it and PowerShell as a module. And now when you set up a dev machine for Stack Overflow, you basically connect to this git repo and download it, and then it sets up all your repos, all your tooling via [chocolatey](https://chocolatey.org/): all your Visual Studio, your SQL, your Redis, your elastic, all the app pools, all the IIS stuff, all your certificates. And you just hit enter and you let it loop through it. You can just [choose] things and like get a database, or set up a specific thing. But if you just hit enter it just goes through the list and installs everything. And it saves a lot of time in two ways. People look at it as it saves a new developer time setting up the machine. Yes, that's one way to look at it, and it's a valid way to look at it; it is a short-sighted way to look at it though. At the same time, not to insult that view, but the real win is this person is set up like everybody else. And everyone's set up the same way. And they mirror production as much as they can. And dev, right. That's the huge amount of value: we don't have 30 different ways of having something set up. Because we did that right? We were a Start Up and everyone set up their own crap, and they debugged it. And they hacked the crap out of it to get it to run. And it was a nightmare. It's like, "why doesn't this work?" "Well, because you had these site settings this way, and you had them this way." And then half your time debugging was, "we're not debugging the same thing. We had two different setups," right? How many times has every dev listening to this, done that? So eliminating that, that's the win. That's all of it. That's all the worth.

And other than some specifics of SO, like our VPN setup, and things like that, it's really probably a reusable script. I just haven't really found a way to open source it and maintain it as a fork with taking out the secrets. I just haven't had time to [do] it. But I think it's a very useful basis for somethin. But yeah, highly recommend people look at it, not as, "you're not a developer saving someone's set up time." That's not the multiplier, you need to consider the, "is it worth doing this time trade off?" It's, "how much time am I saving, debugging all this crap? Just because we don't have a common way of doing it." I didn't look at it that way either. But I'll be honest, we didn't realize those benefits until like a year later. We're not spending time on this. We're like, "oh, yeah. Cool."

**Jamie**

I like it. I do remember that, at a previous role, I wrote a [.NET Core Global Tool](https://docs.microsoft.com/en-us/dotnet/core/tools/global-tools) that was stored as a NuGet package. I would get told, "hey, someone's joining. Provision a machine and set them up." And all I did was connect it to our NuGet feed, do `dotnet tool install` and then the name of the tool, and then run it once. And what would happen was it would detect a first time run and then set up the machine with all of the tools that they would need via chocolaty, set a bunch of group policies and things like that. And subsequent runs wopuld just just literally do `choco upgrade all`, and then just upgrade everything in place.

And you're right, it is a time saving tool. I'm a little bit like how you used to be, in that it saved me time setting up someone else's machine. But then, like you say, once everyone's on the same level playing field - or whichever metaphor you choose to use - everyone is using the exact same set up, with the exact same tools, and the exact same debugging experience. Then one developer can go, "right, I'm gonna go sit at that machine because it matches mine, which is dead." Or two developers are pairing together, and they both know where all the bits of the debugging tools are, because they're in the same places on each machine.

**Nick**

Exactly. It's such an awesome thing once you have it set up, right? It's not just about the person making the tool, right. It's every dev can help every other dev, which is fantastic. I think it's such a great use of time. I think when a company reaches a certain size, like when you get over, you know, a dozen or so - I'm jut pulling this number out of thin air. You need to look at that, seriously. Even if your stuff is simple. Okay, great. That means it won't take a lot of time, because it's simple. There's not much to do. But once you do it, then it's very easy to like, "Hey, we need to add this one thing, we got a new service in prod," or you know, whatever. Okay, well then add it to the tool. It's very easy to maintain once you do it. If you do it later, the the bar is higher to do it, right. Such a great use of time.

**Jamie**

It really is, yeah. Like you said earlier on, it pays dividends in the future. When you have 150 new employees and someone new starts, all 150 people are using the exact same stuff. And you can offload some of the debugging. So let's say you bring in someone new, maybe they're not brilliant at debugging, yet. They can go sit with someone else, maybe pair on it, may be mob with it. Or maybe they're entirely remote, and they could do a screen share on it. It's all about that productivity, isn't it? It's all about, like you were saying earlier on saving time.

**Nick**

Oh, yeah. Any of the scripts or things you do to debug it is outside of the tool, you know, you can assume your paths are the same and that kind of stuff is pretty handy, too. Yeah, that's it's such a great time. It not something we talk about a whole lot. It's just something we kind of take for granted at this point. But I imagine a thousand versions of what we're talking about exist at various places. I've never seen them published much outside as something reusable, and there's probably a good opportunity for that in the space in general.

### Are There Pitfalls In Migrating To Core?

**Jamie**

So you talked about how the migration to Core is less about the perf, more about that scalability, but [that] you are getting those perf bonuses.

**Nick**

Yes.

**Jamie**

Other than the examples you gave earlier with things like the `IHttpString`, what are some of the biggest gotchas from your perspective of going, "Let's migrate everything to Core"? And what are some of those blockers? Did you start experimenting with v[ersion] 1? Did you start experimenting pre-v[ersion] 1? Did you wait for v[ersion] 2? Did you wait for 2.1? Have you waited for 3.0?

**Nick**

Oh, v1. Those where dark times. We just kind of pretend that v1 didn't exist.

So as maintainers of open source, you know, again, company mission: "helping developers, that kind of stuff." Marc Gravell and I have libraries. Other people wanted to move to .NET Core, before we had time to think about it, you know, we were trying to unblock other people moving. So you know before in .NET 1.1 - which is .NET Standard 1.x, which just pulled in the whole library, which is kind of a cluster of dependencies. I can tell you a lot about that .NET Core 1.0.

But we wanted to unblock other people. So our first dip into .NET Core was, I think you got to figure out a couple of things. One of my jobs here is to keep the dependency tree in my head about what's what. Not on the infrastructure side, but also which projects are coming, right. This is not unlike the .NET Core move. One of the first things you have to do: you can't move, you can't literally compile until your dependencies, your package references, are compatible with what you want to compile on, right? So if you're on .NET 4 to .NET 4.6.2, or .NET 4.7.whatever, and you have packages that aren't .NET Core compatible, and that's your first blocker. You are never gonna be able to compile unless you get rid of that package, or get a new version that's upgraded, or something right.

As major open source - a lot of people contribute more than we do, like I'm not minimizing that - a lot of people though, just statistically use our packages. So we are a dependency for many other people. It's just the way it's worked out. Especially for [StackExchange.Redis](https://github.com/StackExchange/StackExchange.Redis) and [Dapper](https://github.com/StackExchange/Dapper). These are very heavily used actually MiniProfiler is heavily used at this point. So those we wanted to upgrade, so that other people could upgrade their stuff to .NET Core, right. We realized that we were a blocker for a lot of people. So that was our first kind of foray into us doing that.

So project.json, right - everyone's favourite. We were porting all those; [we] actually had to port one of these a couple of weeks ago. God, what's [Jil](https://github.com/kevin-montrose/Jil) based on? So Jil is our JSON serializer. We used to make our API very fast, because there wasn't one and we had to build one. It was actually on project.json until, like two weeks ago. We just hadn't released [it]. Because it kept working! Like, .NET Core 1.0 doesn't mean it was broken. Like, it still worked. It was on .NET, Standard 1.5.

So we wanted to fix those first. So we went around and tried to upgrade as much open source as we could, and help people with some test projects. But largely unblocking other people. Right? The next step of .NET Core for us was package ref[erences]. I think you have to do this, it's better to go through this. We had packages checked into the solution, like checked into git - well Sublime, then Mercurial, than git technically. But we had packages checked into a /packages folder on the server, because restoring them was too slow. So we just put them in the repo. I'm sure some people are going to listen to this and scream, go ahead and scream it's fine. It's what we did. So we wanted to remove those and go to package ref, which is really indifferent. The transitive dependency goodness, right? Plus when a transitive dependency changes or shifts - actually .NET Core's not the reason for this, package ref works on both. But the NuGet tooling system moved to a local cache - in a C:\Users\whatever file. That kind of stuff is a good first step to hop on it on .NET Core, right? You need to get those in place. I think we removed like 3 million lines of code with all the XML-Doc and everything. It's the biggest commit I've ever pushed.

**Jamie**

But I mean, that's just changing one csproj, isn't it?

**Nick**

Fun fact, the StackOverflow csproj was 13,878 lines before we started the .NET Core port. It currently sits at 52 lines in the .NET Core version, and that's verbose.

**Jamie**

Wow!

**Nick**

Yeah, I can't wait to get rid of that damn file.

csproj having a conflict at the bottom of GitHub, like you might as well just have a user script to add it there while the build is still running, because it's gonna live there. I hate csproj conflicts. Do you know they're optimized for this? They're optimized to create three way merge conflicts. If you add a file anywhere in the project, and I add a file anywhere else in the project, they'll both appear on the same line. Like they'll both be at line 978. I don't know why, there's something in Visual Studio that always picks that exact line for the next file. I don't know what the algorithm is, it seems random, but it's not because they always pick the same file. Two people push, you will get a three way merge conflict. It's optimized for pain.

**Jamie**

It's the PDD, right? Pain driven development.

**Nick**

So we've had issues about this for years, you actually cannot sort the files in the csproj safely. Getting the semantics of C sharp, but if you have two partial files, and they have static properties, right. If you have a property that uses another property, the first one needs to be initialized before the second one to be initialized or don't it'll get null or ref or whatever, right. If they're in the wrong order, it can be bad. So the order they're included in the csproj is the order the compiler gets them. If you just alphabetize them, you may break people. This is where Microsoft cannot break people. Yeah so they actually cannot, in Visual Studio, just save it alphabetically; you would think that would eliminate a lot of pain. No, technically you can't do it because there's a breaking change. Fun or not so fun facts I guess.

So doing package ref, that's a big move, because then you can move all of your packages up to .NET Core, right? We had things like we were using an old mail library that's gone. We were using [HTML agility pack](https://html-agility-pack.net/), which is funny because HTML agility pack was [abandonware](https://en.wikipedia.org/wiki/Abandonware). And so we moved to I think something called [AngleSharp](https://github.com/AngleSharp/AngleSharp). And then in the course of porting [to] .NET Core, we were like we had two for a while we're like, "okay, when we get to Stack Overflow," the last one, we worked up your biggest project solution right? "When we get there, we will then go move everything over to AngleSharp." Well, in the meantime, someone picked up AngleSharp and ported it to .NET Core - like it got un-abandoned. We're like, "well, hell just remove AngleSharp." So we like changed courses, and turn left, and then went back, right?

But that's your first step, right: Figure out what your dependencies are. Get that out of the way. That's how we kind of dove into it. And that was two years ago, almost right? That was our open source time, that was mostly me and Marc in our spare time doing this kind of stuff. And it was back in those times, it was painful, because you had to do a lot of `#ifdef`, and the way you do reflection and these kind of things were different. So you had to write different code between .NET Standard 1, and the other frameworks. Now. .NET Standard 2.0 was way more compatible. And so a lot of those `#ifdef` - and so `#ifdef`, if you're not familiar, is you say, "if this framework, run this code, compile this code, else do this or whatever". So for anyone listening, it's as painful as it sounds, and you don't want to do that. So .NET standard, being a common API surface area is very important and that made a lot of things easier. So these days, it's not near as painful to do stuff like that we have very little `#ifdef` code. It's mostly around the ASP. NET stuff, the Core, that's a rewrite. That's where `#ifdef` code is during the move, because in the same solution, we need to support old and new as you move, right. And that has its own little set of gotchas.

We're a major public website, you can't take a maintenance window on Thursday night and move. You don't want to move everything at once: you want your releases for anything to be as small as possible, right? Marketing wants releases to be as big as possible, typically. And then for anything else. you want to be small on the engineering side, right? So we're deploying the little websites working up to SO. When we do the things like, you know, we have a common lib[rary]: you take all your common code.

So we have StackOverflow was big project monolith. Okay, so StackOverflow, the web project had all the models and everything in there, okay? It had the database models, the helpers, this kind of stuff. Well, in the other web projects and solution referenced that web project. So we know that wasn't gonna work. Because if the API referenced Stack Overflow, because it uses the same models, or your API is your same objects. So that makes sense. But we knew the API eventually was going to move to that .NET Core before Stack Overflow was, you can't have a .NET Core project reference and MVC project. I don't know what that would do. But it wouldn't be good, right? It's like, "this only builds on .NET 4.6.2," I don't know if you can convince the compiler to make it work, I'd be really interested in what would happen. So let's just assume that's a bad idea.

So all the other projects that use this kind of stuff: we have mobile, and Stack Exchange, yadda-yadda. We wanted to move the common classes out to something called `StackOverflow.Common`. So this is our first step: move all the stuff we can out into another project. The models, the Site Settings, we have a thing called `Current` which is a static access to things. We do our own sort of DI thing, based on the context, when you come in, it's a little tricky to talk about its probably better to illustrate. But move all that out, and then make it compile in both .NET 4.6.2 - because of enterprise - and .NET Core app 2.2 at the time, we've now gone to 3.0 which is a very quick upgrade from anyone curious. 2.2 to 3.0, it was very painless for us. We haven't gone to EF Core 3.0 yet, we're on 2.2 there. We just haven't taken five minutes to look at it. So the `StackOverflow.Common` has all the stuff and then at that point, you've got your web projects still are depending on SO, and SO depends on this thing, okay? The ones that don't need Stack Overflow, you kind of peel the onion, right? You move the things that are web to be dependent on not other web projects. That's step one, because we want to make something ASP. NET Core it can't depend on old ASP. NET, those are just incompatible things. So we ported all the other projects by moving, we have a StackOverflow.Common ASP. NET Project, which is dual compiled: .NET 4.6.2 and .NET Core app 3.0. Now here's where we can do things that you can't do in public, okay? Because ASP .NET Core up to 2.0 or 2.2, at some point they dropped the .NET 4.x compatibility, you have to run on .NET Core app, right?

**Jamie**

Yeah, I think that's 2.1.

**Nick**

Yeah. Okay. So in 2.1, they did that. So before that you couldn't do this trick. What we do is, .NET 4.6.2 is MVC 5, and NET Core app 2.2 or 3.0 is ASP. NET Core, right? These are two builds and the refs are one or the other when you're building, right? So when we have the common ASP .NET project, and even StackOverflow.Common, that same split is happening. So as projects move over, it's really like as they change [TFM](https://docs.microsoft.com/en-us/dotnet/standard/frameworks) they move to the new stack, but we can share as much code as possible. So you have to, peel this onion and go as you go. And then your dependencies are split out that way, that also means people aren't depending on StackOverflow so your builds get a little quicker too. Because a change in StackOverflow, which is where we do most of our work to be honest, don't affect the other projects. They don't need to rebuild, because they didn't change. If you change something in Common or something, they need to rebuild. But a lot of your, "hey, this is built MSBuild doesn't need to rerun it," plays in your favour once you start doing that stuff, right. So when we split out Stack Overflow to this thing. Now we have common, and that's what unit tests go against, right? And then your integration tests go against Stack Overflow and the other top level projects, but they're all kind of split out as a tree. Now instead of Stack Overflow being the root, it's just one of the ones on the end. And that's worked out pretty well. It's the only way to do it: kind of rolling and going. You can't Big Bang and release like this. It's a really bad idea.

**Jamie**

Some people like working until one o'clock on a Friday evening. Some people don't.

**Nick**

The next month. Yeah.

So so that kind of stuff, I think it's interesting what you can do to port a thing, is one set of stuff.  Like [Winter Bash](https://winterba.sh/about/): we could actually go through and port the whole thing, and then just launch it because Winter Bash is hat system. It's a fun festive thing at the end of the year, you can go and do things on Stack Overflow, or the rest of the network, and get hats and wear them and show them off. If you don't like hats, you can click the "I hate hats" button.

So that's the one we just finished porting this week, we started Monday morning, and it took us you know, three and a half days or so. We just went through and ports everything to .NET Core. And that wasn't live. So it was really easy to do. You do something like Stack Overflow or something that's always on, and a lot of devs work on always on systems. That trick gets a lot harder to pull off, right? You need to make this thing run the whole time. You need to test your .NET Core as much as you can, and then probably launch a canary and then pull it down, right?

So here's an example of one thing we ran into this a couple weeks ago. In ASP. NET MVC five, this is not done .NET Core, there is a feature of `HtppCookie` where you can give it a name value collection, have you ever seen this? You can give it key-values on a cookie. That doesn't exist in .NET Core. It doesn't exist in the HTTP spec, either. It's just something they cooked up a long time ago. And then they went, "well, that's not standard. Let's drop it." Well, okay, our authentication cookies use this. So we can't just drop it, we need it to do things. So there's two things we had to do there, which is: read the raw cookie value, because it's by default HTML decoded, and that's bad when you're trying to then decode it right, and sometimes you need to pass it to a backend service or things like this. So that's a feature we had to to port and keep up. You can't just like say, "okay, we'll use pipe delimited now." The world doesn't work like that, because everyone will be logged out immediately, right. Or when you test a canary web server amongst nine others. Or for us, in general, any rolling build is a server at a time. The code from one build to the next has to be a build compatible in either direction, right? Or one ninth of your people get logged out. And then two ninths, or some weird stuff starts happening and you're like, "oh, God, I hate life," Right? This is the kind of stuff you you need to maintain compatibility on some of the things like that: that are user facing, like the cookies, and things like that. And that's where some of your trouble runs into, right? If you could just shut it down and boot up again, and you could read one cookie, and output the other one, that'd be fine. But if you do in a rolling manner, it actually gets a lot harder. And I think that's sometimes not necessarily understood by everybody. Which is fine. You know, once you get through it once you're like, "oh, yeah, that's why."

**Jamie**

It's like we were saying earlier on, you have to go through that pain driven development. You have to go through that pain cycle to get an idea of where those pain points are.

**Nick**

Yeah.

**Jamie**

So then with a big system like this, you can I don't really want to, do you?

**Nick**

Well any system, right? I mean, your life should be easier.

Some devs are happy to take advice and say, "okay, I won't do that," but and not fully understand why that's not ideal either, right? You really want to understand why; you want to understand one level deeper. And some devs wanna, you know, go through and see the failure for themselves, and then that's the way they learn, and either one's valid, right? People learn [in] different ways. Generally, at scale, we try and keep the latter one less.

You know, I feel responsible when our site is down, because that's, you know, 5-6000 requests per second, that are failing. That's a lot of people that are just trying to go about their day, and get an answer, [to] save time, and costing them time. And a lot of people, they're in a hurry to fix something. And a lot of developers are on tight deadlines, way tighter than it should be. And they're stressed because like, "oh god, what am I going to do? My resource is down, my dependency has broken down." No one likes their dependencies to be broken.

**Jamie**

I would love to know what the percentage of that 6000 requests are people checking because someone has said on Twitter that Stack Overflow is down, versus the percentage of people who are actually making requests to find an answer to their actual question.

**Nick**

So it does spike a little bit when it happens. What's funny to me is that the best alert system we have that the website is experiencing problems is tweets per second. People think I'm joking. I'm like, "no, I'm really not. It's really that." Because we have, on our side, we've got alarms for many things. And we're always, you know, improving that. But the Stack Overflow is very, very fast. It's something like, I'm personally proud of, because I've spent a lot of time on it. So yeah, we're proud of it. Because we care. We're passionate about performance. Performance is a feature. This has been baked into the culture for a decade. The average question page is 18 to 20 milliseconds in rendering, in and out the door. This allows us to run on few servers because we don't have a lot of contention, because each request is in and out very, very quickly. right. That's how we do it.

So when StackOverflow starts to go slow, before it goes down, we start getting tweets. So before the errors come in and the timeouts start triggering, the people's timeout of, "two seconds?! This is too slow. I'm going to tweet," right? That actually goes off before our alarms from timeouts. It's really interesting to me because you don't want to have a timeout or error system that ways up and [SRE](https://en.wikipedia.org/wiki/Site_Reliability_Engineering) or something to be twitchy, right. You don't wake people up the middle the night for a false alarm, that's really not a good idea. It makes people angry, and tired, and bloodshot in their eyes, and want to hurt you a little bit.

So you can't do that. But it's okay for the alarm to be 30 seconds, it's gonna make a big difference. But on Twitter, yeah, people are not that patient. And it goes off and it's awesome. I think it's hilarious that that happens. And I appreciate it. People ping me personally, people ping [Stack status](https://twitter.com/stackstatus) and other things. Very cool. I love Twitter, because there's a lot of good and bad on every platform. But in terms of connecting to the right person and like going, "hey, do you know x?" Like, "no, but I know x, and they know x," and you get connected the right person in five minutes. Where else does that happen? That's such a cool attribute of platform, is because it's so quickly relayable.

But yeah, tweets per second. We definitely appreciate people tweeting when we're down. And honestly, if you're in an outage, and everyone's working on it, and we do here, it's a very cool thing to see. It's not something we publicize a lot, but when an outage happens, someone says, "we're down," a Hangout happens - Google meet now because they killed Hangouts, jerks - and everyone hops in. And you'll get like, 10 to 20 people in a Hangout very quickly working the problem all working together, and it's very cool to see every time. And the people who don't have anything to do because you know, you got three hands in this already, someone is checking the tweets and looking for funny ones, and they get posted in our chats, and it's a good little motivator. There's always some gems every time.

**Jamie**

I have been asked by friend of mine to see whether any of the folks on your team may have any of those [silly Jon Skeet quotes and memes](https://meta.stackexchange.com/questions/9134/jon-skeet-facts). Do you have any of those? Or is that just something that you have no intention to being part of because it's, you know, silly and purile?

**Nick**

You have to link me to this. I haven't seen the Jon Skeet [mems]. jon Skeet is awesome. I haven't actually talked to him but a time or two, just because we're in very different time zones and ecosystems. But like, he's a Microsoft MVP as well. I am currently, but he's not at the summit every year. I'd love to meet him. But he works for Google, I think there's some legal thing there. But very, very cool individual and honestly, he's done talks at out office and everything. The great great, great, great, great human.

And people are like, "oh StackOverflow made Jon Skeet, you know, famous for answering questions." And I'm like, "no it didn't. He was doing this long before we were doing it." If you go back and just search Jon Skeet, and go back further on Google, he was helping people on message boards and forums and all these places. I didn't know this when I started, like I looked back. And you know, me and him were top users on SO before I was hired. I was in a job that was ISO 9001 . If anyone's not familiar with that, it's red tape, a lot of it to do any changes, everything is validated. And so you have a lot of spare time as a developer, because you can't fix or refactor anything without a whole bunch of BS happening. So Jon's and I were like the top users on the site for about a year there. I was watching some of the stuff he does and it's very, very cool.

I have a blog post queued about this, not him. But the things he breaks in the site. I really need to write this up. Not his fault, but because he is so prolific in his activity. There are things that he fundamentally breaks on Stack Overflow. Like for example, too much rep overflows the box. That's a simple one, right? That's kind of obvious, too many badges. It makes the layout wonky, right? He's broken the layout every single time, we've had to fix it because of him - like add a little more space, maybe a little smaller, whatever it's because of Skeet. So other things he breaks that are on his apparent: So I was our SQL DBA for years and years, [Taryn Pratt](https://twitter.com/tarynpivots) does it now, she's awesome. We have a dedicated DBA, and it's more than a full time job. [We] didn't realize, till we had somebody else doing it. They're like, "look at all this stuff to do." I'm like, wow, there really was.

When you have a SQL query, and you say, "hey, give me all the answers by this person," or "ones this week by this person," this kind of stuff, right? It does a query plan. And it says, "hey, go find .. filter by this criteria, and then this criteria, and then this criteria," or whatever combination of things. And it makes a plan and it goes about it that way, right? The way you would approach thing for a Skeet versus a user with two questions is very different. So when a new user comes in, and they get the query plan, because they're the first one to run it and it kind of makes assumptions based on the parameter was given. That query may make Jon Skeet's profile go boom because it will just timeout.It's a terrible way to fetch his information, because his volume is so different. It can just play havoc on the system. And vice versa happens: if someone goes and visits Jon Skeet's profile, and it says, "Hey, here's the best way to get this information, the most efficient," it may be extremely expensive for other people. And in a lot of apps, this wouldn't matter. But when you're running that query that is suboptimal for the 99% case now, and you're running it hundreds or thousands of times, it hurts bad.

So yeah, there are subtle things in the system that just break. If you want to say, "I want to cache a list of posts by this person." Okay maybe he breaks that, and like the parameter list in SQL, or the Redis Cache size, or assumptions about the pipeline. would you just have this entity of any sort, in this case a user that is so out of the norm, compared to you know, Stack Overflow which is a long tail of participation? Yeah, oh my god, it could just cause so many things to go wrong. I've got a mental list going but people have asked for this blog pos. This is one of the highly rated ones that people are asking for. It's curious to me, so some of these things you just wouldn't think about but it's really like, "yep yep he broke it just him being here broke it he didn't personally do anything but it's totally his fault." Jon's great, I love all the initiatives he does and public stuff he does he does a lot of outside of programming, too. He's a great guy.

**Jamie**  
Oh, he really is. Absolutely I completely agree with you.

I've kept you talking for an hour and 30 minutes. So I feel like it's only fair to let you get back on with your day. Because otherwise, I'll end up keeping you talking all day and you'll get into so much trouble not doing any work.

**Nick**

Go go play with some hats. Winner bash is about up, they got a few bugs filed, we'll fix those up. But I appreciate it. I['ve] listened to several, getting into the episodes now. Very cool. I'm learning some stuff about .NET Core. I didn't know from this. Thank you.

**Jamie**

Thank you ever so much. That legitimately means a lot to me. Somebody asked me the other day, "why do I do this show?" And it's partially because I'm an auditory learner. So I want to learn loads of stuff. So it's all about me, you know, that first part. But the more important part is getting all of this information. Like all the stuff you said there about, running things at scale, replacing things piecemeal whilst is running at scale, and just the fact that you have a user who, when people do certain things with that user data it can cause site instability. All of this stuff that no one, unless they're running a service as big as Stack Overflow or potentially bigger, will ever have to deal with, right.

**Nick**

Yeah. Some of that stuff is very specific to large systems, right. And people look at Stack Overflow, in some ways is like, "oh, we have to run things at scale. It must be harder. It must be a better way to run things in some ways and not others." We're very efficient, right? We pipe a lot of stuff through hardware. And people think that to mean it's a very, very good thing and all aspects, it's not. Everything's a trade off, every single thing you do. Me being here is a opportunity/trade off with something else, right? You doing this piece of software is something else you couldn't build? Or are you buying it versus [building it]? Like everything's a trade off, right? Every single thing, including in software: how you build a system.

We're looking at right now is, one of the questions we get is, "why doesn't Stack Overflow, you know, run in the cloud?" Well, there's answers about cost and latency and things like this. And one of the things we do is we have very, very low latency to the database and back - like point 0.17 milliseconds. That works very well when it's low. And we can render a web page very fast and get out of the door. When that stops being true, stuff falls over like really quickly. It falls over, something starts going slow in our system, like SQL backs up because a non-yeilding scheduler or something - because that's happened lately. But everything hits the fan, and you fall over. Wo while we are very efficient, and it runs great at scale. It's based on certain assumptions or truisms about the environment in which we run in. Once those things stop being true - so we're very efficient, and we can run on one or two web servers fine.

You think of a highway, is the way I explained it to people, because anything to do with traffic or pipes is like a highway, right? They have four lanes, you run all these cars at 80 miles an hour - or how ever many kilometers per hour, for any one listening - and you can get this many from A to B in that known time period right? Now make them all go four times slower. You need four times as many lanes or there's gaps between the cars, maybe it's not four times as many maybe it's twice as many, right. To get the same number of people across the thing. Same thing is true in any system. You need more threads, or thread pool, or connections, or sockets, or whatever contention bottlenecks you've got. You got this whole pipe going, right. If somebody comes in on HTTP, they hit your CDN, they hit your load balancer, they hit your back end web server, and you're queuing to get in the process, and the process has to run things, and you got a thread pool, and you're hitting SQL, and you got connection pool, all these. It's a big road systems, the way to think of it right? Works great when the cars are flying at 1000 miles an hour. When they start going 20 stuff falls over, and you got a mad traffic jam, and people are going off the road, and calling angry, and people are yelling at their stereo, right? That kind of stuff happens. And so people who run app with small things don't experience that, people who run the cloud with 1000 servers, much bigger than us, also don't experience that. It's this weird confluence of things. It's totally situational. So some of the things that we have problems with other people don't even get bigger scales, because they run in a different way. I find some of that stuff curious. It's not something you really necessarily think about everywhere, but it's it's neat to me at least.

**Jamie**

Trust me Nick, it's neat to me to. Thank you for taking the time out because it's been incredibly interesting to me and really educational. And then I've got to go edit this, so I learned even more, and then I even listen to on the day the richer up so how can I say listening to this conversation, three times at least. And I still probably one taking any more than 25 to 30% of it because there is so much stuff to learn from this one conversation. It's been absolutely amazing, Nick.

**Nick**

I appreciate it. Thanks for having me. And now I look forward to more of these because I'm learning from each one. So it's great. Alright, thanks, Jamie.

### Wrapping Up

That was my interview with Nick Craver of Stack Overflow.  auBe sure to check out the show notes for a bunch of links to some of the stuff that we covered, and a full, searchable transcription the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show), and there will be a link directly to them in your podcatcher. I would genuinely recommend giving this episode multiple listens. I listened to it several times, and each time through there's something new for me to learn.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Nick Craver on twitter](https://twitter.com/Nick_Craver)
- [/Users on Stack Overflow](https://stackoverflow.com/users)
- [My interview with Jon Skeet](https://dotnetcore.show/episode-40-noda-time-with-jon-skeet)
- [KISS](https://en.wikipedia.org/wiki/KISS_principle)
- [Marc Gravell](https://github.com/mgravell)
- [Dapper](https://github.com/StackExchange/Dapper)
- [Stack Exchange.Redis](https://github.com/StackExchange/StackExchange.Redis)
- [miniprofiler](https://github.com/MiniProfiler/dotnet)
- [StackExchange.Exceptional](https://github.com/NickCraver/StackExchange.Exceptional)
- [opserver](https://github.com/opserver/Opserver)
- [Joel Spolsky](https://www.joelonsoftware.com/)
- [Jeff Atwood](https://blog.codinghorror.com/)
- [Jared Dixon](https://twitter.com/jarrod_dixon)
- [Stack Exchange Meta](https://meta.stackexchange.com)
- [stackexchange.com](https://stackexchange.com)
- [api.stackexchange](https://api.stackexchange.com)
- [Samo Prelog](https://twitter.com/m0sa)]
- [Phil Haack's simulator](https://haacked.com/archive/2007/06/19/unit-tests-web-code-without-a-web-server-using-httpsimulator.aspx/)
- [HtmlString](https://docs.microsoft.com/en-us/.NET/api/system.web.htmlstring?view=netframework-4.8)
- [Barry Dorrans](https://twitter.com/blowdart)
- [Moonspeak](https://nickcraver.com/blog/2016/05/03/stack-overflow-how-we-do-deployment-2016-edition/#step-3-finding-moonspeak-translation).
- [IHtmlContent](https://docs.microsoft.com/en-us/.NET/api/microsoft.aspnetcore.html.ihtmlcontent)
- [MvcHhtmlString](https://docs.microsoft.com/en-us/.NET/api/system.web.mvc.mvchtmlstring)
- [HtmlString](https://docs.microsoft.com/en-us/.NET/api/System.Web.HtmlString)
- [My interview with Iris Classon](https://dotnetcore.show/episode-24-migrating-from-asp-net-to-asp-net-core-with-iris-classon/)
- [B-trees](https://en.wikipedia.org/wiki/B-tree)
- [ETW](https://docs.microsoft.com/en-us/windows/win32/etw/about-event-tracing)
- [perfview](https://github.com/microsoft/perfview)
- [Stack Overflow Architecture 2016 Edition](https://nickcraver.com/blog/2016/02/17/stack-overflow-the-architecture-2016-edition/)
- [IHostedService](https://docs.microsoft.com/en-us/dotnet/api/microsoft.extensions.hosting.ihostedservice)
- [Stack Overflow Enterprise](https://stackoverflow.com/enterprise)
- [Teams](https://stackoverflow.com/teams)
- [Marc Gravell](https://twitter.com/marcgravell)
- [Sam Saffron](https://twitter.com/samsaffron)
- [Dean Ward](https://twitter.com/deanward81)
- [Chocolatey](https://chocolatey.org/)
- [.NET Core Global Tool](https://docs.microsoft.com/en-us/dotnet/core/tools/global-tools)
- [Jil](https://github.com/kevin-montrose/Jil)
- [HTML agility pack](https://html-agility-pack.net/)
- [abandonware](https://en.wikipedia.org/wiki/Abandonware)
- [AngleSharp](https://github.com/AngleSharp/AngleSharp)
- [Target Framework Monikor](https://docs.microsoft.com/en-us/dotnet/standard/frameworks)
- [Winter Bash](https://winterba.sh/about/)
- [SRE](https://en.wikipedia.org/wiki/Site_Reliability_Engineering)
- [Stack status](https://twitter.com/stackstatus)
- [Jon Skeet quotes and memes](https://meta.stackexchange.com/questions/9134/jon-skeet-facts)
- [Taryn Pratt](https://twitter.com/tarynpivots)
