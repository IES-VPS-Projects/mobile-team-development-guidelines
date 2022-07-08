# General

* When writing a test, the test folder should emulate or resemble the actual folder structure of the files that are being tested.



```dart script
    //i.e

//--- Folder Structure--
    -- lib
      -- src
        -- core
          -- services
                -- api_service.dart
                -- local_database_service.dart
          -- provider
                -- auth_provider.dart
                -- user_provider.dart
//--Test Structure

        //  DO
     -- test
        -- unit_test
            -- lib
                -- src
                    -- core
                    -- services
                            -- api_service_test.dart
                            -- local_database_service_test.dart
                    -- provider
                            -- auth_provider_test.dart
                            -- user_provider_test.dart

        // Don`t 

        -- test_test
            -- unit
              -- api_service_test.dart
              -- local_database_service_test.dart
              -- auth_provider_test.dart
              -- user_provider_test.dart      
```

* All test files should have a `_test` prefix

``` dart script
//i.e
 auth_provider_test.dart                   

```

* `Mock` and `faker` files should be in the root folder of the being tested
``` dart script

        -- test_test
            -- unit
            -- mocks
               -- mocks.dart
           

```
* Group the test

``` dart script

    // Generate a MockClient using the Mockito package.
    // Create new instances of this class in each test.
    @GenerateMocks([http.Client])

    void main() {

    group('API SERVICE',(){


      group('fetchAlbum', () {

        test('returns an Album if the http call completes successfully', () async {
          final client = MockClient();
        
          when(client
                  .get(Uri.parse('https://jsonplaceholder.typicode.com/albums/1')))
              .thenAnswer((_) async =>
                  http.Response('{"userId": 1, "id": 2, "title": "mock"}', 200));

          expect(await fetchAlbum(client), isA<Album>());
        });

        test('throws an exception if the http call completes with an error', () {
          final client = MockClient();
        
          when(client
                  .get(Uri.parse('https://jsonplaceholder.typicode.com/albums/1')))
              .thenAnswer((_) async => http.Response('Not Found', 404));

          expect(fetchAlbum(client), throwsException);
        });
      });

      group('deleteAlbum',(){
          ...
      })

    })

  }

```



* Use `setUp` and `tearDown` for any initialization and gabage collection.

``` dart script

  !! Setup function initializes all dependencies need to run the test

  \\  setUpAll [Runs once in the lifecycle of the test]

  setUpAll(() {
    _mockInstance = MockFirestore();
    _firebaseClient = FirebaseClient(_mockInstance);
  });

// [Runs after  every test function ]
  setUp(() {
    _mockInstance = MockFirestore();
    _firebaseClient = FirebaseClient(_mockInstance);
  });


!! Tear down function acts as a garbage collector  

  \\  setUpAll [Runs once in the lifecycle of the test]

  tearDownAll(() {
    _mockInstance = MockFirestore();
    _firebaseClient = FirebaseClient(_mockInstance);
  });

// [Runs after  every test function ]
  tearDown(() {
    _mockInstance = MockFirestore();
    _firebaseClient = FirebaseClient(_mockInstance);
  });


```

* Follow arrange,act,assert pattern

  [+]  Arrange - Setup what the test needs

  [+]  Act - Call specific operations and functions that are being tested

  [+] Assert - Check our values if they meet the expected criteria

``` dart script


  test('should return data when the call to remote source is successful.', () async {
    // arrange

    //act
    
    //assert
    
  });



  /// i..e 



    testWidgets('Locate CircularProgressIndicator',
        (WidgetTester tester) async {

      // Arrange

      MapPage page = MapPage();

      // Act

      await tester.pumpWidget(page.wrapWithMaterial());

      await tester.idle();

      //Assert

      expect(find.byType(Scaffold), findsOneWidget);
    });
  });


```



