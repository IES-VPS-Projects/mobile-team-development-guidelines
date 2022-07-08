# Avoid Useless Documentations
 
If your code requires comments  , make sure the comment are specific and direct to the point

```dart script

//i.e 

// BAD:
/// The background color.
final Color backgroundColor;

// GOOD:
/// The color with which to fill the circle. Changing the background color will cause the avatar to animate to the new color.
final Color backgroundColor;
```