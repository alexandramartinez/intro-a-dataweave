
# Intro a DataWeave: El lenguaje de programación de MuleSoft

Por [Alexandra Martinez](www.alexandramartinez.world)

Presentado en el evento "We Lead" de [Women Who Code Monterrey](https://www.meetup.com/Women-Who-Code-Monterrey).

## Contenidos

- [Conociendo el Playground](#conociendo-el-playground)
- [Formatos](#formatos)

## Conociendo el Playground

Simplemente hay que ir a [dwlang.fun](https://dwlang.fun/) para poder ver la página del DataWeave Playground.

Del lado izquierdo se encuentra el `input` para el script, en medio es donde se escribe el código (`script`), y en la derecha es donde se encuentra el `output` o el resultado de la transformación.

[Volver arriba](#intro-a-dataweave-el-lenguaje-de-programación-de-mulesoft)

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
[Volver arriba](#intro-a-dataweave-el-lenguaje-de-programación-de-mulesoft)
