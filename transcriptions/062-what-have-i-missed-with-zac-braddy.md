### Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is Episode 65: What Have I Missed With Zac Braddy. In this episode Zac actually interviewed me about some of the things that he might have missed in the past few years of .NET innovation. Zac is a full stack JavaScript developer these days, but started in .NET Framework. We talked about some of the innovations brought about by .NET 5, and whether the CLI tooling for .NET allows developers to work in VIM or EMACS - something that he is really quite interested in.

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

{{< paracentre "The following is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

#### Jamie

So first thing I want to say that before you take over is, thanks for spending some time this evening with me. And it's, it's though that I feel like it is the hottest evening ever. Right? I feel like I've been sitting on the surface of the sun. And this never happens in the UK. I'm not complaining. Because I've noticed the first thing that happens when people complain about the weather is it then is miserable for the rest of the decade. So I'm not complaining about the weather, I

#### Zac

need to make that very clear. There's so many ways that I could describe how hot it is in Australia, and but none of them would allow your podcast to appear on most podcasters if I did, so I'll just say it's really hot.

#### Jamie

There's no particularly podsafe is it? Now? Fair enough, fair enough. Okay, so Zach, for the for the people listening, Zach and I, and fellow podcaster, James, the cynical developer, stood out, create a show called tappings basis. And we decided that we would do an episode of The dotnet core show together. And if you're listening to this, you will more than likely like the tabs and spaces. And we'll talk about that in a minute. But before we do any of that, Zach, would you mind kind of introducing yourself? Let the listeners know a little bit about you?

#### Zac

Yeah, absolutely. What I would say as well is if you don't like this episode, you'll probably still like [tabs and spaces](https://tabsandspaces.io/) as well. So regardless of what happens right now, yeah, let's let's let's also give some space to try. So, yeah, I am currently a JavaScript developer, full stack, I work at a place called [Koodoo](https://koodoo.io/) in a sentence, we're trying to help people save money on their mortgages, which is a, I feel like it's a bit of a noble cause I like what I like being able to help the every person to get to get somewhere. And prior to me working at at Koodoo, I was a dotnet developer, I was a dotnet developer for probably, I mean, who was counting about five or six years beforehand. And I've done you know, things, I've done things in a number of different industries. You know, white labelling, you know, when you when you've got, like, supermarkets whose jobs, it is not to, you know, they've got all those like home brand sort of things, where it's not their job to manufacture tomato soup, and yet they sell their own brand tomato soup. So the whole thing with the white labelling is that, you know, it links up manufacturers with, with with those supermarkets and tell you what, I'm not going to explain every industry that I've worked in, I've just worked in a lot of them. Yeah. Mainly because of, you know, throughout my career, I've I've hopped job, job to job and that's allowed me to have a fairly broad experience across a number of different industries. And, and now a number of different well, core languages as well. So it's been exciting, I've had a lot of fun.

#### Jamie

Awesome. Yeah, I can, I can totally attest to working in different industries being I don't know whether better is the right word, but having that experience of working on the other side of the software, using the software, and then taking that to your own or making the software, you know, one of the things I always say to people is, Hey, you know, it's its primary gifting period is it's Christmas, the end of the year, try to see what it feels like for the people who are working in the shops, we get it, you want to buy this thing you've waited till the last minute, but it's not therefore, right. And I honestly think that everyone in the country can deal with, they would be made better if they had three or four days of working in retail experience to just understand what it's like. And I think using the salt, using the software that we're making, makes you a better person, right? And being in that position where you know, those problems, or even just have a little experience of those problems makes you a better developer.

#### Zac

Yeah, I mean, empathy is a is a good skill for life, not just development. But but but yeah, as you say, working in lots of different industries, and finding lots of different problems that you're trying to solve for people because you need to not lose sight of that fact, when you're building software. Right? Ultimately, you're out there trying to make someone's life easier. And I can work both ways, which is also why there's some industries or refuse to work in, maybe that's a story for another time. But, but that, you know, it requires a certain level of empathy in order to be able to do well at solving the problems of your domain, in each in each industry that you're working in. And I think that helps you learn exactly what you're saying, you know, like, you know, being able to put yourself in the shoes of different people.

#### Jamie

Absolutely, absolutely. And like I say, yeah, figuring out empathy, raise a hell of a drug. Being able to say it Like, instead of just saying the words, I totally understand the problem you're having, actually being able to put yourself in those shoes, right? And say, Yes, I get the problem you're having because I've suffered with it too. Let's figure it out together, let's solve this problem together. Because at the end of the day, that's what we do. as developers, we solve problems. We provide solutions to the problems we don't. Yes, we use, we build software to do that. But I think I've said it in an earlier episode, that isn't out at the time that we're recording this. We're literally said to clients, you know, I could build the software. But have you tried to excel fast? Yeah.

#### Zac

Yeah, absolutely. Yeah. So I mean, this is turning quickly into a tabs and spaces episode. And I'm cool with it. I'm cool with it.

#### Jamie

You know, forget the sound effects.

#### Zac

Yeah. Awesome.

#### Jamie

Okay. So with all of that said, right, we're actually going to hopefully do is because Zach's been out of the dotnet world for a while, we're going to turn the tables in a minute. And he's going to basically talk to me about what's so great about dotnet these days, compared to what was good or not so good about dotnet in the past, for a little bit of insider baseball, Zack has provided some questions. And I have basically written out the answers in bullet point form. I'm not gonna sit and read them, but they are like notes, kind of like a wood slide, right? So I do know the questions going in, which is something that he's always good to do for podcast he things is to know most of the questions going in. Now, the problem is, I've said that Zack, I'm sure he's gonna throw some curveballs and really, completely destroy everything I've just played.

#### Zac

I'm rubbing my hands together right now, this is gonna be fun. Now. I'm gonna get Google and every time you every time you answer a question, we should probably give you a score at the end to make it really stressful. Yeah, let's

#### Jamie

do a score. Let's do it's gonna have to come up with a rating system first, right? I think that's right about just completely going off topic, whether this is the shows or read magazines or whatever, they give a rating, right? It's like eight out of 10. And then like eight out of 10. What? And what is the mean, if you give everything an eight, and that's literally a five, right? But then if it's a five, it's just sorry, ran over,

#### Zac

someone should run an app for that.

#### Jamie

normalise all of your ratings.

#### Zac

So Jamie, welcome to the dotnet core podcast. It's nice. Nice to have you on tonight. I've been waiting to have you onto the dotnet core podcast for some time. Now. It's, you wouldn't believe the number of people who've said to me, You need to take Jamie on the dotnet core podcast. So it's great to have you. Now, I left, I left the dotnet space probably about about two years ago now. So very early dotnet core days. So my knowledge of it is is fairly limited. And the knowledge that I do have, or at least the experience that I do have in dotnet core was of a very hazy and frustrating time in dotnet, cause life. So first of all, the burning question that I've had in the back of my mind is whatever happened with that cs proj, like, effectively package JSON stuff, right? Because I liked the JSON, I thought that was really great. And I didn't like the fact that it went back to the Cs proj. So what happened there? Why, why do you think they went back to CS proj? Or have they published why they went back that way? What's going on there?

#### Jamie

Yeah, so for the people that don't know, pre v one and v one, up to about just before v2 of Turner, v 1.1. They dropped it. So very early days, dotnet core, instead of using a CS proj file, or an Fs proj file, or I don't know how you do VBA, I guess VB approach. But instead of having a project file, which is all XML, where you had to explicitly list all of the files that you wanted to compile and having all sorts of different feature flags, and all that kind of stuff. That'd be more of that. They did away with that. And you had a JSON file that just said, Here are the dependencies, go build the thing, right? Wouldn't you don't list any of the files to compile or anything like that? greatly simplified everything, and everybody went brilliant, because we actually hate XML, because everybody hates XML, right? Unless, of course, you're building some kind of enterprise level application and you're paid by the line of code that you wrote, then, yeah, everyone hates XML. Even the people who designed XML I'm sure, hey, XML.

#### Zac

Yeah, we hate like, we hate blanket statements at the dotnet core podcast.

#### Jamie

Exactly. So JSON, simplified everything. Let's do everything with a project JSON, which just lists the libraries you rely on and how basically which thing a couple of things to do with how you're going to build it but not all of the files and That was great because at the time, they were they were building the dotnet core tooling to match as much as they could, the sort of the available node tooling, and like the angular tooling and stuff like that, let's use JSON and whatever we can everywhere, because JSON is kind of like an industry standard, right. And then, of course, somebody came along and said, but if dotnet core is going into the future, that means that you're gonna have to build two different versions of MS built. So Ms build is the tool that you that Visual Studio uses behind the scenes that their dotnet core compiler uses behind the scenes, the dotnet compiler is behind the scenes to build everything up. And they thought, well, we don't have to make two versions of everything because everything's got to be backwards compatible, right? Microsoft's big thing is backwards compatibility. There are apps that were written for Windows 3.1, that still have to run in the windows 10 world. And so there's all sorts of hacks in the windows codebase. And in the kernel that actually makes these things run. So we're gonna have to do, we're gonna have to support it. But if we have to support it, then that means we've got to make ms build more complicated, and that's going to be difficult to do. And, you know, I don't know whether you've ever built a compiler, but I didn't like building compilers, because languages are hard, right? And parsing files based on file name and file contents, it all gets a bit wobbly. So well, they ended up doing in the version 1.1 timeframe for the SDK and the runtime, they scrapped project JSON, wrote a little migration tool, and actually went back to CS proj, but greatly simplified it. So now it just lists some metadata about your product, maybe the name, version number, a couple of builds, build time tools, and then it lists all of your dependencies. And that's it. None of this, compile this file, and this file and this file and this file. There is actually an episode where where, Nick river, the episode of this podcast, right, where Nick crevices, that cs proj files are built for merge conflicts. And he's absolutely right, the original ones were built for merge conflicts, it always seems to happen around a very specific set of lines. But yeah, I think it was a was a step. The whole thing was a step in the right direction. We've got a simplified cs proj. They try it out project JSON, you can't blame them for trying, right? You can't ever go with someone who say we tried something, and it wasn't going to work. But at least you're trying right because it led to this

#### Zac

simplification. So you being you can't have taken away my favourite thing though. My favourite my favourite thing was the fact that they are finally doing everything in JSON, and they just took it away. I was like this is it's like everything that what I liked about it was the fact that it sort of it made things like it brought things together, you know what I mean? Like, because the when, when we first started toying with dotnet core, I was in a house that had a myrn stack, and not a moon stacker, but it was a it was a mer with dot mored stack. Like, we thought we had dotnet in the back in the back end. But we had like, you know, all the actually wasn't expressed was it? I've been in JavaScript too long, we had a dotnet back end with a react front end, is what happened, right. And so you know, our stack kind of like it for a little while there. It was, like, everything kind of made, like it all felt comfortable. It was all. It all kind of acted the same. And then when the Cs proj files came back, it was like, No, but if what you're saying is that it got simplified? Well, and, you know, I guess I guess that's a step in the right direction. In terms of the backwards compatibility, you know, I think that's probably why I'm glad that I work in startups. You know, because all that backwards, because because the first thing that comes to my mind is is what, why, why make it so far backwards compatible? That's that, you know, how do you do anything good, if you have to, if you have to continue fighting the ghost of badness past? You know, it's, I don't want to have to deal with that sort of stuff. And I don't have to. But I guess at an enterprise level, I can see why that would be horrifying to think that, you know, your your application would go out of style every two years.

#### Jamie

I definitely Yeah. It's it's something that may actually become a problem moving forward when they move to dotnet five, which I guess we can talk about later. It's going to be a rolling, two year long term release. So five is the short term release. Six is the long term release. Seven is the short term is the long term. So I get the feeling it's very JavaScript T and the way that they're doing it, you know, with a lot like the angular and react of the world, the different version numbers tend to be this is long term, not short term. This is long term, not short term. Which makes sense because like an LTS cycle, right? Yeah, yeah.

#### Zac

Yeah. The and that's the thing, right? Is that Microsoft This so I'm going to use a big word duplicitous is that is? I'm not I'm not sure if that describes that, I'm gonna have to Google that later and find out whether it was smart or not. Like duplicitous in nature, I'm I'm rolling with it, in the sense that on one hand, they'll say, Oh, yeah, we need long lasting support for all the stuff that we build. But then I basically goes out of style every time they do a new version. But also, Microsoft v ones have have a spotted past. You know, in terms of saying, and that was one thing that I was dealing with, when I was leaving the dotnet space was there was a lot of people who are going, should we go with dotnet core, because I'm not sure how much it's going to change. I'm not sure whether I'm going to write a whole thing, and then have to rewrite a whole thing next year. So that still very much exists in that in that space. And so how is that now with dotnet? core? Is it? Like, can I write an enterprise app and dotnet core now, I guess, is the shorter

#### Jamie

question. Oh, most definitely. I have always said, if you're doing something important, like an enterprise level app, wait for version two, because no matter what you're doing, everything is going to be wobbly until version two comes out. And that's not that's not a shorter Microsoft, because the same thing happens like you look at Angular, right? AngularJS, you could argue that over Angular j s v one existed for a long time, he was awfully wobbly. And then Angular two came out, and that was a little bit less warbly. And we've slowly moved towards less and less warbly. But then, I guess you could probably say the same with react, because I never, I've only ever used like, feel a test of react. So I don't know what the early days were like, but if the early days of everything, you're going to be a bit wobbly. Right?

#### Zac

Yeah, I mean, we will disagree about the difference between Angular one and two, two was stank out loud. You know, like, you could you could hear how bad that was. But ya know, that the Feed the Future versions of it were a lot better. But yeah, two, two was reaching to As of version two was a version one of something new. I think that's why it kind of what it was not as good as Angular one. But anyway,

#### Jamie

if you compare Angular two in that instance, then compare Angular two to Angular three. Yeah. Because they skipped three and they skipped, I guess,

#### Zac

I think I think I skipped four. I don't know. But I yeah, I'm not an Angular developer.

#### Jamie

Yeah, I do know that they skipped one version, because they wanted to keep all of their everything in line, everything is version two, until version three comes out. And then everything becomes a version three. But someone had accidentally upgraded one of the libraries to version three, or version four, or whatever. And they had to skip an entire version to bring everything into line, which is hilarious. To others, you know, open source. So

#### Zac

there's heaps of stories like that the the in Angular one, they released Angular two as a beta. But then Angular one was still in, like widespread support. So whilst they were building to, they had no, they weren't able to release major versions. Because if they released them, like, you know, it would end up being Angular two, right. And so there was, I'm not sure if there was there might have been two. There was definitely one because we got standby. It was there was a it was a minor version upgrade in Angular one. That was actually a breaking change. And we got we got caught by the break whilst we're in the middle of building something. Because NPM didn't care. It was just like, Yeah, well, it's not breaking. So whatever. It was, it was a real nightmare.

#### Jamie

I mean, the thing to take away from this is not that Angular is bad, or dotnet. Core is bad, or anything like that. It's just software is hard. Right? versioning software is even harder, you know, leave that to the geniuses to figure out.

#### Zac

Yeah, absolutely. So I am a vim on I'm slowly working my way towards Emacs at the moment, which is an exciting new horizon for me to go down. But I've been a vim user for a number of years at this point. And one of the biggest sort of like things about being a dotnet developer who is also a vim user is there is half of your stack that you can count. I mean, I could use vim there was a vim plugin for Visual Studio that I hated because it didn't do everything that vim did. But you know, there wasn't, there wasn't a lot of options for a vim user out there. Now that dotnet core is like, I mean, the one of the big things about dotnet core is that it's cross platform. You know, anyone can develop anything. Anytime with a on a dotnet stack? How do you know how like, how much more support there are? Do I have to be in Visual Studio? And if I am in Visual Studio? Am I able to make it more comfortable for me? Well,

#### Jamie

I can't really talk for Visual Studio because I haven't used it in like two years. So, yeah, I know that it's gotten slightly better. 2019 was supposed to be better than 2017. But it's still a huge monolithic app, right. And it's still very slow. And it's still single threaded, and it's still a 32 bit app, which means you know, it's very slow. And then if you instal resharper, or something like that, a bunch of plugins on top of it, it gets even slower. So, yeah, it's, it's, it's like, the Swiss Army Knife of development tools, right? It does a billion at one things that you will never need. But they're there, right? So it's like, on the one hand, it's Ace, because it has all of these tools, you you never gonna need another hand, you never gonna need them. So it's like a,

#### Zac

it's the Swiss Army. It's a Swiss Army knife that doesn't have the tool you actually need at any point as well, that's resharper. Yeah, Swiss Army knife that needs a Swiss Army knife on the side of it to make it usable.

#### Jamie

That's the interesting thing is that Visual Studio has slowly been integrating resharper like features into like the Visual Studio Team of short, slowly been integrating these features, like they easy Find and Replace the refactoring tools, all of the squigglies for the suggestions and stuff I got. But yeah, I've not used Visual Studio in a very long time. My daily driver is actually a Linux distro, and I develop all of my stuff on this Linux distro. When I have to use Windows, maybe I'm working with a client that requires me to use Windows. I'll do that. But I'm still not using Visual Studio, right? You know, I flip between vs. code and writer and vs. Code. People say there's an ID, but it's essentially just a text editor. Right? So it's kind of it's not really one or the other.

#### Zac

You're the majority of so the majority of the stuff that I like the plugins and stuff that I use for the vim and all that are actually like vim script over the top of VS code plugins. So sounds like sounds like I might actually be able to make a decent Cova these days?

#### Jamie

Oh, definitely. You know, it's, it's, so a lot of time was actually spent on the dotnet core tooling, rather than so there's only go see ally tooling and the that kind of side of things rather than integrated with Visual Studio. And that was largely because, you know, for one of a better phrase, Microsoft wanted all of the Linux and Mac OS users to try out to jump ship to come over to the dark side, try and use our thing, right. And Linux uses Mac OS developers tend to tend to like the CI tools a lot more than the visual tools. For one reason or another, right? You're going to spend $1,000 on a computer, you're not going to use the user interface It comes with you can use the terminal, but they whatever, right. So yeah, they spent loads of time and effort on the CI tools. And so yeah, there are things like one of my favourite ones is this ci tool called dotnet. Watch, which will just watch your source code, and when you save, it will rebuild, which is really useful, or it can run your tests. So you hit save, and it just instantly runs all of your unit tests, integration tests, that kind of thing. And you could potentially pair that up with them. I'm not brave enough yet to have used them or even Emacs or any of these, these wonderful tools. I don't want to say old school, but wonderful tools. One day, one day.

#### Zac

Well, Emacs is newer. But yeah, it's, I try not to be too jaded when I think about Microsoft, because they like, they seem to have fought open source for so long. And then it's it almost feels like they're grudgingly you know, embrace it. You know what I mean? It's like, Oh, well, if all you guys are just gonna keep on doing your open source, then then I guess we'll have to come and play, you know. And you can, you can see that it actually in resharper, because I've spoken with one of the guys from resharper at a meet up one time. And he was actually saying that the majority of the slow stuff that happens in resharper, is because the the studio engine that they're trying like the API that they're trying to integrate with, is just so slow and doesn't get any looking into because they know that that's what resharper uses to do its stuff. And so rather than being like, Hey, resharper is doing some great work out there, you know, like in the, you know, helping our developers out. Why don't we work on that API that is slowing their software down? We can make this software faster. Our developers will be happier, you know, on and on. It goes into like, No, no, no, I will tell you what we'll do. We'll take all the good ideas they had and we'll put them in Visual Studio native. So that way, you know we've got it and you know, whatever to resharper So that whole experience really sort of jaded me, I think I'm, I'm now really spent trying to spend a lot of effort to undo, like, you know, companies can change, right. You know, like the it seems like some of the moves they're doing with with GitHub and stuff are better, I hope they do good, good work with NPM. You know, so,

#### Jamie

I mean, there's a, there's a quote from, so I added that hand, right. So I don't know how true this is. But I would have to name drop a couple of times to get this out. But there fell hack once told me that Scott hanselman, once told him that Microsoft is like an oil tanker, when it comes to open source, it's turning, but it's gonna take a while. And I can totally understand that if that's the case, because the majority, who I was talking to someone today where I say, you know, it doesn't matter what operating system you use, or what tools you use, because it's all the same. Now, as long as you're using your language, all of these tools and operating systems, it doesn't really matter. That's the whole point of like containerization, and stuff like that, because it doesn't matter what your underlying operating system is that your app is running on. Because you can throw in this container, which will give you a known state to start from, right and, you know, Microsoft, at the end of the day, they just want developers to use as your because that's where the money is, from now on that's where the money is, is hosting and, and cloud and all of these wonderful technologies doesn't matter how you build your app, you build your app, do your thing, but hosted with, with Microsoft or with Google, and they'll be happy with you because you're paying the most money, right?

#### Zac

Yeah, I mean, but that's just that's just the thing, though, isn't it? It's like, you know, Microsoft have a history of of not wanting you to use like, yeah, you can do this good thing, but it's got to have a Microsoft sticker on the front, you know what I mean? Like it with with the whole thing with?

Unknown Speaker  
Oh,

#### Zac

enterprise service bus, was that the thing? And like, that was already like a patent that was out there. And the guys at in service buffalo bus, we're already doing an open source version, but then our users, users users, and it was garbage. It was no, it was not good. And instead, what they you know, I mean, they've got so much money in so much sway, what they could have done is said, you know, hey, let's let's work together, you know, let's make something really cool together. And, you know, we can negotiate some form of, I mean, I don't know how the money works, but you know, it's, I feel like they're slowly starting to get towards that. Now. I feel like they're slowly starting to be like, yeah, the the, the outcome is kind of what's important. And if we get a really good outcome, and people were happy with that outcome, then we can try and monetize that as we go. But the the only monetization model needs not to be, we'll use our stuff and nothing else. And that's where Apple started fall apart as well. Right? You know, that's, that's the I've said for years, that Apple is headed for a big fall, because they won't play nicely with anyone else. You know, they insist on being this behemoth. And, you know, if you just sit there rattling away, it's, you know, you can only you can only burn so many bridges before, people are just going to be like, you know, what, I don't want to pay two grand or two to 2000 pounds for a substandard hardware, for substandard hardware with great software. You know, I can't be bothered with that anymore. I'm just gonna go do something else. You know, anyway, we're way off topic at this point. And yeah, so I mean, I'm not sure how you normally run the dotnet core podcast, Jamie, but how I run it is a tight ship. And we must take back back on dotnet core, because that is what your listeners came here for. So. So yeah, well, my next question was that, you know, as everything is, like, Holy Cross platform now, can a dotnet developer work comfortably in Linux? It sounds like you kind of already answered that question right? Earlier, you are already working on a Linux distro, right?

#### Jamie

Yeah, the one thing that I can't do is Windows specific stuffs like winforms BPF, that kind of stuff. or working with like Windows Authentication. For that I just drop out to my Windows machine or you know, fire up a VM and do it in that, or I have actually in the past, fire up a VM in Azure, or, you know, insert your cloud provider here, fire up a VM instal the tools, do the 20 minutes worth of work, and then destroy the VM and carry on right because it doesn't really matter. And it's cheap enough just to fire one up and spin up and spin it back down again, as long as you actually shut it down and turn it off. Then you may not get charged for it. But yeah, my my daily driver is a pop OS which is based on a boon to and I chose that one because it comes with all of the steam stuff and Vulcan and proton and all this kind of stuff for Video games already installed, so I'd have to do anything.

#### Zac

But also it's like a Windows box because I've been asked the only reason I have a Windows box in my in my house is gaming.

#### Jamie

Yeah, yeah, pretty much a side note that's not really related to the content of the podcast. There's nothing on my Steam account that I haven't been able to run it on my Linux machine on this proper West Linux machine. Wow. Yeah. And that includes like, the recent remake of resin, evil two and all that kind of stuff. It just, it just works. The folks over Valve are very smart in what they're whenever they've done whatever magic wizardry, they've done. He just works right?

#### Zac

As I pop over sustainers. Right. Now, so

#### Jamie

yeah, so pop OS is made by system 76, who make a lot of Linux hardware. And it's based on a boon to, but it has everything enabled from instal to allow you to do like the steam and proton and Vulcan all kind of stuff. Because you need proton to do the windows stuff and Vulcan to do very, very fast UI stuff. And even has a video drivers already installed because Nvidia drivers are difficult on on Linux. So that's already all set up for you out of the box, which is just genius.

#### Zac

Yeah, absolutely. Well, I mean, speaking of stuff that isn't dotnet core, as we have been for the last half an hour. Tell me. WTF is blazer.

#### Jamie

Okay. So the short answer I always give to this is, imagine a world where you don't have to use JavaScript. Now I know I'm already scaring you, right? Because you're a JavaScript, full stack developer. But imagine a world where you don't have to do don't JavaScript to run stuff in the browser. I mean, you can already do that anyway, you can run. I think there's a way to run Python in the browser and Pearl in the browser. But imagine, right, you can run dotnet inside the browser. And it doesn't take forever to start. And that's essentially what it is, right? There's this. There's this new app? Well, new in there. It's been around for like three or four years. There's new technology that's baked into all of the browsers called webassembly, which is a way of creating bytecode for browsers, right? Because the way I always say is JavaScript was was invented over 10 days and was used specifically for moving and manipulating text on a page. It wasn't really meant,

#### Zac

hang on, what were all the things in the browser? Whoa, okay. I'm not going to be responsible for this being perpetuated, right? Yes, it was created in 10 days, many, many, many years ago, and has now been iterated on by a group of peer LED, you know, a peer led committee to become the to become the language it is today. Okay. So we're not talking no one's programming on that language from 20 odd years ago, no one's doing that, then no more no more than we're all developing on, you know, dotnet 1.0, or 0.1?

#### Jamie

Yeah, it was unfair of me to make that comparison. But yeah, imagine, imagine you're not a JavaScript developer, you want to do front end stuff, right? Or you have a huge team of dotnet developers and you want to build a front end. And then suddenly, someone has to go and learn Angular or react or view or svelte or something, right? Well, what if you could just take all of that pre existing knowledge and splat it into the into the front end? Even if it's just temporarily, right? Just get that go in? And then we'll hire someone who can turn that into JavaScript? Right? Because that's the great thing about dotnet. I've always seen it as this rapid application development model. Right? Because, you know, our friend James always calls dotnet pretend programming, excuse me, because it is it's just literally take this chunk of code wire into that chunk of code where into that chunk of code. But you've got your app, alright, the wiring in may take a very long time. But you don't have to write the sockets. You don't have to write IO. You don't have to write time scheduling. It's all pretty much all of the hard bits of actual computer science are taken care of for you. So that's great. But imagine you could do that in the browser. And that's what that's what it does, right? webassembly is this idea of taking, taking this idea of bytecode and putting it into the browser. So then you can write an app in go and have a part of the app in Python and have a part of the app in our No, yeah, dotnet and then another part in JavaScript, you put it all through the same compiler, and it spits out a webassembly binary. That is all it's all. It's all compiled into that web assembly code, right? And that's what blazer is is taking. The browser and razor this templating engine will be used for creating HTML pages on the server and sort of mashing them together. Throwing a cross platform dotnet runtime underneath are called mono, which was the original, originally what was you can think of it as dotnet core beta, but it's not. mono came out in the early 2000s, and was basically a closed a, what's called a blackbox reimplementation of dotnet, based on how the API's worked, and that was created by Miguel de icaza, who is a absolute genius of an engineer. But yeah, this mono runtime, this dotnet runtime is so small, you can load it into the browser over HTTP, or you can go Go get me the DLL, and he comes in, it's like, maybe four megabytes, five megabytes, and just runs, you've got your dotnet, sort of runtime ready, and then your app sits on top of that, you've got dotnet inside of the browser. And that, like I said earlier, and you don't need to worry about all of my people are dotnet people, now we're going to bring in a JavaScript person. And maybe there's going to be some conflicts because of the way that the different technologies work. Or maybe we now need to pivot and all learn, react or learn Angular, and that's not a bad thing. Having to pivot and learn that is just, it will slow your development down. Right.

#### Zac

So, but I mean, we don't live in a world where people don't know JavaScript is full stack developers, right? Like that. No, I'm honestly like, yeah, let's, let's have fun. Let's have an open discourse on this. Like, why why? Like, why is it attractive to stay in the same stack to be able to do all that stuff? Especially when it you saying it costs five megabytes across the wire to make it work? So, so what, like, what's the real driver there other than I don't want to have to retrain my people. Because really, you're gonna have to retrain them in blazer anyway, right? Like, if I don't know blazer, they have to learn it. So So what's up there?

#### Jamie

So So part of it is this idea of sharing the code, right. So your view models that you generate on the server can then be used inside of the browser. So as these actually encode, so that makes it a little simpler. But there's also two hosting models for blazer, there's server side blazer and client side blazer. Now server side blazer, used to be known as razor pages. But you can think of it as essentially ASP. NET MVC, right? You've got a bunch of razor, which is the templating language, C sharp on the dotnet, rather on the server fills in that per request, and then generates the HTML and throws out to the, to the client that's kind of its server side generated pages, right. But the client side, one is where it all gets a bit interesting, right? You've got dotnet code running on the client browser, you got dotnet code running on a, on a server. And when the user hits a button on the client, let's say there's I don't know order pizza button, right? You filled in your form, you've chosen your toppings, you put in your address, and your credit card details, you hit bought a pizza. And in a traditional post, in a traditional MVC app, you need to take all that data, send it off to the server, wait for the response, and then load the response, which would maybe be a different page, or maybe a piece of just Gamla AJAX call. Whereas with blazer, client side, you push a button, it sends the request over and instead of sending the whole page that returns back, the server knows the state of the page in that browser, changes it on on the fly on the server and just sends back literally, the pixels that have changed, right? swap this there for this, they've done a set. So you don't have to actually go anywhere. So you have this real time bi directional communication with the server, and where the client and server can push data to each other over what's called signal at the same time,

#### Zac

is all sorted. Suppose.

#### Jamie

Yeah, it's also space. Yeah.

#### Zac

And so it sounds it sounds like it's kind of like like a like a hosted virtual DOM, you know, like the virtual DOM, as it used to be described in in react where it was kind of like, I've got this version of it. And I've got the rendered version of it. And I only really want to change the parts that have actually changed rather than re rendering the whole page.

#### Jamie

Yeah, that's there's literally there's literally what they call it, they call it the virtual DOM. So right, so there's a copy of the DOM and based on the session ID and based on the connection, and the problem with that, of course, is you need a stable connection. So if you've got people who are going out into the field, either quite literally a field or going into a warehouse or something where they don't have connectivity, that client side blazer is no good.

#### Zac

It's all run through signal. It still helps though, because the if I recall correctly, signal art as like, like a degraded functionality sort of thing where it does HTML long polling, if it can't get sockets, and it tries a whole tries all the different things if I remember correctly, that it tries that no one ever has, but that is chance it is like, well, maybe this will work, you know,

#### Jamie

yeah, right. But then of course, obviously, if your connection is dropped, then you know, I'm gonna have talking about that bi directional, constant communication that that kind of falls over but then as soon as you Reconnect, you've got that bi directional communication, you can just push the button and your report is sent over or He then told to go over here or something. So it's, it's kind of useful in that respect. And, you know, for for the people who some people don't like the the duck typing, right? Some people like static typing. Some people don't like to use TypeScript for whatever reason. You don't have to, you don't have to use dotnet. But you can if you want. And I think the biggest problem with blazer is that no one's come up with that killer app. Yet, you know, every every framework, every library, every language has its killer app, right? And no one's done that for blazer. But as soon as someone figures it out, that'll be the thing that makes everyone stand up, go, wow, this is this can actually be pretty

#### Zac

cool. I think I think you won't know about you won't know about the killer app from from blazer, because from the sounds of it from like, the sorts of apps that you're probably going to build with this, they're not going to be like on your iPhone, right? Like, this is a, this really sounds like something where you would build like an enterprise level system or something, you know, like, you would have something like, I don't know, something that goes out with with mobile mechanics or something like that, you know, I mean, like something that's really widespread, but ultimately behind the scenes for the majority of the majority of the every person on the street, you know? Sure,

#### Jamie

sure. The, I mean, the only thing that sort of close to a killer app that I that I know of is things called Diablo blazer that lets you run as long as you have the original asset files, you can run Diablo inside of your browser, because all it does, all I've done is recompile the binary to webassembly through blazer. And then had they've added this dotnet layer that just goes read the file from disk that you gave me and feed it into the game engine. But then that's not even really blazer, it's not, you know, it's more webassembly. So yeah, I think you're right, I think, I think because it's more of a an enterprise II thing, I think we're never really going to see the killer app unless some enterprise goes, Hey, we'll tell you how we did it. And and hope that you don't break it.

#### Zac

Hmm. So I mean, we're using the magic word here. We've used it a few times here, the enterprise. So what do you think has dotnet core made dotnet? more friendly for a hit hipster. Startup worker like me?

#### Jamie

Well, I think it certainly has with the the leap towards ci tooling, right? If you're using vim, if you're using a console, like when I started working with dotnet, he was back at university. And we didn't actually use Visual Studio for the first because the first year of university was Let's learn C sharp and dotnet. And the first half of that year was okay, so I want to teach you the command line for building your apps. And it was like, you would be typing for four minutes at a time, and then hit return and find out that it didn't work because you had to like you had to invoke the compiler and then pass it every single file in the chain to actually compile everything. Right. So that's immediately gotten easy. You just literally you in your terminal, you open the directory with your coding, you just do dotnet run, and it runs, right. And I can take that folder, put it on my Windows machine run dotnet run and it runs take that same folder, but on one of my Linux machines don't run and it runs, take it over to my Mac don't ever and it runs right. So that's genius to me. Just It doesn't matter. Like I said, I would no longer matters what your underlying operating system is. If you're if you're running Linux, and you're pair programming with someone who's running Windows, you just go here's the code, there's the command, run it and it will just run or you can screen share. And you can help out that way. So that makes it a little easier, right. And you have to remember that the original version of dotnet was kind of built mainly for enterprise apps on an intranet. We're talking 2002 here, right? And so because of that, it was very geared towards windows very geared towards that visual way of building software. But the world has changed now, right? You do you still don't still have those visual tools for building software. But it's less of an issue. Mark. Again, I feel like it's unfair to say it's less of an enterprise level world because there are lots more startups and lots of people who are rapidly innovating. But I feel like the enterprises are still doing that. They're just doing it behind closed doors.

#### Zac

Basically, they're saying startup work isn't real work. I get it. I get it.

#### Jamie

What do you do every day is like it's not real work Says the guy has not had any clients for a week. But but so dotnet itself back in the day dotnet framework was his huge hulking monolith of an entire framework right. And as dotnet framework has evolved, and as Windows has evolved Windows has become reliant on it, which means that they can't iterate on it fast. Because as soon as they iterate on something, they've got 20 years of apps that are going to break, or they've got billions of devices that are going to break like that, because they change something in the framework and Windows breaks, right? So the iteration on that has slowed all the way down to the point where they're now saying, there's going to be no new versions of dotnet framework, there's going to be security patches and performance patches, where they can, but the security will take take priority, right, as long as Windows is supported, dotnet framework will be supported. Because windows requires dotnet framework to run. So as long as Microsoft is shipping windows, then dotnet framework will be around and fully supported. But because core is rewritten from the ground up to be completely modular. First of all, you can go I want this bit of core and that bit of core, and you don't have to pull the whole thing in, right. And secondly, when they go, Well, we sped up this bit, there is maybe the JSON serialise er d serializer, that then speeds up everything else, you know, it has this huge knock on effect that they can go will spit up this one thing in, in, in abstention, I'll take this one part of it, take it away, work on it and bring it back. And it will just continue working. Right. And you know, you have to remember that, if you look at ASP. NET MVC, back in the day on dotnet framework, you run and it would take upwards of 10 to 15 seconds for your web server to actually start ASP. NET Core starts almost immediately, you do dotnet run and starts sending requests to it, and it will start responding. It is because of that that modularity is almost instantaneous.

#### Zac

So that was the thing that there was I was looking forward to coming back to the dotnet space all that time to you know, surf my social, my social networks was thinking compiling. He told me that I get that.

#### Jamie

That's a right, no most social networks for Zach.

#### Zac

Does that work now?

#### Jamie

That's a right.

#### Zac

So fair warning, Jamie. I'm gonna skip over the next question. The so we'll come back to it at the end. So you know, having having spoken about how a hipster like me might be interested in dotnet. Core? Well, to give your listeners just a little bit of background, about the sort of stack that I'm working in at Koodoo we, we use micro services and micro services are all written in Node. And the fact that they're written in Node kind of doesn't matter that much. Because the majority of them are written in node, we've also got other parts of the system that are like the CPU intensive parts, like the CPU intensive services, they're written in go. And the use for all our data analysis as we use Python, you know, we've got it, we've got a couple of different languages in our stack, and each of those languages. They're fine tuned to solve a certain problem. It's like, yeah, we need to do this thing. We want to do it really well. Let's pick the right tool for it. Let's make that tool work for us. So with all that in mind, where does well, I guess you don't know. You don't know my full stack. But where we're dotnet core, hypothetically fit into fit into a stack. What's a good for?

#### Jamie

Well, I mean, it can do pretty much anything. So some of the stuff that I've seen and worked on some of the things I've seen. There's a video game called age of ascent, which is a space space based MMO along the lines of Elite Dangerous and what's that one that you pay for for three months before you can actually start playing? Oh, dear, I can't remember now. But there's, you know, you build up a ship and you go flying around and you destroy everyone in the universe. That is entirely. That's the one thing you EVE Online, right? That's, it's that but it's in dotnet and dotnet core, and the lead developer, Ben Adams actually keeps making changes, because he's making pull requests to dotnet core to make it faster and better. Because he pulls the latest version of the code, puts his game through and goes, Oh, that could be bad effects that submit a pull request. So so it's it's it's, it's running. There's MMR essentially. I don't think it's a Morpurgo but it's definitely an MMR. And then, so let's dial that back, right. Clifford ages, who is a wonderful person, he's making a project called the handy project or rather, has been named as a handy project, which is an IoT hand that is 3d printed that runs dotnet. across the whole stack. He's got the individual servos are controlled by dotnet. On a microcontroller embedded into the arm. He's got an Xamarin app that runs on Android and iOS for controlling the hand. He can also read servo readings from the connector to the To the young gentleman's arm as well. So you could run games you can run, life altering, life. altering is the right word, life and empowering hardware, right? I just said, then you got Xamarin, right. So you can make a mobile app. You don't have to use swift and kotlin or Java to make your app you can use one code base if you need to. microservices are great for for use with dotnet core, because it's so small. And when you hit build, it will go brilliant. I don't need all of this chaff, that gets shipped with dotnet core to do with, say, XML or picking on XML today, but let's we're not doing XML. So we won't include that. Right? See, then your binary is tiny, to the point where I think you can get a an ASP. NET Core web server running on about, I want to say about 20 megabytes of hard drive space, which is amazing, I think right? When you think that ASP. NET MVC required on net framework four point x, which required windows, right, and that's four, five, maybe even six gigabyte instal with all the security patches with all of the software included with IIS, and all that kind of stuff. So it's tiny, right, and it can be just flung around anywhere. I've been I've worked on all sorts of different web services, from blogs to e commerce stuff, I've even done ASP. NET Core hosted JavaScript based single page applications, which is a bonkers set of words thrown together. But it kind of works still. So you have this, there's this JavaScript library that talks to node on your behalf through ASP. NET Core, which is weird, you've got a single page application is still posting back to the server. But whenever dot icon has full support for machine learning through ml dotnet. So you don't actually have to use Python anymore. You can say to dotnet core, you can say to dotnet, go and figure this out for me, here's my machine model. So here's my my machine learning model, here is my data, go do whatever it is you need to do. And sometimes that means it's got to go to some cloud service provider, but it will do all of that and stay in that library in that language word. And then the craziest one, I say crazy, just because it's mental. Think about this right? There. Same code. You've got a Tyson TV, a Samsung branded TV or a Samsung fridge, you can run that same code on those devices. Because dotnet core is the official programming language in running parts of the Samsung Tizen range of home appliances.

#### Zac

So it can do it can do everything is how you say that. But

#### Jamie

yeah, it's because it's a general purpose thing, you can effectively do everything, but he's not going to be the same as. So my experience of doing say ml dotnet is not the same as handwriting, the Python code that runs all your data analysis, but it will get you 90% of the way there because maybe you're a dotnet Dev and you don't know Python, right?

#### Zac

Yeah, but I feel like you've skillfully sidestepped my question there. So let me ask it in a different way, so that maybe we can get the answer that myself and your listeners were looking for? What's your favourite thing to do in dotnet? core? Like, what's the thing that's like, Man, this is sweet. This would this you couldn't do this, like in any other language? Like, and I mean, not everything, okay? Because I get it, it can do everything. That's like a cool thing. Right? That's, that's like a cool thing that it can do that it can let you do everything. But like, what's the thing where you're like, oh, man, I'm glad I'm not doing this in another language. This is this is really cool.

#### Jamie

So my personal favourite one is I know you can do this in Node based stuff. You can make global tools. So you know, like, when NPM you can do NPM instal global, and then you can run Gatsby and it will run the Gatsby duelling. Right? The same, you can do a very similar thing in dotnet, or at least dotnet. Core, you can grab these global tools. And so what that is, is that's a single application, usually a console application, but you can because it's technically pulling whatever you need. If you need to communicate with the web, you pull in the parts of ASP dotnet core, allowing you to communicate with the web, right? So this one of the things that I've built is at the top of the show, I literally say type in done any podcast and there's sound of me typing, right, that has been actually scaffolding a new episode, I bring up my a terminal type in dotnet space new space podcast. It scaffolds everything I need for a new episode of Greece, all of the the show notes for me grades, the sets of everything in the recording software, I use icon stuff, right? But then I've got another one that I use for when I'm sending audio to the editor. So inside baseball, we hit stop on this recording app, I get a bunch of WAV files, right. wav files are massive, right? I've got to send those over the way it might be a gigabyte and a half just round compensation. So I've written an app that can be All of that, that WAV data over into FLAC, which is we're getting a bit technical, but that's a free open source lossless audio codec, right. So a 700 megabyte WAV file may drop to 150 megabytes, I think, zip that up and email across. Well, I can just type in converter into my terminal and type in pods, zip, as one word, hit return, it will take everything in that in the directory where I've just run that. Do all of what I've just said, and then email it out. Right. And that's just a single console out there, I just wrote, now you can do that in Node. But I like that I can do it and done it. Right.

#### Zac

So your favourite things about dotnet? are the things that you've built. Yeah. But no, have you at least have you at least open sourced them,

#### Jamie

I have open sourced one of them, I do have another one that I use to set up an entire machine. So I buy a new laptop, or I rebuild my computer, reinstall the operating system, right, I can pull the code for this app and run it, I don't even need to pull the code, I've got a nougat package, right, I run the new get package. And it instals itself, then instals dotnet core because it needs dotnet core for some stuff. And then it goes through it instals all the apps that I want automatically, it then sets a whole bunch of policies on the computer, and then sets up like even the dust, desktop wallpaper. And then it goes is done. And this is like I I pull a file, run the file and walk away 20 minutes later my computer setup right? I have an open source that one because that's more of a business eating but but I've used that that technique in the past when I was working in a sort of DevOps II role to set everyone's machine up. So they're all running at the same low.

#### Zac

I feel like I've really given your your audience and pretty, like deep secrets in this episode. Listen all the way to the end, there seems to be some real cookies a you know, the fact that did you? Have you told them before that you did the that that typing thing is actually like a real thing that you do?

#### Jamie

I think I've mentioned it once or twice, but I've never actually elaborated on it fully.

#### Zac

Yeah, first time you're hearing it.

#### Jamie

That's it. But just a really quickly go back to that machine setup app. I can run that on my Linux Windows or Mac machines, and it detects the operating system, it's the same code detects the operating system, and then sets it up differently based on Oh, this is a Mac. Okay, so you did instal homebrew bully apps that way. And I haven't had to rewrite it or recompile it, it's literally the same code just pulled straight from nougat or pill pulled straight from GitHub. It's amazing. But then you could do that with node, right?

#### Zac

Well, yeah, I mean, that's fine. You're allowed to be excited by your, your language. I'll allow it, you know, it's okay. So, I mean, you know, let's keep that enthusiasm going. What do you what are you most excited about? in that? What's coming in? What's coming up for core? What should I be listening out for? And, you know, because obviously, after this, I'm going to be inspired to start writing all our services in dotnet. Core, what should I be looking out for?

#### Jamie

Okay, so the biggest thing that's coming up is that they're they're sort of converging is converging the roadmap, I'm going to use the world, I'm going to do what you do, and I'm just gonna own

#### Zac

it, right? Google it. Yeah.

#### Jamie

They're converging dotnet. Core and moto they're bringing these two technologies together, I kind of touched on moto earlier on, but moto is this closed source? Open Source? blackbox, reimplementation of dotnet. From the early 2000s, written entirely in C and c++, right? And so it's more as powerful as what powers blazer, it powers unity is what powers Xamarin. And people are saying, Well, why do we need both? Right? Why did both exist? If they're both doing the same thing? Why do they both exist? So Microsoft gone? Good point. And that's the next step is to merge these two together. And to the point where the, I think this is going on knowledge from like a year ago, the unit tests for mano, when ran on the dotnet, core code base, work perfectly, and all pass. I mean, they may all just be true, but they all pass. And the unit tests for dotnet core all run perfectly on the moniker base, there's a little bit of wiring up to you. But then by merging the two together, dotnet core is written in C sharp, mono is written in c++, you get this small, fast, modular runtime that does all of you don't net things, right. So it's one dotnet code base to rule them all. So don't know, five, six dotnet. Seven is actually going to be a combination of core and mono small, fast, brilliant. And then on top of that, Okay, so we've talked mainly about web stuff. But let's say I want to make a comment or not a console app, but some kind of visual desktop app. Well dotnet core runs on Windows and Mac and Linux is right I'll say Linux is because Linux isn't really

#### Zac

an operating system, Linux.

#### Jamie

Yeah, right. Yeah. Linux, I like it.

#### Zac

So, my Alexa thought I was saying Alexa. Sorry.

#### Jamie

Oh, the world of connected devices. But because of that, because it runs on these three desktop environments or rather with the Linux is there are multiple desktop environments where you've got gnome, you've got Katie got Wayland, you've all sorts of different technologies used to actually draw the windows, depending on the technology used, the different API's are available for those windows. So what's really exciting about that for me, since dotnet, core first came out there were like people would say, but how do I make winforms on Linux, and you can't write all of that is embedded directly into Windows. But Microsoft have come out with a thing called Maui that they should have built this year will not marry actually stands for multi platform app UI. So they've, they've ignored the pay and multiplatform. But they've completely just use the UI, but

#### Zac

whatever, I miss the opportunity to call it my power.

#### Jamie

Yeah, apparently, that would have been awesome. But this is uses Xamarin Forms under the hood. And it is essentially just that is multi platform user interface. Right? Because people have been crying out for it since day one, how do I make my user interfaces multi platform? And how do we make a Linux app that runs on Windows? Well, this is, in the next year, this is promising to do that. There was already an open source. That's open source as well. There's already a third party open source offering for that called uno platform, which does exactly the same thing. So it is based on zamel, right? So you can build up all of your apps in zamel, or Xamarin, or whatever. And run them wherever you are. So that's really exciting to me, this cross platform UI. It's never been a thing, right? Well, when it has with like technologies like Qt, but then you have to pull hundreds of megabytes of dependencies just to display a message box, right. But uno and Maui make this totally simplified. And then yeah, like I said, the convergence of dotnet core and mono making it small and brilliant, right? So with that, the the brilliance of c++, they're that crazy. I can't really understand what this line of code is doing, but it's doing it really well. And you've also got the C sharp side from dotnet core where you have things like span ft and async enumerable. So you have these wonderful high level stuff coming from dotnet core. There's wonderful low level stuff coming from mono and you're mixing it together, you're gonna get an incredibly fast runtime with wonderful tool in there is just or is is wonderful.

#### Zac

Well, that's Yeah, that's that's super interesting. Well, Jamie, thanks so much for coming on the dotnet core podcast. We'll have to see whether we can get you on for the next episode. That would be that would be really great thing to get you on. You know, that would that would be awesome. check my schedule.

But yeah, that's right.

#### Jamie

So yeah, that was a tonne of fun, Zach, thanks for flipping the tables on me and interview me. I felt like I should do one of these every year. I did one last year. don't win this year. Let's keep doing these. I just have to find more people who want to sit and talk to me. So thank you ever so much for wanting to sit and talk to me, I guess.

#### Zac

My pleasure. My pleasure.

#### Jamie

Awesome. So just real quick, then before we fully sign off, if people want to learn more about you, and some of the work that you're doing, what's the best way to do that? Is it Twitter? Is it just shout out the window. They read it down on a piece of paper and throw it up? Throw it into the bin? what's the what's the process?

#### Zac

I'm at? Yeah, most of the usual places. You can get me on Twitter. It's at Zach at the hacker, my my workplace Koodoo is at Koodoo HQ, we're actually hiring at the moment. So if you want to come work with this guy, then you know you can you can check that out. And there's also at tabs and spaces is the Twitter handle for the podcast that Jamie and I run, or you can check out tabs and spaces.io that's just spelt out that how it sounds spaces.io. And, and yeah, you can come and listen to Jamie and I riff for an hour once a month on different developer issues. So you know, they've been really interesting. There have been some some good things we've we've pulled apart is what six hours worth of content at the moment. We've got monthly hourly episodes, recording, uploading, yeah, most likely

#### Jamie

be about maybe eight or 10 by the time it comes out. But yeah, definitely. Our full

#### Zac

day's work of listening to me. Fantasticks.

#### Jamie

Just think of our life lessons you can learn by listening to Zack.

#### Zac

I mean, it might be more than none.

Unknown Speaker  
Because obviously

#### Jamie

it can't trend downwards is what you're saying.

#### Zac

Yeah, I mean is it can only go From here, you can't you can't unlearn life lessons from listening to me.

#### Jamie

If you like that, that's essentially tabs and spaces robot for an hour.

#### Zac

Yeah. Thanks so much. Right? Yeah, yeah. James James hangs out. Yeah. Yeah. So thanks so much for having me, Jamie. It was I had a really great time. I feel like felt like I learned a lot. I hope your audience did too.

#### Jamie

But I have to do otherwise. I've done a really terrible job. But thank you so much for being on the show, Zack. I really appreciate it. Thanks.

#### Zac

Cool. See ya.

{{< paracentre "The above is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

### Wrapping Up

That was my interview with Zac Braddy. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/), and there will be a link directly to them in your podcatcher.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice - head over to [dotnetcore.show/subscribe](/subscribe) for ways to do that - and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Zac on Twitter](https://twitter.com/ZackerTheHacker)
- [Zac's website](https://zackerthehacker.com/)
- [Tabs & Spaces](https://tabsandspaces.io/)
  - Zac and I co-host this with James Studdart of [The Cynical Developer](https://cynicaldeveloper.com/)
- Zac makes a series of videos where he [learns VIM as a Samurai Cat](https://www.youtube.com/channel/UC73GI8tvfbxNbl626M6lUiQ/videos)
- [koodoo](https://koodoo.io/)
  - Zac's employer
