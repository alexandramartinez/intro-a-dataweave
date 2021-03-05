
# Ejercicio 5

Escribe una función que acepte dos argumentos de tipo String y que regrese un tipo String. La función va a concatenar los dos argumentos usando la función plus plus (`++`).

Aquí hay un ejemplo de cómo se usa esta función (plus plus) para concatenar dos strings:

**Script**
```dataweave
%dw 2.0
output application/json
---
"Hello " ++ "World"
```
**Output**
```json
"Hello World"
```