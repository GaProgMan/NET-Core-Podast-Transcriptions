# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is episode 16: .NET Core FAQs. In this episode we will answer some of the most frequently asked questions about .NET Core.

So lets site back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Introduction

.NET Core is still a relatively new technology - the initial releaseonly having happened in late 2016. However, it's a rapdily evolving technology. As such, those who are new to .NET Core (and those who are new to .NET in general) can quite often find that they don't know where to go to get their questions answered.

So I thought that I'd cover a few of the most frequently asked questions that I have been asked about .NET Core. These questions range from beginners topics all the way up to advanced stuff. So let's just right in.

### Question 1: What Can .NET Core Do?

.NET Core can, pretty much, do anything that .NET Framework can do - with a small number of caveats - with the exception that it's cross platform. Whereas .NET Framework was traditionally only found on the Windows family of Operating Systems, .NET Core can run pretty much anywhere.

### Question 2: Which Operating Systems Are Supported by .NET Core?

Because of it's cross platform nature, .NET Core can run on a number of different platforms. It can run on:

- Windows 10
- Windows IoT
- Various Linux distributions
- MacOS
- Azure
- Tizen powered Samsung hardware
  - Including smart TVs and smart refrigerators
- Raspberry Pi

The above list is not an exhaustive one, but it covers most of the common platforms.

### Question 3: Which IDEs Can I Use With .NET Core?

You can use:

- Visual Studio
- Visual Studio Code
- Visual Studio for Mac
- JetBrains Rider
- Atom
- Sublime Text
- Notepad++

Ok, Notepad++ isn't really an IDE but it's very close to being one - depending on what your definition of an IDE is.

Essentially, as long as it can edit plain text files, you can use it (alongside the CLI tooling) to create a .NET Core application.

You can also get intelli-sense support for .NET Core with the [OmniSharp](https://www.omnisharp.net/) plugin, if your IDE supports it.

### Question 4: Can a .NET Core App reference .NET Framework Code?

Depending on how that .NET Framework code is presented, sure.

.NET Core is what's known as .NET Standard compatible. The .NET Standard is a standards document which says which APIs and types a .NET platform must support in order to be a .NET platform.

Both .NET Core and .NET Framework are .NET Standard compatible. So are Xamarin and Mono. This means that a large number of NuGet packages which were originally built for .NET Framework are already compatible with .NET Core. All thanks to the .NET Standard.

However, if your .NET Framework code is in the form of a DLL then you may have to recompile that DLL as a .NET Standard class library. This ensures that the compiled DLL is compatible with all of the .NET platforms:

- .NET Framework
- .NET Core
- Mono
- Xamarin

### Question 5: Which .NET Core SDK and Runtime do I have?

So .NET Core is split into two separate entities:

- SDK
- Runtime

The SDK is what we build our applications against. When we run commands like `donet new`, `dotnet restore` and `dotnet build`, we're calling the SDK. Regardless of where you install the SDK, you can create binaries for any of the supported operating systems.

{{< pararight "there's a little more work involved than just calling `dotnet build`, but the process is the same" >}}

Whereas the Runtime is essentially just the code required in order to bootstrap and support the running of your application.

It goes without saying that without the runtime, you can't run your application. As such the runtime is always shipped with the SDK. However, you don't want to install the SDK on your production servers for the same reason that you don't want to install Visual Studio on your production servers.

{{< pararight "the servers just don't need Visual Studio to be installed; the same with the SDK" >}}

To find out which versions of the SDK you have installed, you can run:

{{< highlight bash >}}
dotnet --list-sdks
{{< /highlight >}}

and similarly, to find out which versions of the runtime you have installed you would run:

{{< highlight bash >}}
dotnet --list-runtimes
{{< /highlight >}}

### Question 6: Can I Install Multiple SDKs and Runtimes?

Yup. In the same way that you can install multiple different versions of the .NET Framework (on Windows only, obviously), you can install different versions of the SDKs and runtimes side-by-side.

In fact, whilst writing this episode I ran the `dotnet --list-sdks` command on my Mac and was told that I have a lot of versions of the SDK installed:

{{< highlight bash >}}
2.0.0 [/usr/local/share/dotnet/sdk]
2.1.4 [/usr/local/share/dotnet/sdk]
2.1.300-preview1-008174 [/usr/local/share/dotnet/sdk]
2.1.300-preview2-008533 [/usr/local/share/dotnet/sdk]
2.1.300-rc1-008673 [/usr/local/share/dotnet/sdk]
2.1.300 [/usr/local/share/dotnet/sdk]
2.1.403 [/usr/local/share/dotnet/sdk]
{{< /highlight >}}

Which reminded me that I didn't have the latest supported version of the SDK installed. But I have it installed now.

{{< pararight "as of writing this episode, the LTS version of the SDK is 2.1.5" >}}

### Question 7: Where Can I Learn More About .NET Core?

I would start with [The MVA courses](https://mva.microsoft.com/learning-path/asp-net-core-2-0-23) on .NET Core.

I would start with the Beginner course, even if .NET is old hat to you because there are a number of changes and gotchas that almost anyone can fall into.

Then I'd take a look into [Exploring .NET Core](https://shortener.manning.com/rBPe), which is a free (as in beer) eBook from Manning Publishing which consists of a number of hand picked chapters from other eBooks It covers everything from .NET Core itself to ASP.NET Core, EF Core and a little on Micro-services.

Then take a look at both [.NET Escapades](https://andrewlock.net/) by Andrew Lock and [Steve Gordon](https://www.stevejgordon.co.uk/)'s blog. These blogs contain some of the best deep dives into .NET Core that I've seen.

Andrew has also written a book on ASP.NET Core called [ASP.NET Core in Action](https://www.manning.com/books/asp-net-core-in-action)

{{< pararight "check the show notes for a discount code which is good for 40% off of his book (or any other book released by Manning" >}}

I'd also take a look at the source code. The great thing about .NET Core being open source is that you can so much be reading through the source code, which is hosted at [GitHub](https://github.com/dotnet/core).

### Wrapping Up

I hope that I've answered these questions clearly and concisely enough for you all. Be sure to check the show notes for links to all of the resources I mentioned in Question 7.

{{< pararight "also for a discount code good for 40% off of Andrew Lock's book (or any other book released by Manning)" >}}

Remember to check the show notes for a link to the full transcription of this episode, which is available at [dotnetcore.show](https://dotnetcore.show/).

If you like this FAQ style episodes, then be sure to let me know over on twitter [@dotnetcoreblog](https://twitter.com/dotnetcoreblog). If enough people like these episodes, I'll put out more of them and maybe even ask you all for your burning questions.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [YouTube version of this episode](https://www.youtube.com/watch?v=)
  - The YouTube version of this episode, if you'd prefer to listen there
- [CoreWF with Dustin Metgar](https://dotnetcore.show/episode-3-corewf-with-dustin-metzgar/)
- [.NET Core SDK and runtime downloads](https://dot.net/core/)
- [The MVA courses](https://mva.microsoft.com/learning-path/asp-net-core-2-0-23) on .NET Core
- [.NET Escapades](https://andrewlock.net/) by Andrew Lock
- [ASP.NET Core in Action](https://www.manning.com/books/asp-net-core-in-action)
  - `podnetcore18` - this discount code will get you 40% off of Andrew's book, in either physical, ebook or LiveBook formats
  - it's also good for all other books that they sell
- [Steve Gordon](https://www.stevejgordon.co.uk/)'s blog
