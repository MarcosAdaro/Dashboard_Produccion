# Programacion_Produccion
Archivo online que facilita la programacion en los sectores productivos
📘 Planificación de Producción – Automatización en Google Sheets

Este repositorio documenta el sistema que desarrollé para automatizar y simplificar la programación de producción en el sector. El proceso utiliza Google Sheets compartido con el encargado de planta, integrando datos de stock, pendientes y ventas para calcular automáticamente las necesidades reales de producción.

📁 Estructura del archivo
Planificacion_Produccion/
  data/
    pendientes.csv
    promedios_venta.csv
  sheets/
    planificacion_produccion.xlsx
    flujo_planificacion.md
  workflow/
    01_registro_operarios.md
    02_carga_datos.md
    03_actualizacion_pendientes.md
    04_actualizacion_promedios.md
    05_calculo_disponible.md
    06_calculo_para_producir.md
  README.md




📌 Descripción del sistema

El sheet cuenta con las siguientes columnas principales:

Columna	Descripción
CODIGO	Código alfanumérico del artículo.
STOCK DEPÓSITO A	Stock actualizado del depósito principal.
STOCK DEPÓSITO B	Stock del segundo depósito.
PENDIENTES	Traído por BUSCARX desde la solapa PENDIENTES.
DISPONIBLE	Cálculo automático: A + B – Pendientes.
PROMEDIO DE VENTAS	BUSCARX desde solapa PROMEDIOS.
PARA PRODUCIR	Cálculo final de unidades a fabricar.
🧮 Lógica aplicada
Cálculo del Disponible
=STOCK_A + STOCK_B - PENDIENTES

Cálculo del Para Producir

Fórmula creada para automatizar la decisión de producción:

=SI(F19<=0, ABS(F19)+G19, SI(F19<G19, G19-F19, "No Producir"))


Interpretación:

Si el disponible es ≤ 0 → producir lo faltante + promedio de ventas.

Si el disponible es menor al promedio → producir la diferencia.

Si el disponible cubre el promedio → mostrar "No Producir".

🎨 Visualización y UX

El sheet incluye formato condicional:

Verde: No producir

Amarillo: Sugerencia de producción moderada

Rojo/Naranja: Prioridad inmediata

Esto permite al encargado ver en segundos qué códigos deben producirse.

✅ Resultados obtenidos

Eliminación del cálculo manual que hacía planta.

Producción basada en datos reales (stock, demanda y pendientes).

Menos quiebres de stock y menor sobreproducción.

Flujo de trabajo más claro entre administración y sector.

Actualización en tiempo real sin intercambio de archivos.
