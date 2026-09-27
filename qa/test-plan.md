# Test Plan — CineVerse

## 1. Objetivo
Verificar que las funcionalidades principales de CineVerse (catálogo, merchandising, estrenos y formulario de contacto) funcionen correctamente desde la perspectiva del usuario final, y detectar defectos antes de considerar el sitio listo para portfolio.

## 2. Alcance

### Dentro de alcance
- Testing funcional de las 4 páginas: Home, Catálogo, Merchandising, Estrenos
- Validación de formularios (contacto)
- Persistencia de datos en `localStorage` (carrito)
- Comportamiento responsive (breakpoints de la hoja de estilos: 768px y 480px)

### Fuera de alcance
- Testing de performance / carga
- Testing de seguridad
- Testing en dispositivos móviles físicos (se probó emulando viewport en desktop)
- Testing cross-browser (se probó únicamente en Google Chrome)
- Testing de accesibilidad con lector de pantalla (se aplicaron mejoras de accesibilidad, pero no se validaron con herramientas como NVDA/VoiceOver)

## 3. Entorno de testing
| Ítem | Detalle |
|---|---|
| URL | https://tpo-diseno-web.vercel.app/ |
| Navegador | Google Chrome (última versión estable) |
| Sistema operativo | Windows |
| Método responsive | Redimensionado de ventana de escritorio (no emulador de dispositivo ni dispositivo físico) |
| Tipo de testing | Manual, exploratorio + basado en casos documentados |

## 4. Estrategia
Se realizaron dos rondas de testing:

1. **Ronda 1 — Revisión de código + exploratoria**: lectura del código fuente para identificar antipatrones y bugs potenciales, confirmados luego manualmente en el sitio. Los defectos encontrados se documentan en `bug-reports.md` y fueron corregidos antes de la Ronda 2.
2. **Ronda 2 — Basada en casos de prueba**: ejecución de los casos formales listados en `test-cases.md`, sobre la versión ya corregida.

## 5. Criterios de aceptación
Se considera el sitio apto para portfolio si todos los casos de prueba de `test-cases.md` pasan (estado *Pass*) y no quedan defectos abiertos de severidad alta o crítica en `bug-reports.md`.

## 6. Riesgos conocidos / limitaciones
- No se probó en mobile real, por lo que pueden existir defectos de touch/viewport no detectados
- No se probó en otros navegadores (Firefox, Safari); el sitio usa Bootstrap y CSS estándar, pero no hay garantía de paridad total
- El carrito depende de `localStorage`, por lo que no persiste entre navegadores ni dispositivos distintos

## 7. Documentos relacionados
- `test-cases.md` — casos de prueba detallados y resultados
- `bug-reports.md` — defectos encontrados durante la Ronda 1 y su resolución
