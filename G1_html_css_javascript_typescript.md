# 🧠 Repaso: HTML, CSS, JavaScript y TypeScript

> **Objetivo:** tener una **plantilla mental** de las estructuras más comunes de cada lenguaje: **cómo se ven**, **cómo se escriben** y **qué hacen**.
> **Fuentes (carpeta `Notas`):** `C2` (HTML), `C3` (HTML + CSS), `C5` (Flexbox y Grid), `C6` (JavaScript) y `C7` (TypeScript).
> **Excluido:** `C1` (cliente-servidor y HTTP) y `C4` (Git, Codespaces y GitHub Pages), porque no tratan HTML, CSS, JavaScript ni TypeScript.

---

## Cómo leer este repaso

Cada subtema empieza con una **🧩 Plantilla** (el esqueleto de la sintaxis) y sigue con una tabla de conceptos:

| Columna | Qué contiene |
|---|---|
| **Concepto / Item** | El nombre de la pieza (etiqueta, propiedad, método, palabra clave…) |
| **Función** | Para qué sirve, en una frase |
| **Categoría** | El **tipo** al que pertenece (solo aparece cuando hay varios tipos; si no, `—`) |
| **Ejemplo** | La sintaxis mínima para reconocerlo |

> 🔍 Al final (sección 5) hay una tabla **"Si ves esto → es esto"** para identificar estructuras de un vistazo.

---

## Contenido

1. [Mapa general: cómo se conectan los lenguajes](#0-mapa-general-cómo-se-conectan-los-lenguajes)
2. [HTML](#1-html)
   - [1.1 Sintaxis básica](#11-sintaxis-básica) · [1.2 Esqueleto y metadatos](#12-esqueleto-y-metadatos) · [1.3 Texto](#13-texto) · [1.4 Listas](#14-listas) · [1.5 Enlaces y rutas](#15-enlaces-y-rutas) · [1.6 Semántica y estructura](#16-semántica-y-estructura-de-página) · [1.7 Imágenes y medios](#17-imágenes-y-medios) · [1.8 Formularios](#18-formularios) · [1.9 Tablas](#19-tablas) · [1.10 Atributos globales](#110-atributos-globales) · [1.11 Accesibilidad y errores](#111-accesibilidad-y-errores-comunes)
3. [CSS](#2-css)
   - [2.1 Sintaxis y vinculación](#21-sintaxis-y-vinculación) · [2.2 Selectores](#22-selectores) · [2.3 Cascada y herencia](#23-cascada-herencia-y-especificidad) · [2.4 Modelo de caja](#24-modelo-de-caja) · [2.5 Unidades, color y texto](#25-unidades-color-y-texto) · [2.6 Display y medios](#26-display-y-medios-adaptables) · [2.7 Flexbox](#27-flexbox) · [2.8 Grid](#28-grid) · [2.9 Flexbox vs Grid](#29-flexbox-vs-grid) · [2.10 Responsive](#210-responsive-media-queries) · [2.11 Estados y formularios](#211-estados-pseudo-clases-y-formularios) · [2.12 Variables](#212-variables-css) · [2.13 Patrones](#213-patrones-css-frecuentes)
4. [JavaScript](#3-javascript)
   - [3.1 Dónde corre](#31-dónde-corre-y-cómo-se-conecta) · [3.2 Variables, tipos y operadores](#32-variables-tipos-y-operadores) · [3.3 Funciones](#33-funciones) · [3.4 Valores ausentes](#34-valores-ausentes-y-desestructuración) · [3.5 Objetos globales](#35-objetos-globales-del-navegador) · [3.6 DOM](#36-dom-seleccionar-y-modificar) · [3.7 Arrays y strings](#37-arrays-y-strings) · [3.8 Eventos](#38-eventos) · [3.9 Geometría](#39-geometría-y-visibilidad) · [3.10 Asincronía](#310-asincronía) · [3.11 JSON](#311-json) · [3.12 Extensiones Chrome](#312-javascript-en-extensiones-de-chrome-contexto) · [3.13 Depuración](#313-depuración-y-errores-típicos)
5. [TypeScript](#4-typescript)
   - [4.1 Qué es y flujo](#41-qué-es-y-flujo-de-trabajo) · [4.2 Anotaciones e inferencia](#42-anotaciones-inferencia-y-tipos-básicos) · [4.3 Literales y uniones](#43-tipos-literales-uniones-y-narrowing) · [4.4 Interfaces y alias](#44-interfaces-y-alias-de-tipos) · [4.5 Funciones tipadas](#45-funciones-tipadas) · [4.6 Arrays y strings](#46-arrays-y-strings-con-tipos) · [4.7 Módulos](#47-módulos) · [4.8 DOM y null](#48-dom-tipado-null-y-aserciones) · [4.9 Render y organización](#49-patrón-de-render-y-organización) · [4.10 Herramientas avanzadas](#410-herramientas-avanzadas) · [4.11 Configuración](#411-configuración-del-proyecto-ts)
6. [Si ves esto → es esto (reconocer estructuras)](#5-si-ves-esto--es-esto)

---

## 0. Mapa general: cómo se conectan los lenguajes

**🧩 Plantilla**

```html
<!-- index.html -->
<link rel="stylesheet" href="css/estilos.css">      <!-- conecta el CSS -->
<script src="js/app.js" defer></script>             <!-- conecta el JavaScript -->
<script type="module" src="/src/main.ts"></script>  <!-- proyecto TypeScript con empaquetador (Vite) -->
```

```text
 HTML (estructura) ──▶ el navegador lo analiza ──▶ DOM (árbol de objetos)
 CSS  (presentación) ─────────────────────────────▶ da estilo al DOM
 JS   (comportamiento) ───────────────────────────▶ lee y modifica el DOM, reacciona a eventos
 TS   (JS con tipos) ──▶ se comprueba y se convierte a JS ──▶ el navegador solo ejecuta JS
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| **HTML** | Describe la **estructura y el significado** del contenido | Estructura | `<h1>Título</h1>` |
| **CSS** | Define la **apariencia** (colores, tamaños, espacios, disposición) | Presentación | `h1 { color: navy; }` |
| **JavaScript** | Da **comportamiento**: reacciona y modifica la página | Comportamiento | `boton.addEventListener("click", fn)` |
| **TypeScript** | JavaScript **con tipos estáticos**; detecta errores antes de ejecutar | Comportamiento (con tipos) | `let n: number = 5;` |
| **DOM** | Árbol de objetos que el navegador **construye** del HTML | — | `document.querySelector("h1")` |
| **Separación de responsabilidades** | HTML, CSS y JS en archivos distintos para reutilizar y mantener | — | `css/estilos.css` + `js/app.js` |

---

## 1. HTML

### 1.1 Sintaxis básica

**🧩 Plantilla**

```html
<etiqueta atributo="valor" atributo-booleano>contenido</etiqueta>   <!-- elemento con contenido -->
<etiqueta-vacia atributo="valor">                                   <!-- elemento vacío: sin cierre -->
<!-- comentario: el navegador lo ignora -->
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| **Elemento** | Unidad de contenido: apertura + contenido + cierre | Con contenido / Vacío (*void*) | `<p>Hola</p>` · `<br>` |
| **Etiqueta de apertura y de cierre** | Delimitan el elemento; el cierre lleva `/` | — | `<a>` … `</a>` |
| **Atributo** | Información adicional con forma `nombre="valor"` dentro de la apertura | Con valor / Booleano / Global | `href="#perfil"` · `required` · `id="x"` |
| **Elementos vacíos** | No tienen contenido ni etiqueta de cierre | — | `<img>` `<br>` `<hr>` `<input>` `<meta>` `<link>` `<source>` `<track>` |
| **Atributo booleano** | Su **presencia** lo activa; `disabled="false"` **sigue** desactivando | — | `<input required disabled>` |
| **Anidamiento** | Los elementos forman un **árbol**; se cierran en **orden inverso** | — | `<p><strong><em>texto</em></strong></p>` |
| **Comentario** | Texto ignorado por el navegador | — | `<!-- nota -->` |
| **Entidad** | Muestra caracteres especiales o reservados | — | `&lt;` `&gt;` `&amp;` `&quot;` `&nbsp;` `&copy;` |
| **De bloque** | Ocupa **todo el ancho** y empieza en **línea nueva** (por defecto) | Bloque | `div` `p` `h1`–`h6` `ul` `section` `article` `header` `footer` `form` `figure` |
| **En línea** | Fluye **dentro del texto** y ocupa solo lo necesario (por defecto) | En línea | `span` `a` `strong` `em` `code` `time` `label` `img` |
| **Espacios en blanco** | Varios espacios o saltos de línea se **colapsan** en uno | — | `<p>Hola     mundo</p>` → "Hola mundo" |
| **Reglas de contenido** | Hijos válidos de ciertos elementos | — | `<ul>` solo `<li>` · `<p>` no admite `div` · `<a>` y `<button>` sin interactivos dentro |

### 1.2 Esqueleto y metadatos

**🧩 Plantilla**

```html
<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Resumen breve de la página">
    <title>Página | Sitio</title>
    <link rel="stylesheet" href="css/estilos.css">
  </head>
  <body>
    <!-- contenido visible -->
  </body>
</html>
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `<!DOCTYPE html>` | Declara documento **HTML5** y activa el modo estándar (no es una etiqueta) | Estructura | `<!DOCTYPE html>` |
| `<html lang>` | **Raíz** del documento; `lang` declara el **idioma** (lectores de pantalla, traducción) | Estructura | `<html lang="es">` |
| `<head>` | Contiene **metadatos**; no se muestra como contenido | Estructura | `<head>…</head>` |
| `<body>` | Contiene **todo el contenido visible** | Estructura | `<body>…</body>` |
| `<title>` | **Título** del documento: pestaña, historial, favoritos, buscadores | Metadato | `<title>Inicio \| Mi sitio</title>` |
| `<meta charset>` | **Codificación** de caracteres (UTF-8 evita `PÃ©rez`); al inicio del `head` | Metadato | `<meta charset="UTF-8">` |
| `<meta name="viewport">` | Adapta el ancho de la página a **pantallas móviles** | Metadato | `content="width=device-width, initial-scale=1.0"` |
| `<meta name="description">` | **Resumen** para buscadores y vistas previas (≈ 150–160 caracteres) | Metadato | `<meta name="description" content="…">` |
| `<link>` | Enlaza **recursos externos** (CSS, íconos) | Metadato (vacío) | `<link rel="stylesheet" href="a.css">` · `<link rel="icon" href="favicon.ico">` |
| `<style>` | CSS **dentro** del HTML | Metadato | `<style>p{color:red}</style>` |
| `<script>` | Carga **JavaScript** (`src`, `defer`, `type="module"`) | Metadato / Comportamiento | `<script src="app.js" defer></script>` |
| `<meta property="og:*">` | Controla la **vista previa** al compartir (Open Graph) | Metadato | `<meta property="og:title" content="…">` |
| **Metadato vs. contenido** | Metadato: está en `head`, lo usan navegadores y buscadores; contenido: en `body`, lo ve la persona | — | `charset` / `h1` |

### 1.3 Texto

**🧩 Plantilla**

```html
<h1>Título principal</h1>
  <h2>Sección</h2>
    <h3>Subsección</h3>
<p>Párrafo con <strong>importancia</strong> y <em>énfasis</em>.</p>
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `<h1>`–`<h6>` | **Títulos** jerárquicos; un `h1` por página; no saltar niveles; se eligen por **nivel**, no por tamaño | Título | `<h2>Experiencia</h2>` |
| `<p>` | **Párrafo** | Texto | `<p>Texto</p>` |
| `<br>` | **Salto de línea** (vacío) | Texto | `línea 1<br>línea 2` |
| `<hr>` | **Cambio de tema** (línea horizontal, vacío) | Texto | `<hr>` |
| `<div>` | Contenedor de **bloque** genérico (sin significado) | Genérico | `<div class="caja">…</div>` |
| `<span>` | Contenedor **en línea** genérico | Genérico | `<span lang="en">hello</span>` |
| `<strong>` | **Gran importancia** (negrita por defecto) | Énfasis | `<strong>Ojo</strong>` |
| `<em>` | **Énfasis** (cursiva por defecto) | Énfasis | `<em>aprender</em>` |
| `<b>` / `<i>` | Negrita / cursiva **sin** significado extra | Énfasis | `<b>marca</b>` · `<i>término</i>` |
| `<mark>` | Texto **resaltado** | Énfasis | `<mark>clave</mark>` |
| `<small>` | Letra pequeña (aclaraciones) | Énfasis | `<small>Aviso legal</small>` |
| `<del>` / `<ins>` | Texto **eliminado** / **insertado** | Énfasis | `<del>viejo</del> <ins>nuevo</ins>` |
| `<sub>` / `<sup>` | Subíndice / superíndice | Énfasis | `H<sub>2</sub>O` · `x<sup>2</sup>` |
| `<abbr>` | **Abreviatura** con su significado en `title` | Énfasis | `<abbr title="HyperText Markup Language">HTML</abbr>` |
| `<code>` | Fragmento de **código** en línea | Código y citas | `<code>npm run dev</code>` |
| `<pre>` | Texto **preformateado** (respeta espacios y saltos) | Código y citas | `<pre><code>…</code></pre>` |
| `<kbd>` | Entrada de **teclado** | Código y citas | `<kbd>Ctrl</kbd> + <kbd>S</kbd>` |
| `<blockquote>` / `<q>` / `<cite>` | Cita **larga** / cita **corta** / título de la obra | Código y citas | `<blockquote cite="url">…</blockquote>` |
| `<time datetime>` | **Fecha** legible por máquinas; la persona ve el texto interior | Fecha | `<time datetime="2025-05">mayo 2025</time>` |
| **Formatos de `datetime`** | Año, año-mes, fecha, fecha y hora, duración | Fecha | `2023` · `2025-05` · `2026-10-26` · `2026-10-26T14:30` · `PT1M` |

### 1.4 Listas

**🧩 Plantilla**

```html
<ul>  <li>elemento</li>  </ul>                       <!-- no ordenada -->
<ol start="1" reversed>  <li>paso</li>  </ol>        <!-- ordenada -->
<dl>  <dt>término</dt>  <dd>descripción</dd>  </dl>  <!-- de descripción -->
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `<ul>` | Lista **sin orden** (viñetas) | Lista | `<ul><li>Harina</li></ul>` |
| `<ol>` | Lista **ordenada** (pasos, ranking) | Lista | `<ol><li>Mezclar</li></ol>` |
| `<li>` | **Elemento** de lista (dentro de `ul`/`ol`) | Lista | `<li>Agua</li>` |
| `<dl>` `<dt>` `<dd>` | Pares **término → descripción** | Lista | `<dt>Levadura</dt><dd>Hongo…</dd>` |
| Atributos de `<ol>` | `start` (inicio), `reversed` (cuenta atrás), `type` (letras/números) | Atributo | `<ol start="5">` |
| **Lista anidada** | La lista interna va **dentro de un `<li>`** | — | `<li>Panes<ul><li>Casero</li></ul></li>` |
| **Menú de navegación** | Un menú es una **lista de enlaces**; luego CSS lo pone en fila | — | `<nav><ul><li><a href="#a">A</a></li></ul></nav>` |

### 1.5 Enlaces y rutas

**🧩 Plantilla**

```html
<a href="destino" target="_blank" rel="noopener noreferrer">Texto descriptivo</a>
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `<a href>` | **Enlace**; `href` indica el destino (sin `href` no es navegable) | — | `<a href="contacto.html">Contacto</a>` |
| **URL absoluta** | Lleva a **otro sitio** | Tipo de destino | `href="https://developer.mozilla.org/"` |
| **Ruta relativa** | Lleva a otro archivo **del mismo sitio** | Tipo de destino | `href="contacto.html"` · `href="img/foto.jpg"` · `href="../foto.jpg"` |
| **Ancla interna** | Salta a otra parte **del mismo documento** (`#` + `id`) | Tipo de destino | `<a href="#experiencia">` ↔ `<section id="experiencia">` |
| **Ancla + página** | Sección de **otra página** | Tipo de destino | `href="guia.html#paso2"` |
| **Correo / teléfono** | Abre el cliente de correo / inicia una llamada | Tipo de destino | `href="mailto:ana@ejemplo.com"` · `href="tel:+593999999999"` |
| `target="_blank"` | Abre en **otra pestaña** | Atributo | `<a href="…" target="_blank">` |
| `rel="noopener noreferrer"` | Recomendado con `_blank` (seguridad y privacidad) | Atributo | `rel="noopener noreferrer"` |
| `download` | El destino se **descarga** | Atributo | `<a href="a.pdf" download>` |
| **Texto del enlace** | Debe describir el destino por sí solo (evitar "haz clic aquí") | — | `Ver recetas de pan` |
| **Rutas de archivo** | `./` misma carpeta · `../` carpeta superior · `/` raíz del sitio | — | `css/estilos.css` · `../index.html` · `/img/logo.png` |

### 1.6 Semántica y estructura de página

**🧩 Plantilla**

```html
<body>
  <header>
    <h1>Título del sitio</h1>
    <nav aria-label="Menú principal"><ul> <li><a href="#a">A</a></li> </ul></nav>
  </header>
  <main>
    <section id="a">
      <h2>Tema</h2>
      <article> <h3>Elemento independiente</h3> … </article>
    </section>
    <aside>Complemento</aside>
  </main>
  <footer><p>&copy; 2026 Autor</p></footer>
</body>
```

```text
┌──────────────────────────────────────────┐
│ header  (marca, título, nav)             │
├───────────────────────────┬──────────────┤
│ main  (section / article) │ aside        │
├───────────────────────────┴──────────────┤
│ footer                                   │
└──────────────────────────────────────────┘
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `<header>` | **Introducción**: marca, título, navegación (de la página o de una sección) | Estructura de página | `<header>…</header>` |
| `<nav>` | Bloque de **navegación principal** (no para cualquier grupo de enlaces) | Estructura de página | `<nav aria-label="Secciones">…</nav>` |
| `<main>` | **Contenido principal**; **solo uno** visible por página | Estructura de página | `<main>…</main>` |
| `<aside>` | Contenido **relacionado pero secundario** (barra lateral) | Estructura de página | `<aside>…</aside>` |
| `<footer>` | **Cierre** de la página o sección (autoría, derechos, enlaces) | Estructura de página | `<footer>…</footer>` |
| `<section>` | **Agrupación temática** con **título** (`h2`…) | Agrupación | `<section id="perfil"><h2>Perfil</h2>…</section>` |
| `<article>` | Contenido **autónomo y reutilizable**; se **repite** dentro de una `section` | Agrupación | `<article class="item"><h3>…</h3></article>` |
| `<figure>` + `<figcaption>` | Contenido **ilustrativo** con su **leyenda** | Ilustración | `<figure><img …><figcaption>Pie</figcaption></figure>` |
| `<address>` | **Contacto** de la autoría | Ilustración | `<address>ana@ejemplo.com</address>` |
| `<search>` | Zona con **funcionalidad de búsqueda** (elemento nuevo, desde 2023) | Interactivo | `<search><form>…</form></search>` |
| `<details>` + `<summary>` | Contenido **desplegable** sin JavaScript | Interactivo | `<details><summary>Más</summary>Texto</details>` |
| `<dialog>` | **Cuadro de diálogo**; se abre con JS (`showModal()`) | Interactivo | `<dialog id="d">…</dialog>` |
| `<div>` / `<span>` | Contenedor **sin significado**; último recurso | Genérico | `<div class="caja">` |
| **`section` vs `article` vs `div`** | `section`: tema con título · `article`: independiente · `div`: solo contenedor para CSS/JS | — | 3 experiencias → **1 `section`** con **3 `article`** |
| **Jerarquía de títulos** | Un `h2` por `section`; un `h3` por `article` dentro de ella | — | `h1` › `h2 Experiencia` › `h3 Ayudante` |
| **Landmarks (roles)** | `header`→`banner` · `nav`→`navigation` · `main`→`main` · `aside`→`complementary` · `footer`→`contentinfo` · `search`→`search` | — | Permiten **saltar** entre zonas con lector de pantalla |
| `aria-label` | **Nombre accesible** (sin efecto visual); distingue varias zonas iguales | Atributo | `<nav aria-label="Secciones del CV">` |
| **Por qué semántica** | Accesibilidad, buscadores, mantenimiento, legibilidad, CSS más claro | — | `<footer>` dice más que `<div class="pie">` |

### 1.7 Imágenes y medios

**🧩 Plantilla**

```html
<figure>
  <img src="img/foto.jpg" alt="Descripción" width="640" height="360" loading="lazy">
  <figcaption>Leyenda</figcaption>
</figure>

<video controls width="640" poster="img/portada.jpg">
  <source src="media/v.mp4" type="video/mp4">
  Texto alternativo si no hay soporte.
</video>
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `<img src>` | **Imagen**; `src` = ruta/URL (obligatorio) | Imagen | `<img src="a.jpg" alt="…">` |
| `alt` | **Texto alternativo** (lectores de pantalla, si la imagen no carga) | Atributo de `img` | `alt="Captura de la aplicación"` |
| `alt=""` | Imagen **decorativa**: se ignora | Atributo de `img` | `<img src="adorno.png" alt="">` |
| `width` / `height` | Reservan espacio y **evitan saltos** de diseño | Atributo de `img` | `width="640" height="360"` |
| `loading="lazy"` | Descarga solo cuando está **cerca de verse** | Atributo de `img` | `<img loading="lazy" …>` |
| `srcset` / `sizes` | **Versiones** de distinto tamaño según la pantalla | Atributo de `img` | `srcset="a-400.jpg 400w, a-800.jpg 800w"` |
| `<picture>` + `<source>` | Varias **fuentes** (formato/tamaño); `<img>` final obligatorio | Imagen | `<picture><source srcset="a.webp" type="image/webp"><img src="a.jpg" alt="…"></picture>` |
| **Formatos** | JPEG (fotos) · PNG (transparencia) · WebP/AVIF (ligeros) · SVG (vectorial) · GIF (animación simple) | Imagen | `foto.jpg` · `logo.svg` |
| `<figure>` / `<figcaption>` | Agrupan contenido ilustrativo y su **leyenda** | Imagen / medio | `<figure>…<figcaption>…</figcaption></figure>` |
| `<video>` | **Video**; contenido interior = alternativa para navegadores sin soporte | Medio | `<video controls src="v.mp4"></video>` |
| `controls` | Muestra **controles** de reproducción | Atributo de `video` | `<video controls>` |
| `poster` | **Portada** antes de reproducir | Atributo de `video` | `poster="portada.jpg"` |
| `autoplay` · `muted` · `loop` | Reproducción automática (suele exigir `muted`) · sin sonido · repetir | Atributo de `video` | `<video autoplay muted loop>` |
| `preload` · `playsinline` | Cuánto precargar (`none`/`metadata`/`auto`) · reproducir en la página (iOS) | Atributo de `video` | `preload="metadata"` |
| `<source src type>` | **Archivo** y formato; se pueden ofrecer varios | Medio | `<source src="v.webm" type="video/webm">` |
| `<track>` | **Subtítulos** o descripciones | Medio | `<track kind="subtitles" src="es.vtt" srclang="es" label="Español">` |
| `<audio>` | **Audio** (igual que `video`, sin imagen) | Medio | `<audio controls src="p.mp3"></audio>` |
| `<iframe>` | **Incrusta** otra página; siempre con `title` | Medio | `<iframe src="…" title="Receta en video"></iframe>` |

### 1.8 Formularios

**🧩 Plantilla**

```html
<form action="/destino" method="get">
  <label for="nombre">Nombre</label>
  <input type="text" id="nombre" name="nombre" required autocomplete="name">

  <label for="motivo">Motivo</label>
  <select id="motivo" name="motivo">
    <option value="a">Opción A</option>
  </select>

  <label for="mensaje">Mensaje</label>
  <textarea id="mensaje" name="mensaje" rows="4" minlength="10" required></textarea>

  <label><input type="checkbox" name="acepto" required> Acepto</label>
  <button type="submit">Enviar</button>
</form>
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `<form>` | **Agrupa** los controles que se envían juntos (`action`, `method`) | Contenedor | `<form method="get" action="/buscar">` |
| `<label for>` | **Etiqueta** de un control; `for` = `id` del campo (clic en la etiqueta enfoca el campo) | Etiqueta | `<label for="correo">Correo</label>` |
| `<input>` | Entrada de **una línea** o control, según `type` | Control | `<input type="text" name="n">` |
| `<select>` + `<option>` | **Lista desplegable**; `value` es lo que se envía | Control | `<option value="empleo">Oferta</option>` |
| `<textarea>` | Texto **largo** de varias líneas (`rows`) | Control | `<textarea rows="4"></textarea>` |
| `<button>` | **Botón**; dentro de un form es `submit` por defecto | Control | `<button type="button">` |
| `<fieldset>` + `<legend>` | **Agrupa** controles relacionados con un título | Contenedor | `<fieldset><legend>Nivel</legend>…</fieldset>` |
| `<datalist>` | **Sugerencias** para un `<input>` | Control | `<input list="ciudades">` |
| `type="text"` · `email` · `password` · `tel` · `url` · `search` · `number` | Texto y variantes (validan formato, teclado móvil adaptado) | Tipo de `input`: texto | `<input type="email">` |
| `type="date"` · `time` · `datetime-local` · `month` | **Selector** nativo de fecha/hora | Tipo de `input`: fecha | `<input type="date">` |
| `type="checkbox"` · `radio` · `range` · `color` · `file` | Marcar · opción **única** (mismo `name`) · deslizador · color · archivo | Tipo de `input`: selección | `<input type="radio" name="nivel" value="a">` |
| `type="submit"` · `reset` · `button` | **Botones** | Tipo de `input`: botón | `<input type="submit" value="Enviar">` |
| `type="hidden"` | Envía un dato **sin mostrarlo** | Tipo de `input`: oculto | `<input type="hidden" name="id" value="5">` |
| `name` | **Nombre con que viaja el dato**; sin `name`, el campo **no se envía** | Atributo | `name="correo"` |
| `id` | Identificador **único** (`label for`, CSS, JS) | Atributo | `id="correo"` |
| `value` | Valor inicial / valor enviado | Atributo | `value="empleo"` |
| `required` | **Obligatorio**: bloquea el envío si está vacío | Validación | `<input required>` |
| `minlength` / `maxlength` | Mínimo / máximo de **caracteres** | Validación | `minlength="10"` |
| `min` / `max` / `step` | Límites para números y fechas | Validación | `<input type="number" min="0" max="10">` |
| `pattern` | **Expresión regular** que debe cumplirse | Validación | `pattern="[0-9]{4}"` |
| `autocomplete` | **Sugiere** el tipo de dato para autocompletar (no valida) | Ayuda | `autocomplete="email"` |
| `placeholder` | Texto de ayuda dentro del campo (**no sustituye** al `label`) | Ayuda | `placeholder="ana@correo.com"` |
| `disabled` / `readonly` / `autofocus` | Desactivado (no se envía) · solo lectura (sí se envía) · foco inicial | Estado | `<input disabled>` |
| **`method="get"`** | Datos en la **URL** (`?a=1&b=2`), visibles; para búsquedas | Envío | `/?nombre=Ana&correo=ana%40ej.com` |
| **`method="post"`** | Datos en el **cuerpo** de la solicitud; para crear/modificar | Envío | `<form method="post">` |
| **Casilla** | Solo se envía **si está marcada** (valor por defecto `on`) | — | `acepto=on` |

### 1.9 Tablas

**🧩 Plantilla**

```html
<table>
  <caption>Título de la tabla</caption>
  <thead><tr><th scope="col">Encabezado</th></tr></thead>
  <tbody><tr><td>Dato</td></tr></tbody>
</table>
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `<table>` | Contenedor de la tabla (para **datos**, no para maquetar) | Estructura | `<table>…</table>` |
| `<caption>` | **Título** de la tabla | Estructura | `<caption>Ingredientes</caption>` |
| `<thead>` `<tbody>` `<tfoot>` | Encabezado / cuerpo / pie | Estructura | `<tbody>…</tbody>` |
| `<tr>` | **Fila** | Fila | `<tr><td>…</td></tr>` |
| `<th>` | Celda de **encabezado** (`scope="col"` o `"row"`) | Celda | `<th scope="col">Nombre</th>` |
| `<td>` | Celda de **datos** | Celda | `<td>500 g</td>` |
| `colspan` / `rowspan` | Celda que **abarca** varias columnas / filas | Atributo | `<td colspan="2">` |

### 1.10 Atributos globales

**🧩 Plantilla:** `<cualquier-etiqueta id="único" class="clase1 clase2" lang="es" hidden data-x="1">`

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `id` | Identificador **único** (anclas, `label for`, CSS `#`, JS) | Identificación | `id="perfil"` |
| `class` | Una o **varias clases**, reutilizables (CSS `.`, JS) | Identificación | `class="item destacado"` |
| `style` | CSS **en línea** (evitar en general) | Presentación | `style="color:red"` |
| `title` | Texto adicional (*tooltip*) | Información | `title="Ayuda"` |
| `lang` | **Idioma** del elemento | Información | `lang="en"` |
| `hidden` | **Oculta** el elemento | Estado | `<p hidden>` |
| `tabindex` | Orden/posibilidad de **foco** con teclado | Accesibilidad | `tabindex="0"` |
| `data-*` | **Datos personalizados** (en JS: `el.dataset.id`) | Datos | `data-id="5"` |
| `aria-*` / `role` | Información para **tecnologías de asistencia** | Accesibilidad | `aria-label="Menú"` |
| `contenteditable` · `popover` | Contenido **editable** · elemento **emergente** | Comportamiento | `<div contenteditable>` |
| **`id` vs `class`** | `id`: único, un elemento concreto · `class`: se repite, patrones | — | `#perfil` / `.item` |

### 1.11 Accesibilidad y errores comunes

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `lang` en `<html>` | Pronunciación y traducción correctas | Buena práctica | `<html lang="es">` |
| Títulos jerárquicos | Navegación **por títulos** | Buena práctica | `h1` › `h2` › `h3` |
| `alt` + `label` | Describen imágenes y campos a quien no los ve | Buena práctica | `<img alt="…">` · `<label for="x">` |
| Botones reales | Funcionan con **teclado** y lectores | Buena práctica | `<button>` en vez de `<div onclick>` |
| `<h3>` solo por tamaño | Jerarquía incorrecta → elegir por **nivel** y ajustar con CSS | Error común | ❌ `<h3>` para "letra pequeña" |
| `<br>` para espaciar | Maquetación frágil → usar `margin`/`padding` | Error común | ❌ `<br><br>` |
| "div soup" | Sin significado → usar etiquetas semánticas | Error común | ❌ `<div class="pie">` |
| `id` repetido | Fallan anclas y `label for` | Error común | ❌ dos `id="menu"` |
| Falta `name` | El campo **no se envía** | Error común | ❌ `<input type="text">` |
| Mal anidado / sin cerrar | Resultados impredecibles | Error común | ❌ `<b><i>x</b></i>` |
| Ruta incorrecta | `404` en Network, imagen rota | Error común | ❌ `src="Img/foto.jpg"` (mayúsculas) |

---

## 2. CSS

### 2.1 Sintaxis y vinculación

**🧩 Plantilla**

```css
selector {
  propiedad: valor;
  otra-propiedad: valor1 valor2;   /* comentario */
}
```

```html
<link rel="stylesheet" href="css/estilos.css">   <!-- en el <head> -->
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| **Regla** | **Selector** + bloque `{ }` de declaraciones | — | `h2 { color: navy; }` |
| **Selector** | Indica **a qué elementos** se aplica | — | `h2` · `.item` · `#perfil` |
| **Declaración** | Par `propiedad: valor;` | — | `color: navy;` |
| **Propiedad / Valor** | Qué aspecto se cambia / cómo | — | `padding` / `32px` |
| **Comentario** | Texto ignorado | — | `/* nota */` |
| **Hoja externa** | Archivo `.css` enlazado: reutilizable, un solo punto de cambio, se cachea | Dónde se escribe: Externa | `<link rel="stylesheet" href="css/estilos.css">` |
| **Hoja interna** | CSS dentro de `<style>` | Dónde se escribe: Interna | `<style>p{color:red}</style>` |
| **Estilo en línea** | Atributo `style` en un elemento | Dónde se escribe: En línea | `<p style="color:red">` |
| **Ruta mal escrita** | El CSS da `404` y la página **se ve sin estilos** (no se rompe) | — | `href="css/estilo.css"` (sin la *s*) |
| **Atajos (*shorthand*)** | 1 valor = los 4 lados · 2 = vertical/horizontal · 4 = arriba/derecha/abajo/izquierda | — | `margin: 32px 0;` · `padding: 12px 24px;` |

### 2.2 Selectores

**🧩 Plantilla**

```css
*            { }   /* universal */
p            { }   /* etiqueta */
.clase       { }   /* clase */
#identificador { } /* id */
nav a        { }   /* descendiente: <a> dentro de <nav> */
h1, h2, h3   { }   /* agrupado */
a:hover      { }   /* pseudo-clase */
:root        { }   /* raíz del documento */
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| **Universal** `*` | Todos los elementos | Básico | `* { box-sizing: border-box; }` |
| **Etiqueta** | Todos los elementos de ese tipo | Básico | `section { padding: 32px; }` |
| **Clase** `.x` | Elementos con `class="x"` (patrones repetidos) | Básico | `.item { padding: 16px; }` |
| **Id** `#x` | El **único** elemento con `id="x"` | Básico | `#perfil { border-top: 4px solid red; }` |
| **Descendiente** (espacio) | Elementos **dentro** de otro; limita el estilo a una zona | Combinador | `nav a { color: white; }` |
| **Agrupado** (coma) | Mismas reglas para varios selectores | Combinador | `.tarjetas, .pie-columnas { gap: 1rem; }` |
| **Pseudo-clase** `:estado` | Aplica según el **estado** del elemento | Pseudo-clase | `button:hover { … }` |
| `:root` | Raíz del documento (≈ `<html>`); aquí se declaran variables | Pseudo-clase | `:root { --color: #fff; }` |

### 2.3 Cascada, herencia y especificidad

**🧩 Plantilla (orden de prioridad)**

```text
estilo en línea  >  #id  >  .clase / :pseudo-clase / [atributo]  >  etiqueta  >  *
a igual especificidad → gana la regla que aparece DESPUÉS
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| **Especificidad** | Decide **qué regla gana** cuando varias compiten | Peso: inline › id › clase › etiqueta › `*` | `#perfil` gana a `section` |
| **Orden en el archivo** | Con **empate** de especificidad gana la **última** | — | dos reglas `p { }` → vale la de abajo |
| **Herencia** | Un hijo usa el valor del padre si no define uno propio | Se heredan | `color`, `font-family`, `font-size`, `line-height`, `text-align` |
| **No se heredan** | Cada elemento tiene el suyo | No se heredan | `margin`, `padding`, `border`, `background`, `width` |
| `inherit` | Fuerza a **heredar** un valor | Valor | `font-family: inherit;` |
| **Casos de especificidad** | `.casilla` gana a `label`; `nav li` gana a `li`; `nav a` gana a `a` | — | `label { font-weight: bold }` vs `.casilla { font-weight: normal }` |
| **Declaración tachada** | En DevTools → Styles marca la que **perdió** | — | `section { border-top: red }` tachada |
| **Id vs clase (en proyectos grandes)** | Se prefieren clases: el `id` tiene alta especificidad y es difícil de sobrescribir | — | `.item` en vez de `#item` |

### 2.4 Modelo de caja

**🧩 Plantilla**

```css
* { box-sizing: border-box; }   /* el width incluye padding y borde */

.caja {
  width: 600px;
  padding: 32px;                /* interno */
  border: 2px solid red;        /* grosor estilo color */
  margin: 0 auto;               /* externo; auto = centrar */
}
```

```text
┌─────────────── margin ───────────────┐
│ ┌──────────── border ─────────────┐  │
│ │ ┌───────── padding ──────────┐  │  │
│ │ │  contenido (width × height)│  │  │
│ │ └────────────────────────────┘  │  │
│ └─────────────────────────────────┘  │
└──────────────────────────────────────┘
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| **Contenido** | El texto/elementos (`width`, `height`) | Capa de la caja | `width: 600px;` |
| `padding` | Espacio **interno** entre contenido y borde | Capa de la caja | `padding: 32px;` |
| `border` | Línea alrededor del padding | Capa de la caja | `border: 2px solid red;` |
| `margin` | Espacio **externo**; no cuenta en el ancho | Capa de la caja | `margin: 32px 0;` |
| `box-sizing: content-box` | **Por defecto**: `width` = solo contenido → total = 600 + 2·32 + 2·2 = **668 px** | Modo | `box-sizing: content-box;` |
| `box-sizing: border-box` | `width` incluye padding y borde → total = **600 px** | Modo | `* { box-sizing: border-box; }` |
| `max-width` + `margin: auto` | Limita el ancho y **centra** el bloque | Patrón | `main { max-width: 1000px; margin: auto; }` |
| `border-radius` | Esquinas **redondeadas** | Decoración | `border-radius: 10px;` |
| `box-shadow` | **Sombra**: desplazamiento x, y, desenfoque, color | Decoración | `box-shadow: 0 4px 14px rgba(0,0,0,0.08);` |
| `border-left` / `border-top` | Borde en **un solo lado** (acento de color) | Decoración | `border-left: 4px solid #2f80a3;` |

### 2.5 Unidades, color y texto

**🧩 Plantilla**

```css
body {
  font-family: Arial, Helvetica, sans-serif;   /* lista de respaldo */
  font-size: 1rem;
  line-height: 1.6;                            /* sin unidad */
  color: #263238;
  background-color: #f4f6f8;
}
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `px` | Tamaño **absoluto** | Unidad | `32px` |
| `rem` | Relativa al tamaño de fuente **raíz** (16 px por defecto) | Unidad | `2.4rem` ≈ 38,4 px |
| `em` | Relativa al tamaño de fuente del **elemento** | Unidad | `1.2em` |
| `%` | Porcentaje del **contenedor** | Unidad | `width: 100%;` |
| `fr` | **Fracción** del espacio libre (solo Grid) | Unidad | `1fr 260px` |
| *(sin unidad)* | **Multiplicador** | Unidad | `line-height: 1.6;` |
| `calc()` | Operaciones entre unidades | Función | `calc((100% - 2 * 1rem) / 3)` |
| **Nombre / hex / `rgba()`** | Formas de escribir un color (`rgba`: último valor = transparencia 0–1) | Color | `white` · `#1f3a5f` · `rgba(0,0,0,0.08)` |
| `color` | Color del **texto** | Color y fondo | `color: #263238;` |
| `background-color` | Color de **fondo** | Color y fondo | `background-color: #fff;` |
| `font-family` | **Lista de respaldo**; termina en familia genérica | Texto | `Arial, Helvetica, sans-serif` |
| `font-size` / `font-weight` | Tamaño / grosor | Texto | `font-size: 0.9rem;` · `font-weight: bold;` |
| `line-height` | Interlineado; **sin unidad** se adapta a cada elemento (con `em` los hijos heredan un valor fijo) | Texto | `line-height: 1.6;` |
| `text-align` | Alineación del texto (se hereda) | Texto | `text-align: center;` |
| `text-decoration` | Subrayado | Texto | `a { text-decoration: none; }` |
| `list-style` | Viñetas de lista | Listas | `list-style: none;` |

### 2.6 Display y medios adaptables

**🧩 Plantilla**

```css
img, video {
  display: block;       /* quita el hueco inline bajo la imagen */
  max-width: 100%;      /* nunca más ancho que su contenedor */
  height: auto;         /* mantiene la proporción */
}
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `display: block` | Ocupa su propia línea y respeta márgenes verticales | Valor de `display` | `label { display: block; }` |
| `display: flex` | Contenedor **Flexbox** (un eje) | Valor de `display` | `.menu ul { display: flex; }` |
| `display: grid` | Contenedor **Grid** (filas y columnas) | Valor de `display` | `.galeria { display: grid; }` |
| `max-width: 100%` | El medio **no excede** su contenedor ni se agranda | Medios | `img { max-width: 100%; }` |
| `height: auto` | Anula el `height` del HTML y **conserva la proporción** | Medios | `img { height: auto; }` |
| **Flujo normal** | Sin reglas de distribución, los **bloques se apilan** | — | `<article>` uno debajo de otro |
| **Separar visual y distribución** | `base.css` (colores, tipografía) y `flexbox.css`/`grid.css` (disposición) | — | misma identidad, distintas disposiciones |

### 2.7 Flexbox

**🧩 Plantilla**

```css
.contenedor {                       /* CONTENEDOR (el padre) */
  display: flex;
  flex-direction: row;              /* row | column */
  justify-content: space-between;   /* eje PRINCIPAL */
  align-items: center;              /* eje TRANSVERSAL */
  gap: 1rem;
  flex-wrap: wrap;
}
.item { flex: 1; }                  /* ELEMENTO (el hijo): grow shrink basis */
```

```text
 eje principal ─────────────▶   (row = horizontal · column = vertical)
 │  [ítem 1] [ítem 2] [ítem 3]
 ▼ eje transversal (perpendicular)
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `display: flex` | Los **hijos directos** pasan a ser elementos flex, **en fila** | Contenedor | `.cabecera { display: flex; }` |
| `flex-direction` | Dirección del **eje principal** | Contenedor | `flex-direction: column;` |
| `justify-content` | Reparte el espacio en el **eje principal** (`center`, `space-between`, `flex-start`, `flex-end`) | Contenedor | `justify-content: space-between;` |
| `align-items` | Alinea en el **eje transversal** (`center`, `flex-start`, `stretch` por defecto) | Contenedor | `align-items: center;` |
| `gap` | Separación **entre** elementos | Contenedor | `gap: 1.5rem;` |
| `flex-wrap` | `nowrap` (defecto) o `wrap`: pasar a **otra línea** | Contenedor | `flex-wrap: wrap;` |
| `flex-grow` / `flex-shrink` / `flex-basis` | Cuánto **crece** / **se encoge** / tamaño **inicial** | Elemento | `flex-basis: 260px;` |
| `flex: 1` | = `1 1 0%` → **reparte el espacio** por igual (elástico) | Elemento (abreviatura) | `.tarjeta { flex: 1; }` |
| `flex: 0 0 260px` | **Tamaño fijo**: no crece ni se encoge | Elemento (abreviatura) | `.lateral { flex: 0 0 260px; }` |
| `flex: none` | `0 0 auto`: **tamaño natural** | Elemento (abreviatura) | `.lateral { flex: none; }` |
| `margin-top: auto` | Un margen automático **absorbe el espacio** y empuja el elemento al final | Elemento | `.enlace { margin-top: auto; }` |
| `min-width: 0` | Permite **encogerse** por debajo del contenido (evita desbordes) | Elemento | `.principal { flex: 1; min-width: 0; }` |
| **Contenedores anidados** | Un elemento puede ser **hijo flex y contenedor flex** a la vez | Patrón | `.tarjeta { display: flex; flex-direction: column; }` |
| **Igual altura** | `align-items: stretch` (por defecto) estira a la altura del más alto | Patrón | filas de tarjetas |
| **Calcular columnas** | Ancho = (100% − huecos) ÷ columnas | Patrón | `flex: 0 0 calc((100% - 2 * 1rem) / 3);` |

### 2.8 Grid

**🧩 Plantilla**

```css
.contenedor {                                   /* CONTENEDOR */
  display: grid;
  grid-template-columns: 1fr 260px;             /* o repeat(3, 1fr) */
  grid-template-rows: auto 1fr auto;
  grid-template-areas: "principal lateral";     /* una cadena = una fila */
  gap: 2rem;
  place-items: center;
}
.principal { grid-area: principal; }            /* ELEMENTO */
```

```text
 línea  1       2       3
        ┌───────┬───────┐
 fila 1 │ celda │ celda │   pista = fila o columna
        ├───────┼───────┤   celda = intersección
 fila 2 │ celda │ celda │   área = región con nombre
        └───────┴───────┘
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `display: grid` | Activa Grid; por defecto, **una columna** | Contenedor | `.galeria { display: grid; }` |
| `grid-template-columns` | Define las **columnas** | Contenedor | `grid-template-columns: repeat(3, 1fr);` |
| `grid-template-rows` | Define las **filas** | Contenedor | `grid-template-rows: auto 1fr auto;` |
| `grid-template-areas` | **Dibuja el esquema** con nombres (cadena = fila, palabra = columna; comillas rectas) | Contenedor | `grid-template-areas: "principal" "lateral";` |
| `gap` | Espacio entre filas y columnas | Contenedor | `gap: 1rem;` |
| `place-items` | Abreviatura de `align-items` + `justify-items`: centra **en ambos ejes** dentro de la celda | Contenedor | `place-items: center;` |
| `justify-content` / `align-content` | Alinean **toda la rejilla** en el contenedor | Contenedor | `justify-content: space-between;` |
| `grid-auto-flow: column` | Los elementos se acomodan **en columnas** | Contenedor | `grid-auto-flow: column;` |
| `grid-area` | Coloca el elemento en el **área con ese nombre** (coincidencia de nombres) | Elemento | `.lateral { grid-area: lateral; }` |
| `px` / `auto` / `fr` | Pista **fija** / según **contenido** / **fracción** del espacio libre restante | Tamaño de pista | `1fr 260px` · `auto auto` |
| `repeat(n, x)` | **Atajo**: repite una pista *n* veces | Función | `repeat(3, 1fr)` = `1fr 1fr 1fr` |
| `minmax(0, 1fr)` | Evita que `1fr` **desborde** con contenido ancho (`1fr` = `minmax(auto, 1fr)`) | Función | `grid-template-columns: minmax(0, 1fr) 260px;` |
| **Filas implícitas** | Con más elementos que celdas, Grid **crea filas** solo | Comportamiento | galería de 3 columnas con 9 imágenes |
| `align-items: start` | Cada elemento conserva su **altura natural** | Contenedor | `align-items: start;` |

### 2.9 Flexbox vs Grid

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| **Flexbox** | **Un eje**; trabaja **de adentro hacia afuera** (el contenido manda) | Dimensión: 1D | menú, barra, contenido de una tarjeta |
| **Grid** | **Filas y columnas**; trabaja **de afuera hacia adentro** (el contenedor define) | Dimensión: 2D | esqueleto de página, galería |
| **Complementarios** | Grid para la **estructura**, Flexbox para los **componentes** | Regla práctica | `.contenedor { display: grid }` + `.menu ul { display: flex }` |

| Objetivo | Flexbox | Grid |
|---|---|---|
| Hijos en fila | `display: flex` | `display: grid` + `grid-template-columns` |
| Centrar en dos ejes | `justify-content: center; align-items: center;` | `place-items: center;` |
| Columnas iguales | `flex: 1` en cada hijo | `repeat(N, 1fr)` en el contenedor |
| Ancho fijo + flexible | `flex: 0 0 260px` + `flex: 1` | `grid-template-columns: 1fr 260px;` |
| Zonas con nombre | — | `grid-template-areas` + `grid-area` |
| Varias filas | `flex-wrap: wrap` + `calc()` | Automático con `repeat()` |
| Apilar en móvil | `flex-direction: column` | `grid-template-columns: 1fr` |
| Elemento al fondo | `margin-top: auto` | Fila `1fr` antes de él |

### 2.10 Responsive: media queries

**🧩 Plantilla**

```css
@media (max-width: 768px) {
  .contenedor { flex-direction: column; align-items: stretch; }
  .lateral    { flex: none; }
}
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `@media (condición) { … }` | Aplica reglas **solo si se cumple** la condición | At-rule | `@media (max-width: 768px) { … }` |
| `max-width: 768px` | Ventana **≤ 768 px** (límite **inclusivo**) | Condición | a 800 px no aplica; a 768 px sí |
| **Punto de quiebre** (*breakpoint*) | Valor donde cambia el diseño; el navegador **reevalúa** al redimensionar | — | `768px` |
| `<meta name="viewport">` | Necesario para que el móvil use su **ancho real** | HTML relacionado | `width=device-width, initial-scale=1.0` |
| **Flexbox en móvil** | Cambia la **dirección** y neutraliza tamaños (con `column`, `flex-basis` actúa sobre la **altura**) | Estrategia | `flex-direction: column;` + `flex: none;` |
| **Grid en móvil** | Basta **redefinir la plantilla** | Estrategia | `grid-template-columns: 1fr;` |
| **Estrategia** | **Apilar**, reducir columnas y ajustar espacios | — | galería de 3 → 2 columnas |

### 2.11 Estados, pseudo-clases y formularios

**🧩 Plantilla**

```css
a:hover { color: #2f80a3; }
button:focus-visible { outline: 3px solid #2f80a3; outline-offset: 2px; }
input:focus { outline: none; border-color: #2f80a3; box-shadow: 0 0 0 3px rgba(47,128,163,.25); }
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `:hover` | Cuando el **puntero está encima** (indica que es clicable) | Pseudo-clase | `nav a:hover { … }` |
| `:focus-visible` | Foco **visible** (teclado, tecla Tab) | Pseudo-clase | `button:focus-visible { … }` |
| `:focus` | El elemento **tiene el foco** (también con clic) | Pseudo-clase | `input:focus { … }` |
| `outline` / `outline-offset` | **Contorno** que no ocupa espacio en la caja / su separación | Interacción | `outline: 3px solid blue;` |
| `outline: none` | Quita el contorno: **exige un indicador alternativo** | Interacción | + `border-color` y `box-shadow` |
| `box-shadow: 0 0 0 3px …` | Sin desplazamiento ni desenfoque = **halo** | Interacción | `box-shadow: 0 0 0 3px rgba(…)` |
| `cursor: pointer` | Cursor de **mano** (señal de clic) | Interacción | `button { cursor: pointer; }` |
| `resize: vertical` | Redimensionar solo en vertical | Formularios | `textarea { resize: vertical; }` |
| `label { display: block }` | La etiqueta ocupa **su línea** encima del campo | Formularios | `label { display: block; margin-top: 16px; }` |
| `width: 100%` en campos | Los campos **llenan** el formulario (con `border-box`) | Formularios | `input, select, textarea { width: 100%; }` |
| `font-family: inherit` | `textarea` usa la fuente de la página (por defecto es monoespaciada) | Formularios | `textarea { font-family: inherit; }` |
| `border: 0` | Quita el borde predeterminado del botón | Formularios | `button { border: 0; }` |

### 2.12 Variables CSS

**🧩 Plantilla**

```css
:root { --nombre-variable: valor; }              /* definir (global) */
selector { propiedad: var(--nombre-variable); }  /* usar */
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `:root` | Raíz del documento: las variables definidas aquí están **en toda la página** | Declaración | `:root { --color-primario: #1f3a5f; }` |
| `--nombre` | **Variable personalizada**; el nombre empieza con `--` | Declaración | `--radio: 10px;` |
| `var(--nombre)` | **Usa** el valor de la variable | Uso | `border-radius: var(--radio);` |
| **Nombrar por rol** | Nombre por **función**, no por valor (si la marca cambia, el nombre sigue siendo cierto) | Buena práctica | ✅ `--color-primario` · ❌ `--azul-oscuro` |
| **Ventajas** | **Un solo punto de cambio**, consistencia, legibilidad, temas | — | cambiar `#1f3a5f` en 1 línea en vez de 4 |
| **Buscar y reemplazar** | Trabaja con **texto**: `6px` también coincide dentro de `16px` → revisar cada coincidencia | Precaución | `16px` ≠ `6px` |

### 2.13 Patrones CSS frecuentes

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| **Reinicio de caja** | El `width` incluye padding y borde | Base | `* { box-sizing: border-box; }` |
| **Centrar un bloque** | Ancho máximo + márgenes automáticos | Layout | `main { max-width: 1000px; margin: auto; }` |
| **Menú horizontal** | Lista en fila, sin viñetas, centrada | Layout | `nav ul { display: flex; justify-content: center; gap: 16px; list-style: none; padding: 0; }` |
| **Tarjeta** | Relleno, fondo, borde de acento y esquinas redondeadas | Componente | `.item { padding: 16px; border-left: 4px solid #2f80a3; background: #f4f6f8; border-radius: 10px; }` |
| **Sección elevada** | Fondo blanco, sombra suave | Componente | `section { background: #fff; padding: 32px; border-radius: 10px; box-shadow: 0 4px 14px rgba(0,0,0,.08); }` |
| **Imagen adaptable** | Nunca desborda y mantiene proporción | Medios | `img { display: block; max-width: 100%; height: auto; }` |
| **Enlaces solo del menú** | Selector descendiente limita el estilo a una zona | Selector | `nav a { color: white; text-decoration: none; padding: 8px; }` |
| **Esqueleto de dos columnas** | Principal flexible + lateral fijo | Layout | `grid-template-columns: 1fr 260px;` |
| **Galería de 3 columnas** | Tres columnas iguales con hueco | Layout | `display: grid; grid-template-columns: repeat(3, 1fr); gap: 1rem;` |

---

## 3. JavaScript

### 3.1 Dónde corre y cómo se conecta

**🧩 Plantilla**

```html
<script src="js/app.js" defer></script>   <!-- archivo externo; defer = espera al HTML -->
```

```js
// app.js
console.log("Hola");    // aparece en la consola de DevTools, no en la página
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| **Lenguaje (ECMAScript)** | Sintaxis y reglas, independientes del entorno | Capa 1 | `let`, `const`, funciones, `Promise`, `JSON` |
| **APIs web** | Objetos que pone el **navegador** (no son del lenguaje) | Capa 2 | `document`, `window`, `location`, `console`, `fetch` |
| **APIs de extensiones** | Objetos que solo existen en una **extensión de Chrome** | Capa 3 | `chrome.storage`, `chrome.runtime` |
| **Motor y ejecución** | **V8**; un solo hilo; **orientado a eventos** (espera y reacciona) | — | un clic dispara una función |
| `<script src defer>` | Carga el archivo `.js` | HTML relacionado | `<script src="app.js" defer></script>` |

### 3.2 Variables, tipos y operadores

**🧩 Plantilla**

```js
const constante = valor;         // no se reasigna (por defecto)
let variable = valor;            // se reasigna
variable = variable + 1;         // o variable += 1;  variable++;

if (condicion) { /* … */ } else { /* … */ }
const r = condicion ? valorSi : valorNo;
for (const item of lista) { /* … */ }
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `const` | Variable **no reasignable** (el contenido de arrays/objetos sí puede cambiar) | Declaración | `const titulo = "Mi página";` |
| `let` | Variable **reasignable** (alcance de bloque) | Declaración | `let contador = 0;` |
| `var` | Antigua (alcance de función): **evitar** | Declaración | `var x = 1;` |
| `string` | Texto (comillas `""`, `''` o `` ` ``) | Tipo | `"hola"` |
| `number` | Enteros y decimales | Tipo | `42` · `3.14` |
| `boolean` | Lógico | Tipo | `true` · `false` |
| `undefined` / `null` | Sin valor asignado / vacío **a propósito** | Tipo | `let x;` · `const y = null;` |
| `object` / `array` | Objeto `{}` y lista `[]` (los arrays son objetos) | Tipo | `{ a: 1 }` · `[1, 2]` |
| `function` | Las funciones también son **valores** | Tipo | `() => {}` |
| `typeof` | Devuelve el tipo como texto | Operador | `typeof 42` → `"number"` |
| **Falsy / truthy** | Falsy: `false`, `0`, `""`, `null`, `undefined`, `NaN`; todo lo demás es truthy | — | `if ("0")` → verdadero |
| `+ - * / %` | Aritméticos | Operador | `5 % 2` → `1` |
| `= += -= ++ --` | Asignación | Operador | `clics += 1` |
| `=== !== < > <= >=` | Comparación (usa `===`, no `==`) | Operador | `rect.top >= 0` |
| `&& \|\| !` | Lógicos | Operador | `a >= 0 && b <= 100` |
| **Plantilla de texto** | Acento grave + `${ }` para insertar expresiones | Texto | ``` `Sección ${i + 1}: ${nombre}` ``` |
| **Ternario** | `if` en una expresión | Control de flujo | `edad >= 18 ? "Mayor" : "Menor"` |
| **Trampa de `+`** | `"5" + 1` → `"51"` (concatena) pero `"5" - 1` → `4` | — | `"5" == 5` es `true` (por eso `===`) |

### 3.3 Funciones

**🧩 Plantilla**

```js
function nombre(a, b) { return a + b; }            // declaración
const nombre2 = function (a, b) { return a + b; }; // expresión
const nombre3 = (a, b) => a + b;                   // flecha (retorno implícito)
const nombre4 = (a, b) => { return a + b; };       // flecha con llaves (return explícito)

lista.forEach((x) => { /* callback */ });          // callback
(() => { /* código aislado */ })();                // IIFE
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| **Declaración** | Función con nombre; se puede usar antes de escribirla (*hoisting*) | Forma | `function sumar(a, b) { return a + b; }` |
| **Expresión** | Función guardada en una variable | Forma | `const sumar = function (a, b) { … };` |
| **Flecha** `=>` | Sintaxis compacta; **sin `this` propio**; ideal para callbacks | Forma | `const doble = x => x * 2;` |
| **Callback** | Función **entregada a otra** para que la llame **después** (es un rol, no un tipo) | Patrón | `boton.addEventListener("click", () => { … })` |
| **IIFE** | Función que se **ejecuta de inmediato** y aísla sus variables | Patrón | `(() => { const privada = 1; })();` |
| **Closure** | La función **recuerda** las variables de donde fue creada | Patrón | `function crear(){ let n=0; return () => ++n; }` |
| **Alcance global / de función / de bloque** | Dónde es visible una variable (`let`/`const`: bloque `{ }`) | Scope | `{ let x = 1; }` → `x` no existe fuera |
| **`function` vs flecha** | `this` propio y `arguments` (function) vs `this` heredado y compacta (flecha); la flecha no sirve como constructor | — | `() => {}` |
| **Callback vs función normal** | Normal: la llamas tú, ahora · Callback: la llama otro código, cuando corresponda | — | `saludar()` vs `forEach(fn)` |
| **Parámetros rest / spread** | `...args` agrupa argumentos; `[...lista]` expande/copia | Sintaxis | `[...nodos].map(…)` |

### 3.4 Valores ausentes y desestructuración

**🧩 Plantilla**

```js
const valor = objeto?.propiedad ?? "respaldo";   // seguro ante null/undefined
const { clave } = objeto;                        // desestructuración
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `undefined` | "No hay valor" (variable sin asignar, propiedad inexistente) | Valor ausente | `let x; // undefined` |
| `null` | "Vacío a propósito"; lo devuelven APIs para **"no encontrado"** | Valor ausente | `document.querySelector(".no-existe")` → `null` |
| `?.` | **Encadenamiento opcional**: si es `null`/`undefined` devuelve `undefined` sin error | Operador seguro | `el?.textContent` |
| `??` | **Fusión nula**: valor de respaldo solo para `null`/`undefined` | Operador seguro | `el?.textContent ?? "Sin título"` |
| `??` vs `\|\|` | `\|\|` reemplaza cualquier **falsy** (`0`, `""`); `??` solo `null`/`undefined` | — | `0 \|\| 10` → `10` · `0 ?? 10` → `0` |
| **Desestructuración** | Extrae propiedades de un objeto en variables | Sintaxis | `const { clave } = await chrome.storage.local.get("clave");` |
| `TypeError: … of null` | Error típico por usar el resultado `null` de un `querySelector` | Error | `null.textContent` |

### 3.5 Objetos globales del navegador

**🧩 Plantilla**

```js
document.title;          // título de la página
location.href;           // URL actual
window.innerHeight;      // alto del viewport
console.log("etiqueta:", valor);
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `window` | Ventana/pestaña y **objeto global** (`window.document` = `document`) | Objeto global | `window.innerHeight` · `window.scrollY` |
| `document` | La **página cargada**; puerta de entrada al DOM | Objeto global | `document.title` · `document.querySelector("h1")` |
| `location` | La **URL** actual | Objeto global | `location.href` |
| `location.origin` · `hostname` · `pathname` · `search` · `hash` | Partes de la URL | Propiedad | `https://es.wikipedia.org` · `/wiki/JS` · `?lang=es` · `#Historia` |
| `console` | Mensajes hacia las **herramientas de desarrollo** | Objeto global | `console.log("hola")` |
| `setTimeout(fn, ms)` | Ejecuta una función **después** de un tiempo | Función global | `setTimeout(() => console.log("B"), 0)` |

### 3.6 DOM: seleccionar y modificar

**🧩 Plantilla**

```js
const uno = document.querySelector("selector-css");          // Element | null
const varios = document.querySelectorAll("selector-css");    // NodeList (estática)

uno.textContent = "texto seguro";
uno.innerHTML = "<b>html</b>";

const nuevo = document.createElement("li");
nuevo.textContent = dato;
lista.append(nuevo);
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `querySelector(css)` | **Primer** elemento que coincide; `null` si no hay | Selección | `document.querySelector("h1")` |
| `querySelectorAll(css)` | **Todos** los que coinciden en un `NodeList` (vacío si no hay) | Selección | `document.querySelectorAll("h2")` |
| `getElementById(id)` | Elemento con ese `id` (o `null`) | Selección | `document.getElementById("app")` |
| `getElementsByClassName` | `HTMLCollection` **viva**, sin `forEach` | Selección | `document.getElementsByClassName("item")` |
| **`NodeList` vs `Array`** | `NodeList`: tiene `forEach` y `for…of`, **no** `map`/`filter`; conviértelo con `Array.from()` o `[...]` | — | `Array.from(nodos).map(n => n.textContent)` |
| `textContent` | Lee/escribe **texto** (no interpreta HTML) — para texto | Contenido | `caja.textContent = "Hola <b>"` |
| `innerText` | Texto **tal como se muestra** | Contenido | `el.innerText` |
| `innerHTML` | Lee/escribe **HTML** (interpreta etiquetas): solo con datos de confianza (riesgo **XSS**) | Contenido | `caja.innerHTML = "<b>x</b>"` |
| `createElement` · `append` · `remove` | **Crear**, agregar y quitar elementos | Manipulación | `const li = document.createElement("li");` |
| `getAttribute` / `setAttribute` | Leer / escribir atributos | Manipulación | `el.setAttribute("alt", "texto")` |
| `classList` | `add`, `remove`, `toggle`, `contains` | Manipulación | `el.classList.add("activo")` |
| `style` · `dataset` | Estilo en línea · atributos `data-*` | Manipulación | `el.style.color = "red"` · `el.dataset.id` |

### 3.7 Arrays y strings

**🧩 Plantilla**

```js
const resultado = lista
  .filter((x) => condicion)       // selecciona
  .map((x) => transformacion)     // transforma
  .join("");                      // une en un string
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `push(x)` / `pop()` | **Agrega** / **quita** al final | Modifica el original | `lista.push("c")` |
| `sort(fn)` | **Ordena** (¡modifica!); copiar antes con `[...lista]` | Modifica el original | `[...lista].sort((a, b) => a - b)` |
| `map(fn)` | **Transforma** cada elemento → **nuevo array** | Devuelve array nuevo | `lista.map(x => x.toUpperCase())` |
| `filter(fn)` | **Conserva** los que cumplen la condición | Devuelve array nuevo | `nums.filter(n => n > 2)` |
| `slice(i, j)` | Copia una **porción** | Devuelve array nuevo | `lista.slice(0, 2)` |
| `find(fn)` | **Primer** elemento que cumple (o `undefined`) | Búsqueda | `nums.find(n => n > 2)` |
| `includes(x)` | ¿**Contiene** el valor? (en objetos compara **referencia**) | Búsqueda | `lista.includes("b")` |
| `indexOf(x)` | Posición (o `-1`) | Búsqueda | `lista.indexOf("b")` |
| `some(fn)` / `every(fn)` | ¿**Alguno** / **todos** cumplen? | Búsqueda | `nums.some(n => n > 2)` |
| `forEach(fn)` | **Ejecuta** algo por elemento (no devuelve nada) | Iteración | `lista.forEach(x => console.log(x))` |
| `reduce(fn, ini)` | **Acumula** en un solo valor | Iteración | `nums.reduce((a, n) => a + n, 0)` |
| `join(sep)` | **Une** elementos en un string | Conversión | `["a","b"].join(", ")` → `"a, b"` |
| `split(sep)` | **Divide** un string en array (inverso de `join`) | Conversión (string) | `"a, b".split(", ")` |
| `Array.from(x)` · `[...x]` | Convierte a **Array** real / copia | Conversión | `Array.from(nodos)` |
| `Set` | Colección **sin duplicados** | Estructura | `const s = new Set(); s.add(x); s.has(x);` |
| `toLowerCase()` / `toUpperCase()` | Minúsculas / mayúsculas | String | `"Hola".toLowerCase()` |
| `includes(sub)` · `startsWith` · `endsWith` | ¿Contiene / empieza / termina con…? | String | `"Rayuela".includes("yue")` |
| `trim()` · `slice()` · `replace()` · `padStart(n, c)` | Recortar · extraer · reemplazar · rellenar | String | `"5".padStart(2, "0")` → `"05"` |
| **Patrón `split → map → join`** | Transforma una lista de texto en HTML | Patrón | ``"a, b".split(", ").map(t => `<li>${t}</li>`).join("")`` |
| **Búsqueda sin mayúsculas** | Normaliza **ambos lados**; la cadena vacía `""` coincide con todo | Patrón | `t.toLowerCase().includes(q.toLowerCase())` |

### 3.8 Eventos

**🧩 Plantilla**

```js
objetivo.addEventListener("tipoDeEvento", (evento) => {
  // reacciona: cambia una variable, el DOM o el almacenamiento
}, { once: true });
```

```text
 usuario actúa ──▶ el navegador crea el evento ──▶ llama al callback registrado ──▶ cambia el estado
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `addEventListener(tipo, cb, opciones)` | **Registra** un manejador (listener) | Registro | `document.addEventListener("click", () => {})` |
| **Objeto evento** | Recibido por el callback: `evento.type`, `evento.target` | Evento | `(e) => console.log(e.target)` |
| **Opciones** | `{ once: true }` (una vez) · `{ passive: true }` · `{ capture: true }` | Registro | `{ once: true }` |
| `click` · `dblclick` · `mouseover` · `mouseout` · `mousemove` | Interacción con el **ratón** | Tipo: ratón | `"click"` |
| `keydown` · `keyup` | **Teclado** | Tipo: teclado | `"keydown"` |
| `input` · `change` · `submit` · `focus` · `blur` | **Formularios** (`input` = cada cambio) | Tipo: formularios | `campo.addEventListener("input", fn)` |
| `load` · `DOMContentLoaded` · `resize` · `scroll` · `scrollend` · `visibilitychange` | **Ventana / página** | Tipo: ventana | `window.addEventListener("scrollend", fn)` |
| `scroll` vs `scrollend` | `scroll`: **continuo**; `scrollend`: **una vez** al terminar (no se dispara si no cambió la posición) | — | `window.addEventListener("scrollend", fn)` |
| **Propagación** (*bubbling*) | El evento **sube** hasta `document`; un listener en `document` recibe clics de **todo** (delegación) | — | `document.addEventListener("click", …)` |
| `removeEventListener` | Quita el manejador (misma **referencia** de función) | Registro | `window.removeEventListener("scroll", fn)` |
| **Ejecutar una sola vez** | `{ once: true }` · `removeEventListener` · una **bandera** | Patrón | `let hecho = false; if (!hecho) {…}` |
| **Evento → callback → estado** | El callback modifica una variable capturada (closure) | Patrón | `let clics = 0; … clics = clics + 1;` |
| **Eventos de `chrome.*`** | Se registran con `addListener` | Extensiones | `chrome.storage.onChanged.addListener(fn)` |

### 3.9 Geometría y visibilidad

**🧩 Plantilla**

```js
const r = el.getBoundingClientRect();     // posición relativa al viewport
const completo = r.top >= 0 && r.bottom <= window.innerHeight;
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `getBoundingClientRect()` | Tamaño y posición **relativos al viewport** (cambian al hacer scroll) | Método | `el.getBoundingClientRect()` |
| `DOMRect` | Objeto devuelto: `x`, `y`, `width`, `height`, `top`, `right`, `bottom`, `left` (`ClientRect`: nombre antiguo, sin `x`/`y`) | Objeto | `r.top` · `r.bottom` |
| `window.innerHeight` / `scrollY` | Alto del viewport / cuánto se ha desplazado la página | Propiedad | `window.scrollY` |
| **Visible totalmente** | Dentro de la ventana de arriba a abajo | Fórmula | `r.top >= 0 && r.bottom <= innerHeight` |
| **Visible en parte** | Al menos una porción dentro | Fórmula | `r.top < innerHeight && r.bottom > 0` |
| `IntersectionObserver` | **Avisa** cuando un elemento entra o sale del viewport | API moderna | ``new IntersectionObserver((es) => es.forEach(e => e.isIntersecting), { threshold: 1.0 })`` |

### 3.10 Asincronía

**🧩 Plantilla**

```js
// 1. Callback
chrome.storage.local.get(["clave"], (resultado) => { /* … */ });

// 2. Promesa
fetchAlgo().then((r) => { /* … */ }).catch((e) => { /* … */ });

// 3. async / await
async function leer() {
  try { const { clave } = await chrome.storage.local.get("clave"); }
  catch (error) { console.error(error); }
}
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| **Asincronía** | Operaciones que **tardan** no bloquean: el resultado se procesa cuando llega | Concepto | lectura de almacenamiento, red |
| **Bucle de eventos** | Encola los callbacks y los ejecuta cuando el hilo está libre | Concepto | `A, C, B` en `log("A"); setTimeout(…B); log("C")` |
| **Callback** | Función que se ejecuta al terminar la tarea | Estilo 1 | `get(["k"], (r) => …)` |
| **Promesa** | Valor **futuro**: pendiente → cumplida (o rechazada); `.then` / `.catch` | Estilo 2 | `p.then(r => …).catch(e => …)` |
| `async` / `await` | Código asíncrono con aspecto **secuencial**; `await` solo dentro de `async` | Estilo 3 | `const r = await promesa;` |
| `try { } catch (e) { }` | Captura errores | Control de errores | `catch (error) { console.error(error); }` |
| **Callback hell** | Anidar muchos callbacks: difícil de leer | Desventaja | pirámide de `)` |

### 3.11 JSON

**🧩 Plantilla**

```json
{
  "clave": "valor",
  "numero": 1,
  "lista": ["a", "b"],
  "objeto": { "x": true }
}
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| **JSON** | **Formato de datos** (texto): describe, no ejecuta | Formato | `manifest.json` |
| **JS** | **Código ejecutable** con lógica; admite comentarios | Código | `content.js` |
| **Reglas de JSON** | Claves y textos con **comillas dobles**; **sin comas finales**, sin comentarios, sin funciones ni `undefined` | Sintaxis | `{ "a": 1 }` |
| **Tipos de JSON** | string, number, boolean, null, array, objeto | Sintaxis | `[1, "a", null]` |
| `JSON.parse(texto)` | Texto → **objeto** JS | Método | `JSON.parse('{"a":1}')` |
| `JSON.stringify(obj)` | Objeto → **texto** JSON | Método | `JSON.stringify({ a: 1 })` |
| **Error típico** | `Unexpected token` por JSON inválido | Error | coma final, comillas simples |

### 3.12 JavaScript en extensiones de Chrome (contexto)

> Contexto de la guía de JavaScript: aquí aparecen los patrones **declarativos (JSON)** y **basados en callbacks** de las APIs `chrome.*`.

**🧩 Plantilla**

```json
{
  "manifest_version": 3,
  "name": "Nombre",
  "version": "1.0",
  "permissions": ["storage"],
  "action": { "default_popup": "popup.html" },
  "content_scripts": [
    { "matches": ["https://*.sitio.org/ruta/*"], "js": ["content.js"], "run_at": "document_idle" }
  ]
}
```

```js
chrome.storage.local.set({ clave: valor });
chrome.storage.local.get(["clave"], (r) => { /* r.clave */ });
chrome.storage.onChanged.addListener((cambios, area) => { /* cambios.clave.newValue */ });
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `manifest.json` | **Identifica** la carpeta como extensión y declara todo; en la raíz | Manifiesto | `"manifest_version": 3` |
| `manifest_version` · `name` · `version` | Campos **obligatorios** | Manifiesto | `"version": "1.0"` |
| `permissions` | **Permisos de API** solicitados (mínimo privilegio) | Manifiesto | `"permissions": ["storage"]` |
| `action` | Botón de la barra: `default_title`, `default_popup` | Manifiesto | `"action": { "default_popup": "popup.html" }` |
| `content_scripts` | Scripts **inyectados** en páginas que coincidan | Manifiesto | `{ "matches": […], "js": […] }` |
| **Patrón de coincidencia** | `esquema://host/ruta` | `matches` | `https://*.wikipedia.org/wiki/*` |
| `run_at` | **Cuándo** se inyecta: `document_start` · `document_end` · `document_idle` (por defecto) | `content_scripts` | `"run_at": "document_idle"` |
| **Content script** | JS dentro de la **página**; comparte el DOM pero **no** las variables (mundo aislado) | Componente | `content.js` |
| **Popup** | Ventana emergente de la extensión (HTML + CSS + JS) | Componente | `popup.html`, `popup.js` |
| **Service worker** | Segundo plano, bajo demanda | Componente | `background.js` |
| `chrome.storage.local` / `sync` / `session` | Almacenamiento **persistente** local / sincronizado / solo de sesión | Área | `chrome.storage.local.set({ a: 1 })` |
| `set` · `get` · `remove` · `clear` | Guardar · leer (devuelve objeto) · borrar · vaciar | Método | `chrome.storage.local.get(["a"], cb)` |
| `onChanged.addListener(cb)` | **Avisa** de cambios: `cambios.clave.oldValue / newValue` | Evento | `(cambios, area) => { … }` |
| **Qué se puede guardar** | Datos **serializables**; **no** elementos del DOM (convertir con `map(el => el.textContent)`) | — | `chrome.storage.local.set({ lista: textos })` |
| `chrome.storage` vs `localStorage` | Asíncrono, objetos, compartido por la extensión vs síncrono, solo strings, por origen | — | — |
| **Ciclo de desarrollo** | `chrome://extensions` → Modo desarrollador → Cargar descomprimida; **recargar la extensión y la página** tras cambios | — | — |

### 3.13 Depuración y errores típicos

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `console.log(...)` | Mensaje general (acepta varios argumentos) | Método de `console` | `console.log("Título:", document.title)` |
| `console.warn` / `console.error` | Advertencia / error | Método de `console` | `console.error("Fallo:", e)` |
| `console.table` / `console.dir` | Tabla / inspección de un objeto | Método de `console` | `console.table(lista)` |
| `debugger;` | Punto de interrupción en el código | Depuración | `debugger;` |
| `TypeError: Cannot read properties of null` | `querySelector` no encontró nada | Error | `null.textContent` |
| `ReferenceError: x is not defined` | Variable no declarada o fuera de alcance | Error | `console.log(x)` |
| `chrome.storage` es `undefined` | Falta el permiso `"storage"` | Error | manifiesto sin `permissions` |
| Sin mensajes en la consola | URL no coincide con `matches` o no se recargó | Error | — |

---

## 4. TypeScript

### 4.1 Qué es y flujo de trabajo

**🧩 Plantilla**

```text
 archivo .ts ──┬──▶ comprobación de tipos ──▶ errores en el editor / al compilar
               └──▶ eliminación de tipos ──▶ archivo .js ──▶ navegador / Node.js
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| **TypeScript** | **JavaScript + tipos estáticos** ("JavaScript with syntax for types") | Lenguaje | `let n: number = 5;` |
| **Superconjunto** | Todo JS válido es TS válido; TS **añade** tipos, interfaces, genéricos, uniones | — | un `.js` renombrado a `.ts` |
| **Borrado de tipos** | Los tipos **no existen al ejecutar**: una `interface` no es un valor; TS no valida datos externos | — | `interface A {}` desaparece al compilar |
| **Tipado estático vs dinámico** | Errores de tipo **al escribir/compilar** (TS) vs **al ejecutar** (JS) | — | `libro.pagnas` → error en TS, `undefined` en JS |
| `tsc` | Compilador: **comprueba** tipos (y puede generar JS) | Herramienta | `tsc --noEmit` |
| **Empaquetador (Vite)** | Transforma `.ts` a JS **sin comprobar tipos** (lo hace el editor/`tsc`) | Herramienta | `vite` |
| **Ventajas** | Detecta errores temprano, autocompletado, documentación viva, refactorización segura | — | — |

### 4.2 Anotaciones, inferencia y tipos básicos

**🧩 Plantilla**

```ts
let nombre: tipo = valor;                       // anotación de variable
function nombre(param: tipo): tipoRetorno { }   // anotación de función
const lista: tipo[] = [];                       // arreglo tipado
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `string` · `number` · `boolean` | Tipos **primitivos** (un solo tipo `number`) | Primitivo | `let edad: number = 20;` |
| `T[]` / `Array<T>` | **Arreglo** de elementos de tipo `T` | Colección | `let notas: number[] = [8, 9];` |
| `null` · `undefined` | Ausencia de valor | Primitivo | `let x: string \| null = null;` |
| `any` | **Desactiva** la comprobación: evitar | Especial | `let a: any = "x"; a.noExiste();` ✅ compila |
| `unknown` | Como `any`, pero **obliga a comprobar** antes de usar | Especial | `if (typeof u === "string") u.toUpperCase();` |
| `void` | La función **no devuelve valor** | Especial | `(): void => { … }` |
| `never` | Nunca ocurre (lanza error o no termina) | Especial | `function fallar(): never { throw … }` |
| **Inferencia** | TS **deduce** el tipo del valor inicial | — | `let cantidad = 0;` → `number` |
| `let` vs `const` (inferencia) | `let x = "a"` → `string`; `const x = "a"` → tipo **literal** `"a"` | — | `const x = 0` → `0` |
| **Cuándo anotar** | **Fronteras**: parámetros, retornos exportados, variables sin valor inicial, arrays vacíos | Regla práctica | `const lista: string[] = [];` |

### 4.3 Tipos literales, uniones y narrowing

**🧩 Plantilla**

```ts
type Alias = "opcionA" | "opcionB" | "opcionC";   // unión de literales
let valor: string | number;                       // unión de tipos
let opcional: string | undefined;
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| **Tipo literal** | Admite **un valor exacto** | Tipo | `let estado: "activo";` |
| **Unión** `\|` | Uno de **varios** tipos; con literales define un **conjunto cerrado** | Tipo | `type Genero = 'rock' \| 'pop' \| 'salsa';` |
| `T \| undefined` / `T \| null` | Valor que **puede faltar** (resultado de `find`, `getElementById`) | Unión | `let r: Libro \| undefined;` |
| **Narrowing** (estrechamiento) | TS **reduce** el tipo según tus comprobaciones | Técnica | `if (typeof id === "string") { id.toUpperCase(); }` |
| `typeof x === "…"` | Estrecha a un primitivo | Comprobación | `typeof id === "number"` |
| `if (x)` | Descarta `null`, `undefined`, `0`, `""` | Comprobación | `if (el) { el.innerHTML = ""; }` |
| `instanceof` | Estrecha a una **clase** | Comprobación | `el instanceof HTMLInputElement` |
| `"prop" in x` | Estrecha a tipos que **tienen** esa propiedad | Comprobación | `"titulo" in x` |
| `as const` | Deriva un tipo de una **lista de valores** | Técnica | `const C = ["a","b"] as const; type T = (typeof C)[number];` |
| **Unión literal vs `enum`** | La unión **se borra** al compilar (preferida); `enum` genera código JS | — | `type E = "a" \| "b"` |

### 4.4 Interfaces y alias de tipos

**🧩 Plantilla**

```ts
interface Nombre {
  propiedad: tipo;
  opcional?: tipo;          // puede faltar (tipo | undefined)
  readonly fija: tipo;      // solo lectura
}
interface Hijo extends Nombre { extra: tipo; }
type Alias = tipo;
const dato: Nombre = { propiedad: …, fija: … };
const lista: Nombre[] = [ … ];
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `interface` | Describe la **forma** (propiedades y tipos) de un objeto: un **contrato** | Declaración | `interface Cancion { id: number; titulo: string; }` |
| **Propiedad opcional** `?` | Puede **no estar**; su tipo real es `T \| undefined` (hay que manejarlo) | Propiedad | `album?: string;` · `c.album ?? "Sin álbum"` |
| `readonly` | **No se puede reasignar** | Propiedad | `readonly isbn: string;` |
| `extends` | **Hereda** de otra interfaz | Declaración | `interface LibroDigital extends Libro { formato: string }` |
| **Tipado estructural** | Importa la **forma**, no el nombre; no hace falta "implementar" | — | un objeto con las mismas propiedades es compatible |
| **Control de exceso** | En un objeto **literal**, propiedades no declaradas dan error | — | `{ id: 1, tipo: "x" }` ❌ |
| `type` (alias) | Nombre para **cualquier** tipo: uniones, primitivos, tuplas | Declaración | `type Genero = 'rock' \| 'pop';` |
| **`interface` vs `type`** | `interface`: objetos, `extends`, se puede reabrir · `type`: uniones, alias, `&` | — | formas de objeto → `interface`; uniones → `type` |
| `Interfaz[]` | **Arreglo** de objetos validados contra la interfaz | Colección | `export const canciones: Cancion[] = [ … ];` |

### 4.5 Funciones tipadas

**🧩 Plantilla**

```ts
function sumar(a: number, b: number): number { return a + b; }
const restar = (a: number, b: number): number => a - b;
export const filtrar = (lista: Item[], q: string): Item[] => { … };
function f(obligatorio: string, opcional?: string, porDefecto = 2): void { }
type Criterio = (item: Item) => boolean;           // tipo de una función
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| **Parámetros y retorno tipados** | Declaran qué recibe y qué devuelve | Sintaxis | `(canciones: Cancion[]): void => { … }` |
| `: void` | No devuelve valor (solo produce efectos, como pintar la página) | Retorno | `const mostrar = (l: Item[]): void => { … }` |
| **Parámetro opcional / por defecto** | `?` o `= valor` | Parámetro | `(saludo?: string)` · `(exp = 2)` |
| **Tipo de función** | `(param: T) => R` | Tipo | `(libro: Libro) => boolean` |
| **Alias de función** | Nombre para un tipo de función | Tipo | `type Criterio = (l: Libro) => boolean;` |
| **Callback tipado** | Función como parámetro | Patrón | `criterio: (l: Libro) => boolean` |
| **Tipado contextual** | Al pasar una flecha, TS **infiere** sus parámetros | — | `lista.filter((l) => l.paginas > 300)` |
| **Función exportada** | Anotar el **retorno** hace explícito el contrato | Buena práctica | `export const f = (…): Tipo => …` |

### 4.6 Arrays y strings con tipos

**🧩 Plantilla**

```ts
const resultado: Tipo[] = lista
  .filter((x) => condicion)        // Tipo[]
  .map((x) => transformacion);     // OtroTipo[]
const uno: Tipo | undefined = lista.find((x) => condicion);
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `map(fn)` | Transforma → **nuevo array** (`U[]`) | Devuelve array | `libros.map(l => l.titulo)` → `string[]` |
| `filter(fn)` | Selecciona → **nuevo array** (`T[]`); por eso una función de filtrado recibe y devuelve `T[]` | Devuelve array | `libros.filter(l => l.paginas > 300)` |
| `find(fn)` | Devuelve `T \| undefined` (con `strict` hay que manejarlo) | Búsqueda | `libros.find(l => l.id === 1)?.titulo` |
| `some` / `every` / `includes` | Devuelven `boolean` | Búsqueda | `lista.includes(x)` |
| `reduce(fn, ini)` | Acumula en un valor | Iteración | `libros.reduce((t, l) => t + l.paginas, 0)` |
| `join(sep)` | Devuelve `string` | Conversión | ``lista.map(l => `<li>${l.titulo}</li>`).join("")`` |
| `sort(fn)` | **Modifica** el original; copiar con `[...lista]` | Muta | `[...lista].sort((a, b) => a.paginas - b.paginas)` |
| `localeCompare` | Ordena **texto** correctamente | String | `a.titulo.localeCompare(b.titulo)` |
| **Inmutabilidad** | Preferir copias (`map`, `filter`, `slice`, `[...]`); `readonly T[]` impide `push` | Buena práctica | `readonly Libro[]` |
| **`map` + `join('')`** | Sin `join`, el array se une **con comas** al mostrarse | Patrón | `["<li>A</li>","<li>B</li>"].join("")` |
| **Búsqueda insensible a mayúsculas** | `toLowerCase()` en ambos lados + `includes`; `""` coincide con todo (por eso al borrar el texto vuelve la lista completa) | Patrón | `l.titulo.toLowerCase().includes(q.toLowerCase())` |
| **Buscar en varios campos** | Condiciones con `\|\|` o `some` | Patrón | `l.titulo.includes(q) \|\| l.autor.includes(q)` |
| `normalize("NFD")` | Ignorar tildes | String | ``s.normalize("NFD").replace(/\p{Diacritic}/gu, "")`` |

### 4.7 Módulos

**🧩 Plantilla**

```ts
// tipos.ts
export type Alias = "a" | "b";
export interface Item { id: number; }

// datos.ts
import type { Item } from "./tipos";          // solo tipos
export const items: Item[] = [ … ];

// main.ts
import { items } from "./datos";              // valores
import "./style.css";                         // efecto lateral (lo resuelve Vite)
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| **Módulo** | Archivo con `import`/`export`; lo no exportado queda **privado** | Concepto | `tipos.ts` |
| `export` | Hace **visible** una declaración fuera del archivo | Exportar | `export const items = […];` |
| `export default` | Un elemento **principal** por archivo (`import x from …`, sin llaves) | Exportar | `export default función;` |
| `import { x }` | Trae **valores** por nombre (permanece en el JS) | Importar | `import { filtrarCanciones } from './utilidades';` |
| `import type { T }` | Trae **solo tipos**; **se borra** al compilar (exigido con `verbatimModuleSyntax`) | Importar | `import type { Cancion } from './tipos';` |
| `import "./archivo"` | Importación de **efecto lateral** | Importar | `import './style.css';` |
| **Ruta relativa** | `./` archivo actual · con empaquetador **sin extensión** | — | `'./tipos'` |
| **Script vs módulo** | Sin `import`/`export` el archivo es script (ámbito global) | — | — |
| **Modularidad** | Encapsulamiento, reutilización, dependencias explícitas, pruebas | — | — |

### 4.8 DOM tipado, null y aserciones

**🧩 Plantilla**

```ts
const el = document.getElementById("id");                      // HTMLElement | null
if (el) { el.innerHTML = "…"; }                                // ✅ verificación (segura)

const campo = document.getElementById("buscar") as HTMLInputElement;   // aserción
campo.addEventListener("input", () => { const texto = campo.value; });
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `HTMLElement` | Cualquier elemento HTML (`innerHTML`, `textContent`, `style`, `classList`) | Tipo del DOM | `const app: HTMLElement` |
| `HTMLInputElement` | Un `<input>`: añade **`value`**, `type`, `checked`, `placeholder` | Tipo del DOM | `campo.value` |
| `getElementById` | Devuelve **`HTMLElement \| null`** | Método | `document.getElementById("app")` |
| `strictNullChecks` | Impide usar un valor posiblemente `null` sin comprobarlo | Aviso | *"Object is possibly 'null'"* |
| **Verificación** `if (el)` | **Comprueba en ejecución** y estrecha el tipo: la más segura | Resolver `null` | `if (el) { … }` |
| **Aserción** `as T` | Le dice al compilador *"confía en mí"*; **no comprueba** nada (si era `null`, falla al ejecutar) | Resolver `null` | `… as HTMLElement` |
| **No nulo** `!` | Como `as`, abreviado | Resolver `null` | `document.getElementById("x")!` |
| `?.` | Detiene la operación si es `null` | Resolver `null` | `el?.classList.add("x")` |
| **Lanzar error** | Falla **temprano** con mensaje claro | Resolver `null` | `if (!el) throw new Error("Falta #app");` |
| `querySelector<T>()` | Indica el tipo con un **genérico**; sigue siendo `T \| null` | Método | `document.querySelector<HTMLInputElement>("#buscar")` |
| `instanceof` | Verifica y estrecha a la vez | Resolver `null` | `if (el instanceof HTMLInputElement) { el.value }` |
| `addEventListener("input", …)` | TS conoce los **nombres de eventos**; `e.target` es `EventTarget \| null` | Evento | leer `.value` desde la variable del input |

### 4.9 Patrón de render y organización

**🧩 Plantilla**

```ts
const render = (lista: Item[]): void => {
  const cont = document.getElementById("lista");
  if (cont) {
    cont.innerHTML = lista.map((i) => `<article>${i.titulo}</article>`).join("");
  }
};

render(todos);                                               // pintado inicial
campo.addEventListener("input", () => render(filtrar(todos, campo.value)));
```

```text
 tipos.ts ──▶ datos.ts ──▶ utilidades.ts (lógica pura) ──▶ main.ts (DOM + eventos) ──▶ página
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| **Función de render** | Recibe la lista **a mostrar** y reemplaza el contenido del contenedor | Patrón | `render(lista: Item[]): void` |
| **Datos intactos** | Siempre se filtra sobre la lista **original**, nunca sobre la ya filtrada | Patrón | `render(filtrar(todos, texto))` |
| **Sin resultados** | Si `lista.length === 0`, mostrar un mensaje | Patrón | `if (lista.length === 0) { … }` |
| **Función pura** | Mismas entradas → misma salida; no toca el DOM ni modifica argumentos | Concepto | `filtrar(lista, q): Item[]` |
| `tipos.ts` | **Contratos**: interfaces y tipos literales | Módulo | `export interface Cancion {…}` |
| `datos.ts` | **Datos** iniciales | Módulo | `export const canciones: Cancion[] = […]` |
| `utilidades.ts` | **Lógica pura** (filtrar, ordenar, formatear); testeable sin navegador | Módulo | `export const filtrarCanciones = …` |
| `main.ts` | **Presentación e interacción** (DOM, eventos) | Módulo | `appDiv.innerHTML = …` |
| **Seguridad con `innerHTML`** | Con datos de fuera usar `textContent` o `createElement` | Precaución | `li.textContent = dato;` |

### 4.10 Herramientas avanzadas

**🧩 Plantilla**

```ts
function primero<T>(lista: T[]): T | undefined { return lista[0]; }   // genérico
const conteo: Record<Categoria, number> = { … };                     // utility type
const esLibro = (x: unknown): x is Libro => … ;                      // guarda de tipo
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| **Genérico** `<T>` | Código reutilizable que **conserva el tipo** | Genéricos | `Array<T>` · `Promise<T>` · `function f<T>(x: T): T` |
| `Partial<T>` / `Required<T>` | Todas las propiedades **opcionales** / **obligatorias** | Utility type | `Partial<Libro>` |
| `Readonly<T>` | Todas **solo lectura** | Utility type | `Readonly<Libro>` |
| `Pick<T, K>` / `Omit<T, K>` | **Selecciona** / **excluye** propiedades | Utility type | `Pick<Libro, "id" \| "titulo">` |
| `Record<K, V>` | Objeto con claves `K` y valores `V` | Utility type | `Record<Categoria, number>` |
| **Guarda de tipo** `x is T` | Si devuelve `true`, `x` es `T` (validar datos externos) | Función | `(x: unknown): x is Libro => …` |
| `keyof T` | **Unión de las claves** de un tipo | Operador de tipos | `keyof Libro` |
| `typeof` (en tipos) | Tipo **de una variable** | Operador de tipos | `type T = typeof biblioteca` |
| `T[K]` | Tipo de una propiedad | Operador de tipos | `Libro["paginas"]` → `number` |
| `A & B` | **Intersección** de tipos | Operador de tipos | `type C = A & B` |
| `catch (e)` | Con `strict`, `e` es `unknown` | Errores | `if (e instanceof Error) e.message` |

### 4.11 Configuración del proyecto TS

**🧩 Plantilla**

```json
{
  "compilerOptions": {
    "target": "ES2020",
    "module": "ESNext",
    "moduleResolution": "bundler",
    "lib": ["ES2020", "DOM", "DOM.Iterable"],
    "strict": true,
    "noEmit": true,
    "skipLibCheck": true
  },
  "include": ["src"]
}
```

```text
proyecto/
├── index.html        ← <div id="app"> + <script type="module" src="/src/main.ts">
├── package.json      ← scripts (dev, build, preview) y dependencias
├── tsconfig.json     ← configuración del compilador
└── src/  main.ts · style.css · tipos.ts · …
```

| Concepto / Item | Función | Categoría | Ejemplo |
|---|---|---|---|
| `target` | **Versión de JS** a la que se compila | `compilerOptions` | `"target": "ES2020"` |
| `module` · `moduleResolution` | Sistema de módulos · cómo se **buscan** los archivos importados | `compilerOptions` | `"ESNext"` · `"bundler"` |
| `lib` | **Bibliotecas de tipos** (`DOM` aporta `document`, `HTMLElement`) | `compilerOptions` | `["ES2020", "DOM"]` |
| `strict` | Activa el **conjunto de comprobaciones estrictas** (TS 6.0 lo trae en `true` por defecto; antes `false`) | `compilerOptions` | `"strict": true` |
| `noEmit` · `skipLibCheck` · `include` | No generar `.js` · omitir revisión de librerías · carpetas del proyecto | `compilerOptions` / raíz | `"include": ["src"]` |
| `strictNullChecks` | `null`/`undefined` no se asignan a otros tipos sin declararlo | Incluida en `strict` | `string \| null` |
| `noImplicitAny` | Prohíbe `any` **implícito** (parámetros sin tipo) | Incluida en `strict` | `(x) => …` ❌ |
| `strictFunctionTypes` · `strictBindCallApply` · `noImplicitThis` · `alwaysStrict` | Comprobaciones estrictas de funciones, `this` y modo estricto | Incluidas en `strict` | — |
| `strictPropertyInitialization` · `useUnknownInCatchVariables` | Propiedades de clase inicializadas · `catch` con `unknown` | Incluidas en `strict` | — |
| `index.html` · `src/main.ts` · `src/style.css` | Punto de entrada HTML · entrada del código · estilos | Archivo | `<script type="module" src="/src/main.ts">` |
| `package.json` | **Manifiesto**: `scripts` (`dev`, `build` = `tsc && vite build`, `preview`), `dependencies`, `devDependencies` | Archivo | `npm run dev` |

| Error del compilador (aproximado) | Causa habitual |
|---|---|
| `Type 'X' is not assignable to type 'Y'` (TS2322) | Valor de **tipo incompatible** (p. ej. `"jazz"` fuera de la unión) |
| `Property 'x' does not exist on type 'Y'` (TS2339) | Propiedad **mal escrita** o inexistente; o falta estrechar (`value` en `HTMLElement`) |
| `Parameter 'x' implicitly has an 'any' type` (TS7006) | Falta **anotar** un parámetro |
| `'x' is possibly 'null'` / `Object is possibly 'null'` | Se usa un valor que **puede ser `null`** sin comprobar |
| `Cannot find module './x'` (TS2307) | **Ruta de importación** incorrecta |
| `'X' is a type and must be imported using a type-only import` | Falta **`import type`** |
| `Property 'x' is missing in type …` | Falta una propiedad **obligatoria** de la interfaz |

---

## 5. Si ves esto → es esto

> Tabla de **reconocimiento rápido**: identifica la estructura por su "huella" sintáctica.

| Si ves… | Es… | Lenguaje | Qué hace |
|---|---|---|---|
| `<x atributo="v">…</x>` | **Elemento** con atributos | HTML | Marca contenido con significado |
| `<img …>` · `<br>` · `<input …>` | **Elemento vacío** (sin cierre) | HTML | Inserta algo sin contenido interior |
| `<!DOCTYPE html>` | Declaración de documento | HTML | Activa el modo estándar |
| `<header>` `<nav>` `<main>` `<section>` `<article>` `<aside>` `<footer>` | **Etiquetas semánticas** | HTML | Dan significado a las zonas |
| `<a href="#x">` ↔ `id="x"` | **Ancla interna** | HTML | Salta dentro del mismo documento |
| `<label for="x">` ↔ `id="x"` | **Etiqueta de campo** | HTML | Asocia texto y control |
| `<link rel="stylesheet" href="…">` | **Vinculación de CSS** | HTML | Conecta la hoja de estilos |
| `selector { propiedad: valor; }` | **Regla CSS** | CSS | Aplica estilo a los elementos elegidos |
| `.nombre` · `#nombre` · `a b` · `a, b` · `a:hover` | Selector de **clase** · **id** · **descendiente** · **agrupado** · **pseudo-clase** | CSS | Elige a qué se aplica |
| `* { box-sizing: border-box; }` | **Reinicio del modelo de caja** | CSS | El `width` incluye padding y borde |
| `display: flex` + `justify-content` / `align-items` / `gap` | **Contenedor Flexbox** | CSS | Distribuye en un eje |
| `flex: 1` · `flex: 0 0 260px` | **Elemento flex** elástico · fijo | CSS | Controla crecimiento y tamaño |
| `display: grid` + `grid-template-columns: repeat(3, 1fr)` | **Contenedor Grid** | CSS | Filas y columnas |
| `grid-template-areas: "a b"` + `grid-area: a` | **Áreas con nombre** | CSS | Dibuja el esquema |
| `@media (max-width: 768px) { … }` | **Media query** | CSS | Reglas solo en pantallas pequeñas |
| `:root { --x: v; }` + `var(--x)` | **Variable CSS** | CSS | Define y reutiliza un valor |
| `const` · `let` | **Declaración** de variable | JS / TS | Crea variables |
| `(a, b) => a + b` | **Función flecha** | JS / TS | Función compacta |
| `(() => { … })();` | **IIFE** | JS / TS | Ejecuta código aislado al instante |
| `` `texto ${valor}` `` | **Plantilla de texto** | JS / TS | Inserta expresiones en un string |
| `a?.b ?? "x"` | **Encadenamiento opcional** + **fusión nula** | JS / TS | Evita errores con `null` y da un respaldo |
| `document.querySelector("css")` | **Selección** de un elemento | JS / TS | Devuelve `Element \| null` |
| `lista.filter(…).map(…).join("")` | **Cadena de métodos** de array | JS / TS | Selecciona, transforma y une |
| `el.addEventListener("evento", (e) => {…})` | **Listener** de evento | JS / TS | Reacciona a una acción |
| `.then(…).catch(…)` · `async` / `await` | **Promesa** · código asíncrono | JS / TS | Maneja tareas que tardan |
| `{ "clave": "valor" }` (comillas dobles, sin comentarios) | **JSON** | JSON | Describe datos |
| `chrome.storage.local.set / get` | **API de almacenamiento** de extensión | JS (extensión) | Guarda y lee datos persistentes |
| `let x: number` · `(a: string): void` | **Anotación de tipo** | TS | Declara tipos |
| `type A = "x" \| "y"` | **Unión de literales** | TS | Conjunto cerrado de valores |
| `interface A { p: tipo; q?: tipo }` | **Interfaz** (con propiedad opcional) | TS | Describe la forma de un objeto |
| `Item[]` · `Array<Item>` | **Arreglo tipado** | TS | Lista de objetos `Item` |
| `<T>` · `Partial<T>` · `Record<K, V>` | **Genérico** · **utility types** | TS | Tipos reutilizables |
| `export …` · `import { x } from "./y"` · `import type { T }` | **Módulos** · importación de **solo tipos** | TS | Comparte código entre archivos |
| `as HTMLInputElement` · `!` | **Aserción** de tipo / no nulo | TS | Afirma un tipo (sin comprobar) |
| `if (el) { … }` | **Verificación** (narrowing) | TS | Estrecha el tipo de forma segura |
| `"strict": true` en `tsconfig.json` | **Modo estricto** | TS | Activa comprobaciones rigurosas |
