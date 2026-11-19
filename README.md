# No Damos Crédito · Tesorería y donaciones

```
index.html   Todo el panel (estilos, animaciones, cálculos y gráficos)
data/        Los Excel: uno por obra y TESORERIA.xlsx
assets/      Logo, icono y carteles (assets/carteles/<obra>.jpg)
```

## Los Excel

**Uno por obra** (por ejemplo `RECAUDACION_HAMILTON.xlsx`), con el formato de siempre: Sesión, Fecha, Día, Hora, Total, Efectivo, Bizum, Receptor Bizum 1, Recaudación Bizum 1, Receptor Bizum 2, Recaudación Bizum 2, Asistentes, Recaudación por asistente, Aforo, Capacidad, Protagonistas de la sesión, Técnicos, Director.

- El nombre de la hoja es el título de la obra. Si la hoja se llama "Hoja1" o el nombre está cortado (Excel admite 31 caracteres), el título se toma del nombre del archivo: `Recaudacion_Ni_Oficio_ni_beneficio.xlsx` → Ni Oficio ni beneficio.
- Los actores van en "Protagonistas de la sesión" (también vale una columna "Actores" o "Ensemble"; se suman todos como actores). Nombres separados por punto y coma.
- Una función sin Efectivo ni Asistentes cuenta como pendiente. La fila TOTAL se ignora.
- Si una función tiene donaciones pero Asistentes o Aforo vacíos o "n/a", su dinero cuenta en la recaudación, pero no en asistentes, ocupación ni euros por espectador.
- **Métodos de pago.** Desde Hamilton el formato incluye también las columnas TPV y QR, y "Bizum" pasa a llamarse "Digital" (Bizum + TPV + QR). Los dos formatos funcionan: las obras sin TPV ni QR siguen mostrando solo efectivo y Bizum, y en las que sí los tienen aparecen sus columnas, colores y comparativas.
- El panel calcula con Efectivo, TPV, QR y las columnas "Recaudación Bizum", así que las fórmulas del Excel no le afectan. Se pueden añadir parejas "Receptor Bizum 3 / Recaudación Bizum 3".

**Hoja "Gastos" de cada Excel de obra**: una línea "Total" con los gastos totales de la obra (o varias partidas, una por fila, y el panel las suma). Con ella se calcula el beneficio. Si está vacía, el beneficio sale como "Faltan los gastos".

**`TESORERIA.xlsx`**, con dos hojas:

- CUENTA (Fecha, Saldo, Pendiente de cobro, Concepto pendiente): el saldo del banco. Se muestra la fila más reciente; si hay algo pendiente de cobro, también aparece el saldo cuando llegue.
- GASTOS (Fecha, Obra, Concepto, Categoría, Importe): los gastos sueltos del día a día, que salen en "Últimos gastos". En Obra, el nombre de la obra o vacío si es general.

## Añadir una obra

1. Copia su Excel en `data/`.
2. Añade su nombre a la lista `ARCHIVOS`, al principio del script de `index.html`:
   ```js
   const ARCHIVOS = [
     'RECAUDACION_HAMILTON.xlsx',
     'Recaudacion_Mamma_Mia.xlsx',
     // ... el resto de obras
     'Recaudacion_Nueva_Obra.xlsx',   // la nueva
     'TESORERIA.xlsx',
   ];
   ```
3. Si quieres cartel: `assets/carteles/<nombre de la hoja en minúsculas, sin tildes y con guiones>.jpg` (hoja "La Función que sale mal" → `la-funcion-que-sale-mal.jpg`).

Mejor sin tildes ni espacios en los nombres de los Excel: evita problemas al subirlos a GitHub.

## Abrirlo

- **Publicado** (GitHub Pages o cualquier servidor): funciona sin más.
- **Con doble clic**: el navegador no deja leer la carpeta `data`, así que el panel muestra un botón para elegir los Excel (se pueden seleccionar varios a la vez).

Con GitHub Pages activado la web es pública, y los Excel llevan nombres y las cuentas de la asociación.
