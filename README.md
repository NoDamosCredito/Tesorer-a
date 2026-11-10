# No Damos Crédito · Tesorería y taquilla

```
index.html   Todo el panel (estilos, animaciones, cálculos y gráficos)
data/        RECUADACIONES.xlsx
assets/      Logo, icono y carteles (assets/carteles/<obra>.jpg)
```

El panel lee directamente `data/RECUADACIONES.xlsx`. No hay que convertir nada: se sustituye el Excel y listo.

## El Excel

- **Una hoja por obra**, con las columnas de siempre: Sesión, Fecha, Día, Hora, Total, Efectivo, Bizum, Receptor Bizum 1, Recaudación Bizum 1, Receptor Bizum 2, Recaudación Bizum 2, Asistentes, Recaudación por asistente, Aforo, Capacidad, Protagonistas de la sesión, Ensemble de la sesión, Técnicos, Director. El nombre de la hoja es el título de la obra.
- Una función sin Efectivo ni Asistentes cuenta como pendiente. La fila TOTAL se ignora.
- El panel calcula los totales a partir de Efectivo y de las columnas "Recaudación Bizum", así que las fórmulas del Excel no le afectan. Se pueden añadir más parejas "Receptor Bizum 3 / Recaudación Bizum 3".
- Hoja **CUENTA** (Fecha, Saldo): el saldo del banco. Se muestra la fila más reciente.
- Hoja **GASTOS** (Fecha, Obra, Concepto, Categoría, Importe): un gasto por fila. En Obra va el nombre de la hoja de la obra, o vacío si es un gasto general.

Para otra obra: una hoja nueva en el mismo Excel y, si quieres cartel, `assets/carteles/<nombre-de-la-hoja-en-minúsculas>.jpg` (por ejemplo `mamma-mia.jpg`).

Si prefieres un Excel por obra, añade su nombre a la lista `ARCHIVOS` que está al principio del script de `index.html`.

## Abrirlo

- **Publicado** (GitHub Pages o cualquier servidor): funciona sin más.
- **Con doble clic**: el navegador no deja leer la carpeta `data`, así que el panel pide el Excel con un botón. Se elige y carga igual.

Con GitHub Pages activado la web es pública, y el Excel lleva nombres y las cuentas de la asociación.
