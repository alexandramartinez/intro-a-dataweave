
# Solución de ejercicio 6

Escribe una función que acepte dos argumentos:
1. La edad de la persona
2. La edad donde se considera mayor de edad a una persona

Dependiendo de los dos argumentos, se va a regresar uno de los siguientes 3 strings:
1. "Es mayor de edad" si el primer argumento es mayor que el segundo argumento
2. "Es mayor, muy apenas!" si el primer argumento es igual al segundo argumento
3. "Es menor de edad" si el primer argumento es menor al segundo argumento

## Solución

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