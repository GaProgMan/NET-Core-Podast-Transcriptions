### Sponsor Message

This episode of The .NET Core Podcast is brought to you in part by {{< sponsor-link link-text="RJJ Software" link="https://rjj-software.co.uk" >}}

RJJ Software is dedicated to helping you to realise your company's digital potential through innovative solutions using the latest technologies.

Utilising the latest in .NET and cloud technologies, we can help you build the solution to your business needs, on time and under budget.

We have world class experience in cross platform development using the latest iterations of the Microsoft technology stack. This includes .NET Core; SQL Server; and Azure. Is Azure not your thing? That's fine, because we have experience with AWS, GCP, Linode, and Digital Ocean, too.

We know what it means to have to be able to iterate quickly, and how important DevOps practises are when it comes to remaining Agile. As such, we have experts in the major build and release pipelines: from Azure DevOps to AWS, from Netlify to TravisCI, AppVeyor, and everything in between).

So get in touch today at {{< sponsor-link link-text="RJJ Software" link="https://rjj-software.co.uk" >}}, or check the show notes for a link.

---

### Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is Episode 71: Azure and .NET With [Labrina Loving](https://twitter.com/chixcancode). In this episode I talked with Labrina about her work as the lead engineer at Microsoft, working on the Azure platform.

So let's sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

{{< paracentre "The following is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

#### Jamie

So thank you ever so much, Labrina for taking some time out of your day, which I completely appreciate is an incredibly busy day anyway, regardless of what time of year what the what the current situation is. So I appreciate you taking some time out to talk to me. So thank you ever so much for that.

#### Labrina

Oh, thank you. Thank you so much for having me. I really enjoyed it.

#### Jamie

Excellent. So I was wondering, before we begin, would you mind telling the listeners a little bit about yourself? You know, usually, some people just go, "Oh, yeah, I work for this company. And I do this thing." It's up to you, however you want to introduce yourself? Yeah.

#### Labrina

Yeah, that's like like that. That's probably the hardest question you'll have all day. So. So yes, my name is Labrina Loving. I have been in and around tech for almost 20 years now. I currently work at Microsoft, working with a lot of customers. Small, what we call ISV partners and startups to help them move to the cloud, which is super exciting. I, as I mentioned, I yeah, I've been around tech for the last 20 years, mainly focused in Microsoft technologies. I started off as a .NET developer, working with a lot of large companies as a consultant, then I moved into SharePoint then I moved into Dynamics, then I moved back into .NET and mobile and yeah, and then back to cloud.

So yeah, I've I've kind of been on this crazy journey in tech. That's been super exciting. I've got to go all over the world. Of course, not anymore. But I've got to go all over the world and meet a lot of great people. So yeah, that's that's a little bit about me.

#### Jamie

That's, that's awesome. I've, you know, I I've not had the illustrious career that you've had. I've only really been in sort of professional in development for about 10, 11, 12 years. But I do feel as though SharePoint is a rite of passage for developers, right?

#### Labrina

It is. It is it's, it's, I feel like it was I, interestingly enough, it's learning SharePoint is really what I feel like really brought me out of my shell. Because SharePoint, it's such a, it's more such a collaborative and social technology. I got to it's when I first did my first talk, like the listeners can't see. But that's my SharePoint shirt. For the very first conference that I spoke at 10 years ago now. And yeah, just most of my good good friends, tech friends, I'll drop the tech part. They're just friends. They're my friends. I met through SharePoint. So yeah, I owe a lot. I owe a lot to .NET. But I probably owe a lot more to SharePoint. Actually. Surprisingly.

#### Jamie

I totally get it. Yeah, it's, it's one of those technologies that like you say, so collaborative, but then it's also really sort of extendable. And because it's .NET, all the way down. You could just be like, "yeah, I'll just write my maybe a C# or VB or whatever thing and it will be there. And everyone can use it. And it's relatively easy to maintain." I totally get it.

Yeah, like I say is definitely a rite of passage. For some developers. It's like, "Hey, I'll go all in and start using it for everything." And some developers is like, "Hey, we need someone to to create something for SharePoint." And it just it touches all of the .NET. I think, almost anyone in at least who has worked in like the windows side of .NET, they must have used SharePoint at some point, right?

#### Labrina

Yeah. Yeah. It's definitely a platform that gets everyone involved. So yeah. Yeah, that's absolutely right.

#### Jamie

Yeah. Unfortunately, we're not here to talk about SharePoint. But it is a wonderful story. But I mean, we get we just sit talk about SharePoint, my experience with it is a bit lacking, I have to say, I have written some things that run alongside it, and that sort of poke at some of the API's, but I've never really gone, "hey I'm gonna learn it and see what it's all of the details." But maybe that's another show.

#### Labrina

I don't Yeah, I'll come back. And we can we could do all SharePoint.

#### Jamie

Excellent. That sounds good. To me. That sounds good. To me. That's another episode that I don't have to do much effort for. That's why we have guests on our shows, you know, so we'd have to do anything.

#### Labrina

Happy to help.

#### Jamie

Thank you so much.

But yeah, so we're gonna be talking .NET and the cloud. And I'm very aware as we're recording. So we're recording this 19th of November 2020. .NET 5 has not very long, it's been out for about a week or two, I guess.

#### Labrina

A week old.

#### Jamie

Excellent. I mean, there have been the the release candidates, but this is like the official "Hey, it's .NET 5. It's here." Yeah. So I'm likely going say, and because obviously, because of the the time cast pod machine, wibbly, wobbliness. We're recording this in advance of time. So there's likely going to be times when I say, "hey, so when .NET Core is superseded by .NET 5," so please bear that in mind, everyone who's listening: we're recording this couple of months ahead of time. 

But, so, so first of all, before we talk about anything, right? You've said yourself, you've been in this this whole this industry for for almost 20 years, right? For me, um, you know, that's, that's, I mean, for anyone, that's a long time, right? That's, that's a whole bunch of innovation that has happened since then, like 20 years ago, we're talking about .NET was like an intranet based technology for inside of the business. And now, it runs a huge portion of the web, you've got Azure, I suppose Azure, I'm not sure how, what the official pronunciation is.

#### Labrina

There is no right or wrong way.

#### Jamie

Okay, so we've got Azure/Azure, that that whole thing, and that's, that's running .NET, presumably, or you can run your .NET thing on it. And we've gone from, like I said, we've gone from small web services to scaled micro services and video games and consoles, all running .NET, you can now run .NET a fridge, which is just blows my mind.

#### Labrina

I've got a, I've got a bunch of Raspberry Pi's somewhere around here that are controlling my that too. I just bought a house. So we're excited about, you know, making our whole house smart enabled. So I'm excited to start using .NET Core on a bunch of Raspberry Pi's and yeah, you know, controlling how long my stepdaughter gets to use the internet, so it's gonna be fun.

#### Jamie

Yeah, it's brilliant is one of these technologies that just scales almost everywhere. Are you talking about the Raspberry Pi. I've got one of Raspberry Pi 400, which is a Raspberry Pi inside of a keyboard - it's sort of one big full kit. And I've been using that to do all sorts of crazy .NET things over the past week. And I'm teaching my brother who's not a developer, to code with it. So I was like, "Hey, you come learn what I do." And it's just bring the keyboard and plug it in. Well I mean, he came over before the, before the unfortunnate-ness.

Over in the UK, we've had like a lockdown. So nobody can go anywhere. And so he came over a few days before that, and we couldn't get him home in time. So he's staying here for the duration. So by the time you're listening to this, hopefully he's gone home. But I thought to keep him busy, I'd like teach him to write some code is totally, totally doable, right?

#### Labrina

That's fine. That's fine.

#### Jamie

But then, so if we're looking at almost 20 years in the industry, what, in your opinion, some of these innovations that have really changed the game? I mean, we talked about SharePoint being collaborative, bringing everyone together. .NET clearly has changed a whole bunch of stuff. Is it purely a Microsoft thing that you're thinking? Or is it just a is a thing?

Unknown Speaker  
I think, um, for me, you know, I I love tech, but I also love the people in tech. And I think for me, what's what's what I've love, that's change is sort of how we work together.

#### Labrina

So I remember when I first started in tech, I started working for this, we built the first installation of, of this insurance company, all states, their first online web presence. So we built their first kind of web application. And that took hundreds and hundreds of people. And it was all these very, very, very siloed teams, right? There was a huge like team of like database administrators, I have no idea what they did, there was a huge infrastructure team. And I have no idea. I mean, I got a chance to, like talk to some of them. But there is a huge infrastructure team there is a huge DevOps - well, we call them the the build guys - but a huge build and DevOps team. And then there was all these teams that came together to build this amazing web application. But we were all really, really, really siloed I felt like and it was such a very everything was so very, very, very specialised.

Whereas you flash foward to today, and I feel like the development team, and, you know, infrastructure engineers and Site Reliability engineers. While yeah, there's different fancy titles for everyone. But that team's like, shrunk significantly. And, and, and, you know, we all work really, really well together, it's not kind of this, like, staunchy, kind of a, you know, separation of people, it's, it's a much more collaborative team, who work much closer together. Because I think the tools and the technologies have evolved in such a way that, you know, everyone can kind of, sort of work together much better. So, I think that part's been, you know, super, super exciting.

And because of that, we're able to get, you know, it's more satisfying, you can see applications getting released, you know, all the time. I mean, you get huge companies like Netflix, they're releasing features, like every day. So it's really exciting to see the pace and, and the change, you know, of how like software and how technology evolves. And then I also think, just the amount of information and you know, how to get involved in tech, it's come to a place where I'm excited that so many people - like you're just talking about your brother, you're literally just teaching him how to code. And so literally, you know, in a cup, you know, after lockdown, he can apply at Microsoft, and get a job.

#### Jamie

I'll tell him, "Labrina said apply to Microsoft."

#### Labrina

Exactly. So, but I love this, I love this I love you know, because of I came from, you know, I originally from Chicago, I came from, you know, modest, you know, modest family. And a lot of people around me are modest living and so I really love that, you know, technology has started to become a good equaliser providing a lot more people opportunities, to be able to code be able to change and then thereby, you know, getting great jobs, and then they're thereby kind of really changing their lives. So it's not, I love seeing, you know, really kind of technology for all and coding for all this whole push for that. That's what's really got me like, super excited about this industry now.

#### Jamie

That's, that's awesome. I have to agree. The, the just the ability for, for anyone, anyone to sort of pick up the knowledge and say, hey, I want to learn to do this, right? It may cost you the price of a book. But you know, the example that I get that I give I gave to my brother before we started dotnet stuff. It was let's do JavaScript, right? You've got a web browser, I've got a text editor, you have everything you need. Yeah, you've also got this guy sitting here, poking at you saying right? type it like this. And, oh, if you get stuck, you can go to Google and just type in how do I do this in JavaScript? There's all the information.

#### Labrina

I can litter I love. I love Twitter, like I literally can tweet, like who's done this? And, you know, I get 10 perfect strangers from all over the world that give me answers. So, yeah, it's amazing.

#### Jamie

It really is, it really is. And just that, like you said that democratising of the knowledge to the reducing that barrier to entry, right? I remember, when I did, I took Computer Science at university, in my own time as a kid that I was going to the library, get the book, learn our computer works. And I went through that, that I was lucky enough to go through that journey. But some people aren't Lucky, lucky enough to go through that journey. And and just being able to go, I want to learn to code, I'm going to hit google and type in how do I learn to code and all of that information is there, you don't have to go to university to have to buy the book starter. Because if you're lucky enough to have if you're fortunate enough to have a computer, you've got what you need. Let's get you started, you know, share that knowledge. Yeah. I think that it's, it's been a long time coming. I think that anyone can sort of join in and being able to I feel like there was a movement when I started back in you know, the early 2000s of let's try and help people get started but I think it's so much better now. So many people going hey, here's here's my experiences, and and let me try and like coach people And can I find an apprentice or something to give back? And yeah, back then that wasn't the case, it was felt very much like a, I have the prestige because I know how to do this. It's like, well, that's not what it's for, let's go and help someone else. And that's great. I absolutely love it. It really has to, to be able to see people just sort of appear and go. Like, when I was who was it, I was I. So before I became a professional, professional, because I'm not a professional, professional developer. Straight out of uni, there were no development jobs. And so I went in and started teaching, I was teaching at a school. And I used to do this, like Computer Club stuff. During lunch times, and after school, let's learn HTML. And, and I think, you know, just just, right, let's get your name on screen. And there's a website. And some of these, you know, 1112 year olds are going, Oh, my goodness, I've just, I've just literally made this, you know, and then we started messing with html5 canvases. I mean, we had to build up to it, like, but, hey, now you're moving something around on screen, and guess what it exists and go home, and you could do it on your computer, you know, you can just run it on it. And just that that moment of, wow, you see all these ideas for my let's do this creativity stuff. It's, it's, it's wonderful.

#### Labrina

Yeah, I mean, I'm super excited about that. I also do a lot of volunteer a lot with STEM organisations. So there's a couple here in the US, like black girls code that I volunteer a lot with, that teaches young girls seven to 17, about coding and equipping them for like, you know, jobs in STEM. And we I've been volunteering with this organisation for about four years now. And it's been super rewarding to see, you know, that very thing, like we have these day long sessions, where they'll do things like, you know, learn HTML and CSS or learn JavaScript. And it's been exciting to see like, you know, the enthusiasm and like, they're like, I can learn that. And even just, you know, listing, like some of the conversations that we have, you know, we were, we had a, we did a session around machine learning, like, where they kind of built a little facial recognition app, super kind of small, but the, you know, some of the questions that they were thinking about and around like ethical AI, and like, the these are, you know, middle, you know, 10 1112 year olds, and we're having this conversation, so I'm super excited about that. And then, you know, it was exciting. Last year, some of the girls were like, this HTML and CSS and JavaScript, that's so easy now, like, we want more challenging curriculum. And I mean, what an amazing problem to have. Right? So yeah, so we're looking at things like Python going forward and stuff like that. So it's like, it's very exciting to see that. So that's something that I'm definitely really passionate about is making sure that, you know, like, you're saying, like, the technology or learning to code isn't just for like, you know, the upper crust. But it's, it should be something that if you if you have that desire, if you have that passion, absolutely go for it.

#### Jamie

Yeah, absolutely. I agree completely. Because I feel like it's something that it's already touching everyone's lives anyway. You know, they're there, the streetlights, the ArrayList. There's cameras everywhere. But the streetlights, there's computers in your car, I'm wearing on my wrist, I've got, you know, there's a bunch of different devices around me. They're all there. They all run on software, let's make something right. And then yeah, these Raspberry Pi's Arduinos, all these kinds of things. Let's just make some little thing and just does this thing. And then you think you see, you see these creative little thoughts going on. Maybe it's maybe it's the ethics of ethical AI, maybe it's going to make this thing, draw a circle, whatever it is, you know, you see these things happening in these ideas, and, and then the people that you're talking to are able to then go in a completely different direction, the rest of their lives going, Hey, this is totally accessible to me. I can do this. I don't have to worry about it. Like you say it's only for the specific people or whatever, everyone can do it. Everyone should do it. And why not? Right. Excellent. We got a little bit of a tangent there, but I really like it. I really like it. And so so one of the things that I wanted to talk to you a little bit about is your because you work. I mean, you said yourself you work at Microsoft, do you part of the Let's Move everyone to the cloud, and you're a very big advocate for the cloud. All of my projects I do I throw, I literally go home, as you figure it out, like is my car to figure it out. And that's what I really like about when I'm using is your is just, hey, here's an app or an app service or a container, just, I don't have to worry about it. I didn't forget it. And it just the URL gets generated, all the network traffic is all figured out. For me. It's like DevOps on, like, turned up to 11. I don't know, but I don't have to do anything. I just go, go figure it out. Right. But I was wondering, you know, what's your, the advocacy that you bring for bringing people to the cloud was, without wanting to sound confrontational? What's so great about it, I feel so great about the show, what's so great about the cloud, is it literally literally what I've just said, there is it like,

#### Labrina

I think, I think for me, it in for a lot of organisations, it helps them focus on the things that they like to do, and that they're good at, right? I work, I really like my current job, where I'm working with a lot of startups and I and partners who have some amazing new, there's some really cool stuff that they're thinking about, and that's coming to bear. And so, but you know, if you imagine your startup, you know, your, your 10, your 20 people, right, and but you're all a bunch of developers, you know, working to build some really, really cool tech, well, you know, traditionally, if you in order to get that really cool tech out to your customers or out to the masses, you needed to hire a bunch of infrastructure, people who really understood servers and understood all of the networking and all of these capabilities. And, um, you know, when you're trying to move fast, that's not necessarily something they that you can do or at anytime, right, like, it gives. So I feel like moving to the cloud, you know, let let us let Microsoft Azure kind of handles some of those, you know, patching of virtual machines, and, and, you know, dealing with some of the security issues and, and all of those things, let us kind of handle that and, and let let you focus on the innovations and doing the coolest stuff. And we'll kind of do like in like, for me the cloud, like, you know, do the cloud does the grunt work, right? Like the the not so glamorous stuff. And then you can get to focus on, you know, innovating and building like cool stuff, right. So I think that's where I see a lot of my customers wanting to move to the cloud, because, you know, they're really good at the things that they do, right? They're not they like, they don't want to become networking and server, you know, networking and server experts, right, they want to be able to focus on their business and focus on the tech that they know. So I think that for me, I think that just, it just makes a lot of sense. And that respect, and it just allows you to just go faster, right? Like you're saying, like, I you know, all the time, like I build a quick application, I click a button. And you know, just as simple as that, especially when you're just trying to kind of, you know, the purpose of what I'm trying to do is just to prove, you know, if if I click that button, then a circle appears. I don't need to have I don't want to ask a question. You know, I don't want to have to deal with finding a server provisioning, setting up that server setting up the networking, like, I just want to be able to, like hate it my code work. Can you see my code on the other side? Can you see my code wherever you are? Okay, cool. So I think I think for me, that's where the cloud is so important, and Azure is so important.

#### Jamie

I completely agree. And it totally makes sense. One of the things that I did when we were in the blazer 0.3 timeframe. So it's just like the first public preview, I watched one of the talks with Steve Sanderson and when I got I got I get it, but I gotta say this. I was like, pull down the code, type some stuff. And I was like, oh, wow, there's some more stuff. And you know, 25 minutes later, I had a big video game fan, right. So 25 minutes later, I had a pokey dex, essentially, just a Pokemon thing. Completely in blazer. It was dotnet. from front to back. It wasn't my API was using the book. There's like an open source polka man API. And all I was doing was putting in HTTP requests, and then doing some JSON d serialising. But then it was doing blazer stuff to show dynamically show things screen and things like that. It was all completely dotnet. I was like, This is amazing. And I went, I can't send this to my brother because he doesn't know how to get it running. But I didn't have to because it was like, Okay. So you know, I know Docker, I know containers, I don't need to handle setting up a so I just go Hey, is your here's a Docker container. And then I go right click Copy URL, paste. Hey, Hey, Mark, how's my brother's name? Right? Hey, Mark, check this thing. I just built it now. He's like, Wow, what's this? This is a common API cover. And I said to him, yeah, you said, You computer guru on your phone is what, what? And he's got, you know, this pixel two, or whatever. It's like, Wow, it just just literally runs, you know, amazing stuff. And just being able to send that link around to whoever needs it. Without having to like you say, I don't have to provision a server didn't have to get an IP address, didn't have to worry about HTTPS certificates. didn't have to worry about DNS propagation. Because that happened. Like, in moments. I was like, Okay, I've got to wait two days for it. No, it's ACS live now? What? What?

#### Labrina

Awesome. That's awesome. love to talk offline. I'll have to get I didn't know that. They they had those API's? We'll have to. We'll have to chat offline about that. I am so excited. To hear more. Yeah.

#### Jamie

Yeah, definitely. Okay, so um, so it This may be a bit pulling the curtains back a little bit or talking a little bit too much about your job, please let me know if it is too much. But let's say someone comes to you and says, I think I need to move to the cloud. How do you how do you how do you figure out whether I need to move to the cloud or not? Like, I'm building some awesome stuff with this amazing app. And it's wonderful. It's maybe the maybe it's the not a hotdog app from Silicon Valley or something. Right? And I want to move it to the cloud. How do you know whether like, should I move it to quote? Do I have to move to the cloud? Or? Like, how do you figure that all of that stuff?

#### Labrina

Yeah, so I think for me, it's really about working with a customer understanding what their goals are, you know, making sure that it's not just a, because it's cool. Although it is that that isn't a great answer, but should not be the answer. And then also really understanding, you know, where they where they are in their understanding of cloud. Because there is there there is some, you know, new skills that, you know, your your team has to learn. And, you know, are you able to take that on? Do you have people that are interested in doing that are willing to do that? It's not unfortunately, you know, moving to the cloud, there's no easy button. I mean, sure, you can do some some quick prototyping and things like that, like we were talking about. Yeah, yeah, that's, like, totally, if I'm just building you know, something for for fun. But if you're, you know, running a, you know, some, you know, large application right there, there are some additional things that you need to think about. And so it's so those are the things that I really tried to kind of work with organisations on, on getting them really prepared for for the cloud. Because there there are some things

that you have to think about.

#### Jamie

I mean, that makes total sense. But what I'll say to you, librium, is I've just made my first app and I want a million users to use it, because I've heard Netflix runs in the cloud.

#### Labrina

That is, right. Yeah. Because Because school is always the right answer.

#### Jamie

Excellent. So then, I wonder if you could, you could maybe talk to us about some of the, you talk there about this, there's a bit of a learning curve. Or if I'm, let's say I'm used to doing, we don't tend to talk about it these days. But let's say I'm used to doing FTP, right click, create a zip file, go over and drop it into the server, and then just hope that it reboots and comes online, right? Or it's an IIS server and, you know, I'm swapping and I've got a right click Deploy, but they've got to put the right password in and someone has to come in and do a little dance to make it work because nobody really knows the actual process for actually deploying anything anymore. Because the person who used to deploy it left two years ago and didn't document it. So apart from things like that, you know, the the effectively the Brent in the Phoenix project sort of thing. Whatever are some of the most unique challenges you've seen people come to you with? Well, we can't we can't really put this on the cloud because the clouds are alien, and it's new and what Before but it's all alien. And we know we can't learn it because it must be complex. Right? So if you can, like, what are some of the most difficult challenges? I think

#### Labrina

they're Sure, absolutely. So there's, there's a couple of things that we should that we should think about. So one of the things that I know a lot of times people really just want to move to the cloud, because, you know, they're, they might want to get out of their existing data centres or things like that. And they, they move, they do what we call as a lift and shift, which means that, I'm just going to pick up my existing application that's running over here and either on premise or some other data centre, and I'm just going to put it in Azure, and run it on a VM there. And so, some of the so that's a lower degree of difficulty. But it's also less of a reward. With with running in the cloud, it's sort of like, so I'm going to, I've recently just bought a house, and I'm thinking about moving. So a lot of my analogies will be around that. So sort of like we called lift and shift, you know, when, when I'm trying to clean out my closet, I basically take all the clothes that are in one closet and put it in another closet without actually going through the effort of you know, saying that, like those bell bottoms that I had from, you know, 20 years ago, yeah, I probably don't need those anymore, or whatever. So, so that's so that's, so that's sort of the first thing. So I think that's a, that's a great approach. And that's a great first step for a lot of organisations, but you really don't get kind of the benefit of the cloud. It's good, and that, hey, we got our feet wet and learning about the cloud and understanding some of the things, but you're not going to achieve some of the cost savings and elasticity, and all of that good stuff in that manner. And so, at, but it makes sense, a lot of times for customers, because they do have code that's maybe, you know, little old has some interesting things. And I love when I'm on customer calls, and the first thing, they're like, you're not gonna believe this. And I'm like, I'll believe it. Like, you know, we were doing this, you know, or something's. So, you know, as I said, the cloud, if you move more into what's called Platform as a Service, where there's even a higher level of management, that the cloud gives you. Why that, that allows you to get more savings, more or less density or scalability, you're even less than like managing. But because of that, there's less things that, you know, we allow you to touch right, so you're not able to, we sort of abstract away the VMs. Right, so let's say you're deploying, just, you know, your standard your Pokemon application and to into app service, which is platform as a service. That's great. But let's say you also wanted to interact, interact with the file system, because you're saving things straight to the files, the file system will a traditional app service that in an app service, you can't really do that, because we sort of because we might move your round, actually, in VMs, like behind the scenes, you don't really know and you don't really have access to that stuff. So there's a lot of a lot of rules. Not a lot, but there's some rules like right, like, if if we're providing all this management capabilities, there's some things that maybe now you have to not do. So sometimes you have to re architect or make some subtle changes to your application. But like sometimes a lot of organisations, it's a good time to do that. But there's also effort in doing that, right. So, you know, it's a good time again, right? Like, I'm moving now. So this gives me an opportunity to look at, do I really need those? Do I really need those plates that I got from McDonald's? Yeah, they looked cool. But can I really get rid of it? Or could I really change these things out? So when you're also moving to the cloud, it gives you an opportunity to start, you know, gives you a fresh pair of eyes to start looking at your application looking at how you can you know achieve

You know, more scalability, more flexibility. So those are all things that I think a lot of organisations kind of start should start thinking about when when moving to the cloud.

### Sponsor Message

I'd like to take a moment to tell you that this episode is sponsored by Datadog. Also stick around for the next 30 seconds to find out how you can get a free t-shirt!

Datadog are a monitoring and analytics platform which monitor your infrastructure, application performance, and log management.

Are you looking to move to the cloud, microservices, or .NET Core? Datadog can help with that. Their distributed tracing and APM provide end-to-end visibility into requests wherever they go. Whether it's across hosts, containers, or service boundaries.

See for yourself! Start a 14-day trial today, and Datadog will send you a free t-shirt!

Find out more at {{< sponsor-link link-text="datadoghq.com/dotnetcore" link="https://datadoghq.com/dotnetcore" >}} - that's {{< sponsor-link link-text="datadoghq.com/dotnetcore" link="https://datadoghq.com/dotnetcore" >}} - or check the show notes for a link.

---

#### Jamie

I mean, that makes sense, right? Because like in, in development, we talk about sort of abstracting things away and single responsibility, right. So if the thing which runs your app, and it's all it's doing is running your app that has the responsibility of running your app, if you want to store some files, go store them in a file storage, right? Because I know that there's file storage and blob storage and all these kinds of different storage options, right? So that has the responsibility of looking after your file storage of that you want to SQL Server, I guess you go to the SQL Server bit that has the single responsibility of looking after your your database, right, you don't want to throw it all in one place. I do know that from my own past experience, some of my apps before I moved them to a cloud, everything was on that. So we got is on there. We got node on there, we've got the Redis caches on there, the the SQL Server database was on there. We got the file storage on there. And I'm like, that's great. But okay, watch this, and a pull Ethernet cable out. And I'm like, That's brilliant. drops dead.

#### Labrina

in one basket. Yeah. And and, and like I said, I mean, sometimes you just gotta move sometimes their customers and they, they choose to just move it there for that bit of time. And it makes sense. Because there's some learnings from just, you know, moving your application as it is to the cloud. But yeah, you definitely want to start thinking about how you could modernise it, and really make it more of a cloud native solution.

#### Jamie

Sure, yeah. And that makes sense. Because I've, I've always, apart apart from on my actual computers, any file system that I interact with, I'm always thinking, well, this is, this isn't going to be around forever, I need to get the files off of here, right. And the same thing with we talked about the same thing in like containers, you containerize your app, the file system is never going to be there. Because the the instance of that container can go down and come straight back up. And all the files you just wrote. And exactly right. But I guess because for the longest time, as developers, we've always had that permanent storage on that server, we have to learn a few things. And maybe, just just maybe just move it over here and move it over there. And if it's, I feel like if it's on the same service, like we talked a lot about Azure, but let's, let's just say, you know, there is AWS and GCP, and all those others. But let's say you're storing it all on one service, not a server, then maybe they're in the same data centre, maybe they're on the same machine, I don't know. But the communications between them will feel like they are right, it's not like you're going from the data centre in, I'm just going to pick some cities, right? It's not like you're going from the data centre in Dallas, all the way to the data centre in Tokyo, just to get your files the the quote literally next to each other. So you're not going to feel the hit, it feels like it's right next to each other, it feels like it's on that desk. It's just you making an API call, but it's on the desk.

#### Labrina

Still the the I think a lot of times people feel like oh, there's gonna be this to your point, just latency, these huge latency issues between communications. And yeah, the there the there's all kinds of the data centres that are close enough. And the the racks and things are close enough where that's not going to be an issue. And again, there's other things where within the cloud, all of the disaster recovery, and backups, and all those things that need to happen to work taking care of that for you, right. So like, for example, if you upload a file and to Blob Storage, we're making three copies of that for you. Just in case like something happens like So to your point when you're on prim are three copies of your, of your file system when you uploaded it. And I upload a file from your IIS web or IIS server into your file system No. So that there's a lot more, you know, kinds of there are experts that have really thought about latency and disaster recovery and resiliency, much, much more deeply than probably, you know, a mere mortal like myself. So yeah, absolutely.

#### Jamie

Yeah. And that totally makes sense. Like, I do remember very, very early in my career, I was doing something. I left a transaction open on SQL Server And just doing that, right? that nothing can happen on your SQL Server. And then then I came back the next day was like, I was supposed to schedule a backup last night. And it didn't work because I left the transaction open. And then someone unplugged the server, and then the spinning disk it was on died, and I've lost it all. And it's like, 24 hours of records gone. Right? Yeah. And, and, and even if you had a backup system, in that, in that example, because I left the hanging transaction, the backup system never happened. To me, all of these moving parts and they're all broken. And, you know, you don't have to if, if, if you're already visa providers are taking that money backwards for you. You don't have to right? Yeah,

#### Labrina

absolutely. Yeah, definitely.

#### Jamie

Yeah, I like it. Um, so then, um, okay, so I, I'm, I'm a solo developer. Let's say I work as a single but I'm working on my world by epoch shattering app, right? It may be the Pokemon app, it may be. Is it a hot dog? Is it not a hot dog app? Or maybe it's something that will genuinely change the world for the better. And I'm going right, okay, I've got my app. It's running. I've got my whole stack running on my machine or machines. I've got my mobile app ready. I've got, you know, the the desktop client ready, I've got it all ready. And I want to I want to move it to the cloud. Do I need to? How do I figure out which resources within as your, I need to use, right? Because let's say I've got a couple a couple of servers, I got a cache, you're gonna know a whole book, let's play buzzword bingo, right? We've got microservices, we've got Bitcoin, we've got Redis, we've got SQL Server, you know, we've got Xamarin, we've got all these different myriad different things. They're all glued together, and I have to run a script on my computer to set the whole thing up. Because it's so complicated. Yeah, how do I know which which resources in Azure? My bit my bits of infrastructure will slot into? Is that a case of just read through the documentation? And three days later, you just get it? Or is it get in touch with someone like LeBron and say, Hey, oh, I don't know how, what's the what's the process?

#### Labrina

Yeah, so I would say there's a couple of different resources, I would definitely go out to aka aka.ms, slash learn. And there's a tonne of learn modules, there's, there's a couple of really good ones that sort of bridge the gap, right? So I'm a dotnet developer, and I want to deploy my deployment application onto Azure, right? So there's some really good learn module that sort of systematically take you through, building out, you know how so first you start with, there's a sample application that you traditionally might build that you know, about, right, I've got a dotnet web application, I've got an API, I've got SQL Server, and some cash and Redis Cache, right. So I know how to build that on my laptop. That's totally fine. And so what I like about those learn modules is that it takes you through Now, how do I systematically deploy that to Azure, right? So first, I've got to set up an app service and and then deploy my, my web app there. And then how do I set up Azure SQL and deploy my SQL database there. So it sort of those are sort of really good ways, I think to I think those are really good ways to sort of like learn by doing right. And then it kind of been that that sort of helps you build a foundation, or a same way, like, if you want to, if you know, like, I want to containerize my application, alright, same, same scenario, but I've decided to containerize it for whatever reason. Same, there's a similar module that will take you through the same steps. So I kind of I kind of, like that approach. And then once you sort of get that foundation under your belt, and you can kind of start exploring the documents, you know, because you've got a good, you get you got your foundation, right. So I think that that's a really, really, really good approach to kind of get getting started.

#### Jamie

Okay. I mean, yeah, it's much better than sitting in just reading the documentation. Yeah, I mean, more power to you, if you if you can learn really deep knowledge just by reading documentation. But I've always found that a worked example or something that, hey, I've got, maybe I've got multiple screens, I've got the video over here with you know, someone from the dotnet team or someone from from the Azure team or someone from Microsoft talking me through it. And I've got my ID over here. PowerShell. And a couple of things I'm like, Alright, okay, so I typed this here. Oh, there it is. It's running. I've got the URL. Yeah. I like that.

#### Labrina

Yeah. And like and, and they could build on each other. Right. So now I've got my, I've got my application running, but I manually deployed that. So now my next step is like, how do I actually get build some, like build automation into it so that when I check in my like, because I'm a developer, I know about checking in code, I know about pull requests, and you know, code reviews, I know how to do that. But then how do I make it so that now I have some automation? So I think it's just like, sort of taking those steps that you do as a developer, and then sort of making the dotted lines to Okay, now, how do I deploy this in Azure? Or how do I deploy this to the clouds?

#### Jamie

Sure, sure. I mean, yeah, the the. So for myself, I just finished a project where I was building something with it was dotnet, core API, React front end, and a bit of Python. behind that, and some, some networking and some Docker, and so all sorts of stuff. And I do know, it was we hosted the code in GitHub. So the private repository hosted and get up and we had to get up action. Soon as I committed anything to one of the branches, it would build a, like it was using GitHub actions, it would build everything for me, and then throw it out to to Azure, and then it would come back with a URL and say, Hey, here's your test URL. And it will only exist for for the next maybe 15 minutes or so because I have a cron job that will then go through and there was like a regex for, for the test URLs, and it would just wipe them out. I could have done that better with like, the deployment slots. But you know, this was throwing something together really quickly. And it wasn't brilliant. But yeah, so you had this this play area you could play with for 15 minutes to make sure it worked. And then you can then spin that back up on demand. So when it came around to code reviews, if there's something wasn't brilliant, you could say, well go check this out. And, and, and that kind of helps, because there was a little bit of a learning curve involved in that. But that would have been something I'd have done locally anyway. Because we have their view at, you know, all these different environments, and staging and all that kind of stuff. And it's just, I feel, at least from my point of view, it was taking the knowledge that I already had in disparate parts, and just going Oh, so this is how you do it with this, or this is how you do it with, you know, as they go, Well, I already know how to duck rice things. And you know how to spin up an environment on my local machine. So how do we do it over there using some API? Or how do we do it over there using some, some function or something. And that's, it feels like that's very much that we already have the Lego pieces, right? We just need the blueprint for sticking it together.

#### Labrina

Yeah, and I think it's exciting because I think it sort of, it gives you a lot more control as a developer, to be able to do that, like I like I remember, actually, the reason why I learned Azure, actually, really, almost, when it started, like 2010 was because back in the day, if you needed a virtual machine from someone, you had to you know, you know, surrender your firstborn child or something to get a virtual machine, and I was like ham, I'm writing some code and building some stuff, I just want to play around with it. And I need to show it to customers. So I can't just, you know, be running only on my laptop. And I was like, Oh, yeah, Could someone you know, provision a virtual machine and, you know, you get the form from the IT person that's like, you know, why do you need this? How are you going to have it for Where's your firstborn child, or kidney or lung that you'd have to give? And, you know, and I, you know, and of course, the I wasn't willing to do that. So the IT person was like, no, we're not gonna give you a virtual machine. And that was when I actually started learning about the cloud about Azure. And back then it was web roles and things like that. But so you know, and it was awesome. Like I was able to, I built this kind of cool application that I wrote, and I was able to deploy it and sort of teach myself that way. So same way that I sort of taught you but it is it is really exciting because there again, that's like sort of removing that barrier from developers and in giving you kind of more control, which is cool.

#### Jamie

Show I have said it's something quite similar. I said I A 24 hour hackathon. And I was, this is many, many years ago and I'd taken my MacBook Air because I was like, I'm going to be there, we're going to take it to and from where I'm staying, wanted to be small, portable light last a while, and that sort of fit that bill at the time. And I got there. And I said, Okay, what are we going to do team? And they went real? Well, we're going to build something with dotnet. framework, or No, okay. And it's going to run on Windows, you're gonna go get parallels installed and surrender all of my harddrive space. And I am Dennard for maybe 1015 minutes, but how it was gonna actually help the team out because at that point, I was like, I can't, it's got it's, it's an error, and it's got 128 gigs of harddrive space. When installing everything on top of it, it's not gonna work. And then I thought to myself, Oh, God, I have as your and I have as your credits. And I have, wait a minute, did you VMs in the cloud VMs with Visual Studio installed on the cloud, and I have a working Wi Fi. So I just went, you know what, I'll take the hit, I spin up a VM in the cloud, installed, Visual Studio installed all the tools. And I had, effectively I mean, it would have cost me if I'd have tried this out. But I had effectively infinite harddrive space, infinite CPU power, infinite RAM, as long as I had that, that internet connection, and most of the build was being done on the build server anyway. So I was like, hey, I've got this Windows VM for 24 hours for this hackathon. I need this. I don't even need a very powerful machine. And I've done it with, with some of my customers before we've brought in designers. And they've been Oh, I forgot to bring my work laptop or whatever my superduper powerful machine that I need to use with Photoshop, but I've got the resources with me and I'll go, okay, where's your machine? Is your VM with, with, with Photoshop installed? You have to put your own licence key in it. I'm not gonna give you a licence key. But hey, there it is. Oh, brilliant. I could just do the work here. Wonderful. All right. Yeah. And that was my gateway into Azure was, hey, I need a VM for 24 hours to do development on. And awesome. Yeah. So then, um, so we're talking. Like I said earlier, at the beginning of the episode, we're talking a week into dotnet. Five, and my provisional plan, but this puts this episode coming out in February of 2021. I think I've got 2020 in the in the notes that. So yeah, a little bit of insider baseball folks, I send, we communicate a little bit and build up an idea of what we're going to talk about nice at this episode's coming out in February 2020. So somehow, I'm going back further into the past. Time. Yeah. But we're a week into dotnet. Five. And you've said yourself, you're a dotnet developer. And I'd love to know, what what is the one feature or the small list of features that are coming in dotnet, five, that folks have had a chance to use for months now. But I haven't had a chance to because it's only been out for a week? What's, uh, do you have a number one feature that you really are excited about? Or is it just a case of, Hey, this is just brilliant, because it just works and is wonderful.

#### Labrina

I think there's a, there's a couple. So one is definitely top level programmes. So really, that gives you the opportunity to start just writing without all the ceremony of, you know, building out typing, you know, building out a function and, or a method, like main and all that I can just start writing code, which I mean, I think one of the things, a lot of the developers now, appreciate that, like, that's, that's, that's how that's how developers start. Right? That's been a long time complaint with dotnet is that, you know, there's so much boilerplate, there's so much ceremony that gets getting started. And, you know, other languages like Python, you know, I just start typing and things magically happen, right? So, you know, I, I'm excited for that. And then also Records, which is really, really, really huge game changer, in terms of being able to build things and make them immutable building objects and making them immutable, really. So those are kind of my two favourites. I think kind of under the covers, there's been a lot of work to help with performance with reducing like, the overall sort of size of You know what, you know, when you hit build like out everything that's good, gets out credit like that, reducing that overall kind of size. So I think in terms of those things, that's that's also really really huge. And yeah, so So generally I'm I'm excited about those things. I'm also excited that we now just have dotnet, five, and next year it will be dotnet, six, and, and so on and so forth. And the year after that will be dotnet. Seven. And we can look for a release every year. So November 2021, will be dotnet, six, November 2022 will be dot that seven. And there's no more that, is it that net framework or is it dotnet? core? Or is it this? Like we have one naming convention, we have one thing because I think if if I had a top one question that I got asked, or that I get asked is, should I learn dotnet framework? Or should I learn dotnet? core? And what's the difference? And what does that mean? And so I'm excited from sort of that position that personally, I will no longer get asked that I no longer have to get asked that question of what's the difference between all these different versions or iterations of dotnet? So to solve one thing, so yeah, that's exciting. I have

#### Jamie

to say, in some of the circles that I travel in, not necessarily the technology related ones, where people have heard of the different programming technologies, but they're not really, Oh, I know, the name Java, I know the name dotnet. I know the name, Python, you know, they know that these things exist. And they for a long time, they've always known dotnet is Windows is windows with a Windows thing and it does the windows stuff. And then when I come to them, and they say, hey, what you've been doing dotnet on your Linux machine for two years, how does that work? Let me tell you about this. Right. Let me tell you, dotnet, core dotnet, five, dotnet. Six is wonderful. You can run it anywhere. And like I said at the top of the show, I could run it on a fridge. And that's a wonderful. He runs everywhere.

#### Labrina

Yeah, that's exciting. I actually have a machine. I'm starting to understand I'm actually beginning to be on Linux convert. So I actually see what everyone's been talking about all these years. I've got a machine. That's totally Linux, I've got Visual Studio running on it. So yeah, I can do all my development there. no distractions. I'm super quick. So yeah, it's, it's, it's it's definitely exciting.

#### Jamie

I've always been of the opinion that, hey, if using this tool makes you super productive, and you're good at and using it, and it gets the job done. Use it. Yep. So you know, if somebody says to me, oh, you should use Windows for this, or you should use Mac for that. And I'm like, well, which Am I better? I'm better at using Windows for this task, and maybe Linux for this task, and maybe Mac OS for that task. Let me do it my way. I know we'll get it done. I'll get it done faster. Let's not, let's not get the I know that they used to be a phrase of people used to use the word evangelical about it, and not worried about the connotations of that word. But let's, let's not, let's not get angry about why aren't you using this technology? Well, you know, I'm using the technology that I'm using, because I'm good at using that one. Let's just do that. Because that gets the job done. Right. And, and I do feel though, as though, for the majority of dotnet developers, learning another operating system over other learning a prism other than Windows might be required from now on, because it's like, yeah, you can you can run just on Windows. But some of your some of your, your customers may not be running Windows anymore, because it now runs everywhere. It doesn't mean you have to go out and buy a fridge specifically. So you can run your app to test it though. But maybe you should write. I don't know. It's exciting.

#### Labrina

Yeah, it's exciting. I think it just again, like Harry talking, it just brings everyone into the fold, right? Like now, you know, whatever, whatever kind of laptop, whatever kind of system you want to run with. run with it. And you know, you know, come like come one come off. So.

#### Jamie

Exactly. Exactly. So I'm back. So what we'll do some wrap up questions, if that's all right, LeBron it is. So how do people keep up with some of the things you're up to the work that you're doing? They want to learn a little bit more about the cloud stuff? How do they How do they figure that out? Is it just, Hey, I'll just shut up somewhere on Twitter and the reader will just magically appear what's the what's the process? Yeah, typically,

#### Labrina

the I'm pretty active on Twitter, so you can catch me on Twitter. I'm at chicks ch i X can code So chicks can code. And I tweet about Azure a lot and dotnet a lot. Unfortunately, it's American football season. So on Sundays, I also tweet about American football a lot. So if you're if that's not your thing, probably don't don't look at my feet on Sundays, but the rest of the week is totally fine. So yeah, absolutely. And yeah, so soon, coming. I got some more media, YouTube videos coming soon. But if you follow me on Twitter, you can learn more about that.

#### Jamie

Okay, excellent. And then would you say then, the learning a bit about migrating to the cloud was that aka, aka ms slash learn URL that you gave out earlier?

#### Labrina

Correct? Yes, I would say that is a great, that is a great starting point for really a lot of different training. Like if you're, you know, wanting to just, you know, nothing about machine learning, and you just want to learn, you know, how to spell it. And just like, learn it peripherally. That's a great, great, great place for kind of learning a lot of different things. But definitely, if you're, if you're new to the cloud, I would definitely suggest going out to aka.ms slash learn.

#### Jamie

Okay, excellent. I do have to say that the idea of learning, machine learning, right, when I was at university, artificial intelligence, and machine learning was something that you had to choose to do. Right, which meant you had to be at the university to learn it. Right. Whereas now, I just got to go on YouTube, what is machine learning? And there it is, but democratising all of that information? I absolutely love it. Let's get more people involved. Right. Absolutely. Excellent. Okay, so we talked a little bit about, I think we did it off air. But you we talked a little bit about the disrupting the cloud. And other you you're on a hiatus for a little while you're planning on coming back, it was a little bit about that, maybe we can get some more. I don't think that that maybe they maybe the audience for my show isn't as big as the audience feels. But maybe because of course.

#### Labrina

So, so I had this vision a few months ago, actually, more than a few months ago, about being able to show different voices and faces that are in cloud technologies and in the hopes to, again, getting get more people involved in doing cloud, perhaps as a career, we've definitely seen the growth of you know, through so many programmes and things are for coding. So I would love to see, I had this kind of idea of building, building a pod creating a podcast that showcased, you know, different, you know, people from very different different walks of life, you know, really focused on people of colour, and women who are in the industry coming together and talking about their journey. And cloud, be it that, you know, you're kind of a cloud newbie that's starting, or if you're like, you know, an old, an old person like me, who's been around for a while. So that's what disrupting the cloud is all about. So we had a couple of episodes. We did a couple episodes at the beginning of the a couple months ago. And the response was really, really great. had to take a little bit of a break, but we're starting fresh again in January. So again, you can also follow at disrupting the cloud or at disrupt the cloud. To catch us catch up. More on that too.

#### Jamie

Awesome. Well, yeah, like I say, I can't say that. The audience for the dotnet core podcast is huge. But if a couple of people go over, there's one or two people extra. I don't know. I'd love it. Yeah, right. Let's talk about the cloud. Absolutely. Excellent. Okay. Well, all it really remains to say their brilliance. Thank you ever so much for spending your afternoon, talking to me about the about as you're in dotnet, and the cloud and all of these wonderful things, the places you can go to learn stuff I got. It is genuinely been a pleasure. And I have had loads of fun, and I'm going to go do some more as your stuff. I'm going to go learn. Tomorrow's your stuff, because there's always something new to learn, right?

#### Labrina

Absolutely. Absolutely. So up there. Yeah. And definitely reach out to me You have my number and my address if you need any more help. I'm happy to help.

#### Jamie

Excellent. I'll to obviously, send you the link to the pokemon API as well. Yes,

#### Labrina

yes, definitely want to get that.

#### Jamie

Excellent. Well, thank you so much Sabrina. It's been wonderful. Thank you.

{{< paracentre "The above is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

### Wrapping Up

That was my interview with Labrina Loving. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/), and there will be a link directly to them in your podcatcher.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice - head over to [dotnetcore.show/subscribe](/subscribe) for ways to do that - and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Labrina on Twitter](https://twitter.com/chixcancode)
- [Pokemon API](https://pokeapi.co/)
- [Pokeblazor](https://github.com/gaprogman/pokeblazor)
- [Disrupting the Cloud on Twitter](https://twitter.com/disruptthecloud)
- [Disrupting the Cloud linktree](https://linktr.ee/disruptingthecloud)
