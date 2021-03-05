
# Scripts

Encuentra rápidamente los scripts que se vieron en el taller.

**NOTA:** Aquí también se encuentran las soluciones de los ejercicios. Si quieres hacer los ejercicios por tu cuenta (sin ver las soluciones) es mejor que vayas a la carpeta de [ejercicios](ejercicios/) o que sigas el archivo de [README.md](README.md).

## Links

* [dwlang.fun](https://dwlang.fun/)
* [codeshare.io](https://codeshare.io/)

## Formatos

### Script 1

**Input**
```xml
<?xml version='1.0' encoding='UTF-8'?>
<message>Hello world!</message>
```
**Script**
```dataweave
%dw 2.0
output application/json
---
payload
```
**Output**
```json
{
  "message": "Hello world!"
}
```

### Script 2

**Input**
```json
[
    {
        "nombre": "Alex",
        "apellido": "Mtz"
    },
    {
        "nombre": "Grecia",
        "apellido": "Castaldi"
    },
    {
        "nombre": "Nia",
        "apellido": "Cortes"
    }
]
```
**Script**
```dataweave
%dw 2.0
output application/csv
---
payload
```
**Output**
```
nombre,apellido
Alex,Mtz
Grecia,Castaldi
Nia,Cortes
```

## Tipos de datos

### Script 1

**Script**
```dataweave
%dw 2.0
output application/json
---
//"Hello world" // Strings - "hello world", "", "abc"
//5 // Numbers - 1, 2.5, -868
//true // Booleans - true, false
//[1, "a", false] // Arrays - [1, 2, 3], ["a","b","c"], [{},1,true,"a"]
{campo: "valor"} // Objects - {}, {"field":"value"}
```
**Output**
```json
{
  "campo": "valor"
}
```

### Script 2

**Script**
```dataweave
%dw 2.0
output application/json
---
{
    uno: typeOf(10),
    dos: typeOf(20.2849484848),
    tres: typeOf(["a","b",{}]),
    cuatro: typeOf({}),
    cinco: typeOf(not true)
}
```
**Output**
```json
{
  "uno": "Number",
  "dos": "Number",
  "tres": "Array",
  "cuatro": "Object",
  "cinco": "Boolean"
}
```

## Operadores

### Script 1

**Script**
```dataweave
%dw 2.0
output application/json
---
{
    matematicos: {
        suma: 1 + 1,
        resta: 5 - 10,
        mult: 3 * 50,
        div: 100 / 3
    }
}
```
**Output**
```json
{
  "matematicos": {
    "suma": 2,
    "resta": -5,
    "mult": 150,
    "div": 33.33333333333333333333333333333333
  }
}
```

### Script 2

**Script**
```dataweave
%dw 2.0
output application/json
---
{
    igualdad: {
        menor: 3 < 5,
        mayor: 3 > 5,
        menorOIgual: 45 <= 10,
        mayorOIgual: 45 >= 10,
        igual: "true" == true,
        igualCoerc: "true" ~= true
    }
}
```
**Output**
```json
{
  "igualdad": {
    "menor": true,
    "mayor": false,
    "menorOIgual": false,
    "mayorOIgual": true,
    "igual": false,
    "igualCoerc": true
  }
}
```

### Script 3

**Script**
```dataweave
%dw 2.0
output application/json
---
{
    logicos: {
        not1: not true,
        not2: ! true,
        "and": true and false,
        "or": true or false
    }
}
```
**Output**
```json
{
  "logicos": {
    "not1": false,
    "not2": false,
    "and": false,
    "or": true
  }
}
```

### Script 4

**Script**
```dataweave
%dw 2.0
output application/json
---
{
    array: {
        anteponer: 1 >> [2],
        adjuntar1: ["a", "b"] << "c",
        adjuntar2: [1, 2] + "c",
        remover: [1, 2, 3] - 2
    }
}
```
**Output**
```json
{
  "array": {
    "anteponer": [
      1,
      2
    ],
    "adjuntar1": [
      "a",
      "b",
      "c"
    ],
    "adjuntar2": [
      1,
      2,
      "c"
    ],
    "remover": [
      1,
      3
    ]
  }
}
```

### Script 5

**Script**
```dataweave
%dw 2.0
output application/json
---
{
    nots: {
        not1: not true or true,
        not2: ! true or true
    }
}
```
**Output**
```json
{
  "nots": {
    "not1": false,
    "not2": true
  }
}
```

## Variables

### Script 1

**Script**
```dataweave
%dw 2.0
output application/json

var myStr = "Hello World"
---
myStr
```
**Output**
```json
"Hello World"
```

### Script 2

**Script**
```dataweave
%dw 2.0
output application/json

var myStr = "Hello World"
var mayus = (str) -> upper(str)
---
mayus(myStr)
```
**Output**
```json
"HELLO WORLD"
```

### Script 3

**Script**
```dataweave
%dw 2.0
output application/json

var myStr: String = "Hello World"
var mayus = (str: String) -> upper(str)
---
mayus(myStr)
```
**Output**
```json
"HELLO WORLD"
```

### Script 4

**Script**
```dataweave
%dw 2.0
output application/json

var myStr: String = 1
var mayus = (str: String) -> upper(str)
---
mayus(myStr)
```
**Output**
```
Expecting Type: `String`, but got: `1`.

4| var myStr: String = 1
                       ^
Location:
main (line: 4, column:21)
```

## Funciones

### Script 1

**Script**
```dataweave
%dw 2.0
output application/json

fun mayus(str) = upper(str)
---
mayus("Hello World")
```
**Output**
```json
"HELLO WORLD"
```

### Script 2

**Script**
```dataweave
%dw 2.0
output application/json

fun mayus(str: String) = upper(str)
---
mayus("Hello World")
```
**Output**
```json
"HELLO WORLD"
```

### Script 3

**Script**
```dataweave
%dw 2.0
output application/json

fun mayus(str: String): String = upper(str)
---
mayus("Hello World")
```
**Output**
```json
"HELLO WORLD"
```

### Script 4

**Script**
```dataweave
%dw 2.0
output application/json

fun concat(str1: String, str2: String): String = str1 ++ str2
---
concat("Hello"," World")
```
**Output**
```json
"Hello World"
```

## Condiciones

### Script 1

**Script**
```dataweave
%dw 2.0
output application/json

fun concat(str1, str2) = 
    if (str1 is String and str2 is String) str1 ++ str2
    else null
---
concat("Hello"," World")
```
**Output**
```json
"Hello World"
```

### Script 2

**Script**
```dataweave
%dw 2.0
output application/json

fun getCodigo(pais) = 
    if (pais == "Mexico") "MX"
    else if (pais == "Estados Unidos") "EUA"
    else if (pais == "Canada") "CA"
    else "Otro pais"
---
getCodigo("Mexico")
```
**Output**
```json
"MX"
```

### Script 3

**Script**
```dataweave
%dw 2.0
output application/json

fun esMayor(edadPersona, edadMAyor) = 
    if (edadPersona > edadMAyor) "Es mayor de edad"
    else if (edadPersona == edadMAyor) "Es mayor, muy apenas!"
    else "Es menor de edad"
---
esMayor(19,18)
```
**Output**
```json
"Es mayor de edad"
```
