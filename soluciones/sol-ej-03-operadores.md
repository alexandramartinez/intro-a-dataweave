
# Solución de ejercicio 3

¿Cuál es el resultado de los siguientes scripts?

**Script 1**
```dataweave
%dw 2.0
output application/json
---
not true or true
```

**Script 2**
```dataweave
%dw 2.0
output application/json
---
! true or true
```

**Script 3**
```dataweave
%dw 2.0
output application/json
---
not true and true and true and false
```

**Script 4**
```dataweave
%dw 2.0
output application/json
---
! true and true and true and false
```

## Solución

**Script 1**
```dataweave
%dw 2.0
output application/json
---
not true or true
```
Resultado = false

Ejecución: not (true or true) = not (true) = false

**Script 2**
```dataweave
%dw 2.0
output application/json
---
! true or true
```
Resultado = true

Ejecución: (!true) or true = false or true = true

**Script 3**
```dataweave
%dw 2.0
output application/json
---
not true and true and true and false
```
Resultado = true

Ejecución: not (true and true and true and false) = not (false) = true

**Script 4**
```dataweave
%dw 2.0
output application/json
---
! true and true and true and false
```
Resultado = false

Ejecución: (!true) and true and true and false = false and true and true and false = false