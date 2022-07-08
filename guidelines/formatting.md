# Use Spread Collections

We often append one collection with other, spread collection syntax leads to simpler code.

```dart script
        //Don't
        var list = [4,5,6];
        var newList = [1,2];
        newList.addAll(list);


        //Do
        var list = [4,5,6];
        var newList = [1,2,...y];

```

# Use `if` Condition Instead Of Conditional Expression

In times when we need to render a widget based on some conditions in Row and Column. If conditional expression return null in any case then we should use if condition only.

```dart script
        //Don't
        Widget getText(BuildContext context) {
        return Row(
            children: [   
                Platform.isAndroid ? _text('Android') : null,
                Platform.isAndroid ? _text('Android') : SizeBox(),
                Platform.isAndroid ? _text('Android') : Container(),
                ]
            );
        }


        //Do
        Widget getText(BuildContext context) {
        return Row(
                children: 
                [
                    
                    if (Platform.isAndroid) _text('Android')
                ]
            );
        }

```

## Exception

> When you have an if statement with no else clause and the whole if statement fits on one line, you can omit the braces if you prefer:


```dart script

            //Do
            if (arg == null) return defaultValue;

            ////////////  [ If the body wraps to the next line, though, use braces:]


            //Do

            if (overflowChars != other.overflowChars) {
            return overflowChars < other.overflowChars;
            }


            //Don't

            if (overflowChars != other.overflowChars)
            return overflowChars < other.overflowChars;

```

# Employ Early Return 

To avoid nested if statements 

``` dart script

  /// BAD

    someFunction(bool cond1, string name, int value, AuthInfo perms)
        {
            int retval = SUCCESS;
            if (someCondition)
            {
                if (name != null && name != "")
                {
                    if (value != 0)
                    {
                        if (perms.allow(name)
                        {
                            // Do Something
                        }
                        else
                        {
                            reval = PERM_DENY;
                        }
                    }
                    else
                    {
                        retval = BAD_VALUE;
                    }
                }
                else
                {
                    retval = BAD_NAME;
                }
            }
            else
            {
                retval = BAD_COND;
            }
            return retval;
        }


/// GOOD

    someFunction(bool cond1, string name, int value, AuthInfo perms)
    {
        if (!someCondition)
            return BAD_COND;

        if (name == null || name == "")
            return BAD_NAME;

        if (value == 0)
            return BAD_VALUE;

        if (!perms.allow(name))
            return PERM_DENY;

        // Do something
        return SUCCESS;
    }


```


 
# Use Cascades Operator


If we want to perform a sequence of operations on the same object then we should use the Cascades(..) operator.


```dart script
            // Don't
            var path = Path();
            path.lineTo(0, size.height);
            path.lineTo(size.width, size.height);
            path.lineTo(size.width, 0);
            path.close();  


            // Do
            var path = Path()
            ..lineTo(0, size.height)
            ..lineTo(size.width, size.height)
            ..lineTo(size.width, 0)
            ..close();

```

#  Use `async/await` Overusing Futures Callback

Asynchronous code is hard to read and debug. The async/await syntax improves readability.

```dart script
        // Don’t
        Future<int> countActiveUser() {
        return getActiveUser().then((users) {
            
            return users?.length ?? 0;

        }).catchError((e) {
            log.error(e);
            return 0;
        });
    }


       
        // Do
        Future<int> countActiveUser() async {
            try {
                var users = await getActiveUser();
                
                return users?.length ?? 0;
            
            } catch (e) {
                log.error(e);
                return 0;
            }
        }


```


# Use Of Const

Use const for variables that won't change


```dart script

        //Do
        const pi = 3.14;


```


# Avoid Using `as` Instead Use `is` Operator
Use of as operator can throw an exception if the cast is not possible. To avoid this exception, we can use is.

```dart script

//Don't

(item as Profile).name = 'sachin';


//Do
if (item is Profile)
  item.name = 'sachin';

```


# Always Declare Return Types



```dart script

        //GOOD

        Future<int> countActiveUser() async {
        try {
            ....     
                return users?.length ?? 0;
            
            } catch (e) {
                ...
                return 0;
            }
        }

        // BAD:

        Future countActiveUser() async {
            try {
            ....     
                return users?.length ?? 0;
            
            } catch (e) {
                ...
                return 0;
            }
        }
```


# White Space

* Use white space/line after every block of code.



``` dart script

// Good
Future<PageModel>  getPage()
{
    final var page = ...

    if (! page) {
        return null;
    }

    if (page.isEmpty) {
        return null;
    }

    return page;
}





```


* Don't add any extra empty lines between {} brackets.


```dart script
var name='name';

// Good
if (name) {
    name == 'not name';
}

// Bad
if (name) {

      name == 'not name';

}


```

# Indent Multi-line Argument And Parameter Lists By 2 Characters

When breaking an argument list into multiple lines, indent the arguments two characters from the previous line.

```dart script
// BAD:
        foo(
            bar, baz);
        foo(
            bar,
            baz);
        foo(bar,
            baz
        );

        // GOOD:
        foo(bar, baz);
        foo(
            bar,
            baz,
        );
        foo(bar,
            baz);

```

# Avoid Lines Longer Than 80 Characters