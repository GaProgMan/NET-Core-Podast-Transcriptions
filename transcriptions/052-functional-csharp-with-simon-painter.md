# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR

and not forgetting The .NET Core community, itself.

I am your host, Jamie "GaProgMan" Taylor, and this is Episode 52: Functional C# With Simon Painter. In this episode I interviewed Simon about the functional programming paradigm, a little about the history of functional programming, whether C# is becoming more of a functional language, and what a [monad](https://en.wikipedia.org/wiki/Monad_(functional_programming)) is. You may know of Simon from his [blog](https://www.thecodepainter.co.uk/blog), the [talks that he gives](https://www.thecodepainter.co.uk/talks), or his twitter account: [@madsimonj](https://twitter.com/madsimonj).

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Simon's Introduction

#### Jamie

So the first thing I'd like to say is I thank you ever so much for spending part of your late evening with me, Simon. I really appreciate it. We've all got family. We've all got responsibilities and stuff, and being able to walk away from all of that for an hour is a lot to ask of someone. So thank you ever so much.

#### Simon

It's much easier when you've got handcuffs on an awful lot of gaffer tape to keep the kids under control.

{{< paracentre "(both laugh)" >}}

#### Jamie

So I was wondering before we get started, could you give us a kind of brief introduction into some of the work that you do and where people may know you from that kind of thing?

#### Simon

I've been a .Net developer for something like about 15 years now. I'm based in the West Midlands in the UK.

I started off working for little local companies here in Telford and worked for folks like Cap Gemini, outsourcing work for the _HMRC_ done some work for places like _The Works_. You know, the bookshops that they're on practically every town centre hereabouts and ah, just finished a stint with Europe Scientific overboard Rampton. But these days, I'm one of those contractors that your mum always warned you about when you were little.

{{< paracentre "(both laugh)" >}}

#### Jamie

So one of the things that I'd like to talk to you about today, if that's okay, is functional programming. But functional programming is C# rather than F#. You know, I don't know too much F#. We have covered [F# once or twice on the show](/episode-34-f-and-giraffe-with-stuart-lang/), but it always has been.: here's this thing you could do, also you need to use F# to do it.

So my question to you before we even start is can you describe functional programming for people who are maybe from an OOP background - an object oriented background - or a procedural background, or something? Is there something there must be something that sets it apart right? Otherwise, it wouldn't be a named thing

#### Simon

Sure. So functional for a start is what's known as a paradigm.

So a paradigm is, if you want to metaphor, that the one I usually use is, like, imagine a musical instrument while the instrument is your programming language and your paradigm is the style of music you play and whether you're playing, pop for rock or whatever. You know that those are paradigms. They've got certain rules, certain restrictions, some things you must do some things you mustn't. That's what set paradigms apart there, sort of defined by what you can't do in a way.

So functional. There's not exactly a one single thing it is. It's more a cluster of properties,

So it always favours statements over functions that is things like `if` and `where`, `for` things like that. Those are statements. Those tend not to exist in a functional code. There are other ways of do accomplishing that exact thing. So in a way, if you just remove those from C# and find other ways you're most of the way there.

It features variables which are immutable, rather immutable. That means once you've set the value of a variable, you can't change it no matter what.

Now C# can actually do that as such, but the way forward is kind of pretend it can, because when it comes down to it, there's always going to be a fun little area where you're not able, to make everything immutable, however hard you try, but it also makes you serve what's called higher order functions. That another property ah high order function is kind of a funky sounding term for something that's not terribly complicated. It's just functions passed around as if they were variables. So if you return a function out of another functional past, one in is a parameter or store. One locally is a variable, so `func`s `func<T>`. That's that's higher order functions that all it is.

It makes use of recursions, which is something that we probably all been you aware of since we started out in this business.

It's stateless, meaning there is no state stored in a variable somewhere that you refer to. There shouldn't really be any concept of that. They're kind of other ways of tracking state.

It uses some legal pattern recognition, which it's a little tricky to describe. But basically switch statements with knobs on is like the nearest taken get. It's like this super advanced version of switches where you could do an awful lot more than just a simple check against value.

And the other important concept is pure functions. It's referential transparency is the technical term for this.

The whole idea is that given the same parameters, a function will always return the same value no matter what, no matter the life of the universe, no matter the state of the system. No matter if you always give these same values and you always get this same value back. It's one of the very powerful properties of functional in that it makes it extremely testable. And that is one of the huge draws these days is functional compared to OO(P) is extremely easy to test and very robust. As a result,

I'd also argue it's not terribly difficult. A lot of people sort of think it is, and I think a lot of it is just lack of exposure. It's a little bit of a mental leap to get around to it, but once you're over that, it's actually not that difficult at all.

I've chatted to folks coming at the university when I've done talks on when I describe a lot of stuff that I do to make C# functional, they say, Well, this is what the teachers at the university now, so it seems like functional is very much the coming paradigm. It's becoming more and more popular as years go by. I notice on the events list for NDC Oslo. Whenever I look at the schedule, there's always more functionally there and not less so. It's definitely here to stay, I think, especially when you consider that it's something like over 100 years old, which it is.

#### Jamie

I was going to say. I do know that it's based on some of the work that [Alonzo Church](https://en.wikipedia.org/wiki/Alonzo_Church) did and oh my goodness, there's a mathematician,  I've forgotten his name...

#### Simon

[Haskell Curry](https://en.wikipedia.org/wiki/Haskell_Curry).

#### Jamie

That's the one, because I was going to say Tim Curry, it's not the same person.

#### Simon

But wouldn't that be awesome? Yes. Not only is he the most awesome kick ass guy that you remember from your childhood, but also is like one of the greatest programmers in the world, he's just that cool now, not him, sadly, but Ah, yeah, Haskell Curry here was I believe no fewer than three programming language is named after him.

I think they've sort of salvaged every tiny bit of his name and used it somewhere.

#### Jamie

Well, I mean, we'll know it's difficult to name things, right?

#### Simon

Absolutely. But yeah, I did actually dig out some of the old maths text because they're on the Internet to go poking around.

In fact Alonzo Church came along when functional programming had kind of already been around for a long time. It wasn't called functional programming. In those days it had a different name. I can't remember something like composable functions or they were a cluster of schools of maths that we're focused around the same area. But they are very, very, very hard to read if you're not a mathematician, and I am not a mathematician, I'm an engineer, so.

One of the other things I think that makes some people struggle a bit with functional is if you go looking up like the proper definitions of how this stuff works on what it is. You're kind of see the maths driven stuff, and it's all like `f of g = x [[[...`.

And honestly, I can't make any sense of that at all as I'm an engineer. So what I want to know is, what does it do? What's it for? How do I use it? And I think once you've let it go and actually doing it, it's not all that hard. 

#### Jamie

So we talked a little bit about the background that we mentioned you, Haskell and Church and you explicitly mentioned universities. And then my biggest worry is that, do I need to have gone to university to understand the paradigms behind functional programming? Or can I perhaps approach it from, like I said, maybe object oriented or maybe a procedural or something? Do I need a huge amount of maths behind me?

#### Simon

Not in the slightest No. In fact, if you're doing C# now, there's a good chance he's already using a chunk of functional as it is.

So if you go use Linq and you know I would, because Linq is, well, cool. But Linq is functional. It really is. It's Ah, it's immutable. So when you do a select, it's not modifying the original array that you came from. It's actually creating a new one based on the old one. That's a functional concept.

And what you're doing is you're passing in a function as a parameter and getting back an interface. That's again that's higher order functions. It's another functional concept. So things like `select` things like `aggregate` or those handy little link helper functions. That's all functional stuff. So all we're doing is kind of trying to take C# and put the whole thing into a link. In a way, you're trying to make everything and see shot look of it, _Linqy_. And if you do that, you most of the way there.

#### Jamie

Okay, so if we're talking about see show being quite functional were mentioning links specifically Andi, I'm thinking more the type of like like you say, where you do a select statement rather than linked to SQL where you're writing the SQL inline.

If I do, I'm gonna use the word lambda. It's not the actual name for it in C#, they're delegates. But that's essentially what a function is, isn't it? Right you're passing in a function of the type `T` to get, is it work to get a `func<T>`.

#### Simon

Yeah, that's exactly it. Incidentally you're right. It is a delegate or the point of trivia they're named the reason they're called Lambda Expressions actually comes from a Alonzo Church's work.

He described a way of shorthand writing functions that used little arrow that we use in C# today. The only difference was that he used the Greek letter _lambda_ to denote parameters. Which is why we called the lambda expressions when he did that back in the 1950s, I think.

But yeah, that's that's exactly what it is. So, yeah, where is a `func<T>` and that generates kind of behind the scenes? What we're doing is generating a function based on that on the arrow, I guess. I don't know a great deal about the IO behind the scenes, but it's, I think it generates and converts it all once you press the run.

#### Jamie

Yeah, as far as I'm aware because it's lazy loaded, it does that sort of conversion last. So I guess because you create the delegate. I'm making a bunch of logical leaping assumptions based on what you said so far. I create a Lambda statement using the `goes to` the _equals_ and then the arrow sign. Then that doesn't actually operate until I iterated over it. I have a collection of numbers and they say, `where X > 3`. When I say go and iterate over that list to produce maybe a list or an array when I say `.toList`, when I say `.toArray`, it will actually then go and perform that. So then, at that point, I guess it's passing that function. Like you said earlier, It's passing the function I've generated over that rather function I've written into the `where`  function to do the thing is doing that almost like a pure function. Like you said, it's passing a function as an argument. I guess.

#### Simon

That's exactly it. The lazy loading thing isn't necessarily a functional concept, although it is, well, cool.

Yeah, I've done an awful lot of playing with with enumerables that you can kind of leave them in the box as it were, without springing it open for as long as possible, but still do all of your work. But that's just a neat feature of C#, but yes, absolutely and also, if you call the function returns a func, because that's something that you can do, then that would be higher order function as well.

So one technique that I sometimes use is you can have an arrow function that turns another arrow function, and there's all sorts of things you can do with that I often use. It is a shorthand way of generating the lambdas for inserting into things like `select` and `where` and similar, just mostly to make it a bit more descriptive. Rather than having the sort of big, long chains of arrows with mathematical symbols in them,

I might actually do something like Create a function that is, let's say, an ad where we have a single parameter. Let's call it `int x`, and then we'll do arrow. And then after that, we'll have `y` and then another arrow so and then at the end of it, we do `x + y`.

This is a functional technique called [Currying](https://en.wikipedia.org/wiki/Currying). So what it means is that effectively, there are two parameters, `x` and `y`, why which you add together. But you can call them one after the other. And when you call the first you get back a function where the first is already filled in for you, and then you need to provide the second into that function to get an actual answer.

That's this is like the simplest version of this I can think of. Currying, of course, after Haskell Curry.

And In that particular instance, I've mostly used that for something like, if I knew that I was gonna do a whole load of chains where there's gonna be some adds and subtracts and stuff like that, I might do something like just call `add(4)` and then passed out into, say, a `select` or whatever to make it more obvious or make it more descriptive. 

That's That's a really simple example, but you can do all sorts of very complicated things. I've used a similar technique in the past for having a func, which is used to break apart CSV files. We have to supply what am I breaking each line by, what am I breaking each field by, what conversions am I playing at which point stuff? What data typed I want out. And if you do arrow functions that generate other arrow functions, you could just kind of write one and then apply the parameters in batches to get out of function, which is already part filled for you. So instead of writing, you know, 50 different pauses. You just write one, and then you supply the bits that you need as you need them. If that makes sense,

#### Jamie

Yeah, that makes sense to me. I feel like it's similar to like your storing part of the parameters you're passing into a variable and passing the variable in rather than the actual value, right, so you might have an add function that takes in two input variables rather than the actual value. If that makes sense, or rather passing in three and four, you might pass in two variables into one and into but in a much more complicated way.

#### Simon

Oh, no, it's not. It's not necessarily complicated. It's as they say, with a lot of these things. Half the trick is just have a go at it. And then once you've actually started using it, it's not hard anymore.

Similarly, really object orientated is a lot more complicated than we think it is. If I have tried to explain object orientation, too, the folks that don't know what it is or haven't been exposed to it, it's surprising how difficult it is to bring across the idea to them, because we've probably all been living with it. Certainly, I've been living with object orientation for 20 years, so to me it's just obvious.

But when you haven't had that exposure. It's very complicated to explain. The whole concept of class was his object. And then we start getting into things like _inheritance_, _polymorphism_. And they're not we as it were, that would just be mind blowing

and similarly function was not all that complicated. And once you've actually been practising for a while, it just becomes obvious after a bit.

#### What is a Monad?

#### Jamie

Sure. Okay, The reason I keep mentioning procedural is because you know, my first bit of programming experience, unfortunately, had to wait until college tow actually do it properly. I did do some programming back in the day when I was, you know, wee nipper in basic. But my first proper exposure to programming was in assembler, which is arguably very procedural. It's, you know, this that this that this that this branch, if not equal or branch if equal like I think there are no objects. There are no global states. There's nothing. It's just one long list of instructions I can remember when I was first getting into object oriented programming at university and they were saying, This is a thing and these things describe its _thingness_.

Trying to describe to someone how you break something down into its _thing-ness_ properties and then splitting those out so that a `cat` is a type of `feline` but also a `leopard` is a type of `feline`. So there are a number of things which describe both of them. The example that I used to give with shoes. You know, you have a `shoe` class but there are different types of shoe `running` shoe `walking` shoe, `dancing` shoes. They're gonna think, and then you can branch off from there. But all of the issues will have common properties. You stick them in that sort of base implementation and use polymorphism to extend each one.

But yeah, that you like. You say it does get a bit confusing to start with. So I guess like you say is functional. But like that once you've gotten past that bashed your head against the wall for a number of hours and it just clicks. Is that the case? Or is it just keep going? And in 10 years time, it'll all make sense. I promise.

#### Simon

No, I mean, I can only speak for myself, of course, but certainly for me, it was very much like, like, bold moment. And then by what? This This is easy. Like, Why did I ever think this was hard? It's very much like that, like with the dreaded monad.

It's not, actually, all that difficult. Once you understand what it is, it's not hard at all to understand it and how to use it. If you want briefly to understand what that is. Although allegedly, according to Douglas Cropfield, the curse of the moan at is that once you've gained the ability to understand that, you lose the ability to explain it. To be honest, I'd argue it's not necessarily all that hard.

So if you want to build the simplest monad in all of the world right now in C#, you create an extension method. You do something like `public static T output`. Call it `map` for now, that's as good a name as any. And then we'll do our our squared chevron's I don't know how you call them. The angle brackets and do `<TInput, TOutput>`. So we've got an input type to an output type, and we don't really care what they are, and then we'll attach to this `TInput`.

So it's an extension method that attaches to everything. And then you take a single parameter, which is a func, which turns a `TInput` into a `TOutput`. So `func<TInput, TOutput>`. But call it whatever you like. call it `f` call it `func`, I don't really mind.

And then the entire body of the function is call that function that was passed in as a parameter and stuff this into it. That's it. You just do that and you've created your first monad. Now this is ridiculously simple and quite fragile.

But what this means is that everything everywhere in C# has got this extension method now where? Let's say you've got a string. Anyone starts adjusting it, you can do `yourString.map()` and then passing lambda expression, which I don't know, maybe it doesn't int pars. Maybe it splits or something, and then that returns a new value. And then you can whatever new value came out there. Let's say, for example, that we're doing a CSV parse so we'll do `"my giant string`, which is everything `.map` and we'll call a `string.split` inside that, and then we'll do another `map` because now the input is an strings. So because `map` attaches to the entire object, it's like a `select` except it operates on the entire array at once, not on an individual element like a `select` does.

So inside the second one Maybe we'll do another split. So now we've got an array of arrays, which is like the first dimension is the row. The second dimension is the column. And then after that, we could do a map to, I don't know, convert everything into integers. And then we've got an array of an array of integers, and so what? We can do all sorts of messing around with this. But that's actually all the Monad, really is that it's very, very, most ridiculously simple.

It's something which allows you to call functions in sequence, and each one takes the output of the last one and then pass it into the next one, like a relay race. That's all it is. So we're just doing chains of functions, each one feeding into the next one after the other. At its very very, very, very most simple. That's all it is. Where it gets interesting is way. Start delving into the Why don't we start putting some slightly more complicated logic into the point at which we switch from one function to the next?

So what we're effectively doing is separating out the function that the user's given us from how we carry it out. How we executed? So maybe we might want to put a `try...catch` around that, in which case now your code has sort of become immune to error because there's a `try...catch` built into every call to the to the map, say function.

There's a whole load more that can be done with this, but that's it. It's most simple. But does that make sense.

#### Jamie

It certainly makes sense to me. But my question to you as a user of functional paradigms is do I need to understand, Monads, to be able to use functional paradigms. I know it's one of the features of paradigm. But is it something that is, "you won't be able to do proper functional until you can figure this out. stroke beard, stroke beard."

#### Simon

Well, I'm gonna say this carefully because as we speak the masses with their pitchforks and flaming torches air outside looking for me. But NO. 

I mean Monad are cool. Monads are amazingly useful. I'm like scratching the surface on this because there's all sorts of amazing ways that you can use thumb toe right code, which is kind of entirely free of errors but also very descriptive. But no, you CAN do without them.

Like I say, if you just start using a lot more Linq, then you're getting a chunk of the way there. Stop trying to adjust variable values and just start to think that each one should be based on the last but converted over using probably a function. Incidentally, that is a rule of thumb with functional. If there's a question, the answer's usually functions, so that's another way that you know you're on the right track. It's definitely very, very useful that there is a wonderful article by Scott Wlaschin called Something like _[Railway Orientated Architecture](https://fsharpforfunandprofit.com/rop/)_

It's a beautiful illustration of how to use a Monad effectively. So what you can do is something like, Imagine having an abstract based class, so we'll call it I don't know what we'll call it. Maybe we'll call it. `Maybe`. That's a good thing as any. So don't worry about why I'm calling it that for the moment. So that's an abstract. And all that is is something which has a single property anf the abstract class takes their generic. It takes a `t`. So it's got something like `public class Maybe<T>` like that. And its just init. All it has is the property, which is of type `T` and locally value.

And that's all there is. That's all we've got at the basic level, and I will inherit from it twice. On the once. We'll call it `something`  the once we'll call it `nothing`. So you've got you've got to actual classes that you can instantiate at any time.

And the something is just a straight inheritance out from the abstract, so it was just a value. Think of it as thing in a box it's just a value in a box. That's all it is,

And then the other one, you override the value with with default whatever. So that would mean if it's a string you get `null`, it's an object, you get `null` if it an int you get zero, if its a boolean you get false. So whatever the default value is, it's nothing. And then you go and create your map style extension method where you're just saying attach this to everything,

But this time was saying that you have to be a type of `maybe` so you'll create two extension methods is to do this. The first one attaches to `t everything` as in the whole of C#, and then just convert whatever you've just called it from into a `Maybe` so you're create from that and you something class, and then take whatever valley was this and stuff it inside. So if you started with a string which would say "my name", then you call that too may be Now what you got is they may be containing a string which is valued with "my name". And then we also need to do a new a new map-y thing, which is where we ask for a function to converted from the old one to the next one.

And a better name for that, in this case, is bind for reasons that escape me. That's what it's generally called.

What we'll do is first off will put a `try, catch` around the whole thing.

And then the second thing we'll do is we'll do a switch statement of the value. And, you know, in the latest person of C#, we could do so much more fun things with switches where you can switch against all sorts of awesome things. But all we really want to do is to say, is the value that's just come into us, which, actually, as it happens at the moment, is "my name". But let's say do the generic version of a null check and If it comes in at no or default, rather, then let's return them nothing.

If it's not default, then we'll take the function that was passed in as a parameter to our bind.
 
And then we'll run. It will pass in this and then pass on out with another, `maybe` containing contained any value. So that's an awful lot of talking. But the way that Scott Wlaschin explains it is imagine that you've got two sets of train tracks running in parallel. They're running from the beginning to the end and. There's a series of points that is shared by each set of tracks,

And each one of these points represents a function. The top track is everything works. That's the track we go along with. Everything worked. So you know, Runner, I don't know. We'd start with a string. We'll do a database operation. Did it work yet? Carry on along the same track. We'll do something else. Maybe we'll try and convert it. Maybe we'll try and pass to him. Did it worked? Great. Carry along the top track. But the moment that something doesn't work, either it errors or it returns. Default will switch to the other track by which it means return The nothing class.

And, we put into the logic that if the maybe is actually a nothing, we don't run the function. So the power of the monad here is the first off we put a try catch every call. And then the second amazing thing is that you can have this single chain of functions one after the other, like lambda or whatever, all defined in one single chain.

And then if at any point one of those functions fails or doesn't return, then all of the subsequent functions are not called.

So all of that usual logic that we have to write into every single function like, you know, get a value run process one check it against null check it against empty check for errors. All of that is actually entirely contained within the structure of the Monad.

So this is one of the other amazing advantages of functional programming is that it's extremely concise compared to object orientated programming. You're talking about reducing the number of lines of code dramatically, because what you're doing is you're embedding the structure of the code into the language and, just sort of giving it the bits that you really care about and allowing the background paradigm to be taking care of all that code noise that we don't want to be bothered reading. Are we making sense?

#### Jamie

Yeah, that makes a lot sense.

I'll make sure that there's a link to the blog post that you mentioned _Railway Orientated Architecture_ just full. You know, folks who want to go and read that and get it. That's slightly more detailed description of it. Just because there are a lot of people will take the majority of that in, but not really kind of get it, I guess, until they've seen that diagram that you're talking about with the two train tracks and it makes sense. It's almost like a state machine, isn't it? We get to this operation. Did it work? Carry on to the next one, otherwise drop out to the second railway track.

#### Simon

Yeah, in many ways, a lot of ways that state machine is implemented is bordering on functional paradigm as well I would yeah, the the blood posting questions on these Web site thing. It's _F# for Fun and Profit_, which isn't half shot website, and I'm not disparaging F#. But if you don't know F# and I don't personally, then don't be put off because this ah, it's a fairly technology neutral article instant. It's well worth a read.

### Is C# Slowly Becoming Functional?

#### Jamie

So you mentioned a whole bunch of stuff they were on about, you know, the fun pattern matching stuff, which is I think you'd said you'd switch statements with knobs on or bells and whistles on like you said. We have that now in C# eight, and there's a lot of stuff that is leaning towards functional life. We know already there.

So I mean, there's nothing stopping  from being a functional language because you could do functional programming in it. But in your opinion is see sharp, slowly becoming a functional programming language and world just being slowly nudged in that direction.

#### Simon

There's no, in my opinion about that is literally what Microsoft have actually said.

So I don't know about it because I don't think any intentions it become the dominant paradigm of C#. But I have seen talks from the head developer of C# in he outright. Right said that the whole intention is that C# to become this sort of hybrid, functional/object orientated language where you can, right to the paradigm that suits you In effect.

I do believe that what's happening is that the F# guys on the C# guys kind of feeding off each other's work. So whenever the F# guys request new features into C# to allow them to do more of their functional stuff, the sea shot because it'll shares the same common language in the background. The C# guys benefit from it as well, and so we, to some degree, can start using it ourselves. It's no coincidence that as of C# 8, we've started having the option to turn on the compiler warnings for if you write code, that might change the value of a variable that's all designed to allow you to start moving more in the direction of the functional paradigm.

So, yeah, absolutely I don't think it's in  anyway a controversial opinion. But C# is absolutely intended to be a hybrid functional language.

#### Jamie

Interesting that makes sense than I don't know, whether it's purely functional, but one of the things that jumps to mind when I think functional programming, that idea of passing in those pure functions those What do you say they were called...

#### Simon

Higher order functions.

#### Jamie

Thank you.

I start thinking about JavaScript and its ability to have the like. So we talked about Linq right, so Javascript has things like `map` and, those kinds of things where you could pass a function in to allow you to somehow iterated over a collection of things. Maybe it's an array. Maybe it's a collection of objects or something and filter things that map filter, those kinds of things. And then I start thinking about when you do asynchronous Web requests or http requests you can do `.then` and passing her function or `.catch` and passing a function on, they start to think a little bit like that. So is that where we're going? Do you think so? We can have, Like you said this hybrid language because, like I see JavaScript as being a hybrid it's an, at the same time, procedural, object oriented, functional. Whatever other techniques you want to talk about language, so is seashell heading in that direction? And what does that mean? Does that mean that hopefully people aren't thinking?  will become JavaScript. The sky is falling because that's no great,

#### Simon

Absolutely let you on a little secret. From what I've seen, JavaScript is actually more functional than C# and particular structure you mentioned, it's called a promise incidentally, that is a moment that in and of itself, that's another example of a monad that that probably people been using for years.

So there is a scary sort of like a knee-jerk reaction gets Monad, but they're kind of friendly and we've been using them for ages. But yes, absolutely. You can do some really wild, certainly. So it is a really wild, functional programming in JavaScript. Er, yeah, I honestly think that functional at the moment, at least, is very much part of the way forward.

It's definitely useful right now. I think one of the reasons has become particularly popular is the increased interesting stuff, like serverless because a serverless function is, in effect, a pure function. It's a function that operates without state and can't depend on anything except for it's own parameters give and take. Oh yeah, I think that's one of the reasons that we're seeing. An acceleration of the interest in functional is because it supports stuff like that, and it the stateless nature of its support stuff like async.

So. One of the things that tends to make large, asynchronous apps struggle is when you've got common shared state between functions. Well, that's the sort of thing the functional paradigm simply doesn't have.

So, yeah, if you wanted to do an awful lot of a think, if you wanted to do an awful lot of serverless than functional, is the stuff you want to be looking into.

I don't think that's a bad thing at all. I don't think that we're looking at a world where you know pure, functional languages are the norm. I think that's I think the object orientation is fine. It's always could have its place. I rather like, C#'s kind of hybrid approach because there are benefits to be had from object orientation and the inheritance system that's quite nice and concise.

But hopefully C# will allow us to use the best features of both.

#### Jamie

If you think about it. For instance, a Web server, his doing proper rest stuff is meant to be stateless. So a Web Server, an MVC application of Web API application seems like a really good target for functional. And we have talked about _[Giraffe](https://github.com/giraffe-fsharp/Giraffe)_ in the past on the show and how there is a way of building an MVC style Web application with with F#. 

But I think you're absolutely right. The idea that serverless functions. Lambdas those kinds of things. The idea is yet to make the code as small as possible, such that it doesn't require any dependencies and can be ran by itself. It doesn't have any kind of holding of any state or anything. I mean, they can read and write to an external thing if it needs to in a way store state. You shouldn't have to rely on it because what if that function goes down?

#### Simon

Well, it's kind of where as well where your monads come in. If you're chaining stuff and you want to, build some robustness into allegedly with pure, functional languages. Once you've actually got to the point where the thing will compile, it will go up and it will stay up like forever. That's the claim, and I've got no direct evidence of some of those languages myself. But I've certainly seen some maps that have got incredible up-times compared to some of the stuff that you, can do sometimes in C# so and we're renting a concession again. But that's actually not something that's to be understated, because by reducing the amount of code that you write your in fact increasing how easy it is to read and to understand exactly what it's doing, which sounds like a small thing. But it is so useful when you're in production because we've always been in that situation where our manager said, Go away and make this quick. Little change here is just a little while and then you look into the code base and it's just so lengthy and so split all over the place. We've got ifs, nested inside, ifs nested, inside ifs. nested inside goodness knows what, and it becomes very, very, very hard to know where to make your change.

But if you follow the functional paradigm and keep everything kind of neat and concise, it becomes potentially very easy to know where to make a change and to understand quickly the code that's in front of you because there's every chance that you'll be regularly delving into areas of the code. Basically, we've never seen before, so we're actually saving ourselves an awful lot of time and therefore an awful lot of money by moving in this direction.

#### Jamie

So one are the things that we were sort of made to do at University was read lots of theoretical text books. And you know, one of them, which I really enjoyed, which wasn't some much theoretical, was Code Complete and in Code Complete. Steve McConnell says that if you I don't think he uses the word "prime directive", you know our main goal as software engineers, software developers, developers, whatever code is whatever word you want to use our our main goal is to make sure that our code is understandable by another human being, because the good pilot will do crazy tricks to make your code more optimised that you would never even think of.

There are hundreds and thousands of person hours have gone into developing the compiler and people with incredible amounts of knowledge about how CPUs work in the virtual machine that .Net runs on works. All of this knowledge has been provided for you for free, such that your code will be as optimised as possible within certain limits. But the C#, F#, VB, javascript, whatever language you're using, that code needs to be a simple as possible to follow for another human being because the other human being is going to be maintaining or changing that gold and that other human being. Maybe you in six months time.

#### Simon

Oh, yeah, and casting for other people. But I can't remember what I had to breakfast yesterday. I definitely can't remember what I was coding last week. I haven't a hope of remembering what was coding a month ago.

#### Simon

Maybe that makes me a bad person, I don't know, but there we have it on. There's only so much I could do with leaving notes for myself. So a side effect of writing in this style is often that what you end up writing is quite close to a sort of natural language way of describing what you're doing as well as actually doing it. So it becomes relatively easy to understand. It's just there is some structures that you take in as well, but they're not. They're not all that complicated. I've kind already talked you through the monad is about hard as it gets, or something like recursion. But then again, recursion is something we've all been using for years.

An awful lot Linq, I believe, is based around recursion, certainly for you use something like Aggregate, which is one of the coolest bits of Linq's. People, if you haven't tried it. Go try it. But that's that's just based on tail recursion.

#### Jamie

Like he was saying, Making the code is simple to read as possible goes back to, but this will date the recording. I was reading a tweet today about an engineer who had already run into the 2038 problem, which is something that will affect all Unix and Linux based systems in 2038 when the integer that is used to log time ticks over back to zero is essentially y2k, but much more far reaching because the financial sector runs on UNIX and Linux and big branches of government run Hunt Linux in Unix. So this could be a huge problem. But the reason that I bring this up is because in the tweet thread I'll put into the show, it's the Indian in the tweets red, the person who tweeted about it and said, We've already seen this in 2018, you know ,20 years before it was meant to have happened, and the reason I bring it up is because the person had mentioned that the reason that this coded crashed was because it's expected some stuff to happen and then because of 2038. But it took them, Ah, whole day on some change to actually figure out how to fix it and answer. And it cost the company $1.7 million in lost revenue because the code was written in such a way that it was very well optimised, but not very well optimised for other human beings to read. I mean, I can't speak for the situation and I can't speak for the code in question. But perhaps from the way you have been saying it, if it was written in a functional way, it might have been easier to understand week it. We'll never know, will we?

#### Simon

No, Probably not. I don't imagine that they want us to wear to see what it is. They were what they were dealing with.

But generally speaking, I mean, obviously you can still write unreadable functional code the same way if you know that lazy code is unreadable, no matter what paradigm and you're working with us. But generally speaking, it tends towards a set of very good practises for keeping your code in a nice, neat order. One of my particular pet aches is one of those gigantic functions I would imagine a lot of us have dealt with where it's a putz of the 1000 lines long, and it's got variables at the top. That reference to, you know, hundreds of lines down and still in scope all the way at the end of the project. And it's got if statements that looked like a family tree, you know, the sort of thing I'm sure we've all dealt with this. And you simply general don't get that in functional code. It's it's far too neat for that. 

It is perhaps worth mentioning on performance, though I haven't done any really in depth benchmarks into the using your mostly see functional code in C#. But I don't believe it's necessarily the most performant way to write it.

That's not to say that it's Unperformant. It's mostly pretty good. But if performance is your absolute 100% driver, then it may not necessarily be for you. I've seen I've dug into the There's a book come out just recently. _High performance C#_, some marvellous stuff in that, but it's kind of looking at it is kind of antithesis to what we're trying to achieve in the functional world. It's code that isn't necessarily terribly read or what is extremely performant. So it's probably a matter of, as is always the case in the computing world. What are you trying to achieve?

And if it's if it's, you know, business applications of business logic. And the most important thing is that we keep turning this stuff out and getting out changes done and into production. They're functional, probably more the sign that we want to go towards.

Whereas if it's the absolute most important that we get this as performant as it's humanly possible to make it, you certainly have C#. You probably want to be very more towards the style of code in that book. C# isn't necessarily 100% optimised towards functional, but it's still it's still very good. It's still very performance,

#### Jamie

You said really run a little bit about how you haven't really got a lot of experience with F#, but other than C# is a hybrid language which allows you to do functional stuff and F# from a 10,000 foot view is this esoteric language, which alleges to do. He's tearing to me anyway. Tio let you do functional stuff and syntax. Is that essentially the only difference? Or is it? Are there things that maybe you don't know the answer to this question of other things that you can do in that shop you can't do in C#?

#### Simon

First, I will state upfront that I've only dabbled in F#. I kind of like it. I kind of like what I saw. I like the look of F#. It's it looks pretty cool. It's even more concise than C#. The syntax is a bit of a barrier because it's not quite so comfortable. Familiar is the good old C style syntax has been around since, when is it, like late seventies or something? But it's a pretty good one of the big difference is I noticed immediately was that all the variables are genuinely immutable. That is, it has actually got it enforced in the language that once you've set a variable, you can't change it. That's actually there, whereas in C#, because everything continues to be mutable, even if you do all sorts of tricks to try and spread the immutable and, Fundamentally, it's still going to allow you to change stuff somewhere in your code, but F# in forces that I know. 

It's got a much more advanced pattern recognition feature than although that might actually not be correct. As of the latest version of C#, which has got the new function style switches, I have played with those a little bit, and they are very, very cool indeed. And we're we're kind of bordering now on the proper F# style pattern recognition system, which is where your case isn't just like a simple value. It's more like a whole series of like a whole cluster of statements, potentially or some more complex. Select based on some properties of your object to decide if this is the case and then the case itself, maybe something more sophisticated than just a return or whatever. So we're getting there. We're getting there, but I'm not disparaging F#. I do like the look of it, and I would like to learn it. My only concern was just picking up F# and running with it is I would always be a bit reluctant to learn it too much because ultimately, I'm not sure whether we're at the point. Yet as a developer community, where we're likely to get a whole production applications written in F# at least as a common thing. I know that they exist.

#### Simon

But there's the reason being that if you go to any dev conference and chuck a stone, you'll probably hit someone that knows how to develop in C#.

Whereas there aren't necessarily that many people that know F#. And in order for us to be comfortable to take on a programming language in production, we want to make sure that we can that the whole team is comfortable to work in it and that we could easily get more folks in whatever we need. to, continue working on it in the moment F# a little bit more of a niche skill compared to see sharp. So that's why I think we're not quite there yet. I'm not saying that one day there won't be widespread F# usage everywhere. I could imagine that happening, but I can foresee that being more in the medium future rather or even the far future rather than the near, but it is. It is very cool on it is worth your time, I think.

#### Jamie

Either way, just check out functional programming anyway.

#### Simon

Absolutely, and since you could just get started in C#, why not just start using today and then one day if it turns out that F# becomes the thing, or Elm, Haskell, or one of those other pure functional languages if you're already doing functional programming and C# or JavaScript or whatever you're comfortable with and you probably find that most of the concept of stuff that you're already familiar with and you just have to learn the syntax and I worry about the extra stuff.

#### Jamie

Again, that all makes sense, you know?

So I've always found it's the syntax or the concepts that stops me from learning some new techniques and new language simply paradigm.

But if you can learn one without the other, which is totally doable, then come back and learn the other. Like you said earlier, you don't necessarily need to know what a moan that is. Even though you gave a really simple example, you don't need to know what one is to be able to use.

#### Simon

Well, I am probably most the people listening a engineer. So what we're really interested in is what's it for? What do we do with it? Why would I use it? Why would I use it? The theory doesn't necessarily matter. So much is there and similar to what you're saying. I'm very interested in the moment in learning a lot about machine learning, because that's that's a very hot topic at the moment.

But if you pick up most of the textbooks, all the examples tend to be Python and a Python looks remarkably cool. But I don't know Python, and I don't work in a company that makes use of Python, so I don't get much exposure. So there's that sort of, like you say, there's a double overhead of. I need to learn the machine learning concepts. Plus, I need to learn Python, and that's a bit of a double hit and makes it rather hard. So what I'm doing is similarly, too. What I've been doing a C# and that is I'm taking just like the textbooks, the talk entirely about the concepts, and then I'm implementing them. The algorithms in a language I'm familiar with, which, hey, it's C#. That's what I do and then if I ever want a transfer that knowledge over to Python, then it's just simply a matter of picking up the the syntax. I've already got the concept. It's going pretty well so far. I could imagine that Python is probably a lot more optimised to machine learning that C#, but that's that's not the point of learning it that way.

#### Jamie

I do remember something that one of my university lecturers said was, and I believe Scott Hanselmann has echoed something similar. And that's If you know, warn programming language and you're trying to learn another. Programming languages are kind of polymorphic and that they have this inheritance tree. You know, we mentioned earlier on you said yourself, sea based languages. So . C, JavaScript, Python Ah, bunch of these languages will have very common things that'll come from C. Presumably F# I'm guessing is coming from maybe a Haskell background of one of the other functional programming backgrounds.

Because, it has a similar sort of syntax tree to it. So once you have the concepts of one you can kind of fumble your way through. So, like if somebody was to show me a page full of Java and be able to figure out what he's doing, I wouldn't be able to immediately make changes and make individual bit twiddling changes. But it's similar enough that it gets you over that barrier and then you know in your example of I'm going to learn the concepts, implement them in C# and then learned how to do that in Python. Perhaps that works as sort of like it's almost like double testing your your knowledge because you've implemented already and . And then you take that C shop and convert it to python and then go look back at the concept and go Oh, yeah, I did it. Definitely. I definitely understand this concept.

#### Simon

Yeah, absolutely. I've even known people who have gone all the way hardcore into a pure functional language like Haskell and like, gone and learned that really well to learn exactly how that works, how its structure. Then come back to something that C# and bring some of those ideas back with you because you kind of missed the toys that you've gotten used to working at Haskell.

So it's all to play for.

#### Jamie

Oh, definitely in them. Like I said that, you know, Hanselmann makes a point of saying, you know, learn three types of programming language an object oriented, a scripted, and some of a functional language because they were all into connected somehow. And you can apply the knowledge from one just like you said that someone's gonna learn the in's and out's of Haskell and come back to  and has changed how the right C# and maybe for the better. Maybe not for the better. I don't know, I can't say, But he gives you that extra understanding of Oh, that's why we do it this way in this language on. I totally get why it's done that way in that language now, because they have exposure of both and the positives and negatives, or maybe not negatives. But the bonuses and non-bonuses, I guess of refusing one language over another.

#### Simon

No, absolutely. I think I think practical experiences. That is the absolute most important thing because.

I think once you've actually had a play with some of these somebody's structures certainly like the Monad is. There is the poster child of concepts that is supposed to be hard to understand. But I think if you just sit down and implement one, I give an example from my talks of just a very simple process for converting Fahrenheit two Celsius, which is, you know, a simple series of operations where you have to. I can't know what it is. It's something like Divide by 9 multiply by 5 and Deduct 32 because, (whispers) of course you have to.

#### Simon

But that's an example of the sort of operation a Monad does well. So if someone, if you were to just sit down, make yourself a couple of extension methods, and then write a function that will do that in steps, you know, the three of the operations or maybe even converted into a string with a degree centigrade symbol on the band, you could do, you know. You could go crazy, do all sorts of stuff with this. But if you just sit down and do it and do it a few times, and I think after that it doesn't really feel all that strange and complicated, it starts to see or feel kind of comfortable in my own code. I tend to write it very functionally, indeed. Like I'm working through the You're familiar with the Advent of Code. Yes, I do love it. Cool, isn't it?

They're tough. I mean, some of them, some of them are easy, but most of them are pretty tough. And I, being an absolute, you know, coding addict, and I enjoy that sort of thing. So my so I tend to practice my functional style coding on on those because they're really nice, meaty algorithms to try and get into. So my challenge to myself is, I'm planning to solve all of them using only arrow functions in the entire application that will solve all of them. It's a bit hardcore, but that's that's kind of like the hardcore functional approach to everything. So by using only arrow functions, I am forced, not to have state. I'm forced to use nice, concise, small functions. It is forcing me to think a little sideways about how to solve things that otherwise I probably do with, you know, half a dozen lines of normal object orientated code. I'm not saying I'd necessarily do it exactly that way in production.

The whole idea is that since I'm doing this for fun, let's go all the way. And then the best bits of what I'm working out how to do to write these nice, concise little structures. I'll bring back to my production work later on. It is working out. I've found all sorts of awesome little hacks that you can stick into C# to make it happen.

#### Jamie

I do like doing things like Advent of Code and, Code Wars and Project Euler and things like that. These air great resource is for sort of daily practices. Those sort of daily katas as it were, just sort of figuring out how to solve a problem in a specific programming language or whatever, because, how do I put it. But anyone can figure out how to hello world or FizzBuzz, most in any language given enough time.

But FizzBuzz and hello world, I'm going to help you in your day to day work. Unless, of course, you are going to lots of job interviews because all they're going to do is ask you how to do fizzbuzz, and you gotta pass the job interview. But then, when you get to the actual meat and potatoes of doing your daily grind, you're not going to be able to actually do anything, because all you know how to do is fizzbuzz and hello world. It doesn't take a lot of time, I guess, to figure how to do those kinds of problems solved those kinds of problems in a new language or framework. But looking at real problems that maybe you won't face in real world, you know, like you know, the heavy mathematical problems of Project Euler or Advent of Code. You're probably not going to solve those on a daily basis if you're a Web developer, but it gives you enough experience of using those higher order. I don't say higher order functions because it's not what I mean, but that how you were thinking of how do I solve this problem with effectively with the Lego set that I have been given off this program or this paradigm or this framework?

#### Simon

Yeah, absolutely. I mean a lot of the puzzles that it gives you in. It's certainly an advantage coat. They are absolutely comparable to the level of complication of some of the hardest systems I've worked on in the past.

In fact, day-to-day coding is probably nowhere near as complicated as that is, which it's so it's definitely good to kind of keep yourself shop as it were. So keep practising and thinking of, like, better ways to do the stuff that we're doing and to look up algorithms that might have all sorts of uses later on. There's no such thing as useless. Knowledge is something I've always try out saying the folks.

#### Jamie

Yep, an old girlfriend of mine once said that she will happily sit and read any book about any topic, fact or fiction. Because somewhere in that book there will be at least one nugget of information that she can apply to her life somehow and make her a better person. And I don't really agree. No knowledge is useless.

#### Simon

That sounds like a challenge. My wife used to say that she would watch anything on telly, and then I showed her Twin Peaks. She has not trusted my opinion since. Way watch the whole of series three together, and I liked it.

#### Jamie

Fair enough, eh? So they keep to a happy marriage is not to watch Twin Peaks together is what you say?

#### Simon

Possibly well, depending. And unless your partner is into in which case, it's the best thing you could possibly do.

#### Jamie

Absolutely. Okay, well, I mean, those are all of the, aside from the you know the question towards the end there.

#### Jamie

Those are all of the questions that I have. What I want to say is, thank you ever so much. I know I said at the beginning, but I really do mean it. Thank you so much for spending this time with me because, you know, it's currently half past 10 at night. And, you know, we've all got to get up and go to work in the morning sort of thing, and you got to find some time to do whatever it is you do to chill out and relax at the end of the day, and talking to me over the Internet is probably not one of them. So Thank you.

#### Simon

I don't know is been fun. Thank you for having me. And if anyone's interested, my website is [www.thecodepainter.co.uk](https://www.thecodepainter.co.uk). You can find all my contact details and links to social media there. I didn't name the website, but people seem to like it.

#### Jamie

I was going to ask for where people could go to catch up with you and find out more about you, but you've already You ready doing that for me? So that's brilliant.

#### Simon

I'm on Twitter as well at [@MadSimonJ](https://twitter.com/madsimonj). And you can find me on LinkedIn and all those various other I'm pretty easy to find.

#### Jamie

Okay. Excellent. So just before we go, what are there any excellent resource is out. Therefore, if someone is a C# developer wants to learn functional paradigms. What's your top tip? Your number one resource, if there is a number one resource.

#### Simon

If I was to be dishonest to say come and look at my website there's a blog but no, My blog has barely started and there's not very much on it. That would be very disingenuous. But now I would I would say that the absolute best resource I've come across so far is a book published by Manning called _Functional Programming and C#_. It's by Enrico Brian. I know it's a fabulous book. I'm not exaggerating. It's just about one of the best programming books I've read in years. I loved it. It was one of those where there's so much interesting stuff. I had to read a chapter and go away and think about it and play with it and implemented and then go before I could go on with the next chapter It It's an absolutely marvellous book and. It's certainly the place I'd recommend, starting with the There are other books on the topic out there, but that is head and shoulders, the very best one that I've come across yet. 

#### Jamie

Okay, excellent. What I'll do is I'll make sure to put a link to that in the shownotes as well, should. People want to look through and find out more about it.

I have noticed that they're awesome programming books out there. That's just a personal opinion. There are some programming books out there. Where is very much a case of  "copy of this code. Now that you've got the code copy this next block of code. Now that you copied that block of code. Look, you've just made a website" and it's like that's not really teaching me anything. That's just that could be a blog post, you know?

#### Simon

Yeah, absolutely. And of course, there is the Scott Wlaschin website. I know it's a sort of F# website, but first off, f# is great. Second off, he has got a lot of articles on there, though there are, like a little bit more technology agnostic, and you can just read and understand without necessarily needing to worry about the F# syntax that's also worth a go, I think Packt have got a book on functional as well. I was like Vishnu Angora. I think the guy's name was That was pretty good. It's not quite as good as the book by Manning, that's that's the best one by far. But there's plenty of plenty of other resources out there.

There's even plenty of resources to have a look around in JavaScript as well, because there's a lot of folks doing functional code in the Java script world. Most of us are probably pretty familiar with Javascript, enough to feel comfortable reading out reading stuff from that.

#### Jamie

Excellent. Okay, Yeah. I mean, the majority of my work is. You know, when they say full-stack developer, they mean you know C# and JavaScript and SQL server. So, like I said, only one. If you can understand one language enough, you consort of glean the bits of information from other languages And you know, a lot of languages that have functional support all use similar syntax they may not know, use exactly the same said tax. But that sort of arrows and tax the equals on the right. Chevron.

I've heard it referred to as goes to. So I've always said goes to. You know, So you might say `X` goes to `X.toString()` or something like that.

But yeah, they all tend to use a similar syntax either equals and then the right chevron or a minus or hyphen on the right. Chevron. That whole idea of pointing this is where we go. We take this variable and put it into this function. So if you can understand it in one language, you probably will be able to understand it in another.

#### Simon

Yeah, And even if F# uses it as well, it's it's not really all that different to kind of imagining a C# application where it's all arrow functions, if you can imagine that. And what? The hoops you have to jump through to make it work. There's still Yeah, there's still some syntactical differences. But, you know, it's not quite such a leap from one to the other, then.

#### Jamie

Yeah, I agree completely, but, I mean, I'm not coming at it from a functional background. I'm just coming at me from learning it from language, but yeah, I could totally see what do you mean.

Okay, Well, like I said earlier, one has been wonderful to check with you this evening and. Thank you ever so much.

#### Simon

Cheers. Thanks again.

### Wrapping Up

That was my interview with Simon Painter. Be sure to check out the show notes for a bunch of links to some of the stuff that we covered, and full transcription of the interview. The show notes, as always, can be found at [dotnetcore.show](https://dotnetcore.show/), and there will be a link directly to them in your podcatcher.

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice - head over to [dotnetcore.show/subscribe](/subscribe) for ways to do that - and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### Useful Links

- [Simon on Twitter](https://twitter.com/madsimonj)
- [Simon's blog](https://www.thecodepainter.co.uk/blog)
- [Monad on wikipedia](https://en.wikipedia.org/wiki/Monad_(functional_programming))
- [F# and Giraffe with Stuart Lang](/episode-34-f-and-giraffe-with-stuart-lang/)
- [Alonzo Church](https://en.wikipedia.org/wiki/Alonzo_Church)
- [Haskell Curry](https://en.wikipedia.org/wiki/Haskell_Curry)
- [Currying](https://en.wikipedia.org/wiki/Currying)
- [Railway Orientated Architecture](https://fsharpforfunandprofit.com/rop/)
- [Giraffe](https://github.com/giraffe-fsharp/Giraffe)
