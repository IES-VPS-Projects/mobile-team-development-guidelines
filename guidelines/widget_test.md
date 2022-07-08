# Widget Test

* When handling widget test we follow a strict structure of name the test file same as the actual file itself followed with a prefix of `test`.



``` dart script
//i.e

   //sample file

        -- lib
            --src
                --views
                    -- landing_page.dart
//test file

        -- test
            --src
                --views
                    -- landing_page_test.dart

```

* In cases where your file depends on the provider package and other external third-party libraries, use an extension to abstract the code.

* This extension will be reused by other files that depend on the same dependencies

```dart script
///Extension

    extension TestExtensions on Widget {
    Widget wrapWithMaterial() => MultiProvider(
            providers: ProviderConfig.providers,
            child: MaterialApp(
            debugShowCheckedModeBanner: false,
            title: AppConstants.appName,
            theme: ThemeData(
                primaryColor: Palette.primaryColor,
                primarySwatch: Colors.deepOrange,
                visualDensity: VisualDensity.adaptivePlatformDensity,
            ),
            home: this,
            ),
        );
    }

//Usage

  testWidgets('should find a scaffold ', (WidgetTester tester) async {
      Landing page = Landing();

      await tester.pumpWidget(page.wrapWithMaterial());

      expect(find.byType(Scaffold), findsOneWidget);
    });

```


* Each widget test file contains all related tests and is grouped accordingly.

``` dart script 


void main() {
  setupFirebaseAuthMocks();

  setUpAll(() async {
    setupLocator();
    await Firebase.initializeApp();
  });

  group('Landing Page', () {
    testWidgets('should find a scaffold ', (WidgetTester tester) async {
      Landing page = Landing();

      await tester.pumpWidget(page.wrapWithMaterial());

      expect(find.byType(Scaffold), findsOneWidget);
    });

    testWidgets('should find welcome text',
        (WidgetTester tester) async {
      MapPage page = MapPage();

      await tester.pumpWidget(page.wrapWithMaterial());

      await tester.idle();
      expect(find.text('Welcome To Kweza'), findsOneWidget);

    });
  });
}

```

* You should write a widget test for at least all common widgets to avoid creating the same test for the same widget.
 > Ensure the common widget are being tested in the files that they are used
 
 # Example
|<image src="../images/widget_test_1.png">|<image src="../images/widget_test_2.png"> |
|:---:|:---:|

