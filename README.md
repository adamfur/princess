# Your princess is in another castle!
## My fall from grace to the circles of hell. Looking for her.

### SignalR + Azure Web Job

SignalR requires a Owin context, usually that means listening to a port unless you do a little hack. :)


```cs
// In the begining of the Azure Web Job
var assemblyName = Assembly.GetAssembly(typeof(OwinServerFactory)).GetName().Name;

using (WebApp.Start<Startup>(new StartOptions
{
    ServerFactory = assemblyName
}))
{
    // Code here !!!
}
```


OwinServerFactory must be in the root namespace
```cs
public static class OwinServerFactory
{
    public static void Initialize(IDictionary<string, object> properties)
    {
    }

    public static IDisposable Create(Func<IDictionary<string, object>, Task> app, IDictionary<string, object> properties)
    {
        return new Disposable();
    }
}

```
