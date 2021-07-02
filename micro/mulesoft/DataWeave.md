# DataWeave

### DataWeave code to find sum, average, median and mode 
```javascript
%dw 2.0
output application/json
var arr = [0,0,1,2,3,4,5]
var len = sizeOf(arr)
fun median(arr :Array) = if(isOdd(len)) arr[len/2] else arr[len/2-1] as Number + arr[len/2] as Number
fun mode(arr :Array) = keysOf(arr orderBy $ groupBy $ mapObject {
    ($$): sizeOf($)
} orderBy -$)[0] as Number 
---
{
    //arr: arr,
    sum: sum(arr),
    average: (sum(arr)/len) as String {format: "0.##"},
    median: (median(arr)) as String {format: "0.##"},
    mode: mode(arr)
}
```

### Dataweave code to format number
```javascript
%dw 2.0
output application/json
type NumberFormat1 = String {format: "0000"}
type NumberFormat2 = String {format: "0.00"}
type NumberFormat3 = String {format: "0.##"}
type NumberFormat4 = String {format: "#,###.##"}
var num = 5393923/3
---
{
    num1: num as NumberFormat1,
    num2: num as NumberFormat2,
    num3: num as NumberFormat3,
    num4: num as NumberFormat4,
}
```

### Dataweave code to format date 
```javascript
%dw 2.0
output application/json
type DateFormat1 = String {format: "yyyy-MM-dd"}
type DateFormat2 = DateTime {format: "yyyy-MM-dd hh:mm:ss a"}
type DateFormat3 = Date {format: "dd-MM-yyyy"}
var date = now()
---
{
    date1: date as DateFormat1,
    date2: date as DateFormat2,
    date3: "01-01-2010" as DateFormat3
}
```
### Update operator
Update operator enables you to update specified fields of a data structure with new values.

```javascript
%dw 2.0
var emp = [{"id": 10, "name": "Ken", "age": 30},
{"id": 11, "name": "Joe", "age": 25}]
output application/json
---
emp map ((e) -> e update {
    case age at .age if(age >= 30) -> age + 1
    case name at .name -> upper(name)
})
```

### Array, Range and String reverse
```javascript
%dw 2.0
output application/json
var name = "Malayalam"
---
{
    arr: 0 to 5,
    substring: name[0 to 2],
    indicesToend: name[2 to -1],
    reverse: name[sizeOf(name)-1 to 0]
}
```

### DataWeave to call a java static and instance method
```javascript
%dw 2.0
output application/json
import java!java::lang::String
import java!java::util::Date
---
{
   String: String::valueOf(true),
   Date: Date::new().year
} 
```

### DataWeave function to traverse an object, array
```javascript
%dw 2.0
output application/json

fun traverse(object: Object) = object mapObject {
    ($$): traverse($)
}
fun traverse(array: Array) = array map traverse ($)
fun traverse(date: Date) = date
fun traverse(string: String) = string
fun traverse(number: Number) = number

var p = {
    "integer": 12,
    "string": "Hello World",
    "date": now(),
    "array": [
        {"int": 1, "string": "Hello", "date": now()}
    ]
}
---
traverse(p)
```
