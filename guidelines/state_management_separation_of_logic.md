# State Management
Flutter offers different state management solutions. At Kweza we use the `Provider package` and `setState` to handle our state.

This is how we access and recommend to access provider(s) in our flutter projects.

```dart script
//i.e
        context.read<AuthProvider>().loadUser();
```
The provider package provides a different way to access registered providers, but for `consistency`
in our codebase we recommend the following pattern to be followed.