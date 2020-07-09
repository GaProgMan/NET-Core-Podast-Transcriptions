# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is episode 48: Rockstar With Dylan Beatie. In this episode I interviewed Dylan about [Rockstar](https://codewithrockstar.com/), but we also talked about whether the work that we do as software engineers, coders, programmers - whatever you want to call yourself - whether it should be treated like engineering and have a code of standards and ethics. We also talked about code as art vs code as science.

This was an incredibly engrossing conversation about some of the topics that we don't usually talk about in our field, and I'm sure that you're going to love it.

One thing to note: this episode was recorded at NDC London 2020, as such the audio is a little less polished than I would have liked, and is a little rough at times but that was entirely down to my post production skills. Remember that the full transcription is available at the website, which is available at [dotnetcore.show](dotnetcore.show). The transcription was produced in collaboration with {{< sponsor-link link-text="Productivity in Tech" link="https://productivityintech.com/dotnetcore" >}}.

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Interview wth Dylan

#### Jamie

first thing I'd like to say Thank you ever so much for spending some time.

Thanks very much for having me.

It's Ah, my first time at NDC. and I can understand that it's very, very busy. I think everybody's got their five talks every hour. There's lots of things going on, lots of new things to learn and lots of people to meet and talk to you. So

#### Dylan

the thing that you sort of figure out fairly quickly with an event like like an ideal lots of conferences, big ones, small ones, little community events, And, when it's your kind of first time you're looking at the program and thinking, I want to see all these talks on that one clashes with that. One of the clashes with that one. And actually there's no way of single of it, like completely forget. Whatever it is that you choose to do, there's gonna be an entire track of stuff that you'll regret not seeing. But you know, one, a lot of the talks NDC does a great job on recording, and everything will be on the Internet eventually. So the talks he didn't see you can watch them later on YouTube. But the things people really remember and this is something I found lots of people said to me is you don't remember necessarily the talks you went to. You remember the people you spoke to, the conversations you had? You know that the ideas and those kinds of things. And so if there's ever a choice between, like having an interesting conversation with somebody, or trying to figure out which talked to go to, you go for the conversation because the conversations where the ideas kind of germinates, you know, business partnerships are born open source projects get started and you know, all that kind of stuff. You know, I love watching speakers. I love presenting. I really enjoy the format. But you know, that kind of stuff. There are ways of picking up on that later. If you didn't get to see it whereas conversations, if you miss the opportunity to do that, you can't do that later on YouTube.

#### Jamie

Absolutely. I brought in my friend Alan [Underwood] just now you to introduce him to you because you know that's a connection. Maybe he can talk to you about something. Maybe you could talk to him about something. I'll admit to having sort of wide eyed, starry eyed Sunday afternoon walking around in the hotel going or my goodness, there's Dylan Beattie. There's Troy Hunt has got a note from Call Franklin and that made my day. I was like, Holy cow! I didn't even say hello. He just nodded at me.

#### Jamie

Good. Let's go have a lay down.

#### Dylan

You know, there's this wonderful anecdote from Duff McKagan, the bass player with Guns N Roses. His autobiography is a wonderful book on. And there's this this bit at the end? The kind of story of his life. After Guns and Roses kind of sold millions of records, he discovered he had no money because of your record company accounting in this kind of stuff. So he went back to school. He went to college to study business and, you know, he wrote magazine columns and stuff. But there's this lovely.. he ends the book with.

#### Dylan

They've just come off stage doing a concert in South America, and there's, you know, fans lining the streets back to his hotel shouting Duff Duff Duff and he gets into the hotel and they're like, there's a message for you and It's his college professor, and he calls him back and goes, You know, Hello, It's it's Duff McKagan and the professors goes, "sorry, who" and he like "I'm in your  business finance class." Oh, yeah, I remember. I love that because it establishes, you know, context within a certain kind of nature bubble. You can be really, really well known. And people kind of...

#### Dylan

everyone in technology I've ever met is lovely, you know, just cause someone's got a podcast or they got their own blawg or I mean, you know, Troy Hunt's kind of different because. He gets called on mainstream TV, and he's like testified before Congress stuff. So it's probably somebody might get recognized, even if you're not part of our little echo chamber.

#### Dylan

But the rest of us, just the same as everyone else. We're just a little bit louder.

#### Jamie

That's it right and I'm sure the same thing happens at other conferences for, say, business conferences. So music conferences or

#### Jamie

what are they called, A&R conferences, you know? "Oh, my goodness. It's that person" Oh, my goodness is that person.

#### Dylan

I got invited to keynote at Flutter Europe last weekend in Warsaw,

#### Dylan

which was great, but it's ah a completely different set of people to kind of the NDC familiar faces and the regulars and everything. And it was kind of interesting because, you know, for the first time a long while I turned up to a conference where, unfamiliar with the technology stack because I've not really used flutter very much at all on. I didn't know anybody there, and they had no idea who I was.

#### Dylan

And, you know, I saw you kind of like All right, let's have a drink and talk to strangers and try and

#### Dylan

figure this out and make some friends and have some conversations on. But it's kind of weird because the first time everybody does it, it's always like That's like "everybody here knows each other on and I don't know anybody and I don't fit in. And I'm gonna go hide in my hotel". And then you realize nobody knows each other? They're just, they've figured that out already,

#### Dylan

but anyway,

#### Jamie

yes, right. We've talked about this wonderful stuff for about five minutes now. Haven't even introduced you. So uh, yeah, like I said, thank you ever so much for taking the time. And was really Could you give us a brief introduction, to some of the work. You do it especially [Rockstar](https://codewithrockstar.com/) and The Linebackers and things like that.

#### Dylan

So yeah, I'm Dylan Beattie, and as of today, I am an independent software consultant. I literally just before I did this tweeted at my new company, which is called [Ursatile](https://ursatile.com/). Just like [the bear](https://en.wikipedia.org/wiki/Ursa).

#### Dylan

Independent Software Training and Consultancy and that kind of thing. So I'm gonna plug that now because I need clients so get in touch. [Ursatile.com](https://ursatile.com/). And we can work together and stuff. I've also been building websites since the thing I built my first Webpage In 1992 which was about a year after, like HTML 1.0 was drafted as a specification. I started building data driven Web applications, you classic ASP, running off access databases way back in the late 1990's. Been building websites ever since. Websites that kind of grew and grew until I was hiring teams and studying distributed systems and software architectural and these kinds of ideas. And Yeah, over the last sort of five years or so, I've been speaking at conferences, meetups, doing more and more stuff with community. Training, teaching, you know the strap line I have on [my website](https://dylanbeattie.net/) is "I do interesting things with computers, video music and comedy. And I traveled all over the world to talk to people about it, which kind of sums it up. So I love nerdy things I love. I love using technology for unintended purposes and seeing what you can make it do.

#### Jamie

exactly. I think I was talking to Clifford [Agius] earlier on today. You know, we were talking about think people like himself. He's making the IOD hand for the young gentleman who has, unfortunately not got a left hand. And they were talking about [Scott Hanselman](https://twitter.com/shanselman), whose diabetes and he's open sourced that is like using the domain knowledge and the expertise that we have to try and solve the problems we see around us. And that's amazing that we can do that.

#### Dylan

I think you know some of the most compelling solutions that technology has created because somebody who understands the capability, you know, the constraints around that technology is trying to solve a problem, that they care about the solution. They don't care about the paycheck or the kudos or whatever. They're doing it because they want this thing solved. There's a fantastic book about the development of the iPhone, which the format is wonderful. It kind of alternates how they develop the device with the supply chain for the current manufacturing process, which is really, really interesting. But basically, you know that the iPhone story has it. It's the phone Steve Jobs wanted because he didn't like any of the other ones and you know he's somebody obviously understood technology and everything. And there were entire teams at Apple. You know, Steve, Steve Jobs was this famously mercurial personality. If you caught him on a bad day, it could end very badly for you. And so they got all these teams working on things like multi-touch displays and, you know, touch screens and this kind of stuff. Like, When do we tell Steve? If we tell him too early before it's ready, he'll fire us over wasting his time. If we leave it too late, he'll fire us often, not telling him earlier. And so they have teams where somebody's job was to talk to Steve every morning and find out what mood is here on. Go back to today's the day we're gonna show Steve jobs multi-touch this afternoon, so they have demos ready to go every single day. But, you know, the first iPhone was Steve Jobs going? I want to build a phone that as a business person and an entrepreneur, I want the phone that I wish I had on doing the same with that whole kind of apples renaissance in the 90s and early 2000s. IPhone iPod, the kind of rebooted iMac, the operating system Mac OS X and stuff

#### Dylan

You know, I think some of the best software that exists is people who are really good at developing building the application they want to use. You look at some developer tools like [Visual Studio Code](https://code.visualstudio.com/) is built by developers using [Visual Studio Code](https://github.com/Microsoft/vscode/), and if something doesn't work for them, they fix it and they push it and it happens on some of my favorite games back in the days when tiny teams were building [Doom](https://en.wikipedia.org/wiki/Doom_(1993_video_game)) and [Quake](https://en.wikipedia.org/wiki/Quake_(video_game)) kind of things. Those folks were building the games they wanted to play,

#### Dylan

and then it was like, all right, we're happy with it. Maybe somebody else will like this. And of course, it was a massive success Yeah. You know, I think that you mentioned Scott Handsome man. His talk about [open-source diabetes](https://www.youtube.com/watch?v=uNhYhlBQoEY) is it's absolutely fascinating. I saw him do it at a dev summit in Stockholm last year. And, you know, it's eye opening to realize this kind of all this technology that is amazing. But none of it is officially good enough to use for anything medical cause. They're like, Well, it's amazing revolutionary smartphone, but I don't trust your life with it. It might crash any moment for no reason.

#### Dylan

But who decides whether it's worth the risk, you know, is that they do we allow the individuals to do that? Is that a certification thing? Is that, you know, some kind of medical board? Is that government legislation? You know, if you want to trust your iPhone to tell you whether your pancreas is working properly that day, who decides whether you are allowed to do that or not. And that's really, really interesting stuff.

#### Jamie

it fits, a bit off topic, but (Dylan: It's a podcast)

#### Jamie

I'll just put it out. But it kind of fits well with the key note that I don't know whether you're in the keynote on top of the key. No, I just watch was basically ethics, and they'll be saying to a few people so far, you know, that talk really sort of reinforces this idea that maybe we should have the _Hippocratic Oath for development_. Is this going to do harm, or can I put something in place that will stop it from doing home or say I'm developing a system that catalogs people and segregates them by some measure, does that have the capacity to do harm? Their quote that that was put up there was about the engineer of the rockets for Second World War Germany.

#### Jamie

That engineer was saying, I'm sending rockets to the moon, but they landed in London, you know. Where do you draw that line? You know,

#### Dylan

[Wernher] von Braun wasn't it? You know, V2 was a good rocket it just landed on the wrong planet.

#### Jamie

Exactly. Right.

#### Dylan

Andi, I don't If you saw the [For all mankind series](https://en.wikipedia.org/wiki/For_All_Mankind_(TV_series)), Series that Apple TV just premiered with

#### Dylan

which is kind of alternate history of the space race. The Soviets got to the moon first. And so, you know, the Apollo program kept going and going and going on that I thought dealt with the whole. You know, the ethics of engineering around there in quite a sensitive and nuanced way,

#### Dylan

It could have been a bit of a whitewashing It wasn't actually gone to a lot of issues I thought they weren't gonna tackle.

#### Dylan

But you know, one of the challenges around ethics and professional accountability and software engineering is we don't have the sort of liability chain. You write your code and there's a kind of idea floating around that you know, the distinction between, like, a coder or developer or hacker, whatever you want And an engineer is that an engineer except professional liability for the consequences of the work they do, which is true in aviation engineering and structural engineering, civil engineering. But you design a building and the building falls down. There is a well established protocol for identifying liability. Was it? You know, you specified steel of a certain specification. Did the steel that was supplied conformed to the specifications? If not, then the supplier there is held to be liable if these correct steel was supplied, but then it wasn't assembled correctly. Then the contractors could be held to be liable.

#### Dylan

And, you know, every single computer you got a CPU that might have a  [Meltdown](https://en.wikipedia.org/wiki/Meltdown_(security_vulnerability)) or [Spectre](https://en.wikipedia.org/wiki/Spectre_(security_vulnerability)) lurking in it, that nobody knows about running an operating system where You accept the terms and conditions which say, I promise I will not use this to run life support systems, nuclear reactors, air traffic, control anything that matters. And then you are expected to drop your code on top of that and say, Yes, I will stake my reputation that this is not gonna crash.

#### Dylan

You know, you ever hear about a court case where a developer is going, "Actually, this was a CPU problem or a memory problem". And there are specialist applications, you know, medicine, aviation, where lives are at stake, where you'd like to think that the whole thing is a lot more rigorous. Certainly friends of mine who worked on software for health care, they talk about like a nine month release cycle. We're talking about 10 deploys a day, and now I can't do 10 deploys a day to all of the MRI scanners in Pennsylvania because you'll kill people. If there's a mistake, we have a nine month certification and roll out process. And you're like, Well, if it takes nine months to ship software that you know isn't gonna crash. How are we getting away with doing it 10 times a day? You know, a lot of time. It's because if it crashes, you just reboot. Start again in and It doesn't matter. But the world is changing fast. People often ask, you know, why are software engineers not held to the same standards as construction engineers? I'm like, we haven't killed enough people yet.

#### Dylan

Um, you know, I hope we don't, But it is possible that we will continue operating in this kind of, you know, wonderful space of just right click deploy to production. It's fine. It doesn't matter

#### Dylan

until something drastic, you know, something terrible might happen. And then it will be like, Okay, hang on a second.

#### Dylan

I don't know. I have no idea how we're gonna get there, But, you know, there are these well documented incidents. That was the [Comet aircraft](https://en.wikipedia.org/wiki/De_Havilland_Comet) in the 1950s and 60 which famously took down an entire airline or entire manufacturing company.

#### Dylan

That was the [Kansas City shopping mall collapse](https://en.wikipedia.org/wiki/Hyatt_Regency_walkway_collapse) in the 1970s, which led to lots and lots of regulation or structural engineering.

#### Dylan

You know, you can. You can highlight these incidents. And I don't think in software. We really have one yet. You know, the [Therac radiation machine](https://en.wikipedia.org/wiki/Therac-25), the example we all learn about school, which

#### Dylan

I don't if you know the history, it was radiation radiotherapy for cancer patients. And, you type in the dosage like 1000 And if you press backspace, it would take a zero off the display. But it wouldn't lower in the radiation dosage of the machine. So people got 10, 100 a couple cases, 1000 times more radiation they were supposed to have got. It killed people. But, you know, that's something we learned about in school. It's not kind of mainstream in our industry.

#### Jamie

It's jolly interesting stuff. And, you know, maybe we should have an ethics. Maybe. But like you say, how do we get that? How do we get to the point where

#### Jamie

doing We'll be in a position where we need people to have passed on people to be harmed in some way so that we get It's a really interesting topic,

#### Dylan

you know, Like I said, I really, really hope that we can find our own way there without somebody else having to intervene. Um, you know, I I enjoy working in technology and software because it's a wonderful combination of creativity and problem solving and, you know, creative expression, allied to engineering rigour and discipline and stuff.

#### Dylan

Maybe it might become necessary, but I take to work in a world where all your software has to be licensed and reviewed before you're allowed to deploy to production.

#### Jamie

Like you say, you can't have 10 deploys a day if you're doing that. But then, you know, I've worked at a small consultancies or agencies were You built this thing for this client, and three months later, you've stopped building, get you're moving on something else. Where's the Lobel till I, though, is it? It's a scary situation and, like junior developers were just coming in who may be starting Web dev. If the website crashes, maybe no one's gonna get home, but then maybe their homes apartment. It's all turtles all the way. Then somebody needs a lot of very smart people to get together and actually figure it all out. And

#### Dylan

there are imbalances here. I remember years ago, a friend of mine was studying to become a lawyer and for various arcane historical reasons. The legal qualification process in the UK basically involves jumping through arbitrary _hoops_ for three years in a row. On they have these application windows, where you have to submit applications to various legal firms to do internships and stuff on bits. All run through a centralized agency, and the software that's used for this was horrific. It was one of the worst pieces of user interface, design and reliability I think I've ever seen. And the people who built it. I'm guessing it was just one outsource project of thousands that they did that year. But to these students, you know that if they miss this window, they are not going to qualify as a lawyer because there is no redress. There's no negotiation. There's no appeals process. You have to work out how to get through their shitty website to get your details on that when you go, did that even work? I don't know. You know, you sort of want that set that developers down with people doing it and go. "Your code is making somebody cry at three o'clock in the morning because your crappy error handling might jeopardize their entire career. You know, How do you feel about that?"

#### Dylan

So I think some developers would be like, "Yeah, we didn't get paid enough to do it properly." I think some developers would be like "it was just a job". I think some developers would be like, "Oh, my God, we need to fix this. This is not acceptable. We need to do better."

#### Dylan

But, you know, that's a lot of the sort of the work that I've been doing in the work. I hope they do. A lot more off is about, you know, improving that understanding on both sides. You know, you've got your users, you have your stakeholders and you have your developers. The users are there to tell a story. They want to accomplish something on the stakeholders wanna, in most cases, benefit from streamlining this process on the developers of the ones who can make it happen. You know, we have the capability to build the technology and the systems and what not.

#### Dylan

and you know, done well like we touched on the bionic hand on that kind of thing. That feedback loop is high bandwidth. It's very, very tightly coupled on. If something is not quite right, it's immediately apparent that developers go in and they can improve it.

#### Dylan

But sometimes, you know there's a spec that someone signed off on six months ago. It ends up on your desk. You can't get hold of any of the people. Maybe you don't even know what the system is for. You've just been told to build this design and do this code with it.

#### Dylan

You know, if you don't do that, you don't get paid.

#### Jamie

exactly right. It might be creating some kind of method or module that just does one thing. He takes the number. It gives you a different number. I may not have a full 10,000 foot view of where that's not said, Um, I responsible for if that thing is used to harm people. Yeah, you know?

#### Dylan

We were talking earlier about you know, the V2 Rockets and World War Two and stuff. And there's a story which may be apocryphal, I suspect it Isn't, that when Oppenheimer was designing the atomic bomb

#### Dylan

At some 0.1 of the calculations he fell. If I've got the numbers wrong, I might set the Earth's atmosphere on fire.

#### Dylan

And so the whole project is completely top secret, classified. And so he isolated that part of the mathematics and gave it to a couple of his graduate students. And so can you just check the workings on here? And, you know, they all went. Yes, fine. And one of them came back to him.

#### Dylan

"Is this what I think it is?" And he said, Come in here. You need to sign the official Secrets Act. You're not allowed to tell anybody about this ever and stuff. On day three of the grad students were like, This is interesting maths. And one of them goes, "Are you using me to check whether you're gonna destroy the world," you know,

#### Dylan

and it's context is

#### Dylan

is rightful. But at the same time, abstractions are a necessary part of allowing us to get a handle on the individual parts of the work we're doing. So we don't get overwhelmed by the whole thing. You know, of course,

#### Dylan

on where you draw that line and how much you allow to permeate across that boundaries so so important to getting those those processes to work effectively.

#### Jamie

It really is. Like you said earlier, we divulged slightly from the topic. But I like it.

#### Jamie

Okay, So in the past, before I'd looked into [Rockstar](https://codewithrockstar.com/), which hopefully they're gonna get a chance to talk about today I'd heard of a number of esoteric programs list we got [Intercal](https://en.wikipedia.org/wiki/INTERCAL), which requires a level of politeness. We got [Ook!](https://esolangs.org/wiki/Ook!), which is based on the mutterings of a certain orangutan librarian on you. No one that I can't say the name of just because it's either [BF](https://esolangs.org/wiki/Brainfuck) yeah, afraid in polite company. Exactly. Right. And I think there's one Chef or something like that. You have right out recipes. Was that your goal going into rockstar?

#### Dylan

So, you know, I always liked I like esoteric languages on. And there's a bunch of language. Is that there? Which would still touring topics.

#### Dylan

it's somebody calculated that you need eight instructions to build a curing. She you're basically, you know, increment the point of sacrament. The point input output on four other codes like I can't remember what they are.

#### Dylan

And so languages like like BF and Ook on the whole bunch of others. Basically, that, like Ook, is just the word look with eight different kinds of punctuation, and so `ook!`  is output the value that is currently at the top of the stack. `ook?` with a question mark. It's read Standard in and put it on top of the stack.

#### Dylan

And so you know, the program's just _ook ook ook ook ook ook_

#### Dylan

Which is kind of a joke, and you know, it's It's relatively trivial, not build compilers for those kinds of languages, and there's lots of it. But the esoteric language is that really fascinate me are the ones that try and incorporate idioms from another domain. Where there are strong conventions around stuff.

#### Dylan

there is, ah, module for perl, [Lingua:Romana](https://metacpan.org/pod/Lingua::Romana::Perligata), which allows you to write pearl code in Latin. And Latin Grammar, has this very formal system off singular and plural, and subjects and objects. And so Damian Conway's the person who created this. This is way back In early two thousands, he incorporated the rules of Latin grammar as a substitute for the syntax off pearl operations. So the difference between modifying a variable as a scaler or as an array or as a hash is now expressed by the kind of Latin grammar and the way you conjugated the verb that refers to the method that does it. I thought this was brilliant. You know, I was actually doing pull programming at the time. I don't really studied Latin, but I scratched the surface a little bit.

#### Dylan

I love that way of kind of taking ideas from one domain and putting them in another this is it's actually what I'm talking about. A lot in my keynote at NDC on not a keynote. It's a closing talk. I keynoted that last weekend in Poland, but my talk on Friday here at NDC is about the art of code and has a big section about esoteric languages and these guys.

#### Dylan

And, you know those languages like, [Chef](https://esolangs.org/wiki/Chef) is one where the program is. Also a recipe. And a guy named Mike Werth created a chef program, which is also an edible chocolate cake.

#### Dylan

And you know, I love that because you could have this this recipe and you give it to somebody who has never heard of Chef and they think they're looking at a recipe, and if they follow the instructions, they actually end up with chocolate cake with a kind of molten chocolate source.

#### Dylan

And there's another language. It's called [Piet](https://en.wikipedia.org/wiki/Esoteric_programming_language#Piet) named after [Piet Mondrèan](https://en.wikipedia.org/wiki/Piet_Mondrian)

#### Dylan

The Expressionist, Cuba's whatever artist

#### Dylan

on duh

#### Dylan

Pete programs are graphics, and the instruction set is what you do when the cursor crosses from one color region into another.

#### Dylan

And so you could print a pete program and hang it on the wall, and people would just think it was art. They had no idea they were looking at Fibonacci or, you know, the program that actually does something,

#### Dylan

and so that to me, you know, he's a tart languages. Are this this wonderful confluence off creativity just for the sake of doing something entertaining on dhe, Having to consider how you translate the like, I said, the idioms and the conventions of one domain into something that is rigorous enough to be compiled but still has enough freedom expression that you can build things like programs that are also pictures or programs that are also recipes or in case of the [Shakespeare](https://en.wikipedia.org/wiki/Shakespeare_Programming_Language) language programs that are also plays

#### Dylan

Shakespeare is this this wonderful eso-lang Will you increment variables by saying flattering things about the characters and you? Decrement them by insulting the characters, and it looks like prose. It looks like Shakespeare Plays.

#### Jamie

That's amazing. I love the idea of being able to take something that is in the peat language hanging on the world, and people say That's out And I'm like, No, that's `FizBuzz`.

#### Jamie

Would you call this piece? I call their "fizz buzz".

#### Dylan

Like, Where's the art? Is that the art, the picture? Or is the art the fact that the picture is also program? You know. Damien Hurst that sort of, you know, notorious, select celebrated artist of the kind of the UK I've seen in the last decade or two.

#### Dylan

I remember reading a quote once that said the mistake. A lot of people think he had this famous exhibit worry. He sawed a shark in half and pickled it in formaldehyde or something. And people like, you know, this is really what you think. That Damien Hurst is using formaldehyde under Shark as his medium, but actually those are his tools. His medium is media. He is creating art works where the press and television and radio, and you know, the whole mainstream media coverage that is actually the thing he's creating that all of us are. What changed the tank with shark, in it? That's like his paintbrush or, you know, is clay. Whatever he manipulates that in a certain way on uses that as a tool to them create a media buzz, which is actually the thing about this that's interesting. Otherwise it's just a dead shark in a tank and nobody cares.

#### Dylan

Which I thought was a very interesting perspective. The whole, you know, where where's the creativity in this process?

#### Jamie

So and so that's the esoteric bit. So was it that that fuelled the idea of I want to Be a Rockstar programmer?

#### Dylan

So actually here's a Pauls Devel who founded Octopus Deploy, which a lot of .Net devs use. He is a brilliant deployment management tool for for .Net systems.

#### Dylan

He put a thing on Twitter, saying somebody should create a programming language called Rockstar to confuse recruiters.

#### Dylan

Confuse recruiters on That was it. That was the whole thing, and I just thought Rockstar developer  And it just kind of stuck in my brain, and I figured somebody would do something with it, and after a week or two, like nobody had

#### Dylan

I saw, you know how

#### Dylan

How hard could it be

#### Dylan

on you? Like a lot of projects that end up really gathering momentum. I did not set out to do anything other than write a parody language Specification.

#### Dylan

I was in a in a bar in Sydney and I basically sat down, got a beer, opened my laptop, and went all right. If you were gonna try and write a language where you could compile, like, 1980s power ballad song lyrics, you know, how would you How would you do it? I said it drew some of the three proper programming languages that influenced this were Pearl, Ruby and VBScript. Because in different ways, all three of those languages are. Perl has this this idea of being able to do the same thing in a lot of different ways. You should be able to express your intention in a way that feels natural and comfortable to you as a developer. Ruby is very, very heavily influenced by natural language syntax and very flexible extensible language with keywords. like `if` and `less`, some ways of expressing things that we'd naturally. And VBScript you know, is also heavily based on the idea of using English is a template for writing program code, but it has some ideas around functions and sytax on expressions. You know, VBScript very consciously in the language design. Didn't want to use curly braces and brackets and this kind of stuff, because guess the perception is that stuff looks scary. And it'll put people off. You know, Basic was always a very kind of friendly language in the beginners.

#### Dylan
And so, you know, those kind of influences and I just started playing around with Okay, how would you start removing things like operators and braces and brackets? And how would you develop a syntax and came up with stuff like addition? Okay, well `X + Y`? What about `X with Y` you know how much is the total? It's _price with tax_, All right, on the _price without the tax_ and division, we talk about the _quantity of the product_ and _the distance over the time_, and it's like, all right, well, that's multiplication and division. Get me 15 of those 15 times that. And so you know this this idea off mathematical expressions that just read like sentences on. Then one of the ideas I had for it was actually came straight from Douglas Crockett from a talk he did about the next generation of programming where he's talking about, you know, these these PascalCase versus snake_case, camelCase kebab-case. And he's like, This is all because what we want are variable names with spaces in them, and we can't have that.

#### Dylan

And I thought, Well, I'm inventing a language in a bar as a joke.

#### Dylan

You know, a little bit of thinking kind of went into this spec about how would you actually do this? Because you can't just have some arbitrary variable spaces on them, but I like, well, really rock songs. Talk about, you know, "my heart", "your love" and "her this" and "his that" "the night" and something something, What if the "my", "your" "her" "his" those prefixes mean that this is a two part, variable like a common variable and on also capital letters so you can write songs about Billie Jean and Dr Feelgood, Black Betty, and you know, he's kind of the tropes.

#### Dylan

The first draft spec I got to the point where you could write `fizz buzz` in it. I had a function of syntax. I had comparisons. I had loops. I had variable initialization. 

#### Dylan

An Idea I had I didn't want like `Fizz=100` because numbers don't work in songs because they don't really sound very lyrical. So I invented this thing called a `poetic literal` where you count the lengths of the words and use the word lengths of the digits. So the canonical fizz-buzz limit is `a lovestruck lady killer`. So `a` is one digit `lovestruck` is 10. But Modulo 10 0 `lady killer` is 10 modulo 0 10 0 So 100 So that's 100 and That opens up all kinds of possibilities for writing, you know, because when you can use any 6,7,8,1 of any digit you need, you can use any words you can write in the risks. That right? Yes, which was something. I was really keen to try and look into it.

#### Dylan

I wrote this language spec and I stuck it on the internet and went to bed.

#### Dylan

and the internet went "OOh". I got 1000 GitHub stars on the repo in 24 hours

#### Dylan

and it made hacker news and the front page of Reddit on. But the weirdest thing that happened with it is I started getting people filing issues on GitHub because of ambiguities in the specification.

#### Dylan

And I was like, "Why do you care?" and they said "I'm building a compiler, and I don't know what to do here." And, within about a week, four or five people had built either compilers or transpilers, based on this parody specifications.

#### Dylan

and I was just like, this is I had no idea, you know at the time I was like "I wouldn't even know how to do that."

#### Dylan

And it kind of just kept buzzing along, you know, kind of died down and then, like another, another echo chamber would find out about it and send it round. Well, their slacks on everything and let it be a massive spiking in traffic. And all this kind of stuff on guy sort of decided that this thing had some... It appealed to lots of people in different ways. There are some really interesting ideas, and they're about programming language designed. It's that interesting kind of test case for building pauses and compilers that kind of stuff. It's a lot of fun

#### Dylan

You know, writing Rockstar programs is actually it's way more fun than I thought it would be. It was exactly a year actually was at NDC London 2019 I decided that I wanted to officially have, you know, Rockstar 1.0,

#### Dylan

I wanted to build it myself because I'm a control freak and this is my pet project. Yeah, I want to do this so I basically had to learn how to build parsers and compilers and learned all about a fantastic single parsing expression grammars, which is basically a declarative of form for doing pattern matching you know, recursively matching tokens and syntax within an input file and translating that into, and you know, PEGs can do all kinds of things. You can't just build transpilers, way of rules that say, Well, if you see that rockstar code emit this JavaScript code or .Net code and that's what actually runs so you can build like a Rockstar to Python transpiler just as a grammar file. Somebody actually did that early on,

#### Dylan

but I wanted to actually build a proper Abstract Syntax tree that then gets fed into an interpreter, which then runs the program and told you what the output of that is going to be. So the first step was. I did this in JavaScript because I wanted to run natively on the Web. I wanted to be something that ran in a browser so that you know the only ones. It's like there's a Skala implementation that was one that was written in Rust. And one that was in Python, but none of them had that kind of, you know, if you don't like 90 seconds of somebody's curiosity before they get bored, they might open a Web browser and play around with something and kind of get hooked into it. But 90 seconds is not long enough to work out how to run a skald program unless you already set up to do that.

#### Dylan

And so I was like, It has to be on the Web, has to run in a browser because I don't want security issues of hosting experimental language code on servers and this kind of stuff.

#### Dylan

So I built in JavaScript using a single peg.Js to translate Rockstar Code into a JSON object, which is the expression tree well, the syntax tree for the language and then a meta-circular evaluator, which then takes that syntax tree and executes it. And I mean, it's a tremendous amount of fun because you get two points where your debugging it and you're like, Okay, is this So I wrote a program. Then I wrote a program that turns that program into a different program. And then I wrote a third program that runs the output of the second program.

#### Dylan

Where's the bug?

#### Dylan

Is this a bug in my Rockstar code? Or is it a bug in the way I'm translating Rockstar into JSON? Or is it a bug in the thing that interprets the JSON and generates the output and stuff.

#### Dylan

and it was There was a lot of fun, and I got to you know what I said, Right? This is one point of this is done, and, you know, I set up a website for it, which is [codewithrockstar.com]([codewithrockstar.com), because [rockstar.com](rockstar.com) belongs to some games company that makes Grand Theft Auto or something.

#### Dylan

No, I'm not hip with cool kids.

#### Dylan

And yes, I want that. And it's just kind of been buzzing along and it's wonderful.

#### Dylan

You know, there's a lot of like on the one hand, it's some of the most fun. I've had writing software in a long time, partly because it is, by design decoupled, from the kind of ethical considerations we were talking about. Like, do not use this in production. Don't even think about it. You know we don't have IO. It'll take standard in and standard out. There's no networking. There's no file system access. There's definitely no database connectors or anything. And people are saying "how are we gonna do this." And I got this big list of ideas that I'm playing around with. The first question didn't even have a `raise`.

#### Dylan

I did the advent of code in December last year. And the first couple of days it was like I will do the  advent of code in RockStar, it's like I can't I need a `raise`. I don't have `raise`, all right, I'll have to add `raise` to the language.

#### Dylan

And so there was this massive spike in kind of the Rockstar feature set on Do you know, coming up with How do you design the syntax? Well, what if we do list collections about push and pop? But that doesn't sound (good) so let's let's do `rock` and `roll` instead. So rock will put something into a collection and roll will pull it off the collection like `push` and `pop` or `shift` and `unshift` These kind of things, Um, mainly because I wanted `rock you like a hurricane` to actually work.

#### Dylan

So yeah, that's the fun part. Like, Is there a lyric somewhere in the kind of, you know, the whole rock and heavy metal genre, that line could become my idiomatic example for how this piece of code can work.

#### Dylan

Andi, it's it's fun. It's a very kind of creative process. But it's also, you know, a lot of people have just really enjoyed finding out about it.

#### Dylan

The biggest testament I think that this is the number of people I've seen. You have one sticker on their laptop. You know, some people, that laptop is pristine, and other people, you know, like me, they got stickers plastered all over it. But I've seen lots of people. We got one sticker and it's the certified Rockstar developer sticker that I give out at conferences and I'm like If you say you don't want any stickers at all. But you break the rules just for this one, then that's kind of that says something to me about the way this is connected with people, which is kind of fun, you know?

#### Jamie

Yeah. Yeah, And it brings us like it brings the fun back to development. Like you were saying. You know, we spend so much time at least. If you didn't say Web development or a forms app, you're doing forms over data. you're just doing... help this person to fill this form to start some data in the database or run a report. But if you're able to, then go Hey, there's this. There's this whole other part of me that I'm into this song lyrics, popular rock lyrics, whatever jazz, blues, whatever on I can turn that into something creative. Someone else has done the hard part of making all rhyme. But if I just sort of tweak it a little bit and make Fizz Buzz, make some program that out. But even if it just writes the word "hello" onscreen you do something silly like that eats the huge step towards making it fun again because, you know, I know so many developers. Who are

#### Jamie

We talked about the 9 to 5 developer, and there's nothing wrong with that. You know, for a lot of people, it's a job. I do it to get paid, and then I go home and do whatever it it. But it's maybe being given the opportunity to do something fun in a similar situation would make them want to go right on and take this,

#### Jamie

take it to the next level or take it. I don't want to say more seriously, but, you know, I mean at that sort of fun to it. You know, there's a reason why we have airsoft guns and Nerf guns things because it's kind of a bit fun to just go out and shoot some bern with with a rubber bullet or ah, foam bullet, knowing it's not gonna hurt them. But it's kind of fun to catch people off guard, and I think that's kind of what Rockstar has managed to do is call. People off guard are going Hey, this is fun thing. You could do Go check it out.

#### Dylan

Yeah, it's also, you know, I think the, um you know, I don't know. Well, for example, you know, there are lots of 9-5 welders. You, you know, welding is how they're good at it. They turn up on a building site for the sheet metal fabrication, whatever they do their job. Well, they go home, you know? What do you do? I'm a welder? No come on. What do you really do? Oh, you know, I play golf and I hang out with my kids and I read military history. Welder, I'm constructing in my head right now. 

You know, there's also amazing art out there which would not exist without the engineering discipline or that the craft of welding and the fact that it is incredibly practical and useful should not be a boundary to using it as a form of expression? If that's the way that you feel like you can express the ideas on, you know, whether let's humor or sculpture or, you know, whatever, technology is the boundaries off are being pushed in all sorts of directions by all sorts of things and, you know, I think art and creativity is a completely legitimate excuse to say. Well, what are the limitations of this technology? Is it a learning tool? Is a way of identifying, you know, maybe some constraints or edge cases in our existing languages, which you wouldn't have found just doing kind of 9-5 enterprise development kind of things.

#### Dylan

Yeah, so I'll talk about .Net now.

#### Jamie

Yes. No, Absolutely. That is gonna be my next thing like we talked on Twitter about. Well, you mentioned it in passing about. You're making, I don't want to say Parer Is that the correct way? Is that a parser or transpiler? There is an interpreter.

#### Dylan

So the approach taken with Rockstar. So basically, there's three schools. There's parsers which just takes him code, and they verify that it's legit and valid. And then they output something on. You have transpilers, which they take Rockstar in, and they output something like Ruby or Python or whatever, which you then run on your Ruby or Python interpreter. Compilers are things which takes source code and generate machine code for a particular architecture. And then interpreters. They take source code, and they run it and tell you what it does. So something like Ruby, for example, or most of the scripting language is we use. They don't ever compiled out native machine code. They run on top of an interpreter layer, which gives you brilliant kind of flexibility and cross platform compatibility, is gonna run a ruby program on any machine, which has a really run time on it. But they have overheads with performance, because when you run your program, you're actually running two programs. You want your program and you're running the interpreter it sits on top.

#### Dylan

And stuff like the .Net and Java. They can have a hybrid of this approach because the your program, your C# or Your Java program compiles to intermediate what's called byte code

#### Dylan

and then the byte code runs on a runtime, which is the .Net common language runtime or in Java, it's the JVM, the Java virtual machine.

#### Dylan

and then classical languages like C. The convention there is you compile C for Windows. You get a `.exe` file that runs on windows. You compile it for Mac OS. You get a executable binary,

#### Dylan

but you know you can take like a Ruby program running on a raspberry pi, and you can take the same Ruby program and running on a Mac, and that works fine. If you want to do that with .Net, you have to compile it twice for different outputs. And compiler engineering, I have not yet got into the whole bit where you have to generate machine code level instructions.

#### Dylan

So Rockstar at the moment is an interpreter. So it is a JavaScript program that takes Rockstar programs and interprets them and producers tell you their output Now, up until now, Like I said, it's been it's been built in JavaScript. But now I started working on a .Net interpreter for ah, talk. I did a couple of conferences last year about parsing. Esoteric language is using 
.Net. There's a NuGet package called `Pegasus`, which does the parsing expression grammar, which is the heavy lifting part. And then there's a lot of really cool stuff you can do. Building Abstract Syntax Tree in an untied language like job script is hard because you have to rely on strangers to know what kind of instruction it is and what type it is and where the arguments go.

#### Dylan

You know, I enjoy working a javascript very much. I also enjoy working in .Net.

#### Dylan

So I got about 3/4 of the language syntax supported in that thing.

#### Dylan

But then the really interesting thing that's happened is Blazor.

#### Dylan

because blazor will, I believe in May this year, Blazor will target Web assembly. Officially, it's a preview and experimental support the moment and you can run Blazor on the server and use

#### Dylan

Web sockets or RX

#### Jamie

signalR or something.

#### Dylan

Yes, you can run blaze up on your server and you signalR to update the browser. But when Blazor targeting Web assembly becomes official exported now, at that point, it means that you would be able to write a Rockstar. Parser and interpreter in .Net compile it via Blazor, to run Web assembly and host it in the browser.

#### Dylan

So you get the the one. You don't have to pay hosting fees for running silly joke languages in your own infrastructure, because your your use users are running it on their own system. But you get immediate feedback. You get browser native performance. It's running in their environment, so the security headaches are all on that side of it and these kinds of things.

#### Dylan

But the code you have to write maintain is C#, with all the brilliant stuff like, you know, switch statements based on type inference, which is a lovely, lovely feature. I've got a thing. Look at it. And if it's a type of this, do that. And if it's a type of this, do that type of this. Do that.

#### Dylan

You know, that kind of syntax is brilliant for building evaluators. Because effectively, what you're doing is iterating through a tree on going right. What's next? It's a print statement. Okay, run this block of code. What's next? It's an if statement. All right, evaluate the condition. All right. What is it? True? Okay, evaluate the next bit run that tell us the output of that.

#### Dylan

You know, this is this wonderfully elegant recursive functions, calling into it each other, calling back into themselves,

#### Dylan

which is,

#### Dylan

you know, the .Net type system is actually a very nice way of expressing those kind of behaviors and constructions and things. And Yeah. Now that the road map says that C# down to web assembly and running in through the Blazor runtime is gonna be supported. It's probably a good time to do Rockstar 2.0 in C#. Well, maybe F#.

#### Dylan

and I've learned a whole bunch of new things. Yeah, but then Target Web assembly is is the output so that it'll run natively in Web browsers.

#### Dylan

You know, it's a nice I've always learned by solving problems I've never been much good at, like reading textbooks or tutorials and, to me, getting Rockstar Rain in dot net in Blazor in a Web browser is a problem that is interesting enough that I will happily put the hours in to figure out how to make this happen. Yeah, so that's very definitely on the technical side of the Rockstar Road map for 2020.

#### Dylan

So yeah, Rockstar in .Net Core running in Blazor in Web assembly is it? You know, a fascinating engineering project that pushes the boundaries of software development or is a waste of time and a joke that's going way too far? Who knows?

#### Jamie

I love that you can say Rockstar in Blazor in Web assembly using C# in the browser. That's a sentence you couldn't say three years ago. That's mind blowing to me.

#### Dylan

And the whole thing will probably developed on Mac OS.

#### Jamie

Exactly right,

#### Jamie

Exactly. That's what I'm running 90% of the time these days. I don't know. I got a surface pro a couple months ago, which is a lovely, lovely device on gets really funny jumping between Windows and Mac OS. I grew up on Windows. Since you know Windows 2.0 or whatever and the best way I think I could describe it now that you know Windows 10 on kind of tablet devices is almost there and it's like Windows. It's full of design decisions I agree with that haven't quite been implemented properly on Mac OS is full of design decisions I disagree with that are implemented really well. The Mac OS windowing system is absolutely rock solid, 100% reliable, and I hate it. It's because you can. You can kill all of the windows that belonged to a process  but the process throws up in your task switcher yet so you can come on tab into something and go well. Where is it? Right here is falling off the edge of a monitor.

#### Dylan

Unlike Windows multi monitor support, you want a window that you are an application of stretching across two screens. Easy. Just travel across two screens. Mac will let you do that.

#### Dylan

You know Windows. You sometimes do it, and it goes horribly wrong because it can't work out whether it's on the high DPI over low DPI screen. And so you get really put faces of all this stuff. Where's Mac? Us. You never see that, But it just won't even let you try. Yes. Oh, but yeah, you know, don't let court in Mac OS using visual studio code, which is a brilliant open source editor from Microsoft running .Net code to compile Rockstar into whether simply to run on Blazor in a browser is almost all stuff that maybe five years ago didn't exist. You know what, if the unimaginable.

And now it's like, Yeah, we can do that.

#### Jamie

It's crazy, isn't it? Just like being literally at the forefront is it's It's amazing when you're when you're at the leading edge. The bleeding is just supposed. There are no limits, you know. Everybody talks about, "There's no limits in technology."

I think Hanselmann says that you know Microsoft's about like an oil tanker. It's shifting slowly. If you are in that situation, we're in a big enterprise. You're shifting slowly. You can still see that there are no limits, but it's harder to see that far into the future, whereas if you're at the bleeding edge, you are the limit. You know,

#### Dylan

it's interesting. You know, I've been following Scott Hanselman particularly. But a lot of the other people who were very influential in the earliest days of Microsoft embracing .Net. So you know the team Hanselman, Rob Connery, Phil Hack. And can't remember the with before. What was I'm really sorry. It's basically that the four people who built the first version of ASP and NVC. I think it was Scott Guthrie. On ASP and NVC. "I think this is gonna be open source".

You know that the analogy there are steering the oil tanker. You know, the only reason why the Microsoft juggernaut is changing direction is that there are people like that who every time they try and straighten up. "No, no, no. Come on, Keep it to the left. Keep it to the left."

You know, it's Microsoft Open source is incredibly interesting. It's controversial in the sense a lot of people have different opinions on who's doing what and what's in it for them. You know, to me, it kind of it makes sense that it's very easy to see a point in time, maybe five years from now, where all software is effectively free.

#### Dylan

You know, because you can duplicate it. Zero cost. Yeah. You know, if you have a copy of Photoshop and you want another one? You copy the binary for a millionth of cents in electricity and disk space.

#### Dylan

So, you know, there's there's no kind of manufacturing supply chain infrastructure to speak of. And so you have to look at what are gonna be the stable revenue sources for technology companies. You can copy code for free, but then you need to run it somewhere, which means either you need physical hardware. So, you know, laptops, smartphones, embedded devices. All these kinds of things are all still growing massively or you need cloud. You know, obviously with a Azure. Microsoft is a serious contender were one of the big Four. If you count Alibaba

#### Dylan

in the cloud hosting space and, it makes perfect sense to me that they're like if happy developers end up falling into the Azure pit of success that generates revenue for us. So what do we do to make developers happy? They want great tools. All right, we'll build them. They want open source. All right, we'll build that. They want to run on Linux and Mac OS, Okay? We'll build that they want transpiled for the raspberry pi. Okay, we'll build that.

#### Dylan

And, you know, like I said, this is This is my kind of looking at it from the outside.

#### Dylan

That makes sense to me. People like, Why are they doing open source? It's like those developers want it on Microsoft want you to run stuff on Azure on. Do you have to realize as well you know, Microsoft are the only one of the Big Three who are still like we do technology. We have no interest in being a grocery store. We know building self driving cars and try to open our own taxi company. You know you look at Amazon. Any company who host on Amazon, it's only a matter of time before they actually, we're gonna do your thing now. Yeah. You know, when Amazon acquired Whole Foods, I've had some really interesting stories from big high street grocery stores, like food shops in the UK who were, like, we host everything on AWS. We're now funding direct competitor of ours for the privilege of keeping our own website up. You know, I think that the competition there between you know, I think Amazon's a fantastic company because I remember how awful mail order was before they fixed him. And I used Amazon to order things all the time now. And I heard stuff on AWS. But, you know, I like the Microsoft kind of ethos of we're gonna do technology really well and, yes, we're gonna charge you money for it, but we're gonna charging money for the bits that ideally scale with your revenue.

#### Dylan

Cloud hosting. If you have no customers, you have no traffic. So it doesn't cost anything if you start getting customers. And that one, if your business model is sound, the customers generate t the revenue, which you so probably, you know, kind of fairly transparent supply chain of supply and demand.

#### Dylan

So but yeah, you know, Microsoft is suddenly Microsoft today is a very, very different Microsoft with one I remember from the nineties. The early two thousands on .Net is very, very different. And, you know, the world open source is very different on it is exciting. It's a still a tremendously exciting time to be kind of, you know, involved with it all. So

#### Jamie

It really is. So when can we possibly I mean, you mentioned you mentioned earlier when it's on the road map? Is it, It will be done when it's done. Or is there a defined goal? I want to have something that runs in Blazor and Web assembly on the browser There's written in Rockstar by their state Is there

#### Dylan

So nominally have a target of having this ready when Blazor officially ships. So when Blazor comes out a preview What

#### Jamie

do you

#### Dylan

think is last? I heard it was gonna be about May, but don't quote me on that gun looking upset, of course,

#### Dylan

but it should be the first half of this year

#### Dylan

on that, specifically the Web assembly target for projects

#### Dylan

on. You know, I would very much like to have Rockstar in Blazor ready to go at that point because it gives me a deadline to kind of structure my time around. I mentioned earlier. I just started up my own consultancy thing.

#### Dylan

If I get inundated with people wanting to pay me to do stuff with I'm not gonna turn down interesting paying work to play with Rockstar. If anyone wants to pay me to do Rockstar, Now we're talking. Maybe get an arts grant or something.

#### Dylan

But I You know, I'm also putting together some training material around Blazor. I'm gonna be running some workshops on it, of course, of this year.

#### Dylan

So the timing is serendipitous who I hope to have Rockstar 2.0, in Blazor in a browser. When it does release to manufacturer or whatever they call it these days. Which should be within the first half of this year. Okay, so yeah, watch this. Watch this space.

#### Jamie

I suppose it would make for really interesting demos as well, because, like, there's only so many times you can do. And here's the Pizza Shop. Here is the Nerd Diner. Here is it is

#### Dylan

one of those you know, kind of pulls come full circle and talk about ethics a little bit.

#### Dylan

There's an interesting question around the value off, you know, I put it this way. I would never, ever want somebody on one of my teams to right, their own parser based on something they saw it a conference. You know, I think if you teach people things like parsing, expression, grammars of esoteric language is you are running a very real risk that somebody who perhaps doesn't have the experience or the context will take that knowledge away and use it to you know, five years later you end up with a company where they're you know their order procurement system is written in an esoteric language that was invented in-house with a compiler. Somebody built because it was interesting issue. There is. I've seen a lot of, I'm not sure what problems risks challenges which come because of the pattern that happens in our industry, where someone's like I'm going to use technology except my next project, because I want to learn it, and so they learn it. But the thing which ends up going into production and having to be supported and maintained was built by somebody who didn't have the background of the experience, really, to understand what they're doing on. Sometimes that approach works, and sometimes it clearly fails. But also a lot of the time it works well enough that they ship it because they can't justify cancelling it or rebuilding it from scratch. So, you know, I'm very, very conscious that if you approach are a room full of people and go and do work-shopping how you build compilers in .Net, there's a risk one of them's gonna go back to work and build their own compiler. Exactly. And then, you know, probably do a pretty good job on it. But the last thing we need is a society. Is Mork companies running weird, esoteric technology that nobody else has ever heard off? And that being the reason why your website crashes at three o'clock in the morning when someone's trying to get into law school? You know, the technology and, uh, the kind of education for the sake of understanding is one thing, but Also, we want to teach people things that a genuinely useful and applicable to what they do.

#### Dylan

Um, so, yeah,

#### Dylan

I think we're just about out of time.

#### Jamie

I think we I am, unfortunately. But like I said, thank you ever so much for a chat with. Absolutely.

It was really amazing from my point of view. Just like all of the stuff that we cover the outside of it, the fun side of it, all the technology involved. It's amazing. Hopefully we can maybe catch up again once the interpreter's out and it's running in Blazor.

#### Jamie

Maybe we can talk about it again.

#### Jamie

Thank you ever so much.

#### Dylan

Thank you.

### Wrapping Up

That was my interview with Dylan Beattie. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/), and there will be a link directly to them in your podcatcher.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice - head over to [dotnetcore.show/subscribe](/subscribe) for ways to do that - and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Productivity in Tech](https://productivityintech.com/dotnetcore)
- [Dylan on Twitter](https://twitter.com/dylanbeattie)
- [Dylan's website](https://dylanbeattie.net/)
- [Rockstar](https://codewithrockstar.com/)
- [Ursatile](https://ursatile.com/)
- [The Bear](https://en.wikipedia.org/wiki/Ursa)
- [Dylan's website](https://dylanbeattie.net/)
- [Scott Hanselman](https://twitter.com/shanselman)
- [Visual Studio Code](https://code.visualstudio.com/)
- [Doom](https://en.wikipedia.org/wiki/Doom_(1993_video_game))
- [Quake](https://en.wikipedia.org/wiki/Quake_(video_game))
- [Open source diabetes](https://www.youtube.com/watch?v=uNhYhlBQoEY)
- [For all mankind series](https://en.wikipedia.org/wiki/For_All_Mankind_(TV_series))
- [Meltdown](https://en.wikipedia.org/wiki/Meltdown_(security_vulnerability))
- [Spectre](https://en.wikipedia.org/wiki/Spectre_(security_vulnerability))
- [Comet aircraft](https://en.wikipedia.org/wiki/De_Havilland_Comet)
- [Kansas City shopping mall collapse](https://en.wikipedia.org/wiki/Hyatt_Regency_walkway_collapse)
- [Therac radiation machine](https://en.wikipedia.org/wiki/Therac-25)
- [Intercal](https://en.wikipedia.org/wiki/INTERCAL)
- [Ook!](https://esolangs.org/wiki/Ook!)
- [BF](https://esolangs.org/wiki/Brainfuck)
- [Lingua:Romana](https://metacpan.org/pod/Lingua::Romana::Perligata)
- [Chef](https://esolangs.org/wiki/Chef)
- [Piet](https://en.wikipedia.org/wiki/Esoteric_programming_language#Piet)
- [Piet Mondrèan](https://en.wikipedia.org/wiki/Piet_Mondrian)
