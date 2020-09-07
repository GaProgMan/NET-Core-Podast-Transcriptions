### Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is episode 60 Uno Platform with Jérôme Laban. In this episode I spoke with Jérôme about precisely what Uno Platform is, how it's more than just an alternative to Xamarin, and how you can use it to build cross platform UI-based .NET applications which leverage all of the APIs that you have come to love and expect.

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

{{< paracentre "The following is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

#### Jamie

So the first thing I like to say to him is Thank you ever so much for taking some time out of your day, I realise you're a very busy person. We've just had msbl you just did loads of demos and stuff. And it's almost middle of the day for you is kind of late and late afternoon for me. So totally appreciate you taking the time. Thank you so much. You're welcome. So, for the folks who may not know about you, and especially, you know, by phone, could you tell us a little bit about yourself and a little bit about uno platforms? Oh, please.

#### Jérôme

So my name is Jérôme Laban, I've been a dotnet developer for just right before dotnet appeared. So probably early 2000 something. So I've done some new lots of dotnet and I've been doing lots of dotnet since then, and quite recently, to see the past six, seven years. So I've been working on the new platform, do you know platform is just about doing zamel in C sharp everywhere, basically, pretty much. Almost everywhere we go we're missing one target yet, but you know, it's it's gonna be there as soon so It's all about just doing this. And it's about using the zamyla comes from when UI. And especially when you're going through the Microsoft announced a new preview build. And the idea is that it's all about reusing skills, and you develop using Windows and pour that over to iOS, Android web assembly specifically. So that one, new was a lot of interests for many people. And as of last week, Mac OS week before, so, Mac OS, so it's, it's lots of it, lots and lots of interesting things that are happening. And in that direction, especially with webassembly. And we have I can probably talk about that one. We're working on some amazing new things that are coming out of the mono team. And yeah, webassembly all the things.

#### Jamie

It does seem to be the new technology that everyone's really glommed on to, you know, like 510 years ago, it was Bitcoin three, four years ago. It was microservices. And now it's everything has to be web assembly.

#### Jérôme

Well, it's it has to be but no it there's there's a, let's say there's a good reason for it, especially for work push for the fact that, you know, previous technologies that were in that direction were not that great. If you're talking about not not that technologies that sell themselves was not great, but that's the integration with the rest of the ecosystem were problematic. You'll civilise flash, Java applets x baps if you're remember those. So all those technologies, you know, they were single vendor for most of the time they were security holes, because of the way they were interacting with the rest of the ecosystem. They were blocked by Apple by running on iOS and now iPad OS. And the big difference is that because it's a secure, it's running, it's on it's in its own security sandbox knew everyone's going in that direction. And for those who don't know about webassembly webassembly is about high level getting all languages and runtimes to run inside of a browser. Or instead of a security sandbox that's outside of the browser as well. So we're getting, we're getting I think it was digitalocean. And other big companies that are using that to, to allow for their customers to run code on the edge of their networks or in specific nodes that that network without having to, let's say, have any concern about what the programme that's running, that's not there's my do new outside of that sandbox. So that's the kind of thing that makes it very interesting. And for the browser, it's all about just, I can deploy whatever I want. If I want to use COBOL, or any kind of language that may be able to target webassembly, then it can deploy literally anywhere, because most major browsers, mobile or desktop or IoT, they just do TVs for that matter, even TVs run web assembly now. So that that's where it gets interesting.

#### Jamie

It's really interesting to think that, how do I put this Not that there's anything inherently wrong with JavaScript? It's just I no longer have to use that right? I can Do C sharp I can do like you said COBOL. I could do Python I can do yes go whenever I want

#### Jérôme

so many languages, there's no there's not a day without any new language that targets the luggage target of language or runtime targets the the webassembly. And it's still it's in its infancy, there's many things that are not there or new that need to be improved for many kind of reasons. But yes, the the, the fact that you can reuse any kind of language, or you can reuse any kind of library that that was developed and is not essentially bug proof. But let's say you bug free in some sense, but you don't have to redevelop it. And you know, if the idioms of JavaScript don't fit the the needs of the things that you're doing, especially one that's that's big as the threading stuff, you know, threading is hard, but it has its advantages. So, so things like new compression libraries and video compression libraries that may run into browsers or new things like No deep learning or anything that needs to have lots of CPU power, and we have lots of CPUs, and JavaScript is only one. If you want to do multi processing, you have to go web workers. But no, it's not. It's not always the easiest. And if you have code that uses that, use it threading properly. Web assembly is one thing to do.

#### Jamie

Exactly, exactly. I can really see why everyone's getting so excited about it. And not just in the other ecosystems, you know, we now have the laser. So yes, like dotnet in the browser, because of because of web assembly and the wonderful work that mano, we're doing the Monaro team are doing to sort of implement all of that it's absolutely wonderful just to see all of these lots of different technologies coming along and just making the choices that we make as developers and now almost limitless. Exactly,

#### Jérôme

exactly. And, you know, one thing that that's been very interesting with regards to you know, being able to develop applications on many and many platforms is the Facts attach. It's a big witness for web assembly and the web specifically. But it's also the lack of, let's say, marketplace. And so it's a problem. But it's also a blessing in some ways, or an advantage. Because that means that that you're going to be able to publish your application on your terms, not on Apple's or Google's or Microsoft turns your or whatever platforms that you want to target. So and that's, that's a, that's a big thing. Because you can choose whatever you want to do. And if you want to promote anything inside of your app, and no one's going to prevent you from doing this. So so that has its advantages in terms of deployment, whether it's public in terms of new deploying the web directly or internally because you have new security concerns or new kind of reasons for that kind of thing. So it makes it very interesting and refer to the new platform. We've been seeing lots of people there that were in the in the civilised space and in They were developing their applications out of the browser. And they saw that the deployment model was was a fit for them. And they see it kind of the the light at the end of the tunnel, because we know is able to do that kind of thing. So blazer for that matter. So it's just about choosing what kind of technology you're going to be aiming up because of the type of developers that you're having or the affinity you have between different technologies that are available.

#### Jamie

Absolutely. And yeah, it's just, I think I was talking to Chris Sainty, not so long ago, just in DC, and he said, it's great because I no longer have to go right. I need to find a bunch of people who are experts in you know, we're saying blazer, right. You don't have to pick find experts in JavaScript. Because somewhere down the line in the last three years, somebody decided we're going to do Angular or react or whatever technology you need to then go find those experts who maybe have experiences outside of your own. And, you know, they can then say, Well, you know, you were using this technology and it's maybe two years old, I want to be paid more you get into that weird politics situation. Whereas if you're all using the same technology, just totally different, essentially a different build agent, pretty much. Yeah, you're all doing the same stuff. So anyone can debug anyone's code, right?

#### Jérôme

Exactly. Yeah. Being able to reuse the status, the same skill set, even if it's, you know, it has its advantages and disadvantages, but the fact that you can reuse the same programming language in techniques and your same set of people also, it has, it's very appealing.

#### Jamie

Sure. We've talked a whole bunch there about sharing the sort of skill set and reusing that sort of skill set. And I feel like that's very much the background towards in our platform is that, you know, this whole idea of writing wants to play it everywhere, kind of thing. Is that is that is that the idea? I mean?

#### Jérôme

Yes, it is. It is. was actually born out of this. So a few years ago, we're talking to you. I think it was right after windows eight, something I don't remember exactly the date. But the idea is that we were at so adventive, the company that that started the platform. We were developing applications for new for Windows devices. So windows eight and Windows phones at the time. And our clients, they said, Well, you know, you're able to do some fine applications using your windows. So why don't you help us do applications on iOS and Android. And we took a look at at doing that kind of development. And we took the route of using Xamarin, Android and iOS directly. And the biggest one that we found out at the time was that because it's iOS and Android, specifically, you have to have two sets of developers in two very different sets of developers. So sure, you have C sharp, that's the same, but that's it, you know, and the rest so you can share or you know UI code, but you know your white coat if your applications Whether it's a non trivial, then, you know, it takes you experts to to do things specifically for the for those platforms. And we made a few experiments. It was not No, let's say not enough in terms of velocity. And we said, well, we have lots of developers at an attempt, they do know how to do zamel in C sharp. So let's try to do the same thing for iOS and Android directly using Xamarin. So what we started to do, and basically just pileup tech on top of Xamarin, Android and iOS directly in Xamarin Forms, and it existed at the time. And we started developing that and one thing led to another we had something that started to work quite well, and enough of the needs that we had for the clients at the time. And, and you're we push, push, push, and then webassembly came out. And we said, Oh, that's that's very interesting where we can do with all that. So let's, let's see how we can how can we scale even more, and we can't keep that gem just for us because it was private at the time. And two years ago, yeah, two years ago. Now. We opened sourced everything and moved to a Red Hat model for for financing ourselves. So basically, that our clients are paying us to prioritise the backlog in some ways. That's pretty much what it is. And that that's the way we use to, to continue developing furuno. And we were taking contributions from from people, so it's free to use and then if people want to have you know, certain bugs fixed or or influenced the backlog, then they can come to us for professional support.

#### Jamie

Excellent. Okay. So you talk there are a lot of there's there's several layers of things that are going on, right, you said, there's Xamarin, that you sort of building on top off, and the use of zamel, and things like that. And it's been a while since I touched SAML, so you'll have to forgive my ignorance. I do seem to remember that there was, who was a conversation I had about a year ago, where somebody was saying to me, there's no zamel standard. There's no standard for zamel No, there isn't. So how do you get around that then if there's no standard How zamel should work across all of these different environments? How does that work?

#### Jérôme

Well there there's no sample standard and new zamel standard in some ways, it's kind of a, your Microsoft way to to make sure that they try to align the different zamel flavours that they have a mute a few counts, there's probably at least four I think, you know, there there was WTF then there's, there's Xamarin Forms then there's Silverlight and then different sillars favourite Silverlight me with different versions and then then then there's when you were Are you WP? So it was all about getting, you know, an alignment of all this and you know, for some reason, I don't know about you know, it didn't it didn't go forward. And what we chose at the time because I went for several reforms wasn't there was to say well, the when you want one WWE one or the one that was using Windows Phone was developed properly to be able to Target all those devices that were going from Windows Phone up to the very large screen that are in the surface, I don't remember their names, but the bigger the bigger ones that you can hang on was. So those devices were the API sets from we knew I was developed with having all those considerations in mind at once. And that's why we took advantage of that. And so we don't have to follow any standard, because we follow one API set specifically. And, and to give you an idea of that, we have a so inside of the uno itself, there's a process that we have that runs almost all the time now, which takes the API set that comes from your WP admin UI, and generates a set of gigantic amount of C sharp files that contains all the classes that comes from those both those two API sets. So that means that in terms of compatibility, where you let's say Almost 100% compatible, you know, there are a few things here and there because of the competitive view with iOS and Android. But that that's pretty much what it is. So there's no, there's no standard per se. So now in terms of stacking, if you will, on iOS and Android and Mac OS we're using as we're we're calling Xamarin native, which is the bare API set that allows to access iOS and Android, and Mac OS. And then on top of that, we're putting all the controls that zamel provides, like grid stack panels, text blocks, list views, and things like that. And we basically were implemented all of those on top of iOS, Android and Mac OS, using Xamarin. And so that means that we can basically integrate anything with anything. So if you have a native control, we can put that native control directly inside of the of a of a stack panel or a grid, if you will. It's the kind of integration that you can have. And the biggest thing that we chose to do with it, the biggest reason we chose to do it that way is that the guideline was to Avoid to be stuck inside of a sandbox that you can't escape. So there's always an escape hatch. So if you can't do something, or just use the platform directly, who knows not who is able to provide some abstractions or implementing common implementation for all platforms if they exist, but if not, just go to the platform and do it by yourself. So you don't get stuck in some weird news section where you can't get out of your specific scenario. That's for iOS, Android, Mac OS. And for web assembly, we're using bare mono. So the same model that blazer uses, we're doing basically the same thing. But instead of using iOS, we're using so web assembly to execute most of the code. And then we go to JavaScript, CSS and HTML to do the rendering. So that's what we're doing for that section.

#### Jamie

Where they see that could be so much stuff, right? Because one of the things I was going to say is, well, building a UI framework for a single platform is really difficult. Oh, yeah. Essentially, what you've done is you've created a UI platform. For them all.

#### Jérôme

Yeah, yeah, well, actually, not all of them were missing just one we're missing Linux. And, but it's coming. It's coming where it is coming. It's coming. We're, we're, we're doing some experiments in there. And we have multiple, multiple directions we could take, but basically it would be something like using skia for the rendering engine or GTK. So we're going to be making some making some changes inside Uno's to to allow for different backends to or rendering static strategies to, to be to be developed. And we we've been doing some things around Linux, and it works still, with the proof of concept that we made, it works. We get real, we've been able to, we've been able to reuse some of the controls from the windows community toolkit and make them run on a Raspberry Pi using using Windows. So that's the kind of things that we're able to do.

#### Jamie

Wow, that's amazing. Wow,

#### Jérôme

that is that's a lot of fun.

#### Jamie

I can imagine it is thank you this windows only component going hey, this really Not to not to say I'm a big fan of the Raspberry Pi not to take away anything from the Raspberry Pi. But hey, this is a single board computer with not that much power. Although I suppose Raspberry Pi four has enough power to be a desktop replacement there. And you're going here, I'm just going to take this windows thing and dump it onto a Raspberry Pi, which is running

#### Jérôme

Raspbian ears running Raspbian. So yeah, it's running Linux using dotnet, core five and all that so and test I made the test I made was using a I think it was a Raspberry Pi three B plus. So it was it was a smaller one because the four is quite quite beefy. And it's uh, you know, it's, it's running quite well. So considering the type of device it is, and you know, the dotnet core falls, folks have been doing your leaps and bounds in terms of improving the performance there and yeah, so expect quite a few things from you know, with regards to what what Linux is able to provide.

#### Jamie

Wow, that really is amazing. Because Yeah, like you said, you practically got all of those platforms. I mean There's a few things that Xamarin can target now, through the ties and devices, yes. Can you target those as well? Like, can you

#### Jérôme

not? Yes, not yet. So Tyson Tyson is a difference. It has to have specific support. And I think for that the I think, yeah, the Tyson team just integrated directly with Xamarin. So know that it has to come from them somehow. But if there's interest, I mean, it's open source. So there's probably someone that will at some point, add support for it somehow. If there's a there's a need there. But no, it really depends on the type of things you if you want to run on TV or Tyson or you webassembly is there still so kind of a Can you can go both ways. There.

#### Jamie

You see, I see. So all we need is someone from Samsung to feed feed off onto the open source repo how to get it to work, and he'd be good to go right.

#### Jérôme

Well, there are so so that that's where that's where we have to work a little bit. So that's why the Linux proof of concepts is not it's still not out yet. We still need to restructure a little Bit of the things and especially with dotnet, five, target timeframe, they're making lots of changes in dotnet, five that will allow us to make all those integration easier to work with. Because at this point, it's not new. It's a bit, there's a few things that, especially with dotnet standard, and all that makes it a bit more difficult. But without that five, it's going to help significantly So, so yeah, it's, uh, you know, next few months are going to be interesting.

### Sponsor Message

I'd like to take a moment to tell you that this episode is sponsored by Datadog. Also stick around for the next 30 seconds to find out how you can get a free t-shirt!

Datadog are a monitoring and analytics platform which monitor your infrastructure, application performance, and log management.

Are you looking to move to the cloud, microservices, or .NET Core? Datadog can help with that. Their distributed tracing and APM provide end-to-end visibility into requests wherever they go. Whether it's across hosts, containers, or service boundaries.

See for yourself! Start a 14-day trial today, and Datadog will send you a free t-shirt!

Find out more at {{< sponsor-link link-text="datadoghq.com/dotnetcore" link="https://datadoghq.com/dotnetcore" >}} - that's {{< sponsor-link link-text="datadoghq.com/dotnetcore" link="https://datadoghq.com/dotnetcore" >}} - or check the show notes for a link.

---

#### Jamie

Excellent. Okay. So let's imagine I'm studying a Greenfield project. And maybe I want to build an app for myself. Maybe it's an Android app, iOS app. Well, maybe a client has come to me and said, Hey, you could build Android apps. I'm looking at the technology stacks that are available. I'm going well, I could go native, but that requires me to learn Java or or any of those things. And then if I want a cross platform, I've got to then go and learn swift or Objective C, which is not a problem. It's just more things to learn. And then I think there was a father Madonna dad. If I could use them, right or I could do, who know? How do I,

#### Jérôme

how do you choose? Yeah, how do I?

How do you choose? So Well, it's all about where you're coming from. Let's say lots of people have been doing some Xamarin directly, because they didn't know about SAML previously. So it was a favour that was there publicly. And it makes sense for them to use that and continue to use that. For the other types of developers that come in that are coming from either civili wp F or, or, or you WP or when UI for that matter, it makes more sense for them to you know, because of the familiarity with the API set. Know, Xamarin Forms, which is its own its own object model, and it's not behaving exactly the same way. So you have to learn a different set of API's. And who knows targeting webassembly so you know, that's, that's another target that's that someone doesn't have by default at this point. So that's where that's where there's a new choosing can be so we're Providing a set of a set of starter kits and you in some ways, providing Visual Studio extensions that you can also do extensions that you can instal and then have a final project that provides you with the base to to get an app running. We also have new templates that you can use on you can use on Windows, Linux, and Mac OS. So on Mac OS and Linux, it's going to on Linux is going to be working on webassembly only, there's nothing else that's supported yet. I'm assuming with dotnet, five, most probably Android is going to come up as well. But that's pretty proven to be the only targets and for iOS and for running on Windows and Mac OS is going to be very versatile for Mac and for Windows on both sides. So that's quite a few options to start developing. And we have we're getting started in the documentation on uno that explains how to do basic things and get your running.

#### Jamie

Okay, so so if you want that multi platform support, it's an hour than Xamarin is amazing.

#### Jérôme

I mean, you know, it's basically a question of familiarity. And if you go a bit a bit if you go up in terms of choosing what technologies you're going to go, that's things with regards to Maui and blazer and you know, what a blazer, mobile bindings and all those technologies are there. It's all about where do you come from? And how familiar are you with the tech that you're going to be choosing? So if you are web dev, and you've been redoing razor pages, maybe it would make sense for you to do some blazer, you could be but you know, we've been we've been announcing recently other windows community stand up that we're also going to be supporting the razor syntax as well on top of Uno. So the blazer blazer model is going to be on top of uno as well. It's it's not black and white. Definitely, you know, lots of lots of possibilities and different solutions that exists. We're just trying to reach to as many developers as we can you know, it's Not always for everyone, because you know, if you've if you've been able to do some some, if you've been doing some reference for a while, then maybe more interesting for you to go there. But if you're doing your new civilised, WTF, you know, is an interesting route.

#### Jamie

So all depends on where you've come from where you want to go. And pretty much pretty much Yes, you brought something up there. And I'm going to drop this on you because a little bit of inside of baseball. Usually when I do these interviews, I send over a few topics and questions in advance. But you mentioned Mary,

Unknown Speaker  
yes. And I want to sort of

#### Jamie

see what your thoughts are off Mary, because obviously that was announced, kind of to the public last week build. For the folks who don't know that is this Mary's ma UI, multiple application user interface. I think

#### Jérôme

I miss it every time. I think you're multiplatform you wait for you must be familiar. Why?

#### Jamie

Yes, sorry. Yeah, yeah. So what are your thoughts as someone who has essentially created a multiplatform UI

#### Jérôme

so now is is all about being able to use the same thing. cross platform, it's basically a Xamarin Forms with more features. That's pretty much what it is. It's the baseline, it's nearly taking the time to do some, some changes and try to do some changes. But it's, it's still far down the line. I mean, we're talking about that six. So it's a, it's at least a year away. So it's going to be Xamarin Forms for a while. And as I'm recording is going to be continuing to evolve. And then and then Maui is going to be it's going to be available at that time. What what interests us in terms of open source project is that because Maui is all is all open source, and it's also using dotnet core and end up in core is also open source. And that means that everything is going to be using to to develop that framework from the base is going to be open source as well. So it's going to allow us to reuse the techniques that they use to integrate properly in Visual Studio, Visual Studio code and on all those environments, so expect something that may come from the uno platform using dotnet. Five quite soon, let's say

#### Jamie

okay, that's cool. I do want to point out that obviously, you know, you said a few things about it Xamarin Forms and then eventually things may change names and namespaces. Yes, that's obviously based on what Microsoft announced last week. You saying, Hey, I know what Microsoft are doing. And that's not me agreeing saying, Yeah, I know what Microsoft's doing these things What I'm saying is these things can potentially change in the future.

#### Jérôme

Now they're going to change the future of course, you know, it's it's all based on what they announced the new drink bill, then we don't know exactly where they're going to go. What we do know is that it's open source and, and they said that is going to be the in the during the dotnet, six target. So that's, that's, that's what we know.

#### Jamie

Sure. Yeah. I just didn't want people to listen again and say, Hey, Sharon said this thing and clearly that's what it is, and then blame you if something changes in the future.

#### Jérôme

No, no, no, no, no, it's definitely gonna change. I can tell you because of this time, that takes you off to a year away, you know, so many things can change. That's, yeah, that's a given.

#### Jamie

Exactly right. I know that takes Giving estimates to some of my clients and things could change on a weekly basis. Right? They only know a year in advance. Absolutely. And you never know some desktop environment may just appear on. Oh, yeah. And everything changes or Apple may decide, hey, we're moving from whatever user interface technology we're using now to some new one. And then absolutely, it's kind of broken. Right?

#### Jérôme

That that could happen.

#### Jamie

So we've we've touched a little on on the platforms that no platform can support. We said like Windows and Mac OS and Android iOS. Yes. And I think he because we've said windows that kind of, you know, UDP, and when you do stuff like that, and blazer or rather webassembly with blazer included, yes. And soon hopefully Linux. I don't want to reduce it to is that all but Is that all?

#### Jérôme

I mean, yeah, it's so most people are going to be seeing uno as a UI framework. But that's not all of it. It's all So a framework that is trying to provide all the non API, non UI API's as well. So for instance, your gyroscope, battery, flashlights, file access, although things that are not UI related that are coming from the winner to API set, we're trying to provide a cross platform as much as we can to ease up the development. So you don't have to guess how the geolocation API works. Because you know, the one that comes from Windows, and then it works, it works. It works the way you want it to work, because it's, it's good enough for all the other platforms, when we're talking about four or five platforms, new learning the, let's say, the inner workings of all those API's every time it can be daunting. So that's the that's the point of doing that. That kind of, it's a non white work. Yeah. So that's, that's another thing that comes from Uno.

#### Jamie

Right? I see. Because you see, my experience of sort of playing around with you know, is essentially the UI stuff. But obviously, you're saying there's access to all of the API as well. Regardless of the platform underneath, yes, yes.

#### Jérôme

We're trying to get to provide all that. Yes.

#### Jamie

Almost like a compatibility layer. Yeah, pretty much. Yes.

#### Jérôme

Yesterday, we're shipping and also it's not chiming or it just implementing. So it's abstracting away that the platform differences using the win RT API set. Yes,

#### Jamie

sure. Sure. So I can poke it through now and say, give me this thing. Who knows? We'll figure out where it's running. And, yes, lots of elven how to do any Well, they go do whatever wizardry magic it needs to do in return.

#### Jérôme

Yes. So So the thing is that, you know, when art here is huge, we're talking I think it's 20,000 API's. It's is huge. So we, we obviously haven't implemented everything. And, you know, it's gonna take a while for us to to to the rest. But that being said, you know, that's the kind of thing that we were able to use, the community is able to provide us some very interesting implementations, and we're progressing slowly with with adding new API's. And we're using Rosslyn to receive analyzers. So if you're writing some code that uses an API, that's not implemented yet, you're going to be notified of that in the code with red or green squigglies that telling you about that that may not work if you want to use them,

#### Jamie

rather, they say, so lots of different things for us to do with, you know, platform, we can do all sorts of things. But we've talked primarily about, you know, we've mentioned explicitly dotnet and blazer, and Xamarin. Is it dotnet? specific? Can I only do dotnet things with mono? Or if it is dotnet? specific? Is it just C sharp is an F sharp? Is it that the weird one that's sort of been deprecated, but not in deprecated? Visual Basic?

#### Jérôme

So Visual Basic, I do. I do not know. I think it depends on the model support, I think they do have some parts of the model support. It's not something that they're targeting specifically. F sharp for sure. Or it's something that's been there for a while and you know, the mono team has been pushing in that direction as well. So it's, it's quite well supported. C sharp is our language of choice because, you know, we've been developing with that for for a while and you know, All the new things that are coming up for C sharp, nine and immutability, and stuff is going to be very interesting. What else interoperating with the rest is pretty much what Emery provides already. So let's say if you want to use a native components, you can use a native component by using bindings, whether or creating your own or using existing ones that that does work for the rest. I mean, it's it's dotnet. So if you want to do p invoke, you can do p invoke some code if you're using dotnet, five. So dotnet five is going to be the target for the next ones, when we do provide Linux support. But for now, it's it's mostly mono support, but it's new p invoke does work. And interestingly, p invoke also works in the web. So yeah, so it's something that you can do, I wrote a blog post about that one. So you can call some C sharp or some c++ code directly from your C sharp, but you can also call some rust code if you want to, or any kind of code that you do basically compile that into web assembly and link it with your application and then you do invoke that And then it works, you know, as you would with any kind of other applications. That's that's kind of integration that that's possible to do. So it's not it's there the the interesting part of web web assembly is not that you can use your own code is that you can use other the code from others that is developing the language that you do not know or do not use. So that's that's the the very interesting part. It's all about being polygon interest, use every day, pretty much.

#### Jamie

I really like the idea. One of my friends, Jay is a hyphen developer. And he's always saying to be jump off and jump over learn Python and leave dotnet behind and I'm like I can, or you can just give me the code that I need to run for everything into web assembly and just

#### Jérôme

Yes, exactly. And that that's probably possible. And we could probably have a new blog post about that one, but I know that Python has been has been ported over to webassembly. So that's the third especially with the AI community. It's It's where it gets interesting with with all All those new new fancy things and fancy API's that are provided there. So yeah, it's it's something that's definitely possible to do. Yes.

#### Jamie

Excellent. So you could do you could potentially do, we're just speculating here, we're just talking as one engineer to another be, it would not be outside of the realms of possibility to do your machine learning things inside of the browser.

#### Jérôme

Oh, it's actually it's it's actually not it's not it's it's actually done already. Yeah, it's done already. So people have been people, you know, people have ported over, actually. So there's, there's two sides of that one. The first one is, the people from TensorFlow have been putting in their own code, you're running inside the browser. So using two features from threadings and Cindy, so the vectorized code so that's where to get some interesting performance there and running it running. I don't think they creating their their training models there, but you're there at least at least using them the models, they're probably training as well. It's probably also possible because you know, you have Interesting things that you can do with webassembly in terms of performance with readings and Cindy, but the other part, it's interesting is that I've been, I've been experimenting with ml dotnet. And I've been able to run ml dotnet inside of the browser as well. So yeah, it's it's not out of the realms of the possibilities there. You can actually do that kind of things. Well, brave new worlds.

#### Jamie

were amazing. Amazing. Okay. I'm gonna shift gears ever so slowly here, just ask you as a personal thing about Ms. Bell, what were some of the most exciting things for you that have come out over the past few weeks? Is there anything there who now have announced or is there anything specifically that Microsoft have announced that you're really excited about?

#### Jérôme

Well, all the dotnet stuff and C sharp, nine new it's, you know, very interesting that they've been in here, especially with regards to source generation sugestion they've been doing with we've been having our own framework for Association for for quite a while sees this. It's So, the, the C sharp six timeframe that was based off of that, and the fact that they're adding that now in C sharp is going to be, you know, kind of a time saver for lots of people dotnet five, you know, because of the performance stuff that they're doing and the fact that Xamarin is targeting that as well. All the code spaces stuff that they've they've been adding we're supporting get pod if you know about get pod. So get pod is all about having a an environment that runs in the browser and code spaces from GitHub is pretty much the same thing. And we've been supporting that to do to do development for you know, for web assembly inside of the browser using get pod and we're probably going to be adding support once we get access to it for two good spaces. So that's going to be that's going to be a fun one oh we haven't we even do support hot resemble hot reload there inside of the browser. So that's going to things that we can do with with that. I mean it's it was like a candy store new ms build so many things that were happening. So but yeah, that's that's probably the highlights for me. It's you know, all the although things and the fact that two web assembly modern web assembly was pushed by by by blazer, you know, that's gonna be another another great one. And you kind of democratise the the the use of web assembly in the browser, so and dotnet dotnet in webassembly in the browser. So that's, that's what I see. And on the windows side, it was there for us the announcement of the Mac OS support. And the fact that we ported over the windows calculator over to Mac OS so so that the windows calculator is now available on Mac OS. So we still have some work to do there. I think we were still working on adding support for the keys. So you can actually use the keyboard to type thing is not clicking on the on the screens. That's that's the kind of thing we're implementing. But that's a that's an interesting, interesting track to to look at.

#### Jamie

Excellent. I can imagine now a bunch of the windows utilities being ported over to Mac OS and thrown on to the App Store.

#### Jérôme

But if it were developed using you WP Yes, they could be ported over to do to the Mac App Store. Yeah.

#### Jamie

Okay. So, so rubbing up a little bit, then what's the best place to find out about uno platform? I know that you you've gotten bought your own TLD every years?

#### Jérôme

Yeah, it's actually its platform. Uno, actually was quite lucky to get that one. So you go to platform that we know and there's quite a few documentation there. And there's a getting started, we recently released an application that's called a CH nine, which is a channel nine RSS reader in some ways, if you will, that allows you to, to see the videos and, and the the content of the of the shows. And the basic ideas of that application is just it's simple enough. And if you want to experiment with with an application developed using Udo, that's the that's one one application to look at. And the GitHub as well, you were GitHub as is all where it's happening. So if you want to see what it's all about, and you'll see some of the demos as well. You know, it's all about it's all it's also available there. So yeah, that's that's how to start up

#### Jamie

Excellent. So then Do you hear about community demos? People have built stuff with, you know? And if so, are there any, that you kind of sat and went? Wow, that's really impressive.

#### Jérôme

Well, we have a, we've got a few people that we have. Martin, that's the Martin zachman, that's developing a site is actually developing its own application for a MIDI MIDI player. So as he is actually developing the integration for that, so he made his own application that that runs on iOS, Android, and web and Mac OS. So we can use the MIDI playback for all those platforms. We have a Igor that's been developing an application that's called pixel 2d, that uses Kia and is able to port his application to know using this and using all the platform so he was developing that application on on on Windows previously, and many other applications that are that we've that we've published on the on the on the platform that you know site for the showcases, so you're going to see quite a few of those that are running there and there's also a mental That's been developing all those applications all those years. So, we have a few other showcases there for applications that will look good using Uno.

#### Jamie

Excellent. Okay, so how about keeping up with yourself? You know, I saw I saw that you were on Twitter. You get active on there. You have a blog if people want to learn a little bit more about the work you're doing. Yes,

#### Jérôme

I do have I do have longer probably going to give you the the URL for for the, for the bio, but yeah, I'm I'm on Twitter, as well. If you search for my name, you're going to find easily and new I'm mostly mostly talking about webassembly lately, and with the with the newer features that we're working on, and the experimentation we're doing with it. So that's that's that's pretty much what I'm looking at. I'm on the discord, the win UI discord as well. So lots of lots of activity there as well. So it's pretty interesting to see the community move there. Excellent. Okay.

#### Jamie

Well, I mean, that's all of the questions I really have for you today. So I just want to say thank you. So much for, again taking the time out of your morning. You're a very busy person. So I really appreciate it.

#### Jérôme

It's always fun to talk about all those things and you text. Thank you ever so much.

{{< paracentre "The above is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

### Wrapping Up

That was my interview with Jérôme Laban and Uno Platform. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/), and there will be a link directly to them in your podcatcher.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice - head over to [dotnetcore.show/subscribe](/subscribe) for ways to do that - and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Jérôme on Twitter](https://twitter.com/jlaban)
- [Jérôme's blog](https://jaylee.org/)
- [Uno Platform on Twitter](https://twitter.com/unoplatform)
- [Uno Platform's website](https://platform.uno/)
  - [Code Samples](https://platform.uno/code-samples/)
  - [Show Cases](https://platform.uno/showcases/)
- [Uno Platform's source code on GitHub](https://github.com/unoplatform/uno)
