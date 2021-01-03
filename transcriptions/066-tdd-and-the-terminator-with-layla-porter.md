### Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is Episode: 66 TDD and the Terminator With Layla Porter. In this episode I talked with Layla about her journey in .NET development, just how useful TDD (or Test-driven Development) can be when working on your applications, and her talk on both TDD and The Terminator.

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

{{< paracentre "The following is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

#### Jamie

So first thing I'd like to say, is Thank you ever so much for spending some of your time talking to me and the listeners. I really appreciate it. And I appreciate it. It's kind of in the middle of your workday. So hopefully, we won't be, we won't be keeping you too long and your employers can, you know, they won't be so upset with you taking all this time talking to me.

#### Layla

They'll be fine with it. So don't worry. It's my pleasure to be here.

#### Jamie

Excellent. Thank you so much. So the first thing we would like to do, if that's right, is could you perhaps introduce the listeners, tell them a little bit about you so that we know we'll be able to like who Layla is, and all that kind of stuff.

#### Layla

Absolutely. Jamie. So Hey, everybody. My name is Layla Porter. I am a Microsoft MVP. I'm a self taught dotnet. C sharp developer. I work for a company called Twilio as a developer evangelist. So I'm not really a developer anymore. I do more Developer Relations say it's kind of like developer marketing. If that's a swear word to you, I apologize. And And recently, I've been elected to the board of directors of the dotnet Foundation, so hoping to make some meaningful change to the dotnet foundation. I'm very excited for that. And I am also the co host of my local dotnet user group on meetup called MK dotnet. In Los Angeles. That's where I'm based, which is about 50 miles north of London.

#### Jamie

Excellent, excellent. So firstly, congratulations for being elected onto the board of directors at the dotnet foundation. So it must have been, I don't want to say a nice surprise, because obviously, you will put forward for it. But like, I don't know, was it a nice surprise? I literally don't know whether it would be a surprise or not I

#### Layla

say they went through like a nomination committee. And they selected 18 candidates from all the nominations. So that was a nice surprise to be put through. And then it was two weeks of I was told campaigning, and I wasn't quite sure what that would involve. But really, it was just writing, like a statement, I guess, a mission statement about why I'd like to be elected. And I also had an interview, the dotnet foundation YouTube channel, just to talk a little bit further and answer a few questions about why I'd like to be elected say, and it was really great to have the support of the community. And to see, one of the things the way that dotnet foundation voting system works as they can break down, they actually show you the breakdown of votes. So it was very humbling to see that. I've, as I say, well voted for I have to say it was quite, that was the surprise, I guess was how much support I had from the community and which was really humbling.

#### Jamie

Excellent, excellent. Well, like I said, congratulations on that. Can you talk to us a little bit about the Mk dotnet meetup as well, because I have not had much of a chance to talk to many people who run meetups, you see.

#### Layla

So yeah, so when I decided to change careers and be a developer, I started to look around and want to join meetups to help grow myself and maybe open up opportunities for employment. I started with a JavaScript meetup that was all there was in Milton Keynes, which was fine, because I was doing full stack. So I learnt JavaScript with Free Code Camp. And then suddenly, there was this dotnet meetup starting definitely to go to that because I'd been learning C sharp, mainly C sharp. In my in my learnings, as I said, right, we'll go to that. So I've been to it from the start. And I was about a year into it that I was asked if I'd be a nice organized nurse, I could do that. I'm good at organizing things. So yeah, it's really grown from there. And we've now got a couple of other organizers on, some people have moved on. And it's just really nice. What I've struggled with is to keep the community aspect of it since we've been in lockdown and unable to meter. And I'm not 100% convinced about the virtual meetups because it loses that core essence of what I think a community meetup is about, which is sharing stories over a slice of pizza or Coca Cola or whatever bomb cola usually, and whilst you drop anchovies on the floor, and it's I think we've lost that because there's in meetings and you got people from all over the world, which in itself is fantastic that we've made it so much more accessible, but at the cost of that local community thing. So that's one aspect that's been a little bit sad from the little But a big plus is that it's more accessible. And but yeah, um, I actually got my current job at Twilio through being a meetup. And my now boss had me speak at a meetup and approached me. So yeah, meetups are good.

#### Jamie

I can attest to that. Whilst I did the sort of university path, I did Computer Science at university and picked up dotnet. Whilst I was there, I was like, This is it, this is where I live. I love this. I do feel as though the university path isn't for everyone. And it's not as if the university path really set me up for anything related to what I actually do. I do like the idea of like, the Free Code camps and code camps and people just going you know what I want to learn this thing, I'm going to find a group to help me sort of learn it. I love that idea. Because part of what I'm pushing towards with my own career is this sort of craftsperson level. So I you know, I've gone inside the software craftsmanship Manifesto, because I want to be able to a push myself into new directions, and also be if at all relevant, sort of give back to people who are maybe, how do I put it not as experienced as I am, if I can share my experiences, and help them out and say, Oh, you should totally go learn this thing. Or I had some great experience using this or this particular technology in this particular this particular setup this particular problem, he isn't as easy to to use as this other thing, or at least in my opinion, it wasn't. So maybe investigate both. And I think that kind of that kind of helps when you're starting out, I feel finding someone who or a group of people who you can sort of bounce ideas off of and get information about what should I look up? Where should I go? Especially if you're technology adjacent? You know, if you're not if you're not a developer, but you want to learn it? Or how do you how do you go about it? Right, you got to find some people that can help you.

#### Layla

Yeah, I think the knowledge share is really powerful. I and I was lucky that my partner is a developer. And I think you do need a slight aptitude, I did go to university and I had to leave due to a loss of finances. And because I was a foreign students, I didn't, I couldn't get loans or things. And I actually did mathematics. So I've got that kind of logical brain. And but then I did shop work. And I worked in retail when I left uni, and you know, fell into lots of different careers from professional horse rider. And Mel recently, the party's teacher and things like that. And but I'd always dabbled in code I played with ActionScript. And I love computers. I was a gamer since sort of my early teens. And I love graphic design, and working on computer graphic design, I should say, and building tools in Illustrator and, you know, designing with illustrator, and playing with those. And I actually tried to go back to university to do graphic design. And then nothing ever, ever worked out. So I just sort of messed around the code, taught myself ActionScript. And I've always been one of those people who tries to teach themselves things. I fancy trying that. So I'm going to, I'm going to play with it. And I do it. And so when it came to, you know, learning to code, I was very lucky that I had my partner, he could mentor me and help me, even though he had his day job. So I was learning in the day. But if I got really, really stuck, I had him as a fallback. And I think having mentors is so important. And I'm a big believer in giving back. And that's another reason to go to meetups because you can make yourself available as a mentor or someone that someone can come and ask the question that they're really insecure about asking because they think it's stupid. And and that's one of the reasons why I stream on Twitch actually, because I want it to be a safe place where there are no stupid questions, and you can come in and ask the most inane question, if that's what's troubling you please ask, you know, and I think mentorship is amazing.

#### Jamie

It really is. It really is. I mean, I haven't really had much of a chance to do it. But when I've been mentored by other people, it's been an absolutely amazing experience. Because, like you say, you know, you're, you're you're wondering, Is this a stupid question? Is this something I should just Google and just trust the first thing or should I go and ask this person that I respect and worry about them saying that so stupid question, but if you've got a good mentor and someone that you do truly respect, and I feel like they wouldn't say that's a stupid question. Because there are no stupid questions. It doesn't matter what industry you're in on. No matter how much experience you have, there are no stupid questions. The way that I see it is you're stupid not to ask the question. But that's kind of mean anyway. But like, if you're unsure, ask because otherwise, you're never going to know. Right? You're only going to assume.

#### Layla

And I think it's good to make ways for people to ask the question in a way that suits them whether, and that this is another problem with the virtual meetups, because everyone's in a big Zoom Room. And the person who's not confident speaking, like unmuting, and talking to the whole room, they stop asking the questions. Where is it, she could be in the queue for food and, you know, you just naturally talk to the person beside you, or behind you or in front? And, you know, did you enjoy the talk? Or Oh, you know, what to do in the question by by x, y, and Zed? And you could be like, Oh, yeah, you know, that's because of this. Whereas if it's in a Zoom Room, they'll be like, I'll just Google that, or I don't need to know that badly. And, and, yeah, it's about making safe environments and different ways for people to ask that question whether through, and like, some people want to ask it and a direct message on slack or Twitter. Or they're quite happy to put their hand up or unmute, and ask it in front of everybody. And that's okay, too. And if you're thinking it, and yet, maybe someone else will ask it. But if you're thinking it and have the confidence to ask it, even if you kind of know the answer, or you think the speaker didn't clarify it, and you think, I reckon beginners might not understand that. And then what I will do, even though I know, for example, what the speakers talking about, to try and make it more accessible to genius and new developers, I will ask the speaker a question that I think other people might be wondering. And I'll be the voice of these people to try and help open up that thing. And I think that's another thing that you can do as a mentor is ask the questions that you think people might want to know.

#### Jamie

Absolutely, it's, um, I feel like it's potentially not an easy thing to be a mentor. And that's why I'm sort of like, I'm not doing it officially. If somebody wants to ask me a question, I'll happily answer it. Or I'll say, I don't know. But let's find out together. Because, because then it's also a case of you flooded the answer to your question. But also, I want to know what it is what it gives you. you've identified a gap in my knowledge, and I want to fill that gap. So then, a I'll know for next time when I need to do it, and be if someone ever asks me again, then go all right. Well, last time, I looked it up. It was this right?

#### Layla

Yeah, yeah, no, that's really it. I have a thirst for knowledge and things like that. So let's, let's go figure it out. And also by you learning better, and you learn together, you get better at explaining as well. And it deepens both your understandings of it. So it's really it's a win win.

#### Jamie

Absolutely. So what about the so I happen to know that you have a workshop coming up? And I also happen to know that you do twitch streaming as well. I thought maybe we could cover both of those at once. Yes. So talk about how one is kind of linked to the other. And

#### Layla

yeah, say I've been, I was streaming on and off last year, and they could never commit to it. Because part of my job is to travel. a good deal of my job is to travel all over Europe and North America to speak at conferences and sponsored conferences and run by first party. We call them Twilio workshops, and events. So I couldn't ever dedicate the time to streaming properly last year. But something happened this year. That meant I was at home a lot, and was able to dedicate the time that I felt I wanted to dedicate to streaming so I started to do that. And I also had this other idea from the stuff I did with Twilio. And we have this cool tool at Twilio called Twilio quest to help people not only learn about Twilio, but also to help them get into programming. We have JavaScript and Python. And I think we've got PHP or for beginners and nothing about Twilio. And you can just learn to program in gamified learning. So I seen that and I was in Tel Aviv, running this workshop. And I think I've been to Tel Aviv before and the developers there are super, super smart and they knew everything. And the beginner sort of the introductory and small demos that Twilio quest and gave once sufficient for them. And I started to think about what could I do that would be a better experience. For developers wanting to learn about Twilio, and this goes for developers wanting to learn about anything, it just so happens, I want to learn about Twilio. And so I thought, right, how can they integrate various different Twilio communication API's? Well, communication security API's? How can they link several of these into a cool application that we can build. And originally, this was going to be an in person workshop I ran. But I had to pivot quite quickly when all of that went out the window, so I decided to make a video series. But I didn't really know where to start, which is where the twitch streaming came in. And it became content for my twitch stream, to build out this application and iron out all the the little small details, all these considerations that I'd never had to think about before that I now take, because I was creating this workshop. And I could start to iron those out on stream with viewers of all levels going, Oh, but I don't understand that. Or why did you do it that way? And so the the YouTube videos that I've created, well, they're not on YouTube, yet. They're they they might go, let's say videos, and RM are much better for it. And features they've almost been tested by the users as I built.

#### Jamie

Okay, excellent. And and and that links in with the the workshop you're putting together because you're you're testing it almost on on Twitch beforehand.

#### Layla

Yes. So I built it out on like the application I built out completely on Twitch. And then I rebuilt it, refining it, and recorded it all at the same time onto video narrated? And that's a very long winded process. If you think I did, I think it's about four and a half hours of video. And you might think, oh, that took about eight hours. Oh, my goodness, no, that was about two and a half months of recording. And some video five days a week. I've never undertaken something like that. It was a huge undertaking. And then you'd be like, Oh, that was really rubbish. Or I did that terribly. And you'd have to re record and re record and re record and then you watch it back and you're like, oh my goodness, I made a right dog's breakfast of that. And how to explain that. And, and that the more I did it, the better I got an eye and that could transfer back to twitch as well because I got better at explaining things. And it really improved my depth of understanding. So the whole thing, and has been a wonderful experience. And I hope I get to do more.

#### Jamie

Excellent. So what see it does the workshop have name at the moment? Or is it still sort of like Baylor's workshop that's currently on title.

#### Layla

So it's, it's learning to build with ASP dotnet core? And Twilio is that's what it does. And the app we build is called the Cloud City cake company, online ordering system. So we actually build an ordering system. so users can order their cake via WhatsApp and and surveys, show them how to do all of that with this really cool wiziwig serverless tool. We have Twilio code studio, he basically drag and drop all these different elements onto it, whether that's an HTTP request, or a reply to a met incoming message or voice call. And you can just build up this old chat bot, we basically built with it, and all using WhatsApp. And I chose WhatsApp because the good thing about WhatsApp is that it works all over the world. And whereas what a lot of people don't know is there are so many restrictions on telephone numbers in different countries and policies. And you can't always get by numbers in certain countries. And you can always buy it by a number that's got SMS capabilities, or by a number with voice capabilities. But WhatsApp works everywhere. So it was really good to work with that. And it's one of my favorite API's. So it's so much fun. So we built that. And then what do you do once you've taken this cake order of someone? Well, you've got to send it to an app and save it. So then the next stage was to build an app. Well, I chose an MVC app. And it needed to be dotnet. Core, obviously, because it's, it should be and it's cross platform. And that was really important to me that it was cross platform to welcome developers on all platforms. So we built a dotnet core 3.1. And I chose MVC because I thought, it's easy to understand maybe not as easy as razor pages for a beginner, but it's still easier than say something bleeding edge, such as blazer. And if you had experienced steps, they're more likely to be on an MVC platform, whether that's framework or whatever. They'll be able to integrate the ideas in the workshop into their existing platform. So it seems like a good choice. So we built that out. And we built in a little UI with some bootstrap nice and simple. And then we learned how to send invoices attached on emails via sendgrid. And also how to send like updates via WhatsApp. So it is cool to integrate it all into one application. And we did some really good refactoring in there putting in some fattens touch on a bit of solid. And, but no TDD or unit testing whatsoever. Something had to give, I have to say, so it was the testing,

#### Jamie

I totally understand that. If you if you're sort of aiming to get less experienced developers using something they haven't used before, you don't want to you don't want to confuse them by adding lots and lots of different extra, right, okay, now that we've got the audit, before we write anything, we have to write some tests well, or indeed, once we've written it, now we're going to go back and write some tests. Whereas like, I just want to get over the, I want to get to the point where I have a working application, and I understand how it works. And then if I want to later on, I can go back and add tests, not the best, maybe not, depending on how people feel about a maybe not the best way to do but at least you have tests Anyway, you know, once you finished, and then I liked the idea of I also like the idea of using MVC rather than blazer and, and razor pages, because MVC has been around for what, 10 1517 years, something like that. And so there's lots of support and documentation so that if someone comes away from this workshop and wants to extend it, but perhaps they've understood exactly what you're saying, but there's one thing that they want to add that you didn't touch on this, at least a decade worth of documentation and videos and resources that they can sort of go and look at all this is how I add this, this is how I this whereas if it was blazer, I mean up until late last year, blazer kept changing.

#### Layla

It's been a roller coaster with blazer. And and razor pages is one of the most beginner friendly frameworks, but I didn't. I've never used razor pages. I mean, I can go in and use razor pages, but I've never like used it. And

I just thought I'm not

confident with razor pages to build a workshop on. And I also think it's it's also newish. And there's not that I don't know how many production apps are built on razor pages. I don't know any of that data, whereas I know a lot of production is on MVC, all of my career, I've worked on MVC, and most of the devs I've spoken to, are all working on MVC, all right through framework, they were on MVC, and as you say, it's long established. And so it would span more developers. If I use MVC as the platform, it's still beginner friendly. But there's experienced devs coming in. Yeah, I know this, I know how to use MVC. Let's get into the meat of how to use Twilio. So it just seemed like the most natural fit. And I i've, I love MVC. And I'm still a big advocate for MVC. So it's great. And if you don't know what MVC is, it stands for model view controller just say, and it's a pattern, and not just restricted to dotnet. It's used on multiple different programming languages. So yeah, so very good pattern.

#### Jamie

It is. It's one of the, I think one of the easiest ones to sort of get started with when you're doing web stuff, because it just kind of it fits really well. There's lots of separation of concerns. There's lots of

lots of separations of concerns that

you don't have one huge block of code doing everything, you've got a smallish block of code doing the thing. There's a reference that I use that I think many people get, and that is from an episode of mash, which was a sitcom in the 17th character says, I do one thing at a time, I do it very well. And then I move on. And that's how I feel about the MVC button.

thing and one thing alone.

#### Layla

And that makes it really testable as well. And because I have no idea how one would get into razor pages and write a test, everything is managed together. And I've had to work with razor pages a lot in the past couple of months. And because I've been doing a lot with ASP. NET identity, and that is a, I think it's called a Razer Core library or core razor library, Razor class library, something to do with razor and library, and it's all sort of a kind of black box. But if you want to and customize it at all. And you then have to scaffold which is a way of doing cogeneration. And bringing in this stuff while extracting the blackbox pages and views out into your code, so you can modify them. And it's all razor pages. And I forced myself to do it in MVC. And so now I've got munged application of MVC, and razor pages, which has been challenging, and I'm building this on Twitch, ready for my next workshop, which will build on the existing workshop for our city cake company and add in identity and logins and things like that, say, and I'm experimenting with it. And but I look at these razor pages where you have the code behind, it's called the code behind the view, you have the model related to the view. So it's kind of like the view models there. You've got your code in there, you can bring reference out external code, obviously, which you could test elsewhere. But I don't know how you test this code in the code behind I'm sure there must be ways but because there isn't a separation of concerns, and it's all managed in and it's doing lots of things all at the same time. It's not doing that one. In my brain. It's like, Oh, ah, I don't know where to start.

#### Jamie

Sure. Sure. I totally get that. I must admit that. Because I've been working with dotnet. Since the early days, when I saw razor pages, I went, ah, it's web forms. No, no, again, never again.

#### Layla

It is it's easier than web forms, because it doesn't have that. And at the bottom of web forms, I did a little work with my plans, I have that massive sort of state management bit at the bottom of web forms. And I don't think razor pages have that. And, and so they're they're an improvement over web forms, which is still widely used. And, but um, yeah, they just don't fit well in my brain. And it's all what works in your brain. And all our brains work differently and learn differently. So it's really important to find something that fits with your brain, I keep trying to learn F sharp, I've done three awesome workshops with F sharp, which is also on the dotnet platform. And it's, it's functional programming. I cannot get that into my head. It doesn't work. I my, my brain doesn't work, F sharp works. But my brain and F sharp don't work together. So it's all about finding something that works for you.

#### Jamie

Absolutely. And you also have to think about the end client, whoever you're building the application for them, really usually care which technology which language, which framework, which methodology you use, they just care about. I have I didn't have a thing. And now I have I think that's all they care about, you have solved my problem for me, it doesn't matter to from their point of view, whether it's C sharp, whether it's F sharp, whether it's JavaScript, whether it's Ruby on whale or rail, sorry, whatever it is, they really don't care what technology is running as long as when they push the button. They get whatever it is that they want out of it.

#### Layla

Yeah, very true.

#### Jamie

Excellent.

So we hinted at earlier on there that your new workshop doesn't use doesn't have to add because it would be a little bit more complex to to build in just because TDD itself is quite a complex topic. But I thought that maybe we could talk about TDD if that's all right. Yes,

#### Layla

absolutely. I am, I am a massive advocate of TDD. And, and that's why I always get people joking with me that a lot of my projects don't have even unit tests and let alone be developed in a test driven development manner. And so it's horses for courses, isn't it when you're building a workshop, and we want to make sure that people understand the content you want them to you don't want to clutter it with additional patterns. If I want to teach someone how to do TDD, I'll do a workshop on TDD. And I need to have separation of concerns on my workshops. And so if I am building something in production, then now I will always build

in a TDD manner.

And that came from one job I was at. We didn't have any unit tests at all. Nothing, no integration tests, zip. We relied solely on a team of six testers, one of which was using Selenium and everyone else was just in manually testing. And we needed like a release every year or 18 months on this monolith of a project. And so we'd be hands off, we'd hand over the the release to the test. And then it would take about a month, they tested all and they'd come back. And it was after this last release I did at this company. And after nine weeks, I was still fixing regression bugs that I thought they really must be a better way. And, and I was still quite early on in my career. So, you know, I hadn't had the breadth of knowledge, and I started to look into it. And that probably could have some tests. So I looked into that and found out more about TDD. And I also started to look into solid principles as well, which has design principles that we won't go into. But they apply across all programming languages. And, you know, they've been around since the late 80s, the solid principles, so very long established. And, and I say, Oh, well, this fits my brains, I remember what I was saying about things need to fit your brain, this TDD and solid principles really suited my brain, I could really get behind this. And so I started to try and teach myself TDD with the hopes of getting a job at a company that employed TDD methodologies. Because I spoke to my current employer, and they basically laughed me out the room. Oh, no, we don't do TDD solids a swear word around here. And is that okay, man? And so I was like, right, so I need to start upskilling so I can move on and work in an environment that I want to see. So I tried to learn TDD while this was epic fail, if there was a compilation of me trying to learn TDD, I think YouTube would be having a payday because it was failure after failure. And every video I watched it look like Matic literally, they're like, everything's gone green. And like, Wait, what? How did it go green? I don't understand what do you did some magic. And normally with a video, they sped it up as well. And I'm trying to follow this. And it's going really quickly and like, the type so quickly, because I'm so stressed about trying to learn, I didn't realize that they've got it on like two times speed or whatever. And so watching videos didn't work for me. And I watched Pluralsight videos, YouTube videos, all sorts of videos as, okay, so I looked at books, and then someone tries to explain it. And books like this doesn't work either. And then I was following tutorials and blogs, and I'm like, I sort of get it, but I, I don't get it. Right. And I probably just rewatch Terminator again, and Terminator is one of my favorite franchises. And my favorite movie is Terminator two. And I love that the new ones have been quite good as well, but we won't, we won't go off on to our Terminator critiques. And it was either gonna be Terminator, or alien. I love the Alien franchise as well say, and I went with Terminator because I'm like, I'm going to develop a killer robot for TDP. And I'm going to do this as I started my project. And

I thought, right, the first thing you need with if you're going to do test driven development, is some requirements, because how can I write my tests if I don't know what my code should do? So as I Okay, so we've got a hunt down children and women and kill them or whatever. And so rates and lease requirements. Okay, so what's my Terminator need to do, but it needs to examine, and children. And if it's a boy, investigate further, because it could be john Connor says, Okay, I can I can write back and say, finally I started t get into TDD, and I could start to write, I can get to write this test. And, and by writing out the name of the test method, like Terminator should investigate further, if it's a boy, I could start to go. Okay, so now I know what my test needs to do. And then I could write my code. Now, I still wasn't doing it. Because I was doing one of these big mistakes that people do with TDD, they write a unit test to start with. So they're doing TDD, great. Then they go over to the code. And all of a sudden, they've got like a massive switch statement or a whole load of code, and then they come back and my test passes, I should write the next test now. So what they've done is they've written on their code, now they're doing unit testing, because it's not test driven, that they're going to write their tests after the fact. Nothing wrong with that, but it's not TDD so I was kind of in this for I did a couple of tests. And then I just get round to unit testing, which is great, because I was still learning how to write unit tests. So I was really happy with that. I actually went for a job interview at a company that did TDD and I told them, you know, they were looking for a senior developer do tg and I said, I'm good for the senior level, but I've never done TDD. So they said, Okay, well, we'll pair program on the technical test. I was like, fine. So they went through and showed me the TDD. And, and something clicked by pair programming with someone. I was I, now I really get it. And I didn't get that job. They said, I was I wasn't experienced enough in TDD. Like, I wasn't upfront about that. But anyway, they did me a huge favor. And because they, they really buy pair programming with that lead developer who was interviewing me. And I was like, Yes, I've got it now. And the thing that he he's, he showed me, which was my big aha moment, was when you write something like, Terminator should investigate children. And if it's a boy return true, the actual code I should write is just simply return true. And that was my aha moment. And that's what I try and share with people when I talk about TDD, is you write the least amount of code to get your test to pass. And it was once I got that, that everything slotted into place for me, and I was like, I've got this, as I went on to do have another interview, and I got that job. And so I got my first TDD based development job, and I was really pleased. And that was a really forward thinking company, that weather like bright, we're gonna sit you down with this fellow besides you, and you two are just going to pair program every single afternoon. And that was revolutionary for me, I was just after, like a week of pair programming, I really had it cemented in and I could just start developing with. And it, I think it's having the time to allow you to get that, that culture change and adapt and understand, which is often missing when people try to do TDD. And I was really fortunate that I went to that company, and not the first company, where they just sat me down, let me pair program and learn how to do it. And so that I was very fortunate that

#### Jamie

Excellent.

Okay.

So you have kind of explained kind of what TDD is there. It's a, my point of view is you've wrote a unit test that fails, or you write the tests are in the fails. And then you go and write the least amount of code required to make that test pass. Like you said, there, you know, if you have something that should return true, you just public, public bool, my method, parentheses, parentheses, squiggly brackets, return to squiggly brackets, that's your test passes. And then you read the next test. And then you iterate on that. And as I think I've heard the term red green refactor, you wrote the write the unit approach, rather, rather write the test, write the code that passes the test, and read the next test, and it will fail. So then you refactor to make the new test pass, which likely will make the previous test fail, you refactor to make them both pass, and then you carry on.

#### Layla

Yeah, and I use the red green refactor pattern as well. And if you're not getting red tests, it means you've gone and done what I used to do, where it is a written holiday code, and then come back to write unit tests. And I just say that that's okay. And there are some purist tbbs out there. And, and I've had people threaten to delete a whole day's worth of code, because they're like, you haven't written this or TDD. Because, you know, starting off. And so there is a way of doing it in a purist fashion. I'm more of a pragmatist. And I think these tools should work for you not not be like a hindrance. And if most of the time I am doing TDD, and then occasionally, I come back and do some unit tests after the fact or, actually, I'm not going to write tests for this at all, because or unit tests for this at all, because I'm going to do an integration test, because it's a, you know, data access and writing unit tests for data accesses, somewhat painful. And then that's okay. You've got to make the tools and patterns work for you and your product and your team and your customers. And so I'm very much about being a pragmatist in these matters.

#### Jamie

Absolutely. It's about what works for you and the team in solving the problem. Like you say, you know, if you're doing something that's data access, then you're not going to write a unit test, which means that you may not want to do TDD, you definitely don't want to do a unit test, which means that perhaps, get the code working, make sure that it compiles make sure rebuilds, okay, now I'll write a test for it, or a suite of tests. Or maybe you'll go I'll write the suite of tests, they'll all fail and then I spend a week writing the actual code and realize Actually, that's not doing what we want it to do. So I got to spend another week rewriting. All right?

#### Layla

Yeah. Well, you might go off and do a spike and go, there must be a better way. And suddenly you come back for some micro service that takes all the way and you don't have to worry about it anymore.

#### Jamie

Absolutely, absolutely. I will say, from my personal experience, I do know that I've seen a lot of people try and write unit tests, integration tests and TDD. For the libraries, they're pulling in, not around the libraries they're pulling in. So let's take Entity Framework as an example. I've seen people write unit tests for Entity Framework, because they're using Entity Framework, I turned to them and said, I think you're going a little bit too far there. Because I'm going to trust that the authors of Entity Framework have tested it. And if you're worried about that, maybe you've got, you know, you've got obviously nothing to worry about with your code if you're testing other people's

#### Layla

code. Yeah, never test other people's code, only test your own. And this comes up to something, a bit of a debate I had recently,

with some people about testing,

doing null checks in constructors, when you have dependency injection, I do them out of habit, even if I'm not doing any tests, if I'm writing demos, I'll still write a null coalescer on an injected value. And some people are in the camp where they're saying that you should test it. And other people are like, no, you're testing the dependency injection layer. And you should trust that that's been written and tested by here, whoever the services that you're using, and whether that's the built in dotnet core or ninject, or whichever one you're using, that you should trust, absolutely, that someone's done the testing, and you can assume safely that it's going to work. I don't know how I feel about that. I probably am still going to right now coalesces in my constructors.

#### Jamie

I feel like it's a good idea anyway. Because

what if, what if you're, you're writing some code that, okay, your, your constructor does take a whole bunch of things in and you're relying on the dependency injector. But what if you need to create an instance of a class without dependency injection being around? Yeah, or Yeah, or somehow you do indeed pass a null in something somewhere as as gone slightly wobbly. And you've got an oil coming in, you don't want the entire app to blow up? I totally, totally get that.

#### Layla

Yeah, I think one place where someone said it can happen is if you use the AI options pattern, and you're bringing in that your, your code will compile, and you won't get an error on your IOC. But when it comes to actually extract the value out of the I options, you'll get a no then an error. So that was one place where they said yes, you should check that your value in your eye options, and injectable is coming through. So that was definitely yes, I've had that where I've forgotten to you and to bring in my configuration and and and add it to the I options. And then when I try and use it in a class, it's not there. So now I think I will always right? No.

#### Jamie

No, I totally agree. I tend to use God causes in some places, not everywhere, but in some places. Because with my god pauses, I tend to raise an exception, because in that instance, where I'm using our course it is exceptional to not have say, if I'm expecting a string and it comes in no or it comes in empty. That's an exception. That is exceptional circumstances. Whereas in the constructor, it's not great. I mean, can you get away with using a default value, I think in most instances, you should be able to get away with passing in a default value. And that's where I would use a no coalescer. It's a, you know, this is injected value, no coalesce, or a default value or a new instance or something because at least then the guards are working and you can sort of you can protect against that later on.

#### Layla

Yeah. And then one thing, and, you know, Lance, when I was doing TDD was to use exceptions for exceptional things, and not for code flow. And so that was something that was really interesting. And I'd never had that before we do use, you know, with throw exceptions, and swallow them and then carry on and do all sorts of things. And then my lead dev at the new place where I was doing TDD was like he if something is an exceptional thing, we can't think of it happening. That's when you throw an exception. So that was a really interesting thing that's always rattled around in my head. Should this be an exception or is there something I can do is this unlikely to happen.

#### Jamie

So yeah, absolutely. Okay, so we've talked a little bit about TDD. What I'd like to know, from your point of view, what are some of the positive points and some of the negative points? Because every, like you said that everything has its positives and its negatives, right? There are some things that just work for some people and some things that just work for other people. And so in your opinion, from your experience of using TDD, what are some of the positives and some of the negatives.

#### Layla

So the biggest positive for me with TDD is having clear acceptance criteria from your product owners and stakeholders. And it really improves the relationship with the people asking you to write the code. If you've been explicit, saying, there's not enough information here, I need more information. They go away and think about it more, if you more requirements, and you know exactly what they want. Therefore, you write code that fulfills that need, and they're happier, and you're happier. So that's a huge thing for me, because you can't write your tests first, unless you've got clear acceptance criteria. Another big thing I love about it, but you get this from unit testing is that safe refactoring. So I would never have had the nine weeks of regression, bug fixing, if we'd had a test in somewhere, a unit test anything any any way, that would have been amazing. And we wouldn't have had to go through all of that pain. And so there's a huge positives. And I think the negatives are more cultural than to deal with the code. So there can be a lot of pushback from product owners and stakeholders and developers, that TDD slows you down. But I think if you're not doing TDD or unit tests, you're accruing technical debt, so it's going to just hit you later. And so it's like, a false perception of the time, you're investing upfront, by getting proper acceptance criteria by getting all of that testing framework in place. Because what you'll generally see is that the productivity will have a massive dip, when you start with TDD, everyone slows down, you've got devs, who are generally pair programming, because it's a really good practice to have pair programming, even with T senior devs. It's not always about a senior dev in a junior Dev, I think having two senior devs together can have amazing outcomes when you pair program. And it's a way of sharing knowledge and experience as well. So you see this dip, but once the, once you get past that debt, and you start to make some progress, and a lot of the groundwork and the foundations there, you'll start to see things get quicker and quicker, quicker, refactors are quicker, new features are quicker, because we're not breaking things. everything's in place structures in place, we've thought about how to architect everything in the best possible way to suit all of the criteria that we've got. So you start to see this huge sweep up now trying to sell that to even non technical people in their life, right, we're gonna have a big reduction in productivity. And they're like, well, how can we do that? And, and that's the hard thing. And it can be disheartening for developers who are used to being high producers. So they know that they get through all the things they're assigned in that sprint. And normally, they're going into the backlog and pulling more things off. And all of a sudden, the team's not getting through the entirety of the sprint. And the next sprint, we're having to reduce the number of use cases we bring over and stories and etc, and, and tasks. And so they're like, why are we obviously slow? Are we being stupid, what what's going on, so that you have to make a safe environment for developers who are used to high rates of productivity to be okay with the slowdown in their production, and not concerned about this at all. And make sure that they know that this is to be expected, and they're not going to be penalized. So I do think it's much more around the culture than TDD itself. And now I do say that you can do a spike with TDD and unit testing. And, and other people are like, No, you just want to hack things. Well, I think there's a happy medium here. If you're, if you're just going to hack things in to get to a point in a spike, but you want to have a couple of tests. So you know that your spike has fulfilled, what you're out there to look at. So I'd say write a couple of tests. Just we're not going like, you know, testing all the constructors, we're just going to go does this method return 200 for example, you know, And so you want to make sure that your end results and the expected outcome of your spike, or the purpose of your spike are covered in a couple of tests. So I think this is where I come from that practical approach. You want to have a couple of things in there just to make sure it's working. Or if you're not sure where the problems are, you can pinpoint them because you've got these tests. So yeah, it's, it can get a lot of steps. But I think it's worth pushing through and knowing the positive so you can sell it.

#### Jamie

Okay, that makes sense. I would also argue that testing, or other automated testing, regardless of whether you do TDD upfront, or you do test afterwards, is immediately cheaper than doing sort of manual scripted tests. My my point for that is, the further away the code gets to the developer, the more expensive it is to revisit and fix a bug. And that has been scientifically proven over the past 20 to 30 years, and there's no way that you can actually argue against those numbers, the further it gets away from the developer, the more expensive it is. And if you have automated tests that take less than 30 seconds to run, versus a script of manual tests, that takes a week to run, which is going to be quicker to run. And which, you know, if you There's nothing, absolutely nothing wrong with having scripted manual tests, but those are the expensive ones, because it takes some time to run them. Whereas an automated test that runs like that, like that, like that can be run every time code is checked in. Which means that you know that the code you have checked in, isn't going to break anything else that someone

else has checked in, because you may be looking at

a relatively small portion of the code is a big, maybe a big slice of the code to you. But the overall code base is huge, right? Let's use the analogy of a pizza, right? We talked about pizza earlier, and you're working on one slice of pizza, it's gonna fall over because analogies and metaphors fall over. But when you put a slice of pizza into the box, everything else breaks, the box falls to pieces, the rest of the pizza falls out of the box, for whatever reason. And by having a test so that when you put that slice of pizza in the box, you can make sure that it doesn't all fall to pieces. And being able to do that for every single time that you put the slice of pizza in the boxes here. I mean, the analogy doesn't work. But you get the idea. Right? Absolutely.

#### Layla

And I think it's, it's having that, that stops these bugs getting checked in when you have and see, over time big projects, big projects can have hundreds of thousands of tests. Because for one class, you might be writing 3040 tests. And you think how many classes and how many services you have, and it all starts to build up into thousands of tests. And if every time you check that in your build servers going through all of those, and it may take five minutes may take 30 minutes. But isn't that better than waiting for someone else to come along and do it and you know, instantly, oh, my check in failed? What did I break and you go and fix it, then well, it's all loaded into your head. And I think code is all about having it loaded into your head. And because if you there's lots of research turned into when you disturb a developer, it takes them a good, I think I want to say five minutes. But I think it's longer. I think if you chat to them for five minutes, it takes them 30 minutes to get back into their flow or something like that. But there's a lot of research around that. And so the best time to fix bugs is when it's all loaded in your head, and you're working on it right there. And they're not. I mean, we had these, remember is that the releases were sort of every year, 18 months. So I have no idea about the code that someone else wrote a year ago, and they're not even here anymore in and then you're like I have I don't have any start reverse engineering it and then they've done some smart coding. You know, let's try and get what was 20 lines of readable code down into some kind of ternary nested ternary. So I've had to deal with and I'm like, Why? Why? Why do we have nested ternary? So yeah, I think you're really right. As soon as the developer can see the errors, they're able to fix it much quicker.

#### Jamie

I would caveat a couple of things you've said there with

an hour after you've checked in the code. You're a different developer. So you said that I don't know what this other developers written. That other developer was you or it could be someone else. It just the pure fact that you've moved on to another task. You've lost all of that context. So you are effectively a different developer. Right. And the The nested ternary I absolutely despise those. And I despise like nested link statements, because Steve McConnell in code complete, one of the sort of accepted texts for how you should write programs. He says, I think he uses a bit of Star Trek when he says he says our Prime Directive as developers, is to write the most

humanly readable code possible.

Because it doesn't matter how smart you are, the compiler is going to be smarter,

and it will make the compiled code

even better. So the only person that really matters when you're writing code, the authorship, the readership of your code is people if people can't read it, you've done a bad job.

#### Layla

Yeah, that's so true. So true, especially when you're looking at nested ternary.

#### Jamie

Because it's not going to be a computer, the debugger is going to be a human. So humans got to be able to read it. And, yes, you may want to show off how smart you are by doing 15 layers of nested please don't ever do 15 layers of nested ternary. But you may want to show off just how smart you are to be able to combine all of these if statements and switch statements into a 15 layer ternary. But in 25 minutes, when you come to debug it, you aren't going to be able to make head nor tail of this.

It's that simple.

#### Layla

I do feel quite clever. When I do some slightly complicated link, though, from memory. I feel I feel like a real developer. I you can get really stupid with link and and make them really deep. But yeah, I there's been somewhere I'm like, Oh, yeah, that's a really nice, tight query, and still readable? Because that's key, as you say, and I do feel like a proper developer, then when I can do that from memory.

#### Jamie

Because that's the other thing as well, if you've got a big ternary, or maybe 25 link statements all chained together.

That's not testable at all.

Or like I said, debuggable Yeah,

#### Layla

yeah. I mean, you can't stick anything that's got an extension method on as you make it harder and harder for yourself. And and then you have to start trusting, you know, you will, you need to be testing extension methods, or it just gets more and more complicated. And it goes back to that single responsibility principle as well, you want things to only have responsibility for a single piece of that functionality. And, and, you know, with some leeway there as well, but you don't want if you've got 25 nested I'm getting big enough, a ternary of 25 nested ternary is, and well, that's a lot of different things happening. That's a lot of code, potential code exits as well. And so where are you going to test? Where do you know, when that fails? How do you know what parts of the test is failing? what's responsible for that test? And that's one of the big reasons why we use dependency injection. Because we don't want to worry about is it when we need it up to that? Did we not give it everything we needed? Was that issue in the class that we need up somehow? We don't know. And that's why we come to use dependency injection. And a lot of people say why you shouldn't use dependency injection, but we're extracting that dependency out to make things more testable, and just loosely coupled, so we can change things without worrying about other bits of code.

#### Jamie

Absolutely. Absolutely. I completely agree with you there. So as we're coming up to about an hour, I don't really want to keep your day. Just because you're a busy person. I'm a busy person. And you know the lesson there's won't be like another four hours of TDD, this is not going to work. So So what would be your top resources for learning TDD the layaway because we I only say that because you said earlier on the videos didn't work for you tutorials didn't work for you. But sitting down with someone did is that is that the way that you would recommend people go?

#### Layla

Say, I would say, start by watching online resources and reading books. If that works for you. You're laughing that's great. If it's still not clear, and even if it is clear, build your own little mini projects like I did with the Terminator come up with an analogy that works for you. Something that you can break down into small, actionable requirements units of work. And you can want to go and have a look and go, what's the unit of work? Okay? Should that be true or false? Stick it stick with it something really simple. This will either return true or false. And just write a little statement. Does this person like pie? And it's going to be a yes no answer. So your tests will go if they say yes, return true, you know, something really simple. And just build up from there and get more complex and then start to look at how you can bring in patterns, but just get that basic mechanic. And I think there's nothing like playing with the code yourself, to get to get the basics of it, and that rudimentary understanding. Once you've got that understanding, and you're ready to progress, then there's nothing like pair programming with someone who's experienced. And just to see how they approach problems. A large part of coding is about problem solving. Not about coding, not about patterns. It's about problem solving. And learning how other developers approach problems and solve them is what makes us all better developers. So that would be my bit of advice on TDD. understanding and learning.

#### Jamie

Okay, excellent. So what about learning about some of the work that you're doing learning about MK dotnet, learning about the workshops that you're putting on the twitch channel? Where can people go to find all of that information?

#### Layla

I guess, on Twitter, I'm hoping that you'll share some links for me, Jamie. So I'm on most things as Layla codes that, say I'm on Twitch and Twitter is Lila codes. The Mk dotnet is on meetup.com. So you can find us on there. And we don't have the domain nk dotnet. That would have been cool. If you do go MK dotnet. I think that's an A user group in Eastern Europe somewhere, like Macedonia or something. And we've we've had chats with them, because we're always getting confused. So yeah, not them. And if you want to learn more about Twilio, I'm very open to talking about it, you can contact me on Twitter, as I said it locates it, or you can email me, which is L porter@twilio.com. And I'm very happy to help people. Whether that's Twilio related or just general coding related as well, I'm always open to help.

#### Jamie

Excellent. Okay. So as the as we're recording this in August, I want to say August 18. Again, the days don't read, therefore fused into one, right? August 18. What's the use of everyone what the workshop name is? But does it have a website or is it just doesn't work and people go somewhere to sign up for see

#### Layla

on 28. And I can give you the link for it. It's and it will go on to YouTube in time, it's completely free. And you just sign up to gain access. It's about four and a half hours of video. And it's the first time I've done this. If you watch it, and you're like, wow, if Layla had done it like this, that would have been amazing. Tell me Be kind. But I would love feedback on how I can improve workshops in the future. And there is a link on my Twitter to it as I talk about it often on Twitch. So if you'd like Laila, what was that workshop, you can come and ask me and I will gladly point you towards that. And so yeah, that's it can be found in places.

#### Jamie

Excellent. Okay. Do you have a regular schedule for when you're streaming on Twitch? I know some people do. Some people don't.

#### Layla

Yes, I stream on Monday afternoons at 330. UK time, whatever that's that I that might be VST or GMT. And I, I have a past stream. On Tuesday evenings, we'll be looking at different things that's on silicon orchids channel. And then I stream on my channel so on Thursdays from TPM, and Fridays from fluff tea. I also did another case stream that's sporadic, which is more on the culture of code. So we that's also on YouTube. And that's with my fellow streamer white Panther. And, and we talk about things outside of code. So our most recent episodes were on project planning and the problem with half baked solutions. So that's on our YouTube channel, which is code cake TV. And you can find out that so that might be really interesting in relation to getting acceptance criteria and better solutioning. Say, Salma, who is AK white Panther and I do that show sporadically as well. So yeah, there's quite regularly on Twitch.

#### Jamie

Excellent. Okay. I do like being able to discuss coding topics regardless of the language with people. I mean, obviously this is the Donegal podcast but being able to say hey, Forget the language I'm using. How would you go about solving this either business problem or requirements gathering problem? I tend, I worry that, that saying soft skills is going to upset some people or turn them off because they're not soft. It's hard to do. And it's, it's more related skills,

right?

#### Layla

It's totally integral to problem solving, which, as I said, is the fundamentals of software development. Salma is a technical lead, and a front end developer. So we have different approaches to things. But it's great to team up with her. And we can bounce ideas off each other. So that's really interesting, because we come from two different complete backgrounds, from different stacks, different ways of approaching things that were united over problem solving.

#### Jamie

Excellent. Well, I'll definitely be checking it out. Because I feel like I could always do with leveling up in that in that arena anyway. And I think almost everyone can and getting the advice and experience from someone else. Again, it's that mentorship idea, right? That even if even if I'm not gonna say it's about this conversation, because this conversation have been amazing, but if you're chatting with someone for an hour and a half, and you get one nugget information out of that interaction, then that was aside from getting to know someone for an hour and a half, that one nugget of information was totally worth that hour and a half conversation, right? Because you can then take that and go, that's what I need to Google to find out a little bit more, but name of the thing that someone said, and then that's it, you're set on this path of, of improving yourself and getting better and that wonderful journey that follows from it.

#### Layla

Yeah, I couldn't agree more.

#### Jamie

Excellent. Well, those are all the questions and topics that I kind of wanted to try and cover with you today, Elena, and you've done a wonderful job you've been, you've been more detailed than than I could have ever been about TVD. So thank you ever so much for that. So yeah, thank you so much for being on the show.

#### Layla

Thank you so much for inviting me. I've had a lovely, lovely time chatting to Jamie. See Thank you. Thank you.

{{< paracentre "The above is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

### Wrapping Up

That was my interview with Layla Porter about Test-driven Development. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/), and there will be a link directly to them in your podcatcher.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice - head over to [dotnetcore.show/subscribe](/subscribe) for ways to do that - and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Layla on Twitter](https://twitter.com/LaylaCodesIt)
- [Layla Porter on Twitch](https://www.twitch.tv/laylacodesit)
  - [SiliconOrchid on Twitch](https://twitch.tv/siliconorchid)
  - [whitep4nth3r on Twitch](https://twitch.tv/whitep4nth3r)
- [CodeCakeTV on YouTube](https://www.youtube.com/channel/UCZoVfq1goxSv63E3jFGHgTw)
- [Twilio on Twitter](https://twitter.com/twilio)
- [MK.NET](https://www.meetup.com/Milton-Keynes-NET-Meetup-Group/)
- [Building with ASP.NET Core and Twilio](https://ahoy.twilio.com/Cloud-City-Cake-Series)
