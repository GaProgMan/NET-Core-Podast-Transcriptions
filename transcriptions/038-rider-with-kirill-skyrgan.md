# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is episode 38: Rider with Kirill Skrygan. In this episode I interviewed Kirill about Rider and ReSharper from JetBrains. Some of you may know Kirill from his work on both the ReShrarper and Rider projects, and some of his work on the JetBrains open source projects.

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Kirill's Introduction

**Jamie**

So thank you very much for joining me on the show, Kirill. I know that it's incredibly, well, it's not it's not the easiest thing in the world to organise a meeting between two people who are in completely different time zones. So I really appreciate you coming on the show.

**Kirill**

Thank you for this opportunity to be here.

**Jamie**

For the people who are listening in who may not know directly about you or who you are. Could you give us a quick introduction into like, who you are the work you do that kind of thing?

**Kirill**

Yes, my name is Kirill. I work at JetBrains since 2010. I started to work in the ReSharper team, I became a one of the principal engineers on ReSharper them, I think, in 2014, or maybe in 2015 I start forgetting all these dates. We started a new prototype with a new idea to build our own IDE. And a couple of years, it turns out that this prototype works out pretty well. So we gathered a team and I became the Team Leader of Rider. Since then I'm leading the Rider a project, as a product as a team lead. I'm just passionate about R ider. That's it, I think.

**Jamie**

Okay, fantastic. Could you give us a bit of introduction to Rider itself and maybe how it differs from Visual Studio? And maybe, I mean, there's a lot of questions here, but like, you know, what's Rider? Why is it different to Visual Studio? And is it related in any way to any of the other IDEs that Jet Brains sort of manufacturers?

**Kirill**

Yeah, sure.

So, back to 2015 I guess. It wasn't November when Microsoft announced that .NET Core [was] gonna be open sourced, and all this stuff. And this was the the point when we decided, "okay, let's do it. Let's just start building our own today. Let's at least try." I don't think there was like a good business or product perspective. We analysed the market very deeply and like we said, "Okay let's do it."

Instead of this, apart from this here [at] Jet Brains we have the opportunity to build our own even products. Not just because we need it for the market, not just because we will generate some money in a couple of years and return back the investments; but because we just want to do this and this makes feel us pumped up, you know. And Rider was one of these project[s]. Well the technical reason for this was that just ReSharper with Visual Studio had a quite hard times in terms of performance for huge projects. Now, the ReSharper solution contains more than 300 projects in solution, and the overall .NET hood contains 600 projects. So you can imagine just huge, huge solution. And we just couldn't open it in Visual Studio and ReSharper anymore. And sometimes we just couldn't open it in in the modern Visual Studio anymore, and we thought, "how, if we will make our own IDE that will be capable to open this?"

And yeah, we were thinking, "how would we do this?" I mean, building the new IDE and it should be cross platform one side because all of our IntelliJ based IDEs are cross platform. The other side, if we would build a new, IntelliJ based IDE from scratch would re-implement all of this ReSharper features from scratch, which would take, I don't know, 10-20 years. And we thought, "what if we will bind together ReSharper and IntelliJ, but bind via our own protocol that will connect not the complex structures like syntax trees, indices, and so, etc. Instead it will bind, the view models." 

So if we will, for example, bind the view model of Alt-Enter in ReSharper and to present ReSharper's Alt-Enter model in IntelliJ as a view, as a render: wwe don't need to re-implemented this features, they will be performed there in the background, in the ReSharper side. And we started doing this and amazingly, but it worked. It worked, although sometimes I look at Rider and for example, when I call a feature, sometimes I'm just amazed how much stuff is done behind the scenes and just incredible and this works well.

Now, in terms of the difference with Visual Studio, and why does it matter to end users?

Well, first thing is that this approach first, allows us to have a cross platform IDE because the background is cross platform: ReSharper. This back end is now 64 bits, not 32 bits as Visual Studio. IntelliJ as the front end is also cross platform. And the protocol is cross platform. So we can do this on Linux and on Mac. Second thing is that while being a ReSharper developer, I struggled a lot with performance issues in Resharper in an IDE in general. And the main performance issue in an IDE - I think this applies to most kind of applications, basically - is the responsiveness of the UI thread. Just change it to dispatch thread if you're thinking about the server, your ASP .NET server and you will get the same. And it can be affected by different ways. But one of those is garbage collection, because garbage collection suspends all the threads. Now when we have the back end separated from front end and - separate process - the garbage collection occurs there and it doesn't affect the smoothness of an editor. It doesn't affect the front end. So point number two is that this architecture, with separated back end and front end, guarantees that garbage collection will not affect the editor. And the third thing is that while being fast and responsive, at least designed to be fast and responsive, we gain all these ReSharper features already in 1.0 release already. It was 2017.5 release. Yes.

So all these three points, the combination of all those three: being cross platform, being fast but still being feature rich, gives the result from my point of view because when you look at Visual Studio, like it is one would say it is quite feature rich IDE, for sure and it's solid .But it's not very fast when it comes to huge project, both in terms of footprint and in terms of latency - in terms of responsiveness of an editor. I'm talking about vanilla Visual Studio without ReSharper. And when you talk about VS code of course we know that it is very, very fast but there are lots of users that complain that it's not feature rich enough it just an editor not an IDE. So Rider I think is a combination for all of these. Yeah, I think this is the case, this is why I think Rider really differs from both, from Visual Studio and Visual Studio Code, and why it grow[s] so fast.

**Jamie**

Okay, that's that there's a lot to unpack there I guess. I mean, I don't I don't wish we to give away the secret sauce I guess but is Rider, is it IntelliJ or is it a separate sort of product?

**Kirill**

Well that I talked about the back end which is based on ReSharper. Rider's back end, like imagine ReSharper taken out of Visual Studio and made as a separate processes, a separate features server I would say. Which runs locally yes, but it's like a server. And the front end is based on IntelliJ, yes. So the UI and UX will be the same as IntelliJ platform. But the main difference with other IntelliJ products that it is a light IntelliJ based IDE. We tried to get rid of all the indices, all the syntax parsing, ASD, and other heavy stuff, to get rid of it and to move it to a back end. So it's like a lightning version of IntelliJ based IDE.

By the way this gives us another interesting advantage, in that all the plugins which do not work and do not deal with syntax trees, all these plugins will be applicable for Rider as well, if they are applicable for IntelliJ IDEA.

**Jamie**

Wow. Okay, so there's a large amount of extensibility, I guess, sort of built into it because it has this common background with IntelllJ.

**Kirill**

Yeah, that's true. Yeah. The [NyanCat progress indicator](https://plugins.jetbrains.com/plugin/8575-nyan-progress-bar) is there. It's quite important. You know, some some people will come to our booth and ask about Rider, they're not aware about Rider,  and I say, "like, hey, like all the syntax trees, performance, garbage collection, this feature, that feature," and all of a sudden they ask, "okay, okay, that's fine. But do you have a dark theme?"

**Jamie**

Yeah, I have to say I'm a big fan of the dark theme, and it makes it a lot easier on my eyes. Some people are different, you know. I can understand that all of the work that you and your team have put into making the software and the first question they ask is, "well, does it have a dark theme?"

**Kirill**

Yeah, well, I have thought, "this is quite important," and we really make a lot of effort not about complete technical stuff like performance or some huge refactoring something internal, but about the UX and UI as well. This is super important of course, for users, we do the UX researchers on the conferences privately. We see how people are using or trying to use Rider. Most of these, of course, have a huge Visual Studio background. And we try to adapt. It's kind of tricky, because on one hand, we try to satisfy these users and attract these users. And on the other hand, we still share that common platform with IntelliJ. So it's kind of balancing between these two. And then the third point, we have to be ourselves we have to invent our own rider stuff. Yeah, but I think it works out pretty well.

**Jamie**

I guess it must work out pretty well because you know, A lot of people use it.

**Kirill**

Yeah.

### A Cross Platform IDE based on IntelliJ

**Jamie**

Just hanging on to that for a moment about IntelliJ being a common, parts of IntelliJ being common and that it's a cross platform IDE: Were there any specific challenges with creating a .NET focused, cross platform IDE, and having to think, "maybe we have to be better the Visual Studio," was that I think that there was a design idea, or was it just a case of, "there are other IDEs, but we're going to focus on this." And like I say, how did you go about the, "it's going to be a cross platform and needs to look good on all OSes," or was that something that the IntelliJ background part of it took care of?

**Kirill**

Well, yes, we actually look at Visual Studio on Windows Visual Studio for Mac and those times, it was called Xamarin Studio, MonoDevelop up on Mac and Linux. And yes, we had the desire to be better in all of these platforms and still we have this desire.

In terms of technical challenges: this back end, this ReSharper runs in mono right now. So if you launch Rider on your Mac, the Rider's backend - all these ReSharper features, all these features of the server I described previously - is running on Mono. We had quite a lot of challenges to make it run on Mono, because Mono of course differs from the classic .NET runtime. We mocked some stuff, we found quite a lot of deadlocks, multi threading, bugs. But I have to say that all of these issues were resolved with the Mono team. And we made some PRs, we've logged some bugs, mostly all of them were resolved, by the way quite quickly. And but we still have some problems with Mono in terms of performance because Mono tends to consume a lot of memory, a lot of RAM, I mean, the footprint memory. And sometimes it just loads extremely slow sometimes regarding the IO operations. So our next goal is to port our back end from Mono to the .NET. Core. And I'm happy to announce that just two weeks ago, we have firstly launched the prototype of Rider's back end on Linux running on .NET Core. So it's quite an amazing result. So looking forward to delivering this maybe by the end of this year, maybe in the beginning of the next year.

And, yeah, what else? What else? What else? In terms of the competition? Well, yeah, in the very beginning. The competition between us and Visual Studio really drove us, made us work, work and work. We still compete with Visual Studio, of course. And we feel that Visual Studio competes with us. When Rider firstly came on the market and Microsoft realises they have a new competitor, they started to be well, sometimes we're just laughing when we see the release notes on Visual Studio because it looks like they just go through the roadmap of ReSharper five or seven years ago and just trying to implement all this and Visual Studio. It's definitely by the way stepping on our toes in terms of business, because there is an idea that some people they do not require ReShraper anymore and they will just use vanilla Visual Studio, since it will have all these features. Well, if it is so it is a threat to us and Rider is the right answer as well as making your ReSharper much, much faster,

**Jamie**

I guess the thing to take away from that point is, obviously, there are multiple IDEs. And you know, people should choose, because it's a tool at the end of the day, choose the tool that fits best with your development practice.

**Kirill**

Yeah, you mean different .NET related technologies which are relevant to Rider?

**Jamie**

Sorry, no, I mean, when you brought up that, you know, Visual Studio is is implementing some of their ReSharper features, I guess. I think having competition in a marketplace is a good thing because it forces innovation. So depending on how you define innovation: innovation may be looking at what your competitors are doing and doing the same thing, or it may be looking at what your competitors are doing and trying to outperform them in some way. And I think that perhaps whilst Visual Studio was the only IDE for .NET developers for the longest time. And like I said, because it's so feature rich, you know. I don't want to detract from the fact that Visual Studio has lots of things that it does, you know. It's got the WinForms designer built in; WCF designer built in; UWP designer a built in; with a few tweaks to the installer you've got the Xamarin designer built in. You've got all of these things, all of these tools, millions of tools that, you know, the majority of developers may use or may not, you know. And I think having that competition in yourselves kind of must help the Visual Studio Team to, I don't want to say produce a better product, but produce a more-innovative-than-the-previous-version.

**Kirill**

Yes, I totally agree. And I think who really wins here is the .NET ecosystem in general because what we have is a wonderful tool, and you can choose. If you have an IntelliJ based experience - for example, some people they they are coming from, let's say PyCharm - you can use Rider and this is a familiar IDE for you. If you're really stick[ing] to Visual Studio, you have Visual Studio and it's really become a much better IDE, a much better place to write your code recently. And I just totally agree, yeah. And now when I'm comparing the .NET ecosystem, the new .NET Core ecosystem with other like, for example Java one, I think that the .NET ecosystem is growing much more rapidly, in different aspects. And tooling is one of those very, very important aspects.

So yeah, I think that this strategic move made by Microsoft to make it open source actually was a good turn because we started to make Rider we forced Visual Studio, we just, you know, like, kicked their ass, and they started to be better as well. And all these movements, all these actions, by the end of the day, they just make .NET a much more better place, to build your application, to build your full stack business solutions.

**Jamie**

Sure. And I mean, like you said earlier, you know Rider is is cross platform right? Visual Studio, there are tools with the Visual Studio branding that are cross platform-ish. So we have like you said, Visual Studio, Code is good if you want an editor, not a full IDE; Visual Studio for Mac is good if you want to do Visual Studio things, but on Mac OS. But there's not been the one tool, I guess, that can be used across all three that have been released by Microsoft. Which is, I guess, where you guys have a corner on the market: you have this pretty tried and tested IDE sort of framework, you can fall back on and say, "yeah, we'll do loads of work to make it work with .NET. But you know, now it works with .NET," and of course we've said a lot that you know, Rider uses .NET Core but obviously, I think if you're a Windows you can build your .NET apps as well. so .NET Classic, I guess?

**Kirill**

Yeah, yeah. Both classy .NET applications are supported; .NET Core; and Mono application on Mac and on Linux. So we basically support all kinds of .NET applications right now. Unity; Xamarin; WinForms; WPF; Mono; .NET Core; ASP .NET.

**Jamie**

Wow. Okay, that's a list of technologies they you support.

**Kirill**

Yeah. The C++ support is coming also, by the end of this year, I think. We will open the private beta by the end of this year.

Some people say, "maybe Rider should focus on something, something you know, more specifically .NET Core IDE and that's it, and be the best of the best of the best. Only here." I think we can do both. And I think that it just kind of silly to close these market opportunities, because all this market parts for example, WPF users; Xamarin users, even though Xamarin is stagnating; or maybe even when .NET is ending. All these markets are huge. There are lots of enterprise, lots of developers which are writing Xamarin. To me, it would be just silly not to invest in all of that, and open this opportunity to support Xamarin, for example Xamarin applications. That's why we've built our own Windows Forms designer. In 2019, we released Windows Forms designer in Rider.

**Jamie**

I mean, why not? Windows Forms is now a supported technology on .NET Core. We're running on Windows, right?

**Kirill**

Oh, yeah. And then all of a sudden a Microsoft release that said that, "hey, .NET Core 3 will support both WPF and Windows Forms."

**Jamie**

Well, I mean, you guys over JetBrains are part of the .NET Foundation, right? So it's not like, I mean, there is an element of competition, but you know, you guys are helping to push .NET into the future, I guess.

**Kirill**

I really hope so, and I believe so. Yeah.

### Things You Would Add to Rider and ReSharper

**Jamie**

I got this question from a friend of mine. So one of the things that I feel like it would be remiss of me not to ask. We are recording this on the third day of .NET Conf, so the final day of .NET Conf. And it was only a few days ago that Microsoft sort of officially released .NET Core 3.0, you know that wasn't a release candidate or a public preview beta or anything. I'm just wondering how quickly you guys can add the support for the new versions of things? So don't .NET Core 3.0 came out a few days ago, C# 8 came out a few days ago. Like is there a huge amount of effort that goes into adding support for these into Rider/ReSharper? Or is it a case of, "well, we've known about these things for a year, so we just need to flick a switch and rebuild," I guess?

**Kirill**

Yeah, we're kind of known about this because there are a bunch of previews for all of these for C# andfor .NET Core, and we constantly support all the previews. And when it comes to the RTM version, we briefly check that like the API's are not broken and still the product functions properly. And if not, we are fixing a couple of features. For example, something was broken between the last preview and 3.0 RTM of .NET Core and we are fixing this right now, and in a week I think we will release Rider 19.2.3 that will officially support both .NET Core 3 and C# 8.

Yes, we definitely monitor all these updates; previews; betas; alphas, and we're starting to support these technologies as early as we can. Sometimes it is a trade off because if we support the alpha version of new nuget packages for example, and we'll invest a lot time, and then in a month they'll rewrite everything. Yeah, it just doesn't make any sense. But even before Rider, in the ReSharper team, it was the same because we had to support lots of technologies which are coming along with Microsoft stack, development stack. So we gotta get used to it and just find all the processes here at JetBrains, and the .NET department is very well tuned to support this.

**Jamie**

So like looking at ReSharper for a moment rather than just on Rider, because obviously you came from the ReSharper team as well. Does this mean that like, do you need to know the C# spec back to front? How do you go from, "oh, this new feature been released for C# 8," for instance, "and we need to sort of add that into ReSharper." Is that a huge process? Or is it a couple of developers sit around and go, "yep, this is how we do it. And this is how we can allow it." Because like I can't even imagine how complex ReSharper has to be, to be able to spot all of the possible things that we can do in C# and .NET and F#, those kind of things. And then being able to analyse the code, figure out a slightly better way of doing something, and then presenting that to the user. Like how does all of that work? I mean without going into the nitty gritty, to give away the magic secret sauce

**Kirill**

Well first of all, we have a dedicated language support team in ReSharper, very very talented people there, and very well educated. Very smart. They, as far as I know, when I was on ReSharper and I was a full timer ReSharper developer. They work with specs, with C# specs, which also come along with a new preview version. Sometimes the specs are not very up to date, I would say and they have to improvise. But yes, sometimes they have to just think from themselves how it probably will be working in the future, and build the the architecture to language support correspondingly. I would suggest to follow on Twitter [controlflow](https://twitter.com/controlflow), our team lead of language support, he has a wonderful tweets and jokes about some corner cases in the language support that you have no idea how trashy and funky and interesting stuff you can ride with the new features of C# and still this should be supported by us. So it is hard but we have a dedicated team to support this and therefore it works.

**Jamie**

So I guess that particular team would have been working hard over the last six months or so as new things are discussed, out in the open now I guess because C# it is now partially, I guess, designed out in the open. So I guess the team there would have been, perhaps part of those decisions or perhaps just sort of a silent person sitting back and going, "ah right. Okay, so how do we implement this?"

**Kirill**

Sometimes, yes. I heard some cases when we complained about some of the decisions that it's it's going to be very, they're not obvious or they're controversial something. But mostly it is in the read only mode: we see all these conversations. I would not say for the language team, to be honest. But I've heard some examples that yes, there is some kind of cooperation.

**Jamie**

Is there potentially a feature that, now obviously I'm not going to hold you to this whenever you say about this, but is there a feature that is not currently present in Rider that you would love to implement, if you are given an infinite amount of time to implement it?

**Kirill**

Very good question.

Well, the most exciting, interesting, and promising features are already being implemented by the team. They're not announced and they're not in public. One of those is, for example, like a live share support, both Visual Studio and VS code, they have a live share feature: you can collaboratively work with each other. We're doing the same, but I believe a much more pleasant way. So, the guest that connects to someone's computer will have not just very, very stupid auto completion, but rich ReSharper-like completion; highlighting; of course the solution explorer; find usages; all the navigation; Alt-Enter; everything. And we are working on this. And I think this would be a very exciting feature.

What will come the next is that Visual Studio Code already shown this: is some sort of cloud IDE when the backend is hosted there remotely on the cloud and the cloud remote node, and you just connect there with a thin client. So I also think this is a future and right now Rider, I said previously that we have IntelliJ as in the front end, but it's like a light version of IntelliJ. Unfortunately, it's not super light. It's not super thin client and there are some things like WebStorm. WebStorm is very relevant to .NET, so all this web related functionality is on the front end right now. And this is the reason sometimes [for] some performance issues. So I believe when we'll do completely thin client that will be still very feature each like todays Rider This will make Rider even more, much more fast, but still very future each.

I also dream that one day coming to my job, I will not just open the IDE and, for example, when I update to master, the fresh master branch, why the heck should I update all this indices and rebuild all this stuff and launch my internal tool, once again? Because there are a bunch of people in my team, or maybe at JetBrains, which already did this. So maybe this could be done previously, a day ago on CI. Then the only thing that I could do is just to take the already built caches and indices from the server from the remote, and voila, it will work instantly. So I think this is another very interesting direction to move. But all of these directions are in our side, and we are working.

**Jamie**

We talked earlier about some of the features from ReSharoer was sort of, you know, added to Visual Studio and I like that you guys have kind of gone the other way. You've gone, "hey this live share feature think looks really cool. Can we implement that?" And you're looking to implement that too. And the idea of perhaps having the thin client talking to a remote server as well, I like that too.

**Kirill**

Yeah. And it doesn't solve only the performance problem here. Sometimes, it is very hard to mock all these services, remote services locally. For example, I have I'm debugging the application that I host in the cloud, and they have lots of services there. And it would be very hard to mock and to like, replicate all the services locally to set up the same environment to debug, to fix. So instead of doing this work, why couldn't we just be there: be on the remote and code there and fix it there, and debug it therewithout all these stupid mocks in your applications? I think this is a also one of the reasons both VS code is talking more and more about the remote divide in these three mode coding, and live share. And we definitely also thinking about this.

**Jamie**

I like that it's like we said earlier on, you know, having competition in the market helps to forge innovation. Because let's say Visual Studio stays the way it is, and you guys stay the way you guys are, then you're going to get to a point where nobody has new features, because nobody wants to implement new features. But I think having that healthy competition helps because then you can compare notes with, "this is how the Visual Studio team have done it, well how about we go and do that?" or indeed, if a third party comes over and says, "we're going to make our own IDE and it's going to be better than everyone's because... well because," you know, being able to innovate is this the reason where we have multiple manufacturers of cars, multiple manufacturers of TVs, you know.

**Kirill**

Yeah, I totally agree. And if you take a look at Unity support in a Rider for the last two or three years, it improved so dramatically. Right now, we have a dedicated Unity team in Rider to support interrelated features. And we introduced just amazing stuff. For example, Rider is now is just - I don't want to market to fully market Rider here - but just to emphasise the most exciting and technologically exciting stuff. Just imagine the Rider is connected with Unity editor via the protocol. So this and we build features on top of these connections. So for example, Unity has Unique which is an editor for game development in Rider, and Unity developers they have to switch from Unique editor to Rider or to Visual Studio, there and back there and back, which is a productivity loss. So what we can do is we can show some Unity related information right in Rider because we have this protocol connection. So this is a good example of a new feature, which is invented by us, by vendor JetBrains, just to be better than Visual Studio to attract more users. But in general, the Unity users, the Unity developers, they win. They got the perfect tooling, they got the amazing IDEs and then the Visual Studio looks at, "hey, Rider guys, they introduced a new code completion that generate the event functions for your let's do the same." They're trying also to improve. So yeah, it's definitely great, great, great thing.

### The Future of .NET at JetBrains

**Jamie**

Changing slightly again, with the new stuff that's coming out in .NET, Core 3 and C# 8, as a person not as a representative of JetBrains or the Rider team: What would be something that you'd like to see in the next version of either .NET, or C#, or F sharp, or any of those tools and languages? What's the one thing that you're looking forward to? If you had a limited budget of, you know, people to work on it and implemented it, what would be the one thing that you would look for in the next version of .NET Core, or C#, or any of those tools?

**Kirill**

Wow, great question. Actually, I'm so excited about the upcoming roadmap by Microsoft that I don't have any of my ideas. Like with .NET 5, which will be the synergistic merge of Mono and .NET Core runtime is just amazing. And I'm very pumped about this. Well, what can I say? Regarding the managed runtimes: I always thinking about the ahead of time compilation, and if this will be sorted, just smoothly out of the box by .NET Core. I know about cross-gen. And I'm seeing the both Java and .NET struggling with this for years. Like they're a bunch of issued with [Ngen](https://docs.microsoft.com/en-us/dotnet/framework/tools/ngen-exe-native-image-generator); there are a bunch of issues with... what's it called? Just ahead of time compilation... [GraalVM](https://en.wikipedia.org/wiki/GraalVM). Yeah, now in JDK, Java's JDK 13. They have the bundled AOT. But still, it looks like it's kind of a raw technology and you have to tune it, you have to do something, to set something up. In my view, this is very important: How fast is your application starting up? So I know. It seems to me that it should be just supported out of the box. There were some efforts regarding the before the Cross-gen, how was it called, like the native compilation, right?

**Jamie**

Yeah

**Kirill**

And the start up of an application. But as far as I know, People in production, they do not use it a lot. Maybe I'm wrong, please correct me. So I wish that this stuff would be much, much more trendy. And it will be just normal to have this.

**Jamie**

I suppose though if the vendors made ahead of time native compilation, the default, then no one would use the just in time stuff, which means that all of the effort that's going into, I guess, implementing the just in time stuff within - I don't think would be wasted, but it wouldn't get used, I guess. So. I wonder whether that's part of the reason why. But I guess like you say, I think bringing in the Mono tool set and the Mono runtime parts of that, especially things like when Mono linker will mean that will be able to get better tree shaking and a lot of ahead of time native compilation, which is important for things like Blazor. You don't want to be shipping 50MB DLL to the user, just because you've included Json.net and you're onlu using `Deserialize<T>`.

**Kirill**

Yeah, exactly.

**Jamie**

So again, without wanting to set any expectations for users, what does the public future for Rider and ReSharper look like? Are there are a lot of extremely exciting features? I know we kind of touched on a few earlier on where said, "hopefully in the next release, we're going to do this and do that." I was just wondering other at the you're allowed to talk about that are definitely coming up in maybe the next six months, 12 months of Rider like what's on the roadmap, I guess?

**Kirill**

Okay, I can talk about the tactic, the local roadmap and the strategic one.

In terms of first one: In 19.3, we almost finishing to implement these technological gaps between us and Visual Studio. For example, by saying this, I mean, like Rider has much better, let's say code completion, navigation refactoring, but if it doesn't support T4 templates, then like lots of teams just cannot use it in production. For the last two years, we've implemented lots of such things like resource generations; Windows Forms; project properties; just lots of stuff. T4 is one of the last things we have to implement and in 19.3, we will release T4 support, and a wonderful language support with generator. Yeah, I'll happy to announce that.

Now, apart from this, well, basically there are lots of stuff. Just if I enumerate all this stuff, it will last for 5-10 minutes. But currently, we are working. Maybe this will be more interesting to our listeners that - and this is more aligned with the strategic plans - we're working on porting our back end .NET Core, so Rider will be faster and Mac and Linux; and maybe on Windows as well because .NET Core is half a year ahead of the classic .NET Framework.

Now another thing is that we're working on live share functionality in Rider. I think it will be released next year. By the end of this year for Unity users, we'll announce hopefully, coverage support for Unity and we will be the first to support test coverage for Unity developers: both test coverage and continuous testing. Regarding the profilers, were going to support .NET Core profilers everywhere on Linux, on Mac in Rider ; and on Windows, of course. So you can finally profile .NET Core applications on Linux with DotTrace embedded into Rider. We're also working a lot about UX and UI. As I said before, some people with a huge Visual Studio background they feel themselves not very comfy when they start using Rider. They cannot find the VCs tool window - their version control, I mean - they can find reverse search; and they can't understand the trunk configuration concept from IntelliJ. And this is fine, we have no right to blame this people yeah, because I always like to say to my developers that: users are always right. So if user said, "it's wrong," you have to listen to it. You have to adapt. You have to adjust. You have to take it into account. Not say, "you didn't understand our concept." I think this is totally wrong. And then step after step we evolve and we introduced in UX UI concept, which tried to solve this problem  So yeah, 19.3 we will try to solve some of these UX problems discoverability problems, for example, visibility problems, some of our features. Some controversial actions, some may be to overcomplicated buttons, UI elements. So we'll try to address this as well.

In terms of ReSharper, we're working on making ReSharper just dramatically faster by moving it out of Visual Studio the same way we've done for Rider. So just imagine the same ReSharper as aback end and standalone headless process, right. But it will be now connected not too IntelliJ, but to Visual Studio. So we will gain the same Visual Studio with ReSharper but much, much faster. And the team is working on this. And we, I think next year, will present something about it. And what else to cover, which I'm allowed to cover?

**Jamie**

Taking a little bit to talk about converting the back end of Rider to .NET Core or non Windows machines. Is that a significant gain for Linux and Mac users? Or is it something that will just sort of happen that they won't really notice? Is it a massive change for users?

**Kirill**

Well, I cannot say users just struggling a lot and they're just screwed on Mac and Linux. They're quite happy there. Yes, there are some performance issues mostly about the run consumption because Mono is very, very greedy in terms of run consumption. And I believe so because we have our own playback framework, which is quite exciting. If you're interested, I can say more about on infrastructure, how we build treasure internally. But this playback framework is a part of this infrastructure, and allows to easily monitor the benchmarks in different scenarios. Quite micro benchmarks, I would say not just like 50 seconds for cold stop for some giant solution, but rather like, "200 milliseconds to calculate completion and this specific scenario," and there are like hundreds of these benchmarks.

So by comparing this benchmarks will see the difference. And this is in the works right now. I cannot say anymore.

**Jamie**

Sure.

**Kirill**

Yeah, we'll see the difference and I really hope that .NET Core will be faster. The other thing regarding .NET Core is diagnostic tools. Diagnose and troubleshoot .NET Core is, seems to be much easier than Mono. This is another factor here why we're moving to the .NET Core. I promise that if will notice that .NET Core for some reasons, surprising will be slower than model, we will still using mono, of course, because the performance is the key here: We're not putting something to something just for to say, "Well, you see, we're now and up .NET Core." No, we're solving the specific problems here. I hope we'll solve this.

**Jamie**

You can then presumably feed back to the .NET Core team, if something isn't as efficient as it could be. You could then, I suppose, using your playback tools go, "ah right, okay. This particular thing in this particular setup is not as efficient as it could be." And then I guess you could if you wanted to - I'm not saying you're going to but you could if you wanted to - provide some of that data and say, "here's some more benchmarks for you to run the .NET Core suite against," I guess.

**Kirill**

Yes, exactly. And we'll surely do this, and we'll surely collaborate with the .NET Core folks. They're all awesome, amazing people. We hung out together at Build, and still we are collaborating a lot, and that all the technical guys from the .NET Core team are just amazing guys, and they're willing to help us. As it worked out with Mono team, and our PRs to Mono, and our bugs and issues and performance issues to Mono. I think it should work the same with the .NET Core team. I really hope.

**Jamie**

Just briefly touching on ReSharper being able to communicate with Visual Studio perhaps for the next version, in the same way that it connects with Rider: in that sort of server-client idea. As a joke, does this mean that you could potentially have ReSharper as a service?

**Kirill**

Ah. you mean for all kinds of front end and now you can...

**Jamie**

Yeah.

**Kirill**

Yes.

**Jamie**

Yeah. So like if I invent a front end and I say, "Oh, I'll team up with the JetBrains team," and licence something and say, "right, I'll talk to ReSharper via this communication method that they've come up with. And then I can add ReSharper into my product," I guess.

**Kirill**

Well, interesting, interesting stuff.

You know which questions to ask definitely. Well, well, well, well, the protocol which binds the back end, and front end is already open sourced. It's called [rd](https://github.com/JetBrains/rd), you can find it on JetBrains GitHub. I think it's JetBrains/rd. And it is already open source.

Now the question is about licensing this closed ReSharper server. Well, there might be an opportunity to sell these servers with a separate licence. I don't think we'll open source the ReSharper as a back end in the foreseeable future. But the might be an opportunity to like say, "hey, there's a closed server, there is already implemented back end connection with this protocol. So all you have to do is just to implement the front end part. And you can connect it anywhere you want. Maybe I don't know, to Notepad++, or to Chrome extension or whatever. Just implement the protocol, and that's it." By the way, the protocol binds not just C# and C#, it binds Java; C++; JavaScript, with the same on the other counterpart. So it's very quite cross platform. You can choose. It might be, we'll see. First we gotta succeed with our ReSharper out of process. It's quite early to say about such plans.

**Jamie**

Of course. Yeah. And like I said, he was mainly said as a joke. So you know, dear listeners please do not hold the JetBrains team or anyone involved in ReSharper to what I said there. That was, you know, mostly used a joke. But yeah, I like the idea that you will need to a little bit about how the protocol for ReSharper is out there in the open. So, you know, people could go in and read about how that works. And maybe there will be someone who connects it to their service. I don't know.

**Kirill**

Yeah, this protocol is a bit more complicated than LSP protocol from Microsoft. But it's fine, because but this - I hate the word complexity, it's not so complicated - but it gives you lots of API's to transfer much more and to control much more between two processes and based on this protocol, we do not bind only Rider's front and back end. We bind lots of things already in production Riders with Unity editor, as I told before; debugger host; remote debugger with a local Rider project model built. All of these separate processes: WinForms designer; WPF previewer. So basically, when you launch Rider, you can notice that multiple processes will be launched under the hood. This is really a distributed IDE right now. And all of these parts, they're connected with these protocols. So it's very, very much battle tested, I can say.

**Jamie**

So would you say that Rider pairing up with ReSharper and all of the different tools that it uses is kind of like a desktop micro service based architecture?

**Kirill**

I hate to say like but micro services because this word some circles is, you know. But yeah, yeah, you there are different services which communicate with each other. And we have front end and back end, which are the major actors here.

**Jamie**

Okay, excellent. Okay, so just a few last questions, if that's all right, don't want to take up your entire afternoon. So let's say that people want to learn a little bit more about Rider, ReSharper, and all of the protocols and things, is the best place to go to head over to [jetbrains.com](https://jetbrains.com) or whatever? Or is there a better place to go to learn all these things?

**Kirill**

Well, there is certainly better place to go, ping me on Twitter: [kskrygan](https://twitter.com/kskrygan). You can find me on Twitter just search for "JetBrains Rider" and you will find me. And we'll invite you to our separate Slack channel. This is a dedicated Slack channel for all kinds of plugin writers both for you ReSharper, and Rider, and the protocol. And we'll be happy to answer all these questions there. I think I really believe that works much smoothly there in the slack. Not by instead of answering the emails, it is a better place to answer this question there.

Yeah, so ping me and we'll send you the invitation.

**Jamie**

So if listeners want to keep up with what you're doing, is the best way to do that via Twitter or is there like a GitHub what's what's the way for them to find out more about you?

**Kirill**

Twitter is the best place, I constantly monitor Twitter. And if you have any questions related to Rider, ReSharper, I don't know... licensing, plugins, SDK API. Any kind of question regarding Rider, feel free to contact me. Either I'll redirect it to the relevant person or I'll answer that directly. I'm happy to answer that.

**Jamie**

Excellent. Okay, I got a bunch of links to put them in the show notes. People are furiously writing down. So you know, send a message to this person, little tweet us to do this do that. Rider is obviously a paid product, right? There's like a free 30 days trial.

**Kirill**

Yeah. Okay with trial.

**Jamie**

Excellent. Yeah, I'd like to thank you for being on the show. I didn't expect to go as technical as it did. But yeah, that's really opened my eyes as to just how much work you, and the people on your team, and the people on the ReSharper team, and I guess the people who JetBrains themselves put into their product. So thank you ever so much for for being on the show.

**Kirill**

Yeah. It's been a pleasure talking to you. Thank you. And yeah, regarding maybe too much technical talk today, this is what happens when a technical guy becomes a manager.

**Jamie**

No, I like it. I like it. I always love hearing, talking technical with someone.

**Kirill**

Great. Awesome. Awesome.

### Wrapping Up

That was my interview with Kirill Skrygan of JetBrains. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/) and there will be a link directly to them in your podcatcher.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Kirill Skyrgan on twitter](https://twitter.com/kskrygan)
- [JetBrains](https://jetbrains.com)
- [NyanCat progress indicator](https://plugins.jetbrains.com/plugin/8575-nyan-progress-bar) 
- [Ngen](https://docs.microsoft.com/en-us/dotnet/framework/tools/ngen-exe-native-image-generator)
- [GraalVM](https://en.wikipedia.org/wiki/GraalVM)
- [rd](https://github.com/JetBrains/rd)
