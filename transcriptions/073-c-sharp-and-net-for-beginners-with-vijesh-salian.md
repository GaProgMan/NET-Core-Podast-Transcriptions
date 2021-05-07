### Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor. In this episode I talked with Vijesh about some of our advice for beginner developers, and whether C# and .NET are right for those who are just starting out on their journey in development.

So let's sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

{{< paracentre "The following is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

#### Jamie

So first thing I'd like to say, Vijesh is thank you ever so much for spending your afternoon with me talking about what we're about to talk about. So a little bit of insider baseball, usually we have a topic and a bunch of ideas we want to talk about, but you know, it's an easygoing show, we can go off in a different direction. So at the moment, I've got an idea of what we're going to talk about, but we may end up talking about something else. I don't know. It's a Saturday afternoon, we're having some chill out time. You know, we're both sans children, it's brilliant. We're having just some time to chill. So thank you for spending that time with me.

#### Vijesh

Cool. Thank you for having me. It's a pleasure.

#### Jamie

You're very, very welcome. Very welcome.

So I was wondering - before we get into sort of the the topic that we're gonna tackle today - I was wondering, could you let the listeners know a little bit about yourself, give us a brief introduction, you know, the sort of technical background, the places you've worked at the projects that you're working on, if you can talk about them? that kind of thing.

#### Vijesh

Cool. My name is Vijesh Salian. And I'm a software engineer, primarily in the .NET ecosystem. And I started my career coding in Delphi, and then moved on to C#. And I like to mentor beginners and upcoming developers as well. So that's like, you know, I've learned a lot from my peers. And it feels like giving back to people who want to learn more as well.

And I worked in Bangalore, in India, and currently I'm working in Netherlands. And I've been here for about three years now. And I'm working for a healthcare company, which is called Vital Images. It's part of Cannon group. And, yeah, and I've been part of healthcare companies before as well. So I like the domain. And it gives a sense of purpose to what I'm doing.

#### Jamie

Sure. I can, there's a whole bunch of things you've mentioned that there, I can totally get behind.

I really like the idea of giving back to the community. That's, that's wonderful to me. You know, like you said, we're always learning from our peers, if it's reading a blog post is listening to a podcast, if it's just interacting with people and talking over the water cooler or whatever. "hey, I'm having a problem with this," "Have we tried this?" Or "I really can't figure this out," "hey, why don't we talk about this?" Or just going to a meetup and listening to someone give a talk. I absolutely love that idea of giving back. And, and I try to do that whenever I can. But I'm not much of a mentor. I don't think I'm that good at teaching people. But that remains to be seen, I suppose.

And then, yeah, the the talk about, you said there about giving the work that you do a sort of sense of meaning, which I think gets lost on a lot of us developers. Especially if, you know, a project I've just worked on was essentially a CRUD app - create, replace, update, delete stuff like that. It's a sort of create, read, update, delete. It's just an interface to a database where there's no context, there is just this company wants to store this data from a form into the database and pull that data out. It's it's not there's no real meaning to is meaningful to the to the client, but not to me. But I totally get the idea of searching for that meaning let's do something that helps people that helps society.

#### Vijesh

Yeah. Yeah. That's also very important to have that a sense of importance of what are you going to do? And yeah, and C# has provided me that I, like I said, I began coding in Delphi. And it is also a wonderful language to be in. But at that point in time, everybody was getting into C# .NET in Bangalore, and I started learning C#, and I remember picking up "Headfirst C#" at that point in time. And it was a good book to start. And I'm glad I did.

#### Jamie

Excellent, excellent. I have to admit, I've never touched Delphi - I've never worked with it. I have worked with C and some friends of mine told me it's quite similar; it's in that same language family - the C, C++, C#, Java - it has a similar syntax and things like that, but I've never never touched it before. So I can't comment on on Delphi, unfortunately.

#### Vijesh

Well, yeah, but I think C# and Delphi might have the same ancestry or from the same origins, if I'm not wrong, but it's also cool language. Yeah.

#### Jamie

Cool. Maybe this this winter I'll pick up.

So I'm just before I say that, because of what I call the "time cast pod machine wibbly wobbliness" we're recording this ahead of time. So I'm about to mention winter. And this is coming out in hopefully April if everything works out well. So maybe this coming winter or for the listener this past winter, I picked up Delphi and made something with it, I don't know. I'm always looking for new projects to do in other languages. I recently started. Well, this was ages ago, I should have recently I started making a game for the Sega Megadrive, the Sega Genesis, in low level C, because I was like, "it's been years since I've touched C. Let's see what I can do," right?. I don't want to just make a command line application. Let's make something fun. Little did I know that making games isn't that fun?

#### Vijesh

Yeah. The other side of games like playing is much more than making games. Yeah.

#### Jamie

Oh, absolutely. Absolutely. I would much rather than that. Well, no, that's not fair. I think using the slightly older technology, because it's so constrained. If you don't know about those constraints, and you in and you're used to using, say, C# and .NET, where it's like, I don't need to worry about memory management, I don't need to worry about sockets. Although you wouldn't really use a socket in a mega drafted. But you know, I don't need to worry about buffers and memory access and, and pointers and things like it's just taken care of, for me going from that to Oh, well, I've got a buffer overload, because I kept writing to the same pointer, and I've wiped out my memory, or I got some kind of stack allocation error. And I don't know what it means because the compiler is really bad.

#### Vijesh

Yeah, a game development surely fascinating. And I've been meaning to, you know, give it a shot with C# and unity. But seems like the time for us to aim for it has not come yet. It's not Yeah.

#### Jamie

Yeah, I totally understand that. I've wanted to get into Unity. But it's again, it's the it's the it's, it's, I'm not a very artistic person. So it's like, where do I get the 3d models? from? Where do I get the textures from the sound effects, all that kind of stuff. And then I end up spending hours looking around on on Google for free textures, or licence free textures that I can use. And I do that for three or four days rather than actually building something?

#### Vijesh

Yeah, that's major part of it, as well. Like, I think I think I'll mention this. First, when I started my career with the Delphi coding. I had his senior developer in the company who helped me, you know, begin my professional coding career, one of the first thing he taught me is how to Google. So looking for resources on the internet is, you know, is one of the skills that is very important. And I think most developers at this age in 2020, are pretty good at googling stuff. But in 2008, it was not that, you know, it was popular, yes. But it was not the go to thing right away. And he taught me a few operators in Google like this plus this or put in, put this search them in quotes, and then you get a better search results. Especially when I had to do something in C#, I had to put it in quotes, because it was the Google wasn't, you know, smart enough to recognise the the pound symbol there. And it is the search results to see. So I think that's a very, very important skill for any developer to start searching on the internet. That's, that's a very important skill to mention that. Sure.

#### Jamie

So I think it's a it's an important skill for anyone to learn how to use a search engine, not just Google, but let's use actually use it, let's use Google as as the, as the example. Everyone should know how to use a search engine to utilise it, you know, a friend of mine puts full, like, correct grammatically correct English sentences into Google. And I'm like, that's not how it works. You can do like that. But that's not how it works, you'll get the best results if you rearrange the words into like, the most important words in your sentence. Because obviously, you know, English is very, the the important chunk of the sentences at the end. So Google has to work its way through everything to get to the end. But But yeah, I do think that if folks spend a little time learning, they the search engine that they're using, they will make them make their lives much better. And I think you're absolutely right back in 2008, I think, I think StackOverflow had started, but it was very quiet. And so you're looking at forums, you're looking at official documentation. And, you know, the Microsoft official documentation back then wasn't the state that it's in now. It wasn't the best, but it was getting there. Whereas now it's completely open source and you know, you want it you see something that's wrong, you can go in and put in a pull request and hey, you've you've, you've contributed towards a Microsoft product. And if it's during October, and you want a free t shirt, do that four times you've got your Oktoberfest t shirt, but make sure it's good quality. You know, it's not just like a button. period in here or change the spacing here, you know, it's got to be a good quality commit.

#### Vijesh

Yet Microsoft talks us, you know, it's definitely a good starting point for anyone starting in .NET. And I've been 12 years doing C#, but I constantly go see Doc's dot microsoft.com, for any syntax or any new information that's available. And I remember in 2008, you're right, saying that in a Stack Overflow was not that popular as it is now. But there used to be expert exchange, which, for C# and Delphi also, there were some question and answers, but it was a paid one. So you get only limited views. That was a bit of a challenge. And Microsoft docs, there were no, there were classes and methods and metadata information about that assembly. But now it's so much so much better. Much more than a book also, perhaps in some cases,

#### Jamie

maybe so maybe Microsoft has released the Microsoft press C# docs edition. I think maybe not.

#### Vijesh

It'll be a large one and might not be able to accept the hours there. Absolutely.

#### Jamie

Well, this is it right? I started working in C# and .NET. Back in 2004. I think so we're talking the .NET two timeline, I think. And at that time, you got a or I received an official ISO download for Visual Studio came across two CDs, I think you could actually download the entirety of the MSDN. The documentation across I think it was two or three DVDs. And you download that burn it to disk and then instal it onto your computer. And now obviously, you had the offline documentation, right. But that was at that time, I was like, oh, my goodness, what am I getting into this for DVDs of information? This is a huge amount of information. But you know, the, I guess the the key point, we'll come on to in a minute, I suppose. I suppose we're already there now is don't try and learn it all at once, I guess, you know, just about enough to get you past the next step. But that's my that's my advice. But there you go.

#### Vijesh

Yeah, you're absolutely right there. And I'm falling into that trap many times, like, if I'm learning something, I will just want to learn everything that involves that matter. And that is perhaps not a good idea. And and, you know, also lately in the software industry, we do a lot of agile work in a scrum and agile. And it has got many principles that I can apply to not just software development, but also learning and other stuff as well. And learn a bit of what you can and then improve on it. And I think that's a, that's a very nice way to go so that it keeps you motivated. And you just don't burn out in one day. You learn everything. And the next day, you don't have enough energy to continue learning this stuff. So you're absolutely right.

#### Jamie

Yeah, absolutely. And I like the idea of continual feedback. You know, if you are that, let's just talk about learning for a moment, right? So I did actually used to be a teacher, I graduated, I graduated from uni with a computer science degree, and then decided I wanted to become a teacher trained to be a teacher, and left that because of the politics involved with the particular school that I was working at and went back to computer science, right. But if you see yourself as the client, and you're you're wanting to expand your knowledge, you have a short turnaround time, maybe not two weeks, maybe that's a little too much. Maybe every few hours, right? If you're trying to study something, you start learning it, you make notes on the important bits, like you say, just learn the important bits. At the end of that hour. Have a retrospective and look at what worked, what didn't work. Which bits do I remember, which bits Do I need to cover again? I go back and cover those bits again. It may like you said it makes perfect. That's

#### Vijesh

absolutely yeah. And, you know, doing makes much more, you know, help to you than just reading. And, and that's what I like about developers now. And I also came from a background of, you know, computer science and there was a lot of reading of books and stuff, but actually doing stuff. And it makes more makes more sense now than ever that you know, you don't need a degree to learn coding. Just how to start, open up your editor, start typing, find errors, and search, fix it. And that's how we had to learn and that's, that's absolutely a very nice way to learn, I think

#### Jamie

absolutely the majority of the tools that you need to start doing Any kind of coding is they are built into your computer, you'd be I'd be very hard pressed to find someone who has just bought a laptop or just bought a computer and it doesn't have a web browser. It's got a web browser, you got a JavaScript execution engine right there. You know, it may not be the best, it may be the best, I don't know. But you've got the tools right there. And all operating systems have text editors, like you said, You open the text editor, you start typing, and if it goes wrong, you start searching around for the answer. There's, it's there are some sometimes there are licences for tools. But the majority of the compilers and the editors are free. So, you know, and and the knowledge is free, you just have to look for it. And if someone is that, like one of the things I always say to people, you want to learn computer programming, find someone to teach you don't you can go to university and get a computer science degree. But that's going to be like you said, mostly theoretical, right? elearning? Why does binary search work that way? Why does Why do computers work the way that they do? What what how do we go from code, which is written in a text file to an executable, and none of that will help solve the problem of a customer wants it to look like this? Yeah,

#### Vijesh

absolutely. And a lot of computer science stuff is only in niche companies, I would say, and I'm doing more of programming and coding and not actually computer science. So to make a career and, you know, as a programmer, it's more and more The reason that computer science degree is not a mandatory thing. And I remember this being one of the requirements for some of the jobs. And I think now companies are becoming more and more relaxed in that way, saying that, if you know this language, and you can work with it, that's that's fine enough.

#### Jamie

Absolutely. I mean, you know, I hate to pick on JavaScript, I'm not necessarily picking on it. But I feel like we'll we'll talk about C# and .NET in a moment, I guess. But I feel like JavaScript, because of that incredibly low barrier to entry of the tools are already on your computer. You just need to figure out where they are and how to access them. That makes it one of these languages that's very trivial to get started in not easy to get started in, but very trivial, your must, you falling over yourself not to get started. And so there's almost no excuse not to, you know, and I know, a whole bunch of people who never went out, either never went to university or went to university for some other field of study. And then they've come out the other end, worked in an industry for 510 15 years and then gone, you know what I want to do programming. I know one person who is a retired doctor, like a GP, right. And he used to teach medicine as well. And he's completely resigned from all of that. And he's gone. You know what I want to learn .NET. And so we're working together to help him learn a little bit more about .NET and C# and F sharp. And what's the difference? And why would you use one rather than the other? Or should you use one over the other? You know, that kind of stuff? And it's a brilliant journey to go on? Because he doesn't have to go to university, why do you Why would you need to go to university to learn about C#, right? It's the documentation. There's things like this show this people on Twitch all the time, you know, you don't have to, you don't have to?

#### Vijesh

Absolutely. It's like, you know, if you can count and do simple arithmetic, you can code. And you don't have to need an official certificate to say that you can do this or not. That's absolutely,

#### Jamie

absolutely, absolutely. So I guess that, that brings us on to so we've been talking a lot so far about that, you know, we've we've said that you don't need a computer science degree to get started in the field that we work in. And I think that is, by and large, absolutely correct. If if all you're doing is and I don't want to, I don't want to reduce what anyone does as a job like, okay, let's say you go to university for three years do computer science, right? You go through the there's this meme, right, this joke of you go through the interview process really gruelling, and it's a whiteboard and some markers. And it's like implement bubblesort implement this sorting algorithm. You have these constraints now figure out how to reverse the string without using any library components. And then the first thing I say to them is why am I not allowed to use string dot reverse? But that gets the job done in like four keystrokes, right? And then they say, Oh, well, we're using .NET. But you're not allowed to use .NET. And then I say, Well, why are we using .NET? Right? So we put that to one side, right? So you got through this gruelling interview processes, multiple stages to the interview process, you got to talk about memory usage. You've got to talk about, you know, data usage or like hundreds of different things to talk about. And you're talking about low level SQL and all sorts of stuff. And then you get to the first task is, this button is blue, it needs to be read. And it needs to be four pixels to the left. You don't need a computer science degree to do that, you know?

#### Vijesh

Anyone? If you had it, it would be still difficult because of CSS and a lot more things to it.

#### Jamie

Absolutely. Absolutely would be just as difficult for someone without a computer science degree to make the button blue and shifted four pixels to the left, then it would someone with a degree?

#### Vijesh

Absolutely. Yeah. If, like in computer science, we might have read about trees, or red black trees and everything. And if I have to do something very similar, I still have to go look it up. Because I've forgotten all that stuff. And anybody who without a degree can also look it up and acquire that knowledge straight away.

#### Jamie

Absolutely, I guess the immediate difference would be that your I would know what to search for, like the actual terms. Whereas perhaps someone who hasn't had that experience of talking about binary trees or different types of search algorithms, they may not know the exact words to search, but then you can ask someone and they go, Yeah, what you want is a binary tree, or you want to search for the the a star algorithm to search for that, find a version of it and see sharp return it get your get your head around it, and then implement it. And that would you normally, with certain juniors I've worked with turns into find it copy, paste don't.

#### Vijesh

Yeah, as long as you have a pretty solid test suite, I think it still works fine. Although I would recommend to, you know, just understand the bit of code, but your copy, that's absolutely the best way to go.

#### Jamie

That's it. That's it. That's what I always tell juniors I'm like, okay, you just copy pasted it. Close the browser. Now tell me what he's doing.

#### Vijesh

Yeah, totally. I've done it loads of times when I was a beginner. And I got told the same things by my senior peer who said, Okay, what does it do? I said, I don't know. We'll test it out and see. But that's not always the best strategy.

#### Jamie

No, that's true. But I guess, being able to read some code that already exists, and understanding what is doing, that's 90% of the job that we do, right? Because the code that we are working with, or the majority of the code that we're working with already exists. And it's either fix this thing, or add this thing to it or make this thing better. And obviously, being able to understand the code is maybe the most important step. You know, I tell people all the time, yes, I'm a developer. But I spend about 70% of my time debugging I don't, I very rarely write new code. Once you've gotten past the first maybe three or four iterations of a project. You're not writing new code anymore, you're debugging or at least that's my experience. Maybe I'm a terrible developer, I don't know.

#### Vijesh

But that's a very, very good point that you bring up. And, and I absolutely agree with you. And me, being a C# developer, I've done more code reading than code writing, and more of debugging others code. And that's also very important. And also, along the years, I developed empathy. And there was a time where I used to call, hey, who did this this really bad code? And and now I don't feel the need to say that. And because whoever has written that point, at that point in time, he felt that was the best code. And if not, he might have added a comment a bit, hey, this might not be the best part of the code. And and after these many years, I think I do have some empathy towards developers who have written that. And that's also very important during code reviews, and everything you're seeing so much of other score than your code. And and reading of the code is, is definitely a very important skill, which is which setting every beginner should start at it?

#### Jamie

Sure, I think you've hit on a really important point there about having empathy for other developers, because I think you almost exactly said what I'm about to say, which is you don't know the pressure that that developer was under in order to get this code checked in. Right? It could be that they've chosen a substandard algorithm or had to implement their own version of CFR reach or an iterator or something where they've had to integrate it they'd had to create their own because the version that they were using works for now. 99% of the cases, but then it is 1%, which might be quite often it breaks. And so they've had to work around that. And yeah, I totally agree that empathy for your fellow developers is something that we should all have. I don't know about you, but I definitely have a case where I had gone. Who wrote this, this is dreadful. I've done a git blame. And it's either been me or the person I've sat with. And I've got, oh, no, I don't care if it's me. But I've just, you know, I just said that your code is dreadful. That's no good.

#### Vijesh

Yeah. And we all go through that. And one of the, you know, past that you become a good developer is you start from being a bad developer. It's not a good term to say, for a beginner. But that's, that's what that's what happens. You You don't write perfect code when you start and and that's fine. And that's absolutely fine.

#### Jamie

Yep, there's this. What is it, there's this idea of a thing called ontological humility. And that is the ability to take a step back from a situation and say, the way that I'm observing it is limited. I'm looking at it through, say, like a cone. And I'm not seeing the whole world. So what I'm seeing doesn't, doesn't necessarily reflect the actual situation. I may be looking at this four line block of code, right? And I might be thinking, well, that's dreadful for all bunch of reasons. But I looking at that four line block of code, I can't see what's coming in, or what's going out of it, I can just see the full line block of code and being able to sort of look at that and go, Okay, I'll take it for what it is, but maybe I should investigate a little bit more around it, and ask the questions, less of an accusatory question, and just a hate. Just just explain this to me, because I don't know what else is going on. But just explain what's going on, you know, asking that. Why is it done this way, but not in a? A accusatory way is really difficult to do? I think,

#### Vijesh

yeah. But yeah, I think in code reviews, I've found in my experience that what questions are worth much better than why questions? If I ask a Why did you do this? It seems it seems a little bit accusatory, it depends on who takes the question as well. But if I say, oh, what does this code accomplish? It's, it's already a bit softer there. And I tried to come up with what and how questions during code reviews and rather than why questions, and that has been a bit of learning for me, and I think everybody should do code reviews. And it's definitely helpful for pair programming and, and building up the team. That's very important.

#### Jamie

Absolutely, absolutely. I tried to think of, what were the constraints while you're building this? Or how have you worked around the constraints, you know, then it's more, it's less a case of what are you doing more? What is this thing that you're working with? But like us? I don't know. I may be a terrible developer. You never know. Right?

#### Vijesh

Yeah, we are made of both things, either. It depends on the time and at some point in time, we could be okay. Today is not the best day the codes going out. And there was a time pressure, but some other days. We are we are very good at it. It feels good. So there's a bit of that too.

#### Jamie

Absolutely. Okay, so we've talked about a lot of advice for beginners and how we can get to a point where, how do we go from where we are to, to, to where we want to be right, the advice that we would give to junior developers without really actually saying what is our advice to junior developers. But when we were first talking about this, recording this episode, we were talking about how C# and .NET are actually quite good for beginners. And, you know, as someone who started, like, I actually started my, the first code that I ever wrote was in basic, but the old school basic, non Visual Basic. And then after that, I started writing in assembler. So maybe I'm not the best person to talk about, where should a beginner start, you know, because I went in hard. But, I mean, how do you feel about that about C# and .NET being good for sort of beginner developers?

#### Vijesh

I think C# is very good language for beginners, especially now, that you know, if if you don't want to spend any money and you still want to learn programming language, C# is definitely one of the top languages out there. And there's so much documentation happening. There's so much content on blogs, there's so much content on video, no matter what you're learning. And techniques are learning in a favourite learning technique. It's there, the content content is out there and I really like you know, not the experts and doing the trainings, but also people who are not the experts, not from Microsoft or not from any big companies, when they write blogs, and when they create videos, they're touching upon certain aspects of the languages that, you know, the experts might have not even thought about it. And that will definitely help few other people who think in that way. And, and as a community, I think we should, you know, let beginners also share their learning experiences. And, and there's so much content out there for C#, I think any beginner would be definitely happy to do it. And also on the other side of the things is what you get out of C# and .NET is the platform and the ecosystem is so huge. You think about platform, web, mobile, and IoT. With one language and one platform, you can do multiple things. And if I was picking up language, and I will be biassed towards .NET, of course, because I'm there now, but it will be definitely one of the things I would consider.

#### Jamie

Sure, yeah, you talked a couple of things. I want to pick up on that. Because there's some really good points that I know, from my own experience. So I don't know about what other people have experienced. But I feel like the .NET community is quite open to beginners. Every every community has its its bad apples, it's people who are like, Oh, well, you shouldn't be doing it this way. Don't Don't do it that way. Because you're being silly, because you're a noob you're gonna avoid those people. And they happen in every community, not just programming. They happen in health and fitness. They happen in science, they happen everywhere. If you can find a group of people to work with who maybe they are Twitch streamers, maybe there are bloggers, maybe they don't maybe they do a podcast, I don't know if you can find these content creators and these mentors who don't have that attitude. And I feel like the .NET community is is really open to beginners. I do know that. There was someone who was on the show very early on Jeff Fritz, and he does C#. I think it used to be what was it called C# and friends is what it used to be called. But he does like almost daily twitch stream where he's always building something. Right? And if you ask a question doesn't matter if it's super high, like, let's talk about async enumerable? Or if it's, hey, I've literally just started, where should I go? He goes on a journey with you straightaway. And that I absolutely love. But then again, he's a Microsoft employee. So he's taking the happy path, right? He says, go download this, go download that. I do this. And you hinted at the beginners producing all of this content. And it's wonderful to see that because even like if you get stuck, if you're, I mean, I don't live coding streaming is not for everyone. But if you're doing it and you get stuck, you can ask the people who are in the chat window, you can ask the viewers, hey, I'm kind of stuck. Has anyone ever seen this before? They can then tell you what to look for when they can give you the answer, and then talk through it. And you're like, Oh, well, we've just been on this journey. Excuse me, we're literally pair programming. And we've just learned this thing. And I absolutely love to see that. I don't get to use twitch that often these days. But when I do, I'm always looking for the beginners. And and it can be grateful if you want to learn a new language too. Because I'm a C# guy, right? If I want to learn Python, I'll go find a beginner's Python, because I'm at the more or less the same level as them. And even if they get stuck, if I don't know the answer, I can ask a relatively similar question like, oh, okay, so in C# we we do this way, have you tried looking for like, there was someone who was saying, How do I iterate over a collection in in Python? And they said, well, in C#, we have a thing called link. Is this something similar to link in Python? Let me have a Google for you. Whilst we're here. And I switched over to a new tab I started Googling around, I have found this resource try and check this out. And the pair of us went on this journey of what is the Python equivalent of link right. And so it can totally be helpful. Yeah. Yeah, I agree with you that the beginners and the the non experts can they can hit on these issues whilst they're building up their knowledge. And the the the most important tip that I give to a beginner developer is you're going to get them anyway. So get used to reading the error message, read read via don't just get pass on their back, I'll just carry out the error message at least in C# and .NET will literally tell you what was wrong. You know, they they're one step away from saying change this variable and you don't, you know, they're they're one step away from actually fixing it for you. And that can really be a game changer. I think

#### Vijesh

yes, absolutely. And I was once mentoring developer who started coding almost at the end, almost half of his career later. So he was into management, and then he picked up coding, and then he started C#. And then he started hitting these issues, you know, errors and stuff, which are, which can be, because errors look like failures to write correct code. But it's, it's, it's in a different direction. And I think you, you were right on point saying that, you know, just reading the error message solves, it puts you on the right path there to fix the problem. And it also develops, you know, what a mechanical sympathy to, to what you're working with, and that is very crucial to develop. And in the, in the rust ecosystem, I've tried a bit of rust programming language, and the compiler can be, you know, how do you say, it complains a lot, especially as a C# programme and our first try, but the community is kind of say that compiler is your friend. And it does a lot of work for you. There, I think that applies to most languages. And we need to get used to that it's not something that we should be disappointed when there's error. But that is a point where we can pivot and learn, okay, what needs to be changed? And it can be very satisfying to fix that once you do it.

#### Jamie

Absolutely. I chase down a bug recently, that took almost two days of constant. Constant why work inside of you know, I was in a US writer from JetBrains. A lot. This isn't an endorsement, I just really like it. And I was for several hours each day across two days going, why is this? No, I don't understand why this isn't working, should be working and putting more breakpoints in putting debug statements in writing out to the console, writing to the logs, increasing everything, you know, to the point where just reading, it was bringing the performance of my laptop down to the floor, it was like the laptop was going to stop. It's too much data, so many things to do. But then I eventually got to the end. And it turns out that I had some ID column in the database the wrong way around like I was using a foreign key as a primary key. And, and just that, that moment of elation like that, that that is not a standard experience for a junior developer, I have to say, if you found yourself in that situation, and you're a junior developer, go get help. Don't Don't sit there and stress over it. And I use the phrase bash your head against the keyboard. Don't keep doing that. Go get help. But because I was the only .NET dev on the project, I had no one to turn to right. So I was like, I got I got to figure figure this out. But yeah, that moment where you go from this is erroring. This should be working. Why is it not working? Oh, my goodness, it's working. You feel invincible? Right?

#### Vijesh

Yeah, absolutely. And that's a very good point, like, go get help. And it's, I would say, I wish I had done that more when I was a junior developer. And at that point in time, there was kind of a, you know, if you had to do an internet search for some C# syntax, I had to be sure there's no way around. But now, I think it's not associated with that, you know, shame if I can, if I use that word, but now it's more common for people to do an internet search. And that is absolutely fine. But I still see some, you know, some group of people that you know, searching on the internet, okay. It's, he doesn't know something. But the fact in the in the software industry is it's not possible to know everything. It's it's just not possible. And it's okay to do a search on the internet. It's okay to ask your peer. And sometimes I if I'm stuck with a problem, and if I'm the senior developer in the team, I just need an extra pair of eyes. So I I even, it could be a one year junior developer. I just asked him to join me and just work through the problem with me, that also helps.

#### Jamie

Oh, absolutely. Yeah, I always get it the wrong way around. I think it's the pragmatic programmer. But it may be the mythical man with one of these two books, I always confuse them, I sort of fuse them together because I read them back to back and just like in a fever dream of I want to be a better developer. And there's a story in one of those. I feel like it's the pragmatic programmer, about a developer who carried a rubber duck around with him and his engineer and he was just like he had this rubber duck everywhere he went, you know, the kind of duck you would put in a bathtub, rather flow. On the water, and he would just have that with him and he was in it on his desk. And if he went up to get a cup of coffee, take it with him, they sit back down. And the idea was, it's where we get the term rubber duck debugging from and that is literally talking about the problem will activate the parts of your brain that are not activated when you are thinking. And so if I'm talking to you, and I say, vishesh, I have this really tough problem with the database when I start talking to you about the problem I had a few days ago. And like, it says that it's a foreign key constraint issue, but there's no foreign key and use, the part of my brain will go a go check for foreign keys that, but I'm not checking that I'm checking everything else. Right. And it's proved science does even, it's a bit silly. And I don't always recommend people go to Reddit, because it can be a bit toxic in places. But there's a section of Reddit called shower thoughts. And this is just people who are exercising that they thinking about a problem, and then they'll walk away from it. And these, the stereotypical example is I went and had a shower, you're doing something else, you're having a shower, he's talking to someone, you make a cup of coffee, and then suddenly, the solution comes to you, oh, wow, I've got to write this down. You know, and that's why writers and comedians will sleep with a pattern pen next to their next to their bed. That way, if they wake up in the night, great idea for a story, great idea for a joke, they've got to write it down, because they're doing something else. And there's this wonderful. It's almost like a synergy. I feel like I'm talking in the business terms here, but almost like a synergy between your conscious brain and your unconscious brain. When you give up on a problem with your conscious brain, you can allow your subconscious to take over. And that is much more powerful than your conscious brain because your conscious brain is dealing with all sorts of other things. And so handing that off, or just talking to like literally talking the problem out loud. I've had it before where I used to call it consults, because I used to be a big fan of the TV show house with you, Laurie, can I can I get a consult? I'll go with someone else. But here's the problem. This is what I'm doing. And as I'm describing the problem, I get the answer like, Oh, thanks, brilliant. I've got an hour walk away. And they're like, Well, I didn't do anything. I don't know what happened. Okay, yeah, you can thank me for that. That's fine. And that getting help pair programming, asking someone for help, or just describing the problem, even if you describe it in a technical way to non technical people, the answer will just come to you. I promise you.

#### Vijesh

Absolutely, I can definitely relate to that. That has happened many times within my team with me and with my fellow colleagues as well. That's a great technique, just explain the problem to somebody. And you're in that direction already. While you do that.

#### Jamie

Absolutely. Because then even if you don't come up with the answer, describing the problem, they will see, they may see like you've tried to solve it in three different ways. And none of those solutions have worked. And you explain those in these. I don't understand why these three solutions have worked, then they'll go, how about this fourth one that you're not thinking about? That's it? That's the answer. Excellent.

#### Vijesh

Yeah, yeah.

And also, something that you touched upon was that, you know, just take a break, sometimes it really helps. It's very important as well. And even though you're starting, and there might be people telling you need to work hard and everything, but it's taking a break is as important as working hard.

#### Jamie

Absolutely. You have one, buddy. I mean, in the future, this may change with all the signs. You have, you have one body. And if you don't look after that, you can't do the programming, right. And so, if you've been sitting down for 45 minutes, perhaps consider getting up and having a walk around, walking around clear. Maybe get a drink, maybe go stand outside and get some fresh air and feel the sunlight on you and feel refreshed that way. I don't know, whatever it is. Yeah. Yeah.

#### Vijesh

Yeah, absolutely. That's, that's not much talked about, but that's one of the very key things. If you're a software engineer, that really helps. Yeah,

#### Jamie

absolutely. Okay. So we we talked a little bit about how we think that .NET is it's good for beginners, right? And I tend to agree with you because, like you say, if you don't want to spend a lot of money, you buy a computer, if it runs Windows, if it runs a Linux distribution, if it runs Mac OS, you can instal the .NET tools on there. And if you're running Windows, kind of already has them on there just well under the covers. It's .NET framework, but it's still it's still there. Because I remember when I did my computer science degree, we we did we use .NET for a lot of it. And the lecturer was saying you don't have to instal anything, just remember this really long file path. And that's the C# compiler is like C programme files Microsoft .NET framework version four and version two point something, slash tools slash csc.xe. And we would just, we would invoke it from the command line and pass all of the files through and it would produce an executable. It was brilliant. Not very user friendly at all. But if you don't mind that slight lack of user friendliness, yeah, get yourself Visual Studio code, get the .NET core SDK, or I guess, by the time this comes up the .NET, five SDK, I'm not sure. Get the .NET SDK get the Visual Studio code. And it's literally all there, right?

#### Vijesh

Absolutely, absolutely. And especially with .NET, five, there's a lot of confusion being cleared and much more beginner friendly there. And I absolutely love that direction. .NET is taking just one .NET .NET, core .NET framework. It avoids. And that if you're a beginner, and you're confused, what's the .NET core was .NET standard. Don't worry about it. A lot of people are confused with that. Even I was even with 10 years experience. So there's a lot of confusion there. But that's going to go away pretty soon, I think we are in the right direction.

#### Jamie

Absolutely. I do. Like there's a I believe it's a C# nine thing, I may be wrong, maybe a new .NET thing. Where you do if you have the canonical hello world C# console application, right you've got if you're trying to teach someone it's like ignore all of this cruft at the top using system, using system collections, public static void, ignore all of that namespace, whatever. And you can actually ignore all of that. Now, in the new version of C#, you could just literally read system console writeline Hello, world, and it will compile. And I think that's a wonderful step forward, especially for beginners. Because if you look at a HelloWorld, I believe it's using system. blank line namespace, my app, a curly brace, public static void, main, curly brace, console, dot write line, curly brace, curly brace. So you've got 10 lines of code, and the only one that's relevant to a beginner is right in the middle. And it's a single line. So I totally agree, get rid of all of that corrupt, you don't need it if you're a beginner. And you don't need it if you're writing tools as well, because it can all be sort of inferred. It's brilliant.

#### Vijesh

It's brilliant. Yes, exactly. Yeah. I remember after I finished my university, and I found a job as a, as a Java teacher in one of the computer Institute's and had to teach HelloWorld programme there. And Java also had the same thing, public static, void, main, and I think it was, I don't remember now, it's systemd or printerland. Or it was very similar to console writeline. And to come to that line, I had to explain Okay, what's what's, what's namespaces? So what's, what's the class was public, what static was wide. And I think getting all that, you know, away from the beginner is, is absolutely brilliant. Yeah.

#### Jamie

There really is, simplifies it so much. I remember watching some, so we talked about, there's loads of resources, right? There's some videos that Microsoft have put together, used to be called Microsoft learn. I'm not sure what it's called now, and I definitely don't know what it's called, when the episode comes out. But I'll put a link in the show notes if I can find it, where it's like, ASP. NET Core 101. And I believe it's Scott hanselman, who hosts it and he goes, what you do is you type this command into the command line, and it spits out 100 files. It's not 100 files, but let's say is 20 files, right? Go to this Warden file, scroll all the way down to the bottom, ignore everything at the top, and type this line in, and then run it and you'll see it says hello world in your web browser. I don't like I absolutely get it. But all of that like for a beginner. Like, I'm one of these people, when I'm learning something new, I brought up I async enumerable. This is not something for beginners. But I brought that up earlier on. And when I wanted to learn, instead of learning, why would I use this? How would I use this? I went okay, so how's it implemented and went on this deep rabbit hole of how it's actually implemented .NET core and then worked my way back out. And I was like, Oh, I get why I would use that. But only when I got to the end. And you know, there are some some beginners who are incredibly curious or want to be poking at things and say, well, what's this? Like? You said I have to explain what a namespace is what a class is. Public means what static means all of these things and then we get to this one line where a source valid right?

#### Vijesh

And and beginners are very curious and it's a good thing. And but having that you know, top level statements in C# and I think that's one For beginners to start with, and I like the fact that, you know, the dogs are getting improved continuously, which wasn't the case some time ago. And, and that's, that's definitely a good, proper place to start with. And you mentioned Scott hanselman, and absolutely a fan of his videos, which he puts out computer stuff they didn't teach you. And I love them. I love those videos. And if you're a beginner, I recommend you to go see some of the things there. It's, I wish there were more more and more content like that is absolutely goes to the basics and starts from there. And it's great. And I wish more and more beginners also put their experiences out there.

#### Jamie

Yeah, absolutely. Um, like I said, I trained as a teacher. And I knew that when you learn something, if you so there's, there's several different levels to learning something right, there's a I know, a four levels, there may be lots of other what I'm about to say maybe outdated. I don't know. But there are multiple levels to learning. There's like basic recall. So I say to you two plus two equals four, and you say two plus two equals four. Right? That's basic recall, you're just remembering what I've told you. And then the highest tier is being able to put that knowledge into your own words, to take it, internalise it, and produce your own reasoning based on the rules and logic I've provided to you. So if I said to you, the for each keyword in C# tells the .NET compiler to get the iterator for a collection, and work that will work its way through the collection. Now my description is going to be horrendously wrong, there's going to be people yelling, no, it doesn't actually do that. But that's my understanding of how it worked. Because that fits my worldview of my of using a for each in a C# listing. But just saying those words, it's kind of boring, right. But if you are able to just repeat that straight back to me, you've taken it in, it's gone into short term, it may go into long term at some point. But the way to reinforce that push that knowledge all the way into long term storage where you can, where your brain will make lots of synaptic connections between all the neurons, and it will always be there is to think about it to reflect on it, to play around with the ideas. And then to put those words out again, but in your own context, in your own words. And so we'll begin are going hate. So today, I learned how f strings work in Python, here is an F string. And here is what it's doing. And this is how I build one and this is how I use it. That is someone who is operating on the highest level of learning because they've taken that thing that they've learned that theoretical, let's put it straight right? compilation stuff to the majority of developers kind of boring, right? How do f strings work in Python, you can look it up. But you don't really need to know, you just need to know that an F string exists. So taking that knowledge, that dry, boring knowledge of what an F string is and how it works and applying it, and then getting your own understanding of it. That's where the money is. That's that's the wonderfulness of learning. And so being able to echo that out and just just write a little blog post. Today, I learned how to do f strings. And it greatly simplified my my way of using printing strings in Python. And let me show you why. Boom, there you go. You've just proved you've learned it. And it's a reference for when you come back later, I found that when I first started getting into .NET core back in version one, free version one, I started blogging about it every week, I'd write a whole new app and then tear it to pieces in the in the blog post. And I found that a year later, I was going on to my own website and searching for keywords to find that I'd already written about it and just Oh, yeah, totally. I get it. Because I'd forgotten it. Like you said, You're right. You've learned all this stuff, but then you forget some of it. And you mentioned Scott hanselman. Right. This is brilliant quote by him where he's like, I've been doing this for 15 years, 20 years, whatever it is some some huge amount of years. And he's like, I still Google how to do a jQuery selector. And I am there for that. I totally agree with that. Because it's not something you do every day. It's not something you're going to remember. Right?

#### Vijesh

Right. Right. Yeah. And that leaves, you know, some space to remember important things. If you can look up something you don't have to remember it and, and putting things out is a blog or a video or or a tweet or whatever. It's it's a good way to round off whatever you're learning. And I think a lot of beginners should do that more. At least I wish I did that more.

#### Jamie

Yeah, I agree. I agree. Because then it's Like taking control of your own learning, even if you are at a university, even if you are taking your course, you're following some prescribed thing, right? making notes on that and making them public so that you can look back on them. And maybe other people who are studying the same thing can then draw their own conclusions based on what you've said and what the course material says they can. It gives them a chance to sort of learn a little bit more. We deepens that knowledge. And then, you know, like you said, it's a reference material for later. Yeah, I've got I've got stacks and stacks of binders full of my handwritten notes from university, I will never look at them again. But over that one time, when I'm like, how did that do that binary tree? I can't remember how I did it, because they're a Google. But if I digitised it all, I could just search through it. Oh, there it is. That's the image. Right? I got it. You know?

#### Vijesh

Right. Right. It helps you and it helps others as well. Warren does a similar path.

#### Jamie

Absolutely. Absolutely. And that's what it's all about, right? He said at the beginning, you have to give back, you have to mentor people, and then help people get over that, that next step. And I think that's what it's all about, really, you know, there the majority of the knowledge that we have, as developers was given to a second hand by someone else, you know, when we're not going out and going, right, I'm going to build a C# compiler for .NET. It's the tools already exist, the language already exists. Let me show you how it works. As I'm passing that knowledge on, either in a passive way, we just like, here's a blog post, here's a video, or in an active way, where you're sitting with someone and saying, let's first talk about this, what are you struggling with? Okay, you're fighting with the, you're fighting with select, and, and, and projecting the results of a select onto a new onto a new object type. Okay, let's talk about that. Let's, let's figure this out together, because then it reinforces your ideas of it, and it helps the other person to see a real world example of what you're trying to teach them.

#### Vijesh

Absolutely. Yeah. And sometimes, the beginners encounter few questions that are so basic, that sometimes it takes a senior developer to think about it a bit. For example, we talk about single responsibility principle a lot. And by reviewing the code, and we take that as granted, okay, this is what it should be. And when a beginner, I faced that, once that, you know, he asked me why single responsibility principle? Well, that's, that's a principle you have to follow that. But why, and when I started talking him through it, and it helped me also trace back my steps and not just take it because it's a principle or because somebody wrote a book about it or not, but he walk, take the journey with that beginner in the same same level. And that helps both of them, the senior and the junior developer. And, and when you put that out, let's say something very trivial. And you learn about that. And you can still put it as a blog post, even though it looks basic, it definitely helps a lot of them and basics and fundamentals. We need more content out there, when it comes to basic and fundamental things.

#### Jamie

Absolutely, I've seen, I've seen a lot of people recently, sort of want to dive directly at, let's read about the super complex thing. And let's do this super complex that, like you said, right? Let's ignore the single responsibility principle. And let's maybe write a blog post about making a game in C# and .NET. And then they've got code everywhere that's talking to everything, and it's just a jumbled mess of spaghetti. horrendous, it does the job. But it's going to be difficult to maintain. And the idea behind these principles and these patterns is that, yes, what you've written today works. But tomorrow, when you're a completely different person, six months down the line, when you're a completely different person, or when a completely different person looks at it, they are going to be able to understand what's going on, they are going to know that when you change this variable over here in class number one, it somehow affects the variables in class number two, but they don't understand how it's all wired together because it's all a jumbled mess.

#### Vijesh

Absolutely. And and and I think one of the tips that I would give a beginner is when you see a principle or a law or anything in in the in the programming languages, wall or design world, it all comes with a certain trade offs. And it's generally hidden. Nobody talks about that. This is the principal or this is okay. You need to do unit tests for all your code that you write. Yes, but if you're crunched for time, You need to do a trade off, test your most important code and not testing, some of the other parts might still be okay, when you're crunched for time. So that you still maintain the quality that you want to and test the most riskiest part of the code. And any advice or any things, some someone claims on social media or we need to take it as a trade off, we need to take it with a grain of salt there and, and be open to challenging that principle or challenging that law. And that is very important as a beginner. And I think beginners bring in so many important questions. That that is one of the reasons I like mentoring is because they ask why to some of the basic questions that I think that it is, in a fixed that does not change. But it may, perhaps,

#### Jamie

yeah, absolutely. And by asking these questions, you're not. It's not rocking the boat is not being offensive. And at least as long as you don't do it in a defensive way. You know, it's not being offensive is not rocking the boat is not trying to be edgy, is it's not, and definitely never, ever be afraid of asking a question. Right? Never be afraid of asking a question and never be afraid of making a mistake. Right? Because there, as long as you have a team around you, there are checks and balances, to make sure that if you do do something that's not quite right, the rest of the it's sort of responsibility of the team to make the project. It's not your responsibility. You know, at least that's that's the way that I've always worked when I'm in a team. Again, maybe I'm a terrible developer, but you know, it's, you have the rest of the team to ask questions of and to check things with. There were times there have been times in my career where I've worked on something super complex. And I've walked away from it for an hour maybe to go get some lunch or something and come back and said, Can I please talk this through with someone? Because I'm not sure this is even a good way to do it? And just talking through it. And then someone else understands where you're coming from? and says, yep, totally, I get it based on the assumptions you've made, because that's the thing, right? If we're working for a client or a customer, you're making assumptions on what they have said, right? You're, we always talk about, we always talk about the, the the experience that someone's had, right? My experience with things will be different to your experience with things. So when somebody says to me, hey, I want you to write an application that translates text. Okay, I will do my best, right? What is it that you need it to do? Now my understanding of translate this text may be different to your understanding of translators text I am, you know, I'm from a, a culture, which reads left to right. And that uses predominantly English. But let's go all the way over to Far East Asia, where technically they read from right to left. And their language is completely different. The written language is different, there are subtle nuances. There are things that you don't even have to say, I studied Japanese for years. And you can have an entire conversation with someone. And the things you don't say, are the most important things, right. But if you're not saying it in your machine, translating it, the things you haven't said won't be translated. And so my assumption that you want to translate this text, which is a transcription of what someone has said, will lose some of that context, because there are things missing, right. And that's because my assumption is based on what you what I think you want me to predict. I've always said read, the customer never knows what they want, until you give them what they don't want. And that as always held true. Every single, every single project I've ever worked on is you don't know what you want, do we give you what you don't want. And that's why we have short iterations. And that's why our jail exists. And that's why waterfall doesn't always work. But again, like you said, there about trade offs, right? agile works. In some instances, when you can trade off the let's do loads of work and deliver a huge piece of piece of functionality. Because if you can get rid of that, that's waterfall, right? Huge, huge amount of effort, loads of work deliver one chunk of functionality, whereas agile is more, let's start iterating towards what we think the solution is slowly in chunks and let they let the customer tell us whether it's right or not. And then we can gently readjust our course. Whereas waterfall is very much a case of this is what you will get. And if it's not right, we need another six months.

#### Vijesh

Absolutely. And I think I've read in one of the books that software design is very fractal in nature. So changing something after a long period of time, once it's built is going to come More in terms of money as well as time and also in terms of energy that you need to think through that the developer needs to solve. And and short iterations are wonderful so that you need to process only a limited number of information at that moment. And you solve it, fix it. it's it's a it's a wonderful process. And I think most software companies needs to embrace it in one way or the other the Agile processes.

#### Jamie

Again, it's it's a number of trade offs, right? If you need to have the small iterations, the maybe your your domain requires you to work on a huge amount of information at the same time. Maybe waterfall works better for you. Again, it's that trade offs.

#### Vijesh

Absolutely.

#### Jamie

It's no one solution fits every problem.

#### Vijesh

Yeah, yeah, it applies to software industry more than I don't know about other industry, but definitely it applies to software industry.

#### Jamie

Yep, I agree with you completely. Okay. So what I'll say to you, visiativ, is we've spent a lot of time this afternoon already talking about such wonderful things. And I do want to thank you very much for being on the show. But where can people go to find out more about you and the the content that you're putting out there? You mentioned earlier on a more beginner issue, but I content? Well, if the beginners are putting out content, shooters, non beginners be putting out content? I don't want to call myself an expert, but obviously you are. So should the experts be putting out content as well? And if you are putting out content? Where can people find it?

#### Vijesh

Well, that's very flattering, you call me an expert. And I'm always on the path of, you know, learning more and more things and are more experts in the industry. But I like putting out content. But I'm doing is much lesser than I want to, but I am on Twitter, not so active. But I'm on Twitter, if you ever want to, you know, talk to somebody who can, you know, speak a bit about his experience. And perhaps if you look for a mentor, I can be that person. And I love doing that. And I write blogs on medium. And one of the goals that I have for next year is putting out video content as well and go into, you know, some of the things that are pretty basic in C#, but not much talked about. So it answers some of the why questions. For example, why C# properties or how interfaces are related to delegate some stuff like this, but that's for the future.

#### Jamie

I mean, that may be the present by the time this episode comes out. I don't know. Remember that time cast pod machine wibbly, wobbly? Enos.

#### Vijesh

Absolutely hope so.

#### Jamie

So watch this space, I guess? Yeah. Excellent. Okay, well, what I'll do closer to the time of this coming out is I'll communicate with you again, see if I can get some links to some of the other things that you're doing. You know, if you started the video content, or maybe you haven't, I'm not sure. But if you're interested in finding out more about Vidya, all of the links will be in the show notes. The way that it works is when you're listening, there's some redacted shownotes, which is like the short version and a link through to a transcription. In the transcription, there'll be loads of links. So give that a read as well. I like to produce the transcription because it can be useful for grabbing a quote or for our friends who maybe can't listen to the show, they can then read, you know, they can read through the show, or maybe they have some issue there. They can use a screen reader to help them but I don't, you know, I'm trying to be as accessible as possible as what I'm getting at. But there you go. Excellent. So yeah, I'll get those get those links for from you for Josh. slightly later on. A little bit close to the time of releasing this episode. Because obviously we do the time shifting. Yes. So thank you ever so much for Jesse, it's been a real pleasure to talk to you this afternoon. And I really appreciate you taking well over an hour out of your afternoon to talk to me to talk to the listeners about about beginners things and getting started with C# and .NET for beginners. Thank you ever so much.

#### Vijesh

Thank you so much, Amy. Thanks for having me.

#### Jamie

You're very welcome Vijesh.

{{< paracentre "The above is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

### Wrapping Up

That was my interview with Vijesh Salian about our advice for beginner developers. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/), and there will be a link directly to them in your podcatcher.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice - head over to [dotnetcore.show/subscribe](/subscribe) for ways to do that - and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Vijesh on Twitter](https://twitter.com/vijeshsalian)
- [Vijesh on Medium](https://medium.com/@vijeshsalian)
