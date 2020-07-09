# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is Episode 49: Configuration in NET Core With Steve Collins. In this episode I interviewed Steve about the way that .NET Core handles configuration files, the many different built-in providers, how to build your own, how the hierarchy works, and how you no longer have to deal with the dreaded web.config and it's related transforms. Some of you may know Steve from his blog posts - over at [stevetalkscode.co.uk](https://stevetalkscode.co.uk), or his talks on .NET Configuration best practises.

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Steve's Introduction

#### Jamie

So thank you very much, Steve, for taking the time out to come and speak with me about, about, well .NET configuration.

#### Steve

Yeah. Thank you for having me.

#### Jamie

Thank you very much. I really appreciate anyone who takes the time to come and talk about anything .NET Core with me. Because there's a whole world of .NET core stuff and. There's a lot to learn.

#### Steve

Oh, yeah.

#### Jamie

Speaking to people like yourself, who are experts in all the different parts of it about maybe one moving part is just it makes it easier to sort of take it. I think in there. So, yeah, I greatly appreciate your spending part of your Wednesday evening with me talking about this.

#### Steve

No problem.

#### Jamie

So I was wondering for some of the folks who may not know much about who you are on the work you do. Could you give us a brief introduction?

#### Steve

Okay. I'm Steve Collins. I'm a contract developer architect. I've been building stuff with Microsoft Technologies for, oh gosh, the last 25 years or so - starting with VB three, and Access 2, and a bit of SQL Server 4. I've been contracting for the last 12 years, and recently I've been giving talks at [DDD events](https://www.developerdeveloperdeveloper.com/) around the country about configuration.

#### Jamie

Awesome. Okay, so you're gonna teach us everything there is to know about configuration in .NET today.

#### Steve

I'll try. I can't promise, but I'll try.

#### Jamie

Excellent. Excellent. Okay. That's good. That's good. You know, I've always thought that the... So I have a bit of a background in teaching and the best way to explain something to someone at the best, rather the best way to learn something and to keep it sort of in your head and put it into long term storage is to sort of explain it to someone else. And so I think obviously you must know your stuff, otherwise. You know, you may be standing up there blagging your way... No way, I don't think you're blagging your way through it.

#### Steve

Feels like it's sometimes.

#### Jamie

Well, I mean, those are your words, not mine.

.NET Core. Let's say I create a new web application. Maybe I'm using the command line. Maybe I'm using Visual Studio maybe I'm using Rider, something else. I'm using something Somewhere. I've gone `file new` or whatever it is. I've created a brand new ASP.NET Core, say Web application. I know that there is an `appsettings.json` and `appsettings.development.json`, and when I go poking around in there, there's some stuff to do with logging and may be a connection string if I'm lucky. Is that what configuration is? Is that where I to store all of my stuff?

#### Steve

That's your starting point. But configuration is way more than that.

So yeah, When you create a new project by default, you get the `appsettings.json` and `appsettings.development.json`. So the way appsettings works in .NET Core, is it takes a layered approach. So what it will do is if you're in .NET 2.1-2.2, you'll get a default Web host builder and what it will do for for you is, it automatically knows the orders of configuration files to look at.

So what it will do is it will start with your `appsettings.json` and pick up anything from there. Then it will go to `appsettings.development.json`, if you're in your dev environment. What it will do is he would look at your environment and either pick up `appsettings.development` or `appsettings.staging` or `appsettings.production` if you've got one of those in there as well.

But it goes beyond just the json Files. What you also have is, if you're using the default Web host builder, it will also pick up settings from your environmental variables, and also it will you pass on the command line arguments to it. So that's what you get out the box. We'll talk in a minute about user secrets as well. That's another thing that helps you keep your secret configurations out of source control.

#### Jamie

Okay, excellent. So there was a lot of unpack there, but there's something you said there about your environment. So I know through my own experience of playing around with .NET Core and other .NET tooling is that if I'm inside Visual Studio and I hit `f5` and, if I'm in the cli and I type in `dotnet run`, I get two slightly different environments. I know that the `dotnet run` command will run - because if you if you actually run it, you will see something pop up saying you're running in production whereas if you run inside of Visual Studio that runs in development, right?

#### Steve

Yep, that's right. That's all down to an environmental variable. So if you hit `f5` in Visual Studio, if you look in your project settings, there's an environmental variable set there where you can say whether you're running in `development`, `staging` or `production`.

#### Jamie

Okay, I mean, that makes sense, because if you're running directly from the command line interface, the command line interface  the CLI itself does not know where it is. It doesn't know whether you were on the server with your on your local machine. Whether you're in staging, whether you're on your mate Bob's machine. It doesn't know anything. It's just assumes I must be in production because I'm running the app.

#### Steve

Yup and that is the default for .NET.

#### Jamie

Okay, so if I don't supply the environment variable, it will default to `production`?

#### Steve

That's right. So I think with the .NET command line, you can supply that variable as part the command line.

#### Jamie

Okay, cool. So if you wanted to run it as a developer version on your machine from the command line and you could just pass something in, and it will do it?

#### Steve

Yeah or we could just set the environmental variable in your command prompt.

#### Jamie

I think I've done that before. I think there's something. When I was doing it before, it was something like `ASPNETCORE_ENVIRONMENT=`. Then you pass the string in or something. That might be an old version, though. I remember that being an issue during one about live coding streams because they misspelled "development", and because that didn't match any of the known strings that I'd told the app about it wouldn't work. It just defaulted to production.

#### Steve

Yeah, so, yeah, I'd say it's `ASPNETCORE_ENVIRONMENT`.

#### Jamie

There we go then. So there's a thing called User secrets. Which stops you from adding your secrets. I guess you're API keys and your settings into source control.

#### Steve

It doesn't stop you per-se if you go and drop into your `appsettings.json` or `appsettings.development.json` and type them in there, in they'll go and they'll get committed with your source control. But that's a big no no, you really don't want to be doing that. The way I look at it is, what if your company is like Microsoft, where everything is closed source. But then all of a sudden, someone high up goes, "we're gonna go open source" and if all your connection strings or API keys are in source control. Uh, they're gonna get exposed.

#### Jamie

That's true. Yeah, I wouldn't want to be working on something and then suddenly, "oh, there's my connection string from my production database," or my API keys or something.

#### Steve

Yeah. So to get around that instead of committing to source control when you create an ASP.NET, or any .NET Core, project what you can do is you can right click on the application project in Visual Studio and, say, "manage user secrets." What that does behind the scenes is it adds an entry into your `CS.proj` file, which is a guid.

What you can then do is, once it's done that and you say, "manage users secrets" it opens up a json file on that lives in your user profile. Now the location is slightly different, depending on whether you're on Windows, Linux or Mac, but the core thing is, is that it's part of your profile. So unless your machine is open to everyone, only you should be able to see the values in that `userSecrets.json` file.

#### Jamie

Because it's in your your profile?

#### Steve

It's in your profile. So unless someone's gone in and granted administrative rights to everyone so that everyone could go into each other's user profiles, only you should be able to see it.

#### Jamie

Okay, I did attempt to [write an article back in, I think 2017 or 2018 about uses secrets](https://dotnetcore.gaprogman.com/2017/09/07/user-secrets-what-are-they-and-why-do-i-need-them/), and to sort of drive home the point I put a link to: "If you go to GitHub and you type into the search box, remove API key" you can see - I've just done it now and [I can see 4003 commits across the entirety of GitHub](https://github.com/search?utf8=%E2%9C%93&q=remove+apikey&type=Commits) for people are removing API keys.

Now obviously, that's that's a problem that the user's secrets is attempting to fix?

#### Steve

It is yeah.

Because it's not just about open source projects. Within your closed source what you may have eased. You may have certain keys that are only for production, some keys for staging, some keys for development. If you If you're in a coding shop where certain people are only allowed to see certain keys, if their all in source control in various versions of json files, well, anyone who's got access to your source control will be able to see them, and potentially use them when they shouldn't be able to use them.

#### Jamie

Exactly. Right. So you may have, say, an API for, just gonna pull something out of the air, say you're integrating with mailchimp. You may have a developer API key, which doesn't actually send the messages out. But if you post something with the API key to mailchimp, it may say, "Yes, I have successfully send that because this is a test endpoint." Whereas if you've got a say live endpoint and production API key that will actually send the data right, and you have someone in development or test who sends an email out to that endpoint with the production API key, but it is clearly a test email. Let's say, I'm not going to say that I've done this, but you know someone somewhere will have sent some stupid message as a test say, maybe "This is test email McTest Face" and potentially harm your brand.

#### Steve

It could, yes. And What's interesting is that if you've got GitHub, it will warn you if it thinks you've got some user secrets within your repository.

#### Jamie

Oh, that's really useful. I did not know that. I know there's a lot that GitHub does behind the scenes. I know that there's a few repos that I have that are on .NET Core 2.1, for instance. And every time I go in to have a look, and check on the issues and things, I get a little banner that says, "this is on an old version or supported version of .NET Core," which is incredibly useful, but I just don't have the time to upgrade it.

I like that these sort of open source - well, I guess GitHub isn't open source - but these open-ish tools are doing That's really useful.

### Secrets All The Way Down

#### Jamie

So we talked a little bit about user secrets, and we have said that user secrets are kind of your secrets, like connection strings, API keys, things like that. That are meant to be kept, well secret. I mean, they would be called that, if they weren't secret. So we're saying that if I create a project, and I do whatever it is I need to do to enable user secrets, and I add a use a secret that stored in my profile somewhere out there. Do I have to worry about where it is?

#### Steve

Not really, Because if you're using, say, Visual Studio and you click on manages users secrets, it just opens the json file up within Visual Studio. If I just have a look at mine to see if I can open the containing folder. So on mine is in `/appdata/roaming/Microsoft/user_secrets`... then the GUI from the CS.proj file.

#### Jamie

you can track it down, if you need to find it.

#### Steve

Yeah so if you prefer something like [notepad++](https://notepad-plus-plus.org/) to edit your json, you can open it up in something like that.

What you can also do is at a command line level with the .NET command line. You can use a command to edit your user secrets in there. I think it's something like a `set` command where you can set it just part of sort of the `dotnet` command.

#### Jamie

Okay, that's useful. So then that that exists on my machine for my profile. So someone else, like you say, if someone else accesses my machine and let's say that in the that the system admins whoever set up the machine - I don't want to say "correctly," but with the best security intentions in mind is probably what I'll say. So that we're sitting at the same machine, I log in, I can't find your users secrets. You log in, you can't find my users secrets.

#### Steve

That's right. Yeah.

#### Jamie

So let's say I have everything checked-in to source control. I've got me user secrets separate. What if computer gets destroyed? Does that mean that I need to recreate may user secrets because obviously that they're stored separately from source control?

#### Steve
You would, yeah.

#### Jamie

I mean, that  makes sense because you want them stored separately.

#### Steve

So in an ideal world what you do is, at a company level you'd also have those secrets stored in something like [one pass](https://1password.com/) or something. If you're a corporation, you'd have some digital vault where you got those stored away anyway.

#### Jamie

Sure, so that the point I'm getting at is obviously that user secrets isn't the "be all-end all answer" to keeping everything separate? You still have to sort of manually manage those.

#### Steve

Yep. And also, of course, that's only while you're in development. When you get towards deploying it, you haven't got the concept of the user secrets,

#### Jamie

right, yes. That's a really good point, because the whilst the app will probably be running with a user profile system or something like that. It won't have a user secrets area, and it's his profile area. And it's home directory I guess.

#### Steve

No. So I think I'm right in saying that, within the default Web Host builder, it only checks that whether you're in the development environment as to whether it pulls in user secrets or not.

#### Jamie

Okay, that makes sense because, like I say, even if it wasn't, it would be wasting time trying to look for user secrets.

#### Steve

Yeah

#### Jamie 

When it's not possible to have them.

#### Steve

Yes, so then you have to think about well, where are you going to store your secrets?

#### Jamie

That's true. Let's jump straight past staging, or UAT, or whatever: straight to production. I have my app running on a production server. I have a bunch of configuration in my `appsettings.json` files. I'll come on to that in a moment cause I got a question about those. Let's say I'm running on Azure, can I add those secrets in Azure outside of source control, or do I have to store them in a key vault or something?

#### Steve

So you got two choices in Azure. So Azure has a console where you can store your use secrets. And then what it does is when it's running, it actually puts those in those environmental variables for you. So your application is none the wiser because one of the last entry points is environmental variables and command line, so it'll just pick them up from the environmental variables.

Alternatively, if you if you're running in Azure - well, even if you're not running in Azure - there's also the Azure key vault that you just touched on. So that gives you hardware or software encryption, depending on how many bucks you want to pay for it. And that then gives you a proper encrypted store, and its completely encrypted until you pull it down into application. For that, you actually have to specifically say that you using Azure Key Vault so it becomes one of your application configuration sources. And so you have an extension method. So you have to bring in the [NuGet package](https://www.nuget.org/packages/Microsoft.Azure.KeyVault/) to use that.

Not only Azure, [AWS have a similar offering](https://aws.amazon.com/secrets-manager/), and [HashiKey Corp have KeyVault](https://www.vaultproject.io/api-docs/libraries/#c) as well. But the NuGet package for that isn't an official one. There's just two or three sort of open source ones out there on GitHub.

#### Jamie

That's good to know that I don't have to go with Azure if I want to keep everything secret. That's good to know yet. So what you're saying is, I need to have some configuration for my app to be able to pull the configuration from a key vault. Is that right?

#### Steve

Yeah, that's right. So this is where it gets fun and games, because to access the key vault you need to have a client id and a client secret. So where do you store those? So all you've done is move the problem down the road a little bit. So then what? You need to think about is how you handle that client ID and client secret.

So that could be an environmental variable. So again, you've still kept it out of source control.

You could have an `appsettings.json` that sits outside of source control and gets deployed to a different directory so you can use a different file provider and say, "I'm going to grab the `appsettings.json` file from outside the application directory." The problem with that, of course, is if anyone gets access to your production server's file system, your client ID and Secret is still exposed.

So that's when maybe you need to think about having some sort of encryption going on as well.

#### Jamie

But then I suppose, where do you store the encryption decryption keys?

#### Steve

Exactly. And this is turtles on turtles. At what point do you stop?

#### Jamie

Yeah. I guess, though, that they'll be probably some enterprise-y level thing somewhere that handles all of this. Somebody's probably thought about this, and it has a package or something for enterpriset stuff.

#### Steve

And one other option is if you've got certificates available to you. I think I'm right in saying you can register certificates with the azure key vault, and it'll take that certificate as authentication to go and pull out your values.

#### Jamie

So there's more than two different ways to do it. You're not really stuck with just one.

Well let's say, "I'm a Web developer. I like json, but I don't like it that much." Do I have to use `application.json`?

#### Steve

No. Out the box, there is support for XML files, but they're not the dreaded `web.config` files. These are just XML serialization of your configuration in the same way that the `appsettings.json` is a serialization of some settings. So we're not going back into the dark, murky world of `web.config` ever again.

But even more of a throwback to support for `ini` files.

#### Jamie

Oh wow.

#### Stuart

which took me by surprise back to the days of Windows 3.1

#### Jamie

Wow. I remember opening up `.ini` files for many of the games that I used to play and go, "What happens if I change this value?" And suddenly you have unlimited money or whatever.

#### Steve

Yeah, but what is stranger is that in Windows 10, if you go and hunt in the Windows directory for `*.ini`, you will still find a load of ini files. I don't know whether they're they're actually used or not, But there are so many files still in Windows 10.

#### Jamie

Well, I mean, I suppose you gotta put config somewhere.

#### Steve

But in addition to file based ones, you can write your own.

So everything centers around two interfaces in .NET Core: There's the `IConfigurationSource` and `IConfigurationProvider`. So [IConfigurationSource](https://docs.microsoft.com/en-us/dotnet/api/microsoft.extensions.configuration.iconfigurationsource). You can write your own implementations that go and pull in values from wherever you want. So certainly there's demos out there on the Internet, and I've seen YouTube videos, of people using things like SQL Server so you could put it in from there - I think [Andrew Lock has got one that uses YAML files](https://andrewlock.net/creating-a-custom-iconfigurationprovider-in-asp-net-core-to-parse-yaml/). And I've been to a talk where someone was talking about using [GraphQL](https://graphql.org/) to supply the configuration. So you can use any any data source you want if you're happy to go and write your own `IConfigurationSource` implementation.

The thing to do then is there's a `Build` method on the `IConfigurationSource` that generates an [IConfigurationProvider](https://docs.microsoft.com/en-us/dotnet/api/microsoft.extensions.configuration.iconfigurationprovider). And that's the bit that takes your configuration source and generates key-value pairs. And that's the thing that `IConfiguration` is interested in because everything boils down to that.

They key in that situation is actually, sos ay in your json file that's got top level of `A` then `B`, then `C` then `D` that is represented in the key with `a:b:c:d`, and that's how the hierarchy is represented. With environmental variables you've got a similar thing and you'll see underscores to represent the hierarchy breaks.

#### Jamie

So I can have json files, ini files, YAML files, Dave files, some sort of server of some kind serving it up. I wonder whether - and if you wanted to really do this, I don't think it's worth doing because it's not very secure - configuration over HTTP, or GRPC indeed.

#### Steve

Indeed. And it's something I've, sort of, seen someone talking about was using GRPC to serve it up. Because if you do that over HTTPS, then I don't see a particular problem with that.

But one of the things to think about is: if you go a custom configuration source, how secure is that back-end? So we've talked about json files being innately insecure because they're on the filesystem [and] could get checked in. If you've got SQL Server database, how look down is that SQL Server database? As if anyone in your company can go and see the values in that database, you're back to square one

Now, one of the things I talk about in my talk is actually encrypting values within your configuration. So a double layer of security. So to be able to implement that, you've got two choices you could either write an `IConfigurationSource` that decrypts stuff on its way out. Or, and the method I have advocated in my talks, is to write a [Bridge class](https://en.wikipedia.org/wiki/Bridge_pattern).

So for those not familiar with the term of bridge class: Bridge classes are a way of intercepting data. So say you've got of `Car`, then you might have a bridge class that's called `Supercar`. And what Bridge class can do some enhancements and change values on the way out. Between your caller and the underlying `Car`.

#### Jamie

[If] you had an implementation of your class `Car` and it represented a `Mini`, you could access it via the super class and it some how becomes a `Tesla`?

#### Steve

You could do, yeah.

But the reason I sort of advocate that is that if you bound your configuration to a class using the options, which we can talk about in a minute, then you have the encrypted value in the bound class. And then what you can do is unwrap that class using a bridge class which will do the decryption for you.

#### Jamie

Okay, so you're saying to the bridge class, "go get me the value for my API key for say twitter," and if you access it directly through your options class or whatever that has that raw encrypted version - you just get a get a bunch of [gobbledygook](https://en.wikipedia.org/wiki/Gibberish) that you can't do anything with.

#### Steve

Yeah.

#### Jamie

Whereas when you go through your bridge class you'll say, "go get me the thing," the bridge class talks to your your options class, pulls that value in, decrypt it, and sends you the actual API key back.

#### Steve

Yeah

#### Jamie

Bcause then, yeah, there's only one path to get a valid value for your your settings.

#### Steve

Yes. So then what you can do is in your dependency injection registration, with the container, what you can do is if you implement it as an interface you can use your bridge class to unwrapp the `IOptions` and expose it as `IMySettings`, for example. And that way, when you've got a constructor that requires those settings you don't even need to worry about `IOptions` any more. You just ask for you an implementation of your interface, `IMySuperSettings` or something like that.

So that way, if you've got libraries that rely on your settings, you don't have to drag along the NuGet package for `IOptions` along for the ride.

#### Jamie

That makes a lot of sense, because I've seen that before.

So one of the things I've seen before is the `IOptions` or the `IConfiguration` class dependency injected all the way down. So I have maybe got a controller that takes in `IOptions` or `IConfiguration` because it needs it some value, and then you call an action on that controller, and it reads the value from the configuration. Or maybe it just passes that straight down to - not a great design - but maybe it passes the `IConfiguration` down to the service, which then passes it down to some other method because it needs a connection string somewhere. Which is not good.

#### Steve

No. So one of the other things I advocate is: if you extract interfaces out of your classes that you used in `IOptions`. That way, it gives you two things. It means you're only passing the implementation of the interface down, which may be your bridge class. But also in terms of things like your controllers or libraries, that require that you only have to mock that interface. So you don't have to get involved configuration at all whilst you're doing your unit tests because you could have a controller that says `ISlqConnectionString` with just one property of SQLConnection String, and you just mock that one property on the interface instead of having to mock `IOptions<MySetting>` something like that.

#### Jamie

Sure, that makes sense. Like you say, it makes it easier for mocking, which means unit tests, integration tests, and end-to-end tests become less of a pain because you don't have to supply the actual value. Just supply an interface, which will return any string or return a known string or something.

#### Steve

Yeah

### Strongly Typed Configuration

#### Jamie

So we've talked about it a little bit there anyway. So you can represent some form of objects, I guess, inside of your `appSettings.json` and can you can read that out as strongly typed?

#### Steve

Yep. When you're doing your dependency injection registrations, there's an extension method called `Configure` and that's a generic. So what you can say is you can say `Configure<MySettings>` and then say `GetSection("mySettingsBit")` from within the json. And what it will do is, as long as the `IConfiguration` marries up to the layout of your class, it will go and bind it for you.

The downside to that is it exposes it through the `IOptions` interface and not directly. This is how I came about doing my journey into configuration to start with, because I wanted to do a bound class and I did the configure. And in my controller, I made a request for `MySettings` and I kept getting `null`. And then I had to go back and read the documentation - something developers hate doing - But then the penny drops that why I actually had to do was either consume `IOptions<MySettings>` of my settings or `IOptionSnapshot<MySettings>` or `IOptionsMonitor<MySettings>`.

So those are the three interfaces that get registered when you do a `Configure<T>` in the dependency injection container.

#### Jamie

Let's say that you're not bothered about having to expose it through `IOptions<T>` for instance, you could pull that out actually as a POCO in C# class.

#### Steve

Yes. So what you could do is within your dependency injection after you've registered the configuration - so `Configure<T>`. So there's two ways you can deal with that. You can either use a lambda expression which will go and unwrapp the `IOptions`. So, for example, you've got `Configure<T>`, which will give you `IOptions<MySettings>`. You can then register a transient of `MySettings` and use the lambda that says, `GetRequiredService(IOptions<MySettings>).Value` and that will do the unwrapping of your POCO out of the options and can serve it up just as `MySettings`. So that's one way of giving you your POCO.

The other way, by using the bridge class, is to take the `IOptions<MySettings>` in the constructor of your bridge class, and register your bridge class as transient. So that way, when you make a call for your bridge class `MySettingsBridge`, it will automatically get the `IOptions` injected into it. And in the constructor of your bridge class, you go and unwrapp the value from the options.

So with that, that way you only ever have to take in your POCO into a constructor. I then prefer to then have an extracted interface, which comes back to the whole mocking principle.

#### Jamie

If you can mock what the POCO is gonna look like and you handling all of that dependency injection for your real instance, you can then mock that interface and say, "when I say get me the connection string just return this value or just return a known string or just return any string. It doesn't really matter because it's a mocked version." Um,

#### Steve

Yeah. It's a mock, yeah.

#### Jamie

Okay, so we touched on it really early on when you said that there was a hierarchy. Looking at the code that I've got in front of me. I've got an `appsettings.json` and an `appsetting.development.json`. And you said that you can have a staging and a production. And When I start my app, it figures out, through whatever magic it uses, the environment tag or maybe something like that. It figures out where I am, which environment I'm in. Does it load all of the json files?

#### Steve

No. Behind the scenes, what it does is it uses string interpolation to replace your environment. So it'll look for `appsettings.{ENVIRONMENT}.json` So whatever uses string interpolation behind the scenes to know which json file to load.

So what it will do is, say in appsettings you've got a setting called `message`, and it says "say hello". In `appsettings.development` that will override the basic one, so it might have a value that says `goodbye`. That might get overwritten in user secrets, and it could get overridden by the command line in a variable. So each time it goes up the tree override an underlying value.

#### Jamie

So the development one will override any values in the normal one, I guess.

#### Steve

Yeah. And then user secrets can override that. What it also does as well as overriding, it allows you to upend additional sections into your settings. So you might have a very bare skeleton is your basic app settings. But then you might enhance it more with your development one. So you you might have some extra stuff to do with logging, for example. And then that might get extended again with your user secrets. So you might put a value in your user secrets that allows you to do some debug analysis in there.

#### Jamie

So let's say there's a bunch of common values between all of your environments. You're not having to copy them into your development, your production, your users secrets, your key vault. That kind of thing.

#### Steve

No. So you could think of it very much in the way of class inheritance. in that you might have a abstract base class that's got your your basic settings, and they you might inherit off of that and then go and implement some abstract values so you can keep going. So it keeps going up the tree, either by overriding or by enhancing.

#### Jamie

So then, if you need some extra configuration for development that isn't required in production, as long as your app can deal with that, then you could just not include it in your `production.json`.

#### Steve

Yeah. And, if as part of your Web host builder, you've used extension methods to add in custom ones then those would come in as well.

#### Jamie

Okay, let's say I've got a development environment which is on a server, and that's not very stable at all. I've got a pre-QA environment that is meant to be stable for developers to test in. And then I have a QA environment for the QA to test in. I could create an `appsetting.preqa.json`, tell my web post builder about it, and then it will just know when I start with preQA to load this file rather than the development one?

#### Steve

Yes. So it comes down to the value you put in the `ASPNETCORE_ENVIRONMENT` environmental variable.

So if you go to your project properties in Visual Studio in debug, there's a section there for environmental variables where you can go and set it up. I think you can also set it up within the app `launchsettings.json` file for Visual Studio. And lastly, you could just set it up as an environmental variable if you're using `dotnet run`

#### Jamie

I think we covered earlier on: when you start something by default without going through Visual Studio, it will default of production because, I mean, the tooling doesn't know where it is, So it's best to assume.

#### Steve

Yeah, that's the safe assumption. Yeah.

#### Jamie

So we talked about the user secrets that I can have essentially configuration per user.

#### Steve

Yes.

#### Jamie

So I've seen this in the wild. I don't know whether this is something that was missing from the deployment tools that were being used. So to give the background: we were using Azure DevOps to deploy our application out there onto a server, and we noticed that even though we were telling it, "this is going to be a production," all of the `appsettings.json` files went with it. Is this required?

#### Steve

It's not required. I think what that comes down to is on those files, whether you say `copy always`, or `copy if newer`.

#### Jamie

So that's not necessarily something in DevOps or your build tools or anything. It's just they're packaged by default.

That's just something I think that it's worth knowing about for other developers that when they ship their application, unless they explicitly set it up, all of their configuration is going to go with it. So potentially your development keys are gonna go with it if you store it in your `appsettings.json`. But then, if you're keeping everything in user secrets then maybe that's not too big of an issue.

#### Steve

Yeah. And, if you're using the CI/CD pipeline, you could always do something in your CD pipeline to say, "go look at the environment I'm deploying to and go and exclude the other files."

#### Jamie

Of course. So that was going to be my other question as well: you've hinted earlier on about app settings in .NET Framework. Those long, long may they be forgotten XML files and how, back in the day, if we wanted to change the value in there based on which environment we were deploying to, we had to do it with an `application.config` transform, which was I'll say not very nice to read XML.

#### Steve

No, no.

#### Jamie

Because we're not doing those transforms anymore. We don't have to do that.

#### Steve

No. So, whereas in the web config days it was a transformation. So it was running effectively an XML transformation over your web config or app config as part of the deployment. Now because it's a hierarchical thing, you're not actually changing your files, you're just providing extra files or extra other configuration sources and saying: A overwrites B overrides, C overrides D override, et cetera, et cetera.

#### Jamie

So then, if I was that, I don't want to say masochistic. But if I was that horrible to myself, is it possible to do transformations in your CI/CD. So let's say using Azure DevOps. Is it worth going, £Yes, I want to transform this." Or is it just worth having a separate json file and not having to deal with the horror of having to move things around?

#### Steve

There's two approaches you could do. You could do some sort of transformation, and certainly where I'm working at the moment we use [Octopus Deploy](https://octopus.com/). And what we do is in our appsettings.json's and the various environment ones what we do is we just have a placeholder curly brackets, and the actual secrets and values are in octopus deploy, and Octopus deploy effectively does that transformation for you. And you could do the same thing with Azure Devups. So it just has some substitution for you, but that's not really a transform per se. That's just text substitution.

The other way that you could do it is: if you're deploying to azure then we've talked about having the dashboard because if you're deploying to azure and you're using the dashboard, the `appsettings.json` doesn't get deployed. What happens is you used the dashboard, and that sets everything for environmental variables.

#### Jamie

That completely negates the worry of, "what if my server for is compromised."

#### Steve

Yeah.

#### Jamie

There are no configuration files. And if someone wants to try and get to your secrets, assuming they don't have access to the dashboard, But we've somehow managed break into Azure - which is if someone manages to break into Azure, you have slightly bigger problems. But yeah, let's say they've managed to break into the backend of Azure. They've got onto the server where your application lives. They found the files, There's no `appsettings.json`. They can't get to your database connection strings, and you're API keys and all that kind of stuff, because they literally don't exist.

#### Steve

Well, they do, but they're environmental variables. So if someone knows to go sneaking around the environmental variables. That's why I advocate encrypting stuff and using the bridge class to decrypt stuff as well. So anything that touches the surface, such as environmental variables, command line parameters, json files if you've encrypted as well. But it comes back to, "where do you store your decryption keys?" At some point, you gotta have something that's in clear text to be able to go through the motions of then decrypting. That's where certificates can come in useful. Because if you've got a certificate based encryption decryption, there is no passwords to go look for.

#### Jamie

But then presumably you have a certificate somewhere on file or in storage somewhere.

#### Steve

Yeah, well, certainly on Windows you've got the certificate store, of course. I can't speak for Linux because I'm not so familiar/

#### Jamie

Yeah, of course, that there is something similar and he's got the key store, which is essentially the same thing.

But what I'm seeing in my in my head is that, uh, I'm seeing this wonderful [Rube Goldberg machine](https://en.wikipedia.org/wiki/Rube_Goldberg_machine) of, "we'll load a file from storage, which has a key in. We'll decrypt that, using another key that we pulled from GraphQL. And then then we'll pull under the thing from SQL Server, combine all three to get the URL to poke to get the settings. Go get the settings from there, and then decrypt it with something else."

#### Steve

And, meanwhile, your user has disappeared because of the latency.

#### Jamie

Of course. That's absolutely it.

#### Steve

We've just taken five minutes to decrypt this value and the user has disappeared.

#### Jamie

That's right. Well, yeah, I mean, the system is incredibly secure if no one's using it, right?

#### Steve

The best systems are the systems with no users.

#### Jamie

That's exactly it: seal it and concrete, dump it in the ocean. There we go.

#### Jamie

So 's really useful to know: that there is a hierarchy to hear the appsettings; you don't have to use json; you can use .ini files; you can use XML files. There are people have written API that will that use YAML files and that kind of stuff. So it's kind of the location of the `IConfiguration` is almost agnostic as well as the format?

#### Steve

Yeah. Because ultimately it boils down to these key-value pairs at `IConfigurationProvider` level. And then that goes into `IConfiguration`, and at `IConfiguration` stage that gets broken down, so you can say `IConfiguration.GetSection("blah").GetSection("blah").GetValue()`.

I really wouldn't advocate using the `IConfiguration` interface raw. The only place I would ever advocate using that is if you could just got a single value that you don't want to bind to a class. You could just pull it out in there and just sort of exposed it through some simple interface,

#### Jamie

I say. Okay, so try not to use `IConfiguration`, use `IOptions` instead?

#### Steve

Well, you could use `IOptions`. Or, as we were talking about earlier, unwrapping the `IOptions` and just passing your POCO or interface down the chain. That way, it's taken a lot of the plumbing away from your code. Your code just doesn't care about _how_ it gets some settings. It just says, "I've got an interface or a class that's got some settings in. DI will give it to me." And it really doesn't care about the plumbing.

#### Jamie

Just a sort of simplify everything like you say: when my lamp dies, I don't need to rewire my house to get a new one, I just plug a new one into the wall.

#### Steve

Yeah.

#### Jamie

Because the socket on the wall where I plug it into, or indeed the USB port on my computer, has inverted that that dependency, I no longer have to wire it up and solder it into my machine. They just plug something in.

#### Steve

Yeah. Because if your passing say `IConfiguration` down all the way through your application, your application has to have knowledge off the layouts of your configuration. So you've got something nested three layers deep. You've gotta go `GetSection("A").GetSection("B").GetSection("C").GetValue()`.

Whereas if you could just get that bound to a class, that's `MySettings`. Your application only needs to worry about `MySettings`, and it doesn't care how it got there, whether it was through configuration, whether it was through a mock, whether it's been done through a hardcoded class, for example.

#### Jamie

That makes sense. And then good class design steps in, and you're able to go, "right. This section off the `MySettings` class is only related to database stuff. When I need to pass this to the database, I wont will pass the overall class, I'll just pass the `MyDatabaseSettings` class."

#### Steve

Yeah. So that's where the [Interface Segregation](https://en.wikipedia.org/wiki/Interface_segregation_principle)from the [SOLID principles](https://en.wikipedia.org/wiki/SOLID) comes in useful. Because what you might do is you might have `MySettings` that implements `IMyDatabaseConnection` plus `IMyLoggingSection`. But all you need to do to pass down to your constructor of, say, your controller might be `IMySqlConnectionString`.

And then what you can do to is: in your DI container you just say, "Go and get my settings class, but then also register the various interfaces as well to go and get it out of that settings class." So that way you can get your interface segregation all come back to the settings class. But when it comes to mocking, for example, you've only got to mock that one property on `IDatabaseConnection`, which is `ConnectionString`.

#### Jamie

Yeah. Rather than having to mock the entire class,or the interface which represents the entire classes, just mocking that one.

#### Steve

The infamous one was, I think it was one of the Microsoft original ones for one of the database interfaces that had about 200 properties and methods that you had to implement.

#### Jamie

Wow.

#### Steve

I can't remember whether it was `IDbProvider`, something like that. It had masses and masses they hadn't obviously done interface segregation.

#### Jamie

Well, I guess at that point, you know, if you're having to crawl that far down into the stack, then you're essentially you're mocking Microsoft Code, Framework code rather, than your code, I guess.

#### Steve

Yeah.

#### Jamie

I think that's been incredibly useful. I I now know loads more about configuration, and how I should be doing it and stuff. I'll have to look into bridge classes. I hadn't used bridge classes ever in any of my code, and I think I'm gonna do that now. And I might even write a little terminal app, a console app that I ask for a mini and it gives me a Tesla, just as proof that it works.

#### Steve

You have to pay for the charger.

#### Jamie

Okay, So what about keeping up with yourself then, where can our listeners go to learn a little bit more about you, to read, do you write blog posts? Do you have YouTube stuff? Do you do talks?

#### Steve

Okay, so I haven't written a blog post for a while. But I wrote a [four part series about the using the bridge class on configuration](https://stevetalkscode.co.uk/category/net-core/configuration) that's on [stevetalkscode.co.uk](https://stevetalkscode.co.uk). I tweet quite a bit. So I'm [@stevetalkscode](https://twitter.com/stevetalkscode) on Twitter. And I usually sort of bounce around some user groups and [DDD conferences](https://www.developerdeveloperdeveloper.com/) around the UK. So I think I've got a few user group talks coming up in the new year in Bristol and Nottingham. I believe.

#### Jamie

Oh, fantastic. Okay, So if there's people in the UK in those locations, they can maybe come along and see a much more detailed  and graphically enhanced version of your talk

#### Steve

Yep.

#### Jamie

Okay. So I'll make sure, put links those things in the show notes, and that way people can keep up with you. And are you open for bookings for meeting ups? You said that you travel around a bit for meet ups. so should someone who's running an event want to talk .NET configuration?

#### Steve

Yeah, sure. If they DM me [@stevetalkscode](https://twitter.com/stevetalkscode) code on Twitter. I'm sure we can come to some arrangement.

#### Jamie

Brilliant. Well, I mean, all that really remains to say is thank you agains Steve for taking some time out. Like I said, I really appreciate it. And I know that before we hit record, we had a few technical issues. I know that I've still had some technical issues whilst we've been talking, with some Windows nonsense happening which wiped out my CPU a few times. So yeah. Excellent. Thank you ever so much for spending some time and setting everything up and having a chat with me. It's been really, really interesting.

#### Steve

Thanks, Jamie. I've enjoyed it.

#### Jamie

Thank you very much.

### Wrapping Up

That was my interview with Steve Collins. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/), and there will be a link directly to them in your podcatcher.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice - head over to [dotnetcore.show/subscribe](/subscribe) for ways to do that - and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Steve on Twitter](https://twitter.com/stevetalkscode)
- [Steve's website](https://stevetalkscode.co.uk)
- [DDD events](https://www.developerdeveloperdeveloper.com/)
- [User Secrets - What are they and why do I need them?](https://dotnetcore.gaprogman.com/2017/09/07/user-secrets-what-are-they-and-why-do-i-need-them/)
- ["remove API Key" on GitHub](https://github.com/search?utf8=%E2%9C%93&q=remove+apikey&type=Commits)
- [notepad++](https://notepad-plus-plus.org/)
- [1password](https://1password.com/)
- [Microsoft.Azure.KeyVault NuGet package](https://www.nuget.org/packages/Microsoft.Azure.KeyVault/)
- [AWS Secrets Manager](https://aws.amazon.com/secrets-manager/)
- [HashiKey Corp KeyVault](https://www.vaultproject.io/api-docs/libraries/#c)
- [IConfigurationSource](https://docs.microsoft.com/en-us/dotnet/api/microsoft.extensions.configuration.iconfigurationsource)
- [Creating a custom ConfigurationProvider in ASP.NET Core to parse YAML](https://andrewlock.net/creating-a-custom-iconfigurationprovider-in-asp-net-core-to-parse-yaml/)
- [GraphQL](https://graphql.org/)
- [IConfigurationProvider](https://docs.microsoft.com/en-us/dotnet/api/microsoft.extensions.configuration.iconfigurationprovider)
- [Bridge class](https://en.wikipedia.org/wiki/Bridge_pattern)
- [gobbledygook](https://en.wikipedia.org/wiki/Gibberish) 
- [Octopus Deploy](https://octopus.com/)
- [Rube Goldberg machine](https://en.wikipedia.org/wiki/Rube_Goldberg_machine)
- [Interface Segregation](https://en.wikipedia.org/wiki/Interface_segregation_principle)
- [SOLID principles](https://en.wikipedia.org/wiki/SOLID)
