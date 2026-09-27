# 🎬 CineVerse

Sitio web de catálogo de series y películas, desarrollado como trabajo práctico integrador para la materia **Diseño y Desarrollo Web** (UADE). El objetivo fue aplicar HTML5, CSS3 y JavaScript para construir una interfaz moderna, responsive e interactiva, con contenido y funcionalidades dinámicas manejadas 100% del lado del cliente.

🔗 **Demo:** [tpo-diseno-web.vercel.app](https://tpo-diseno-web.vercel.app/)

## 👥 Autores
Paula Batalla - Mateo Larrosa

## 📌 Descripción del proyecto

CineVerse simula la plataforma de un sitio de streaming: permite explorar un catálogo de series y películas, ver próximos estrenos con trailers, y comprar merchandising a través de un carrito de compras funcional. Todo el contenido y las funcionalidades interactivas se manejan con JavaScript vanilla, sin frameworks ni backend.

## 🚀 Funcionalidades principales

**Catálogo**
- Filtrado por tipo (series/películas), género y búsqueda por texto (título o actor)
- Ordenamiento por título o año, ascendente/descendente
- Búsqueda global desde el header, con redirección a resultados filtrados

**Merchandising**
- Carrito de compras con persistencia en `localStorage`
- Agregar, eliminar y vaciar productos, con cálculo de total en tiempo real
- Paginación de productos

**Estrenos**
- Acordeón horizontal con trailers embebidos de YouTube y descripción extendida de cada título

**General**
- Diseño responsive (desktop, tablet y mobile)
- Formulario de contacto con validación
- Navegación consistente entre secciones

## 🛠️ Tecnologías utilizadas
- HTML5 semántico
- CSS3 (Flexbox, Grid, variables CSS, media queries)
- JavaScript (ES6+, manipulación del DOM, `localStorage`)
- [Bootstrap 5](https://getbootstrap.com/) (carrusel del home)
- Font Awesome (iconografía)
- Google Fonts (Poppins)
- Deploy con [Vercel](https://vercel.com/)

## ✅ Testing
El sitio pasó una ronda de QA manual cubriendo filtros, ordenamiento, carrito de compras, formulario de contacto, acordeón de estrenos y comportamiento responsive. La documentación completa está en [`/qa`](./qa):
- [Test Plan](./qa/test-plan.md) — alcance, estrategia y entorno de testing
- [Test Cases](./qa/test-cases.md) — 37 casos de prueba ejecutados
- [Bug Reports](./qa/bug-reports.md) — defectos detectados y su resolución

## 🎯 Objetivos del trabajo
- Aplicar buenas prácticas de desarrollo web (HTML semántico, separación de responsabilidades, código legible)
- Implementar interactividad y manipulación dinámica del DOM sin frameworks
- Lograr un diseño visual atractivo, consistente y funcional
- Desarrollar un sitio navegable, responsive y accesible

## 🌍 Deploy
https://tpo-diseno-web.vercel.app/
