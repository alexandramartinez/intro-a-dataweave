
# Scripts

Encuentra rápidamente los scripts que se vieron en el taller.

**NOTA:** Aquí también se encuentran las soluciones de los ejercicios. Si quieres hacer los ejercicios por tu cuenta (sin ver las soluciones) es mejor que vayas a la carpeta de [ejercicios](ejercicios/) o que sigas el archivo de [README.md](README.md).

## Links

[dwlang.fun](https://dwlang.fun/)
[codeshare.io](https://codeshare.io/)

## Formatos

### Script 1

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

### Script 2

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
**Script**
```dataweave
%dw 2.0
output application/csv
---
payload
```
**Output**
```
nombre,apellido
Alex,Mtz
Grecia,Castaldi
Nia,Cortes
```

