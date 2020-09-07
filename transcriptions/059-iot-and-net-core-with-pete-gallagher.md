### Sponsor Message

Are you a lead developer? Would you like to bring mobile development in-house?
ARE YOU A DEV provides you and your team with everything needed to prototype, code and support a mobile product in-house.

Deliver your first mobile app and upskill your in-house team within 3 months.

The ARE YOU A DEV program includes 3 hours of bespoke video content tailored to your project, over 18 hours of mobile product video material, weekly live video Q&A and email support with SLA response times for those annoying bugs.

Visit {{< sponsor-link link-text="areyouadev.com" link="https://areyouadev.com" >}} to schedule a 1 to 1 demo of our business team programme.

---

### Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is Episode 59 Iot and .NET Core With Pete Gallagher. In this episode I spoke with Pete about his adventures in IoT (both with and without .NET). We talked about IoT cows, kettles, washing machines, stamp dispensers, and even [Astro Pi](https://www.raspberrypi.org/education/programmes/astro-pi/). This was a wonderful episode to record, and I really hope that it'll be as much fun to listen to as it was to make.

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

{{< paracentre "The following is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

#### Jamie

So the first thing I'd like to say is thank you ever so much for spending part of your Friday evening talking IoT, because, you know, everybody wants their Friday evenings for chilling out. And you decided to spend a little time talking to me about IoT and dotnet core. So, thank you ever so much for that.

#### Pete

No worries at all. Always happy to talk about IoT.

#### Jamie

Excellent. Um, so for the listeners who may not know so much about you, I was wondering, could you give us a bit of a brief overview of some of the stuff that you do? And I mean, the people who are listening now know that you do do a lot of IoT. But is that all that you do is is Pete just the IoT man and nothing else, you're not a 2D character. Common on, tell us all about you.

#### Pete

I'm a freelance software engineer. I've been doing it for years and years and years now. Before that, I was working for a company that made change machines and kiosks and vending machines and stuff like that. So it was embedded software. So it's always been embedded software right? been interested in that.

And then I was made redundant from there and started out on my own and I still consult for that same company in a different guise now but I also do anything else that people will pay me to do, you know, almost as far as dancing in the rain. if they'll pay me to do it, I'm happy to do that. But in all seriousness, I work for free companies that do the change machine stuff all the way through to to WordPress websites for for little guys who make paintballs and stuff like that. So

it's quite a broad list of things that that I'll do for money.

#### Jamie

So quite literally the whole stack right from the silicone right out to the screen. I like it.

#### Pete

Yeah, yeah, I am that unicorn with all horns only. I'm not covering rainbows. I'm just covered in everybody's work.

#### Jamie

I have been told that the true unicorn in development is a different With design knowledge, I don't know how true that is. We're friend James is one of those. He's come from the design background. And he loves to refer to the work that we do as pretend programming. Because essentially, right, it's not really programming.

#### Pete

Unless you don't see us all day, then you're not doing anything hard.

#### Jamie

I agree with you completely. I agree completely. Okay. So I've seen that you you've run like 12 billion user groups. What's that? How to get into that, and how many groups do you run? And can you give us a brief overview of the groups?

#### Pete

I think it worked out that I've run like 8% of Nottingham's, or at least I'm involved in has not boast 8% of Nottingham's meetup groups, but there's a whole heap of meetup groups in Nottingham some really awesome meetup groups there. So I'm lucky to be involved in that I've run and not so T is my It's a group so that's the only one I've run all on my own and don't get any help for but I do get help from us the sponsorship. Rebel helped me with that Misha Bell rebel specifically is invaluable and I couldn't do it without her so they're fired for that but I was so co organised dotnet knots and knots workshop and then hearing loss bro. I'm on the board of another group called Lottie. So yeah, I like to keep yourself busy speaking to people.

#### Jamie

That's really cool. What's really interesting in that aspect is that you know, a few of a few of us actually went down to the two most recent hack 20 fours now that's really old news, right? Because they haven't been able to do them for a while. But they take place in Nottingham as well and we so they want a whole bunch of prizes or the last one. I think it was 2018

#### Pete

awesome. Yes under an MC see with a

We used to run those. I'm hoping they're gonna bring that back. But I never actually managed to make it to it because my youngest daughter, it was her birthday that same weekend. And this always that same weekend every year. So.

#### Jamie

Right. Yeah, a little bit.

#### Pete

Yeah. So sadly, I never made it to that. But maybe when they bring it back at a different date, and I'll be able to go,

#### Jamie

there'll be other hackathons that you can win out,

#### Pete

right? Well, yeah, I mean, that one in Lincoln. Lincoln hack is fantastic. And I've done that a couple of times now. And I want my first other Lincoln hack, which we'll talk about, I guess in a bit.

#### Jamie

Yeah. I had I had found that we were the first year we went to hack hack 24. And that the guys that I went with, keep telling me you're not better at all. We stayed up for literally the whole 24 hours, heads down at the terminal. Each one of us built separate part of this pipeline, and we went from nothing to an enterprise level app in 24 hours, and a bloke who When he had written a spreadsheet

#### Pete

Are you kidding me Really?

Well, that's not his fault for winning. That's his fault for being chosen to win by judging.

#### Jamie

Be more effective with his time.

#### Pete

Well, yeah, true. Although, you know, it just depends on what he managed to make that spreadsheet do. Of course, if he managed to make that spreadsheet, do something pretty cool, then he probably deserved to win to spend that much time in Excel.

#### Jamie

Now, yeah, absolutely. This was measuring employee sentiment via commit messages. So really, yes. Okay. Very, very clever guy. I like it. Yeah. Yeah. Yeah, we did when we had a, we had a system that used get hooks, and you would commit and type something really horrible into your commit message. And it would go through the Azure cognitive services, assign it a score, show on a dashboard and all that kind of stuff. Yeah, we didn't win because it was way too over engineered.

#### Pete

The whole point of a hack there is.

#### Jamie

What else are you gonna do with the other 12 hours? Well, yeah, that's true. But then the the next time we would, we went and we won with one of the apps was just an HTML page with, you know, map and some some pointers on it, because it was more a case of what the app could do rather than what it did. So actually still tell the judge is that right?

#### Pete

No, no, no, absolutely. I don't think we can take it back. So good.

#### Jamie

Good, good. Good. So yeah, let's, let's talk about because you're, you're recently an MVP as well. So congratulations on that. Thank you and Pluralsight author as well. So again, congratulations on now that's a very, very exclusive club. Both of us are very exclusive pubs to get into. So congratulations for both of us. And you write a whole bunch?

#### Pete

Oh, yeah. Yeah. I mean, I mainly do that. So I don't forget, because my memory is really bad. And so if I don't write it down within, you know, moments, it's just gone. So I figure, you know, I can help somebody else at the same time, and has a bonus. But

#### Jamie

yeah, I do something similar in that. As soon as I figure out some problem that's taken a few hours, is I'll try and read it in a generic way. Just post it somewhere on the internet, if it's a get, like a markdown file and get or a blog post or something. Because invariably, two weeks time when I am a different person, I'm going to need to solve that same problem again, right?

#### Pete

Yeah, yeah, I have solved my own past me has helped me with a problem when I've, and I've forgotten everything written in that particular blog post that I've typed in and it's coming physically, the answer is, ah, ah, now I remember.

#### Jamie

It's, he's genius when that happens. So, like IoT, it's a huge field. Right, it's embedded systems that are connected to the network. Oh, well, yeah,

#### Pete

yeah, that's the broadest term. I mean, Wikipedia have got very similar, you know, since devices that can talk to each other in the cloud is the way that I'm going that way. Anything from you know, wearables and nest and Philips Hue and all of those sorts of things, but I like the cool stuff. I like connected cows and and stuff like that, which is really fun stuff.

#### Jamie

Yeah, yeah. Yeah. So

#### Pete

the, one of the things I talked about, in one of our talks is this particular topic and we managed to, to figure out that instead of sitting watching cows to find out when they're on, eat when they're ready to to have new cows made and then normally they just have to sit there and watch them when the cows are more active when the heat so they strapped a wearable to the cow and the measured steps basically a pedometer

#### Jamie

a cow

#### Pete

And then they fed all that information up through machine learning algorithms and, and instead of like guessing when it counts on heat and getting it right about 50% of the time, they get it right about 80 90% of the time and and don't have to sit and watch and go to bed, sitting watching cows because they're going heat at night as well, which is the last thing you want if you're a farmer, as you've probably been out all day farming. And the last thing you want to do is sit around watching cows all night. It's not good for you. So

#### Jamie

I did laugh, because I had this thought of a cow wearing a Fitbit. But the idea just there is this problem, and we can solve it. So why never solve it? I love it.

#### Pete

Yeah, yeah, it was that cool about it is that they because they can pinpoint the time when the cow is in heat and the optimum time them using the data to figure out when the best time to artificially inseminated is because they don't put a ball in the field anymore with the cow. They got some To fit methods, but they realised that if they inseminate either side of this perfect time, you can pick and choose whether you get a boy or a girl cow.

Unknown Speaker  
It's

#### Pete

just, it's probabilities. But the probabilities would say if it was earlier, it would be, I think, a boy. And if it was later, it would be a girl. So if you're running low on anyone, you can just pick and choose when suddenly

#### Jamie

it's pretty cool. You see I left but that is really, really cool.

#### Pete

The power of big data? Yeah,

#### Jamie

yeah. Doesn't it to to have a boy or a girl cow? That's Yeah, yeah, that's mad. We've talked about Raspberry Pi, and dotnet core in the past on this show. But you've been working not just with raspberry pi, but with like, bare breadboards. And you said earlier and you've worked in embedded systems and stuff. So I was wondering, can you talk through some of the projects that you've you've done in the past, give us an idea of some of the stuff that you've you've built in brief Yes,

#### Pete

well projects, previous versions of me. And yeah, well, I mentioned earlier I worked for a company that made change machines. And so that was all embedded. microcontrollers, microchip, embedded microcontrollers, actually. And all of that was written in assembler as well. So my background really in programming other than the Zed expectrum. Before that was writing assembly. And it wasn't until I found VB six and stuff like that, that I got back into high level stuff. But one of the first projects that I took over I didn't begin the project that I took over from the guy that I've replaced was an internet connected Royal Mail stamp vending machine, which is a bit long title. But we had a fleet of these stamped vending machines out in the wild and these were just normal stamp vending machines apart from that they had a modem inside them, and we could dial into them and pick up all the audit trail. event logs and, and that sort of information. But I mean, you're talking about late 90s here. So this is really before there was a proper internet, it was around, obviously. But this is before traditional IoT anyway. And so I was I was a really cool project to try to cram because of quite a small memory limited processes, these are trying to be able to cram all of that operating system essentially into a tiny little processor and get that to work was it was interesting to be part of that. And then obviously, we did many other things. After that were involved in the card vendors that used to get when you just get to hospital, there was a company called patient line that that used to make cards, dispense cards for the bedside TVs. And they were similar. They had modems inside them, and you could dial in and grab the stats and stuff like that. So, yeah, and which kind of I mean, that's why I like the Lower level stuff I like the fun stuff rather than sort of just the easy stuff but is so good but I that makes me mess around with stuff like Arduino as well, which I like you mentioned as an alternative to raspberry pi, which is a full on computer. I like the Arduino for the lower level gets me closer to the to the metal and makes me feel a bit more at home I guess in some ways.

#### Jamie

I do remember back at college when I was about 1617 they gave us these pic chips p IC pictures.

#### Pete

That's the exact ones. Yep, there

#### Jamie

you go. Right. And they said, Look, here's the thing, make a thing and I was like, What do you mean? And they were like, right, make it pretend that it's a washing machine. I'm like, this thing's the size of a credit card. This can't be a washing machine. What are you talking about? I know I have a well okay, we'll talk about Roseburg, Oregon but I have a Raspberry Pi first size of a credit card that sits on my TV with hundreds of gigabytes of movies attached Do it on a USB drive and I just that movie, that movie that I'm gonna play is there other sitting in the kitchen ready to be wired up again because I dismantle it. That is what it's fixed. It's going to be a almost like a jukebox in the kitchen. Okay small app that I've written for my phone. As long as I'm on the home network, I can say, okay, play that song, and it will start playing in the kitchen, which is like it. Yeah, just silly little things. I'm sort of playing around with that. I haven't written any of the software for it. I've written the app, but I haven't written any software for it. That's pretty package.

#### Pete

Yeah. Well, I mean, for the most part, we're using other people's code for half our lives to help me. That's what Stack Overflow was invented for.

#### Jamie

I do remember around that same time when I was a college, one of my lecturers, it said, The thing to remember about programming is it's like Lego, you get all of these pre coupled bits and just glue them together. And this was like, back in 2002. So he's very prophetic is what I'm getting

#### Pete

at Yeah, well, are we, um builders for just copying and pasting the bits in? It's good. I was surprised. I thought you were gonna say you're going to use it as a pie hole actually, because it seems to be taking off again now people are a little bit worried about certainly works for the IoT space as well. People are worried about plugging in Alexa's and all of their smart fridges and crazy stuff like that into the home network. Because Yeah, I think there was a scare. Not even a scare, but people were buying internet connected kettles of all things. And they were coming with Bitcoin mining Bitcoin miners built into the system, the farriers company built in somehow so yeah, it's funny Never mind. Obviously, the other problems with internet connect to CCTV cameras and stuff are scary, but

#### Jamie

he reminded me there are two IoT stories and that was one was the internet connected kettle, but I think it took the guy 47 hours to get it to actually boil because there were problems getting connected to his network. And then once he was The networking needs to sync it with his phone. And he ended up having to call the manufacturer and say, Look, it's not working. They sent him a bug fix on a USB. And it was just, it was amazing. And the other one was there was an internet connected washing machine. But it had a, an FTP server on it. There was exposed out to the manufacturer. But because it was an FTP server, it could like it could use n map to figure out what else was on your network. And they could jump into your network through the FTP server.

#### Pete

And learn Yeah,

#### Jamie

I do have I do have a piehole setup so

#### Pete

good Anya, the other one the other one of those on the on the kettle idea, Ember, make an IoT mug. And there's there's people posting that you buy the mug, and then you've got to accept the terms and conditions and then you've got to do a firmware update before you can drink your coffee. I mean, just buy a normal mug For heaven's sake. What is it, apparently so that you can keep Your mug at exactly the right temperature for coffee. And I think I'm not a massive coffee drinker.

But yeah, maybe maybe if you have internet connected beer glass that would keep my beer exactly the right temperature.

But I've got to firstly I'm not I don't think I'd sit there wait for it to not know if it's anything like your Xbox

#### Jamie

thing right? Let's see you get an internet connected Cal. You still have to go to the castle. Take it to the tap and fill it up. Put it back up on the cradle walk into the other room and then switch it out. How are

#### Pete

we laugh though, but the first IoT device was a toaster, funnily enough, and the guy's name now, but he created it. I think a year

after

Tim Bowers, Tim berners Lee created the internet but the year before the first public facing website appeared so I am He actually predates the web, which is just crazy to think of that. So he'd wired it up so that you'd still have to put the toast in and put it down but it would turn the power on to the toaster through a rudimentary Internet Protocol. And then the next year his boss dared him to actually make it go down and he did it. But you know, he's kind of spoiled it by that point, and everybody was bored. But

#### Jamie

Toki Tosa from Red Dwarf right.

#### Pete

Yeah, that's exactly it. Yeah, absolutely. Yeah. Like a bagel

#### Jamie

mean loads of fun talking to me. It was a tiny Enigma machine that you worked on as well.

#### Pete

Yeah, that was that was loads of fun. And that came out of we watched a TV programme with my eldest daughter about encryption and specifically about how easy it is just to do letter substitution cyphers Stuff like that. And not long after that we all went down to Bletchley Park and other wander around there and our island. My eldest, she was all five, maybe when we did that, and she was a nightmare while we're down there, to be honest, but when when we came back, we were talking about how easy it is to send secret messages. And she was really excited about that. And she had not been writing long, of course, at that point, but she knew the alphabet. So I'd read the alphabet out and then just mixed the characters up underneath. For him then drew wrote out a message and showed how to make that into a real message and back into encrypted message. And she was fascinated with that. And it wasn't around that same sort of time that I was playing with the micro bit as well, which is fantastic. Little board BBC made board which is sort of aimed at kids and young adults to try and get into STEM subjects similar sort of idea to the Raspberry Pi, but it's a microcontroller based thing. myself Oh, I wonder what I can actually make this micro bit do and the micro bit I don't know if you've ever seen it It's like a little square with some LEDs and a couple of buttons and a gyroscope. And it's got a set of breakout pins on the bottom, but you only get about 10 IO pins. But if you thought how am I going to possibly wire up a full, you know, alphabet of of keys to this thing. So I used Microsoft make code and you can make add ons extensions for for make code and you can at the bottom of the micro bit is serial ports, an SPI port and I created an I plugged in an i o expander into that and wired it up and then created an extension to talk to it actually two IR expanders and then all of the buttons. And this was an idea in my head and I showed my daughter it and showed her that you could press the buttons and get the the the letters to come up and a B and C and then I showed her how easy it was to pick a wire up and swap it with another wire and press that same button and now it's a C and then that that sort of gave me the the platform to be able to tell a little bit about how a real Enigma machine worked and It was it was also led by one of our friends, Andrea, who works down at Coventry transport museum. And they've got like a young stem lab down there that she runs. And they were having a world war two and day and she wanted something to take down to that she didn't I don't taking it actually. But I promised her that I'd get it to a point where, where she could and I think probably next year now, because about anything that's happening this year. We'll get it a bit further and, and and see what we can do with that. But that was really fun, just not only from my own personal benefit to be able to learn how to get micro bit to do stuff that most people aren't doing with it, but to sort of get my daughter a little bit more stem wise.

It's good.

#### Jamie

Now that's cool. That's cool. If it's at all possible, I would love to see a comparison photo of a real Enigma encoder. And this moment Bear with a little keyboard. Yes,

#### Pete

yeah. Cheers. sighs there wouldn't be well if you've got it done properly. It'd be similar size I guess. But you'd have to put emojis of like a serious face on the Enigma machine and just be

#### Jamie

laughing

#### Pete

or maybe just that Picard thing where he puts his hand on his forehead it gets

#### Jamie

wider not That's amazing. I do. I do. Remember I went to bless the park as well. And I just remember I stood in front of the bump. And was just just I did not move. And I was just like, the whole time. Just watching Alan Turing's machine just tick away. Gio is incredible.

#### Pete

Absolutely. And that the film as well there was that film called

Yeah, that's so good. One of my favourite films. And yeah, it's such a was such an experience. I need to go back there because a lot of it was spoiled by my daughter. Same one screaming in my face because she was bored of me

#### Jamie

doing exactly what Did

#### Pete

it look? I mean, they don't like that do the children standing around doing nothing, apparently. But I wanted to, like absorb everything and go look at everything. And he can't do that with a five year old. It's not practical Austria. Say I need to go back just me, me a mobile for I think actually there's a good chance that there's going to be a trip or Microsoft trip down there at some point. So whether it'll go to Bletchley Park or to the Computer Museum, I'm not sure. But I don't even get to go to the Computer Museum either. Sounds good. It

#### Jamie

is definitely a multiple day thing. Definitely. Mm hmm. I haven't been to the Computer Museum. But I really want to. I could see here that you've done a privacy camera using Python and as your cognitive services as well.

#### Pete

Yeah, yeah. That goes back to the Lincoln hack. So that was my first step, a hack a couple of years back. Rob persuaded me to go to Lincoln hack and I'm really glad I did because it's such a great space. That hack is awesome. I know you've been to hack 24 I've not been, I can't give you a direct comparison. But, um, I mean, I think the tech nothing in the hack 24 one is like super organised and they do an absolutely fantastic job of that. And the Lincoln hack just seems really friendly and down to earth and everybody gets involved. And of course, I've never been to one before, so I didn't know what I was doing. So I went along with a plastic crate full of stuff just for everything. I had no idea what I was going to do and you get there and they give you exactly the same as hack 24 I guess they give you all of the different categories and they're always really broad. So you can fit pretty much anything into it. But and, man, I can't I can't even remember the name of the company. But it was a scholar pack. I think actually, the company who gave they just wanted something that would make teachers jobs easier. And by medicine daughter had been at school for a year at that point, I think a year or two We'd go through these learning journey books, and they'd be photos in there. And they'd be like just Island and then backs over the children or the sides of the children. And we spoke about to the teacher about photos and they said, Ah, that's a real pain point. Because they, they have to be really careful about exposing other children in photos of just one child, because then you can possibly take that learning journey home and safety and stuff, and it makes perfect sense. So I thought, well, I've got a Raspberry Pi here and a camera and I know how to do as your cognitive services. So I'll, I'll make a camera that allows you to take a photo and automatically blur everyone but one child in the photo out and then create a series of images with just one child's face visible.

#### Jamie

And so

#### Pete

I was one of the annoying people. I got that most of that done on the first day and I went probably left about I don't know, half 910 and went to bed and got back about 10:10am The next day, and just finished it and then the two hours that were remaining. But while I was doing that even I was next to a really cool

web design company called epic media. And they were making the coolest zombie destroying building that I've ever seen it was that made such a lot of effort. I was fantastic. But they even had an Alexa and I helped them get that set up. So that we can ask Alexa, how many zombies were outside, and it would tell them how to do something that was really cool. So I even managed to help them do that as well as finished mine off. And then a one and a one a whole heap of really expensive board games and I was over the moon. And I saw one of the judges last year after Jess White's DVD. And she says, Have you made that thing and sold it yet because you need to fantastic and I still haven't. Mainly mainly because it uses Azure cognitive services and I love Azure cognitive services, but it relies them on an internet connection for your camera the whole time and it's just going to zap any battery that you're trying to attach to it. So this is Lincoln hack,

Unknown Speaker  
I

#### Pete

sat down and we enjoyed the team with with Epic, said had such a good time with them last year and we made we built on their zombie idea by having a zombie bunker that had a camera on the front of it, and it would use open CV to check for zombies, and it would tell the difference between Bill Gates and a zombie and it would open the door for Bill Gates and not for a zombie. I don't know what would happen to Bill Gates would have turned into a zombie mind you. But it had an air quality sensor in there as well. And I'd hooked up an IoT central dashboard to it and it was the same as overboard and we didn't win. disappointed because I think it was fantastic. But it was all it would work all offline because of open CV and I'd really good fun with that. And that was a video feed it wasn't taking photos. It was just live taking the video and tracking faces and doing recognition in those. So do that though. did get about two hours sleep. So it seems as though the more effort you put into these things, the less likelihood of you actually winning it

#### Jamie

would echo that sentiment, I think and hack 24 to the second one that we turned out to win, we won a whole bunch of prizes. You have to you have to make the thing. And then you have to make a video explaining what the thing does. Because you know, they don't have time to try everyone's piece of software. But you've got to make your video in like two minutes or less, two minutes or less in life. And we spend more time making the video software

#### Pete

and obviously, that was the key you see exactly. You had a really good idea and nailed it in a couple of hours and then

#### Jamie

12 hours making the video. That's it That's exactly what we did. super hot on the VR and then made a video.

#### Pete

Yeah, that that that game is apt the name of that game because you are boiling. Hot play in that game, it's hard to stay still and play that game. It's good game is

#### Jamie

one of the things that I'm interested in with IoT is the DevOps and containerization side side of it. Because a lot of people talk about like DevOps and I can I could do the Netflix that I've talked to someone this earlier on today about Netflix, and I said, don't do because I'm kind of a consultancy type as an as I'm like, Don't aim for Netflix. Because you're not Netflix. You're a startup, right? When you've got a million customers and 10,000 servers, then aim for Netflix, right? Yeah. But until

#### Pete

somebody does what he's paying you at that point to do that work, do the work that no one's paying you to do.

#### Jamie

Make it stable class, right? I think so. So my thing is with with containerization with DevOps with as your AWS, whatever your provider is, like push a button spin up another thing, right? But I can't push a button and spin up another IoT board. So, how does DevOps and IoT fit together? Is that just like, how, how does that work?

#### Pete

Yeah, it's something that not a lot of people speak about, funnily enough, but it's really it's a requirement, actually, if you want to do it properly. And I think, funnily enough, the IoT is still in its infancy for the most part and people are playing and prototyping still, and a lot of it small scale and a bit. And people like Microsoft, specifically have really thought about this whole process and things like that. It's not pure DevOps, but as IoT edge service there is fantastic and that's a containerized systems that runs on whatever device you want. And Raspberry Pi tends to be the one that that I look at most, but you have a runtime that right On the Raspberry Pi, and that's constantly looking at a Container Registry and Azure for updates to a module, they call the modules but they're essentially containers and they are Docker containers. It's a Docker version of Docker, but they're running on there. And so yeah, you you can code a module on your PC here and then push it out. If you're just if you're just prototyping, you just right click on it until it's published out. And it'll go into a Container Registry. And you can tell that device that it needs to have that module and the runtime on the device will say, all right, well, I know what I'm doing is going through something called as IoT Hub, which is like a big switchboard and as your device if you have millions of devices connected to this, so it has a version of the IoT Hub running on the device itself, and then that's talking to a real IoT hub in Azure. And those two things coordinate together. But I mean, that itself doesn't give you DevOps, because you're still pushing a button on it, you know, you've written the code to push it A button code or Visual Studio, it's not it. So you can integrate all of this platform into Azure DevOps, agile pipelines if you like. And so you can have it build your whole ci CD pipeline, you just check the code in, and it does all of that building, and creating a deployment manifest, and then pushing out devices, either one at a time or at scale. So it can do that. But you kind of highlighted the fact that you can't just spin an IoT board up. And that's one of the issues, certainly, if you're talking about Raspberry Pi, because that's arm, arm 32 for the Raspbian operating system, and they don't offer arm as a build agent in DevOps, or at least not arm 32. I think there's an arm 64 one funnily enough, but that's no good either. Although I think there might be an Ubuntu 64 for the Raspberry Pi that's just come out recently. But aside from that, what you have to do is use in this particular model, you have to use your own self hosted build agent, and you have that on a real Raspberry Pi. And so part of that DevOps pipeline, ships off the bits down to the pie. And it builds though that container on the on the hardware in the right format and sends that back to the pipeline. And then that gets bundled together and sent down. And that works really well actually. And there's there are other ways of doing that though. I've not figured out how to do this in Azure. But the open source equivalent of this with Jenkins, you can you can containerize with something called chrome you a 32 bit ARM processor. So it's essentially an emulated 32 bit ARM processor. And you've run Jenkins on a virtual machine and you have Docker running on that virtual machine with a chromium image. And then you use ship down into that to build and you're doing it with Docker, not Azure IoT edge at this point, you create a Docker image in a Docker image, and then feed that back into the pipeline is very inception. That works really well and all of that other than the VM storage And you know, that sort of stuff. You're using Docker hub for you Container Registry. And it's all really cheap, I think the VMs most expensive part, and that was like 16 quid a month or something to to have the VM sitting there. And I've just stopped that recently. But it

#### Jamie

is pretty,

#### Pete

pretty cheap. And there's lots of moving parts when you need something called Watchtower, or an equivalent, I think you can do it with Kubernetes if you get really, really complicated, but you have something a Docker image called Watchtower, and that's looking at images in Docker hub to see if there's an update. So it's very similar process. It's just rolling your own. But you're gonna need something like that. The problem with any of these systems is that you need to build a lot of resilience into that whole pipeline. Because if you deploy at scale, and you've got 1000 or 10,000 devices and you break them all somebody's gonna be knocking at your door. They're not gonna be happy because they can't boil the kettle. Yeah.

Temperature tea or coffee.

#### Jamie

No is no longer a million dollar mistake. Yeah, not sending the correct Docker image up and wiping out. The fleet is now a mistake. Yeah, yeah, it really would people would be annoyed. Excellent. Okay.

### Sponsor Message

This episode is sponsored by {{< sponsor-link link-text="ConfigCat" link="https://configcat.com" >}}

ConfigCat is a feature flag service.

- It has a central dashboard where you toggle your flags visually.
- Hide or expose features in your application without redeploying code.
- Set targeting rules to allow you to control who has access to new features.

Easily use flags in your code with ConfigCat libraries for .NET and 9 other platforms. Get builds out faster, test in production, and do easy rollbacks. Release new features with less risk, and release more often.

With ConfigCat's simple API and clear documentation, you'll have your initial proof of concept up and running in minutes. Also, train new team members in minutes and don't pay extra for team size.
With the simple UI, even product managers can use it effectively.

You can try it out with their forever free plan. Or get 50% off any paid plan with code `NETCORESHOW`

Release features faster with less risk with ConfigCat. Check them out at today at {{< sponsor-link link-text="configcat.com" link="https://configcat.com" >}}

---

### Jamie

So there's a lot of those moving parts. So then. So let's take the Raspberry Pi out of the equation, right? Let's say you're using Arduino or some other device. Is it still as I don't want to say complicated, but I don't really want to replace it or complex because they're kind of the same word. But is there still as many moving parts in wanting to deploy something to say, Arduino or any of the other formats? the Adafruit those kinds of things?

#### Pete

Yeah, well, you're talking about different beasts entirely at that point. I mean, the closest you get to that is something called the MX chip dev board actually, which is another Microsoft piece of kit and that's Arduino based, looks very similar to a micro bit, that same sort of form factor and it's got that same edge connector idea, but it's Got a new lead on it and, but that can hook itself straight up to IoT Hub and you can manage that in a very similar way. So you can do deployments through IoT Hub. But just blanket if you say Arduino then you're talking very low level stuff. And and yeah, you're probably gonna have to roll your own at that point. But there's been a recent announcement a builder rather something went ga something called articles as your articles and they've created a whole operating system for really low powered devices. And I think unless you're using the GUI elements, and then it goes all the way down to two K, so it's a whole operating system that runs just in two K of memory so I mean that Yeah, when you say TK to somebody you can't even write a game in TK anymore. So you can you can kind of

#### Jamie

I don't know whether you know, but there was the guy. Oh dear, what was his name? McHale Stroh Ostrowski who Took C sharp dotnet snake and reduce it to a case book. But he had to put like, days of work into it right? And he rolled his own compiler and mess around with his own to write his own interfaces for the actual dotnet stack and say, don't, don't eat this, don't eat this. Just implement empty interface versions of them. And yeah, so it's possible, but just Yeah, you're not gonna go to commercial products.

#### Pete

Like, like the guy who managed to because oh, well dotnet cause cross plat isn't it? So why don't we compile some of this stuff to run on Windows? 311 I think we even managed to get it to really docile so they didn't they somehow

#### Jamie

Yeah. It's the same. I was it out. There you go. Yeah. Yeah, he's, he's part of the core RTT. And he's telling me Yeah, it's just, I'm playing around with it to see what we can do with it, and then show it off. Because, look, you can write your apps for Windows 3.1

#### Pete

Yeah, exactly because I can. When is he going to be the Commodore 64 version? Is he gonna be

#### Jamie

an interesting question? rusty Linux 64 went out to the Viet amazing Vegas they

Unknown Speaker  
gonna do?

#### Jamie

Yeah. Oh, that's it. We'll have to do it once we finish this recording, tweet the boss and say, Look, when's the C 64 dotnet core SDK come out.

Unknown Speaker  
I can't wait.

#### Pete

Sorry. It's got to be the one to eight and can't do it at the 64.

#### Jamie

Exactly. So, so then so one of the one of the things that I'd like to ask is, have you seen Clifford Aegis is a handy project.

#### Pete

We had him not say it, but he was I think the last time Speaker we had before we had locked down. And that was one of the best meetups we've ever had. We had Clifford and Thomas bartowski terrible at pronouncing his name. So apologies, Tom. I should have pronounced that incorrectly. But yeah, so, Thomas, we're talking about IoT hubs and stuff, which are close to my heart and all that stuff. And Clifford was talking about his handy, which is like a Xamarin controlled. I think it's an Arduino that he's caught in for gadgets. Yeah. It's an Arduino. Yeah. So he's been struggling with it recently. I think it got broken, didn't it?

#### Jamie

I think when I talked to him about it, he'd swap the Arduino for an Adafruit. And then yeah, this was back in January when I talked to him. He said in March, I'm going to be installing and trying to instal a meadow, because their Bluetooth stack wasn't quite right. It's like I have to be able to controller from the phone, you know?

#### Pete

Yeah, we can write a C sharp if it's a matter of fact, here. x labs has done myself one of those. Because Yeah, it really does look cool that in fact, they have a boot camp. I think it's going on right this very minute that I'm not attending because I'm talking to you. The reason I'm not attending is because I don't have one. And so a lot of watching people do it. Isn't this fun? Yeah, it's Clifford has also been he's just brand new MVP as well. And for good reason. He is mega cool. Like, he's gonna go a long way. And plus, he's a pilot. So he wouldn't be to be it's just not fair.

#### Jamie

I was sat there talking to him. And I'm like, like, so you've made this project in your own time. You made it with your own money, and you're giving it away, which is wonderful. But you're not even a developer by trade. What are you doing to us all?

#### Pete

He is the guy that wins when he does the work, but obviously, there's a shitload of work. And it's the nicest guy that you'll ever meet as well. It's just got everything. And and yeah, I think most recent sent me I saw him down at NDC London and we had to catch up down there too and, and then he came up to not saying it and spoke there and everybody was in on. There is a really cool coincidence at the same time actually, there's one of the most popular people in the 19 community is Juana and she runs pf knots and project function thing, which is for disadvantaged people to get into tech and that's a fantastic thing but her sister Can I think lives in Germany was over and she was doing a uni project on a hand she wanted to create a hand and she emailed me a couple of days old tweeted me I forget a couple of days before not so tea and I said you just need to come because is going to be able to answer all your questions so she came to that and then resin and her came round and I wired up because she bought and I think she did it with the Raspberry Pi Zero perhaps but she bought the header and didn't realise you needed to sell would have a header in and stuff so I sold it all of the stuff together and I think it all work thankfully. Although missing Folding arms having a bad day that day. But it did it worked still. So yeah, it's so much fun. All the different stuff that cliff Clifford is able to talk about in that they're just 3d printing on its own. All that stuff was cool and then all the little tendon II type things to be able to, to pull the hand a mate, and then yeah, there's Ammar inside and the different sort of functions that he could make it do and it was even able to play Xbox with it and ice just yeah, incredible stuff.

#### Jamie

fascinating, fascinating stuff. I do remember I don't have to catch up with it. But I do remember when I talked to him at NDC London, he said I need someone to help me with machine learning. So hopefully by the time this goes out, he's already found someone to help him but I was thinking sure a cognitive services that's kind of machine learning, right?

#### Pete

Yeah, to a degree I can tell it whether the hand is happy or not Yeah.

#### Jamie

sets off the singularity. See, it'll be here. It's true. I like it. There. Okay, so we've, we've left the job to love IoT, but I've got a so how do I get started with? Let's say, I don't have any boards, but I want to write an app and I want to run it on a simulator is there is there a simulator that I can get is there? What can I What can I do I have this itch to do the IoT. But my my deliveries aren't going to come in for three days. What do I just wait three days? Is there like a What can I do? Is there a VM I can run a simulator? What's the file?

#### Pete

Yeah, you don't even need just don't even bother ordering anything to begin with is what I tell people, I guess a trade simulator, actually. I mean, there's there's so many good ones. It really just depends on I guess it depends on your level. And if you're really sort of proficient experienced programmer and you're happy with either mode or, or see even then there's there's a couple of simulators out there. I mentioned the MX chip. device. And if hooking up to something like Azure is really what you want to get to work and sort of the hardware is almost second second fiddle to the fact you want to connect it to Azure, then this is really good. You go in there, it's all in C. I'm not an expert in C at all, but all the codes there. So you hit this MX chip simulator up there. And this is a, an open source GitHub project that Microsoft have made. And if you've got show notes, then we can put the link to all of these in there. But all you need to do is click a button and it'll run you through provisioning all of the services in Azure. So don't even need to worry about how to do that it will do that path for you. And it will take a connection string from the IoT hub that you're connected to and it'll put it in the box and you run it and there's a little simulator there next trip device with its own LED on the right hand side and a couple of buttons and it tells you to hit a button and then you can shake the device and then it'll send a message up to IoT Hub. And you can download something called the IoT explorer on IoT twin SDK. And there's a little application you can run there. Again, it's open source. And you can paste a different connection string in slightly different connection string in there for the hub rather than the device. And you can monitor those messages so you can get that that comes. But you don't have to have a device for that. So if Ash is the way to go, then that's, that's fantastic. There is a Raspberry Pi flavour of that, and that's all in Node. And that's again, another open source Microsoft Project. So, Raspberry Pi as your simulator, and you just need to create the the IoT Hub and there's some instructions, a nice useful help file in there that you can go read and guide yourself through that, grab the connection string, paste it into the note j s and hit run and do that same thing and it just works and there's like a fake temperature sensor and a little fake LED and you can see the LED flashing and it sends some simulated temperature, humidity and stuff up to IoT Hoping you can you can then the good thing is, once you've got it going into IoT Hub, then, you know if again, if Azure is the goal, then it you don't need the device, it's all the data is actually going there. And you can you can play with me time series insights or analytics or apps or a logic app or you know, anything that you really want to do at that point. And, but if the hardware is what you want to do, if you like a young adult, then always pointing them at the mate code website for the micro bit because again, that's really a simulated micro bit and you hit up and you get a micro bit on the left hand side and you get a blockly based programming paradigm on there so you can drag blocks to make your code rather than having to type it but it is reasonably powerful even you can go into the advanced section and there's like a pins area and you can drag a servo on there, and it servo will appear underneath the micro bit and you can make a fake servo move and the wire colours and everything all line up with a real server you buy. And say you can buy a micro bit by a server and some crop clips and hook them up to the same wires that you can see on the screen, download the code from make code and just copy it onto the to the micro bit and it will just work.

It's really cool way of just getting started with stuff. But then my favourite that I always like to leave too last bit in the talk that I give. It comes out halfway in between because you Lambada on somebody that they don't know anything about it. And yeah, they get a little bit bamboozled by that but there's somebody called tinkercad. It's made by Autodesk and people make AutoCAD and you it's a circuit playground. And you could drag resistors and led batteries and 74 Ls chips on there and make whole circuits but you can drag an Arduino Uno on there as well. And when you do that, and you hook up your components, there's a little code button that appears, you hit the code button and you can programme the simulator Arduino in a block based paradigm in there, too. Now, I don't know if you've ever tried to programme an Arduino but it's in C. And if you just start out in programming c isn't where you want to start if in fact, people say start with JavaScript don't start with JavaScript either. Oh, actually, if JavaScript that easy to start, it's just when you don't want to do anything that's HelloWorld. in JavaScript. That's complicated. But yeah, it's a drag, you track the blocks in and you can, you can make your Arduino do stuff. But when, when you're a little bit more proficient, you can switch that off and go for the C

Unknown Speaker  
version of it.

#### Pete

But even better than that, you can even put breakpoints in your code. And he can, you can stop and step through your code and inspect variables and stuff. And that's massively powerful. So I mean, you could, you could drag all sorts of stuff on their servers again, like we did with the micro bit, make code, but you can drag like motors on there and make like, foam robots if you like. And I made a full like four For motor robot in, in tinkercad, before I made it for real just to get the software working properly and understand how the circuit was going to work, it looked horrible, but it did work. And yeah, that's by far and away my my favourite demo to show people because nobody knows about it and no one knows about tinkercad. There's a similar one by Microsoft for for bunch of different devices. But based on make code, and what's that called, coming from, it's called now, maker dot make koat.com. And you can select from a whole heap of different Arduino based devices on there and you, you choose whatever your platform is, and it brings you up something that looks almost exactly the same as bytecode. And because it is displayed based on the same underlying design, but instead of a bike, repeat and you get saved An Arduino zero. And you can drag pins on there and tell it to turn a pin on and off. And it will know that you want to turn an LED on and off and it will create your little simulated breadboard with an LED on it and a resistor and it'll connect it up to the pins you tell it to. And then you can just write your code by dragging blocks on there. And it'll simulate an LED turning on and off. And it's incredible actually what you can do without buying a single piece of hardware. And people need to know more about that because so many people are a bit scared or or put off by the number of options. There's so many options that I mean, there's an assumption for simulation, but you don't want to make the wrong choice and go and buy an expensive board 20 3040 quids worth of stuff or you know 7080 quids worth of Pataki Raspberry Pi and not really know if it's for you or not. So yeah, the coolest one actually is there's an Astro pi simulator. You've heard of Astro pi. I have no say on the space station right now. There's two Raspberry Pi's. Tim Peake took them up. When he went up there, and there must be pies and a book a dice case with a hat on board that's a little bit like a micro bit with with temperature, humidity and a gyroscope and magnetometer and a display and stuff like that. And kids and young adults can write experiments down here on Earth, and they get sent up to the space station and run and they get the results back.

Oh, and it was really just, it's so cool. And they have

a hack every year, and I think we've just had as the January and you can write, like even five year olds can write stuff that will go up there and just say hello to the astronauts, and he got a picture of it running in a certificate to say that it's running. And

younger adults

then get to run proper experiments and there's like a lottery system as to who's or which which one gets chosen but that's all Raspberry Pi in the sense hat that you plug into it and possibly a keyboard and mouse and monitor an SD card and power supply and a case and also Both things add up to a lot of money. But there's a simulator for that written in trinket. And it simulates the whole sense hat part of the Raspberry Pi. And so you can write the Python code right there in in trinket

and, and then run it and it will show you the results

directly on the screen there. And then you can just copy and paste that code onto a real Raspberry Pi with the sensor and run it and it will just run. And so I'm going to tell anybody, anybody that cares, get everybody's space. Just cool.

Never mind that a child is

Unknown Speaker  
expired.

#### Jamie

Right? One of the little ones, one of my little ones. This is just gotten really hardcore into science and he's like, got to do science when I'm a grown up. I'm going to do science right here, what kind of science but he's going to do science. So I can set that up for him. I got three PI's, laying around the house, getting some code and getting running in space. That'll be amazing, right.

#### Pete

I think moon hack is coming up

where we ask you to make money related projects. And I taught my eldest how to do a scratch programme where we had the Phoenix lander was coming in, and it was too many boulders and we had to carry on and it was running out of fuel. And we simulated all of that. And she, like, I told her what to do for a lot of it, but she had the ideas. And then she wanted an alien who would be scary and stuff at the end of it, obviously, there's got to be aliens. And

yeah, it's really accessible stuff like scratch,

which I know it's not really IoT, but it's been popularised by Raspberry Pi. That sort of stuff that brought based programming languages is awesome, in fact, that broad base programming paradigm is is starting to take off again now. And a lot of people frown at the fact that it's simplified, but stuff like Power Apps, Logic Apps, it's all block based programming. And I think that will will not get parity ever, obviously. But there will be a point where a lot of what we're going to do I mean, we laughed earlier about the fact that we're just putting blocks together. But why you don't need to reinvent the wheel for? I mean, what is no do we download one package to get 600? Is the same sort of idea. We're just plugging blocks together.

#### Jamie

Exactly. And, and the people who say that this isn't real programming that isn't real programming, you know, I left earlier on about my friend James and I talked about C sharp as real programming because you know, but we talked about that because, you know, you're not writing the low level stack. You're not writing the TCP IP code and all that kind of stuff. But even even if you're working in C and c++, you still not doing the enemy you pull back on it. But people will say that this isn't real programming This is or what I do his real programming, what you do isn't all they're doing is gatekeeping where they're telling people who want to know how to do it, that they can't do it, because oh, well, you're not as good as me. And I'm like, shut up, check this thing out. You know, come and have a look at this. It's amazing.

#### Pete

Yeah. But find people that are really frustrating. And, and I mean, have a stem Ambassador as well. So, you know, I've kind of driven by the fact that I've got two young kids to do that and It puts everyone off. But it puts people that, that believe that off more. And the only way to hear that one's from somebody that is respected. And I'm hoping that I mean, Scott hanselman is doing an absolutely fantastic job of dispelling all of those myths and build. He had an interview with a young girl I come and what I mean was, she was fantastic actually. She'd entered a space competition with a bunch of friends and they were making a space caps your radiation monitoring system, and they were doing that in and make code and Scott was interacting with him. And he was he was awesome. The way that whole interview went down was fantastic. And he was talking about the block base programming paradigm in that and how people frown on it. And yeah, it was like, Yes, exactly what Scott was saying. Exactly. Just that, please.

#### Jamie

Yeah, it's just what we do. I think on a day to the races is hard enough. Anyway, you know, we've got to take this vague set of why won't the To do and make something that is never going to reach that, because what they want the app to do isn't what they actually want the app to do. So that is difficult in itself. Right. So and then writing the code. Yeah. All right. Maybe you've got decades of experience, but he's still going to be there's going to be parts that you don't quite get. There's going to be difficult to do. You're going to hit some roadblocks. So it's going to be hard anyway, telling people when they start stop it because you're not doing it properly. Is No, let them get the experience. Right. I still remember when I was a kid, we had an Amstrad CPC 464.

#### Pete

Right, was a green screen. Tell me how to Green Green Green

#### Jamie

Screen tape deck, very rhythmic carrier. It's nice. And, you know, I sat there with this magazine, we had whole bunch of old stack of magazines, right. They all had these basic listings, and it was a Yep, copy this into here and run that. And you know, I wasn't a good typist, and I got a lot of stuff wrong. And I struggled for hours and hours and hours. But then when I hit that button, Animated a stick figure was going across the screen. It was the greatest feeling ever look at what I've just done. None of you can do that. And if you could do that with Brock bass, if you can do that by typing in arcane commands, if you could do that in Python and C and C sharp or JavaScript, whatever it is, you're doing, do it because you'll feel that elation, right. You're definitely right.

#### Pete

Yeah, I mean,

that's that's how I started cider spectrum. So my cousin had a 464 funnily enough, I think Yeah, john blade and that game is awesome. And but yeah, so I had the same thing so your Sinclair or whatever the magazine was with a really bad listing that never worked. But one funnily enough when I was 14, and I had something called a Sam coupe, which is like a souped up super spectrum. And I created an advert for lemmings for a disc magazine called Fred back then, and recently I managed to get rid of the some key players of discs and I found that programme that I created when I was 14 on that disk So I'll put that on YouTube. But yeah, for that's like, I don't know, 26 years ago, something like that 20 2028 years ago, something along those lines, but I wish I had the actual code. That would be fantastic. Because I think Colin, the guy that ran the magazine, it was really basic, but I made a really hacky, I think he recoated it into like this half a cable TV, all singing or dancing version of what I've done in half a minute. So, you know, gutted at the time, but it was awesome to see my work on there, and I've done a few things. But you're right, and I kind of want to instil that in my daughter and I was really proud. And one day when after we'd been doing all this scratch work, and she had a project to do a science project. She did it in Scratch. We worked on it together and she went to school, which couldn't get it to work. And she was good too. But she said but don't worry daddy because I just showed them how to make it.

Run essentially ran a class on how to make a new scratch and make it fail.

Fantastic. And now she has we have every night o'clock past six.

My father in law reads a story to all of his grandkids it's really cute. And he disappears off after he's read the story and all the grandkids sit and talk to each other. And I've caught either a few times on scratch

showing how

cousins how to do stuff and they do it as well.

So they're making these janky little programmes and so she's really excited about it.

And yeah, I'm chuffed and stuff like that. And but I mean IoT is one of the reasons why. Well the reason why I like it is because of this because it's great. It's been caught and scratched but when you show them something real and robots what you know kids love robots, or anything that moves and to show them how easy it is certainly the the micro bits, they're good for that and there's loads of little robots that you can go buy off the shelf and plug the micro bit into and and the counts just drag and drop and you copy it onto micro bit. And nothing goes in the gutter robot and they love that physical physical stem stuff is fantastic for that. So, I love that.

#### Jamie

Yeah, I still remember using Did you have one of these the turtle robots at school? He had like, a 10 Turn left by 45 degrees

#### Pete

there. Yeah, yeah. BBC that was that was Yeah, I've got a BBC BBC recently. Exactly that one. It's like scratch scratch is almost that exact same thing. Have you seen the guy that's hooked an Arduino up to a real BBC? And you can tweet it. He tweet The, the the Twitter account I come up it's called, but he tweeted your programme, it runs it on a real BBC sends you the video of the output. Right?

#### Jamie

How cool is that?

Okay, so. So we talked about the simulators. We talked about how you don't have to actually buy anything. So then I guess the difficult thing is like, Okay, I have an idea. I've got my little one. We're going to build a robot. We're going to use we don't know what we're going to use yet, but we don't know what Would you really use the URL of the device's language agnostic or we talked about Arduino requests see right and then like the micro bit requires I think he said C as well and but you can use scratch in the maker stuff uses visual paradigm what? There's so many different languages. How do you how do you settle on one device one language and build your app?

#### Pete

Yeah, well, I mean, Arduino funnily enough, yes. See, mainly but the circuit Python. So you could do Python for for Arduino as well, and pythons a lot more accessible than C. Well, anything is a lot more accessible. Actually, Russian i think is lovely.

Unknown Speaker  
But,

#### Pete

yeah, so But the good thing again, about something like tinkercad or that make code. In fact, they make code equivalent you write in JavaScript, and then you download a file prebuilt file and you just copy it on to an Arduino zero. works a little bit like a micro bit in that stage. I mean, you go to Raspberry Pi, and you can do whatever you want. Really just up to you, that micro bit you're doing in either blocks or JavaScript again, because it's the same underlying system. But again, all of those things, you just download the code, and you copy it onto your device. And perhaps you don't even need to see the JavaScript. Something Yeah, the more complicated you get the area, if you want to do anything at all that's going to connect out to something like Azure, then you're going to need C or C sharp or node or Python, any of those sorts of languages. And Microsoft and I mean, the AWS equivalent as well, obviously, they'll give you SDKs for all of that. I mean, oh, Crikey. Trying to do any other lines. See, though. Sorry, see programmers. But it seems hard.

#### Jamie

And this is from the guy used to do assembler.

#### Pete

Yeah, well, yeah, that's true. I said was hard.

But as far as what you said, Did

you see at that same company, actually, but I spent a lot of time on forums asking people what the heck and can people give them the answers Copy paste that in. And that worked. I've got no idea why. But what it does is sees hard pointers and all of that Archie's too many hands. I don't like it. But, yeah, I mean, again, you just don't have to get too involved with that. I mean that tinkercad, it will download the code for you as C, so it'll convert your blocks into C, which is good. So if you wanted to learn C, or at least the Arduino flavour of C, then that's a really good way to try and move people. And that's kind of what happens. So with, with something like make code, you can start with the blocks, and then you can switch to JavaScript. So that's a really good way of teaching JavaScript. And there's an equivalent for baking arcade games as well, which I think Scott hanselman demoed. And so that's really cool. But then yeah, Raspberry Pi. If you want to do anything as you agilely then you're going to be on something that I spent a lot of time in node, but obviously we're on the dotnet core podcasts so you could quite happily run dotnet core on So I've made a single line instal script to be able to instal dotnet core on a Raspberry Pi now. So before it was rather difficult with quite a lot of steps. And so yeah, he said, I write a lot of posts, and that's part of that series of poses is how to do that instal process and I just got bored of telling people, it's too hard, because as we discussed earlier, you don't want to tell people stuff salad, because they're just not going to do it. So if it's one

single line to instal it, then oh, yeah, I'll do that then don't have to worry about it.

#### Jamie

It's all about reducing that barrier to entry, isn't he? Precisely? I argue that. Although Yeah, we talked about JavaScript isn't maybe not a really language to start with. But when you get your computer with a laptop or desktop, whatever, it has everything you need to be able to do JavaScript. You've got a text editor, you've got a web browser, don't write your barrier to entry solo. C sharp dotnet. Yeah, you've got to instal the tools. But once you've done that, at university, right, I studied at the University of hull and Rob miles now he's a very big DDD and IoT. person, but all of his lectures were done with notepad and the C sharp command line compiler. So you just didn't know the name of the file and the notepad will come up. And then you do CSE the name of the file and it will compile, right because you don't need these fancy tools. But yeah, that's that's a little bit more complex, but reducing that barrier to entry. If your entryway into development is all right, I grabbed a couple of bucks boxes and I drag them in and I draw lines between them. Fantastic. If you if you're brave enough to look behind that and see what he's doing, even better. If not, don't worry about it. We'll move on to something else. I love it.

#### Pete

I think Microsoft have recognised that as well with the push that they're making to make this many, many bits of that learning journey free. And certainly I mean just just ms learn all on its own and now Ms. Learn TV that's just been launched is a great way of starting that off and then things like vs Community Edition and get hubs now free and bringing Xamarin and making that free Yeah, they're, they know what they're doing. Because certainly, if you can grab students early enough, and make universities use it, because it's also free, they'll go into a job where they already know that stuff. And if that company isn't using it, then they'll go, I don't know how to do this. And then suddenly, you know, five years down the line, you have a gold partner and that company, and they're spending a lot of money. So I mean, that they they're doing it for a good reason. But they're also altruistic. And at the same time, it's, yeah, it's fantastic. Removing roofing barriers is the forefront of what I want to do really is. It's great.

#### Jamie

So what about everything else? So what's the let's, let's say not everything else, because that could take years. Everyone wants to reach out to you and say, Hey, Pete, I've got this great idea. Can I talk to you about it? Can we figure out something about one of your meetups or talk about how we can, you know, you said you're a stem ambassador. So how can I talk to you about that? What's the best way for folks to get in touch with you to sort of further this conversation?

#### Pete

Yeah, Twitter's definitely the best way. So at PT underscore codes on Twitter, just send me a message on there and start the conversation that way. Email. I've got, I think, email bankrupt on several different email accounts. So yeah, I tend to miss emails. But yeah, Twitter is definitely the best way. And I'm more than happy. I love I'm just a massive geek. So I love hearing about what people's projects are the number of times that people come to a talks and then they'll go home and they'll send me a tweet to say, oh, what I bought all of this stuff now and I'm gonna hit wide open, please. Can you help me with XYZ? Yeah, I'm trying to work actually. But I'll definitely helped me because that looks really cool. I saw somebody making in this world of COVID. They were using micro bits. And you can you can look at the radio power between two different micro bits to look at proximity and say they're gonna make a warning system VTT might tell me if you got to, like the government tracing app, but micro bit version. That's a really cool idea.

#### Jamie

Yeah, right. They're not that expensive. So you could just make a whole bunch of them and just give them out to people where you can wear them like Iron Man's or chest thing, right?

#### Pete

Yes. We got a million out two years, seven and eight or seven or so. Yeah, do it again. Yeah, right. Every bit

#### Jamie

better. I like it. Excellent. I like that. I like that. Yeah. Oh, geez, this is, this has genuinely been an amazing conversation. I really, really love this conversation. So here we talked about how people can get in contact with you. So what are what were those meetups again and we'll put those links in the show notes but just so that people can sort of re hear them because obviously people have maybe driving or something I don't want to reach another distro. grab a pen whilst they're driving, you know,

#### Pete

now that just be very, very dangerous. And yeah, please, please don't bring us if you're in a ditch.

We shouldn't be the first person.

#### Jamie

I can't fix cars okay.

#### Pete

Body Parts actually.

So knots at dotnet knots

not step workshop and Lottie are the the the four main ones I'm also i know i was really bad, but I'm also part of the Agile engineering podcast. This is four of us that five five of us are doing for those of us. And in fact, Liam Gulliver, one of the guys whose runs that he also runs and DevOps knots, and he's got Jean Kim at the end of this month.

Oh, they love me from actually that depends on when this goes out. It might be too late.

#### Jamie

Well, I can take a small snippet and push that's no problem.

#### Pete

Yeah, definitely. So So Yeah, that'll be good. That'll be recorded anyway, so you'd be able to watch the recording after this recording.

#### Jamie

Oh my goodness. Yeah. I've had a tonne of fun talking with you today up and we'll have to catch up again. When this whole this whole situation is over. I keep referring you know Other guises as the nonsense but not because of any political reason just because let's make fun of it and is easier to deal with. So once all this all this nonsense is over, let's figure out a way to meet up I owe you a beer or something.

#### Pete

Yeah, anytime that involves beer, then I'm going to be there anyway, which is half the reason to go to all of the DVDs that I always see you at.

dotnet core guy.

#### Jamie

Well, like I said, Thank you ever so much, and I hope whatever it is you do with the rest of your Friday evening, you have a wonderful time doing it.

#### Pete

I'll save it myself. I'm not I'm not not gonna wait for the firmware update to happen on the machine. Thanks for having me

#### Jamie

Thank you.

{{< paracentre "The above is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

### Wrapping Up

That was my interview with Pete Gallagher about IoT and .NET Core. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/), and there will be a link directly to them in your podcatcher.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice - head over to [dotnetcore.show/subscribe](/subscribe) for ways to do that - and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Pete on Twitter](https://twitter.com/pete_codes)
- The many Meetup groups that Pete is involved in:
  - [Notts IoT](https://www.nottsiot.co.uk/)
  - [Dot Net Notts](https://dotnetnotts.co/)
  - [Nott's Dev Workshop](https://www.meetup.com/Notts-Dev-Workshop/?_xtd=gqFyqTEyMzIzNTY5MqFwp2FuZHJvaWQ&from=ref)
  - [LATI](https://lati.org.uk/)
- [Agile Engineering Podcast](https://agileengineeringpodcast.com/)
