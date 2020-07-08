# Episode Transcription

This episode is sponsored by elmah io. elmah io is cloud logging, deployment tracking and uptime monitoring for asp.net core, mvc, web api, well everything .net really. Sign up for a free trial and use the discount code netcorepodcast, all in lowercase, for a 10% discount.

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is episode 18: The History of .NET with Richard Campbell. In this episode I interviewed Richard Campbell about his upcomming book on the history of .NET, and the Humanitarian Toolbox. Some of you may know Richard Campbell from the [.NET Rocks!](https://dotnetrocks.com/) and [Run As Radio](http://runasradio.com/) podcasts and his work with the [Humanitarian Toolbox](http://www.htbox.org/).

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Advice From The Zenith of Podcasters

**Jamie**:
Thank you very much for being on show Richard. It is a great pleasure

**Richard**:
My pleasure too Jamie. Thanks so much for asking me.

**Jamie**:
I talk about different members of the podcasting community and I feel like people like yourself, and [Scott Hanselman](https://hanselminutes.com/), and Carl are right up at the top as the zenith.

**Richard**:
I appreciate that. I think the only thing that we've done right is that we got started early - we've been around for a long time. I really enjoy what we do, and I have a great time making those shows, and I don't see us stopping any time soon.

**Jamie**:
Everybody that I talked to before I started this show said:

> Record four or five episodes first  and just find your voice, find what you want to say. Then just ditch those five because they're going to be terrible. And now that you've gotten those five out of the way, you can start sounding a little more professional.

I don't think I've managed to do those five in the 13 or 14 episodes that I've put out so far, so hopefully I'll find my voice soon.

**Richard**:

Yeah, I would agree.

Don't throw anything away. Your legacy is important too. And I think that listeners appreciate that you're evolving.

Honestly, we've dialed the professionalism down a little on [.NET Rocks!](https://dotnetrocks.com/). We really, in the early days, looked at ourselves as like radio and wanted everything to be perfect, and fixed every little thing. But I think more people are comfortable with the fact that there are mistakes in audio. And so we've left in things that we though were funny but were mistakes, and I think it makes it a little more personal. I think we're in an era now in podcasting were that familiarity is almost more important than perfection.

And so I would definitely encourage you to not waste anyone's time. Like if I'm looking for a note or I have to double check a fact or something, I'm gonna edit that out. But if you fumble on something and it's a humorous outcome, that's just real life and I think people appreciate hearing that we're not as perfect as the audio engineers make us seem, and that  we're human.

I think that warmth and reality and truth are more important than perfection.

**Jamie**:
That makes a lot of sense. I do know that I spend *way* too much time going through and removing all of the "umms" and "errs" thinking that it'll sound brilliant. But when I listen to it again, I can hear where the volume drops off.

**Richard**:
Yeah, well you're your own worst critic and you always will be. I have a tough time listening to podcasts *because* I only hear the mistakes.

I have the good fortune that I primarily learn through reading, so I don't have to listen to a lot of podcasts. I do listen to some, but it is painful for me because I'm very critical of the product. I've made a lot of it, and so I think it's interesting to decide how far to edit. We have done the "anti umm" thing, but I'm only going to make edits where I know it's not going to be intrusive - like, we're actually making it easier to listen to the show.

**Jamie**:
That makes perfect sense because, like you say, you want that personal experience: this is a group of people discussing something.

**Richard**:
Yes.

**Jamie**:
And it's off the cuff. It's not scripted, it's not preplanned. There aren't certain beats to hit.

**Richard**:
And so at the same time you don't wanna waste anyone's time by not knowing what to talk about. What everybody really wants is "I wan that sense of a conversation"

You know Carl's original inspiration for .NET Rocks!, which predates the word podcast by a few years, was actually in the speakers lounge at conferences. Seeing, you know, a [Billy Hollis](https://twitter.com/billyhollis) and a [Rocky Lhotka](https://twitter.com/RockyLhotka) arguing over the way that a particular piece of code should be written, what was the right way, and just acknowledging that that sort of conversation is so valuable that everybody should here it. So let's capture it.

And if you actually put on a pair of headphones and listen to .NET Rocks! you'll notice that we kinda position ourselves around a table using panning. So, I'm a little on the right, Carl's a little on the left, and the guest is more in the centre. But I really wanna simulate that effect that you are sitting at a table with us while we have a conversation.

**Jamie**:
I may have to emulate that for this episode.

**Richard**:
Feel free.

Everybody needs to learn more anyway, right? And anything that we can make it easier to learn, and so making people feel comfortable so that they can focus on the story, on that conversation, that's absolutely the goal. If I can have you even forget that this is a recording, that you're just there, then we've done our job.

**Jamie**:
I've been making notes the entire time

**Richard**:
(laughing)

Well after a couple thousand podcasts you sort of get a feel for some things. Although admittedly, the industry has changed several times since Carl started out in 2002. So being old in this isn't automatically an asset. I also struggle with: "are we dinosaurs?" that we have a lot of behaviours that aren't relevant any more; because technology has evolved, and the audience has evolved and the perception of podcasting has evolved, too.

**Jamie**:
I suppose it's a difficult line to balance.

**Richard**:
Yeah.

I'm grateful for what we've done so far, but I don't presume infinite longevity in this either. I am very aware that we all have a lifespan, and that you can only make so many things, and if you're not still passionate about it, there's just no point.

**Jamie**:
That's very true.

### The Book And a Different Show

**Jamie**:
Hey you never know, in 20 years time somebody might be writing a book about the history of .NET Rocks.

**Richard**:
Yeah, that's an interesting question. And part of working on that book has been how much do I interject about making the shows?

You know, many of the conversations and connections come from making the shows in the first place. I've done a few live presentations about the history of .NET 

*see the links section for links to a number of them*

and I do interject moments from the shows where, "here's how the story ties into..." and "we actually make a show with that guy at that time". I mean, once of the classic ones is "why did we make [The Tablet Show](http://www.thetabletshow.com/)?"

You know there was this period from 2011 to 2014 where we made 130 episodes of a different show. And the reason is, I'm happy to talk about it today but I didn't want to talk about it at the time because I thought we were overreacting. But we came out of the BUILD conference, the first one in 2011, where they were talking about Windows 8 and WinJS and real JavaScript Focus, and they really didn't talk about .NET. I looked at Carl and said:

> What if .NET doesn't rock anymore? What are we gonna do?

I Microsoft were going to make this shift, not that they were saying that they were going to, but all of the hints were there. We were a bit freaked out about it. Plus we were also struggling with at that time .NET developers didn't build stuff for Android and iOS and so forth, so did it make sense to do those shows at .NET Rocks! anyway?

So lighting up The Tablet Show was our contingency plan. Here's a place to put all of this content that I think it important, but doesn't necessarily fit within the .NET Rocks! theme. And if .NET is really going away - which we know now it didn't do, but it seemed threatened at the time - we have another show to fall back on, and that's what we'll end up putting all of our energy into.

And then by 2014 it became apparent that iOS and Android development was just part of the .NET repertoire as well, it became hard for me to figure out which shows should I do on .NET Rocks vs do on The Tablet Show, they were two of the same, and so we rolled them back together.

**Jamie**:
Yeah. If you're standing at the forefront and this fork in the road is appearing, you don't want to place all of your eggs in the same - I keep using loads of mixed metaphors today.

**Richard**:
(laughing)

Well, and that's the whole thing: it was a contingency, and it solved certain problems that I was having in content planning anyway. And it was enjoyable, like it was fun to make another show, to pick up new advertisers, and to build up a new audience.

You know, one of the side effects of being first is that you have this huge audience because you were first. Could we actually build another show? We didn't know the answer to that. Even with the support we had, the number for The Tablet Show never got as big as .NET Rocks! It's just not that easy to get new listeners. It's a challenging thing, even for old guys.

And so rolling it back was just

> why are we separating this? It doesn't make any sense anymore. .NET is clearly thriving, and tablet developers are .NET developers, so let's just put this thing together

And we consolidated the two shows together. So there's just this stamp of time of 140 episodes still running over on thetabletshow.com

**Jamie**:
And, like you say, it's part of the legacy of the .NET Rocks! family of shows.

**Richard**:
Yeah. But also, I think, a part of the story of .NET itself.

The reason that it's interesting to write a book at this particular point is that that light is shining very brightly on .NET, and we're in a good place. But you don't really know that you're in a good place, unless you've been to a bad place.

And so, part of writing down the story is not only to capture that early history where I think, you know, we're gonna lose it soon - it was 20 years ago. But also to talk about how dark it got. Because you don't appreciate the light unless you appreciate the dark.

So I really don't want to shy away from both aspects of what actually happened with .NET. And I'm a little conflicted, as the storyteller, because I was also there. I had my own emotional reactions to it, my own plans for business to it. But I'm also trying to take the middle road of:

> What were we thinking?
> Why was it going this way?
> Was it unreasonable, that focus on JavaScript at the time?
> Did .NET still make sense? 

I appreciate the idea that you need to question those things from time to time. Because if you don't, if you just presume that you're right all the time - that it's always been this way, and it should continue to be this way - well you're gonna be surprised one day when you're really, really wrong.

### Ontological Humility

**Jamie**:
A lot of people who are new to development, I find, and some of the people who haven't had a chance to read some of the great books of our industry:

- The Pragmatic Programmer
- The Mythical Man-Month
- Code Complete

they forget that we don't write code for the computer to understand, that's what the compiler does, we write code for other developers or other IT professionals to understand. Because it's their job to maintain it, and to make it better, and to add new features to it. It's not the compilers job to do that, it's other humans. I think Steve McConnell actually calls it our prime directive, as developers, to write code that other people can read and understand.

**Richard**:
I lean heavily on this concept called "ontological humility". Which is

> Don't presume that the way you're thinking is the only way, or the right way to thinking

New people that are gonna look at your code in the future are gonna think differently, and if you can help them to understand what you've done, and if they have the humility to understand that you did the best that you could with the skills and knowledge that you had at the time, knowing that later on there will always be new knowledge, then you'll perceive things differently.

We respect the code that we wrote before, and we sustain it, we find ways to maintain it. You just don't look at a piece of code and think:

> This needs to be re-written

If it works, even with it's rough edges, it's still worth while.

**Jamie**:
Precisely. Just because some code already exists, it doesn't need to be refactored and rewritten.

**Richard**:
Well code that already exists is automatically more valuable than code in your head, because the code that already exists does something. The code in your head is really just noise.

**Jamie**:
That's true. I'm really enjoying this conversation. It's getting incredibly philosophical all of a sudden.

**Richard**:
I'm afraid that I'm getting old Jamie. All I have left is philosophy. I can't do any real work anymore, nobody let's me type like that.

**Jamie**:
(laughing)

### The History of .NET

**Jamie**:
The reason that I've asked you to be on the podcast is that I would love to talk to you about a little on the history of .NET.

**Richard**:
Sure

**Jamie**:
I know that you've been quite vocal about the fact that, as you said earlier on, you're writing a book on .NET, and I believe that there was an episode of .NET Rocks where you said that it may end up being several books. Or that there may be several companion books, just because there's that much information.

**Richard**:
I've also come to appreciate that .NET is different things for different people.

So I've had conversations with someone who has worked in .NET for many, many, years but they've always been a web developer; and so their relationship with .NET is with ASP.NET. Like maybe they did some time in webforms, and they did some time in MVC, and maybe tied it in with Entity Framework. But that's their view of .NET.

But then you spend time with someone who is a client developer. Perhaps they came from Visual Basic, working in the early versions of WinForms, and moved over to .NET; but they're still a WinForms developer. And they may or may not have gotten involved with WPF, but they're a client side developer. That's their experience, that's their relationship to .NET.

And the same for mobile. Windows Phone - the modern one - has certainly had a bumpy life. But we talked to folks back in the CE era too, that were building stuff in mobile. Then Windows Phone 7 was actually a variant of Silverlight, so a lot of Silverlight folks jumped over there. But 8 was substantially different, and 10 different again.

So there's a story there as well in Compact Framework, and some of the early IoT stuff. There's a lot of different aspects to .NET. It's too broad a product, and I want to make something readable. It can't be War and Peace; I don't want this titanic book, it doesn't serve anyone.

But I also want to honour these different aspects. So I've come to appreciate the idea that perhaps I don't need to dive deeply into any aspects of the technology of .NET and more talk about the story of .NET, which is this product originally developed to support enterprise developers consuming Windows. And then evolved away from that.

You think about February 2002, when .NET is announced, and literally the tag line is:

> 22 languages, one platform

Which was the counter point to what Java's marketing was, which was:

> Every platform, one language

That's where .NET began. And now look, today, at this cross platform, open source product. It's not anywhere near the same product. What happened? How did that happen? That's kinda nuts.

And that's the story that I'm revealing, bit by bit, in all of the research. We're recording this at the end of November, and it's been about a year of doing interviews and I've got 60 to 70 hours of interviews with various people, both inside and outside of Microsoft, about their experiences building .NET. And I'm not done, there's still much more research to be done, so it's going to be a little while longer. But the meat of that is large enough that I can just tell that political story, and it should be an interesting book.

And then the companion books could be, "how about a book about web development in the Microsoft stack" that goes all the way back to Active Server Pages and InterDev, as well as up through .NET itself. And the same for client side development. So it's a way for me to manage myself to not put too much into the book; but to say that there's a place for each of those things, if we can do them all.

...

But I think that if there's anything that I'm going to do is to let people know, again getting back to that concept of ontological humility that: consistently, in all of my research, in everything that I've seen, all of these people went to work each day trying to make a better product and trying to make a better world, and fought what they believed was a good fight. And their decisions were rational, even if it didn't appear that they were rational to the rest of the world.

And so, to be able to pull back that curtain a little bit and to say: "here's how that decision came to pass," and why things worked the way that they did.

### The Humanitarian Toolbox

**Jamie**:
I recently had a [conversation with Steve Gordon](https://dotnetcore.show/episode-13-steve-gordon-continual-learning/), and I was talking to him a little about the Humanitarian Toolbox. Perhaps we could discuss the Humanitarian Toolbox a little bit, if that's alright?

**Richard**:
For sure.

The origins of the [Humanitarian Toolbox](http://www.htbox.org/) come from the .NET Rocks Visual Studio 2012 Road Trip.

So going back as far as 2005, Carl and I were able to rent an RV and drive across the United States, making stops and talking about the new version of Visual Studio. And the biggest one of these turned out to be the 2012 one. We knew that it was going to ship in the fall of 2012.

And so during the summer time, I think it was in July - and I still have my OneNote notes from this meeting - I'm talking to some Microsoft folks who were gonna provide sponsorship money so that we can rent the RV and pay for things. And we put logos on the side of the RV so it looked like a NASCAR driving from city to city, and in the end the 2012 road trip was 34 stops in 13 weeks - it was a beast.

But it was the Microsoft folks who said:

> There should be a charitable element to the tour. Can you come up with a way to include some sort of charitable element to the tour?

And I think that if I'd have had any brains, I'd have taken the easy way out and simply said, "how about match us dollar for dollar for kids who code?" Something like that would have been the easiest solution. But in stead I went on a bit of a rant about how frustrated I was for how hard it was for software developers to donate their time, as coders, to a charity.

Because code is never free. If you write some code for someone, they have to live with that code. Code is free like a puppy is free: you have to clean up after it, you have to maintain it. Software lives, it needs work. I think most software developers understand this, and when given the opportunity to support a charity with some code, they also recognise that it's a permanent commitment, and so they resist doing that.

So with those things in mind, and knowing that developers do want to donate their time to charity, want to do good with their software. Often the things we write at work is not our passion project. You can only do so many forms over data where you're like, "done it". But if it's paying your bills then you keep doing it; you're good at it, you are valued at it, but it's not your passion project. Which is why we often end up in open source, writing things that mean more to us. But could you do that as a charity project as well?

And the challenge of course is that software is more than the code that is written. It is the project management parts, it is the planning of features and the writing of user stories, and hopefully the organising of tasks. And then giving programmers a space to work, and how do you care for them?

And that was really the essence of Humanitarian Toolbox: what if we did all the other things, so that volunteer developers could sit in a place where they knew their code could do some good, and that it would be properly cared for so that they can put in their volunteer hours and then walk away with a clear conscience when they have to do the next things in life that matter for them.

It took us a few years to figure out how to do it right.

We chose disaster response because it was an equal opportunity problem. Disasters happen everywhere in the world, and everyone needs help with them. They are technologically unsophisticated, so there are plenty of opportunities to introduce mobile, and cloud, and techniques that we know how to use to improve their ability to respond to these things.

And it was something that every developer could relate to. Whether it was a tornado, or a hurricane, or an earthquake, or a typhoon, pick your disaster and we can make a difference here with software. So that has been the mission.

...

The Already Project's - which is one of the Humanitarian Toolbox projects - initial implementation was focused on a Red Cross initiative for putting smoke detectors in homes that didn't already have them. And the early stats when they did it the manual way - where they set up a stand at a home improvement centre and take down names, and they would get enough names to get a qualified volunteer to install them - it would typically take a few months to get that whole thing together; and the day that person could volunteer their day would be a Saturday. They would send them out with eight smoke detectors with eight address to install them, and people weren't home or they'd forgotten about it and wouldn't let them in. Often they'd only get two or three of the smoke detectors installed.

But when we were running the first trials with the software, we were utilisting social media to run the campaign and collect names and addresses, we were shipping the smoke detectors directly to volunteers so they didn't have to go to a central location. We were using mobile apps so they already had the GPS stuff all sorted out. We tied in Twilio so that on their way to a location, they could call ahead automatically. And now we were getting 70-80% of the installs successfully.

so we used that volunteer's time more efficiently and, ultimately protected more homes. That was a real world consequence for what was not a terribly complicated piece of software... It's not rocket science, it's just the right piece of tech in the right place, but it's result is: I think we saved some lives.

I don't want anyone to have a house fire, but if you're going to have a house fire have a working smoke detector. And if we were responsible for getting that smoke detector in that house, well we saved some people that day.

### Wrapping Up

That was my interview with Richard Campbell. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and a collection of text snippets from the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/).

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [YouTube version of the episode](https://www.youtube.com/watch?v=lH8DlaOasGg)
- [Richard Campbell on twitter](https://twitter.com/richardcampbell)
- [.NET Rocks!](https://dotnetrocks.com/)
- Some of Richards live presentations on the history of .NET:
  - [The History of .NET by Richard Campbell of .NET Rocks!](https://www.youtube.com/watch?v=FFCn_z7dn_A) at SSW
  - [The History of .NET - Richard Campbell](https://vimeo.com/239969756)
- [The Tablet Show](http://www.thetabletshow.com/)
- [Run As Radio](http://runasradio.com/)
- [Humanitarian Toolbox](http://www.htbox.org/)
  - [Humanitarian Toolbox on Twitter](https://github.com/HTBox)

> Ontological humility is the acknowledgment that you do not have a special claim on reality or truth, that others have equally valid perspectives deserving respect and consideration. There are many ways to look at the world, and each way has its bright and its blind spots. Only from the perspective of ontological humility can you accommodate that diversity and integrate it into a more inclusive view.

This is a quote from [Conscious Business: How to Build Value Through Values](https://www.goodreads.com/book/show/1169674.Conscious_Business) which helps to describe ontological humility.
