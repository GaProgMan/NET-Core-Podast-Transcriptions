# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself

I am your host, Jamie "GaProgMan" Taylor, and this is episode 3: CoreWF with Dustin Metzgar. In this episode I interview Dustin about CoreWF, the Windows Workflow Foundation, and a little about the challenges of converting a .NET Framework application over to .NET Standard. Some of you may know Dustin from his work at Microsoft (he has worked on both .NET Framework and .NET Core teams during his tenure there), or from his book ".NET Core in Action".

Dustin is much better at introducing himself than I am, so I'll let him do that.

So lets site back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Dustin's Introduction

**Dustin**

My name is Dustin Metzger I used to work for Microsoft I was on the .NET Framework team kind of  in and out for about almost 10 years. And when I started, they were just getting ready to ship .NET 4. And before Microsoft, I had worked for a bunch of different companies that actually had, had been using.net framework. I was using Workflow  in one of those companies.

And then I was really interested actually went for an interview with Microsoft and got accepted into the into the workflow team. And I was kind of working on performance and actually set up for quite a while and then moved around, did some Azure services and actually came back to workflow and ended up running the the Workflow team, at least what was left of it. I had a team of about 10 people and we were supporting workflows on the .NET Framework ,also System.Transactions, which is includes that like TransactionScope, which was introduced in .NET Framework 2.0. That was ported into .NET Core, and then my team supported that as well. We had made an attempt to port, the Workflow Foundation over to NET Core, but ran into some roadblocks.

But while the whole .NET Core thing was going on before 1.0 came out, I was approached by Manning Press, and they were - actually Manning Publications sorry - they wanted to see if I was interested in reading a book on .NET Core. And I thought, wow, that'd be great, I'll spend few months and write a book, and check one of those things off my bucket list. Two years later, it's finally in print. The name of the book is .NET Core in Action. It's actually a lot thinner than I imagined it was when I was writing it, because it certainly felt a lot bigger but I'm actually glad with the size I think it's for approachable.

The book is actually part of, like a set of four books, so Entity Framework Core in Action, ASP.NET Core in Action, and Xamarin in Action all fit together with my book, my books kind of like the lower level, the foundational part of what is .NET Core? What is .NET Standard? and then EF, and ASP.NET, and Xamarin are all kind of branching out from there. Although Xamarin was a bit earlier, and I think that book was already being built before mine was being written, so.

Even after Microsoft, I'm still doing some, like a basically took the code that we had done for, for the Workflow Foundation and made my own repo and started trying to convert that over to .NET Standard. And it's presented some really interesting challenges as far as kind of enlightening me to how would somebody convert something that's in the .NET Framework over to .NET Standard, and what kind of things would you run into and that's something that we can talk about later.

**Jamie**

I mean, just looking at some of those points there. You know, there's a lot of stuff. You mentioning that you worked on the WF team. I guess you could be Mr. WF, to coin a phrase.

You're attempting to open source it. And you know, you have that background knowledge as well, which is incredibly useful, I guess.

**Dustin**

It's a it's interesting what they attempted to do with Worflow. So when I say Workflow, just I mean, the Windows Workflow Foundation, what they did with it, and the .NET Framework was, I think they just had that one vehicle for releasing things, and then kind of crammed everything into it. They didn't have what we called out of band. So like in band would be you ship with the .NET Framework on their ship train, which is like every year every or two years, and that's doesn't give you a lot of chance for iteration and you got to make sure everything's thoroughly tested and stressed and everything before goes out. So it kind of creates a lot of pressure for features that go go into that.

But also, it doesn't give you a lot of vehicles to get things out. So later on they had this thing this term called out of band where you could make like a library that you just released, say through I think CodePlex was the thing that they called it at the time. But now it's like you have .NET Standard and .NET Core on all on GitHub, the releases go on to NuGet, everything's kind of out of band, there's, there's well .NET Core actually has like a, an actual ship, train with point releases, things like that. But you can actually have a library that's not part of the .NET Standard that can ship whenever it wants. And that really wasn't a concept at the time. So what they ended up doing was, they didn't have these out of band things and have other ship vehicles. So they decided like, let's just take everything that we want to ship and cram it into the .NET Framework.

And that was things like they had a SQL persistence provider that went with Worflow that you could persist your workflows to a SQL server database. And that came with there are actual SQL files in a .NET Framework. If you go into the .NET Framework directory, there's actual SQL files, and you can run them against your database to set that set that schema up. There's a part in there were workflow uses expressions and those expressions can be written in either VB or C#. But when they were doing the VB part, which was what they had initially for .NET 4, there was no external compiler that they could use. So what they ended up doing was basically taking a copy of these, this VB compiler, embedding it in the .NET Framework and then using that to parse the VB expressions and during the startup time for the Worflow, and later when .NET 4.5 came out to edit C# support but then what they did was they used MSBuild to run C# compiler against the workflow to parse the expressions, and then it builds the thing into the assembly.

So this is all before Roslyn was available. So they have all these kind of tricks mixed in there to make it work. And then then there's actually a Workflow designer. That's a whole WPF app. And they put the whole source code for that into the .NET Framework and people actually, people rehost it. So there's actually companies out there, say like, FlowStir and UiPath. Actually, there's a, there's a product that VMware uses where they rehost the Workflow designer from the .NET Framework to build workflows inside of a custom application. So it's, it's a super complex chunk of the .NET Framework that has all kinds of issues with trying to port to .NET Standard or .NET Core.

### What is the Windows Workflow Foundation?

**Jamie**

So would you mind, for people who don't know what the Workflow Foundation is, is there a brief overview that you can give?

**Dustin**

Sure. And the idea, I used to explain to people as let's say you have a console application where it writes something to the console, and it waits for your input, and then responds to the input that you give. And the classic example is basically that input, there is no, no guarantee and when the input is going to come because it's coming from some external source, which is the human that's typing in, so they could start that programme and not type anything in ever or they could wait a whole year or whatever. But basically, they're locking up a thread, at least, or an entire process to wait for some input. And the thing with a workflow is basically you're saying, I want to wait for this input, but I can unload that object, that whole thing, that whole process, and persist it and wait until the input is available, and then wake it back up, and then run it.

And that's the really the core idea. And from there, you can put all kinds of things in and basically build long running applications that need to respond to inputs, you know, at unpredictable times, and you know, might need to set timers and wake up at certain times and do things and but yeah, they're the real core of it is just the this kind of long running in response to or, you know, timers or, or in response to inputs. Yeah does that fill it in or?

**Jamie**

Yeah, that makes sense. So you could build something like a, I guess, I guess it's where things like Workflows for SharePoint came from.

**Dustin**

Yeah. Actually, so SharePoint uses the Windows Workflow, and in a number of ways, and there's because there's different SharePoint workflows. So SharePoint 2010 workflows uses the old workflows from .NET Framework 3.0. And then SharePoint 2013 workflows use the .NET four and above workflows. And then there's now there's flow and SharePoint, which uses the, the Azure flow system, which is totally different than the .NET Framework version.

**Jamie**

Okay. So I can imagine that, perhaps like you were saying, maybe I create a maybe not a web app, because that would be a bad idea. But if you created an app that would run on everyone's machines, when they login, for instance, let's say that they needed to supply some credentials to access a network drive or something, and you didn't want to use the windows internal, like the AD stuff, for some reason, you could then have a WF system, or is it an app?

**Dustin**

it's called a Workflow.

**Jamie**

Oh, so it would just be a workflow, okay.

So you would have a workflow that would sit and would be running would be would be waiting for the user to type in some credentials or type in some secret to give them access to something and like you say they could do that for, it could be five minutes after they've gotten in, it could be as soon as they turn the machine on, it could be I turned the machine on I login. I don't lock my computer, for some strange reason I walk away and make a cup of tea, cup of coffee, get talking to Jeff about something go to a standup meeting, come back on lock. And then yeah, that makes sense

**Dustin**

Right

**Jamie**

Because you don't want you don't want the processor to be sitting there just burning through a process or a thread and wasting time and wasting memory.

**Dustin**

Yeah.

**Jamie**

That makes sense. So it's kind of like async programming, I guess, in that aspect.

**Dustin**

Yeah, it is. And it's, it has a weird relationship with async, because it's, this is kind of before the whole, the TPL came out of the whole async/await and task parallel library and that kind of thing. So it's actually if you're looking at the code for the, it's using this, this ancient thing, which is the IAsyncResult, which is begin end programming. And that's, it's a terrible way to do async. It's so confusing.

**Jamie**

So obviously, you're attempting to, to create an open source version of this in the form of CoreWF

**Dustin**

Right

**Jamie**

I'll put a link in the show notes. So I guess, essentially, it is an open source implementation, or is it an open source version of here is the code that runs it, I'm just literally taking that and open sourcing it?

**Dustin**

We've pretty much established like, we're not going to be able to, well, actually, there was no desire, and there's actually a lot of technical challenges to convert the Workflow Foundation into .NET Core and .NET Standard within Microsoft. And that's usually just based on how many customers are, are using it. So I that's a decision, I can totally understand him. And it's, it's a big investment from from Microsoft's standpoint to, to do that conversion. But the, you know, it's not as nearly as high volume as say something like ASP.NET, but for for the customers that do use Workflow, it's a big deal. Because it's, it's, it's a critical part of their app or you know, that it's doing something that's really, really a key piece of their business. And I'm hoping that I come up with a version of this, that's good enough that people could actually kind of convert over to .NET Core and .NET Standard and then run on Linux or but we'll see.

So but basically, I'm taking the the code from what we had in .NET Framework and trying to convert it to run on on .NET Standard.

**Jamie**

So you talking about there's a lot of technical limitations is this literally because there are maybe API's that are exposed and .NET Framework, which aren't in .NET Standard yet? Or is it that there's just a lot of difficulty in converting something that like you say is using the old way of doing async stuff over to using you know, async/await?

**Dustin**

Actually so that's what's surprising is that that's not actually a problem anymore.

So like before .NET Standard 2.0 it was a big problem there was all kinds of like System.ComponentModel things, there was just a lot of pieces that we had to work around to get it to work and we did manage to get it to work on .NET Standard 1.3 without XAML and I can go into that. But now with .NET Standard 2.0 it's almost the exact same source code.

But they're the the technical challenges come around say with when when Workflow persists ot uses a serioaliser are called the NetDataContractSerializer and for people that have used WCF Workflow might be familiar with this, but basically there's there's a thing called the DataContractSerializer and then you put you mark your classes with DataContract and you include things in a DataContract by marking your properties with DataMember and things like that. And that allows you to serialise your objects and XML.

The NetDataContractSerializer is it builds on that but it adds type information into the XML so that when you're reading it, it knows which where those types are. Because if say like it says, like, you know, if you're serialising a Shape, this will actually like the NetDataContractSerializer will say you know, the element name is Shape plus it's the type is this assembly this type specifically, and then you know, so that thing is reading and can pull it back in.

So NetDataContractSerializer is not included in the .NET Standard and it's not going to be converted. The DataContractSerializer is there but it's not good enough for the for what Workflow does needs that NetDataContractSerializer because it needs that type of information. I'm kind of going through another thing where there's a binary serialiser now .NET Standard, but BinarySerialiser works differently, where it's a it's an opt out model versus DataContractSerializer is opt in. So basically, I have to go through all the types and kind of reverse the the properties because by BinarySerialiser is going after the fields and I have to say don't serialise this. And you know, as opposed to being inclusive on the other side. So. So that's one of the challenges. The other one is XAML.

So there is not a .NET Standard of System.Xaml. And there's lots of reasons for that. And they all make sense. So the because there's an implementation of XAML in Mono, there's one in the .NET Framework, as well, UWP. And they're all different. And making one version of System.Xaml in .NET Standard, it just wouldn't work, the implementations are all different. So they, they started coming with something called the XAML Standard, which has like, kind of the, the core pieces of XAML, that should be implemented the same across all of them. But it's not an all inclusive thing. And it's also not a tangible thing, really, it's more like a document that says this is the XAML Standard. So you don't have System.Xaml, snd then Workflow used it heavily because all the Workflow definitions are done in XAML. And I had, I found something where it was there's something called Portable.Xaml. It's a it's a library out there on on GitHub and a NuGet. And it's like a port of the Xamarin version of XAML over to .NET Standard. And I'm taking that and trying to fit it into into WF and trying to get it to work, which is it's going pretty well actually so far. So there might be some fixes that we have to do there. But

**Jamie**

So you'd mentioned that Microsoft, I guess I tried to create a XAML standard. But because each of the different platforms had implemented their own version, it's similar, I guess, to the base class libraries and why we have the .NET Standard, I guess, except that would be more difficult to implement. Because each version of a platform so like, like you said Mono has its own sample. And .NET Framework has its own XAML. And I guess, you know, if and when .NET Core gets a XAML it will be maybe even slightly different still because of the different platforms?

**Dustin**

So in the .NET Standard, right. So they don't want to put XAML in there.

Well, actually, for say like starting with.net core so .NET Core is an implementation of the .NET Standard plus whatever they have in .NET Core just like .NET Framework, you could say is an implementation have .NET Standard although it's retroactively like the .NET Standard was applied to the .NET Framework. But that's that's a it's a weird can of worms. But in the same thing with with Mono where it's it implements a version of the .NET Standard so it's like the .NET Core, there's no reason to have ZAML in it, because it doesn't have a cross platform UI. And it's, it's, you're primarily going after ASP. NET for .NET Core. So, like Xamarin would be the real cross platform XAML system. And on Windows, they still want to keep the UWP the Universal Windows Platform, I guess, as you know, where you're writing XAML apps on Windows.

So they didn't want to put like System.Xaml that whole package into .NET Core. They're definitely not going to put it in the .NET Standard because if you put it in the .NET Standard, and you have .NET Core, .NET Core wants to implement the latest .NET Standard all the time. So you know, it's if you put XAML in there, then it's like, basically, you're putting XAML in .NET Core too. So it's not not something that they want to do.

And also the so the XAML Standard is basically to kind of look at all the things, all the different implementations of XAML and try to come up with the core of it, that's the same on all of them. And then kind of use that to drive forward, you know, new versions, we expand the XAML Standard, and then we get Mono to do that, the UWP part to do that. But what's interesting is also the .NET Framework is actually on its last release, there will not be another one after 4.8. There will be you know, new versions of .NET Standard new version of XAML Standard, but the .NET Framework is not going to change. There's not there won't be any new versions to implement those standards..

**Jamie**

Is that because of effectively feature complete at this point?

**Dustin**

Yeah, it's it, we like to use the term at Microsoft as "Done. It's not dead."

You know, for people still usin .NET Framework, there's just still plenty of people at Microsoft that support it. All the new development goes in the .NET Core, .NET Standard, kind of things. But there's still there's still support going on is still in that support. Because .NET Framework ships with Windows, every time Windows ships, it's renewing that support, you know, that timeline, so there's no end in sight for this.

**Jamie**

That's good to know, that's good to know, that's, that's good for me to take them to the technical directors at work and say, you know, don't worry, we don't have to do everything in .NET Core. It's not like it's going away.

**Dustin**

Yeah, absolutely. I mean, it's definitely a, like a long term thing. It's, I feel like, there's a, well, I can understand that the outside opinion too, because there's something like LINQ to SQL, if you adopted it when it came in. And, you know, you you put your app in it, and then you know, think it's really awesome. And then they come along with Entity Framework, and then all of a sudden LINQ to SQL is kind of sunset, it's still there. But it's, you know, it's not going to get new features. And and if there's, you know, a security fix that it needs. And it's, you know, it might not get it. And if it does kind of feel like you're being orphaned out there. So, the only the only difference with the whole .NET Framework is that it is part of Windows. And that, you know, it's Windows is using it and it's being used under the covers by UWP. And so there's there's still things, Microsoft things that are running on it. So it should have better support in the future, then products that are done by Microsoft, but

**Jamie**

Well, let's hope so.

Is there a difference between a Workflow and say something that is a serverless function? So if I have a serverless function that has long polling or something I know it's a completely different technology stack. But if I had a serverless function with SignalR with long polling, which would cost me a lot of money. But if I had that, and I had a Workflow, is there a huge difference other than the underlying technology, it's not using HTTP calls, as you know, that kind of thing.

**Dustin**

Yeah, we're workflow is a bit old.

It uses WCF for communication. And there... it doesn't have this ability to open up like a REST endpoint, there's implementations of workflow, like in servers, say like, this is server calls, workflow manager that does have a REST endpoint. And it's a kind of an event based system, you just send it messages, and then it, the workflows will actually apply filters on, like, like, topics. So the message is going to the topic, you said, you put a filter on it, then it if it matches, the filter will get delivered to the workflow.

But for for specifically, for your question, there's, let's say you were totally okay with using WCF one side and SignalR the other because I mean, the performance differences, it's not even close. But the workflow would be holding a state. And when you've talked to it each time, it's moving along the progress of that workflow. So you could totally have a SignalR service up and then receive signals on it and send them to workflows underneath. Because workflows based it's it can open an endpoint listen to it, but it's, it's more valuable when it's progressing along some state and, and, and handling the, the incoming messages that way. So, yeah, it's it's just basically, it's not locking a thread or anything like that. It's, it's, it's kind of load up when you need it, do some work, get to a persist point, and then unload.

**Jamie**

Is there a lot of overhead from, from an end users point of view from maybe not an end user, but from a developer's point of view? So as a developer who wants to use WF or CoreWF is there a lot of overhead from my point of view, in persisting that state, as it were? So my app reaches a point where I need to contact the user for some information, or I need to contact some other service for some information, and I decided that I want to, you know, hold or, you know, persist the state for now and await the response. Is there a lot of overhead? Or is it just a case of, I don't know, call an API function, and it will just persist and wait?

**Dustin**

In that kind of case, it's a, you would put something into your workflow. So basically, it's it's designed, you can design it either with code, or you can do it graphically, with a designer, where you kind of drag and drop boxes onto it. And then you would put this activity on there, this little box and that workflow that says, receive message or something along those lines. So basically, that that activity is waiting for some input. And then the activity is saying, while I'm waiting, the workflow can go idle, and it can persist. So the workflow runtime sees that it's idle, and it can persist and it persist it for you. And then when it gets other input, it says, "Okay, this input is intended for this workflow instance, and I'm going to go load that up and then send it the the input."

So the, the whole persistence part is kind of dealt with automatically. You have to set up the where the persistence goes, like it has to go to SQL Server, or it has it goes to a file or something like that. But once it's set up, it's kind of its handling that, that persistence, and loading and matching to the right instance, starting new instances, completing them, that kind of thing.

But from a developer standpoint, it's, that's where it gets interesting. So it's like, you could write the workflow as a developer, but it's, it's almost not the target user. Really, the target user is kind of like a business analyst that wants to see their, the way that the system runs in a graphical manner, and be able to, to modify it themselves. So it's not totally like, you could have a BA write the workflow, and do it totally by themselves and just take it that's that never works. And, you know, ask me how I know. But there's a but yeah, you could, you could take a workflow from a BA and then have a dev go over it, and put it into like a format that that makes sen

e to the as a program. And I've seen companies do this actually. There's a this company called EPS Go, they're done in, its Alabama. Their BASs and their Devs work together, and they communicate via the workflow. So instead of the BA writing a big document with a, you know, drawings and Vizio diagrams and things like that, they work on the same workflow. And then when they try to show it to the business, they literally just pick up the workflow and show it to them. And then it's, it's so it's very visual, and makes it very clear of like, you know, this is what each of these boxes are doing. And this is how they're connected how the decisions work. And I think that was the kind of the target for the whole system. And usually, it's, it's those designer experiences that that you can communicate with non developers that that made it the you know, that there was a real value add of the whole thing.

**Jamie**

It's little like what UML originally promised, except that someone can create a pattern. Yeah, so someone could create a workflow with essentially with these, these UML like blocks, and then push a button and actually have the computer, run through the process. And then someone can, like you or me, come along, and maybe tweak it to make it like you say make it make sense, or make it a little bit more optimised or because we, you know, we would have that domain knowledge, we can go actually, you don't want to have this kind of control, you want this kind of control, because it does exactly the same thing. But it's better somehow or, you know, it has a better wait policy or a better persistence or something like that.

**Dustin**

Right, right. And, actually, if you're using, like, if you're writing a SharePoint add in, you can put workflows in it, it uses windows workflow, and they have their own designer on the SharePoint site. But you can also make an ad in Visual Studio and use the regular workflow designer. And basically, that's just allowing, you know, you can, if you're an independent software, vendor writing and add-in, and you can make a workflow or if you're just a regular person who runs SharePoint, you can write your own workflow and the SharePoint designer and upload it to your SharePoint site, which is, it's powerful, but also kind of scary, in the sense that like, you know, just anybody can write a workflow, and whether the biggest job of my team before like when I was working at Microsoft was like, basically, we had a, an Azure service running workflow for SharePoint Online, and we would see all kinds of creative ways of breaking the workflows. So I mean, people are impressively good at finding these things, so.

**Jamie**

I'm reminded of that, oh, like XKCD comic where cue ball is asking someone so how did you download this video from YouTube. Well I copied the link into Word, went file save as and then change the file format, a file extension to mp4 and it just plays."

**Dustin**

That one's pretty good.

### Porting to .NET Standard

**Dustin**

For specifically for for your listeners, I mean, there's the the whole .NET Standard conversion that have been going through and I mean, it's probably the more interesting part of this whole thing is what it's like to convert something as complex as this over to .NET Standard.

So there's, there's definitely interesting pieces. So like, Workflows do allow transactions, and I worked on the System.Transactions team, and we ported that thing over to .NET Core. But the problem was, we didn't port it, like it didn't make it into the .NET Standard. It's part of Core, but it's not part of Standard. And it's not its own library. So you can't just go and pull a, a NuGet package for System.Transactions. Which was really unfortunate, because like, I want to use System.Transactions, but I'm not writing a .NET Core app, I'm writing a NET Standard library.

So what I, what I had to do basically was just copy the, the Systen.Transactions code, put it into my into my implementation for workflow. I don't like doing that. But you know, that's that transactions code hasn't, you know, in the .NET Framework, it hasn't changed for a very long time. So I'm pretty sure I'm not going to have to do much patching.

So yeah, that one was pretty interesting. There's, there's, there's this whole section about within workflow. So I've got the XAML part kind of working with Portable.Xaml. And there's a big missing piece, there were workflows can have expressions in them. So say like, you could have a, like an IF activity. And in the, you could have an expression that basically evaluates the true or false and you can write whatever you want in there, some, some VB or C# expression. I don't have that ability right now to parse those expressions. And the obvious choice is to go for Roslyn, it was never done with the workflow part because we already had other things. And also the way that was built was like, part of the build system was to run MSbuild. And then there was a custom MSbuild target that would go and look at the workflow and pick out all these expressions and compile them and create a assembly out of it. So I don't have that, that whole thing put together. Like what I'd rather do is use Roslyn as part of the the runtime so that when you actually load the workflow, it's going to parse the expressions right there. And the same thing for VB. And then you know if you'd even use an F# expression if you want to suppose but actually, I don't know if Roslyn does have sharp or not. But

**Jamie**

I suppose we'll find out soon enough.

**Dustin**

Roslyn, they don't call it runs on anymore, I think they call it I forget what the name of it is, but it should be supporting the .NET Standard.

And some other things that were interesting was like... Oh, one thing that I had to change was the the whole the way that events were emitted. In the .NET Framework there's all this old old code for emitting events to this ETW system, which is, ETW is Event Tracing for Windows. And that obviously has a, you know, it's geared to Windows, there was a replacement, like a kind of a, an abstraction layer that was built over ETW called Event Source. That was in the 4.5 timeframe or a little bit later, probably. And none of that was it was rewritten back in, you know, like and .NET Framework part for WF. And the WCF team when there according to .NET Standard and .NET core as well, they had the same problem, basically they... an Event Sources is, you could you could take your HW code and converted all over. But what was weird about it was like, they use these ID numbers for each of each event. So each event has keywords it has a task has an OP Code, it has a unique ID number. And that ID, the WCF and workflow were combined together and they were using really high numbers like 60,000, 30,000, things like that, which is totally fine. But what happens in the implementation of Event Source, they allocate an array for the largest number, the ID number. So if you have a number ID that 60,000, you will all of a sudden get an array that has 60,000 elements in it. And then when it tries to compile the system and build the Event Source, it's actually going through and comparing each event with every other event to check for duplicates. So if you've got 60,000 elements and are, you know, most of them are empty, this thing just takes forever. And it is like basically I had to redo all the IDs and you know, that would break any, you know, somebody had stuff that was depending on it, like those ID numbers, and all kinds of things kind of changed with that. So it's like moving to Event Source is, it's it's much cleaner code, but it also loses a bunch of stuff that was there before, if people were using it, it's, you know, they might not be happy about it.

**Jamie**

So if I wanted to use CoreWF and create a workflow, because we were porting it to .NET Standard, how would I go about doing that? Do any to, is this, so it's CoreWF a part of the WF runtime? Or do I need a runtime as well.

**Dustin**

Workflow, basically WF comes with this thing. Like there's workflow application, there's so there's, there's a couple of different runtimes. Theres, basically there's a kind of like one that just does, it's kind of like a one and done run it workflow. And just to test it out kind of thing. And then here's like the the workflow application is a runtime that you can run in a console app that, you know, can host any, you know, any number of workflows. So it's like, they made this kind of base part. And then you could have implementations of that.

So another implementation that wasn't .NET Framework was a WCF service, so that you could have a workflow hosted in IIS, and then when a request came in, it would load the workflow and definition and run the instance that kind of thing. So that stuff's not available. Because WCF server side is not available in .NET Core and .NET Standard. It's basically down to just a console app. And you can use a workflow application that way. So which is not too bad. I mean, you can make a Docker container and throw a workflow application on it and then send it signals and run workflows to their.

Right now the the package that's on NuGet is only supporting workflows that are written in code. The, I have a great big PR for adding XAML support, but it's, you know, not all the tests are passing right now. So I'm trying to go through and figure out what's, you know, we're all the gaps are that kind of thing. Yeah, so it's it's a, it's the the functionality of, of WF is like, the core runtime part is there. But it's like, there's lots of features that are missing still. And I'm still building it up and going through the whole conversion.

**Jamie**

If developers wanted to try it out, they can go get CoreWF from GitHub, I'll put a link in the show notes. And then they can build a WF app to run on top of a console app for now.

**Dustin**

Right.

**Jamie**

But there is a there is a you know, an update coming where they can build a workflow in XAML?

**Dustin**

Well, yeah, it's it's a simple workflow. So they can try out like they have an existing sample workflow and try to run it on there. So expressions don't work. So that's, that's one thing that will a lot of people use expressions. So that's, that's the next big thing after that. So

**Jamie**

I mean, it's a it's a, it's an early release, you know, you can't expect everything to be in there.

**Dustin**

Oh, yeah. Hopefully, you know, people will try it out and contribute and, you know, move it along a little bit faster. I mean, I just work on it on my spare time. So

**Jamie**

if folks want to, if the listeners want to go and learn more about CoreWF and perhaps contribute to the to the source, they just, they need to head over to the GitHub page, do they need to know a lot about how workflow works more, or other parts of the system that folks can be contributing towards that don't exactly rely on workflow, or is you know, are there any resources that folks can go to learn about how it all works, so then they can come in and go, I can make this change here, or I can make that change there.

**Dustin**

If you're not familiar with, with workflow, actually, you could look up just Google/Bing "Windows Workflow Foundation", there's, there's like a kind of a landing page we have for that. And then there's like a Developer's Guide to workflow. And that would walk you through all this, how, how it works, and how to create one. And there's also a whole section of like, we have a lot of tests in this in this GitHub repo. So there's a part of it that has a bunch of like sample applications, like a Hello World, and that kind of thing. So you can actually go through and, and see how it's done, how you write a workflow and how you run it, that kind of thing. And the readme for the GitHub repo, has a full description of all the things that are missing, and that I really need help with

**Jamie**

What we need to do is we need to send every single person who listens to this episode to the GitHub page, so then they can all contribute something.

**Dustin**

Yeah, I mean, if they're, especially if you're interested in workflow, I mean, for people that are not interested in workflow and just interested in .NET Standard, it's, it might be interesting to look at how the project was constructed. You know, you could try to compare it against reference source. Because I don't know if you're basically reference source as a referencesource.cicrosoft.com, I guess, is the is the address. Basically, that's all the .NET Framework source code. And that's kept pretty up to date. Yeah, you could actually try to compare the two if you, you know, really bored, but I tried to put into the commit messages where, you know, you know, what I'm what I'm changing and, and that kind of thing.

But yet, for people that are trying to take like a big project like this and convert it from .NET Framework, to .NET Core, I think the best advice comes from the there's like a Microsoft page that tells you how to do this conversion. There's no tool. You can't go in Visual Studio and retarget your .NET Framework, project over to .NET Core, or .NET Standard, it's, it's basically, you should start with the .NET Portability Analyzer, it's an extension and Visual Studio, you would pick in, you know, you'd say I want to see what's the difference, say, between my app on framework and my app on .NET Standard 2.0. And then it will show you the problems like, and it will actually have suggestions, you know, things like, if you're writing to the Windows Event Log, it will say, "No, you can't do this, you got to use Event Source." Or if you're using like, the really old, I think it's what is WebRequest or something like that. It'll say like, you know, you can use this instead or so there's, there's a bunch of things that it will actually have really good suggestions about what you can do to replace that code with something that's equivalent, but what actually run and .NET Standard on .NET Colre. And then you could take that code, and copy it somewhere and take the csproj and open it up. And basically just like, it's like, literally, you go in there and you delete everything.

**Jamie**

I do love that, about the new csproj format, it's so much simpler.

**Dustin**

Yeah, it's, it's really cool. And I think the easiest way for me was like, I just go into console and I say ".NET new some class library", and I get that example, you know, project file, and it take that and I just paste it into my, my new product, you know, the part that I'm trying to convert, and then work with it piecemeal, and try to fix things and all that stuff. Because, uh, I mean, it's that that basic format includes all the cs files, and it's just awesome.

What I found to with a lot of Microsoft projects, internally is that they will leave source files in the directory, but remove them from the project. So the still in source control, it's still in the folder, but it's, it's not part of the project anymore. But there's no way you could tell like, like, you know, you can try to look through the csproj and try to see if that file's missing, but you wouldn't know unless it actually tries to compile it. And it says, this files broken or whatever, but basically, you could find all this dead code that was in there. So that's a, I think it's a healthy way to, you know, you, you include all that stuff, and you figure out "oh this, there's a whole bunch of files in here that I left in here that I excluded from the project, but you know, never really removed from from from source control."

And besides that, there's other things like, if you had special MSbuild steps, and that some of those come with certain NuGet packages, those you have to kind of redo and see if they're still valid, like things like StyleCop, it adds things to the, to the csproj, as far as MSbuild targets, and that's not gonna work anymore. So they've redone it, I think, for .NET Standard, so you can actually still use that StyleCop NuGet package, but it just works differently.

### Connecting and Contributing

**Jamie**

If listeners want to learn more about you or connect with you, or perhaps contribute towards CoreWF, what's the best place for them to go to, to get all of this information?

**Dustin**

Yeah, I would go to the GitHub repo for for CoreWF and then usually, so that's under it's like, it's under my, my user. So it's github.com/dmetzger, I have some other repos in there, like with the one for the for the book, and but actually, that I actually have a repo for my, my blog in there too. And there's a little link in there, the the blog is actually it's called mode19.net, mostly because mode13h was taken. There was originally they wanted to call it mode13h, because that was the thing that I use growing up, it's that it's 320 by 200 pixels, but 256 colours per per pixel.

**Jamie**

I was going to ask.

**Dustin**

But yeah, so mode13h is it because it's small, 13 in hex is the same as mode 19. So you could still call it mode 19. And

**Jamie**

That's cool. I like that.

**Dustin**

But yeah, so that's basically my my blog, and then I have actually the, the the source for it is actually checked into GitHub, and you can actually see that and that's, that's, that's done with Hugo and it's all in markdown and that kind of thing.

**Jamie**

Okay, so the best way for folks to get in contact with you would be to go to your GitHub profile, I guess, I'll leave a link in the in the show notes, and then they can sort of splinter off from there to find a way of getting a message to you, I guess.

**Dustin**

Yeah, absolutely. I mean, you know, can yell at me for for, for workflow, things, or for taking too much of Jamie's time on his .NET Core podcast to talk about workflow, which, you know,

**Jamie**

There's no such thing as too much time, it's was no problem.

It's been fantastic chatting with you today. Definitely. Thank you ever so much for being on the podcast.

**Dustin**

Yeah, absolutely. It was my pleasure. I hope it's I hope it's useful to the listeners. Really, it's

**Jamie**

Yeah, yeah. Well, I mean, even even just taking a, like you were saying a pre existing .NET Framework application, and putting it to standard, you know, I feel like there's going to be a lot of people who do that. Now, that version 2 of .NET  Core is out, there's going to be a lot of people trying to create class libraries that are truly portable, you know, they're going to be creating the portable class libraries, as opposed to the .NET Framework class libraries, you know

**Dustin**

Yeah.

**Jamie**

And I think it's, it's some good information and advice for the, for the listeners to know and places where they can go to get information on these things. Because Yeah, the next couple of maybe the next iteration of a bunch of .NET Framework, apps may move over to using .NET Core. Like you say, since .NET Framework is, you know, done and .NET Core is going to be the new hotness, we're, you know, we as developers are going to need to have code that works in both places, rather than "I'll make a copy, or a branch and this will be the .NET Core version." Yeah, knowing that at least someone else has done that.

**Dustin**

And so there's other things too, for a friend of mine was going through doing a conversion of a an existing application, trying to get to .NET Standard, and was looking through the dependencies of their of their class library. And they were actually using the old Windows Azure caching. So this was before Redis, they had a different had this whole caching library for for Windows Azure.

So she, basically she found out that you can use non .NET Standard DLLs, you can take references on them. But what happens is, is like, there's no compile time checking to make sure that those those things are actually going to work. So basically, if you're going to, you can, you can do it, like you can take a reference on a package that's not been targeted for the .NET Standard, but the only way to tell if it's going to work is to like test it really thoroughly, because it's only going to break at runtime. So it's, you know, it's an option, but it's it's a scary one. So

**Jamie**

Is that the N1701 message, I believe? There is a, like you said, there's a specific compiler error, not a compiler, sorry, compiler warning that essentially says, "We don't know whether this package works with .NET Standard or not. You're on your own," essentially.

**Dustin**

It must be I think you're you're more familiar with the codes than I am, but it will tell you like, you know, this is a your own risk. But what it doesn't say it in those words, but it really should, it shouldn't look at the big warning thing that says you know, if you should shoot your foot off, that's your fault. So it's

**Jamie**

Perhaps it should be like a skippable error or something. So they're actively grabs the developer's attention. "Hey, you know, this is something that you need to be aware of," sort of thing. Because you know, it's easy to miss warnings You know, when you're the first running through the first time it's easy to miss the warnings because you're surrounded by errors. Or at least I'm anyway.

**Dustin**

Yeah, yeah, I know that feeling.

**Jamie**

Fantastic. I think we'll probably end it there if that's okay, Dustin.

**Dustin**

Yeah, great.

**Jamie**

Absolutely. Fantastic talking to you. Definitely.

**Dustin**

Yeah. Thanks for thanks so much for the invite. I hope you can cut something out of here that would, that would be useful. So.

**Jamie**

Oh, definitely. Yeah, definitely. Yeah. Thank you ever so much. And thank you for so much for being the first person to be interviewed as well.

Transcribed by https://otter.ai


### Wrapping Up

That was my interview with Dustin Metzgar. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and a collection of text snippets from the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/).

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [YouTube version of this episode](https://www.youtube.com/watch?v=jMmaL_NNM_4)
  - The YouTube version of this episode, if you'd prefer to listen there
- [Dustin's blog (Mode19)](https://www.mode19.net/)
- [Dustin on Twitter](https://twitter.com/DustinMetzgar/)
- [The CoreFW GitHub repo](https://github.com/dmetzgar/corewf/)
- [The Microsoft documentation for Windows Workflow Foundation](https://docs.microsoft.com/en-us/dotnet/framework/windows-workflow-foundation/)
- [The Portable.Xaml repo on GitHub](https://github.com/cwensley/Portable.Xaml/)
- The "in action" series of books from Manning are:
  - [.NET Core in Action](https://www.manning.com/books/dotnet-core-in-action/)
  - [ASP.NET Core in Action](https://www.manning.com/books/asp-net-core-in-action/)
  - [EF Core in Action](https://www.manning.com/books/entity-framework-core-in-action/)
  - [Xamarin in Action](https://www.manning.com/books/xamarin-in-action/)
- [XKCD: Workaround](https://xkcd.com/763/)
- [Reference Source](https://referencesource.microsoft.com/)
- [Porting from .NET Framework to .NET Core](https://docs.microsoft.com/en-us/dotnet/core/porting/)
