# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is episode 30: Reflections on .NET with Pablo Santos and Phil Haack. In this episode I interviewed Pablo Santos and Phil Haack
 about the journey that the .NET ecosystem has taken from it's early beginnings, through to the open source revolution. Some of you may know Pablo Santos from his work on PlasticSCM and the last time he was on the show ([episode 26](https://dotnetcore.show/episode-26-plastic-scm-with-pablo-santos/)). And some of you may know Phil Haack
 from his work at Microsoft, his work at GitHub, or his work on The .NET Foundation.

Just before we begin, Pablo was on a previous episode and we bring up a few things that we had referenced in that episode. So if you haven't heard that episode yet, it might prove useful to listen to that one too. I'll add a link in the show notes to his earlier appearance.

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Pablo and Phil's Introduction

**Jamie**
  
So thank you very much, both Pablo and Phil for taking the time. This afternoon. Well, this afternoon for me. And this morning, I guess for Phil. For those who don't know, we're all in different time zones and getting everything ready. It's been a, it's been a bit of a nightmare for me, because today, all of my hardware decided "That's it. Today is the day that I force the update, and you have to reboot everything." It's been an interesting couple of hours. But yes, thank you both so very much for taking the time to talk with me today.

**Phil**
  
My pleasure.

**Pablo**

Sure. It's my pleasure to thank you for having us.

**Jamie**
  
So Pablo, people who have heard the this podcast before will know a little bit about you. But I thought maybe both you and Phil could maybe introduce yourselves a little to the listeners. I know obviously, like I say Pablo you've been on the show before, but I think it would be maybe a good idea for people who maybe haven't heard that episode, to hear a little bit about you and a little bit about Phil and that kind of thing so that they know who we're talking about.

**Pablo**

Okay, sure. Phil, would you mind starting yourself?

**Phil**
  
Okay, I can go first.

Hi, everyone. I'm Phil hack. I am currently independent. And I started a little consulting company called hacked LLC. But most people in the .NET world will know me from when I used to work at Microsoft, I was on the teams that created ASP. NET MVC, and also NuGet, which is the package manager for the .NET ecosystem. And, you know, we were among the early rise of open source within Microsoft, especially, you know, ones with permissive licence, and that accept the contributions back.

After Microsoft, I left to join GitHub where I started working on GitHub for Windows as I went back to programming. So I was a program manager, Microsoft, and back to programming, doing C# and WPF. But then I was at GitHub around close to seven years, and I became the director of engineering for client applications, which was pretty much everything that wasn't in the browser. So the text editor, Atom, text editor, the GitHub desktop product, electron, and extensions to Visual Studio and Unity. And that's it. Go ahead, Pablo.

**Pablo**
  
Okay, so I'm Pablo Santos and the founder and CTO at PlasticSCM, we've been in business for the last 14 years, and we developed a version control system, plastic, in fact.

So, well, my, my job is basically wearing many different hats, I do a lot of things from, you know, from development to designing new stuff, little bit of content creation, and so on. Well, our main challenge is basically to to continue giving something good enough for all the teams out there, giving a good alternative to the excellent, you know, version control authorities, especially the free ones that you can find them market. And that's basically what we are obsessed with.

**Phil**
  
And I should probably add. So the reason that Pablo and I are together on the show is that PlasticSCM is one of my clients, I'm an advisor to them. And, you know, we've been looking at, you know, what does it mean for their product to live in a world where git is so dominant? And, you know, they do things that really well, that git doesn't, and so I'm kind of excited to, you know, think through that, you know, they're not here to destroy or replace git, but, you know, the world's a big place, and I think, a lot of money for different ideas about what version control could be.

**Jamie**
  
Certainly, yeah, I mean, you know, we don't get innovation in the marketplace without having, I think, maybe competitors. I'm not sure that's the correct term. But yeah, by having competition, you're able to innovate faster, I feel.

**Phil**
  
Yeah, absolutely.

**Pablo**
  
Yeah, I think that's, yeah, I mean, that's, that's our goal, right. And our key idea was, because at the end of the day, there's no single solution every developer is going to go with, it's a big challenge for us as a small team to actually try to come up with something huge to compete with, you know, git and perforces of the world and all that. But at the same time, we feel we are doing, you know, something super exciting, because we are basically giving choices to teach, right? So it's not like single solution for everyone. It's like really having different choices and different ways to understand development.

**Jamie**
  
What I thought that we could maybe talk about today is both of your impressions of the .NET ecosystem, having sort of evolved from, you know, I mean, probably you started PlasticSCM in .NET, before cross platform .NET was really a thing. And obviously, Phil, you know, you were working as a program manager at Microsoft, in the earlier days, of .NET. You know, I've read that you've, you've obviously worked on ASP. NET, classic and NuGet. So I was wondering if we could talk about your perspectives on how everything has evolved since then, I know that you mentioned earlier on Phil about being one of the key proponents of the sort of open source Renaissance, I guess, you could say, and Microsoft. So I was wondering if we could lead with that, like, how do you feel personally 10-15 maybe years on Phil about the everything now being an open source, Microsoft versus the, and, you know, I hope not to be political or scary about this. But there, you know, a lot of people saw Microsoft as like the closed source, big, scary monster, and not so much. Now, you know, how do you, how does that come about? How do you feel about that, like everything?

**Phil**
  
I mean, I feel great. Like, yeah, there were many people within Microsoft, even in those days, who rejected the, you know, ["Linux is a Cancer"](https://www.theregister.co.uk/2001/06/02/ballmer_linux_is_a_cancer/) view model, that - Did I just say, you model? Oh my God -  the view that a Steve Balmer said, and a lot of us thought as inevitable, we saw the direction that the software industry as a whole is going and saw that like, you know, open source as a core component of the business model was necessary. And I think one of the things that really bears that out is, as Microsoft has moved, a lot of its, you know, primary business model over to Azure, in the cloud, it's become essential, like, the closed source model doesn't really work that well for them to, to charge or to, you know, keep a web framework closed, when there's so many great alternatives. And when you look at their business model, they're selling compute, they don't really care. nor should they, what you're running on there. I mean, other than, you know, they don't want you to run anything bad or Bitcoin miners, but what they care about is that you're using their platform, right? And so if open source means for them means that they get more people on Azure more people being productive. That's good for them.

Way back then I remember Hanselman used to use the supertanker analogy - that's Scott Hanselman who continues to work at Microsoft - he would often say like, "Microsoft's, like a super tanker: a giant company. It's turning, but it will take a lot of time sustained pressure." And I think we've seen the result of that that constant pressure. I think the supertanker certainly was accelerated with the rise of folks like Satya, and you know, Guthree, you know, along with him to high ranks at Microsoft, and I think it's great. I do see, a lot of people were like, "Oh, well, you know, Microsoft has this history of bad behaviour in the past, you know, embrace and extend and all that." And, you know, yeah, we are talking about a very large company with a very long history.

I think the differences, you know, these are we have new leaders in place. And, more importantly, you look at, like how their incentives are aligned with their behaviour now. Like back then, when their whole business plan was on Windows, you know, dominance, like, of course embrace and extend lines with their incentives, but that's no longer the case, it would just doesn't make any business sense for them to take that approach. And, and that's one of the reasons why I feel like, you know, this move to open source has been really genuine, because it does align with their business interests,

**Pablo**
  
In our case, what we can say is that it's like a exciting time to be a .NET developer, because we've been using the .NET Framework since 2005. When we started the company, we decide to make everything in Plastic in C# and .NET. And to be honest, we went through quite difficult times.

I remember for instance, like back in 2010, or 2011 or so, it wasn't that great to be a .NET developer. I mean, you didn't have the feeling you were just using like a cutting edge or using something super cool. I don't know if Phil agrees on that. But it is more like you were on something that was built already just for corporations or for you know, in house software or something like that. I don't say that wasn't good because it was, but the general trend the general feeling for on the market, and might my feeling is that it was like, "Okay, it's not node.js, and not the super cool new thing or something." And now, we are again, to very good moment. because .NET is more active than ever. There are many more new projects, and you know, and bigger, bigger open source ecosystem, and then the .NET Core and now the NET 5 incoming, really trying to push for cross platform application. So for us is like a dream come true. Because when we started, we only went for .NET because mono existed, we always thought we needed a cross platform solution, we need to build Plastic cross platform. So we only went ahead because, "Okay, we love C# and. NET. But because mono was there," so we always dream about, "okay, what if Microsoft has dominate everywhere, really running everywhere?" And we always said okay, "but they were never going to make it for Linux of the Mac." And that's true right now. It's reality. So, you know, it's amazing times for us.

**Phil**
  
Yeah, that's pretty exciting. I remember before I left, Scott Hunter, who now is kind of runs the program manager for all the .NET Framework, he and I used to joke, part of the problem with running on early ASP. NET, and even ASP. NET MVC is that it was built on this really old code base, right? ASP. NET has been around like 13 years at the time, even longer now. And as such, it was very tied to Windows, and they had accumulated a tonne of cruft, we had these what do you call it the stealing labs, right performance labs that would run long term, I'm blanking on name anyways, stress test labs, you know, they run these long term stress test. And they would find these really obscure bugs, like, "oh, if you run this, with, you know, hundred thousand hits a second for, you know, two days, you'll run into this bug. And so now we got to fix it. And it's a bug that relates to some obscure thing about Windows or whatever."

But the long story short, after 13 years of accumulating those things, like, we couldn't make it fast, it was slow to change anything. Plus, we had the, you know, the 10 year support contract. And Scott and I, you know, we would joke, like, "we really need to build ASP 2 .NET, like, which would be rewritten from the ground up, and it would be fast, and it wouldn't carry this all this legacy baggage." And it was something that I really wanted to do, but I just didn't think we could ever, like get that to happen. And, you know, and I've since left and somehow Hunter - Scott Hunter - was able to kind of push that vision and help it, you know, become a reality. And, and as we see, that's .NET Core, which is pretty much, you know, a somewhat of a rewrite. And I think that's what's really exciting to me is that now we have this modern, extremely fast platform to build applications on. But we get to continue to use a language like C# that I really like, or if you're into F#  or any of those. It's a fun time to be a .NET developer.

**Jamie**
  
It really is. It really is. I remember, I think it was one of the first ASP net community stand ups with Scott Hunter, Scott Hanselman, Damien Edwards, and a bunch of other people. I'm blanking on exactly who was there. But I remember that the two of the three Scots and Damien were there. And they were talking about what what's the whole point of this ASP net vNext thing, because I think it was still called vNext at the time, and Scott hunter broke in with "Linux servers, I want you to be able to run your ASP. NET applications on Linux servers, as easy as you can on Windows servers." And I think that was kind of alluding to we both were saying, you know, this ease of moving to maybe a different server technology. And, you know, going back to something that Pablo said, you know, I've always thought that .NET was always a sort of enterprise level programming arena, sort of like a programming framework specifically for enterprise level applications. That was, like you said, fairly was he was tied to Windows, you can only get so much technical debt before, you have to kind of step back and go, actually, now we have to deal with this. And that was not a good thing or a bad thing that is, you know, being able to step back and go, actually, I think we need to rewrite part of this or take care of this. Because, you know, there's long standing bug that, like you were saying, you know, two days of thousand requests a minute, and then eventually it falls over. Well, maybe there are some real world applications where we can't have that.

**Phil**
  
Yeah, I think it's often developers always want to rewrite things, right. And a lot of times, that's actually a very poor decision. But when your fundamental assumptions change, a.k.a "oh, we actually want this to run on Linux," then a lot of times the rewrite is in order because you have years of code written against a different assumption, which is, you know, all we care about is Windows. So yeah, made a lot of sense.

**Jamie**
  
So what about C# then? So C# has come along in leaps and bounds in the last 10, maybe just even 10 years. But obviously, it started as I don't want to, say the little programming language that could be you know, it has some pretty simple beginnings from back then. And, you know, we we've we've all said that we like working in C#. So from a personal perspective, are there any parts of C# that you each love that you think, "Hey, this would be brilliant in another language?" or maybe something that should be another language that you think are this should be in C#? You know, what are your opinions on the evolution of C#, I guess?

**Phil**
  
Well, you know, what, in terms of things in C# that are going into other languages, I mean, we've seen the async/await, which I think, actually had to start in F#, and kinds gets into C#. And now, you know, Rust is, if I just, if I heard quickly, Rust just decided on what their async/await syntax is going to be. And I think that's been one of those really great innovations to come out of the .NET community. A lot of time, we look at the .NET community, .NET ecosystem, and we see it adapting the innovations from other places, and I don't think that's bad at all. And I think there should be a lot of sharing, and that's how good things come about is when we have a diversity of ideas from all these different communities. But there's often a sense of well .NET is always adapting, you know, taking and not actually seeding these great ideas, I think, two that come to mind, where .NET seeded it: async/await, and then [reactive extensions](https://github.com/dotnet/reactive).

Reactive Extensions hasn't actually caught on in the .NET community as strongly as you know, as you might expect, but what was interesting is that in the Java community, and like, for example, especially a company like Netflix, it's really taken off. And it's a really interesting paradigm for writing async code. I mean, as [Moore's Law](https://en.wikipedia.org/wiki/Moore%27s_law) slows down, you know, we need better and better tools for asynchronous programming and parallel programming.

In terms of what C# could adopt, you know, I haven't really thought about that lately. C# seems to be adopting things pretty quickly from, you know, other ideas like functional programming, with pattern matching, you know, some of the best ideas and F# are starting to make their way into C#. One of my favourite things, is, you know, the non-nullables now, or nullable reference types, as they call it, you know, trying to fix [Tony Hoare's billion dollar mistake](https://www.infoq.com/presentations/Null-References-The-Billion-Dollar-Mistake-Tony-Hoare/) in .NET. You know, the challenge with that is that it's not something that you can just like wave a wand and do, and add in after the fact and not have any problems. But I think it's great that the team is attempting to tackle it head on. But you know, that's the kind of thing where in a language like F#, because it's baked in from the beginning, you know, you get a stronger guarantee there.

**Pablo**
  
From the language perspective, I think, you know, development, we had a quite a few special circumstances that didn't allow us to adopt new features as, as quickly as we wanted. We have a, well I know if it's a reason as an excuse, but we still cross compile part of our command line, to Java through a very old project that is now open source, and basically lets you, you know, build to Java virtual machine code. And that prevented us to use some of the new features, because they were probably not, well they were not supported, right. So you try to do some stuff, from .NET three dot something, or something, or some of the newest, C# versions that are simply not supported, right. So that actually prevents us to explore new things in some parts of our code. And that we're a little bit constrained by that. And we are free to do anything we want on the server side, or the web interfaces, or most of the GUIs. But some parts of the core are really using very, you know, I will say, legacy style, or old style or something like that.

But what I found myself doing is that, the more we move forward into that thinking, or maybe the older we get, or I personally get is like, I don't get so much excited about the new things like okay, I like reading about them. I like to be aware of what's new. But I remember in my early days, I was like trying to use every new feature every single day. I don't feel like that anymore. Right now, which I don't know if it's good or bad. But it's more like, "Okay, let's try to be as practical as possible, as pragmatic as possible, and really focus on on really solving the problem." So I always have this feeling that some of the new things, you find that a little bit of syntactic sugar right now. Not all of them, right, but many of them. In my case, I might be completely biassed. But this limitation doesn't mean we are not up to date with the new things. No, I mean, we will love the async/await, we didn't use it for a while because we were a little bit into the old async pattern, just launching callbacks and so on. But yeah, they are clearly a big advantage of that. And then of course, well, it's not new anymore, I mean, it's quite old. But I mean, I'm thinking about some of the new improvements in the language. So my vision is, I like to see the language is alive. But it doesn't mean as application developers, we're going to use everything in the first day because it's sort of I prefer simpler, simpler, simpler code, something that everyone really can understand that following every new trend that shows up.

**Phil**
  
Yeah. I will say this, to be fair, the like a lot of these improvements and C# are actually about making the code simpler, removing unnecessarily ceremony and boilerplate, and that sort of thing. You know, I think you're in a situation where like, you know, having coding against mono, for example, like you can't necessarily take advantage of the latest features. But, you know, the nice thing for you is there's this bright future with that .NET 5, coming out that everything converges, and now, you know, there's this one .NET platform. So, you know, I wouldn't suggest that you adopt your every new feature the language, but at least you have the opportunity to say, "well, this one will make our code even simpler, or this one will reduce, more importantly, reduce concept counts." Like it, the thing about async/await is it not only simplified your code, but it kind of reduce the complexity of how you thought about asynchronous code, you know, versus, you know, calling all the `begin await`s with the callback functions, which was really way more complex and difficult to follow. Now you have this simpler way of following. So I think, you know, that's one of the things that really excites me about .NET 5 is for people who are doing cross platform .NET, you know, development on Mono or Xamarin, they'll all be on the same page. And that should make it easy, especially for like package authors should hopefully make it a lot easier to write libraries that target all these platforms, and not have to worry about this so much.

**Pablo**
  
Yeah, that's absolutely right. And the other nice thing about C# in general, is that many of the things, you start simply using them, you don't really even I mean, you just don't really even realise you are coding in a much different style, that 15 years ago or something. So you look at very old code that wasn't really being very active for a while. And then you notice a difference. Hey, I mean, I'll just go to the spot, something super old, right. But remember, the [ArrayList](https://docs.microsoft.com/en-us/dotnet/api/system.collections.arraylist?view=netframework-4.8) or something like that? I mean, we don't use them anymore because you use generic there. And that's something that simply happens, like, you know, it seems like that's super old and that's not probably a good example anymore. But it's like, you know, even if you don't do it on purpose, that's something I didn't say before you start modernising the code. You know, it just simply happens, because you read about the new things. And then you start using LINQ in here or there, or of course, it async/await is something they also introduced here and there, and many of those things. So the continuity in C#, you can still compile the old code from 15 years ago, but you can put something super new together. I think it's, it really makes it easy to move forward, step by step.

**Jamie**
  
Yeah, I think that's one of the one of the best things about the .NET languages, and that all of the compiler versions will always compile older versions of the code, if that makes sense. Kind of like what Pablo was saying, you know, you can take some code from 15 years ago, and put it through Roslyn now. And it will still compile. The framework may have moved on, and you may not be able to access the same API's in the same way. But the code will still compile in and you'll still get something out the other end, which is incredibly useful, I think. Especially when you know, for people who come on to maybe doing a maintenance sort of role where you have to take really old code and just add a new feature to it. But then I guess, you can then use was the principle is that the [Boy Scouts principle](https://deviq.com/boy-scout-rule/) of going, "I have this 15 year old code, have to add a new feature. I could tidy have this little bit and maybe tidy up the code around it."

**Pablo**
  
Yeah, that's true. Right.

And I will say that the only thing I like to get rid of, or in our case, and I don't think it will be ever possible, because you know, that null checking is like, I love new approaches that much. I mean, I really find super buggy some of the things where we're checking for null or something I know we could have done better to actually avoid that. But

**Jamie**
  
Sure. Well, I mean, for me, one of my favourite C# features ever is the so-called called [Elvis operator](https://blogs.msdn.microsoft.com/jerrynixon/2014/02/26/at-last-c-is-getting-sometimes-called-the-safe-navigation-operator/), not just because of the name, because I mean, the question mark of the period next to each other do kind of look like Elvis is sort of bouffant hair. I don't know whether that's the right word, but the sort of haircut. But I love the idea of being able to do that null check, that null reference check, without having to do, "if object not equal to null and property not equal to null, give me the value." It just is that wonderful little piece of syntactic sugar that on first look makes it a little bit more complex. If you've never seen that Elvis operator before, it looks a little bit more complex. "Why's this question there?" Not so complex as the Is it the question mark bang operator in C# 8? But once you get the hang of it, it makes more sense than writing 15 layers of if not null checks, just again, a value of a property.

In both of your opinions, what is it about C# that's allowed it to stay so fresh? Is it because it has this ability to sort of seed ideas out to the community or take ideas from the community and mix it in? Is it because - most programming specs are open source, but - the programming spec is open source, the compiler is now open source? Is it because of the amount of communication with the community? What is it about that, that you think that has made C# one of the I'd say lingua francas I guess of the modern programming community,

**Phil**
  
I think I give a lot of credit to the guidance of the C# team, especially, you know, the leaders Anders at the beginning and Mads Torgersen now. In terms of setting a strong kind of vision of what they want C# to be in what they don't want it to be. And having a clear goal of it being an approachable language. And it won't take in, you know, just in the feature, like they're not constantly adding things all the time where you get, like a Swiss Army knife with 100 knives, you know, isn't all that useful. So, but at the same time, they are willing to learn from, you know, other languages and take some of the best ideas. I think it's a it's a very curated language. And I think that's important.

I do think the open source aspect, especially the fact that they're doing their discussions, their design discussions on the GitHub repo and conversations there. And that Roslyn itself is open source is really fantastic for the growth and evolution of the language, because what it means is that people feel connected and engaged in it. And they, you know, I sometimes like going in and just reading a discussion, even if I have no skin in that particular game. But like, it's kind of exciting to see, like, Oh, you know, an idea that you thought would be simple, you hear all the edge cases and how deeply they think about, you know, any new language feature, but with Roslyn they can then go quickly, even spec out if they really liked it, they could spec it out and try it in a branch and you could actually try the feature out and see how it feels, rather than just debate it and, you know, try to hypothesise about it. So I think they have a really, they're fostering a really healthy community around the language and the language design.

**Pablo**
  
Yeah, in my case, I will say that, I think it's, it's fair to say that the Microsoft team did a a spectacular job all the time. I mean, all the years they were developing C# and .NET in general, right. I mean, we can give a lot of credit to the latest move to become open source, which I think is great. And it's really reenergised, th entire thing. But my belief is that they did an excellent job over the years, even when, you know, I'd say, okay, maybe around 2012-11, something like that, it was not so trendy anymore. But I don't think it was mainly due to a technical thing. I think the language on the framework was very good. The things that probably, you know, there were many of the things, different approaches to development, and so on. Although the core was still very good for me.

I still remember my first approach to C# before I was doing some C++ programming and Java programming for a while I also developing Delphi, in Delphi, the the object Pascal thing, from the same creator, if I'm not mistaken, than .NET. So when I first moved to C#, and .NET I got this magic feeling that you know, everything works. The first time you try it, right, that's first strike. And it was never like that, at least not for me, was C++, right was like, okay, you run something that doesn't build, or it doesn't work as expected or something and you try again, even for the smallest thing. I mean, C#, everything so smooth. And I think I've never lost that feeling. And truly I now to take it for granted, because it's like so many years on procedure. But I think, you know, that there's one of the magic things for the language. For me, I mean, everything is just in the right place.

And then, of course, over the last few years, and as Phil said, all these open meetings, they, they host and so on, that's super good to see that, you know, they are taking nice things from the community and also from other languages and getting ideas and you feel it's alive. And even what I said before, even if you are not using everything on a single day, every single day, because you cannot keep that pace it's still good to know, you're on the right path. I mean, you don't want to be on the language that is dead. Right? I mean, I don't think many of us want to be there. So that's super refreshing.

**Jamie**
  
Great. So I guess this next question relating to C# is a bit potentially thorny. It relates to Java. And a lot of people over the years have sort of compared C# to Java, rightly or wrongly, a fairly or unfairly, you know, that's for greater minds the mind to figure out. But what I guess, comparing with it without having to get into a thorny discussion about C# versus Java. If someone came to you today and said, "Hey, we're going to start a new project, and it's going to be in C#, or it's going to be in Java, and you get to decide," would your instant reactions be, "hey let's use C#"? Or would they be, "maybe I should investigate Java? Because I haven't looked at"? Or would that be more a comfort thing? Or would it be a case of ,"nope, it's definitely this language versus that one"? Or is it more a case of, "well, let's see what the problem domains going to be and figure out, you know, maybe Java is better at the these particular problems, maybe C# has more support for these particular packages, these particular pieces of open source software", or maybe it's a case of, "well, we'll do some of the code in one language in the code in some of the code another language and have them communicate via web API is or something"?

**Pablo**
  
I mean, I'm very biassed, because you know, I've been using C# for so long, and we have the choice to go for Java and we didn't go that, that in that direction. So to be totally honest with you, I think, every couple months, I I think we'll be in a better position. If we, if we have gone the Java path instead of C# and .NET 15 years ago. I don't know my belief is that I mean, I'm my happier with C# because I I love the the environment. I love how it looks. I love how you code it. But it's also a matter of getting used to it. Right? So if someone came to me, which was the original question and asked me, "What would you choose?" I will say, C# .NET.

But I might be currently biased. So I'd love to hear what Phil has to say.

**Phil**
  
Yeah, I mean, I think you know, as engineers, as programmers, we like to delude ourselves to think that we're purely rational in our, in our technical decisions, in that we choose the right tool for the job. But I think that most of that is we're trying to find a polite a word, then BSing, I'd say that we're BSing ourselves. Because a lot of these tools are sufficient for the job, right. And, you know, when I look at Java and C#, I think they're pretty similar in terms of the types of domains and tools and apps that you can build with them, that they're really good for that there's certainly differences in the community.

Java has been around longer and has a huge ecosystem. You know, it's one of the top languages on GitHub, so you're going to find, you know, especially for certain problem domains, you know, more live more available libraries, and that sort of thing. If you're doing something really specialised, you know, like, yeah, you might do a Java interop, because like, you know, there's a Java library for that, that you need and different C# library. But I think in most cases, like people choose the tools and the libraries that align with what they're comfortable with what they've already known, what communities are already a part of. And so yeah, if I'm going to be one of the people coding, and I'm working with other .NET developers, I'm going to choose C#, I'm gonna try to choose C# because that's what I know. But you know, if I'm just going to be like, let's say the leader, the effort, and I'm not actually gonna have to write code, like, and the existing developers a Java developers, yeah, I'll, you know, run a Java thing.

I mean, I'm fine with using other tools, like at GitHub, you know, I led teams that were doing TypeScript, for example. And, you know, and in that case, it really felt it was kind of the right tool for the job. But it also reflected the existing skill set of the developers we had on, you know, on staff, and it made a lot of sense, you know, let's ramp up time, then, you know, we could have chosen some sort of cross transpilation option like using closure script, or, or Elm or something. But we decided no we like TypeScript, we had existing JavaScript and C# developers. And it, what was comfortable for us, it's what would make us productive more quickly. Each language can find this proponents that say it's the one true language or a better language. But I think it's really about where your background is and what you're comfortable with.

**Jamie**
  
I like that, that seems to align with some things, I read the I believe it was the Phoenix Project, along the lines of until the product is in the client's hands, that is not making any money for them. So let's just get the product out to the client first, get them to make some money with it. And then they can get back to us about well, maybe it doesn't do this, maybe it doesn't do that. At that point, we can decide that maybe this new feature needs to be implemented in a different language or a different framework, or, hey, there's already an open source project, which sort of handles this, why don't we just sort of leverage that instead of writing our own?

**Phil**
  
Yeah, absolutely. There's no, nothing that replaces getting something into users hands for really learning about what it is that you should be doing?

**Jamie**
  
Sure, I've always said that the customer doesn't know what they want, until you give them what they don't want.

**Pablo**
  
That's very true. I'll take note of that.

**Jamie**
  
Please do please do.

Okay, so we touched on the upcoming sort of combination efforts that emerging as aware of all of the .NETs into one .NET. I guess you could say one .NET, to rule them all. But I know that we touched on how it would make maybe some of Pablo's work a little simpler. And definitely, I think, from a skill set will make hiring and firing people, maybe not firing people but hiring people, finding that human resource a lot easier, because you'll be able to say, "hey, you are a. NET developer?", rather than, "are Mono developer? Are you a Xamarin developer, or you are you know .NET, core developer?", that kind of thing. So what are your opinions on the that upcoming merger,

**Pablo**
  
Okay, for me, it's as I said its a huge opportunity, because we are really invested into the .NET stack. I mean, we've been using Mono for eight years, and we've been through many versions and so on. So the super nice thing to me is that, if you think of .NET, right now, it's a really full stack. And you can do everything, I mean, you can develop really low level code, and we have cold using, you know, memory map files and stuff like that. And then we have super high level code doing GUIs and then we have database code, and we have web. And now you can have people web assembly. And you can even have mobile, you know, code for mobile devices, and so on. So it's like, you can do everything. I don't know if that's, that was the original code goal? I think it was.

Some people will say it's better to have smaller specialised languages for each task. But I think from a very practical perspective, is super good to be able to do everything on a single language. I mean, probably C# and the entire .NET I don't know, maybe this is a new C, right? There's something we can use for everything, maybe one day, we'll see all the tools, adopting, but not everything, because that's not possible anymore right? There's Rust, and many others out there that are super good, too. But it gives you an opportunity to need to really leverage your expertise, so many different areas. From, as I said, web, you know, a desktop application, super fast performance code, stuff like that. So I think that's really good and games. Let's not forget about games, unity alone has many, many developers using C#.

**Phil**
  
Yeah, I think the convergence is great. But you know, like, to caution, kind of keep expectations and reasonable. Like, it doesn't necessarily mean that suddenly, you know, you're only looking at, "oh are youa .NET developer, you don't have to worry if there's Xamarin or this or that," because, you know, what we're talking about here is a convergence of the language and platform. Which is great, especially if your server side or back end or low level library developer, any of these things, it really will reduce the number of concerns that you have in terms of, "Oh, like, this runs differently on Mono than it does a .NET Core than it does on .NET Framework," like that kind of for sure. It's going to reduce that. But you know, the language and the platform, it's just one small part of building an application. Right? If you're is it, you know, building mobile applications, that's a whole other domain on top of that, right, like, understanding. Okay, what's the cross plat part? How do you interact with the controls that run on Android versus iOS? And that's a set of domain expertise on top of like, just the .NET and C# part of it, that you get the benefit of experience. So you know, if you're building mobile apps, you're still going to want to, you're still going to, you know, want to find experts in that domain, right? If you're building cross platform apps, on desktop, you know, like, there's all kinds of, you know, as Pablo can tell you all kinds of considerations

**Pablo**
  
Yeah

**Phil**
  
For running on different operating systems when you're trying to use, you know, native UI controls with with things. Yeah, you wanna talk about that?

**Pablo**
  
No, sorry. Yeah. And I was gonna say, yeah, you know, how hard it is to have GUIs on different platforms. So yeah, sorry to interrupt.

**Phil**
  
No worries, I was pretty much done with that thought. I mean, to summarise, I am excited about the convergence. But I think you know, we're still going to have these very deep expertise in these vertical spaces,.

**Pablo**
  
There are a couple of things I like to say. One is, we're talking a lot about .NET. Core and how the future .NET Core is going to be, but I think, I failed to say how much credit the Mono team deserves. I mean, I really admire what the did over the years, everything that they have achieved, and actually they proved they had the right vision, because now what they have in mind is going to be mainstream. And I have a question for Phil, do you think, I mean, like the next .NET, .NET 5 or something, is going to be somehow like the next Java. I mean, maybe we need I don't know, like, a community to get I don't know, Google to develop, natively the Android thing on .NET or something like that. Before, it was not an option because of the, you know, under the Microsoft umbrella, but now that is completely open and so on, maybe you are just seeing the next Java or something like that. I don't know. I don't know. Like you think about that.

**Phil**
  
Tou know, I kind of hope so. Next up in the sense of like, it's a true community cross platform framework. So I'm, I'm on the board of the .NET Foundation now. And it's one of our goals is to make, you know, the .NET open source ecosystem healthier, but also, you know, to create a little more independence of the .NET ecosystem. You know, even now .NET, at least, you know, in the minds of everyone, it's very tied to Microsoft, and they see it as an extension of Microsoft. But when you dig deeper into that, you realise that, well, they've open source the spec. And, you know, they have a standard, right, whereas, you know, the Java spec is like, they didn't open it to standardisation community, committee, like a standards committee. like .NET did. And so things like that, you know, make you realise that like .NET is a great platform for this because everything is open and standardised. So anyone could create their own implementation if they ever needed to. But I think that, you know, there are more and more placing as a good foundation runs on all platforms has the potential to run on any new platforms. Open Source, yeah, I think it could be a really good place for the featured efforts like that.

**Jamie**
  
I'd like to sort of echo what Pablo said about the Mono team. And you know, what Phil has just said about .NET itself, the ecosystem being such. I mean, I'm a bit one sided, because I've, you know, I've been developing in .NET related technology since 2008. So, you know, I, when I say I think it's Ace, it's because I've been doing it for 11 years. But, you know, I yeah, it really is an amazing community to be in and, and amazing group of technology companies to be working alongside of, and it's like, like you said, Phil, everything is open, you know, you know, all the there's there are open source packages or closed source packages, the language is open source, the standardisation has happened, the compiler is open source, everything's, it's like open source for you, open source for you, open source for you. And I really like that. And I think that kind of ties in really well, with, like Pablo was saying about the work that they are the engineers of Mon have done, you know, when I talked to Jim Bennett, he'd mentioned that a number of the unit tests, a large percentage of unit tests for the Mono framework were lifted and shifted into the .NET Core code base, and vice versa. And it all just ran perfectly. And I don't think you'd get that if .NET as a platform was closed source, you wouldn't be able to have an open source re-implementation in the way of Mono. That is, as I mean, it's had its teething problems, let's not beat about the bush, but an open source platform like Mono that is a re-implementation of what was at the time a closed source platform that just works. And it works across different operating systems, and then just being able to sort of take some of that supporting code around it, and sort of throw it onto a completely different implementation of that framework. And it all just work.

You know, a lot of people don't realise that, with Mono coming into the .NET ecosystem comes the Mono linker, which means that you'll be able to build, you know, platform specific executables, that presumably will make your code smaller and faster, and bring in all of your dependencies and tie that up with ahead of time. It just, it's all wonderful. And I don't think, I honestly don't think, because I've not been in this game for as long as you know, either of you guys, you guys all have the experience on me on this. But I don't think there's been another programming framework that has taken that trajectory.

**Phil**
  
Yeah, I want to add like that. So I was rambling early on, what I was trying to say is like C# ECMA standardised, the standards by the ECMA.

But yeah, I think a lot of like you said, going back to the Mono community, I mean, what they've done, you know, it shows that like, Miguel de Icaza is a Distinguished Engineer over at Microsoft now, and he's, you know, heavily involved in the new, .NET. And I think it it really shows and I think, you know, when you think about the level of talent of the Mono of developers and how many talented developers who were working on this platform that was trying to, not only re-implement the closed source .NET back then, but also, you know, create all these new innovations on top of that, so that they can run on like small devices and things like, like the [Meadow project](https://www.wildernesslabs.co/meadow) comes to mind, right? is impressive is amazing. But you start to think about the future of, "Well, imagine that they're all working together on a single code base, and not just trying to re-implement and extend but actually, you know, drive the whole same thing forward." Like, I think, you know, that shows that there will be potential for even faster, better advances in the platform.

We've seen how, like the, you know, the doing the benchmarking, and the what do you call it? The power...

**Jamie**
  
[Tech Empower](https://www.techempower.com/benchmarks/)?

**Phil**
  
Yeah, Tech Empower benchmark. Yeah, the Tech Empower benchmark that there's going great on there. You know, there's so Meadow, I mentioned Meadow, they're a company that's building a, an IoT device board, that runs .NET Standard on Mono. And you can see that down the road, like, you can imagine that that will probably move to .NET 5 at some point. But by being done .NET Standard, you don't really need to know what the underlying framework is, right? You just code against the .NET Standard. But seeing .NET running on IoT devices, and the kind of thing where, before when I was, you know, at Microsoft even never really thought about running .NET on like little devices and programming, you know, like the internet of things with .NET. Like, it was [.NET Compact](https://en.wikipedia.org/wiki/.NET_Compact_Framework), but it was extremely kind of hamstrung, right. These are new, you know, platforms, new arenas, where we can have that that kid running that like, you know, we wouldn't, wouldn't have even been able to imagine that before. But now these things will be realities. And it'll be interesting to see, you know, where the future that takes us.

**Jamie**
  
Yeah, it's, it's exciting times, exciting times. I remember talking to one engineer, and they were saying, "but fridges and TVs, you know, with the Samsung's Tizen operating system supports .NET Core, means I can run an app on my Mac, push a button, and it runs on my TV and then push a different button and it runs on my phone, and then push a button, another button," And like you said, when the Meadow devices come out, "push a button and is running on the edge." Everyone who's ever touched .NET the amount of work that's gone into it is just quite simply astounding.

So Pablo the last time that we spoke, you discussed the PlasticSCM, a lot of the early evolution of it was kind of figuring it all out as you went along. Especially, you know, creating a source control system out of nothing. You know, figuring out, what do these hashes mean? What does, how do we store these files in the best way possible? How do we keep histories of files and things like that? And especially since you know, you'd started the project, I actually looked into it the other day as preparation for this, you know, it came along before Stack Overflow as well. And a lot of a lot of the younger devs or maybe that's the wrong phrase, a lot of people who are less experienced in development won't realise that there was a time on the internet to before Stack Overflow. So I was just wondering how having Phil, as an advisor on the team has helped, since he was, you know, sort of brought on has it changed your workflow in any way? Or has it just as it just being a case of, there's this huge amount of experience that we can sort of pull from and and knowledge that we can sort of apply? Or is it more a case of Phil's hands on and we're going to do well, you know, we're both going to write this algorithm together and this kind of thing.

**Pablo**
  
So in the early days, when Stack Overflow was not there, we were big fans of MSDN. I remember receiving the DVDs for Office, and I was a big fan of it and when I was at college too, reading everything through MSDN and you know, later on Channel Nine, and all that, right. So yeah, everything changed after Stack Overflow and all that. Now, there's any interesting thing, I mean, you the internet connection goes down in the office, everyone knows five seconds later. So it's like, okay, you're always checking something online, or you always have something open on, that's a reality.

Then, the second thing you mentioned: okay, for us having feel aboard is super special. I mean, at the end of the day, we try to be a very competitive team, but we are small team out of a small place in Spain. And for us having the chance to collaborate and to receive the you know, the advice at the end of the day, from Phil, from his experience, his overall view, it's given us a lot of data right in front of from many perspectives, from business side of things to more technical certainly. Just yesterday, and that's completely true. At the same time, we're talking to multiple, same time we're talking now, we were discussing whether we should go for, you know, electron GUIs or not, and, you know, is like, being able to ask that, you know, a very special person who already did it before, and who knows all the people who's developing that. So that brings us a lot of, you know, confidence in what the next step is going to be. So it's like, you know, for me, a lot of times, I felt a little bit like alone in terms of, you know, having some sort of mentors, mentoring and stuff like that. And now, it's like having someone who's been through this, who knows very well with version control field, who knows very well, the technology we are, I mean, he developed ASP.NET, right. So I mean, it was like, really, I mean, a big opportunity for us. And we are, I mean, I'm personally super excited, if I talk just about myself, I'm super excited, because I've been following you for like years, right? So it's like, you know, unbelievable for me. So it's a really great experience. So I can only say good things.

**Phil**
  
I'm glad it's a podcast, so you can see me blushing over here.

**Jamie**
  
Fantastic. Okay, so before we get into the "where can people find you?" section, I just wanted to friend of the show, Arlene Andrews, asked me to pass on a question to you both. And it's not necessarily about .NET, not necessarily about C#, not necessarily about PlasticSCM or any particular framework or technology. And her question was:

> What is the most useful thing that you found that you haven't yet had a decent chance to talk about? Or to sort of introduce to someone yet? So this could be a framework, a technology, a package, a tool, even a development methodology, in either software development over in real life, what is the one thing that you've maybe in the past couple of years, you've gone, "oh, wow, this is fantastic, I need to find a project to try this out"?

**Pablo**
  
There's a small thing, I always love to to give a try. And we'll do a couple of attempts but not really, like really gone through it, which is [Wi-Fi direct](https://en.wikipedia.org/wiki/Wi-Fi_Direct). So I love the idea of being on a train or on a plane and then do push and pulls - again, I'm talking about PlasticSCM - push and pulls to another colleague, or during an event on the network is not good enough or something just connect hook up with two computers together is not something super fancy, we can get a good sound things get in there, but at the end of this site, so how not that easy to, to make. And that's something I'm super excited about.

And the second thing is file system stuff. Like, I'm always looking to how to create some sort of file system level version control. There's something I'm super excited about. And I could continue on and on because I have many, many things I like to look into not all relate to technology, like I don't know, like Program Management stuff I am currently finishing it, it took to much for me to like this badass making user users awesome. And I'm super excited about it. I'm also trying to learn a little bit about, there are plenty of things I'm super excited about. And I like to have more time to learn.

**Phil**
  
Yeah, I'm in the same boat in terms of the number of things I want to play around with and try out and haven't had a chance to is immense. I mean, two things come to mind. One is, I mentioned Meadow earlier, like I is a Kickstarter campaign, and I was a, I went on it, because I really want to play around with IoT, I don't yet have like, sort of like the killer app, or anything that I want to use it for. But like, you know, I think once it's in my hands, and I can, you know, start to experiment with it, I hope I come up with, you know, some interesting ideas for like, you know, I don't know home automation or something useful, that helps people in the world. I don't know what that might be.

And the other thing I want to play more around with is, you know, some of these AI and ML tools, machine learning. For example, I wrote a post, Microsoft has this really great set of cognitive services, and these just API's, and you can, you know, send an image and it'll classify, or you could send some text, and it'll tell you the sentiment. And so I like, you know, taking that and connecting it to like, you know, the GitHub API and doing sentiment analysis on issue comments and things like that. But there's a lot, I'd like to go a lot deeper into that. And, you know, perhaps running some of this sentiment analysis on my local machine so that I could actually do sentiment analysis on larger bodies of text or, you know, coming up with an overall sentiment score for an entire repo or an entire community, and see if that is actually meaningful or useful. So experimenting with a lot of these tools, like I've been wanting to play around with TensorFlow and things like that. But those are all areas that I'm really excited about, I just haven't really devoted a lot of time to it. Yet.

**Jamie**
  
Those are both really cool. I like I like all of those things. I for one, I definitely want to get into more sort of audio stuff. So I want to be able to maybe automate parts of this preparation for this show, maybe automate the editing and stuff like that. But that requires a kind of intimate knowledge of how audio works. And I don't have that yet. But going back to something that Pablo said about maybe a file system based source control system, that would have been really helpful for me a few months ago, I was editing - I do a number of different podcast shows, and was editing some audio for one of the shows, and the app I was using crashed, and it wiped out everything. All of it, I'd hit save, like, I just imported the raw audio directly from, you know, the different apps that we used to record everything with. So the audio was not saved anywhere. This was the process of saving it to desk, I hit Save in the app crashed. So if I'd have been able to do something with that with source control, I would have been nice, but we live and learn.

I really like the idea of doing machine learning stuff and sentiment analysis. I just don't feel like I'm smart enough to do it as well. So as we're coming towards the close, then where's the best place for listeners to find out more about both of yourselves and some of the work that you do. Twitter, maybe a blog post? I don't know what's, what's the best places for people to go to find out more?

**Phil**
  
Well, for me, I have a blog at [haacked.com](https://haacked.com/). And I'm also on Twitter[@haacked](https://twitter.com/haacked). I'm pretty much haacked everywhere you go. So like, but if you go to Twitter or my blog, you can kind of find out more about me and what I'm up to. I I've been trying to write more often. So yeah, there's a lot there to read.

**Pablo**
  
Okay, my case, they can follow them. Well, they can find me on Twitter [@psluaces](https://twitter.com/psluaces), which is like, my first name and then family name. And then while the best place for you to find things I write and things I speak about version control and development and so on and experiences we have in our team is [blog.plasticscm.com](http://blog.plasticscm.com/). We are not like super, super active. It's not like we are, you know, overloading people with content, but we try to be, you know, active. And we blog about many different things from super technical stuff to things that happened to us, as developers practices we put, and we try and help , for instance how we move from SCRUM to Kanban recently, and stuff like that. So we want to learn more that's the place to go to.

**Jamie**
  
Great. I'll be sure to include links to those all of those resources, and all the things we've talked about so far, in the show notes.

Just tangentially I just want to share this really, you probably this all the time Phil. But I was telling my brother who's a completely non technical person about this interview, and I said, "I'm going to be interviewing this guy called Phil Haack." And he said, "my goodness, that is the greatest name for a computer programmer ever."

**Phil**
  
Yeah, Phil is a great name for that.

**Jamie**
  
Yes, indeed.

**Phil**
  
I actually tell that joke all the time, when I introduce myself at conferences, and I probably need to retire it. But what I tell people is that, you know, I care about the environment. So I recycle my jokes.

**Jamie**
  
I like that. I like that.

Like I said earlier, and thank you ever so much to both of you, Phil and Pablo for taking the time to talk to me today. We're all in completely different time zones. So what is late evening for me is roughly mid morning, I guess fro Phil, and you know, even later evening for Pablo. It's all, juggling this is quite a task. So what I want to do as well as I want to, I want to say thanks to Pablo's colleague, Jordi, as well for sort of helping to arrange this. You know, it's all been a wonderful experience talking with the pair of you today. It's been absolutely amazing. Thank you ever so much.

**Phil**
  
Thank you and there's a pleasure talking to you. Yeah

**Pablo**
  
Thanks for having us

### Wrapping Up

That was my interview with Pablo Santos and Phil Haack. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and a full transcription of the interview. The show full notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/), or by clicking the link in your podcatcher.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Episode 26 - Plastic SCM with Pablo Santos](https://dotnetcore.show/episode-26-plastic-scm-with-pablo-santos/)
- [Pablo Santos on twitter](https://twitter.com/psluaces)
- [Phil Haack on twitter](https://twitter.com/haacked)
- [Linux is a Cancer](https://www.theregister.co.uk/2001/06/02/ballmer_linux_is_a_cancer/)
- [Reactive Extensions](https://github.com/dotnet/reactive)
- [Moore's Law](https://en.wikipedia.org/wiki/Moore%27s_law)
- [Tony Hoare's Billion Dollare Mistake](https://www.infoq.com/presentations/Null-References-The-Billion-Dollar-Mistake-Tony-Hoare/)
- [ArrayList](https://docs.microsoft.com/en-us/dotnet/api/system.collections.arraylist?view=netframework-4.8)
- [Boy Scout Rule](https://deviq.com/boy-scout-rule/)
- [Elvis Operator](https://blogs.msdn.microsoft.com/jerrynixon/2014/02/26/at-last-c-is-getting-sometimes-called-the-safe-navigation-operator/)
- [Meadow project](https://www.wildernesslabs.co/meadow)
- [Tech Empower](https://www.techempower.com/benchmarks/)
- [.NET Compact](https://en.wikipedia.org/wiki/.NET_Compact_Framework)
- [Wi-Fi Direct](https://en.wikipedia.org/wiki/Wi-Fi_Direct)
- Phil's website [haacked.com](https://haacked.com/)
- [PlasticSCM blog](http://blog.plasticscm.com/)
