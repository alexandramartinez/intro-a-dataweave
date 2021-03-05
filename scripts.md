
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
```
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
```
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
```
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
```
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
```
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
```
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
```
{
  "nots": {
    "not1": false,
    "not2": true
  }
}
```