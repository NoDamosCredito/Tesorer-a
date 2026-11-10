# No Damos Crédito · Tesorería y donaciones

```
index.html   Todo el panel (estilos, animaciones, cálculos y gráficos)
data/        Los Excel: uno por obra y TESORERIA.xlsx
assets/      Logo, icono y carteles (assets/carteles/<obra>.jpg)
```

## Los Excel

**Uno por obra** (por ejemplo `RECAUDACION_HAMILTON.xlsx`), con el formato de siempre: Sesión, Fecha, Día, Hora, Total, Efectivo, Bizum, Receptor Bizum 1, Recaudación Bizum 1, Receptor Bizum 2, Recaudación Bizum 2, Asistentes, Recaudación por asistente, Aforo, Capacidad, Protagonistas de la sesión, Técnicos, Director.

- El nombre de la hoja es el título de la obra.
- Los actores van en "Protagonistas de la sesión" (también vale una columna "Actores" o "Ensemble"; se suman todos como actores). Nombres separados por punto y coma.
- Una función sin Efectivo ni Asistentes cuenta como pendiente. La fila TOTAL se ignora.
- Si una función tiene donaciones pero Asistentes o Aforo vacíos o "n/a", su dinero cuenta en la recaudación, pero no en asistentes, ocupación ni euros por espectador.
- El panel calcula con Efectivo y las columnas "Recaudación Bizum", así que las fórmulas del Excel no le afectan. Se pueden añadir parejas "Receptor Bizum 3 / Recaudación Bizum 3".

**`TESORERIA.xlsx`**, con dos hojas:

- CUENTA (Fecha, Saldo): el saldo del banco. Se muestra la fila más reciente. La que hay (8.300 €) es de ejemplo.
- GASTOS (Fecha, Obra, Concepto, Categoría, Importe): un gasto por fila. En Obra, el nombre de la hoja de la obra (Hamilton), o vacío si es general.

## Añadir una obra

1. Copia su Excel en `data/`.
2. Añade su nombre a la lista `ARCHIVOS`, al principio del script de `index.html`:
   ```js
   const ARCHIVOS = [
     'RECAUDACION_HAMILTON.xlsx',
     'Recaudacion_Luna_Sobre_Buffalo.xlsx',
     'Recaudacion_La_Funcion_que_sale_mal.xlsx',
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
