# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is episode 32 - Coravel with James Hickey. In this episode I interviewed James about his open source library Coravel, which is based on the extremely popular PHP library Laravell. Some of you may know James from his blog, his community outreach over at dev.to, or from his work on Coravel.

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### James' Introduction

**Jamie**:
  
So thank you ever so much for being on the podcast James, I realise that it's early afternoon for you mid evening, I guess-ish for me. So I totally appreciate you taking time out of your, your afternoon to talk to me this evening. So thank you very much to start with.

**James**:

You're welcome. Thank you. I appreciate this opportunity.

**Jamie**:
  
So I thought before we get into the topic at hand, I thought we could maybe Introduce yourself, talk a little bit about yourself. So the listeners know, kind of who you are and where you're coming from, and that kind of thing.

**James**:

Sure, my story kind of dovetails into what we'll be talking about anyway, so it's a good way to introduce the topic.

So I've been a software developer for over five years now. Right now I'm a senior developer, mostly doing .NET based stuff. Right now I'm leading kind of my big project I'm leading is a mobile app for the company over four, and that it involves a lot of like re-architecturing sharing what's there and then building an API on top of that and the actual mobile, leading the mobile app stuff too. So that's kind of today.

As far as kind of my journey. I have two years of college. And then after that, I started working right out of college into a ASPX web forms kind of project. So I got a lot of experience with web forms, and C# and that kind of stuff, and JavaScript. And kind of over time, just got a lot of experience with pretty much the whole stack. About two years into my career, maybe two, two and a half, somewhere around there, I started getting interested in you know, doing side projects and things like that are just playing with ideas, and .NET Framework I want to say at the time, but still wasn't very easy to use to build side projects quickly. Because you need like a Windows Server and you need IIS and all that kind of big, expensive infrastructure to use .NET Framework. And this was before .NET Core was really popular.

So anyways, I started exploring other languages and frameworks, and actually tried to pivot, like get different jobs. Actually like a front end, I almost got a front end a job as a front end developer. And the only reason I didn't get that job is because there's like last minute, I discovered what some of the projects I would have been working on. And they were just like, ethically not appropriate. So I kind of bailed on that.

One of the big things that I discovered was Laravel, which is a PHP web framework. And it's just so easy to use. It kind of automates a lot of tedious like, you know, things you have to do over and over and over in typical web apps. I'm thinking like, authentication; it comes with an ORM that's really easy to use. And then it has kind of these a lot of these really, really nice features like background task scheduling, that's really easy to use; queuing: it's kinda like baked in, you just tell it, "Okay, I want to queue using my database," or "I want to queue using maybe some other queuing service," or whatever, it's really easy to just kind of plug these things in. So yeah, at that point, I really love kind of that ability to just rapidly build stuff and not have to worry about all that extra kind of those cross cutting concerns kind of things.

So that kind of comes back to Coreavel. And Coravel is kind of pieces of what are in Laravel which is the PHP framework that I wish would have been in .NET. And so it's the first thing that I kind of toyed around with and played around with was a task scheduler that was, you know, similar or inspired, by the way that you would do it in Laravel. And so that's kind of where that was first. It's kind of birthed out of like a career crisis was like well, do I really want to continue with .NET or not, and then I, .NET Core kind of brought that back to life kind of my interest in .NET. And anyways, yeah, .NET Core is fantastic. And it like, it has a lot of stuff. Like dependency injection, for example, that Laravel has baked into it. So it does bring a lot of those things into it. But there's still a few features that I would have liked to have in .NET Core that weren't in there. So that was kind of my my idea was to just play around and try to add some of these little features.

### Removing The Ceremony

**Jamie**:
  
One of the things I really like about the higher level languages and frameworks is that they take a lot of the ceremony away from the sort of important yet busy work tasks, like you said, there, you know, Laravel has all of these things baked in the you don't have to spend weeks architected. Whereas, you know, as you were saying .NET didn't have them, and I can't even imagine working in low level C and C++ and building, say, a web server or building, I mean, even starting from scratch and building a video game engine, you know, I know that there's a YouTube video series that I follow called Handmade Hero, where .it's an engineer who's been building a video game engine for about three years. And he does it in two or three hours snippets at a time. And live streams, the entire development, I can't even imagine like, writing code that just draws a pixel on the screen. I mean, I did that back at university, but just having to hand engineer all of that, it just boggles my mind. How much ceremony goes into all of these things and projects like Laravel and Coravel and things like that are brilliant for this, because it just takes away all of that complexity, doesn't it?

**James**:

It does. Yeah. And kind of, from a business perspective, kind of the idea that, why would you want to waste your time on solving problems that have already been solved, where you can just kind of them out of the box in there, they've already been tested, you know, they're secure, and you know, those kinds of things. And then you can just focus on delivering, like impact for your business, right. So you can focus on the core, kind of the core of domain things that whatever your business does, and not have to worry about all that other stuff. So I think that kind of, I guess, mentality, I get maybe similar to like, the agile approach or whatever, where you kind of just want to focus on what your business is doing and kind of be smart about what you're going to build and what you're going to buy. As far as like an off the shelf or whatever, things like that.

Yeah, that's just it as a software developer, now, in my career, I'm to the point where I'm still learning. I mean, we're always learning every day, and there's always so much to learn. But I know enough that I really want to focus on just like delivering value to customers, making customers happy, you know, improving the business. So a lot of those kinds of things. I think, once you do get, you know, years into your career, you start to get to a place for either you want to do that, or you just you know, you want to be a code monkey, I think there's kind of maybe a fork in the road that many of us kind of take so yeah, I'm definitely in the camp that I, I want to just help people and deliver value for businesses.

**Jamie**:
  
Definitely. I know, there's a quote, and I can't remember it off hand exactly. But there's something in both The Phoenix Project and The Goal - which is what part of The Phoenix project is based on - that essentially states that until the product that you're building, so The Goal was originally written about manufacturing, and The Phoenix project is all about - for people who haven't read it - is all about the process of like, why dev ops and why sec ops are a thing. And essentially, the quote is along the lines of, "until you get the product, whatever that product is, into the hands of the client, the customer, the user, whatever word you want to use, until it gets to that point is not making anyone any money, it's just a big time sink. So why not take away all of that busy work of glueing things together and building a task scheduler or building the code to draw a pixel on the screen, take all of that away, and just get something out to the customer first and get that important first bit of feedback first?" Because you'll always find, and I've said this many times, but you'll always find that I've said this for years, "your client, your customer doesn't know what they want, until you give them what they don't want."

**James**:

Yeah, that's a good one.

**Jamie**:
  
Speed that up, get the product to them quicker, by using things like Coravel, Laravel, Hang Fire, all these kinds of different projects, use them as much as you can to get something out there first. And if you've architected your application well enough, you should just be able to dependency inject that library. So let's say you started with Coravel, or rather let's say you started with Hang Fire, and decided Actually, I don't quite like this, swap it out for Coravel without anyone even noticing with maybe a couple of changes in some code base somewhere. Maybe one or two commits a pull request, bang, you've changed it all. Nobody's any the wiser.

**James**:

Yeah, definitely. I think that that whole idea, like it did applies to so many different situations. I think people get tunnel vision. I mean, myself included with that kind of thinking. So we think, "oh, you know, to be agile, you have to use, let's say microservices, or whatever," right? It's easy to just kind of like, grab this one, I think the term is "Golden Hammer", where it's just like, "this is the thing that I'm going to use to like fix all my problems every time no matter what." It's like, you know, you can be agile. And that's what led to the whole, like, serverless, stuff and you know, Functions as a Service, those tools are super useful to be able to just like put code in a function on the cloud, and then you can run it remotely like that is fantastic. And you know, that is good for specific cases. But then on the other side of the like, same spectrum, I guess the Agile spectrum, if you want to call it, you can still be agile, with you know, running a monolith like that, right? Just like you said, if you're smart about how you architect it, and what tools you use, you can still build fast.

I've been in companies where I've done like, been a developer for like one product. And I've also been doing professional services where I've been doing a lot of like smaller projects. Yeah, and I've seen it quite often where it's like, "okay, we're going to start a new .NET project. And we're going to start from scratch, we're going to build our authentication from scratch, we're going to build, you know, all the cross cutting stuff from scratch. We're not gonna like leverage anything we've done before." And yeah, I've seen that. And I mean, nobody enjoys that, right? Like, if you're a developer, and you have to, like start from scratch, and before you can even start attacking like the business problems, you have to spend three months like building your own little framework in house like, yeah, I guess if you do one time, it's fun. But then it have to do it over and over and over. It's, it's not very fun. I've had to do it. And yeah, it's not fun. So yeah, I think I think these kinds of tools are awesome. And when you think of like Functions as a Service, or microservices, those are definitely more like enterprisey things, I guess. Maybe not so much Functions as a Service, but definitely microservices.

But Coravel, I think, at least the original intent was more on the other side of the spectrum for let's say, individual developers, let's say I'm just like my, I want to start a new .NET Core app. You know, maybe I want to start a new business or whatever. But I'm starting off small, I'm just, I have a web app, I'm not doing load balancing, or I'm not, you know, doing that kind of stuff. And I just have a really just a web app. But I do want to have some of these more advanced features like task scheduling, or queuing. Like for example Coravel has caching too, and there's tools for making mailing simpler, and event broadcasting, that you can do all that stuff in your simple - I don't wanna say simple - but your monolith .NET Core web app, and you don't have to use RabbitMQ, or having an event bus, or a service bus and kind of all the you know, all that like, heavy extra infrastructure that you think of when whenever you think of like background scheduling, caching, like Redis. Yeah, like event broadcasting, usually you think of like, "Okay having to do pub/sub on like RabbitMQ, or whether," but you can do all that in memory and have it just, you know, easy to use, right. So that's kind of what I really liked about Laravel, the PHP framework is, you can still use a lot of these really fantastic patterns, but you don't have to bring in like this huge infrastructure to use them. And like you said earlier, you can replace them later on if you need to. And I guess that's one of the benefits of dependency injection, and using interfaces and stuff like that, you can easily just kind of replace stuff as you go. It kind of depends where you are, what what your project needs are, and Coravel is at least intended for originally, these kind of smaller projects that you know, you don't need to do like enterprise scale.

**Jamie**:
  
Even at you know, enterprise scale, you could feel like you could still use something like Coravel to sort of cover those bases, you know, the setting up task scheduling, and I mean, we'll mention it later, I guess that we can handle hooking up their email API's and things like that. All of that sort of, like you said, you know, the queuing and all that kind of stuff, it sort of takes away all of the the busy work of connecting all of those things together just to make it simpler to use. Like we said earlier, just get product out to the customer doesn't matter how it all fits together, maybe in the future will replace it, maybe not. And you know, like you were saying there about having to write an entire authentication system from scratch. Well, like you said, you know, it's fine until you have another project, at which point, you might not be able to use the same authentication, because you're going to write it all again. And I keep saying it, but like you said, you know, you're three months into the project, and you've got nothing to show the customer yet. Maybe if you HTML mockups, maybe, if you really are lucky, maybe just a Photoshop PSD to show them. This is what it will look like.

**James**:

Yeah, I've been there done that.

**Jamie**:
  
It's not fun as it is. Yeah. This is what the system will look like. We've got a couple of JPEGs here. And maybe I can click this part of the JPEG. Well, Jeff surreptitiously pushes next on his keyboard.

**James**:

I've been on projects where it's like, "okay, we need this new feature, we're going to demo it. We've already like sold the idea. We're doing it like live demo next week. We need you to like just fake it, build the feature is just like total front end, pretend it works." And then the person doing the demo knows exactly what pieces to click on. Yeah, it's like ridiculous stuff like that. It's just no button, like, as a developer is just at demotivating for sure. Yeah. I mean, you can leverage kind of these tools to just do away with all that and start actually building stuff. That's fantastic to be able to do that.

**Jamie**:
  
And of course, it can swing the other way, where you build quite clearly a prototype, you keep telling everyone this is a prototype, it doesn't fully work is never intended to fully work. And then somebody sells that to someone and you're like, Okay, that's fine. But now I have to go and build the app. And then they say to you, "well, why you have an app, and it's running here?" And he keeps saying, "No, it's a prototype, no matter how many times you press this button, you will always get the same response back." You know, and then you get into trouble somehow.

**James**:

I think once that happens a few times, you learn never to do that.

**Jamie**:
  
Definitely.

**James**:

Let's build a prototype. But let's let's actually have something robust underneath just in case, because it's bound to happen.

**Jamie**:
  
Yeah, sure. I mean, it's only ever happened to me once, where I built a Windows Forms app. And I was told by my project manager, "just do a prototype every time you push this button, just do the same thing. It doesn't matter." And then, you know, it was only I think it was two or three weeks later, I was receiving bug reports about how this product that we've paid for doesn't actually do what you've told us it will do.

**James**:

Surprise, surprise.

**Jamie**:
  
Yeah, it happens. It's not a problem.

I mean, you kind of touched on it earlier on, but what kind of things does Coravel allow me to do? What will Coravel do to take away, that sort of procedure of setting up my application, the bells and whistles work? What can I do that I could pull into an app today?

**James**:

Sure, we can start from a high level from like the features. And then later on, if you want can even talk about how its implemented and kind of some of the some of the, I guess lower level things that's going on, which kind of relates to .NET Core, because there's a lot of like... For example, the `IHostedService`, which is new and .NET. Core, this test scheduler relies on that, and it's just such an easy API to use - it's Fantastic.

So anyways, feature wise the first one that I started building, which at that time was just, I had no intention of actually like having people use Coravel that much, was just kind of a challenge to myself, "Hey, can I build something like Laravel?" Yeah, so the task scheduling is basically, I have some kind of job or jobs in my system that I want to run periodically. Maybe it's every minute, maybe it's every hour, or maybe it's like every Monday and every Wednesday, you know, those kinds of like combinations. So I kind of familiraised myself with the way Laravel did it, and tried to borrow a lot of those techniques with the way Laravell; as far as like the API goes, it's a very fluent API. So you think something like Linq in C#, is that's a fluent interface.

I guess the overall intent that I had started Coravel, which is that shares the philosophy with Laravell is just to make it super easy to do stuff. Like for example, if you go to the GitHub repo for Coravel, there's a picture on the readme of some code to schedule a task. And it's literally like, it could be one line if you want it, but it's three lines. So it's literally reads like

{{< highlight csharp >}}
scheduler.Schedule<SendDailyReportsEmailJob>().Daily;
{{< /highlight >}}


So it's very easy to read. And then the job itself is within that class that's in there.

So yeah, test scheduling is that kind of thing. I ended up when I finished it the first time I posted it on Twitter. And it kind of blew up, I guess, if you want to put it that way. At least you know, from my perspective, it did. It was like, okay, people are actually interested in this kind of thing. So I ended up I think I added the queuing feature. It's basically, so if you're in your web app, and you let's say you want to have a controller action, you know, someone fills out a form and they hit submit, and part of this business process that you have to do in the back end involves doing some kind of like IO, maybe you're like hitting an AP, an external API, or maybe you want to send email, which can take a while, you know, a few seconds, you don't want your user waiting a few seconds to be able to get to the next screen, they don't really need the feedback to say, "okay, we really sent your email," usually, you just want to put that on a background thread or queue it up. And then just return to your user immediately and say, "okay, we did your stuff, but it's running in the background." So that's kind of what queuing is for, you can do something in the background thread, and it won't hang your, your request, so your user can just kind of move along.

I'll go back to task scheduling. So after I created the queuing piece, I went back to the task scheduler and just totally rewrote it, because it was, you know, was a first try just for fun. And people that started actually using it. So it's like, "Okay, I need to make this little more robust." So I ended up rewriting it. And so now there's a lot of like features like, you can prevent overlapping tasks. So let's say I have a job that I want it to run every five minutes. But for whatever reason, maybe my job is running a little slow. So it actually takes longer than five minutes to run. So what would happen in that case is while that task is running, and hit that five minute threshold, in some cases, you don't want another instance of that job to start running, because you already have one running. So there's a feature in Coravel where you can just say, "I only want one instance running, if that is due to run again, and it's still running and just ignore it. Just keep it running and only keep one instance going." That's obviously very helpful if you're depending on what you're doing.

And then recently, I don't know maybe a month or two ago or two months, time flies, so probably a few months ago, there's a feature called Schedule Workers. So the way the schedule works, because it's it's targeted towards web apps, is the task scheduler only runs on one thread, but it does everything async. So it's very efficient if you're doing asynchronous stuff. So if you're calling API's and doing a lot of like database IO, your schedules aren't going to be blocking. So if you have like 10 jobs that are scheduled to run, but most of the time spent is is async IO, all of your tasks was run fine, they'll run efficiently, they won't be blocking each other. But in some cases, you might have tasks that maybe do some synchronous work. And in that case, they would be blocking all those other jobs. So if your first job starts running, and it's doing synchronous stuff, like a lot of CPU heavy work, all the other jobs are going to have to wait for it to finish because it's only running on one thread. So the Schedule Workers is kind of a way to solve that. And basically, you can just tell your individual jobs to run on their own threads. Or you can group different jobs. So I can have like three jobs, give them their own dedicated thread to run on and, and maybe just leave all the rest on the main thread. And that's probably, I'd say, that's more so helpful if you're building like a console app, and you're using the scheduler.

And I wrote an article last week about how to do that. Just a really simple one, about [.NET Core 3 worker services](https://www.blog.jamesmichaelhickey.com/NET-Core-Worker-Services-Background-Job-Scheduler-With-Coravel/). So I have an article there on my [personal blog](https://www.blog.jamesmichaelhickey.com/), how to use Coravel's scheduling with workers services. And you can do that you can in that case, if you're using too many background threads, it could affect the HTTP requests that are coming in for your web app. If you're basically hogging all those threads that otherwise would be used to handle HTTP request. That's not good. It affects your scalability. So yeah, typically, you want to like do scheduling in a console app or something else, if you want to go that route. Schedule workers lets you do that.

Caching is another feature in its .NET Core actually has a really nice in memory caching feature. I think the interface is `IMemoryCache` if I'm not mistaken. And Coravel's caching is basically just a wrapper around that. It just gives you a really, really simple interface to use. And just like an extra feature that isn't built into the .NET Core interface that you can do. There's event broadcasting, which is basically you have like events and listeners in memory. So sometimes you might have some kind of like, complex business scenario that you need to do, you can have an event like user created, and then you can have multiple listeners that you fire off whenever you broadcast that event. The event broadcasting is pretty great; not Coravel in particular, but just like event broadcasting, and generally using like an event based, I don't wanna say architecture, but pattern really helps to decouple your code. I think, for developers who haven't used kind of an event driven way of building apps, I would highly recommend it, it you know, it's a bit more advanced, but it's a lot easier to extend your app.

So instead of having to like go into your, your classes, and add some new code and, and muck around and what already exists, if let's say your business comes to you and says, "okay, when a user is created, we actually need to send like this email, or we need to hit this API to like sync our user and fill with an external service or whatever." In that case, you would just build a new event listener, and just say, "okay, whenever this user created event happens, just fire off this new listener that that I made." And you don't have to touch the other code that you've created. So yeah, it's really easy to to extend your apps that way.

And there's mailing: Coravel Mailer. And yeah, that is very inspired by Laravell's mailing feature. And again, it's just a lot of like easy abstractions, to do mailing in your apps. So for example, you would have a `IMailer` interface that you would use dependency injection, you would get an instance of that, let's say your controller. And Coravel has this concept of a mailables, which is borrowed or stolen from Laravell. and a Mailable is just a class that you create. And it basically just, it's a class that represents who you want to send mail to, and the template for the mail that you want to send. And it's all encapsulated in one class. So you might want to say like

{{< highlight csharp >}}
mailer.Send(new UserWelcomeEmail());
{{< /highlight >}}

And then I would pass by user into that class, and it would know, "okay, I need to display the username or whatever in the email." But all that is abstracted way. So it makes her controllers really clean. So you just say, "okay, I'm sending this this mail, I don't have to worry about the details now." And the Mailer is a bigger feature, it has a lot to it. So I guess if, when you look at like the official docs, there's kind of a lot to it, it comes with some pre built email templates, which is kind of cool. So you can kind of just l it and start using it right away. And you will already have kind of a email template set up for you already. And you can configure it to use like, like logo or whatever, it's kind of pretty easy to configure that kind of stuff like a footer and a logo and all that kind of stuff. And of course, you can replace it with other kinds of things if you want. And like you said earlier, the actual interface uses SMTP, there's a way to kind of provide your own driver, so if you want to use like Amazon's email service, you can just kind of call this method on Coravel. And as long as it uses the same interface, that Coravel uses: the `IAMailer`, then you can just pretty much just plug it in and and not have to change any of your code like you're talking about earlier. We can just switch email services pretty easy, and not have to change any of your actual implementation code.

And there is a CLI, which I haven't really done any work on for a long time, but there's a CLI that you can instal as a .NET Tool. And it's just kind of like an easy way to create some of these classes that Coravel uses. So like events and listeners, just command line command, I guess that you can easily just say, "okay, I want, I want to build the new user event. And then here are my listeners I want to create," and then it'll just create all those classes for you automatically. Yeah, that's kind of the high level survey, I guess, and all the features.

### Event Driven Programming and Classes

**Jamie**:
  
I just want to harp back to something you mentioned about Event Driven Programming. Because it's a wonderful system is a wonderful architectural design. One of the first big applications I ever worked on was essentially a system that you we had these USB devices, and this was back in .NET 3.0 days, and we would communicate with the USB device. And it would use radio technology being suitably vague, because it doesn't matter what technology used, you can think of it as being dependency injected. And we wrote an app that essentially would communicate with the device. But it wouldn't long poll for a message, it would wait for a message to come in. And we built an event, almost like an event driven system that we used delegates, at the time. And we created this custom delegate, and we had the first time you read through the code and looked about like spaghetti code, because there was no real entry point for these messages, until you'd run it a few times. And then you'd send a message from the device. And then suddenly, a breakpoint would fire. Because there were some event watcher set up somewhere in the system that would then go, "Hey, this message just came in via USB, here is the message." And it is wonderful. It's brilliant. It's not the same. But if you've ever done any, like Windows Forms, or WPF, stuff and bound to a click or typing into a text box or taking a checkbox or something, it's a similar sort of paradigm, as soon as the user hits that button, or presses a key or whatever the message is sent from the UI down to your business logic layer, which in a Windows Froms App is on the same program, but you know, same sort of idea. And I guess, same with web forms. I've only done a little bit of web forms for a couple of months. But it's the same sort of idea that sort of event driven HTTP, that I mean, it served a purpose.

**James**:

Yeah, definitely. And like, the Coravel each listener is an individual class, which like you're saying, like web forums, for example, it can easily become like really messy, when you just have a class that's full of all these different methods that handle events. So kind of I like the idea of just having like, one class that can do one thing. And if you need to do anything else, and you would create some new listeners or new classes in that case. And yeah, like this pattern is used heavily in like domain driven design. I mean, pretty much once you get into like any kind of like enterprise level systems, or you know, that are done well, you start getting into event driven systems. I mean, yeah, like you said, it's hard to follow if you're not used to it. And just I think probably the hardest part is that you don't have those concrete dependencies. Like you don't have a way to say, "okay, this class concretely depends on this other class." You know, in my IDE, I can hit F12 on this class, or shift F12, like Visual Studio, I think it'll show you like all the references where that classes used. But yeah, using an event driven kind of pattern. You don't get that direct connection between classes. But once you understand that, yeah, it makes it so much cleaner, to extend and end even to understand because then you have, everything ends up being a lot simpler, right? It's handling one thing. And if you need to do this other stuff, then you just create a new listener, as opposed to just shoving everything into one class, which is very common.

**Jamie**:
  
Yeah, but single class with all of the functions and all that kind of thing. It's a bit of an anti pattern. But sometimes you have to use it just to get the work done, don't you?

**James**:

Yeah, if you're using web forms, you kind of give them a choice. I've never used WPF before, or any, like those kind of MVVM frameworks. But yeah, I mean, even when you're looking at like front end frameworks, like vueJS, or Angular, you end up having to create a lot of like, individual methods to handle events. But definitely, when you're talking about like business processes or business logic, doing that event driven kind of stuff, where each listener is an individual class makes a huge, huge difference.

**Jamie**:

It really does.

Okay, you talked about the mailing and the messaging that Coravel does, and you said that it comes with bunch of templates, the templates, easy to set up as it just literally CSHTML, or is there some other sort of language you need to learn to use it?

**James**:

No. Basically, when you install the mailers - so the mailer is separate and NuGet package - then Coravel Because it does have dependencies on like the SMTP thing I think, probably some other stuff. Yeah, basically, once you install it, I think by default, because there's two different templates, there's like a simpler one. And then there's kind of a more fancier one, I think the fancy one is installed by default. It's just kind of out of the box installed. So basically, the way it works is you create a razor file, just like you would do in like, creating any kind of like razor view. And that razor view has certain pieces of data injected. So Coravel does a lot of like a, I don't want to say "magical stuff". But that's kind of, I want to put it that way "magical". I'll just use one example: so when you're building a mail, let's say for your like, welcome user email, you create a class that inherits from this Mailable class. And you have to implement a few methods on there. And the name of your class is actually going to be parsed by Coravel and it becomes the subject of your email. So if you're, if you're Mailable is called `WelcomeNewUserEmail`, then it'll automatically make the subject of your email, "welcome new user". Of course, you can override that. But it does stuff like that. And there's other things that it'll inject for you.

So basically, yeah, you just make a razor file, like a normal razor file. And you can use the ViewBag. And there's certain properties that you can use and go look at the documentation. And yeah, so you just basically build a razor file, and you have access to let's say, if you want to inject your user, this is your welcome user email, you can inject your user into your template, your is your template, or your original razor file, and just put your users first name or last name into your email wherever you want. And then in the class that you created, you just point it to whatever razor file that you want to use for that specific email. You don't have to learn any new like template languages or any anything like that it's still razor, it's just that Coravel kind of handles all of that stuff around the outer shell for you. So that razor view that you create will be injected into like the overall template. And so you're like your header and your logo and your footer, and all that stuff is kind of all done automatically for you. And each email, just kind of have to code the body of it. And then you can have whatever data you want to inject in it, you can, of course, they'll do that for you. So yeah, that's kind of the gist of it.

**Jamie**:

Okay.

### Extending Coravel

**Jamie**:
  
You mentioned earlier on about it being sort of extensible, the mailing system. You said, "it can use SMTP, or you can if you implement a specific interface, you can pull in an Amazon emailing system, for instance," I can imagine that perhaps there might be some system for using Microsoft Exchange and things like that. But I was just wondering, and it might come across as a bit of a silly question, but can it be extended to use non emailing systems? So for instance, I know this week, a friend of mine, Paul Seal, he released the new version of his [slack messaging bot](https://www.nuget.org/packages/SlackBotMessages/) that is now .NET Standard compatible, I was just thinking, maybe I could hook it up to that. Is that something that's possible? Can I talk to non emailing system? Where is the paradigm specifically for you will use the mailing system for mailing only

**James**:

you can if you want, the interface is definitely like email specific. So you'll have like a message and subject to an even like a carbon copy and blind carbon copy. If you want to extend that to use some sort of API of any kind. You can. So yeah, if you want to do that.

**Jamie**:
  
That's cool, I like it. Being able to extend a library or a system that I'm using, I like that, rather than being sort of, what's the phrase not really trapped in the design of the system, but being able to sort of push those boundaries out a little, because you and I both know, and I'm sure the listener knows that we build a system for someone, and then they come along and say, "that's great, but can it do x?" And you say, "well, that's doable, but I'd need to rewrite a huge amount of the system," and they'll go, "but it's only a tiny change." and I'm like, "Who's the expert?"

**James**:

Yep. Laravell actually has like, they have a feature, I think it's called notifications, maybe. So it's kind of like a higher level on top of the mailing idea where, basically, you can send notifications, and you can kind of configure that to be like SMS or email or like slack messages or whatever. That's not in Coravel. But that's definitely a feature that, you know, if people ask for it, then I'll probably put it in that that's very handy kind of thing to do. So yeah, probably just having like a much simpler interface of some like `INotification` interface or whatever. I guess you wouldn't have like the blind carbon copy and carbon copy those kinds of things. You wouldn't need those for like sending slack messages, probably. But you could use what's there if you wanted to.

**Jamie**:
  
Okay, so what we're saying is, there's an open call to the community: submit your pull request now.

**James**:

Yeah. And, like, I've got other features that I'd like to build, eventually. But it's a lot of work. And I don't have much time. So if I see that people are interested in you know, there's kind of a common thing that people are interested in, then gives me more reason to do that. For example, eventually, and I don't know when, but I'd like to add a feature to the task scheduler, the basically make it a distributed Task Scheduler. So for example, if you're doing load balancing, you can just configure all of your jobs in your code. And Laravell has this feature, which is super nice. And basically, if Server A, like you have two servers that are doing load balancing, if Server A starts running your first job, and then S erver B, is starting to check the schedules, they won't run a job, if it's already running on the other server, you know what I mean? So that's something I'd like to add, obviously, that they'll probably take a bit of work, but those kinds of things. I'd like to add eventually. So lots of work to do.

**Jamie**:
  
That's the problem with these passion projects outside of work, they always take up so much of your time, I have a few that I work on, they're never going to be monetizable. It's just something that I want to do you know, and I think it was Will over at [Complete Developer](https://completedeveloperpodcast.com/) who said recently that, you know, not everything you do has to be monetizable, as long as you can get something out of it - be it some kind of professional growth, or some kind of new technology figured out on a new paradigm figured out, then that's a net gain. Even if you don't even if you just go down a path of a wonder how this works. Why doesn't that work? Or can I do this? Figuring it out is a gain.

**James**:

Definitely

**Jamie**:
  
Exactly, right? So I've got a bunch of personal projects that I have, just for learning new technologies, you know, a couple of web API's couple desktop apps. Just a case of wonder how I do this in this technology, which is new to me is maybe not a new technology. But yeah, we all only have so much time, don't we for working on these passion projects.

**James**:

Yeah. And I've got a large family. So I probably don't have have nearly as much time as most people have. But yeah, like that even implies the Coravel. When I first started building it, I didn't know that much about .NET Core. And it was definitely a way for me to learn a lot about .NET Core, which is why like I mentioned, I ended up just totally rewriting the scheduler, because I have learned so much about .NET Core, and you know how to do things, right? So yeah, like you said, even if it's just to learn a language, or learn how something works better, it's definitely worth the investment,

**Jamie**:
  
Most definitely, and nine times out of 10, you can take that to something that you're already being paid to make. You know, so a couple of years ago, I started looking at the Docker to see how that worked. And then it turned out that someone at the company was working for at the time said, "Hey, why don't we learn Docker" and I just kind of said, "Hey, I know, I'll teach it, I could do this." And I ran a few, you know, lightning talks or lunch and learns and just sort of taught people how to use it. And six months before I left, all projects, were using Docker just because it made things easier. It's not the be all end all. It's not for everyone, but for the particular tasks that people were doing. That made perfect sense. So everyone sort of adopted it. And that's a case of I wanted to learn how to do it. It was nothing to do with work, nothing to do what I was paid to do. But you know, wanted to learn it. And then it paid dividends.

**James**:

You know, it's the same thing with Coravel because I was able to learn so much about .NET Core. And I was able to use all that knowledge, like in the project that I'm working on right now. So

**Jamie**:
  
Definitely. So with the task scheduler, then because I have a question about that. So if the system recoverable? So let's say I have a number of tasks that have been started, are they persisted anywhere, I think we kind of touched on this a lot earlier on, but they persisted anywhere. And if so, if my app crashes, and I need to restart the server, can I load the queue of tasks back into memory and carry on from where I left off,

**James**:

There not stored anywhere, because they're just run in memory using an `IHostedService`. But there is a way to hook into kind of, there's kind of these hooks for the Task Scheduler. So you can configure like an error handler for your tasks. Or you could just do it in your task, if you wanted to do like a try catch or whatever. Probably relevant is, for example, if you have some tasks that are running, and your app is shutting down, for whatever reason, Coravel, keep that process running for you until all of those tasks are done running. For example, if you just try Coravel out on your own, and just schedule something to run, like every minute or whatever, but just hard coded, make it run for five minutes. If you try to do Control+C and kill your process, you'll see like a console message saying, hey, you still have some tasks running, we're not going to shut down until they're done. So that's probably where the line needs to be drawn between, like how robust you need your test scheduler to be. If you do need your tests persisted, for whatever reason, then, probably not, you shouldn't look at Coravel. But yeah, if you don't need it, then it might be a good fit.

**Jamie**:
  
I mean, that's fair enough. We were saying earlier, when you know, you only get so many hours in the day. And you know, this is essentially, I hope you don't mind me saying but essentially, this is kind of a "in your own time, passion project" sort of thing. So you kind of expect to be able to do everything. But then again, if you have a bunch of tasks, and you need them to persist, maybe you should possess them. you know what I mean? Maybe it's a task left to the implementer, the user, to actually persist them somwhere.

**James**:

Yep, and there's an issue open right now, for a feature so you can pass in cancellation tokens, do your jobs. And that probably help with something like that. So for example, if you're, if the app is shutting down, then your job would get notified of it. So then, as a developer, you can handle maybe you're doing like a, you know, a for loop that's hitting an API every time you do your for loop. And then you get your cancellation token saying, "hey, the apps shutting down, maybe you want to cut it off short and store your results, and then the next time that task comes around, pick up from where you left off." So that's a feature that I'm hoping probably going to be not next, but the one after that, but I'd like to implement. So that would address that kind of scenario. I'm not totally sure, like, if you're persisting tests, like if your app is shutting down, you wouldn't be persisting your whole, like your actual job, you'd be persisting the data that you've processed so far. So I think typically, that would be up to the developer anyways, there could be like an automated way to do that. I think maybe HangFire has a way to do that. I might be mistaken. But I mean, basically, it just comes down to getting a cancellation token and whenever it's up, then you can choose to store what data you have, and then pick up later next time the job comes around. Yeah, that's upcoming someday.

**Jamie**:
  
Fantastic. Well, like I said earlier on: get your pull requests in and let's see if someone can figure that out for you, figure out how to implement that.

Brilliant. Okay. So what about connecting with yourself, then? How can folks get in touch with you learn about the projects, learn about what you do? What's the best way to do that?

**James**:

So the project itself, so the [github.com/jamesmh/coravel](https://github.com/jamesmh/coravel), and that would be the repo for the project. All the documentation is hosted on its own site. So if you want to check out the actual documentation, you can go to [docs.coravel.net](https://docs.coravel.net/), and you can check it out there. There's also like another project that I have going called Coravel Pro, which we haven't talked about. Iif you want to check that out, you can go to [pro.coravel.net](https://pro.coravel.net/). And that's basically just it's extending Coravel. And it's an administrative panel for .NET Core apps. So if you have a web app, and you want to be able to manage your jobs visually, from like an admin panel, you can fire off all your jobs using a UI. There's like a CRUD for your EF Core entities. It's in preview right now. But I'm working on it. And there's like health metric dashboard, stuff like that. So check it out, if you're interested in that. As far as getting in touch with me, I'm on Twitter at [jamesmh_dev](https://twitter.com/jamesmh_dev), I think is my handle. If you want to check out my website, it's [jamesmichaelhickey.com](https://www.jamesmichaelhickey.com). That should be enough enough areas for people to find me.

**Jamie**:
  
Brilliant, what I'll do is I'll make a point of putting all of those in the show notes. That way, you know, people aren't furiously scribbling down what to do, and where to go. I know that I've done that in the past where I've been listening to a podcast - In fact, I was listening to a podcast earlier this week episode of the InfoQ podcast and there was some quote about security. And that was like, "ahh! Pen. Paper, I'm not fast enough with my thumbs to type it into my phone!" So I had to keep rewinding, to hear it again, to write it down. So let's avoid that. Plus, each episode has, you know, transcription so people can look back through and just hear just how many times I say "you know," because I say them a lot. The only thing left to do and this is anything you want to bring up James is to thank you ever so much for being on the show. Like I said at the beginning, you know, I appreciate that. It takes our an hour and a half out of someone's life to come and talk to me and listen to me say "umm" lot and figure out what to ask people. So I really appreciate that. So thank you ever so much.

**James**:

Yeah, thanks. I appreciate it, too. It's always fun to talk about tech, so why not.

### Wrapping Up

That was my interview with James Hickey on Coravel. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and a full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/).

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [James on Twitter](https://twitter.com/jamesmh_dev)
- [James' Website](https://www.jamesmichaelhickey.com)
- [Laravell](https://laravel.com/)
- [Coravel](https://github.com/jamesmh/coravel)
- [Hand Made Hero](https://handmadehero.org/)
- [Hangfire](https://www.hangfire.io/)
- [The Golden Hammer Anti Pattern](https://exceptionnotfound.net/the-golden-hammer-anti-pattern-primers/)
- [RabbitMq](https://www.rabbitmq.com/)
- [Redis](https://redis.io/)
- [.NET Core Worker Services: Background Job Scheduler With Coravel](https://www.blog.jamesmichaelhickey.com/NET-Core-Worker-Services-Background-Job-Scheduler-With-Coravel/)
- Paul Seal's [SlckaBotMessages NuGet package](https://www.nuget.org/packages/SlackBotMessages/)
- [Complete Developer](https://completedeveloperpodcast.com/)
- [Coravel Pro](https://pro.coravel.net/)
- [Coravel Documentation](https://docs.coravel.net/)
