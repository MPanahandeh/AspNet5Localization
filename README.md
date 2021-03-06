Localization.SqlLocalizer [![NuGet Status](http://img.shields.io/nuget/v/Localization.SqlLocalizer.svg?style=flat-square)](https://www.nuget.org/packages/Localization.SqlLocalizer/)
========================
Documentation: https://damienbod.com/2016/05/26/released-sql-localization-nuget-package-for-asp-net-core-dotnet/


<a href="https://www.nuget.org/packages/Localization.SqlLocalizer/">NuGet</a> | <a href="https://github.com/damienbod/AspNet5Localization/issues">Issues</a> | <a href="https://github.com/damienbod/AspNet5Localization/tree/master/AspNet5Localization/src/Localization.SqlLocalizer">Code</a>

<strong>Release History</strong>

<em>Version 1.0.2</em>
<ul>
 	<li>Updated to dotnet 1.0.0</li>
</ul>

<em>Version 1.0.1</em>
<ul>
 	<li>Added Unique constraint for key, culture</li>
	<li>Fixed type full name cache bug</li>
</ul>

<em>Version 1.0.0</em>
<ul>
 	<li>Initial release</li>
	<li>Runtime localization updates</li>
	<li>Cache support, reset cache</li>
        <li>ASP.NET DI support</li>
        <li>Supports any Entity Framework Core database</li>

</ul>

<strong>Basic Usage ASP.NET Core</strong>

Add the NuGet package to the project.json file

```
"dependencies": {
        "Localization.SqlLocalizer": "1.0.0.0",
```

Add the DbContext and use the AddSqlLocalization extension method to add the SQL Localization package.

```
public void ConfigureServices(IServiceCollection services)
{
	// init database for localization
	var sqlConnectionString = Configuration["DbStringLocalizer:ConnectionString"];

	services.AddDbContext<LocalizationModelContext>(options =>
		options.UseSqlite(
			sqlConnectionString,
			b => b.MigrationsAssembly("Angular2LocalizationAspNetCore")
		)
	);

	// Requires that LocalizationModelContext is defined
	services.AddSqlLocalization(options => options.UseTypeFullNames = true);

```

Create your database

```
dotnet ef migrations add Localization --context localizationModelContext

dotnet ef database update Localization --context localizationModelContext
```

========================

# ASP.NET Core 1.0 MVC Localization Example

<ul>
	<li><a href="http://damienbod.com/2015/10/21/asp-net-5-mvc-6-localization/">ASP.NET Core 1.0 MVC Localization</a></li>
	<li><a href="http://damienbod.com/2015/10/24/using-dataannotations-and-localization-in-asp-net-5-mvc-6/">Using DataAnnotations and Localization in ASP.NET Core 1.0 MVC </a></li>
	<li><a href="http://damienbod.com/2016/01/29/asp-net-core-1-0-using-sql-localization/">ASP.NET Core 1.0 using SQL Localization</a></li>
</ul>



