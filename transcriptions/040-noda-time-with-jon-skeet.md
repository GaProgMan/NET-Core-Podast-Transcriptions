# The Third Annual C# Advent

This episode of the .NET Core Podcast is proud to be part of the [Third Annual C# Advent](https://crosscuttingconcerns.com/The-Third-Annual-csharp-Advent), which is an event happening throughout December 2019. Throughout December, 50 incredibly high quality posts of top tier content are shared via the hashtag [csadvent](https://twitter.com/hashtag/csadvent). To find out more, go to [Third Annual C# Advent](https://crosscuttingconcerns.com/The-Third-Annual-csharp-Advent) blog post on [crosscuttingconcerns.com](https://crosscuttingconcerns.com).

# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is episode 40: NodaTime with Jon Skeet. In this episode I interviewed Jon Skeet about [NodaTime](https://nodatime.org/), his work as convener for the ECMA standard for C#, a little on API design, and some of the trivia he has gathered about timezones due to his work on NodaTime. Some of you may know Jon from his almost legendary appearances on Stack Overflow, his work at NodaTime, his place on the .NET Foundation board, his work at Google where he works on the .NET libraries, or perhaps some of the humorous comments about him on a certain [Stack Exchange thread](https://meta.stackexchange.com/questions/9134/jon-skeet-facts).

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Jon's Introduction

**Jamie**

So the first thing I'd like to say, Jon, is thank you ever so much for taking some time out of your Monday evening.

**Jon**

My pleasure.

**Jamie**

It's always a great pleasure talking to anyone in the .Net space. And if you don't mind me saying, you know you're a bit of a celebrity and it's a great pleasure to be talking to you.

**Jon**

It's my pleasure. It's a very weird situation, being this sort of weird micro celebrity that if you're not within development, you have never heard of me at all. My wife is a Children's author. So far, far more people have heard of Holly. But within the developer community, obviously there is this a strange perception off me. I'm not nearly as smart as people seem to expect or want me to be. But, hey, it gets me on podcasts. It gets me to conferences and things, so I will take advantage of that while I can.

**Jamie**

I Don't blame you at all. So I was wondering if you could maybe introduce yourself to the listeners. I know that there's going to be very few people who have maybe heard of you and don't know who you are. But I was wondering, Could you maybe give us a couple of minutes?

**Jon**

Sure. So my name's Jon Skeet. I work for Google out of the London office, although I spend most of my time where I am right now, which is in my shed at the end of my garden, which is a lovely home office. And I currently work on the Google Cloud client libraries for .Net, which is fantastic. I've been doing that for three or four years now, which means I get to work for Google, which I love doing, and I've been a Google for 11 years, but I still get to work with .Net and C#, which are my passions in terms of technology. So it's best of both worlds on. I love being. I love working in developer relations, which is the area that I'm in because it means that my customers are other developers. So I care about the same things that my customers already care about, which is a great position to be in. So that's that's work work.

For fun, I write to the Date/Time Library. I dabble in all kinds of things. I am hobbyist in terms of the C# language design. So I'm proud to be the convener of the ECMA Standardization Committee, which a couple of years ago standardized C# 5. So now, given that C# 8 has now come out with a little bit behind. But basically working on tooling and things to take things forward for future versions that C#. I'm a committed Christian on Methodist local preacher. I have a family. I have a wife and three Children. Or rater I am married to a lovely woman... I hate that "I have a wife sounds so "ownership-y.  But I am the husband off a wonderful woman called Holly. Um, I thoroughly enjoying musicals and other shows. It feels like I must be missing something. Oh, and yeah, Stack overflow is probably where people have heard of me. So I'm a big contributor on stack overflow. An I have a book on C# called C# in Depth, which is currently in its fourth edition, and I should really get started on the fifth edition soon.

**Jamie**

Wow. That's a very long list of achievements. I have to say.

**Jon**

That's a list of stuff I do on and I would challenge each of your listeners if you're thinking, "Wow, how does Jon get it all done?" Because people ask me this. I don't do any more than other people. It's just it's all visible, so stop, stop what you're doing now. pause the playback on. Think of all the things that if you were to give a reasonably exhaustive list of stuff you do in your life, I'm sure all the listeners would have just as long a list. So this is not achievements, really. It's just stuff. I do.

**Jamie**

I like that. I like that. I think you I think you're right in that, um, you know that there's a reason why a lot of people in the technology space people like Scott Hanselman and yourself, create projects for people to use or create blog posts, go on podcasts, video streams go to talks and things. It's to spread that knowledge, isn't it? I guess, to give back to say I created this thing and here are the good parts. And here are the bad parts is where difficult and here is what was easy.

**Jon**

Yeah, and to basically have fun. So one thing I didn't mention just now is As of July, I started learning the drums. So I'm a terrible, terrible drummer. But I'm having loads of fun playing with my electronic drum kit on and writing code that can interact with this in terms of the configuration and things. So it's a matter of why do you think I do well is try to bring the whole of myself to everything I do. So I'll bring the coding side of myself to the drums, the drumming side of myself to music. when I'm listening to music, Now I hear the drum part much more than I do. But other times I bring my faith into**, hopefully, everything I do without sort of forcing it down anyone's throat. I do find that if you can make all of your life sort of pull in one direction, even if that's in many, many different ways thing you get a lot of benefits because things just rip off each other.

**Jamie**

I like that too. It wasn't that long ago I interviewed a man called Thomas Betts who is a fantastic engineer and he said along the lines of study something that is outside of your comfort zone, and you can then bring that knowledge that information that that experience into your regular practice of whatever it is that you do. And the example he gave for studying the liberal arts. So go and study something that has nothing to do with engineering. And when you come back to your engineering job, you will see that your understanding of how the way that you and your team do things, and they way you as a collective do things is like that because of a set of very specific reasons. And maybe you can bring the ideas and the experience you have from looking at something from a different perspective into that team and maybe change the way that everything works.

**Jon**

And that's one specific aspect of the liberal arts. I would encourage everyone, to, do some aspect, particularly if you're if you're relatively young on your choosing, your majors and minors at university, whatever it is, don't go so tech focused that you lose love of the written word or love of communication because I tend to view the difficult bits of software engineering tend to be communication. So how do you communicate requirements precisely but not too dogmatically? How do you communicate when you write code? You're communicating to the computer and to whoever's reading the code later on. When you're talking in meetings, or the writing emails to your colleagues, all of these things are communication on. That's actually a much bigger part of a reasonably senior software engineer's job. Then you're writing four loops, etc. the logic part. Don't get me wrong. It's still very, very important. But if you can communicate when you're having trouble on, when you do know things and you're trying to mental someone else, the communication is much more important than do I know a particular API.

**Jamie**

Absolutely. I agree with you 100% on that and I think I'll lean on your ah [blog posts on "how to ask a question"](https://codeblog.jonskeet.uk/2010/08/29/writing-the-perfect-question/) for proof of that.

**Jon**

Sounds good to me, 

**Jamie**

Excellent. I definitely agree with you on ah communication being a very important part of the work that I suppose anybody does. One of the things that I did at university was I studied a Japanese language for a bunch of reasons, but one of them was it is so different from English language that it gave me, I guess, that third person perspective on the language they use every day understanding. Oh, I get it. That's a verb. That's an adjective. And if I mix them up, somebody doesn't know what I'm talking about, you know "which Which is which?" you know.

**Jon**

And you get to see how the language that you can use to express yourself effects what you what you do express. It's to give a very concrete, technical example in Java and C#, reasonably similar languages. They both have virtual methods and non-virtual methods, but in Java for methods are virtual by default on in C#, they're non virtual by default. And people tend to go with the defaults so you can see how The language they're using, despite having the same capabilities in that particular example changes what you're expressing, what you bother to bring out. In other cases, there may be human languages that don't have appropriate ways off expressing a particular feeling or a particular situation. And what you can express just changes your way of looking at things. So the more different perspectives you can get absolutely the better.

**Jamie**

Excellent. I really like that. Anytime anyone wants to tell me, go and learn more about a language. I'm on board. I do love the learning how we communicate as a species, you know, the different have different groups of people with different words and phrases that'll mean different things. I read an article today about how the use of masculine words can actually home certain groups, and I completely I can see where that's going, where they're coming from. I totally understand that Which has now made me take us that back and go right. Okay. So how do I approach the word when I'm talking to a group of individuals. All right, OK, so I'll use this word. Maybe in the future, I'll force myself to use a different word. Or maybe actually asked that group of individuals. Is it okay if I use this noun or this group phrase what's the best way to communicate with everyone so that we're all on board?

**Jon**

Yeah, because that could be very cultural as well. So I've certainly, in the US, been in rooms with 90% women. Where the woman presenting as the right guys, I thought, What what? Hang on. Isn't that gendered? That's like No. Well Maybe not in a situation where most of rumors women anyway. Whereas maybe in with some of the same people still in the US. And I think this is part of a US / UK difference. But if the room had bean only 10% women that maybe guys would have bean more gendered because it would have emphasized that disparity more. So yeah, It can be absolutely fascinating. I should say, by the way, that I am a complete hypocrite on this. In terms of I only know English I am terribly monolingual on, even in suffer engineering. I love the idea of being a polyglot programmer, but basically I know C# and Java, and it's been quite a long time since I've done a real Java. So if you look at any of the python or bash scripts that I've written in the last couple of years, they are primitive in the extreme. I get what I can. I copy based quite a bit. Yes, so do as I recommend, not necessarily as I do when it comes to language. But I do think that communication is worth spending effort in. I do put time and effort into it, just not in terms of learning a different language.

**Jamie**

That's fair enough. I do like the idea of being good enough to be dangerous in the language, because that's how I have to do. Somebody says to me, "Oh, can you create me a bash script that will do this" and I sit there and say Yes. I'm sitting in front of my Linux machine on I know what bash is but I guess that's what stack overflow is for, right?

**Jon**

I have copied so many bits of bash on fighting from stack overflow, absolutely on C# and Java, because there are things that you don't know how to do. It's usually not in terms of the language, but whatever API you're using, people sometimes act surprised when I say, Oh, I looked something up on stack overflow. Well, of course I did!. It's It's sort of like science. I can't remember when it was, but There was a period of history where it would be reasonable for a scientist to know kind of all of science that have been discovered and worked out, but that time is long, long since passed. So if you take the finest scientific minds on the planet. On and, they're still gonna be asking colleagues for all kinds of things because no one knows everything.

**Jamie**

Precisely. I'll be willing to bet that even people who work at Microsoft on the dot net APIs probably have to ask their colleagues about something or other.

**Jon**

Yeah, yeah. Probably not about their own pet (project), the bit of the API that they work on. But if you're working in globalization and you know everything about one particular calendar system and how the numbers are represented within that or whatever it is and you need to find someone who's got WCF experience well they're Galaxies apart.

**Jamie**

Precisely. I guess that leads us on to part of the topic. We're going to talk about it. Did you feel that segue?

### What Is NodaTime? - Part One, A Little Background

**Jamie**

You mentioned NodaTime earlier on on and, I've done a bit of investigation. Just thinking, without sounding confrontational. Why would I use NodaTime in place off, say, `System.DateTime`?

**Jon**

Right. So it's it's probably worth going into the history of this back when Stack overflow was relatively young. I can't remember the exact date, but I can find it cause I wrote a blogpost about it Shortly afterwards. There were stack overflow conferences around the world, and I spoke at a London one on and the talk was called "Humanity, epic Fail". This was the first time I had used "Tony the Pony", which is a little sock puppet that I used in some talks. Great fun. And the premise of the talk was that if you take the basic units of data that almost everything else is made up, off: numbers; text; and dates and times, that kind of represents a huge amount of the data we work with and humanity, whether it's people entirely outside computing or architects of how we represent dates and text and numbers and things, or your lowly engineer who's trying to work with this mess. We all mess it up, and we have made things worse and worse. And frankly, it's wonder that the software ever works at all**, sometimes so as part of that mostly lighthearted talk, but with a few hopefully grains of truth in there as part of that I was saying, You need to use the right tool for the job. So if you're in Java, then you should absolutely not use Java util date java util calendar because they are terrible. Instead, use [JodaTime](https://www.joda.org/joda-time/). That was before the `java.time` API. And, I said, And if you're using dot net well, you kind of scuppered there's no equivalent of Joda time. I went away from the conference and thought, "I sort of don't want to do this, but I feel having identified the problem, I really need to Address it".
 
So basically, date and time are far harder, far more complex than the `System.DateTime` and even `System.DateTimeOffset` types make them out to be. Partly because there's a sort of effort within a lot of software to spot patterns. "Well, this thing over here looks like that thing over there, so I will combine them in a common type", and in many cases, that's a good thing to do. But in other cases, it hides fairly important differences, and that's the case for datetime. So in .Net, you've got  datetime, datetime offset time span, time zone info, and that's kind of it. Whereas in NodaTime we say you know what? There are lots of different things. A date is different from a date in time, so currently it's the 14th of Octoebr 2019  That's a date on it in the Gregorian calendar system. On the local time, as I'm talking to you is 9 21 on the 14th October 2019 on the local time Part of that is just 9:21 p.m. And so we've already identified various different things. So in NodaTime just to list off the top of my head, some of the types that we have we have local date, local datetime, local time zone, datetime offset datetime, instant, duration, period, time zone, sorry  datetime zone on various providers, calendar systems, et cetera. And The point is, there's a lot to learn there. And that's a good thing, because you need to be aware off what the data you're working with might be on. Then work out what it is and make the right decision.

So some API designers take an approach of. "Don't make me think. Don't make the user think, make it all so obvious that you just do the right thing." And, that's great and I try to apply it within NodaTime. I tried to make it hard to do the wrong thing, and I'll give an example of that later. But sometimes you need to make the user think. I don't know if you've got a piece of data saying 9:22 p.m. 2019 14th October Well, is that 9:22 p.m. UTC? Is it 9 22 PM in some specified time zone? Is it 9:22 p.m. in some arbitrary time zone that we don't really need to record because it's not part of the data we're interested in at the moment? Do we have an offset? I'm not sure whether even mentioned offset date offset datetime or offset time. So there are all kinds of choices, and I think when when an API can't make the right choice automatically and reliably, then it should force the developer to make the choice. So there's a steep learning curve in NodaTime. You're suddenly faced with this barrage of types and you need to look at the information in your program and say, "Well, which of these umpteen different types am I meant to use." And hopefully that's where the documentation comes in and makes it a bit easier to understand. But  you are forced to think, and then hopefully once you made your choice, then the second half of my job is is make those choices really easy to express. So once you do know what you're trying to achieve in NodaTime, hopefully we make it really easy to achieve that on to not go wrong. I mentioned some mentioned earlier on that you try to avoid people doing the wrong thing. One thing I've seen several people do is call `DateTime.Ahead()`. So if you say you take now and you want to add five minutes to it, you could declare a variable:

{{< highlight csharp >}}
var datetimeNow = Datetime.Now;
{{< /highlight >}}

and then

{{< highlight csharp >}}
datetimeNow.AddMinutes(5);
{{< /highlight >}}

and you look at that code and that sounds okay, doesn't it? Well, until you know that datetime is a value type, and all the add methods return a new value. But if you just read the code, it sounds okay. The equivalent code in in NodaTime would be `localDatetimeNow =`, and then you'd probably users own clock. I won't go into the clock aspect, but it tries to encourage you to write testable code. So we get `localdatetime.now()` and then. If you write `now.` then intellisense will suggest, Well, there's no add method, but there is a `Plus` method, and if you do, I can't remember off hand whether there is a `PlusMinutes()` But assuming there is, if not, there are multiple other ways you could do it if you do `now.PlusMinutes(5)` and have that as a statement in its own right. It sounds kind of wrong because, `Plus`, is something you do to get a result. You wouldn't write `5+2` and just do nothing with it. You need to assign it back to something.

So we're trying to make wrong code look wrong on and, even if it's just a subtle as well "What method name do you give?" Don't make a method name that sounds like it modifies a value if actually it just returns a new value. 

So in general, NodaTime tries to force you to make the right decisions with date and time. It also has somewhat side benefits that are actually some of the reasons that people do like to use it. So the Windows TimeZone Database is quite different from the [IANA](https://www.iana.org/time-zones) or TZData (TimeZone) Database that kind of the rest of the world outside Windows uses. so the timezone I'm in, I would normally refer to as `Europe/London` and that's the time zone identifier and Linux Systems or UNIX systems all over the world will know what that is, and it can be really annoying if you can't get that from Windows because Windows only knows it is as British standard time or whatever it would say so NodaTime allows you to use the IANA timezone database.

We also allow you to use the data - e publish the data from the Timezone database in a NodaTime specific nicely compressed format. So when the timezone data is updated, which happens several times a year, we can publish a new file onto the website. We do publish a new NuGet package as well, So if you just keep your NuGet references up to date, you will get the right data. But equally you could. You could have something on a device where you can't change the code easily, but you can make network calls. So if you have your application polling, [nodatime.org/tzt/db.latest.txt](nodatime.org/tzt/db.latest.txt) that will give you the URL that you can use to fetch the latest data, and it's a fairly horrible way of polling it to just return the URL. I'm not using e tags or anything that would probably be nicer. This was a fairly quick and dirty but quite effective way of doing it. You can then download the latest data and Load that into NodaTime, even within the same process, and you've got a new datetimezone provider and, if your application does that automatically, you may well be getting the latest time zone data before 99% of the applications on the planet. Because normally most of the time operating systems have timezone data, and they're are only updated when the operating system updates on and many date and time APIs don't let you load from specific data sources. So those were just sort of almost tangential benefits. And I mentioned using an `IClock` for testability. So don't use the system time. Inject the idea of a service that provides the system time. inject that as you would any other dependency. And then it's really easy to fake out and say, Well, I wonder what would happen if my code is running at the time when there's a time zone transition at the end of autumn or whatever it is, you can really easily test that, whereas if you've got a hard coded `system.datetime.UTC.now()` or just `datetime.now()`  it's much harder to to test that.

So these were somewhat tangential benefits, but it was mostly around, allowing you to express the data that your application uses in a really, really clear way, so that if your code only has a date and  only wants a date, then don't let me find the seconds and the minutes and the hours because they're irrelevant. They're completely meaningless. Likewise, if I only want the time of day while don't make me express that as a time span, which is sort of a duration of time, and it's just a bit wrong. So it's mostly about expression, which so it comes back to the communication idea earlier on. I am very, very keen on clear communication and in this particular case, it's clear communication off what exact date and time concept you're trying to represent.

Sorry that was a very long answer.

**Jamie**

No, I like it. It's a very comprehensive answer is how we'll put it.

### What Is NodaTime? - Part Two, How Did You Get Into Working With Time?

**Jamie**

I do like that, like you say, it's making the API communicate to the consumer, "Hey, this this may not do what you think it's going to do, and it's worded specifically so that it makes you as the consumer think about what you're doing."

I like that.

**Jon**

Right and we avoid... Another example of where we force you to make a choice is you can take a local datetime. So it's now 9:30 p.m. and, as I mentioned, that's in the Europe/London time zone. So we're currently one hour ahead of UTC, and you may want to convert from a zoned datetime, which is a local date and time in a particular time zone. Sorry from a local datetime, which is a local date and time without a particular time. Then say, "right. Well, when did that occur? When did that local datetime happen on the timeline as an instant?"  Most APIs that I've seen will just let you convert. And if you're lucky, they'll document what happens if the local date and time that you're converting is either skipped or ambiguous, and to go into what that means: at the in spring, we in the UK skip forward from one o'clock in the morning to two o'clock in the morning. So on that day, 1:30 in the morning doesn't exist. Where is later in, its in November? It's the kind of thing I really should know off the top of my head, but I don't know when we fall back we go. It goes 1:58, 1:59, 1 o'clock. So we skip back from 2 o'clock back to one o'clock, which means 1:30 in the morning happens twice.

So if you've got 1:30 in the morning on that date and you say, Well, what instant does that represent like Well, I don't know, it could be one of two things, or in spring, well, that didn't happen at all.

So we force you to decide. Well, do you want to sort of do it in a lenient way? So if there are two choices oh, just take the later one. If there are no choices at all, then you take, uh, that point on our later or whatever it is, I can't remember the rules off what the lenient timezone resolver does. But it's all clearly and very precisely documented. Or you can be strict and say, Well, if it if it doesn't map to exactly one thing, just go bang or you can express the whole thing. In terms of this, datetime resolver that knows how to for the vast majority of things where there's only one thing it doesn't need to consult any custom code. But you can say, Well, if it's ambiguous, then I will do this. If it's skipped, then I will do that, and you can provide your own delegates to do whatever you want. So maybe if it's if it's skipped, you go onto the whole next day or whatever it is. But you can't there's no just default. You have to choose which of those things you're going to do, because otherwise you're making code that will run fine, except for two hours per year. Now, what are the chances of you picking up on those two hours per year in testing? Almost none. What are the chances of your application being used during those two hours per year? Well, that entirely depends on the on the application. If it's some accounting software, then maybe you're fine. In other cases, you definitely wouldn't be. And so you may find that you've got a bug that you weren't aware of for sort of 10 years on. Then something terrible happens on you have no idea why it's wrong, and it's a choice that you weren't asked to make. And you should be.

**Jamie**

I like that. It reminds me the description there of you know this one in 10 year bug reminds me off their was. I believe it was a bug with openoffice where on specific, I think it's under a very specific set of circumstances, on a Tuesday afternoon at 3 p.m. No one could print anything because of something to do with datetimes.

**Jon**

Right. Uh, I remember one of my first date and time bugs. I don't know whether it was in code that I was writing or something else, but there was the program crash every Wednesday, and it turns out it's because the name "Wednesday" is longer than all of the other days of the week, and so there was a buffer overrun. Yeah, you could get weird things, so that States in time and localization at same time.

**Jamie**

 Yeah, So I guess then to be able to create NodaTime, you have to go and learn a lot about time zones and dates and things like this.

**Jon**

So I started off... It ended up a little bit like the broom that you say. Yes, I'm using the same broom that I've been using for 10 years. I've replaced the handle five times and replaced the head six times, But it's still the same broom.

And I started with the Joda time API . And I thought, right. "How far will I get Just porting Joda Time?" Okay, we'll start with the engine, keep the engine the same. When I say engine. I mean, the bits of code that do the complex calendrical computations. The simplest example being "is this year a leap year?", but they're they are really complex things, particularly for some of the different calendars.

So I started thinking, Okay, well, I'll port all of that code and make it internal, because a lot of joda Time - almost everything was a public type. And I thought, I really don't want people messing with this too much, So I made lots of things internal and sort of redesigned the public API partly because in java you don't have structs, whereas we obviously do in C# and they're a good fit for many date and time things and that changed the the class hierarchy, and Joda Time is very, very deep. So by the time you get to local date, that's about eight levels down, possibly exaggerating a little. So I had to redesign a bit on. There are a few things that it handled nulls as a sort of a "well, "I'll just use system default times then," But now I want to be a bit stricter than this. So I redesigned the public API while keeping the engine internal. Then oh, I think in something like the 1.2 time frame, I completely changed out the engine. I thought, Well, now I know what I'm doing. A bit like I did a lot of the initial work without understanding the code at all. I really didn't know much about* date and time. I was just porting in a fairly wrote fashion. But by the end of this, I knew kind of what I was doing on, so I thought, "Well, I wonder whether I can make things significantly simpler and more efficient if I rewrite the engine." And so I did that and it worked really well. And then I rewrote the internal data structures. So not just the computations, but how you store things. I used to store almost everything as time from the UNIX Epoch. So originally that was Windows ticks since the UNIX Epoch I'm and then later on it, it became nanoseconds. But I was storing local datetime as ticks since this sort of local Epoch it was a bit weird, but it was still okay. I will store three year 2019 as kind of 49 years as a duration that made a lot of the competition's really, really painful, because what do you typically ask? Dates and times you ask Well, what's the year? What's the month? What's the day? What's the hour? What's the minutes and what's the second?

If you're formatting a date in time, you've got to ask for those six thins and maybe the fraction of a second on and for each of those things, certainly the year, month and date I was finding. I was doing a load of different computation, so I thought, well, What about if we just stored the year as a few bits in an integer, and the month is a few bits in an integer, and the day as a few bits here. Let's assume that there won't be more than 31 days in a month, or at least not more than 32 So store a six bit integer on and we're away. I might mean five bit. Yes, I do mean five bit. So we store the day as five bits we store the month also has five bits because there are some counter systems with more than 16 months. Um, on and. The year is, however many bits we need for that. That means that when you convert from, say, an instant in time, which doesn't have a calendar system associated with it into a local datetime or its own datetime or whatever it is, then there's a one time. Okay, now we've got to work out the year, month and day, But after that, it's blazingly fast just getting it. The what's the day? I can do that really, really quickly. What's the month? I could do that really quickly, so that was a really interesting bit of redesign because I've always assumed that it was just appropriate to use this still information dense but annoying format of just ticks since Unix Epoch. And I was really pleased that I was able to do that without changing the public API at all. So that was, I think, between 1.3 and 1.4, or possibly 1.2 on 1.3. And it was a great example for me. If people ask about encapsulation on information hiding, that's a really good example for me. And do you want public fields? No, absolutely not. If the field of being public, I could not have made that change so, that was a sort of secondary engine that I did, and by that time I didn't know pretty much what I was doing. In terms of dates and times, there are still things that surprised me. So it was actually fairly shortly before two point was released that I started learning about the Wondrous calendar, which has 19 months. So that's where we needed to adjust the implementation of it so that we could handle a month number up to 19. But other than a few bits like that. There haven't mean too many little tweaks.

### The "Silver Bullet" That Is UTC

**Jamie**

I think it goes back, I guess, to looking outside of our comfort zones because, like you say, you know, most of the time, um, we creating, you know, our business line enterprise line apps are for want of a better phrase forms over data. And you, you know, you're assuming that the data is correct in whatever form that you're receiving it. But you know what iff your company does business with another company who are in a completely different time zone using a different calendar?

**Jon**

Right. Yeah. Yeah, And you need to think, What do you want to store and in particular, there's this sort of silver bullet that people say of we'll just store UTC in the database and everything will be fine. Well, but sometimes good advice. If you're storing past events, that's usually not always, but that's usually fine. You might want to stall the time zone in which the the event was recorded as well, in case you need to know that. But that's usually fine. But if you're storing future events, then recording UTC may be entirely the wrong thing to do on. I've got a blog post that goes into much more detail, so I assume we can link that in the show notes. But knowing that time zone rules do change over time. So the European Union, we think, is going to stop observing daylight saving time sometime in the next few years. So if you're trying to plan an event that's in three years time and you say I know I will convert your 9 a.m. in Paris into the UTC instant that it will be at nine o'clock in Paris, and then you turn up at that UTC instant in three years time. You may well find that it's 10 o'clock or eight o'clock because things aren't quite as you thought they would be. And you you made a guess based on the current time zone. Rules on those may not be in place in three years time, so it's really about thinking quite deeply about what data are you really, really, really trying to express? What's the user told you? If you are throwing away any of the information that the user told you, are you sure you want to throw it away? And you need to be aware off when you are throwing things away versus when you want? So many people were assumed that converting to UTC is not throwing away any information. But if what's really important is the time that the user entered, then just be aware that you're using time zone rules that can change over time.

**Jamie**

Yes, yes, exactly. Remember, watching a [wonderful video by Tom Scott, where he talks about the difficulty of time zones and calendars](https://www.youtube.com/watch?v=-5wpm-gesOY). I've gotta think I've got a link in my notes for the conversation, so we'll put that in the show notes.

**Jon**

It's a great video. I'll confess my bit of geekiness in that I was watching, and I think he says, "and then you've got time zones like Nepal. That's five hours and 15 minutes from UTC." I was screaming at video. Saying "no. It's 5 hours 45 minutes". Things, time zone trivia. I happen to know that. But no, it's it's a great video. Yeah, that one mistake aside.

**Jamie**

It's it really is. It really is. And then I remember reading about is it Fiji or one of those islands that are on the international date line? And now the mayor or whatever decided that today we're on this side of the international date line. Whereas tomorrow when you wake up, it is two days hence because we've moved over the international timeline.

**Jon**

Yes, absolutely Yes, yes. So in NodaTime we do account for that that the we have an idea of a local date, which is just a date on, you can say right, give me that in a particular time zone at the start of the day, we don't say at midnight because it might not be midnight like Brazil changes when it does the spring forward. It would go 11:58, 11:59, 1 o'clock in the morning, so there's no midnight in that day, so we have localdate.atStartOfDay and you pass in a timezone. But for Samoa, if you pass in the day that was skipped, it will say no that date didn't exist. There's no start of that day at all. It was skipped entirely.

**Jamie**

That's it. Sorry, yeah Samoa. And then I I know that there's a time period in Japan's history Post World War Two where we shifted forward, I think a few months or something like that.

**Jon**

So I don't know about that. The bit I do know about Japan that confuse things is that I think it was three years around 1949. I could be wrong, very definitely over on this. But the officially the day before the fall back. So you know when you're going to put the clocks back, went on for 25 hours and you put your clocks back from 25 o'clock to midnight of the next day. And I think probably almost every date and time API in the world, including NodaTime models this as, "We'll just we'll change the date, and then at one o'clock in the morning, we'll go back to midnight." But that's no really quite right.

So I'm completely making up the date now. So say it was Third of July. So say the third of July is the 25 hour date. That means if you have a birthday if you were born at, say, half past 12 on the third half past 12 - so there's AM then PM and then I guess PM again - the third half a swell on July the third, then you were born on July the third. That should be your birthday, whereas most state in time APIs would say you were born on July the fourth. Now that could affect when you get your driving license It could affect whether you get a pension. It could affect so many legal things. It's quite scary to think that there's there will be this population in Japan that was born during that one hour, which I guess, in many legal documents etcetera may have the wrong date of birth. I know, but times in, well, not just time zones, but calendar systems and everything. Date in time is just so full of trivia. It's wonderful. I've got a page on the NodaTime documentation that is just full of trivia on There's so much that I don't even go into at all: so I don't handle leap seconds at all - I just, NodaTime pretends that leap seconds do not exist - and that's problematic in various ways, but for line of business app, it's mostly fine. Every so often someone will call me up and say, "Well, what do you actually mean about this?" and I say, "Well, it gets kind of tricky." I don't really mean TAI, and I don't really mean UTC, I fudge it.

And it's It's mostly fine. I don't think I've had anyone seriously say, "I can't use NodaTime because it doesn't handle leap seconds properly." But leap seconds are just a real pain, even in terms of how do you think about them? Because we sort of assumed that you need some, uh, some rock to base everything else on. And when you try to do that with leap seconds, my brain just doesn't cope with it. Maybe you'd be fine with it. I'm sure many of the listeners would be absolutely fine and will be writing in and saying, "no leap seconds are dead easy, Jon."

In which case you're better developer than I am. Please come in and tell me what we should do in NodaTime without hurting developers who don't want to use leap seconds and don't need to know.

**Jamie**

Well I mean, [NodaTime is open source](https://github.com/nodatime/nodatime), isn't it? So maybe someone could submit a pull request.

**Jon**

It certainly is. Yeah.

**Jon**

Yeah, the tricky bit isn't giving people what they might need for leap seconds without forcing that complexity onto a bunch of people who don't need leap seconds. And the same could be true, we make calendar systems part of the API everywere, but we default to the Gregorian calendar. .Net default's more to the Gregorian calendar, so you can pass the datetime constructor a calendar. And then it says, "Okay, I will do the conversion for you," and there's no sign that it was ever constructed with that calendar. So you can pass something in with a particular year and then ask immediately for the year and it'll give you a different value because it's done the conversion to Gregorian for you originally. Whereas we thought, "Well, no, it's useful to be able to say this is a date in this calendar even though 90% of people, 90% of developers aren't going to need that," we wanted to make that reasonably feasible without being too distracting. My guess is that leap seconds: it would be very hard to make a leap seconds work without breaking a lot of code. And that's really what I want to avoid doing.

**Jamie**

I See?. So I guess if leap seconds is your requirement, maybe look at different timezone API.

**Jon**

Absolutely. Yes, yes. And you're likely to be writing quite specialised software at that point. So probably half the things in NodaTime wouldn't be useful to you anyway.

**Jamie**

Maybe someone needs to fork NodaTime and come up with science / physics(specific) NodaTime? I don't know.

**Jon**

Who knows? who knows?

### What about ECMA and C#?

**Jamie**

So I wonder if I can ask you a few questions about your role with ECMA, C#, and so on?

**Jon**

Sure.

**Jamie**

So with the Khmer Technical group for C#, I think you touched on it earlier on in your introduction, and you said that the ECMA group standardizes C#? Is this different to the work that goes on in, say the public GitHub repo for C#?

**Jon**

So the work that goes on in the public repo is more before standardization and before specification, it's sort of deciding the shape of the language. And certainly what has happened in the past - and we're aiming to streamline this - but what's happened in the past is that Microsoft have designed the language, implemented it, come out with a new version of Visual Studio or whatever, and shipped the specification as a Word document or whatever, and that's it. And then the ECMA group has made the same changes that say, between C# 2 and C# 3, made the same changes that were in the specification - we port those over to the standard. And while the standard and the specifications have, they are strongly similar. But there are some differences, and bringing the ECMA standard from C# 2 to C# 5 was a multiyear effort from many people. The ECMA working group is mostly Microsoft folks now, although some of those folks were not in Microsoft when they joined the ECMA group, but have now been hired by Microsoft - other people such as myself are not in Microsoft. And the idea is really to go through what has previously been done with a fine tooth comb and pick out, there are little mistakes and problems and bits that are ambiguous or whatever, and try to nail it down a bit further. Eventually, we were like more of a sort of open source of field two things where the standard is the one and only document. And, in an ideal world, any proposed features would be in the form of, "Well, here's a patch to the standard," and obviously with a lot of design work beforehand and community input, because the the process of writing standard appropriate language that has to be really, really precise and cover every example every possible nook and cranny; that's not how you want to originally come up with features. You want to get sort of the "well, what's the 90% case? And then we'll focus on the other bits slightly later, make sure they all fit in." But ideally, a language feature would be in terms of, "here's a patch to the standard," and then those will be collected, and then we have whatever it is C# 10, maybe that would be the draft standard, and then the EMCA team would could come behind and just say, "OK, we'll just do an extra level of code review on this, or spec review effectively, and check that we've got everything appropriately," and this could be much more of a single living document. Which we would like to go that way instead of having a separate specification that's from Microsoft and then the standard that's from EMCA, when these all slightly different versions off the same thing.

**Jamie**

I see. That would help to bring greater agility, I guess, to how we get from, "Here is Microsoft's version, the version that is shipped with Visual Studio, to here is the EMCA standard version." 

**Jon**

Yes. And many people, to be absolutely honest, many people don't need to care about that agility at all. But itt feels like it's the right thing to do for the ecosystem. And there there will be people who can't use a language unless it's standardized, so may be stuck on C# 5 until we standardize it to C# 6, 7, 8, 9, etc. So those people who care very greatly. Everyone else should sort of care that this work is going on behind the scenes because it can fix bugs, it can find bugs in the Roslyn compiler. We found some really interesting corner cases over the years. But yeah, it's good to have this kind of work being done, and done mostly in the open. We have teleconferences that are not recorded, not published where people can assert things that turn out to be wrong without feeling embarrassed to do so. But the results are still effectively public.

**Jamie**

Sure, that makes sense.

### Is It Worth Reading The C# Standard?

**Jamie**

One if the one of the books that I come back to, and it's it several times a year, is the version of C# in Depth that I have. I have had several versions of it over the years, and lend them out to a slightly more junior developers, and I never got them back. Which I suppose helps them but doesn't help you.

**Jon**

Oh, no. If you're replacing it with another copy for yourself and it's all helping me.

**Jamie**

But it genuinely is a book that I come back to several times a year. And every time I come back to it there is something new in there, because obviously there's only so much information that we could take in at once.

**Jon**
Absolutely.

**Jamie**

And also, I'm an auditory learner. So I would have to have someone read the spec to me, which is perhaps something we can come back to another time: when you read the spec.

**Jon**

Right.

**Jamie**

Do you, as a C# developer, as a .NET developer, as a developer of NodaTime, as an all round developer - and I believe this might be a leading question - is it worth developers reading the specifications document for the language that they are working in, or should they just rely on, "Okay, I'm going to go learn this language either by looking a PluralSite" or looking at, I mean any other training provider, or read some books and just trust that what has been said is correct and just work with that? Or is it worth maybe after reaching a certain point in your career, looking at the specifications going "Ah, yes, I get why that happens there."

**Jon**

Right. So it's definitely specifications are not designed for learning, that's the first thing to say. You don't generally learn a language by reading the spec because it's usually presented in a way that makes it feasible to find things as a reference, and make sure that things are exhaustive, so that if you're writing a compiler etc. you can do the right thing. But I think it is important that you know where to find the specification. And t's worth dipping into it. So next time you have some question about, "Well, what does what does this do in C#?" Then maybe, sure reach for C# in Depth, or Essential C#, or C# in a Nutshell - there are lots of good books available. But also make a conscious decision, "I will check that I know how to find that in the specification." And it's an acquired skill. It takes a while to get used to the spec terminology, which I tried to follow in C# in Depth to sort of make it easier to get into the spec, if you want to. But finding your way around it can be a bit daunting to start with. But if you just do it occasionally when your job doesn't depend on it - if you see what I mean - then one day you may find that you really, really need to get the answer to that now. And by "now#2 I mean sort of "in the next half hour," because sometimes it can easily take half an hour to find the answer to a particularly tricky question; particularly if there's overload resolution and generic type inference going on, and all kinds of things. If you've already looked at the spec and your kind of familiar with how it's structured, and how things tend to be explained, then you'll be in a much better position to have a look. So yeah, definitely. Whatever language you are looking at, check that there is a specification, and then yeah, dip into it when you can.

**Jamie**

Okay. I do remember the date when I found the C# spec loaded into my Visual Studio 2008, I think. And I was just like, "Oh, what's this? Oh, wow a whole Word document. These are a bunch of words that I don't understand."

**Jon**

Yeah. 

**Jamie**

It's worth having a look, if you will to, as it were, sort of level up a little bit. Dip in and dip out to see what things you can understand, I guess.

**Jon**

Yes, Absolutely.

**Jamie**

It gives readers a chance to go, "Oh, I wonder what this word means?." Wwhich one is it? It's not - what's the word? It's not idempotent, it's the, oh dear it's to do with parameter overloading.

**Jon**

Oh, invariance. Contravariance, covariance, and generic variance in general. Yes.

**Jamie**

That's the one. It takes you out of the unknown unknowns into, I guess, known unknowns: You don't know what it means, but you know that it exists.

**Jon**

Yes. And there are some bits of spec terminology that you never need really outside the spec. So some of definitions around generics are really for the sake of the spec itself. Not in terms of covariants, but some of the open constructed types, etc. It is all a bit obscure, but there's plenty that isn't quite as obscure, and it can really open your eyes to, aside for anything else, how beautifully designed the language is.

**Jamie**

Fantastic. Okay. I'll encourage listeners to go and have a look at the spec if they want and figure those kinds of things that I guess.

**Jon**

Yeah, absolutely

**Jamie**

And obviously, go get C# in Depth.

**Jon**

Thank you.

**Jamie**

Last couple of really short questions then. What's the best way for listeners to keep up with what's happening with you in terms of maybe the development work you're doing? Maybe with NodaTime that kind of thing? What's the best way to find out more about Jon?

**Jon**

So I'm on Twitter as [Jon Skeet](https://twitter.com/jonskeet) on Twitter. I have a pair of blogs. So my coding blog is [codeblog.jonskeet.uk](https://codeblog.jonskeet.uk). And I've got [blog.jonskeet.uk](blog.jonskeet.uk), which I usually used to write about feminism. And frankly, I haven't written for a little while and I need to, I think the last thing I did was a couple of tiramisu recipes. So not really feminism on that front. 

Yeah. Those are probably the best ways of keeping up with what's going on. For NodaTime, you can subscribe to the NodaTime mailing list. And given that most of my work is open source, f you go to [github.com/googlecloudplatform/google-cloud-dotnet](https://github.com/googlecloudplatform/google-cloud-dotnet) get up dot com slash google cloud platform slash bugle dash cloud dash dot net you can see me work in real time. Pretty much.

**Jamie**

Fantastic. I'll make sure to put links into the show notes so that for people who may be driving into work, they don't have to dive across their car together a notepad.

**Jon**

Yeah.

**Jamie**

Because we don't want people crashing their cars.

Well, that's essentially all of the questions that I have. Jon, thank you ever so much for being on the show.

**Jon**

My pleasure.

**Jamie**

We've gone a little bit over time, which I feel it's a little bit relevant. But thank you ever so much for sticking around Jon. And if it's okay with you, I'd like to ask in the future, when you have some more time, maybe we can come back on talk a little bit more about C# in a little bit 

**Jon**

Yes, definitely. Definitely.

**Jamie**

And about the sort of diversity and inclusivity. If there's any advice, you can give on that because that is a very I think I said to you before we started the interview, t is a very spiky and scary subject. And it's a very important subject. I think perhaps it shouldn't have to be a scary one. But like I was saying to you earlier on when I planning this out, I was worried about, "have I said something in my notes that I sent across to you, that is you know, would it be considered a bad subject to talk about?"

**Jon**

No no. We should absolutely talk about it. Yup.

**Jamie**

Definitely is a conversation that needs to happen, I think in all walks of life, you know.

**Jon**

Yeah.

**Jamie**

But we leave that perhaps for another time.

**Jon**

Indeed, indeed.

**Jamie**

Yes. But thank you ever so much, Jon. It's been an absolute pleasure talking to you.

**Jon**

Thank you. My pleasure.

### Wrapping Up

That was my interview with Jon Skeet of (Company Name). Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and a collection of text snippets from the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/).

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Third Annual C# Advent](https://crosscuttingconcerns.com/The-Third-Annual-csharp-Advent)
- [Jon Skeet on twitter](https://twitter.com/jonskeet)
- [C# in Depth](https://www.manning.com/books/c-sharp-in-depth-fourth-edition)
- [NodaTime](https://nodatime.org/)
- [Jon Skeet Facts](https://meta.stackexchange.com/questions/9134/jon-skeet-facts)
- [Writing the perfect question](https://codeblog.jonskeet.uk/2010/08/29/writing-the-perfect-question/)
- [JodaTime](https://www.joda.org/joda-time/)
- [IANA](https://www.iana.org/time-zones)
- [The Problem with Time & Timezones - Computerphile](https://www.youtube.com/watch?v=-5wpm-gesOY)
- [NodaTime on GitHub](https://github.com/nodatime/nodatime)
- [Jon's code blog](https://codeblog.jonskeet.uk)
- [Jon's non-code blog](blog.jonskeet.uk)
- [Google's .NET APIs](https://github.com/googlecloudplatform/google-cloud-dotnet)
