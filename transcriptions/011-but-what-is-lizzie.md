# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is episode 11: Using Lizze to Secure Your Apps with Thoman Hansen. In this episode I interviewed Thoman Hansen about his programming language Lizzie, what it is, and how you can use it to secure your applications.

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Thomas' Introduction

I'm a software developer, obviously.

I work in both ends: back end and front end. I work a lot with .NET. And I've actually been coding since I was eight years old, believe it or not; and I'm 44 today, so that makes it a couple of generations almost.

So I work currently in the finance industry, creating CRM systems, Exchange systems, stuff to do trading, etc. 

I guess that's the spiel.

### What Is Lizzie?

So Lizzie is my latest open source project; it's MIT licensed; and it's a dynamic scripting language for .NET.

You see, as I'm studying languages I - I mean, having done software development for 36 years, obviously I know dozens of programming languages. I've always envied PHP, although I've never been a PHP developer.

I mean, for instance on my WordPress blog, I can log in to the dashboard, I can open a PHP file, and I can edit it and change my blog. I can change the code that's running on the server, from my browser. And this is such an amazingly cool feature, for anybody who has never been able to do this, because they are using statically compiled programming languages. I figured:

> You know what, that static developers deserve this too.

So I figured

> How can I make C#, .NET, and the Common Language Runtime more dynamic?

And obviously the answer to that is Lizzie.

### What's In a Name?

**Jamie**
I'm always interested to find out where the names for projects come from. So one of my open source projects is called [dwcheckapi](https://dwcheckapi.azurewebsites.net/swagger/), and it's a WebApi for looking into the Discworld books - so all of the books that are written by Terry Pratchett that revolve around the Discworld series. Because I'm a huge fan of Terry Pratchett, and I'm forever going into books stores and thinking

> Do I have this physical copy of this book?

So I have a little API that helps me to figure out whether I've checked them off or not.

What I'd like to know, is does the name Lizzie have a special meaning to you?

**Thomas**
It's actually my girlfriend's nickname. So I've literally created a programming language named after my girlfriend's nickname.

### But What Does Lizzie Do?

You basically turn the server into a dumb box, that really arguably does nothing besides exposing some Lizzie methods or functions which you can invoke, passing in your own Lizzie code. At which point stuff like authentication and authorisation are arguably the only thing you actually have to worry about.

When you've done this you can create generic, for instance

{{< highlight javascript >}}
mySql.customers.get
{{< /highlight >}}

taking an argument telling which field you would like to sort on, how many records you'd like, the offset, etc. And then when you extract that code from you MySql database on the server, the client decided which records it wanted to extract. You can further massage these records and add on, for instance, "OK, I want every single contact for every single customer, when sorted alphabetically, ascendingly, by their name.

So you can imagine this if you were to create it using just HTTP REST endpoints. You'd ave to do multiple HTTP REST requests, right? Because first you'd have to get every customer, then interate over every customer to get every contact. This would create, if you were to display 10 customers, at the very least, 11 HTTP requests.

But with Lizzie, you can reduce it to one. Simply because, first you get all of the customers, then you go to the other tables and get etc. etc.

### A Server Query Language

**Jamie**
Does [Lizzie] support both Framework and .NET Core, or is just Framework, or is it .NET Standard?

**Thomas**
Lizzie is implemented in .NET Standard

**Jamie**
Ok. So it's implicitly across all of the formats then?

**Thomas**
Yeah.
...
I actually only have one DLL, there's only one assembly. And, I mean, it links perfectly into everything I've tried it on; which ranges from .NET Core WebApis to console .NET Framework 4.5 assemblies, etc.

Actually, if you build your server accepting Lizzie code, I mean you can have other types of clients. You can create a client in Java, in Objective-C, etc. So if I can solve that server query language "problem", or if the community together with me could solve it, then arguably it's not longer a .NET project.

Because you don't need to develop in .NET any longer.And you can still have a .NET server, but the fact that it's a .NET server is irrelevant because it accepts Lizzie code. So it would be like MySQL in that regard, in that you can use it in every single language on the planet.

### Wrapping Up

That was my interview with Thomas Hansen. I'd love to hear what you think about Lizzie and how you might use it i your applications.

As always, be sure to check out the show notes for a selection of links, and a collection of text snippets from the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/).

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Thomas on twitter](https://twitter.com/@MisterGaiasoul)
- [Thomas'Website](https://gaiasoul.com/vision/)
- [Full Stack Development From Client-Side JavaScript (No Node.js)](https://dzone.com/articles/full-stack-development-from-client-side-javascript/)
- [.NET - Create Your Own Script Language with Symbolic Delegates](https://msdn.microsoft.com/en-us/magazine/mt830373/)
- [Lizzie on GitHub](https://github.com/polterguy/lizzie/)
