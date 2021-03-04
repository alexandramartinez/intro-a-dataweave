
# Intro a DataWeave: El lenguaje de programación de MuleSoft

Por [Alexandra Martinez](www.alexandramartinez.world)

Presentado en el evento "We Lead" de [Women Who Code Monterrey](https://www.meetup.com/Women-Who-Code-Monterrey).

## Contenidos

- [Conociendo el Playground](#conociendo-el-playground)
- [Formatos](#formatos)

## Conociendo el Playground

Simplemente hay que ir a [dwlang.fun](https://dwlang.fun/) para poder ver la página del DataWeave Playground.

Del lado izquierdo se encuentra el `input` para el script, en medio es donde se escribe el código (`script`), y en la derecha es donde se encuentra el `output` o el resultado de la transformación.

:arrow_up_small: [Volver arriba](#intro-a-dataweave-el-lenguaje-de-programación-de-mulesoft)

## Formatos

El uso más básico de DataWeave es para transformar datos de un formato a otro. Por ejemplo de `XML` a `JSON`.

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

### Ejercicio

[Ver ejercicio de tipos de datos](ejercicios/ej-02-tipos-datos.md).

:arrow_up_small: [Volver arriba](#intro-a-dataweave-el-lenguaje-de-programación-de-mulesoft)

## Operadores 

Se pueden hacer diferentes operaciones con los datos, dependiendo de su tipo. Por ejemplo, sí se pueden concatenar dos strings, pero no se puede concatenar un string y un array.

Puedes hacer esto para concatenar strings:
```dataweave
%dw 2.0
output application/json
---
"hello" ++ " world"
```

Pero si intentas concatenar un string y un array, DataWeave te regresa un error:
```dataweave
%dw 2.0
output application/json
---
"abc" ++ []
```

**Operadores matemáticos**
* `+` - suma
* `-` - resta
* `*` - multiplicacion
* `/` - division

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

### Ejercicio

[Ver ejercicio de operadores](ejercicios/ej-03-operadores.md).

:arrow_up_small: [Volver arriba](#intro-a-dataweave-el-lenguaje-de-programación-de-mulesoft)
