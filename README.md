Middleware on Future for Dart

## Features 
- Working with async/await
- Zero dependencies

## Usage

```dart
import 'package:middleware/middleware.dart';

class Context {
  DateTime now;
}

final composedMiddleware = compose<Context>([
  (context, next) async {
    // Step 1

    await next();

    // Step 4

    // Print the current date from the next middleware
    print(context.now);
  },
  (context, next) async {
    // Step 2

    context.now = DateTime.now();

    await next();

    // Step 3
  }
]);
void main() async {
  var context = Context();

  composedMiddleware(
    context,
    () async {/* Last handler (next) */},
  ).then((what) {
    print('Middleware finished work');
  }).catchError(print);
}
```

## Features and bugs

Please file feature requests and bugs at the [issue tracker][tracker].

[tracker]: http://example.com/issues/replaceme
