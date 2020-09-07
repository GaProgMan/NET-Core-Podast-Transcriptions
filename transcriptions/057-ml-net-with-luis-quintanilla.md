### Episode Transcription

### Sponsor Message

ARE YOU A DEV is the only program exclusively for .NET developers, learn how to prototype, code, launch and market your mobile app product whether you're an indie developer starting out or a dev lead wanting to bring mobile development in-house.

Interested in ML.NET? ARE YOU A DEV shows how to utilise ML .NET in your mobile product, walking you through the code, functional limitations and the privacy implication you need to be aware of when using machine learning.

Try out the program for free at {{< sponsor-link link-text="areyouadev.com" link="https://www.areyouadev.com/" >}} - that's {{< sponsor-link link-text="areyouadev.com" link="https://www.areyouadev.com/" >}}  and get a complimentary 20 minute 1 to 1 chat with a fellow developer to ask any program or technical questions

---

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is Episode 57 - ML .NET with Luis Quintanilla. In this episode I talked with Luis about just what machine learning is (and how it's different from general artificial intelligence), what ML .NET is, the many ways that you can leverage it in your applications, and what the future might hold for machine learning in the .NET space.

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

{{< paracentre "The following is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

#### Jamie

So thank you ever so much, Luis for spending part of your morning, my afternoon because time zones are so fun, right? But thank you so much for agreeing to be on the show and talk about ML - machine learning. Or as some people call it, "artificial intelligence, the sky is falling!" Because I literally have no idea when it comes to this stuff.

#### Luis

Yeah, no. Thanks for having me. I listen to the podcast, I you know, a few episodes. And I really like what you're doing here. So thanks. Thanks for giving me the opportunity. And hopefully we learn a few things here about machine learning.

#### Jamie

I'm sure we will. Because you know, you're a bit of an expert.

#### Luis

Yeah, you could say that.

#### Jamie

Could you introduce yourself a little bit to the listeners? We know you called Luis but like who you are, what you do? That kind of thing.

#### Luis

Yeah, absolutely. So I am a Content Developer at Microsoft. I've been in my role for a little bit over a year. And I've basically been working on creating content for different technologies on the Microsoft Doc's website. Right. And those technologies include ML .NET, .NET for Apache Spark and Azure machine learning, right. So I'm, I'm based out of the New York City area just outside of New York City in New Jersey. Prior to working at Microsoft, I worked in consulting, so I helped companies in various industries, whether that was hospitality education, sort of think about and implement AI and machine learning solutions for their businesses. Prior to that, I was in the financial services industry. So I've kind of jumped around a bit. But it's it's been a fun experience.

In terms of working in the ML space. I've been here for, you know, I've been working on it for a few years. And again, I've used various tools, mostly working with Python, which tends to be sort of - nowadays, it tends to be sort of the platform of choice for building these workflows. But I do I have a very special place for .NET. I actually dabbled in .NET, pre .NET Core, but I didn't dabble in it too much. And it wasn't until .NET Core that I was sort of like, "okay, well, there's a sort of clean slate that I can kind of get on board right and and sort of start trying this stuff out." And I immediately fell in love with the languages, fell in love with the tooling. So I really like the community and I like the direction that .NET is heading. So I'm just excited to be here talking about .NET and how I can apply that, and how we can use that with machine learning.

#### Jamie

That's awesome. I do, like I said, I don't know very much about machine learning. All I know is that it's a Python thing, right? You need to know Python to do the machine learning. But we'll come back to that in a moment.

#### Luis

Yep.

#### Jamie

Yeah, you've mentioned there was a Virtual ML Conference. So just a few weeks before we recorded this, there was a Virtual ML .NET Conference. Was this the, was it maybe the first one? Is it something that as a complete novice, I can approach, or is it for ML .NET professionals who've done it for years and years?

#### Luis

Yes. So that was a nice thing. It was the first one so that was really great. You know, we'll talk a little bit about this later. But ML .NET has only been around - or at least open source iteration of it has only been around for two years. So it's it's fairly new. It's, you know, the new kid on the block, relatively speaking.

So the conference itself, it was the first one it was organised by the community and for the community, which great. And what happened there was it spanned over two days. Bri [Achtman] - who is the the PM on the on the ML .NET side - she and myself we sort of ran a [workshop](http://mlnet-workshop.azurewebsites.net/) the first day where we sort of went, you know, the end-to-end: so everything that you need to know about ML .NET you know, or at least we covered most of the basics of ML .NET to help you get started. And then on the second day, you had a lot of really great talks from from individuals, folks from the community and everybody just talking about different use cases and ways that you could leverage ML .NET, within your applications. We also had a few sessions, we had interviews that we did with with some of the customers that are using ML .NET in production. And again, it was just a way for to bring awareness and a way for people to become acquainted with ML .NET, and the things that they could do, and how they can leverage it inside of their applications.

It was actually well received for being the first one. It was well received, well attended, and a lot of that you know, I think that goes you know, hats off to the organisers who who did a really great job of putting this together. And it was completely virtual, right. So the nice thing that is certainly COVID has changed how these types of events takes place - I'm sure you saw Build -  that as opposed to being in person now everything was virtual. And and there's a lot of benefits to that, right? Like the reach that you have, and you sort of democratise, who can and can't attend your events,; the fact that everything's sort of recorded and after the fact, if you weren't able to make the event, you can access that sort of on demand. There's a lot of really great benefits to that. So again, it was very well attended. And by all standards, it was it was a really a great success, you can certainly feel that there's a buzz. In terms of the community, there's a lot of people that are sort of engaging, they're they're talking, they're they're collaborating on different projects that might help or at least bring awareness to ML .NET. And, and that's great. You know, there's, there's even a virtual community that came out of it, you know, probably can include in the show notes at some point. There's a community on slack that you can join, and you can sort of continue that conversation and talk with individuals who are just as passionate about making use of ML .NET.

So yeah, it was again, great success. And we would love to keep putting on these types of events. Again, to sort of continue to bring awareness and continue to educate individuals on how they can take advantage and build more intelligent apps. Again, using the the tools and using the languages that they know and love in .NET.

#### Jamie

That's really cool. That was gonna be my follow up question is, "we've just had one other gonna be any more?"

#### Luis

We certainly hope so. There's a, you know, it takes a lot to put on these types of events and try to get them right. And there's there's always gonna be challenges, of course, right? With these virtual types of events. But overall, yeah, we would be excited and happy to continue to put on more events and different types of events that allow folks to engage in different ways.

#### Jamie

Sure, that's awesome. I do like this idea of democratising it because this year was the first year I've ever been able to attend MS Build, because it's either been in some very expensive place in the States or in the States. Sp just getting there is difficult enough, you know.

#### Luis

Exactly, yeah, well, I mean, it was my first one as well. So.

#### Jamie

Like you say, because it's all recorded, you can watch it all afterwards, it makes it so much easier. And yeah, running these virtual events isn't easy. As we record this, I'm actually going to be giving a talk at one next week that is for the Northeast of the UK. And we've been told that we have to use OBS to record it ahead of time, use this particular thing, upload a version of it here for sort of review, get your friends to peer review it and submit all sorts of things ahead of time. And that's just for a, I think there are eight or 10 talks across an entire day. So I can't even imagine what it's like for let's bring lots of people in from different communities and different companies and then put it under the banner of - and I don't wish this to sound bad in any way - but Microsoft is uber professional. "Let's do it professionally." You know what I mean? Not just, "let's just sort of hack it together. It has to be done really well." So, hats off to everyone who organises them, big and small I think.

#### Luis

Yeah, absolutely. I mean, I think, you know, after going through this experience, I have a newfound respect for content creators and folks like yourself who create this content, right? It's It's not easy people sort of see the finished product, but sort of the behind the scenes and what's happening and all the things that you need to manage to make sure that the product comes out well, and, and and it's something that's enjoyable to everyone. It's challenging. So yeah, I mean, I have a newfound respect for producers and folks that are working behind the scenes to make sure that these events are great.

#### Jamie

Yeah, absolutely. Absolutely. Let's talk about machine learning and ML .NET then. So like, I know that ML .NET - or at least machine learning is not this one small thing right. I did, at university when I did my computer science. We did two separate, I guess, semesters - there's one course that covered two separate semesters on artificial intelligence, machine learning, and the background, where it came from, the whole Prolog versus Lisp versus this language versus that language, and how all the different algorithms were created. And then we get to now and it's like, "throw all of that out the window, because let's learn Python." And then that happens. And then it's, "throw all out the window and just learn .NET and you can do it all." Right?

#### Luis

Yep.

#### Jamie

So with that being said, do I need to know Python to be able to use machine learning if I'm using ML .NET?

#### Luis

So the short answer to that is "no, you don't." You can get started with ML .NET using the, again, the tools and using the languages that you know and love, which is really great. And, you know, I think, you know, there's no denying that that Python is sort of the, you know, the standard now or what a lot of the libraries and popular libraries are being written in.

That being said, there's a bit of a positive to sort of not being the dominant platform, right. You can think of that right. It's one of the things where, you know, if you're behind if the one that's in front of you falls off the cliff, you're able to sort of learn from that mistake and and sort of not make that same mistake yourself, right. And you're able to learn from the challenges that this other more popular platform and community have sort of encountered, and you're able to learn from the problems that they've solved. So from a .NET standpoint, you know, you're able to take a lot of those learnings and sort of make the product better from a .NET standpoint. Well, at the same time, you know, making sure that you're still staying true to your community, you're still staying true to the way that your users are using the tooling and are using the languages to build applications. So short answer is no, you definitely don't need to know Python to use ML .NET or to do machine learning with .NET.

#### Jamie

Okay, does it help in some way? I'm not saying, "definitely go out learn Python," but if you know a little bit, and you can sort of figure it out, does it help? Or does ML .NET just hide everything away? And you just say, "here's my model, go do the thing that you need to do."

#### Luis

I think that If you have worked with, with Python before, and whether you use libraries like [scikit](https://scikit-learn.org/stable/) to  build your machine learning models, there are certain parallels that it's not so much on the functionality and what you're doing with the library itself. But it's more of on the process, right? So if you're using those types of libraries in your work with Python, or you work with R, you know that you are loading your data, you're transforming your data, you're using an algorithm to train your model. So if you've worked with it, and you are familiar with the steps involved with creating a machine learning model with these types of libraries, bringing that sort of knowledge into ML .NET helps, right, it certainly helps. That being said, you know, the tools themselves, they work differently enough or they have significant differences to the point where, you know, you don't necessarily need to know one to be able to use the other.

#### Jamie

Okay. It's a bad metaphor, but I guess it's like C# and the IL that it creates, right? You don't really need to know that much about IL. But if you know a little bit it will help you to create slightly better, slightly more performant C#.

#### Luis

Yeah, absolutely a good you can think about it that way. Yeah, absolutely.

#### Jamie

Okay, so let's say I want to get into ML .NET. What's the, is it just `nuget install machine-learning`? What's the...?

#### Luis

Actually it's even easier than that. Right. So there's many different ways of interacting with ML .NET. And it really depends on what your preferences are. So it could be as easy as using, you know, `dotnet add package` on the CLI or managing NuGet packages.

So there's the code first approach, right where you can use an API and you have full control over what it is that you're building. That of course requires a little bit of knowledge on your end in terms of what you're trying to do the types of transfers that you're trying to achieve. Still with the code first approach, you have this other API called the Automated ML - or [AutoML API](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/how-to-use-the-automl-api). And what the AutoML API allows you to do is it allows you to essentially try to find the best model given your problems. So you just need to give it, "here's my data set. Here's the problem that I'm trying to solve. I'm trying to find a numerical value and I try to categorise values," what is it that I'm trying to solve? And then based on that, I sort of let AutoML try to pick the best model for me and it will try different algorithms, different parameters to try to find it will search the space of algorithms to try to find the best model, right? So again, that's a code first approach. And it's easy enough, but again, it requires some some prior knowledge.

Now, a level above that. And really, the easiest way to get started with ML .NET is the tooling, right? So you have tools like model builder, which is a graphical user interface that's built into Visual Studio at least. It's been built into Visual Studio since version 16.6. of Visual Studio, and what model builder gives you inside Visual Studio is a graphical user interface for both training and consuming your models in your .NET application. So it's as easy as you create your project - that's an ASP. NET Core application, WPF, whatever .NET application is that you're building - and you just right click and hit "Add machine learning", and then it sort of takes you to a wizard. And this wizard takes you through the process of loading your data, telling it what type of problem you're exactly trying to solve. You're able to evaluate your model to make sure that once your model is trained, you can evaluate it to make sure that it's performing as you would expect it to and then at the end, what you get is you get code that's auto generated for you that allows you to easily consume your model inside of your end user application. Right? So you have that piece of it. There's the there's model builder, and again, model builder leverages AutoML to try to find that best model so it's iteratively searching, "for based on your data and based on your problem what is the best model for you to use?" The CLI, there's a CLI component as well, which it works very much similar way it's built on top of AutoML. But that, again, there's no graphical user interface, but you're using it through the CLI, and again, because it's cross platform, just like a lot of .NET tools, you can use it on Windows, Mac or Linux, right? So you're not constrained to just using inside of Visual Studio. And the nice thing is, you know, you can of course, there's the benefit of being able to use that within Mac and Linux environments, right - or Unix environments - but the other real benefit that comes from using the CLI, or where it can be sometimes beneficial to use a CLI, is inside of continuous integration and continuous deployment pipelines as sort of some automated process of sort or some machine learning operations pipeline or [MLOps](https://en.wikipedia.org/wiki/MLOps), to again iteratively train your models based on whether that's changes to your data, or whether that's changes to your to the code that is used to build your machine learning model.

#### Jamie

Wow. Lots of different ways that we can use machine learning in our .NET applications. That's amazing. It isn't just like, "here's the process and go adapt you're code." It is like, "here are a bunch of processes. And you pick the one that works."

#### Luis

Yeah, absolutely. Yeah. And, you know, that sort of went on a sort of longer answer, but the short answer is model builder and CLI.

#### Jamie

Sure, okay. The only real example of ML .NET in action that I've seen was I once saw a talk by Scott Guthrie where he crafted - in about 5 10 minutes - an application that was able to tell whether you gave it a picture of him or a picture of a cat.

The ML field - the machine learning, artificial intelligence, whatever field - is huge. And we go through waves of, "machine learning is the greatest thing ever," and then, "artificial intelligence will kill us all." Now, when I'm talking to my non-developer friends, and they're going, "artificial intelligence is the worst thing ever." And I say, "it takes about three days to teach a computer what you look like this. It's taken millions of engineering hours, to gets to the point where it can classify within 90% probability, whether it's a cat or not. So we're decades away, hopefully, from all that horribleness." But what my question to you is, have you got a quick description of what machine learning is? You know, because there'll be people who will come in and gone, "Oh, machine learning. That's great." And I thought, let's get the "Get Started" bit done. And let's talk about what machine learning is. Just for a couple of minutes. I wonder if, because everyone I speak to has slightly different versions of what machine learning is. And very few of them can talk about it without saying artificial intelligence. So in that kind of, they are related, but are they the same thing?

#### Luis

Yeah, absolutely. So it can sometimes be interchangeable. And it can sometimes the terminology can be a little confusing. But typically, one of the ways when I talk about this is you have artificial intelligence, which this broad umbrella that sort of everything sort of falls under right. And AI, you know, you mentioned that in your courses. You took a few courses that taught you about AI and different ways to solve AI problem(s). So if I think, you know, usually, if you're taking an AI class in university or you you take a course that's purely based on AI, you're going to learn something about search algorithms, right? So you're going to learn about [A* Search](https://en.wikipedia.org/wiki/A*_search_algorithm) and these types of things.

Which is great, but it's not necessarily machine learning, right? That's just AI and and what AI ultimately was trying to do is, you are one way to think about AI is rules based systems, right? So AI is this way of thinking about, "there are processes that I as a human usually do. And if I have some sort of agent that is doing them on my behalf," think of like a spam filter or something like that: you provide rules to your inbox saying, you know, "ignore all the messages from this person," or, you know, "move these items into this particular folder." And now you have this sort of autonomous agent that is doing that for you. But at the end of the day, what you're doing is _you're_ giving the system the rules, right? And the system is operating within these rules, which is it's great, right? And it works at a small scale.

The problem is, can you scale? And how can you start building rules about complex systems? So for example, in the example you're giving, what does it mean to determine what a cat is? Like how would you even begin to code the rules for a system like that? So machine learning, what it does is you give it examples. And based on those examples, it learns what the patterns are, and the relationships in the data are. And then what it spits out are, what it thinks the rules are to make decisions based on data and based on examples, right? So machine learning is a subset of AI in the sense that it's using algorithms and data to learn and become intelligent, and still perform the autonomous tasks that you want it to and behave autonomously. But again, it's using data to back that rather than you [providing the samples](https://github.com/dotnet/machinelearning-samples) and input right? As far as how the environment and what the world It operates in should look like. So that's a way to think about it.

In terms of are we far away? Yeah, we're certainly very far away from, you know, sort of Skynet scenario. The current systems - while they're very advanced, and they're very useful in a lot of scenarios - they're still very limited. And they're very targeted. There are some techniques like [Transfer learning](https://en.wikipedia.org/wiki/Transfer_learning), right, which is actually one of the things that ML .NET leverages to train custom image classification models. Which basically what that allows you to do is it allows you to take a problem that is solved, and then you apply what you've learned for that particular problem to a similar, but unrelated problem. And you're able to sort of transfer a bit of that knowledge and you're able to sort of teach your models or customise your models for whatever domain it is that you're using, you're able to train them at a faster rate, right? Because now you're not sort of learning from scratch you're learning based on you know, prior knowledge that you had before.

That being said, though, you know, it still doesn't get you towards what the real goal is, which is [general artificial intelligence](https://en.wikipedia.org/wiki/Artificial_general_intelligence). Which general Artificial Intelligence, that's kind of the Skynet scenario where, you know, you have this system that sort of able to autonomously learn new things, right? And learn different things based on, you know, different contexts and things like that. So we're still very far away from that. So yeah, I would say that at the moment, there's no need to worry. But it shouldn't be something that's part of the conversation, right?

It should be something that's part of the conversation as it relates to, "well, what does it mean for AI, and what does it mean for machine learning systems that are becoming more and more ingrained in our society, to make decisions for us and to make the decisions that impact us as as human beings as well as our society?" So those types of conversations certainly need to take place, and it's better to have those conversations early rather than you know, when things sort of go haywire. So yeah, it's it's very important to think about, but in its current context, not necessarily something that should be something that you that you worry about: that the robots are going to take over.

#### Jamie

As a consumer of a library, I shouldn't really be worried about the ethics of what's gonna happen potentially in the next 20 30 40 50 years. But to know that that conversation is happening is a good thing. But then I don't need to worry about it. Because all I'm doing is classifying these images or this data, you know, I'm looking at a bunch of bar charts, or a bunch of data around a specific group have something, some kind of measurement. Whether it's an image, a bunch of numbers or some text - maybe I'm analysing some text for sentiment or something. I don't need to know that at some point in the future, there is already going to be these rules and ethics around it. Because all I'm doing is dealing with this text, right?

#### Luis

Yeah, absolutely. And actually at Build there was a sort of a - this is not necessarily related to ML .NET - but it's certainly within the AI space and kind of within the context of the conversation we're currently having. There were a few systems that, for example, Azure Machine Learning, that's called - you know, if you were to have a term for all these systems and tooling that Azure Machine Learning has and these open source systems it "[responsible machine learning](https://azure.microsoft.com/en-us/services/machine-learning/responsibleml/)" right? And that deals with making sure that your models are fair, and that you can understand your modele. Because like you can have the best performing model, but if you can't control it, if you have no idea why it's making the decisions that it's making - especially in those cases where it's it has a direct impact on people's lives, right? It's worrisome, right? Because you're not able to determine why a particular model is behaving a certain way. And as a result, when it's making wrong decisions or biassed decisions, or you know, something that is negatively impacting people not being able to fix it, right, it becomes a real problem. And then the other thing is these systems, they need data. They need lots of data. And where are you going to get this data from? Chances are that it's some of it might include personal data. So what does it mean to preserve data privacy and preserve the confidentiality of the users whose data you're using to build these intelligent systems? So again, it's stuff that is definitely been talked about. It's definitely stuff that is being addressed. Yeah, it should be considered. But again, as it relates to the capabilities of the systems at the moment, they're not there yet in terms of you know, taking over.

#### Jamie

Yeah. I don't have to worry that my website's chat bot is somehow going to launch nuclear weapons or anything.

#### Luis

Yeah.

#### Jamie

As long as I've separated my conserns out correctly, then then launch nuclear codes but should be somewhere else in the codebase. Right.

#### Luis

Absolutely. Yep. Single responsibility principle.

#### Jamie

There. That's it.

Okay, so we've hinted a number of things that, you know, we both said a classification of different types of data. I mentioned chatbots. I think I said something about reading through text and things like sentiment analysis. These are the presumably the sort of bread and butter tasks that ML .NET can help with - the non trivial tasks of, "I have oodles of data. Go find me the answer."

#### Luis

Yeah, absolutely. And yeah, so you can use ML .NET for a lot of your traditional sort of classical machine learning problems again, classification regression. So you know, whether you're predicting a numerical value, you're classifying objects, you're categorising images, you can use in classical machine learning scenarios. You can also use it for deep learning scenarios, right. So that's, again, your image classification, object detection, right, which is something that's useful for cars, right? Self driving cars, definitely leverage to some extent, object detection, among other use cases. And and you can do both of those with ML .NET.

So that's one of the really nice things about ML .NET is that while you're encouraged, or it's intended to be used within the .NET ecosystem, it's extensible, right. And what that means is you're able to - in the case of image classification - you're able to both train models, custom models with ML .NET, and the model that's output is both an ML .NET version of the model as well as a [Tensor Flow](https://www.tensorflow.org/) version of the model. And TensorFlow, for folks who may not be familiar, it's a very popular library for building machine learning and especially deep learning types of models. And so you can do that and we can train these tensor flow models with ML. NET. You can also consume tensor flow models. Not only limited to using image classification, but let's say you have a text classification model that is a TensorFlow model. You can consume that and use that inside of your .NET applications using ML .NET.

The other thing, it's like, "okay, TensorFlow is great. But you know what, I don't use that I use other frameworks." Another method of interoperability and extensibility that ML .NET gives you is the ability to work with [ONNX](https://onnx.ai/) models - or Open Neural Network Exchange. And open neural network exchange, what it is, it's a format, you can think of it as a format that other frameworks may choose to sort of allow both export and consumption of, right. So let's say that you've trained your model in scikit-learn, or you train your model with [PyTorch](https://pytorch.org/), which is another popular framework for building deep learning models and machine learning models. But at the end of the day, you have to get this model working in your WPF application. So what do you do?

Well, you take the model that's built in PiTorch, TensorFlow, or scikit you convert it into ONNX - the sort of standard format. And then from ML .NET, you just you're able to consume that, right? So you're able to take that model and use it inside of your .NET application with the help of ML .NET. So that level of extensibility, right, is one of the things that really helps, ML .NET shine is like, "okay, well, you can use and you can stay within the .NET domain and building ML .NET type models. But you're not constrained to that." So what that allows, it allows for you to, for example, let's say you have your data scientists that are building the models, and then you are worried about the end user application and making sure that that application is able to leverage those models, you're able to have both of those worlds sort of come together, and talk, and communicate, and be productive in a fairly seamless way.

#### Jamie

I do like that, because, you know, if I need to get some data scientists to do some data sciencey things, I'll literally say that because I have no idea about that whole ecosystem - anything they need to know about. And so making that easier for the two teams, the two people to interact and say, "well, there's my data." "Right, here's the model. It's in an open standard." "Oh, brilliant, I can just throw that into ML .NET. And it will do the wizardry magic that it needs to do". And then we get a message at the end, "90% probability, cat."

#### Luis

Exactly. Yeah. And that's really the goal, making sure that it's as easy as possible to get these models into production, right? Because that's actually one of the challenges, "how can you get these models into production?" You can have the best model, and you can experiment and find you know, what the best parameters are and stuff like that. But at the end of the day, if you don't get these models into production, it's almost kind of a waste of time, right? So it's important that it's easy to get these models into production. And you know, ONNX sort of is a way for allowing that and not only can you do that from within your traditional applications, right, but an area where it really shines and where machine learning is kind of going to the edge, right and your IoT devices. So yeah. It's great that with ML .NET, and ONNX, you're able to leverage those scenarios.

#### Jamie

That's great. Okay, so then is "this pull down a library"? The code runs on my machine? Or, because we talked about Azure Machine Learning a few times, is it "I can run it on my server or on my instance," you know, not necessarily a server these days, but inside of my - let's play buzzword bingo, right? inside of my Docker container that's running on a Kubernetes cluster, or somewhere on Azure or somewhere. Is it both? Is it just the one? Do I need a huge amount of CPU time is what I'm saying?

#### Luis

The answer is yes.

### Sponsor Message

I'd like to take a moment to tell you that this episode is sponsored by Datadog. Also stick around for the next 30 seconds to find out how you can get a free t-shirt!

Datadog are a monitoring and analytics platform which monitor your infrastructure, application performance, and log management.

Are you looking to move to the cloud, microservices, or .NET Core? Datadog can help with that. Their distributed tracing and APM provide end-to-end visibility into requests wherever they go. Whether it's across hosts, containers, or service boundaries.

See for yourself! Start a 14-day trial today, and Datadog will send you a free t-shirt!

Find out more at {{< sponsor-link link-text="datadoghq.com/dotnetcore" link="https://datadoghq.com/dotnetcore" >}} - that's {{< sponsor-link link-text="datadoghq.com/dotnetcore" link="https://datadoghq.com/dotnetcore" >}} - or check the show notes for a link.

---

#### Luis

You know, this statement is either going to age really well, or it's really not going to hold or stand the test of time. But I do think that .NET, at some point it will become one of the best platforms to at the very least to deploy machine learning models to right. And why is that? It's because .NET is everywhere. You can do IoT with dotnet. You can do games, right, with the Unity. And one of the things that you know, folks may not be aware of is with Unity, you might think, "okay, well, you know what, I will never code or write a game or build a game." But actually Unity, you can build AR and VR application with Unity, right. So now you have that other sort of, you know, platform to deploy and build applications for for AR. You know, you can do the desktop, right WPF. With .NET Core 3.1, you now have the ability to build WPF applications with .NET Core 3.1. You know, long story short, you can deploy work to so many places, right?

So going back to your question is like, "can I run this inside of my Docker container and my Kubernetes cluster?" The answer is yes, because you can containerize ASP. NET Core applications and deploy them to Kubernetes cluster, you can't do that, right? Conversely, you also have the IoT scenario where you're able to if you can run .NET in this IoT scenario, you should also be able to build and run your applications - your machine learning models - inside of an IoT type of device, right? So, in terms of where you're deploying and how you're using these models, it's really depends on where .NET runs. Now there are some scenarios where there are some limitations. But that's not to say that you couldn't do it right. So what I mean by those limitations are, there are some things within ML .NET, that require native code. So perhaps that may pose a challenge to whether you can run it on a particular platform, right. But again, because you have proven that .NET runs on this platform, such as web assembly, right, if there are some tweaks or there could be changes made, so that now you can get ML .NET, which is .NET code, you know, running on this platform, then it should be fairly trivial to get those scenarios working. But again, because it's all dotnet, and it can deploy to any of those target platforms. Ideally, you should be able to use them with .NET from any of those devices and deployment targets.

#### Jamie

Just thinking about that, the ".NET Anywhere" is just, It's amazing. There are a number of people I've talked to on the show who have kind of underlined and highlighted that ".NET Anywhere" idea. So I remember talking to Jim Bennett. And he said, "yeah, I really want Microsoft to pay to have me bring a Samsung Tizen fridge onstage and we deploy my app to it. Because can you imagine .NET on a fridge?" And then just this year, in January, I was talking to Clifford Agius, who is built the handy project. And he was saying, "yeah, I just need to get this Meadow board. And then I got .NET in the hand," and I'm like, "that is not a sentence that should be said."

#### Luis

Yeah, the folks over at wilderness labs, they just had their conference. And they showed off a lot of really neat things where you can run .NET on these microcontrollers, which is it's amazing, right? You can run .NET and these sort of low power devices. And and that's kind of where - in terms of machine learning or machine learning trends - that's kind of also where it's going right? You want to be able to make decisions as it's happening in real time. And the way that you do that is by putting machine learning on these edge devices. So it's really great that it you know, because that can run anywhere, they you have those scenarios enabled where you can either run it on a device on a microcontroller. Or you can also scale up to a Kubernetes cluster. And really, it just depends on what your use case is. But again, there's from a platform standpoint, there should be relatively few, if any restrictions for you to do that.

#### Jamie

Yeah, like I said, it blows my mind all of these different devices. And you know, I recorded an episode, not so long back - at the time of recording - with UK MVP [Pete Gallagher](https://www.petecodes.co.uk/), and he was talking about all the different IoT things and I'm like, "this is just amazing," and we just sat geeked out for about an hour. Like, I think he said "smart cows" at one point, which is like we do with insemination of cows, you can use IoT and artificial intelligence - or rather machine learning - to figure out the peak time to do that and all this kind of stuff and it's just like, "yeah but, you've just said smart cow. Internet enabled cow, I'm not sure that's a sentence that I really want to think about."

#### Luis

It's actually interesting that you bring that up. So there's actually customer stories in terms of how he how customers are interacting and using ML .NET across various different scenarios and use cases. But one of them is hazelnuts, right. So getting hazelnuts into sort of the state where they're ready for human consumption, it's a pretty laborious task. And it can be error prone. And you know, you have to constantly monitor and sample and make sure that the conditions such as temperature, moisture, and things like that are just right. So sort of very similar to your cow scenario, "when is the right time to take some action?" right.

So what this customer did was they went ahead and they put sensors to measure temperature moisture inside of their dryers for hazelnuts. And using a machine learning model, they are able to determine and be alerted, "hey, The conditions are just right, so that you can now take out the hazelnuts from the dryer," and you know, package them or do whatever it is that else that you need to do. So, I mean, there's another scenario where there's IoT, there's machine learning that's enabling sort of this use case that you might not think that that you know, these technologies fit into, but you know, it's been successfully leveraged by by these companies and these these customers.

#### Jamie

That's it. There's so many - and I want to use the bunny quotes - the hidden aspects of civilization. I don't mean to say that they are somehow behind doors, or anything like that. But there are so many things that the majority of people don't even really realise. I saw a demo, it was image classification, but it was a demo of soldering circuits. And they were saying, "there's a machine that does the soldering, and millions of boards go past every second, we need to classify whether the contacts have been made, and it's a good join," I guess, or whatever the verbiage is. And they said, "what we did was we use machine learning." You know, it was a very, like you said, a very labour intensive task. If one person would have to look at an image, that's fine. Next one, that's fine. Next one. Whereas if you can pass the images in as they go past the machine, and decide there and then in that few milliseconds, "no, that one's no good. Put it in for a recycling or get a human to redo it or something."

#### Luis

Yeah, absolutely.

So we actually have a sample on a somewhat related to what we're talking about on docs for ML .NET. And what this uses it's a data set from I forget what it's some University here in the United States and it's a data set of different infrastructure. So we've narrowed that so I think I believe we do sidewalks right? And we're able to we're trying to do is basically determine, "is this sidewalk or a piece of infrastructure, whether it's a bridge or wall sidewalk, is it cracked or not?" Right. And in the scenario that we have, it's fairly simple, right? But you can think of how you can sort of scale that or how you can build an application around that, where, for example, let's say that you work in the oil industry, and you want to make sure that your pipes are not damaged, right? So you can fly a drone that's got this machine learning model on top of it, it's got a camera, and then it's just looking, it's looking and it's like, "are the pipes cracked?" You know, "is there damage to the pipes?" Like what's going on? And again, you don't have to send people out to survey those sites. You can just autonomously and intelligently do it with machine learning. And again, ML .NET. And the different technologies sort of enable you to do that. And especially if you're building these applications in dotnet, right, you're able to, again, leverage ML .NET to help you with those tasks.

#### Jamie

That's the difference between your examples and mine, I guess, because I'm very, very naive about the machine learning sphere, the world around it. And obviously, you're deeply ingrained in it. So obviously my examples have been, not silly but definitely trivial. Is this a cat? Is this a dog? Whereas yours are very much a case of here is a real world example, right? Here's a thing that is happening in industry that we can somehow make easier, make simpler, make safer, less error prone that kind of thing. Because with your walnut example, right? If I'm having to go into a drying machine to check on it, then clearly there is a safeguarding aspect of "if I fall into the machine," or "I may hurt myself, somehow," - I have no idea what the machine looks like or how it works. But if I'm having to put something in and it's having to dry something out, maybe that's too hot, maybe that's gonna cause some kind of breathing issues. I don't need to worry about that. Because if there is an IoT device or some kind of device with machine learning on there, that's figuring it out for me, that makes it safer for everyone involved.

#### Luis

Yeah, absolutely.

And you know, in terms of you know, your examples. So what we try to do, at least when we're building content for for docs is we do try to do some more like business type scenarios and things that would be more real world. That being said, though, when you're thinking of machine learning and AI, it often helps to think in terms of games. And because it's people can easily understand those things right? And you don't need to be so sort of like a domain expert to try to understand these these types of scenarios. And I think a perfect example, which it's somewhat related to machine learning as reinforcement learning, I'm sure you saw, you've seen in, you know, [AlphaGo](https://en.wikipedia.org/wiki/AlphaGo). Where this machine was taught how to play go. And it basically beat sort of the grandmasters or, you know, sort of the top players around the world, right? At the end of the day, that was a game, right? So you start off with games, and any sort of branch out. So okay, well, how can we take the learnings from these games where you have some sort of adversarial relationships or whatever it may be or that and take the learnings from there? And then how can we extract them and bring them into some more real world scenario? So yeah, I mean, I would say that it's actually a really great way to think about in terms of games and simpler scenarios. Because it's easier to conceptualise. Right.

And it's a great starting point. You know, there's in terms of games, like there's also I think there's some machine learning model out there or some system that plays Starcraft right, which is very complex. But at the same time, there's a lot to be learned from from those examples. And those games, right? And those scenarios, because, again, you can kind of take and extrapolate a lot of those things, what it's learned into the real world.

#### Jamie

Sure. So with that in mind, then, one of the things that are really interested to find out is, in your opinion, what are some of the most interesting projects that you've heard about that maybe people who are doing ML .NET things are doing right? Because we talked about, you know, my examples are slightly maybe slightly easier to conceptualise, "I'm classifying a cat; I'm classifying some text." Your examples are very, very much industry driven, business driven, save money, or save people time or make things easier, keep people safe, but what are some of the most interesting things projects that you've heard of?

#### Luis

Yeah, so certainly, you know, there's there's that hazelnut example. There's another example where a company, it's a grocery store chain. And what they're using ML .NET for is forecasting, right. You need to manage your inventory levels. It's not easy to manage inventory levels, right? There's certain practices, techniques, whatever. So using machine learning, you're able to essentially forecast what your demand is going to be for each of the items in your store. And you're able to more intelligently sort of stock your shelves, right. So so that's a really cool, interesting, another business example.

There's this other one that there's, I don't know if he she'd demo at the at the virtual ML .NET conference. But essentially one of our community members, he's working with this, he's trying to build this model and do some data analytics around building the system for like a smart alarm, right? So like smoke detector and fire detector and things like that. And he's trying to use them with .NET to sort of enable intelligently sort of making detection. of whether certain elements like you know, smoke and things like that are present in the environment using again, IoT and sensors. And sort of alert and build some alerts around that. And again, it's all built with with dotnet. So there's certainly a lot of scenarios, there's certainly a lot of use cases that that can be sort of implemented with not only with machine learning, but with ML .NET, specifically. So those are some few that I can sort of top of my head think of.

#### Jamie

I do remember when I talked to cliff, it said with his handy project. For the folks who either haven't [heard that episode](https://dotnetcore.show/episode-51-creating-an-iot-hand-with-clifford-aguis/) or don't know much about Cliff's project: there's a young adult that he knows who was born with only one arm, and he's essentially 3d printed and built an IoT arm for him to use. And he had said, I need to check back with him to see whether he's managed to figure it out. But he said, "I need someone to talk ML .NET to me, because I need to do some ML .NET stuff for the hand." So just like Okay, so first of all, you've got a 3d printed hand which is a sentence I couldn't have said before this year. You've got its IoT 3d printed hand, which that connects to the young gentleman's phone. And you want to do machine learning;  machine learning on a hand. That is 3d printed. This is just, I love the future.

#### Luis

Oh, absolutely. And I actually, I, it wasn't until recently, I know he did it a while ago, but I just recently watched the presentation he did at NDC and, you know, it's a it's a really great project. And yeah, so it's, it's really awesome that the best thing about all that, right, is that it's it's all dotnet. So again, it sort of reinforces that scenario, where whatever it is that you're trying to do, you know, obviously, some capabilities are still in the early stages, right, like IoT, I think I still think of it as it's still in its very early stages of in terms of the in the .NET ecosystem, right. But still, it's pretty capable. Right. And machine learning and AI it's it's sort of a in a similar place, right, where I think developers in .NET have been traditionally building on the desktop, web, and different types of applications. And AI is just sort of a new type of application that you can now build. And it's going to take some time to sort of ramp up and get started in building these types of applications. You know, one of the parallels that I'd like to draw is when Xamarin came around, right. Like when Xamarin came out, and now you can do mobile with with dotnet. There was certainly a learning curve there and sort of a shift in how you think about building your applications. But there's no denying now, right, like that Xamarin is probably one of the if you're building native apps for mobile, it's, it's definitely something that you should be considering as using, especially if you're if you're using dotnet.

#### Jamie

Definitely. And it all comes back to that "dotnet anywhere" like you said. Because yeah, if I can run the same code on my phone, and my computer, and a smartwatch, and whatever device, Raspberry Pi and Metro board or whatever, and I am a .NET developer, I'm more likely to choose that because just the ease of use that convenience right. Because certainly in the industries that I've worked in, it's more about "solve this problem," rather than the constraints of "this technology, this hardware, this thing, this thing, this thing." It's, "I have a problem, and you need to solve it." And making that easier, regardless of which technology to use, and being able to stay - not within a walled garden, because that's the wrong metaphor, but to be able to take this technology and migrate it anywhere. Just it makes perfect sense to me.

#### Luis

Yeah, absolutely. And, you know, it's interesting that you kind of brought that up. And that's one of the feedback that we've heard from some customers, right, in terms of ML .NET. It's the fact that it allows them to go from zero to production in a very short amount of time. And there's a few reasons for that.

Number one is because, you know, it's .NET if they are .NET developers, and you know, chances are that they're familiar with, you know, at the very least able to read the code, right, you know, maybe they might not be too familiar with the IDataView and the different concepts that are associated with ML .NET. But at the very least they can read the code, right? They can read and understand what's what's happening. That's to a certain extent, but also the tooling, right? From its only standpoint, it allows you to prototype rapidly, without investing too much time upfront. And you can sort of make a call from there. It's like, "Okay, well, this is something that will be beneficial to include into my application?" You know, and if it's all great, I'll go ahead and include it and put try to put it into production. And if not, that's okay. I didn't invest too much time in in sort of going down this rabbit hole. So yeah, that's definitely encouraging. And we, you know, we'd like to continue doing that, in terms of making it easier for users to get started making it easy for users to build applications, right. And again, at the same time staying within this ecosystem that they're so productive in.

#### Jamie

So what's next for ML .NET, right? We've talked about there's all of these tools you can use and Azure, or on prem, or in your buzzword bingo powered device. What's next, right, you've already have essentially, everything covered, right?

#### Luis

So with that one, I think I probably and then we kind of did a cover, we could probably do like a A Dan Carlin style talk or podcast is five hours long. But uh, given the time, you know, I'll sort of touch upon a few things both on the ML .NET standpoint, and overall from a .NET perspective.

So, if we talk about .NET there's a lot of really cool and really exciting projects that are that are taking place and a lot of the pieces to foundations are sort of there from a platform perspective. So one of the things that you have is the work that's been done on [System.Numerics](https://docs.microsoft.com/en-us/dotnet/api/system.numerics) right. And specifically, what is of interest there at the very low levels is the [SIMD](https://en.wikipedia.org/wiki/SIMD) enable types, right? And some of the things that you get with this SIMD enable types are like vectors and matrices, which are data structures that are very commonly used within machine learning applications. How does that relate to ML .NET, is ML .NET is using a lot of those types to speed up computations and and sort of more efficiently compute data, right?

Sort of at the language level, right? You're Seeing C# if folks caught the the talk with Mads on on C# 9 and what's coming for C# 9, there's scripting capabilities, right? So it's going to be easier to script with C# 9, right? So we're used to building you know, `public static, void main`. And we have an entry point. And that's kind of how you build C# applications. But now with C# 9, you're going to get great scripting capabilities. On the F# side, you already had really great scripting capabilities to begin with. So it's nice now they're going to be able to get those with with C#.

The other thing is sort of along the lines of tooling, right? So kind of to the original question that you asked me like, "do you need to know Python?" So a very popular library for representing and manipulating data is [Pandas](https://pandas.pydata.org/) right, on the Python side and working with [Data Frames](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html) if you're working with R or Python pandas, you're familiar with the data frame. There's a data frame API that is still in its early stages, but it's supposed to if you're coming from, say a Python pandas type of environment, you can leverage some of the similar functionality from within .NET with this data frame API.

In terms of tooling, you have [Jupyter Notebooks](https://jupyter.org/), right? So Jupyter Notebooks is a very popular interactive computing environment that data scientists use for exploring their data and things like that. With [.NET Interactive](https://github.com/dotnet/interactive), which is this, this sort of this way of it that interactive is among many things is it provides a kernel for running C# code as well .NET - so C#, F# code, and PowerShell - inside of Jupyter Notebooks. So now you're able to sort of use the same tooling that, you know, data scientists typically use for their data exploration, workflows. And there's a lot of really neat work being done there. I don't know if you caught the Scott Hanselman his keynote, but there was a part of the keynote where he was executing code inside of Microsoft Teams, and that code is being interpreted for him behind the scenes that was done at interactive working interpreting code. So it's a way for against interactively run C# and F# code inside of this, again, interactive environments. So there's a lot of really neat work being done there. There's also some integrations happening with VS code.

In terms of building and processing data at scale, you have [.NET for Apache Spark](https://docs.microsoft.com/en-us/dotnet/spark/what-is-apache-spark-dotnet), right? So NET for Apache Spark, what it is, is it's .NET bindings for [Apache Spark](https://spark.apache.org/), which is a very popular sort of platform for doing analytics, right and running ETL jobs and data processing at scale, right. So you have that.

And the really nice thing is that so talking about data frames, .NET interactive and .NET for Apache Spark is you can use data frames in certain scenarios. It's interoperable with ML .NET. So you can go from exploring your data, and then into building your model sort of in one shot. And you can do that inside of this sort of scripting, iterative computing environment, which is Jupyter Notebooks, right, because it can run .NET it can also run ML .NET. So you can do the scripting inside of Jupyter Notebooks. You can use .NET for Apache Spark to pre process your data that's going to go into building your model. At the same time, you can use that for Apache Spark to make predictions using ML .NET, right, because again, they're both dotnet. They're built on .NET standard, you get sort of, there's certain scenarios where they sort of interact quite nicely.

And then what's next for ML .NET. So in terms of all dotnet, it's, it's all about first and foremost, it's about stability, making sure that the platform is stable, that is trustworthy. And then you can sort of trust the models and the results that you're getting from ML .NET. The other thing comes from basically improving AutoML support. So AutoML right now has some scenarios that are supported, like classification, regression, and different other scenarios. So it's improving and adding more scenarios to the AutoML or automated machine learning. There's training for object detection models. So currently, you're able to consume object detection models, using ONNX format. But there's some work being done to eventually train object detection models with ML .NET. And then finally, around the tooling, right, just making sure that the tooling, just like .NET developers are used to with Visual Studio and all the tooling involved with .NET making sure that it's top notch, that it's easy to use, that you can leverage different scenarios like GPU training, and things like that all these, you know, they're they're at different stages of development, and their team is looking at them, sort of, you know, some will make them out later than than others. But those are sort of the things that are happening both across the .NET ecosystem to support these machine learning and AI scenarios, as well as from an ML .NET. standpoint, right.

So and with that said, though, if you there's something that you really, really want to see in ML .NET. And you know, the team either, you know, doesn't have the bandwidth or it's not planning to later it's open source. So you can totally contribute and build your own right, if it's not there, you can sort of go build it and everybody from the community and ecosystem benefits from that, right. And that's the same for .NET for Apache Spark, .NET Interactive, all these things are being developed in the open so if there's something you really want to see, and you don't see it there, you're more than welcome to contribute.

#### Jamie

Awesome. I really like that. One of the things I really like about modern software development is just how open the majority of the tools are. If you get the tool, you install it, and it doesn't really do what you want, and you want to spend a little time figuring out how to make it, do what you want us to do. Do it, submit a pull request, and boom, everyone has that ability now. And I really, really like that, not just that, right. If I wanted to get into machine learning, and I wanted to learn the deep, dark secrets of it, I could pull down all of these libraries and dig through the code because they're in dotnet, right? Like you said earlier, you know, and I may not be able to understand the concepts, but I can understand the language. And then I go buy a book that teaches me machine learning. And it teaches me the concepts. I have the concepts in the book over here. I have the code over here in a language that I can understand. There we go, I can learn, not the same as taking a degree course in machine learning or something. But I can learn enough to be just a little bit better than the people that were just going, "poke that API or send that over here." And that's nothing to say that the people who are poking the API and sending the data around, don't know machine learning, because they're leveraging it. So they know enough to, I use the phrase "enough to be dangerous," right? So I know enough to be able to use it just by flinging this data over here or calling this method or polling this library. And then if I want to go dig deeper, because it's open source, let's do this. I'll go dig deeper and learn how machine learning works.

#### Luis

Absolutely. Yeah. And that's, that's the goal, right? Like you want to know enough that you can be dangerous, and you can actually do something productive. But again, you don't need to know the math behind why it works. You just need to know what problem you're trying to solve. And then use the tools appropriately to solve your problem, which is really what ML .NET tries to do.

#### Jamie

Excellent. You've given a number of resources earlier on, so I'll make sure they're in the show notes. But you talked about there's a [slack community](https://join.slack.com/t/virtual-mlnet/shared_invite/zt-galp4khg-gUJiri5yvEfTD2vkLa9v0w) that grew up around the virtual ML .NET group. I wrote the link for the [ML .NET repo](https://github.com/dotnet/machinelearning), which is samples and documentation and stuff, and more importantly, the link to all of the recordings from the virtual conference as well. So we'll put those in the show notes. If you're interested in those. In your podcatcher, you have to click the link to go through to the full show notes. Because otherwise, it's gonna take forever, and a day just to download all of these wonderful resources to your phone. So good luck with that.

But with that being said, What about catching up with yourself and Luis? What's the best way for people to find out more about what you're doing, where you're talking about the work that you're working on? All of the different things that you're saying, "hey, you should check this out. Check that out." What's the best way to do that?

#### Luis

Yeah, absolutely. So Twitter is probably one of the better waste. So [@ljquintanilla](https://twitter.com/ljquintanilla). So my last name, you can also catch me Mondays and Wednesdays on [Twitch](https://www.twitch.tv/lqdev1). So I'll stream on machine learning and I have a little bit more focused on F#, right. I personally think that F# is really great language for building workflows. So if you want to catch me on Twitch, just join the fun so we're learning together. That's a that's also a place where you can find me.

#### Jamie

Excellent. Okay, I'll get some new from those of you off air, and I'll put those in the show notes as well. Really all that remains to say is thank you ever so much for spending part of your morning with me, Luis, I find it incredibly fascinating because now I know that machine learning is more than just "is this Scott Guthrie or is this a cat?" Or indeed, as what happened in the talk that Scott gave when he showed it off, it is both because there was a picture of a Scott with a cat on his head. So that broke the system.

#### Luis

Yeah, absolutely. No, it's it's been incredibly fun. I you know, I appreciate you having me. And yeah, it's just exciting to be able to share these these technologies. And you know, these scenarios with folks.

#### Jamie

But let's hope that lots of people go out and figure out how to do machine learning things with their apps and then get permission from their bosses to add the machine learning to it. And then just go, I'll just pull ML .NET and just do it that way.

#### Luis

Looking forward to it.

#### Jamie

Thank you ever so much.

#### Luis

Thanks.

{{< paracentre "The above is a machine transcription, as such there may be subtle errors. If you would like to help to fix this transcription, please see this [GitHub repository](https://github.com/GaProgMan/NET-Core-Podast-Transcriptions)" >}}

### Wrapping Up

That was my interview with Luis Quintanilla about ML .NET. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/), and there will be a link directly to them in your podcatcher.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice - head over to [dotnetcore.show/subscribe](https://dotnetcore.show/subscribe) for ways to do that - and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Luis on Twitter](https://twitter.com/ljquintanilla)
- [Luis on Twitch](https://www.twitch.tv/lqdev1)
- [Luis' blog](https://www.luisquintanilla.me/)
- [ML .NET Docs](https://docs.microsoft.com/dotnet/machine-learning/)
- [ML. NET Repo](https://github.com/dotnet/machinelearning)
- [scikit](https://scikit-learn.org/stable/)
- [AutoML API](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/how-to-use-the-automl-api)
- [MLOps](https://en.wikipedia.org/wiki/MLOps)
- [A* Search](https://en.wikipedia.org/wiki/A*_search_algorithm)
- [Transfer learning](https://en.wikipedia.org/wiki/Transfer_learning)
- [general artificial intelligence](https://en.wikipedia.org/wiki/Artificial_general_intelligence)
- [responsible machine learning](https://azure.microsoft.com/en-us/services/machine-learning/responsibleml/)
- [Tensor Flow](https://www.tensorflow.org/)
- [ONNX](https://onnx.ai/)
- [PyTorch](https://pytorch.org/)
- [Pete Gallagher](https://www.petecodes.co.uk/)
- [AlphaGo](https://en.wikipedia.org/wiki/AlphaGo)
- [Creating an IoT Hand with Clifford Aguis](https://dotnetcore.show/episode-51-creating-an-iot-hand-with-clifford-aguis/)
- [System.Numerics](https://docs.microsoft.com/en-us/dotnet/api/system.numerics)
- [SIMD](https://en.wikipedia.org/wiki/SIMD)
- [Pandas](https://pandas.pydata.org/)
- [Data Frames](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html)
- [Jupyter Notebooks](https://jupyter.org/)
- [.NET Interactive](https://github.com/dotnet/interactive)
- [.NET for Apache Spark](https://docs.microsoft.com/en-us/dotnet/spark/what-is-apache-spark-dotnet)
- [Apache Spark](https://spark.apache.org/)
- [Virtual ML.NET recordings](https://www.youtube.com/channel/UClv1sloNF4mzWQiQbemHXRw/videos)
- [ML .NET Slack Community](https://join.slack.com/t/virtual-mlnet/shared_invite/zt-galp4khg-gUJiri5yvEfTD2vkLa9v0w)
- [ML .NET Workshop](http://mlnet-workshop.azurewebsites.net/)
