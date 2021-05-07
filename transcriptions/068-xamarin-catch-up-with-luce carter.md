### Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is Episode 68: Xamarin Catch Up With Luce Carter. In this episode I talked with Luce about some of the things that have been happening in the Xamarin and Maui world recently. Luce is an MVP, a curator for the [Weekly Xamarin newsletter](https://weeklyxamarin.com/), a Twilio champion and international speaker.

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

{{< paracentre "The following is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

#### Jamie

So thank you ever so much, at least for being on the show. It's a it's a great, it's a great pleasure to have you on the show. we've, we've not talked about Xamarin very much on the show, and I really want to get into it. So hopefully we can cover a little bit about that. But yeah, welcome to the show.

#### Luce

Hi, Jamie. Thanks. Thanks a lot for having me. It's exciting to be here. And yeah, I love talking about Xamarin. So if anyone ever says to me, Hey, come and talk about your favorite subject for a while. I'm always up for it.

#### Jamie

Excellent, excellent. Okay. Um, so I guess before we get on to Xamarin, and all that kind of stuff. I was wondering, could you give the listeners a bit of an introduction, just so that, you know, they may not know a lot about who you are, and the work that you're doing? and all that kind of stuff?

#### Luce

Yeah, absolutely. So I'm Luke Carter. I'm a software developer at a customer data science company called dunnhumby, who are probably better known as being the founders of club card long, long time ago, because it's actually named after the people who created club card, which is quite interesting. But yeah, so we're part of the test groups group, but we're our own company. And I currently do QA for them at the moment. So I started as a developer, but imposter syndrome bit quite badly last year. And I'm quite happy to be open about it. And so I just took a break and move into QA for a bit and actually just really liked it. Because it's, it's still the same logical thing as writing code. It's just a bit less terrifying. And so I've been doing that for about six to eight months now. And then a couple of weeks ago, I started doing automated testing with Cypress, so I get to kind of write a little bit of code again, but still on the testing side, then away from work. I am a Microsoft MVP under developer technologies. Obviously, developer technologies covers pretty much anything code related but I probably say that although I'm a sort of jack of all trades for some Microsoft products, Sumerian is definitely my speciality. And it's my favorite subject. I'm probably the only person in the world who has a Xamarin shrine in their kitchen.

#### Jamie

Okay, we got to talk about that a minute.

#### Luce

But yeah, so as well as being a Microsoft MVP, and you know, the only person that's amarin Shrine, I'm also Twilio champion. So for those who don't know, because it's not Microsoft related. Twilio is a tech company that provides API's and SDKs for communication. So anything from chat from SEO, not putting up just SMS chat, but WhatsApp and other products like that video and phone calls. It just I really like them as a company. And I don't use them much with Xamarin itself. But I've just got some really great friends that work there. And I've done blogs and stuff and said they honored me with that sort of MVP equivalent title of Twilio champion. So if you've got any communication needs, check them out, because I think they're great. And that sort of outside of that, I tend to stream sometimes write the blog, YouTube occasionally. And or try take a break from the computer because I'm guilty of working way too much. If I guess that's me in a nutshell.

#### Jamie

Awesome. I have to attest to taking some time away from my computer. The people who know me in real life will never admit to, you're really fat Jimmy, but I'm really fat Jamie. And so I try to go out for a walk or run at least once a day. But this will date the recording because of time machine. Time Caspar machine wibbly wobbly. This is what I call it. There's like a time slip involved in podcasting. We're recording this about a week after thuggery, the heat wave of 2020. So that kind of put it down, put her on going out and going for a walk around.

#### Luce

Yeah, I can imagine I do run sometimes I was ever tradition of running a five k on Christmas Day. So I've got an excuse for Christmas dinner. And yeah, that's fine in December, but I couldn't imagine running running a five k right now. It's it's been hotter this week, but it was sort of 3334 Celsius, which is something that between 87 and 90 Fahrenheit for our Imperial metric, whichever it is listeners, so pretty warm and humid.

#### Jamie

Absolutely. It's been it's been a nice break because over in the UK I always joke over in the UK our some of our hotness, further heat in summer lasts about two hours. So it's been a nice break,

but then you kind of get he kind of gets old very quickly.

#### Luce

Yeah, I'm still I don't enjoy the mugginess of all the humidity but at the same time I like the sun and so I'd rather have this than winter.

#### Jamie

Hmm, absolutely.

That's it if I had the choice of going somewhere hot or go somewhere where you can't leave and you have to put on 15 layers of clothes just to get out of bed. I'm going to my heart is

Okay, so we've we've talked, we talked a little bit about Xamarin. And I was wondering, before we even talk about Xamarin, what's with the Xamarin shrine in the kitchen, if you don't mind sharing.

#### Luce

So I used to work as a graduate for an IT company called Fujitsu, who started making a Xamarin based app, which is actually out in the wild. Now, if you've ever been on UK trains, and you've seen some of the red and black phone cases that they used to sell tickets and check tickets, that's actually like phones with the Fujitsu made Xamarin app running on the phones. And so we had a Xamarin partnership back before Xamarin was purchased by Microsoft. So again, the logo stickers for had loads of really cool sunset color, sort of gradient type salmon stickers, they rerelease them last year, but they weren't quite as good quality as the old ones. And still great stickers. I had all these stickers left and then, and anyone that knows that Xamarin was probably heard of James monta Magno at Microsoft, and he does a podcast with Frank Kruger, the one and only creator of SQL light net that a lot of people probably have heard of. They so they do this podcast together. And on New Year's Day, I think it was 2018 or 2019. I woke up at like eight in the morning, UK time. And so that's midnight on the Pacific coast. And so I saw that they've released an episode, but they announced after the patron, and I became the first ever patron supporter. And so I actually got a very nice handwritten card from both James and Frank. So it kind of ends up at this point where I had this handwritten card that I was really grateful and proud of plus all the stickers and I just said, Stop thinking, what can I do with it? And so the stickers, I just stuck to some lined paper and then cut around it into a fun shape. And then put the card on the card on the wall. So yeah, I just have some stickers, and a card on the wall. Because why not?

#### Jamie

That sounds awesome. To say,

yeah, being the first patron for something is always being first at something like a second thing is always it's always fun, right?

#### Luce

Yeah, it's just so sweet of them to send me a card just because I was a first supporter. And you know, they said really kind things in it as well. So yeah, it's just something I didn't want to just stick in a drawer. I wanted to put it somewhere prior to place and say my kitchens in perfect.

#### Jamie

It's a good place as any I suppose. I mean, we spend we all spend a lot of time in our kitchens, right?

#### Luce

Yeah. And I've got open plan as well. So I've got a little table in my kitchen. So it's just next to the table. So it's a key part of my living space.

#### Jamie

They say and then if, when all of this, I'm about to say when all of this nonsense is over I like to say nonsense just because well, they on podcasts, we're not allowed to say the name of it, because you actually get shut down and be because I feel like making fun of its they makes it a little less scary. When all of this nonsense is over. When people come over, they're like, Hey, what's this? Oh, well, let me tell you about this.

#### Luce

Yeah. Yeah. I mean, it's been up on the wall for a couple of years now, I think. Yeah, definitely. When people come around for the first time, a few of them were like, Oh, what's this? And then I can tell them the story. So they might not benefit from Xamarin? Because they're not technical. But it's still a fun story.

#### Jamie

Yeah, right. They probably still benefit from Xamarin, even though they're not developers, because it's like, Hey, I have a mobile phone. Right. Which I guess takes us neatly on to, I guess, the subject of the episode. So we've, we've talked a little I've talked to Jim Bennett in the past on Xamarin. But that was like we recorded it in really early 2018 and released it in very early 2019. And it's an Arizona 2020. Which means there's a whole bunch of stuff that's changed, right.

So

I was wondering, can you can you talk to us a little bit about so because people, let me just dial back a bit. I'm going to lay I've got 15 different threads going on. I'm really bad for this. So for the folks who don't who was on marinas, can you give us a really brief intro to what it is because people don't listen to podcasts in our from the beginning to now they pick them up when they want, right?

#### Luce

Yeah, so so Zambian essentially is a thin dotnet wrapper around the native SDKs and API's for a lot of the platform like it started out as mobile platforms, but now supports more than that. So there's iOS, you WP, Android, Mac OS, but then it also supports some other things as well like watch TV, iOS, but some stuff from Titan from Samsung, which we'll cover later maybe because that's quite cool and deserves a conversation of its own. And briona so it can go on watches. TVs, obviously because you don't even got an Xbox if you want. I try filling out the day with YouTube as well. So I actually put in a chapter to see what happened to Xamarin I put an Oculus quest

#### Jamie

credit.

#### Luce

And so yeah, so pretty much it supports. It really supports dotnet everywhere. But yeah, so it's this thin wrappers. But because it's just a wrapper, it means that you get all the native tools and everything as part of it. So you use the light, whether it's C sharp or F sharp, you know, whichever language you prefer, you can use that to write your applications. And it's 100% API access. So anything that you could do an objective C, and swift for iOS, or kotlin, and Java for Android, you can do using C sharp or F sharp. But once you step away from that wrapper, it starts to use the native compilers again. So you know, androids own compiler and iOS build chain, use all of that under the hood. So it's all native after that. So you write to how you want, but from that point onwards, it's fully native. So you get access to everything, you know, all the API's and SDKs. But it also looks and feels identical on the platform. So once you're using the app, you have absolutely no idea what's written in Xamarin. It's just a, it's just an app on your phone. So you know, that's, that's pretty cool. But said, it's the fact that it allows you to use dotnet, that I think is really powerful. And because it's just a wrapper, unlike some of the other competitors, it means that it really is just a native experience and everything. It's only the code writing level that is anything but native.

#### Jamie

C, I have noticed that when I've used things like ion is ionic. Is that the company that does web hosting is ionic, yes, using ionic and all the different, like JavaScript based tools to actually like, is it React Native and all these Apache Spark and things like, are you running everything in JavaScript or hitting a belt, and then hopefully, something comes out the other end? It hasn't, it's the developer experience has not been, shall we say, as exciting to us as ever. And I know that when I hit belt on a Xamarin project, it actually produces some thick.

#### Luce

The, one of the great things as far as not, because you can use dotnet and the native tools, but because it is the native tools, if you're using something that you know, JavaScript related, or whatever, or another language, a lot of the time because it's not native, you're waiting for someone to make it available to you if a new feature comes out. Whereas Xamarin is is great at being available almost day one or very quickly, you can only get access to a preview builds that will give you access to the next release. You know, even just today on Twitter, I saw a was a today, the day of recording, I saw a tweet about you know, if you go to the preview channel on Visual Studio, for Mac, for example, the same Visual Studio, you can target. The next was iOS 14. So it's not even in public preview yet. But Xamarin is already giving you a preview channel that you can go and update Visual Studio and have access to all the new features straightaway. So it's very, very powerful.

#### Jamie

That is amazing. I do like

#### Luce

that. It's it's not just, you know, allowing you to write dotnet code. But it's also allows you to kind of get the same native performance, because it's all the same build tools underneath. So you're not seeing any kind of hit because you've got an extra layer, it's just a wrapper that disappears at build time. And so that's cool. And kind of the way it works as well is that you've got kind of two flavors of Xamarin. You've got some renders that kind of stack some of the traditional one where you can just target specifically Android or iOS. Or say you WP I guess if you're just targeting you, WP, if you just do you WP rather than Xamarin. But it gives you shared business logic. So it's not just allowing you to write apps with C sharp or F sharp, but it's actually allowing you to reuse the code. You write it once, and you can use it cross platform. So it saves you loads of time, as well. And it's just and because it's dotnet. And it's the shared project, as they call it. It's dotnet standard project, it also means that you can bring in other dotnet projects and use them as well. You know, there's no, it because it's dotnet standard, rather than say something like dotnet core, yes, it's awesome differences. But you can still go well, I've got this and they might be a dotnet core application that just makes them REST endpoint calls, we can just reuse that just add it in the solution and carry on. So it's very powerful and productive.

#### Jamie

Sure, sure. That's, that's the kind of thing that I that I like to hit. That's not a code reuse. Because otherwise you're gonna you know, you spend ages writing some wonderful class structure or some things and a bunch of functions that work wonderfully. And then you're like, this is great, kind of architected it really well, and it's really clean. It's really testable. It's 100% test coverage, you should never really aim for 100% and then you're gonna write Okay, new project. I'm going to stop all of that all over again.

#### Luce

Yeah, no, it's great for that. It also as well as sort of the Xamarin native, as we call it, as I said, which just targets one platform. They also have something which a lot of people probably use automatically called Xamarin Forms. So all Xamarin Forms is is just an extra part to your project that allows you to share UI as well. So you're saving even more time by being able to either in zamel, which is a extensible application markup language. If you've done WP F or you WP before, it's, it's the same, it's not the same flavor dialects are slightly different, but it's very similar. And it's still declarative and nice to use. You can do ui enzymol, you can do them in C sharp. And again, because it's just a native tools underneath, once it's out on the phone, you know, it looks how it should an Android out of the box, it looks how it should on iOS out of the box on whatever other platform you target. And you just don't know. So to you know, forms is nice to use, and it's even more code sharing.

#### Jamie

Sure. And I guess, does that mean that it hooks into like the platform specific XML accessibility tools and stuff it

#### Luce

doesn't even need to plug in, because it's because it's all native underneath? Once you start building and compiling, anything that you get, it's all just native after that. So all the features that you'd be used to like accessibility is all there. Yeah, there are, don't get me wrong, there are some things that can be improved with accessibility with some of the components or reforms. But you know, anyone who's frustrated by it, I can assure you that I'm actually a member of an advisory group for accessibility in Xamarin Forms where we meet monthly to talk about how it can be improved.

So yes, getting better all the time.

#### Jamie

Sure. Show. So it's, it's it's pretty good. But it can be improved, but it will be improved is being improved, correct? Yes.

Okay.

#### Luce

You might have drastically improved or changed in some way, by the time this podcast

#### Jamie

comes out. Oh,

yeah, definitely. Definitely. Okay. So you mentioned both Xamarin and Xamarin Forms? Are they the same thing as one a subset of the other does one hang off of the other? Or is it completely

#### Luce

hands off the other. So Xamarin is the like salmon itself is the sort of technology stack that allows you to use, you know, mono, and all the other things to and dotnet to make the apps. But then Xamarin Forms is just the shared UI part of it. So if you, you can either, as I said, makes target Xamarin native, as we call it, which is just using, you know, dotnet to write a single target to platform app. Or you can do forms but forms, so forms of both forms and native to share the same underlying technology, if that makes sense. So you can when you create an application, you can pick which flavors are any wants to target when you create the application. So you know, it could be Yeah, it could be Xamarin Forms or Xamarin. Native, you can just pick, you know, in whichever ID you choose to use, because server is supported by Visual Studio for Windows Mac and Ryder.

#### Jamie

Okay. Okay. So I will go in a little bit off topic from the stuff that we have. So inside baseball talk, I put together a document and send it over. These are roughly the things we're going to talk about. And one of the things that's not on there is what's the 10,000 foot level difference between Xamarin Forms and Xamarin native that just because you brought them up, right?

#### Luce

Yeah. So it's literally to do with which one which platforms it targets and how the UI is written. So if you pick somebody native, and so you say that when the Xamarin, dot Android app, or when the Xamarin dot iOS app, or Xamarin, dot you WP or whatever, you're just target that one platform, which means that UI is not shared. So you'd have your shared business logic in a dotnet standard project still. But when you want to declare things on the UI, you still have to use XML for Android that used to be dot XML, or storyboards in iOS. So you still need that knowledge of how to do it in those different platforms. Whereas with forms, instead, it's just SAML or C sharp, and it takes care of the rest of how it would be generated on those specific platforms. And so it's much easier. And I think it lowers the barrier to entry a lot. And for anyone who's doing salary in the enterprise, of course, it lowers your time to market because you don't have to develop a multiple UI. So you save money on hiring people that know about how to write these you eyes, and you'll get to market quicker.

#### Jamie

Sure, okay. I like that I like anything that lowers the barrier to entry. I am all for, you know, regardless of whether it's for developers who have already used something, or whether it's someone who's completely new to something, lowering that barrier of entry, allowing more people to come in and use it. I'm all for that.

#### Luce

Ya know, I I love Xamarin Forms. I've been using it a few. I'm just a hobbyist average developer. But yeah, I've been using it for years, I discovered it, it was much, much easier. I didn't have to worry about how to do it on every platform, and I'm so great sold. And every single new app I make is salmon forms. No question. I've got no reason to limit what you know what platforms I target. So why would I make my life harder by not showing the UI as well? Absolutely. I think it might be interesting to touch on actually we're discussing the differences between native and forms is that they actually support mixing the two So you can actually have a native project and go right? Well, this, you know, I've got Xamarin, Android, and I've got salmon native, you might have reasons, which back in the day mattered. So a long time ago, it was much harder to do things like graphics. And so you'd have to go to the platform level and use those, those libraries, there's options, much more options now, like scare sharp and things like that. But yeah, back in the day, there was fewer, like what we call libraries that allow you to, you know, do stuff that be done differently on each platform, and they take care of how it's done. And, yeah, so you can have, maybe you might have a native application that you created many years ago, but you can go well, I want this login page, for example, to look, feel and work the same on every platform. So you can just use your native app, but just drop in a forms page. And vice versa. You could have a forms application, but then you decide that you want something to look specific on each platform. And that's when you can then go down to the platform level and just be like, hey, on this platform, right to look like this on this platform or look like that. And then you just include that page in your forms. So in fact, you've got even less reason to pick and choose now because you can just, you know, do what works for you.

#### Jamie

Man I see. So it isn't a case of one or the other. It's which bits would you like in this one? And which bits? Would you like in that one? Or you can just go with one or the other?

#### Luce

Yeah, I mean, I still stand, I still stand by forms being the best choices, like I say, if you create a new application now, stick with forms, because it's getting a lot better, you can still add in, you know, platform level features, you know, platform level code, if you need to, for whatever reason. But yeah, apart from that forms is great. And there's a lot of plugins out there, as well as libraries, or plugins, whatever, terms are interchangeable, but they're all out there. So there's a lot of things that may be out of the box salmon forms, doesn't allow you to do. So for example, taking a picture, or a video, because how you'd access the camera, or your gallery or photos, whatever it wants to call it on Android and iOS is completely different, not just obviously from a user perspective, but from a code perspective. So people have generated plugins that, you know, literally, excuse the pun, but plug the gap. And so it's, you know, it's getting even better to use forms now. And James montemagno, who mentioned earlier, he wrote, a lot of plugins start dating back to when he first started using Xamarin. And a lot of his plugins, he created so many of them that now he works at Microsoft, he started a project to create something called Xamarin essentials, which is bringing in as many of his plugins as possible with a refactor and a bit more, you know, proper enterprise style, build into the deployment pipeline. But he brought all that in, and that's now with you quite a new Xamarin Forms app, it brings in that new get packaged automatically. So you've already got access, I think it's something about hundred API's that you didn't before. So all the silly things that you probably take for granted that you need access to like factory status, internet connectivity, because you're on a phone, people can lose signal, it's not like sat at home, and they're always going to be on Wi Fi. And so yeah, this accelerometer is 100 of those of them. But yes, you know, the plugins are getting a lot bigger. So I just generally don't think there's a reason not to use forms for a new application these days.

#### Jamie

Sure, sure.

That makes sense. And yeah, as long as you don't have to, if you want to be I guess it's, I guess it comes down to like, if you want to be able to make your application cross platform is and, and reach the highest level of user base, which enterprise really loves that. And startups really like full of that if I can push one button, produce one app and just deploy it everywhere. But it's wonderful.

#### Luce

Yeah. And it comes back to what I said before about, you know, I take time to market such an enterprise term, but you know, even so, you know, whether it's time to market or just time to get it in pockets. Yeah, I'm an iPhone user. And I do have an old android phone because only moved to iPhone last year, but you know, that you might be that you want to try out the different platforms. And you can just say, you know, can you try this out for me, but, you know, you know, out of the box that you can just do that, you know, you don't have to do any extra work, you just go, I want to talk at the mall.

#### Jamie

It's like Pokemon, and I got talking to them all. That could

totally be it now. Yeah, they probably wouldn't go for that, because that would be a copyright strike. But yeah, we can totally do some. Excellent. Okay. So there's lots going on in Xamarin. And there's lots going on, as we move into dotnet, five and six and dotnet. exe, I guess or dotnet. And, and that's probably the better one. I don't know. I don't know. But

yeah.

So um, so what are some of your favorite maybe new features or if they're either new to you new to the Samara universe, I don't know whether ecosystem asset or whether it's just new to someone like me, who's only really heard of Xamarin from like a year ago. What are some of your favorite things?

#### Luce

Oh, God. So many things. So I could be here all day. But

one of the great things is that I think it was in 2018. But apologies for the date is wrong, but at some point, they open sourced sovereign forms, which means that it's all out there on GitHub. So the community has been submitting prs and raising issues and doing things to improve it and add new features for a long time now, so it's ever expanding with all the different things it can do. And sometimes it's you know, might not be a new feature might just be Oh, I've got you know, I want this this feature to target you WP, because it might be that they've got Well, our stats showed that not many people use this on you WP. And so we're not going to spend the time supporting it, but feel free to. So that, you know, opens up all that. And so there's a lot of regulars, a lot of new stuff that comes in, that's fantastic. There's a I don't know how to say surnames, I'm not going to butcher it. But I think he's just Vincent dotnet on Twitter. But he generated a fantastic library called C sharp for markup, which allows you for those of you that write you eyes in C sharp, which people do zamel tends to be the most common. And you see that most in code samples and documentation. But it does support C sharp, and C sharp for markup just gives you a nicer experience. But Vincent was able to just go on to GitHub and incorporate the C sharp for markup into Xamarin Forms, go through the process with the team. And now it's in Xamarin Forms as if I think it's 4.7 or 4.8. So yeah, the ability to add new things is a feature that I love, but it just means a lot of cool stuff is coming. So 4.8 came out recently of Xamarin Forms, and they introduced gradient and like shapes and brown piles and gradient brushes, which to some people and we've been able to use for years. And it sounds like nothing. But you know, all developers like to make things look shiny. Yeah, things like brushes only came out recently. And I tried it last night, it took me less than 10 minutes to make a rainbow gradient across a component. So it's that kind of iteration I really like so brushes is one I like because I was able to make a rainbow yesterday.

No, no, you have to see this. As a podcast, I actually have a rainbow heart on my wrist. So I'm all for rainbows. So it's fun. I'm trying to think of some of my favorite things. So some of them I think we'll be looking ahead. So as you mentioned, dotnet, five and dotnet. Six salmon forms is not been rebranded it's evolving. So go back to your Pokemon reference. It's evolving in into dotnet, six. So what they're trying to do with dotnet, five and dotnet. Six is unifying the dotnet platforms and try and get away from dotnet. framework. That's apologies, but don't get offended by what I just said. But yes, yeah, they're trying to move away from that to one dotnet platform. So it was going to be in dotnet. Five, but obviously, you know, the thing that we can't talk about is impacted a lot of people's it's been pushed back to dotnet. Six. And but yeah, they move they're evolving Xamarin Forms into something called Maui or multi application user interface, as part of dotnet, six. So that's an evolution Xamarin Forms. So it's a lot of the things that you're used to already but with some improvements. And so it will kind of there'll be performance and some of the simplify some stuff like how you contribute or how you extend existing controls. But the thing that I'm most excited about is because it's moving on to the dot dotnet. umbrella efficient, obviously, it's already dotnet, because it's moving on to that one dotnet idea that Microsoft has got, which is a bad idea. there and Dell, it will start moving over to the fingers, Windows templating engine, which means it will finally be able to do from the dotnet, SDK, ccli dotnet, new, and wherever they decided to call the acronym to create a Xamarin project. And we know not only is that nicer for those of us that like the COI, but also because it's moving to the templating engine will be able to make templates a lot, lot easier. So you get some great, but you get a blank template in Visual Studio. And there's also some like templates that you can pick for some other styles or maybe a layout like a grid or on staff. So that gives you code samples to work with, which is great if you're trying to learn something. But yeah, even regardless whether it's as every project or something else, I'm sure there's certain libraries or architecture that you implement in your app as soon as you create it. And so by introducing a templating engine, we'll be able to actually just spin up templates and then you can say dotnet new and create this. So one for me is Xamarin Forms. The most popular architectures used for it is Model View viewmodel or MVVM. And MVVM is great and it is very simple to use. But to make it even simpler. I like to use a plugin that James created called MVVM helpers. So the first thing I do when I create new application is set up the view models folder, put it bring in the library. Yeah, maybe create a you know extend the class in have tried to implement the MTA using MVVM. helpless because it can, there's something called a base view model that you can, like extend your time of beam to want to think straight.

#### Jamie

That you can inherit from

#### Luce

so inherit from Yeah, so you can, yeah, say, base view model. And it's so so that's one of the things I do straight away. And what I'd love to do, and I tried to do it, and I'll tell the story in a minute, is Yeah, just bring that in, so that you can say to people, you know, no consorts here, if you wish, use MVVM help with MVVM. Here's a template that you can use. So you can just spin up an app in the shape that you want. So just touching on that story. So because I always do that repetition. The few months ago, I actually tried creating a template in Visual Studio, the old fashioned way, you know, you create the project. And then you start saying to Vishy Joe, Hey, can you use this template. And now I'm made it nice. I said, I was just going to be great, isn't it. But then I learned what the problem is, it doesn't dynamically change the name. So it's given me a new project with all the names of the files I gave it for as I wanted it, to replace them with whatever you wanted to call it. So you know, I didn't want it to be called, you know, Xamarin Forms MVVM template, few namespaces, I wanted to be whatever you called your solution. Now, therefore, a former Xamarin program manager, who at Microsoft is still at Microsoft has just done on a different team. Now Chris Brogan, he said to me on Twitter is Oh, yeah, if you use a templating engine, you can solve that problem. So that's one of the things I'm really excited about. With Maui. It's just I couldn't create a template that only helps me but other people, just save time and don't have to then import the new get and set it all up. It'll just be there. So that's really cool. So yeah, that's the thing I'm definitely most excited about with Maui. And what's coming.

#### Jamie

Okay, a couple of things to unpack there. I just wanted to only because early in the show's history, somebody said something about moving away from dotnet framework, and somebody came out with this guy is falling, because somebody said on this podcast, I just want to, I'm not an MVP, so I'm not privy to it. But my understanding of the whole situation is dotnet framework has the same support lifecycle as Windows. So as long as Windows is around dotnet framework will still be around. It's just the new innovations. The term that I've heard is the new hotness will be IE dotnet 5678. But framework will still be around. It's not like the sky is falling or anything.

#### Luce

Yeah, yes. Yeah, I should don't upset anyone. Yeah, you're right. It's not going anywhere, it will always be supported. It just won't be evolved upon, you know, wherever they'll be. I don't know the exact number. But there'll be a version of dotnet framework where they go up. That's the last kind of release. And it'd be the same as our reforms. I think after Xamarin Forms five, that'll be moved to Maui. And so yeah, yeah, don't panic Sky's not falling dotnet framework, it's not going anywhere. But yeah, as you said, the new hotness is going into this into dotnet, five and six.

#### Jamie

Sure, sure. And there was something he said there about the templating engine, I absolutely love the dotnet. New, I think it's called on the new three, because they've iterated on it, the dotnet new CLR path is wonderful, and an employer that I used to work for, I've since moved on and done other things. I actually spent some time in built because they were building, they would basically do the same thing in Visual Studio file new at this project at this project, have loads of new get packages settle up and then spend four or five days writing boilerplate code. And I kind of went, can I get a copy of that when you're done at the boilerplate code set aside, and then I create, all I did was you create a template dot JSON file, and then that's it is a template and you just do dotnet new install this template. And then you can just do from the command line dotnet, new in the name of your template. And if you do, I think is dash dash n earners or a single dash n or double dash name, then whatever you type in becomes the core namespace for everything, which is wonderful. But yeah, I did try to do it inside a Visual Studio. And I think only one person on the planet really knows how to make templates inside Visual Studio. And that's Mads. And that's it. No one else knows how to do it. You just got

#### Luce

the downside.

If I was doing I was doing it wrong, because it didn't update things. But yeah, nothing I've said anyways, is that exciting? I don't know any secrets like that at the minute like everything I'm talking about, we can put the link in the show notes. But it all comes from the readme for the Maui because it's all on GitHub, open source. She could look at it, you can change it, you can raise questions. Yeah, very much clear as day. Yes.

#### Jamie

That's exactly right, exactly. But that kind of needs to happen anyway, because I feel from some my personal perspective. Again, I'm not an MVP, not a Microsoft play, but from my personal perspective, I feel like the CLA experience has been the first class. So there's an for reasons that are essentially Visual Studio itself. The version of Visual Studio four Windows isn't available for Mac isn't available for Linux with good reason. And so I've I have felt, in my own personal opinion that dotnet new dotnet CLA has become the first class citizen. And then the people who you like the gooeys, who like to move the mouse point isn't like, and there's nothing wrong with that. There's a lot of stuff that I can do really quickly with a mouse pointer. And there's a lot of stuff I can do really quickly with the CLA. But for the people who like to stick in File, New Project, you haven't typically gotten things as fast as the CLA folks, because like I said, building those extensions, individual studio is hard, and only one person knows how to do it.

#### Luce

In I'm sure, you know, not only is this being recorded months before it comes out, but also you know, dotnet, six is quite a way away. So things will change. And you know, what's gonna actually happen with the templates? And what have you? I don't know. But all I know at the moment is that, you know, the dotnet CLR supported on Twitter, I was told that I can use the templating engine, in theory to create new templates. So you know, it should be exciting times ahead. Just Yeah, a strict subject to change.

#### Jamie

Absolutely, absolutely. And that's, that's one of the important things that I wanted to get across when talking about the sort of the new technologies that are coming out. And I think you hit the nail right on the head there. And he said that when we are recording this, I'll this for the people that are listening to this on day release, yes, we recorded this on August 14, of 2020, which is way ahead of the dotnet. Five actual release is still in one of the early access previews. And memory is dotnet. Six. So that's at least a year and a bit away from where we're sitting.

#### Luce

So yeah, absolutely. So a lot. Yeah, anything I say here could completely change. But at the moment, you know, as far as I'm aware of it, you know, yeah, it even says on the GitHub page, I mentioned that CLR will be supported. And yeah, because I tried to templates I know about templating engine. So what they're gonna do with that stuff, who knows? It's exciting to see, but I don't know the answer right now. But there's a lot of potential and that's what's exciting.

#### Jamie

Yeah, exactly, exactly. So one of the things I remember being blown away by when I talked to Jim was, he said, and I think you you've mentioned it earlier on, and you said that we could maybe look back to it is Tyson. In fact, one of the thing that he said that blew me away was he said, The Tyson system, all of these Samsung devices, the phones, the TVs, the watches, the fridges, they all support ties in and Tyson's official in bungee cords, at least at the time when he said that I don't know whether it's changed the official programming language and platform is C sharp dotnet. So, like being blown away by the fact that I could potentially buy a taser infringe, write a Xamarin app for it, run it on the fridge. And then when the nonsense has ended, invite all my friends around the gun. Look, look, look, I wrote that app and then go, Jimmy, you're weird. And then I go get some new friends. Right?

#### Luce

So excellence, Samsung, the Tyson team have a very good relationship with the Xamarin team at Microsoft, and they're forever contributing. So Titan has excellent support is forever evolving. I think Titan might be one of the biggest contributors. Yeah, yeah, I don't work at Microsoft, not Program Manager at Microsoft. So I can't read off stats, like some of my wonderful friends in the Xamarin. team can. But yeah, so he ties in and Samson make a lot of contributions to form. So the support is very much there. I don't own a smart fridge that learning Titan fridge, so I couldn't. I couldn't go You know, I've run one in the wild. And it worked. But yeah, Titan is supported. So there's nothing stopping you making your own, you know, to do. Let's be honest, you're doing it and sticking it on your fridge.

#### Jamie

Yeah, exactly. Right.

That's it is pretty brilliant.

It consistently blows me away that dotnet is finally reaching that. I say Finally, it's been like, five years, six years in the making, that we've reached that Pinnacle that Java promises towards the middle 90s. That was right, your your code wanted to run everywhere. And we still haven't hit that with Java. But with dotnet we are officially right once run anywhere with a few small caveats.

#### Luce

Yeah, like, it's so right once run anywhere, like say a few caveats to the point that Microsoft actually, you know, say dotnet everywhere. It's one of their like, least it's certainly last year from their slogans and you see it in their slide decks. And you know, Jim, actually, who I'm very good friends with, and I've, you know, spent plenty of time with, he gave a talk event we went we spoke spoke out together, I think it was in 2018 in Germany, and he actually did the keynote and he talked about dotnet everywhere and he was showing you often, you know, screenless, IoT devices, to all sorts of things, you know, if it pretty much if it can run dotnet, you can run Xamarin for like, say with caveats. So for example, Unity can run with dotnet. And so as I touched on at the beginning, I tried sticking a Xamarin app on on my Oculus quest, it crashed my quest. But that's only because I might have written it wrong, because I don't do unity. So that's probably more on me. But it's, for me, what blows me away is the fact. I didn't even hesitate to go, oh, it supports dotnet. All right, let's stick of Xamarin app on it then. And, you know, okay, it's quite solid, nothing about it, I just use it to beat Sabre and get some exercise in. And it's, it's the fact that you don't hesitate to go, Oh, it's not now just give it a try.

#### Jamie

And like you said, you know, you spotted earlier this week that the iOS 14, support is already there, in one of the preview belts of Xamarin. So

#### Luce

yeah, now, of course, as we speak, it's in a preview. So obviously, I was gonna hear this until much later on iOS has been on iOS 15 by that point. But yeah, you know, it won't, you'll be out of preview. By the time you can't, I'll see, you know, if anyone listening to this uses preview to do stuff for iOS 15, or whatever. There are, of course, as a caveat, it's in preview. So there might be issues, but you still have access to these things to try it out. Yeah, I wouldn't recommend preview anything, if you're working in a proper app that needs to be, you know, you need to make sure it's fully stable. But even so, you know, it's the possibilities are endless. And it's so exciting. And I think the move to Maui and dotnet six, because you know, Maui is formed. So dotnet, six and Xamarin is more than just Maui. But yeah, it's just exciting to see what's gonna happen. So much is going in the right direction.

#### Jamie

There really is, it really is. And yeah, I personally am incredibly excited to see what happens in the next six to eight months. Yeah, because they don't have five, we'll get released. And then we'll start getting, obviously MVP is will likely be tall first, but we'll start getting drip feeds of this is going to happen in dotnet, six, and this is going to happen in dotnet. Seven, and this is going to happen in dotnet. And you'll be like, Wow.

#### Luce

I think Bill 2021 is going to be a great place to be.

#### Jamie


Let's Let's hope that all of this nonsense can be over by then. So I can do it in person. And then I can have a reason not to go because we'll be too expensive.

#### Luce

might say Microsoft actually announced that they're not doing anything non digital until at least July 2021. So build will definitely be virtual next year. But build is free. So it just means that even more people can sign up and attend and learn about all the exciting things happening.

#### Jamie

Exactly. Excellent.

#### Luce

is pretty much virtual. Just to clarify.

I got I got to go a couple of years ago, actually, which is when I'm sat next to James watching him do some stuff. And that was hanging out with James in real life is a pretty cool experience. And he laughs when you say that you get starstruck The first time you meet him. But anyone that you know, most people have heard of James montemagno. Let's be honest. And it's just such a nice guy as well. But I actually got to go to build thanks for Jim. So it's a nice little full circle. Because, Jim, if you haven't listened to the episode, Jim is a senior cloud developer advocate at Microsoft. He's in the Education team now and does a lot of stuff with Python and IoT. But he's historically been a Xamarin developer. He was, you know, before they changed structure as a team, we moved to education. He was the go to one of the go to Xamarin developer advocates. And as part of that, they were able to give tickets to build members of the community. So he kindly donated me a ticket. I still had to personally fund the flight to the hotel. But I got to go to build because of him. So yeah, it was a one of the best experiences of my life. Cool.

actually do it.

#### Jamie

Yeah, yeah, definitely. I remember built this year, and it was like, it was like a three day rolling conference. There was stuff that was different for each day, but most of it was kind of repeated. Now San Diego is terrible in the morning. I'm really tired. But I'm super excited to see what this is gonna be about.

#### Luce

Yeah, no, it was interesting for me, because I actually sort of got involved a couple of times. So I, in parallel, the Microsoft developer twitch account was running streams where they will have guests on or employees on to talk about things that got mentioned that build. So for example, I think he had a guest, but I might be wrong. David otter now who's another program manager, Principal program manager for mobile rated things. He came on and talked about Maui after it been announced. because he'd been dropping easter eggs for months by putting Hawaiian themes in some of his applications. But yeah, so once that came out, you know, he came on the stream, and he did a section where he started to talk through it and people could ask questions. And so one of the things I got to do was join another Microsoft employee who was on the Xamarin team, but now works on code spaces. And I was actually a guest on his slot on the build channel. For this another build live stream And then later in the week, I was honored to be invited to be a guest on the UK his coverage. So they were doing this cover and but they called it now but we get billed live or something I'm not sure. But it was, it was what would normally be like channel nines studio and they're sat there, you know, and they have a desk and they're constantly interviewing guests, but to deal with the time zones, they had presenters from around the world. So there were when the UK contingent Ron, which was dean, Brian and Amy Boyd did a fantastic job. Oh, and then he was a seam and Simone on the first back for two days. And then Dean and Amy for the next two to end in an NGO presenting I was invited on for like a 10 minute slot, just to talk about my thoughts on build. And yeah, let's be honest, a lot of people attend build, so I was a little bit distracted by nerves. But yeah, build this year was definitely exciting. And yeah, it was, it was fun to see the easter egg, David's easter egg finally out in the wild, and we can talk about it.

#### Jamie

One of the things, I don't

know whether you can talk about some of these, hopefully you can, but I was I was wondering of all the Xamarin projects you've ever heard of? Are there some that you saw sort of stick out to you and go, hey, that's really cool. I wish I had a thought of that. Or, like, Oh, that's really innovative for you know, what, what a brilliant idea. Is there anything ever sticks out?

#### Luce

So I can't think of any directly that jumped out at me. But I think one of the cool things about Xamarin is that how many apps are actually written in Xamarin? That you have no idea. So everyone's heard of the BBC. And, yeah, I know, the BBC is very much British, but a lot of people around the world, you know, know about the BBC, and I really enjoys cooking. And so an app I've got on my phone is PVC, good food, which gives me recipes, and you know, and, and stuff for ingredients. And that's a Xamarin app. And other cool ones as well. Ups. For anything there is actually I'll send you a link that you can put in the show notes. But there is actually a whole page about that Microsoft have customers that use Xamarin. And that's always an interesting one. And even in house stuff, some of it is written with Xamarin. So the Microsoft news app uses Xamarin. And if anyone does DevOps stuff, or and has the Azure portal app on their phones, that's something up, you know, because it's all native features, you wouldn't know when you use it. But yeah, a lot of these apps, you know, you might have heard of, I say like ups like Microsoft news, even just giving and ones like that there's a lot of companies that are using Xamarin to make apps. And I think a few years ago, there was a cool one, I think Pepsi Max, or some kind of like, add game thing with an app where you could I think it was augmented reality based. I just remember it involved football, I think it ties in with the World Cup that was run up through. I think for me, it's less about, oh, wow, it can do this. And it's more like, Oh my God, look how many people use this or, you know, I didn't realize until I looked into this that BBC good food is written in summary. Yeah, it says, to me, it's really interesting, the wide perspective of large corporations that you would have heard of that you salmon, and then, but other cool stuff. So these aren't sort of officially out and the App Store apps, they're not secret. They're just like proof of concept things that I've talked about in some of my talks is using Microsoft's AI, machine learning service, Azure cognitive services with Xamarin to do some cool things. So some interns at Microsoft garage a couple of years ago actually developed an app that allows you to take photos of X rays of chest x rays. And then you just come to services, to look at the pictures and decide whether there's anything like pleural thickening or other reasons to be concerned in the x rays, which means that a doctor is not a specialist in like cardiothoracic stuff, so that you know, chest and heart, they can just be qualified to take the X ray, then the app can then don't you know, you don't need a consultant and maybe a city that's far away. So opens up all these health things, the developing world. And there's some other great ones as well about skin cancer prediction. So for me, I think the most exciting use of Xamarin is combined with come to services. So that's definitely my favorite.

#### Jamie

Excellent, excellent, I do. I went to a talk that Scott Guthrie gave, and he was like Azure cognitive services, and machine learning is awesome. And he just corrected all thing in front of me. And it wasn't really it was a silly idea. But it really showed off what cognitive services can do. It was like an image classification. It was then he made it public also over there is like, go to this URL and put an image in and it will tell you whether it's me or whether it's a cat. And of course, as soon as he did that people started abusing it by putting pictures of him and cats the system, but you know, they could have been worse. Yeah.

#### Luce

And that's what I love about it. It's just it's so easy to get started. So again, Jim will come up a lot Because Jim's had a big impact on my life, you know, it's been a great mentor and friend to me over the years, but he gave a talk at one of the global Azure boot camps that we both talked about together a couple years ago on come to services. And he did something similar with image classifications during his talk. And, you know, anyone that's watched him talk necessarily freestyle is very engaging. So I was just between the low barrier to entry would come to services and Jim's talk, I was hooked. So it actually led me to create my own app that use come to services. It's not it's open source, because the code on GitHub, but it's certainly not App Store ready, but that users come to services. And you know, there's no, I don't have to train anything, I literally just say here, here's a picture, tell me the emotion, the picture. Or, you know, here's some text tell me what you think the sentiment of is, because I'm like slightly on the autistic spectrum. And there's plenty of people out there who are neuro diverse, who maybe can't read body language and sentiment easily. And so this just opens up a way for me to practice a bit. There's also a demo app for talks, but I didn't generally use it for things day to day. And so yeah, again, quality services, it took fewer than 200 lines of code in this application, most of it is silly things like setting up HTTP client. So yeah, I was blown away by how little effort it takes to come to services. You know, as I touched on, I didn't even do any kind of prep, I didn't have to go on and say these, what the emotions are, there's just a load of concrete services that I've already know, sort of services and features that they put for you under different categories. But I like to call the five pillars of awesome. can just go on and have a look, I think it's I think it's the language, fishing, search and some other stuff. And and it's, yeah, it's brilliant. And we can put a link in the show notes. So they're kind of doxford conscious houses that show you what it can do. But yeah, they put they've trained millions of bits of data just to make your life easier. So a lot of the time. Yeah, if you want to say, you know, okay, here's some images of what something is and what it isn't. So you can create your own custom models. Great. You can even do it on the portal actually created a YouTube video how easy it is to do where I compared? Is this house from a house MD? Or is this Wilson from housing. But yeah, you can just very, very easily train your own models. But for a lot of the features, you don't need to it's there for you out of the box, Microsoft have done all the hard work. And so yeah, I just love coming to services. And so I think anything with it, and actually took a lot of good things, I think one app specifically deserves a shout out. So it was started independently, I think, but it's definitely part of Microsoft now and the developer behind it works for Microsoft, but something called seeing AI. So it's a Xamarin app that that you can use the for the visually impaired. And it will literally use the camera to describe what you're seeing. And so you can set it to say that I want to care about the scene that I'm into it might say, Oh, you know, around you is a bench in a park, or it might be you want to focus on people. So it will say, oh, there's a boy on a skateboard doing a trick. But it's literally describing the world to you constantly. So that you're you know, it's seeing the AI seeing the world for you. And I was actually lucky enough during built to meet the developer behind seeing AI when we all went to a meet and greet with James at a coffee shop. And so you're seeing it in action in the real world. And it just blew my mind.

#### Jamie

Wow. See, this is these are the kinds of stories people need to hear when, you know, when people come to me, I think at the time of recording, I released an episode where I'm talking with Luis Keaton here. And I was I said to him, Look, tell me about machine learning and AI and tell me how it's is it? The sky is falling, and everybody's gonna lose their jobs and Terminator and all that kind of stuff? And he's like, no, it's classifying images and helping people. And these are the stories people need to hear, you know, that they're seeing AI needs to be. I had never heard of it before he brought it up. Right. And admittedly, I'm not in the machine learning cognitive spaces AI space, but then the majority of the population isn't in that space either. So I think more needs to be sort of said about these these wonderful apps.

#### Luce

Yeah, Microsoft are doing a better job of that, you know, they have this whole dedicated page. Now you can literally, you know, if you've made an app using Xamarin, and you want it mentioned, you can I think there's even a GitHub repo where you can just fill out a form as it were, and then you'll get featured on this page. You know, I think it goes hand in hand a lot of it with the sort of open minded mindset of moving to open source is that they want to go you know, they want to see salmon do cool things. They want to show off what people are doing. Yeah, the team are very pro, giving a spotlight on people. So a lot of listeners might know that the dotnet I think it falls under the dotnet Foundation, but the dotnet community stand up. I think there's different you know, there's different subjects from you know, Visual Studio to ASP. NET to maybe GitHub, this they do different stand ups, they call them you know, It's always once a month for each topic, but they're on a regular basis, like for the month, and there's a mobile community stand up. And so one of the things they do, the first thing they do is go through blog post links for anything interesting that they want to showcase for the month, and Microsoft employees don't count. Like, so many employees don't count, you know, they are showcasing the community, they then go through any cool request from that month, and they, you know, in the, in the release notes, and in the standup, you know, they give a spotlight to the people whose work in the community has ended up in that release. So yeah, it's amazing what someone can do. But I think it's easier to work with someone because they make you feel cared about and what you know, you feel that, oh, if I do something cool, they're gonna care about it. And they'll help me with it if I'm stuck. And all that stuff is just brilliant.

#### Jamie

Sure. Yeah. Well, well, I've talked about how great the dotnet community stand up there in the past, and I have to say they really are. I'll make sure to put a link I think, I don't know, the URL is still around, but it used to be live dot ASP. dotnet or something along those lines.

#### Luce

Now it's live dot dotnet. I never know how it's written. I remember it because, you know, James always James tends to be the if he's around the main host of the stand up for mobile. And yeah, he's forever talking about live dot dotnet. But I never know which way around the dawn. Go. But yeah, yeah. Whether it's dot the word.or whether it's the word dot and then dot. Yeah.

#### Jamie

Sorry, I was just gonna say i think i think it's both cuz there's, I remember talking to some people about if you got to try dot dot dotnet. You can try it on net and the browser and they're like, I'm sorry, do that one again. try.dot.net. And it's try full stop. Do it fast off net. And they're like, even so that is a confusing URL.

#### Luce

As well, though, is that when the extremely stand up, so don't just you know, it's not just maybe to a dedicated website, they also stream to YouTube Twitch, I think in last community stand up. That is the first Thursday of the month for mobiles. I think it was last week. I'm sure they were doing it to periscope on Twitter as well. There was an extra platform that James wasn't there, I think. And I guess he was sorry, James, if you hear this, I didn't forget about your promise. But I've watched a lot of content in the last week. But yeah, it's not just on these different it's on these different platforms, which means it you know, there's on I think it might be on the dotnet foundation channel on YouTube, but you could just google it on like, on YouTube, not google it search on YouTube, got way to train to use Google's In other words, search. Yeah, you can. It's all on YouTube. So there's a playlist of all the previous ones and yeah, there's even a sub channel for Zarya. But we can cover we can touch on that one later. But yeah, certainly all the dotnet community stand up stuff is very easy to watch back. And it's just, uh, you know, I pretend to some of the other ones like the visual Visual Studio One, because, you know, we all care about our ID. But yeah, you know, certainly I can vouch for the fact that in the mobile standup they shine a spotlight on the people that use Xamarin. Because, you know, as they always argue, yes, they're the people making the tools. But if there's no one to use it, then what's the point? So they very much put an emphasis on improving, you know, David Autor now sends out some informed surveys almost monthly, just to improve and he reads every single response he gets. And so yeah, I think that means great. And, you know, if you've got an app you want to show off, tell them about it. And they will give you the space to shout about it. James does a does a YouTube show with Channel Nine called Xamarin show where he brings on guests either for short, or long form. episodes, and they'll talk about whether it's a new feature or, or a library they've written again, it's a place where James goes, Well, this is cool. Come talk about it, you know, show the people. So yeah, I just think they've got a really great open minded mindset of showing showing off other people's stuff. So you know, pick up some and show off what you've done, be proud of it. Awesome.

#### Jamie

Cuz that was going to be, then the next thing I asked about, we were unfortunately, coming towards the end of our sort of our allotted time. So I was just wondering, what are some of your favorite resources for learning about Xamarin? Right, there might be someone who listens to this and goes, summer incense meeting, I want to go learn it, what's the best place to go and sort of figure out what to do.

#### Luce

So I'll give you a few few of them because everyone's heard about learning styles, everyone learns differently. So I'll kind of try and cover some of the different content styles. So keep for written. Then you can go to docs.com. And then on the landing page, you will see on the right I believe it is at time of recording, it's on the right a nice big Xamarin button. If you click it, it'll take you to all the docs. The docs are open source. If you see a mistake or something that you think could be written better. Again, there's a little button at the bottom of the page to give feedback. You can just go on GitHub and submit a pull request. So Dr. Brilliant covers forms native navigation, you know, the different parts of the things you might want to achieve in an app and how you do it. So that's great for written content. If you prefer something a bit more interactive, there's sovereign pathways on Microsoft learn. So if you don't know what Microsoft learners learn is Microsoft's free, completely free learning platform. So you can go on there. And you can take learning pathways which are made up of modules, or just individual modules for a topic. And the page does allow you to filter it so you can find what you want. But that's brilliant for going on there. So if you want to learn some stuff to seven modules, nothing Jim wrote one of them. And so I can get that fantastic module, just Xamarin stuff that you can learn, then there's off, there's other stuff as well on learn. And if you're using Azure, for example, they actually create sandboxes in the browser for you to doesn't cost you a penny either to try out all these services. So learn to brilliant one, four written in sort, but it's more interactive, because you're actually going off to do something. And it's more like talking through it stuff. And the dotnet foundations GitHub, which again, we could put in the show notes, James recently released a new Xamarin Forms workshop on there. So that's another kind of route to go down. Or if you prefer listening, it's not so much a how to get started. But if you just want to learn a bit more about certain things, we've got an interest. There's a Xamarin, official Xamarin Podcast, where James is joined by Matt stonecrop, who's another senior developer, developer advocate at Microsoft. So they do that together. Then, as I mentioned earlier, James has merged conflicts, which has a lot of stuff in it as well. And then lastly, if you prefer videos, there's loads on the load on YouTube a lot of people and create VIP content, but there is an official Xamarin Developers channel, I think it's a sub channel for dotnet. Or like Visual Studio. But I think if you just type Xamarin developer into into YouTube, you'll find it. And that's where you'll find James's Xamarin show. Jas, originally, but magilla shares taking on this as our informs one on one. So she'll take you through a little snippet of Oh, you know, maybe you want to achieve this today. And then the video will show you how to do it in literally a few minutes. So if you like videos, that's a great one. So yeah, there really is like resources to shoot suit your learning style. So it's just, it's not about just the resources exist. It's more about what way do you want to learn and here's a way to do it. Okay,

#### Jamie

cool. That's, that's really good to know. I get loads a stick, because I always bring it up. My friend Paul says to me, that he gets upset. Yeah, how many times I say that I'm an auditory learner. So I definitely prefer this sort of the audio but officially putting across code in audio, is it that's a non starter? Unless, of course, for some people, unless, of course, maybe you're visually impaired or whatever. But yeah, reading our code in about kasina. public static void, main parentheses, parentheses, open curly, squiggly brackets, isn't it? That's gonna get you nowhere, right?

#### Luce

I've not

it's JavaScript. I think it's JavaScript. But there's a Microsoft MVP here in the UK who Rob miles, who recently I've noticed that I've not listened to it, because it's not a language that I have a particular desire to use. But I'm sure he started a podcast series recently where he's actually teaching code. And so I might find a link to actually for the show notes, because that might be quite interesting to listen to how he's teaching you something. Just auditory, auditory, or whatever the word would be.

#### Jamie

This interesting Libra probe miles because I studied computer science at the University. And he was the first lecture that I had to have. Oh, yeah, he's he's geniuses is Rob. He, like, I think, I can't remember the actual joke. But at my graduation ceremony, he was the sort of person giving the speeches and he said, the problem with these things is you'll get really nervous. So the best thing to do is to talk about an icebreaker. And he talks about a ship that breaks ice.

#### Luce

Yeah, last

last, last year, now it feels like yesterday. After build, yeah, real life build. They, Microsoft do what they call the the inside at all. And so what the inside of the tool is, is kind of the full time employees got given a break because build is very, very intense to prep for. And so they go well, we still want to kind of get the word out there about the stuff that we've announced to build. So they asked MVPs to get involved in the instance this might be inside of def torch you don't so I should know this. I spoke with three of them last year in space for a week. But in London, Manchester in Brussels. That was cool, but Rob was there for London and Manchester, I think but he did one of the talks, and it was just brilliant. It was IoT stuff. And it's just Yes, man. It's such a genius. Like you say, it's so funny with it at the same time, you know, he is clever. And it's Yeah, really nice guy. But yeah, he did a podcast on learning to code. So I might give it a listen. And so we can see how you do do curly brace curly brace in, in over the over video. I guess a lot of it is you just talk through it as best you can. But then put episode links in where you put code sample?

#### Jamie

Sure, yeah, sure. That makes sense.

#### Luce

Because I'm not I stream so I should know better. But if you're down with the kids, and like Twitch streams, there's a lot of people who stream as well, you know, so like James streams, usually every week, but yeah, there's other people as well out in the community who do salmon streams every week. So if you like streams, where you can watch it happen live, also interact and ask questions, then Twitch, or YouTube, streaming is an option anyway.

#### Jamie

Okay, excellent. I've, I don't know whether you've noticed those for the entire baseball when we do these. When when I'm interviewing, sorry, I keep bashing the microphone when I'm interviewing someone. And we have a sort of video feed so that we can see, you know, if I lean back, and then that kind of thing. But I've also been making copious amounts of notes. I'm on my third page of notes. So hopefully, all of these things will go into the journal. So for future reference, Jamie, when you when you come round to edit this, Jamie, all of these text needs to go in the shownotes. Excellent. So I mean, all the where can people go to find out more about what you're doing and the work that you're doing? And the stuff you're putting out there for people to? To do

#### Luce

that? So the best one is probably Twitter. So I'm at Lou's castle, one on Twitter, I'd love to be at least Carter we know what it's like to Twitter, someone still. And but I think it's because I used to because something else on Twitter, but then when I started to actually use Twitter properly and, and public speak, I changed my username to be something so it's a bit too late. But yeah, Twitter's the best one. Because if I write a blog, all right, maybe decide to go live on Twitch or post a video on YouTube. I'll always tweet about it. So yeah, Twitter is definitely the place to go. Of course, I've also on GitHub as not at be loose carta, but we can put it on the show notes. So as I touched on very briefly earlier, all my code is out in the open. As an MVP, I'm entitled to be a pro on GitHub, which means I could have private repos, but I choose not to. So if you want to look at my code and judge it accordingly, then go for it. But yeah, Twitter's the main one. And I don't keep my DMS closed or anything. So if anyone's got any questions, honestly, just messaged me on Twitter. I try and get back to everyone. Because learning is fun.

#### Jamie

Why not? Hell, yeah. Absolutely, absolutely. Being able to sort of help someone get to that moment where they go, Oh, I totally get it now. And then they get super excited and say, check out the thing that I've built. And you're like, that's awesome. That's just you didn't have something and now you have something. Look at how amazing it is to create all of these things.

#### Luce

Yeah, and also a quick sounds like a bit of a shameless plug. But I co curate the weekly newsletter with Kim Phillpotts who works at Microsoft, but he used to work for salmon University before serving got purchased, and they just merged into learn. Hi, Miss salmon University. Yeah, so Kim and I curate the newsletter, which is, we can put it in the show notes, which is weekly xamarin.com. And what that is, is a newsletter that we bring out every Friday, Friday for us anyway, or me, where we just curate the some of the best community blog posts or posts in general from that week. So it's not just communities also Microsoft as well. But it might be blogs, it might be podcasts and videos as well. So if you just want a quick place to go and get, you know, latest cool posts and content coming out without Xamarin, you can subscribe to the newsletter. So you can actually get it to your inbox as well, not just a web page. So there's a bit of a shameless plug, but it's genuinely a really good place to go to find a really wide variety of content.

#### Jamie

Excellent. See, I'd have put that down in the learning resources if that was me. But you know, I may do that anyway.

Because why not? Right, and somewhere to go.

#### Luce

Is this a good resource for learning? I guess I just because I'm involved in it. It just feels a bit of a shameless plug to go. Yeah. If you want to learn it, come look at our newsletter. I just mentioned it because it is genuinely useful. I've had people some of the only times in my life I've ever been recognized when I've gone somewhere. It says I'm an event where people going Oh, yeah, I know your face in the newsletter. So you know, it does help people. When you go to an event, when you go to something and it's like you go to get your name badge.

#### Jamie

Yeah, I'll talk about it off air. But I've had a similar experience at a conference by someone sort of spotted me with Jimmy. Oh my goodness. I got to talk to him. The podcast was an amazing experience.

But yeah, but that's essentially

covering all the things that we're going to talk about. So thank you ever so much for being on the show. Lucy has been a real pleasure. I've had a laugh. I've learned a lot of stuff. And I hope that the listeners will too.

#### Luce

Yeah. Well, thanks for having me. Again, I'm not quite sure what do you need to learn about my sermon shrine? But why not?

#### Jamie

Yeah, right. Why not?

Make sure more 3d person I feel

#### Luce

my real passion. That's it. You're diverse people can come a bit like a robot. I'm not but you know, you feel like one sometimes when you can't understand someone's face expression. But yeah, I we all have things that we love, and I love Xamarin.

#### Jamie

That's it. That's it. Excellent. Well, thank you very much for being on the show, Louis. I really appreciate you having me.

{{< paracentre "The above is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

### Wrapping Up

That was my interview with Luce Carter on the amazing things happening with Xamarin and Maui. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/), and there will be a link directly to them in your podcatcher.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice - head over to [dotnetcore.show/subscribe](/subscribe) for ways to do that - and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Luce on Twitter](https://twitter.com/LuceCarter1)
- [Code with Luce](https://lucecarter.co.uk/)
- [Weekly Xamarin Newsletter](https://weeklyxamarin.com/)
- [.NET MAUI](https://github.com/dotnet/maui)
- [Azure Cognitive Services](https://azure.microsoft.com/en-gb/services/cognitive-services/#features)
- [Mobile Chest X-Ray Using ML](https://www.microsoft.com/en-us/garage/blog/2018/05/mobile-chest-x-ray-analysis-uses-machine-learning-models-to-demonstrate-smart-medical-apps/)
- [Skin Cancer Prediction Using ML](https://medium.com/miccai-educational-initiative/intelligent-edge-building-a-skin-cancer-prediction-application-using-azure-machine-learning-5bbb7de84406)
- [MS Learn Xamarin](https://docs.microsoft.com/en-gb/learn/browse/?expanded=dotnet&products=xamarin)
- [Xamarin Developers on YouTube](https://www.youtube.com/user/XamarinVideos)
- [The Xamarin Podcast](https://www.xamarinpodcast.com/)
- [Merge Conflict](https://www.mergeconflict.fm/)
- [Microsoft Xamarin Customers](https://dotnet.microsoft.com/apps/xamarin/customers)
