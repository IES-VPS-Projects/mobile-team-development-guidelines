# Avoid `print()` Calls
Not only can print expose log messages in production,
but print calls also have a limit on the length of message or information you want to display.
Consider using `log()` from the `dart developer package`.

```dart script
   // i.e

   // GOOD Practice
   final Response _response = ... ;
   log(_response.body)

  // BAD Practice
   final Response _response = ... ;
   print(_response.body)

```
