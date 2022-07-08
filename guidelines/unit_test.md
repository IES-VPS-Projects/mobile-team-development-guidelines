# Unit Test

* Unit test also follows all test guidelines pointed out in   <a href="guidelines/testing.md"> Testing </a>file.

* When mocking services and external libraries such as firebase, make use of ; 

    * [fake_cloud_firestore](https://pub.dev/packages/fake_cloud_firestore) - for mocking cloud firestore.

    * [Mockito](https://pub.dev/packages/mockito) - for mocking other services i.e dio,http ...

 * All stubs are places under `arrange` from our setup pattern `(Arrange, Act, Assert)`

``` dart script
// i.e 

    test('should return data when the call to a remote source is successful.', () async {
        
    // arrange

        when(instance.collection('users').doc(senderID).get()).thenAnswer((_) => null);

    //act
    
    //assert
    
    });

```

* Bever import any UI-related packages into your unit test suite (we are testing only the apps logic).

* Sample

```dart script

        //  MOCK

    class MockAPI extends API {
    @override
    Future<List<Product>> getProducts() {
    return Future.value([
        Product(id: 1, name: "MacBook Pro 16-inch model", price: 2399, 
            imageUrl: "imageUrl"),
        Product(id: 2, name: "AirPods Pro", price: 249, imageUrl: "imageUrl"),
        ]);
    }
 }


```

```dart script

            //Test


    group('Given Product List Page Loads', () {
    test('Page should load a list of products from firebase', () async {
        // 1
        await productListViewModel.getProducts();
        // 2
        expect(productListViewModel.products.length, 2);
        // 3
        expect(productListViewModel.products[0].name, 'MacBook Pro 16-inch model');
        expect(productListViewModel.products[0].price, 2399);
        expect(productListViewModel.products[1].name, 'AirPods Pro');
        expect(productListViewModel.products[1].price, 249);
    });
 });

```
