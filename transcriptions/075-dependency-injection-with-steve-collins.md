### Episode Transcription

Hello everyone and welcome to _THE_ .NET Core Podcast. A podcast where we reach into the core of the .NET technology stack and, with the help of the .NET community, present you with the information that you need in order to grok the many moving parts of one of the biggest cross-platform, multi-application frameworks on the planet.

I am your host, Jamie "GaProgMan" Taylor. In this episode I talked with Steve about what Dependency Injection is, what Inversion of Control is, what an Inversion of Control container is, and how to leverage the built-in IoC container provided with .NET 5 to more loosely couple your applications, making them easier to test.

This is is actually the second time that Steve has been on the podcast. The first time he was on the show was in [episode 49, when we talked about configuration in .NET Core](/episode-49-configuration-in-net-core-with-steve-collins/). There will be a link to that episode in your podcatcher, in case you want to learn about that.

So let's sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

{{< paracentre "The following is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

#### Jamie

So, thank you so much, Steve, for agreeing to be on the podcast again. Well, welcome back. You're, you're in a very esteemed club. There's only you and Steve Smith, I think, at least at the time of recording, who's been on the show twice.

#### Steve

And now just need to get Steve Gordon back in there to triuvirate of Steve's taken over the show.

#### Jamie

I like it. I like it. Maybe we should have a special episode where you three

#### Steve

it's a bit like the three Scotts. I'm one of the lesser of Steve's

#### Jamie

that's it. The three Steve's I like it. Excellent. Okay. So, like I said, you were previously on the show, and I think it was Episode 49. When we talked about config stuff. I think that was shortly. I want to say it was after when we were a DDD North. No, it would have been before.

#### Steve

Just before we were at DDD North.

#### Jamie

That was it because you gave the talk there.

#### Steve

Yeah, yeah.

#### Jamie

Yeah. Yeah, excellent stuff. I do remember, there's some really cool stuff about dependency injecting your config.

#### Steve

Yeah. So that's sort of led me on to sort of looking more into the DI a bit more. So digging in a bit more now hopefully, got some information to tell people.

#### Jamie

Fantastic, fantastic. So for the one or two people who may be catching this episode, and haven't had a chance to listen to Episode 49. By the way, if you haven't heard it, definitely go back and give it a listen. You know, there's some stellar stuff in there. And it's well worth a listen, because that may sort of help inform some of the things we've talk about. And it might be the, you know, the points you raise here will sort of maybe answer some points that we came up with last time. I'm not sure, but definitely go check that out. 

But for the folks who haven't done that, could you give us a brief sort of quick introduction, so that they know who you are who you're talking about?

#### Steve

Yeah, sure. So I'm Steve Collins. I'm a developer based in the UK. Been working with Microsoft technology since the early 90s. Start with VB three, but last sort of few years been working on .NET and .NET Core, and just lately been delving into .NET Five. I tweet @steveTalksCode, and I've also got a blog site at stevetalkscode.co.uk.

#### Jamie

Excellent, excellent.

I think that's, that's gonna be one of the the the strange things about the podcast going forward. Because of what I call the time was at the time, the pod, pod time cast machine, wibbly, wobbliness. We're recording this only a few weeks after .NET Five was officially sort of released to the public. It had been released as release candidates beforehand, but it's now official .NET Five. And it's, it's left me wondering about the future of the name of the podcast.

#### Steve

I did wonder.

#### Jamie

You know, when people listen to this in the future, they're gonna be like, ".NET Core?" So you know, maybe you're hearing it here first, folks, maybe it'll be "The Core of .NET," I don't know, "The Core .NET Show," or something. I don't know. I don't want to I don't want to be stepping on .NET Rocks!'s toes, but maybe maybe I need to. But there you go. I don't know. Not that I could. I could maybe step on the tiniest of the toenails.

But yeah. So for context, for anyone listening, we recorded this, like I said, only a few few short weeks after .NET Five was officially released. So there might be a couple of things that I say, "well, with .NET Core," what I now mean is "hey, with .NET Five." So you know, take that with a pinch of salt, everyone. And obviously, because of the whole "on demand" thing with podcasts. Y'all can listen to this whenever you want. If you want to wait four years, and let's do it that he can.

#### Steve

.NET Ten.

#### Jamie

I know. Right. There you go. Excellent. So yeah.

#### Steve

Or would it be .NET X by then?

#### Jamie

Ooh! That's good. Yes. Or would they? You see, now you got me wondering how they would do it because maybe it will be .NET X? And then 10 years later, it'd be .NET OS.

#### Steve

.NET Cappuccino.

#### Jamie

Ooh. I like it. Yes. The name in the the the .NET version numbers after different drinks that you can get a Starbucks. This podcast is not brought to you by Starbucks, but I like the idea.

Anyway, right. So we're gonna be covering a couple of the couple of the points from a talk of yours recently about dependency injection. And I figured because a lot of people get these sort of terms mixed up, muddled up, sometimes confuse them a little bit. I was wondering, could you quickly talk about the relationship between like dependency injection and inversion of control? Because I have an idea of what it is, and you may have an idea of what it is, and the listener may have an idea of what it is. And guess what, since they're all opinions, they're all right. Because opinions can't be wrong, right?

#### Steve

Do not take mine as a definitive. Go to someone like Martin Fowler for the definitive. But yeah, sure, it does get confusing, doesn't it cuz you got inversion of control, and then you've got dependency inversion in SOLID. And then you've got dependency injection, it all becomes a great big sort of alphabet soup of all these terms that sort of sound a bit similar.

But yeah, so inversion of control, and dependency injection, I think of sort of a bit sort of yin and yang, in that inversion of control is sort of a design pattern or concept, where instead, when you say, "I need an instance of something," instead of newing it up yourself, you say, "I'm going to rely on someone else to give me that instance."

So you mentioned Steve Smith, in the introduction, and he has a phrase of, "new is glue." Because then you're, if you knew something up inside your class, you are stuck with it, you made that concrete. Whereas if you can say, "I want someone to give me that instance," how they give you that instance, well that's kind of up to them. That's kind of where dependency injection comes in. So inversion of control says, "I'm not going to do this myself, I want someone to give it to me." And dependency injection comes along and says, "and here it is."

#### Jamie

Right.

#### Steve

And where dependency injection is nice in the if you want lots of things and things that go into dependencies, it will go and marry up all that hierarchy together and say, "Yes, I'll work this all out for you. And tada, here it is."

#### Jamie

Sure. Okay.

I mean, that makes sense. So my, my sort of the weather, I always think about it is very similar to how you've set it is that I think of IOC is kind of like an interface to dependency injection in that, you know, it doesn't define how it should happen. It just defines what should happen. And then dependency injection comes along and says, cool, yeah, I'll I'll hide the implementation for from you. But when you say like you say, when you say, give me a new instance of something, don't worry about how it gets there. I'll figure that out. Is the new instance. Right?

#### Steve

Yeah. And that's where dependency inversion in solid kicks in because dependency inversion takes those principles, but it adds in the Lair about abstracting out and saying, use interfaces use abstract classes, not concrete, because then you can swap them around, it becomes all testable. And then if I mean, the, the one that's always touted is I'm going to change from SQL server to Oracle, and no one ever does. Yeah, but that's the kind of example that's always touted in examples. Hmm, yeah, I

#### Jamie

once worked at a place where, sorry, I once worked on a project where they said, We want interfaces for everything, right? We're gonna use dotnet framework, but we're gonna wrap everything interfaces, just in case we swapped from dotnet framework to Java. And I'm like, if you do that you got a bigger problem than system dot console dot readline. You know? Yes. So what I'm pointing out there is I think you can take it too far. Like if you're, if you're abstracting around the entire framework that you're using the entire language that you use it, maybe you should rethink it. But yeah, if you're wrapping around, say, Well, I think one of your canonical examples is the same as one of my examples, your system dot data dot Now, if you're using that anywhere in your code, that then you can't test it. Because now is not then and is not the future is always changing. And so you can never write an assertion against that. But let's say you're doing I mean, I'm sure you'll come to it later on. But let's say you're saying, do this thing and give me the time. Well, if you inject the system, dot, dot, date, time dot now in through some kind of interface, or through some kind of dependency version, then you can set that value ahead of time. And then it goes through all of your layers of complexity. And you could check it's still the same value at the end, right? Yeah,

#### Steve

exactly.

#### Jamie

I'm glad I got that. Right.

But yeah, and the other one I always think of is when it comes to like, di and IOC is like, the plug sockets on your wall, right? You don't you don't have to if you buy a lamp, right, you obviously listeners can't see but just off camera, I've got a lamp on my desk. In fact, if I do this, you can see it right. I didn't have to wire that lamp into the electricity source coming into my house. I take this three pin because we're in the UK three pin adapter, plug it into the wall and flick a switch. And all of the magic complexity of getting the power from the power station down the other end of the country. down into the street into presumably a transformer, and then split off into my house and then split from there to the room moment, and then split from there into the wall. And then from there into the lamp, all of that magic is taken away, it doesn't matter how the electricity gets there, I get that new instance of electricity. Right.

#### Steve

And it's interesting you give that example because Steve Smith again, he's coming up an awful lot this episode, I think I forgot what's called I think it's called the calendar or code or something. And one of the one of the months was about abstractions, and the example was the two wires from a lamp going straight into the electricity socket without the plug.

#### Jamie

Yeah, it's, it's, it's a wonderful example. And I sometimes when I was at university, one of my lecturers, Rob miles give an example of an mp3 player. Right? When it comes to abstractions, this is not dependency injection or inversion of control. But a brilliant example he gave was, I have the I mean, this tells you how long ago was right, I have the mp3 player of my headphones plugged into it, I push play, and sound comes out the speakers. That's all I need to know, I don't need to know that when I push play, it starts a File Stream, it loads the bytes in, it then does decompression, to convert it from mp3 into presumably some kind of WAV or something. And then it does amplification and then it does signal processing. And then it sends it over to the sound chip that then does a whole bunch of magic wizardry to turn it from digital signals or an analogue signal. And then it sends it down the way where it gets so that all of that stuff's taken away, because you push the button, you get the get the sound, right? Yeah. abstractions are great strikes. Exactly, exactly. But anyway, we've said all of that. We haven't really talked about anything about what that's what the what I think is great about the the sort of tech space, right? You could, you could say, right, let's go with this sort of almost canonised dictionary definition of something, and talk about the very intricacies of how it's supposed to work. Or you can say, look, we could do that. Or we could talk about any kind of metaphor or whatever, that just any. Oh, my goodness, how long ago was it? There's an early episode of the podcast, where I talk about using metaphors as a way of getting the point across. And it's great, because everyone listening will have understood, because they've just done it to listen to this episode. They've pushed play. And they've started listening to the show, and it's coming out of speakers coming out of headphones. It fits right. When I use metaphors.

#### Steve

I love metaphors. Sometimes I take him a bit too far. But

#### Jamie

yeah, as long as everyone knows that it's not exactly like this. But this is kind of a way to get you to understand how it works, then it works, doesn't it? Right. Okay. So. So I was worried that talking about inversion of control and dependency injection would complicate things a bit. But, I mean, we're both quite experienced in the technology sphere. Hopefully, the folks who are listening get the idea that they are subtly different. But when is it almost like an implementation of the other? And I feel like hopefully, we can we can go on from there. So

#### Steve

to use another metaphor, I think of it a bit like a jigsaw puzzle, where one sides got the hole. And the other sides got the bit that juts out. That's a logical example. One plugs into the other.

#### Jamie

That's it. Yeah, yeah. So then, in that case, then, so I feel like I know the answer to this one, because I've been using ASP. NET Core, or I suppose as the ASP dotnet, five, I haven't really still coordinate

#### Steve

core on they. Fair enough, then

#### Jamie

I mean, it will soon be,

#### Steve

who knows, by the time this comes out? Who knows?

#### Jamie

Exactly, send me a tweet to let me know what it's called. But, so I've used ASP. NET Core to build a whole bunch of stuff. And I happen to know that if I put I, whatever my interface is into the constructor, I'll get an instance of it, as long as I've done some wiring up. So I, I have this feeling that there is dependency injection inside of that. But is that dependency injection? And is it different in some way from say, autofac, ninject? That kind of thing? Or is it just it's all kind of all? What's the phrase, I'm looking for so much of a muchness, it's all kind of similar solutions. And so yeah,

#### Steve

so So if we take a step back before dotnet core and dotnet, dotnet, five, so if we go back to good old dotnet framework, there wasn't an out of the box solution for Microsoft. And that's when you did have these third party and open source ones like auto fac and Castle Windsor and inject Microsoft patterns and practices at Unity, nothing to do with the games engine thing. So you had all these different things, but if you're going back down to real basics, you don't even need a framework. You could create a DI thing in your own right and it's often referred to as poor man's di because what you could do is just effectively have some stuff Some class that sort of says, I know how to create these things, and I'll do it. But you could tie yourself up in knots of very, very quickly. It's one of those things that people set. That's why you sort of see frameworks come in and then die quite quickly. Because it's super complicated stuff under the bonnet. And, yeah, I've looked at some of the dotnet calls implementation and, and so I just don't get this

#### Jamie

thing where you're saying is that, leave the PhDs to figure out compilers, and di and crypto, we could do everything else, right? Yeah,

#### Steve

yeah, we will, we'll just go along and use it. So So whilst you, in principle, don't need a framework, it's, it's good to have one now, as you say, in dotnet, core dotnet. Five, is there out the box for you? Well, I say that is there for you in ASP dotnet. Cool, it's all it all comes part down of when you say I'm using the ASP. NET nougat package, which comes as part of the template, that's a meta package that brings down about 101 different nougat packages, and one of them is the Microsoft extensions dot dependency injection. And within that, you'll, you'll see the startup class and so on. But if you're doing a console app, and I don't think Xamarin does it, you don't get it. Now that you have to go and bring that nougat package in. That doesn't preclude you from using things like auto fac, or some of the third party ones. Now, some of the ones I mentioned before, haven't come into dotnet core world, they've sort of stayed in framework. That's because coming into dotnet core world, that particular nougat package has a set of interfaces, I services, I service collection, and I service provider. Now, a lot of them have come along and play nicely with it. So they that interface sits over the top of their their ones, but they can do a whole load of things that the dotnet one can't and don't doesn't expose through its interface. So Mark Seaman has got books and does talks about dependency injection. And he refers to Microsoft one as a conforming container, which is a posh way of saying it's the lowest common denominator, it does the bare basics that Microsoft wanted it to do. And if you want to go beyond that, you have to go to these other these other container frameworks that, that way you you can get the best of both worlds. So if it doesn't do everything for you, you can watch one of these other ones. But then you're managing to different frameworks, if you want to do anything fancy. Now, in this talk I gave, I show a few ways where you can get around some of the deficiencies of the Microsoft one. So for example, the Microsoft one only uses constructor injection. And we'll talk about that a bit later. But fancy things like property injection, and named keyed injection, these these other frameworks do the Microsoft one doesn't do it. So when I first started with dotnet, core, I was bringing autofac in, and I was actually going you know what, I don't actually need any of these fancy features. So I dropped autofac and just use the uptobox implementation. So that's a long winded way of trying to answer. So yes. If you're in ASP dotnet core world, yes, you get you get it out of the box. So in your programme, you've got a host that has a house builder. And that will go and create an instance of the AI services collection for you, that goes into a startup class fee, right. And you have two methods on there. One which is configure services, and one which is configured. So the Configure services is where you do all your registrations. And then configure is once the container has been built. You can do some more stuff like adding middleware and stuff in once the container has been built. So yes, a lot of it is all all out of the box for you. As I say, if you go and write a console app, then you have to go and bring that new get package in and build the container yourself or use the host builder to go and go and do some stuff.

#### Jamie

That makes sense. I know that they've made a few changes around the used to be, I believe it used to be weapon moulded. And then they changed it to host builder because then moving it slightly away from the web. If you wanted to bring in IOC in serie di into your dotnet console app. You then had to like it was weird. You had to build a web host and it was a bit weird.

#### Steve

Until also enabled you to do things like have the background services hosted as well moving to the more generic host what was interesting was When we moved from core to one into, I can't remember if it was two, two, or it was three that they made that change. But what happened was on your startup class previously, you say, configure services and the signature of that had to return service builder, the sorry, the service provider that you'd have to build yourself, when he changed over, is now avoid, because the host goes and calls the build on it. And that changed how some of these third party was because you used to go and say, now go build my third party container. Whereas now you have to do a couple of different extension methods on the host to say, third party go and build your container instead. So so that was kind of breaking? We're not well, yeah, it was breaking changes going into one into the later ones. Hopefully, now. Now we're in five and six and seven, things have settled down. And hopefully, we won't have many more breaking changes like that.

#### Jamie

Yeah, hopefully, there is another conversation, but it's something I've been talking to other people off air about, then it's like, it's not for this for this show, we will really cover it. But it's like, if if dotnet is going to evolve every two years. What's that mean for the long term survival of your application? Yeah. You know, because like just putting, putting the the DI compositional ones, I will only cover this for another couple of minutes. But like, Microsoft have always prided themselves with it. Backwards compatibility, you know, I know of companies that are running dos applications from the early 90s on their windows 10. machines, because it First of all, it works, right? Second of all to replace it would be way too expensive. But if we're looking at dotnet as as an ecosystem, making drastic breaking changes every two years, that's, that's not gonna sit well with certain

#### Steve

edge cases. Because even the LTS versions, you're only supported for three years. And you're non LTS. You're only supported for three months after the LTS comes out. So yeah. Let's, let's hope they don't break too much. Yeah.

#### Jamie

I mean, that's that's for greater minds than mine. At the very least. I have to figure that out. Yeah. But yes. Okay. So we've got got this idea of a conforming is IOC container system. And you've said that, yeah, maybe the built in one provides 99% of what you need. It feels like, at the very least for me for what I've been doing, maybe I'm not using it and stretching it to its, its its maximum, it feels like it does almost everything I need, you know, I've got, we'll hopefully talk about it later, we've got the different lifetime scopes, and I can inject interface out Sorry, I could I could say say to it, go make me this implementation of this interface. And they'll just pass the interface around. And it just kind of works. Right. Yeah. Yeah.

#### Steve

I mean, we'll probably come on to lifetimes, animated by there are things about the lifetimes, which can trip you up?

#### Jamie

Yeah, definitely. I think I got tripped up recently, because I was using Entity Framework. And I was passing a service around that, that, you know, I had a service that use Entity Framework, and it created a repository and everything, and I was passing it around as a deal. What was it? There's only three it wasn't. So it was it was a singleton, and everything went wrong, because obviously, the singleton will he will talk well, maybe maybe we should talk about anything, right? Yes, my understanding is the singleton lives forever. And if it lives forever, and it's talking to my database, then anything can attack that same database and nothing is acid anymore.

#### Steve

I like to do the Highlander quoted, there can be only one. I like it. And that's how I think about seeing Singleton's in that in that? Well, well, if we flip it on its head first let's let's start with the short lived one. So transients, are your fairweather friends, they just come and go as you as you need them. So if you've got, say, HP dotnet, you got a controller, the controller gets fired up and says I need this business service thing. And it only needs to live for as long as I'm doing something my controller is living. So the transition will get fired up, controller will use it. Then when garbage collection comes along and takes away the controller, then the container will get rid of the transients and it's gone. Down the other end of the spectrum. We've got Singleton the you've just mentioned. And that leaves to intents and purposes for the life of the application. Being pernickety about it. It's for the life of the container so your application could live longer than container but certainly in ASP. NET Core that doesn't really happen. So you've got those two extremes, very short lived very long lived. smack bang in the middle is scoped now. scoped The proper technical term is you associated with a unit of work. Now, in ASP dotnet core, what that unit of work really is, is the lifetime of your HTTP requests coming in until the point the response has gone out. They're not absolutely bound. But that's sort of kind of the analogy of if you're working in ASP dotnet. That's the way to think of it of something scoped will come in, will get created as the HTTP request comes in. And whereas the transient is only injected into, say, your controller, your scoped and your Singleton's can get shared amongst lots of objects. So say you've got several things that depend on that, that same object, whereas transients, each thing will get its own copy of that object, its own instance. Singleton's everything within that scope of that request response lifetime we'll share the same one and Singleton's everything within the whole application will get to share it. where things get tricky is if you're depending on different lifetimes. Now, transients can depend on scoped or Singleton's scoped can depend on Singleton's but the longer the lived, you can't depend on the shorter lived. So what happens is if you try injecting a transient into a singleton, if you're in development mode and debug load, you'll get an exception thrown saying you're not allowed to do this. But that's not the whole story. That is only when you're working with whether your environment is set to development or in debug mode. If you're in production, what will happen is it will merely inject that transient into the singleton at the time the singleton is created. And it becomes what's called a captured dependency. Because what it will do is it it will freeze it. And in my talk, I'll give the example of an insect inside a lump of Amber. Because he eats eats just in case at that point in time. So that transience suddenly becomes a singleton. And likewise, if you inject into a scope, it becomes scoped. So it all gets a bit messy. So when you come to register things, you need to be aware of what your consumers may be, and start registering things at the right level. But then you end up with the situation that you had Jamie, where if you register something with a longer life than it should have a you end up with, oh, I've got this one database call that's gonna last forever.

#### Jamie

Yeah, never gets written to it's no longer transactional. I mean, I have to point out obviously, I was doing is like a, you should never because I was giving a bit of a training and I was like, okay, don't have it. The was it? The short answer I always give people is never use Singleton. Because you're never going to need it. And then and it's like, you remember on the TV show house where it was never lupus, except for that one time, it was lupus. Never gonna need a singleton. except for that one time. You need a singleton? That's a bit but that's my, that's my experience, my experience won't be the same as everyone else's.

#### Steve

Yeah. And and I think I think he comes back to what things do you have talking to each other? What What is that unit of work? Is your unit of work? Just my controller? Is it the things includes the things I'm injecting to my controller? Or is it something I've got across the whole application? Now? Typical ones are HTTP client factory. The factory itself is a singleton, but the things it produces for you are transient or scoped.

### Sponsor Message

#### Russel

Rolling. Action in three, two, one

[bleep]

#### Jay

Hi everyone. I just wanted to give you a heads up on an upcoming episode of the podcast: it’s an interview with one of the developers behind RyuJinx. RyuJinx is a Nintendo Switch emulator, written entirely in .NET Core/5. Right, Squidge?

#### Squidge

And if you’re interested in that, you might be interested in The Waffling Taylors. It’s a blog and podcast about video games, their history, gaming culture media, and video game movies. We even have some interviews with legends in the gaming industry.

[phone vibration and ringtone]

#### Jay

No one calls me these days. Oh hey, what-ho Squidge.

#### Squidge

[distorted through a phone line]

Have you finished that big new feature for the website yet?

#### Jay

Absolutely.

[tpying sounds]

#### Squidge

[distorted through a phone line]

Hang on.

Ah, that's not bad, It loads pretty quickly. It has every episode on it as well.

#### Jay

Thanks

#### Squidge

[distorted through a phone line]

What's this button all about?

#### Jay

Don't push that button.

#### Squidge

[distorted through a phone line]

That aint gonna happen

#### Jay

[yelling]

NOOOOOO!

#### Squidge

[distorted through a phone line]

Nothing happened.

#### Jay

That's what _you_ think.

Waffling Taylors is a podcast all about video games and nonsense. Check us out on Apple podcasts, Google podcasts - wherever you find your podcasts - or head over to [Waffling Taylors dot Rocks](https://wafflingtaylors.rocks/).

So if you want to hear more from my brother (who may or may not be a cartoon wolf) and myself about video games and silliness, head over to [Waffling Taylors dot Rocks](https://wafflingtaylors.rocks/); or look for us wherever you listen to audio.

#### Squidge

And don’t forget that we have tonnes of guests and that we’ve covered over 1,300 games in our show so far.

#### Jay

And we have 110 episodes to choose from, too

#### Squidge

[Waffling Taylors dot Rocks](https://wafflingtaylors.rocks/)

[bleep]

#### Russell

Cut. Print

#### Jay

Was that OK Russel?

#### Russell

It was sufficient. Editing now.

[radio sounds, industrial sounds, bleeps and bloops]

---

#### Jamie

Okay, so yeah, that is interesting. I didn't realise that. Yeah. So you create a, you can create this. Yeah, sorry, because I'm, I'm trying to wrap my head around that.

#### Steve

So So, so you've got a factory class, where you can say, this factory is taunting some purposes, static II eat something that will just go and generate something for you. And I can pass parameters into it. And then the result of that factory, you will just go off and use and for whatever the lifetime of however you use the result of that factory, right? Yeah.

#### Jamie

Yeah, yeah. So yeah. See, that's the thing where I've I've hardly ever used factories. Again, we were talking OFF AIR about I've recently got the Gang of Four. I've used builders almost exclusively. So factories kind of confused me a little bit sometimes. And then people say to me, Well, you know, you could use a factory can use an abstract factory and I'm like, What have we got warehouses now? What's that? You've got factories, factories. This is just blowing my mind.

#### Steve

Well, I mean, I I could talk about factories now, or we can talk about factories later,

#### Jamie

oh, let's do it later give my brain a bit of a job. Because you said there about, you need to think about what your, what your thing is going to be using. And then what you're calling things are going to be using, you know, you said the RAID controller, you've got maybe a business service, and then maybe the business service, talk to something else. And then maybe somewhere down the line, you talk to the database, at some point, you've got to figure out how those all chained together. And you've brought up Steve Smith a bunch times, I want to bring him up as a, there's a project that he has been working for work on API endpoints, you think is fantastic for this, because instead of having like one controller with 12,000, different inject statements, or 12,000, different interfaces, maybe if you've got 12,000 interfaces, you might have to rethink it his own a little bit. But let's say you've got five things coming into a controller. And each one of those injected services is used by different action. Right? That's that's five things that the the DI container has to then somehow magically new up for you with the correct scopes, and the correct lifetimes and all these kinds of things and all of their dependencies dependencies. Whereas like API, endpoints make it so much simpler, because you've got one, almost like one controller with one action, you don't have to have it tied to that. But then you just have its dependencies, right?

#### Steve

And it comes back to the solid principles of single responsibility. Say, say you got under, if you use a controller, you might have the crud action to create, read, update, delete. But for the if you've got four different repositories to do the reads and writes, say you're doing CQ RS or stuff like that. You're having to bring in all those different repositories, just to use one thing. So I'm bringing in all my reader, all my update ones, just to do a read. I don't need it. So it's back to the single responsibility principle from solid.

#### Jamie

Yep. Yeah, that makes total sense to me. And, yeah, it's all about sort of cleaning up and making it easier to read. And like you say, bring those solid principles and make it you've got your, your update endpoint that just has the updating, it doesn't need all of those other things, because then you're effectively you're slowing things down, right? By make it by bloating, your controllers with hundreds of different inject statements. And I keep saying saying inject statements, but you know, we did a bit, all of the dependencies that are injected in by depend by injecting a million different dependencies, you're going to slow down the creation of that controller. So technically, you're going to see a slowdown. So just separate it all make sense? Yeah. Excellent. So let's take a look. So we've talked a little bit about lifetimes. So excuse me one second. So we I brought it up once or twice. And then we talked about factories, we talked about it just before we started recording, do I need to have read the Gang of Four? Now it's in my, I've reached this stage in my career, and I've never read the Gang of Four, do I need to have read the Gang of Four to understand injecting and dependency control?

#### Steve

Not necessarily, because the Gang of Four book has been around since I think was the early 90s, about 9293, something like that. So all the principles still hold valid now. But personally, I'd say if you're coming into it now, by all means, go and read the Gang of Four book, but there's PLU. The ubiquitous Steve Smith has a psycho design pattern. But but there's all sorts of resources out on the internet. There's books that are dedicated to design patterns in C sharp, whereas I think the Gang of Four one was

#### Jamie

Java, essentially. Like I say, I have it here. It's the version I've got is small talk c++. I mean, yeah, I can speak c++. So I get it, but I could totally understand.

#### Steve

So if you're a dotnet, developer, I would say, Go look as Pluralsight course Go, go look at what the dedicated C sharp books. I went back and read the Gang of Four book just because I'm a big geek, even though I don't really understand small talk and c++. But that that was a long time ago now. But sir, certainly a lot, a lot of the principles and I talk about them in my talk. So Singleton is a gang of four patterns. But there's a big difference between a singleton in Gang of Four and Singleton in containers. If you've got a singleton as a straight C sharp Singleton, you have to do a lot of boilerplate code to go and say, go and create the instance. Put some locks around it so that other people can't create an instance limit on creating the instance. So you sort of like the lazy on there to make it thread safe so that only one thing can Go and create it, then you've got to expose a static property that says instance that says I am the singleton. And they can go off and do do stuff. With containers. Pretty much any C sharp object can be a singleton. But with great, great power comes great responsibility to use. You need to be aware of, because you've got that singles, especially if you're using it in in a website, you could be hammered by lots of different rates. It's fine. If your Singleton is a read only thing and it's immutable. It does, it doesn't matter. But if you've got some state in there, like a cache or a dictionary, look up where things might be going and adding and removing stuff. Things can get pretty messy, multi threaded programming of race conditions, it's all be well, I'd say around that is you can put some things like thread locks in and what have you. But then all your threads start queuing up behind one another. So I think very seriously, before you got state in a singleton, if you really must have it. There may be go and look at some of the things that in the base class libraries. Microsoft's got a whole load of concurrent things like concurrent dictionary, concurrent cash, concurrent property bags, stuff like that. If you've got something that's using lists and collections, maybe go and look at one of those to ease your pain of it, but do big d be aware that Singleton's and threading do come with a cost. Okay. So I'm sorry, I'm sorry.

#### Jamie

I was just gonna say that makes total sense. I remember there was a blog post many years ago by john skeet he was like, how to not do Singleton's and it was like every single give you Google Singleton in C sharp. It's every single one of those examples from Stack Overflow on his website like Nope, that's wrong. No, that's wrong, that's wrong. And you should never do it yourself. Because it's so difficult.

#### Steve

Because I think I think he lists about six or seven. And I think when I think it was dotnet, four came out. And they brought out the lazy type. That's when he said, this is how you can do it thread safe. Because lazy gives you a thread safe way of instantiating it because when you look in the i o there's all sorts of weird attributes that sort of says when things can be thread threading, and not threaded, and all all very complex stuff. Whereas I tend to use that last example. Whereas if I'm really must have some kind of static Singleton inside a class, I'll go do a private static read only lazy blog construct it and it's there. But as I say, if you're going into containers, Singleton's very much easier than trying to do all that boilerplate stuff yourself with the book Gang of Four. Other patterns, so we've touched on factory and builder. So the way I look at those is that factory is you know, everything you need to go and build that object upfront. Now, where I tend to use factories with the dependency injection container, is say, I've got some old class that has just a parameterless constructor, and I've set properties that I have to say it. And then it might have an init method that says, Now go and do all the stuff and put it together. You can't really do that with the Microsoft do container because it doesn't support property injection. But what you can do is if you write a class, we say, I will go and get those things from the container in my constructor. Now I can go new up that that other thing, go set the properties in it, and then return it in my create method, for example. Well, that's also useful if you've got so for example, say you've got you want to say, go create instances of food, for example. And now, some properties might be coming from the container. But some properties you might not know until you go and say I want one of these. So a restaurant app, the container knows all the ingredients to go and make a hamburger. But you don't know till runtime whether you want wanted. One Patty, two patties are three patties.

#### Jamie

Right? Yep. Obviously, some of them are indeed with cheese balls. Oh,

#### Steve

yeah. So so with that the factory method Say, I will go and get all these bits out of the container. And then it's up to you that says, you can pass in some parameters to your create method. And it can then go and put it together. That's your factory. builder, on the other hand, is more of a continuous state for want of a better phrase, where you sort of say, here's some foundations. And now I'm going to add these extra bits on top added. So quite often, you'll see them expressed with a sort of fluent syntax. And certainly in a good example, is the host builder. In dotnet, C will say, here's my host builder. And now I'm going to add one of these and I'm going to add one of those and I'm going to add some logging, I'm going to go to the good figuration build, and it comes out at the end, and the the dot, the dotnet. Di container itself is effectively a build pattern, because you got your services collection, where you go and say services, add all these services, and then say, build service provider. So there's a slight difference between between the two. Now, that's what I quite like quite like factories we di because you could say in your construction of a controller, go and get me one of these. But if you're relying on some parameters that are coming from your HTTP request, with a container won't know that. So inside your control, you could say, well give me the factory that knows how to build one of these things. And I will go and pass you the bits. I now know from my request, factory go and put it all together for me. Right, I say? And because your factory is just a recipe for building something that can be a single turn, because it doesn't need a new one of those every time because effectively. It doesn't have any state. where things get tricky is if some of the things you're relying on in your factory coming from the container aren't Singleton's, then that's where you things get a bit a bit messy. But there's ways and means rather, which we'll come on to a bit later.

#### Jamie

Sure. Yeah. Because otherwise you end up with that. Was it the captured? Yeah. Okay. So you might be thinking, well, this, this, this service on pulling into my Singleton is transient, and it will go away, eventually it will come back. But no, because the singleton exists forever. Effectively, that instance of that transient exists forever, or at least until the singleton is gone, right.

#### Steve

And a good example of this is middleware in ASP. NET, because when you register a middleware, the actual middleware itself is gets registered as a singleton. But the operation itself, the invoke is called as part of the ASP dotnet. pipeline. So if you've got a dependency, and it's scoped, or transient, and you put it in the constructor of your middleware, then you've got a captured dependency. But because the invoke is dynamically created through reflection, you can add your transient or scope dependency to the end of the invoke signature, and you'll get the correct transition or sculpt coming into the invoke. So that so there's a slight so being aware of, and certainly the middleware one trip me up very early on in dotnet core, because I was going I don't understand, because we talked about configuration in my previous episode, and we talked about options snapshot, an option snapshot gets registered as a scoped that was injected by option snapshot into it again, but this is changing, because I was putting into the constructor instead of the invoke. Right.

#### Jamie

Right. Because Yeah, the constructor creates you, like you say, that Singleton instance. And because the singleton is passing, they're just saying what makes me sound smart. But if you've got that Singleton instance of the middle where class itself, and you're passing in a transit to the middle away instance, then the transit will be or indeed scoped will be captured at the start of when that Singleton is created. And that will be the instance you get, whereas if you're passing in to invoke because it's, again, I'm just parroting back but I'm learning, right? Because you're passing the instance into the invoke method, which is created at runtime via reflection, you could pass in today's this moments instance of this transaction, not the instance that you're passing into the, into the actual middleware. Yes, interesting. I would, I think I would challenge people to go try that out, create some kind of middleware that takes in something maybe a configuration snapshot in the constructor, and then pass it into the invoke fire. In this each section as well, and see what the differences are, because I think that's, that's an interesting experiment to do and to learn a little bit more about it, because I can see in my head our work, but not many people learn through audio. So go go do it, I guess go give it a try and watch it happen in front of you. That's, that's interesting. Okay, so now you've just blown my mind. You can have a captured, captured dependency, this is not the same as the instance dependency, right? Oh, there you go. Right. You don't have to deal with configuration, do with date, time dot now, do date time dot now and pass that in to your middleware through an interface at the time of creating the middleware, and then wait a little while, pass it in, in the invoke stick a breakpoint and compare the values, they'll be completely different. I like it. I mean, that example is useless for real world stuff, but it will give you an idea because they don't know always changes, right? Or does it? Yeah.

#### Steve

It doesn't change in a unit test.

#### Jamie

Well, that's it Well, hopefully,

#### Steve

what that's what, that's what we'll come to.

#### Jamie

So, okay, so I know that this is something that comes up in your in your talk a little bit, and it's something that I've always fallen over, right. So we have this idea of registering these dependencies, right? So you said in your configure method, you say, hey, add this, add this as a scoped add this as a transient, add this as a whatever, or, you know, add these interfaces, you know, if you use interfaces, this interface and point to this concrete thing, or this interface point to this method, which creates the thing. So what about if I have a list of things I want to add into I register with my dependency injector. And the list is as long as my arm I might trapped in this purgatory of like, an hour, these Apple these? Are these, like doing it manually? Or can I just say, go over here and figure it all out?

#### Steve

If you're a control freak and a masochist like me, yes, you will go and manually go and add them all in. But that's me. There are tools out there, I think the most well known one is scooter. And what that can do is you can define rules that sort of says, go and go and look at this assembly, and go and get all the types that match these rules, and go and register them as Singleton scope. transients, go and register if they support multiple interfaces go and make sure you can register them all against the same that all the different interfaces that they support. screws has got a nice thing. We talked about design patterns, just now another design pattern is the decorator pattern. So say you've got a class that you haven't got the source code for. And you want to see all the calls being logged as they come in and logged as they come out the decorator, what you do, if it's got an interface or an abstract base class, then what you can do is re implement that interface or abstract, inject the, the original thing that you haven't got the source code for, and they sort of kind of acting as a proxy, but with added functionality. So as you say, you may have a method, say hello, then the original thing just returns Hello. But your decorator can say my say hello says go and log someone's asked to say hello, go and call the thing, get the return value, log what it returned. And now return that Hello. So that's another thing. Now doing it yourself, you can do it all manually. But it gets a little bit messy screw you can, you've got a couple of fluid extension methods where you can effectively say, Go and take this thing and go and decorate it with my thing. So there's a couple of out others out there. But screwdriver is kind of the best known. I think there's a happy middle ground, depending on the size of your project. If you've got 101 different objects that do very similar things, and they will all be the same lifetime and they are very basic. Go ahead and use something like screw to lock yourself out. But if you're a control freak, like me, and you because when it comes to trying to go, this thing's not injecting as I thought it was going to inject, then you've got that extra layer of abstraction as to what how did screw to do it. Because once once you've got past the service provider and next injecting things, you don't have a way back to the original services collection to see how things were registered. So it becomes a bit tricky. Now I think since core to two I think there is some logging that tells you about registrations in there. But he did and this is why I'm a bit loath to use. Something like that, unless it is some middle ground where I can say these things. I really want to be in control of these things there. I don't really care. Just go and register them for me.

#### Jamie

Okay. Okay. I mean, that makes sense, right? We're all about productivity. We're all about trying to make things easier. There'll be something out there that automatically does it. But I think I think I fall into the camp similar to have a case of, yeah, it's, it can be a bit annoying to have to go dot add transience of this to this dot add Singleton of this to this and don't add this or don't add that. But again, you know, you know, at compile time, exactly which scope that I keep saying scope, I feel like it's more lifetime. But you know, at compile time, what the lifetime of that injected dependency is going to be right. So that you can have in your mind, where I'm injecting This is a transient. So which means that these things are going to live for as long as that thing, or I'm injecting one great big whacking Singleton, and I've got all of these things. So these things are being injected in, and they're not going to be the same instances of those things over there. And you can make that decision that sort of informed decision ahead of time. Is that a good idea? Or is that not? Because there will be legitimate cases? I guess? We're having a singleton make sense. Yeah. Okay, and I guess perhaps the, these automatic libraries, they probably do the best they can to figure out what there needs to be. And sometimes, you know, machines get it wrong sometimes.

#### Steve

Yeah. I mean, I think it comes down to how you define the rules of games. Good. And I think you're gonna have some edge cases where you might have conflicting rules that somebody might get registered twice. Yeah,

#### Jamie

that's fair enough. And I mean, like, what I tend to do with my with my code is I have a loads of extension methods all the way down, right? So I tend to build an extension method onto I think this is more dotnet core to the lifetime of the services provided for when you're injecting your services. And I would, or is it just is it whatever it was, I think, is I services, and I will do another method called transients. And that's where all my transients would live, add scoped. And that's where all my scopes live. And then you know, from the name of the method, hey, I'm adding this business logic service, and it's going to be transient, or it's going to be this, it's going to be that. So you know, when you're digging into startup, you don't you're not looking at 5000 lines of ad savings, you see any relevance,

#### Steve

it comes back to the clean code principle. So say, Okay, I'm going to group all my repository, registrations together, I'll group all my service registrations. Here's where I'm going to go and do my HTTP client conflicts, break them all up into smaller functions. And then, and there's nothing nothing to stop you writing a unit test that goes and takes your starter goes and takes if they're public, goes and pulls them out individually, says, here's a collection, go and build it. And now, do all those things resolve as I expect them to resolve?

#### Jamie

Absolutely, I've done a similar thing. It's completely different technology. But I've done a similar thing with when I've used auto mapper in the past. Whenever I'm, whenever I'm using something like auto mapper, I like to write a test around it. And say, because one of the good and bad things about things like Automat because it uses reflection, is if it fails, it only fails at runtime, there's no way to test it unless you throw a test on it. And then you can run through the tests a million times a second. And they'll pass or as soon as they fail, you know, before you've even wrote have not moved on any just stop maybe red green refactor, or is it tests and commit or reverts or TCR. So then you get a chance to sort of take a step back and go, what are broken? Right. I'll go and fix that, you know. Excellent. Yeah.

#### Steve

It'll be interesting to see what you mentioned about using reflection about the new source generators in five is to weather things like that. Do a lot of reflection, start using source generators to actually go and build concrete.

#### Jamie

Mm hmm. Yeah, that would be interesting, because then that would be easier to test though. And then you've I mean, you could physically test it by going go and build it as the code right. Read through it. Right. Yep. That makes sense. Yeah. Interesting. Okay. We have talked about unit tests quite a lot. And we do use, I know, for a fact, we unfortunately, I'm a little busy today, we're running out of time, but we I would like to talk about when I'm writing my unit tests, and they have some kind of injected service. You know, I've got some, some eye service coming in. I know that I want to mock that service is mocking similar to dependency injection, or is it just a case of is a wrapper? I mean, do you know much about this, you may not. The way that I understanding is, if I'm using the the nougat package and mock ml Q, then that's probably that all that's doing is creating like a proxy instance. surround it. Yeah. And I define what the each method needs to do. And if I don't define it, it doesn't exist. And it just, that's not it doesn't exist, right?

#### Steve

Yeah. So this is back to the inversion of control in the, instead of my di container, giving that instance, walk is generating the instance. So and this is why it's so so crucial to have abstractions be interfaces or abstract base classes as the signatures on your constructors, because then your thing doesn't care what the implementation is. It just says, I know I've got that contract, and it will do what I'm expecting it to do. Send me your mock your own handcrafted, mock, which funnily enough I was doing today, I was writing a whole load of handcrafted ones, because I, I had to do some stuff where I was testing how many times something was called in certain conditions. So I ended up handcrafting one. But because I'd passed in an interface, my di container would say, oh, here's the runtime thing that goes off and talks to Redis. But I wanted to test that, well, if Redis comes back, and says nothing's here, or something's gone wrong with threading, and it's called Redis. And I've got a corrupt thing. How, how do I deal with it? So I had my own handcrafted mock

#### Jamie

That needs its interfaces and abstractions all the way down, isn't it? I have, I have wondered about reading through things like the ASP net dependency injection, because I've got a feeling it's going to be injecting a lot of dependencies itself. I go, what point do you get down to?

#### Steve

So classic one is the HTTP context, context. accessor, which is a strange hinterland of a class in that HTTP context, is scoped by HTTP context. accessor allows you to get to the scoped HTTP context from inside a singleton, because it's doing some weird stuff with async context, which is a bit like thread context. But it sort of parses it all down. So when it goes off on an async, and goes off and does something comes back on a different thread, it still transfers it to a new thread. And that's this sort of strange hinterland where you can kind of have these thing that gets to a scoped from a singleton. We really does say, bend your head a bit.

#### Jamie

Yeah, I can only imagine just how, because like the like to, before this conversation, that would have made perfect sense. There is a sculpt over there. And I mean, there's Eagleton not abrupt But no, you're saying earlier on you were saying because the singleton it captures its its bother what was it captures its dependencies? Yeah, that's it really is it's captured that dependency, but then in this is the ICB context accessor is accessing it from it's not the captured version is

#### Steve

what's happening with somewhere along the pipeline. Hmm. It's putting this HTTP context into the async. thread. Sorry, the async context, right? Yeah. So so it's all gone outside of the DI container and saying, it's over here. Right. And now, anything can get to as long as he can understand that content. I bent my head when I

read through it.

#### Jamie

Yeah, I'm sure what it sounds like it's already doing it to me. You're describing it the fully understood version. And I'm like, I don't have a clue.

#### Steve

I don't promise I truly understand it. David Fowler might be listening and shaking his head. I

#### Jamie

mean, if David Fowler was listening, I don't mind. Okay. Um, so, sort of wrapping up a little bit, then. Do you have any quickfire tips? I know, I know that before we started recording, you were like, I got loads of tips. But maybe

#### Steve

I was Jamie. I could talk for hours. So So yeah, we've talked about factoring builder patterns. Be aware of when you can use them is a good one. middleware we touched on Be aware that middleware is created as a single turn use the invoke to pass in less escapes.

One that not many people know is that you're not just limited to interfaces and classes, but the DI container.

You can't register value types. records you can register but there's kind of no point. But you could register a factory to generate records, but the one people don't really think about is custom delegates. So custom delegate is actually a function definition. Yep. So going back to our example about date time now, now we sort of said, Well, you could have an interface and have a method of get current date time. So your concrete implementation would have system date time now that your mocks in your unit test could just say, just this fixed date, time. Yes. But that's a lot of ceremony of having to go and create an interface and a class just for one method, you could just have a custom delegate that says, I've got this function that doesn't take anything, but it returns the current date time, just one line. And then in your startup class in, you'll configure services, you can just have a lambda that says, if if someone asked for that function, return date time now. And then someone executes that function in their consuming class, and they'll get the current date time. So you've saved having to write an interface having to write a class, you've just got it with one line of code, well, two lines of code one to define the delegate and one to register it. So it's quite nice one that one leads on, it's on my blog site, because it's quite complex to explain, but named dependencies, you can't do them in the dotnet. Core one, but you can have like, the likes of autofac, where you can say, I want to, whenever I say, I've got a dependency called Steve, I want you to go and get one of these. But if I've got, if I pass in Jamie, I want a different thing. You can use the custom delegate that says, Take a string, and then go into this lookup table inside this other class, and go and get me the appropriate instance, just based on a string. Sure. So so it's on my blogs, blog sites about about that, cuz over audio, it's very hard to describe that one. My my last one is we're short of time is trying not to inject I service provider. So I service provider is the the the general interface to the dotnet core container. And he's got methods like get this, get get service, get required service, things like that. The reason I say that is because it's a service locator pattern, or rather service locator anti pattern. So long before we hit the frameworks, I talked about poor man's dependency injection, and you heard a static class that knew how to construct everything. And that was the service locator. But over time, that went from being a pattern to an anti pattern. Now, by injecting by service provider, you're placing the responsibility of your consumer to know how to use a service provider, whereas the consumers are just really say, I want an instance of I business rules, for example. And when when it comes to locking it in your unit test, if you're having to mock ISOs, Brian, you've got to build a service collection, you've got to then build the provider to then pass that in, just to go and get this dependency. So try and avoid doing that. The exception to that rule, the classic It depends, is if you've got a factory, or a builder, which may need to use that go and grab some things of runtime, depending on the appropriate lifetime. The caveat I put around that is if you've got those classes, possibly make them private inside your startup class, because startup classes wherever, wherever I service collection and service provider. But if you put them inside there, your implementation of that factory that uses our service provider. The outside world doesn't know about it, because it is private to your startup class. But if you're exposing your factory through AI, service factory, then I service factory will say, I'll go and give you my hamburger. So I should have said I hamburger factory.

#### Jamie

Yeah, of course.

#### Steve

But you get the idea of where I'm trying to cut come from. So yeah, that's my last tip. I have got 101 other tips. But we're short on time.

#### Jamie


Well, I mean, perhaps that's an idea for a blog post, right? And then we can link to it from the show notes

#### Steve

we can do when this comes out. Hopefully I'll have a whole raft.

#### Jamie

Well, that's a series of events 101, that's 10 Top 10 tips for dependency injection. A lot of the content they

#### Steve

get on by the time this comes out.

#### Jamie

Well, we'll soon see well soon. See, unfortunately, like you said, we are running short on time, but I'm just wondering, could you let the folks who were listening know the best way to keep in touch with you.

#### Steve

So if you want to keep in touch with me, I'm on Twitter at that Steve talks code. As we've just said, I've got Got a blog post at Steve talks co.co.uk. If you're interested in stuff we've been talking about, I do do a talk. I've been going around the various user groups in the UK. There is a recording of it that I did for dotnet. Southwest on their YouTube channel when I'm sure Jamie will put the link in the show notes.

#### Jamie

Certainly. Excellent. Excellent. Well, thank you so much, Steve. This is the thing every week we get together and we talk about one - I say to you, "let's talk about this one very specific topic," and we end up going everywhere and rapidly running out of time. But I think I think that just shows how much fun it is to get together and talk about these kinds of

#### Steve

Great catching up with you again, Jamie.

#### Jamie

It's been great catching up with you too, Steve. They gave us so much.

#### Steve

Okay, Thanks, mate.

#### Jamie

Thanks.

{{< paracentre "The above is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

### Wrapping Up

That was my interview with Steve Collins about Dependency Injection. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/), and there will be a link directly to them in your podcatcher.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice - head over to [dotnetcore.show/subscribe](/subscribe) for ways to do that - and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Steve on Twitter](https://twitter.com/stevetalkscode)
- [Steve's website](https://stevetalkscode.co.uk)
- [DDD events](https://www.developerdeveloperdeveloper.com/)
- [Interface Segregation](https://en.wikipedia.org/wiki/Interface_segregation_principle)
- [SOLID principles](https://en.wikipedia.org/wiki/SOLID)
