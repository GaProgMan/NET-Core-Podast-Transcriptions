# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is episode 14: Templating in .NET Core. In this episode, I'll cover how you can work with templates for your .NET Core applications, how to create them, and how to share them.

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Introduction

It used to be that when you wanted to create a new .NET Framework solution, you had two choices:

- Use one of Visual Studios templating wizard
- hand roll you're own project using Visual Studios new File options

And that worked well when you where building a greenfield project with no preexisting code or solution template that you wanted to reuse. You could even download new templates for Visual Studios wizard, but they had to be installed on a per user, per computer basis.

{{< pararight "if multiple users had access to the same development machine, you'd have to install it for each user" >}}

This wasn't optimal, but it was the way things worked for years.

Some folks even created applications which could scaffold an entire solution for you, based on some input parameters. But these where generally slow and a little clunky to use.

If you were brave enough, you could even create a VISX package with your template in and install it on each machine. The problem with this was the barrier to entry: learning VISX wasn't the easiest thing to do, and a lot of VISXs where very much based on other VISXs

{{< pararight "I know that my own VISX packages are based heavily on the ones created by Mads Kristensen, for example" >}}

Then along came .NET Core.

Anyone who has read my blog "[A Journey In .NET Core](https://dotnetcore.gaprogman.com/)" since its inception will know that one of the early ways of scaffolding applications was to use a yeoman based application. This was great, and it worked swimmingly. But it did require nodejs (which is an essential piece of webdev software, these days), and was a little slow to get up and running.

But that's where the .NET Core templating system comes in

### dotnet new3

When version 1.0.1 of the .NET Core SDK was released, Microsoft added support for the templating system. This was originally called `dotnet new3` and allowed you to create templates for solutions by adding a single file (`template.json`) to the solution and running a single command.

As a side note, each time you've used the `dotnet new` CLI command or used the File > New wizard in Visual Studio to create a new .NET Core application, you've used dotnet new3 but haven't realised it.

Not only that, but you could then upload these templates to a NuGet feed and anyone with the .NET Core SDK could pull them down and consume them.

{{< pararight "I've written about the templating engine before, and you can find that article [here](https://dotnetcore.gaprogman.com/2017/04/06/net-cores-new-templating-engine/)" >}}

The absolute magic, we'll get into how this all works later in the episode, with the templating engine is that it will do namespace renaming and conditional code inclusion for you.

Let's have a really quick example using one of the built in templates. If you open a terminal and type in

{{< highlight bash >}}
dotnet new console --name myConsoleApp
{{< /highlight >}}

The .NET Core SDK will scaffold an entire code base for you, based on the global `console` template, and it will ensure that all namespaces start with `myConsoleApp`. That's pretty cool, right?

Now imagine that you want to start an MVC application, well entering:

{{< highlight bash >}}
dotnet new mvc --name NerdDinner --auth Individual
{{< /highlight >}}

Will scaffold an MVC Web application using individual auth.

Hopefully you can see just how powerful this can get. And as Dave Rael said on an earlier episode,

> the Tooling can then get out of your way and let you build applications the way that works for you.

### Custom Templates

 But how do you create your own templates?

It turns out that it's really simple

{{< pararight "again, I've [written about creating your own templates before](https://dotnetcore.gaprogman.com/2017/10/05/creating-a-custom-template/) so check that article out for a deeper dive" >}}

Essentially, you need to create an entire code base first. This could be a console app, an MVC app, a Blazor app, a WebApi app, or a combination of those. You can also use whatever architecture you want - nTier, Onion, whatever. The important thing is to have a working application, but that it must be a skeleton application - i.e. It should have no core business logic or customisations added.

Then you need to create a folder in the top level (or root) of your code base called `.template.config`. This can prove a little tricky in Windows, but should be doable in either Explorer or the command line/powershell. Once you've done that, you need to create a file within that new directory called `template.json`.

The contents of this file can range from incredibly simple to ridiculously complex, depending on what you want the template to do. One of the simplest template.json files will have the following five key value pairs:

- `author`
  - takes a string
  - represents the name of the author of the template
- `classifications`
  - takes an array of strings
  - represents the typos of apps you can build with the template
- `name`
  - takes a string
  - represents the name of the template
- `identity`
  - takes a string
  - represents the base namespace of the template
  - this is the value which is replaced when you supply the `--name` flag
- `shortName`
  - takes a string
  - is the CLI reference name (examples are `webapi`, `mvc`, and `console`)

All of this information is used by the .NET Core CLI to display information about the template, and to provide names pace renaming at creation time.

Command line switches (like `--auth`in our MVC example earlier) can be added by including a section called `symbols`. This is an array of objects, each has the following values:

- `type`
  - usually this will be set to parameter
- `dataType`
  - takes a string representing the parameters type (boolean, int, etc.)
- `defaultValue`
  - takes a string
  - represents the default value of the symbol, if the user does not provide one or use it
- `description`
  - takes a string
  - describes what the symbol does

An example, from one of my [open source templates](https://github.com/GaProgMan/FullStackTemplate/) can be found below:

{{< highlight json >}}
"symbols": {
  "enable-gnu-pratchett": {
    "type": "parameter",
    "dataType": "bool",
    "defaultValue": "false",
    "description": "Whether to include and activate middleware which will include the X-GNU-Pratchett header in all requests"
  },
  "enable-secure-headers": {
    "type": "parameter",
    "dataType": "bool",
    "defaultValue": "false",
    "description": "Whether to include and activate middleware which will include a range of OWASP suggested security headers"
  }
}
{{< /highlight >}}

### Installing Templates

It's all well and good being able to create templates, but how do install them?

Once the template is working, it can be built into a NuGet package and placed either in the public NuGet feed, or on a private or MyGet based feed. Once that's done, you can install the template on any machine with access to that feed by issuing the following command:

{{< highlight bash >}}
dotnet new --install theNameOfTheTemplate
{{< /highlight >}}

As long as that operation completes successfully, you'll have the template installed. You can confirm this by running:

{{< highlight bash >}}
dotnet new list
{{< /highlight >}}

You can even install the template directly from the code base that you're building up. This can be a great way of testing that the template that you are building is correct.

To do this, you just have to run the following command from the root of your template's source code:

{{< highlight bash >}}
dotnet new --install .
{{< /highlight >}}

This will use the `template.json` file found within the `.template.config` directory to install your template locally.

Uninstalling a template (depending on how you've installed it) can be a little tricky.

To uninstall a template that you've installed from NuGet, run the install command again but swap the `--install` for `--uninstall`. So an example would be:

{{< highlight bash >}}
dotnet new --uninstall theNameOfTheTemplate
{{< /highlight >}}

Whereas if you have installed a template the other way (i.e. `dotnet new --install .`), I've found that the sure fire way to uninstall it is to swap `--install` for `--uninstall` and swap the `.` for the full path to the root of the template.

For a real-world example of installing and uninstalling templates see the [commands file](https://github.com/GaProgMan/OnionArch/blob/master/commands.md) found in my OnionArch repo on GitHub.

### Wrapping Up

In this episode, we looked at what dotnet new3 is, how to create templates for the .NET Core CLI, and how to share them.

Remember to check the show notes for a link to the full transcription of this episode, which is available at [dotnetcore.show](https://dotnetcore.show/).

I will see you again some time soon. See you later folks.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [My .NET Core CLI Templates repo](https://github.com/GaProgMan/DotNet-New-Templates)
  - I literally do type `dotnet new podcast` when I'm writing a new episode, you know
- [.NET Core's New Templating Engine]((https://dotnetcore.gaprogman.com/2017/04/06/net-cores-new-templating-engine/)
- [Creating a Custom Template]((https://dotnetcore.gaprogman.com/2017/10/05/creating-a-custom-template/)
- [How to create your own templates for dotnet new](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/)
