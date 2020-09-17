# Getting values from configuration and using them in code

You can get values in HostBuilder/Startup using various available methods, most
notably `Configuration.GetSection(string)` and then inject them into
constructors. However there are several readily available classes to unify this
usage generally known as `IOptions`. `IOptions` support various scenarios and if
your use case has special requirements it's worth exploring full article @ *[docs.microsoft.com](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/configuration/options)* 

## Create options class:
```csharp
public class MyOptions : IOptions 
{
    public string MyProp1 { get; set; }
    public string MyProp2 { get; set; }
}
```

## Register option in dependency injection:
```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.Configure<MyOptions>(Configuration.GetSection("MyOptions"));
}
```

## Injecting options into your class:
```csharp
public class MyClass 
{
    private readonly IOptions<MyOptions> _myOptions;
    // this is solely for convenience
    private MyOptions Options => _myOptions.Value;

    public MyClass(IOptions<MyOptions> myOptions) 
    {
        _myOptions = myOptions;
    }
}
```