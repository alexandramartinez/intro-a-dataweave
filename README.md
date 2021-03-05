
# Intro a DataWeave: El lenguaje de programación de MuleSoft

Por [Alexandra Martinez](www.alexandramartinez.world)

Presentado en el evento "We Lead" de [Women Who Code Monterrey](https://www.meetup.com/Women-Who-Code-Monterrey).


## Contenidos

- [Conociendo el Playground](#conociendo-el-playground)
- [Formatos](#formatos)
- [Tipos de datos](#tipos-de-datos)
- [Operadores](#operadores)
- [Variables](#variables)
- [Funciones](#funciones)
- [Condiciones](#condiciones)


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

Así como en otros lenguajes de programación existe el String, Integer, Float, Char, Tuple, etc. En DataWeave existen varios tipos de datos, pero nos vamos a enfocar en estos 5:
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

Cuando se crean variables en DataWeave, no se tiene que seleccionar un tipo de dato ni se tiene que inicializar, como en otros lenguajes. Para crear una nueva variable, se tiene que usar la palabra clave `var`, seguido del nombre de la variable y la asignación (usando el signo de igual `=`). Nota que la declaración se tiene que hacer sobre los tres guiones (`---`) del script.

[Ver documentación oficial de MuleSoft sobre variables](https://docs.mulesoft.com/mule-runtime/4.3/dataweave-variables)

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

Como DataWeave es un lenguaje de programación funcional, las variables se pueden usar como funciones.

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

Al crear funciones en DataWeave, no se tiene que especificar el tipo de dato de los argumentos, o el tipo de dato que va a regresar la función. 

Para crear una nueva función, se usa la palabra clave `fun`, seguido del nombre de la función. Después, entre paréntesis, se escriben los nombres de los argumentos separados por coma (`,`). Finalmente, se asigna el código a la función con el signo de igual (`=`). Nota que la declaración se tiene que hacer sobre los tres guiones (`---`) del script.

No es necesario poner el código de la función entre paréntesis (`()`) o llaves (`{}`). DataWeave puede reconocer que el código siguiente le pertenece a la función.

[Ver documentación oficial de MuleSoft sobre funciones](https://docs.mulesoft.com/mule-runtime/4.3/dataweave-functions)

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

Para evitar errores, puedes asignar tipos de datos a los argumentos de las funciones. Al igual que con las variables, se escriben dos puntos (`:`) después del nombre del argumento, seguido por el tipo de dato que se le quiere asignar.

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

También se le pueden asignar tipos de datos a las funciones (es decir, lo que van a regresar). Esta vez se escriben los dos puntos y el tipo de dato después de los paréntesis donde están los argumentos, o bien, antes del signo de igual.

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

El mayor beneficio de asignar tipos de datos a las funciones es para poder usar Function Overloading (o sobrecarga de funciones). No se tocará ese tema en este taller, pero puedes leer al respecto [aquí](https://docs.mulesoft.com/mule-runtime/4.3/dataweave-functions#overloading-functions).

### Ejercicio

[Ver ejercicio de funciones](ejercicios/ej-05-funciones.md).

:arrow_up_small: [Volver arriba](#intro-a-dataweave-el-lenguaje-de-programación-de-mulesoft)


## Condiciones

Al igual que en otros lenguajes de programación, existen formas de controlar el "flujo" o la lógica del código usando condiciones. En DataWeave se utiliza `if`/`else`.

Para crear condiciones, se usa primero la palabra clave `if`, seguida de la condición entre paréntesis (`()`). Después de esto no es necesario abrir paréntesis (`()`) o llaves (`{}`), ya que DataWeave puede reconocer que el código siguiente pertenece al `if`. 

A diferencia de otros lenguajes, aquí sí se tiene que agregar un `else` después de un `if`, para asegurarnos de que ambas rutas van a estar cubiertas en el código y siempre se va a asignar un valor sin importar si la condición se cumple o no. Después de crear el código del `if`, se agrega la palabra clave `else` y tampoco es necesario abrir paréntesis o llaves; con escribir código después de esto, DataWeave reconoce que pertenece al `else`.

[Ver documentación oficial de MuleSoft sobre control de flujo (condiciones)](https://docs.mulesoft.com/mule-runtime/4.3/dataweave-flow-control)

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

Se puede agregar más de una condición usando las palabras `else if` antes del último `else`. En realidad lo que se hace es que se crea otro `if` dentro del `else`, anidando así varias declaraciones de `if/else` para contemplar diferentes condiciones.

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

### Ejercicio

[Ver ejercicio de condiciones](ejercicios/ej-06-condiciones.md).

:arrow_up_small: [Volver arriba](#intro-a-dataweave-el-lenguaje-de-programación-de-mulesoft)

