#### Dart

**Syntax**

```dart
contextData["&&products"] = "Category;Product;Quantity;Price[,Category;Product;Quantity;Price]";
```

**Example**

```dart
//create a context data dictionary
var contextData = {};

// add products, a purchase id, a purchase context data key, and any other data you want to collect.
// Note the special syntax for products
contextData["&&products"] = ";Running Shoes;1;69.95,;Running Socks;10;29.99";
contextData["m.purchaseid"] = "1234567890";
contextData["m.purchase"] = "1";

// send the tracking call - use either a trackAction or TrackState call.
// trackAction example:
FlutterACPCore.trackAction("purchase", data: contextData);
// trackState example:
FlutterACPCore.trackState("Order Confirmation", data: contextData);
```