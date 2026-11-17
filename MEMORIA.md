# MEMORIA TÉCNICA DEL PROYECTO
## Pastelería "16 de Agosto"

---

### Datos Generales
- **Proyecto:** Sitio Web Comercial e Interactivo de la Pastelería 16 de Agosto
- **Estudiante:** Maura Mamani Fernandez
- **Cliente:** Karen (Propietaria)
- **Ubicación:** Plaza principal de Colquencha (Av. Samuel 002)
- **URL de Producción (GitHub Pages):** [https://maurafernandez.github.io/PROYECTO-PASTELERIA-16/](https://maurafernandez.github.io/PROYECTO-PASTELERIA-16/)
- **Fecha:** Octubre de 2026
- **Tecnologías:** HTML5 Semántico (Drag & Drop API, Canvas 2D, Web Storage, Geolocation), CSS3 (Flexbox, Grid, Variables, Paleta por Sabores y Modo Oscuro), JavaScript (ES6+, Fetch API, Promesas), jQuery (v3.7.1)

---

## 1. Resumen Ejecutivo
La **Pastelería 16 de Agosto** es un emprendimiento local ubicado en el municipio de Colquencha. A pesar de contar con productos artesanales de alta demanda como pasteles, alfajores, galletas y bizcochos, presentaba dificultades para difundir su catálogo, informar los precios y horarios de atención actualizados, y canalizar los pedidos de forma ordenada.

Este proyecto web resuelve dicha necesidad mediante una plataforma web completa, rápida, accesible y responsive. La aplicación permite a los clientes:
1. Consultar el catálogo de productos con fotos reales, descripción, precios oficiales, etiquetas de sabor por color y disponibilidad de stock en tiempo real.
2. Filtrar por categorías (Pasteles, Dulces, Salados), ordenar por nombre, precio o stock, y buscar productos al instante.
3. Hacer clic en cualquier producto para seleccionarlo de forma automática y tramitar el encargo mediante un formulario validado que previene recargas innecesarias de la página.
4. Armar y encargar una **Bandeja de pasteles personalizados** donde cada sabor se identifica visualmente con un color diferente (Vainilla, Chocolate, Avena, Frutilla, Limón, Dulce de leche, Coco y Naranja).
5. Gestionar la planificación diaria en un **Tablero Kanban con Drag & Drop** (*Hornear hoy*, *Reponer vitrina*, *En pausa / Agotados*) acompañado de un gráfico estadístico animado en **Canvas 2D**.
6. Revisar la tabla de horarios y precios oficiales, recordar preferencias en `localStorage` (modo oscuro/claro) y calcular la distancia hasta el local al final de la página.

---

## 2. Arquitectura de Archivos y Módulos

El proyecto está organizado de manera modular, separando la estructura, la presentación, los datos y la lógica funcional e interactiva:

| Archivo | Rol / Responsabilidad |
| :--- | :--- |
| `index.html` | Estructura semántica completa (encabezado, navegación, catálogo, horarios, pedidos con selector de sabores, preferencias, tablero Drag & Drop, armador de bandeja personalizada, proveedor remoto, panel y ubicación al final). |
| `estilos.css` | Sistema de diseño: variables CSS, Flexbox, CSS Grid, modo oscuro, estilos del tablero Drag & Drop y paleta de colores distintivos para cada sabor de pastel (`.sabor-*`). |
| `app.js` | Inicialización de variables de entorno, constantes de marca, tipos de datos y aviso de stock inicial. |
| `datos.js` | Catálogo de 9 productos (incluida la *Bandeja de pasteles personalizados*), mapa de colores por sabor (`SABORES_COLORES`), pedidos registrados, métodos funcionales y clases POO. |
| `funciones.js` | Funciones de cálculo comercial (totales, descuentos, impuestos), closures y funciones de orden superior. |
| `render.js` | Generación dinámica de tarjetas de productos (`article.tarjeta` arrastrables con insignias de sabor coloreadas) y tarjetas de pedidos registrados (`#lista-pedidos`). |
| `eventos.js` | Manejo de eventos nativos: filtrado por categoría, buscador en vivo (`input`), ordenamiento y registro de pedidos (incluyendo sabores personalizados de la bandeja) con `FormData`. |
| `jquery-comparado.js` | Laboratorio 3: Implementación de jQuery v3.7.1 comparada con Vanilla JS (smooth scroll, auto-selección al clic, animaciones fade/slide y utilidades `$.each`, `$.grep`, `$.map`). |
| `jquery-panel.js` | Laboratorio 3 (Panel interactivo): Menú móvil desplegable (`slideToggle`), acordeón de preguntas frecuentes con delegación `.on()` y avisos escalonados con `.delay().fadeIn()`. |
| `remoto.js` | Módulo de asincronía y red: peticiones HTTP con Fetch API (`async/await`), jQuery AJAX (`$.getJSON`), Promesas, manejo de estados (cargando/ok/error) y serialización JSON. |
| `preferencias.js` | Persistencia de preferencias en `localStorage`, modo oscuro/claro accesible y geolocalización Haversine ubicada al cierre del contenido principal. |
| `tablero.js` | Tablero Kanban con HTML5 Drag & Drop de la pastelería, armador interactivo de bandeja de pasteles personalizados (cada sabor con color diferente) y gráfico animado en Canvas 2D. |
| `datos.json` | Estructura de datos JSON con el catálogo de insumos y materia prima del proveedor mayorista. |

---

## 3. Desarrollo Técnico por Etapas

### Etapa 1: Estructura HTML5 y Maquetación CSS
- **HTML Semántico:** Uso riguroso de `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<table>` (con `<caption>`, `<thead>`, `<tbody>`, `<th>`), `<aside>` y `<footer>`.
- **Formularios Accesibles:** Agrupación con `<fieldset>` y `<legend>`, vinculación estricta de `<label for="...">` con `<input id="...">`, atributos `required`, expresiones regulares para teléfonos bolivianos (`pattern="[0-9]{7,8}"`) y control de fechas.
- **Diseño Visual y Accesibilidad:**
  - Definición de tokens en `:root` (`--color-principal: #7a3f08`, `--color-acento: #d31463`, `--color-fondo: #e6a00ba1`, `--borde: #27b68b`).
  - Corrección de contraste: se ajustó el color principal sobre fondo naranja para cumplir con la norma de legibilidad WCAG (ratio superior a 4.5:1).
  - Distribución moderna con **Flexbox** en navegación y controles, y **CSS Grid** (`grid-template-columns: repeat(auto-fill, minmax(18rem, 1fr))`) para que las tarjetas de productos se adapten a cualquier dispositivo móvil o de escritorio.

---

### Etapa 2: JavaScript Moderno (Lógica del Negocio y DOM)

1. **Catálogo de Datos (`datos.js`):**
   - Estructuración de 8 productos con propiedades esenciales: `nombre`, `precio`, `categoria`, `stock`, `disponible`, `imagen` y `descripcion`.
   - Programación Orientada a Objetos: clases `Producto` y subclase `ProductoConDescuento` con métodos `estaDisponible()`, `valorEnStock()` y `precioFinal()`.
   - Métodos funcionales: uso de `.filter()` para stock disponible, `.map()` para nombres, `.reduce()` para cálculo de valor total de inventario y `.sort()` para ordenación por precio.

2. **Renderizado Dinámico (`render.js`):**
   - Eliminación de productos estáticos escritos a mano en el HTML.
   - Creación de la función `crearTarjeta(producto)` que genera nodos `<article class="tarjeta">` con imagen, nombre, precio formateado a dos decimales (`toFixed(2)`), indicador de stock o clase `.agotado`.
   - Función `render(lista)` que limpia el contenedor (`#lista-productos`) y dibuja solo los elementos requeridos.

3. **Interactividad y Eventos (`eventos.js`):**
   - **Buscador en Vivo:** Escucha el evento `input` en el campo `#buscador` para actualizar la vista mientras el usuario escribe.
   - **Filtros por Categoría:** Delegación de eventos en el contenedor `#filtros` para activar botones (`todos`, `pasteles`, `salados`, `dulces`).
   - **Envío de Pedidos:** Intercepción con `event.preventDefault()`, validación de que la fecha de entrega no sea anterior al día actual mediante `setCustomValidity`, lectura con `new FormData(formulario)` y mensaje de confirmación inmediato.

---

### Etapa 3 (Laboratorio 3): Integración de la Librería jQuery (`jquery-comparado.js` y `jquery-panel.js`)

En lugar de botones aislados de prueba, la librería **jQuery 3.7.1** se integró para potenciar la experiencia de usuario directamente sobre el sitio de la pastelería, contrastando su sintaxis con Vanilla JavaScript:

1. **Carga y Espera al DOM:** Inicialización mediante `$(function () { ... })` frente a `DOMContentLoaded`, garantizando que todo el árbol HTML esté construido antes de ejecutar la lógica.
2. **Selección, Clases y Encadenamiento (Chaining):** Uso de `$(".tarjeta").addClass("tarjeta-interactiva")` y encadenamiento `.css().attr()` sobre `#aviso-stock`.
3. **Interactividad en las Tarjetas:** Al hacer clic en cualquier tarjeta del catálogo:
   - Se destaca con la clase `.destacado`.
   - Se selecciona automáticamente el producto en el campo `<select id="producto">` del pedido.
   - Se ejecuta un desplazamiento suave (`animate({ scrollTop })`) hasta la sección del formulario.
4. **Smooth Scroll en la Navegación:** Los enlaces del menú (`#productos`, `#horarios`, `#pedido`, `#tablero-zona`, `#remoto`, `#panel`, `#contacto`) realizan transiciones fluidas hacia sus secciones.
5. **Panel Interactivo (`jquery-panel.js`):**
   - **Menú Móvil:** Apertura y cierre con `.slideToggle(200)` sincronizando el atributo `aria-expanded`.
   - **Acordeón de Preguntas Frecuentes:** Delegación en una línea con `$("#acordeon").on("click", ".titulo", ...)` cerrando los paneles hermanos con `.not($cuerpo).slideUp(200)`.
   - **Avisos Escalonados de la Pastelería:** Animación secuencial con `.each()` y `.delay(indice * 120).fadeIn(250)` informando sobre las bandejas de pasteles personalizados por color, pasteles recién horneados y alfajores.
6. **Efectos Visuales y Utilidades de Datos:**
   - Transición del catálogo con `.hide().fadeIn(350)` al cambiar filtros, resaltado de filas con `.hover()` y confirmación de pedido con `.slideDown(400)`.
   - Uso de `$.each()`, `$.grep()` y `$.map()` sobre el arreglo `productos` de `datos.js`.

---

### Etapa 4: Datos que Llegan por la Red (Asincronía, Fetch API, jQuery AJAX y JSON)

Se implementó el módulo **`remoto.js`** y el archivo de datos **`datos.json`** para simular la integración con el proveedor mayorista de materia prima e insumos:

1. **Estructura JSON y Serialización:**
   - Creación de `datos.json` conteniendo la información de la distribuidora (`negocio`) y la lista de insumos (`productos`).
   - Demostración de serialización y deserialización con `JSON.stringify()` y `JSON.parse()`.

2. **Gestión de Estados de Red en la Interfaz (UI):**
   - Implementación de la función `mostrarEstado(texto, tipo)` para reflejar visualmente los tres estados de una petición HTTP:
     - **Cargando:** Clase `.cargando` con animación pulsante (`@keyframes latir`).
     - **Éxito (OK):** Clase `.ok` informando el número de productos y procedencia.
     - **Error:** Clase `.error` capturando códigos HTTP (ej. 404) y excepciones de red.

3. **Consumo Asíncrono con Fetch API y `async/await`:**
   - Función `cargarConFetch(url)` con control de excepciones `try/catch`.
   - Verificación de la respuesta con `if (!respuesta.ok) throw new Error(...)`.
   - Renderizado dinámico de tarjetas de insumos en `#lista-remota` mediante `pintarRemoto(productos)`.
   - Botón de prueba de error (`#cargar-roto`) que solicita un endpoint inexistente para comprobar la captura del error 404.

4. **Consumo Alternativo con jQuery AJAX:**
   - Implementación con `$.getJSON("datos.json")`.
   - Encadenamiento de callbacks `.done()`, `.fail()` y `.always()`.

5. **Promesas y Ciclo de Vida:**
   - Función `consultarDisponibilidadProveedor(insumo)` retornando `new Promise((resolve, reject))` con simulación de latencia de red mediante `setTimeout`.
   - Demostración práctica mediante el botón `#probar-promesa`.

6. **Herramientas de Desarrollador (DevTools Network):**
   - Guía para inspección de peticiones HTTP en la pestaña Network / Red de las herramientas de desarrollador.

---

### Etapa 5: Preferencias del Usuario, Persistencia (`localStorage`) y Modo Oscuro

Se implementó el módulo **`preferencias.js`** y la suite de diseño accesible en **`estilos.css`** para memorizar la configuración del visitante:

1. **Persistencia con `localStorage`:**
   - Lectura resiliente mediante `JSON.parse()` envuelta en bloque `try/catch`.
   - Guardado inmediato de elecciones con serialización `JSON.stringify()`.
   - Botón de reinicio ("Olvidar mis preferencias") con `localStorage.removeItem()`.

2. **Modo Oscuro Integrado y Accesible:**
   - Activación mediante la clase `.tema-oscuro` en el `<body>`.
   - Paleta de tokens oscuros refinada: fondo `#16202a`, superficie `#1e2b38`, acento cálido `#e88a5c` y contraste tipográfico que cumple normas WCAG.
   - Sincronización del botón interactivo con atributo semántico `aria-pressed` y cambio dinámico de etiqueta ("Modo claro" / "Modo oscuro").
   - Adaptación completa de tarjetas, tablas, formularios, acordeones y encabezados en modo oscuro.

3. **Sincronización del Catálogo con Preferencias de Orden:**
   - Integración directa entre el criterio seleccionado (`#orden`: nombre, precio, stock) y la función `actualizar()` de `eventos.js` para reordenar dinámicamente el catálogo.

4. **Geolocalización Asistida (`navigator.geolocation`):**
   - Cálculo de distancia en kilómetros mediante la fórmula del semiverseno (Haversine) hasta el local en Colquencha, con manejo granular de permisos y estados de carga.

---

### Etapa 6: Tablero Drag & Drop, Bandeja Personalizada y Gráfico en Canvas (`tablero.js`)

El módulo **`tablero.js`** organiza la producción diaria de la **Pastelería 16 de Agosto** mediante HTML5 Drag & Drop (`dragstart`, `dragover`, `dragleave`, `drop` y `dragend`), permitiendo arrastrar los productos entre tres columnas según su función: **🔥 Hornear hoy** (sirve para listar los lotes activos que entran al horno como pasteles, galletas y bandejas personalizadas), **🧁 Reponer vitrina** (sirve para controlar los productos con pocas unidades en mostrador como alfajores y bizcochos que deben reabastecerse) y **⏸️ En pausa / Agotados** (sirve para agrupar los productos temporalmente sin stock como masitas y queques hasta su próximo turno); además, integra el **Armador de Bandeja de Pasteles Personalizados** (donde cada sabor tiene un color diferente para arrastrarlo y registrarlo como pedido) y el **Gráfico en `<canvas>` 2D** (`#grafico`), que sirve para visualizar y comparar en tiempo real la cantidad total de unidades acumuladas en cada columna.

---

## 4. Tabla de Precios y Catálogo Sincronizado

Se corrigieron las discrepancias existentes entre la tabla física de horarios y el inventario dinámico:

| Producto | Categoría | Sabor / Color | Precio Oficial | Estado / Disponibilidad |
| :--- | :--- | :--- | :--- | :--- |
| **Bandeja de pasteles personalizados** | Pasteles | Surtido (6 sabores por color) | Bs 120.00 | Disponible (15 en stock) |
| **Pastel de vainilla** | Pasteles | 🌼 Vainilla (Dorado) | Bs 45.00 | Disponible (40 en stock) |
| **Pastel de chocolate** | Pasteles | 🍫 Chocolate (Cacao) | Bs 55.00 | Disponible (25 en stock) |
| **Pastel de avena** | Pasteles | 🌾 Avena (Ámbar) | Bs 45.00 | Disponible (8 en stock) |
| **Masitas** | Salados | 🧀 Queso y sal (Azul) | Bs 35.00 | Agotado (0 en stock) |
| **Alfajores** | Salados | 🍯 Dulce de leche (Caramelo) | Bs 10.00 | Disponible (30 en stock) |
| **Bizcochos** | Dulces | 🥥 Coco (Índigo) | Bs 45.50 | Disponible (2 en stock) |
| **Galletas** | Dulces | 🍋 Limón (Esmeralda) | Bs 35.00 | Disponible (50 en stock) |
| **Queques** | Dulces | 🍊 Naranja (Coral) | Bs 1.00 | Agotado (0 en stock) |

---

## 5. Depuración y Errores Corregidos

1. **Etiquetas y Estructura HTML:**
   - Corrección de etiquetas mal cerradas (`<h1>` y `<h3>` se abrían dos veces).
   - Corrección de etiquetas `<img>` que tenían atributos anidados incorrectos.
   - Reparación de la tabla de horarios (cerraba con `</body>` en vez de `</tbody>` y carecía de cierres `</tr>`).
   - Corrección de ortografía en el catálogo: de `Alfabores` a `Alfajores`, `Pastel ` a `Pastel de vainilla`.
2. **Contraste de Color:**
   - Reparación del error de sintaxis en CSS (`s#e29a3c` &rarr; `#7a3f08`) y ajuste para garantizar lectura cómoda sin fatiga visual.
3. **Manejo de Errores en JavaScript y jQuery:**
   - Eliminación de errores de ejecución por llamadas a `document.querySelector` nulos.
   - Retiro de botones artificiales de prueba (`#boton-vanilla`, `#boton-jquery`) para integrar jQuery directamente sobre los componentes productivos de la web.
   - Enlace correcto del script CDN de jQuery antes de los módulos que lo consumen.

---

## 6. Conclusiones
El proyecto de la **Pastelería 16 de Agosto** ha alcanzado un estándar profesional de desarrollo frontend. La combinación de Vanilla JS para la arquitectura de datos y renderizado dinámico, junto con jQuery para animaciones, efectos y navegación interactiva, logra una plataforma robusta, veloz y atractiva para los clientes de Colquencha.

---

## 7. Control de Versiones y Despliegue (Git)

El proyecto utiliza Git para el seguimiento de versiones y control de cambios en el repositorio local y remoto:

- **Rama principal:** `main`
- **Última Actualización (Octubre de 2026):**
  - **Mensaje sugerido:** `feat: tablero drag & drop de pastelería, bandeja personalizada por color de sabor y memoria actualizada`
  - **Archivos incluidos y actualizados hoy:**
    - `index.html`: Incorporación de la *Bandeja de pasteles personalizados* en tabla y formulario, selector de sabores por color, armador Drag & Drop (`#armador-bandeja`), avisos reales en `#panel` y reubicación de `#ubicacion` al final de `<main>`.
    - `estilos.css`: Diseño del tablero Kanban, armador de bandeja y paleta cromática por sabor 
    - `datos.js`: Mapa `SABORES_COLORES`, producto *Bandeja de pasteles personalizados* y pedido inicial personalizado con 6 sabores de diferente color.
    - `render.js`: Renderizado de etiquetas coloreadas por sabor (`.pill-sabor`) en tarjetas de productos y de pedidos registrados, además de habilitar el arrastre de tarjetas del catálogo hacia el tablero.
    - `eventos.js`: Captura de los sabores seleccionados al registrar pedidos de bandejas personalizadas.
    - `tablero.js`: Lógica completa de Drag & Drop del tablero de producción de la pastelería, armador interactivo de bandeja personalizada, soporte móvil/táctil y gráfico animado en `<canvas>` 2D.
    
### Instrucciones para sincronizar con GitHub:
Para publicar los cambios en el repositorio remoto:
```bash
git add .
git commit -m "feat: tablero drag & drop de pasteleria, bandeja personalizada por sabor/color y memoria"
git push origin main
```
