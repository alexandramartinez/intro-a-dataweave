
# Solución de ejercicio 2

Usando la función `typeOf()`, confirma los tipos de datos de diferentes valores. Ejemplo:

**Script**
```dataweave
%dw 2.0
output application/json
---
typeOf("Hello World!")
```

¿Qué tipos de datos son los siguientes valores?

1. `10`
2. `20.2849484848`
3. `["a","b",{}]`
4. `{null}`
5. `not true`

## Solución

1. `10` - Number
2. `20.2849484848` - Number
3. `["a","b",{}]` - Array
4. `{}` - Object
5. `not true` - Boolean