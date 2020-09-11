### Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is episode 61: Azure and Live Conferences With Andy Morell. In this episode I spoke with Andy about he and the [Live Coders team](https://livecoders.dev/) ran two live video conferences using a single VM in Azure.

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

{{< paracentre "The following is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

#### Jamie

First thing I want to say, Andy is, thank you ever so much for taking time out of your Monday evening, to talk to me, Mondays are traditionally one of the hardest days in development. I tend to think of Tuesdays being honest, because you're chilled out, you're coming into the week slowly. And it's Tuesday where you get hit with all of the stuff you didn't get to do on Monday. But that's my personal opinion. But yeah, thank you for spending part of your Monday evening talking to me about all sorts of stuff.

#### Andy

No worries. It's not nice and bright outside, which sometimes you won't be outside in the garden having a bit of a beer at the end of the day. But monday so me I started midday finish at like 9pm. So it's one of the one of those things working with a US client.

#### Jamie

I see it I totally get that with some of my clients. I'll start five, six o'clock in the morning sort of thing and work through and then just stop when I hit my end of day sort of thing, but everybody works in different ways.

#### Andy

That's what should be really what's the point of remote working point of being your own boss and all that sort of stuff. Really?

#### Jamie

Absolutely. We're not necessarily going to be talking about being your own boss or kind of remote working today, but maybe we should look back and talk about that another time, I guess. Definitely. Yeah. So any interest of letting folks know who you are, I guess, could you give us a bit of an introduction?

#### Andy

Okay, so as Jamie said, I'm Andy Morel. I am a dotnet developer and have been for a long time since dotnet. One when I finished university, I've been developing since since a young age since I was eight. So you're looking at 31 years of development experience right now. But that was back in the days of ZX Spectrum and copying programmes out of books, and just going, you missed the go to line. So I'm a dotnet developer and recently, I'm a Microsoft MVP in developer technologies. The standard Yeah. And I've got my own business called seventh heaven. I basically just do a lot of software consultancy, and cloud architecture, developing a few bits of software for anyone who wants it really. And that's about it. I

#### Jamie

feel like I had a similar initial sort of origin story development. I think I've covered it in earlier episodes where we had oakiness this is an Amstrad CPC 464, we had and we did the similar thing of, oh, wow, here's a magazine copy paste this out of the magazine. And I still kind of I was doing it early this year actually, because I got a book called code the classics Volume One which is written by essentially the the Raspberry Pi foundation. And it's a whole bunch of the old coin op games but rewritten in Python with PI game zero. And he quite literally is maybe 510 pages of interview with a developer off say Pong or something. And then 510 pages of how we are going to re implement it, and then the entire source code listing and then go here, you know, go to this GitHub repository to get the rest of the code or to get the documented code and stuff like that. It's really

#### Andy

quite cool. Yep. And that's the way that's the way we used to like it. Until until the internet came up.

#### Jamie

Yeah, that's it. And then, yeah, the internet came along. And it was just a case of get cloned and you're done.

#### Andy

For the first few years, but

yeah, it definitely got there in the end.

#### Jamie

It did it did. Goodness, I can't even imagine working without source control these days. I can't even imagine whether like, if you think about it. The Unix operating system was written before source control was even a thing. Like before they even thought put it onto tape and check out the master tape and make a copy of the master tape, make your changes and then put the changes that are on the copy back onto the master tape and that becomes the master tape before all of that just mad in it.

#### Andy

It is crazy. And we've gone a long way in a short time Really? Hmm.

So let's see where it goes from here. Yeah.

#### Jamie

So one of the things that that I know you're very interested in is this this lovely idea of live coding. And I know that we talked to Jeff Fritz in the past one of the really early episodes about live coding and his sort of experience of it back then. And that was almost two years ago. So I was wondering, because it's been two years and because our industry moves so quickly, could you tell us a little bit about sort of maybe your experience with live coding and all that kind of stuff, maybe how you got into that kind of thing?

#### Andy

Yeah. So my, aka also known as his lucky number, Slevin, and yes, it's taken from the film back in 2006. That is my gamertag and has been for years, and I joined twitch Which wasn't twitch back then 10 years ago, it was as a gamer, and I was one of the first people in the UK to get one of the Halo games. I think 2010 was Halo Reach. And, and it came out, and I did my first game stream. And it was fantastic. Lots of fun. So three years ago,

Unknown Speaker  
I

#### Andy

started gaming again, I had the I had,

I had the developer rig, but at the same time, we also had

a gaming rig and sat in front of me. So I thought I'd use it started streaming again, started playing games. This was three or four months into my youngest child's being around and I didn't want to spend more time with them. So I didn't really go out on the bike as much so I actually attached the bike to the PC and did some cycling streams, believe it or not on zwift then very, very soon After that, I just decided,

no, not for me.

And a chatbot at the time was shutting down. I decided to do a coding stream of doing my own twitch chat bot, which is basically a rite of passage for any live coder is become a live coder, build your own chat bot,

and then then move on to the rest.

So yeah, it's been a crazy three years. And I think I just started just before Jeff did. And since then it's just it's just been absolutely mad. And this is why this is how I've sort of got to where I am now. And I am part of Jeff's team, the live coders, which he probably didn't mention back then because they are new, we will establish at the beginning of 2019.

It's progressed

and in those three years, we've now the tech committee In the live coding community has grown. I mean, the live code has as a team in its on its own is 160 plus members right now. And it's growing. And we're accepting pretty much anyone into the team, as long as you sort of got prerequisites to do with Twitch, so it's a case of you've got to be affiliate, you've got to sort of hit a decent average viewer count and that sort of thing, just and you've got to be in the right mentality of inviting people in teaching people to code

and not sort of

inclusivity is basically one of the main things about it and just trying to teach anyone and what I get from it is, my knowledge in the past three years has grown exponentially. I will talk about it in a few minutes. But in the first live coders conference, I did a talk on finding your niche in your career in Learning to progress and stay relevant in your career. And my niche is literally streaming. Because I learn I teach. And that's how I grow. And that's how I have grown. And where I am today is my client is currently Twitch, which is crazy to think about that three years ago, I started development on Twitch. And now today I'm working with them.

#### Jamie

That's pretty cool. There's a whole bunch of stuff I want to try and unpack in that bit. But the key part, I guess, is that I love this idea of there are some live coders who I don't know whether they're part of the team or not, but but when I've watched, you know, when I've tuned in and watch them, they've essentially been going red. I know how to do part of this. But I'm also going to go on this journey. And if you stick around, you can go on the journey with me of how to learn this API or learn this technique or something. And I honestly think that's a brilliant way to learn. In any previous careers, Australia, the university I actually went down their path of becoming a teacher. And one of the best ways to get people engaged and to help them retain the knowledge that they've just learned is to get them to teach something else. Someone else sorry. And so this whole live coding thing is is wonderful to me because it's immediately you're reinforcing what you've just learned by discussing what it is you've just learned and how it all fits together. So I completely can get behind all of the live coding stuff, even if it's just for your own personal development. But then I do remember watching I think it is, Jeff. So you're Jeff Fritz and one by James monta Magno where they like they'll maybe spend the first 10 1520 minutes sometimes up to 45 minutes and just say, hey, how is everyone? So yeah, let's let's get questions from from the audience. And let's see if I can maybe redirect you to the right place or show your resource that works

#### Andy

and I think I think that's sort of why I'm still doing it. And I mean, it's one of the big reasons I became a Microsoft MVP is because I've been doing it, and I got recognised by it for it. It's been it's been such a crazy experience. And I would say, it's not for everyone, just like anything is not for everyone, like remote working like working in sips companies working in small companies. It's not for everyone. It's awesome. And I love doing it. And I will teach and try and impart my knowledge on others, as long as they listen. It's an experience that you need to see to believe it. I think there's been some crazy stuff over the past few years. And some of the stuff I've seen and learn is amazing. And I think that's where entertainment. Okay, this is one thing is edutainment is one thing because it's education, entertainment. It's where People get their entertainment from now, there are so many more possibilities. And it's not just about sitting in front of the telly box and viewing a series of something on Netflix for 14 hours straight, breaking bad. But you know, I mean, it's a case of, you can get your entertainment from anywhere. Now, as long as you've got that little bit of an internet connection, which is one prerequisite for the moment, but and it's been a bit that's been a bit up and down, but at least it's seems to be fairly solid,

#### Jamie

as to so that was going to see, that's kind of related to the other thing I was going to say. But you've kind of already answered it anyway. And that's, you've said, it's not really for everyone, right? And we've just basically you've just said that you're sourcing your own. Entertainment essentially just requires you to have a stable internet connection. Is that really all that's required for the live coding stuff Because I know I gave it a go a few years back, and I had a Mac air right 2015 Mac air, which is not the most powerful machine in the world, and had a little external webcam and an external microphone connected to my Wi Fi and it went pretty well. I mean, do I need oodles of hardware Do I need a specific just a laptop and an internet connection? Not specifically.

#### Andy

So when you start streaming, you can just download a little bit of software, twitch have their own bit of software called twitch studio now. And you download that and there is literally a button that says go and you don't need a webcam you don't even need a microphone usually.

And you can just share your desktop and or share the game that you're playing. Now,

that can get a little bit messy at times because when you do that you are generally using your CPU to do the encoding. So when encode and then on to out of your internet and over to twitch and then they broadcast it for you. Now, yes, you can throw money at it, then you start to improve and you see the marginal gains and you see the extra little bits. So if you are starting on a MacBook Air be not the best thing to stream on because the CPU is going to get

hammered.

So maybe a 500 pound $500 Mini PC, I've streamed from a Dell optiplex which was an old Dell from an office that I got for pennies on eBay, because it was an old office stock that they didn't want anymore. So I grabbed that and that's what I streamed on for a little bit as well. And then you sort of add a webcam which usually has a built in mic that adds to it and then you sort of progress. So I have now got an audio technica 80 2020 XLR mic plugged into a nice little focus right preamp, which then is USBC straight into my PC. My camera is the next thing I'll probably upgrade because that is a Logitech nine, c 920, which is a fantastic camera, but you can get better and it's, it's all part of the broadcast quality and you slowly build up and is not needed. But it's a lot of fun.

And it's a good hobby. And when that hobby becomes your job, be a little bit interesting.

#### Jamie

sounds a little bit like podcasting to River. This will de the recording but last week I gave a talk on my experience of getting started because I've been doing this for now for almost three years. And it's getting started and getting set up and stuff and it is this almost exactly the same like you said you get yourself something that you likely already have all the hardware you need already right because I have a laptop before front of me, it's got a microphone built into it. It's not brilliant. I'm using a external mic, but you know, it's got a microphone built into it. If you want to get that those first two or three episodes out of the way, use that one. whilst you're still sort of cooking the idea, and when you get to the point where the idea is cooked, you then go, right, okay, I think I can upgrade this now when you upgrade one thing and carry on, and then you upgrade the next thing and then you carry on right? When I do interviews for either this show or some of the other shows that I do. And they're in person, I have a bunch of hardware that I use that I just literally sit down on the desk, plug a whole bunch of microphones in and push a button and it does everything for me, you know, I don't use a laptop because it's too big. But I have this very specific piece of recording hardware called the zoom h6, which is not in any way related to the zoom video conferencing software. But yeah, and then plug a whole bunch of microphones in, everybody gets a microphone, it's got a preamp and all that kind of stuff in it. But I'm not in the room that I'm in right now. I've got a whole bunch of hardware for preamps And filters and equalisation and stuff. But yeah, that's been slowly added to. So I guess the streaming stuff is kind of the same, then you just slowly adding in iterating, right in the same way that we slowly add and iterate features when we write code, right? You don't, you know, go from zero code to the finished product in one step. Yes, exactly.

#### Andy

And I think I think that's what we're here today to talk about, isn't it? It's, it's about the live streaming. And the next thing on the map as it were, because one thing that you can do, if you don't have the hardware

is borrow it.

So you can if needed using as your VM to stream from.

So you have your laptop,

that may not be maybe just a Chromebook, in this case. So you load up Chrome, you go to a specific site, there's a little little app called

OBS Ninja, which is

based on web RTC, so it will share your webcam and your desktop. And what you can do is you can stream those to a virtual server

as your and then have

that as your actual streaming hardware. Because if you're not going to be doing gaming, if you're going to be doing gaming, you're going to need the hardware. If you're just streaming, say, a desktop and a microphone and camera, Bob's your uncle, you can actually just rent the hardware for a couple of hours, and then shut it down, and then it won't cost you anything. So you're looking like a couple of dollars for a two hour stream, maybe a little bit more. And I think that could be useful for somebody.

#### Jamie

So going on the idea of renting a virtual machine to do the difficult bit for you. I think I've done something similar in the past, or one of my previous employers, we had a contractor come in and they needed to do some work and for some reason, we couldn't get them a powerful enough machine. And so what we did was we said here is a Relatively okay laptop for doing your work with. But here are the remote credentials for using your Windows VM in the cloud. And we just literally rented a VM for a month that would automatically shut down at, I think half, six in the evening and wouldn't be available again until 9am. And he just came into the office, switched his laptop on connect to the VM, which had, you know, Visual Studio and Photoshop and all of the tools that he said he needed. All of those pre installed. And then yeah, we just at the end of his contractor, we just screw up the machine. And there we go. It's a great idea because as your GCP AWS, they have this unlimited compute on tap, right?

#### Andy

Pretty much. Yes.

There are limitations.

#### Jamie

Yeah. Unlimited body cards. Yeah.

#### Andy

Yeah, in But definitely, definitely in bunny quotes, especially when you're looking at the instances that I'm going to be talking about.

#### Jamie

Yeah, so for Related to that, then I know that one of the things that we were sort of chatting about before and that I've seen you talk about a lot before and something you mentioned in passing there is using that in bungee cords are limited in Balakot CPU time that you can rent as long as you have the money to pay for it using that as your AWS or whatever, compute to support conferences, right. I mean, more virtual conferences but to support conferences.

#### Andy

Yeah. So at the start of March, one of the live coders team came into our Discord server and said, I won't be speaking at this event because it's being cancelled, which we do are an online conference. And instantly got jumped on as Yes, why not? And one month later, we were running our conference. It was very, very, it was completely nuts how quickly it all came together. sort of how we got, I'm going to say it was 10 speakers or 1414 speakers. And we had a 17 hour long conference. There was ridiculous numbers flying about. So the actual total time watched by all the viewers was 3.2 million minutes, which equates to around about six years. Wow. So if you take that sort of six years of watch time, and say the stream was 17 hours long, you sort of get a good amount of time and people just sat there watching you, that was just mind blowing to us. And it was crazy how we got to pull together. But it was very, very simple because every single one of the actual speakers that that on that day was a live coder, we decided to sort of stick stick within the team for the first one. Just because Ease of actually doing it, because we were all streamers. So we all knew how to do it. And we all have the care. We all know,

our

own broadcast skills, because that's what we've been doing. So why not use that. And that was fantastic. Because what we did or what I did was come up, I ended up being lead producer to voluntarily. And that is definitely not a word. I accidentally became the lead producer on that and actually creating the hardware around what we were doing. So we put in some tests about those broadcasters streaming to me, and then from me streaming out to twitch.

That worked

partially, the reason it only worked partially is because some of those streamers were getting heavy traffic traffic shaping from their ISP across the Atlantic or from New Zealand, all from even the UK into my connection. So there was some that would actually not connect to me at all, some that would connect to me from Alaska perfectly. And then the guy from New Zealand, that was just no. So sweet. So we had to sort of figure out what we were going to do with that. So I thought, why not a remote server, so they could all stream to it. I can collect those streams from that server, and then I could stream to twitch. Now, that was all well and good again. Because what we had is we had everyone connecting to a JIRA server. Now that as your server was perfect, absolutely no issues at all. The reason we didn't want it going to me was twofold. One was, I would be bringing in a lot of streams into my personal internet connection which may fail it especially during the time that this Until the ninth of April. So this was, as everyone started working from home in the UK, then outside that everything going into as your is free, everything coming out is not. So I would have multiple streams coming out the best way of doing it. So what we did is we stood up a Windows VM with I think, on the day was a 32. Core VM.

But the total cost

of it was for the actual cop 17 hours was under $50.

Wow, well under. I mean, you're looking at almost $1,000 server a month, but because you're only using it for such a short time. It was cheap in comparison. I'll get onto what we did later on. And that works really well. It was fantastic. There was the conference round start to finish. I sat in my desk chair for 20 hours doing the production will not make that mistake. Again, I wasn't here the whole 20 hours. I did go for food and

bio breaks. But

that's another story. After that,

that conference was a success. We had to modify a little bit. So we had a little problem with the server that you that the broadcaster's was streaming into, we use a protocol called rtmp, which is real time messaging protocol. It wasn't great. The reason it wasn't great is some of the audio was sinking. And this was because we had one rtmp server on the east coast of the US. And we had people connecting from West Coast, East Coast UK, one from the Netherlands, one from New Zealand. And by the time it travels,

you get audio D sync.

So LiveCode has conference too. We had multiple rtmp servers, wherever the speakers were. So we had one East one West coast us, and one UK. Then we used network peering to use the back channels within us Europe. So they were all as your servers in those three regions, and they all use the back the VPN peering. So we were like,

on

the is your backbone, it was absolutely fantastic. And the OBS VM, we changed it from a 32 core 128 gig system like just a compute instance. We changed it to a GPU instance. Now,

believe it or not, the GPU instance was cheaper. Okay?

It was mainly because the the actual amount of memory and the CPU count drops, because you're doing the rendering on the GPU. So you don't need as much. So you keep all the CPU encoding and you keep all the memory for the actual running of it. BS in the running of the conference, where is the encoding before it gets sent out to twitch, and the rendering of the actual rtmp streams that are coming in from the servers, all done by the GPU. And it's a Tesla based GPU type instance. And it's fantastic piece of kit. And it was a great, great change that we made, really was worth it. Because we we saw that instantly, that it would work a lot better. And then the rtmp servers, we didn't go for the open source version, we went for an enterprise version of a media system called ant media. And the reason we went for that is because it's got a built in API. So this is a REST API. And I think you can sort of possibly get to where I'm going with this. We did build a custom bit of software and we're actually improving that so just just bear with me on that point. So we got a media server, we went to the enterprise version because the open source community version has a timer delay of strings of up to 1012 seconds. Whereas the enterprise version, they take out that barrier. And then you can end up with almost no delay. So it'll be like half a second, maybe two seconds, not 10, which can be important, especially how far the stream gets behind because you've got a broadcaster streaming to our servers and then a streaming to twitch, and then that going from twitch to the viewers. So there could be a massive delay. We didn't want the 10 seconds. So we went with this enterprise software. The total cost of the live coders conference to which was like this weekend, and I'm just talking the is your cost $150.

#### Jamie

Well,

#### Andy

it was a it was a 10 hour stream, or no sorry, 11 hour stream because we did an extra little bit and bang included all the tech tests as well beforehand. So this is me spinning up the servers and shutting them down to actually instal them and get them all running. Yeah, less than $150. And I'm going to keep that secret, I'm afraid. Sorry. On how those are all completely set up together. Oh, totally. Yeah. It's the live coders are

in a little bit of a

consultation type stuff right now. It's very interesting. And, like big times ahead. So have you got any questions so far? doing?

#### Jamie

A whole bunch? Yeah, that's, that's amazing that you should keep it under $150. Because like, I've seen and been part of a number of these virtual conferences where it's like, hey, instal zoom, and we'll figure it out after that. And there was a there's one where we did a live episode of tabs and spaces, which is one of the podcasts they do, there was almost entirely done over Google meat. Because I mean, that's it was it was organised by us. One ad that was what they wanted. And that's what we used. And I think that there's a lot of experimentation and noise that's gone into the the live coders conferences that I think a number of conference organisers won't know about. So I know that earlier this year, Dylan Beatty started doing a whole bunch of I think there were daily or weekly lunchtime conferences where he'd have people do talks, and that was all how it but it wasn't thrown together at the last minute, because there was a lot of experimentation and a lot of like, slightly open, slightly closed beta is and you know, join in and download the software and do this and do that. But that was very much a case of almost daily repetition of how do we do this? How do we do this? So my first question must be how in the heck did you know about the the different? The different server instances, I guess, and the different protocols that you could use and, you know, where do you start? With let's say you want to figure out about OBS ninja and you don't know about OBS ninja? How in the heck do you go from? I don't know what it is to, oh, there's this thing that happens, right? Because no one else will have very few of the people will have blog posts that list, hey, if you use this software, or if you're trying to start a virtual conference, you should use this software and this software and all that kind of stuff, right?

#### Andy

Yes. And I think that that is actually a problem. also partially something that has not come around until now. So there are streaming software and software companies out there that do this and provide this as a service. They do software as a service or platform as a service. And they go, okay, you can stream to us. Then they'll stream out to twitch and Facebook or mixer or whichever one it might be. And they are little known that no one knows about

them. It's like no one really knows about the life coders outside of twitch?

Well, apart from people are starting to,

if you know i mean. So

outside our little bubble of Twitch and other streaming platforms, it's not known about people don't realise what it's there for how useful it is and how far the reaches. So you look at something like Ms build,

which was mid May, that went

really well. I absolutely loved it.

They had the two sides three days, it was sort of over three days because of the time zones and everything sort of went on. And they had the same talks three times to go around the world. And then they also had the twitch channel going for 48 hours and they also had another couple of things. And it was just they knew where their market was

#### Jamie

because they actually got Jeff to work on it as well. Alright, interesting. So he actually ran

#### Andy

the twitch channel side of things For those 48 hours with a couple of other

MX guys just and it's one of those things where his knowledge

and also live code has confidence, one that he took to them as well,

because they, they spotted it, they noticed it.

They noticed the numbers. It's like, we only had a couple of sponsors in the first live coders conference. We had people knocking on the door guy,

the sponsor, the next one

is a case of

the question was, how do you get started? And I think the the thing is, you go and see somebody who is already doing it, and they will teach you I have no problem. Getting somebody started with streaming. So I will talk about it until the cows come home as the saying goes, and I will it was it. It's one of those things that I will just keep on going and going. Energizer Bunny stop And I think that's where you will find that, especially with the live coders. We are enthusiastic about it. It's our niche. We want people to do it. We want to educate people, not in just coding, but in doing the live coding in doing streaming, because we know it helps we know it

sort of helps you and other people learn. And

who doesn't want to learn something new every day.

### Sponsor Message

Are you a lead developer? Would you like to bring mobile development in-house?
ARE YOU A DEV provides you and your team with everything needed to prototype, code and support a mobile product in-house.

Deliver your first mobile app and upskill your in-house team within 3 months.

The ARE YOU A DEV program includes 3 hours of bespoke video content tailored to your project, over 18 hours of mobile product video material, weekly live video Q&A and email support with SLA response times for those annoying bugs.

Visit {{< sponsor-link link-text="areyouadev.com" link="https://areyouadev.com" >}} to schedule a 1 to 1 demo of our business team programme.

---

#### Jamie

You mentioned it earlier. And you said, Oh, this the software that we're that we use this enterprise level software has this REST API. And you wrote some software, and was there on it? Was that some kind of function what like, function on like a serverless? Was it C sharp, was it I mean, it's just sending like posting and getting actb right. So it could have been anything but like, what was it without telling us how it worked? Because obvious See, that's that proprietary API like,

#### Andy

okay, so Amelia has got a really nice API to sort of go and get, get streams. It's even got web hooks in there. So it's getting who is streaming to which server, that there's a whole ballgame that I haven't even got into yet on that. So it's got an API and web hooks, where you can tell if somebody's streaming to one of your servers, which how fast their connection is. You can't quite get latency yet. I'm trying to figure out where that API call is, on trying to find out what latency they have. And also the little niggles and little like what encoder they using to push their to push their video to the server. And using that API using a web hook server attached to OBS OBS is Open Broadcaster Software. And OBS is what we use to stream to twitch so there is a Little bit of a plug in format called OBS WebSockets, which basically generates a WebSocket server that pushes information out. So, my dotnet core view app was connecting to this REST API, connecting to web books and connecting to OBS web socket server to give the production team more options, and more automation, compared to the first conference. So this was only ready for buck partially ready for live coders conference two, and hopefully we'll be fully ready by low coders conference three

date to be decided.

mixing all these API's and all these systems in

you think where do you put that

and being as you're nice and easy, just put it in an app service

and go and turn it off when you don't need it. But It's all donek or it's all there's a little bit of signal are in there for the front end communication. So what we were doing, and what the aim is to do is, so we can click the hosts of the conference. And the speakers both have a dashboard that they can look at, know when they are live, know when they're going to be live. So like a countdown, know what their latency is. So when they get the live lights, well, what we're trying to do is we're actually trying to give them the live light when they are actually should be live. So step back a second. Sorry, this is a little bit of a weird explanation. I've been through it so many times on the stream. And there isn't really a good way of describing it without blowing people's minds. When you stream from one machine to another. You have a latency. So from my machine Here to the rtmp server that was a bit noisier, there may be a latency of around about two seconds. And then from that box, there may be another half a second until it gets the broadcast box.

And from there,

you've then got another five second trip into Twitch and back out again. So we forget the five second trip out to twitch and back to the viewer. And we sort of concentrate on the, from me to the rtmp server to the broadcast server. Now, the speaker side when I say change the scene, so I want to go back to the host of the of the conference because my talk is done. I signal the server now that signal takes about what maximum about a quarter of a second to get to the server, but the server should not switch the scenes straight away. Because it's got to wait two seconds for your broadcast to get to the rtmp box, then another second fret to get to the broadcast box. So when you say goodbye By clicking that button, you've actually got to wait three seconds until you can then change the scene, right. And that's what we are trying to build in. So we are trying to build in that latency tracking. So then what we can do is we can change the scene, so the host at the right time, so you're not caught up halfway saying saying goodbye. And you're not caught up halfway through introducing a speaker when you go to that speaker.

But the big trick is,

how do you detect the latency and tell the speaker to start speaking, before he's actually physically live?

Unknown Speaker  
Hmm.

#### Andy

What we're doing is we're also keeping track of the latency of the speaker when they're connected. Now, there's a problem with this sort of solution.

And I'll get down to that in a minute.

But what we're trying to do is we know that what the latency is to the server because we could track that when the the host says and now Over to Jamie for their talk on remote working clicks the button. We know we've got about three seconds until we can actually transfer. Now if the latency is more than three seconds to the speaker, we can just say start speaking now you're going to be live by the time it gets to the server. If it's less than three seconds, then we've got to sort of wait sort of half a second or how however long that transition takes and then tell us so if the host is three seconds lag, and the speaker is only one second, then we have to wait two seconds before telling the speaker that they're alive. So then the transitional takes place in the right time. And Jamie's just gone. What

#### Jamie

No, it totally makes sense. Because I got a I have a family member who works in TV behind the scenes and is in no way the same sort of situation but a similar setup for switching to camera feed number one switching to camera feed number two and those camera feeds may be different buildings are different. Different parts of the same building and, you know, they're the cable in between them may not be the best. So I kind of understand what you mean. Yeah.

#### Andy

All the viewers are going to be commenting going What?

So yeah, that's what we're building. And we're sort of we're trying to improve that and make it a better experience for speakers hosts and production crew all at the same time. Because from that first conference where I sat in a chair for 20 hours, the last conference, I was only there for six

out of the 11. And

the reason for that is because I had another couple of team members doing the switching for me, and we're sort of building on that experience. And I want to automate more. And I think that's just what my attitude is. I love automation, but we're using out of the box, API's and software and customising it and adding our little app on top of everything else. It's very interesting to see what others are providing, and, unfortunately, how much they're providing it for. Because it's not cheap.

#### Jamie

That's an interesting point, though, because you brought up then, you know, we're taking these pre existing, not intentionally German usage, but you're taking these pre existing lumps of functionality effectively glueing them together by providing the goal and then maybe adding another layer on top. Well, that sounds almost awfully like almost every piece of development ever. Yes.

#### Andy

Can't argue with that. I'm afraid can't argue with that.

#### Jamie

I mean, obviously Nish? The specifics are different. But you know, when a client comes to me and says, I want you to interact with these three API's and produce a report, well guess what, I've got these three pieces of functionality. I'm providing the glue and painting over the top of aright

#### Andy

definitely, definitely. You is it's the special people that create their own API's?

#### Jamie

Well, I mean that the point I'm getting at is that, although you're talking about these incredible technical details about we have this very niche problem, we're trying to resolve the latency and being able to switch from one fee to another. And do we need to presumably have some kind of animation or seeing that happens whilst we're switching? Or can we just do it and don't worry about it? And how do we message everyone until they're ready? Taking that part out? Which, admittedly, is the big problem, right? It is, essentially, almost anyone could if they had the background knowledge, look into doing something like this anyway, I'm not saying that it requires. I'm trying not to say that you folks aren't required, but what I'm saying is that you don't need to you wouldn't need to be part of the live coders team to be able to do something like this. Oh, no, no, definitely not.

#### Andy

These aren't open bits of software. These are as I said, off the shelf products. And yes, we are just providing the glue. So if you know The NIJ and you can do it, do it, because it's a lot of fun doing it. It's a lot of fun creating the software.

Well, it's my day job. So,

of course, I'm going to say a developer's job is to develop seems a bit of an odd statement. But I think if we have a sort of get to that point where we are just sort of, I don't know where we're taking it yet, is the point. We're very early days and we don't know what's going to happen once we know what post COVID world looks like. Will a lot of physical conferences, never go physical again? Because I mean, when you look at what same looks after done, and they said, okay, when the MVP summit was June, it was as the lockdown hit the UK and the US, and it was a case of Okay, cancel the MVP summit. Then build King quickly. And then very quickly after that it was we're not doing any physical conferences until at least July 2021. And then you've got Twitter going. You can work remotely, if you want from now on, and it's this whole, we're going to decentralised stuff. And if we get 5000 people going to a conference, but then we can reach 35,000 over a weekend, across the whole world. And we're not losing money on that, because we're not paying for a conference venue. We don't have to pay for advertisers. Oh, yes, you've got the Where are we getting our money from?

#### Jamie

But I don't know what the future looks like on a lot of physical conferences. To be honest. I honestly think it is already a good thing. And it's going to continue to be a good thing, right? Because you're talking about what happens with the future of physical conferences. And I mean, what if you can't physically attend, right? You could say you can maybe sell tickets have a greatly reduced cost. Just make sure you go to this URL and you can watch it. And we'll let you sort of ask questions and stuff and all that kind of thing or, you know, then you're, you've recorded it. So then you can upload it to some kind of video sharing site, maybe YouTube or whatever, after the fact, which is what things like NDC do. I don't want to put words into your mouth. But what I've inferred from what you're saying is, you know, the folks who can attend or what about folks who can't write, we talk about inclusivity we talk about bringing as many people in as possible, but what if there is some actual barrier which stops you may be a physical distance, maybe some kind of disability, maybe some kind of personal circumstance? Well, guess what you can still attend. I'll be a virtually and join in and we'll still take questions from the folks who are joining in virtually and a number of the conferences that I've gone to over the past few years have had chill out rooms specifically for if it's all getting too much go and certainly jaren I don't want to say that you don't need that anymore. But you don't need to worry about those this conference have a chill out room or somewhere I can go if you need to, or some friends have social anxiety, some friends have issues where they can't be around big crowds, if you're sitting in your own space is a space you've crafted that is comfortable for you. And you can still join in. Right,

#### Andy

exactly. And there's the whole cost of going to all these conferences as well. So you can attend more, as we said, at the top of the show, is I'm a Microsoft MVP, and I got that in January. Now I had the chance of going to the MVP summit over at Redmond. And I just couldn't this year, because it was it was very, very early and at the time, I was sort of starting a new contract. I didn't have time to sort of take any time off at all, or to spend X amount to get over there, spend four or five days over there and then come back and still be Partially seen due to jetlag to actually start work again. Then you've got ms bill just after that. And then you've got, he was going to be twitchcon in May in Amsterdam, and then another twitchcon over in September. And what's the one that was in New Orleans Ignite. And it was crazy that you have these five or six conferences over the year that I could have gone to, that I would have had to spend money on, I would have to sort of spend the time to try and sort out family try and sort out what they're doing while I'm off gallivanting around the world. And I know that's not exactly what I'm doing. I'm sort of networking with people. And so spending a few hours in the evening, watching the MPP summit or watching ms build or is nothing. It's included in your internet bill and monthly electricity usage. Thank you. It's fantastic. Let's continue with that. Even if I have to pay just an hour a nominal fee just to get into a room or a subscription on on something, just to like $10 a month.

It's like There you go, you can you can actually attend

this summit or this event and just becomes a little more, as you say, a little bit more accessible and inclusive for everyone.

#### Jamie

They could even be you see, you brought up the idea there of subscriptions, right? Instant thought in my head was it's like Netflix, but for conferences.

#### Andy

Wow. Right. Okay, so when we starting the company that

#### Jamie

hopefully before this episode goes out, right.

#### Andy

I'm gonna I'm gonna gonna go and grab a domain right now.

#### Jamie

Yeah, it makes it so much easier, like you say, and then companies may then be able to afford to send more than one person to a conference. I've worked in close the smaller teams where it's been. If you want to go to a conference and you Want the company to help you with paying for it, you know, you've got your due diligence, and they will pay for you to get there. But then it's your job, your responsibility to basically go to every single talk and be in four different places at once, and produce all of that information. Whereas, if you can take a skeleton staff with maybe 10 people and say, right, you three on a rotating basis can sit in this room and watch this conference and have some time with the people speaking. Why not right,

#### Andy

take it in shifts that you go work. Right. And then when you get the timezone issues? I think there are there are downsides because we've talked about the positives of going, going non physical, but there are downsides like the water cooler sort of talk afterwards. And so the so that that interaction and physical interaction with people and Twitch is a very weird one because it has twitchcon twice a year now, one over in Europe. Wallen in North America. And when you're an online broadcast, I think you need that physical conference to make it different. Because if you just make it an online conference, it just doesn't feel right. I don't know. It doesn't sit well with my mind that they would actually go fully physical and they they haven't. They've gone right when we're not doing the conference, we're just going to cancel these two. They have cancelled September. Now. Let's move on to the next thing. And I think by the time we get round to next year, I think we're going to be in a better place to maybe go to those, I hope.

Because I do want to go I do want to go. Yeah,

#### Jamie

as long as you're supporting a live in person conference with you aren't able to attend Well, here's a greatly reduced ticket price and you can just attend the things that you want. And maybe we'll try and organise something or maybe as a community, you can organise a Hangout or a meet or whatever it is zoom. Whatever takes knology where you can all sit together and there's three or four of you having a chat, right? And with that, you can then create this little cottage industry, I guess of people who are like, hey, I've got this plugin that you can use for your thing to implement some new feature like it's cupcake time, and it shows a GIF of a cupcake or something, you know, it's a silly idea, but you know that the smaller things that can be added to it.

#### Andy

Exactly. And I think we've got a little sidetrack into actually talking about physical and virtual conferences. Right. But I think that's the whole point. It's the light coders when one person at the time was had their physical conference cancelled since then, everyone has and pretty much call for papers are almost non existent for physical conferences right now. Because no one knows when we are allowed to get back to that and actually do anything. So you look at these call for paper sites and they are doing virtually conference after virtual conference after virtual conference, and a lot

of them are held in zoo, and a lot of them are held in other places.

But then where is the reach in that, and I think this is where in in mind turn Nish, you can see where viewers would come from. And with being Twitch, if you are an affiliate or partner, you have to wait 24 hours before broadcasting, broadcasting the content that you've just broadcast on Twitch elsewhere. Now, if you're not an affiliate, like you just literally sign up for a twitch account and go, I'm going to stream to hear you can stream to their mixer, Facebook and YouTube

all at the same time. Oh, and sorry, Twitter as well. So you've got the five

platforms that you can stream your conference to all at the same time and get viewers on all those platforms. It sounds crazy but that is free. Far more reach than trying to point people out a zoom meeting? Definitely, in my eyes. No, it might not, isn't might not be completely true.

But you're going to get

the people that can't get into zoom that don't like zoom because of what they've done in the past, and they've tried to modify themselves, or you can't get people in the Hangouts or you can't get people on the teams live stuff. So on Microsoft Teams, they've got this live broadcast, which is almost anyone can join, but there's no chat for everyone. So it's one of those things where I think you've got to know your platform, and you've got to know your reach. And I think that's where we're in a very interesting nice that we can actually help you there.

And I think that's where I want to be anyway, I want to help people

as much as possible, if you want an online conference yet, so I'm happy to talk to you with no no issues. It's a lot of fun.

#### Jamie

And it's an interesting thing that sort of pop Because one of the people I've been talking to recently, again dating the podcast, I recently have been talking to a lot of games developers from back in the 80s. And the end of the 70s 80s and early 90s. And they're like, yeah, we're all bedroom coders back then. And now it's all gone a bit corporate and I'm like, having this conversation with you. I'm like, without wanting to reduce the iPhone is team but it's a bunch of bedroom coders

Unknown Speaker  
changing the world.

#### Andy

So the live code does have a website. And when you go on to that website, and you see the list of streamers that they have got all sorts of different names. Like there's a there's a game called board bearded builder, or there's C sharp frets or there's me as lucky number Slevin. Everyone has got their the other name that they broadcast under. And when you look at those people And you go, Oh, hang on Microsoft employee. Oh, hang on that. Well, okay. There's a few that don't don't broadcast under a pseudonym like Jeff Blankenburg, who works on Alexa. And then you've got Microsoft, Microsoft, Microsoft. Okay, really good deck game developer. It used to be a Microsoft got myself, you've got like, all these people that are like broadcasting, they are bright people. And sometimes you think, what am I doing? I should not be broadcasting with this law. I really shouldn't. It's like, you've got people messing around with AI, you've got people who use who work or used to work at Stack Overflow, and their minds just make yours just explode. And the brains behind some of these people are amazing. And when you sort of realise who they are, and what they've done, or what they've built in the past, and you just go, alright, I'm going to take a step back from this sorry. No, no I'm out. What is it imposter syndrome is the one isn't it? Yeah, yes, it is very hard to sort of, sort of get your mind around that you do, or could belong in this group. But everyone does everyone for new developer everywhere, as I say, new developer, and that's very, very gaming term. Sorry. So when you are a new developer, you are invited into the fold. There's one that comes to mind who's just got his first major major development job at HubSpot, and it he has been literally learning on string. He's been doing react view, he started at C sharp Python. He's done everything under the sun, just to sort of learn more and more and more over the past sort of year and he Yeah, he's just landed a job at HubSpot.

#### Jamie

I think that's it is that democratisation of sharing that Knowledge, right? I think that's one Uh, I don't have much experience in other industries. But I feel like our industry is very much geared towards that, Hey, want to come and learn? You want to put in the effort, come over here, and I'll show you how this works, or should we both go over there and learn how that works. It's all about sharing everyone's journey is right. It doesn't matter if you're new to the industry, if you've been here for five years, 10 years, 20 years, 30 years, 40 years. It doesn't matter if you work for Pied Piper doesn't matter if you work for hooli. Doesn't matter if you work for Google or Microsoft or anything. Well, he does. But it's not. It doesn't enter into that conversation. Hey, do you want to learn something? Let's go and do this. Right?

#### Andy

Exactly.

#### Jamie

I remember there was a stream, an early stream of one of Jeff Fritz's, where he was saying we're going to be doing this thing and we're going to use a virtual machine. We're going to go on this journey of learning about installing virtual machines or for installing operating system. We're going to choose because he wants to do some Linux stuff, and this was just before to be us one. So we're going to do some Linux. Development, we're going to choose a boon to because it's famous, so there'll be lots of support. And so we're jumped into the chat with, well, why are you choosing this one? Really? You should be using this one because you're a elite hacker and he's like, you're not helping the conversation? No, you want to go and complain about this technology versus that technology go somewhere else. This is where we're learning. We, you know, he himself may have already near may have already known the things that he was doing. But the people who were watching and participating and joining in, maybe not, and that's what's great about the live coding and Twitch and all of this kind of stuff is there is it's allowing that sharing of knowledge, right. Let's come together and let's learn this thing. Definitely.

#### Andy

Yes, exactly. And I think we'll Let's move on.

I don't know where we're going. I pretty much know where we've come from. And that's

three.

In terms of Jeff rez, he started two and a bit years it maybe two and a half. So I think it was a bit about six months in between me and him. Starting. And with that it's a case of please pushed hard. I've pushed hard, we've all pushed hard. And we have seen this thing happen where it's just increased. And the number of developers, the number of people doing this is amazing. I want Matt to continue and grow, where it will be in three years. I don't know, because I don't know where twitch will be in three years. And who does To be honest, but I think it's one of those things where it's been here for 10 years. Let's see where we can push it and see where we can go.

#### Jamie

Sure. It's exciting times, isn't it? It is it is. So you talked about the live coders conference, one in two, and how they were in the very recent past and now is talk of a live code history. I'm not asking you for a date. But is there is that open to the public? Is that someone something that anyone could join? Or is it is there a website? How do you find out about more about that

#### Andy

Three we have nothing we live code is conference two was Saturday the 20th of June. So, as we are recording this two days ago, I had to put in that reference for everyone who is listening. Sure. So that was two days ago we the initial conversation is future.

And I think the answer is yes, there

will be one. That is it right now. With with live coders conference to the call for papers were actually open to public. And we could have done better in actually advertising that and pushing that out there. I mean, we did get 200 submissions nearly, but we could have pushed it out there and got a bit more variety in in the folks that were coming in, which is which I think we're going to sort of push for next time and sort of do more back office stuff than the front office stuff because the friendly stuff seemed to work and seems to be working so We just sort of need to get that back end organisation a little bit. A little bit better. It's always constant improvement as you know sprints and

agile methodologies and all of us always improve and improve and improve and

we push things forward.

#### Jamie

So let's say I want to go and learn more about it. Are the previous conferences uploaded anywhere is it just go to twitch slash live coder or the live

#### Andy

coders have a YouTube and it's under the live coders, you can actually use the search bar and search for that one. We will be putting the live code has conference to up over the next week or so. Depends when I get the time to cut it up and actually upload it. And I just downloaded the actual conference and it was something like 128 gig, which is a nice file. And the good thing is I've got plenty of room in this machine to open it up in Premiere and slice,

Unknown Speaker  
slice it all up.

#### Andy

It's better Be a fun time. And yes, it will be on the YouTube channel. The first line of code is conferences up there. Bar two talks. We had an issue during the first conference where

I forgot to hit record ha,

for the first speaker. And then one of the other speakers, one of the twitch servers went down and we got disconnected, which meant we actually lost half of their talk. Unfortunately, we lost two talks out of them. And we've never got back to re recording or getting a recording of the

#### Jamie

of the streamers of those ones. But no, all 16 talks from this weekend will be up. And you know, that was a lot of fun. And so because of the very nature of podcasts with what I call a pod machine Tynecastle wibbly, wobbly this. We're actually discussing this in the past. So hopefully, as long as Andy's had the chance to answer they get the work done. Those will already be uploaded, I presume, by the time this comes out.

#### Andy

As Dr. Who put it to me why me stuff?

Yes, they will be up there. And we may even know when conference three is out.

So if you are listening

at that point,

it's comp dot live coders dot Dev,

#### Jamie

I'll make sure to put that link in in the shownotes for that, at the very least. So if you're listening in, click through and you can read the full transcript and the link to the live coders conference website. Okay, so we'll talk about socials and things in a moment. But I do know you see a little bit of inside baseball talk, we do have a planning document every time that we do one of these episodes. And you've got a list of small projects or these projects that you've done in in Twitch, as I've called are these just projects that you're really excited to talk about.

#### Andy

know these, these these couple of little mini projects are the stuff that I sort of get up to on stream. So I recently bought a new heart rate sensor because I'm a keen sight And I haven't done much over the past few years because of kids and moving house and jobs and all this other sorts of stuff in between. And I want to get back out on the bikes and do a little bit more cycling again. So I bought myself a new heart rate sensor. And it wasn't just for cycling. I actually got the Bluetooth and amps which are two protocols version, and I'm using Bluetooth to connect it to my PC to display my heart rate on my stream. Oh, so it literally has because it's Bluetooth LE which is low energy. It displays my heart rate on stream and over. It also displays a graph of what it was over the past minute or two, I think. So it just plots the lines as it goes. So you can see when I'm getting stressed at coding or things are going wrong, and it just goes I've already had one called comment on it and said, while your heart rates low while you're resting, okay, so during my stream, at that point, it was around about 70. But I know somebody who that their heart rate is definitely not 70 when they're resting, it was a bit higher than they should

have been. And it is

like, you actually can't be down because I just kept watching your heart rate. I was like,

Unknown Speaker  
fair enough.

#### Andy

And then the other thing is, I do things like little chat overlays. So Twitch, twitch has its own built in chat, and I put that onto my own stream. And we can you can have a little bit of fun with emotes so emotes are also in twitch chat. And you can put those on screen and make them like burst like fireworks and do all little tweaks and little things like that. And it's a lot of fun just to play around with what you can do in JavaScript, because these are all browser source based overlays. So as long as you can do JavaScript, then that's fine. And I believe I haven't tested this yet. You may be able to do something with blazer.

#### Jamie

Oh, Exciting,

#### Andy

which is maybe a next thing to do, and maybe do that hook a blazer and signal laughing together and see how that works.

#### Jamie

Because why not? Right. This is this is what's great about all this thing. Just have fun and play with it. Right? Yeah, it's just like,

#### Andy

I know we'll do today. Oh, well, hook blazer

and signal are into a browser source Overlay and do something fun with that.

#### Jamie

Yeah. You mentioned earlier on about the live code a rite of passage, you said, you know, the first thing you want to do is write something super chat and then like a chat bot, and then you can set up a system and then you're you're off to the races. Is that something that you'd you'd recommend people do? Or is it more just a case of Hey, just spin up a thing? start broadcasting and just write some code?

#### Andy

Yeah, exactly. That, yes. Do that. Now the answer is,

do what makes you makes you feel comfortable to start, and then start going out of your comfort comfort zone. Because when things start going wrong, Or things start not working, you then become stressed and then you become a not so great broadcaster, you slip back into a developer mode. I'm going to say this is one of those things. You've got to be slightly extroverts and ever so slightly narcissistic. It's a strange moment. And people have come to me and gone. I'm not a narcissist. It's like you're broadcasting to which you're putting yourself out there. And it's all about you. It's this much narcissism. It is only a very tiny amount, but there's definitely

some in there. And they go, Oh, actually, yes,

I agree with you. So this is why I said it wasn't for everyone is because you have got to put yourself out there. And if you do have anxiety about that, and you've and you fancy Getting out. I will be there to support you because you may not feel comfortable doing it. But you hopefully. And you usually do in the in the tech side of things, is you get the good viewers coming in and saying, Oh, it's your, if you've got first streaming your title, they'll come in and say hi, how you doing? What are you up to what you're building? And they'll ask you questions. They won't barrage you and you will get somebody coming in and go, hang on a minute, slow down. This is your first stream. I've been doing it for three years. Take a step back and collect your thoughts. I will keep trapped at bay, as it were. And that's the whole point of the twitch tech community. And science and tech sort of section is we are inclusive automatically. And we do we do look at when we look after our own as it were is our family. And it's one of those things that that is definitely a twitch thing. In some aspects, excellent.

#### Jamie

So we've we talked about the lifeguard as group. Definitely check that website out. So you can learn who is in the list. Do you have the URL to hand out your religious list in the in the show

#### Andy

notes? It is live coders dot dev is easy to remember.

#### Jamie

Right? Okay, so what about catching up with you then learning more about like when you go live and all the projects you're working on, what's the best way to do that?

#### Andy

Okay, so on Twitter, I am the Sullivan but that is spelt. The es

seven EV i en I couldn't get the L unfortunately.

And my Twitch is

lucky. No

as in no and Slevin again but with the seven instead of the L and that is s seven e vi n and that is where you will find me most of the time. I do have a couple of sites and that's 11th heaven.com. And that is Slevin with an owl this time. Sorry, folks, too many ELLs and sevens everywhere. And one of my main projects, which is the project I built for Twitch is called featured chat, and that is featured dots chat. And this is something that I built for twitch for twitchcon last year in 2019, where you can feature a chat message from twitch chat on your stream. It's expanded a little bit since then to include things like q&a gathering, and include tweets for some broadcasters. So you can actually feed your tweets on stream.

Yeah, it and then we want you to build this and I was like,

okay, so I built it and they went, right, we need you again, to come back

and

flesh it out. So I did.

#### Jamie

What I'll do is I'll make sure to put all of those links into the show notes. They won't be the show notes that appear on your pod catcher. So there'll be a link in there to the transcript page, click through that. And then they'll be listed there just to make it a little easier that way. You know, if people are driving and listening, they're not diving over their car to get a pen and write it all down. Although if you're listening to a podcast by your phone, presumably through your car, while you're grabbing a paper and pen, I don't know. But there you go.

#### Andy

Yeah, probably probably not a good idea.

#### Jamie

No, exactly. Excellent. Thank you ever so much, Andy, for spending some of your evening. Because it has been wonderful to chat with you learn so much more about the live coders stuff. If I do ever get round to restarting the live coding that I've done, maybe take some of your advice and use my desktop machine which is orders of magnitude more powerful than any of the laptops I've got laying around. But that's the whole point, right? You don't need all of that power. You can just just get something and start going right. You don't need that. thousands of pounds worth of equipment.

#### Andy

There's always options. Yeah, I think that that's another thing. Sorry to interrupt and go back on this. There's always an option to get started is not about hardware. It's not about money. It's pick up something and go and see if it works.

#### Jamie

Excellent. Well, like I said, anything Thank you ever so much. We'll have to check in in a little while see how maybe live coders conference seven or something goes?

#### Andy

No, no live coders conference, Slevin? Oh, yes.

#### Jamie

Excellent. Well, like I said, thank you so much for spending some time with me. And thank you.

#### Andy

Thank you very much right by now.

{{< paracentre "The above is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

### Wrapping Up

That was my interview with Andy Morrell about how to use an Azure VM to facilitate a globally distributed live conference. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/), and there will be a link directly to them in your podcatcher.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice - head over to [dotnetcore.show/subscribe](/subscribe) for ways to do that - and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Andy on Twitter](https://twitter.com/s7evinth)
- [Andy on Twitch](https://www.twitch.tv/slevinthheaven)
- [Slevinth Heaven](https://slevinthheaven.com/)
- [Live Coders](https://livecoders.dev/)
- [Live Coders Conference](https://atndesign.github.io/Live-coders-conference/)
