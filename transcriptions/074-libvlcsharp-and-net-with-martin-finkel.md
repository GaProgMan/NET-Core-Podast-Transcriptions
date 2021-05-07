### Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor. In this episode I talked with Martin about libvlc, what it is, and what are some of the absolutely amazing things you can do with it, what libvlcsharp is, and how you can use _it_ in your .NET applications, and even how you can use it with Unity and VR headsets.

So let's sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

{{< paracentre "The following is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

#### Jamie

So, first thing I want to say, firstly, is it Martin or Martin or Marchin? I'm not sure about the pronunciation, but I don't ever want to assume you know, is it, Martin?

#### Martin

It's as you want, honestly, it's fine. It depends if you have a French accent or not, but basically, Martin is fine.

#### Jamie

Okay, fair enough. Well, welcome to the show Martin. It's a great pleasure to have you on here. This was this was an episode we sort of hastily thrown together that isn't to say that it's in any way inferior to any of the others. It's just like, Martin got in touch with me. And I was like, "oh, yeah, let's totally do this." And then I dropped the ball completely. Because you know, the whole current situation that's going on - we don't like to mention it on the show. I tend to use the term "unfortunate-ness," but we can use the term "the situation,"  that's not a problem.

But yeah, I was just wondering, Martin, could you give us a bit of an introduction to yourself for the for the folks who are listening who maybe don't know much about you?

#### Martin

Right. Thank you for having me, Jamie. So my name is Martin. I'm French, obviously. And I'm 28 years old. And I've been living in Asia for a few years now. Being .NET and Xamarin developer for the past few years. I blog sometimes, and I teach a bit. And I started working with this VideoLan I think over three years ago.

#### Jamie

Excellent, excellent.

So yeah, um, we are going to be talking about libvlcsharp, which is a wonderful project you've started. But just to give a little bit of background information: VideoLAN or the VLC player - well, I have a feeling that VLC itself is the client, and there's a server portion to it. But I as a user of VLC: it's a media player on my computer, I play everything through it. That's my entire experience of VLC. I know that it can play, audio CDs, DVDs, blu rays, video stream, audio stream, I can do podcasts with it. I can just, "hey I've got a file on my computer," I just double click, you know. It  essentially does everything for me. It's the best abstraction tool I've ever seen. "Here's a file," "Oh, brilliant. I'll play it." You know, that's it. I've even got, I've even had broken files, like because, you know, produce the show a bunch of others. I'll get sent broken audio and it just plays. It is brilliant.

#### Martin

Yes. So so as you said, there is VLC and VideoLan. So VLC means VideoLAN Client, as you said, which means where is the server, right? So, initially, so the project was started in the 90s. And there was clients initially, and then a server, but a few years later, the server components got merged into VLC, even though it kept it's name. So you can still do like, streaming with the VLC application. So we can sort of use it like a server. But, but it kept its name VLC.

So yeah, like you said, the app was born [in] 1995 was the foundation of the projects, and it got open sourced in 2001. It was a student project initially. And in 2007, I think or 2009, the VidoeLAN nonprofit was born, which, which does all kinds of projects, not just VLC, which is the most known one, but x264, as well.

#### Jamie

Yeah, it is. It's like the Swiss Army Knife of media, playback. I think. Like I say, I know that we can do streaming and multiplexing. And there's even a built in support for converting and stuff. But yeah, there's so many features that I never use.

#### Martin

Yes, it's like so it's, it's mind blowing the number of things you can do. And I see like, I've been working on this project for three years and I still discover new features. Sometimes, the reason can do so many things is that and you mentioned also that it can play broken finds of fights, like like midstream, there is something we are any synchronous, try to play it. And the reason it's so good at doing this and all the failures cannot is because Because Initially, it was meant to be. It was meant to be to, to play streams or internet. So it's, it's used to having networks falling down. And it's not it wasn't built for local media in the beginning. So it's very reliable.

#### Jamie

Sure, sure. And yeah, yeah, it's it's one of the most Reliant pieces of software I've ever seen. And, and I mean, we're talking a lot about VLC video. And but obviously, you know, you've worked with, you've worked on creating this lib VLC sharp. So it is, I was wondering, could you talk a little bit about the relationship between the two? Is it a wrapper around the API's? Is it how to how does it all work?

#### Martin

Right? So when people think about DLC, they think about the code and think about the application, right? What many developers don't know is that the application itself is also available to call features of the application itself, also available through a library, it's like, get like, so you have a good ci application where you can manage weaponry, but you also have to leap git, which is the dynamic native library of git, where you can embedded get inside your own application. So it's the same for your C VFC, application, UI, C, Li, and you have, etc, which is native, dynamic library, mostly written in C with a bit of c++ and assembly. And it's actually using, like, hundreds of open source libraries, like networking, for all the different products and network protocols it supports. So it just abstracts all of these for you and provides pretty high level c API. And also difference that I want to say about libvlc and VFC. projects is that VFC is gpn. Why? lithium Livia, she is a GPS. So if you want to use MVC, for example, in a closed source, proprietary application, you can that's completely possible. It runs pretty much everywhere on Linux is Windows, Mac, iOS, Android, TV, iOS, as berry pie, arm 64. Yeah.

#### Jamie

It really is the sort of universal media playback library, isn't it? Right.

#### Martin

So when I, when I arrived in this video, there wasn't much dotnet happening. And I saw that. So the, the apple guys had like, Objective C and swift wrapper to be able to call the ESC C library into their iOS applications. The Android guys had like Java gennai bindings, and then there was a c++ binding and everything. And there was ensured c++ cx binding to be able to do is interrupt on the UW p application. But there was no C sharp. And I saw what dotnet is, like very portable, it runs very well. And live yet is also very portable. So I thought there is probably something interesting that can be done here, because the interoperability part of the dotnet platform with the platform location services and DLL import, and all of this is pretty cross platform, thanks to mono and dotnet. So the decision chart is basically a very thin layer of C sharp that goes into the GRC public API interacts with it. And it exposes C sharp dotnet API which can be called from F sharp as well. Which is very idiomatic. So you have a simple wait for a synchronous operations. You are You can dispose of objects that are that are pointing to a four c structure. And so it's very, it feels very dotnet easy to use, which was the goal?

#### Jamie

Sure. Okay. So we've got this. So we've got this. So that's how libvlc sharp was sort of created. Right. And that's, that's, that's your goal, right to create this, this one sort of library that that allows you to wrap around that that C API that libvlc. Is it live video and live below? I forget which one it is. But they'll say, okay, so So you've heard that that one dotnet library that sort of wraps around all of that. And I guess, because it's dotnet code, you can drag it into anything where you can, like I said, you can do Xamarin, you can do dotnet, you can do mono, you can do whatever whatever dotnet can do, you can run this, right? Because there's that wonderful thing that dotnet does about the it can load unmanaged code, and it can do all of the things that it needs to do. Right. That's Yes. And that's wonderful. And so, so let's say I'm building a Xamarin app. Right? That's, let's say, right, I want to build a podcast playing app. Right. I've got a keen interest in podcasts. Sure. I got a keen interest in dotnet. And I want to learn Xamarin, let's do this, right. So I could pull in VLC sharp and use this tiny amount of it to play mp3 is right.

#### Martin

Yes,

#### Jamie

exactly. Okay. Okay. And then, presumably, if I want to, because some people are doing mp3, some people are doing videos, I can natively support that I just do the thing and get me the stream. Right?

#### Martin

Exactly. This is like you have, you just create a media object. And you give it to you Eri which can be a local file, which can be a remote stream, any format, anything, you just give it to it, and then you set it on the media player, you press play? And does it say? Well, yes, it's very simple. There is a few lines of code on the readme, where you can see, like call that initialise, which just loads the native library, then you create an object, then media object, then a media player object, and then you press play. And that's

#### Jamie

fantastic. I love that I love how we can make things that are super simple to use, you know, as, as a you know, because we're all developers, right? And there's a wonderful quote by Bill Gates, who said, you know, the best developers are the lazy developers. And, you know, if I can if I could pull the library in and read five lines of code, and it does, it solves the problem for me. Fantastic. Fantastic. Because then all that complexity, all that business logic II stuff is handled by someone else. Right. And that's what I love. And and like you said, that's kind of the point of this of lead. VLC sharp is it's like, let us handle let's let that do the difficult part of figuring out the media file format and the codecs and it does all of that stuff. It just presumably returns me a stream, or, like you say, you have a media player, and I just hook that up to the UI somehow. And it just all magically works. Exactly.

#### Martin

Speaking of streams, you can even if you have your own stream, you can also provide it to the GC doesn't have to be a UI. Otherwise, it's gonna do the file access of the network access itself. But if you want to provide it with a dotnet stream, any kind of stream that's also supported.

#### Jamie

Oh, cool. So I've got some kind of binary stream coming in with some audio data. And I just say is the stream do do the thing.

#### Martin

Right? Yes.

#### Jamie

I love it. Okay, so then. Okay, so let's go with Darkhorse. Right, we've talked about unit there we talked about, almost give the game away that we talked about Xamarin. Right, I've built this Xamarin app. For the you WP app that can do the same thing. Let's just pretend and get, you know, get a desktop app that's running udv due to VPS playing some videos and stuff. And then I go I know, I know I'm making a video game. Wouldn't it be awesome if I could play some kind of media inside the video game? Or I'm using the or maybe I'm using unity to create some kind of some VR experience and I want to play a video will place it right here. Right? I know that unity supports dotnet I know that live DLC is sorry. libvlc sharp is dotnet. Yes. Is there a cross over there? Is that it? Can I just drag and drop and it just works?

#### Martin

Yes. I'm gonna explain a bit more how it works. But yes, we started working on the Unity Suboxone so we got windows walking and you can instal it directly from the Unity store. But it's also open source. So if you want to build it yourself, you can. And we have an Android prototype, almost working. So it's just one last issue in MVC that was working in the past, and we'll get it rocking soon. So how does linear C sharp walks in unity? there's basically three components to understand. The first one is, of course, you have to have a linear c bit, but not any VC did. The currently VFC version that I ship on nugget is version three, because that's the stable version of the DFC. And also of the VLC app is version three. But for unity, we use VLC for. So those are preview, bleeding edge builds, and why do we use them, we use them because there is the new API in the VFC for which arose to have GPU decoding of XML textures. So if you want to, to, to have like, direct 3d, OpenGL OpenGL rendering to have hardware acceleration, through the VLC playback, then you need to use media c four, which got this new, very low level API added. So that's the first component, second component, you need the C sharp built in T turnkey ami supports, net stand out to zero target frameworks. So the data and then there is a small c++ plugin that binds them together. It does. So it talks with, with Unity. When you when you create a native Unity plugin, you have access to some components of unity, notably, direct streaming 11 components. And so it does some, some interoperability with the Unity wall and with the FC wall. So that's necessary missing piece. It could also be written in C sharp, but we chose to write it in c++ for now, to have notably, better performance interoperability, because it's a hot group, you know, every frame has to come really quickly. And you do interoperability between c++ and C. Right now, which is faster. C sharp. Right. I

#### Jamie

see. I mean, that totally makes sense. I mean, unmanaged code is until we get to some kind of supercomputer usage, unmanaged code is always going to be slightly faster than managed code, right? Until dotnet. Six, maybe? Yeah, well, yeah.

#### Martin
One or the other.

#### Jamie

Absolutely. And you know, we're saying this on the the several hours before dotnet, five is officially launched, which get a dice the episode, but that's fine. Because of the podcast, what I call the podcast Time Machine, wibbly, wobbly Enos. We're recording this a couple of hours ahead of dotnet. Five being announced that dotnet, conf 2020. But it's likely not going to go out until early 2021. We're looking at a fairer release date for this just so that people who are listening in the future are going but dotnet five is superior to c++. Well, that's because that's happening as we're recording in the future, but for you the listener in the past. Okay, so then, um, okay, so I can I can take, I can take a couple of at the moment, there's a couple of moving parts required, I take these, the experimental nightly superduper, amazing build of libvlc. I take the build of libvlc sharp, which matches that. And I take the c++ plugin, I do some wiring up. And I have media playback within unity.

#### Martin

Yes.

#### Jamie

That's awesome. But again, I'm saying media playback right. Like I said, at the beginning lip, lip, VLC does so much more than just media playback. So let's say let's say I want to watch some kind of video that's being streamed to me on the headset. And I want to look around, I know that there's, there's some support, we can maybe talk about it a little bit later. But the support for I think called 3d video, is that that's sort of turned my head and see different parts of infinity like,

#### Martin

yes, so in the in the unity package. Actually, these are a couple sample scenes to get you started where you just double click, press play, and then you have something walking One of them that I added a few months ago is 360. Play large sample. So I use the Unity keyboard events, and 360 video, which is, was a, it was recorded with a video camera sets on an eagle. And then the eagle just flew around. And the camera is like 360. So during the playback, you can use your keyboard, arrow keys and navigate through 60. Around the World Eagle that's flying. Easy. Wow.

#### Jamie

That's me, I love the future. I absolutely love it. That is that is amazing. And you know, there I am upgrading, you know, business loan credit apps that take this data from a form stored in the database, pull data back from the form, and you're doing all the really fun stuff.

#### Martin

I'm sorry, I'm sharing.

#### Jamie

Okay, so you're sharing the fun stuff. There you go. Okay, so there's all sorts of loads of really wonderful things that you can do with it. So what's the so we, we, we talked about how you can do a unity stuff. But what are some of we're sort of jumping around for that? That's Yeah, that's fine. For the for the context for the listeners, I send over a document with a whole bunch of I'd like to talk about these things. But if we meander off, then that's totally fine. I'm interested to know, you know, we'll come back to the VLC sharp as a project in a moment. Sure, because we talked about the different demo projects that you can do. Do you know of any Really? Like, what are your favourite projects that you've seen? You've done? Oh, wow, that is really cool. what's what's, what are some of those? Because obviously, we've said so far that, you know, you just bring this library in, and you have access to unlimited things. Right? So but that's kind of that's not as maybe not as interesting to some people when they go, Yeah, but what can I actually do?

#### Martin

Right? I discovered a new one very recently. I got in touch with the maintainer. It's an open source project. It's called race control. And so the maintainer is Formula One fan, and really loves watching races. And he told me that reverse engineered cine wave API of the Formula One platform so we could get access to the live stream, as you have to have a paid subscription to do so. But you probably wasn't satisfied with that player. And you wanted to have access to all kinds of channels and stuff. So he coded an open source player, which you can find on on GitHub. And he actually reported an issue with audio tracks switching in VLC and the VLC. And he told me to reproduce, you need to have a VPN that goes through the Netherlands, because my subscription is, is Dutch. So is there it's a do they do geo restrictions. So I need a VPN that goes through like Amsterdam, or something, and it's only on live streams. So the race is at 2pm. Amsterdam time on Friday, Saturday and Sunday, and you have an hour and a half during which you can reproduce. Yeah. But it looks like a pretty, pretty fun project. And it's some parts of the there is a screenshots that are two screenshots on the on the readme of the project at the bottom, and it has a playback playback view, looks kinda similar to the VSC UI in some way. Which would change the FC UI change in the next version. So

#### Jamie

that's really cool. Yeah. So just just to confirm, then to be able to use that you need a valid f1 TV subscription, right? Like, just just in case anyone listening is like, wow, I don't need to pay and now I can use this open source app. But it's totally not how that works, right? You do need to provide your own credentials. So that's proof that's just a little bit worried about lawyers coming knocking.

#### Martin

Sorry about that.

#### Jamie

No, that's fine. I always like to confirm things like that. Just because You don't want people to take things out of context. Excellent. Okay. That's, that's, that's really cool. I'll put a link to this in the in the show notes. Because like you say, if I if I scroll down into the readme, it looks very much like, not exactly like, but very much like, like VLC.

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

Oh, hey, it says, so there's a button that says Chromecast. Is that something that the VLC sharp can do? Or is that something that they've added? themselves?

#### Martin

No. Yes, it is. Chromecast arrived in the version three? And, yes, it's a very fun. It's a very fun feature, I think, because you can just stream anything you want on on your TV, here, music, or movies. But that two interesting things specifically having to do with with a Chromecast about the first thing as to it has to do with the legal side. So this, he cannot use a proprietary code, right. And the Chromecast SDK from Google is not open source. So technically, VLC can cannot use it. So what the VFC core developers did, is that a reverse engineered the Chromecast SDK to somehow build their own. And that was, yeah, pretty good. feet, I think. But there was some kind of limitation, in a way, not in their z chain, but in how the Chromecast walks from clasts only supports a few clicks, right? Like h 264. was known once. But yes, it doesn't. Right. It's more moderate. So let's say someone wants to play a dx ensemble. And so they started working at this as expected, and then they see a Chromecast feature, and they want to adjust it to to the Chromecast, then it's not gonna work, right, because the Chromecast doesn't support it. So knowing that the SE developers implement T the way to do transcoding in real time, so that if the media that you want to pay is not natively supported by the Chromecast, then VLC will transcode it in real time while it's being played. So that you can cast your DVD through your Chromecast if you want.

#### Jamie

That's amazing. I do have to say that transcoding audio and video, like you say, in real time is, you know, it's not a trivial thing to do,

#### Martin

especially on mobile devices. Yes. Yes,

#### Jamie

that's amazing. Um, you know, I do have a couple of friends who have servers running things like Plex and similar, open source of things, projects that are similar to that. And they were always talking about how I need to get more RAM or I need to rebuild my computer because it can't transcode this media format to that media format. Because, you know, I've got all my super ultra HD content, and I can't watch it on my TV, because it doesn't support it. And because the transcoding is too too much heavy lifting at the time. And so what I'm trying to get there is get out there is transcoding, any kind of media is not easy. And like you say, especially on a mobile phone right. Now, most mobile is mobile phones, tablets have arm chips, and they aren't really designed for heavy media, heavy lifting with media. So being able to do that in real time. Is is amazing. Yeah. Okay, I love that. So I could, I could throw together something using dotnet that uses some kind of UI. I have a collection of media, and I go read, play that on my Chromecast or maybe perhaps connect in a stream to another device on the network. There's not just a Chromecast. So I have another device that's running, some writing and there's a stream of the read. Is that possible?

#### Martin

I think we had Google Summer of Code students that walked on aeroplane spot. I'm not sure what's the status of this, but that was in the works. Is that some point? And if you have a UPnP NASS device, that's not I mean, you can read from it. I don't think you can stream from it. But to it, but you can. You can. You can pay for it.

#### Jamie

Okay, so there's a little support there. That's, that's pretty cool. Um, so what about so you've said earlier on that via video and the project started a good open source, and then they created this not for profit organisation, is it not a profit? Did you say? Yes? So does that does that mean that, you know, if you wanted to commercialise libvlc sharp, is that something you can do if you wanted to, because I'm not 100% ofay with all of the many, many different software licences that are around, right. So if you Yeah, right. So, so if you wanted to, so does that leave you in a in a strange position? If you and the other collaborators say, hey, let's commercialise this because it's using some other? He said, lgpl. Right.

#### Martin

Right. So it's dual licenced. So we do offer a commercial licence. And that's an handled by the commercial arm of VLC, which is called the labs which is a for profit company, which does all kinds of support, customising and missing the world here, but concerting plays a while making sure which so you don't have to there's all kinds of support customising and consulting around VLC and the VLC. But all of the projects are still open source and can be used from proprietary applications without an issue. So yes, that's a French nonprofit. videolan isn't French nonprofits. And video Labs is the commercial arm. So yeah, no, no problem there.

#### Jamie

Okay, cool. Okay. So I saw that when I was clicking around and doing some research, yes. In preparation for the episode, you have a you have a book for libvlc sharp in unity. Is that a? what's the what's that all about? Is that, is that just getting started? What was the Yeah,

#### Martin

I don't have a book yet. But I'm writing. Right? Yes. I'm writing it. It's about beadalon. About the sea. And about C sharp, specifically? Yes, definitely. I'm still writing it, but I'm hoping to release it in a few months. Yes. Cool. Okay, so

#### Jamie

what's the what's the target audience for that? Is that a I want to implement some some feature that libvlc sharp provides in my unity app? Or is it just a case of, hey, there's this other thing you can do? Come check this out? What's the

#### Martin

right so it's not specifically on unity. It's really any dotnet projects. So who might be interested dotnet developers that need to build multimedia applications, for example. other developers that would like to use the DSC with any language, because there is one part that is specifically on the DSC. And since the DSC is the same everywhere. On every platforms, no matter which language you're going to use is maybe a few different API's because of the wrapper, how it exposes things in your target language, but the core features are the same. So these parts will be relevant or not.

#### Jamie

Okay, so as developers of all kinds and shades and sizes, and all sorts, all kinds of languages, all kinds of whatever, all kinds of frameworks, as long as they are interested in media playback, and all of the millions of different features that live VLC and libvlc. Sharp can support pretty much really see. Okay. All right. So what we talked about race control. Do you know of any of this any other interesting projects that are built with libvlc? shop?

#### Martin

Yes.

And this one is called lively. And it's a live wallpaper. So you can get interactive desktop wallpapers.

#### Jamie

Oh, cool.

#### Martin

Yeah, it has a readme with a few images, you can see. But it can do and this is I've talked with the maintainer of this project as well. And he mentioned he was interested in avalonia support because he was bought this application two minutes. So we are about to ship.

#### Jamie

Oh, cool. Okay, that's, you see that that to me is really interesting. I can because I was looking through the Examples just now as you were talking in this, like, Hey, you can have these, you know, images, maybe a GIF or a GIF, a moving image as your background, you can have a video as your background. And then right at the bottom of the readme is like, oh, also you can use emulators. So if you want to play, you have a video game playing as your desktop wallpaper. You know, as someone who is very into video game, so one of the I do a few other podcasts, and one of them is a video game podcast. And I'm like, Whoa, whoa, whoa, whoa, here we go. This is now you're talking my language? Right, I have to show this to my co host, who is a Windows user, and until the avalonia support as Bill and B, he may be able to use this and just have some video gamers. assessable. Yeah, I think it'd be quite excited about it.

#### Martin

You can another that not full known feature of EDC is that you can actually record your screen.

#### Jamie

Oh, wow.

#### Martin

Okay. So you can you can cast it to the Chromecast as well.

#### Jamie

Right. Okay. So you see, I do know a lot of people who, who do video training stuff for software. And they tend to use OBS the open Broadcasting System and just do right or locally, which is fair enough, if that works. But hey, if libvlc supports it, then that must mean that they've VLC sharp supports it, which means I could throw together an app that goes right. Okay, record my screen. Right. I went to do some things and then hit stop. And our pops of video of some kind, right?

#### Martin

Yes, exactly.

#### Jamie

Excellent. Okay. You see, this is I'm learning so much more about the VLC and what video land supports whoops, gives me and what veal libvlc sharp supports, just by talking to you. It's amazing. Okay. So, so we talked about that. What about? So we hinted at it a little bit when we talked about the the f1 viewer, the race control app. So technically, since the lip feel C sharp exists, and that helps to bind to the live VLC library. Yes. I can totally re implement VLC in dotnet. Goodnight.

#### Martin

Yes.

#### Jamie

Yeah, totally. I mean, assuming that, like avalonia, or some other cross platform UI system, right. Kay, something like that. Right. It totally just, you know, whatever. I'm build my own VLC.

#### Martin

Yes. So the VLC app trophy is cutie cutie. I don't know how to say that. But yeah, Qt. Qt framework, which is cross platform framework, and it's used for Linux and the Windows application for the Mac OS applications. Based app. So yes, you could definitely create a new dotnet based app using, you know, any job just like regular WPS and build your own chrome of DSC? Yes, definitely.

#### Jamie

Have, you see, this is what I mean, this is why I love talking to other developers to find out what they're working on. Because now I'm like, do you know what, I might just spend some time because like, when I'm when I'm looking for when a new technology comes out, and I'm looking for a project to how do I use this new technology, right? You look at the documentation, and let's say you go with, I don't want to pick on anything, but let's say Angular, right? There's the angular heroes thing. And it's like, create a Hello World. And I think that's, that's fine. But I'm elbow deep into a project and I need to create a UI lol isn't gonna help me? No. But if I'm, if I'm making if I let's say I want to learn it. So you've said that libvlc sharp is quite literally a case of here's a bunch of code 567 lines, and you've got your player go here. If it's if it's, if it's that simple, and I want to learn some UI technology, well, why not use the code that I already know, works? a file that I know already works in the code because the code can handle any file. And let's explore the intricacies of building this. This, this, this user interface, rather than creating a to do app, maybe, maybe we can make libvlc show, then you to do app that everybody starts with Sure. Nothing anything, right?

#### Martin

I'm done with that. That's, that's

#### Jamie

excellent, excellent. Let's do this. Let's do this. Maybe that's what I need to do. Because I still want to pick up, I want to still want to explore uno and avalonia, and a bunch of the other UI frameworks. So why don't I do this? Right, let's, let's do this. Excellent. Okay, so you've talked about with with with libvlc sharp, it's a couple of lines of code, and I've got media playback from wherever. I've got perhaps a few more lines of code. And I can record my screen. I've got the these wonderful people who've done some things like, let's watch the f1 stuff. And I saw some buttons there that I'm not sure. Like, share the stream, copy the stream, download the stream, you know, I don't know whether f1 TVI should do that. But if that's a button that they've enabled, that's a button that that developer has chosen to an apple, but that's fine. You can have you can have like a live wallpapers. Where have you have you got, like maybe one or two other examples that you can share with people going, Hey, let's do this thing.

#### Martin

Yes, I've I've written a small sample. So I have, I have a git repository that is called the C sharp samples. Well, there are a lot, a few few minimal samples. I really like to have samples that are complete, but very minimal. So the least amount of code to perform a given specific task is how I like to write samples not to have like, all kinds of unnecessary code just really focused. And one of them is called NP St. It's a it's a small ci app I wrote earlier this year. And it basically uses mono current. So monitorings is libtorrent. Implementation birds in C sharp, so it's not a C sharp binding over a native library. It's an actual C sharp full implementation of the torrent client libraries. So it allows you to, to connect to torrents and consume them. And new newish API that was added in the model to encode was to give you a stream, that was just like a stream of your off of your forums that you're consuming. It was never ending, right? Because you're constantly getting it until it's finished, I guess. And you only see. So I found a media that is free to use. So no pirating here, and I hooked it up, I could hook to stream from monitoring to live decision. So that when you start Yeah, monitoring starts, it starts receiving packets and pcs of your current. And when you have enough gifts, he starts playing in real time while getting the stream. And if you add the C flag to the command line, you can also send that to the Chromecast in real time.

#### Jamie

I see I see. So I can imagine that I have. Okay, let's see. Let's see, we've all seen these things. Right. We've also see I this is why I love talking to create a such as yourself, because I'm starting to have ideas, right? I've seen in the worlds you know, the big screens they have at for kiosks and information desks and things that are constantly playing video, right? Yes, most of the time, that is a view a video player with maybe a playlist that is running through the media is stored locally on that device, right? Let's say I have 100 of those to manage. And I want them all to play the same. The same content was the trivial answer is take a USB, copy the content onto every single device and set the play, which is brilliant. But when they crash and need to go to that machine, maybe some overflow happened, or maybe some update happened or whatever, and then need to manually reboot that machine or restart the media playback. To get it working. What about if I had a central server that had a collection of all of my content that I want to display on each screen? And all I do is I create a an individual torrent file or a playlist file with each of those videos for those specific screens. I go to that screen. I run this app. Boom, there's my content constantly playing on that machine, right? And if the machine crashes, I just have to reboot the machine and I could do that remotely. I don't need to go up and plug in a USB, right? Yes. It can be an incredibly thin client that just ruins the screen. Something maybe like a Raspberry Pi Zero I guess as long as it can support the video codec or a screen with a Chromecast plugged in. And the super low tech right? Yeah. Because I've seen like I said, I've seen a whole bunch of these that have crashed in the public. As you know, you'll see the people who work there like we don't know how it works, we don't know what to do. We're gonna wait for the engineer to come in. Whereas something like this if you have a torrent on some Over the yuan, you could likely just stream directly to it. Yeah, I like it. Such a great idea. And like you say, it's using a, a was the public domain. Phil nagus. So

#### Martin

the woman was looking for? Yes. And I, I focused on making this one as small as possible. So if you look at the number of lines of code, I think it's like 145 counting the using uses lines, which really smart.

#### Jamie

Yeah, and it works

#### Martin

on Windows, Mac, and Linux.

#### Jamie

Excellent media playback via return file of any media playback, and then transcoding over to Chromecast, regardless of your operating system. This is what I love about the future. This is it. Excellent. Okay. So we talked about libvlc, sharp a little bit. But it's not just you, is it? I mean, I'm not trying to reduce the amount of work that you're doing. But it's not just you who's working on this, right, of course.

#### Martin

So there's a few contributors. And I, as it was a small community around it, that starting to, to get bigger and bigger. We have a small Discord server, with about 200 people in it now with all VLC bindings, and only VLC users to the dotnet people, but also like, the Java, maintainer of the VLC, j. c, which is a Java binding. And there is VSC. CIT, which is Objective C swift banking. So yeah, we we have a small community around around BTC, all bindings included and quality a C sharp, we have contributors, reviewing requests. So you know, support was mostly done by Stefan mechanics, which is another French guy. And yeah, I just got a request recently for Java support, actually, which I read it today. So yes, it's definitely not just me.

#### Jamie

Excellent, excellent. I like that, when I'm, when I'm looking at some kind of open source project to poke out and dry. I always like to know that this, you know, it's not something that's been abandoned, or it's not just a one person thing, right. I don't mind using a project that is, is one person. But then I wonder, like, what happens if that person like decides to move on? Or? Or what if, what if they decide That's it? I'm done. I'm gonna I'm gonna abandon this or

#### Martin

is it Right, right. Yeah, right. Right. But yeah, of course,

#### Jamie

or what if? And, you know, it's terrible to say this, but what if they pass on? Right, right, then what happens? Yeah, I mean, there's more things to worry about than my project is using this opens. Awesome. But you know, I mean, what happens in having a healthy community around something really helps, because then, of course, you can, presumably, if I if I wanted to, I could join the community and maybe ask for help. Of course that, you know,

#### Martin

I mean, yeah, so there is a Discord server, just come join and ask your question. Someone will reply,

#### Jamie

no problem. Excellent. See, that's what I really like you see, you need to be able to have that help and support should you get stuck. But from the sounds of things getting started, you probably won't get stuck.

#### Martin
I hope not. But let me know if you.

#### Jamie

Excellent. Okay. So what about what's the best place to go to find out all about libvlc? sharp, let's say someone's Listen to this. And God, I've had this fantastic idea. I'm gonna go build my app. I want to get started with libvlc sharp, how do I get started? Where do I go? What's the best place

#### Martin

and says, Get repository and the discord server. The Git repository is contains the documentation, where you have simple apps where you can just clone build, run, and you can just start from something that's already walking 10 community projects which are also linked inside the documentation, and the discord server if you want to chat his people and ask questions you have like questions about contributing the documentation, or just if something is supported or not, then this goddess

#### Jamie

Okay, excellent. What about catching up with you then? You know, I saw obviously we connected over Twitter. But is that a place that you talk about the the, the progress of libvlc shop? Or is it a better place to go? And okay.

#### Martin

I'm not always active, but when there is a interesting update, or something, I will usually send out a tweet.

#### Jamie

Okay, excellent. And I can see as well that you you do you do have a blog? Is that something that you're doing a lot more? Because obviously, I can appreciate you going live VLC shop that I know about that, because we've talked about it. You've got this idea. If you've got the book coming. You've got Twitter, you've got the blog, boy, do you have time to update the blog? Is this something that you do occasionally? Who was it just like, it's there? It's it's been sat there for a year, I'm gonna come back to it, because I've done that. If there's something out there that I will come back to eventually. Right.

#### Martin

So I've actually looked at it recently, and I think I need about three or four articles per year for the past three years. So that's Yeah, not that much. Okay.

#### Jamie

Sure. So there's some content there if people want to go check it out and learn way more. Excellent. Okay. Well, I guess. I mean, that's, that's essentially all the things that I've got written down there, I'd like to ask you about. So we've got we've got links for libvlc sharp, there'll be in the in the, in the show notes, we've got links for I'll have to see vango link for for the discord, if that's okay, so people can join if they want to. And I guess the VLC sharp is available on nougat right. So I just do dotnet new or dotnet add package and we're done. Right? Exactly. Excellent. Okay. Well, thank you ever so much, Marty. There's been it's been fantastic talking to you. I realised that it's your your evening my morning but that's our time zones working. Yeah.

#### Martin

Thank you so much for having me. It was a it was very nice meeting you and

#### Jamie

excellent was really nice talk to you, too. Thank you ever so much. See you. Bye.

{{< paracentre "The above is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

### Wrapping Up

That was my interview with Martin Finkle about libvlcsharp. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/), and there will be a link directly to them in your podcatcher.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice - head over to [dotnetcore.show/subscribe](/subscribe) for ways to do that - and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Martin on Twitter](https://twitter.com/martz2804)
- [libvlcsharp on GitHub](https://github.com/videolan/libvlcsharp)
- [Martin’s blog](https://mfkl.github.io/)
- libvlcsharp examples:
  - [Lively](https://github.com/rocksdanister/lively)
  - [RaceControl](https://github.com/robvdpol/RaceControl)
  - [lvst](https://github.com/mfkl/lvst)
  - [JukeCore](https://github.com/selmaohneh/JukeCore)
  - [More examples](https://github.com/videolan/libvlcsharp/blob/3.x/docs/made_with_libvlcsharp.md)
