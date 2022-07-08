# Imports Formatting
Avoid trailing path from file imports

```dart script
    //i.e

    //GOOD Practice

    import '../../core/utils/language_util.dart';
    import '../../widgets/layout/c_app_bar.dart';

    //BAD Practice

    import 'package:store/core/utils/language_util.dart';
    import 'package:store/widgets/layout/c_app_bar.dart'; 



```

# Do name import prefixes using lowercase_with_underscores
Use lowercase to typecast/ name alias of imports


```dart script
    //i.e

    //GOOD Practice

    import 'package:js/js.dart' as js;

    //BAD Practice

   import 'package:js/js.dart' as JS;



```

# Do specify exports in a separate section after all imports


```dart script
    //i.e

    //GOOD Practice

    import 'src/error.dart';
    import 'src/foo_bar.dart';

    export 'src/error.dart';

    //BAD Practice

   import 'src/error.dart';
   export 'src/error.dart';
   import 'src/foo_bar.dart



```

## NB: All of these styles can be achieved  by using dart format extension
|<image src="../images/dart-import.png"> |
|:---:|
|dart-import extension|
> Open the file you want to format in VSCode then  press `ctrl+shift+p` 
