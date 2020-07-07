# Episode Transcription

Hello everyone and welcome to _THE_ .NET Core podcast - the only podcast which is devoted to:

- .NET Core
- ASP.NET Core
- EF Core
- SignalR
- and not forgetting The .NET Core community, itself

I am your host, Jamie "GaProgMan" Taylor, and this is episode 12: Entity Framework Core. In this episode, I'll talk a little about what Entity Framework Core is, and what it allows you to do.

So lets sit back, open up a terminal, type in `dotnet new podcast` and let the show begin.

### Introduction

All CRUD apps require access to some data store or other. We need to Create, Update, Read and Delete records in that data store, but how do we do it? It seems that Microsoft has created many different technologies in order to let us do just that.

First there was ADO NET; this was a technology which allowed us to create an instance of the `SqlConnection` class and perform arbitrary commands on a SQL database using the `SqlCommand` class - including possible SQL injection code, too. ([Bobby Drop Tables, anyone?](https://xkcd.com/327/)).

Using ADO NET allowed us to read rows from the database via the `Read` method on an instance of the `SqlCommand` class. This would read the values from the database row into an object array. The value for each column from the row is read and exposed as a string, but there are extension methods to attempt to read the values as certain types (`GetDateTime`, `GetInt32`, `GetGuid`, etc.).

This allowed us to manually read each row in a POCO (Plain Old C# Object), however it was a slow arduous task. If you did a select for the first 100 rows, for instance, you would need to attempt to read from the reader 100 times before you could close the `SqlConnection` instance.

{{< pararight "and of course it was important to close the connection to the database for reasons which should be obvious" >}}

Then Linq to Entities came along and made everything so much simpler.

Unlike ADO NET which required an instance of the `SqlConnection` and `SqlCommand` classes, Linq to Entities used the idea of an `ObjectContext` which is a wrapper around the connection to the Database.

The big innovation that [LINQ](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/linq/) brought was the ability to include SQL-like statements in code. Rather than wrapping a SQL command in a string (and parameterising scalar values, of course), you could literally type the commands into your C# or VB source files.

An example of a LINQ to Entities based query would be something like:

{{< highlight csharp >}}
var query = from books in context.Books
    select new
    {
        BookName = book.Name,
        BookId = book.Id
    };
{{< /highlight >}}

{{< pararight "remember to check the show notes for the code listing that I just read out" >}}

And this is a much simpler way of achieving the same goal.

### Entity Framework

So just what is Entity Framework and what is so great about it?

Imagine being able to query your database without having to deal with creating instances of `SqlConnection` objects (and remembering to close and dispose of them, of course). Imagine being able to query your database as if it's some in memory collection of strongly typed class instances, as well. Those two points are _some_ of the killer features of Entity Framework.

Whereas previously we had to write all of the code for communicating with the database (as you saw earlier) and we had to manually script any schema changes that were required in order to reflect changes to the models. This is all taken care of for us by Entity Framework.

With Entity Framework, everything revolves around the `DbContext` class. This class represents all of the code required to communicate with the Database. It also includes things like change tracking, so that you can build up a large transaction of many database actions before committing it to the database.

The `DbContext` class requires a connection string and a range of `DbSet<T>` properties (one per table in your database). But once those have been provided, you can query the `DbContext` object with familiar LINQ to SQL or LINQ to Entities code in order to query the database and return pre-hydrated object instances back from it.

EF allows you to use one of two different models:

- Database First
- Code First

These both expose different ways for your application to work with a database. In Database First, you connect Entity Framework to a database and it will aid you in creating a set of .NET models which represent the schema.

{{< pararight "I haven't used this EF model that much, but it can be really good at querying a pre-existing database, or if you have a DBA who can draft the schema for your project" >}}

Then there's Code First. With Code First, you create a collection of .NET classes which represent the schema that you want and EF will generate and run the scripts required to set up that schema in the database. This can be great if have lots of experience with .NET, but not very much experience with your chosen Database technology.

That sentence isn't meant to be offensive in anyway. Some folks have more experience with .NET than they do with Database engines and schemas, that's all.

In either of those two (Database First and Code First), there will come a time when your .NET models will have to change; this could be a for range of reasons. Perhaps a new feature is requested and more data needs to be stored, maybe a field needs to be removed from a table, maybe you need to enforce data type limits (you may want to enforce some kind of validation at the schema level, for instance).

Either way, your database schema will need to be migrated in order to represent these changes.

In the old days, we had to manually write the migration scripts ourselves. Then we'd have to re-write them because we'd probably forgotten some field or other, or gotten the database into some strange situation.

Entity Framework can abstract all of that away, as it can detect when those migrations have happened. Essentially, it compares the schema with the `DbSet<T>` instances which represent that schema. When it detects that changes have happened, it can either automatically migrate the schema to reflect those changes or it can provide you with scripts so that you can migrate the schema differently.

### Auto vs Manual Migrations

Both auto and manual migrations have their place, but I tend to prefer manual migrations.

In auto migration mode, when EF detects that there is a mismatch between the schema and the `DbSet<T>` reflected in the `DbContext` object, it will automatically and 

{{< pararight "and this is the important part" >}}

silently alter the schema in order to match the new `DbSet<T>` instances and their relationships.

No system is foolproof, and mistakes can happen. By enabling Auto Migrations, you run the gambit of EF intuiting your changes incorrectly and leaving your database in a state where it's unusable.

That is why I prefer manual migrations.

In manual migration mode, when EF detects that there is a mismatch between the schema and the instances of `DBSet<T>` reflected in the `DbContext` object, it will throw a runtime error and will force you to manually migrate the database schema.

"Manual" here is a misnomer, because EF will still help you by generating the scripts required to migrate the database, but you will have to run them manually.

All of that is a bit complex, so let's have an example.

Let's say that your database schema is represented in the `DbContext` with the following two classes:

{{< highlight csharp >}}
public class User
{
    // Primary key
    public int UserId { get; set;}
    public string UserName { get; set; }

    // Foreign key to ShippingAddress table
    public int ShippingAddressId { get; set; }
    // The shipping address refered to by the
    // ShippingAddressId will be hydrated into
    // this instance of the ShippingAddress instance
    public virtual ShippingAddress ShippingAddress { get; set; }
}

public class ShippingAddress
{
    // Primary key
    public int ShippingAddressId { get; set; }
    public string AddressFirstLine { get; set; }

    // Foreign key to users table
    public int UserId { get; set; }
    // The user refered to by the UserId will be
    // hydrated into this User instance
    public virtual User User { get; set; }
}
{{< /highlight >}}

hopefully, you can imagine the database schema which would represent these two classes

Each class has a `virtual` member - the ShippingAddress has a `virtual` User, and the User has a `virtual` ShippingAddress. The `virtual` keyword is used here to help EF to figure out which tables map to other tables through their foreign keys.

Now lets say that you need to add a new property to the `ShippingAddress` table called `ZipCode`. Well, you alter the `ShippingAddress` class to add it, then tell EF that it needs to migrate the schema.

The altered `ShippingAddress` class could look like this:

{{< highlight csharp >}}
public class ShippingAddress
{
    public int ShippingAddressId { get; set; }
    public string AddressFirstLine { get; set; }

    // This is our new property
    public string ZipCode { get; set; }

    public int UserId { get; set; }
    public virtual User User { get; set; }
}
{{< /highlight >}}

Then, depending on whether you are using Visual Studio or the dotnet CLI, the command that you need to run to tell EF that there is a migration to add will be slightly different. Here is the command for migrating the database from the CLI:

{{< highlight bash >}}
dotnet ef database migrations add AddedZipCodeToShippingAddress
{{< /highlight >}}

This will scaffold a new class called `AddedZipCodeToShippingAddress` (or whatever you called your migration) which will have two methods:

- Up
- Down

The `Up` method is used update your database and add new features to the schema. Whereas the `Down` method can be used to undo them. The contents of `AddedZipCodeToShippingAddress` migration class should look something similar to the following:

{{< highlight csharp >}}
public partial class AddedZipCodeToShippingAddress : Migration
{
    protected override void Up (MigrationBuilder migrationBuilder)
    {
        migrationBuilder.AddColumn<string>(
            name: "ZipCode",
            table: "ShippingAddress",
            type: "TEXT",
            nullable: false,
            defaultValue: ("")
        );
    }

    protected override void Down (MigrationBuilder migrationBuilder)
    {
        migrationBuilder.DropColumn<string>(
            name: "ZipCode",
            table: "ShippingAddress"
        );
    }
}
{{< /highlight >}}

Once you've given the migration code the once over and made sure that it reflects what you want it do to, you can force EF to apply that migration by running:

{{< highlight bash >}}
dotnet ef database update
{{< /highlight >}}

This will force EF to convert the contents of the `Up` method into SQL and apply it to your database.

### What About Querying

As I said earlier, you can access the `DbContext` object and query any of the tables that you find there, using LINQ to SQL or LINQ to Entities. Let's say that you have a method on a`UserService` which is used to search for a given user's `ShippingAddress` entity.

{{< pararight "the following may not be the best or most efficient way to do it, but it will do for the example I'm trying to make" >}}

This method may end up looking like the following:

{{< highlight csharp >}}
public class UserService
{
    private readonly DbContext _dbContext;

    public UserService (DbContext dbContext)
    {
        _dbContext = dbContext;
    }

    public ShippingAddress GetShippingAddressForUserId (int userId)
    {
        // dbContext here represents a connection to the database.
        // EF will use the LINQ we write here to generate a SQL
        // script to get the relevant ShippingAddress from the database
        var shippingAddress = _dbContext.ShippingAddresses
                    .FirstOrDefault(shipAddr => shipAddr.UserId == userId);
        return ShippingAddress;
    }
}
{{< /highlight >}}

The LINQ statement in the previous example method will be translated into something which matches the following SQL:

{{< highlight sql >}}
declare @targetUserId as int;
SELECT *
FROM [dbo].[ShippingAddresses] as shippAddr
WHERE shipAddr.UserId = @targetUserId
{{< /highlight >}}

The actual SQL wont match because EF will do some things in the background to make the SQL more performant like using short scalar values and such.

The most important thing to remember is that EF will utilise LINQs deferred execution model.

### But What's Deferred Execution, Jamie?

Because connecting to a Database, running a query, parsing the results and hydrating them into POCOs takes time, EF uses Deferred Execution. This allows it to run the query and get the response when you actually use the response rather than when your LINQ code is interpreted at the IL level.

All of that is an incredibly roundabout way of saying that EF will not actually run the generated SQL when you call `GetShippingAddressForUserId` (from above). It will only run that SQL when you actually use the returned model. Here's an example using the `UserService` from above:

{{< highlight csharp >}}
public class controller UserController
{
    private UserService _userService { get; set; }

    public UserController (UserService UserService)
    {
        _userService = userService;
    }

    public string GetZipCodeForUser (int userId)
    {
        // call the service
        var shippingAddressEntity = _userService.GetShippingAddressForUserId(userId);

        // tell EF to actually run the SQL and hydrate the
        // shippingAddressEntity variable, then use C#'s property
        // accessor to get the ZipCode value
        return shippingAddressEntity.ZipCode;
    }
}
{{< /highlight >}}

EF will only actually access the database, via the DbContext, when we call the property accessor (i.e. the dot operator) on the entity that we returned from the service. This is a very important distinction, and is something that you need to remember as you start to work with Entity Framework.

### Change Tracking

Let's say that you start making updates to tables. Well, EF keeps track of all of the changes that you make to any fields on any of the things reflected in the `DbSet<T>` objects.

Again, that's complex, let's have an example. Let's say that you need a method to update a user's `ZipCode`. Remember that EF will not run the actual SQL until you tell it to access the properties of the returned entities:

{{< highlight csharp >}}
public async Task<int> UpdateZipCodeForUser(int userId, string newZipCode)
{
    var shippingAddress = _dbContext.ShippingAddresses
            .FirstOrDefault(shipAddr => shipAddr.UserId == userId);

    // When we run this line, EF runs the SQL generated
    //in the previous line
    shippingAddress.ZipCode = newZipCode;
    // At this point the hydrated model's property values
    // no longer match those in the databse row. So we
    // need to tell EF to generate a script to update
    // the values for that row

    // This line generates and runs the SQL required
    // to update the values in all rows which have been
    // changed since the _dbContext last queried the
    // database
    return await _dbContext.SaveChangesAsync();
}
{{< /highlight >}}

Each time that you query the `DbContext` object, EF will make a note of the entities that you've accessed. This way, when you call `SaveChanges` (or more likely `SaveChangesAsync`), it knows which tables to run update queries on. Without this, EF wouldn't know which tables and entities that it needs to update.

If you are doing read-only queries, then you can tell EF not to worry about tacking any changes by doing something like this:

{{< highlight csharp >}}
dbContext.ShippingAddresses
    .AsNotracking()
    .FirstOrDefault(shipAddr => shipAddr.UserId == userId);
{{< /highlight  >}}

This tells EF that we're not going to be making any changes. As such, the next time that we call `SaveChanges` (again, or `SaveChangesAsync`) EF will not know about any changes that we have made to the value or entities that we've asked for, it will also not bother to write a SQL query to update those values.

### Wrapping Up

Although EF and EF Core and incredibly simple to use, they can be quite complex under the hood. EF Core is arguably faster than EF, but it has fewer features than it's older sibling. I didn't have much time to touch on it, but EF Core doesn't do things like lazy loading because (and I'm quote [Julie Lerman](https://twitter.com/julielerman) here) a lot of folks get it wrong.

Entity Framework (regardless of whether you use the original version or the Core version) can make querying databases incredibly easy, and simplifies a _lot_ of the common stuff that we do with CRUD apps.

Using EF when you don't know a lot of SQL can make the developer experience of interacting with a database a lot simpler, and can be a great way to get up and running very quickly.

There is a _lot_ more detail to EF and EF Core that I've intentionally left out of this episode. EF can get quite complex, but I've covered the basics in this episode, and I'll provide links in the show notes.

{{< pararight "head over to dotnetcore.show, or check your podcatcher for a link" >}}

Hopefully you've found this interesting, if you did then let me know by sending me a tweet [@dotnetcoreblog](https://twitter.com/dotnetcoreblog/), or head over to the website [dotnetcore.show](https://dotnetcore.show/) and let me know what you think.

Remember to check the show notes for a link to the full transcription of this episode which also has links to a bunch of related websites and resources. These is available at [dotnetcore.show](https://dotnetcore.show/).

And don't forget to spread the word, leave me a rating or review on your podcatcher of choice, and to come back next time for more .NET Core goodness.

I will see you again real soon. See you later folks.

### External Links

- [ADO.NET on Wikipedia](https://en.wikipedia.org/wiki/ADO.NET/)
- [Exploits of a Mom on XKCD](https://xkcd.com/327/)
  - Also known as "Johnny Drop Tables"
- [ObjectContext](https://docs.microsoft.com/en-us/dotnet/api/system.data.objects.objectcontext/)
- [Deferred Execution](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/linq/deferred-execution-example/)
- [EF Core Documentation](https://docs.microsoft.com/en-us/ef/core/)
- [LINQ](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/linq/)
