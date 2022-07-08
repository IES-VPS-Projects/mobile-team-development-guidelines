# UpperCamelCase
Classes, enums, typedefs, and extensions name should in UpperCamelCase.
```dart script
//i.e
    class MainScreen { ... }
    enum MainItem { .. }
    typedef Predicate<T> = bool Function(T value);
    extension MyList<T> on List<T> { ... }

```
# Lower Case
Variables, constants, parameters, and named parameters having one Word should be in lowerCase.

```dart script
   // i.e
    const int count; 

```

# Lower CamelCase
Variables, constants, parameters, and named parameters should be in lowerCamelCase.

This should be done on acronyms and abbreviations longer than two Words

```dart script
   // i.e
    var item;
    const bookPrice = 3.14;
    final urlScheme = RegExp('^([a-z]+):');
    void sum(int bookPrice) {
    // ...
    }

```

# File And Directory Naming
All directories, libraries, and source file's names should be saved in snake_case(lowercase_with_underscores).

```dart script'
    //i.e
    library firebase_dynamic_links;
    import 'socket/socket_services/socket_manager.dart';

```

# Naming Consistency
 All files naming styles chose should be kept and used consistently

 ```dart script
     //i.e

    //GOOD Styling
 
     --lib
       --src
          -- models
            -- user_model.dart
             -- location_model.dart

    //  BAD Styling   

    --lib
       --src
          -- models
            -- user_model.dart
             -- location.dart      

```

# variable Naming

All variables should reflect what they are storing/being assigned, avoid short forms and abbreviations

 ```dart script'
  
    //i.e

    //GOOD Styling

   late ProductService productService;

    //  BAD Styling   

   late   ProductService ps; 

```
