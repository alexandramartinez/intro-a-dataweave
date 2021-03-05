
# Intro a DataWeave: El lenguaje de programación de MuleSoft

Por [Alexandra Martinez](www.alexandramartinez.world)

Presentado en el evento "We Lead" de [Women Who Code Monterrey](https://www.meetup.com/Women-Who-Code-Monterrey).


## Contenidos

- [Conociendo el Playground](#conociendo-el-playground)
- [Formatos](#formatos)
- [Tipos de datos](#tipos-de-datos)
- [Operadores](#operadores)


## Conociendo el Playground

Simplemente hay que ir a [dwlang.fun](https://dwlang.fun/) para poder ver la página del DataWeave Playground.

Del lado izquierdo se encuentra el `input` para el script, en medio es donde se escribe el código (`script`), y en la derecha es donde se encuentra el `output` o el resultado de la transformación.

[Ver documentación oficial de MuleSoft sobre los principios de la programación funcional](https://docs.mulesoft.com/mule-runtime/4.3/dataweave-language-guide#functional-programming-principles)

[Ver documentación oficial de MuleSoft sobre la estructura de los scripts de DataWeave](https://docs.mulesoft.com/mule-runtime/4.3/dataweave-language-introduction)

:arrow_up_small: [Volver arriba](#intro-a-dataweave-el-lenguaje-de-programación-de-mulesoft)


## Formatos

El uso más básico de DataWeave es para transformar datos de un formato a otro. Por ejemplo de `XML` a `JSON`.

[Ver documentación oficial de MuleSoft sobre formatos](https://docs.mulesoft.com/mule-runtime/4.3/dataweave-formats)

Para hacer esto, solo se tiene que cambiar el tipo de `output`. Ejemplo:

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

### Ejercicio

[Ver ejercicio de formatos](ejercicios/ej-01-formatos.md).

:arrow_up_small: [Volver arriba](#intro-a-dataweave-el-lenguaje-de-programación-de-mulesoft)


## Tipos de datos

Así como en otros lenguajes de programación existe el String, Integer, Float, Char, Tuple, etc. En DataWeave existen 5 tipos principales de datos:
* Strings (`"hello world"`)
* Numbers (`1`, `2.5`, `-868`)
* Booleans (`true`, `false`)
* Arrays (`[1, 2, 3]`, `["a","b","c"]`, `[{},1,true,"a"]`)
* Objects (`{}`, `{"field":"value"}`)

[Ver documentación oficial de MuleSoft sobre tipos de datos](https://docs.mulesoft.com/mule-runtime/4.3/dataweave-types)

### Ejercicio

[Ver ejercicio de tipos de datos](ejercicios/ej-02-tipos-datos.md).

:arrow_up_small: [Volver arriba](#intro-a-dataweave-el-lenguaje-de-programación-de-mulesoft)


## Operadores 

Se pueden hacer diferentes operaciones con los datos, dependiendo de su tipo. 

[Ver documentación oficial de MuleSoft sobre operadores](https://docs.mulesoft.com/mule-runtime/4.3/dw-operators)

**Operadores matemáticos**
* `+` - suma
* `-` - resta
* `*` - multiplicación
* `/` - división

**Operadores de igualdad y relacionales**
* `<` - menor que
* `>` - mayor que
* `<=` - menor o igual que
* `>=` - mayor o igual que
* `==` - igual a
* `~=` - igual a (convirtiendo diferentes tipos de datos en uno mismo)

**Operadores lógicos**
* `not` - negación de todas las condiciones en conjunto
* `!` - negación de solo la primera condición
* `and` - regresa `true` si todas las condiciones se cumplen
* `or` - regresa `true` si al menos una condición se cumple

**Operadores para Array**
* `>>` - anteponer
* `<<` - adjuntar
* `+` - adjuntar
* `-` - remover 

### Ejercicio

[Ver ejercicio de operadores](ejercicios/ej-03-operadores.md).

:arrow_up_small: [Volver arriba](#intro-a-dataweave-el-lenguaje-de-programación-de-mulesoft)


## Variables

Cuando se crean variables en DataWeave, no se tiene que seleccionar un tipo de dato ni se tiene que inicializar, como en otros lenguajes. 

Como DataWeave es un lenguaje de programación funcional, las variables también son funciones.

[Ver documentación oficial de MuleSoft sobre variables](https://docs.mulesoft.com/mule-runtime/4.3/dataweave-variables)

**Script 1**
```dataweave
%dw 2.0
output application/json

var myStr = "Hello World"
---
myStr
```
**Output 1**
```json
"Hello World"
```

**Script 2**
```dataweave
%dw 2.0
output application/json

var myStr = "Hello World"
var mayus = (str) -> upper(str)
---
mayus(myStr)
```
**Output 2**
```json
"HELLO WORLD"
```

Para asignar tipos de datos a las variables, se escriben dos puntos (`:`) después del nombre de la variable, seguido por el tipo de dato que se le quiere asignar.

**Script**
```dataweave
var myStr: String = "Hello World"
var mayus = (str: String) -> upper(str)
---
mayus(myStr)
```
**Output**
```json
"HELLO WORLD"
```

### Ejercicio

[Ver ejercicio de variables](ejercicios/ej-04-variables.md).

:arrow_up_small: [Volver arriba](#intro-a-dataweave-el-lenguaje-de-programación-de-mulesoft)


## Funciones

## Condiciones

## Map