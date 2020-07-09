# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is Episode 36: .NET Core and the Raspberry Pi with Al Rodriguez. In this episode I interviewed Al about creating applications for the Raspberry Pi, and other IoT devices, with .NET Core. Some of you may know Al from is podcast "[Developer Side Quests](https://www.developersidequestspodcast.com/)", or his blog at [programmerAl.com](https://programmeral.com/). Shortly after we recorded this interview, Al placed his podcast (Developer Side Quests) on hiatus. However, it's still worth checking out - and not just because I was on episode 7; check the full show notes for a link.

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Al's Introduction

**Jamie**
So the first thing I'd like to say Al, is thank you ever so much for taking some time out to be on the podcast. I know that we're at an absolutely completely different time zones. So sort of organising things and having to sort of re-arrange it slightly because of me, unfortunately, at the last minute, can be a bit hectic. So thank you ever so much for being understanding and taking the time out.

**Al**
Oh, no problem. No, I mean, it's so happy to be here. I'm really excited to jump in and start talking about all this all this fun stuff, because this is what makes me happy.

**Jamie**
Excellent. I thought before we get to today's topic, could you maybe sort of introduce yourself to the listeners?

**Al**
Yeah, sounds good. So I'm Al Rodriguez, a generic everyday developer, doing development related things in my free time. And for the most part, my background is pretty much just all been in C# .NET since I started, I guess, started with it in college. And I've kind of branched out in a few other things. But for the most part, I kind of specialised in the C # .NET camp of stuff. And then recently, I've kind of started jumping into the embedded IoT space. So that's kind of been a fun passion of mine for the past couple of years, and haven't done anything work related. But you know, all my fun, crazy projects at home have definitely benefited from that. But yeah, it's been a lot of fun, except for the few times that I've had to jump down and do things and embedded C on an 8bit microcontroller. Because that's, that's its own special level of fun. But it uses a different definition of fun that I think for that, but yeah,

**Jamie**
Yeah, I can, I can totally appreciate that. My very first programming job out of university, I was working alongside some very low level hardware. And we were building like a Windows Forms app that would communicate with the hardware. But we also had to sort of, we had to maintain the firmware as well. And that was low level saying this was a very custom bespoke device. So I can totally understand how difficult was sort of keep on top of that, and add new features and all that kind of stuff?

**Al**
Yeah, I like to refer to it as the hair pulling work.

**Jamie**
That will explain why I have no hair. Oh, dear. Oh, yeah, obviously, as well, you have your own podcast as well. Would you mind telling the listeners a little bit about that?

**Al**
Yeah. So I'm the host of Developer Side Quests. And so every two weeks right now, we're putting out a new episode where I interview other developers on the projects that they work on outside of work. So the things that we usually use to learn and level up our own skills. And, Jamie, you've been on the show, which came out a while ago, I realise that I haven't actually asked you when this episode of the .NET Core Show will go out. But I guess I don't know, a month ago, in relation to when this drops, maybe two? I'm not sure.

**Jamie**
Yeah, I'm not entirely sure when this episode will drop. Unfortunately, I've got a bit of a tiny backlog of episodes to get through for editing. And so inside baseball fans, were maybe recording this a month, maybe two before it goes out. Just simply because I have that many editing things to do. And, you know, I run another podcast as well. So trying to do both of those and do full time job stuff and do outside of work stuff. It can be a bit challenging at times, but I love it. I love doing it.

**Al**
Yeah, I feel like that's a regular issue with podcasting of just remembering when an episode is going to go or planning it because the the other podcasts that I do, where we talk about all the Marvel movies and TV shows, it's the same thing, like we have a schedule written down to if one episode is going to come out, we don't even think about it ahead of time when we start recording. And we'll mention things and realise that we're recording and have no idea when it's actually going out either. So it's probably a regular thing for everyone.

**Jamie**
Oh, definitely. I know that I've done that with my, the other podcast I do is called the Waffling Taylors, which is just me and my brother talking nonsense about video games. And occasionally we'll record for maybe three or four hours. And I think, "that's three episodes right there." And then when I come to edit it two months later, I'm like, "Ah, right. Okay, so we talked about this particular thing. And it has since been proven to be false. Do I need to put a disclaimer at the beginning?" do any to, you know, it gets a bit it gets a bit of fun trying to sort of harangue that. And then we had a series of episodes that came out just sort of E3 adjacent. So there was it was a three parter. The first part came out before E3, the second part came out during E3, and the third part after E3, we're all three were recorded a month before E3.

**Al**
The magic time shift.

**Jamie**
That's it. I like to call it the "time cast pod machine wibbly wobbliness".

**Al**
I like that phrase. That's that's a lot better. Yeah.

### .NET and IoT Devices

**Jamie**
Okay, yeah. So regarding today's topic, we're going to talk a little bit about Raspberry Pi and embedded devices, maybe a little bit of IoT, a little bit .NET Core a little bit .NET for sort of .NET technologies, because at least less than a year after this episode comes out Microsoft are rebranding .NET, and they're renaming it so everything's going to be .NET. Mono, Xamarin, .NET Core, its all becoming .NET. So I think the very least for this episode, if we just say .NET just to simplify things, it might be a little easier.

**Al**
Yeah, that sounds good to me. And that's going to be a whole fun conversation once once that actually, you know, becomes a thing: .NET 5 and all that because I still have no idea what that means for the embedded side of things, or at least the IoT stuff with C# and .NET.

**Jamie**
Yeah, it's gonna be a fun couple of months next year. And then I feel like the year after there might be a mad scramble to try and get as many people involved to convert legacy .NET Framework apps to, what's the phrase I'm looking for: "contemporary .NET stuff". So that'll be fun. Keep us all employed, I guess.

**Al**
There's never a shortage of work. That's always true.

**Jamie**
Exactly, exactly. Okay, so we're going to talk a bit about Raspberry Pi, right? So I have - and I did a count of them a few hours before we started recording - I have five different models of Raspberry Pi in my house: I've got the OG model B - so the Raspberry Pi model B - three model 3S's, and a Raspberry Pi Zero. And I'm going to be getting some of the new, at least as we record this, the new Raspberry Pi 4s in the next couple of weeks. So is it possible then to write .NET apps for all of these? Or is it just like the latest ones?

**Al**
So that is unfortunately a loaded question.

You know, like everything in technology, right? It depends. But to answer your question directly, yes, you can. And really quickly, I want to say I think you have me beat on Raspberry Pi's. I think I only have four. So

**Jamie**
I mean, I've only got one in use. So.

**Al**
And that was the other thing I was going to ask How many are you using? Yeah.

Yeah, so it's a really just to jump into it. The the ability to use, you know, C# and .NET on a Raspberry Pi has been there for a while, like ever since the Raspberry Pi even first came out, you've been able to use Mono to write .NET applications on the Raspberry Pi. And there are benefits of using Mono. Even now that we have .NET Core, there might be a reason that you would choose Mono over .NET Core. Mainly, the big reason is AoT - ahead of time compilation. Because that is something you can do with Mono right now that you can't exactly do with that .NET Core. So it kind of comes down to one of those things.

On the  .NET Core side of things as far as writing an application for running on your Raspberry Pi. If you're going to the whole Linux route. Currently, as it stands, it's a little bit weird as far as the arm 32 versus the arm 64 instruction set. So now I have to worry about you know, bitness and, and all that stuff. So that's a little bit of a headache. The the first fully official version of .NET Core that you can run on a Raspberry Pi, like the fully supported one, I think is only 64 bit, I don't think they're doing 32. And I could be wrong. I really should have looked that up ahead before saying that. But you know, disclaimer, if you look that up, and it turns out that I'm wrong, cool. But if not, then all right. Well, that's, that's an unfortunate, you know, one of those dependency issues that we always have to work around, especially when you're, when you're working on things like this, where you have to worry about the you know, the actual hardware, like you have to care a lot more about the dependencies.

But tangent aside. You know, everything that I've said so far has been specifically if you're using a Linux operating system on the Raspberry Pi, but another option is taking windows 10 IoT, and throwing that out there. And now you have a whole different set of of options of what you can run on the Raspberry Pi itself. If you're writing applications there, you're using UWP application. So that's, that is .NET, but it's not .NET Core, it's not Mon, it's kind of its own separate special little thing. And pros and cons there: you have a lot of stuff kind of built in for making a UI for the application itself. You know, UWP has some pros and cons there. But you also get some other stuff just kind of built into to make it quicker and a little bit easier for for actually making the applications there. So I hope that answered your question, maybe not too much of a response to be able to just say yes.

**Jamie**
Oh, it covered a lot of stuff. And it, you know, it's always incredibly useful to have those sort of detailed answers. Because I mean, not so much for me as a podcast host, because you've essentially answered a bunch of my questions already. But it's always useful for the listener to be able to hear that, you know, all of that information all at once, rather than having to refer back to me in thinking, "Well, I hope he asks this question."

**Al**
Yeah. Oh, and I mean, just, like throwing that out there for this. You know, that's, that's kind of like part of the reason why I wanted to start the developer podcast, just because there are so many times where I hear just the generic thing of, "I kind of want to dive a little bit deeper into that." So whenever I try to answer a question, I kind of, I feel like maybe sometimes I answer a bit too much. But yeah, I tried to just, you know, get it all out there. So you know, at least we have a nice start for the conversation, something that somebody go with.

**Jamie**
Exactly, exactly. So we talked a little bit there about arm 32 and arm 64. And you mentioned windows 10 IoT Core. So I just want to cover those things a little bit more, if that's all right.

So, as we mentioned earlier on, you know, I've done a little bit of embedded programming. So I know, kind of what the difference between arm 32 and arm  64 is, and then I suppose a lot of people who have maybe built their own systems will know what, you know, 32 versus 64, is for CPUs. But I just thought, could you really sort of really quickly, briefly, if possible, describe what the difference between arm 32 and arm 64 is without going into all the details of, "well it has this instruction, and that one has this instruction", just sort of like the brief overview of the differences, I guess,

**Al**
yeah, no problem. And I will keep this brief because I don't think I can even go anywhere near as detailed as he told me not to go. So I think that's perfect.

The, you know, when you when you talk about 32 bit versus 64 bit like there's the technical reasons behind it. But in the end, it's it's just a dependency as far as the application goes. So if if you take a 32 bit application, you can probably run it on a 64 bit processor, if you do that the other way around, if you go from above at 64, down to 32. That's not going to work. And that's that's just one of those dependency things that happens. And then has to do with the different types of instructions that are supported and, and how the processor starts loading things in a memory and all that fun, crazy stuff.

But if you're worried about this, the easiest thing to do, especially with the Raspberry Pi, is to just go online and look at which one you have. I believe the Raspberry Pi's and the original ones, the one and the Raspberry Pi twos are both 32 bits, and the PI threes and the new PI fours are both 64 bit. So for the most part, if you if you go out and you buy a new Raspberry Pi four today, then you're pretty good on support for everything. Where things get a little bit difficult, and something that that might trip you up, because it's definitely trip me up is making sure that the operating system you put on there is of this same bitness. So if you go to, I think it's [raspberrypi.org](https://raspberrypi.org), I try to remember the URL top of my head. But basically if you go to that site, and you get the suggested for newbies, the Raspberry Pi OS, then that I believe as it stands today is 32 bits. And I don't know if there's a 64 bit version of that operating system. And that bit me because I tried to put that on a 64 bit raspberry pi, which I believe still worked. And it installed, I think, but then I had some trouble running other applications, I had the issue where I was running the 64 bit version of .NET. Core.

So just kind of going back and forth, as long as everything is that that same number, you're going to be good. When you start mixing and matching. That's where you can have some issues.

**Jamie**
Okay, so from a, let's say, a desktop or web developer point of view, let's see, we're talking about a full stack web developer, usually, you know, we don't have to worry about where the app is going what operating system. At least, you know, as a let's say Node JS application, you don't usually have to worry about operating system bitness, versions of packages that are supporting, all that kind of stuff. But we are saying is that with the Raspberry Pi or any other embedded devices, there's a lot more to think about, as you go into it." Which version of the operating system am I on? which version of Framework? Are they using?" Maybe, "what version of supported NuGetr packages, libraries, that kind of thing," a little bit more planning involved, I guess.

**Al**
Yeah. And that's, that's unfortunate, just because of the space that we're in, when you're when you're on something that low level, you're you don't have the same abstractions that you do when you're on the web side of things, right. Because if you're doing you know, JS, if you're you know, all that JavaScript, that kind of stuff, you're so far abstracted that you have your code running on a virtual machine. And then that's all being taken care of by the actual underlying code of whatever node JS runs on top of. And to be fair, there's a little bit of that, with, you know, being able to run .NET on something like Raspberry Pi, your code for the most part is going to be the same, like you're not really going to have to worry about how you write your code is a 32 bit versus 64 bit how you compile it. However, that's that's the difference. And for the most part, that's just kind of clicking a button. But it is that paperwork of just making sure that you select the right thing. And that's, again, just because of the thing that we're we're having to worry about, especially on like the desktop or mobile at this point, it's rare, that something is going to be running on 32 bits on, you know, a desktop laptop, even a cell phone these days, just about everything, 64 bits. So it's not going to be a normal case to worry about it. It'll happen, there are those those edge cases, but not as big of an issue

**Jamie**
Sure. I mean, I still remember, the early 2000s probably happened lot farther back than that. But I remember the early 2000s in university when everyone was going, the world's going to be 64 bit in like two years, and no one will ever run 32 bit apps ever again. And everything will be 64 bits. And we'll be in this wonderful wonderland. And, you know, we got to, I think it was two weeks ago as of recording and Steam, Valve sorry, said that they weren't going to support 32 bit operating systems anymore for their Steam platform. They've since I think step back from that. But yeah, this is like, maybe 12 years later. And we're still running 32 bit operating systems with 32 bit dependency. So it's a it's a slow burn. And I think for a lot of maybe for a lot of developers who haven't had to deal with, "which, you know, which CPU am I running? And how much RAM do I have?" And all that kind of stuff, it's a bit of a shock, I guess.

**Al**
Yeah. And at the same time, if you've written a 32 bit application, and you just want to keep keep it running on 64 bit, that's fine. I mean, operating systems candle that for the most part, as far as an application goes, Visual Studio, as far as I know, is still a 32 bit application, even though it's been around for so long, which is funny to me, because Visual Studio code is a 64 bit. So it's just kind of funny how those, those work. Yeah.

**Jamie**
I know at least as far as 2017, Visual Studio still a 32 bit app, which is one of the reasons why it can be a bit slow from occasional use, and how if you instal things like re-sharper and things like I can sort of chug along and not really look like it's responding. But that's because everything's happening within that 32 bit process. And you know, for the people who know a little bit about it, but not too much. The biggest difference, I guess, is it's called 32 bit or 64 bit because that's how much you know, address space you have for commands and data and how much RAM you can you can address. So the more bits you have, theoretically, the more data you can process at once, essentially.

**Al**
Yeah, I believe it's something along those those lines. I'm, I'm scared of getting it wrong. So I'm just going to agree. And I'll stop there.

**Jamie**
I will happily happily have someone come along and correct me because I don't mind learning by getting it wrong. I don't mind. So, dear listener, if you know what the biggest difference is, and you could put it across in a sort of tl;dr way, please let me know and I will issue a statement and redacting my statement or correcting it, or whatever it is I need to do, I'll happily do that. Because I'd like to be a little more correct about these kinds of things.

### Do I Have To Use Linux?

**Jamie**
You said a few times, you know Linux and Raspbian and things like this. And you mentioned about Windows IoT is, do I have to be running Linux to do this? So because you mentioned Windows IoT and you can do .NET stuff with UWP, but that's not really not at least not until dot .NET. Core three comes out, which will then be renamed next year. But until .NET, Core three comes out, you don't really have UWP. So do I need to be running a specific operating system to build these apps to run these apps? Or so I work in the command line? Can I do .NET build some crazy combination of feature flags to build for my Raspberry Pi? Or do I build on the Raspberry Pi? We look, there's a lot of questions there. I appreciate but how would I go about doing that? And do I have to be running Linux or Windows or Mac OS? what's the what's the plan?

**Al**
So you know, I'm going to go back to the consultants answer: it depends. And so if we wanted to focus on a .NET Core application of using that, what I've been doing, personally for my projects is I do all of my development on my Windows machine. And it's a .NET Core application, and I write it just like I would be writing any other .NET Core application, the only time something weird pops up is what I need to do something directly with the hardware, you know, that's where I can't run it locally, that kind of stuff. And so, you know, thankfully, with net, we have abstractions, and I make an interface and I just programmed to that.

But if I were to compile the application and put it onto my Raspberry Pi, my workflow has been on my Windows machine, I type the .NET Core command to build the application, I do a `dotnet publish` the application, I personally always use the self contained flag so that way, it includes all of the .NET Core stuff on there with the application, that's not something you have to do. But if you have .NET Core itself installed on your Raspberry Pi, you're good, you don't have to worry about that. But it's just the thing that I prefer to do. And then when you publish it a self contained, you do have to mention the architecture. So that's where it matters of saying, you know, the Linux arm instruction set and all that kind of stuff. So once that happen, I always just copy paste it over the network on to the Raspberry Pi. And then I just run it from there from the pi, I have a little keyboard and monitor hooked up to it. So I just type in there, I could do it remotely, I assume but never, you know, sat down and actually went through the process of getting that setup. You know, it's one of those things as a developer, we we automate so much, but then we just kind of want to really get into it. So not as much of it is is as automated as as we can really go.

But yeah, just running your application or getting it compiled to run on there. You're good with that. I think you also asked the question about compiling on the Raspberry Pi.

**Jamie**
Sure.

**Al**
So that is, as of today that I'm saying this, I believe it's not something that you can do. I might be wrong on this, because I think they might have got a little back and forth in the documentation, or I'm just remembering it wrong. But I believe when .NET Core 3 comes out, that will be an option on the 64 bit version of the arm on Linux, and I believe at that point, you will be able to compile directly on the Raspberry Pi itself. But for now, that's not exactly an option.

**Jamie**
Okay. I mean, that makes sense. Like from a pure hardware point of view, I think this is correct up to the Raspberry Pi 3, writing and reading to the SD card is pretty slow. So is reading and writing to the USB. I believe that's the case. And so that's why when the Raspberry Pi's first came out there was this big push to, "can we boot from USB?" Because it's faster.

**Al**
Yeah. And and you know, and that's, you know, comes down to that other question, right? Do you want to compile on the Raspberry Pi, maybe maybe you don't want to, maybe it's just longer to do that. Because when I when I compile on my desktop with my, you know, 16 gigs of RAM and my however many cores I have that I don't even know anymore with whatever gigahertz that they're all running at. That takes, I don't know, 30 seconds to do that. And I have to copy paste everything over the network. I have no idea how many minutes it would take on the Raspberry Pi. But I'm assuming somewhere in that range of minutes.

**Jamie**
Definitely. Because I mean, like you were saying, you know, so the whole idea behind the Raspberry Pi is as a low power device, you know, and, you know, it's running that arm instruction set, which is not the same as the x86-x64 instruction set. Because, you know, the the R in arm means reduced, I believe.

**Al**
Oh, you know, I've gone this far. And I did not know that arm. So for something.

**Jamie**
Yeah, I believe it's, I'm pretty sure is Advanced Reduced Machine Code Instruction Set or something like that. Again, I'll happily be wrong. So somebody can quite happily send me a message, send me a tweet or whatever, tell me that I'm being an idiot. But I will happily be wrong about that. But I believe that the R means reduced. And it's to do with the instruction set.

So really, really quick sort of CPU introduction: the CPU has a list of instructions that you can give it. And the whole point with arm and the reason why uses less power is because it doesn't have some of the instructions, which might take 2, 3, 4, 5, 8, 9, 10 cycles to complete. It has this reduced number of them, or maybe a reduced set of number of iterations that they can do on a on a piece of data. Sorry, I got, I got lost in my words there.

Whereas the CPU in your PC or laptop is like a general case, CPU. So it has instructions that's for almost anything that you can think of to do with maths. So adding, subtracting that kind of thing. And things like your maybe a PlayStation or Xbox, you have incredibly specialised instructions that are all to do with 3D geometry and floating point numbers and all that kind of stuff. So each set of CPUs has this different set of instructions that's going on, you know, education from back when I was a university in 2000 and _mumble mumble_; I don't really want to go back.

**Al**
That you know, everything you said there that fits with what I have been going on as far as my assumptions, and the bit that I've read specifically there. So, you know, unless someone says otherwise, I'm just going to go on believing exactly what you said. I think that's probably about right. Yeah.

**Jamie**
Fair enough. That's all right. And as long as you're saying is, it sounds about right, then that's fine. You're my expert for this episode.

**Al**
All right. High praise, all right.

**Jamie**
Okay, so we talked about whether you could build on the Raspberry Pi. And we talked about how there's different versions of the operating system, I guess you can get the Raspbian or you can get a Windows IoT. Now, if I install Windows IoT, I can do .NET, did you say? And .NET Core, perhaps maybe Mono and Xamarin. But if I instal Raspbian I'm locked to .NET Core and Mono, I guess? and Xamarin? I guess?

**Al**
Yeah. So a couple of that is, is a little different. So if you're using Windows 10, IoT Core on on a Raspberry Pi, your only option as of today is using a UWP application. I don't know if you'll be able to do UWP with .NET. Core in .NET. Core 3, I thought that that was only a WinForms and WPF thing. I'm not sure about UWP. But maybe. And the thing about writing your applications that will run on a Raspberry Pi on when you're using Windows 10 IoT is that Microsoft has their own SDK for for working with that. And so there are there own things for accessing the individual pins. So if you want to turn an LED on or off or access a motor or sensor, it's actually a really nice API for working with that kind of stuff. Whereas if you're on the Linux side of things, you can get your own from a plethora of options out there or roll your own, if that's something you want to do - which I did, I will say that was kind of a mistake on my part, I probably should have gone with the you know, already pre tested options out there that other people have made. But it was a learning experience. And that's that's kind of half the reason I did that. On the Mono side, as far as if you're making the applications. Yeah, it's pretty much you know, what I said there, you've got Mono, or .NET. Core pretty much as far as your options with those.

**Jamie**
So we have a bunch of options for releasing apps on to embedded devices on Raspberry Pi's, based on the operating system. So you would again, that's another thing I guess you need to know going in: "I'm writing this software, and it's going to be running on a Raspberry Pi, running the latest build of Raspbian which is 64 bit. So that tells me I can't use UWP. And when I build I have to do whatever it is the arcane command line switches to build specifically for x64. And then I'm probably best to build on a server or a development machine and copy it over." Whereas if I'm running Windows IoT, I could do maybe .NETT Framework, or maybe a subset of .NET Framework, I'm not sure maybe we'll come back to that. And I can use UWP if I want to. But there'll be a certain set of challenges with publishing that to the device, in the same way that there are completely different challenges for the Raspberry Pi running Raspbian, which I guess is something like I said earlier on most .NET devs, I guess don't have to worry about these things, at least traditionally. We've gone, right click publish, and either copied it to, you know, using FTP or whatever, copy it to a server, or throw it up Azure DevOps or whatever your DevOps pipeline is, and it will take care of it for you.

**Al**
Yeah, yeah, exactly. I mean, the only thing I kind of want to point out is that if you are using Windows 10 IoT, on your Raspberry Pi, Microsoft actually has a handful of tools that make moving the application and just controlling the Raspberry Pi itself a lot easier. When I'm doing this work with Linux, I'm pulling up SFTP to copy-paste those files. And then I have to manually go to the Raspberry Pi with my keyboard that's attached to it and put the the terminal and start running the application there. If you're using Windows 10, IoT, then that you kind of have this little dashboard that connects to it and keeps track of if it's even on or off. And you can deploy directly from Visual Studio. So that way, you don't have to do that all those those manual steps. So there are definitely benefits to going with with that set of tools.

**Jamie**
Okay, so there's ways in means and if you're, if you're running the windows 10 IoT, you can perhaps just right click publish, and Visual Studio will do all the magic for you. Whereas if you're running Raspbian, and there's a little bit more involved, I guess.

### What Can I Build?

**Jamie**
So if we were to build a .NET Core app for the Raspberry Pi, is it literally just a console app? Or can I use ASP .NET Core and host a web app from there? Could I mean, this might be stretching a little bit maybe, can I do a Blazor app for my Raspberry Pi?

**Al**
I believe so. The reason I'm saying I believe so is because as far as I know, I think you can, if you were doing .NET Core, I believe, as of today with .NET Core 2 your only options are console applications. I don't believe that .NET Core itself can do anything with the UI - you know, outside of now with .NET. Core 3 coming out, you know, you have the options for WinForms or WPF. But those are state windows only. So to answer your correct your question directly, yes, ASP. NET Core, that's a console application and Blazor, also a console application. So yeah, you should be able to build those and hosted directly on your Raspberry Pi and do whatever normal stuff you want. I mean, I would, you know, give the the reminder that, "hey, it's going to be a little bit slower than running on your dev machine." But if it's not doing too much, then yeah, have at it. Feel free to, you'll make that maybe make a home server sort of deal have that running on there. Cool.

**Jamie**
I can imagine building my own little sort of family scheduling app or something for everyone at my house, using a Raspberry Pi. And just maybe if I could find a cheap enough touchscreen, and wire that up, I can have you know, the week and you know, homework has too be in on Tuesday or, you know, football practice or soccer practice maybe martial arts on the Thursday, or you know, that kind of thing. And little family events. And we can all just tap the button and see what it does or maybe just have it on the screen or something. That sounds like a cool idea. And if I can run that from a Raspberry Pi, that I could maybe attached to the back of the screen. Excellent.

**Al**
Yeah, and you get all the benefits of a Raspberry Pi too, right? Because it's low powered. So you don't have to worry about all of a sudden running yet another machine 24/7 at home, you know, all that kind of stuff. So yeah, it's lots of benefits. And you have the downside of now all of a sudden you have another project to take care of. But you know, that's a whole other another issue.

**Jamie**
I think, so I run, at least on my desktop, I'm a Linux user. So I'd be quite comfortable jumping around in a command line. And so I think with if you're running Linux and pushing to a Raspberry Pi, you can use a tool called `rsync`, so that's R SYNC. And that's essentially a command line application that you run. And it uses SSH in the background to sort of push files creates a secure tunnel to that device. And you can literally write files directly to the file system on there. So I'd probably use that to move things around. But thats just me talking nonsense, I guess.

**Al**
Already planning how to do this, I like it.

**Jamie**
That's it. That's it. And then I can automate it. You know, like you were saying earlier on about how it's always fun to automate stuff, but then you kind of miss out on the minutiae of how it's actually being put together, I guess.

### So What Have You Built With .NET Core?

**Jamie**
What about some of the apps that you've already written and deployed to the, you know, the hundreds of Raspberry Pi's around your house, I mean, we talk in these sort of just little fun little projects, "oh I'll get this working, I'll do that," are they like, integral cogs in the machine of Al life? You know, we're all kind of, we're kind of projects, and we talk with?

**Al**
So, so my style of side projects is mostly just, "hey, I want this thing to exist." So it's, unfortunately not the, "hey, I want to learn how this thing works." It's, "oh, I want to make this thing. I guess I have to learn how this works now." And so there's, there's a project I've been working on for years. And someday I'll finish it. But the majority of my work in this space with .NET on a Raspberry Pi has, has been around this this one project for I guess, six years now. And it's kind of evolved and changed a little bit over that time. For you know, it's an on and off side project, that kind of thing.

But right now, it's essentially something similar to an arcade machine. And the idea is that in this arcade machine, you have like a sensor of what's going to go ahead and pop up a little target and then pop it down. So that way you can kind of, you're going to be shooting this target with something similar to a laser tag gun, so you're just kind of shooting it. And in this arcade machine, you're going to have so many of these targets pop up and maybe move in side to side, that kind of stuff. And so the Raspberry Pi itself is going to be kind of the the main controller, but there's also a couple of other things to that, that you have to integrate with. And so during that time, I've had to learn so much about the electronic space. Because I started that journey with zero knowledge. And I feel like I've gone up 10%, you know, we were talking about that a hair pulling work at the beginning. Anytime I get to any kind of having to share information, like data over RF signals over radio, that kind of stuff. Especially, there was a one point where I was working on being able to read the the signals of the shot. And so the way that works is it's, well, if you've ever had to had to work with infrared signals, and it's the same like your TV remote control, it just turns this light on and off a whole bunch of times. And depending on how many times it was or how long it was on how long it was off, that's the one in zero has to encoded a certain way. And just kind of a tangent on that story reminding of the hair pulling this of why I prefer the C# side, instead of this, you know, embedded C on an 8bit microcontroller.

I wanted to make this application, you know how I would architect an application, I wanted to add some unit tests for the logic and you know, all that kind of stuff. So I had nice separation, some abstractions. And when I was having the code, turn that infrared light on and off the code that was calling that would then call some wrapper, and then that wrapper was calling, you know, basically a function pointer or you know, similar to a delegate in .NET Core. And then that thing that it was calling was then actually turning the light on, and then it would call something else and same concept to turn it off. So it called the wrapper, and the wrapper would call the pointer, and then the pointer would actually call the the method to turn the light off. And it turns out that when you're running that on an 8bit microcontroller running at 8 megahertz, or kilohertz, I have to look that up I already forgot, I think it's. So when you're doing that, just calling those extra functions, the overhead of that is enough to mess up the timing of this, When the light needs to be on and off for just a few nanoseconds. So that was a nice couple of weeks right there just trying to figure that out.

So anyway, just kind of back to this, this project. And so the project has been a lot of fun, because you know, I'm able to have multiple pieces of this application where there's a main Raspberry Pi, that's kind of the brains of this arcade machine. And then that's having to work with these small, 8bit microcontrollers. And those are what's going to be controlling those servos, and the little laser tag type of guns, you're going to be shooting at the targets. I still haven't decided what I'm going to do for a UI, it might be something Blazor, if the Raspberry Pi has the ability to host that also and not slow down everything else. That would be great. You know, another option could be something like a Xamarin application running on a screen, that would also be awesome. And that's how I've kind of architected everything so far. But hey, you know, its my own project, maybe I'll just go ahead and change that, because that's an option now, you know, going to Blazor instead. So we'll see how that goes.

**Jamie**
I feel like I want to talk to you for hours about this arcade machine anyway.

So my college days, which I guess is gonna sound a bit weird, because I know that in the US and Canada, I believe college and university are not separate things. Technically, they're not in the UK, because you have University colleges. So College is a group of like a collective, like a house, within a university. But yeah, so UK colleges 16 to 18 years of age, you maybe do two years, maybe sometimes three, four years, depending on what you're studying. There, you go off to university you doing, you know, that's when you get your bachelor's degree. So when I, the reason I brought that up is because when I was at college, my courses were electronics and computer programming and telecommunications. So a lot of what you were saying then was lighting up parts of my brain that haven't lit up for years. Yeah, so I could happily talk to you about all of that for hours.

One of the things you brought up, then, aside from when you were talking about the the overhead in calling the method, which calls the function pointer, which calls the actual device to turn the LED on and off again, you were talking about how your 8bit microcontrollers are running in megahertz, possibly kilohertz. And I think that's, again, that's another thing that most modern developers don't have to worry about is the actual clock speed of the CPU. And just how lucky we are to have these, you know, I think I think AMD released their CPU with 12, 15, 27 calls at 3 gigahertz and, you know, Intel have released similar things. And your GPU has about 12ty bajillion cores on it, you know, all of these running at millions of millions of gigahertz, but you know, up to five, six gigahertz, if you're incredibly lucky. And then you know, the data centres are running at the speed as well. So sort of having to step back and go, "Wow, this thing is running in the megahertz range. You know, this is essentially a Mega Drive, or a Nintendo Entertainment System that I'm plugging into," you know, I guess that's been a heck of a challenge.

**Al**
Oh, yeah. Well, I mean, especially, you know, we start out writing all this code on, you know, it's super powerful desktop, essentially. And then we're talking about running .NET code on a Raspberry Pi. And that alone is a cool thing. But if you remember it, even those are pretty powerful, right? There's, you know, over one gigahertz on the CPU, and I think there's at least two cores on the PI three, I don't remember on the PI one or two. But you know, that's multiple core, the amount of RAM on those things is about a gig or so depending on the model that you get are up to four, I guess now with the Raspberry Pi fours that have just come out. So those things are beefy for a you know, pocket computer. And then yeah, then you have to start worrying about really small embedded things. But when you get to that point, you're not running .NET on those because the CLR hold everything for the runtime that does not work well in there.

**Jamie**
Maybe that should be Steve Sanderson's next big project. "Guess what, guys? I got .NET running on an eight bit microcontroller running eight megahertz."

**Al**
Oh, if he can do that, I am all in. I would love to stop using all of the the embedded C tools and all that kind of stuff. But hey, more .NET anywhere. I'll take it anywhere else we can squeeze it. I'm in.

**Jamie**
Yeah, sounds good. Sounds good. So you've been using a whole bunch of different, presumably a bunch of different tools as well. So you've got your Raspberry Pi, you've got .NET Core, presumably, building that you were saying earlier, and you're using Visual Studio, building .NET Core, sending it over to your Raspberry Pi. And then maybe, I mean, how professional we're talking, we're talking crocodile clips and random bits of cable, connecting your microcontrollers to your Raspberry Pi, or using a hat or any kind of device that sort of plugs it all in.

**Al**
Oh, it's it's definitely in the unprofessional realm right now. Exposed wires all over, I'm looking over right now. And one of these modules that's attached to the Raspberry Pi is just kind of dangling in midair. Because the wires are just keeping it up there. And it's been like that for about a year at this point. I really hoping that I've taken enough pictures, because if someday, if that ever goes away, then then I'm just going to spend like three hours dealing with wiring issues, I'm sure. That's the benefit of you know, having this as a personal project, not something from work.

**Jamie**
Of course, of course, I guess, you know, that's like you were saying this is where we we learn the new things that we bring into our maybe, maybe not to work, but maybe to our other projects is when we do things in our side project, you know, you can be a little bit less professional. You can sort of not worry about, "well, I don't need to run a unit test for this, because I'm just trying to get my head around our works," or that kind of thing. Or in your case, we'll just have some dangling wires everywhere doesn't matter. No, no one's going to come in and electrocute themselves. And even if they did, it's an embedded device. And they'll only do it once.

**Al**
That's the theory.

**Jamie**
Fantastic okay. And presumably using lots of different software tools to compile all of that as well.

**Al**
Yeah, yeah. So I mean, I've kind of mentioned before running net on the Raspberry Pi's themselves, I've actually been pretty slim on the different tools that I've had to go ahead and get in order to, to work with this stuff. So like I mentioned, I've been using Visual Studio Community Edition on my, on my Windows desktop to write up the code. Because it's .NET Core or Mono if I wanted to pull up VS code, that's an option, too, that's not too bad.

This project, the whole thing with .NET Core that I've been working on is, because of that, I've had to get a little bit more familiar with the .NET CLI. So you know, things like making sure I compile the application self contained mode, when I want to put it on to the Raspberry Pi. But for the most part, the most of the learning that I've had to do when working with running this .NET Core application on a PI has has been learning Linux. I mean, I haven't really jumped into that too much before this stuff. And that alone has really increased my understanding of how Linux works, how you interact with the different pins, the the IO, the input output pins, you know, all of that is just kind of ramped up a tonne. And I would say the the only application that's really different that I've had to work with, since starting this project is WinSCP and that's just because that's a thing that I used to copy-paste all of my files over the network directly onto the Raspberry Pi.

**Jamie**
But that that's always a good thing. You know, learning something new is always a good thing, because I'm sure, you know, I'm sure you can attest to, "Well, yeah, I spent some time learning this thing, but I'm pretty sure I could maybe use this new knowledge in some other some other place some other arena," you know, maybe in your nine to five, somebody says, "Hey, does anybody know anything about Linux?" And you can go, "yes, I know how to list files."

**Al**
Yeah, well, and, you know, learning new things for project is always great. But at the same time, I always feel like there's a limit. Right? You know, at some point, there's just too much to learn. And that's its own blocker. And so I kind of like that, you know, I've been learning how to write these types of applications instead of having to learn, you know, every single thing. And this project alone is, you know, kind of opened up the different types of applications that I could write, you know, like, there's, you know, web apps are so different from desktop apps, different from mobile, etc. So, you know, now embedded type of stuff. Hey, that's another thing. In the in the repertoire.

**Jamie**
Yes, another string for the bow. That's the one I was looking for another skill that you can sort of market, I guess. Another thing that you can say, I know how to do this, and let me show you.

**Al**
Yeah, you know, I don't think I've ever heard that phrase before. But I love it, I need to start using that.

**Jamie**
I think that's more of a UK English thing. I think.

**Al**
Well, my mind immediately went to superheroes, and you know, you've got Hawkeye, or the Green Arrow, and both of them, you know, they're always shooting different types of arrows. You've got the exploding arrow, the punching arrow, you know, that could add. So I was assuming it's something like that. But, you know, I guess that works too.

**Jamie**
See, that's the difference between you and me Al, although I get those references. When you say Hawkeye, I think MASH. So that's just the difference in my upbringing, I guess.

### Are There Other Boards?

**Jamie**
So we talked about all of these things your answering, but we focused entirely on Raspberry Pi. I mean, there are obviously to coin a phrase that the BBC use, and I guess Microsoft use from time to time, "there are other devices." You know, can I run maybe .NET stuff on other IoT devices? Is this a thing? Or is it just Raspberry Pi?

**Al**
Oh, yes, yeah. So there, there are a handful of other options. And they're surprisingly growing to which I'm excited for in the future, see how this works out. So way, before, we had the concept of .NET Core running on a Raspberry Pi, we had something called a Netduino. So I don't know if you've ever heard of the .NET Micro Framework. This was a open source version of the .NET Framework that was specifically meant to run on microcontrollers. So you know, the things that are not running an operating system, these are the things that are way less powerful than a Raspberry Pi, it's effectively an Arduino, if you've ever worked with with that.

The Netduino was the the main board that you can run off of this. There were a couple of others, some other companies that that built things, but the Netduino was basically the the popular one. And the micro framework ran directly on the board. And it was, it was an interesting experience, because it didn't have everything that you could use with .NET itself. So for example, generics weren't supported on the TinyCLR, which is what it was called. So imagine writing LINQ statements without generics because LINQ was supported. So that was interesting. So that project itself isn't really around anymore. So Microsoft is, I believe they've had that open source. Maybe even since the beginning of that project, it was on, oh dread. Now I'm forgetting the name of the the open source site that they had before they move everything to GitHub.

**Jamie**
Oh, Codeplex.

**Al**
Yeah, exactly. Yeah. So it started on Codeplex. And so now, it's all on GitHub and everything.

But the reason that I brought that up is because there was another company called GHI electronics. And they had also gone pretty far in with supporting the .NET Micro Framework, and they had their own boards that work with that. And because Microsoft stop supporting the .NET Micro Framework, GHI electronics, then decided to kind of make their own thing. So it's what I like to call the spiritual successor to the micro framework. So GHI electronics, they have their own boards, they actually have different types of boards for different types of stuff, too. So I definitely recommend looking at their stuff, if you're new to this, and just trying to understand, you know, what you can do with these with these types of boards. But the thing that they created is what they call the TinyCLR OS. And the programming model is exactly the same as what you would be writing out as far as code for Windows 10 IoT.

So I gave a talk this past March on the different options. So pretty much similar to what we're talking about here. And before that, I created an application that would use a ambient light sensor to determine, "ok, is it light out? If it's light out, then make sure that this LED is off, and if it's dark outside, then turn that light on." So you know, just something to turn that on and off. And when I wrote the code for Windows 10 IoT, I got that working, I spent some time. And then I had to write the code for running on this GHI electronics board, the it's called the FEZ board F-E-Z, I believe it stands for fast and easy. When I did that, it was a direct copy-paste, I may have had to change a couple of small things like some namespaces, but that API was exactly the same. And so that was actually really nice. So the the programming model for that it's great, you can use NuGet packages to get the specific version of stuff that you want, you just plug that board into the USB slot in your computer, and you're good to go. So if you're getting out and starting, that is a great place to start with embedded style of development with those GHI electronics, the FEZ boards.

Another option is something that's not even out yet. Maybe fingers crossed by the time this episode drops. But so the the company that I had mentioned, that made the Netduino board was eventually bought by another company called Wilderness Labs, which is I don't remember it's founded by or co founded by, but one of the people, you know, leading wilderness Labs is Brian Costanich, whose name I'm hoping I pronounce correctly. But he's also previously famous for being one of the co founders of Xamarin. So he's kind of been in this space. And so he really wants to make microcontrollers, you know, a big thing, right? I mean, we, we kind of keep seeing reports that, you know, microcontrollers, and IoT, and all this stuff is really taking off. And we're kind of at the beginning of all this stuff. And so they're working on a board that they called the Meadow Board, and they had a Kickstarter this past year. And so they're, they're working on it and keep seeing some updates from them. And looks like they're making a lot of good progress. So I'm super excited. But the cool thing about this Meadow Board is that it's a small, what's called an F7 Development Board. And you can look that up if you want to get a picture online. But basically, it's a small board, it's kind of this long stick sort of thing. But still small enough that yo  know, if you were to make a project that you could kind of just use that and you know, start with that and attach things to it directly. But this board itself runs Mono on it. And it's still kind of small enough that even though it does have an operating system, it's in my mind, it's kind of that middle layer between a small microcontroller and something like a Raspberry Pi, because the operating system it's running is like a real time operating system. And it's meant for this type of board for this type of thing. And the types of applications that you would run is a essentially just all .NET Standard. So the code that you write for running on the Meadow Board would all be completely .NET Standard 2.0, maybe higher by the time the board comes out now that .NET Standard 2.1 is coming out.

But yeah, so those are the options. And sorry for that whole history lesson at the beginning. But yeah, so those are pretty much everything. So you've got Meadow, you got GHI electronics, and you have like three or four different ways that you can run a Raspberry Pi too, I guess. With Windows or Linux, Mono, .NET Core, UWP, all that fun, crazy set of combinations.

**Jamie**
Wow. And these are rule presumably cheap ish bits of hardware. I mean, obviously we got say directly about the Meadow, I guess. But the Raspberry Pi is famous for being a $35 computer. And I guess the Netduino would be - oh, sorry, the FEZ would be around the same price may be cheaper?

**Al**
Yeah. Well, cheaper, actually. So the fence board that I have sitting on my desk right now I ordered online for $15. I don't know what that translates to, in, you know, other currencies. But you know, at least in the US, $15 is incredibly cheap, a Raspberry Pi is 35. So saving, you know, more than half.

**Jamie**
Yeah, that's what the price of maybe three coffees? It's pretty cheap.

**Al**
Oh, yeah, you do have to buy, you know, whatever other electronics that you want to run on this thing, different types of applications that you'll be running on something like this FEZ board over here, because this is just the board. If you want the wires and little LEDs or servos, that kind of stuff, that's that's going to add some some costs , too. But you're probably going to be buying the same stuff for a Raspberry Pi, if you want to do the same hardware level of applications.

**Jamie**
Sure, sure. That makes sense. Just like looking back on this conversation, just taking a moment to do that. It's like, I remember when .NET Core 1.0 RTM was announced that they had this little graphic and it was "write once, run anywhere." And it really is true. You know, we've got Windows desktops, Linux desktops. And that in itself is an achievement because there are hundreds of different desktop environments for Linux, it's not just like Windows where you have Explorer, and you're done. You've also got Mac OS and embedded devices. And Tizen fridges, you know, the Samsung line of Tizen hardware, .NET Core is the official supported language for that.  You've got smart watches, you've got mobile phones, you know, Android, iOS, whatever, whichever one of those two you've written, you can run it there. It's amazing, just the amount of effort that has been put in, so that you and I can just do `dotnet build` at the command line, and he just figures it all out. And then you can like you say you transfer that application? Maybe with Was it WSCP. WinSCP? And transfer that over and it just runs. It's mad.

**Al**
Yeah, yeah, exactly. You know, WinSCP just makes it easy, just copy-paste DLLs that are, you know, compiled on my machine. And there we go.

You know, kind of going back to what you were saying about running everywhere. I remember when I was in college, you know, hearing a lot of people say, "yeah, you know, basically Java runs the world, right?" Because at the time, it was probably the best option for running everywhere. Java was supported in so many different architectures. And it wasn't, you know, C/C++ that had to be compiled specific for that architecture, all that stuff. And, you know, hey, maybe someday we'll be saying the same thing. about .NET, right, you know. It's able to run everywhere, on everything. So we'll see how that goes. We have other choices now, too. So it's not just a .NET that can do that, hey, maybe JavaScript or when it kind of has won a lot of other things, too.

**Jamie**
Yeah, exactly. I think it goes back to what we were saying earlier. And there's another tool in your tool belt - that's probably the better version of the phrase, I was trying to say - it's another tool in your tool belt to know that .NET exists and to know vaguely how to do it, which is kind of what I do every day, don't tell my clients.

Having all of these different technologies that can just literally write one song real anywhere, is an amazing feat. I'm not trying to detract from the folks who get you know, who are doing low level C/C++. Like yourself, you know, with the project you're working on, because they will, they'll always be you know, call for that. But when the majority of your work is, you know, the day to day humdrum of what Richard Campbell calls, "forms over data," you know .NET, Java, JavaScript, these can all do these things. With the added bonus of, you know, I don't know whether you can run Java on a Raspberry Pi.

**Al**
That's true. I guess I assume you can do that. But I've never actually tried.

**Jamie**
There you go, you see. Yeah. So at the very least, we can run .NET on almost everything will probably be able to run on the moon at some point, I don't know.

But yes. So a couple of quick questions then Al, if that's alright, before we sort of wrap up. So where can people get in contact with you maybe to learn a little bit more about this project and other projects you've got going on? was the best place to find out about this kind of stuff?

**Al**
Yeah, so the absolutely easiest way to do that is on Twitter, I am [@programmerAl](twitter.com/programmeral). If you just type it out, it kind of looks like programmer AI. When you're using the lowercase l there. It's not that is not my Twitter handle. I assume that someone else. I don't actually know if if that one exists. But I get that question a lot. I I have heard people mispronounce it. I don't really care. People get my personal name wrong all the time. But just just letting you know, in case you're typing it out programmerAl.

**Jamie**
Okay. Well, what we'll do is we'll make sure that there's a link in the show notes at the very least. So click through to those sort of main show notes off of the podcatcher. And, you know, it'll be in the most definitely. What about your podcast? And is that something? Is there a website for that? Is there an easy way to catch that? I know that I've been on episode, so obviously, you know, people want to hear that. But.

**Al**
Yeah, exactly. So our website is [developersidequestspodcast.com/](https://www.developersidequestspodcast.com/). Or you could also just find us on Twitter, we are [@devsidequests](twitter.com/devsidequests). So or if you just do any kind of general online search for `developer site quests`, you'll be able to find it.

Do not click on developersidequests.com. That is a domain that I do own. But I used it for a little while decided to stop using it. I had some plans because it's cool. And I want to use it for something better than what it was for. I think Google still has that that cached because it was basically my blog for a while. So if you're confused why that's not working, because you're not at the podcast site.

**Jamie**
Okay, fair enough. Again, there'll be a link in the in the show notes. But yes, and it's kind of really cool. I don't want to say gimmick, but it has this really cool feel, doesn't it? The idea that you're going on to talk about your side quests, but it's not like the conversation we've had, Is it?

**Al**
No, yeah, yeah, I try to keep like the nice theme of, you know, side quests, or requesting like an RPG sort of thing. So try to have fun with it. Right? Yeah, there's a lot of interview shows out there that all kind of do their own thing. And, and my thing is games. So love playing RPGs that kind of thing.

**Jamie**
Excellent. So if you're a fan of development, and D&D, or any kind of RPGs definitely check it out. If you're a fan of development, definitely check it out. If you're a fan of me, for some reason, definitely check it out. Because I was on an episode. Surprisingly, not talking about don't .NET Core. I remember.

**Al**
That's true. It was still a great episode. I had a lot of fun talking to you.

**Jamie**
Thank you very much. We would say what I talked about, because then that will make everyone who listens to this want to go and listen to it. Right?

**Al**
Exactly. Yeah,

**Jamie**
Exactly. Well, those are all the questions I have for today, at the very least, at least relating to Raspberry Pi's, IoT devices, edge devices, and .NET Core.

I would love to talk to you for hours and hours about your personal project about the the arcade machine and how your engineering it all and how it's all sort of fitting together. Because you know, like I said earlier on is lighting up parts of my brain that haven't really had anyone to talk with for a while. I remember that a friend of mine, that university that he was doing electronic engineering and decided, "I'm just going to build a Van de Graaff generator, why not? I'll buy the parts and build one." And I remember I would speak to him for hours at the pub:"So where are you up to? What are you doing? How's it all fit together? Can I come out and see it? What's going on?" It's brilliant. And then he said he was going to build a Tesla coil as well. Those are fun.

**Al**
And did he did he build these things

**Jamie**
that he built the Van de Graaff generator didn't build the Tesla coil for I think, understandable reasons. I don't know whether you've seen a Tesla coil. Those things produce the, like bolts of lightning or plasma or whatever it is. So maybe not, maybe not one of those.

**Al**
Yeah, some will probably be a little upset. You know, the first time it fries everything in the room, I'm sure.

**Jamie**
Exactly. Yes. So yeah, those were all my questions Al. Like I said, happily talk to you about your project, your personal project, another time, I guess. Because that just sounds wonderful. And I'd love to hear the sort of development of as it continues on. That's something that's really sort of lit up parts of my right. So honestly, I'll thank you ever so much for being on the show. It is it's been a lot of fun talking to you about all of these things. The listeners should definitely check out the show notes. Maybe I don't know is there is there maybe a blog post on your, your sort of progression with this or if you've been documenting it, your personal project?

**Al**
You know, not not too much to be honest. I've written a few things on my blog. So if you go to [programmeral.com/](https://programmeral.com/), you can find my blog, but I don't write anywhere nearly as often as I should. So maybe maybe this will be the the kick in the pants that takes me to actually start start writing more. But I should I have like the whole list of topics that I should be writing on that I have yet to go back in and talk about.

**Jamie**
Well, I know for myself, it would be an incredibly interesting read just sort of figuring out how you've how you figured it out. I guess they're the tools you're using the hardware using, you know the common problems, you having all that kinda stuff, we will be wonderful. So then I don't have to learn how, I just go, "ah. I'll go just by all the pieces that Al bought and then I can build it, right?"

**Al**
Yeah, yeah, maybe. We'll see how that goes. I mean, I still haven't built it yet. I've done no physical stuff outside of you know, just the the wires that are touching servos and all that fun stuff.

**Jamie**
Like I say, it'll be interesting to follow it at the very least.

Yeah, so definitely click through, get all the show notes and click through to Al's stuff, see what he's doing. And yeah, like I said, only run I think I'll say three times now. But yeah, thank you. Thank you so much for being on the show. Al it's been a wonderful experience.

**Al**
Yeah, and I've had so much fun. Thank you for having me.

**Jamie**
No worries. Thank you ever so much.

### Wrapping Up

That was my interview with Al Rodriguez. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and a full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/).

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Al Rodriguez on twitter](https://twitter.com/programmeral)
- Al's podcast [Developer Side Quests](https://www.developersidequestspodcast.com/)
  - The Podcast has a twitter account, too [@devsidequests](twitter.com/devsidequests)
- Al's website [programmeral.com/](https://programmeral.com/)
- [raspberrypi.org](raspberrypi.org)
- [Raspbian](https://www.raspberrypi.org/downloads/raspbian/)
- [FEZ board from GHI Electronics](https://www.ghielectronics.com/products/fez)
- [TinyCLR OS](https://ghielectronics.com/tinyclr/features)
- [Meadow Board](https://www.wildernesslabs.co/meadow)
