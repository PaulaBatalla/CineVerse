# Test Cases — CineVerse

Casos ejecutados en la Ronda 2 (ver `test-plan.md`), sobre la versión corregida del sitio. Todos los resultados corresponden a lo verificado manualmente en Google Chrome, escritorio.

## Módulo: Home

| ID | Caso | Pasos | Resultado esperado | Resultado obtenido | Estado |
|---|---|---|---|---|---|
| HOME-01 | Carrusel automático | 1. Ingresar a Home. 2. Esperar sin interactuar. | El carrusel avanza automáticamente entre las 3 imágenes. | Según lo esperado. | Pass |
| HOME-02 | Navegación manual del carrusel | 1. Click en flecha "Siguiente". 2. Click en flecha "Anterior". | El slide cambia en la dirección correspondiente. | Según lo esperado. | Pass |
| HOME-03 | Indicadores del carrusel | 1. Observar los indicadores mientras el carrusel avanza. | El indicador activo coincide con el slide visible. | Según lo esperado. | Pass |
| HOME-04 | CTA del carrusel | 1. Click en el botón de cada slide ("Explorar catálogo", etc.). | Redirige a `catalogo.html`. | Según lo esperado. | Pass |
| HOME-05 | Toggle Series/Películas | 1. En "Lo más destacado", click en "Películas". 2. Click en "Series". | Se muestran solo las cards del tipo seleccionado. | Según lo esperado. | Pass |
| HOME-06 | Buscador del header | 1. Escribir un texto en el buscador del header. 2. Presionar Enter. | Redirige a `catalogo.html?q=texto` con el catálogo filtrado. | Según lo esperado. | Pass |
| HOME-07 | Formulario de contacto — envío válido | 1. Completar nombre, email y mensaje. 2. Click en "Enviar". | Aparece confirmación y el formulario se limpia. | Según lo esperado. | Pass |
| HOME-08 | Formulario de contacto — campos vacíos | 1. Dejar un campo vacío. 2. Click en "Enviar". | Se muestra aviso de campos requeridos, no se envía. | Según lo esperado. | Pass |

## Módulo: Catálogo

| ID | Caso | Pasos | Resultado esperado | Resultado obtenido | Estado |
|---|---|---|---|---|---|
| CAT-01 | Carga inicial | 1. Ingresar a `catalogo.html`. | Se listan las 24 cards del catálogo. | Según lo esperado. | Pass |
| CAT-02 | Búsqueda por título | 1. Escribir un título parcial (ej. "dune") en el buscador. | Se filtran solo las cards cuyo título coincide. | Según lo esperado. | Pass |
| CAT-03 | Búsqueda por actor | 1. Escribir el nombre de un actor (ej. "pedro pascal"). | Se filtran las cards donde ese actor participa. | Según lo esperado. | Pass |
| CAT-04 | Filtro por tipo | 1. Click en "Series". 2. Click de nuevo en "Series" para desactivar. | Al activar, solo se muestran series; al desactivar, se muestran todas. | Según lo esperado. | Pass |
| CAT-05 | Filtro por género | 1. Seleccionar un género del select. | Se filtran las cards que coinciden con el género. | Según lo esperado. | Pass |
| CAT-06 | Combinación de filtros | 1. Activar tipo + género + texto de búsqueda simultáneamente. | El resultado respeta las tres condiciones a la vez. | Según lo esperado. | Pass |
| CAT-07 | Ordenamiento por título | 1. Click en "Título ↑". 2. Click en "Título ↓". | El orden alfabético cambia según la dirección; el botón activo se resalta. | Según lo esperado. | Pass |
| CAT-08 | Ordenamiento por año | 1. Click en "Año ↑". 2. Click en "Año ↓". | El orden numérico cambia según la dirección; el botón activo se resalta. | Según lo esperado. | Pass |
| CAT-09 | Búsqueda desde el home | 1. Buscar un término desde el header del Home y presionar Enter. | El catálogo carga con el buscador precargado y ya filtrado. | Según lo esperado. | Pass |
| CAT-10 | Mensaje sin resultados | 1. Buscar un término que no coincide con ningún título/actor. | Se muestra el mensaje de "sin resultados". | Según lo esperado. | Pass |

## Módulo: Merchandising

| ID | Caso | Pasos | Resultado esperado | Resultado obtenido | Estado |
|---|---|---|---|---|---|
| MERCH-01 | Carga y paginación | 1. Ingresar a `merchandising.html`. | Se listan 12 productos, paginados de a 3. | Según lo esperado. | Pass |
| MERCH-02 | Navegación de páginas | 1. Click en "Siguiente"/"Anterior" y en números de página. | Cambia la página mostrada; los botones se deshabilitan en los extremos. | Según lo esperado. | Pass |
| MERCH-03 | Agregar al carrito | 1. Click en "Agregar al carrito" de un producto. | El contador del header suma y aparece una notificación. | Según lo esperado. | Pass |
| MERCH-04 | Ver contenido del carrito | 1. Abrir el ícono del carrito. | Se listan los productos agregados con nombre, precio y cantidad. | Según lo esperado. | Pass |
| MERCH-05 | Agregar producto repetido | 1. Agregar el mismo producto dos veces. | La cantidad del ítem suma en vez de duplicar la fila. | Según lo esperado. | Pass |
| MERCH-06 | Eliminar ítem individual | 1. Click en el ícono de eliminar de un ítem del carrito. | El ítem se elimina y el total se recalcula. | Según lo esperado. | Pass |
| MERCH-07 | Vaciar carrito | 1. Click en "Vaciar carrito" y confirmar. | El carrito queda vacío. | Según lo esperado. | Pass |
| MERCH-08 | Finalizar compra | 1. Con productos en el carrito, click en "Finalizar compra". | Se muestra el total correcto y el carrito se vacía. | Según lo esperado. | Pass |
| MERCH-09 | Persistencia del carrito | 1. Agregar productos. 2. Recargar la página (F5). | Los productos siguen en el carrito tras recargar. | Según lo esperado. | Pass |
| MERCH-10 | Cerrar carrito | 1. Abrir el carrito. 2. Click en el overlay o en la "X". | El carrito se cierra. | Según lo esperado. | Pass |

## Módulo: Estrenos

| ID | Caso | Pasos | Resultado esperado | Resultado obtenido | Estado |
|---|---|---|---|---|---|
| EST-01 | Carga inicial | 1. Ingresar a `estrenos.html`. | Se listan los 5 estrenos con poster e info breve. | Según lo esperado. | Pass |
| EST-02 | Expandir item | 1. Click en la flecha de un estreno. | Se expande mostrando trailer y descripción extensa. | Según lo esperado. | Pass |
| EST-03 | Solo un item expandido a la vez | 1. Expandir un item. 2. Expandir otro sin cerrar el primero. | El primero se contrae automáticamente al abrir el segundo. | Según lo esperado. | Pass |
| EST-04 | Reproducción del trailer | 1. Con un item expandido, dar play al video embebido. | El trailer de YouTube reproduce correctamente. | Según lo esperado. | Pass |
| EST-05 | Contraer item | 1. Click de nuevo en la flecha de un item expandido. | El item se contrae. | Según lo esperado. | Pass |

## Módulo: Responsive

| ID | Caso | Pasos | Resultado esperado | Resultado obtenido | Estado |
|---|---|---|---|---|---|
| RESP-01 | Home en viewport reducido | 1. Reducir el ancho de la ventana a ~375px (emulado por redimensionado, no dispositivo real). | El layout se adapta sin elementos cortados ni superpuestos. | Según lo esperado. | Pass |
| RESP-02 | Catálogo en viewport reducido | 1. Ídem anterior en `catalogo.html`. | Filtros, cards y controles de orden se adaptan correctamente. | Según lo esperado. | Pass |
| RESP-03 | Merchandising en viewport reducido | 1. Ídem anterior en `merchandising.html`. | Productos y carrito lateral se adaptan correctamente. | Según lo esperado. | Pass |
| RESP-04 | Estrenos en viewport reducido | 1. Ídem anterior en `estrenos.html`. | El acordeón cambia a layout vertical sin romperse. | Según lo esperado. | Pass |

## Resumen

- **Total de casos ejecutados:** 37
- **Pass:** 37
- **Fail:** 0
- **Cobertura:** funcional completa según el alcance definido en `test-plan.md`. No incluye mobile real ni cross-browser (ver limitaciones en `test-plan.md`, sección 6).
