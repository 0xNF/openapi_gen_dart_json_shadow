# openapi.api.DefaultApi

## Load the API package
```dart
import 'package:openapi/api.dart';
```

All URIs are relative to *http://localhost*

Method | HTTP request | Description
------------- | ------------- | -------------
[**shadow**](DefaultApi.md#shadow) | **GET** / | 


# **shadow**
> ItemWithFieldNamedJson shadow()



### Example
```dart
import 'package:openapi/api.dart';

final api_instance = DefaultApi();

try {
    final result = api_instance.shadow();
    print(result);
} catch (e) {
    print('Exception when calling DefaultApi->shadow: $e\n');
}
```

### Parameters
This endpoint does not need any parameter.

### Return type

[**ItemWithFieldNamedJson**](ItemWithFieldNamedJson.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

