# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is episode 19: The .NET Foundation with Jon Galloway. In this episode of The .NET Core Podcast, I talk with Jon Galloway about The .NET Foundation. Jon is one of the hosts of the [Herding Code](https://herdingcode.com/) podcast, one of the hosts of the [ASP NET Community Standups](https://live.asp.net/), and is the Executive Director for [The .NET Foundation](https://dotnetfoundation.org/).

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Jon's Introduction

**Jamie**:
First thing I want to say, John, is thank you so much for devoting sometime and coming onto the podcast. I know that you're an incredibly busy person.

**Jon**:
Well, thank you for the invite. And and I'm excited about what you're doing with your podcasts and I'm happy to be here.

**Jamie**:
Thank you ever so much. But I really do appreciate everyone who takes the time to be on the show, you know, because I'm just some guy really digs on .NET Core and I want to sort of bounce it out to the world and say, "Hey, you guys, you should be using the software, and you should be using this framework" because I'm so excited about it. 

**Jon**:
Yeah, I agree with you.

**Jamie**:
For the incredibly small number of people who listen to this show but may not have heard of you or some of the work you do I was wondering, could you maybe give us a brief introduction?

**Jon**:
Sure. I have been developing with .net since you know, it was early on. I mean, played with betas. Before that before that I was doing, You know, VB6 and classic ASP. So I was really excited when ASP NET and just .NET in general came out. So I've been using it since beginning.

Prior to joining Microsoft. I worked at a variety of different companies, Internet consultancies, financial companies. My two kind of recent jobs before joining Microsoft: I worked one job with Phil Haack, who went on to, you know, be the PM for a ASP.NET MVC and some friends. And we had, you know, small consulting shop and that that was fun doing .NET development and you know as much open sources we could. And then after that, I worked for Vertigo software, and we get all kinds of, like keynote demos and things for Microsoft.

And so I've been at Microsoft since I think end of 2009 and worked in a variety rules, but they've always been related to .NET, open source development and a lot of kind of communities stuff. So presentations, building demos, supporting key note demos, building training kits, things like that.

And then for the past almost two years, I've been executive director of .NET foundation and at least half of my job at the .NET foundation is explaining what the heck the .NET foundation is so

**Jamie**:
Well, that's good. Then you'll have lots of practice for this episode of the podcast. 


**Jon**:
Yeah, exactly. Yeah, that that kind of takes us up to today.

### So What Is The .NET Foundation?

**Jamie**:
Since you've had so much practise, could you maybe give us a quick introduction to the .NET Foundation? You know what it is, how it works, all that kind of stuff?

**Jon**:
Sure. Yeah.

So the .NET Foundation is an independent, a nonprofit organization dedicated to supporting open source .NET. So that first kind of key word there is its independent. It's not part of Microsoft, so in the U.S it's registered as a 501(C)(6), which is it's a nonprofit, and it's a separate company.

So we do all the separate, you know, we file taxes we have a board of directors, we're separate business.

However, I'm a Microsoft employee. So the way that works is Microsoft donates my time to the .NET foundation. Same way as a company may you know, allow you to dedicate some of your working time towards an open source project or something like that.

So the .NET Foundation is its external to Microsoft.

It has some some kind of primary goals in supporting open source .NET. One of those is when you have an open source project that you care about, it could be really sad to have that project being dependent on one or two developers hacking on their weekends.  And then that developer moves away, or gets abducted by aliens, or just is not interested any more. And then that's the end of the project.

So we really want open source projects that we care about to be sustainable. And so we do a lot of work with .NET foundation to set up projects with legal, with support systems, build processes, things like secret sharing and that kind of stuff so that projects can be supported not just by one or two people, but by or, you know, small little group of people, but that they could be long term sustainable.

So what that means is, let's say, you know, you've got a project that I'll give you an example, a project like recently, JSON.NET joined. So as part of joining, we review who are the main contributors to the project. And it's almost all James Newton King, and this is the top open source, NuGet (package) you know, downloaded and used by millions of people, but really supported and developed by one person. So what we want to do in terms of making sure that it's bigger, it's continues to have the full support of James Newton King, but also is long term sustainable and kind of has his stamp of support and all that is, we set up things like code signing and instead of the log-ins and GitHub rights and all that just set up with James's GitHub account. We actually have the project owner joining GitHub org and this DNF admin account to that and that admin account, then can add on other contributors with, with James's permission. And then again, if James gets abducted by aliens or whatever, then we're able to bring on new contributors.

We also do things like, just kind of good practices for projects. Make sure they have the things like contribution guidelines and their licenses are all in place. We have legal services to review things as project join and on an ongoing basis. You know, it's all those things that are really important. If you're a big company and you want to use a library and you say,

> Can I trust this library to be around in two years and that they have legit license and all that kind of stuff

It's really important. But it's also boring and time consuming for an open source Project leader. They don't want to spend their time with all that stuff. So instead of that, well, try and bundle that up and handle that for as many projects as we can, so so that's a huge part of it.

Then there's other things that the foundation does just port open source .NET. One of those is we have a MeetUp pro group for meet ups around the world, and we have one 150,000 members, 245 groups have joined so far, and we pay the MeetUp pro fees for them.

What we're trying to do is build this center of gravity for open source .NET. It's got the full support of Microsoft, but it's not just Microsoft, it's the entire community. I mean, there's a lot more, but I've already kind of rambled on a bit. But that's kind of The goal is to support open source, .NET projects, and then to catalyze and and empower the community to kind of guess. That's a lot of business buzz words. But to make it really come alive and make it easier for new people to get involved in contribute and all that stuff. Is that clear? Is that good? I don't know. I'm still working on the pitch.

**Jamie**:
That's great, that that answers a lot of questions, actually. I did have a bunch of smaller questions that I had written down just before this interview And I was like, "ask about whether there's open source or closed source or whether it's big teams or small teams."

It seems like it's pretty much anyone creating anything open source for .NET can contact the .NET foundation and get these services: the legal, I think of the website, it says SSL and like you said, build engines and things like that.

**Jon**:
you know, SSL is one thing, but a tougher one to crack has been code signing.

If a team wants a code signing certificate, you actually need a business entity. So one of our members of our board of directors currently, as we're talking in January - and that's going to change in the future, as we're going to have elections coming up - but Oren Novotny has set up this code signing service, and we worked out this deal where we actually register trade name, or in the US it's known as DBA "doing business as" registration. So if a project wants to set up code signing, we actually are able to kind of register in their name and issue a certificate to them. And so it's an actual code signing certificate that will say something like Identity Server or auto mapper or JSON.NET or whatever.

And then we also automate things so as their CI builds run, those builds, are code signed. And that's useful because that works with NuGets kind of security systems, identity systems, and it's again it's helpful for if a company wants to use a NuGet package or a library that they can verify that it kind of meets all their requirements of "Yes, this is *the* distribution of it."

And again, those are super boring things as an open source project leader or developer  you don't want to spend your time messing with getting a trade name registered or getting a certificate issued to you and getting builds set up. And so that's something where we want to help out there and kind of handle that.

**Jamie**:
That's great.

Is it a case off any open source .NET project? Or is there like, a threshold for you must have this many users, this many downloads on NuGet, this much community involvement on GitHub? Or is it just:

> Hey, I have created on open source .NET library, and I want to get the .NET Foundation to help me out.


**Jon**:
Well, I'll tell you what it has been, and I'll tell you where we're hoping to go in the future.

So what it has been, is it's case by case projects have applied to join, and we actually have a backlog and I have some people that ping me and say, "Hey, we we've requested to join and when can we join?" And there's only so many that we can bring on at a time and also that we can support well.

Up till now, it's been basically me as Executive Director doing the day to day work, I get approval from the board of directors for new projects to join. We haven't advisory council that helps out some, but a lot of that is also waiting on me to kind of get them information or ask for help on things. And so up till now, we've had in the range of 60 to 65 projects have joined.

I would like to see to things happen in the future: one is for more projects to join, and we've got some plans for this year how to kind of expand that tthe .NET Foundation to handle that. But then also, there are a lot of projects that are below the threshold of: we don't necessarily need hundreds or thousands of projects joining the .NET Foundation, but there are hundreds or thousands of useful open source .NET projects out there.

So we'd also like to be able to do more kind of informally or more lightweight support for open source .NET projects where we're able to just say:

> Hey, you don't have to join the whole .NET Foundation and go through this whole kind of legal process and this review process and all that

We'd like to just be able to say:

> Hey, click through on this form if if you're in open source project and, you know, maybe we'll be able to set you up with these things.

So having kind of a lightweight model would be great, too. We don't have anything officially, in the works for that. TThat's just kind of along the lines of some of the things we brainstormed with the advisory council is like:

> Hey, how could we help out the broader open source dot net ecosystem, you know, with a kind of more lightweight model, too?

So those are, you know, the two kind of answers there: One is bring on more projects officially, and then Two is be able to kind of be more flexible in terms of helping projects that don't join the .NET foundation but are still part of the open source .NET community.


**Jamie**:
It sounds like, like you say that's an informal plan and not set in stone. You're still sort of figuring it all out, but that sounds like a brilliant way to think about it. I'm envisioning now - obviously I'm inferring, is that the right way around? I always get implying and inferring the wrong way round.

**Jon**:
Yeah.

So imply is what I say to you and infer is how you hear it. That's how I tried to remember.

**Jamie**:
Okay. I'll try to remember it that way too.

The way that I'm inferring it, the way that I'm envisioning a system is like I have an open source .NET thing - it could be .NET Framework or it could be .NET Core, you know, Mono, Xamarin, whatever - I submit to the .NET Foundation and you or The council might say, actually, that's not quite what what we can support at the moment, but let me put you in touch with a bunch of open source .NET contributors who may be able to help.


**Jon**:
Yeah.

**Jamie**:
And that might not be on a person to person basis, but that might be:

> here is a forum full of people who want to help but don't know what they can help with.

**Jon**:
Absolutely. Yeah, and that's the kind of thing where like connecting people, getting contributors in touch with projects that need help. That's a great thing that doesn't take a huge formal joining of a foundation to do. It's just more like thinking strategically about it.

And you know, we've taken some baby steps with this, and I'd love to see it get bigger. But for instance, in August and September of 2017, we ran a thing called [.NET Summer Hackfest](https://dotnetfoundation.org/blog/2017/07/07/announcing-net-summer-hackfest-2017) and it was end of the summer and we took a six week period and we had probably about five to 10 projects - it's been a little bit, so I don't have the exact number, but I would say seven or eight projects - and they hosted a two week hack event and it was virtual is online. We had some guidance for them. We said, "Hey, have a bunch of up for grabs issues. Have a page that says Here's how to contribute. Here's how to get started, maybe having event." Some of them had a video call and said:

> Hey, if you want to get involved, here's what to do

We had a budget for it. We had some some of the projects had large... one of them turned it into  a mini conference.

And so we just got developers hacking on projects and contributing to projects. And then the project's set some goals of "here's what we hope to get done during this time. Here's the little steps, you know, here's some issues from small to large," and so that was really cool and over a course of of six weeks, there's [Humanitarian Toolbox](http://www.htbox.org/), there were several projects that upgraded .NET Standard 2.

That was an example of a thing where we just connected people and we didn't you know, it was more of a lightweight sort of thing. And we also, just from time to time, have done things where we'll see a project on Twitter says, "help. We need, you know, our certificate expired and we're taking up a the collection." Well, that's something where we have budget where I can use the company card and donate a hundred and fifty bucks or something. That's not a big deal.

But again, that's something where I'd love to expand, and have a larger fund and have some people looking out and saying,

> Here's where we can you know, we've got a budget of five thousand or ten thousand dollars a year and let's strategically jump in and help out a project.

And that could be all sorts of, you know, maybe something where Project needs translation services or a vendor to help review come tests or documentation or soemthing. Maybe write from tutorials. The sky is kind of the limit, you know, when you start thinking about it and again, there are larger projects that need really dedicated services, and then they're other projects that just could use some help from time to time.

### What Is The .NET Foundation Based On?

**Jamie**:
I don't think that there are very many other application frameworks - I guess .NET is a framework, but it's more of a framework and a runtime and hundreds and thousands of APIs and libraries and stuff. But I can't think of another foundation off the top of my head that does this for a very, very popular framework and API set, that can offer something like that.

I know, obviously we all have access to Twitter, or we can just shout out:

> Hey, can someone help me with you know, I'm looking for someone to help with this; get someone code review this?

But I guess having this large foundation and a lot of people, I've seen, in the foundations say:

> Yeah, Okay. I will bounce this out

because I've seen you do it. I've seen you go: "Hey, can anyone help this person?"
and retweet something.

I mean, that's a huge thing for all of the smaller open source developers. Just getting the voice out I guess.

**Jon**:
Well, yeah, it is great to have, like, taken a more organized look at that. You know, like probably the thing that makes me the most excited. When I think back of, you know, recently in my career or just my entire career is being able to help other projects out.

Like the code I've written has been fun and and some of it still use frighteningly enough. But the best thing is when developers come up and talk to me and say, "Hey, I used your course to do this, or and now I might have a job in software development." 

And that same sort of thing being able to highlight projects over time, I've been able to do that on the ASP NET Community stand up and on the ASP NET website over the years. And it's It's so great when projects say, "Hey, thanks for that boost and we got new contributors out of it," or, "we got, you know, big bump and downloads." So being able to have that not just be random, like, Oh, I happened to see this thing on Twitter, so I retweeted it. You know, like, have it be a bigger orgainsed is great.

Also, you mentioned the thing about like that there's not much else out there like this, and I had not cared about or thought about software foundations at all. But as being part of this I've got more aware of, you know, there's several other software foundations out there, and in a lot of ways we're still learning from them. For instance, there's the Apache Software Foundation. There's Linux Foundation. There's Node Foundation there's, you know, tons of foundations and these foundations all have these similar sorts of goals of: they're non profits and their supporting open source.

And whole idea is: "Hey, if you care about open source, you want it to be sustainable" and open source is hard to, the way open source is set up is it's volunteer time; it's community contributions; it's people donating, you know, and so it's hard to kind of think long term about it and to make sure that it stays around. It's hard for companies to say, "Yeah, okay, I've got these paid companies that I can buy their product from, and they'll offer me a support contract or it can use this open source projects that looks great, but I don't know if this project's going to be around in two years." And so software foundations really kind of have this dedicated goal of supporting open source projects.

And so, you know, in some ways we're we've done some things that are new and breaking new ground. .NET has an interesting heritage because it's been almost completely run by Microsoft, but from the beginning there were some kind of open source routes to it like it was developed as an ECMA standard. And there've been a lot of things that Microsoft over time has released as open source. But it's been this weird kind of, "yeah it's open source, but it's mostly a Microsoft product, and you need to run it on Windows and you need IIS." Microsoft runs all this stuff. And so, whereas other open source projects have been open source from the beginning you think about like Linux or Java a lot of others. And so in some ways we're catching up a bit to some of these other ecosystems, and we're learning what's worked well for them.

And I think that's great. I think it only makes sense to learn from what's worked well for people and  to contextualise it in places where the same model works great for us, that's great. And if there are others where we say, "Hey, we can we can do something that works better for .NET. That's what we'll do."

**Jamie**:
Just switching it up slightly, then. I think you've mostly covered this anyway, but it's still like to ask: So you are the executive director for the Dark Knight Foundation, could you give us an idea of what that means? Is this a community outreach thing? Is this a developer advocacy thing? Is this a you are, and I hate to belittle it slightly but,a go-between between the community and the directors, you know? How does that all work?

**Jon**:
Yeah, so an Executive Director works for the board of directors. So it's funny. It's it's a job title that both sounds really big and impressive, and on the other hand, it's like I work for people. So I'm not in charge of anybody, right? So it's a lot of things. It's basically the person that oversees the day to day operations of the foundation.

So this week some of the things where paying off bills and setting up financial things and making sure beginning of the year financial stuff was done. There's other things that's as simple as running the website and updating content.

There is stuff like supporting projects. So you know, a project says, "Hey, CLAs aren't working on our website - contributor License agreement - can you help side that up?"

Just before this podcast, we had our monthly advisory council call, and so I was briefing the advisory council on, "Here's what we're doing," and getting advice from them. And our advisory counsel is amazing and they are great at saying like, "All that stuff sounds good. Except for this thing. I think you're going about it wrong. And have you considered this?"

So those are, the sorts of things. It really is all over the place, there are so many things. I have huge OneNotes that have spelled out all the processes of: "Here's how to set a new project up in the CLA Bot"; "Here's how to add a new project"; "Here's a checklist for adding new projects, and the approval processes"; "Here's the legal steps for registering a new DBA." There's just tons and tons of of admin sort of things.

So there is that, there's also the kind of public face of .NET Foundation. So things like, you know, talking to you on podcast and helping get the word out, and hopefully explaining software foundations in a way that doesn't bore people and makes it real to them. I speaking conferences.

It's really hard to kind of narrow down what it is. I would just say it's the person that every day cares about what the .NET Foundation is doing and and manages the business stuff to get it done.

**Jamie**:
Wow, that is an awful lot. I mean, I turn up for work, I look at the back a lot of work, I write some code, I test my code, I write some extra documentation and I go home. I can't even imagine how you managed to get all of that done. And I seem to remember seeing you say about how you're traveling all over the planet to go to conferences and things, and I hope you don't mind me saying this, but it is only a few days ago when you tweeted out something about how you wake up in the morning, you work out, you do a whole day's worth of work, you fly to Europe, you work out at local time, midnight, then go to bed.

**Jon**:
Well, that's that's not every day.

**Jamie**:
How do you manage to get all of this done during the day?

**Jon**:
That's a bit of a side thing. But that's this past year I had made a silly New Year's resolution that I sometimes regret. But I told myself I was going to exercise every day for a year.

You know we're all getting older and sitting working at a desk it's harder to kind of keep active. And and so I somehow did it, and I hadn't thought ahead about how difficult that was going to be on days where I had a flight from California to Europe and there were days where I was getting up at five o'clock, exercise, hurry to the airport, fly, with the time change it would be night before I would get to my hotel. And then before midnight, I would sneak in that day's exercise. But I actually found that it gave me a lot more energy. Exercising consistently actually made me have more energy day today.

You know, it's funny. Every day I feel like I've got a backlog and my my goal is always to make the backlog a little bit shorter than it was the beginning of the day, and many days that's really hard to so.

So a lot of it is kind of looking at a big list and saying, "Which of these things do I absolutely have to get done today?" But then also looking at the long term things and saying, "This has been sitting out there for a month, I need get done."

**Jamie**:
Okay. So what you're saying is for a long, happy developer life: lots of exercise. I mean, it's good for you, right?

**Jon**:
Yeah, I really think so. It's something where it kind of shifts around. I've seen some really interesting things with this, where they talk about how it actually changes your brain chemistry, you know, and it changes your body.

And I haven't been completely rigid with this, but I've been trying to do DuoLingo and learn some Mandarin Chinese. And the same sort of thing: I'll never be good at a Mandarin Chinese, but it's exercise.

And I think also it is really easy for developers to just be online, developing programming and being the developer community all day every day. And your brain sometimes just needs a rest from some of that.

**Jamie**:
I can understand that completely.

I'm a bit of an amateur Japanese speaker. I studied it for a while at University. And when I need to switch off, it might sound really big headed, but when I need to switch off I'll just put on a movie that's in Japanese - with the English subtitles in case I can't be bothered to try and parse what people are saying. And it's just that big switch of, "I've been writing lots of code and doing lots of problem solving" to "I'm going to turn that part of my brain off and let this language parsing bit take over and just let the logical side of or the logical parts of my brain just relax and chill out."

**Jon**:
Yeah. That sounds fun.

**Jamie**:
Well, I mean, it can't be. You can't be running on full steam all the time, can you?

**Jon**:
I think that that also makes your time that you are writing code or doing your work makes that time more productive too; Because you're more flexible in your thinking. And you're not so mechanical about it all.

**Jamie**:
Sure, Yeah. I feel like it gives you subconscious a chance to sort of go, "I'll figure this out for you whilst you're doing something else - you're doing the dishes, you're making some dinner. I'm going to figure this out for you in the background, and I'll present you with the answer." Because the subconscious part of the brain is so powerful. It's much more powerful than, from what I've been told, much more powerful than the conscious part of the brain. So it's able to figure things out a lot quicker than your consciousness, you know?

And like I say, you've gotta rest, you know, something's going to give.

**Jon**:
Yeah, absolutely.

### The Elections

**Jamie**:
Now that we've had a little diversion from the .NET Foundation, maybe we could bring it back to the foundation just for a couple more things, if that's all right?

**Jon**:
Yeah, and you know, one of the things that's probably most important that we should talk about is some of the recent announcements we've been making.

**Jamie**:
Sure, definitely

**Jon**:
I'll start with the simple one, and then I'll go for the bigger one next.

So the simple one is we have expanded our technical steering group to a corporate sponsor program. And what that means is previously we had a technical steering group, and that was companies like Google, Red Hat, Jet Brains, Samsung, Unity. And those companies, for the most part, were like doing things that were pretty deep, technically, into .NET.

They were doing things like shipping .NET or supporting frameworks on top of .NET, and we had companies talk to us and say, "Hey, we'd like to join .NET foundation." But a lot of times they were companies that cared about .NET, that their business depended on .NET, or they had large line of business applications in .NET, that sort of thing, but it was kind of a different model.

So what we've done is we've expanded the technical steering group to a corporate sponsor program. We announced at the Connect event that we had three new companies joining us, and those are Pivotal, Telerik, and Insight. And what's neat with that is Pivotal is more of a platform company, and Progress Telerik is Developer tools, and Insight is a consultancy systems integrator. All of these are companies that heavily used .NET, their businesses rely on .NET.

This kind of show is kind of the breath of what we're looking for in other companies, and I encourage other companies and people that are listening: If this sounds interesting to you, reach out to me and I'd like to see more companies join. And so these companies are sponsoring .NET foundation, they're they're contributing towards supporting open source projects, so that's really cool.

The other big thing we announced though, is open membership and one of our secret weapons in the .NET foundation is a member of our board of directors is Miguel de Icaza. And Miguel helped early on in the Gnome foundation on their border directors, and he kind of helped us figure out and evolve our membership model. And also the previous executive director Martin Woodward had done a lot of work on this.

So what we settled with is a newer, open a membership model that makes it easier for people listening, if you've contributed to .NET, to join the .NET Foundation as a voting member. And then voting members are also eligible to run for election in the .NET Foundation board.

So up until now .NET Foundation has had three members on the board of directors, and two have been Microsoft employees, and one has been a community director, but they've been appointed by Microsoft as well. And what we're moving towards is: we're expanding that from three members on the board of directors to seven, and only one of those is appointed by Microsoft. So that's six other members of the board of directors at our community elected.

Let's step back and see what that means. Let's say you have contributed two .NET Foundation project. That doesn't just mean, you know, Core CLR or Core FX, it could be .NET Docs. It could also be a .NET Foundation project: Automapper, Identity Server, Polly Project,  tons of different open source .NET Foundation projects. So say you've contributed to one of those projects,  you can apply to join .NET Foundation, and now you're eligible to either vote in the elections or run for a board seat.

So we're going to have the elections process kickoff late January and the elections are: somebody will say, "Hey, I'm going to run for border directors. This is why I want to be on the board of directors. I am pushing for," whatever it is your passion about. Maybe you feel like .NET Foundation should be more present and active in the start-up space, or should be engaging with students more. Or you would like to see .NET Foundation doing more to make open source projects more economically viable. You know, making sure that companies are able to pay to support projects or things like that, right? So people will campaign. It's a one month election process and then anyone that's a member can vote in that election.

This is now the time where the .NET Foundation very clearly is much more than Microsoft, and it's got the full support of Microsoft. We've got one board seat that is appointed by Microsoft, and Microsoft deeply cares about and uses .NET. So this isn't the open source where it's going away kind of open source, right? This is the open source where it's like we love .NET so much that we want more people to be able to join in and get involved.

So we would love to see the community leaders, and it was amazing it the Connect even when we announced it. Immediately, we had tons of people, the top names and .NET open source were signing up.

So if you go to the .NET Foundation site [.NET Foundation dot org](https://dotnetfoundation.org/), right at the top there's a banner that that gives you information about joining the .NET Foundation. It's a quick little thing You fill in your your contact info; give your GitHub account name; give us some links to some commits or contributions you've made. We review that and then we're planning to be like, "Hey, if if these are legit contributions, you're welcome aboard."

We based this partly off of Gnome Foundation and F# Foundation. Both of those are projects where people join. We do ask for a membership fee or dues, so we're asking for $100 per year. This is based on like F# Foundation has had that. However, we understand that, like for students, that varies economically and around the world in different countries $100 US may be asking too much, and that's fine. Basically you're able to change that amount. So we're asking for one hundred dollars by default. But you're able to lower that or exempt yourself if you need to as a student or whatever. Because we want anyone that really cares about .NET, and is a contributor to .NET to get involved.

Looking at other foundations out there like F# Foundation, there's thousands of members, Gnome Foundation, several hundred. And we would love to see lot of developers join. And we'd like to see thousands of members of .NET Foundation.

The election process for the board is every year, and we'd love to see the leaders, the people that are writing the blog posts, that are starting the discussions on Twiiter and saying, "here's how open source should be better in .NET."  Great, get involved and run the show. Do it.

And we've got a budget now for you with corporate sponsors. It's up to you. It's up to you to get involved in to run things, and I'm excited to see where it goes. I have some ideas of things I love to see happen, and one of the biggest things is I'd love to see new ideas come in that are better than I've got.

That's the kind of pitch on what we've announced: the corporate sponsorship, to provide a budget, and then a board of directors that is community elected and can spend the budget, and can get involved and get stuff done. 

**Jamie**:
Almost anyone who has made a sizable contribution to one of the open source .NET Foundation projects? So the Core CLR, the docs, anything like Polly, like you said or I guess orchard. That's one of the .NET Foundation projects, isn't i?

**Jon**:
One of them. Yeah, and you can go out onto the .NET Foundation site. There's a projects thing where you can click through there.

As part of this, we've had people say, "Hey, I'd like to be a contributor. What can I contribute to?" And so part of this is going to require us to make that easier for projects. Some projects honestly, are kind of hard to contribute to, you can't just wander into the Core CLR and start making contributions and pull requests. However, docks are a lot easier to. And then there's a lot of other projects out there that can use more help, smaller projects. You know, you've got something like Automapper JSON.NET, Identity Server, all these projects. And so some of them have up for grabs issues. That's something where we're going to be publicising:

>Hey, if that's what's holding you back, if you'd like to become a contributor, here's some projects where you can jump in and do that.

And they don't have to be huge contributions. If you correct spelling on two words in the docs, yeah that's not really a valid contribution. But it doesn't have to be huge, we're not looking for for enormous contributions. We're just looking for your contributor to .NET.

**Jamie**:
Sure. Okay, so it's more like a passion that's coming through for .NET, and open source, and helping out rather than just you've written up the suite of tests, but we can't really tell that that's what you've done. Maybe there's some docs that aren't really well written, or maybe they haven't been translated to another language. Someone jumps in and starts that translation project, getsmaybe three quarters of the way through it goes, "that's about as much as I could do at the moment. But maybe I'll come back to it."

**Jon**:
Absolutely. Yeah.

**Jamie**:
So you've mentioned the elections. They're coming up soon, are they?

**Jon**:
Yeah, so the target date we have for that is starting January 21<sup>st</sup> and running for a month. The election process is pretty lightweight. It's basically a pull request to tell us what your credentials, are and why you're running for the board, and what you'd like to accomplish.

I'm interested to see where it goes. People make campaign on social media, or get on podcasts, or whatever. That's all fine. But you know, we'd love to see people that are passionate about .NET campaign. And then any member can vote. It will be an online election process. We based on what Gnome Foundation does using a system called OpaVote, and it's a single transferrable boat. It's a rank choice vote where you can vote for multiple people.

So, and again, there's there six open seats. The Microsoft appointed seat is going to be Beth Massi, we're excited about that. She's been part of .NET for forever, and she's been working with .NET Foundation. She's currently .NET Foundation secretary. She was part of the original kind of founding of the .NET Foundation, so she's perfect person to have seen Microsoft board seat.

But we've got six open seats, and I'd love to see people that are passionate about .NET, and ready to get involved, and push it where you want to go. I'd love to see those people actively campaigning and in those board seats.

**Jamie**:
Also, if anybody wants to be on the podcast and talk about why they should be elected, just get in touch.

**Jon**:
I'd love to hear it.

Honestly, that's like I said, the biggest thing I have ideas, and dreams, and goals for what I'd love to see that .NET Foundation do. But I'm certain that there are plenty of people out there with better ideas and bigger ideas, and I'd love to see him.

**Jamie**:
Great.

So if people want to get in contact with you, or the .NET Foundation or, anything like that, where's the best place for listeners to go to to learn more about maybe yourself, or to get in contact with the .NET Foundation?

**Jon**:
So you can get in contact with me directly on Twitter, I'm [John Galloway](https://twitter.com/jongalloway). My email address is Jon, JON, at .NET Foundation dot org. You can also just email contact at dot net foundation dot org, that hits me, and it also hits a few other people: Beth Massi and some other folks.

So that's kind of the official generic email address contact at dot net foundation dot org. We have a Twitter handle also for .NET Foundation, that's [@dotnetfdn](https://twitter.com/dotnetfdn).

I'd recommend follow .NET Foundation website. We have a blog, we also have a newsletter. You can sign up on the .NET Foundation newsletter, and that's linked on the website. There's a thing "Get the news", and from the news we have links to that signing up for the newsletter. So that newsletter goes out usually about once a month. And then we also have others just kind of as something comes up.

Those are some of the main ways, if in doubt, just ping me [@jongalloway](https://twitter.com/jongalloway) or contact at dot that foundation dot org and happy to hear from you.

**Jamie**:
All that remains to say is thank you again, Jon, for being on the podcast. It was an absolute pleasure to talk to you today is a little nervous going in if I'm honest but an absolute pleasure to talk to you.

**Jon**:
Oh, this has been great. I've been happy to talk to you, and I thank you for what you've been doing for the .NET community. I was excited to see your podcast come up, and I really enjoy the depth that you you've put into your show's. Starting from the [first episode](/episode-1-a-brief-history-of-net-core/). If you haven't heard it, the first episode I thought was really good. Which a lot of podcast don't start, I can tell you [Herding Code](https://herdingcode.com/) did not start out very well. It was kind of all over the place. So I really appreciate what you're doing is Well, thank you.

**Jamie**:
Well, thank you very much for saying so.

So I definitely get in contact with Jon. Seriously, one of the best guests I've had so far. Loads of fun. Thank you ever so much.

**Jon**:
Thank you, Jamie.

### Wrapping Up

That was my interview with Jon Galloway of both .NET Foundation and Microsoft. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and a full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/).

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [The .NET Foundation](https://dotnetfoundation.org/)
- [ASP NET Community Standups](https://live.asp.net/)
- [Jon Galloway on twitter](https://twitter.com/jongalloway)
- [.NET Foundation on twitter](https://twitter.com/dotnetfdn)
- [The Herding Code Podcast](https://herdingcode.com/)
