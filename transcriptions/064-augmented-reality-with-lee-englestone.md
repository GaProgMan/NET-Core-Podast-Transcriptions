### Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is Episode 64: Augmented Reality With Lee Englestone. In this episode I spoke with Lee about just what Augmented Reality is, how it's different from virtual reality, and how you can start leveraging Xamarin and .NET in order to create AR based apps today.

So lets sit back, open up a terminal, type in `.NET new podcast` and let the show begin.

{{< paracentre "The following is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

#### Jamie

So thank you ever so much for taking some time out of your evening, Lee, I know that we're all incredibly busy these days, even with, you know, the incident, I don't like to name it. But you know, with what's going on at the moment, everybody's really busy. So I really appreciate you taking some time out to sit and talk with me today.

#### Lee

No problem. Thanks for having me.

#### Jamie

You're very welcome. You're very welcome. And so I thought, first of all, could you maybe give us a brief description of like, I hate saying this, but like, who you are and the work that you do, just for the people who are tuning in and may not have heard of you? Or some of the work or some of the talks that you've done?

#### Lee

Yeah, absolutely. I so my name is Lee Englestone, I am the software development manager at Leasing.com. My day job nine to five is predominantly web based working on the website Leasing.com. But recently, I've been spending quite a bit of time exploring augmented reality, and specifically been able to do it using .NET, and C#. And I'm just finding it a really, really useful and really, really fun. But a little bit difficult because I don't feel there's much in the way out there for C# and .NET developers unless you want to be developing for the HoloLens. So what I'm trying to do is sort of share the knowledge that I've gained learning this stuff so that other .NET developers can can play around with this stuff as well.

#### Jamie

Sure, okay. So, a couple of things to unpack there. Before I ask you what augmented reality is, does this mean then that there will be an augmented reality version of the company website at some point, or? Yeah, I just like to ask silly questions like that.

#### Lee

I'm afraid No, I think my experiments with augmented reality is, is just that; experiments at the moment. That's not to say that I, we couldn't leverage it to use it in various industries. And the automotive industry that I work in, has already seen some augmented reality innovations. So when you start combining both the automated automotive market and the sort of retail market and e commerce, yeah, maybe there are some things that could we could do there, but nothing planned or in pipelines just yet.

#### Jamie

Okay, that's, that's fair enough. That's fair enough. So I guess, could you give us a brief description of what augmented reality is because taking a you know, two steps back and say, putting my hands up and saying, I know, next to nothing about it, I'm thinking Minority Report, right, you know, that whole gloves thing, or is using the computer just by waving his hands in the air? And thinking Xbox Kinect, you did mention HoloLens earlier on, is it? Is it that kind of thing is what's what's the deal here? And is it different to virtual reality? And if so, what's the difference?

#### Lee

Sure, I'll try my very best to explain some of those terms ok so when I'm talking about augmented reality, what I tend to mean is the ability to make something appear in the real world around you, that isn't actually there. And that is different from virtual reality. Because in virtual reality, you put a headset on and your whole vision is occluded, you can't see anything, the only things you can see is created by a program that's running. Whereas augmented reality, there's still a program running, and it's still inserting things into the real world around you, but you can still see the real world around you. So that's, that's sort of the differences, how I would describe augmented reality and virtual reality. So to answer your question, as to if we're getting a bit closer to the Minority Report, I'd say yes and no. So yes, I think that we're starting to build user interfaces that have got a higher degree of freedom. So almost, if you put a headset on, you can build a virtual world or virtual interface. The same with augmented reality, that's, you've got 360 degrees freedom, which is very liberating, because we've, up until recently, fairly recently, we've been very restricted with our 2d interfaces, with our little tiny black screens, and slightly bigger laptops and desktop screens. But this is one of the reasons I really do like, playing around with augmented reality just, it feels like a very, very creative way of making things appear. And you start second guessing how you can build interfaces, you've not just got Oh, everything could just be a one distance away from you, or everything could just be in your immediate line of sight, you can start placing things to the side of you to the above you in front of other things. And so I'm definitely enjoying that aspect of it. So Minority Report.. I think we're getting closer.

Maybe without the creepy conspiracy sort of stuff that is.

#### Jamie

on in it. That's fair enough. I do remember. It's definitely not augmented reality, but I do remember when, like the, you know, the Oculus and all of those people. No headset started coming out, I thought a bit off. That's amazing. I no longer I'm limited to a, you know, anywhere between 15 and 30 inch screen, I can throw these headsets on and have my windows all around me, you know, or I can just have one massive not screen but one massive area just for my code, you know, literally look up and down the code pitch in your my head to look around which would with that, I feel like that would be a good use of my time.

#### Lee

It is exactly the sort of thing that I do like to investigate experimenting with. It does feel like virtual reality has had a bit of a hard time of the years, it's sort of been up and down the sort of hype roller coaster being the next biggest thing like 10 years ago. People then dismissing it, say no, it's not really delivered. But then as you say, fairly recently, the most recent virtual reality headsets are very, very good. And I've never played beat Sabre, but I really want to play that that looks like a lot of fun.

#### Jamie

Oh, my goodness, I do remember. So my brother and I do a video game related podcast, we just sort of talk with our friends about video game things. And near to where I live, there's one of those, you can pay some money and go in and play all of the arcade games. And on one of the upper levels, I think there's like two or three levels. On the upper level, they do have beat Sabre. And you know, he put the headset on, put the headphones on, put the gloves on. And you know you he was literally jumping around the room to get around stuff of waving his under and that was loads of fun to watch. And I have a feeling it was loads of fun to play, but it's definitely enough for me.

#### Lee

I would get one in a heartbeat. I just need to convince my wife that it's for sort of exercise purposes or something like that I think.

#### Jamie

that's it, you just show a beat Sabre etc only but you're doing all of your moves. you're exercising every part of your body. Yeah, that could totally work. Right. Excellent. Okay. So we talked about augmented reality and how it's this sort of thing that we're moving towards. So if I, if I, as I wrote before we talk about as a developer, like I say, I'm completely new to augmented reality as a user of it. Do I need anything specific? like do I you said, then, you know, with virtual reality, you tend to put some headsets on but a headset on and carry on? I do remember a number of years ago, there was a project called Google Glass. Is that similar to augmented reality? Is it a case of I just have an app and I sort of look around and it captures the camera and draw some things on it once? Because the actual as a user was the

#### Lee

Sure, there's different ways that we can experience augmented reality, I think, yeah, Google did experiment a bit with Google Glass a few years ago, it didn't unfortunately, take off. And one of the main reasons was privacy concerns, I think, because you could basically record people and they wouldn't know about it. And we're always going to run into these sort of moral problems. And we're going to run into them in future, I'm sure. But I think what's a lot of people are doing now is, is taking advantage of our mobile phones that we carry all around with us all the time, which makes sense, because these are very powerful devices, you just gotta look at the processing speed that these things have. They're, they're incredible. And they've got an increasingly increasing number of sophisticated cameras on as well with the depth perception and all sorts. So it does make sense to first be able to wave our phones around and see things that are there via augmented reality. And I'm seeing a number of industries taking advantage of this. One of the biggest ones was Pokemon Go, if you remember about five years ago, which was released, and you could, you could run or you could walk around, and you could try and find Pokemon and train them. I didn't actually play it myself. But it looks like a lot of fun. But I believe in you could trade them and stuff like that and find gyms to get your Pokemon to work out. And it was one of the things that really made me sit up and think, Wow, this this augmented reality, it's, it's it's going to be big, because it proved to me that people are willing to wave their phones around and make things appear there that aren't actually there. They quite enjoy it as well. So I don't know if you know, but pokemon go in the last five years has made $3 billion. That's, it's not a small sum. Yes, that's billion with a B. So this is not all about entertainment, you do get a lot of games develop. Which makes sense because there's a lot of fun that there's one where you can make the floor look like lava, which is great for kids because they they do that in their imagination anyway. But so when it comes to big businesses, they want to know how they can make money out of it and how they can sell their products with it. So I'm starting to see more manufacturers and retail outlets showing how they're different products could appear in your home and that's everything from a food mixer or a fridge freezer,to try on a watch on your wrist or Or a Burberry handbag? Or even trainers and clothes? You know, we can we can, there's some apps now that let you see how they look on you. So it feels like the businesses are starting to understand that there's a lot of money to be made using augmented reality that people want to use augmented reality. And everyone's already carrying these devices around, they're fully capable of delivering these augmented reality experiences. So it's up to sort of developers like us to be building experiences to make for these businesses.

#### Jamie

Sure, okay. I mean, that makes a lot of sense. The idea, remember, at an old, an ex employer of mine, they had a project that we they were building for a series of, for a company that built houses. And the idea was, you go on their website, you know, you say, I want to buy a house, and you go through this step of Yeah, what four bedrooms or five bedrooms or whatever. And then part of that by buying the house as it would be partially furnished, and decorated and stuff. And so the project that the folks that I was working with, I didn't get to work on the project, but the project that they were working on, was, you would walk around this house inside the web browser, and you would go up, don't like that, put that covered in or don't like that wallpaper, swap it out for that. And it feels like that's kind of augmented reality ish. Like, he's, it's not exactly that, because you're not actually walking around in the room and swapping things out. But you know, it's being presented to you on the screen.

#### Lee

Yeah, I think anything, which sort of helps you out of imagination is a good use case for this sort of thing. I mean, IKEA, they do an AR thing where you can go through their catalogue and see what the various chairs look like in your living room. And I think when the big players are starting to do this, then the small and medium enterprise businesses starts doing as well or the startup start doing it. And it feels like we are just on the on the cusp of a really big tidal wave of augmented reality experiences. They've been predominantly made for the devices of today, there's a dozens and dozens of manufacturers that are all racing to become first to market to create augmented reality glasses. And they might still, the processing of these glasses might still happen on our phones, you know, that might be doing the the hard work. But certainly, if we can get there, and we don't have to wave our phones around anymore, we can just require glasses, then I think that is going to make even more people interested in this technology.

#### Jamie

Excellent. I do feel like it's sort of come on leaps and bounds in, say, the last 10 years or so. So when I was at university 2004 to 2008. In around 2006, I had this graphics and reality class. And the lecturer was saying so what Well, guys, we've got the pipe cards with these up patterns on it. And they were about the size of maybe a coaster or a beer mat, and you would hold the the plaque on under the camera. And they'd written they had written some software that recognise the pattern and display the 3d model on screen, you know, they would show you that, and like that was 2006. And now we're at a point where you can do that without having to have the little pattern right, you could just you could just like go, there's a 3d model, throw it somewhere on screen, and have it wander around. I know that friend of mine was showing me before, before the incident, right? A friend of mine was showing me his phone and he was using I think Snapchat and you can create this little 3d character. And you just literally put your phone to the floor and he's really character walks up on screen and interacts with things that are on screen like so he pointed at his table like, and he's you know, the length of his table, his character character walked, I'm not looking dunked into it and fell over and I'm like, just the sheer amount of CPU power to do that must be amazing. And then the fact that you could do it on a device in your hand. And like I said, my my other experiences 2006 where we're holding a pieces of God with patterns. It's leaps and bounds, you know? Yeah, it's certainly come a long way from what would have been specially software probably written during Junior University is to, to what's now probably that second example is probably just built upon frameworks, where a developer can readily readily pick this sort of framework up and just start making experiences with it, which is what I tend to be doing these days, I'm not writing complex mathematics or doing anything too complex. I'm just using out of the box, augmented reality, stuff that you can do using the Apple's AR kit framework. It's very much like when people ask me about what it's like to be a programmer, you know, when they say what's it like doing web dev for console dev or whatever they say, you know, the majority of the time you're playing with Lego You've got the prefabricated bits, and you sticking them together and see what happens, right? You're writing the glue that holds them together and you're reading, excuse me, you're writing code that helps to transform data from one place to another. But for the majority of the time for them, like 99% of your average cases for, say, web dev, it's for this library in pulling ESP .NET core, that gives you all of the stuff required to actually receive and send receive requests and responses, it's then your job to do the business logic. Well, guess what? You're going to use JSON, you're pulling in something to do something with JSON, you're going to talk to a database, you call something in to talk to database, and then you just sort of glueing those layers together. Yeah, so

#### Lee

Good example, would definitely say that in our line of work, where we're sort of standing on the shoulders of giants, all those brilliant people that have come before us and all those brilliant people that came before them.  Most definitely.

#### Jamie

most definitely. So I guess, is that the case with you were saying then, you know, you do this kind of thing with, with your augmented reality experimentations. And your work with that? Is that very much the case is it just the lens of frameworks, and do the little bit I'm doing the bungee cord stuff, people are listening, the the the glue bit that sort of glues it all together, you're you're just basically doing that, I don't want to sort of reduce what you're what you're doing. But

#### Lee

yeah, that's, that's fine. So I can only talk really about ARKit, Apple's Augmented Reality framework, which I've experimented quite a lot with, there is so much built in stuff in that, that you really don't have to do much much of the complicated stuff yourself. So in there, you've got things like image detection. So if it detects an image in a scene, it will fire an event, and then maybe you can place something else in the scene near that detected image. And then when you move that image, anything you placed around it will also move. And you can do face tracking so that if it detects a face in a scene, it could it tracks its movements, and you think maybe why would you want to do that? Well, if you there's a I think it's Specsavers, or there's a business that we can try and different glasses frames. So you've got to be able to track the face to do that. So there's that. And then you've got plane detection that's built in as well. So it could detect surfaces like floors or walls, because they're going to serve as our boundaries because we want our experiences to sort of be the same in real world and you don't want to be in the real world to kind of go through a wall, can you walk through the floor. So we want to place things in a scene, we wanted to hit these boundaries. So that's just three out of the box, you've got, you know, face detection, image detection, facial tracking, but there's a whole bunch more, I think there's body detection as well, that, you know, I'm not writing any complex code for to be able to identify face, or to identify a surface or to our image, any image processing stuff. It's all built in. All I'm doing is just building upon that to make some cool experiences for want of a better word.

#### Jamie

Excellent. Okay. So obviously, I'm a .NET dev read, do I if I want to do .NET things and augmented reality things? Do I need to go out and get some very specific software and hardware or? I mean, you were saying that you're using Apple AR kit, right? So obviously, I can't leverage that on a Windows machine or an Android device, right?

#### Lee

Yes, I'll try to explain a bit. So the way I came about it was I wanted to do some, some general some basic development for iOS devices. So I went out and got a Mac. But then I got distracted, distracted by Apple's AR kit stuff with all this augmented reality stuff looks good, but I need to go off and learn swift and Xcode.. and then I realised or found out that Xamarin had converted the AR kit or ported it to .NET. So that I could write C# and .NET code, call this AR kit framework and deploy to my iPhone through Visual Studio for Mac which is very Visual Studios, very familiar environment for me, all without touching Xcode too much or, or using Swift, or Objective C. So then it became very easy for me to say I already got it an iPhone, already had a Mac that you fought, you still need a Mac on the network, or to do the compilation.

Which is great, because I didn't want to learn Swift, Objective C, I'll be perfectly honest with you. So being able to make or create augmented reality experiences using C# and .NET just suits me down to the ground in the comfort of my very familiar Visual Studio. And that's what I'm really trying to tell other developers, .NET developers about because last time I checked there were there are a heck of a lot of .NET developers. So if you look at the last StackOverflow survey, and there's a factors More .NET developers than there are swift developers, except swift developers have got all this fun playing with augmented reality for a while now. Now I want to tell .NET developers how they can write C# code and target the iPhone and create these experiences using tools and languages that they're familiar with.

#### Jamie

Okay, excellent. Sounds good to me. So I can use Xamarin and I guess to be able to pull that in. So I guess, I don't know whether you'll have much experience with it. Because you were saying, you know, you mentioned iOS a few times. But if I want to make something, there's augmented reality that's both Android and iOS. Obviously, I can't use I'm guessing I can't use Apple's AR kit bindings for Xamarin. But maybe there's something else for Android? Is that how it works?

#### Lee

So the answer is no, you won't be able to use AR kit to target Android, but Android have developed their own sort of augmented reality framework called AR Core. And unfortunately, I've not got much experience with that so I can't go into too much detail. However, one of the the benefits of using Xamarin is that if you write your code in a sort of cross platform way, and use dependency injection in in the right way, I believe you could, you could work out if the devices if your app is being deployed to are built for iOS device or an Android device, and then perhaps load the appropriate augmented reality framework, AR Kit, AR core, the codes probably going to be different. I imagine these are two different frameworks. But you could in theory, possibly target both and have a bit of code reuse, but they are still different augmented reality frameworks.

#### Jamie

Okay, that makes sense. So like you have, so from, from my perspective, I'm going to have in my solution, I'm going to have maybe an iOS specific project, and an Android specific project and maybe like a shared or a core project that has all my business logic II things. And then perhaps, if I'm on iOS, I'm going to use Did you say was AR kit for apple? So that will be included in the iOS project. And when my iOS project is running on Apple, it will be using AR kit. And then in the Android one and the Android project, it will be pulling in AR core. And then when it's running on an Android device, we'll be using that because it's because you're only pulling the one library and then like you said, dependency, injecting it into the correct one. You don't really have to worry about it so much, I guess, I think so it's

#### Lee

Not something I've tried. But I do remember a code sample where someone asked exactly the same question, can I write? Can I create a project that I can create augmented reality, a similar augmented reality experience on both my Android device and my iOS device? And I'm pretty sure they did something quite clever with with dependency injection, depending on what the device was that was being built are targeted.

#### Jamie

Okay, that makes sense. So then, can I use the augmented reality things inside of unity as well? Because I'm thinking, if there is, let me talk you through my process or my thought processes. So essentially, if there are Xamarin, slash dotnet, bindings for AR kit, and there is Xamarin, slash .NET bindings for AR core, then is there something similar for unity?

#### Lee

So I've not used unity that much all the augmented reality stuff in it, I believe, they deliver augmented reality experiences for using something called AR Foundation, which I believe and someone can correct me if I'm wrong. So apologies if I am wrong, and I believe it's just an abstraction over AR kit and AR core. So they have built another just a layer on top of those other frameworks, I think..

#### Jamie

okay, that's fair enough. I mean, if you the way they're that I like to run these is, if you're not sure, then yeah, someone can point out that maybe this is a bit a bit lacking, you know, the, the way that I always the way I was approached is if I don't know that, I'm going to go look it up. So if somebody you know, and the reason I'm asking you these questions is because I don't know whether you know these things, I'd like to know you. Absolutely. Yeah. Okay. So, okay, so let's so we've talked a little bit about some of the things that AR kit can do via the augmented reality bindings for Xamarin. And I'm guessing you can do like you said, if you wanted to, you can learn swift and AR kit at the same time, except that it becomes difficult to manage, right, ie, the weather I've always told people is learn one thing first and then learn another because if you're if you're getting errors with swift if you've missed let's say you go and build something else. Language, you don't have any experience with using a framework you don't have any experience with first time you get an error, you don't know whether it's the language, the framework, the tooling, you know, all of these things, right? So it makes sense that you can sort of wrap all this up and and put it inside of a .NET experience, right?

#### Lee

Yeah, absolutely. I think when I first started trying to learn how to call, various functionality, in our case, from from a C# project, I ran into a small problem that not many people are doing that. So there weren't that actually many code samples, or tutorials online, there were one or two, but not many. So then what I had to do is very easily be able to find the equivalent in Swift or Objective C. So most of my time is trying to work out what they were trying to do in that sample, and then convert it into C#, and this is one of the things I'm trying to do. I've got a website that points given or speak about later, why I'm collating all the samples that have almost translated into C# so that the next developer after me who wants to do the same thing in C# doesn't have to translate it from swift or Objective C like I have. And someone said to me, Well, why don't you just write it natively in Swift and Objective C? And my only answer is, well, because I don't want to, and I know C#, I know .NET. And someone went through a lot of trouble to actually port it from from into Xamarin, did a went through a lot of efforts to port it into a way that it can be called from .NET. So I don't see any reason why I shouldn't be calling it from .NET or C#. Not that I've got anything against swift or Objective C at all.

#### Jamie

Oh, no, of course, you know, we're, I'm certainly not trying to promote that there is something either better or wrong or worse with one language over another. Yeah, it's just the you know, the point that was made so far. And that is if you know, one language or one framework, and you can do a task by leveraging some kind of port or whatever of a different language or framework, then you do that way, because you already know how to use you use the tools that you know how to use, right, yeah, rather than, let's learn this, like, let's say, a customer client, project manager says, I need you to build me this thing, right? You're going to go and build this thing in the tools and frameworks that you know how to use because you know, that you can be productive and effective in those tools and frameworks. Yeah, you know, being paid to learn how to use a brand new set of tools or frameworks, right?

#### Lee

That's the way I see it. I think. The people that have learned swift and Objective C and been doing iOS development for a while they've had all the fun doing this augmented reality stuff. It's, I just want to show C# developers and .NET developers that they can create these the same augmented reality experiences with with technologies they know.

#### Jamie

Exactly right. And that's the whole point of having these ports and abstraction layers is that you can then take that wonderfulness that somebody else has created, and use it elsewhere. And that's what's great about it.

#### Lee

Yeah, absolutely. And you know, arkit wasn't isn't the only app or framework that's been ported by some that can be targeted by C# and dotnet. Developers, I think the Apple's core ml framework might have been ported as well. And that's their machine learning framework. So you could easily target that as a .NET developer. And I think there's some other frameworks that that have been ported as well, but my mind's gone blank a bit. So it's not just the AR kit that's been ported this, there's quite a few of the frameworks.

#### Jamie

So we've talked a little bit about how you can use Xamarin, and how we believe for the time of recording that you can use unity. And you mentioned HoloLens earlier. And now, I feel like this is going to be at least the leading question, right? We talked about how to use the technology already know. I feel like the answer is going to be because it's the hardware I already have. But why iPhone have a HoloLens? Just like it's a leading question, right?

#### Lee

Yeah, there is going to be a few reasons why you would choose either one of them. I think access to the devices themselves is one thing I mean, we tend to carry either an Android or iPhone around with us. Again, they're not cheap, but the general consumables that people tend to have the the HoloLens, I think the HoloLens 2 comes in at around three and a half grand now three and a half thousand pounds. could be wrong, but I did check that fairly recently. And that's quite a lot of money for me to spend to experiment with. There's definitely use cases for the HoloLens, the certain industries that are put it to very good use, and the can afford obviously to buy the hardware and equip the staff and workforce with them. I think I've seen it used quite well in in the medical industry where Can I think procedures have been performed using the HoloLens actual surgeries I've seen I think the the MOD or the military in America, they use it, they're experimenting it as well as a bit of a like a heads up display for giving them a bit more information on the battlefield perhaps. And I know that there's been police constabularies in England that have in their headquarters, they what they like to have is great big TV screens showing the status of maybe crimes in certain areas, when they have the HoloLens on think and have absolutely huge screens, rather than that would be restricted for the wise, you know, you can't have a 200 inch screen, you know, at hand. But if you use the HoloLens you can, you can have as many of these as you want to project information on. So there's certainly use cases for them. I believe, if you want to target the HoloLens device, you have to use the Microsoft mixed reality toolkit which is not something I've played around with mainly because I don't have a HoloLens. If Microsoft want to send me a HoloLens to play around with, I can provide the my address, I'll be happy to sort of do some samples of that and try that out. But until then, I'm going to stick with creating augmented reality experiences for device that carry around with me.

#### Jamie

Okay, excellent. And you talked to earlier on, is one of the sort of double backbones within them just for the fun of it. Now, you talked a little earlier on about how you're putting together a website, have all of the samples that you've for one of a better phrase translated from, you know, here is how this is how you would do it in Swift. Or rather, you could do this thing in Swift. And let's see how to do in C# Yep. dotnet, or, I suppose F sharp? I'm not sure. That's going to be a question in a minute while I remember. So one of the things that I really like about that is that the way that I got started doing blogging and things like that was my ultimate self, I've got this, I've got this problem, and I can't figure out how to solve it, I need this library or need this function or this thing, solve the problem, write down how I did it, turn into a blog post, because three weeks later, when I am literally a different person, we talk about this all the time, right? You're writing code for another person, the other person may be literally another person, or maybe you tomorrow, right? You come against you come up against the same problem. Oh, there's that website. On the website. There it is. Right. So I for one, really like that idea.

#### Lee

I think.. I'm a firm believer in that one of the best ways of learning something is to teach it. And by that I mean, you need to be able to understand it, get a grasp of something well enough to be able to explain it to other people. And you probably gonna learn around the subject as well, so that you can talk about it with with others with some authority, because you're gonna have to field questions back. And that's exactly what I've done really is just in the website, and I'll talk about it later, is really simple, basic things. That's because I started out really basic, simple, like, how do I just get it a blank app deployed to the device? There's actually a few gotchas and a few hurdles you have to overcome, you have to give the camera permissions, you know, this, this and that. It sounds silly. But that's the like, the first lesson on my website is how do you? How do you deploy a blank app, mobile app to your phone? And then the next one is how, how does the coordinate system work? You know, x, y, z. And the next one is, okay, well, how do I place a basic cube? Just just a basic cube in the scene? How do I make it red? How do I make it blue? Okay, how do I make multiple cubes? How do I make a sphere? How do I make it rotate, and then going back to your Lego blocks analogy, one Lego block by itself isn't particularly interesting. But if you start combining them together, and each different Lego block have different functionalities, as you know, there's just to start to start being able to quickly build up interesting experiences. So I can put a cube in a scene. Pretty boring by itself, I could create a wall of blocks in a scene, I can turn on physics within blocks. And then I can shoot a fake sphere with with mass and force at that wall and see all knocked down. And that's just using some blocks built in physics into the scene and a sphere. Pretty basic stuff. But yeah, that's the kind of thing that I'm trying to have fun. I've had a lot of fun learning this stuff. And I'm trying to teach you by in the same way by by encouraging people to try different things.

#### Jamie

Sure, yeah, sure. I do like that because like you say, you got a box that's not exciting. Couple of boxes, a little bit more exciting. You know, you build up to her it. Yep, same with it. All of us. Let's learn to code right? We don't start with you know nothing about writing code and then you now have a website or some ecommerce platform, you start at hello world, then you start up loops and if statements and then you move up to method calls, and then you move up to API's, and then you move up to being able to do things like maybe in a functional manner, or then you maybe look at extensions and classes and may or maybe you go for functions and learn what a mon ad is, right? You slowly build up that knowledge. You don't just go, I'm gonna make the game. So I'll start with nothing. And then two days later, I have a 3d dribble a table.

#### Lee

Yeah, absolutely. It is just learning the basics, building up bit by bit by bit.

#### Jamie

Sure. Okay. So then so the question I wanted to come back to is, we talked a lot specifically about C#. And now I don't know whether you have much experience with F sharp, but do you know whether you can do the same augmented reality things with F# or like, like I say, your experience may be limited to C#. But can you also, do you know whether you can also do with F sharp?

#### Lee

So the quick answer is I don't know if you can, but I'm optimistic in that these VB .NET, C# and F#, combine down to the same MSL intermediate language. So I don't see why you couldn't. I've got a feeling, you probably can. But I've not tried it. So I can't say yes or no.

#### Jamie

Fair enough. All we'll do is we'll leave that as an exercise to the listener to find out whether they can build something in F sharp, then they can build something, then they get both let us know and tell us how they did it. Right. Excellent. Okay. So let's just have a look at this. Okay, so you've talked a lot about how you're making all of these, these augmented reality experiences, these demos, these products, I do want to quickly throw in something about. So this I want to say about May last year, April, May time last year, I actually went to Japan on a vacation. And we went to a place called canal city, which is a shopping centre and hotel. It's weird. But a multi level Shopping Centre in the middle of a city called Fukuoka. It's called canal city, because there's a literal canal that runs through it. Whilst we were there, they had a number of experiences that I want to say augmented reality, but they had nothing to do with the phone. So we were there for the Pac Man 25th, I think 25th or 30th anniversary. And one of the things they did was they chose one of the walls or projected a game of Pac Man or Pac Man sorry, Space Invaders onto the wall. And the whether it was working is you have to clip on to the music to make the this that the logical at the player or whatever, shoot the Space Invaders, you know, someone else was controlling left and right. And you all had to clap as a as a group to make it shoot, which I don't know whether it was more of a gimmick, you know, someone was actually pushing issue but not but or whether it was actually all filmed, I don't know. But it was loads of fun. And the other one was, there was a quite It was quite literally called New Godzilla Shin Godzilla. This was a new movie that was coming out a few weeks after we went home. And they had the thing there as well. It was like Godzilla is attacking. And you have to get this when you needed your phone, you have to get your phone out and go to this URL, or push a file button on your phone. And it will fire a rocket from roughly where you were in relation to the screen app God does. So if you were on the top deck looking down, it would fire roughly from like the top road downwards. I don't know how they word it, maybe just GPS or something or elevation. But that's kind of my experience of augmented reality. They are certainly

#### Lee

..Becoming mainstream aren't they and more prevalent. And I think they do a really good job of, of getting you engaged and getting getting noticed. And one of the best things it is used for is by marketing. You know, because all of a sudden, we're talking about Pac Man, and we're talking about Godzilla, when would we normally be talking about that? One of the ones I've seen a really good is I think in a bus stop on one of the sides of the bus is actually a TV screen. But there's a camera on the other side. And 99% of the time you can it looks like you can see through and it looks like glass. And then it might have like aliens attacking on the other side. And you'd see people like looking around the bus stop to see if it's really happening. It looks like it looks like this aliens on Oxford road or some street in London.

#### Jamie

That's wonderful. I really want to see that out in the world now. Because I can imagine that just like you just go about your day you know nothing about augmented reality. Boss goes by it's got a window in it. You can see aliens attacking past genius. I love that But yeah, so I guess what you talked about how you've done some of your demos and sort of experiments and things like that. What are some of your favourite ones that you've built? So far, like, give us an example of some of the things that you've done that you really sort of proud of and excited about?

#### Lee

Sure, I did one that I fairly simple one, but it looks quite advanced, I assure you, it's not. And that was showing that the sort of periodic table in in augmented reality that you could then walk around and it had all the names and symbols of the periodic table, and you click click on them on the screen, of course, and it would animate them appear to animate them in the real world. And I could do more with that I could maybe show the element or I could show the atoms in element, or I could show a bit more information about when it was discovered and stuff like that. But that I think that's quite a nice use case for education. Because it's been proven that children engage a lot more with education, if if the subject they're learning is taught to them in an engaging way. You know, when I was at school, we just had textbooks, I think, a few years after that, they start giving kids iPads. And they're now My, my, my six year old girl, seven after this weekend, is given her work because of the incident, as you say, to do do a homework online, on on on websites. So and it works just learning a timetable. She's learning to read, not from textbooks, not from teachers, but from deeds, different experiences that people have built. And I think augmented reality is a play a big part to play in teaching for education.

That's what I did, trying to think of some others have done. I think that's probably my favourite one. The for education reasons. There's other industries I want to experience experiment with, I want to do one in the automotive industry, I've seen a good example of that, which is probably a bit beyond my skills at the moment is that you can get a Tesla to appear on your driveway, and then you can you can customise the colour and trim and, and various aspects of it, that would be a good one to play around with. Yeah, there's, there's, there's all sorts of things I want to do, I'm going to just get started with it.

#### Jamie

Sure, sure. I do remember, this was this is going back a few years. So in 2015, I was working on a project, there was a car ecommerce site, but for sort of used vehicles. And they they had this system where the sales people would have to use the they use the term iPad, but it could be any any branded tablet. And they had to make a video of going around the car hitting very specific points at very specific time. So it was like a minute and a half. And they had to sort of walk up to the car from the driver's side and sort of stick the camera into the interior of the car, look at the steering wheel, come back and then walk around to the back and open the boot and go in. Because it was almost like an OG, they were trying to do augmented reality without doing augmented reality. So you can watch the video and see what the car is like. But I could imagine doing like a walking tour around a car. With your phone, right, just like there isn't a car there, be holding your phone up and you walk around and you go Alright, yeah, so that's what, that's what the steering wheel looks like. And that's how big it would be if I were to hold it, you could maybe put your hand out to try and hold it to give you an idea. And you know, this is how big how much space there is in the back for little ones off shopping or things and this is how big the boot feels this is what it feels like to this is what it would the experience is like to open it obviously not feeling like butter, open the the boot, the the whatever it is with I don't know what the the international term for the storage space at the back of the car. You know, that kind of thing, just sort of walking around and getting an idea of what it looks like and, and the sort of space it takes. And rather than just like make what appear on my drive and change the colour.

#### Lee

I think the experience that you talked about there, I think I've seen videos of them people developing some similar things. I've definitely seen a virtual reality one where you can put a headset on and you can almost sit in the car. I imagine you probably sit in the chair. But but it looks would then look like what it would if you're behind the steering wheel. And you can look around into the backseat passenger vehicle. But yeah, I think that's actually been developed by someone. I've just remembered another experience that I'm quite fond of that developed. So another one that I quite like is calling photography an API. And that is and then surround myself in a photo sphere, what I call a Photo Sphere anyway, and it's it's about, I don't know 50 images all pointed towards the centre where I am in the middle of this sphere. And I can look around at them and I quite enjoyed that and that was one of the first experiences that I made and it was again Very simple. And then I thought, well, where can I take this, and this is where your imagination is really important. If you've not got very good imagination, it's probably not the best technology for you to learn. Conversely, if you've got a good imagination, you really limit unlimited what you can do with this sort of stuff. So something that I've been playing around with is getting the talking to the Twitter API, and placing tweets in augmented reality space. And then you can think, Well, why can you take that you could call a number of social media API's and maybe combine Instagram, Facebook, Twitter, I don't know what the cool kids use these days, Snapchat. tik tok, I think is the coolest one these days that are not on there. and place them in some sort of timeline. They say, Okay, this, this tweet happened, and this Facebook post happened. And then this Snapchat happened. And then just being able to, again, not having to jump between them on a 2d screen, you can just look around and see what's going on in your sort of combined social media world that's that's maybe just having them fade out after the 30 seconds on and then fade a new one in that's just happened using sort of real time communication using signal our or something like that. And that's another experience that I'm really fond, really keen to develop.

#### Jamie

Sure. And then perhaps you can maybe reach out and touch one of these status objects. And they can maybe go read, okay, this is the one tweet by, you know, by Lee, you press it, or you tap it on your phone, or whatever it is that you do some user interface interaction, and he can maybe show you a thread or go. Okay, so let's show you this. And the most recent tweets around it that Lee had said, or maybe I could do some sentiment analysis, figure out what it is you were talking about, and search for other related things, right? Totally limitless?

#### Lee

Absolutely. It is, once his imagination starts playing around, it was just that it's going it just takes off the way I want to take that next is getting voice control. I don't know how to do voice control on Xamarin iOS devices. I'm not sure how possible it is. But I do know how to do it in dotnet. So I could have a .NET console application running somewhere that's got microphone and I could say show photos of cheese, I don't know. And then it would show cheese or show show me search twitter for I don't know WWDC or, and then it would just filter the tweets. So starting combining different technologies, I guess, is what I'm saying. You don't have to just use augmented reality. They're using speech recognition, using signal on real time communication. When you start combining all these separate technologies, you do start making some amazing things.

#### Jamie

Sure. I do like that. I like the see my mind problem is that I end up with the almost two overactive imagination I get up like, why would it be awesome to do this? And then this and then this, and then I come up with a huge list of things to do and never do it. It

#### Lee

Yeah, it's about baby steps. Really? Hear it? You know, small iterations?

#### Jamie

Yeah, sure. Okay. So I've read that you're, you're also in the process of putting together a book as well. Is that?

#### Lee

That's right. Yes. So I was thinking, Well, I'm very keen on on letting the .NET. And C# developers know that they can create these experiences over there in the website that I'm putting together, how else can I tell people? And it's things I talk to yourself on these sort of things. It's, it's talking to user groups. And then I thought, Gosh, I wonder if I could write a book about it. Because there's been other books written by how to create augmented reality experiences using swift and Objective C? Why can't I write one in C# and .NET. So I just contacted a publisher, I think A Press in this case, filled out a quick form, had a bit of an idea together. And then lo and behold, they seem quite interested in the project. So I'm just at the moment, I'm just churning out chapters, and just submitting them. And one day, there might be a book at the end of it. There certainly is an agreement there, but some of these things don't always these things don't always end well. But I'm very optimistic, you know, the technology moving on before the books completed. But yeah, I really hope it doesn't like that.

#### Jamie

So due to what I call the podcast, pod, cast time, machine, wibbly wobbliness. We record these a little bit in advance. So to give inside baseball, this is sort of the middle of July, and when we're recording, and my current schedule means that at the moment, this episode may not drop until November. So what I can do is if you'd like I can get back in contact with you around about the time it drops and say, Hey, is there any more information on this? And if there is, we could put it into the show notes. If there's not, then I can say, Well, you know, like, maybe there's a mailing list or some way to register interest or something like that. Maybe we can maybe we can drive people towards that. Because it's something I would be interested in for sure. Because like I said, I'm going into this conversation, I had no no idea what augmented reality is. And now I've got loads of ideas, everything in my head. So, you know, maybe we can drive people towards that. So is that going to be like you said, is that just going to be? What is he just going to be? I don't mean to just put the in bernicourt? Is it? So it's .NET augmented realities? amarin. That kind of thing?

#### Lee

Yeah, that's it's it's, I think the book is, the draft title is something like augmented reality for .NET developers using C# .NET and Xamarin.

#### Jamie

Fantastic. Okay. So we'll, I'll try and make the listeners we need to do is get the listeners to do some googling on that and try and find that out and see if there's some kind of register your interest page and get loads of people to be interested. And then, you know, a press will definitely take you up on in. Let's see what happens. Right. Excellent. Okay. So what are some of the places that you would recommend people go to to learn a bit more about augmented reality that I know that you said earlier on, there's when you started at least there weren't that many places to go and find it? So is this like, obviously your your your website, you're putting together the maybe the talks you're doing was was was the best place? To put words any method?

#### Lee

Sure, i'd say Apple, if you search for Apple augmented reality, their augmented reality section is quite good. I guess from the the basic principles, it talks about their framework AR kit, and it's a good starting point. And then you can start downloading samples and deploying them onto your phone. That's quite good phone as well. Because if you have got Xcode, I think installed on your on your Mac, you can just download these, the the their examples, and they're pretty good to go. Really, you just compile them, deploy them to your phone, and all of a sudden, you're tracking your face? Quite good, especially to get your imagination going like like you're saying,

#### Jamie

sure. Okay. So you mentioned earlier on about the website that you're putting together, does this exist yet? Or is it still sort of in a state of flux now.

#### Lee

It does, and I'm constantly adding information to it. So XamarinArkit.com. So kind of the title is the clues in the title, combining them two technologies Xamarin and AR kit, and there's, I call them lessons. But that's a very loose definition of the word. It's merely my understanding of the concept, some code of the things I've tried, that you can copy and paste and try yourself. And then sometimes most of the time, if you do have the effect as well, whether whether it's a basic sphere, or if it's this periodic table that's floating the code samples on there for as well.

#### Jamie

Sure, excellent. Okay, so we'll make sure to where people go towards that. So if you are listening, so what I say to the listeners is, when you download the episode, in your pod catcher, which is the app that you use to listen to the episode, there'll be a link to the full version of the show notes. Otherwise, it will take very long for the, the showrunners to download, because there'll be a transcription and a bunch of links. So press through to those for those full show notes. And you'll see a bunch of links towards the bottom of all things that we is talking about. So then you don't have to, what I'm saying is, if you're driving anywhere, don't be diving across the dashboard to get a pen and paper to write down a website, because I've written it all down for you. Excellent. Okay. So those, the those the places you recommend to go to, to learn more, is there. So there's Xamarin AR kit, and the apple documentation, that's where you'd start. I guess that's where it starts.

#### Lee

 I think it's not the best starting point, if you're, if you're an Android sort of person, you might want to start looking for the Android side of things. I think if you're interested in unity, or you already know a bit of unity, just google around unity and augmented reality, and I'm sure they've got quite a few tutorials as well to show you.

#### Jamie

Sure. Okay. So you said on the website, there are these sort of, you know, in your words, the lessons that you can sort of grab hold of and try out. Are there you said that there are code snippets, but I do have any sort of open source, hey, here's a full project, you can grab a download and try out yourself.

#### Lee

Not yet. However, as part of the book project, what I'm trying to do is create a single codebase that's got all of the examples in it. So you can run each at a time, almost like a companion app to the book. So you can say, Okay, you've got this one app, you can deploy to your phone. Let's try face tracking. Let's try image detection. Let's try plane plane detection. So I'm not quite work tonight. Yes, yeah. But okay, that's kind of in the works. Sure.

#### Jamie

That's, that's fair enough. That's fair enough. So what about ways that listeners can sort of catch up with you see where you're doing what you're working on? Is there? A you active? I know that we sort of connected on LinkedIn. But are you active on Twitter? Or is it just check out the website? Or what's the deal? How do I find out more about you?

#### Lee

Yeah, well, I certainly try to be active. I'm fairly easy to find on Twitter. And on the web, there's not many Lee Englestone, there is another Lee Englestone and he's a racecar driver. That's not me. I'm the other guy is not a racecar driver. So I'm on Twitter, just @LeeEnglestone. And on YouTube at the same way I post my videos. My blog is at www.Manchesterdeveloper.com. And I'm going to probably try and start doing some Twitch streams as well, but never tried. I've never done a live streaming, but I'm gonna give it a go and see how I do.

#### Jamie

Sure, as someone who did for a while and then stopped for a while, because the podcasts get in the way go away. It is a very fun experience, especially if you can get some people sort of helping out in chat, I hear these people asking questions, or they'll say, hey, you missed the semicolon, or I have you tried this method, or whatever it is, really, it's a wonderful collaborative learning experience. Even if you already know everything you're gonna do is this great way of sort of, like you said, to reinforce that learning experience of teaching someone else, you know, in a previous career, I was actually a teacher. And one of the things that I would do at the end of each lesson, you've got 10 minutes. Do you have 10 minutes, get all the things you need? I want you to each do a presentation for 30 seconds on what you've learned today, is forcing them to sort of reiterate it right. And that's a great idea is teaching What else?

#### Lee

Yeah, that sounds like a really good idea. I'm still getting my head around Live streaming this this thing's like rates where where people, just a bunch of people just come to your live stream. And it's it's a raid? Yeah. I need to read up about these things. But it's something I'm keen to do.

#### Jamie

Sure, I would recommend. There's a previous guest at the time of recording the episode isn't out yet. But there's a previous guest for the show called Andy. morale. I believe that's how you pronounce it Andy morale. He's part of the live coders team that Jeff Fritz and Microsoft are sort of put together. And he has recently been helping out put together a conference for live coders if you can, maybe have a chat with him about you know, how, what kind of things do I need to know to get started, but essentially, when I did it, I used an external microphone and the camera built into my laptop. And I was just a way the problem then is you've got window management, right? You're trying to share their screen, but everything's happening over there. And but it's, from my limited experience, there's loads of fun, and you don't really need to do that much. Most of the heavy lifting is done for you. So that's pretty good arts good.

#### Lee

If it's another avenue that I can sort of tell .NET developers about this stuff, then it's definitely one I want to try.

#### Jamie

Oh, excellent. Yeah, definitely. And you can do, you can do a thing where you can capture the screen of your phone as well, I believe. So I can maybe go, Hey, send. So I'm literally compiling it now. And guess what? Push your button and your phone screen appears on screen. And here I am. Playing with it and moving around and pushing the button. I don't know. It's, it's loads of fun to do.

#### Lee

Sure. I'll let you know when, when if that goes live.

#### Jamie

Excellent. Well watch this place. Excellent. Well, what I'd like to say is, thank you ever so much for joining me this evening to talk about augmented reality, because like I said, I going in, I had no idea. I'm thinking all Minority Report, you got to use this special gloves, but apparently not. So that's good.

#### Lee

That's fine. The last thing I'll probably say on the subject, if that's ok, is that augmented reality is coming. It's it's here in many regards. And more and more of as software developers are going to be developing augmented reality experiences and user interfaces for for these companies that wants to take advantage of it. So I'd probably start getting on your radar if you can, if not now then sometime soon. It'll be a good skill to have in the next few years, I think.

#### Jamie

 Sure. Okay. So what you're saying is, we should all run out and buy your book, right?

#### Lee

When it's out. Absolutely. Yeah.

#### Jamie

Excellent. Excellent. Well, yeah, like I said, Lee, thank you ever so much. It's been really educational for me, and I'm sure it will fill the listeners. Thank you.

#### Lee

Thanks for having me.

{{< paracentre "The above is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

### Wrapping Up

That was my interview with Lee Englestone about Augmented Reality. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/), and there will be a link directly to them in your podcatcher.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice - head over to [dotnetcore.show/subscribe](/subscribe) for ways to do that - and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Lee on Twitter](https://twitter.com/leeenglestone)
- [Manchester Developer](http://www.manchesterdeveloper.com/) (Lee's Blog)
- [Lee on YouTube](https://www.youtube.com/user/LeeEnglestone/videos)
- [Visual Studio Tips](https://visualstudiotips.co.uk/)
- [Xamarin Arkit](https://xamarinarkit.com/)
- [Code Review Checklist](https://codereviewchecklist.com/)
