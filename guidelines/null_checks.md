# Lazy Instantiation 

To initialize variables later, use late initialization

``` dart script

//Encouraged

 late AuthProvider provider;
  @override
  void didChangeDependencies() {
    super.didChangeDependencies();
    _authProvider = context.of<AuthProvider>(context, listen: true);
  
  }

// Not encouraged

 final  AuthProvider? _authProvider = null;

  @override
  void didChangeDependencies() {
    super.didChangeDependencies();
    _authProvider = context!.of<AuthProvider>(context, listen: true);
  
  }


```

# Use `??` And `?.` Operators

Prefer using ?? (if null) and ?. (null aware) operators instead of null checks in conditional expressions.



``` dart script


// For   [If null]

//Don't
v = a == null ? b : a;

//Do
v = a ?? b;



// For [null aware]

//Don't
v = a == null ? null : a.b;

//Do
v = a?.b;

```


# Don’t Explicitly Initialize Variables


``` dart script

//Don't
int _item = null;

```