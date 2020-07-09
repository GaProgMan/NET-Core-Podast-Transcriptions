# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is episode 37: Rebus with Mogens Heller Grabe. In this episode I interviewed Mogens about Rebus and how it can help with asynchony in your applications. Some of you may know Mogens from his work on Rebus, his [blog](https://mookid.dk/), or his brewing company - [The Alley Beer Company](https://alleybeer.dk/) - .

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Mogens's Introduction

**Jamie**

So thank you very much Mogens for being on the, er Mogens. Sorry. Let me start that again. I got it wrong straightaway, didn't I?

**Mogens**

No, no, it was good. It was good. It's Mogens.

**Jamie**

Fair enough. I might leave this bit in.

So yes. Thank you ever so much Mogens, for being on the podcast. I appreciate it's a, you're a very busy person. I mean, we'll come on to just how many things you're currently doing in a moment. But I thought, just for the people who are listening in who may not know about you all the work that you do, I was wondering could you give us a sort of brief introduction

**Mogens**

An introduction to the work that I do?

**Jamie**

Yeah, sort of like an introduction to you and sort of the work that you do that kind of thing.

**Mogens**

Yeah. My name is Mogens and I'm, I'm working as a programmer. I've been doing that for 13 years now. I think and the last three years I've been self employed business. Basically trying to build a company around an open source service bus that I made. And for people who might be familiar with , for example, in service bus or mass transit, then that's the kind of service bus that I made. Mine is called the Rebus.

In addition to that, I brew beer, and I actually have registered a company to do that. But it's kind of on a hobby basis still, so it's gone really, really slowly with, like, getting anywhere with the beer thing. Yeah. So I guess that that's the work that I do.

**Jamie**

Cool. Excellent. Um, so yeah, you just said that you brew your own beer and you've registered your own Brewing Company.

**Mogens**

Yeah.

**Jamie**

How did that come about? Are you just a big fan of beer or?

**Mogens**

Yeah, I can't deny that.

I'm really interested in beer and I used to work with a guy who was a brewer too. And he introduced me to brewing. And he made me sign up for a short series of lectures that would like introduce you to beer chemistry - there's a lot of chemistry involved. And it really like I suddenly could see like a use for all of the chemistry lessons that I had in the secondary school. So suddenly, all of these things could be put to use and it all made sense. And the end result is beer. So what's not to like about that? So it basically just, yeah, I just went on from there. But I had kind of a kind of a rough start with my brewing career because I basically learned too much too fast. So I just constantly like pushed actually starting brewing, because I could not just buy a starter kit, because I knew that then, "this and this would be wrong." And so I basically started out like buying everything. So I had to buy off kind of measurement devices for measuring sugar concentration in the water and the PH metre. And yeah, basically all the stuff that you need to brew really good beer. And then I just sort of dove into trying to make use of that. And I'm still learning. So I don't think I can brew really good beer yet. But I also think I'm being pretty critical of my own results, because people actually like the beer that I brew.

**Jamie**

I see I see. So maybe what we can do is we can get everyone who listens to the show who's interested in beer to place an order.

**Mogens**

Oh, yeah. Oh, yeah, that would be cool. But unfortunately, I cannot sell the beer that I produce right now because I'm not I'm not approved for you know, selling foodstuffs. You have to make your, like produce your foodstuffs, and then in an approved facility to do that. So my plan is to at some point, when I have a recipe that I really believe in, then I can rent myself into a professional facility, and then, you know, rent the facility and produce a batch and maybe like end up with a couple of hundred litres of really good beer. And then I can try and sell it.

**Jamie**

The sounds really good. So is this a, is this going to be a side project alongside of Rebus? Or is this a retirement plan?

**Mogens**

It is as a side project. It's very much a side project, and I don't spend that much time doing it. But I don't know. Let's see. Maybe it's a retirement plan. I don't know.

**Jamie**

I like that. I do know that there are a number of developers that I spend a lot of time talking with about our side projects, you know, for learning new techniques and new tools and new frameworks and sometimes new languages. But I don't think I've met many developers who take their side projects outside of development, which is I think it can be quite good. Because, you know, you're applying, perhaps you're applying the same sort of design methodologies, you know, and stuff, but it's taking it in a different direction so that you can improve in that area. So one of the things that I do is I sometimes play bass guitar, and obviously, I take an agile-like technique to learning songs and learning pieces and learning music. In that I don't have to worry about all of the minutiae of what I'm doing. Just get the the basic form, right.

**Mogens**

Yeah.

**Jamie**

And I'll go back and you know, improve upon that. Yeah, revisit.

**Mogens**

Yeah, exactly. Yeah, you're absolutely right. And I think it is, [to] brew beer, lot of a lot of his craft craftsmanship and it's like in the hands, but also a lot of It's like being able to like reflect over your results and having like an engineering like approach to it, where you somehow systematically like focus on an area, and then you change the variable. And then you evaluate your output, basically. So it is a lot of it is also engineering, at least in my head.

**Jamie**

So, do you have a name for the brew that you're brewing yet? Or is that still a trade secret?

**Mogens**

My company is called [The Alley Beer Company](https://alleybeer.dk/). And that's because my office is in like a shared office space that is called Le 87. So I basically just took my name after our office space here.

**Jamie**

So you've stolen the name because naming things is hard, right?

**Mogens**

Yeah.

### What Is a Service Bus?

**Jamie**

You mentioned earlier on about Rebus, and you said this a little bit like a service bus.

**Mogens**

Yes.

**Jamie**

I was wondering, could you tell us a little bit about Rebus and what it's aiming to solve? And maybe a little bit about what a service bus is?

**Mogens**

Yeah, sure. Well, when people say service bus, people have like very different, I guess, perceptions of what a service bus does and should do. This type of service bus is what [ThoughtWorks in 2010, I think described as "a message bus without smarts"](https://www.thoughtworks.com/radar/tools/message-buses-without-smarts). And Sam Newman in his recent [microservices book](https://samnewman.io/books/monolith-to-microservices/), he called it "smart endpoints dumb pipes." So the service bus in this case would be the pipes, the dumb pipes. So the point is that it's a kind of a piece of infrastructure that doesn't try to solve all of your problems, but then it it just solves some well defined problems in a good way. And then if you want to integrate with some particular system or something like that, then that's the smarts that you have to implement. I don't know if that makes make sense.

**Jamie**

Yeah no, that makes perfect sense. I'm seeing it more of like a framework that allows you to implement some things. It will do the sort of transportation of messages around, but it won't do any translation of those messages. You're literally saying, "Take this message and take it over there." And then it will come back and say, "Yeah, I delivered that." And then, "Okay, now take this message and deliver it over there." It's almost like a, what's the analogy, I guess, kind of like the postal system, like, the person who delivers the mail, doesn't need to figure out how to use your door and doesn't need to figure out how to sort of read the letter to you. They are given a letter, they drive to your house. 

**Mogens**

Yeah

**Jamie**

They give you the letter, and then they drive back to the sort of post office.

**Mogens**

Exactly. That's a really good analogy. I'm probably going to steal at least do this.

**Jamie**

Please do, please do.

**Mogens**

And then the fact that you have a mailbox. I mean, you have this interface., that is like the mail system and the mailman and the mailbox, that's, that's kind of the infrastructure. But then what happens behind the mailbox. That's, that's all the smarts that is still up to you.

So another way I can explain what it does is I can, I can go back to one of the first, like really frustrating problems that I experienced as a professional software developer. I was a developer on a mortgage deed administration system. And one of the things that we needed to do the system was to handle a web request. And then inside the handling of this web request, we had to update a fairly complex domain model in a database - we used [NHibernate](https://nhibernate.info/) for that. And then send some, generate some prints and send them to the printer. And the only way we knew to do that would be to like open a database transaction, and do all of the stuff that we need to do in the database. And then send all this stuff to the printer, generate the documents using Office interrupt inside the web requests - which is all kinds of unmanaged stuff with memory leaks and everything that we would do in inside the web request inside the database transaction - and then commit the transaction.

And this would sometimes fail, and it would end up in. I mean, we didn't know any better way to to solve this, this problem, which is actually it can be considered a situation where we have two transactions. In this case, one transaction would be a database transaction and the other one would, some kind of yeah, using this office interrupt library and sending stuff to the printer. We didn't know how to have two transactions and have them like complete and be committed at the same time are not be committed at all. So we couldn't have like a unit of work that would reliably spend all of this work.

A better way to solve this problem would be to use some kind of messaging. And then, inside this web request, we would send two messages, we could send like a message that would perform the modifications in the in the domain model and the database. And then we could send a message that would generate the prints and send it to the printer. And then these could fail or be completed individually, instead of trying to do all of this stuff at the same time.

**Jamie**

Sure, yeah. So let's say you sent a message through the previous system, the database transaction for creating the documents, creating the print job fails, you can't be sure that it ever gets to, you will never get to the printer and it may leave a transaction open.

**Mogens**

Yeah.

**Jamie**

And then you said another transaction. Because the first one is still open, you can't access potentially the same tables. You might be able to generate the documents, but you can't send it to print because there's no way to write that to the table to say, "hey, this job has been done."

**Mogens**

Yeah.

**Jamie**

So that's what service busses are. So is there anything specific about Rebus and its implementation of a service bus? Like, I don't want to make it sound like this. But what's so great about Rebus? And what's, you know, how's it different to other service bus implementations?

**Mogens**

I think it's, it's different because my initial starting point was that I used [NServiceBus](https://particular.net/nservicebus) and I was really happy about it in some ways. And in other ways, I wasn't that happy about it.

For example, NServiceBus didn't have good error messages. So it would like just throw null reference exceptions sometimes when you try to start it up. I thought that was really frustrating. So one of the initial goals for Rebus was to have like really exceptional error messages, like all of my error messages. I decided should follow this pattern of both explaining what was wrong, but also suggesting a path forward so that experiencing an error with Rebus would not be a slap in the face, it would always be also a step forward in some way.

An example of that is if you try to start Rebus up, and you try to configure encryption, but you don't provide valid encryption key, then it will automatically generate one for you and suggest, "here, I generated this key for you try and use that," small stuff like that. So, like being really pleasant to use, I guess that's how I think Rebus differs from the other service buses around.

**Jamie**

That's, that's fantastic. I always like when you know when I get something wrong, or I get a compiler error or runtime error. You know, like you say it's a slap in the face.

**Mogens**

Yeah

**Jamie**

You know, because you may be elbow deep and then debugging knowledge going, "Yes, I can get this. I can do this, I'm checking this, I'm running this test," and then all of a sudden: wham! It fails. You know, you left questioning yourself, you left questioning your life choices. Maybe that's just me. I don't know.

**Mogens**

No, it's not just you.

**Jamie**

But having the system be able to tell you, "hey, this went wrong. And here's why. And this is potentially what you can do to fix it." I feel like that was greatly speed of development time and make it a much better experience.

**Mogens**

Yeah

Okay. I feel like more frameworks, tools and languages and stuff like that should do things like that, because let's take a runtime error, null ref. runtime error. What am I supposed to do with that? You know, yeah.

But But I think just to be fair to NServiceBus, I think they have made an effort in this particular area. And I think it's, it's pretty much following the same pattern now, where they also suggest solutions to whatever problem it encounters. So they have probably improved a lot in that regard,

**Jamie**

Probably by using Rebus.

**Mogens**

Yeah, yeah.

**Jamie**

So you mentioned that it's, it's open source.

**Mogens**

Yeah.

**Jamie**

But you're making a business out of it. So I'm always interested to find out how different open source companies, what their business model is, you know, we recently had - so at the time of recording, it's not going to add yet - we recently interviewed someone who has an open source library that you can use in development for free, but you have to pay for a licence to use it in production. Is that how this works? Or is it more the sort of the Linux distribution model where you can use it for free, we have to pay for support, you know, what am I looking at if I'm building a production system?

**Mogens**

Much more like the second model you described.

**Jamie**

Okay.

**Mogens**

I like to think of [MongoDB](https://www.mongodb.com/) which is a free database, free document oriented database that you can use. And you can pretty much use it for anything. Although I think they actually made a small change recently where you cannot set yourself up to be a commercial MongoDB hosting provider using MongoDB unless you pay them.

But MongoDB is just a really, really good document oriented database that has become better and better. Even the free version has like had features added to it. And it's just become better over time. But then they have this company where if you want training, or if you want the support agreement, or if you want additional monitoring tools, then you have to pay for it. So that's the model I'm trying to follow everything in Rebus and all of the integration libraries is MIT licenced, and completely free to use. And the thing I want to make money of is then to sell support and some additional tooling in the form of what I call Fleet Manager. Fleet Manager is, obviously if you have many buses, then you have a fleet. So Fleet Manger is the tool that makes it easy to manage your your fleet of buses. So that's that's the model, everything in Rebus is free. But if you want Fleet Manager and support, then you can subscribe to that.

**Jamie**

So I guess if the error messages that user friendly

**Mogens**

Yeah.

**Jamie**

Would I even need the support?

**Mogens**

Yeah, that's a it's a good question. And maybe I'm naïve. I've always had this belief that I should just make Rebus as good as I as I could. And then I don't know if I, maybe I'm naïve, but I just believe that if I make Rebus really, really good, then everything will end up in a way where I can make a business out of it.

So I had this picture of my pipeline, which is I have to make Rebus really good. Make many companies use Rebus. And then I will probably not hear from them for a couple of years, because they will just build stuff using Rebus and have fun doing that. But then at some point, they will want to, like, ask for some advice for some concrete problems that they have on they want they need this tooling to monitor their, at the at that point pretty large Rebus installation and see that what it's doing and help them manage failed messages and stuff like that. And then they come to me. So that's what I what I hope will happen.

**Jamie**

Sure. I mean, it makes perfect sense. Having worked in development teams for very large businesses. I know that in some places, you're not allowed to use a library unless it comes with some kind of support agreement.

**Mogens**

Yeah

**Jamie**

So I think you're targeting the right end of the spectrum there so that an individual developer like me, who wants to be try out a message bus and try out the different alternatives can try Rebus and build something with it. Yeah. But then when I take it to the client and say, "Look, we're going to invest in this. And we're going to build something with this technology, you don't need to know about it. But we're telling you so that if anything goes wrong, you can contact these particular people, and they will help you out with, you know, support requests and stuff like that." I think that's a good idea.

**Mogens**

Yeah.

### Do You Have Any Real World Examples?

**Jamie**

So do you have any examples of where I would use Rebus in a project? You know, we talked a little earlier, we use the analogy of like a sort of a mailman, a post delivery person who takes a you know, a letter or package and puts it into your mailbox, and then you have to go to your mailbox and figure out what you're going to do with it. But, you know, that's pretty good for analogies but other any, you know, real world systems that you know of that I've used it or any example systems you've built that have used it?

**Mogens**

Yeah. And I've built a couple of things myself. The first two things that I heard of that Rebus was used for was actually before I even started using it for something myself was to control a power plant - a little power plant that had this, I don't understand this domain completely, but I think they have these plans for how this power plants should produce its power. And then they used to Rebus to coordinate that. And that was something with like communicating with some price prognosis. And so apparently, they built this system that would use Rebus to coordinate that. And another thing was, there was a company in, you know, who's that use Rebus for automating some kind of payment flow in their system.

They're probably both really good examples of backend stuff happening in systems that needs to be carried out in a reliable fashion. So I guess whenever you need some kind of asynchronous thing going on in a reliable fashion, possibly involving multiple steps, then reliable messaging, using durable message queues is a really good, really good solution.

**Jamie**

So I guess then, I mean, we're on the .NET Core Podcast. So this Rebus is .NET Core compatible? Is it done .NET Standard? Is it just is there a binary for Core, for Framework, for whatever? Or is it just a standard library? How does that sort of work?

**Mogens**

The Rebus core library is, is targeting .NET 4.5, .NET 4.6, and the .NET Standard 2.0. And the reason it targets both the .NET 4.5 and  .NET 4.6 is because some people are still using .NET 4.5. But .NET 4.5 does not have async local. I don't know if you're familiar with that. So it uses a logical data slot on the thread to store some thread static like things. But yeah, so I guess it's available on on all relevant .NET platforms.

**Jamie**

Okay, so I could I could create a Xamarin app or a Unity game that uses Rebus to do some stuff, I guess?

**Mogens**

Yeah, you could do that. But I guess if you build something with Xamarin, or Unity, it would probably be more like a front end kind of thing you would be building, wouldn't it?

**Jamie**

Sure. Yeah. I guess. Yeah. Yeah, that makes sense.

**Mogens**

And then that's actually one thing that I sometimes hear of people that want to use Rebus as a sort of, like in a situation where you would otherwise have used HTTP. For example, to have Like many clients that contact some kind of back end. So for example, if you want if you if you have a Windows Forms app that needs to communicate with a server somewhere, I would not suggest that you use Rebus for that, I would suggest that you use a synchronous remote procedure like protocol, for example, implemented using HTTP.

**Jamie**

Sure that makes sense. You don't want your form sitting around waiting for Rebus to be able to handle the message and then send the response back.

**Mogens**

No, and and also it's not asynchronous, like truly asynchronous communication is not that well suited for a situation where you have a front end that actually needs to reply as fast as possible. And also, if the Windows Forms app dies in the middle of after having send a request and not having received a reply, then the reply has no value.

**Jamie**

That's true.

**Mogens**

It doesn't make sense to deliver a reply when the application, it probably doesn't makes sense if, when the application starts up, and it gets a reply to a request that it sent before it dies. Because that's how miscues work. And yeah, so in that way Rebus would not, it's not a really good client server communication library. It's more meant as a sort of a server server. Communication library.

**Jamie**

Sure. Okay.

The way I'm thinking about is it's more for, we talked about earlier I guess, it's more for transactions of data rather than send a request, get a response. I want to tell another service to go do something.

**Mogens**

Yeah.

**Jamie**

And then when it has finished, it will tell me that is done something. So like, I mean I use the word transactions, but I know that at least in the UK, the majority of non business banking transactions - so you go to the ATM, you take some money out, that doesn't actually leave your account until the overnight periods. So like midnight, one bank will send a massive transaction, or a series of transactions to another bank to update all of their records. So let's see you bank with Foo Bank Limited, and I bank with Bar Bank Limited: two completely different companies. But I send you some money, I know that that transaction will go through overnight. So maybe Rebus or a service bus like system would be better for sending that transaction over because you need to get a response. And I suppose it doesn't really matter when that response comes through.

**Mogens**

Yeah.

**Jamie**

Whereas if the ATMs were connected to the Rebus, I would have to put my pin in, push the button to take some money out and have to wait for you know, the message to go to the service bus, go to Rebus and sit there waiting for Rebus to be able to process it.

**Mogens**

Yeah.

**Jamie**

Rebus then goes, "brilliant. I've cleared my queue is this message, send it over to the bank and I will wait," and then the message comes back it goes on to as maybe a return queue or something, and then it has to sit and wait for a time slot to be able to send it back to the ATM. And then eventually I get my money, but that may take minutes.

Whereas an ATM, you push the button, you type some numbers in, you get some money out, and the money comes out instantly - as long as you have, you know, a positive balance - itcomes out instantly. And then eventually that transaction is sort of like, is the eventual consistency that that transaction is eventually written back to the database.

**Mogens**

Yeah.

**Jamie**

Whereas, you know, I guess yeah, you wouldn't want that for a, like you were saying like a real time operation an ATM or a Windows forms app or maybe an app on your phone or something, you don't want to sit and wait for potentially minutes for that transaction to go through.

**Mogens**

Yeah, exactly.

So you know, I mean, many systems have this, this requirement, I mean, whenever you you have a requirement that can be formulated like whenever this happens, and this should also happen like when, when I process an order, then I also want an email to be send, and I want some items to be allocated from the inventory or, "whenever this happens, then this should also happen." That would probably be a situation where you could use messaging and decoupled the steps of the entire workflow, the entire process that is going to be carried out here, and then process these steps as individual transactions where a message is, represents whatever is going to happen in that transaction.

### Do I Have To Use Microservices?

**Jamie**

So a lot of the talks that I've been to recently regarding service buses and Service Bus architecture and message buses, they've been specifically about micro services. So do I need to have a microservices architecture to be able to make use of Rebus or can I have a monolith that sends a message that is wrapped in a generic format to Rebus, Rebus then forwards that to another monolith, the monolith does the whatever it needs to do with that message, and then sends a response back? Or do I literally need to split my system into hundreds of different micro services in order to talk to Rebus?

**Mogens**

You do not need to split your system into 100 tiny bits to use Rebus. In fact, I advise you to not do that.

A problem I often see people solve using Rebus, a sort of the first problem they solve using a message bus, is whenever they need to send an email from their application. That's a really simple scenario where an application just wants to send an email in a reliable fashion. But the communicating with an SMTP server from a web request handler can be kind of icky. And I know you can then maybe have an IIS with an email pickup directory or something like that to make it more reliable, but maybe you want to send your emails using SendGrid or whatever. And then people would just introduce a small Windows Service that would have a Rebus instance inside it and would start up and have an input queue. And they could call this their mail service or something like that. And then whenever they want to send an email, they just send a message to the mail service. And then that one will take care of actually sending the email.

So if for example, they're using their local exchange server to send the emails and the exchange server is down, because sometimes it's down. Yeah, then it will actually because they're using Rebus it will try five times by default to send this email and then if it still fails, it will move the message to the "dead letter" queue; by default, Rebus will create a queue called "error" to which it will move messages that cannot be processed. So that way, if the sending of the email keeps failing, it will move the message to the error queue. And the information will not be lost in any way. And the message can be moved back later on when they have solved their problems with their Exchange Server. So that's a that's really nice and simple scenario that yields a clear improvement of the reliability of their system.

**Jamie**

So I'm thinking if I take that example a little bit further and make it slightly more concrete. So let's say I have an ASP. NET Core system, I have a website or a service that you can sign up for that has authentication on there, and I require you to verify your email address. And as part of the signup process, you put in all of your details, and then the system will send you an email with a link you have to click to verify your email address.

**Mogens**

Yeah

**Jamie**

I don't want my HTTP controller to be sitting spinning waiting for a confirmation message from the email service that I'm using to say, "yes, that emails been sent," do I? I want my, "data is validated." And then a message is sent to a message queue or a message bus, some kind of messaging system that will say, "forward this detail, this email message, on to the email provider who will do whatever they need to do with it." And then eventually, that email will be delivered to the customer, to the client to whoever it is that we're signing up. Because I want to be able to display that, "you should receive an email," message instantly versus sitting and waiting for anything between my app and the email system, the email server could hold that message up. So I want to be able to display to the user as quickly as possible, "check your emails. In the next couple of minutes, you receive a message that says 'click this link'", so I want to display that quickly as possible without having to wait for the email service to tell me that it has been sent. Because presumably, they may have a message bus their end for sending the messages out. Because you know, you can't send 5000 messages all at once because SMTP servers don't like that.

**Mogens**

Yeah,

**Jamie**

That's a good. It's a bit of a rambling example, but I think he got the point.

**Mogens**

Yeah.

### Resources on Rebus and Contacting Mogens

**Jamie**

So where can people go to learn more about Rebus then, is there a website? Is there a forum? Is it a YouTube channel? What do we do? If you want to learn more about Rebus?

**Mogens**

A good starting point would be to look up the project on GitHub. I have created an [organisation on GitHub](https://github.com/rebus-org) for all of the open source Rebus bits and some more stuff that they may or may not be be relevant to people building systems using rebus. And the Rebus Core project has a [wiki](https://github.com/rebus-org/Rebus/wiki) on it that documents a lot of stuff, on Rebus. So that's a good starting point.

Another way would be to sign up to the mailing list. I have a [weekly Rebus tips mailing list](https://rebus.fm/2019/01/16/we-have-a-mailing-list/), there's a link on my [Rebus.fm](https://rebus.fm) is my company website. But it's it's not commercial tips in any way. It's basically just little weekly nuggets with tips on on how readers can be used and different accessibility mechanisms can be produced and stuff like that. So that's also a good way.

And then I'm actually a little bit unsure if I should mention this because I'm not writing as quickly as I really wanted to, but I'm actually in the process right now of writing a book, "The Little Messaging Book" but things are not going as quickly as I really wish they were. But I at some point, there will be a book, which I will publish for free. It will be on [thelittlemessagingbook.net](https://thelittlemessagingbook.net/). I already purchased the website. So I guess I'll also that would be a good a good way to learn Rebus. But unfortunately, I haven't published anything yet.

**Jamie**

So there's a bit of a queue, shall we say, of podcast episodes before this one. So it will be, you know, two or three months I guess before this one comes out. I also produce two podcasts, two separate, completely unrelated shows. So being able to edit two completely different shows. And one of them we record three and a half hours of audio each time. So that takes a while to get through.

**Mogens**

Yeah, I can imagine. Wow.

**Jamie**

So we talked about the website is there a lot of documentation on examples. So like, if I want to implement Rebus in a .NET stack that I have, can I go to the website and read up how to do that? Or is that something that I kind of have to figure out by myself?

**Mogens**

On the wiki, I have a couple of scenarios where I kind of described like, some typical business scenarios that I have encountered. And then you can see how they can be solved using Rebus. I think the scenarios are, I can't remember exactly what the two first are about. I think one of them is is about how to de-couple, how to use [publish-subscribe](https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern) in Rebus, basically. So the scenario is you have an application and it wants to provide information to the world about the work that is doing. And a good way to do that would be to use publish subscribe with Rebus. So whenever this thing does something, it will then publish a message saying, "I did this." That would enable whoever might be interested in hearing about that to subscribe to the relevant events. So, that would be one scenario.

I have another scenario that is pretty interesting and that is a scenario that is using Rebus' [Process Manager](https://en.wikipedia.org/wiki/Process_management_(computing)) implementation. You know, Rebus is, is an implementation of some officially described messaging patterns. And one of these patterns is the Process Manager. You can think of it as a state machine that is running on whose transitions are defined by messages. And you can have multiple instances of the state machine. So, the state machine can implement some kind of messaging workflow of some kind. And the scenario described here is, I think is that I have a trade that happens in our trading system. And then whenever I get a new trade I need to have this trade approved both by legal department, and by credit assessment department before I do something to it. I don't know if I remember this completely correct. But the point is that there is an example that describes how Rebus can be used to solve that problem of having individual flows for each trade, and then carrying out a, some asynchronous processes with multiple systems, and then have that. Yeah, have that handled that way. And that's on the wiki. Yeah.

**Jamie**

Fantastic. Okay, so that's all documented and so if somebody wants to go away and learn how to use Rebus, they can go and check out the wiki, and, "this is how I'd implement this." And then they can get some ideas about implemented in their own system.

**Mogens**

Yeah. And then there is also a [Rebus samples repository on GitHub](https://github.com/rebus-org/RebusSamples), with just plain code examples that use different things. It's called Rebus Samples.

**Jamie**

Brilliant. Okay, so what if I, in the unlikely event if I'm using Rebus I spot something that a bug or have an issue with it. If I raise that on GitHub, is that a good way to get in contact with you to say, "Hey, this is this is something that I've spotted. That's not brilliant in my use case."

**Mogens**

Yeah, raise issue and GitHub, or if you have a question, you can ask it on GitHub or in Stack Overflow. And if you [tag it appropriately on Stack Overflow](https://stackoverflow.com/questions/tagged/rebus), then I will notice, and I will probably answer your question.

**Jamie**

Okay.

**Mogens**

Or someone else will.

**Jamie**

So let's say I find a bug. And I go, "I can fix this." And I submit a pull request, do you accept pull requests as well?

**Mogens**

Yeah, I love pull requests.

I mean, I should also mention this, I mean, Rebus consists of a core project and I think 30 or 40, or maybe 50 projects in addition to that. So because this is much, much bigger than I would have been able to make it myself.

**Jamie**

Sure.

**Mogens**

So the only way it can become this big is by accepting contributions from people. So in addition to me, I think, I think almost 100 people have contributed to Rebus. So it is like, much bigger than then I would have been able to make it.

**Jamie**

Wow.

**Mogens**

So yeah, pull requests are most welcome.

**Jamie**

That's a lot of people working on this. I like that. Where can the listeners go to learn more about yourself? And so we've talked about Rebus, can folks, is there a, do you run a blog? Can folks reach you or reach out to you over Twitter? That kind of thing, is there a way for folks to connect with you? Is that something you you you know, you are interested in you allow?

**Mogens**

Yeah, sure. My Twitter handle is [mookid8000](https://twitter.com/mookid8000). Mookid is from an Aphex Twin song.

**Jamie**

Okay.

**Mogens**

I used to listen to electronic music a lot. But yeah, my handle is mookid8000 pretty much anywhere so on GitHub and on Twitter. That's where I can be found. Yeah, people have something to say, then please get in touch.

**Jamie**

Fantastic. Well, that's all the questions I have for you today all the topics that I wanted to cover, I guess. The only thing left for me to do, I guess, is to thank you ever so much for being on the podcast. Mogens, I appreciate that you're a busy person. We're all pretty busy these days. But you know, taking the time out - because we're in separate time zones as well. So taking the time out, during what is your, I guess, coming up to mid morning and my early morning, I really appreciate it.

**Mogens**

Oh, thank you for having me. It's been a real nice experience to be in your podcast.

**Jamie**

Thank you ever so much. We'll see if we can get as many listeners as possible to check out Rebus and maybe to do some google-Binging for your your Brewing Company and maybe we can get loads of orders in. I don't know.

**Mogens**

Yeah, that would be cool.

**Jamie**

Like I say, Thank you ever so much for being on the podcast Mogens. It's been a wonderful experience talking with you today about about Rebus

**Mogens**

Yeah. Thanks

### Wrapping Up

That was my interview with Mogens Heller Grabe of Rebus. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/) and there will be a link directly to them in your podcatcher.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Mogens twitter](https://twitter.com/mookid8000)
- [Mogens' blog](https://mookid.dk/)
- [The Alley Beer Company](https://alleybeer.dk/)
- [A message bus without smarts"](https://www.thoughtworks.com/radar/tools/message-buses-without-smarts) from ThoughtWorks
- [Sam Newman's Monolith to Microservices](https://samnewman.io/books/monolith-to-microservices/)
- [NHibernate](https://nhibernate.info/)
- [NServiceBus](https://particular.net/nservicebus)
- [MongoDB](https://www.mongodb.com/)
- [The Rebus organisation](https://github.com/rebus-org) on GitHub
- [Rebus wiki](https://github.com/rebus-org/Rebus/wiki)
- [Weekly Rebus tips mailing list](https://rebus.fm/2019/01/16/we-have-a-mailing-list/)
- [thelittlemessagingbook.net](https://thelittlemessagingbook.net/)
- [publish-subscribe](https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern)
- [Process Manager](https://en.wikipedia.org/wiki/Process_management_(computing))
- [Rebus samples repository](https://github.com/rebus-org/RebusSamples)  on GitHub
- [Rebus on Stack Overflow](https://stackoverflow.com/questions/tagged/rebus)
