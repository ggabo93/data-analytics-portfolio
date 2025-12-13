# Dashboard de Cobranzas de Préstamos (Excel)

## Contexto
El proyecto parte de una planilla “base” completamente desordenada: sin formato de base de datos, con campos mezclados (préstamo/cuotas/pagos), sin relaciones y con poca consistencia para analizar (fechas/estados/montos).

## Objetivo
Transformar esa planilla en un sistema simple y usable para:
- Controlar **cobranzas** (qué se cobró vs qué se esperaba cobrar)
- Medir **mora** (cuánto y cuántas cuotas están vencidas)
- Priorizar acciones (ranking de **clientes con mayor mora**)
- Estimar **cobro esperado a 30 días**

## Qué hice
- **Limpieza y normalización** de datos (estandarización de fechas, montos y estados).
- Diseño de un **modelo relacional** (tipo “base de datos”) separando la información en dos tablas:
  - **PRESTAMO** (cabecera: 1 fila = 1 préstamo, datos principales)
  - **CUOTAS** (detalle: 1 fila = 1 cuota, vencimiento, estado y monto)
- Creación de una relación **PRESTAMO (1) → (N) CUOTAS** usando **ID_PRESTAMO** como clave, para poder:
  - filtrar por cliente/prestamista desde PRESTAMO
  - analizar ingresos/mora por fechas desde CUOTAS
- Creación de campos de control para análisis:
  - **INGRESO** (cobrado real según estado Total/Parcial/Impago)
  - **CUOTA_ATRASADA / SALDO_EN_MORA**
  - **COBRO_ESPERADO_30D** (proyección de cobro próximos 30 días)
- Construcción de **tablas dinámicas**, **segmentadores** y **gráficos dinámicos** conectados al modelo para armar el tablero.

## Dashboard (KPIs y visualizaciones)
Incluye indicadores y visualizaciones para monitoreo mensual/operativo:
- **Capital prestado**
- **Ingresos reales vs esperados**
- **Saldo en mora**
- **Cuotas en mora**
- **Cobro esperado a 30 días**
- **Top clientes con mora** (ranking)
- **Ganancia y benficio neto**
- 
## Resultado
Un archivo listo para uso diario, que permite tomar decisiones rápidas:
- cuánto entra por mes
- cuánto falta cobrar vs lo esperado
- cuánta mora se acumula y quiénes son los principales morosos

> **Nota:** El dataset publicado está **anonimizado/simulado** para preservar confidencialidad.

## Herramientas / Skills
- Excel
- Validación de datos
- Fórmulas
- Tablas dinámicas y segmentadores
- Gráficos dinámicos
- **Modelado relacional en Excel** (PRESTAMO 1:N CUOTAS, clave ID_PRESTAMO)

## Cómo usar
1. Abrir el archivo `dashboard_prestamos.xlsx`
2. Actualizar: **Datos → Actualizar todo**
3. Usar **segmentadores** para filtrar por cliente/mes/estado
4. Revisar **Saldo en mora**, **Cuotas en mora** y **Top morosos** para priorizar cobranzas
