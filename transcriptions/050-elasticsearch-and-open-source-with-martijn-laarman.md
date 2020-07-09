# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is Episode 50: Elasticsearch and Open Source With Martijn Laarman. In this episode I interviewed Martijn about his many contributions towards open source projects, some of the ways that open source can be incredibly useful, and about his work on the .NET client for Elasticsearch.

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Martijn's Introduction

#### Jamie

So the first thing I'd like to say, Martijn, is it MAR-TEEN? Or is it MAR-TIN?

#### Martijn

I accept any form of my name, but it's the proper pronunciation. Is MAR-TINE

#### Jamie

MAR-TINE? Okay, I'll try and use that from this point onwards then. I'm really bad at pronouncing names. Give me something Japanese to read out, and I'm your man. But most of the Western European names. I kinda fall over on the pronunciation because I don't have that education in most of those Western European languages, you see, So.

#### Martijn

All right, I'm not fussy at all. Feel free to mispronounce it for this podcast. That's alright.

#### Jamie

Okay, well, yeah. Thank you. Ever so much Martijn for taking the time out. And it's during the work day. Usually, these recordings happened kind of late into the evening than they usually thank folks for spending part of their evening with me. But yeah, it's part of the early afternoon. So thank you ever so much for spending your afternoon with me.

#### Martijn

Yeah, that's great. I do hope to chat a bit about Elastic Search and I actually I work for Elastic, that makes Elastic Search, So I guess this qualifies is working. So but either way, we're fully remote and in charge of our own hours. So I guess I guess even if it wasn't about the Elastic Search or I would have probably start on it in the afternoon.

#### Jamie

Okay, Well, what we'll do is we'll just tell your boss that you just talked about Elastic Search for 45 minutes.

#### Martijn

All right, if you can sign off on that one that that that would be great.

#### Jamie

Absolutely. Send the paperwork over. After that, we're going.

So for the folks, it may not know too much about the work that you do. Could you give us a brief introduction to yourself and a little bit of maybe a little bit of background knowledge? Maybe we've heard it already. That you work for a last exertion will come out to that in a minute. But how did you get to their? What's Martijn all about?

#### Martijn

What am I all about. big question.

I work for Elastic. A cement before them. The charge of the clients, older clients for Elastic. So not just the .Net one, but also the other languages that we support. But I started off Elastic as the .Net client person for Elastic Search. And, yeah, I've always done development. I started developing when I was 17. Started working professionally from 17 onwards and mainly in web development, and I've always done big data projects as well. And so naturally just let me to discover Lucene, Solr. And as soon as Elastic Search poked its head up, I started working on the client, I think, two months after Shy, the original author of Ballistic Search wrote the first version off it.

Then, ever since, I've been working on that client, and it's almost 10 years in the making. Yeah, it's kind of weird to work for this on the same open source project for 10 years and more always all a little bit apologetic, because I feel like it should have been done by now. But at the same time, things are moving fast and I  that's why I was still working on it, that everything's evolving enough, always done open source projects whether in .Net or previously javascript or you name it. I tried to do is much open source worker as I can.

#### Jamie

I do like long term projects open source or closed source because... I think he was only a few weeks ago I was reading an article about I think it was react or something similar, that one of the many millions of JavaScript frameworks and how there are very few projects that I have lived and breathed in this one particular framework for more than two or three years and how we're starting around the time of angular, react, Docker, All of these frameworks that sort of popped up seemingly out of nowhere. But out of a lot of people have put lots of effort into creating them.

But very few projects have actually lived past the five or six year standard support life cycle before they've been trashed and started, well not trashed but being rewritten from the ground up. And I think that's maybe something that we're gonna have to deal with in the next 10 years. Is all of these legacy applications written in frameworks that were sort of almost created will feel like they were released to the public overnight that have no support in them, and people are just gonna have to become experts, which is why I prefer to work with libraries, open source or  closed source that have been around for a long time, regardless of whether they are in the done state or not, because what is done?

#### Martijn

Absolutely, and I think .Net quite a different culture in that regard. Many other ecosystems where, most of the libraries in .Net have been around for many years, and the developers stick with them for quite some time, which is in many ways, I think, a blessing for the .Net ecosystem, that a lot of the big, I would say from the top 10 NuGet packages. Just a lot of them continued to be supported through everybody's hard work. I don't know if things will change in the future, but yeah, it's always disheartening to find an NPM package that that you like. But then the last commit was four years ago, and then how do you evaluate that? Is that still a good package? Is it done in dusted? It's hard to evaluate those things.

#### Jamie

Yeah, I agree completely us. As someone who creates and maintains a number of open source projects. It's disheartening, like you say, to go "Brilliant. There's a NuGet package which does all of the majority of this chunk of functionality I'm trying to create," and then, like you say, you go have a look and the NuGet package, you have a look at GitHub or wherever it's sourced from. And yet the last build, not even the last, commit, the the last build was a number of years ago. You start to worry about Well Is it maintained? Is it is it finished, like you said? Or are there bugs? If there are bugs and someone hasn't worked on it for four years, what are the chances of someone replying to a bug report?

#### Martijn

Yeah, exactly. So it's quite quite hard to evaluate packages. There's also a bit of survivorship bias. The packages that keeps getting updated might get popular just because it's keeps on being the most recent one, even though another package might be actually better for your purpose but has just stopped development four years ago. 

It's interesting to see in the .Net ecosystem what that will do in the long run. I don't know if we'll ever adopt the same culture as Node.js, where packages are pushed very fast and abandoned very fast. I hope to see that Internet more. I'd rather have too many options to choose from than too few functions to choose from.

#### Jamie

I totally understand you. In any kind of business, always better to have options because let's say I want to try and use something that's not software development related. Let's say you walk down the street and there are five restaurants to choose from. That's probably better for you as a consumer and for them as businesses. For us, the consumer. You get a choice of what you want and as a business, there's that enterprise. I have to stay in competition with everyone else around me. So it's sort of drives innovation.

#### Martijn

Absolutely. That's, I think, just different attitudes and it's It's funny that these editors are so much dictated by language and by ecosystem because I think if you speak to many .Net developers, there's a big barrier to actually make a package and put it on, NuGet. Some of it is technical where you have to package it the right way with the right arguments making sure that the automated data's correct and tested and so there's a big churn to actually produce a package and publish it on NuGet where's maybe another ecosystems? It's a bit easier.

For instance Go just references through git directly. So pushing it to git is basically publishing. Node.js also, the tooling is much more geared towards getting it out there fast and in .Net, I think that there's still bit off a technical challenge to get packages up on NuGet fast. 

But there's also, I think, a cultural barrier for a lot of folks, too, where this mental block exists if it's not good enough, where it's not ready yet, whereas sometimes pushing something that's not ready yet. But it's v0.1. It's totally fine, and you can maybe flesh things out sooner and see what sticks rather than either working too long on something on, then finding out that nobody wants it or you worked hard on something and then you get burned out, and you never actually share it with the world, which is a shame.

So I definitely hope to see more of that as .Net core progresses and the tooling gets better and easier. Yes, I definitely hope to see that progress in the future.

#### Jamie

I totally agree. There have been times when I've been working on something, thinking this is not good enough to release. And then I'll back up my planning notes because I take these meticulous (notes). I feel like I'm not like very many individual open source developers, you know people who work in teams of one, In that, I'll actually plan out what I want to do. We got a piece of paper, even if it's just a piece of paper with scribbles on it. I want to do this, I want to do that, I want to do that, And then, open a big circle, put MVP. Everything above that is the minimum. That's the initial release, minimum viable product. Without those features, it's useless. It's pointless having a library that claims to do string concatenation if it doesn't concat any strings.

Yeah, that's my minimum viable product and then all of the features. After that, our individual feature releases, so get it at that. Like you said, because you don't know whether what you've just created, he's actually useful to someone until someone starts using it.

#### Martijn

Exactly. And it's funny you mentioned, like string concatenation Think I keep on referencing Node.js that it's a comparison point, but they get often flack for producing like the quote unquote stupidest little packages, like a string concatenation package for the famously the left pad package. Where I actually see that this is strength of that ecosystem, where there's just because the barrier to entry is so low producing this quote unquote stupid little package is so easy, this also mean that if we actually do need that, something you perceived. a little feature. It's probably out there. There's probably a package that does that five line function that you might have written by yourself or had to think about. I don't know. I see. It actually is the strength off the Node.js ecosystem where .Net you have much less of those little functions or, like it either gets packed up in a big util library. Where as, it might have been better just to, publish them, as tiny little packages.
Yeah, but that's definitely like a kind of bit of a cultural thing within the .Net ecosystem where it's not. If it's not big or grandiose enough, maybe it's not worth publishing.

#### Jamie

Well, you never know. We may see a renaissance of .Net packages now that .Net Core is starting to pick up steam. And when he gets renamed to .Net 5 later this year, it might be that more cross platform developers who want to create small utility libraries may go, Hey, if I just learn the..., I mean I'm not trying to say its easy to learn how to package something up for NuGet. But like you say, there is that barrier to entry. Once you get past that and you go, Oh, brilliant, I can create 500 tiny NuGet packages that just do this one thing that may be a number of really useful extension classes for strings or for ints or something, or maybe some conversion classes or something. And I mean, we've seen that with Microsoft anyway. They've split the .Net core, base class libraries and ASP.Net core and  EF core to hundreds of smaller NuGet packages such they deployed binaries and then infinitely smaller than a .Net framework version because it doesn't require the entirety of the runtime and all of the supporting libraries to install because you just need to install that one dependency that you have.

#### Martijn

Yeah, absolutely. It's a bit of a move in the right direction. In my opinion, at least, that that's definitely happening with the theater packages do get some of the ASP.Net now gets deployed through special SDK projects, which is kind of a move in the opposite direction again.

But, uh, old in the greater scheme of things, they do still exist off their smaller packages, Which is a great thing. I guess.

### What is Elasticsearch?

#### Jamie

We were gonna talk a little bit about Elastic Search earlier on, and the night sort of diverged is on this other path, talking about .Net and Node.Js and Go and all of these wonderful languages. But you give us a quick, brief introduction into what Elastic Search is, what it provides. what kind of systems I can run it on. Is it .Net? Is it Node? What can I leverage it with?

#### Martijn

Absolutely. Elastic searches so many things that just condensed like the elevator pitch, for It's always starts injustice to one big feature or one big use case for it. But in essence, it's a full text search and analytics engines that skills both vertically, obviously and horizontally quite easily. So you can run many instances on many different nodes and create & cluster them quite easily. And it's great for many different years cases, so you can run either search for e-commerce sites, but you can also use it for the store logging of any type of data. That's more time-series based, such as metrics or logging or errors or any data that's unbounded, basically, because Elastic Search skills horizontally can always add more nodes so you can grow with your data, if you will. The elevator pitch does injustices to some use cases. But in essence, that's what Elastic Search provides you with.

I personally started using it. That's just a straight up a search for my SQL databases, basically. So I would quite often built e commerce sites, and then, obviously you need to do things like provide search pages that provides facets on the left side that you can click on and filter by all the blue products and combine it with other products with size L, for instance, in the same time. So it's also great for things like after completion. So if you have a search box, you want to through a predictive search a lesson. Elastic Search helps out a great deal there as well.

And the nice thing about Elastic Search is that basically said one data system that also allows you to plug in your logs from your system as well back into Elastic Search so it can correlate who's doing certain searches and maybe optimize our searches for the Dutch demographic differently, then for the English demographic for instance.

So yeah, like I said, my elevator pitch turned out a bit long. But there's a lot of use cases that it's really, really handy for. It's a great tool to have in your tool belt.

#### Jamie

Sure, what I'll do is well is when we were communicating off line, [you sent me a video link on YouTube](https://www.youtube.com/watch?v=sKnkQSec1U0), and I'll make sure to put that in the show notes. So if you want to learn a lot more about Elastic Search, definitely check the show notes for the YouTube link to a talk that I was linked to.

I'll make sure it's in this part of the transcription and in the useful links down at the bottom of the transcription.

#### Martijn

Awesome. Yeah,

#### Jamie

So you said it's for any kind of sight you mentioned SQL. Do I have to have a database? Or is it I create some data in some fashion and give it to Elastic Search and it will just do its magic.

#### Martijn

Yeah, so I haven't touched on the deployment part. So it's basically a Java process. It's its own database. If you want to think of it that way that you can speak to through Ah REST API. You deploy it by running a java process on your hardware. So, yeah, if you want to migrate from or not necessary migrate, but run Elastic Search side by sight with your, uh, Elastic Search deployment you can use. For instance, Logstash to send your SQL records over to Elastic Search so that it can index them and makes them available for search. Logstash is a tooling, which allows you to extract from many different data sources. SQL is one, but it can talk too many, I think, over 200 different data sources and transform it. Mutate those events or records or whatever the data source is into a the form that you need to and then load it elsewhere and Elastic Search is one off the different outputs for log stash, but it can emit those things back into again. I think offer 200 different outputs a swell. You can obviously also just code it yourself. So we have provided clients for Elastic Search. That's exactly what my team does. And so you can write a .Net application that reads SQL creates, C# objects for that, and then persist those using the Elastic Search using .Net drivers?

#### Jamie

So you can use the ETL or extract transform.  You can use the ETL tools that are provided by Elastic Search. You can indeed write your own, because is there like a schema or something or a package description? So I know that I have this data in this one format that maybe SQL that might be Mongo. We might be my own data format as long as I could transform that into whatever Elastic Search is looking for I can send it over.

#### Martijn

That's a great observation. I will try to explain why that's great observation in a second. Because, by itself, Elastic Search is schema-less. It's not completely schema free, but it's schema-less in the sense that you can send any type of JSON to Elastic Search, and it will infer the schema out, based on the JSON document that you sent to Elastic Search.

So in that sense, it's pretty free form and what type of data it accepts. However, there is a push from within Elastic, and it's publicly available, as well, too, come up with a sort of a common scheme out that works well for a lot of different use cases. Something that we call ECS Elastic Common Schema, and it basically allows show to map your events or any type of time series data. That could be logs, errors, or metrics, or event up messages, anything that's basically unbounded. And if you make it to this ECS format, then you can create a common format for all of these different data sources, and Elastic Search will also be able to provide to it better and easier visualizations on top of that. 

So by itself, Elastic Search doesn't have a UI. The UI component for the stack is called Kibana. Which is a Node.js application that you can run and which basically acts as the BI tool for Elastic Search as well. So it allows you to create official  on top of the data that you store analyst expert.

#### Jamie

That's really interesting. Then it sort of being schema-less infers, a schema. So there must be some kind of very intelligent, almost like reflection going on there to figure out what this data is and how it's all related. If it is indeed related. Does it have to be relational data. Or can I just give it here is a JSON Blob or whatever BSON Blob or something. Here is another one and here is another one, and they are not related in the slightest.

#### Martijn

They're not related in the slightest. So Elastic Search is not relational at all. So you basically store data denormalized into Elastic Search. So the document that you stored in Elastic Search, it should have all of the information inside of it that you wanna use to find it, so you cannot create relations between different documents as well. So Elastic Search is really fast, but it's fast because it basically pre-computes all of the answers for you at indexation time. Rather than at query time.

Yeah, so if you want a your data, you have to do a form of denormalisation so that in terms of consistent .Net, it means creating the whole object graph and storing that object as a single document in Elastic Search.

#### Jamie

In the same way the static sites are always gonna be faster than any kind of servers based Web application, known relational flat normalized data will always be quicker to query than data that has four hundred tables and everything is linked via foreign keys and sometimes a foreign key link table. And it all gets a bit confusing, isn't it?

#### Martijn

Absolutely so, for most cases, Elastic Search is just something that you run side-by-side next to an existing data source. That does have the guarantee that you want to have. So if you need a set or if you need transactions over multiple records, then you would need another data source next to a Elastic Search.

#### Jamie

I've read somewhere that I can just point the output of a static site generator that as long as it creates some kind of data set. I can use that with Elastic Search and similar things to provide a search like functionality on a website that doesn't have a server. Is that correct? Am I heading in the right direction there? I don't know whether it is true is one thing.

#### Martijn

Yeah, so Elastic Search is part off the whole product suite that Elastic provides, And part of that suite is also a component that's called Site Search, which is a SAAS offering that allows users to basically scan and scroll your website for you and provide a site search bar on your site without having to install anything for a server-side component, so we definitely offer this component as well. But it's not yet something at least something that you can run on your own machine. So purely a SAAS offering for now.

#### Jamie

Okay, that's fair enough. I mean, search is hard anyway. And if I can offload that to someone else to do.

#### Martijn

Absolutely, yeah, and actually Site Search will try to do a lot of smart things with ranking. Provide you with the most relevant pages users are looking for data on your site.

#### Jamie

You mentioned it just now that there is a dark net client library for last exceptional. I don't have to point. It's, um esoterica Web en pointe. I could just call this API presumably in my .Net code, and it will do whatever is required to talk to the end point. But you did mention off air that it was one of the first things that were released for videos, a phrase that I don't think many listeners will know what it means. DNX, which was the long term evolution of .Net before it was called .Net core.

#### Martijn

Yeah, definitely one of the 1st to release packages for DNX, which is I'm not sure if that's still.. It was call DNX or ASP.Net 5. I think those terms were used interchangeably. Yeah, I think that's one of the precursors that David Fowler and this team built before .Net Core really took off, which for me at the time, I was super excited to see it was already trying to implement cross platform .Net Cross platform tooling command line tooling. And it was basically a completely new runtime with new case and base Project files and with NuGet support for loading these packages as well.

#### Martijn

And so our client was one of the first packages to adopt this has well, and we've been on the .Net Core train ever since, and that's purely because I think that that course one of the biggest things to have happened in .Net and it might have been in a way, it's saving grace like it's a viable option now again for anybody that's a linux person or  OS X (macOS) person. And at the time of the next I was using OS X as my main development machine and now I'm on Linux. And thanks to the advent of .Net Core and in many ways only sharpened Rider like the experience is just so fantastic. I kind of have to confess that I think the last time I opened Visual studio might have been two years ago, which is kind of crazy.

#### Jamie

We'll come back to the Elastic Search NuGet library in a moment. But just the ability to have these C# files on do .Net builds on a machine on a USB. Unplug the USB device. Plug it into someone else's machine and just run it on that machine. I'm running Mac OS. They're running windows. Just that ability to just do that is just it's mind blowing. It's something that Java has promised for a long time, and Java did deliver on that. I think I was in the same boat as you know. I was running OS X on my MacBook air when .Net Core was first announced. Before then, I was trying to figure out how to do .Net based development on a Non-Windows machine, and I think I've got a blog post somewhere in the history of all the things I've ever written all about, using GTK # on Mono-develop and all this kind of stuff to create a small binary that I could just run and I think the target was. I had a backup of all of my SMS text messages from my phone in an XML format, and there were duplicates, and I just wanted to use C# and .Net. Load them in with this comments schema group them by conversations and then remove all of their duplicates. That's all I wanted to do, and it took me about five hours just to figure out how to compile it and build it and run it on my OS X machine. And now that same code. I just do .Net run and it is on I'm currently sitting in front of a Windows machine. But my desktop is a Linux PC, and that same Macbook Air has survived this long. So you know, I still use that, too, and I could just run it. It's amazing.

#### Martijn

Yeah, I think for me I thought that whole movement of DNX and only C# for me it's really kept me on the .Net because at the time, just seeing how agolie or how fast you can prototype ideas in Python or Ruby or like other languages, its basically you create a file and point Python or Ruby to it, and it runs it. In that sense, I think that that can still do better, like we still have project files and solution files that are pretty archaic. So if you come to .Net completely fresh, then see this project file and solution files look completely dumb. But we're in such a good state now with the .Net Core CLI and just being able to run a project from the command line without ever opening an IDE or anything like that. This is just great.

#### Jamie

It really is. Unlike you, say that barrier to entry for Python and Ruby and Go and JavaScript. It's just so low that you just create a file and point the runtime or compiler or your tooling at it and it just works. And I think we'll get there with C#.  I think so at the moment. I do know that on Windows you could just invoke the C# compiler. If you have a single file or a number of files. But the problem with that is that the call to that command gets a bit massive.

#### Martijn

C is not for the faint of heart. I guess that could be easier if you can just say, `.net myClass.cs` and it programs in CS and run. Maybe in the future. Or we can create .csx files and graduate from .csx files to C# files similar to what you can now do in  F# just prototype in FS6 files. And then, if you want to make it, ah compilable. Something with artifacts, then you just switch over to F# script files.

So but having said that, even if that's not the case now or not the case in two years, I think that where we're at right now. It's just amazing. Personally, in the personal level, found my joy with .Net again because of all this push that has been happening to create a cross platform environment and the wrong time available everywhere.

Even though there’s so many things that you might still want such as ahead-of-time compilation and like even smaller binaries, it's just it's just fantastic where we are right now.

I would much rather create binaries in .Net than I Go. I can waffle on about Go. It's It's great, the right system tooling and you crack. I got this 20 megabyte file that you can run anywhere. We're not there quite yet with the .Net either, but yeah, we're definitely not far off either so. Yeah.

#### Jamie

that's true. Like you say, with the head of time completion in the

#### Jamie

Rather than having it cross platform, you can target a specific platform, reduces file size and I think a I saw a wonderful blog post on a few days ago where the author of The blog post had written the the Classic 2D Game Snake. He'd written that in C# as a .Net binary and gotten the execute herbal binary down to 8 kilobytes.

#### Martijn

Yeah, I saw the blog post in amazement that just the fact that it's possible This instils me with so much hope and joy. It's head's crazy. Yeah,

#### Jamie

That was a feat of technical engineering. I think I read that blog post and was like, I understand about who 60% of this.

#### Martijn

That’s way more than I claim to know.

### Martijn's Journey in Open Source

#### Jamie

You and your colleagues have worked on the Elastic Search .Net client has their been, aside from the project, JSON, which, you know, we tend not to talk about, what has that evolution been for you as a library creator as someone who creates, um, software that will use this new technology. What has that journey been like?

#### Martijn

I think at the time it felt a bit rough. I think looking back, I paint a bit off a rosier picture in my head. I mean, it was okay, I think the biggest issue. And I still think it's the notion of TFM's and producing libraries that have to be loaded in different runtimes. I think that's the hardest thing to wrap your head around as a library author. So Okay, I build a package for .Net Standard 1.1. What does it mean? Where can it be? Loaded? .Net Standard is really fantastic, because prior to that, we had PCL profiles. And then I think it was PCL 1.68 I believe there was the magic profiled it had the most environments that the deal l could. We loaded it through NuGet. I think that's still a bit off a Harry spot for the .Net ecosystem. So just just a constant. Okay, building the .Net Standard 2.0 packages in my NuGet package. Okay, but then NuGet has support, so I need to also to create .Net 4.61 packages for people that are on older versions of new. Get this a lot off knowledge that you need to have a library author that I think you shouldn't have. And even now with .Net Standard ideally, you'd just be able to build packages for a .Net Standard. But that's not necessarily always the case because the .Net core is moving along faster than .Net standard.

So you might quite often have to build on that core specific packages as well. And so this makes sense to me or to any .Net developer but somebody who comes in blank wants to do .Net and then is faced with packaging the project. It's a bit daunting, I would say. Still, and even for me, as somebody who's had a NuGet package for I think eight or nine years. Now it's It's still it's a bit of a hassle to keep up with us. Well, to know exactly what the pitfalls are with packaging project and being on the bleeding edge, you cannot complain. Obviously the next tooling had had rough edges and the court ruling had rough edges, but

#### Martijn

in the end it's all been worth it. And if you're on the bleeding edge and you get cut, I don't think you should be standing on the soapbox and starts shouting that something is rough. That's what you signed up for. If you're on the bleeding edge and like I said, the place where we are right now, we think that it's just any kind of hassle has been worth it.

#### Jamie

I tend to agree with either. Although I have created a number of smaller libraries for ASP.Net Core specific. So I think up until 2.1, you could still use them with .Net framework. There was, ah, stepping stone build, I believe, where you can still run ASP.Net Core on top of .Net Framework for a little while. Whilst .Net core 2.1 or 2.2 were still supported to allow people to sort of slowly migrate things over because there's a little bit of work involved, ASP.Net and a ASP.Net Core are two completely different beast, so allowing that support, But I haven't created anything big, and I haven't created a lot of stuff and it hasn't lived for very long. So I can't really comment myself about the tooling of than like I said, the project JSON stuff was a bit rough and like I said, we try not to talk about that.

#### Martijn

Yeah, exactly. I think any horror stories from that scouring for the right versions and combination of first since I think belongs in the past. It's no no years off, digging up old sores like that, especially since it's not actually relevant to this day and age.

#### Jamie

You've done a lot off open source development that I can see. Worked on OmniSharp and iterconfig, a number of different, really high profile things. Like I wouldn't say the OmniSharp is a library, but I feel like it is. The first question is for the folks who don't realize that when they fire up visual studio code for the first time and installs OmniSharp what's actually being installed, what's going on there.

#### Martijn

So, the OmniSharp project is something that Jason Emmerson started because he needed something for VIM out of process. Because VIM script itself is blocking. So if you anything you do that's heavily processed will lock up the editor. So he created OmniSharp. Basically, as an out of process brain, if you will, for .Net.

#### Martijn

And from that the effort And with rustling obviously being released, it became quite easy to take on more editor implementations on the OmniSharp server that Jason Emmerson had built.

#### Martijn

So my involvement with OmniSharp is quite limited and haven't done that much since I initially started the Atom integration just for I was still looking for a nice editor that I could use. And although I do quite like VIM on and I just started playing with Atom. So I just tried it out and see what the integration there look like on a tactical. Created a website And the logo for it and that's about it. But I have to confess. A soon as Rider was released. I gave up development on OmniSharp just because Rider had everything that I wanted and more. Yeah, so the other tool that I've built was editor config against it is an existing effort that I joined where there was already an editor config visual studio looking, and I just joined the open source project to help out and to go for ownership of that.

Then I also created a port off the C++ parser, that was at the heart off the editor config for most implementations, and I did that to actually be able to... Editor Config is basically a file that you can put in your projects and have a common set off conventions for your files. Basically. So files should use tabs or the use spaces. Do you use spaces with a space of two or four and then you can configure that based on file patterns and dictate the convention settings each files should use. And I'm a big proponent of tabs. And that's not the default in .Net. If you open Visual Studio for a New project, you get spaces. So obviously I wanted to encode that. Okay, all the files should be tabs, and I think Editor Config is a great way to do that.

And so that's how I got involved in that project. But and it's just fun to see how things can find a place. So I wrote the Editor Config Core C# Port because Visual Studio  was relying on the C++ DLLs, which were a little bit hard to build, especially a cross platform because they heavily relied on the visual studio make files.

And so I wrote the C# port for that just to be able to have an easier deployment with visual studio plug ins, which are not easy to build in their own right. And then that found its way into the Resharper and Rider And now, every time you open a file in ReSharp or Rider you go through that little thing that I wrote and that is kind of pointing back to the first thing that I mentioned in this podcast is that I debated quite a bit like should I even put it online. Like this isn’t useful to anybody else but me because I have this isolated use case for it, and then it find another use case for it as well. So now I'm super happy that I put it online and actually took the time to package it properly, etcetera. That's just the fun of open source, like you never know who's going to use it, how they're going to use it. And I think that doesn't get old for me.

#### Jamie

That is interesting. This, I don't want to say throwaway idea, but this idea that you had, I mean, I believe GitHub has support for it, too. You know, if you commit, it can make little comments when the GitHub UI as well. So yep, this one idea that you had has been largely adopted by I think you said, Ryder and Visual Studio and all of these tools that almost anyone can use.

#### Martijn

Yeah, I can't claim to have invented the editor config file format, but it's fantastic effort across many different ecosystems and the level of production in tooling and like you say, GitHub has support for it, and any editor nowadays has support for it. So it's amazing to have seen that grown where it's in the beginning that the one of the things I wanted to push to OmniSharp and Roslyn was to actually introduce editor config support. And then, while I was working on the PR for editor config support in Roslyn, I found out that they had already internally built an Editor Config.  Sadly, not using my package, but that's totally fine, like it's it's there like we know we can. Format your C# files completely with Editor Config with support from the compiler. 

#### Jamie

Excellent. See, I guess it just shows that anyone can have an idea. And especially if its open source, anyone can contribute to the idea and make it better.

#### Martijn

Yeah, absolutely enjoying existing efforts as well.

#### Jamie

So what about some of your other .Net tooling that you're working on? Did you want to talk about those?

#### Martijn

Yeah. So part of the reason I'm doing this podcast is to draw attention also to some of the tools that we're hopefully going to release soon, which is the .Net tools. So we're gonna publish a assembly differ project which basically allows you to create a diff between two different packages. Then just easily glance whether they contained breaking changes. So obviously you can use this for many different purposes. One of them would be that in CI or in Pull Requests that you can fail the build if a pull request will start tointegrate breaking changes So that's definitely something that we want to release this month. It's called Assembly Differ, and it's based on just Decompile and just assembly. That's another thing. We created this, tool. And then I created the pull request back to just decompile and just assembly. And now, because of that, I'm in contact with the original author off those two, And we're gonna hopefully work together now to get assembly differ into a state that we both wanted. Basically, what we did was repackage those and making sure that you can pull down NuGet packages and picked the right DLLs from the NuGet package.

And then while speaking with the author that was one of the original intentions off the two dlls JustDecompile and JustAssembly but they just never got around to actually finishing that part of the two amazing libraries.

Yeah, he was quite happy to see that actually taking shape. And now we're kind of hopefully working together to finish that off this month to release so again.You do stuff out in the open and get in contact with the quite amazing people like that. And the other tool that we're gonna release this assembly rewriter which allows you to rewrite DLLs to internalize DLLs and rewrite their namespaces. This is something that we've used in the .Net client for Elastic Search in the version 6. It was one of, I wouldn’t say The biggest problem we had, but it's one of the most common problems that we had is that we shipped it all that client with the dependency on JSON .Net version 8 and then JSON .Net releases a major new version 9.

And then because we tend to update fast, we also update our package. But even though we probably update maybe a week or two later, we get an issue. The first issue that we get after JSON .Net released their new major version was “Please update your dependency to the latest JSON .Net” It s so we follow along and then we update our NuGet tickets dependency. And then, as soon as we upgraded our dependency to the latest major version, two new tickets would be created, saying “Please downgrade your JSON .Net. major dependency because we're not ready to go ahead to JSON .Net 9 yet.

So with the tool assembly rewriter that we have there is basically allowed us to internalize JSON .Net into our own DLL and rewrite its namespace. So it would be, I don't know. I think we rewrote it to Elastic.JSON.Net or something like that. So and internalize all of those types so we could actually still use JSON.net, but package it in such a way that is completely hidden to our users. So we don't have the NuGet package dependency on JSON.Net anymore. That's a tool that we've used for. I think two years and very keen to get out there could be useful to other library authors as well.

And the last one that we want to release is something that we've used for years and has saved our butt quite a few times it's an assembly validater where gold NuGet pack or in the olden days, NuGet.exit pack and then you get these NuGet packages, but then these NuGet packages as just DLLs and they're signed and they contained version numbers. How are you certain that they contained to right version numbers and they are signed with the right key.

So we have this tool that basically unpacks NuGet packages and in first inspects DLLs to say, OK, is this actually signed? Are we gonna publish this NuGet package with the signature that were basically the assembly identity that we expect to publish with. And so I'm very much looking forward to getting these three little .Net tools out there so that they get a bit more wider use as well.

#### Jamie

What I want to say about these is they seem very useful in the last one that we talked about the assembly differ on the assembly validator. I don't want pressure everyone to using them, but they or something like them should be used in everyone. See, I see the pipeline, right, Because otherwise, how do you know that the assemblies you’re loading in have not been tampered with?

#### Martijn

Yeah, exactly. Or it's quite easy to forget to built in, release mode or build a DLLs with the wrong version.

#### Jamie

What maybe using an old signing key or something?

#### Martijn

Exactly. Yeah.

#### Jamie

And I must say I have come across an issue where I would have loved to have use assembly rewriter. There was a few years ago. I was working on a project. The team that I was only built this project for a year or so. We needed some new functionality, and one of the members of the team went here. There's a NuGet package for that, so I would Okay, I inspect and you get package. It looks good. Fine. Let's pull it into the project, and I'll do a spike, do some work in progress from some experiments to see if I can get it working on. I couldn't because they'd use the same name space that we had. So we got all these names, space collisions somewhere. And he couldn't pull in this code and that code because do you mean this name space over here or that name space over there? And we'd used British English spellings and the NuGet author used American spelling. So there was a zed in there somewhere, so that helped, but not for a human reader. If you're looking through in your right gets away.

Somebody misspelled our internal name space. Do we need to go  and change that? No we just we've unfortunately had to pull this package, which has the same namespace.

Now this was open source so we could have just forked the code renamed the namespaces and. Put in a little notice inside app “This uses issues is a forked, an altered version off the software.” We told that to legal and they effectively pulled the hair out and said, No, you can't do that.

#### Martijn

That's crazy. I apologize because these tools, like wrote I mentioned earlier, I wish people would throw things over the wall earlier and see what sticks and I completely did not heed my own dogma where the stores have been lingering for way too long and, you know, hopefully like yourself. They like they will, they will find a use case and somebody's CI pipelines as well.

#### Jamie

Yeah are these open source tools? Are they close source tools.

#### Martijn

They're open source. They're currently under a GitHub organization. I’ll provided links towards them.

#### Jamie

Yeah, sure. I can get the links to those.

#### Martijn

Yeah, they're not on NuGet.org yet, But that's what I'm hoping to accomplish this month, for sure.

#### Jamie

And do you take requests for these? So if someone looks at and goes, Oh, I could change this, are spotted an issue and and and I can fix it?

#### Martijn

Absolutely. Yes. Oh, thank you for raising that. I welcome everybody to hammer away on those. Absolutely,

#### Jamie

They're open source. But the free to use because obviously there's a difference between open source software and free open source software isn't, you know. So can I just pull down the code, hit compile. Pull down an .exe or something and throw it at my CSC pipeline and not have to worry your? Is there some kind of licensing?

#### Martijn

No everything is tool licensed, so they're free and open source tools.

#### Jamie

Okay, so there's there's really no argument for not using that.

#### Martijn

No, it's true that it's a good segue back to Elastic and maybe because something I haven't mentioned with Elastic Search is that it's also open source completely free to use. But we do have a licensed proprietary version as well, where some features and Elastic Search would require for you to have the license. But with that set, Elastic Search itself is open. Even the proprietary features are on GetHub, but to actually use them. You will need appropriate license for them, and so they sometimes create some a little bit of confusion because the default distribution that you download Elastic Search might have this proprietary bits in. Even now, they don't necessarily get activated if you don't have to right license.

#### Martijn

And so we also realize if that's a concern, we also ship a completely open-source distribution as well. That doesn't contain any of those proprietary bits

#### Jamie

that's incredibly useful to know. Yeah, because on the one hand we'll have to make a little money to pay our bills and make sure that we eat. But it's also nice to know there's a free to use open source version of the tool that I could sort of dip my toes in. And if it sounds like I'm going to use the proprietary features that yeah, I could fling some money towards yourselves and pay for the the license for those proprietary parts of the system must oppose.

#### Martijn

Absolutely. And so I encourage everybody to check out Elastic Search as well because It's such a a great tool. And even the Open source version contains so many great features that I would say, like the features that typically get pushed into the paid versions are enterprise features. So if you're for looking to really write something, ah, if you want to do something functionally with a less secure is typically it will be available in the open source or basic versions of less exert.

#### Jamie

So if I wouldn't have learned about last except try and go to visit elasticsearch.co, is that the best place to find out?

#### Martijn

That's a perfect starting point to start your Elastic journey.

#### Jamie

Okay. And what about these tools that you've mentioned? Is there a website for those? Where is it? Just check out GitHub for now. Yeah, the plans to be a website.

#### Martijn

There won't be a website for those. There will just be a GitHub. But they're they're all under a common organization called which a link will be provided as well.

#### Jamie

Sure. Yeah. I'll make sure to put this in the show notes. I mean, we've talked a lot about open source, right? So what are your main reasons, I guess, for being in open source development because you know, there's a lot off. A lot of people have turned off by it because if it's open source than it's free, then I can't make any money. But you seem to be very excited about making stuff open source for people to use. What's your top? Maybe two or three reasons for doing that?

#### Martijn

They’re completely selfish reasons. 

A. You do meet a lot of fantastic people just by putting yourself out there or your coat out there, which I don't know which one of the two is scarier.

But you do meet a lot of really nice people and the way I started in open sources before get up before

and if those sites were available doors I started. He started scripting in MIRC, which is like a chat program for Windows, and it came with this little scripting engine and around it. Amazingly, there was a big community that formed around it and at multiple sites to do with publishing scripts and showing screenshots about what you did, and people would reply to it. He would get feedback and they would say, Have you tried doing something differently? If you do it this way, it's gonna be faster. So for me and I was also like, accelerated learning for me as well, where it's like I learned about regular expressions and DLLs and calm and all these different things that the normal, like 13 year old, would never actually have find just because you were talking to the right people online. And I think that promise for open source is still there, and especially nowadays when you have GitHub and others as well. Where getting feedback on  projects from others. It's not always gonna be nice and friendly, but it's going to get from former feedback. I think it's kept me going as well.

#### Jamie

so folks should be definitely checking out your open source projects, even if its assembly rewrite or assembly differ. Assembly validator. But it should also definitely check out Elastic Search.

#### Martijn

Yeah, exactly. The Rider .Net team within Elastic are also working on and have shipped already a .Net APM agent that allows you to monitor a running application so you can visualize how well your application is performing inside of a Elastic Surgeon And Kibana. So definitely check that out as well. And we're going to start shipping a lot off more integrations with the common schema out that I mentioned earlier as well. For the stack were gonna ship with log formatters that emit log messages in ECS format and allow you to ship that data into less crew. It's easier as well. That's all open source as well. Hopefully we can provide a link at the end of this round, but guests as well for those

#### Jamie

You're definitely check through the show notes for some links. So then it seems, is there are a lot of your work, at least at the moment, is going into I hate to use the term because people are gonna think is a job title but DevOps type stuff. The CI/CD stuff platform monitoring, getting logs, All that kind of stuff is he was very DevOps. Is this something that you would recommend everyone look into Or is it more a case of? You know, me and my friends or my colleagues of building these tools so you don't have to miss that. Which which way around Is that what you say?

#### Martijn

Oh, I I think I think it's both of both. Definitely like the APM agent for Elastic APM agent for .Net. It's easy to install if you run it and you have a running Elastic Search instance or APM server to point to.
It really takes a lot of the work out of your hands so you can start monitoring your SQL queries, How well your controllers Are performing. Oh, and more integrations definitely to follow there. And so but a lot of this is definitely geared toward devOps stuff.

#### Jamie

Working folks go to find out a lot more right? You like, What's the best way to find out about Martijn’s work. what you're getting on with the project. You're working on that kind of stuff. Where's the best place to find that

#### Martijn

I guess I’m on Twitter for you to follow me, so I put myself out there not too much for him for myself. More so for the project. So I don't really have a landing page or like ah, even my blog post. I think the last blog post I wrote was four years ago - Five years ago.

#### Jamie
Okay, Perfectly valid dancer, you know, but okay, so in that case, where do we want to go? If I want to learn about all the different projects, then so Elastic the APM. Stuff for Elastic, Kibana like other stuff the assembly rewrites and all that kind of stuff. Is there, there won't be one commonplace, But is it like Elastic.co and GitHub. So if I got is not the best best way to do it?

#### Martijn

Yeah, exactly. So for .Nets specific integration, there isn’t a single landing page from the elastic site, which is actually a great idea that I should circle internally as well. But the different integrations exists as part of different products. And so the information for the actual innovations will be part of the product pages on the elastic.co site.

#### Martijn

Definitely check those out on. And for the tooling, everything is on GitHub as well which is part of the Nolean organization on GitHub.

#### Jamie

What I'll do is I'll make sure to collect the whole budget links from you, and I'll put them in the show notes. So yeah, whatever you're listening to this episode on, make sure you click through school down to the bottom and all of those things will be there and you'll be able to Click through and learn about Elastic and all the different things Elastic can do and all the assembly rewriters, the Differs and validators and things. Like we used a lot off acronyms and technical terms that some folks may not know about, so I'll make sure to put some links to some of those in there as well. In case you don't know what the TFM, which is a target framework moniker is or you don't know what application monitoring is that kind of thing. I'll put some links in that just to sort of help with providing some of the background information.

#### Martijn

Perfect. Thank you very much,

#### Jamie

All that remains to say is a checkout Martijn's open source stuff. Definitely check the links in the show notes to get those and thank you ever so much more time for taking the time out to talk to me. I have really, honestly enjoyed it, and I've learned so much more about open source stuff. DevOps things and a little bit more about how my editors of choice work. It's ah, absolutely wonderful. Thank you ever so much

#### Martijn
Thanks.

#### Jamie

Thank you.

### Wrapping Up

That was my interview with Martijn Laarman. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show), and there will be a link directly to them in your podcatcher.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice - head over to [dotnetcore.show/subscribe](/subscribe) for ways to do that - and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Martijn Laarman on twitter](https://twitter.com/Mpdreamz)
- [Elasticsearch](https://www.elastic.co/)
- [What is Elasticsearch?](https://www.youtube.com/watch?v=sKnkQSec1U0)
