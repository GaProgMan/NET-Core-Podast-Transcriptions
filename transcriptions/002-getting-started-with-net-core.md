# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR
- and not forgetting The .NET Core community, itself

I am your host, Jamie "GaProgMan" Taylor, and this is episode 2: Getting Started with .NET Core. In this episode, I'll take you through how to get started with .NET Core, the software you'll need to install in order to build things with .NET Core, and a little on the different types of applications you can build with it.

So lets site back, open up a terminal, type `dotnet new podcast` and let the show begin

##### Introduction

Returning listeners will know that I've been writing about .NET Core for almost two years (as I record this). And I'm quite an evangelist - although, on a small scale at the moment.

I'm _not_ a Microsoft employee, I just want to say that before we begin. So everything that I say during the course of this podcast episode is my own opinion or interpretation of the subject.

In this episode, I'm going to take you through the essentials for getting started with .NET Core:

- What tools you'll need
- What operating system you'll need
- The benefits and pitfalls of using specific things

All that kind of stuff.

As a reminder, I do write about .NET Core over at [dotnetcore.gaprogman.com](https://dotnetcore.gaprogman.com), and if you take a look at the very first few posts that I wrote there - I'll link them in the show notes, so check your podcatcher for a link - you'll see the basics of getting set up. However, I'll point out that these posts were written back in the early days of .NET Core 1.0, so some of the points will be a little out of date.

Also, as time goes on, the stuff I talk about in this episode will become out of date. I'll try to keep any links in the show notes up to date - did I mention that you should check those? - for a short while after this episode goes live, and I'll make a point of creating an up-to-date episode as time goes on, as this might be something that we revisit from time to time.

Anyway, let's get started with .NET Core - right after this.

##### What Do I Need To Get Started?

Where this an episode about .NET Framework, I'd be advising you to fire up your Windows PC; but gone are those days because by it's very nature, the .NET Core runtime is completely cross platform. As is the SDK, the compiler, tool chains, and IDEs (that's "Integrated Development Environments").

I'll take a moment here and explain something about me:

Back in 2004, when I was a freshman at uni, my programing 101 class was taught entirely in C# using version 2 of the .NET Framework. Our lecturer, Rob Miles (yes, _that_ Rob Miles; the Big Yellow/Pink C# book guy - check the show notes for a link, if you don't know who I'm referring to) taught the course using his laptop, a VGA to overhead projector, notepad and the .NET Framework CLI (that's "Command Line Interface"). He'd open notepad, type some code live, then drop out to the command prompt to compile and run his application.

Combine that with my background (I'll add a link in the show notes to a blog post I once wrote on the first computer that my brother and I ever had), and you'll understand why I've always been a fan of the CLI. Where possible, I've used the CLI on my machines. The invention of Docker (which we'll cover in a later episode), Node, and the work of folks like Jess Fazelle have brought about a renaissance (of sorts) for the CLI. But I digress.

As a further side note: if you're into Docker, I would heartily recommend checking out [Jess Frazelle's dockerfile GitHub repo](https://github.com/jessfraz/dockerfiles). She has dockerised, pretty much, every application you'll ever need to use.

Because of my background, I took to .NET Core via the CLI which is something that I'd recommend every developer tries out. The developer experience with the .NET Core CLI tooling is fantastic. In fact, it's a first class citizen and Visual Studio has been (until _very_ recently) a second class citizen to it. There are reasons for this, which we'll come on to soon enough.

Anyway, back to the plot. What do you need to get started? Well, first you need a computer. It has to be running either:

- Windows 10
- MacOS High Sierra
- One of the supported "Linuxes"

I don't know whether you could tell, but I did bunny quotes when I said "Linuxes" there.

The supported list of Linuxes are:

- Ubuntu and Debian
- Arch (and all of it's derivatives)
- OpenSuse
- Fedora

And that list is obviously subject to change at any point.

For the most basic of .NET Core code, that's all you need.

Seriously.

Well you need a web browser, too.

Microsoft have built a wonderful page which allows you to try [.NET Core in the browser](https://microsoft.com/net/learn/in-browser-tutorial/1) - I'll add a link in the show notes.

No, it's not running Blazor (which we'll talk about in a later episode). The way it works, is you type your code into the browser, it gets packages up and sent to a compiler in the cloud, and the output is sent back to you. It's a little bit like .NET Fiddle, if you've ever used that service.

##### .NET Core on my Desktop

But let's say that you want to get started with .NET Core on your desktop or laptop computer, without having to rely on the cloud.

Well, the first thing you need to do is head over to [dot.net/core](https://dot.net.core) (check the show notes).

Once you get there, you'll see links to the SDK and instructions for setting it up on your computer. It's not fool proof, but there is some JavaScript embedded in the page which tries to identify what your computer it running and will try to present the most relevant instructions to you.

Once you've downloaded and installed the SDK, you can check whether it's running by opening a terminal (or a command prompt if you're in Windows) and typing in `dotnet --version`.

The first time you run it, the .NET Core runtime and SDK will do some extra setup stuff (and it might take a few seconds to complete) then it'll tell you which version you have installed.

I ran that command on my Macbook Air shortly before recording this episode and it cheerily reported that I was running version 2.1.302 (which is also known by the more common name of 2.1.2),

Once that's done, you'll need a way to write .NET Core code. I mainly write C# these days, and I can write that using anything that I want - as long as it saves your code as plain text, then you're good to choose whatever you want.

I really like Visual Studio Code, which is a free editor from Microsoft and is based on Electron. There are plugins for it which will add support for just about anything you could think of.

But you're tooling isn't limited to Visual Studio Code, obviously, there's also:

- Visual Studio for Windows (which I sometime called this VS)
- Visual Studio for Mac (which is a rebranded version of Xamarin Studio)
- Atom
- Sublime Text
- Vi/Vim
- Emacs
- Jet Brains' Rider
- Notepad
- Notepad++
- TextEdit
- Partridge in a pair tree

Ok, that last one was a little silly. But, like I say, as long as it can output to plain text files, you can write your code in it.

Anyway, let's say that you want to install Visual Studio Code like I have. Well, you can get an installer by heading over to [code.visualstudio.com](https://code.visualstudio.com/)

Once you've install that, we're ready to take a look at making our first app.

##### Hello, .NET Core

You might be worrying about how I'm going to describe a code listing using just audio.

Although it's not unheard of (I have an audiobook version of Dreaming in Code, and that has sections where the narrator is literally just reading out code listing ), I'm going to avoid that as much as possible. Mainly because it's boring.

Also, because I'm from the UK and I'll probably use slightly different words for different characters (most of us over here call parenthesis "brackets" and some of us call braces "curly brackets", and obviously there the "dash" and "hyphen" issue, for instance).

Anyway, you've nothing to worry about in that respect.

Now that you have the .NET Core SDK and a text editor installed, we're going to create an application together. Are you ready?

Ok, open a terminal (or command prompt if you're in Windows) and type in the following command (you're probably best to check the show notes for this bit - remember, they can be found over at [dotnetcore.show](https://dotnetcore.show/)):

{{< highlight bash >}}
dotnet new console --name hello
{{< /highlight >}}

When you hit return, your computer is going to go away and scaffold an entire .NET Core console application. It'll place the resulting files in a directory called `hello`, and the namespace will default to `hello` as well. Go ahead and take a look in that directory.

.NET Core defaults to creating code projects in C#, but that can be overridden by a CLI switch to use F# if you'd like.

You should find a bunch of files in your `hello` directory, one of which will be called `Program.cs`. Go ahead an open `Program.cs` in your text editor.

For the folks who are checking the show notes, I'll include a full listing of the version of the code that was generated for me. Right here:

{{< highlight csharp >}}
using System;

namespace hello
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
{{< /highlight >}}

The code itself is easy to follow, especially if you have a background in C, C++ or Java. Can you guess what the code is going to do? It's one of the most [famous programs in the world](https://en.wikipedia.org/wiki/%22Hello,_World!%22_program), and the first one that almost everyone learns to write.

Lets build and run the code. Go back to your terminal and make sure that it's currently in the same directory as your `Program.cs` file (you can use the `dir` command, or `ls` command f you're on Mac or Linux to check), and run the following command:

{{< highlight bash >}}
dotnet build
{{< /highlight >}}

When you hit return, the .NET Core SDK is going to take over and build our application. It'll download any NuGet packages that we need, put the source code through the C# compiler (that's also know as Roslyn), then it'll take the output and package it up into a `dll` file.

The `dll` will be found buried in a subdirectory within the, newly created, `bin` directory. The file extension (`dll`) means `dymanically linked library`, and is a file type from Windows - but don't worry, as it'll run on non-Windows machines.

When you're ready to see the output of our program in all of it's glory, type the following command (again, assuming that you're in the same directory as your `Program.cs` file):

{{< highlight bash >}}
dotnet run
{{< /highlight >}}

What will happen here, is that the .NET Core runtime will take over. It'll be passed a reference to your `dll` file and it will run the binary code found within it.

That's a bit of a lie, as the `dll` contains what is called `IL` (or `Intermidiary Language`) code. This IL is a little like a half way house between the C# code we saw earlier and the binary code required to run an executable file on your computer.

When your stupendously useful application is run, the IL code is read by the .NET Core runtime and it does some magic to convert that to code which your computer can understand. All of this happens in a fraction of a second and, before you know it, `Hello, World!` is printed to the screen.

##### But What Can I Actually Build With .NET Core?

Building `Hello, World` is all well and good, but what about useful applications?

Well, .NET Core is an implementation of the .NET Standard (we'll find out what that means in a future episode, but I also mentioned in the previous episode. So, you know, go check that one), so it has access to all of the APIs, methods, types, and system calls that the .NET Standard outlines.

Because of that, you can technically write anything using .NET Core.

- You want to write the API for a micro service? You want the `webapi` project type
- You want to write a library of functions? You want the `classlib` project type
- What about Console Applications? Well we've already seen that the `console` project type gives us this
- Websites? We have a bunch of options here
  - `mvc`
  - `razor`
  - `blazor`
  - `spa`
  - these are all part of the same namespace: `ASP.NET Core`

You can build practically anything with these project types. In fact, if you create a class library and target .NET Standard (there it is, again) rather that .NET Core, then your class library becomes entirely cross platform. This is because that same class library can be consumed by a .NET Core code base, a .NET Framework code base, a Mono project, and even Xamarin or Unity.

How cool is that?

Here's a run down of the types of applications I've built so far, with .NET Core (I'm including ASP.NET Core here for simplicity, but remember these are  two separate things):

- [A web api for giving out high fives](https://github.com/GaProgMan/Bro-As-A-Service)
- [A web api (using an Entity Framework Core to drive a Sqlite database) for cataloguing books](http://dwcheckapi.azurewebsites.net/)
- [An Angular powered single page application front end of the book catalogue web api](https://github.com/GaProgMan/dwCheckUI)
- [An entire application stack template](https://github.com/GaProgMan/OnionArch)
- [A Blazor application for searching the Pokemon api](https://pokeblazor.azurewebsites.net/)
- [A Configuration Management Database](https://github.com/GaProgMan/Open.CoreMDB)
- A few globally installed Command Line Tools
  - We'll cover what this means in a later episode
- And some [ASP.NET Core middleware](https://www.nuget.org/packages/ClacksMiddlware/) packages for [making websites more secure](https://www.nuget.org/packages/OwaspHeaders.Core/)
  - Again, we'll cover what this means later

As you can see (or hear, as the case may be) you can definitely create any type of application that you could possibly want. All with our wonderful .NET Core.

##### The Developer Experience

This one is a bit of a controversial topic, but I'm going to cover it anyway. Remember, I'm _not_ a Microsoft employee, so I can't speak for them. I'm just giving my opinion here.

As I said earlier, the .NET Core CLI offers a more fully featured developer experience than by using things like VS for Windows. This is (in my opinion) because Microsoft's .NET Core team wanted to target the Linux and MacOS developer communities with their tooling, so they put a huge amount of effort into designing the best possible tooling for .NET Core, when using the CLI.

In fact, there have been a few episodes of the .NET Core Community Standups (check the show notes for the previous episode for a link to those) where Damien Edwards has said that the VS developer experience for .NET Core  needed to be improved.

My opinion of this is that the .NET developer experience on VS for Windows has always been about the .NET Framework, and shoe horning .NET Core into that was always going to prove problematic.

You can see just how wonderful the CLI tooling for .NET Core is by issuing the following command in a terminal:

{{< highlight bash >}}
dotnet --help
{{< /highlight >}}

This will show you all of the commands that the .NET Core SDK tooling exposes to you. And each of those commands can take a `--help` argument and give you instant documentation. This is pretty similar to almost any CLI application on Linux or MacOS. If you've ever used the Node or Angular CLIs, you'll be familiar with what I'm talking about.

It's a lot easier to scaffold new applications using the .NET Core CLI than it is with VS for Windows (for example), because the `dotnet new` command (the command which does the heavy lifting involved with scaffolding a new application) exposes a number of templates which aren't available for VS for Windows.

For those reading the show notes, I'll leave the default list of templates that `dotnet new` has access to, right here:

{{< highlight bash >}}
Templates                                         Short Name         Language          Tags
----------------------------------------------------------------------------------------------------------------------------
Console Application                               console            [C#], F#, VB      Common/Console
Class library                                     classlib           [C#], F#, VB      Common/Library
Unit Test Project                                 mstest             [C#], F#, VB      Test/MSTest
xUnit Test Project                                xunit              [C#], F#, VB      Test/xUnit
Razor Page                                        page               [C#]              Web/ASP.NET
MVC ViewImports                                   viewimports        [C#]              Web/ASP.NET
MVC ViewStart                                     viewstart          [C#]              Web/ASP.NET
ASP.NET Core Empty                                web                [C#], F#          Web/Empty
ASP.NET Core Web App (Model-View-Controller)      mvc                [C#], F#          Web/MVC
ASP.NET Core Web App                              razor              [C#]              Web/MVC/Razor Pages
ASP.NET Core with Angular                         angular            [C#]              Web/MVC/SPA
ASP.NET Core with React.js                        react              [C#]              Web/MVC/SPA
ASP.NET Core with React.js and Redux              reactredux         [C#]              Web/MVC/SPA
Razor Class Library                               razorclasslib      [C#]              Web/Razor/Library/Razor Class Library
ASP.NET Core Web API                              webapi             [C#], F#          Web/WebAPI
global.json file                                  globaljson                           Config
NuGet Config                                      nugetconfig                          Config
Web Config                                        webconfig                            Config
Solution File                                     sln                                  Solution
{{< /highlight >}}

And, as we'll cover in a later episode, adding to that list is really quite easy, and requires the use of a single command. But then again, you need to remember that these new templates wont be expose to VS for Windows.

##### Wrapping up

Anyway, that's going to do it for this episode. Hopefully you've found this interesting, if you did then let me know by sending me a tweet [@dotnetcoreblog](https://twitter.com/dotnetcoreblog/), or head over to the website [dotnetcore.show](https://dotnetcore.show/) and let me know what you think.

Remember to check the show notes for a link to the full transcription of this episode and links to a bunch of related websites and resources. These is available at [dotnetcore.show](https://dotnetcore.show/).

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [YouTube version of this episode](https://youtu.be/Ep-SjSDDTZc)
  - The YouTube version of this episode, in case you would like to listen to it there
- [My First Computer – The I Ever Used or Programmed](https://blog.gaprogman.com/2014/02/my-first-computer-the-i-ever-used-or-programmed/)
- [Rob Miles](http://www.robmiles.com/)
- [The Big C# Book](http://www.csharpcourse.com/)
- [https://github.com/jessfraz/dockerfiles/](https://github.com/jessfraz/dockerfiles/)
  - Jess Frazelle's dockerfiles repo
- [https://microsoft.com/net/learn/in-browser-tutorial/1](https://microsoft.com/net/learn/in-browser-tutorial/1)
  - .NET Core in the browser
- [dot.net/core](https://dot.net.core)
  - Installers for the .NET Core SDK and runtime 
- [code.visualstudio.com](https://code.visualstudio.com/)
  - Installers for Visual Studio Code
- [Common Intermidate Language](https://en.wikipedia.org/wiki/Common_Intermediate_Language)
- [K. Jay Miller's blog](https://kjaymiller.github.io/)
- [.NET to the Core!](https://cynicaldeveloper.com/podcast/8/)
  - My first interview on the Cynical Developer
