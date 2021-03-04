
# Solución de ejercicio 1

Transforma el siguiente input de formato `JSON` a un formato `CSV`.

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
**Output**
```
nombre,apellido
Alex,Mtz
Grecia,Castaldi
Nia,Cortes
```
**Script**
```dataweave
%dw 2.0
output application/csv
---
payload
```