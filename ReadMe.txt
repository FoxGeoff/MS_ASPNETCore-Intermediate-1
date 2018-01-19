Working Log
********************************

Microsoft Virtual Academy: AP.NET Core -Intermediate
********************************
* Video:ASP.Net Core Internals
********************************
********************************

Feature: Users Secrets
********************************
Context Menu > Manage Users Secrets
Tip DO NOT use Configuration and appsettings.jason -   You can read this in source control :( 

Feature: Application Insights
********************************
Context Menu (project) > add > Application Insights Telemetry
Tip set to local
Tip How to use in @page
	@page
	@inject Microsoft.Extensions.Configuration.IConfiguration Configuration
	@Configuration["MyKey"]

Feature: One place to keep using statements, asp helps for all Razor Pages
*******************************
_ViewImports.cshtml

Video:Tag Helpers
*******************************
#1 Buit in Tag Helpers
*******************************
Pages > Account > Mange > 
_layout.cshtml

<enviroment include="Development">
</enviroment>
<enviroment exclude="Development">
</enviroment>

Ref:   docs.microsoft.com/en-us/aspnet/core/mvc/views/tag-helpers/built-in

_Viewimports.cshtml
	@addTagHelper *, MicroSoft.AspNetCore.Mvc.TagHelpers (assy not name space)

#2 Build Custom Tag Helper
*******************************
Example: RepeatTagHelper used in Index.cshtml

 NB: in _Viewimports.cshtml
 @addTAgHelper *, MyMVA

<repeat count="6">
    <p> Geoff said repeat!</p>
</repeat>

#3 Other people's Helper
*******************************
https://github.com/DamianEdwards/TagHelperPack
https://github.com/dpaquette/TagHelperSamples


* Video:Entity Framework Core
*******************************
********************************
BlogingContext.cs > (Hint: Use peak definition)
	public DbSet<Blog> Blogs {get; set;} //#1
 
	protected ovveride void OnConfiguration(DbContextOptionBuilder optionsBuilder) //#2
		optionsBuild.UseSqlServer(@"Server=...; Database:...; Trusted_Connection=True; ConnectionRetry")

	protected ovverride void OnModelCreate(ModelBuilder modelBuilder) //#3
		modelBuilder.Entity<Theme()./SeedData( 
			mew {},
			new {}
		)

#2 Migrations
*******************************
> Add-Migration <name>  Remove-Migration <name>

> Update-Database

> Script-Migration

#3 Test Console App:

foreeach( var theme in db.Themes)
{
		console.WriteLine(@"Id= {theme.Id}, Name= {theme.Name}")
}

#4  Flexable Mapping

public string Url {get; private set;}
public void SetUrl(string url)
{
	//Do some logic...
	Url =url;
}

TODO add code snippets to the toolbox view!! *************
	 drop and drag custom toolbox items?

	 modelBuider.ENtity<blog>()
		.Property<string>("Url")
		.Hasfield("_url");

#5 SetupDatabase...

private static void SetupDatabase()
{
	USING (var db = new Bloggingcontext)
	{
		db.Database.EnsureDeleted();
		db.Datbase.EnsureCreated();
	}
}

#6 Flutent API... more ...
modelBuilder.Entity<Blogs>()
	.HasMany(b => b.Posts)
	.WithOne(0
	.HsForeignKey(p => p.BlogFK); //because we are not using the convention "BlogId"

	/*Check output to see that the shadow property "BlogId" is now gone!

#7 Querey Filters (new to Core)
*****************************
Eager loading (Include) as opossed to lazy loading!

var blogs = db.Blogs
			.Include(b => b.Posts)
			.where( p => p.date == date)
			.ToList();

Setup a filter in OnModelCreating(..)

	//Configue a n entity filter
	ModelBuilder.Entity<Post>(0.HasQueryFilter(p => !p.IsDeleted);

	Two ways to impliment 
	#1 add IsDeleted to DB
	#2 in code (If property is missing)..

	public override int SaveChanges()
	{
		foreach(var item in ChangeTracker.Entries<Post>.Where(e =. e.State = EntityState.Deleted)
		{
			item.state = EntityState.Modified;
			item.CurrentVBalues["IsDeleted"] =true;
		}
	}
	
#7.2 Tentant Filter
*******************************
modelBuilder
.Entity<Blog>()
.HasQueryFilter(b =. EF.Property<string>(b, "TenantId") = _tenantId);

Sesssion Resources
Demos https://github.com/anpete/efdemos
Project https://github.com/aspnet/EntityFramworlCore
Docs https://doc.microsoft.com/ef/core
Twitter @divega @anpete @efmagicunicons
Blog https://blogs.msdn.microsoft.com/dotnet


*Video:Authentication and Authorization
*******************************
*******************************


Video:Web API and Swagger
*******************************
*******************************
cc

Video:Publishing & Development -  Azure & Docker
*******************************
*******************************

