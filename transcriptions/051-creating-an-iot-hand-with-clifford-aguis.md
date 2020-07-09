# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is Episode 51: Creating an Iot Hand with Clifford Aguis. In this episode I interviewed Clifford about his experience in technology, a little about being a pilot, creating an IoT hand completely from scratch (from 3D printing the moving parts to writing the software for the Arduino boards and the accompanying Xamarin app), and what his hopes for the future of the project are.

One thing to note: this episode was recorded at NDC London 2020, as such the audio is a little less polished than I would have liked, and is a little rough at times but that was entirely down to my post production skills. Remember that the full transcription is available at the website, which is available at [dotnetcore.show](dotnetcore.show). The transcription was produced in collaboration with [Productivity in Tech](https://productivityintech.com/dotnetcore).

I would also like to thank both Carl Franklin and Richard Campbell for allowing me to use their recording space: The Fishbowl for this interview and the interview included in [episode 48 (with Dylan Beattie)](/episode-48-rockstar-with-dylan-beatie/).

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Transcription

#### Jamie

Thank you ever so much Cliff for being on the show. I really appreciate it because we're at NDC, everybody wants to go see all the talks, and speak to everybody. So taking some time out to chat with me, I really appreciate it.

#### Cliff

Thank you for the invite. It's a great podcast. I've been going back through the back catalogue.

#### Jamie

Thank you.

Some of the listeners may know a little bit about because I've talked a little bit with a connection that we share - Jim Bennett - about the IoT hand that you going to show off here. But could you get basically give us a brief introduction so that people know who you are, where you're coming from, that kind of thing?

#### Cliff

Yeah. Well, I kind of left school and managed to get a job in engineering with the Ford Motor Company. So I did electro-mechanical engineering, a lot of robotics, and PLC programming which is it controls the machine equipment. I worked int the industry for some 11 years, left the car industry and became an airline pilot, and I now fly for British Airways.

#### Jamie

As you do.

#### Cliff

787, flying them around the world.

A few years after flying, it was early hour of the morning, jet-lagged somewhere in the world - I can't remember where it was, probably New York or somewhere like that - and I was bored. There was nothing to do. There was no nothing on TV. I was literally bored, and I got my laptop out, and just started [faffing](https://en.wiktionary.org/wiki/faff) around. And I was like, "you know what? I can get back into doing this software lark. It can't be that much different from programming robots and things like this." And I got back into it. I now do - besides flying - do freelance .NET development, mostly in Xamarin and the IoT space, but I do the odd website and the likes here and there. And that's me.

As for handy, the hand project: that come about back in, I think it was late 2016. There was news reports of a Dad that had 3D printed an arm for his daughter. On the day I went to school to pick up my two sons and Sharon, Kaden's mum - Kayden is who I'm building the arm for - was standing there. She was like, "Cliff, you seen the news about the Dad whose 3D printed this arm?" And I was like, "Yeah, yeah I have actually." And she said, "could you make Kayden one? You've got 3D printer, haven't you?" Sharon's not one of these people you say "no" to, so I said, "Yeah, course I can." ANd off I went and fired up the 3D printer, and off we go.

Give a bit of back story to Kayden: Kayden is now 15 years old - you can do the maths - he's now 15 years old. He was born with no left forearm, so he's got little stump from his elbow on his left side. And the middle two fingers on his right hand are missing. Just a birth defect, it's not just him. There's many thousands of people around the world born like this, or more commonly they have amputations due to things like meningitis and the likes.

So I went away and did some Googling, some searching, and I found the projects from these reports. The design was open source on GitHub, so I download it and had a go at printing it. And the printer I had at the time was was woefully inadequate. And so, as all good developers, I went and bought a new one. So I got a Prusa Mark 3 printer, which is awesome. I think it cost me about £850 at the time, they're now around £600, they're awesome printers. And started printing.

I printed out early designs, and they were OK but they were biomechanical; there's no electronics in them. It was it worked similar to the NHS claw that Kayden already had, which is solid forearm and then basically a metal claw on the end, which he activates by moving his other shoulder. He moves his right shoulder backwards and forwards, and a bit of cable across the back of the shoulders and opens and closes the claw; which works. And he could do things but was trying to make it better.

So we 3D printed this, and it works in same guise, but it was a five-fingered hand as opposed to claw. I gave it to Kayden and said, "here Kayden, try this." He tried it for less than five minutes and he said, "I hate it. It's not good. It's horrible, I'm going back to my claw". And it, kind of, got chucked away and, well it lived in a box of broken dreams on the bench.

 So yeah, that's kind of where the project started, and it's moved on somewhat from there.

#### Jamie

Sure. There's a lot to unpack there, like I think we were talking earlier on and you said, "Yeah, I just I printed a .NET Bot." and I'm like, "hang out. Wait a second." Dial back about five years ago 10 years ago. Fabricating 3D objects with a printer is science fiction. Now it's like, "I spent £850, "which is obviously a lot of money.

#### Cliff

It is, yeah.

#### Jamie

But, "I've spent this money on this device, and I can make a 3D thing that wasn't there several hours ago."

#### Cliff

Yeah

#### Jamie

Or, "maybe 20 minutes ago." I don't know how they work. S being able to just go, "okay, I appreciate that you have this situation. Let's go print you a hand."

Like, what?

#### Cliff

Yeah, it is. I mean, it is still quite amazing that these printers are around. My first printer - a [Reprap Mendal](https://reprap.org/wiki/Mendel) - is what about 8 or 9 years old? And you look at that now and you think, "wow, that's that's really [Heath Robinson](https://dictionary.cambridge.org/dictionary/english/heath-robinson), it's really basic and, you know, just about print things."

My Prusa I3 Printer is 3 or 4 years old now, and the new [Mini](https://www.prusa3d.com/original-prusa-mini/) that they just bought out - which is a mini version of what I have - is $300. I mean it['ll] print as good as the I3, it's bigger brother, and it's an awesome printer. 3D printers are, it's basically just like an inkjet printer: it prints out a page, and it moves up the z-axis by whatever you set it to - normally 0.1 or 0.2 of a millimeter - and it prints the next sheet of paper. And it just keeps doing that with melted plastic, and eventually you end up with a 3D object. So, yeah, some prints take, as you say, 20-30 minutes. Parts of the hands, like the palm section of the hands, is about a 9-hour print, and then it takes about 20 minutes to clean up and take out all the support material [with a] pair of pliers and break it all out, which is quite therapeutic, actually.

I mean all the plastic, all the material that's used to make the hands from the wrist upwards: it costs about £6. So the material is really, really cheap. You buy it in weight, so you by a spool which weighs a kilo, and one spool is about £25-£30 depending subtleties in the material. And yeah, that print 2.5, nearly three hands.

So you can talk, it is not a lot of money goes into 3D printing. So it brings the cost base down dramatically. And that's one of the reasons behind the project: is the fact that, you know, the NHS will provide you with an arm and a claw, and every few months or every 6 to 8 months ago, you have to go back to the hospital and they remould your prosthetic limb because obviously you grow - that's what Children tend to do. And then you get to a new one, and it's too big because they make it too big. And as the saying goes. "don't worry, you'll grow into it." And you grown into, and a few months later it's now too small, he goes back and gets another one.

This, you know, the socket that we connect to Kayden is 80 pence worth of plastic, and It takes about an hour and 20 minutes to print. So when he says, "oh, this one's a bit tight Cliff," you click print, "yup, one minute mate. go and have a cup of tea," and we'll have some biscuits and tea and wait for it come out and, "there you go, there's a new one." So the turnaround time it quite quick.

My aim of the project was to move it on. I love IoT, .NET and Xamarin. So I started looking and think to myself, "I'm kind of invested in this project now. What to do next?" The biomechanical arm didn't work. So I did some more searcing. There's a team called [Open Bionics](https://openbionics.com/) that were developing open source, under the Creative Commons license, a hand which was literally the wrist upwards. Fantastic device had a lot of open source people putting into project on GitHub -  it's still there on [GitHub](https://github.com/Open-Bionics/Brunel). And yeah they had this all open source. Even the electronics, how to assemble it, and everything else.

So I took that project, looked it and started building it. But things that the motors, the electronics, the sensors, they were selling on a store, but they never had them in stock. It was never there. So, you know, I waited 3 or 4 months for the controller board, and it just "out stock," "out of stock," "out of stock". [So I thought] "Fine. right well, I know how do electronics. I know how to do software. I'll make my own." So I searched around, found my favourite store: [AdaFruit](https://www.adafruit.com/). And looked at their boards and they had a Bluetooth - it's called [BlueFruit M0 AdaFruit board](https://www.mouser.co.uk/new/adafruit/adafruit-feather-m0-bluefruit-le/) - which works on the [AVR processors](https://learn.adafruit.com/neopixels-and-servos/introducing-avr-peripherals). So I got one of those, got their motor controller board, wired it all up on my bench, and literally an hour later I was moving the motors back forwards.

Because the libraries AdaFruit put out are awesome, they're fantastic. Literally downloaded it, `#nclude that`, `#include this`, `open()`, `close()` and had the motors, and thus the hand, moving backwards to forwards. I was like, "Excellent. This is great." And those boards, instead of the board from Open Bionics which was channelled £250 - when they had it in stock - those boards where I think the main microcontroller board was $26, and the motor controller board was $19. So [if] you to convert that into pounds, and it's not a lot.

#### Jamie

Yeah, it's like... what? 35-40 quid? Something like that?

#### Cliff

About that, yeah. Somewhere around there. Compared to 250 quid for a board that I can't actually get.

Fun story was the fact that yeah, I accidentally blew up one the boards and turned into a smoke generating machine a before a day before giving the talk in NDC Last year. But the good thing is that these boards available on Amazon. So literally Amazon-man was at the door next day delivering me a new board and saved talk. Which is just good, but it means again that I've gone with a board that is around the world. You can get it here. They're made in New York, but you can get them anywhere in the world.

And then I start thinking, "well, you know what? I fly planes around the world." You know, I've made this prosthetic arm for Kayden, and you know it's still work in progress, there's still some bugs to iron out, some issues - mainly around connecting to him and getting viable sensor readings. The work: the natural Mechanics of the hand work brilliantly, but the actual connections to Kayden is that bit where we still playing, and trying to work out in the best way of doing it. But then it's like you can buy a printer for £300, you can buy the spool of plastic, and buy the electronics. The most expensive part inside the hand is motors, they're about $60-$70 each - made by [Actuonix](https://www.actuonix.com/), they're little, mini linear actuators. You can build this thing, and you could probably build the whole hand without printer for less than £5. With a printer, you talking £800-£900. So less than £1000, you can build an arm. That's your first arm. Your next arm goes down in price. So there's no reason why - all this is on [my GitHub](https://github.com/CliffAgius?tab=repositories), it's all open source. You can put the links in the show notes,

And the idea is: I can fly around the world, and if there's somewhere I go to on the aircraft that I fly, that actually has a little centre that wants to print these for local Children or even adults - just size up a bit. Then, yeah, I'll happily go along and help them, show them how to build it. It's not difficult.

The problems had with early earlier version of the soldering - you needed to be very dexterous with a soldering iron - I've now managed to remove those by using different connectors and finding ways of doing it differently. And again, I'm trying to make this a simple cost-effective, as cheap as possible.

So yeah, I mean, Open bionics, hats off to them. They made an amazing design. They've moved on, they now have a they've closed their store and they don't iterate the open-source GitHub anymore. I think is last commit was late 2017. They now have a company that are run. And for reasons known to them, they are running the company and selling these commercially. I don't intend to do that. I intend to, whatever changes I've made to the hands to fit the electronics, the motors: the changes that I've done to iterate the design is all on GitHub. Download it, use it, don't use it. Do a PR - if you see something I have done wrong in my coat, do a PR.

#### Jamie

The whole point with open source, right?

#### Cliff

It is.

#### Jamie

If you spot something that can potentially be done in a slightly different way you can go, "Hey, I see what you were doing. I think I understand the problem. Here's how I would maybe approach it." And then you can come back to say, "actually, yes. But what you don't understand is that this these considerations," and stuff like that. We all collaborate, we all make the product better. We all improve people's lives, right?

#### Cliff

Yeah

#### Jamie

And that's one of the reasons I got into the business was: I want to change people's lives. I want to make - maybe having the goal of "making the world a better place" is a bit lofty for just me. But make someone's world a little better is, you know?

#### Cliff

So, I mean, this project literally came out the blue. It was Kayden's Mum saying, "you've got 3D printer. Can you help?" And I was like, "Yeah, Why not?"

It's a project, my side kind of project that I popped back to and that. But the kids you involved, my kids. The community where I live are all interest in the project. You know, it's kind of, you know, when Kayden wears it and takes it to school people are interested.

#### Cliff

You know, the reason - See, you can't see it in a podcast, but is printed in black plastic with green highlights. And the reason Kayden picked that colour was because I originally picked a kind of skin tone, and Kayden was like, "I don't that." And I was like, "why?" And he said, "because people look and they're not sure if it's real or not. They don't know," he said. If it's black and green, he says, "it looks killer and it's it's sick," and the words that the teenagers use these days that, you know.

#### Jamie

Get that fortnight branding on it.

#### Cliff

Yeah, that's it. Yeah.

And so for him, he wanted it to look different so that people can see that is different. It's not real. It is a biomechanical arm, and that for him was very important. Some of the things that Kayden has come back, you know, and talked about is like, "I don't like this." And it's like, "okay, let's change it. Let's fix it. What can we do to make no different?" So, yeah, it's all coming around like this.

And it's little things like, you know, OpenBionics use a big - in their design - use a big, the motor is powered from 12 volts; so they use a big RC battery out of a radio-controlled car. It's big and heavy, but you need a specialist charger to charge it. You need, you know, all the things to power up your arm. And I looked at it and thought to myself, "my board runs on 3.3 volts. So, you know, that's quite low power," with 12 volts of the motors. And I thought to myself, "how can I? I want to be able to do this where, actually, I'm not [using] a big battery pack," and I had some [Anker power bricks](https://www.anker.com/products/taxons/107/power-banks). And I thought to myself, "could I? Well, why not?"

So I did some research, and [Pololu](https://www.pololu.com/) make these power boards, and they do a step-up board that steps up from, you know, 3-4-5-6 volts up to 12 volts; and it's a stable DC output. And I was like, "will that work?" So I did some testing: it does. So I now use a normal 5-volt power brick that we all use to charge our mobile phones, and transfer up to 12 volts to power the motors, take the five volts into - it's five volt tolerant: the board, the AdaFruit board - and power the board.

So now I've got - rather than a big, hefty battery - I've got a normal USB chargeable battery pack, which is fantastic. Downside is that when Kayden wears his arm to school and his friend's got a flat battery, he's "Kayden can you charge my phone." But there's ups and downs.

#### Jamie

Give and take, yeah.

#### Cliff

But yeah, it just means that, again we reduce it down to, "if you can't get that power brick or that battery in wherever you are in the world, then you use a USB power supply from whatever one you've got," and just somehow...

#### Jamie

Stash one in your pocket and run the cable up your sleeve.

#### Cliff

Exactly, yeah.

You know, you can see on the design I've kind of Heath Robinson just stuck in the forearm. You know, that kind of works. There's other ideas were having about how to do it in a little compartment. But yeah, the idea is the fact that we make it with off the shelf cheap components that Amazon, eBay, Alibaba, wherever, you kind of can shop around the world and get it delivered to you.

So that got the arm working, and then obviously, I had the BlueFruit, which is a Bluetooth enabled board. And it's like, "okay. So, right, the next step is the fact that a notice with Open Bionics hands and with other companies that produce these is that when you have something that needs to be changed: settings because you don't use the muscles - or Kaydens's never used those muscles in the forearm because he's never had to. He's now using them to tense, to trigger the action of the sensors. Because they were never used but now he's using, they're starting to grow in strength. So now a small movement for him is now a big sensor reading, so his sensors need to be adjusted. Things like the motors over time start to wear down so they don't move quite as quick, quite as precisely. So you want to change the settings on those as well.

So invariably, it meant a visit back to the prosthetic department and getting, you know, tweaked and adjusted. And I thought to myself, "again, we can fix this." I do Xamarin development, I can build a mobile app. The advantage of it being Xamarin is the fact that is, you know, again, it's open-source, Microsoft platform. It means that I could build this app such that it uses the native layer of the device - so Android or iPhone. And the advantage of that is a fact that if some, like Kayden that has no left arm, he's only got two fingers and a thumb on the other hand, uses the accessibility options in his iPhone quite a lot to make the buttons bigger - that sort of thing.

And it's like, "well if I do it in Xamarin, I don't need to worry about how he accesses the phone because Apple take that, and Xamarin just step on top of that, and I've got my code running on top of Xamarin, running on top of the iPhone platform," and the same will work for Android. So the fact that I could do that, you know, the fact that I can access the Bluetooth stack from with the Xamarin meant that I built an app, put it together fairly quickly and had it sending [UART commands](https://www.circuitbasics.com/basics-uart-communication/) - so basically serial commands - backwards and forwards from the hand to control the hand.

And it's like, "well, now we can start to get somewhere." So things like the fact that the hand has seven grips loaded the memory that it loads from the [EEPROM](https://en.wikipedia.org/wiki/EEPROM), and those seven grips you cycle through.

So if you think that your hand can only do seven things, and you've got to select which one of those seven things you want to do, and if you miss it you have to go back around the circle to get back to where you started again. And invariably miss it a second time again.

#### Jamie

It's like those old rotary phones, isn't it?

#### Cliff

Yeah, exactly. So I was chatting to Kayden, and he's like, "don't like this because, you know, I keep not having the one I want." So I'm like, "well, let's make the list shorter."

"Yeah but now I want that one and not that one." And it's like, "OK. Well, what if I put that into the app?" So in the app, you can select which grip you want enabled at any one time; you go to another part of the app, and you can select the order. You know, "I want in that order, then that one and that one."

One thing that has been suggested to me but I haven't put in yet is having grip sets. So you can select, "well this is my set that I'm using for school," "this is my set that I'm using at scouts," because he's quite active in the scouts. "This is something going to use when I'm gaming on my Xbox," that sort of thing.

#### Jamie

Yeah.

#### Cliff

And again, it's quite simple to do in the app. You know as the muscle sensors change he can quite easily go in there and just tweak the settings himself. If anyone's listen to this and that anyone is on expert on machine learning, please contact me because one of the things I love to do is work out - I'm not machine learning novice, let alone expert - is having machine learning learn the fact that sensor values are changing.

#### Jamie

"It's 9 o'clock on a Monday morning, he's going to school, I'll automatically switch to the school set."

#### Cliff

Even that. That's a genius idea. I never even thought of that. A timing your system.

#### Jamie

Yeah.

#### Cliff

I was thinking more about the sensor is starting to see, "actually, we're hitting the peak. We're clipping off the top of sensor readings. Therefore, let's adjust the gain levels down." And because it's just a value, an arbitrary integer value, we can adjust their values dynamically. So yeah, a way of the app learning, having a little machine learning model, that will learn, "okay, we're now starting to clip," or "it's too quiet that put the gains up because maybe he's tired."

#### Jamie

Yeah, his arm is getting fatigued. It's getting late into the day, he's getting tired - or whoever using it. Sorry. Whoever's using is getting a bit tired, they're getting fatigued. Let's increase the gain; or drop the gain because its first thing in the morning or...

#### Cliff

I mean, it sounds simple, you know, I was talking about it. But I have no idea how to get ML .NET or whatever to make this work. I do know that you can run a machine learning model from within Xamarin and you can do it in .NET, I just don't know how to do it.

#### Cliff

If someone's listening, I'm on Twitter [@CliffordAgius](https://twitter.com/CliffordAgius) come and find me and see if you can help on the project.

#### Jamie

Or maybe you can shout it out during [your talk](https://www.youtube.com/watch?v=WHL2v4mXbRE) as well.

#### Cliff

I will, yeah. Tomorrow morning.

#### Jamie

Or maybe talk to people as we're walking through and say, "hey, you know machine learning? Go see Cliff."

#### Cliff

So now the project is the fact that we have the hands, the electronics in the back, and we have a power system that uses bog-standard - in this case and Anker battery - but whatever USB battery supply that you have. This is a 10,000 milliamp battery, it lasts him about two days - a bit less when his friends and he isn't charging his iPhone at school.

But it's kind of, good enough to get him through today and it's small, lightweight battery that hew can just have a spare in his backpack.

#### Jamie

Exactly.

#### Cliff

The Xamarin app is almost to the point where I'm ready to start pushing out to other people. I have tested /is and worked through it Kayden, and little things to come up with. Little things that he's asked for is he's never sure which grip is currently enabled on the hands, so he says, "can not just have, like a light in the back that changes colour?" And this is the things that I'm not thinking of, but as the user he - he's like, "can I not just have a light?". It's like, "OK." So we initially put a light on the back of the hand, which Open Bionics do as well - the put a Neo Pixle LED on the back of the hand. And he's like, "no, it's not good, because when I hold my hand, the back of the hand is always facing away from me. Could we not put it on the side?" So the design iteration we've got going on at the moment is putting it just where the thumb is, because it's the left hand we're doing for him, so just where the thumb is. So he can just glance down and see the fact that we nearly always see your left thumb is. And the little LED strip there will give him a colour indication.

So I've got on my bench, it's not here at NDC, but on the bench is a demo version of this. Kayden was over last night and was having a tinker and a play to see if we can work out, kind of, some of the subtleties of it. And then within the app I've engaged it such that you can change the colours of the hang grips. So they're primary colours: red, blue, yellow, green - that sort of thing - so when he's selecting in the grip he can set the LED colour. So he will, over time, learn what he wants it to be. But there may be another child that, you know, hates red. I don't know.

#### Jamie

Exactly.

#### Cliff

Or maybe they're colour blind. And for them, it's a different sequence.

#### Jamie

Or flashing.

#### Cliff

Flashing that sort of thing, exactly. Yeah. But once we get it there, we can decide what we want to do. And again it's little things like that, that you don't think about because you're so engrossed in... I'm engrossed in the 3D printing, in the power system, in the Xamarin app. And you hand it across and he's like, "it's all right." And you'll never say it's not nice, but his mum was like, "just tell the Cliff truth. If you tell him what you really think he can then change it, fix it." And. you know. the LED the on the back, he was saying, "it's all right, but it's not, you know..." and it's like, "can we not just put it there?" And I'm like, "of course we can. Let's make it happen."

Yeah. And hopefully, as I say, fingers crossed we'll get to a point where we can have this such that, you know, it's open-source and everyone can get it. And then hopefully I'd love to see other people downloading and building these. If not, contact me and say, you know, "can you help build one?" I'm more than happy to help anyone.

#### Jamie

Awesome. So what about the circuit boards inside? We were talking earlier on, and you were saying, "it's got a couple of these," - I honestly don't remember the model number because they all came out really quick because. like you were saying, you're so involved in it. But you mentioned there's the [wilderness Labs one](https://www.wildernesslabs.co/meadow) that you're looking into, and things like that. And that's like low-level - well it's not _low_ level - but that's .NET inside the arm, isn't it?

#### Cliff

Yes, that's the next iteration.

The next iteration is that we're gonna take out the AdaFruit board which is running Arduino C, which is great. It's fantastic. It's not the quickest in the world. It does the job, it works, but there's things where we're either communicating between the hand and the app, or the hand is working. It's either-or.

I want to move across. Wilderness Labs have developed am [F7 micro board](https://store.wildernesslabs.co/products/meadow-f7), which is based on the [AdaFruit Feather](https://www.adafruit.com/feather) footprint; it's slightly longer, but it's the same pinout. Which means it can drop straight into the hand with very little work. And then it'll run .NET. So I have .NET in the hand, .NET on the phone, and if this machine learning thing comes off I dare say that there'll.NET in the cloud somewhere running on Azure.

And then we'll have .NET everywhere. And that isn't because I need to do it, it's because I'm invested in this project now. I'm enjoying it and it's fun and it's like, "why not? Let's try it. Let's see what happens."

#### Jamie

Yeah.

#### Cliff

You know, and if I can get .NET into the hand on a microcontroller board, that'll be fantastic.

At the moment - I do have some Wilderness boards - the problem we got the moment is that the Wilderness boards Bluetooth stack isn't baked. They're still working on that, I think it's beta 4 which they're releasing in - I think it's March, is their timeline for releasing that - that way I can then start to link the phone and the hand together.

Some of the I{{< sup "2" >}}C - which is a serial protocol that the main controller board speaks to the motor controller board - I've found some issues there; reported them back to the team. And they're aware of them, they were things that they knew about, and again, they're things that they're going to bug fix in the next beta release. So hopefully from March/April time, we'll have a board that could do what I need it to do, and then I'll bake it into Handy. Then we'll have .NET Everywhere.

This will be awesome

#### Jamie

Yeah, So I mean, you were saying earlier on about you showing this off to the potential users and them saying, "can we do this? Can you do that?" And you're essentially doing the same thing but with this Wilderness Lab board. You're saying, "hey I'm using in this real thing. Can it do this? Can it do that?" "Well, it can, but it's coming soon."

#### Cliff

Yeah

#### Jamie

This is the exact same thing. The same thing that you are experiencing with Kayden is what they're experiencing with you. "Hey this person is doing this thing, right. And we're getting real-life data. Because in our lab we've only ever really poked it with a stick, and it's kind of done what it needs to do."

#### Cliff

Yeah.

#### Jamie

So does that mean then, the current iteration - presumably the device sat in front of us right now - is low level C? Is it Python?

#### Cliff

It's [Arduino C](https://www.arduino.cc/reference/en), which is a version of C that's been kind of ripped up and large chunks of it chucked in the bin because he's not required because it's a microcontroller. So things like, you know, you're standard out and stuff like that - which would go to a screen - well there's no screen, so we don't need that: chuck it away. So they've really stripped it down [to] low level, But then they've added parts, like the fact that on your computer when you running C you don't have a [GPIO](https://en.wikipedia.org/wiki/General-purpose_input/output) - General Purpose Input Output - port; you don't have I{{< sup "2" >}}C; you don't have you UART ports and serial protocols that sort of thing. So they've developed libraries that do those functions instead.

So it is C. It's a bit quirky in places. Anyone that's worked with Arduino will know. But it works, it does the job. The AdaFruit board is awesome; built and made in New York by AdaFruit Industries, and they're dirt cheap, and as I say you can get them from anywhere. All the other electronics in there are simple cables, wires, and things that this. There's nothing expensive or difficult or challenging in the build. The circuit diagram is a simple as I can make it.

#### Jamie

Sure.

#### Cliff

But yeah. We'll move, hopefully, across to .NET; not because we need to because I want to.

#### Jamie

Yeah, simplify the whole thing right? If you're only using one language for the whole stack - it's the same reason we're getting Blazor in the browser: because if it's one language in the whole stack that everyone understands, everyone that is working on it understands it, it becomes so much simpler to make a change, right?

#### Cliff

Yeah. And not only that, it's C#. And a lot more people, you know, understand and read C# than can read and understand C#, and Arduino C is a little bit special in the way it does things sometimes. But yeah, and it means that a lot of the code that's there at the moment can disappear; because quite a lot of it is, kind of, boilerplate stuff that you just need to do just turn on an LED. Whereas in the Wilderness Labs C# it's literally one line of code and it's done, you know.

#### Jamie

```csharp
led.On();
```

or something?

#### Cliff

Yeah, it's pretty simple stuff.

So that's the plan, the future of the project. I enjoy coming and talking at conferences and meetups around the UK. You know, I've been to Boston (MA) and given the talk - more than a one night stop. "Come along to our meetup and have a chat."

But yeah, it's purely because, you know, to get some kind of ideas. Ideas like what you was talking about minute ago for machine learning: 9 o'clock in the morning. he's going to school, therefore put in "school mode". I never thought about that before, I'm not sure that Kayden had. But it's an idea that actually will probably make it to, you know, to be in the app.

So yeah, that's good.

#### Jamie

So you were saying earlier one that is this, I don't know, the technical terms - I mean I did do electronics, but this is more like the biomechanical - there's a tension that he provides in his muscles that's read by the sensors?

#### Cliff

Yeah, we've got some sensors in the socket that goes on the Kayden's arm. And we started out with these [MyoWare sensors](https://www.pololu.com/product/2732) that just like a little sticky patch you have when you having an ECG with you doctor. And they measure electrical impedance, and they can decide that actually that muscle is being moved because we met a reading. But they used a little sticky patch. You need of the sensor boards, and they're $35 each - so that's $70 straight away - the little sticky pads, you need six of them, 3 for each board. And a pack of 50 costs £5, so they're not expensive; but a pack of 50 is only gonna last you, what, 8/9 days and you're gotta be out.

So that's like every other week, or not even that, every week you're spending £5 on sticky tabs. Just to keep your arm going. Which, you know, is no a small amount of ongoing costs. So that was one of the early things I wanted to get rid off. [Hacker Space Magazine](https://hackspace.raspberrypi.org/) did an article about a year ago - not even that about - about debugging Arduino, and as part of that they used a little [piezoelectric sensor](https://en.wikipedia.org/wiki/Piezoelectric_sensor).

And I was like, "Debugging Arduino is a brilliant article. But actually, that sensor, what's that? I want one of those"

#### Jamie

One sentence in a whole article?

#### Cliff

It wasn't even that, it was a picture.

#### Jamie

Oh, right.

#### Cliff

It was literally a picture. You could see the picture, and in the code, it was taking a sensor reading. And it's basically a stress centre and it's used in drum and guitar pickups. And it senses vibration. And I was like, "ooh, hold on. Well tensing a muscle is just a low-frequency vibration - it's either on or off. So would that work?" Back to my favourite Amazon postman/delivery guy, and I got a pack of 10 for I think it was £1.80, or something really ridiculously low price. How Amazon delivered that free to my door, I do not know. But I got them, wired it up, and it worked. I was like, "This is cool." So we chuck out $70 sensors and the £5 every other week sticky pads. And we've now got super cheap sensors.

They worked. The difference is they can only sense or give you a spike. So if you push it, you'll get Spike but they're no more output. And a piezoelectric sensor is basically, you know, the buzzer in your PC that tells you that you memory is bad, and it beeps - what's it, four times for memory or something?

#### Jamie

Something like that, yeah.

#### Cliff

Whatever it is.  It's basically that reverse. So you pass electricity voltages through your piezoelectric sensor, or through you piezoelectric beeper, and it make a noise. If you push it, it would generate a voltage out, which is only a low voltage, but it's enough to be picked up by the analogue input on the Arduino boards. So that's all it was. So you get a spike which is great, you can actuate the hand and it works. But as soon as I gave it to Kayden he's like, "But it's not stopping in the middle now." I said, "what do you mean, Kayden?" And he said, "well before, I could not move it a bit and then stop it.

And that's because the myoelectric ones you could kind of control the motion, just like you can be real hands.

#### Jamie

Yeah.

#### Cliff

I hadn't noticed that I've been working on this for a couple of weeks, on my bench. I was like, "I've cracked it. Genius. It's brilliant. Fantastic." I give it to the user, and the user instantly picks up on the fact that this functionality they had before had gone. I hadn't noticed because I'd been "open hand," "close hand," "open that grip," "do the OK signal," "not OK signal." And it's like he noticed it straight away. So I'm like, "ok, Right. Back to the drawing board. We'll go away." But that got me thinking about, "actually, if there's that out, what else is out there?"

So I'm down root somewhere in the world, I was googling away trying to find what I could find. And I found these force-sensitive resistors, which you apply a voltage and as you apply pressure you get a voltage linear to the amount of pressure you apply. Again, super cheap - I think about 4-5 pound each. And they normally come in a pack of, an even bigger pack and it's even cheaper. So I got some of those in different sizes so that we can try the different sizes. Couldn't wait to get back from my trip, I was like, "come on. Fly faster. I want to get home." Got home, there was the package waiting for me, tore it open, went into my lab, and evil genius time, and hacked away and got it working. And a day or two later I had it set up so that it works _almost_ the same as the MyoWare sensors, but they're a fraction of the cost and they work great.

The downside then, that we're still battling with at the moment, is where the MyoWare sensors stuck on to his skin and they were there. So no matter what arm grip we had, the sensors are always sensing. With these, we stick the sensors on the inside of the socket - where he puts his stump in to - and which means sometimes a sensor is not quite in about place. Or sometimes his arm isn't quite right isn't quite actuating the sensor. And again that comes back to the machine learning thing that I want to try and work out a way of detecting that that's happening and saying, "actually, let's turn the gain levels, and the peak thresholds and the hold dwell times down to this level because that's the readings we're getting today."

#### Jamie

Or maybe if he's moving around a lot, literally moving around on the socket and the readings aren't quite right because the sensors aren't quite where they need to be. So maybe you could have an alert [which] goes off on his phone, "hey, it's come a bit loose. Just rotate it a little bit."

#### Cliff

Yeah, something like that. So I mean, that's where we've gotten to. But again, we've reduced the cost down.

#### Cliff

My aim, you know, my dream that I really want to get to is to be able to take the 3D printer out the cost, but be able to literally buy all the materials and build one of these for less than £500. I'm just shy of 600 at the moment. There's bits I'm going to take out, which should make it a little bit cheaper, and it will be easier to print. Some of the springs that used inside are quite expensive: there's 3 of them on the end of the motors, and they're like £7 each. You know, I'm trying to work out whether we can reduce those.

There's a different motor that I've found recently: a linear motor, which is about half the price of the Actuonic ones I'm using, but it's slightly bigger. So I've got a couple of those on order coming from the US, and hopefully, I can see if I can fit those in. Again, that reduces the cost. And, you know, if we can reduce the costs and get functionally. The advantage that one: that one also gives you not only a [potentiometer reading](https://en.wikipedia.org/wiki/Potentiometer) of where it is in this position; but it'll give you a current output. So it'll tell you the amount of current that it's currently drawing. Which then for readings, you can then kind of work out, "actually, I'm drawing a lot current. Has it stalled because its gripped something?" And things like this.

#### Jamie

And then presumably you could use that information for, "how much power does it have left yet?"

#### Cliff

Yeah.

#### Jamie

!Will it last until the end of the day?" Do any to swap out the battery?" "Do I need to plug in?" That kind of thing.

#### Cliff

Exactly. There's all those sorts of things. But again, as I say, it's gotten to point where Kayden can use it, pretty much now. But it's now, "what else can we do? What can we do to make this better? What we do to improve on this?"

Like I say, Open Bionics are now got their product that they sell, which they've taken far beyond what I have managed to. But they've got a whole team, and a company behind them, and funding. But they sell these as commercial products, and then they're not cheap. We're talking in the many thousands. They're not available on the NHS because they deem them...

#### Jamie

They're too expensive.

#### Cliff

They're too expensive, and they've got the hook system, which works. And you know that works for them, But they are being sold in, I noticed people in mainland Europe - France, Germany - there's lots of people across the U.S. There are people in the UK, but getting crowdfunding to get their arms and stuff like that - their [Hero Arm](https://openbionics.com/hero-arm/). And hats off to Open Bionics, they've done an amazing job. It's phenomenal what I've done. There's one of me, and I do it as a side gig. And yeah, I started out doing this for Kayden and his family just because, "why not?" And it's morphed into this project, which actually keeps me busy.

#### Jamie

Yeah, I can imagine.

So then with the the app, because its Xamarin presumably if the user wanted to switch to Android they could just do that because it's just cross-platform and presumably exposes the same low-level systems: the Bluetooth and all that kind of stuff. And then if you need to update the software, you can presumably download a file, open the app and go, "send this to the device." And it just...

#### Cliff

Yup. Over-the-air updates is on the on the to-do list, for doing over-the-air updates for the hand.

But yeah, the way that the Xamarin works is your .NET Standard project: all of my code is in there. I've made a point of trying to prove a point to myself that I _do not_ want to touch the Android or iOS projects. I mean, they're there, they sit there in the solution file. But I really do not want to touch those. So other than pulling in NuGet [packages] that need to be pulled in - you know, [Xamarin Essentials](https://docs.microsoft.com/en-us/xamarin/essentials/) and the Bluetooth files that are pulled in to all three projects: .NET Standard, Android, and iOS.

I have not written any code in those two platforms. So all of my code is in the .NET Standard [project] and it all runs in there. I use [Xamarin Shell](https://docs.microsoft.com/en-us/xamarin/xamarin-forms/app-fundamentals/shell/introduction) to do the navigation and the layout because it does the job.

#### Jamie

Drag and drop a button, and it's there.

#### Cliff

Yeah. And then I've got the separate pages, and all the Bluetooth comms is sorted with an open-source library. So everything that's there, that you can go and look up on [my GitHub](https://github.com/CliffAgius?tab=repositories) is all open source. I, literally on the train ride in this morning, one the things it was annoying me was that I wanted a picker, like a ListView, where you can re-order the ListView. I've been using [SyncFusion](https://www.syncfusion.com/) tools on actual paying projects for client - awesome, brilliant tools, amazing tools to use. I've been using their re-order ListView and have been using that in this project. And I was like, "that means that I've gotta have a license," and you Sync Fusion do give away free licenses to open source projects, and I think it's amazing they do that. But it means that if you take the NuGet [packages], you've got go and login to get the new license key. Which means if I open source on my GitHub and _you_ download it, you gotta go get your license key. Which can be a barrier to some people, some people who are new to .NET, new to programming, new to Xamarin for example. It may be a bit of a, "hmm... I'm not sure."

When the train arrived this morning, I'd seen someone on Twitter - I can't even remember his name now, Aplhonzo I think his name is, he's a French guy who lives in Paris and is a Xamarin MVP and the likes

---

Edit note: Cliff was talking about [Jean-Marie Alfonsi](https://www.sharpnado.com/hire-me/)

---

And he has this thing called [Sharpnado](https://www.sharpnado.com). And I'm like, "oh, what's that?" I looked through his GitHub, and he has a re-order ListView that's part of this project. All open-source, all there on GitHub.

So at some point in the next few days, I'm going to pull in that NuGet, remove the SyncFusion tool - sorry SyncFusion - and put in this Sharpnado. Which then means there's no licensing issues, and it's all open source.

#### Jamie

Anyone new to the project just pulls down the source code, hits F5

#### Cliff

And it just works.

So at the moment, to get it on to Kayden's device - onto his iPhone. So I develop on Android. I'm an Android user, I'm not a fan of Apple. And I deploy to my Android device, when I'm happy, I deploy it to my test devices - my test iPhones - that I've got. And when I'm happy, I push it to [AppCentre](https://appcenter.ms/) - Microsoft's Cloud Resource.

In fact, I don't even push it. I do a `git merge` into master, and AppCentre watches my master branch, and when it sees [the merge], it does a build and it publishes out and sends an email to Kayden to say, "there's a new update to the software," it sends an email to me that says, "there's an update into the software." And I've got various teams in there: so there's me as a developer, there's a collaborative branch which Kayden is on as the test team and his mom's on there as well, and they push of the app from AppCentre. Just by me doing a merge to master, and Microsoft take care of it.

#### Jamie

It's just that whole CI/CD pipeline.

#### Jamie

push a point. I literally pushed a master and I used to master whatever. I literally push to master - merge to master, whatever - and 10 minutes later it's on everyone's devices.

#### Cliff

I don't need to worry about it. I don't need to do a Mac build, and get my MacBook out of our storage, and fire it up and do a build for iOS. I mean, even now in the last - not even a few months - last a few weeks I think, Microsoft and the Xamarin team have released [Hot Restart](https://docs.microsoft.com/en-us/xamarin/xamarin-forms/deploy-test/hot-restart). Which means I can plug my iPhone into my Windows machine, and I've had to install iTunes because it uses the iTunes tooling. But I don't need a Mac any more. So I can build, and run, and deploy to my iPhone, from our my own Windows machine, using Xamarin without ever touching Apple, other than iTunes being stored on my laptop. Which pain to me to install that.

#### Jamie

Small price to pay.

#### Cliff

But it means that I don't need a MacBook. Which means now, when I travel around the world, I've got an old [knackered](https://dictionary.cambridge.org/dictionary/english/knackered) iPhone that I can just chuck into my suitcase and take with me, and I can check, and I don't carry my iPhone.

Or the way I was doing before was sending the build to AppCentre, and then waiting for AppCentre to build, 10 minutes later for it to push down to the iPhone and, "oh, I missed that bit." The dev-loop cycle was long enough for me to go to the gym and back kind of thing. Whereas now it's literally Hot Restart and it just, and it just works. And you know the dev cycle is in seconds rather than minutes.

#### Jamie

That's amazing, yeah.

#### Cliff

And hats off to Xamarin team, to the guys over there, who have pulled this out. It's phenomenal stuff.

#### Jamie

Have you been in contact with the Xamarin team and talked about it?

#### Cliff

Yeah, I was lucky enough to be in Boston a few months ago, and I popped along to the Xamarin offices - or the old Xamarin offices, they're Microsoft office now - in Boston and met some of the team, and went and had lunch with them. But yeah, Microsoft are taking an interest in the project through all the tooling I'm using. So hopefully they're going to be doing some things with it, in the near future.

As I said earlier, I try and blog about the project, but I've got many, many blog posts that I have written kind of while I'm flying along. But in gaps in what I'm doing: flying the plane. But then don't put the images in the right place or the code snippets and things like this, because you can quite easily type a document on your iPad.

But yeah, blog posts are coming out slowly on the project. And every time I write it, I go back and look at it and it's like, "no, I've done that now. So I need to change it."

Yeah, hopefully, the idea of the blog posts is that someone who wants to build one these will be able to look at the blog posts and go through, and see how I got to where I am, but also how to build it themselves. So it'll become _almost_ an instruction manual of how to build your arm.

#### Jamie

Yeah. That's amazing. Like, I mean, I'm a developer for my job. You were saying, your, sort of, full time paid work is being a pilot, and you do this sort of development stuff on the side. And I do the development stuff full-time sort of my own and I can't imagine what that must be like: you land somewhere, you go to the hotel, presumably, you get checked in and then you go, "right. I wanna spend three hours doing development."

#### Cliff

Yeah, it doesn't tend to work like that. We tend to land, go to the hotel, go out for dinner. And get some sleep. But yeah, you go to the U.S., Canada, places like this,  and your body clock, you're awake a 2-3 o'clock in the morning because that's 9-10 a.m. in the UK.

And certainly, you go to the West Coast, like San Jose and place like this. So I'm awake have nothing to do. The gym's not even open yet, it doesn't until 6 a.m. So get my laptop and have a little pot of porridge out my bag and a coffee, and start coding. You know, when everyone else is wondering about and just seeing the sights that we've all seen hundreds of times - because we've been there that many times - I'll sit in the coffee shop and code away. You know, be it working on this Handy project or client projects, doing a Xamarin project or an IoT project, I'll sit and code away. And because all I need is my laptop, and the mobile phone to work on Xamarin, I don't need anything else. I pack light, and off I go.

#### Jamie

Do you ever get like - you said then, you'll sit in the coffee shop and code away - do you have handy with you? Like do you get people looking and going, "what the heck?!"

#### Cliff

No. I learned fairly early on that carrying that sort of thing in your suitcase me just gets opened by the TSA, and they want to know, "why is there an arm in there?" So yea, I don't carry the parts with me. For a while I was carrying the Arduino AdaFruit boards with me but, like I say, the TSA and the authorities - I can't remember what they're called - down in India see it as an electronic device, and wanted to know what it was. And it could cause delays because I was then having bag searched, and had to explain what it was, the paperwork etc. So I just don't bother anymore.

For IoT projects I wok on those at home; I  work on the code and have very different branches of ideas I've had that I can't test. But yeah, and that's another exciting thing about the Wilderness board, is the fact that it's .NET; which means that I should theoretically be able to write a console app around it, and test the code.

#### Jamie

Yeah.

#### Cliff

And when I get back, plug it into board and I should have already tested and ironed out maybe 80 or 90% of the bugs. It's just .NET.

#### Jamie

You could, Yeah, it's a console app that's running on your machine, not running on their hardware. And then perhaps you could have someone who's back home who's willing to just plug it in. "Just do me a favour. Run this command and it will download it onto the device."

#### Cliff

My family have gotten wise to that because we've made too many smoke generators in the past. To the point where you know my kids joke about the fire extinguishers in my office. It's like, "what are they for?" when they come and show their friends the Handy project. "So why the fire extinguishers?"

"Oh, it's because Dad sets fire to things."

#### Cliff

But I'm hoping, at the point where it's just .NET, that I can write a console app around it that is just the same code. And have like a test project, where I can test my code and see that it works. And instead of blinking an LED on have a print statement that prints to screen LED on. It's a bit Heath Robinson - it's a bit basic - but it will do. It'll get me to where I need to be, so that when I _do_ get back to the UK, and I can plug into board and load the code.

#### Jamie

Just strip that UI off.

#### Cliff

Yeah. And you know, I should be a point where just 80-90% of the work is done. And it's just finessing for for the board. And it's all C#, so you can then do things like put suite around it - which you can't do with an Arduino. Not that easily anyway.

#### Jamie

Or if, because it's open-source you could push to a testing branch, some collaborator can go, "yeah, I#ll pull that down and I'll try on my Wilderness board that I have in front of me. This LED has come on that, LED has come on. This didn't work. I've got this report this," maybe I don't know. Maybe you can hook up a small screen it with a hat or something. Or just read the GPIO or something. "Hey, I've got someone who was on the other side of the planet who is awake at the same time, or will be awake in the next few hours, who could try it out for me because it takes five minutes." Give me a report. Sorted.

#### Cliff

Well, I mean, even the hope is that would be out to still link it to the Xamarin app, and use the Xamarin app instead of a screen.

#### Jamie

Oh, right. So you go to like a diagnostic mode?

#### Cliff

So it would report back to that.

I have that working with the Arduino board at the moment. But having a test suite where you can test and build-out, just like you would do with any .NET Core project. And being able to test your code. You know, "I've made this change and it's broken all of my tests. Well, the change wasn't good" Whereas, at the moment you make the change and it breaks, and the hand doesn't move. And it's like, "well, now what?" Is it a software fault? Is it in Xamarin? Is it in the code in Arduino C? Or is it the fact that I've been bending that wire so many times that it's now broken off? That happens every now and again, you look at the wire and it's like, "oh it's broken off," then you have to go and get your soldering iron and solder it back together again.

So yeah, it's been a fun project. I've certainly learned a lot from it, which I think is what everyone likes to do with their side gigs

#### Jamie

Of course, yeah.

#### Cliff

And on their things that they are taking back to their paying customers when they're doing that. I've got the advantage of the fact that the day job pays the bills, and the software stuff is fun. And, it's enjoyable to do and I get come to conferences like this.

#### Jamie

Of Course. Everybody benefits, right?

#### Cliff

Everyone benefits. And hopefully, there'll be a few people that benefit from the project.

#### Jamie

Yeah, awesome. So where can people go to find out about the project? Is it just follow you on Twitter and watch for updates.

#### Cliff

Follow me on [twitter](https://twitter.com/CliffordAgius). I'm quite often post in [#handy](https://twitter.com/search?q=%23handy). That seems to be what keeps getting called, so it's kind of stuck now on. And yeah, my [blog](https://www.cliffordagius.co.uk/) and [GitHub](https://github.com/CliffAgius) are where you'll find a resources and can download the code; come and jump in with PRs. If you see something I'm doing that isn't quite right. Yeah, jump in. Yeah, I'm quite open to feedback him.

#### Jamie

Okay. I'll put all those links in the show notes. Hopefully, yeah, we get some people submitting pull requests, accelerating the... building up the agility of the project, getting out new features sooner and, you know that would be awesome wouldn't it?

#### Cliff

It would. Yeah, and as I've said I have kept the Xamarin projectors as simple, and lightweights as I possible possibly could. The reason behind that is I think a great kind of resource is to look at a project that is actually being used in the world, rather than there being a demoware app, it's an actual app. But is as simple as I can make it. So that people pull it, and if you want to learn Xamarin - you're a .NET programmer, you're writing .NET Core and stuff like that, the jump to Xamarin and putting it on mobile is not that big. It's not that big at all. It looks big and scary, and you think, "wow, I've got all the CI/CD of getting it on to [a device]." But just throw it at AppCentre, and let AppCentre worry about that.

You know, download the tooling that's part of Visual Studio. I even use Visual Studio for programming the Arduino board.

#### Jamie

Oh, right.

#### Cliff

Instead of using the [Arduino IDE](https://www.arduino.cc/en/Main/Software), which, if anyone's used it they're probably bald from pulling all their hair out. It's not brilliant. VS Code uses the Arduino IDE under the hood. So again, you've got VS Code in the loveliness of VS Code, but you've still got the Arduino IDE issues as I say.

Whereas Visual Studio, there's a fantastic tool, which is free, called [Visual Micro](https://www.visualmicro.com/), and it's on on the extensions and plug-ins for Visual Studio. Download that, and install that. The paid-for version just stops it popping up every 5 or 6 times [that] you open Visual Studio and gives you a message, "please buy me." But I think even the paid for is not much - we're talking £50. And it's an awesome tool. So I stay in Visual Studio, and I develop the Arduino C, and I can push to the Arduino boards. And then because it's not the Arduino IDE, I get back my F9 debugging tools, which is amazing. I can put breakpoints, and what happens is when it's a breakpoint: where you put a breakpoint, and you rebuild and republished to the board, what it does is it puts a little `while` loop in there. So when it is at a breakpoint, it waits for a command back form Visual Studio to say, "carry on." A very clever idea. So it just sits there and the board runs.

#### Jamie

`No-Op`in, and just doing nothing.

#### Cliff

Yeah, `No-Op`ing, doing nothing. But you get the breakpoint, and then when you hover over - as you do in Visual Studio - it's reading the memory locations, so you get all your tooling back that you know and love.

#### Jamie

That sort of rich debugging.

#### Cliff

So your F5, your F9, you F11. It's all there. All from this, I'm sure it's about £40 or £50 - it's not a lot at all - for Visual Micro, a great extension. And it means that I'm, used to the keystrokes of Visual Studio, as we all are, and it's all there. And I'm away from the [Ardunio] IDE. And when I install a library, it does it for me, rather than the Arduino IDE where you have to go and find it, install it, and put it in the right place. Visual Micro has managed all of that for me, and I don't need to worry about it.

#### Jamie

That's awesome, I like that.

#### Cliff

It's cool.

#### Jamie

And then pretty soon it might be .NET across the, quite literally, the whole stack?

#### Cliff

Yet the whole stack. Yeah.

#### Jamie

And then it's like, ".NET runs on the phone, runs on the browser, runs on the server, runs on a hand."

#### Cliff

Yeah.

#### Jamie

Like that is a sentence that 5 years ago would not make sense, 10 years ago would not have made sense.

#### Cliff

No. Well, a year ago it wouldn't have made sense.

#### Jamie

Well yeah, exactly. Right?

#### Cliff

The Meadow board was literally kick-started. And I think we all got our boards, kind of, the tail end of last year in November-December time. And my talk to come to NDC was the fact that I was gonna have .NET running in the hand. But because their firmware stack hasn't quite got the point where I can use it. It's not, sadly. But hopefully in the next year, some point after March, when they release his beta 4, we'll be able to put it .NET everywhere. And in the future, I'll be able to talk a bit more about the .NET stack. All of it. I think the only this missing is the cloud. I suppose AppCentre is the cloud, isn't it?

#### Jamie

Yeah, right. There you go.

#### Cliff

Yeah, I suppose someone from Microsoft could come and tap me on the shoulder and say, "you need to put an Azure function in or something."

#### Jamie

Yeah

#### Cliff

Someone will think up some way of needing that. But the moment I don't think we are using that.

#### Jamie

You could use an Azure function to push the update to the phone, which then pushes the update to the hand.

#### Cliff

There you go. You see? You should work for Microsoft in their sales team.

But yeah, it's a great project, it's been fun, and I've learnt a lot. And most importantly, put smile on Kaydens Face. And when I gifted the early version of the arm for his 15th birthday, I literally pitched it up at his door. His Mum knew about it, He didn't. And open the box, and he sees this arm. The look on his face, the smile. You know, the kind of little giggly scream that he made going, "oh this is cool. Look at how cool this is." That was worth more than any money they could have given me for doing this. I've done it all off of my own back, any money that's been put into it has come out of me funding it, so the family don't have to own the cost. Because a lot of this has been really trial and error, and they shouldn't bear the costs.

#### Jamie

Of course.

#### Cliff

Nut hopefully, once I got it complete to the point that I'm happy that others should build these, there'll be a full bill of materials, "these are all the parts you need. This is where you buy them from." There are a few parts that are easy to get from the likes of Amazon, RS Components, AdaFruit, those kinds of things. There are a couple of components where you have to get to specialist suppliers, but they're like the springs I mentioned earlier that I'm looking for a different version that will do the same job, either to make the price cheaper or to make it easier to obtain, so that you don't have to wait 3 weeks lead time for a part to come from the other side of the world.

But yeah, and that will be hopefully at some point next few months we'll get to that stage. And then people start building these themselves and have a little arm that sits on their desk and moves around for them.

#### Jamie

It's brave new world. I love it

#### Cliff

And it's all built on .NET - or will be soon.

#### Jamie

Yeah.

Well, thank you ever so much for talking with me. This is an amazing product an amazing... well, is it a product? It's an amazing project.

#### Cliff

I never plan to sell this. I'm never gonna sell it. It's always going to be free, open-source for people to download. If someone doesn't have the skillset to build it, download it, or it doesn't have a 3D printer. Yeah, contact on Twitter or email. And yeah, I'm happy to help out. If you just need the 3D printing done, let me know, and I'll 3D print the parts. And you can do the rest yourself. Or if you're not very proficient at soldering, let me know, and I'll solder the board together for you, and we'll collaborate and do it that way.

#### Jamie

Or indeed you could build up a team of like I know I'm no good at soldering, but I can go to someone I went to uni with who did electronic engineering and I could say, "look, do me a favour. It's a couple of hours, but can you solder this stuff for me?" And they'll go, "sure. Done." You know, call in a bunch of favours.

#### Cliff

I mean, them sorts of skills: the soldering, the electronics, the wiring. I got taught in my apprenticeship when I was at the Ford motor company. So I did electrical engineering, but half of that was electronics as well. So we got taught, you know, fine skills at doing soldering, de-soldering, using solder wicks and stuff like that. So I spent weeks, if not months, learning solder. And them skills that I learned then, are coming back, you know. It's like when you learn trigonometry at school, "when am I ever gonna use this, sir?" Whereas now, actually, I'm using it and it's kinda cool.

#### Jamie

Thank you. Like I said, thank you for having a chat. And I'll see if I get as many people to click through, and figure it all out, and help you out in some way. I'm sure somebody can help in some way.

#### Cliff

Yeah. Someone with machine learning skills.

#### Jamie

Yeah, that's it right? We'll have to start poking people as we walk round. "Do you know machine learning?" "Do you know machine learning?" And get them all to help you out.

#### Cliff

Cool. Excellent. Thank you very much.

#### Jamie

Thank you ever so much.

### Wrapping Up

That was my interview with Clifford Aguis. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/), and there will be a link directly to them in your podcatcher.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice - head over to [dotnetcore.show/subscribe](/subscribe) for ways to do that - and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Cliff on twitter](https://twitter.com/CliffordAgius)
- [Cliff's website](https://www.cliffordagius.co.uk/)
- [Cliff's GitHub Repositories](https://github.com/CliffAgius?tab=repositories)
- [Cliffs talk from NDC London 2020](https://www.youtube.com/watch?v=WHL2v4mXbRE)
- [faffing](https://en.wiktionary.org/wiki/faff)
- [Heath Robinson](https://dictionary.cambridge.org/dictionary/english/heath-robinson)
- [Reprap Mendal](https://reprap.org/wiki/Mendel)
- [Prusa Mini](https://www.prusa3d.com/original-prusa-mini/)
- [Open Bionics](https://openbionics.com/)
- [Open Bionics GitHub](https://github.com/Open-Bionics/Brunel)
- [AdaFruit](https://www.adafruit.com/)
- [BlueFruit M0 AdaFruit board](https://www.mouser.co.uk/new/adafruit/adafruit-feather-m0-bluefruit-le/)
- [AVR processors](https://learn.adafruit.com/neopixels-and-servos/introducing-avr-peripherals)
- [Actuonix](https://www.actuonix.com/)
- [my GitHub](https://github.com/CliffAgius?tab=repositories)
- [Anker power bricks](https://www.anker.com/products/taxons/107/power-banks)
- [Pololu](https://www.pololu.com/)
- [UART commands](https://www.circuitbasics.com/basics-uart-communication/)
- [EEPROM](https://en.wikipedia.org/wiki/EEPROM)
- [Wilderness Labs Meadow board](https://www.wildernesslabs.co/meadow)
- [F7 micro board](https://store.wildernesslabs.co/products/meadow-f7)
- [AdaFruit Feather](https://www.adafruit.com/feather)]
- [Arduino C](https://www.arduino.cc/reference/en)
- [GPIO](https://en.wikipedia.org/wiki/General-purpose_input/output)
- [MyoWare sensors](https://www.pololu.com/product/2732)
- [Hacker Space Magazine](https://hackspace.raspberrypi.org/)
- [Piezoelectric sensor](https://en.wikipedia.org/wiki/Piezoelectric_sensor)
- [Potentiometer reading](https://en.wikipedia.org/wiki/Potentiometer)
- [Hero Arm](https://openbionics.com/hero-arm/)
- [Xamarin Essentials](https://docs.microsoft.com/en-us/xamarin/essentials/)
- [Xamarin Shell](https://docs.microsoft.com/en-us/xamarin/xamarin-forms/app-fundamentals/shell/introduction)
- [SyncFusion](https://www.syncfusion.com/)
- [Jean-Marie Alfonsi](https://www.sharpnado.com/hire-me/)
- [Sharpnado](https://www.sharpnado.com)
- [AppCentre](https://appcenter.ms/)
- [Hot Restart](https://docs.microsoft.com/en-us/xamarin/xamarin-forms/deploy-test/hot-restart)
- [knackered](https://dictionary.cambridge.org/dictionary/english/knackered)
- [#handy on Twitter](https://twitter.com/search?q=%23handy)
- [Arduino IDE](https://www.arduino.cc/en/Main/Software)
- [Visual Micro](https://www.visualmicro.com/)
