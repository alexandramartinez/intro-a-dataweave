
# Ejercicio 3

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
