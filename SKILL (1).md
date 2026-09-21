---
name: web-corporativa-desatascos-laravel
description: >
  Genera desde cero (o completa) una web corporativa en Laravel para una empresa de
  servicios de desatascos / fontanería de urgencia / saneamiento, con panel de
  administración (Filament) totalmente editable y "white-label" (marca, textos,
  colores, servicios, zonas y datos legales configurables, con datos de ejemplo de
  "Desatascos EM" precargados por defecto), arquitectura completa de páginas para
  SEO local (home, servicios, zonas de servicio, blog, legal, contacto/presupuesto),
  jerarquía de encabezados H1-H6 estrictamente correcta, capa técnica de SEO
  (metadatos, schema.org, sitemap.xml, robots.txt) orientada a posicionar en Google
  para "desatascos" y variantes locales, y animaciones de scroll modernas
  (GSAP + ScrollTrigger) con guion de venta pensado para que el visitante llame por
  teléfono ante una urgencia. Usa esta skill siempre que el usuario pida crear,
  planificar, ampliar o auditar una web de desatascos, fontanería, saneamiento,
  alcantarillado, limpieza de fosas sépticas o cualquier negocio local de urgencias
  del hogar en Laravel, o cuando pida SEO local para ese tipo de negocio, un panel
  admin editable para una web de servicios, o animaciones de scroll orientadas a
  conversión telefónica.
---

# Web corporativa de Desatascos en Laravel — Skill completa

## 1. Qué construye esta skill

Una web corporativa completa, en **Laravel**, para una empresa de **servicios de
desatascos** (tuberías, WC, fregaderos, bajantes, arquetas, alcantarillado, fosas
sépticas, videoinspección, detección de fugas, urgencias 24h), con:

1. **Panel de administración** (Filament) desde el que se edita el 100% del
   contenido, la marca, los colores/diseño, los servicios, las zonas geográficas,
   el blog, las opiniones, las FAQ, los textos legales y los leads recibidos —
   sin tocar código. La web sale de fábrica con los datos de ejemplo de la empresa
   **"Desatascos EM"**, pero está diseñada para poder reutilizarse con cualquier
   otra empresa del sector solo cambiando esos datos desde el admin.
2. **Arquitectura de páginas orientada a SEO local**: cada intención de búsqueda
   relevante ("desatascos [ciudad]", "desatascos urgentes", "desatasco de
   tuberías", "fontanero desatascos 24 horas"...) tiene una página propia,
   indexable y enlazada internamente.
3. **Jerarquía de encabezados perfecta** (1 solo `<h1>` por página, H2/H3/H4 en
   cascada sin saltos) en todas las plantillas.
4. **Animaciones de scroll de última generación** (GSAP + ScrollTrigger, 100%
   gratis desde 2025 incluido uso comercial) con un guion escena a escena pensado
   para generar urgencia y terminar en una llamada de teléfono.
5. **Cumplimiento legal español** (LSSI-CE, RGPD/LOPDGDD, guía de cookies AEPD
   vigente) con aviso legal, política de privacidad, política de cookies y banner
   de consentimiento conformes.
6. **Zona de servicio real** de referencia: **Cunit (Baix Penedès, Tarragona) y
   alrededores** — Calafell, Segur de Calafell, Cubelles, El Vendrell, Coma-ruga,
   Bellvei, Banyeres del Penedès, L'Arboç, Sant Jaume dels Domenys, Santa Oliva,
   Albinyana, Vilanova i la Geltrú, Sitges — usada como datos de ejemplo, pero el
   modelo de "Zona de servicio" es una tabla editable: cualquier empresa puede
   sustituir estas poblaciones por las suyas.

## 2. Principio rector: CERO contenido "hardcodeado"

Nada de lo que vea el usuario final puede estar escrito a fuego en un archivo
Blade: ni el nombre de la empresa, ni el teléfono, ni los colores, ni los
servicios, ni las poblaciones. Todo debe salir de la base de datos y ser editable
desde `/admin`. Las vistas Blade son siempre **plantillas**; el contenido vive en
modelos Eloquent. Esta es la diferencia entre "una web para Desatascos EM" y "una
plataforma de webs de desatascos que hoy usa Desatascos EM como demo" — es lo
segundo lo que hay que construir.

## 3. Stack técnico recomendado (verificado, 2026)

| Capa | Elección recomendada | Motivo |
|---|---|---|
| Framework | Laravel 12 o 13 (PHP 8.3+) | Última versión estable en 2026, sin cambios drásticos entre ambas |
| Admin panel | **Filament** (última versión estable v4/v5) | Estándar de facto en Laravel para paneles editoriales tipo TALL, gratuito y con Form Builder muy adecuado para "settings" de marca/tema |
| Frontend | Blade + Tailwind CSS + Alpine.js (ya vienen con Laravel) | Cero dependencias extra, ideal para SSR y SEO |
| Animaciones scroll | **GSAP + ScrollTrigger** (npm `gsap`) + **Lenis** (smooth scroll) | Desde 2025 GSAP es 100% gratis, incluido ScrollTrigger, SplitText y el resto de plugins antes "Club GreenSock", incluso para uso comercial |
| SEO técnico | `spatie/laravel-sitemap`, `spatie/laravel-sluggable`, `ralphjsmit/laravel-seo` (o `artesaos/seotools`), `spatie/schemaorg` | Sitemap automático, slugs, metadatos y JSON-LD sin reinventar la rueda |
| Media | `spatie/laravel-medialibrary` + conversión a WebP/AVIF | Imágenes ligeras = mejor Core Web Vitals = mejor SEO |
| Formularios | `spatie/laravel-honeypot` + Google reCAPTCHA v3 (opcional) | Anti-spam en el formulario de presupuesto/contacto sin fricción para el usuario |
| Base de datos | MySQL/MariaDB | Estándar, compatible con cualquier hosting Laravel |

Todos los comandos de instalación exactos están en
`references/08-stack-tecnico-paquetes.md`.

## 4. Orden de ejecución recomendado

1. Instala el stack base y monta el panel Filament en `/admin`
   → `references/08-stack-tecnico-paquetes.md`
2. Diseña y migra el modelo de datos (Service, ServiceArea, Testimonial, Post,
   Faq, Lead, CompanySetting, LegalPage, Redirect)
   → `references/06-modelo-datos-laravel.md`
3. Construye los recursos del panel de administración sobre ese modelo,
   incluido el "Theme Customizer" (colores/marca vía CSS variables)
   → `references/05-panel-administracion.md`
4. Ejecuta el seeder de datos de ejemplo de **Desatascos EM**
   → `assets/seed-data-desatascos-em.md`
5. Construye el mapa completo de páginas públicas y sus rutas
   → `references/01-sitemap-arquitectura.md`
6. Aplica en cada plantilla la jerarquía de encabezados obligatoria
   → `references/03-estructura-encabezados-hn.md`
7. Implementa la capa SEO (keywords, metadatos, enlazado interno, schema.org,
   sitemap.xml, robots.txt)
   → `references/02-seo-estrategia-keywords.md`
8. Maqueta el home (y páginas clave) siguiendo el guion de animaciones de scroll
   escena a escena, con el copy de venta orientado a llamada telefónica
   → `references/04-guion-animaciones-scroll.md`
9. Redacta e inserta las 3 páginas legales + banner de cookies conforme
   → `references/07-legal-cumplimiento.md`
10. Pasa el checklist de lanzamiento SEO técnico antes de dar nada por
    terminado → `references/09-checklist-seo-tecnico-lanzamiento.md`

## 5. Reglas de oro (no negociables)

- [ ] Exactamente **1** `<h1>` por página. Nunca 0, nunca 2.
- [ ] Jerarquía estricta H1→H2→H3→H4 sin saltarse niveles (nunca H2 seguido
      directamente de H4).
- [ ] Cero marca/teléfono/color "quemado" en Blade — todo desde modelos o
      `CompanySetting` editable en `/admin`.
- [ ] Las páginas de **servicio** y de **zona** se generan de forma dinámica
      desde su tabla (`{service:slug}`, `{zone:slug}`), nunca duplicando un
      archivo Blade por cada ciudad o servicio.
- [ ] El botón de llamada (y WhatsApp) es **sticky/visible** en móvil en cuanto
      el usuario hace scroll más allá del hero.
- [ ] Todas las animaciones respetan `prefers-reduced-motion: reduce` y se
      pueden desactivar globalmente desde `/admin` (accesibilidad y rendimiento).
- [ ] Cero afirmaciones publicitarias absolutas no verificables ("los más
      baratos de España", "100% garantizado siempre") — ver
      `references/07-legal-cumplimiento.md`.
- [ ] `robots.txt`, `sitemap.xml` y las 3 páginas legales existen desde el
      primer commit, no se dejan "para el final".
- [ ] Ninguna página de "combinación servicio × zona" se publica sin contenido
      realmente único (ver nota anti contenido duplicado en
      `references/01-sitemap-arquitectura.md`).

## 6. Mapa de archivos de esta skill

| Archivo | Contenido |
|---|---|
| `references/01-sitemap-arquitectura.md` | Listado completo de páginas, URLs, intención de búsqueda de cada una y rutas Laravel |
| `references/02-seo-estrategia-keywords.md` | Clusters de palabras clave, plantillas de title/meta, enlazado interno, schema.org, SEO local |
| `references/03-estructura-encabezados-hn.md` | Esquema H1-H6 exacto por tipo de página |
| `references/04-guion-animaciones-scroll.md` | Guion escena a escena de las animaciones de scroll del home (y patrón para servicio/zona) + copy de venta |
| `references/05-panel-administracion.md` | Especificación de cada recurso de Filament, incluido el personalizador de marca/tema |
| `references/06-modelo-datos-laravel.md` | Tablas, campos y relaciones Eloquent |
| `references/07-legal-cumplimiento.md` | Aviso legal, privacidad, cookies y banner conforme a AEPD/RGPD/LSSI |
| `references/08-stack-tecnico-paquetes.md` | Comandos composer/npm exactos |
| `references/09-checklist-seo-tecnico-lanzamiento.md` | Checklist final antes de publicar |
| `assets/seed-data-desatascos-em.md` | Datos de ejemplo listos para seeder: empresa, 10 servicios, 14 zonas, testimonios, FAQs, ideas de blog |

## 7. Cómo usar esta skill con tu agente (OpenCode / Mimo u otro)

Pega el contenido de este `SKILL.md` como instrucción de sistema/tarea, y deja
que el agente vaya abriendo cada archivo de `references/` en el paso
correspondiente del punto 4. Si tu herramienta no soporta carpetas, puedes pegar
los `.md` uno a uno en el orden indicado: el propio agente irá teniendo todo el
contexto necesario sin que le falte nada.
