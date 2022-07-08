# Split widgets into sub Widgets

When setState() is called on a State, all descendent widgets will rebuild. Therefore, split the widget into small widgets so the setState() calls to the part of the subtree whose UI needs to change.


```dart script

        //Don't

        Column(
        children: [
            Container(
            child: RaisedButton(onPressed: () {
                setState() {}
            })),
            Container(
            child: RaisedButton(onPressed: () {
                setState() {}
            })),
            Container(
            child: RaisedButton(onPressed: () {
                setState() {}
            }))
        ])

        //Do

        Column(
        children[
            widget1(),
            widget2(),
            widget3(),
        ]
        )

```


# Use raw string
A raw string can be used to avoid escaping only backslashes and dollars.

```dart script

//Don't
var s = 'This is demo string \\ and \$';

//Do
var s = r'This is demo string \ and $';

```

# Use Const in Widgets

The widget that will not change when setState is called should be defined as constant. It will prevent the widget to rebuild so it improves performance.


```dart script

 ///i.e

        Container(
            padding: const EdgeInsets.only(top: 10),
            color: Colors.black,
            child: const Center(
                child: const Text(
                "No Data found",
                style: const TextStyle(fontSize: 30, fontWeight: FontWeight.w800),
                ),
            ),
            );

```

# Use interpolation to compose strings

Use interpolation to make string cleaner and shorter rather than long chains of + to build a string.

```dart script

//Don’t
var description = 'Hello, ' + name + '! You are ' + (year - birth).toString() + ' years old.';


// Do
var description = 'Hello, $name! You are ${year - birth} years old.';

```