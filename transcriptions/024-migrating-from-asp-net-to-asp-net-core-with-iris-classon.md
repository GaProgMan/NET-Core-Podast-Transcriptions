# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is episode 24: Migrating from ASP.NET to ASP.NET Core with Iris Classon. In this episode I talk with Iris about the strategies that she has used to successfully migrate ASP NET Framework applications over to ASP NET Core, which she has written about in her upcoming book: "Migrating ASP.NET Microservices to ASP.NET Core: By Example" . Some of you may know Iris Classon from [her website](http://irisclasson.com/), her previous books, [her work in the community as an MVP](https://mvp.microsoft.com/en-us/PublicProfile/5000086?fullName=Iris%20Classon), [her place on The .NET Foundation board](https://dotnetfoundation.org/blog/2019/03/28/net-foundation-board-of-directors-election-results), or her [Not So Stupid Questions videos](https://www.youtube.com/playlist?list=PLh0LZUZnuiJZTk8I8-9_SZbOBB98lWYy0),

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Iris' Introduction

**Jamie**
So the first thing I wanna say Iris, thank you ever so much for being on the podcast. Everyone's living busy lives, but obviously with a tiny baby as well. I can't even imagine how much more busy your life has become.

**Iris**
Definitely, things have changed a little bit. Yeah.

**Jamie**
I can't even imagine being a professional developer this stage of my life, if I were in your shoes, and having a little one that's staying up and crying and screaming, and I hope you don't mind me saying but I've seen that on Twitter and things you've been posting that, "I have gone to this meet up with the little one and we're doing this activity." And I'm like, I couldn't do that.

**Iris**
Yeah, he's keeping me busy. I'm trying to keep him busy. I'm lucky because he really likes it when it's there's a change in scenery. So if there's a lot of noise and yeah, noise sounds and lights and patterns and things, I mean, obviously he can't make out faces yet, he's only ten weeks old. So it was a very nice trick to take him different places because he'd be very excited and happy about it and then completely wiped out when I come back home. So we got me into sleeping during the night quite early on. And I think probably the meetups bored him to sleep.

**Jamie**
I think maybe that's where I went wrong, then. I think if I ever have another one, have to take them along to meetups.

**Iris**
When I try to get him to sleep, I'll walk around in the apartment and I go like "SQL Server 2001; SQL Server 2001;" you know. And then I go like, XML, XML, even more XML. XAML. Extended Markup Language," you know and it will actually work, he will fall asleep. It might be just my voice, but I like to think it's the words I'm saying of helps him sleep.

**Jamie**
He'll end of every up being the smartest programmer ever, obviously. Being taught all these things from day one.

**Iris**
Oh, he'll hate it?

**Jamie**
So for the small number of people who listen to this show who may not know very much about you, I was wondering, could you give us a brief introduction, about sort of who you are and the kind of work that you do and all that kind of stuff.

**Iris**
Yeah, sure. God, I never know where to start with these introductions.

My name's Iris Classon. I live in Sweden, but I pretty much lived all over the world. I have a background in dietetics and personal training - for those who think that's a real job: I used to - and I did a career change later in life in and decided that I wanted to learn programming. So I am now a programmer, and I work for a start up in Gothenburg. Definitely a back-end programmer, I do a lot of DevOps stuff and Cloud Architecting, I could call it. And I'm an MVP, and I'm very active in the community, very engaged. And I can definitely talk about myself for a long time, but I only do it because I'm nervous, so I'm gonna let you have some questions instead.

**Jamie**
Okay, that's fair enough, obviously doing a little bit of looking around and looking into the things that you've done as preparation for the podcast, I found that you do a series of "not so stupid question" videos. And I was wondering could you tell us a little bit about those and how that came to be?

**Iris**
Oh, yes. Oh the stupid questions, yes. They used to be called just "stupid question of the day," but then people didn't understand the irony. Because I didn't mean they were stupid.

It all started when I was learning programming. I asked my teacher if he knew somebody I could do like an internship with, and just sit with the  programmers there one day a week and just, you know, stare, learn, ask questions. And the first guy he paired me with was a little bit of ah, jackass and, he wasn't very nice. And he used to make fun of my so called "stupid questions". And I didn't think they were stupid because I was learning things, you know? So I started that blog post series back in 2011, I believe, when he started calling my questions stupid; and turns out they weren't that stupid after all. And so yeah, right back at you, he doesn't even know about the questions, obviously

**Jamie**
that's great. I mean, one of the things is that we should all try to remember is that there are no stupid questions.

**Iris**
we'd like to say there are no stupid questions, but if you look a Stack Overflow they have quite a [long wiki on how to ask questions](https://stackoverflow.com/help/how-to-ask). So we said there are no stupid questions, but we seem to have a lot of rules in regards to how to ask a question. And it's not so easy for some people, particularly if English is not their main language and they want to ask on Stack Overflow. Some people like to associate that if your English is not perfect, then it reflects your intelligence, although you speak multiple languages. So there are a lot of people who do think that there are stupid questions, but I try to ignore them, and I hope people learn to ignore them, and also learn to ask better questions. But at the same time, rather ask a so called stupid question that not asking at all.

**Jamie**
Definitely. I hate when I'm sitting in a meeting and I could see everyone just sort of nodding their heads. I'll go, "OK, I'll be the idiot and ask the stupid question. What is this thing you're talking about? Could you just fill in the gaps a little bit?" Because, like you say, it's sometimes better to ask the question that just sit there and just nod, "Yes, I think I know what they're talking about," and get it completely wrong.

**Iris**
Yeah. Don't you feel like sometimes it feels like a lot of people, or some people, seem to know everything? Another place [where] I did an internship and I ended up getting a job, a .NET mentor, really awesome company. And they had another intern, and he was like, one year junior to me - if that's how  you say it - and whenever we went through things, he would just go, "Yeah, yeah," you know, And I was, "like holy [bleep]! He understands absolutely everything. I am so stupid."

And then later on, we're having lunch, I asked him, "did you get all that?" and he's like, "No, I have no idea." And then I just realised he was just umm and arring because he didn't know what to do. And he didn't, he didn't want to say that he didn't understand it, but I honestly thought he got everything. I was feeling so stupid.

**Jamie**
How do I put it? As we're recording this, there was a [recent .NET Rocks! episode](https://www.dotnetrocks.com/?show=1621) where their guest was talking about how to educate developers, and how to teach developers new tricks. And the guest that they had on said that we should all embrace stupidity, because we're all stupid at some point, and there's no way that we can know everything. We should embrace that idea of this mystery, and ask the questions regardless of how we worry that will come across. Because there will be a time when, no matter how many years of experience you have, there'll be something that you don't know. I mean, it goes back to, there's a blog Post by Scott Hanselman called [How do you know all this crap?](https://www.hanselman.com/blog/HowDoYouEvenKnowThisCrap.aspx)

**Iris**
Haha.

**Jamie**
He was talking about how he was sitting with some engineers and they were saying, "Oh, yes, we need to draw," it was for a Web app, "we need to draw a circle with an x in it for the cancel button. So let's pull down the whole of font awesome. And let's pull down all of these javascript libraries so we could draw this x in a circle."

And he said, "No, no, no. There must be a Unicode character to do this," and they where astounded. And they asked him, "How do you know all this crap?" And he said, "Well, it's just experience, isn't it? You know, you learn these things as you go along." It's not that he sat there and read the entirety of all of the characters of available and unicode. He's just gone, "there must be a character for it. Why don't we have a look there first? Rather than pulling down several hundred kilobytes of dependencies, we can use this one byte character."

**Iris**
The amount of information out there, in particular as a programmer, is overwhelming.

I went back to the school where I started and I did a lecture on how to stay up to date as a developer and so on. And one of the questions I got is how much time do you spend just to stay up to date? I'm the wrong person to ask, because I am a little bit of a fanatic when it comes to programming, and I spend way too much time trying to stay up to date. But I decided to ask on Twitter how much time people spend, besides work, just to stay up to date, to stay current.

It was like 7% said they didn't spend any time, they got everything done at work and then they went home and we're happy. And then I think about 40% said up to four hours, and then another 38% percent said up to 10 hours. And there was, like, 16% 15% that said they spent more than 10 hours a week just to stay up to date. And I'm just makes me wonder do that in other professions, or is it just programming? No wonder people feel stupid if they don't spend that much time if some people do it. So I don't even know where the responsibility lies. Is it the work place that helps you stay up to date? Are you supposed to invest so much time? Are you stupid if you don't? How do you accumulate all this information? Because you're never gonna catch up with everything that's out there.

**Jamie**
But my personal feeling is that like you should if you have the chance. Not everyone has the time to spend hours and hours keeping up to date. But then you could have maybe two or three people who you work with who will do that, and then disseminate the information. Because there's nothing wrong with being a 9-5 developer: Someone who turns up at nine works until it's time to go home, and that doesn't do anything in development at all.

I've known, people who are full time developers, and then in their own time, they're working a chefs - they're doing cooking for other people because it brings them joy. And I'm like, "Oh, yeah, that's fine. Do what makes you happy," you know. Because at the end of the day, you've got to look after yourself.

**Iris**
I had a colleague like that, Tobias. He was There is really good developer, like one of the best developers I've worked with. And at five PM, he closes the lid on his laptop and he goes home. Unless the build server or the production machines are literally on fire - they're virtual, so I guess that's not gonna happen unless there's an actual fire - he probably would not open his laptop again, and I have tremendous respect for that. He's got such a good balance, and sometimes I wish more of my colleagues had that because I've had several colleagues burn out and can take years to recover.

**Jamie**
It really can really can. I was speaking to someone on a local meet up only a few weeks back and he said, "I'm done with doing conferences I.'ve done with doing talking because for the last year, I believe, I was doing a different conference or different meet up for a different talk almost every week," and he's saying to me, "I've got to fly out to Europe in in two weeks and I just can't because I'm so tired. But I've already made plans to meet other people while I'm there," and it is tiring to constantly be on the move. You've got to find the time to relax.

**Iris**
I do feel like there's a pressure that you have to spend your own time to stay current. You know, the complexity of software, increasing more frameworks, you know, every single day. There's like a [static site that says "days since last Java script framework," and it says zero](https://dayssincelastjavascriptframework.com/). I checked the markup is just zero, you know, because just it's gonna assume there's always gonna be new frameworks. There's a lot of pressure and if you additionally have the pressure of feeling stupid for asking questions that's a problem.

**Jamie**
I feel as though Sometimes, though, that's more of a environment thing, maybe a company culture thing. And, like I say, we should all embrace the stupid anyway. You know, it's better to ask a question that may seem stupid and get a definite answer or get somewhere where you can go, "Oh right, okay, so I need to be Google/Binging for this particular topic to learn more about this angle". It's better to do that than to sort of fumble through. And then I realise it's been two hours and you've got nowhere.

**Iris**
Yeah, I completely agree.

### Non-Computer Science Backgrounds

**Jamie**
Related to that - and I didn't even realise it would be related to that when I was planning the questions - but related to that, we've seen a lot of folks in the technology space coming from, I don't really want to say like this but, non traditional backgrounds. By that I mean people who haven't had a computer science or software engineering background; haven't gone to boot camps haven't gone to college or University and studied those things. They've maybe decided, "I don't want to be an investment banker now. I'm going to learn how to do development in my own time and transition over." And from what I understand, obviously you mentioned earlier on you came from a sort of dietician/clinical dietitian background and moved into development. But you didn't just move into it, you seem to have moved into it and gone from zero to 100%, and done more than some folks can achieve in multiple years, in a single year. Could you tell us a little bit about that? I know that there's a lot of stress involved with, "I have to learn all the things," and especially if you're sitting with people and their making, you feel stupid. You know that's not good.

**Iris**
Where do I begin?

This could be a very long story or a shorter one. The short answer is: I was so excited when I found programming because it was just so right for me. And after years and years of feeling out of place, and feeling like I didn't belong anywhere, I just hadn't found my community. I suddenly came across something that I was extremely passionate about, and I was sharing this passion with other people that were equally passionate about programming, and it's just like I had been homeless my whole life and finally got myself a home. So I wanted to move in.

I mean, I brought all my boxes. I bought [bleep] loads of furniture, I assembled more Ikea furniture, than any other person. I was so excited. I just wanted to inhale everything at once. It maybe sounds a little bit weird. I do have ADHD, that probably helped a little bit because I could certainly hyper focus on something, and I did in the beginning. But mostly it was finally feeling at home and being able to release all this energy I had inside of me, just ready to embrace something that I was really passionate about ,where people also gave back appreciation for, you know, having another a community member that was passionate. It was really life changing for me, and it still is. I'm incredibly happy to be a programmer.

**Jamie**
Fantastic. All I can say is it's great to have another person in the team. Like you say, we're a huge community and, you know, we all want to help each other out. We all want to achieve the same goals. The more the merrier, that's how I see it.

**Iris**
I do like that a lot of people have different backgrounds. I mean, we live so long now, you have time for several careers if you wanted. Just the word "career" is sort of loaded because he sounds like you have to be like a go getter with sharp elbows.

But I mean we live for a long time. Gone are the days where you got the golden watch because you worked in the same place for 50 years. Now people look at you like you're weird if you're working in the same place, doing the same thing for 50 years. We have a lot of time to try different things, and as our personality evolves, you can sort of try new things and evolve with that. And I think that's bloody awesome.

**Jamie**
Yeah. I was talking to someone the other day, and they said that they'd spent ten years at a company, and I said, "How have you survived?" I suppose for some of the really big companies like the Microsoft and the Googles, you can expect people to stick around for a very long time. But with it being so easy to start a company and get a product out there we've become, I think, more of a startup culture, which is a good thing and a bad thing. But it also means that, like you say, it's so much easier to work for someone for a year or two years and then move on because you're not tied down anymore.

**Iris**
I think that's a good thing. You wanna have a little bit off freshness, and I think in larger companies you can try on different roles, different teams, different products. But in the smaller companies, I think it helps getting in a new person. I'm just worried that the team will sort of become a little bit too stale if it's the same people, doing the same things, for a long, long, long time.

**Jamie**
No, I totally agree. Totally. It's too easy. Havel into the trap of, "Well, we'll use this particular architecture, with this technology to solve this problem," and then the customer comes to you with something that would not necessarily would require a different technology stack, but it may run better, or maybe easier to develop, may yield better results to do it in a different technology stack. And when your employees go, "Yes, we'll use the same architecture, the same technology stack in the same process."

**Iris**
Yeah, it's like, "Hey, we've got a toolbox and it conceals like a bunch of hammers."

**Jamie**
Yeah, right.

**Iris**
It's like, a team is a family or close friends. I mean, you spend probably more time than you spend with your family, unfortunately. And I think like you sort of become synchronised, and you become more more similar - unless, you know, you have a lot of conflict, obviously. But I've felt this before. I think as the team you start, sort of, adapting to each other so much that it's very difficult to get new ideas out, and at some point to sort of just give up and give in, and you just reach for the same tool. It's time just to get [bleep] done. And with you know, the overwhelming amount of information out there, you just cannot be bothered taking aboard another framework or, God forbid, do another migration.

**Jamie**
Definitely. I was talking to someone about JavaScript frameworks, and we were talking about Angular, and React, and Ember, and Vue, and all of these things. And I said, "But what you've done with your react is you've mixed all of this HTML and CSS into JavaScript. So when you want to migrate to a different framework, it's not gonna be easy at all. You're gonna have to rebuild the entirety of your UI, rather than just swap a library and change a few things, it's going to be a complete rewrite."

**Iris**
Yeah.

**Jamie**
Migration is hard.

Talking about migrations then, we've connected a few days ago, and you've talked to me about you have a new book coming out that is all about migrating ASP.NET services to ASP.NET Core, and that should be out sometime soon after this episode goes out. And I was just wondering, could we maybe talk about about that book, if that's okay?

**Iris**
Absolutely. It's been very interesting writing this book. In particular, when we started writing this book while we're on an early version of ASP.NET Core - like project.json file early version. And then a few tiny changes come out, and I've done this before. The first book I co-authored we wrote Windows Store Apps - they were called Windows Store Apps back then. And you know, we were pretty much done, and then Windows 8.1 came out with their "minor update" to the Store Apps, and we had to rewrite basically the whole book. So I'm just having like, a déjà vu writing this book now. It's just writing about technology in general: unless you're writing about something that's never going to change, they can be such a pain. And this one has been challenging because I'm a little bit late.

**Jamie**
I remember when I talked to [Andrew Lock on the podcast](/episode-17-asp-net-cores-middleware-pipeline-with-andrew-lock/), he's written a book for Manning Publishing called ASP.NET Core in Action

**Iris**
Yeah.

**Jamie**
And he said one of the biggest problems he had was like you: he started writing the book when version one was out and they had project.json and they had a whole bunch of stuff. Then they dropped project.json, which meant he had to review everything he had written up to that point. And then they went, "Let's change a few things and release version two," and then he had to rewrite a whole swathe of stuff in the book.

**Iris**
Well, At least he's not writing about Azure, right?

**Jamie**
Yeah, that's true.

**Iris**
Oh, yeah.

ASP.NET Core certainly had some challenges in the beginning, and there are a lot of benefits, and there are some downsides. And one downside to being a popular and now open source framework is that everybody has an opinion and they're very happy to share it. Which means there will be changed because people will not accept that if you just keep things the way they've always been, if it's not, you know, considered best practise. So discussions end up with people wanting to change things, and you have, you know, the not so popular breaking changes.

**Jamie**
Luckily I've managed to avoid all of those so far. Most of the stuff that I've worked on in ASP.NET Core has been me building things, or building things for talks. But I did sort of scaffold an entire framework for the company that I work for, that they push a button and then, you know, it's essentially a `dotnet new` template. But it does most of the stuff for you: it sets up CORS; it sets up secure headers; all that kind of stuff. That took a while, that's good. But then, like you say, breaking changes, you know. For a while [global.json](https://docs.microsoft.com/en-us/dotnet/core/tools/global-json) was the way to go because the SDK wasn't evolving so fast, and then they went, "actually the SDKs on the Runtimes are evolving way too quickly. Drop that. Quick, just get rid of it."

**Iris**
So I don't know if you know our if a lot of people know that there is actually a repository called [announcements](https://github.com/dotnet/announcements), where you can see all the issues that are announcements and breaking changes. So actually, they have labels "breaking changes" and "announcements". So you can subscribe the repository and you will only get no notifications about announcements and breaking changes, compared to subscribe to another repository and you get announcements about absolutely everything, and you're never going to check your e mail account. So I highly recommend that people do that. If you use ASP.NET Core because you want to know ahead if there's a breaking change coming because there's gonna be more.

**Jamie**
Like you say it's a good idea to keep an eye on these changes because you don't want to get to a point where they're almost ready to ship an app, and then they release an update. Like with your book, you're almost ready to ship the book, they released some kind of update, and now everything's now invalidated.

**Iris**
Yeah, and I just hope there's not going to be more surprises. Oobviously I have a lot of contact with the team, and so on. Some I;m staying ahead of the game, but still had a few surprises I didn't expect. Actually, one of them was that so early on, they said that they would not support the full .NET Framework with ASP.NET Core. I thought I would come out later in 3.0, that's called me actually a little bit by surprise, and I haved to go and sort of change things a little bit in the book.

**Jamie**
As we are recording, it was only recently that they said that ASP.NET Core on top of .NET Framework for .NET Core 2.2 will be supported indefinitely. But everything after that, no. If you want to do ASP.NET Core three, it has to be .NET Core 3.

**Iris**
If you go to the support site, though, it won't say indefinitely.

**Jamie**
Oh right. Maybe I'm operating on old information.

**Iris**
One of the team members said that, but the support site,  maybe they're not allowed to write that on the support page, you know, there's a lot of liability promising something like that. "I'll never break up with you. It's you and me forever, and ever, and ever." All relationships come to an end, you know, at some point. So yeah,

### Iris' Book

**Jamie**
So if we talk about the book a little bit but that's okay.

**Iris**
Yeah.

**Jamie**
So do you have a hard and fast rule for when you should migrate an ASP.NET service over to ASP.NET Core? Or or is it more a case off gut feeling? Or is it more a case of your boss has heard of some great new technology called ASP.NET Core, and that's all the talk about, and then we've got to migrate over?

**Iris**
I would say when the pros outweighed the cons, and now people going to say, "Yeah, well, duh, of course."

Well, what I would say, if some of the benefits seem very interesting: say that performance is extremely important to the service that you're working on, and you've tweaked everything else and you really need this extra bit of performance, or you have some other specific reason. What I would do is I would go ahead and do an analysis before actually deciding to migrate. So first, do an analysis, and they have a [portability tool](https://docs.microsoft.com/en-us/dotnet/standard/analyzers/portability-analyzer) that you can use, which is quite helpful. But you still need to manually go through the result and, sort of, do some pros and cons that you might have some dependencies that is going to be a lot of work to replace. You might have some deal breakers and so on. So the answer to whether or not you should my great depends upon the result of doing a proper analysis.

And if you decide to migrate, you can start off by just migrating a tiny part. You don't need to migrate everything at once. And the problem I've seen is that when you see examples of doing a migration, a lot of people do sort of like pretend projects, you know. "Let's pretend we have a Web shop. My Web shop has three files, you know, and now we're gonna migrate. We do new project, we pull over the file, and we update the reference, and look how easy this is."

Obviously, that is not very realistic. The Startup I work form, I've actually used our actual production code as an example, well parts of it. Although there are some micro services, we also have sort of [distributed monolith](https://cynicaldeveloper.com/podcast/111/) going on. So we have challenges that if you want to migrate one service, you have to migrate some of our internal dependencies, that our dependency on other services that you do not want to migrate. So you have this cascade off migrations that you need to do with your dependencies, and that's a little bit more challenging. So you can actually start out by just migrating a smaller part, breaking out something from a service and make it a micro service. Or you just decide on migrating one out of your many services and then making all the dependencies .NET Standard libraries, unless you have some dependencies that makes it hard to do that. And then you have to sort of manage compiling for different platforms.

**Jamie**
So let's say you've done your analysis on a small service. Now obviously, as you've said, where people have been showing this off, it's a case of, "I have this tiny project and I changed some files and it just works."

**Iris**
Yeah.

**Jamie**
Is it a case of, with that I have a bunch off micro services, and I want to take one of them out and replace it with an ASP.NET Core micro service. Is it the case off: I just change a few lines of the csproj, I add some references, and then I stay in NuGet hell for weeks, and then eventually I hit build one morning and it just works?

**Iris**
You could be incredibly lucky and be able to do that. Most likely there's gonna be more work involved because most micro services I've seen still have some dependencies on some internal libraries that are going to be used somewhere else in the project. And the question then becomes: "how do you manage those and how do you test them?" You know, because you need to test both for .NET Core and also for the full .NET Framework, if those libraries are used in projects that use .NET Framework not .NET Core. So there are certainly more things need to think about than just simply creating a new project file, and pulling over new references for NuGet packages.

And also another important thing to think about is: the architecture is, in my opinion, all still loosely coupled modular and so on, it's still a little bit more opinionated than what I guess you can call the old ASP.NET. Because they're certainly trying very hard to encourage what a lot of people consider best practises. So you have to sort of make your convention align with them as well, if you really want a benefit from a lot of the things that come with ASP.NET Core.

So when you decide on doing the migration, you have quite a few things you need to think about and make some decisions: How you want to deploy; which conventions you gonna take aboard' You have to rewrite some parts of the authentication and authorisation and so on. So you're basically moving over to, not whole new concept, but the very opinionated framework with a lot of good practises that you might not have used before. And it's starting to look a little bit weird if you just migrate your code as is, and you try very hard not to use than you good things that come with it.

**Jamie**
So let's say I have taken some time and have I want to replace some ASP.NET stuff with ASP.NET Core. And I wanna put this to my boss and I say, "Look, boss, you want me to swap this over. I've done analysis, I've  separated out some of our concerns. I've looked at NuGet packages and internal libraries that we use." And the boss says to me, "How long is it going to take Jamie?" So how long's it gonna take, Iris?

**Iris**
I's gonna take forever! No. Actually, I thought it would be a lot of work for us to migrate because we have dependencies between services that are not supposed to be there. And we've a lot of a funky, outdated libraries, and so and I couldn't easily find any NuGet replacements for those.

But turns out that once you get started migrating it actually gets a little bit easier, because you get into a flow and now is better than earlier. So we migrated quite early on and at the time, although .NET Core has great support, there's still a lot of NuGet packages that were lagging behind. But nowadays most NuGet packages do support at least .NET Standard, and that helps a lot. It's not as much work as I thought it would be, but exactly how much: putting a time on it, and estimating is one of the hardest things in programming. So that's very difficult to estimate. If you start off by migrating one service, if you have several services I guess you could use that as a reference point. But it does get easier if you have shared dependencies and you migrate those to .NET Standard, at some point you have migrated most of the shared dependencies, and the only thing you have left is actually the ASP.NET service itself. And migrating just the service itself and not the dependencies, and you know, the tests and all that, that's not a lot of work. Honestly.

**Jamie**
Okay, so you're saying it depends a little bit on your design, I guess how you've architected all of your services together. And it also depends on how much of that code you can share in a .NET Standard library. And, like you say, as you start going it will be a monumental task when you start. But as you keep chipping away that you'll get to the end faster, I guess.

**Iris**
Yes. And I always say: always grab a dependency graph, there are different tools you can use for that, I use [ReSharper](https://www.jetbrains.com/resharper/). And you start with the leafs, because the outermost dependency is usually are the ones who have the least amount of third party dependencies, and are easiest to migrate. And then you sort of work your way in towards the service unless you're lucky and your ASP.NET service is quite lightweight and doesn't have a lot of external dependencies. Then I guess it's much easier.

### Converting to ASP.NET Core

**Jamie**
So we talked about the process of migrating, how you can estimate how long that's going to take. So let's say I don't have a micro service. Let's say I have a business line app that's been around for ten years, and then my boss says to me, "right, converted it over to ASP.NET Core. Go!" Is there a plan? Is there a gut feeling that you have for how do I split up this monolithic application and convert it over to ASP.NET Core? Do I want to split it up? Do I wanna attack it all at once? What would be your advice?

**Iris**
My first question would be: why? You've really got to make sure you know why you want to do this. Because ASP.NET is not gonna vanish overnight, it's gonna be around for a long time. So it's not like you're sitting, you know, on a ship that already sailed, if you're still maintaining an ASP.NET solution.

If, however, you're convinced that you really want to do it, and you know there's a lot of benefits and doing so and, you know, you weigh the pros and cons and decided, "OK, I'm gonna do it," and then you've done your analysis. If you're gonna migrate a monolithic service, please, please consider looking into, "Could this be split into at least a couple of services?" There might be reasons why you don't want to do that, because obviously managing a lot of services can also be challenging. Maybe you have a monolith that works really well, but you could try to just break out a little part into a service and sort of get a feel for it, setting up their continuous integration and deployment pipeline and see if that works. If it does work and then migrate the rest of it.

I would be very hesitant embarking on a very large migration without really having considering it properly first, and also given it a try. Because I found a lot of the things that we thought we wanted to migrate to a service for, such as, "Oh God, this is perfect for Containers because it's so small, modular, and lightweight," we didn't end up using that. And other benefits that we hadn't considered instead, and we wouldn't have known that if we hadn't tried sort of selecting a few services first and migrating them, and also breaking out some pieces that could be independent services. That's how I would recommend going about it. Then start really asking the question "why?"

Don't do it just because it's new and juicy and sexy. That's not good enough for a reason.

**Jamie**
I was gonna ask if we could go back to the why just because it is a very important point to make. You don't want to just convert because, or just migrate sorry, just because you *can* migrate, You know, you want to pick the time that works, and pick a technology that works. If the app is already running, and it's already running really well and, like you said earlier on towards the beginning of the conversation: if you're not seeing a reason to upgrade, maybe you don't need the extra performance; maybe you don't need the things the ASP.NET Core can give you like the cross platform. Then why are you looking to those?

**Iris**
Exactly. And also in terms of performance, you might want to do some benchmarking first. And maybe the performance is not so much in the Web service itself. Maybe the performance is more in code and you can still benefit and leverage that without having to migrate to another ASP.NET framework. So you know it is performance, do benchmarking, and consider other places. If it's that you like the new architecture, well we've been using dependency injection way before this came around, and you know, you can do that independently. And if you like modularity, you can still have a modular service without having to ASP.NET. If the argument is that you want a flexible deployment model, then that's completely different, but I know cross platform sounds really good, but not everybody's going to actually use that, and you don't want to do it just in case. So you want to make sure that you actually have a plan. If you know that you are going to deploy to, you know, different operating system then OK. But you don't want to do it so you can have the option in the future, because when the future comes, maybe there's another framework around that you want to use instead. Maybe you're not even working on the same system anymore, so don't do that.

**Jamie**
Sure, and just back up a few points there. Obviously, the majority of people in our age bracket, I guess that are .NET developers are primarily Windows developers.

**Iris**
Yeah.


**Jamie**
Not only do you need to learn ASP.NET Core, you also need to learn the differences between Windows and a Unix like operating system. If you are going to go cross platform. You need to understand the differences, and you need to understand the different paradigms and the different ideas that were used to generate these two operating systems. And, you know, you mentioned obviously containers as well, you know you don't want to just jump to, "Let's move to ASP.NET Core *and* do containers *and* do orchestration *and* do this *and* do that," because there's way too many things right.

**Iris**
If you want to use containers, containers are awesome, I can talk about that for another hour. But you can start by just lift and shift, you know, to containers, the system as-is and try out containers separately without, you know, putting in a migration in the mix. So just one thing after time. So look at the reasons first and see if there's another way to achieve that. Besides doing a full migration,

**Jamie**
Definitely. I mean ASP.NET Core is really mature now, anyway. But it's still an early version, you know. Like you're saying another on: there are some people who will work on it, who are very opinionated and bring that opinionated state of mind to the development of ASP.NET Core. The same thing could be said for node; the same kid thing could be said for React; the same thing could be said for Ruby on Rails; PHP; all of these technologies. Maybe not jumping across whilst there is still that process of, "Maybe we should do this way. Maybe we should do it that way," going on.

**Iris**
There's there's a lot of value in using a mature framework, and ASP.NET, not ASP.NET Core, ASP.NET is very mature. it's tried, it's tested, it's being used heavily, and there's a lot of benefits from using a mature framework, you know, just documentation. Just look at Stack Overflow, look at the amount of questions *and* answers. So you know, one of the downsides with jumping on board something new is, you know,  documentation is going to be a little bit frustrating to navigate because you have different versions; there's gonna be lack of documentation; the forum's aren't as busy, and so on. So maturity, you know, is something people tend to ignore when something new and juicy comes out. But maturity is what allows us sometimes to develop software faster because there's already so many questions answered.

**Jamie**
Definitely. Like you said earlier on, it's not like ASP.NET Framework is going anywhere. So looking at swapping out your entire system for something that's brand new and shiny, when the thing that is brand new and shiny is literally brand new, may not be the best idea.

**Iris**
Yeah, the grass isn't always greener either.

**Jamie**
Definitely.

Other than what we've talked about today there any other top tips that you could think of for migrating an application? And obviously we're not saying don't do it.

**Iris**
No. I mean buy my book, and then do it.

Well, I have some advice. First of always, if you're gonna use ASP.NET Core, you really want to stay up today, because it's going to keep changing, and it's changing at the quite rapid pace compared to other, more mature frameworks that really are pretty much done in terms of how much they're going to evolve. So you want to make sure that you are engaged and maybe you can share the links - I have a few links I can get to you. Obviously subscribed to the repositories. Keep an eye on announcements. There are various stand up videos that you can watch. Obviously, you have this podcast, which is awesome. And the ASP.NET team is very active on Twitter, and they will actually answer questions, and do not be afraid to ask questions, or to submit issues to the repository.

So that would be my main advice. And even if you decide, "okay, I'm not gonna migrate right now," You still want to keep an eye on this. And I would still take a look at the repository, because there are a lot of really, really good architectural discussions going on in the different issues. And I've learned a lot from that, even before we decided to migrate. That would be my parting recommendations. I guess.

**Jamie**
what I'll do is I'll get the list of links from you, any links that you want to send out, and I'll make sure that they're in the show notes. Do you know roughly the release date of your book? Or maybe what the title is going to be? I know you said earlier on that you have a goal in mind for when you want to release it, but I just thought maybe you could tell us a little bit about it, where we can get it from.

**Iris**
The book is going to be published with Apress, and we're aiming for [Build](https://www.microsoft.com/en-us/build), which is in May. I don't think I know exactly when in may, I think it's the beginning of May. I finished the book, so I'm basically I'm just formatting stuff now and just looking over things, and everything has been approved by a technical review and so on. So it is done, and then the money will come rolling in. You don't make money on books, really. But that's a different story.

**Jamie**
So have you got a finished title for it, or is there still a work in progress on the title?

**Iris**
Well, the working title is ["Migrating ASP.NET Microservices to ASP.NET CoreBy Example"](https://www.apress.com/book/9781484243268)" It's a bit long, we're probably going to go for something like that.

**Jamie**
So then just a couple of last few questions about the book, then. Because it's by example does that mean that you've written some applications already that you are showing off how to move across?

**Iris**
I'm actually using production code, which is awesome. And yes, I did ask work first. So we got some code that, you know, I'm less than proud off, but I wanted to use real code and a real example, so it's actually a part of our system that is used as an example, and I didn't try to make it pretty before I pulled it in. The example is quite realistic, which, hopefully will help people because I think it's very common the scenarios that we're struggling with, that I'm sure casing in the book.

**Jamie**
Okay, so is it one example of migrating one set of services? Or is it a couple of disparate examples that are: "Here's how you might do it for a Web shop; Here's how you might do it for an authentication service"?

**Iris**
Firstly, I'm not doing any front end migration, that is definitely not my area of expertise, and we don't render our front end from the server side that's completely independent to the client. So it's a slice of our systems. I'm actually migrating a few services with share dependencies, and some of the dependencies have to support .NET Framework as well, so we have to have tests for both. One service is migrated as a whole; one service we're breaking out a little part, showing examples of how to replace NuGet packages with new packages, and how also to work around things where you don't have that opportunity. I'm also covering how you can use, for example, conditional compilation and other hacks that are, you know, maybe sometimes a little bit questionable, if you really need to support called for different platforms.

**Jamie**
Okay, so it is really, like you say, a really example. Like how most of the people who will be buying the book will be thinking of migrating their services?

**Iris**
Yeah, for example, before we do the analysis I just go through like, basically want to remove all of your dependencies that you don't use, you want to remove. And I remember there's actually example in the book where I do a quick analysis to find out if there are any  dependencies that we actually don't use. And I found, like, heaps of code that we don't use anywhere in the project. So I even show those types of examples how first of all you want to go through the solution and clean out unnecessary and unused dependencies. Be that you know, classes, and members, and actual dependency assemblies. Though I'm not scared to show the ugly parts off the code because we all have it. And that's where you need to start actually. We can't pretend like, you know, you're migrating from a Greenfield to Greenfield because that's not gonna work. When he tried to apply this to a real life scenario.

**Jamie**
Fantastic. That definitely sounds like something I want to read, not just because it's .NET Core. But, you know, it sounds like even if you're migrating, you could maybe apply the same principles to if you decide to migrate away from ASP.NET Framework, or any of the Microsoft technology stocks, I guess.

**Iris**
Yeah, definitely. And, you know, if nothing else it's at least an interesting read because it's always fun to look at somebody else's production code. Because I think deep down inside, we're all curious. Like, how does your code look like? How do you do things? I know I am. And the source is available and everything.

**Jamie**
Wow. I definitely will be checking that out once is that so that's "Migrating ASP.NET Microservices to ASP.NET Core By Example"?

**Iris**
Yes.

**Jamie**
And you're hoping for May, around Build?

**Iris**
Yes, that's what I'm hoping for.

**Jamie**
So if the podcast goes out after then I'll obviously try to get a direct link from you to put into the show notes. But if it goes up before then: listeners, you need to be looking out for this book. Definitely.

So just a few more questions, if that's all right - I always ask these questions at the end of the podcast. How can people maybe find out more about you and the work you're doing? Or maybe connect with you to talk about things that you're interested in? Or maybe like your YouTube channel, things like that.

**Iris**
Yeah. Well the easiest way to get a hold of me is on Twitter [Iris Classon](https://twitter.com/irisclasson). I have my block, which is [irisclasson.com](http://irisclasson.com). And my Stupid Questions are published there as well as on [YouTube](https://www.youtube.com/playlist?list=PLh0LZUZnuiJZTk8I8-9_SZbOBB98lWYy0), as I do both blog posts and video on that. But those are places I'm the most active, and you'll find me at various user groups and conferences. But Twitter is the easiest way to get the whole of me. I could be a very slow, replying e-mails.

**Jamie**
I think that's the same with all of us. Like you were sayingearlier on about if you subscribe to the wrong GitHub repositories, you end up not checking your e-mails ever again. I could totally understand that.

**Iris**
I've also learned that if you're too quick to reply to emails, more will come. "Email Iris, she replies straightaway." But now everybody thinks like, "Oh gosh, she never checked her email. I'm just gonna even bother emailing her," which is excellent, Less e-mails for me,

**Jamie**
I like that. I may have to start practising that myself.

Thank you ever so much for being on the podcast, Iris, I appreciate that it's getting quite late where you are anyway, because we're in different time zones, so I totally appreciate that. Thank you very much for taking the time out to be on the show. And I can't wait to read this book.

**Iris**
Thank you. Thank you for having me.

**Jamie**
Thank you very much.

### Wrapping Up

That was my interview with Iris Classon. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and a full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/).

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Sign up for the mailing list](https://buttondown.email/dotnetcoreshow/)
- [Join the Slack group](https://join.slack.com/t/thenetcoreshow/shared_invite/enQtNjIwNDY1NDk4MTE3LTM3NWZiMDAxMWVlMDQyZGU3NDAyYzgyY2EwYjk2MmZlMjU2NDI4YTNjYzVlZDc2YzYxMDExYjFhZjYzMThlMDM)
- [Iris Classon on twitter](https://twitter.com/irisclasson)
- [Iris Classon's website](http://irisclasson.com/)
- [Not So Stupid Questions](https://www.youtube.com/playlist?list=PLh0LZUZnuiJZTk8I8-9_SZbOBB98lWYy0)
- Iris' new book ["Migrating ASP.NET Microservices to ASP.NET Core
By Example"](https://www.apress.com/book/9781484243268)
- [Stack Overflow's How To Ask page](https://stackoverflow.com/help/how-to-ask)
- [How do you even know all this crap?](https://www.hanselman.com/blog/HowDoYouEvenKnowThisCrap.aspx)
- [Days Since Last JavaScript Framework](https://dayssincelastjavascriptframework.com/)
- [global.json documentation](https://docs.microsoft.com/en-us/dotnet/core/tools/global-json)
- [.NET Core Announcements repository](https://github.com/dotnet/announcements)
- [.NET Portability Analyzer](https://docs.microsoft.com/en-us/dotnet/standard/analyzers/portability-analyzer)
- [Iris on The Cynical Developer discussing distributed monoliths](https://cynicaldeveloper.com/podcast/111/)
- [Microsoft Build](https://www.microsoft.com/en-us/build)
