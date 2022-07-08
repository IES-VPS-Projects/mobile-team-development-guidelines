
# Intergation Test (end-to-end test)

* For integration test we use the `intergation_test` package rather than the `flutter_driver` package.

*  Create an integration_test/ directory for your package. In this directory, create a <name>_test.dart, using the following as a starting point to make assertions.

> rootDirectory/integration_test/integration_test.dart

``` dart script

    import 'package:flutter_test/flutter_test.dart';
    import 'package:integration_test/failling_test.dart';

    void main() {
    IntegrationTestWidgetsFlutterBinding.ensureInitialized();

    testWidgets("failing test example", (WidgetTester tester) async {
        expect(2 + 2, equals(5));
    });
    }

```

* Integration test has driver entry point (script) where the execution is initialized. Create a directory `test_driver/` and create the file there.

* This will be shared across all integration tests.


``` dart script
        import 'package:integration_test/integration_test_driver.dart';

        Future<void> main() => integrationDriver();
```

* Folder structure

 ``` dart script
        lib/
        ...
        integration_test/
        foo_test.dart
        bar_test.dart
        test/
        # Other unit tests go here.
        test_driver/
        integration_test.dart

 ```

 * Launch the test

 Target the file you want to test and run this command in your console to launch the test.

 ``` bash script
flutter drive --driver=test_driver/integration_test.dart --target=integration_test/falling test.dart

 ```

 * Sample

|<image src="../images/e2e_test.png"> |
|:---:|

 
