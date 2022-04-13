# Purpose

Demonstrates how the OpenAPI tools Dart SDK generator will incorrectly shadow field variables named `json` in the generated `toJson()` method.

# Scope
Tested using [openapi-generator-cli-6.0.0-20220412.074015-127.jar 	(Tue Apr 12 07:40:21 UTC 2022)](https://oss.sonatype.org/content/repositories/snapshots/org/openapitools/openapi-generator-cli/6.0.0-SNAPSHOT/openapi-generator-cli-6.0.0-20220412.074015-127.jar)


# Reproduction steps
1. clone the repo
2. cd into it
3. Run the generator jar with the shadowspec.yaml as input and dart as the language
    * `java -jar openapi-generator-cli-6.0.0-20220412.074015-127.jar generate -i .\shadowspec.yaml -g dart -o shadowed`
4. Open `./shadowed/lib/model/item_with_field_named_json.dart` and find the `toJson()` method

# Input
>shadowspec.yaml

```yaml
components:
  schemas:
    ItemWithFieldNamedJson:
      type: object
      properties:
        json:
          type: object
          additionalProperties: {}
```

# Output
>shadowed/lib/model/item_with_field_named_json.dart

Some fields from the generated file below have been omitted for brevity
```dart
class ItemWithFieldNamedJson {
  ItemWithFieldNamedJson({
    this.json = const {},
  });

  Map<String, Object> json;

  Map<String, dynamic> toJson() {
    final json = <String, dynamic>{};
      json[r'json'] = json;
    return json;
  }

```

# Bug
`final json = <String, dynamic>` is a shadowed variable over the field variable `Map<String, Object> json` causing serialization to end up in an cyclic pointer reference.