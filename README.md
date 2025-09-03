# Cobol-port# Loan Management Project

## Descripción
Proyecto sencillo a modo de ejemplo de gestión de préstamos desarrollado en **COBOL**, con soporte para **batch**, **CICS** y **DB2 con SQL embebido**.  
Incluye creación, actualización, consulta y generación de informes de préstamos, usando ficheros secuenciales e indexados, y simulación de transacciones online.

Este proyecto está pensado para **entornos Mainframe** y puede probarse parcialmente en **GNUCobol** para la versión batch.

---

## Estructura del proyecto

```
/loan-management-project
├─ /cobol
│   ├─ loan_creation.cbl
│   ├─ loan_update.cbl
│   ├─ loan_query.cbl
│   └─ loan_report.cbl
├─ /jcl
│   ├─ loan_creation.jcl
│   ├─ loan_update.jcl
│   ├─ loan_query.jcl
│   └─ loan_report.jcl
├─ /cics
│   └─ cics_commands.txt
├─ /db2
│   └─ sql_embedded_modules.txt
├─ /test_data
│   ├─ loans.dat
│   ├─ loan.idx
│   ├─ loan_input.dat
│   ├─ update_data.dat
│   ├─ loan_query_input.dat
│   └─ loan_query_output.dat
├─ README.md
└─ LICENSE
```

---

## Descripción de los módulos COBOL

### Loan Creation
- Archivo: `loan_creation.cbl`
- Función: crea préstamos nuevos a partir de `loan_input.dat` y los almacena en `loans.dat` y `loan.idx`.

### Loan Update
- Archivo: `loan_update.cbl`
- Función: actualiza los préstamos existentes según los datos de `update_data.dat`.

### Loan Query
- Archivo: `loan_query.cbl`
- Función: busca préstamos por `loan_id` usando `loan_query_input.dat` y genera resultados en `loan_query_output.dat`.

### Loan Report
- Archivo: `loan_report.cbl`
- Función: genera un informe completo de los préstamos actuales.

---

## Estructura de ficheros de prueba

- **loans.dat / loan.idx**: fichero maestro con todos los préstamos  
- **loan_input.dat**: préstamos a crear  
- **update_data.dat**: datos para actualización  
- **loan_query_input.dat**: IDs de préstamos para búsqueda  
- **loan_query_output.dat**: resultados esperados de la búsqueda  

> Todos los ficheros son **de ancho fijo**, sin separadores, con los formatos definidos en cada módulo.

---

## Ejecución

### Batch (GNUCobol)
1. Compilar los módulos:
   ```bash
   cobc -x loan_creation.cbl -o loan_creation.exe
   cobc -x loan_update.cbl -o loan_update.exe
   cobc -x loan_query.cbl -o loan_query.exe
   cobc -x loan_report.cbl -o loan_report.exe
   ```
2. Ejecutar:
   ```bash
   ./loan_creation.exe
   ./loan_update.exe
   ./loan_query.exe
   ./loan_report.exe
   ```

### Mainframe / JCL
- Lanzar los JCL correspondientes (`loan_creation.jcl`, `loan_update.jcl`, etc.) para ejecutar los programas batch en un entorno Mainframe.

### CICS
- Declarar las transacciones en CICS usando `CEDA` y ejecutar cada programa online usando el comando `EXEC CICS`.

### DB2
- Los módulos con SQL embebido realizan consultas y actualizaciones sobre tablas simuladas con los ficheros de prueba.  

---

## Licencia
Este proyecto se distribuye bajo **MIT License**.folio
Ejemplos de proyectos COBOL, JCL, DB2 y Mainframe para portfolio técnico
