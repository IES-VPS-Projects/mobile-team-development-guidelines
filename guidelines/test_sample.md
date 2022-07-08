## Data


``` dart script


// get_tasks_response.json
[
  {
    "userId": 1,
    "id": 1,
    "title": "delectus aut autem",
    "completed": false
  },
  {
    "userId": 1,
    "id": 2,
    "title": "quis ut nam facilis et officia qui",
    "completed": false
  },
  {
    "userId": 1,
    "id": 3,
    "title": "fugiat veniam minus",
    "completed": false
  }
]

```



# Api Client

``` dart script

class TodoApiClient {
  final String _baseAddress;
TodoApiClient(this._baseAddress);
...
 
  Future<http.Response> _get(String endpoint) async {
    try {
      final response = await http.get(
        '$_baseAddress$endpoint',
        headers: {
          HttpHeaders.acceptHeader: 'application/json',
        },
      );
return returnResponseOrThrowException(response);
    } on IOException catch (e) {
      print(e.toString());
      throw NetworkException();
    }
  }
Future<http.Response> _post(Task task) async {
    try {
      final response = await http.post(
        '$_baseAddress/todos',
        body: json.encode(task.toJson()) ,
        headers: {
          HttpHeaders.acceptHeader: 'application/json',
          HttpHeaders.contentTypeHeader: 'application/json',
        },
      );
return returnResponseOrThrowException(response);
    } on IOException {
      throw NetworkException();
    }
  }
Future<http.Response> _put(Task task) async {
    try {
      final response = await http.put(
        '$_baseAddress/todos/${task.id}',
        body: json.encode(task.toJson()) ,
        headers: {
          HttpHeaders.acceptHeader: 'application/json',
          HttpHeaders.contentTypeHeader: 'application/json',
        },
      );
return returnResponseOrThrowException(response);
    } on IOException  {
      throw NetworkException();
    }
  }
Future<http.Response> _delete(String id) async {
    try {
      final response = await http.delete(
        '$_baseAddress/todos/$id',
        headers: {
          HttpHeaders.acceptHeader: 'application/json',
        },
      );
return returnResponseOrThrowException(response);
    } on IOException  {
      throw NetworkException();
    }
  }
  

    
  Future<List<Task>> getAllTasks() async {
    final response = await _get('/todos');
final decodedTasks = json.decode(response.body) as List;
return decodedTasks.map((jsonTask) => Task.fromJson(jsonTask)).toList();
  }
Future<Task> getTasksById(String id) async {
    final response = await _get('/todos/$id');
return Task.fromJson(json.decode(response.body));
  }
Future<Task> addTask(Task task) async {
    final response = await _post(task);
return Task.fromJson(json.decode(response.body));
  }
Future<Task> updateTask(Task task) async {
    final response = await _put(task);
return Task.fromJson(json.decode(response.body));
  }
Future<void> deleteTaskById(String id) async {
    await _delete(id);
  }
  
    ...
}



```


# Mock Api Client

``` dart script

    class MockApi {
    MockWebServer _server;
    Future<void> start() async {
        _server = MockWebServer();
        await _server.start();
    }
    void shutdown() {
        _server.shutdown();
    }
    String get baseAddress => _server.url.substring(0, _server.url.length - 1);
    Future<void> enqueueMockResponse(
        {String fileName = '',
        int httpCode = 200,
        Map<String, String> headers}) async {
        final content = await _getContentFromFile(fileName: fileName);
    _server.enqueue(body: content, httpCode: httpCode, headers: headers);
    }
    void expectRequestSentTo(String endpoint) {
        final StoredRequest storedRequest = _server.takeRequest();
    expect(storedRequest.uri.path, endpoint);
    }
    void expectRequestContainsHeader([String key, String expectedValue, int requestIndex = 0]) {
        final StoredRequest storedRequest = _getRecordedRequestAtIndex(requestIndex);
        final value = storedRequest.headers[key];
    expect(value, contains(expectedValue));
    }
    Future<void> expectRequestContainsBody(String fileName) async {
        final expectedBody = await _getContentFromFile(fileName: fileName);
        final StoredRequest storedRequest = _getRecordedRequestAtIndex(0);
    expect(storedRequest.body, expectedBody);
    }
    ...
    }

```

# Test

``` dart script
    TodoApiClient _todoApiClient;
    MockApi mockApi = MockApi();
    String anyTaskId = '1';
    Task anyTask =
        Task(id: 1, userId: 1, title: 'Finish this kata', completed: false);
    void main() {
    setUp(() async {
        await mockApi.start();
    _todoApiClient = TodoApiClient(mockApi.baseAddress);
    });
    tearDown(() {
        mockApi.shutdown();
    });
    group('TodoApiClient', () {
    group('GetAllTasks should', () {
    test('sends get request to the correct endpoint', () async {
            await mockApi.enqueueMockResponse(fileName: getTasksResponse);
    await _todoApiClient.getAllTasks();
    mockApi.expectRequestSentTo('/todos');
        });
    test('sends accept header', () async {
            await mockApi.enqueueMockResponse(fileName: getTasksResponse);
    await _todoApiClient.getAllTasks();
    mockApi.expectRequestContainsHeader('accept', 'application/json');
        });
    test('parse current news properly getting all current news', () async {
            await mockApi.enqueueMockResponse(fileName: getTasksResponse);
    final tasks = await _todoApiClient.getAllTasks();
    expectTasksContainsExpectedValues(tasks[0]);
        });
    test(
            'throws UnknownErrorException if there is not handled error getting news',
            () async {
            await mockApi.enqueueMockResponse(httpCode: 454);
    expect(() => _todoApiClient.getAllTasks(),
                throwsA(isInstanceOf<UnKnowApiException>()));
        });
        });
        
        ...
        
    });
    }
    void expectTasksContainsExpectedValues(Task task) {
    expect(task, isNotNull);
    expect(task.userId, 1);
    expect(task.id, 1);
    expect(task.title, 'delectus aut autem');
    expect(task.completed, false);
    }

```