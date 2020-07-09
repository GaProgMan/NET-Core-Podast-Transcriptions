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

I am your host, Jamie "GaProgMan" Taylor, and this is episode 43: How Do You Even Start with Josey Howarth. In this episode Josey Howarth actually interviewed me on how to get started with .NET Core. Some of you may know Josey from her work on the [Documentation Not Included podcast](https://dnistream.live/), as a [GitKraken ambassador](https://www.gitkraken.com/ambassador), or from her company [Love Sudo](https://www.lovesudo.com/). It was quite a lot of fun to be on the other side of the interview, after having been the interviewer for a year and a half; it was also a lot of fun to be able to go "back to basics" (as it were) and provide some information on how to get started with .NET Core.

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Josey's Introduction

**Jamie**

So first thing I want to do Josey is thank you ever so much for agreeing to be on the show. I know that it means losing a little bit of your evening, and we're all super busy these days. So thank you ever so much for that.

**Josey**

Not a problem. I'm only in the middle of a massive migration. It's okay, it's all right.

**Jamie**

It gives you a chance to sort of step away from that. And then maybe we can talk about whatever we're going to talk about, and then you'll come back to you with a fresh pair of eyes and hopefully you'll go, "Ah, yes, I see now," rather than the, "Oh my God! What am I doing?!"

**Josey**

Normally that would be the case, but I actually have a very well planned out migration, and it's all ready to go. It's just a matter of walking through the stubs.

**Jamie**

Fantastic.

**Josey**

And it's not a code. Well, a little bit is, but it's not like, it's not "code" code, so it's not me sitting there going, "Why can't I get this function to work?"

**Jamie**

I always like when everything is really planned out. Like you've had the time to think of the "what ifs" because, invariably your deployment or migration there'll be a hick up. It's not that it will go wrong, it's just that something will, maybe you'll be distracted for a second or two and forget what you're doing.

The perfect example I can give is a friend of mine once had a Raspberry Pi set up as a Home Theatre PC. And he didn't do Linux, but he'd asked me to come round and see if I could maybe help him back it up and stuff like that. Because he was gonna install the update, he was very worried about, "what happens if the update fails?" And we sat there and I said to him, "Ok right. Here's a USB; plug it into your laptop; live boot into a Linux distro; I'll talk you through the process of backing it up." We took the SD card out of the Raspberry Pi, because you can only access the partitions which have the operating system installed on the SD card through non-Windows because Windows can't address it. So okay, we'll plug that in and get that running, and I said

> Ok, right. We'll do a bunch of commands to see where everything lives. We'll craft the command, bewteen us, in a different window, and I'll sanity check it, then we'll run it. Because if we get it wrong, it'll wipe your computer.

So we built the command, and I said, "OK. It's sanity checked. But give me a minute, don't run it yet because I have to nip to the bathroom."

**Josey**

Oh no

**Jamie**

Came back out of the bathroom and he'd wiped his computer.

**Josey**

You know in the world of IT, there is this fantastic perception from people who I guess they could say they sit there and go, "but it's a complicated," or whatever terms they want. "I'm not technologically aware," whatever terms use there is this fantastic division - or perception I should say - of how they see us. And it is this whole thing of, "Oh my God! Uou have to come help me!" And they never listen to anything you say. No matter what advice you give, no matter how much you try and lay things out, they never listen. And it's just like, "Why do you waste my time? I have important things to do." Not really, no. I live in my boring life ever possible.

Yeah, I'm actually here for one purpose, and one purpose only Jamie.

**Jamie**

Yes?

**Josey**

And that is to bring down the educational level content of your podcast.

**Jamie**

That's unfair to say. You're assuming that there's a high level of educational content of this podcast.

**Josey**

I have listened to it, and at times it's complicated, Jamie. It's complicated.

**Jamie**

So I guess we've gotten this far into the podcast. I think it might be a good time for the listeners to find out a little bit about who you are and stuff. So I was wondering, could you give the listeners a brief introduction to sort of who you are, what you do, and all that kind of stuff?

**Josey**

Certainly. My name is Josey, and I go by quite a few pseudonyms online; including `Sudo Nimh` as a pseudonyms. I also go by Darth Securitas, because I am utterly unamused by people's practises when it comes to security. And that is because I am a bit of a fiend, which is why a friend nicknamed me Darth Securitas. I've also been nicknamed a rogue verbal alchemist because I am great at words - not really, but for some reason someone thought it was funny. So it's kind of dug and stuck. But for me, I have been involved in technology since I ripped apart my mother's stereo when I was like two and a half, trying to find the tiny people in it.

And that was a long time ago. We don't ask people who are as old as I am their age, because honestly, at this point I'm older than most people think I am. And it doesn't really matter anymore.

But my day to day life is literally managed services for websites; web hosting; I do development/design. I mainly work in WordPress; I mainly work on nGinx; PHP; mySQL; Maria, sometimes. Is it Maria? Or is it mongo? This is what happens when you catch me so late in the day. It's an M base gosh darn it, and that's what I'm going to stick with. But like, yeah, I basically work in that world now.

Now my history however, has me involved in things like application development using C# way, way back in the day. I actually was learning C# before came out properly, because they hit the universities. If you're going to get any product out on the market, just so that you know for those of you who are currently crafting tools: hit the universities. You get the people who are learning a language, a tool set or anything else with your tool or language or what have you. You've got the market.

So a little bit of life lessons for people, you know. But I've been around the block a few times. And then I started doing a development podcast called [Documentation Not Included](https://www.dnistream.live/) for developers, where we talk about everything from consulting to freelancing; to development, which I say with a big sigh. But I love what I do.

Yeah, that's that's basically me. Mostly I am an uninteresting person who was here to grill Jaime about .NET Core.

**Jamie**

well, I mean, it's only fair, isn't it? I've spent, you know, the better part of a year and a bit asking other people questions. So.

**Josey**

Yes, this is me interviewing you. This is going to be a divergence for those who are listening in the future and in the past. Wait. Can that work that way?

**Jamie**

Yes.

**Josey**

No, no, it can't. No.

**Jamie**

No.

**Josey**

No. Well. It depends on when our, you know, AI overlords come and take us over.

**Jamie**

Exactly. The way I explain it a different podcast I do called [The waffling Taylors](https://wafflingtalyors.rocks) is it's `the great time cast machine wibbley wobbliness`.

**Josey**

Exactly. You know, someone may listen to this in the future and be like, "Yes, I've heard this before," and they'll be like, "that's because half the stuff that comes out of my mouth has been said before." And I'm sorry. For those of you listening. I'm sorry if you get bored, Hopefully you're entertained and hopefully you learn something. If not you can pick on Jamie.

**Jamie**

Yes. It's all my fault. It's always my fault. That's fine.

**Josey**

Excellent.

**Jamie**

The one thing you learn as a developer is, it's always your fault.

**Josey**

Yes.

### But, What IS .NET Core?

**Josey**

So do I get to ask you questions now, Jamie?

**Jamie**

Yeah, I guess. If you desperately want to ask me a question and that's absolutely fine.

**Josey**

Basically what this comes down to is that you and I have had a conversation, cause we've had you on documentation not included. And Chris, who is my co host on that show, he loves .NET. It's Donna corps. He loves it. I have never touched it. Like I've never played with it; I've never really done much with it. I've looked into getting involved in it, but there have always been barriers. But what I want to do is, I kind of also want to make certain - and I'm gonna play even more dumb than I normally am - but I'm gonna play sort of this sort of devil's advocate thing; where I'm gonna ask you some questions that I might challenge you. But at the same time, I may ask your questions and you just not along going, "Ah, so that is how a sycophant answers." But no, you know, I just wanna know things.

Let me start with the most basic question. Now, you've probably said this before, but I want to know: what, to you, is .NET Core?

**Jamie**

Okay, that's a good one. So .NET Core, here is thie longwinded, official answer that requires even more jargon; because that's how it works, right? You need to know words before you can understand other words. So

**Josey**

Excellent. We're gonna need a dictionary now?

**Jamie**

Yeah, why not? Let's get the dictionary and let's do this.

**Josey**

Okay.

**Jamie**

So .NET Core is an open source implementation of the .NET Standard. So let's dial that back a second, and find out what the .NET Standard is.

.NET Standard is a standards document, which lists a bunch of API and methods, and all that kind of stuff - object types, and classes, and things - that you can expect a platform which implements the .NET Standard to have. now the .NET Standard isn't like a thing that you download - I mean, you can download it, but it's not anything you download to help you make applications. It is literally a document, and it's kind of like how your language specification works. It's the same sort of thing, except they call it standard, rather and specifications, which is bit of a misstep, in my opinion.

So .NET Core originally started as a subset of .NET Framework. It has now become a completely separate animal because .NET Framework is kind of... How do I put it? I don't want to confuse people like an early episode of the podcast did. .NET Framework is essentially "done" in bunny quotes, in that it is finished, there's not going to be new features added to it, but there are going to be security updates. And it is going to be supported for the length of the windows, kernel, because the Windows operating system requires .NET Framework to be installed, and present, for it to work. So it's a very Windows centric sort of enterprise-y thing, and it is required. So if you know anyone with the Windows 10 device, then they have .NET Framework installed.

**Josey**

Well, I could take it even further: if you play video games, you have the .NET Framework installed.

**Jamie**

Indeed you do.

**Josey**

I'm sorry I had to interrupt this because this, to me, is hysterical, right? I have a non techie friend of mine who is very much so a gamer, and a bit paranoid when it comes to technology. So anything happens, it's immediately, "Josey. Josey, Josey. I need to check this and verify this. Is this what it is supposed to be doing?" And they went in to add/remove programs to remove something from their PC - and even then I had to hold their hand. And they were scrolling down through the list, and it was just .NET Framework, .NET Framework, .NET Framework, .NET Framework, like this huge lists of all .NET Frameworks, and they were all pretty much the same thing. He was like, "Why is this happening?" I'm like, "every time you download a game and install it from steam 5, 6, 7 times out of 10 it's going to require the .NET Framework, and it's going to re download it. It's okay."

Yes, sorry had interrupted Interject that.

So Going back to what I was saying, one of the things that you have made mention of in your explanation is one of the biggest deterrence I have for wanting to get into using just this framework. Well, technically speaking, several other frameworks as well. And it literally comes down to the whole concept of, "well, it's slightly complicated," and that's literally what it is.

Let me ask you this. Who wrote this .NET Standard, this document?

**Jamie**

So the .NET standard was written by Microsoft.

**Josey**

Right. And originally back in the day, one of the big problems a lot of people had with that was the fact that it was very closed source.

**Jamie**

Yes,

**Jamie**

But Microsoft is. How do I put it? So I have an analogy. There was put to me by a third party. So it wasn't the person who created the analogy. It was the person who heard the person saying it.

**Josey**

Hearsay, excellent. Bring it.

**Jamie**

Hearsay-naology? Can I combine the words together? I don't know. Put a hyphen in there. There we go.

**Josey**

Sure. We'll go with saladed. He-Sal-Ogy.

**Jamie**

That's it: hesaolgy.

**Jamie**

Yeah, that's it. If we say it enough times, it will go into the English Dictionary.

**Josey**

Ah, if it's not already. Someone will probably grab it, trademark it, and we'll lose all rights to being able to say it, even though we said it first. But go on.

**Jamie**

Exactly. The analogy that I have [heard via a third party](https://dotnetcore.show/episode-30-reflections-on-net-with-pablo-santos-and-phil-haack/) is that one off the sort of leads of the .NET ecosystem over Microsoft is called Scott Hansleman, and he once said that, "Microsoft is like an oil tanker, it's slowly turning," if you want to stretch the analogy, "is slowly turning away from close source over to open source. But because it's so large, it's going to take time."

So over the past 5, 6, 7 years is being moving and turning very slowly. So one of the big portions of the what people consider is .NET is called MVC, or ASP .NET MVC. Now ASP .NET MVC is a completely separate thing; It can be added into your - I'll go into a world of these mean in a moment, but the point of driving towards is that: whilst the .NET Framework _was_ entirely close source, at the time that they developed ASP .NET MVC completely open source. And so you could literally downloaded the source code in C++ and run it on your machine, and you know, compile it, and do all this kind of stuff. And it was entirely open source; which started this short, slow amble, I guess, towards open source. Like I said, the beginning of that oil tanker turning. It started that off.

But yeah, there is a big history of people, I don't want to say mistrusting Microsoft, because I think that's unfair term. But the displacement off 100% trust; a lack of trust with Microsoft because it's a close source. And I feel like it's both justified and slightly unfair.

**Josey**

I think. Well, that's the thing. You know, at least to me, I'm a huge fan of open source for a variety of reasons. But there is also serious problems within the open source community as well. So there's never going to be a silver bullet for whether you should be open or closed. It is always going to be situational.

I could very easily play the cynic and say that [they are] getting involved in the open source community with the intent to drive what can and what cannot be actually used. Or basically figure out a way to eat up every resource possible within the open source community before killing it off.

There are people who believe that. But to me as much as you know, we can pick any soapbox we want and stand on it. It comes back to one thing, and that is the barrier to entry. I would love to get into understanding my co-host Chris better, by being able to speak half of his language, which is .NET Core. Am I able to do that right now? Not easily.

Perfect example: In preparation for this show, I decided to look up things like .NET Core versus things like, you know, PHP, whatever. But just simply .NET Core. When I went to look for information about .NET Core, you know what came up?

**Jamie**
Stack Overflow?

**Josey**

I would love for it to be Stack Overflow. Know what came up was ASP.

**Jamie**

Oh ASP. Yeah yeah.

**Josey**

ASP .NET. So it was like, "wait is ASP .NET Core or is .NET Core ASP?" Like the barrier to get involved just seems so high to even start finding information. And then when I find blog's, I'm like, "Oh, there's a little thing here that's trying to explain that," but again, like you started at the start of this show, it's all terms, and things that make no sense to me are not broken down. And I'm like, "you know, I'll go to one of the beginner-beginner things and I'll start looking at that," and I go and I look and it's five years old.

It's like, "come on."

All of us can speak from this when we're talking about technology that we're using or things that were investigating. We know that we have to do our own due diligence. We have to make certain that whatever we're looking at is actually valuable and viable. I can't begin to tell you how many Angular tutorials I ran across had it had security flaws in them.

**Josey**

And yet because of the fact that these things were out and people don't always read and don't always do their due diligence, they just go, "Oh, there's code here for 'how to do an instagram integration into a web app'," and they don't actually stop and check. They just copy and paste the things and it just drives me absolutely bonkers.

But there's so many steps in the development cycle and trying to find the information that is applicable to get started. It just seems like, um what's a good analogy since you are Mr Analogy man? A good analogy would be: It's a bit like being a drop of die being dropped into an ocean.

**Jamie**

Ok.

**Josey**

I really would like to reach and colour the world with my own opinions, applications, implementation, support, and then education. Because to me, I don't just delve into learn things. I delve into learn things to a point where I can teach them. Because when you can teach somebody what you have learned then that shows, in my opinion, almost a love of what it is that you are talking about or teaching. So I always revert things back to love hearts to everybody who is listening.

But how? How does one even begin to get started? I know, thanks to you, that Microsoft has now implemented a sort of lesson video introduction, thing on their learning website. But, you know, there's different types of people who are gonna be looking to get involved in this. There's the people who are crossing over from either other frameworks or they're looking to expand their knowledge. Like, you know, I know somebody in the WordPress world right now who wants to completely leave everything PHP and go into things like Angular and all that other stuff, but they have no clue how to get started in this .NET Core anything. And then you have other people who have, like almost zero to limited knowledge at all about programming in general. Therefore, you know they're not going to bring with them the habits that another language would say have them bring with them. So it's a little easier, in my opinion, to teach those people if they can find the right resources.

But like, how? How and why should I even bother?

### Why Should I Even Bother With .NET Core?

**Josey**
Let's start with why. Why should I bother with .NET Core, like at all?

**Jamie**

Okay, so how did I explain it before? I think I said on Twitter, Didn't I? Essentially it's a static. Well, okay, so .NET Core requires you to use one of two languages which are statically typed, compiled ahead of time languages. They allow you to do things that you can do, kind off, in the lower languages C/C++, but without all of thie ceremony that's involved with memory management, and dealing with individual hex codes, and byte arrays, and all this kind of stuff.

**Josey**

I'm sorry. You've just completely turned me off from it. If I can't play with it; no I'm just joking. Continue on, convince me, Jamie, convince me.

**Jamie**

It's also inherently cross platform. So .NET Core is, from the ground up, built as a cross platform application-

**Josey**

You mean its Java?

**Jamie**

Well, this is the thing, right? Okay, So when Microsoft announced .NET Core [version] one, they had a wonderful image and it said, "one run time everywhere," or something like that. It's alluding to; "you could build it once and run it anywhere," which is what Java promised in the early nineties and obviously Java kind of delivered on that.

But its Java.

**Josey**

Don't get me started on pointers in Java.

**Jamie**

I mean the fact that you are actively encouraged _not_ to use the default types for certain things in Java - like the built in provided ones for things like datetimes and things - you're actively encouraged not to use them and to use a third party, should tell you almost everything you need to know about Java standard library. But I'm jaded because I'm a C# developer.

**Josey**

Well, I'm going to go out there and I'm going to say Java has its purposes. Right. We wouldn't have Minecraft without it.

**Jamie**

That's true. We wouldn't have Blu-Ray players.

**Josey**

No.

**Jamie**

We wouldn't have Android as an operating system.

**Josey**

No.

**Jamie**

Those both require Java. If you've ever written an android app that hasn't used some kind of cross compilation to like Xamarin - which is the .NET thing - or any of the tools that allow you to build a Web app and then create an Android binary for it. Or if you've ever used a blue ray player, they use Java to decrypt, I think, part of the DVD and they have the interactivity. parts are provided by Java as well. So yeah, Java is huge and Java is everywhere.

**Josey**

I'm going to say this, and this will impact future of people who are listening, you maybe even more so: this Thursday on our show for Documentation Not Included, I actually have a B Y O M - which is a "bring your own manual," where we teach people things that we have learned or we share knowledge during the show - about Java, Java specifically, and I so want to reveal it. But I am holding my breath because I want you to watch or listen to the show - whichever one you want to do.

Okay, so let me boil this back. What you're saying is that that .NET Core pretty much allows you to build your app - it makes difference whether you're doing a web app or an actual application itself. And it doesn't matter what platform it is, as long as they've got the framework installed - which is pretty much a guaranteed download from Microsoft in some way, shape or form. And in the right framework, therefore can make use of whatever libraries you make calls on for dependencies.

It's a good thing.

And that's basically what makes .NET Core so fancy is the fact that it, it's basically, for lack of a better term, a container that lets your app run without using containers in the form of docker. Or like - I hate the world of IT. But I love it so much, you know, terminologies.

**Jamie**

You're ruining the keyword gambit there. I was expecting you to say, "machine learning and BitCoin," right about now.

**Josey**

BitCoin drives me nuts for a variety of reasons, But that's a show for another day.

So what, you're basically tell me, let's pretend I know bugger all about anything. And that's always a good way to start with me 'cos yay.

You're telling me that whatever I develop where I have .NET Core as the foundation for my app, it will run anywhere. So I don't have to sit there and go, "I need to import this particular library if it runs on this or that." Like you can just build it and it will work as long as they've got .NET installed. Is that what you're telling me?

**Jamie**

Yes.

**Josey**

If you had said that at the very start, I would have gone, "Oh, really?" But the thing is, this is the problem I have, and it's not just .NET. Like, let's be honest: It's every type of framework out there. It's that, "What is the brass tacks of what makes this thing powerful? What am I looking at? Why should I bother this" and the reality is, it is that platform independence.

It is the fact that it is the foundation for an app. Because I could only think of two platforms that do that .NET and Java. Like those are just the two that come to my mind like I can't think of anything else that is really that free.

I mean, one could jokingly say PHP but thats a completely different type of thing. Because that still has its issues. Depending upon whether you're trying to run that on IIS, nginx, or whatever. But my point is: it's .NET Core and Java for the two big foundational parts of the stack. Would you agree?

**Jamie**

Oh, definitely.

**Josey**

So now that I understand really what .NET Core is, because everybody I've asked has come back with all kinds of different fluffy explanations that made no sense to me. But you're one of the first who has done so, so congratulations. The barrier to entry has been lowered.

**Jamie**

Hooray!

**Josey**

The the next question that I have then is: well, how do I know what the right resources are to learn? I mean, you've got multiple types of learners. You've got the auditorial learners who do best when they hear things. You've got the visual learners to do best when they see things, and you've got what I like to call me: the hands on learners; and there is a proper term for it but bugger if I remember what it is.

**Jamie**

It's kinesthetic.

**Josey**

Thank you. It's a k word. And that type of liner has to do while also reading, watching and, like, "I have to put my hands into it to play." So how would I get started in this? Because it sits so low on the stack, I don't even know if I want to go Vue, or Angular, or like any other type of framework on top at all.

I just want to know How would I get started in a way that gives me information that is not completely dated? Or, you know, "this only works on version 2, not version 5.6," which is the latest release thing. Or my favourite one is:

> When you go to download this, please be aware that the website might have changed and the download version may have changed. You can click on this button to download the version that reflects what we're using in this tutorial. Don't mind the fact that some of the changes that have happened in the last you know, six months since I wrote this tutorial and are showing this material to you have drastically changed everything.

Where do I start?

**Jamie**

On your final bit there, you hit upon a problem that actually did happen in .NET Core;s initial evolution. So when the first version came out, the way that you logically clump a bunch of code together is you create a project file, the project file says, "everything within this directory and below it, is considered compile-able unless it's a type of dll, binary, or an exe, or some kind of blob." So then that way the tools that build everything know where to start to build the app, if that makes sense. It always looks for a program.cs file and always looks for a main entry point. But then it needs to obviously, then jump out and got to this source file, and that source file.

**Josey**

Oh wow, `main.c`.

**Jamie**

The reason it has to do that is because .NET Core supports being written in F#, which is a functional language; C#, which is object oriented. But it also supports- 

**Josey**

I am actually familiar with F#. You know, it's not discussed very often, might I add.

**Jamie**

It's really not. It should be discussed more because-

**Josey**

There's your next podcast.

**Jamie**

Well, there you go.

The way the compilation tools support those two languages and a language called VB, which is based on BASIC. So it supports all of those, so it needs to know where all of the files are so that it can start the compilation process.The problem is that .NET Framework uses a project file which has XML-like syntax. And when .NET Core 1.0 came out, they said, "Let's change that a little bit and see if we can get away with simplifying it by using JSON." So in .NET Framework land you have `project.csproj` - which stands for C# Project - and in .NET Core land in version one, you have `project.json`. Taking away the fact that it's XML vs JSON, the formatting and contents of those two files are wildly different.

**Josey**
 Yes.

**Jamie**

And then they brought out version of 1.1. And version 1.1 ditched the `project.json` and moved everything back to the XML type of project file. And the problem with that is, everything that's written for 1.1, the code still works, but when they say, "Make sure you have this line in your project.json,` you then have to figure out some kind of arcane wizardry to convert that from the JSON lines into the XML lines. So even in V1, before we even got started, there was this huge sort of issue of, "But this works in version 1, but it doesn't work in version 1.1." So there's a lot of complication around that, I guess, in that initial set up. But they've moved completely away from that. And if anyone is still using version 1.0, why? And secondly, there is a command line bunch of arguments you could pass into your build tool that will convert from project.json over to the sort of XML format. Now, it is XML, but it's not horrendous XML. Like most of the people who implement XML, and it's not the bad implementation of XML is a relatively good one.

But yeah, but on your point of, "how do we get started?" I would say, "you don't even have to install anything. Just go over to [try period dot period net](https://try.dot.net/).

**Josey**

That's funny because I just tried to get to `try dot ml`, which has absolutely nothing to do with it.

I will jump in here and say, you're telling me that I should go to [try full stop dot full stop net](https://try.dot.net/)n or for people in America: [try period dot period net](https://try.dot.net/)

**Jamie**

Yes

**Josey**

'cos dot dot dot net is just horrible.

**Jamie**

Well it's because the try part is a sub-domain of dot dot net or dot period net. You're absolutely right. The URL is horrendous.

**Josey**

It's ridiculous, to quote you.

**Jamie**

But when you realise that `dot.net` is a Microsoft domain that the own for .NET things, because you can't have period net can you? Because that's not gonna work, is it?

**Josey**

Exactly.

**Jamie**

Because that's a TLD [Top Level Domain]. So you need to have something in front of it.

**Josey**

Anyway, moving on from you URLs and domains and even that, like I could go all over that particular thing that it's another area. So I have [try.dot.net](https://try.dot.net/). Wow!

**Jamie**

It is a bit silly, but what you'll notice about that page when you load it is it will give you an actual text file and a run button, and you hit the wrong button, and it will run whatever is typed in there. The most interesting part about that, though, is that inside of your browser you have a full .NET Core runtime running inside of the browser, because of a thing that Microsoft have co-opted, I guess, called Blazor. Well, now that it's based on some older work done by a different team. But if you if you bring up the dev tools inside of your browser-

**Josey**

I'm looking at `succeeded true`, `diagnostics null`, `runner exception null`.

**Jamie**

So what you've got there is: inside of your browser, you have the dlls - so these are the libraries that are required to run a .NET environment, but they're being run inside of your browser because of a thing called Blazer, which is built on WebAssembly.

In this page, you can take the code that is written out for you - on my screen, it's [Fibonacci](https://en.wikipedia.org/wiki/Fibonacci_number) stuff - you hit "run" and what happens is the code that is inside of your browser will then be compiled, inside your browser, then run in a .NET environment inside of your browser. So you don't even have to install anything because it's all there, in your browser.

**Josey**

You know, if nothing else, I take away from this episode that .NET Core is powerful because it can run on any operating system and any browser.

**Jamie**

Well, exactly.

**Josey**

And that says something because browsers are pain in every developers wahzoozie. That is my technical term. And yes, you can bleep out wahzoozie, if you so desire. But it is a pain, an absolute pain. Because I work in the world of CSS, like a lot, with the stuff that I do. And I get so utterly frustrated when it's like, "Well, this works on Edge," you shouldn't be using Edge to begin with. But I understand. I get that it doesn't work on Edge. But you know, it's one of those things.

Okay, so the first thing you say is basically to play around with it and to see what it actually is.

**Jamie**

Yeah.

**Josey**

And you could do that with try dot dot... that place, that website. Which would be in the show note, because you're a smart man and you'll do that right?

Okay. So if I wanted to build something, or I wanted to you then take myself to the next level, like, "I now have a foundation. But what do I do with it?" Like great. I can have people installed .NET every time they you know, install my app.

**Jamie**

OK, so one of things I'll say is you don't have to install .NET Core to run the app, you should indeed have the .NET Core runtime. You need a runtime, right? But the build tools allow you to do what's called a self contained build. So you hit "build" and you get out a bunch of binaries that also includes the relevant version of the the .NET Core runtime in the same directory.

And what happens is when you run the app, the app will go, "where's my .NET Core at?" It will start by looking where you started from, and then we'll travel up. So I mentioned travelling down before, so if you imagine, like, the file system is a tree right with the root of your drive at the very top of the tree, and all the leaves and nodes represent all the directories, right?  And when I said before, "we look down the path," we start in the directory and we look all the subdirectories. Well, what .NET Core does is when you've run an app, they will look in the directory where the app lives for a runtime that it can use. And if it can't find one, it will go up a directory to the parent directory and look there and then up another level to the parent or it all the way until it gets to the root of the drive. And then it will go into known places. So we'll look in programme files. We'll look in your user bin area - if you're on a unix, I guess.

There is on Windows, there is a defined path for `C:\Program Files\Microsoft\DotNet`, I think. And on UNIXes and Linuxes. I think it's less `usr/bin/dotnet`. Bu because you can run the app anywhere it has the ability to travel up and down the file system looking for a runtime which matches. But it will use the path first. It will say, "I am here, is there one here? Is there one in the path? Right okay, travel up on."

**Josey**

So question then what is the footprint size?

**Jamie**

What is the footprint size? Okay, so one of the one of the most interesting things - I'll prefix this. I'll give you the answer in a minute. I'm looking like a very good politician here.

**Josey**

Yes, you're filibustering. I just want to deal with the footprint is and you're filibustering.

**Jamie**

So it will depend on which APIs within the runtime you're using. So if you do a self contained build, you will get the .NET Core runtime, and if you're doing Web stuff, you may get the ASP .NET runtime as well and all of those libraries. But with that obviously comes a lot of hard drive space, so you're looking at 120, 130 megabytes to start with. But the .NET Core build tools can now do a thing that is a highly experimental called tree shaking.

So if you're familiar with Angular or Vue and linting, and things like that in JavaScript, what you can do is you can say, "I've pulled in this 12 megabyte library, but I'm only using this one API. So recompile this DLL, this library, only with the code that I'm using." So if I'm pulling in, there's a big library in .NET called JSON.NET, which helps you two serialise in deserialise into JSON and .NET types into .NET types and classes, so you can serialise and deserialise very easily. Problem is, that library itself is 20 megabytes. But if you only deserialising JSON into a known type, you only need 50, 60 kilobytes of library. So what you can do is, if you're only using this one method, it will recompile the entirety of that library with just that one method; so instantly you can see that particular library becomes 95% smaller.

And then because .NET Core is written in .NET Core the compiler can do that to itself. So the compiler could do that to the runtime. So then what originally was 130 megabytes can then drop down to 50, 60,  maybe even 40 megabytes. But the problem is that .NET stuff allows you to use a thing called reflection to  load in things at runtime that you didn't explicitly say were there. So if you do this tree shaking in ahead of time competition, then you use reflection, [and] you then try to call something which isn't there, and the whole system blows up.

But yeah, you can ship the entirety off the bits of .NET Core that your app needs with your binary. This wasn't available in .NET Framework, because .NET Framework is all tightly coupled. The whole thing is very couple to itself. Whereas .NET Core is designed, from the ground up, to be entirely modular. So you may only require the logging aspect of it, or you may only require the configuration aspect of it. And because of that you can say, "I want just .NET Core and logging," or "I want .NET Core and the web stuff and the Xamarin stuff," so the mobile app stuff, "and I want configuration, and I want this," and it will give you all of those things when you hit Compile.

**Josey**

and Mongo. I want to play with Mongo.

**Jamie**

Exactly.

**Josey**

Okay, See, that makes sense. Although I have to admit the whole concept of a tree shaking just, it's interesting.

Okay, so what I've basically gotten so far then, is that I need to understand that .NET Core is simply a runtime environment that can run anywhere.

**Jamie**

Pretty much. The most important thing to remember about that, though is: so .NET Core can power desktop applications, right? You can hit compile, and you have the desktop application for Windows. You hit compile again and you've got it fill Linuxes - obviously, I have to say "es" on the end there because Linux is the kernel isn't it, it's not the operating system - You then hit couple again and you got MacOS. You could do all of those things with a single command line switch so it will develop them all at the same time. You can then go, "make it for Xamarin," so that makes it for iOS and Android, with the flick of a switch. You then go, "make it for Blazor," so it runs in a Web browser, with the flick of a switch. A couple of lines of code needed to be added in, but with a flick of a switch, you've got all of those targets.

But then you go one step further, and you realise that Samsung have released a series of electronic devices, TVs, fridges, smartwatches, that all run on the Tizen operating system.

**Josey**

I do not want my app to run on my fridge. Just the whole concept of IoT just makes ... ugh, Darth Securitas is here. Not a good thing.

**Jamie**

Of course, I mean it's not going to be secure code at all. But the idea is that because Tizen's official programming environment is .NET Core, you push a button, you can run your up on your fridge. _And_ then you push another button and you've got it on IoT devices that are the small form factor devices: RaspberryPi or [the Meadow Project](https://www.wildernesslabs.co/meadow), which is another device that has a bare-bones operating system and .NET on top of it.

**Josey**

Will it run on an Arduino?

**Jamie**

Yes. There is a runtime called [Netduino](https://www.wildernesslabs.co/netduino), which is .NET on the Arduino. So it literally runs anywhere.

**Josey**

Okay, but what you should say is:

> but wait, there's more

Okay.

**Jamie**

But wait, there's more.

You ever heard of the videogame engine Unity?

**Josey**

Let's see, in many years is it came journalist and a gamer? I don't think I've ever run across anything called Unity -  Assassins Creed, right?

Of course I've head of Unity. Go on.

**Jamie**

That one's .NET, too.

So you could push your button and, essentially, import it into a Unity game and have it running on the Nintendo Switch, or the PlayStation, or the Xbox, or a PC runnning Windows, or anything that Unity targets. So, yeah, it really does run anywhere.

### What Are My Resources Here?

**Josey**

You know, I know we're coming to the close of the episode, and I've basically come in as resistant as I possibly can be to .NET Core.

**Jamie**

Yes.

**Josey**

Like I said, the barrier to entry is way too high and trying to find good quality resource is to learn on the go is really hard. I mean, we haven't even touched really on too much beyond that. I mean, basically the show is complaints with, "and then but wait, there's more."

You know, you have actually convinced me to put the time in to find the resources. And that's how limited our time is in today's day and age, whether it's the companies we run; the clients we work for; the companies we work for; family; entertainment, and all the other things that go with it. You've actually convinced me to put time aside to dig into this, and find the proper resources to learnt this. And that's saying something.

Now, Whether or not this progress beyond just in initial, "interesting, I kind of get it now." We'll see; because for me, and I'm sure this is the same for a lot of people, when learning something, I need to have a project. I can't just go, "OK, I pressing a button, and yay I can do the [Towers of Hanoi](https://en.wikipedia.org/wiki/Tower_of_Hanoi)." Yay, bubble starting. Don't even get me started on sorting algorithms. Oh my God.

But that means nothing to me. To me, it's the practise application of things that matters. Now I have several projects sitting around part done, in quite a few different languages because time; lack of drive; be realistic laziness. You know those kinds of things, but there has to be a spark that keeps me going. And I think what might keep me going on this, and we'll have to do like a check-in in the future - if people care to have me back, or if they're bored with me, they could let me know - but if in the future we do a check-in again and it could be, "Well, what did you do with the information? Did you actually study it, learn it? Or are you a proper convert?" I mean, it'll be interesting to see what happens, but the fact is, I now actually want to put time aside. It's not just, "it'll be kind of cool thing to do when I, you know, have a moment." It's now, "where can I fit this learning process in?"

And that is a bigger step than I think anyone could have gotten. I mean, Chris. I love my co-host, but my goodness, he has like .NET Core is his thing, it's his baby. And he has tried to explain it to me. And I probably didn't ask the right questions, because when he and I talked, and we talk dev and everything, and all over the place. Because he's enterprise, and I'm not right. So there is, like, this slightly different mind set between the two of us, which works great for show, but not necessarily for the sit down educational process.

But you've literally convinced me with this show to learn. And now you do realise that I'm going to be on your case when I'm like, "what? What? My resource is here?"

**Jamie**

Okay, well, how about I give you a bunch of resource is now?

**Josey**

Why, yes. I don't think that would hurt it all. It's not like others listening could not make use of this. This was not planned. It really wasn't actually

**Jamie**

Okay.

**Josey**

But I also expect these to be on the show knows. So that, you know, two weeks from now or a month from that, when I finally get a chance to sit down to do something those resource is better still be usable; better still be good; and better not make me download version 2 or 1.0.

Don't make me use JSON. But anyway,

**Jamie**

Don't worry about that. They've officially abandoned everything to do with that `project.json` thing. It was a nice experiment, but it didn't really go anywhere. And it got too complicated, because then the build tools - there's a tool called MSBuild, which is what is used to sort of bootstrap the building process - MSBuild got inherently, stupidly complex because it had to support both the XML and the JSON built project types.

**Josey**

Bloat comes from bad decisions.

**Jamie**

And then obviously, when they said, "right, .NET Core, 1.0 is no longer supported," they were able to wipe that out of the MSBuild tools, which is wonderful. I think it's the one time that Microsoft haven't been, "we need to be 100% backwards compatible," because I think that they realised it was - I don't want to say a mistake, just ah, maybe a poorly timed decision, because they're trying to get as many people to move across and the tools didn't work or whatever.

**Josey**

You know what? This is gonna sound so kind crazy weird, but at the same time it shows the tangential track my mind takes.

But I wonder if this is why so many games for Xbox are starting to be backwards compatible. This whole in the gaming industry with consoles, it's all about like, "Oh, no, the PlayStation five is coming. Does that mean that anything from PlayStation four is backwards compatible or not?" Like all of the the gaming issues. But Microsoft seems to be a lot further ahead along the trend, and I'm wondering if because of .NET Core.

**Jamie**

It could be. But part of that is also, you have to look it the way that Microsoft have always produced their operating systems. So Windows inherently, even though - let's pretend I don't know whether you are, but let's pretend that you're running Windows 10. I don't know whether you are, I'm definitely not. I'm running Pop!OS 19.10. But let's say you're running Windows 10, your Windows 10 machine - you have to futz with it a little bit - but can run all binaries all the way back to Windows 3.1.

**Josey**

Sort of.

**Jamie**

Yeah, I'm not saying you should. And there's a lot of futzing required to do it. But on top of that, So for instance, Creative Suite 2: we talked a little bit about Creative Suite off air, right? Creative Suite version 2 required a number of hacks to get it working on early versions of Windows

**Josey**

Or Mac.

**Jamie**

They needed to be present in the Windows kernel; they are still present in the Windows kernel.

So you could still run Creative Suite two as it was first released, the vanilla version of it, on your Windows 10 machine; because those hacks are still present in the kernel and they need to be sort of transported across for every subsequent release of the Windows kernel. So what I'm getting at is that Windows is so backwards compatible because it is entrenched in that enterprise arena. I mean you'll know yourself, Josey. When a company comes to you and says, "we need to upgrade our fleet of computer hardware, but we need to make sure the applications still work."

**Josey**

Yeah, but see, this is why, in the world of Web development, you know, containerisation is a thing and way now have things like AWS and other cloud based things. Yadda yadda yadda.

So these resources: perhaps we should let the viewers hear them. Not just me.

**Jamie**

Yes, indeed. So I would go with, the first one is [learn.microsoft.com](https://docs.microsoft.com/en-us/learn/). In the past six months to a year, Microsoft have been very, very active in recreating a number of their learning tools. Before then it was [academy.microsoft.com](https://academy.microsoft.com/). There was a bit of a sort

**Josey**

MSDNAA

**Jamie**

Yeah, pretty much. And it became kind of gameified. So you would pass a course, and you get a certificate, or you get 50 points, or whatever. It didn't mean anything. But the idea was obviously to get you to do more of these courses, I guess, than you friends or your colleagues or whatever.

But [learn.microsoft.com](https://docs.microsoft.com/en-us/learn/) is a completely rebuild of the entire system. I mean, he actually has tracks the you could follow for .NET Core. So you are complet newb, and people like Scott Hanselman and Kendra Havens - a number off prominent Microsoft educators and outspoken prominent Microsoft people - take you through going from, "I know nothing about .NET," to "I have a website open running."

Some of videos are very much a case of, "let's go all the way back to basics and say, you know, this is a source file on this is a namespace," and some of them jump straight into the deep end with, "you have your website up and running. And we're gonna add middleware, and a bunch of things to do stuff." So there's the progression is what I'm saying. It doesn't just go, "part one: you know nothing," "part two: [draw the rest of the owl](https://knowyourmeme.com/memes/how-to-draw-an-owl)". It's very much a case of learn this; learn learned; learn this.

Some of them are a bit slow, but they are designed for everyone to sort of follow along. And they and they are supported by Microsoft. With that, there is [docs.microsoft.com](https://docs.microsoft.com/en-gb/) - so that's docs period microsoft period com.

**Josey**

That's been there forever.

**Jamie**

Ah, yes, but this has been rebuilt completely. So this is completely open source documentation. If you spot an issue with their documentation, there's a link on every single page for the GitHub version of that documentation; you then submit a pull request, and your change is live on [docs.microsoft.com](https://docs.microsoft.com/en-gb/) within 15 minutes.

So the documentation is always up to date now. On each page there's a drop down for which version of .NET Core you're playing with; it will always assume the vLatest that is in long term support, but it lists all of them. So if you go to one of the pages now, I think it should say .NET Core 3. And then there's a drop down and it'll say, .NET Core 3, .NET Core 2.2, .NET Core 2.0, .NET Core 1 - although it's not really supported anymore. So you can say, "I'm actually supporting an old app that runs .NET Core 2.1," which is still long term support, even though .NET Core 3's out. And you could say, "I have this project which is running [on] this, and I need to know how to do this." So that's always really useful. You can always read the docks.

Another really useful thing, but only once you've started playing around with .NET Core, and if you have a background in .NET Framework - or .NET classic, or .NET Full Fat as I call it - is [apisof.net](https://apisof.net). Which allows you to search for a type; an API; or a class; or a namespace, and it will tell you which versions of .NET support that. So it'll say, ".NET Framework supports it from 4.2; .NET Core supports it from 2.0; Mono supports it from this particular build number, Xamarin and Unity and all of these". It will list which versions of what things support that API. And it will also list if, for instance, it only has partial support; it will say, "this class is implemented. But these two API aren't, so you can't use everything," so that helps you if you're migrating a Framework app to core; or a Framework up tro Mono; or you're messing about and chopping and changing between the two; or between the three: to Mono, to Xamarin, to all of these different platforms. You can see which versions of what support which APIs. That's a really, really horrendous way of saying it, but I think you get what I mean.

**Josey**

I get what you mean. I hope other when listing does. If not, you can totally blame him.

**Jamie**

That's right's definitely all my fault. That's not a problem.

So I would go with those two. There are a number of Pluralsite courses. If you have Pluralsite, I do have it. But I've forgotten the names off some of the people. I can always put some links in the show notes, but that's a paid service. So that's something that you would have to obviously go out and pay for.

**Josey**

Pluralsite site is. I mean, honestly, if you are interested in your own education in the IT world, Pluralsite is the best investment you can make it yourself. So even if your company doesn't cover you, and no this isn't sponsored, but damn it, we should be. Well, everyone should... Well, I say "we" because I'm thinking of [Documentation Not Included](https://www.dnistream.live/), but you should be, too. Just saying.

**Jamie**

there's also an incredibly short - I don't want to put people off by saying it short, because it's very feature rich. There's a book called [.NET Core in Action](https://www.manning.com/books/dotnet-core-in-action), and that was written by one of the first guests on this show called Dustin Metzgar. And that essentially takes you from, "I have no idea what .NET is," to "Oh, I have some idea of what .NET is." And that's available via Manning publishing. So you know there's a cost involved in that, too. But that's a really good book, and it goes from, "no idea," to "some idea," along the route of, "Let's learn the debugger and things."

**Josey**

The thing that turns me off from books - and this is not to say I'm not going to look at it in this book, or anything else like that. It's more: the thing that tends to turn me off with books is, Oh, wow, this is gonna make me feel so, so, so, so, so old. I recently found a book for PHP that it's old. I think it was published before I was born, and as I said at the start of the show, I'm pretty old. So information gets outdated so damn quickly. So will this become outdated?

**Jamie**

So the book itself was released in, I think. 2017

**Josey**

2018  It's okay. Time travelly, Wibbeley wobbley stuff.

**Jamie**

Exactly. So the author was part of the .NET Core Team. So at the time, things were in flux. But a lot of what's in the book is still applicable to a .NET Core

I would say [learn.microsoft.com](https://docs.microsoft.com/en-us/learn/) and [docs.microsoft.com](https://docs.microsoft.com/en-gb/) first, and then for more of a sort of theoretical grounding - if you really want to get into the nuts and bolts - [.NET Core in Action](https://www.manning.com/books/dotnet-core-in-action). He does go through it a certain piece of certain velocity, because the Manning inaction series is all about going from no knowledge to, "I have something that is built." So it does sort of make a number of small leaps but explains those leaps after you've... leapt to them? Is that correct?

**Josey**

I get what you're saying.

Out of curiosity, why that particular the guy on the cover?

**Jamie**

Oh, I don't know. I'm not sure why Manning choose to... All of their books have-

**Josey**

Historical figures.

**Jamie**

Yes, I mean, it's like the O'Reilly books. the O'Reilly books all have animals, and it's like, "well, what does an owl have to do with nodeJs?"

It's explained in the publisher notes or whatever. It's an interesting story as to what the image is. They don't explain why I think they're literally just go, "we haven't used this image yet."

**Josey**

I was just curious.

**Josey**

All right, cool. So those multiple resources. And anything else you want to throw out there?

**Jamie**

I mean, this podcast?

**Jamie**

I mean, it is primarily an interview show, but the first few episodes are "What is .NET Core?", "What is Mono?", "What Is .NET Standard?". So there's a little bit of a theoretical grounding there for if you want that sort of detail. But I also have a number of streams that are available. They were originally done on mixer but then I edited them, and threw them upon to YouTube. And I think you can go to you to [youtube.com/c/](http://www.youtube.com/c/JamieTaylorDotNetCore)  I think it's Jamie Taylor dot net or something. I can't remember the url, but I'll put it into the show notes. And a soon as I figure it out, I'll send it to you, Josey. Either that you go slash channel and then a bunch of characters. I don't know what it is.

But yes on that page there are a number of videos. Some of them are episodes of this show, because there are people who legitimately like to consume podcasts via YouTube; so let them do that. But in there there is a playlist of live streams. One of them, I believe, is me going through, "I have no code," all the way up to, "I have a built application," in about two hours. You talked about implementing certain algorithms? Well, I implemented [Fizz buzz](https://en.wikipedia.org/wiki/Fizz_buzz) entirely in .NET Core using [TDD](https://en.wikipedia.org/wiki/Test-driven_development).

**Josey**

You know what? I'm gonna actually have to go look at your Fizz buzz, because it can say so much about someone.

**Jamie**

Fair enough/

**Josey**

And I am going to peer over your shoulders into your choices for how you implement that particular algorithm. So that I can then, you know, narrow my eyes at you and be like, "Oh, you're one of those."

[I'll] get to be ah, really good manager who got their MBA in business management instead of programming, development, or working their way up the stacks and going, "you're not doing it right." "I don't even know what I'm doing. Go away."

Wait, wait. Let me use all the buzz words and all of our ducks in a row and, you know, have all of the hymn sheets. It's in the same book or something.

**Jamie**

Have you ever seen the [Enterprise Fizz buzz](https://github.com/EnterpriseQualityCoding/FizzBuzzEnterpriseEdition)?

**Josey**

No, I haven't.

**Jamie**

Okay, I'll put it in the show notes. It's Fizz buzz, is written in Java, but for the enterprise. So everything is dependency injected; there are tests that mock the entirety of the framework, and all that kind of stuff. It is ridiculous.

**Josey**

You know, I have to say if a framework not take being mocked, they shouldn't exist. Because the people who end up mocking frameworks the most, regardless of what type of framework it is, are you sure the people who love it.

**Jamie**

I agree completely. That's an exercise for the listener, and an exercise for you for later on. It's got nothing to do with .NET Core, but it is fantastic to read.

**Josey**

Well, Excellent. Okay, well, thank you very much. I'd leave with homework.

### Where Can Listeners Find Out More About Josey?

**Jamie**

Thank you ever so much for being on the show, anyway. Even though we had some technology problems, it was a blast talking to you. One of the things that I always round these off with is: "tell us a little bit more about how we can get in contact with you, and all of the projects here interested in, and the things that you're doing," you mentioned [Documentation Not Included](https://www.dnistream.live/). Tell me all about it.

**Josey**

Well [Documentation Not Included](https://www.dnistream.live/) is the podcast that I run on a weekly basis, which is actually also a vodcast because unlike, you know, smart people who pre-record, who can then edit and cut things, we do it live. We live in the cutting edge of our discussions. But no, Documentation Not Included is all about development, and not just development. It's all flavours, etcetera and including because Chris, my co-host, and I, we run her own companies; and for some they're contractors, for us where companies that get hired for our services in my case, you know, managed services along with some virtual assistants. Whereas Chris actually does enterprise type solutions and other things that go with it. You can learn a lot about him by just going to [Documentation Not Included](https://www.dnistream.live/). And it is there that you will find all kinds of ways to link to us because we use three directions.

Other than that, I have to bring this up only because I am an incredibly proud ambassador for [Gitkraken](https://www.gitkraken.com/), which is a visual get client. So I try to bring them up were I can. I don't bring it up on DNI because we have a certain philosophy where, you know, we try not to push technologies, but it's not my show. So I get to push. But yes, I'm an ambassador for Gitkraken, and I highly recommend it. And for people who may listen to this for the, "why should you learn something?" or "how do you even get started?" That is really a good title for this episode: "How do you even start?"

I highly recommend also getting involved in your you know, the visual side of things with Gitkraken for git because, oh my gosh. If you ever I wanted to really see how it all links together in a very pretty interface, then you definitely want Gitkraken.

Plus, I mean, come on. Their mascot is Keith. Keith is this adorable, like octopus type, kraken and monster thing. And I absolutely love Keith, and They designed Keith version for [Ada Lovelace](https://en.wikipedia.org/wiki/Ada_Lovelace), actually on my recommendation. Which I hold very near and dear to my heart - one of the first female programmers.

Yeah, Other than that, the things that I find interesting in life are reading. Reading, and development; and just learning actually. The biggest thing I want to say if if anyone actually listens this far, you know, reach out to me on my Twitter at [@joseyhowarth](https://twitter.com/joseyhowarth), and just say hi.

I want to meet more and more people. It is hard for me to leave the house right now, so having my developer community online.

**Josey**

It's one of the things that fascinates me about technology. I mean, our voices are ones and zeros right now, and yet there is more to it than that. You get tone inflexion volume like it's crazy. I'm not gonna go Brian Blessed. But yeah, just reached out to me, say hi and let me know that you've heard something. And if you've got a bit of advice or suggestions and the .NET Core world, send it my way, I would like to know. But I'm going to open source my learning process case may be.

**Jamie**

I like it.

**Josey**

I will stress one of the big things that I want people, if you are listening and you actually cared to get involved in, send me things about the security side of things for it. How do you make certain it's properly secure? How do you do all of the things that go with it? Because in the end, if I run across something and I see that you know there's no real proper fix for it other than hacks as a case, maybe I'll cry a little bit and it might actually turn me off from it.

so send me security things I want. And I want to know the security side of things too.

**Jamie**

That's interesting, because I have actually created; so in dot net, we create packages that are called NuGet packages. I don't know the etymology as to why is NuGet, but it's essentially a zip file with all the code that you can add as a library of dependency for you app. And I have created an HTTP middleware that injects the [OWASP recommended security headers](https://www.owasp.org/index.php/OWASP_Secure_Headers_Project) and values into the response that your application will generate when it receives a request. If that makes sense.

Thats's a really complicated way of explaining what it is, but yeah, so we would be interested to see what you think about that. It's all just strings at the end of the day, but yeah.

**Josey**

Yeah.

**Jamie**

So just real quick, then when does DNI steam live go out? Because you mentioned it was a vodcast, and it's live and stuff. But when does it go out?

**Josey**

Well, it is Thursday's UK time. 7 p.m. on [twitch.tv/dnistream](https://twitch.tv/dnistream). I didn't include it because all our links are on our website: [dnistream.live](https://www.dnistream.live/). We're on things were just like, "Oh, we exist out there. Oh, we're on there too." We're everywhere. You can listen to us. You can make fun of us, and hell if you want to be on our show get in touch. We talk about absolutely anything and everything. We're not platform dependent. We are the .NET Core of podcasts for developers.

**Jamie**

I like it.

**Josey**

Did I make it relevant? Yeah, I so

**Jamie**

Yeah.

**Josey**

Awesome.

**Jamie**

Obviously I was on an episode as well, but I wasn't talking about .NET in the slightest, was I?

**Josey**

No, we weren't. We were talking about static site generators, and frameworks, and stuff.

Thank you so much for having me on. Thank you so much for being willing to face the firing squad of one who just is literally looked into and then got fed up with it. And then just said, "blugh"

**Jamie**

I think everyone needs that kind of person around, the person that will look into it and give up and they go to someone go, "go on then why should I? What's what's so great about it?"

**Josey**

Yeah.

**Jamie**

Well, thank you very much, Josey for spending of time with us, and talking to me and getting me to answer questions. It's a nice little revolving chairs, my analogies part of my brain is-

**Josey**

Role reversal/

**Jamie**

That's what I was trying to think off. The analogy. Part of my brain is all broken now.

**Josey**

I'm sorry, listeners. I broke Jamie.

**Jamie**

That's right. I've got a null reference exception happening. That's what it is. Segmentation fault.

**Josey**

Hey, that is something I could put on my CV. I broke Jamie from .NET Core.

**Jamie**

Thank you ever so much, Josey. I really appreciate it. It's like I say, it's the evening. We all need time to chill out in the evenings, we've gone over our allotted time by I almost a whole hour because of a few technical issues. But, you know, we got there in the end, and I have answered a few questions. And maybe we could check-in with you in a couple of months, maybe in six months maybe in a year, see if you've built anything.

**Josey**

You know what, I think that would be good, because one of the cool things is if you have someone that you are held accountable to. That's what mentor is gonna be really, really good for.

So yeah, hold me in .NET Core accountability.

**Jamie**

Ok.

**Josey**

Well, thank you so much again.

**Jamie**

You're very welcome. Thank you ever so much for agreeing to spend the time to talk to me for a while.

### Wrapping Up

That was my interview with Josey Howarth. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and a full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/).

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Josey Howarth on twitter](https://twitter.com/joseyhowarth)
- [Documentation Not Included](https://www.dnistream.live/)
- [Love Sudo](https://www.lovesudo.com/)
- [The waffling Taylors](https://wafflingtalyors.rocks)
- [source of the oiltanker analogy](https://dotnetcore.show/episode-30-reflections-on-net-with-pablo-santos-and-phil-haack/)
- [try.dot.net](https://try.dot.net/)
- [Fibonacci](https://en.wikipedia.org/wiki/Fibonacci_number) 
- [The Meadow Project](https://www.wildernesslabs.co/meadow)
- [Netduino](https://www.wildernesslabs.co/netduino)
- [Towers of Hanoi](https://en.wikipedia.org/wiki/Tower_of_Hanoi)
- [learn.microsoft.com](https://docs.microsoft.com/en-us/learn/)
- [academy.microsoft.com](https://academy.microsoft.com/)
- [docs.microsoft.com](https://docs.microsoft.com/en-gb/)
- [apisof.net](https://apisof.net)
- [.NET Core in Action](https://www.manning.com/books/dotnet-core-in-action)
- [Jamie's YouTube Channel](http://www.youtube.com/c/JamieTaylorDotNetCore)
  - [TDDing, Fizzing and Buzzing](https://www.youtube.com/watch?v=GG_toHeMC_k)
  - this is the video where I go from no code to Fizz buzz with TDD
- [Fizz buzz](https://en.wikipedia.org/wiki/Fizz_buzz)
- [TDD](https://en.wikipedia.org/wiki/Test-driven_development)
- [Enterprise Fizz buzz](https://github.com/EnterpriseQualityCoding/FizzBuzzEnterpriseEdition)
- [Gitkraken](https://www.gitkraken.com/)
- [Ada Lovelace](https://en.wikipedia.org/wiki/Ada_Lovelace)
- [OWASP recommended security headers](https://www.owasp.org/index.php/OWASP_Secure_Headers_Project)
  - [OwaspHeaders.Core](https://nuget.org/packages/OwaspHeaders.Core/)
  - This is the NuGet package that I created
- [twitch.tv/dnistream](https://twitch.tv/dnistream)
