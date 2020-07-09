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

I am your host, Jamie "GaProgMan" Taylor, and this is episode 44: Learning .NET with Mark Price. In this episode I interviewed Mark about some of the ways to learn .NET Core, and a little on his history with educating others with the Microsoft Stack. Some of you may know Mark Price from his extensive experience of being a Microsoft Certified Trainer, his work at EpiServer, or from the latest edition of his book ["C# 8.0 and .NET Core 3.0" available from Packt Publishing](https://www.packtpub.com/mobile/c-8-0-and-net-core-3-0-modern-cross-platform-development-fourth-edition).

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Mark's Introduction

**Jamie**

So the first thing I'd like to say Mark is Thank you ever so much for taking the time out of your Friday evening to talk to me about your recent book, and your history in the .NET and Microsoft ecosystem.

**Mark**

Thank you very much Jamie for inviting me. I'm pleased to be here.

**Jamie**

Excellent. I'm always glad to hear that guests are pleased to be here because it makes it a better episode.

So I was wondering, could you perhaps start by giving us a brief introduction to yourself, for maybe the listeners who who haven't seen any of your work before or anything like that?

**Mark**

Yes, of course. Happy to. So my name is Mark Price. I'm based in London in the UK. And I've been working with Microsoft developer tools and technologies for pretty much my whole career. And I'm rapidly approaching 50 now, so that's a pretty long time. I'd like to describe myself as an expert educator from a family of educators. my sister, was a primary school teacher. I have cousins in education as well. And My grandfather sort of taught at the military Academy at Sandhurst. So a lot of educators in my family. And When I was a teenager back in the 1980s, I'd earn extra pocket money teaching local business owners how to use their first computer that they might have bought for doing basic word processing and spreadsheets. And then when I went to university, I studied computer science. At the time, this is the early 90s, Microsoft have just released a Visual Basic version one which was a rapid application development tool that really took off, and I recognised the the significance of that, and so do I taught it to myself. And I had a pretty successful self employed training career in the UK until the late nineties. That was when the dot com boom was happening in Silicon Valley. So I moved to America, lived in San Francisco. It was a very exciting time to be in the industry. And that was a fantastic experience. Going out to the bars and seeing all the different start ups and the different projects that they're working on, even though a lot of those of course, flamed out at the time.

I then moved up to Seattle to join Microsoft. And I helped them to educate the millions of developers worldwide that were currently using their products like Visual Basic and C++. And Microsoft, at the time, had just released their new C# programme language running on the .NET Framework. And since then, I've continued to be heavily involved in that world, helping developers of all different levels from apprentices [at] 16 years old coming out of school early wanting to get into programming; all the way up to professionals who might have decades of experience, and they want to be able to get up to speed as fast as possible with this .NET development world, knowing that it's a rapidly changing world. Along the way, I have taken a few diversions. For example, I took a year off to do a sabbatical to study screenwriting [at] Vancouver film school, and that was a fantastic experience which has actually helped me as an educator in some ways. And I also was temporarily a maths teacher at a couple of London schools and also has helps my educational background. So I've done a lot of travelled a lot. I have had a fantastic life and I really enjoy passing on my skills and knowledge to other people and, improving their lives as well.

**Jamie**

Wow, that's a very impressive career. I have to say.

**Mark**

Thank you. It's been a lot of fun.

**Jamie**

I can imagine there has.

So I remember. Straight out of university, I went into a teaching role, and I was teaching Maths. And from a personal point of view, I remember the joy of watching someone sort of figure something out. You know, the students would come in, they had no idea about Pythagorean Theorem, and then 45 minutes later, there's one or two who it just clicks and it makes perfect sense and the rest got it. But you know, they're going to forget it because they're going off to another class in a minute.

**Mark**

Yes.

**Jamie**

Just that when you see it in someone's eyes, when they go, "Oh wow, yeah, that makes total sense." And that was an unbridled joy for me for a while. So I have to say, I completely get the education background, not to the same extent that you have, obviously. But I totally get that. Presumably you see this every day.

**Mark**

I do. Even in my current day job, I still occasionally get to go into a classroom. It tends to be adults, programmers, professional programmers who were trying to update their skills or learn a new platform. And it's fascinating to see how professionals react to learning something new. I believe that for human beings, learning new things is one of the hardest things we do. And for a lot of us who are comfortable in our careers, it can sometimes be a shock going back into the classroom and, having to absorb a lot of technical information in such a short amount of time. Because these days we all have so many time pressures on us, taking that time to absorb the information and really practise, get the hands on practise, which is so vital to learning a new skill could be a real challenge and. That's one of the things that I'm particular rested today in my kind of career is: how to help people juggle their personal lives with their careers what their day job involves, but still giving them the space to be able to as efficiently as possible. But still in a fun way. Actually learned something that they they get takes him joy from and can feel comfortable. "Yeah, I really know that now. And I can apply it to my day job."

**Jamie**

Yeah, that's the best part. Like you say, being able to see that deep knowledge. The way that it was described to me during my teacher training was the higher level knowledge, the ability to sort of self reflect take the input knowledge and, reword it into your own understanding of how it all works.

**Mark**

Yeah, you're absolutely right. It's only when a student can do that can then turn it around, and either apply the kind of principles that they might have learned to a new situation or, yes just reword it in their own language that they're comfortable with. And that has such a satisfying feeling because when they do that, you know that they have genuinely learned it and. They're excited to have learned something new.

**Jamie**

Definitely. I still see it from time to time myself. So I'm a contractor, and one of things I do is mentoring and sort of helping out with getting an idea for maybe a design pattern or getting the basics of, "Well, this is how this technology works." I guess on a very, very, very small scale version of you know what you've described you do. And watching someone who previously had no idea of, say node, and then going. "Oh, wow, I could do a hello world. And now I know what Hello World is." And then you walk away and come back 45 minutes later, and they've got some kind of sorting algorithm or they've got some data coming in, they're doing something to the data and sending it back out to third party. It's amazing, just to watch how fast someone can, once they have those fundamentals, how fast they can apply that knowledge and and learn some more and build something else on top of it. It is absolutely amazing.

**Mark**

100% agree on. It's a genuine pleasure to chat to someone who has a similar kind of educational background. And I can geek out a bit with you, Jamie, about education. Because not everyone is that excited about how to educate people and, yeah, enabling those kind of activities.

**Jamie**

Yeah. So from my background. I always found that I tried to figure out - we've gone slightly off topic, but I'm gonna leave it - try to figure out how the student or the person that I'm working with can learn the thing that they want to learn best. So the canonical example that I give from when I was working as a maths teacher is working out, the circumference of a circle.

**Mark**

Yes.

**Jamie**

The circumference of a circle is a very dry topic, you know, πr{{< sup "2" >}} and you've got the distance around the circle, fantastic. But what I would do is, especially with the younger students, so this was secondary school, so 11 years old and up. 

**Mark**

Yeah.

**Jamie**

What I would do is, I would say, "draw a circle on the whiteboard or whatever, and we'll draw some lines on it. Just make up some names for them. It doesn't matter what we call them." Then I would say, "right, we're not gonna work out any maths yet. We're actually going to go and get this," I don't know they're called, it's a wheel on a stick that collects every time it goes around.

**Mark**

Oh, yes, I know what you mean.

**Jamie**

I would say to each of the students, "we're going for a walk around the school, and we're going to count how many times it clicks, and that's all we're going to do." So we walk a route around the building and listen to how many times it collect, get back to the classroom, and then we'd say, "Okay, so it's maybe clicked 200 times or something; write that down. Now take the take a ruler or a tape measure and measure the distance across the very centre of the wheel, we'll give that a name. It doesn't really matter now. We'll half it for no real reason whatsoever, because we only want to go from the middle to the outside. And then we'd apply the πr{{< sup "2" >}}to it," and we'd round up to figure out why it's three and what's not four; and why it's not 3.2. And then, by that point, we've then calculated the length of the route because we figured out how far around the wheel - the distance of the circumference - and then how many times it's clicked. So we know maybe the wheel is one metre into conference, and it's collect 200 times. We've just walked 200 metres. It's that application of it.

**Mark**

Yep. And hearing stories like that from other mass teachers, and different approaches to teaching the same subject, I find it all so fascinating. There's a YouTube a couple of years ago who now works for Google and he was a maths teacher in the equivalent to Secondary school - sort of High School in the United States. I used to love his videos. He would use clips from sitcoms like Parks and Recreation in order to talk about probability or statistics and things like that and. It was great seeing how engaged his students could be. When you can be a bit more creative than just the traditional teaching of things like Pythagoras' Theorem.

**Jamie**

It is brilliant because then it makes it kind of really for the student. So let's say you were going to, teach someone how to create, I don't know, an input form on a HTML Web page. Well, you could talk about divs and you could talk about spans, and you could talk about block elements, and all this kind of stuff; or you could say, "right, Let's just give it a name. Whatever. Let's draw out a form on paper and go from there." You know it is. The possibilities are pretty much endless. When you're when you're teaching someone

**Mark**

They are, yes.

### Where To Start? Mark's Book

**Jamie**

We're talking about the extensive experience, I want to say, of your background working with the Microsoft Stack. And I think this episode will fit very well with one that's planned to be released just before it. For those who don't realise, we record these a little bit ahead of time; and the episode that is planned to go out just before this one is effectively an interview where I've turned to the tables. I'm the one being interviewed on the interviewer is a developer called Josie Howarth, and the thesis of the episode is, "how do I get started with all of this?" So I think that combined with this one, I think will work really well because you have the experience of showing people how to get started.

**Mark**

Absolutely. Yes, I totally agree that it sounds like there's gonna be a really interesting fit between the episode where you get interviewed and this one where I'm being interviewed about my book. Because yeah, I wrote my book to answer the question, "Where do I start?" For readers who either want to learn C# and .NET for the very first time, or for readers who have maybe used C# and .NET a decade ago and they feel a bit left behind by some of the rapid changes that we've had recently in the platform. This book is where I hope they will get a great start because once you've completed the book, it's full off step by step, detailed tasks that you can complete. Because one of the things that I learned with screenwriting the kind of classic quote about screenwriting is:

> show don't tell

And I really believe that with education as well. So rather than going into long, detailed conceptual descriptions about a particular language feature or an API call, I like to get in as quickly as possible and actually show some working code. Because I believe if you're actually doing, if you're type in the code yourself in small, relatively simple examples that can actually run, and see it work, that's a great starting point to then taking it further. Hopefully, readers will have been out of follow along, get that code working and then wonder, "what if I were to change this?" Or, "does that mean that I could also do that?" And try it on their own.

Some books, I think, almost take you too far. I'm hoping to show you a broad enough range of topics to enough depth that you get the idea on that you've actually seen the code work. And then point you two further information; perhaps in the official documentation - Microsoft tend to have done a great job of that - or to blog articles and things like that. And when you're reading those more advanced blog articles or the official documentation, you'll understand what they're trying to tell you because you've already now got that kind of solid foundation of skills to build up.

So yeah, "where to start" is yet the primary goal of my book.

**Jamie**

So just so that the listeners know could you tell us the title of the book?

**Mark**

Yeah, absolutely. So the full title is "C# 8 and .NET Core 3: Modern Cross Platform Development", and it'll show you how to build applications using, of course, C# and .NET Core, but also some of the sub components of that like Entity Framework Core for working with databases; ASP .NET Core for building websites; and even now, in the fourth edition, I've added a brand new chapter about machine learning with [ML .NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet), which is Microsoft's set of class libraries that can help you add artificial intelligence embedded in any .NET application.

**Jamie**

That is amazing. It does sound like it's a, like you say, a book that's aimed at a beginner, I guess in the journey. Or get someone who has been on the journey and come back. But even the inclusion of the newer things like ML .NET, and I believe when we were chatting by email setting this up, you'd said that there's a section on content management systems as well. Is that correct?

**Mark**

That's right. That's another completely new chapter in this fourth edition of the book, yes about content management systems. Because what I've realised with my real world experience, actually going out into the world and implementing websites for businesses and charities all over the world, is that it's actually very rare that a website is built just purely on say ASP .NET MVC. That's what most programmer books might cover if it's a book about Web development with .NET, they would teach you all about controllers and models and views - the MVC design pattern - and of course, the basics of HTML, and JavaScript, and CSS for creating the structure of a webpage and styling, and maybe some client side interactivity with some JavaScript.

But in the real world, if you go to any big company or any organisation that has websites, and  all do now of course, that's almost never what they're actually using for the public websites. They're going to be using a contact management system because you need to enable the business users, the marketing department, maybe the people who are the merchandisers who are managing the catalogue if it's an e-commerce website. Those business users are not programmers, they shouldn't have to learn HTML or ASP .NET just to be able to manage the content on their own website.

And so, as a .NET developer, I decided that it was quite important for us to go beyond just what Microsoft gives us in platforms like ASP .NET Core, and actually have a look at an actual implementation of a CMS and show how that is then built on top of ASP .NET. And so all of your skills are still very relevant in order for you to understand how the CMS works together with the data, merges it with templates that might be implemented as a razor page or an MVC view, in order to then turn into HTML. But that's much more practical. That's going to give you some real world skills that you can then leverage to get a job with any business really, that's going to be using a CMS.

In my book I wanted to make sure that I picked a CMS that was compatible with .NET core and therefore truly cross platform, and open source. And at the moment a lot of the bigger enterprise type CMSes like [Episerver](https://www.episerver.com/); or [SiteCore](https://www.sitecore.com/); or [Adobe Experience Manager](https://www.adobe.com/marketing/experience-manager.html) for example, those don't run yet on .NET core - they will in the future, but not today. I also wanted to make sure that I could cover the topic of a CMS in just one chapter. So I decided to pick [Piranha CMS](https://piranhacms.org/), which is a real lightweight, fun, easy to understand CMS. You're going to learn a lot about the principles of how .NET CMS is tend to work that you can then leverage when you're then learning something like [Umbraco](https://umbraco.com/) or Episerver. So I'm hoping that that chapter will actually be eye opening for a lot of .NET developers, and actually leads to a lot of practical skill building. So we'll have to see. Have you ever worked with .NET CMS Jamie?

**Jamie**

Yes, I have. I've worked with siteCore back in the .NET Framework days. I say that because I work almost entirely in .NET Core these days. But I also [built something with Umbraco headless and Blazor](/episode-25-blazor-you-want-to-run-net-where/).

**Mark**

Oh, that's such an awesome topic. Yeah. Where you using server side Blazor?

**Jamie**

So it was entirely client side. Well I say, "entirely client side." There's obviously still a server side to it to host the files. But yeah, at all of the interactivity and everything was client side. So [it wasn an] entire .NET stack inside the browser. And this was Blazor 0.3 as well, so it was incredibly early.

**Mark**

That's really on the bleeding edge, as they say. That can be very challenging when 0.4 comes out and things break. So you're a braver man than I am.

**Jamie**

I did it for a talk as well.

**Mark**

Oh, even worse. I hope the demo gods were kind to you.

**Jamie**

Oh, yeah. Everything worked, except for when I needed to login live. I use password manager and my password manager popped up on screen, and gave everyone my email address.

**Mark**

Yes. That is exactly the kind of thing that can happen when you're doing live demos.

**Jamie**

The code all worked. I just hadn't logged in. That's that's the difference.

**Mark**

Yeah.

**Jamie**

That was amazing, too. Because you're making a change in some thing that exists elsewhere. It felt very much like the [inversion of dependencies principle](https://deviq.com/dependency-inversion-principle/): I'm making a chance in some backend storage of the CMS for this website and then, magically, something on my browser just changed automatically. I didn't have to do anything, I think that maybe I had to refresh the page, and that's the magic of development. Like you were saying, the business user doesn't need to know the magic of the details of how it's all stored, and how it all works. They just need to know, "I go to this page and change the title of the page in whatever CMS amusing. I don't even need to know. It's called a CMS. I just need to know I got to this URL on the website and I log in, I change something. And it changes on the website."

**Mark**

Yep. Blazor is a technology that I'm super interested in. But as I kind of hinted at a few moments ago, I wasn't brave enough to try, and add a chapter into the fourth edition. But I can promise all the listeners to this podcast that Blazor will be in the fifth edition, coming next year.

**Jamie**

Fantastic. So we've got the inside scoop.

### What Has It Been Like To Watch .NET Change So Much?

**Jamie**

You see, this leads into a question that I have: Unfortunately, we have multiple .NETs.

**Mark**

Yes

**Jamie**

We've got Framework; and Core; and Mono; and Unity; and Xamarin, and they're all .NET related technologies. To be able to say, "yes, I will write this code in .NET and I can run it quite literally anywhere." Versus 20 years ago when .NET first started and it was, "yeah, we've got .NET and its Windows Enterprise applications." 2002 and we got windows .NET; Maybe 2005/2006 we've got Miguel de Icaza with his Mono Project, and then you can kind of do .NET on Linuz, but you can't because sometimes it's ahead of the spec and sometimes it's behind it.

**Jamie**

I wondering what has that experience been over the last 20/25 years of watching this technology that appeared as a Windows specific, enterprise specific thing, this admittedly hulky, slow framework that allowed you to do rapid application development that is now incredibly small and install-able pretty much anywhere?

**Mark**

Yeah, it's definitely been, a bit of a roller-coaster. As a .NET developer who makes my living from these technologies, I've had the same concerns that I think a lot of .NET developers have had. In watching, particularly starting, say, five years ago. Wondering what the future of the .NET Framework is. Once it became tied to the Windows operating system it, by necessity, had to slow down in the implementation of new features just to maintain compatibility. And although I think a lot of .NET developers at that time where fairly happy with the capabilities of the .NET framework 4.5. As developers, I mean one of the things that I think draws people into programming is that we love new things. And so when Microsoft started talking, about 4/5 years ago, about .NET Core and approaching that as almost like a kind of reboot of the principles behind .NET, and taking this more of an open source cross platform approach, it was exciting, but also very scary. Because it raises all of those questions about, "what about our existing code? What about our existing investments that we've made in these technologies?" And being aware of these other branches off .NET, as you mentioned things like Mono and Unity.

And Microsoft's first approach was to try and create, of course, the .NET standard. And particularly two years ago when they released the .NET Standard 2.0, it was a pulling together of all the major different branches of .NET, so that it was a little bit easier for us developers to write code to target a single standard set of APIs. That was a great first step, but I was actually very pleased to hear at the Build conference this year - May 2019 - when they made the official announcement about finally reunification almost of .NET into .NET Five next year. It really helped to you clarify where Microsoft sees where they're taking .NET. And I think it's going to, although it would be a little bit rocky as people start switching and migration from .NET framework to maybe .NET Core three in preparation for .NET Five next year. I think most .NET developers are now feeling a lot more comfortable that Microsoft is taking the right approach to prepare for the next decade. .NET 5/6/7 having these annual releases, a bit like Apple does with their iOS every second week in September. Now we can start getting used to every November, starting November 2020, we're gonna have a new version of .NET. That kind of regularity and a single platform, I think, is going to be fantastic. And I can almost see C# boost up the rankings of most popular languages, partly based on the fact that it can be used on a single version of .NET; whether you're using technologies like Blazor on the client side, in the Web browser, or serverside, cross platform, mobile devices, and it's genuinely an exciting time to be a C# or .NET develper. Although it's almost 20 years old now, it feels re-energised

**Jamie**

That makes sense.

So for me, I'm still a young one in the business, in that I've only really been in the development business for about 11 years. But my main concern going into Core was, at the time I wasn't running windows. I'd had some hardware issues with my Windows machines and so had moved across, had migrated to Linux and UNIX and looking at all of those things. So for me, when they announced .NET Core I was like, "finally, I could do .NET things in my own time at home. I don't have to learn another language or a framework."

A few years ago, as the business that I was working for was preparing to move and go all in on .NET Core, I then started thinking to myself that the other developers around me were primarily Windows developers and, let's not beat about the bush, there is a fundamental difference in the way that Windows does things to the way that the UNIX compatible operating systems do things. So that was my main concern, although is very excited that, you know, there's this whole new technology coming out that's based on some of the old stuff, a rewrite of it, ditching some of the old stuff, making a faster and cross platform and all that kind of stuff. And then I'm thinking, "what about all of these Windows developers who maybe are coming back to the .NET? And not only do they need to learn .NET, but they've also now perhaps got to learn the differences in the operating systems as well."

**Mark**

Yeah. It's definitely a challenge both for Microsoft in designing their APIs, or deciding how the .NET platform should react to maybe calling an API that doesn't make sense on a particular operation system. Definitely a challenge for them and for us as developers to be aware of those kind of differences. I would love to see some statistics from Microsoft to see how many applications that are .NET Core applications are actively executed on these different platforms. But I suppose there's a lot of regulation, GDPR type privacy implications to that. It's a bit of a shame that they can't kind of add those kind of recordings to their framework. But yeah, you can totally understand why that's not sensible idea.

**Jamie**

Yeah, that's true. Going slowly off topic, I guess, technologies like docker tend to sort of make all of that go away, because then your underlying operating system is then an implementation detail: You don't have to worry about it. If your application and your Ops system doesn't really matter so much. Because although you are interacting with an API that is interacting with an operating system, you could swap the operating system out and, like you say, as long as the designers of the API have really thought about, "what should happen if... " then it shouldn't really be a huge problem, should it?

**Mark**

It shouldn't, no. And docker is actually something that's been kind of bubbling and under my consciousness for a while now. And it's my plan for the quiet moments over Christmas is to try and get to grips myself with docker, because I just haven't had the time yet. But that certainly seems to be containerisation - those kind of ideas - that's really important for enterprise development.

**Jamie**

Absolutely.

### Tell Me More About The Book

**Jamie**

So you said earlier on about how the book is really aimed at someone who's either brand new to C# and .NET, or has touched on it before. So does that mean then that the book is incredibly detailed? Am I looking at something that's maybe the density of, say, [The Art of Programming](https://en.wikipedia.org/wiki/The_Art_of_Computer_Programming) or [Code Complete](https://www.goodreads.com/book/show/4845.Code_Complete)? Or am I looking at something that's along the same lines as an in-action book from Manning? That sort of, "you're going to build an application and I'm going to teach you a little bit about it on the way." Or is it incredibly detailed? Because, like you say, you're touching on so many different things: you're touching on .NET Core; you're touching on ASP .NET Core; EF Core; ML .NET and all that kind of thing. I guess The question I'm asking is: is it a huge amount of investment to get through the book?

**Mark**

Absolutely not. No, I've designed the book to be relatively - I was going to say "lightweight" but that can have negative connotations. What I mean by "lightweight" is it's not gonna be a heavy reed. Some of these books can feel a bit like you're wading through molasses just to get to the end of each chapter. I've specifically focused each chapter on a different topic, made them about 30 pages long, with little tasks and exercises that will keep you motivated. So I think actually, it's going to be quite a quick, fun read. Where you're learning lots of little nuggets of information, building up your skills and knowledge. So you won't have to wade through thousands of pages of details. Because those kind of details you can actually look up in the official documentation; while I show you maybe some basic functionality of say a particular class in the APIs. Once you've learned those basics, you can always just click in the class name and press F1 to get to the documentation. And because I've told you the basic way that thing works, then you can kind of take it further yourself.

So at end of each of these tasks, where you've got a lot of hands on practical experience, you can see the code working in on your Macbook, or your Linux VM, or even a Windows laptop - if you're still using one of those - at the end of each chapter, there are links to further reference materials. So you're not gonna feel overwhelmed by going through this book. At least that was my goal. And reading some of the Amazon reviews that are already up on Amazon, it seems to be resonating with readers and. They are finding it very - I think you mentioned that you had a couple of friends who found the book useful.

**Jamie**

Yes, I have. A few of my friends are "programming adjacent" I'll say. In that they are the type of people who will say to you "I'm very interested in technology, but I haven't got a clue." And so I sat with him and said, "look, why don't I teach you a little bit of what I do? And show you there's hundreds of different programming languages and technologies frameworks." And, in my opinion, probably coloured because I've used .NET for so long. I do honestly think that .NET is one of the easiest to on board someone with, especially with Core. Because you just install an SDK, you don't even need any kind of development environment you can use, you know, notepad or whatever and you're good to go within moments.

For instance, at university, the first lesson that we had in computer science was .NET, based, and the lecturer literally put his laptop onto the lectern, plugged in the overhead projector system and said, "right, I'm going to type out some code into notepad, and it's in a big enough font that you call all read it. This is what it's going to do," and he pulled up `csc` and manually compiled it from the command line, and ran the application in front of us. And every single one of his lectures was done in that way. And somebody had said to him, "Why aren't you using visual studio?" And he said, "because you don't have to use visual studio to do all of this."

**Mark**

Yeah.

**Jamie**

At least for me, one of the great things about .NET is that you can pick your own tools, you're not tied to a specific piece of software to build your applications.

So with these friends I said to them, "get a copy of this book because its designed for brand new people, and I'll sit with you and if you get stuck or if that's something you don't understand," and they very, rarely had to talk to me about anything. I think the one thing was, "which version of .NETs do any to install? There's 2, 2.1, 3, 3.1."

**Mark**

Yes.

**Jamie**

So that's the bit that they got stuck with. So I can say that from second-hand experience, I guess, of watching someone learning the basics of .NET Core that the book is really quite good. I have to say.

**Mark**

That is so gratifying to hear. Because new people to programming, I would say, is the audience that I personally feel feel the happiest in that I'm helping out.

**Jamie**

I do feel as though over the next couple of years we're going to be seeing a lot of people come towards programming. As more roles and jobs throughout the world rely more on programming. There's a person that I know called [Shawn Wang](https://twitter.com/swyx), who three years ago he worked in finance and made his money that way, and then he then went away and took a boot-camp, and now he's an incredibly prolific online person in the development space. He's made tonnes of money and got loads of exposure by learning to program, and then going and teaching other people or talking about it; and I think that's gonna be the next step in workplace evolution: you're gonna have people who - I mean we've seen it before with VBA. You had non-developers kind of writing scripts to help them with macros inside of Word files, and Spreadsheets, and e-mail clients. And I think it's just the next step along that trajectory.

**Mark**

Yeah, absolutely.

### What's Your Favourite New Feature in C# 8?

**Mark**

Do you have a personal favourite new feature in C# eight?

**Jamie**

I like the look of [pattern matching](https://devblogs.microsoft.com/dotnet/do-more-with-patterns-in-c-8-0/), but I haven't been able to find an instance where I would use it. But it's the [nullable reference types](https://devblogs.microsoft.com/dotnet/embracing-nullable-reference-types/).

**Mark**

Yes.

**Jamie**

That is, it's a game changer. As someone who has written library code before, being able to say to the compiler, "alert me when something could possibly be null." And then I'll just say, "no, that's okay. That one's fine." Just seeing all of my code be littered with the little red squiggles of, "you haven't thought about this. You haven't thought about that," and having the compiler just be that one step smarter, and helping me to be smelter is absolutely amazing.

**Mark**

Yeah. That knew null handling behaviour is genuinely a potential - I think when Microsoft was first saying that they might implement this like 18 months ago, I think a lot of developers were nervous about what the implications would be if they made it mandatory. Luckily, I think they thought really hard. They had a very long preview for that null reference type feature. And I think they made the right decision in the end, in that if you're creating a completely new code, you can take full advantage of that and avoid the infamous [billion dollar mistake](https://www.infoq.com/presentations/Null-References-The-Billion-Dollar-Mistake-Tony-Hoare/) that even supporting nulls or allowing them in too flexible [a] way; but also allowing you to maybe my great existing code slowly over time and kind of opt in to that new behaviour, so that you can you're not suddenly overwhelmed by lots, and lots of errors or warnings in your compiler.

That's one of things that I have always appreciated about Microsoft and their approach to develop tools and technologies: is that they really do understand the real world demands on developers. And they really put a lot of effort into making their platforms backwards compatible, so that you don't have to completely rewrite everything and just junk everything that you've done in the past.

Although .NET core has been a long process, I think they have genuinely made it as easy as possible for existing .NET developers to make that jump and now that .NET Core 3 and C# 8 have gone beyond what's possible with .NET Framework - literally, there are some language features in C# 8 and certainly APIs that a part of the .NET Standard 2.1, which are not supported by the .NET Framework 4.8. Now is the right time for .NET Framework developers to make that jump to .NET Core 3 in preparation for the unification to come next year.

Yeah. Other really small improvements with C# 8 that I personally have got irrationally large amount of satisfaction from are just simple things like [switch expressions](https://docs.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-8#switch-expressions): rather than having to use a big switch case statement, there have been a couple of situations where I've been able to really create a beautifully succinct switch expression, and it just made me very happy; and little things like [tuples](https://docs.microsoft.com/en-us/dotnet/csharp/tuples). What what's your what's your opinion on the correct pronunciation of tuple?

**Jamie**

I've always pronounced it tuple.

**Mark**

Tuple. See, for me, that just makes me think of, "it only has two parts to it." And then it also then makes me think of well, would it be a three-ple or thruple? Although we probably shouldn't get into that kind of thing. I tend to use tuple.

**Jamie**

I don't tend to use tuples in code, but I genuinely see where they can be used.

I think for me, the other big thing is in [Async IEnumerables](https://docs.microsoft.com/en-us/archive/msdn-magazine/2019/november/csharp-iterating-with-async-enumerables-in-csharp-8) is absolutely amazing. Absolute game changer.

**Mark**

Yeah. Really takes what Microsoft did with C# 5 when they introduced async and await and really leverages it in so many very powerful, very important situations. Yeah, I agree. Game changer there.

**Jamie**

So with a developer coming into the C# and .NET Core ecosystem. Are these [APIs, classes, etc.] covered in your book? Is it important for a developer who is new to this to know that, or are they just learning just enough to get them past the next set of tasks? And then maybe at some point, you'll introduce Async IEnumerable if it fits within the scope of what the book is trying to achieve?

**Mark**

What I've tried to do with this fourth edition of the book is to balance readers who are completely new to C# and .NET, and not overwhelm them with technical or, say, performance related features that would just be way over their head. So I haven't covered some of the really advanced performance improvements, which would be made in .NET core three. Whereas things like the new language features which are genuinely useful even in just day to day programming, I have included all of those. And that's partly where the book then becomes useful for that second audience: the type of audience who have maybe being using C# 20 years ago, or 10 years ago, haven't really done that much recently; and they are now interested. They've heard about .NET Core. They've heard about some of these new language beaches in C# 8. They want to start embracing that. They will find pretty much all of those new features are covered, at least to an introductory level, with then references to the official documentation or the design decisions that were made around that language feature on github so that they can learn maybe why that feature was implemented in a certain way.

**Jamie**

That makes sense to me because as a beginner developer, you maybe learn about control flow and for and looping and things like that. But you don't need to know exactly how a `foreach` works and how it gets the enumerator and yields the return[ed] results, and how LINQ works on a low level. You can, when you're starting, just assume that it's magic that when you put a `where` in, and you `.where(` a bunch of esoteric characters, and then it eventually sifts through my collection and gives me the things that match. And then when you've done that, you can go back and learn what is actually happening.

**Mark**

Yes. And actually taking that as a specific example: for the beginners, I do just take the approach of, "well, here is the syntax for a for loop. This is how it basically works. Let's see some code running." And then, for that particular example, I will actually say, "hey, are you wondering how this works? In a later chapter, I'm going to be introducing you to these things called interfaces. And there is this interface called `IEnumerable`. And so what's actually happening internally is that the compiler is doing a bit of work for you, but if you don't want to worry about that, don't worry about it." I'm just giving kind of hints to the more advanced readers, the ones who really love to know the nitty gritty details about what's really happening underneath. I don't want to hide that kind of information from them; while also not overwhelming the beginner. So I will often show a little bit, or just have a little bit of a paragraph just to say, "hey, in case you're wondering, here is where you can read more about how it actually works; for those of you who are interested. Otherwise, let's just move on to the next topic on. We'll learn about branching statements as well. A looping statements," that type of thing. Does that make sense?

**Jamie**

Yeah, that makes perfect sense. The phrase that I use is "learning enough to be dangerous."

**Mark**

Yes. After reading my book, there will be a lot of dangerous C# ninjas out.

**Jamie**

I've always found that it's the juniors who call themselves ninjas. Those of us who have been around for a while don't bother with "ninja", or "rockstar", or anything stupid like that.

**Mark**

Yeah.

**Jamie**

But that's my personal opinion.

### How Can Listeners Get In Contact?

**Jamie**

So where can people get the book from? What's the best place to do that? Is there a link on your website? Is it directly through the publisher? Is it Amazon? What's the best place?

**Mark**

My publisher, I'm sure, would want me to say that you should go to you [packtpub.com](https://packtpub.com) and purchase it through the website. Either as an individual ebook or a printed version. Of course, it is also available on Amazon and all good bookstores worldwide. You can also purchase a subscription to a whole bundle of great content, from my publisher Packt. Wherever you buy your IT books from.

**Jamie**

Just look for "C# 8 and .NET Core Three Modern Cross Platform" in whatever system, or shop, or whatever.

**Mark**

Absolutely, And as you can imagine, authors love to Google and search on Amazon for their own books; and I noticed yesterday that my book is the number one best seller in .NET Programming on Amazon.

**Jamie**

I have some more questions in a moment. But what about getting in contact with you, then? Is this something that you allow readers or other people like that to reach out to you to say, "hey I enjoyed the book." Or is it something that you discourage?

**Mark**

I would encourage it. You can contact me. Probably best through my github. My [account name on GitHub is Mark J Price](https://github.com/markjprice). So I do get some very useful feedback about the code that's included with my book, which is available in a repository on my github. And also just feedback, actually about errata, typos and things, in the book. So that would be where I would recommend or Twitter - same username: [markjprice](https://twitter.com/markjprice) or Gmail - same username: markjprice

**Jamie**

Excellent. Okay. So people can get in touch and tell you what they liked about the book, that kind of thing?

**Mark**

Yes, I welcome hearing from my readers. And as we kind of touched on earlier: I have already started working on plans for fifth edition. So if there is anything that a reader really feels that they'd love to see in the fifth edition, late next year, I am very open to hearing those suggestions.

**Jamie**

Okay. So that could be maybe go to github and reason issue? It doesn't seem like it fits.

**Mark**

Or just DM me on Twitter, or shoot me an email on Gmail.

**Jamie**

Okay, fantastic. One last question, then: you've been through an extensive career of learning, and re-learning, and teaching others. And your new book is about teaching new people the new technology, or teaching people who have already touched the technology but haven't gone into it in great detail a lot more about, "let's build something and let's talk about it. And let's get a little bit more detailed." Without giving away any of the secret sauce of how you are paid to teach people, what is maybe the one thing that you think is a great piece of advice to give out to someone who wants to learn something brand new, whether its programming or mountain biking? Is there one piece of advice that works, or is there a piece of advice that you think you would give out to someone to say, "hey, you would learn how to do this programming thing? Here's the nugget that you need to keep hold off in your brain whilst you are learning."

**Mark**

I do have some advice that works for me. Obviously I have a day job, so writing a book like this with 850 pages of detailed technical information takes a lot of effort, and the only way I was able to get that work done in a timely manner was by getting up at 6 a.m. in the morning, going to my local Starbucks - which happens to have a basement - and getting two hours of writing done before then going to work at 8 a.m.

Putting aside at least two hours of time in a quiet environment where you've got some water - keep hydrated - where you can really focus. What works for me is early in the morning. What works for other people is maybe in the evening. If you've got a family, try and get away from them. And really put in those two hours every day. It's about forming good habits that then keep momentum going. It's a huge challenge. That's something that works for me.

I've been quite interested in reading about the political suggestion off a shift to a four day week. What I think I would do if I lead a team of developers is I would try and persuade upper management to allow me to say, "okay, we're not going to switch to an actual four day week, but what I want to be able to do is have a four day development week. And then one day a week, I want my developers to be able to work from home or go to a cafe and spend those eight hours learning something new. And in order to get management buy in, maybe I'd have to say that that's going to be directly relevant to the job. But personally, I think even if that the day job a four day week was C# and .NET development, I'd say, "hey, if you want to learn python and if you want to learn about machine learning, go ahead. Spend those hours those eight hours learning something new." Because that releases the creativity, seeing a different language, seeing how it can be implemented. When they're then doing those other four days work there will be refreshed, interested, and, I honestly believe, more productive than if they were working five days. That's what I would do if I was managing a team of developers: develop for four days, learn for one day. Whatever that learning is.

**Jamie**

I like that. Primarily because it scratches the itch of wanting to help someone learned something, but also because I believe that, you know, it's been said before: No one can know absolutely everything. But the industry that we're in requires the discipline of lifelong learning.

**Mark**

Yes. That's a skill that you have to practise. And so by having management buy in and understanding that dedicating one day, it's not a waste. It's absolutely vital to building those skills in learning something technical and complicated in an official way so that you can then put it into practise. Yeah, I'd love to see all Business is kind of have that approach to lifelong learning.

**Jamie**

Well, I think that's a great point to leave the episode on, I think. That works out really well. Thank you ever so much for agreeing to spend part of your Friday evening when you should have been relaxing, and doing whatever it is that you do to enjoy your friend evenings. Whereas instead, you're sat talking to me, which is not so relaxing.

**Mark**

It's been a genuine pleasure. Thank you very much for inviting me. I've had a fantastic time, and it was really interesting hearing your background as well. So maybe in a year or two, I'd welcome an invite back.

**Jamie**

Oh, most definitely. Yeah. Let's talk about version five of the book. Yeah, when it comes out.

**Mark**

Yes.

**Jamie**

Let's talk about that. Definitely. Maybe we can get some of the audience to submit some ideas for things they'd like to hear for version five.

**Mark**

Oh, that's an awesome idea. Yes. Excellent.

**Jamie**

Just before we go then, could you just remind us of the title of the book again, please?

**Mark**

So the title of my book: "C# 8.0 and .NET Core 3.0: Modern Cross Platform Development," and I'm Mark J. Price.

**Jamie**

Excellent. Thank you ever so much.

### Wrapping Up

That was my interview with Mark Price. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and a full, searchable transcription the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/), and there will be a link directly to them in your podcatcher.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Mark Price on twitter](https://twitter.com/markjprice)
- ["C# 8.0 and .NET Core 3.0" available from Packt Publishing](https://www.packtpub.com/mobile/c-8-0-and-net-core-3-0-modern-cross-platform-development-fourth-edition)
- [ML .NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet)
- [Episerver](https://www.episerver.com/)
- [SiteCore](https://www.sitecore.com/)
- [Adobe Experience Manager](https://www.adobe.com/marketing/experience-manager.html)
- [Piranha CMS](https://piranhacms.org/)
- [Umbraco](https://umbraco.com/)
- [Blazor: You Want To Run .NET Where?!](/episode-25-blazor-you-want-to-run-net-where/)
- [Dependency Inversion Principle](https://deviq.com/dependency-inversion-principle/)
- [The Art of Programming](https://en.wikipedia.org/wiki/The_Art_of_Computer_Programming)
- [Code Complete](https://www.goodreads.com/book/show/4845.Code_Complete)
- [Shawn Wang](https://twitter.com/swyx)
- [Pattern Matching in C# 8.0](https://devblogs.microsoft.com/dotnet/do-more-with-patterns-in-c-8-0/)
- [Nullable Reference Types in C# 8.0](https://devblogs.microsoft.com/dotnet/embracing-nullable-reference-types/)
- [The Billion Dollar Mistake](https://www.infoq.com/presentations/Null-References-The-Billion-Dollar-Mistake-Tony-Hoare/)
- [Switch Expressions in C# 8.0](https://docs.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-8#switch-expressions)
- [Tuples in C#](https://docs.microsoft.com/en-us/dotnet/csharp/tuples)
- [Async IEnumerables](https://docs.microsoft.com/en-us/archive/msdn-magazine/2019/november/csharp-iterating-with-async-enumerables-in-csharp-8)
- [Packt Publishing](https://packtpub.com)
- [Mark on GitHub](https://github.com/markjprice)
