#### C#

**iOS**

Register the Identity extension in your app's `FinishedLaunching()` function:

```csharp
public override bool FinishedLaunching(UIApplication app, NSDictionary options)
{
  global::Xamarin.Forms.Forms.Init();
  LoadApplication(new App());
    ACPIdentity.RegisterExtension();

  // start core
  ACPCore.Start(startCallback);

  return base.FinishedLaunching(app, options);
}
```

**Android**

Register the Identity extension in your app's `OnCreate()` function:

```csharp
protected override void OnCreate(Bundle savedInstanceState)
{
  base.OnCreate(savedInstanceState);
  global::Xamarin.Forms.Forms.Init(this, savedInstanceState);
  LoadApplication(new App());

  ACPIdentity.RegisterExtension();

  // start core
  ACPCore.Start(new CoreStartCompletionCallback());
}
```