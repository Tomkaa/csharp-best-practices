# Configuration

Configuration can be set up using extension method on host builder class.

```csharp
IHostBuilder ConfigureAppConfiguration(Action<HostBuilderContext, IConfigurationBuilder> configureDelegate);
```

```csharp
Host.CreateDefaultBuilder(args)
    .ConfigureAppConfiguration(SetupConfigurationBuilder)
```

Configuration typically needs to contain 2 configuration sources:

- **appsettings.json** and **environment specific jsons** (e.g. *appsettings.Development.json*) for settings that can be persisted inside GIT and are unlikely to vary between platforms but can still change.
- **Environment variables** for settings that vary between platforms or contain
  sensitive information. Environment variables are most common for this because
  of their support in containers.

```csharp
private static void SetupConfigurationBuilder(HostBuilderContext hostContext, IConfigurationBuilder configBuilder) =>
            configBuilder.SetBasePath(Directory.GetCurrentDirectory())
                .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
                .AddEnvironmentVariables();
``` 
