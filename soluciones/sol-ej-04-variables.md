
# Solución de ejercicio 4

Define diferentes variables para los tipos de dato `String`, `Number`, `Boolean`, `Array` y `Object`. 

Después, intenta asignar un valor diferente al tipo de dato que se le asignó a la variable y observa el error.

**Script 1**
```dataweave
%dw 2.0
output application/json

var str: String = "hello"
var num: Number = 1
var bool: Boolean = true
var arr: Array = [1, 2, 3, "123"]
var obj: Object = {
    a: "b",
    c: "d"
}
---
obj
```
**Output 1**
```
{
  "a": "b",
  "c": "d"
}
```

**Script 2**
```dataweave
%dw 2.0
output application/json

var str: String = 1434234
var num: Number = 1
var bool: Boolean = true
var arr: Array = [1, 2, 3, "123"]
var obj: Object = {
    a: "b",
    c: "d"
}
---
obj
```
**Output 2**
```
Expecting Type: `String`, but got: `1434234`.

4| var str: String = 1434234
                     ^^^^^^^
Location:
main (line: 4, column:19)
```