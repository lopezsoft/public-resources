# ROL DEL AGENTE

Actúa como un **Senior Creative Developer** experto en Astro, Tailwind CSS y Diseño UI/UX. Tu objetivo es construir un sitio web corporativo (Landing Page) de alto impacto visual y rendimiento perfecto (100/100 Lighthouse).

## OBJETIVO DEL PROYECTO

Crear el sitio web oficial para **"ASAIE ÉXODO"**, una plataforma de gestión académica.

### Especificaciones Técnicas
- Framework: Astro (última versión estable)
- Modo de generación: SSG (Static Site Generation)
- CSS Framework: Tailwind CSS v3+
- Optimización: SEO, rendimiento web (objetivo Lighthouse 100/100)
- Compatibilidad: Navegadores modernos (últimas 2 versiones)
- Enfoque responsive: Mobile-first
- Accesibilidad: WCAG 2.1 nivel AA como mínimo

**Referencia Visual:**
El diseño debe seguir estrictamente la estructura y estética definida en las reglas de diseño a continuación.

## REGLAS DE DISEÑO (STRICT)

### Tipografía

#### Fuentes
- **Poppins** (Google Fonts): Títulos, encabezados y elementos destacados
- **Roboto** (Google Fonts): Cuerpo de texto, párrafos y contenido general
- Pesos disponibles: 400 (Regular), 500 (Medium), 700 (Bold)
- Importar desde Google Fonts con preconnect para optimización

#### Jerarquía de Texto
- H1: Poppins Bold, tamaños grandes responsivos (móvil: 2.5rem, desktop: 4rem)
- H2-H3: Poppins Bold, escala proporcional descendente
- H4-H6: Poppins Medium, para subtítulos y secciones menores
- Párrafos: Roboto Regular, tamaño mínimo 16px en móvil, 18px en desktop
- CTAs y botones: Poppins Medium para énfasis

#### Espaciado y Legibilidad
- Line-height: 1.625 (leading-relaxed) para párrafos
- Line-height: 1.25 (leading-tight) para títulos grandes
- Márgenes generosos entre secciones
- Ancho máximo de línea: 65-75 caracteres para lectura óptima

#### Contraste y Accesibilidad
- Texto oscuro sobre fondos claros: usar grises oscuros (no negro puro)
- Texto claro sobre fondos oscuros: blanco o grises muy claros
- Garantizar contraste WCAG AA (mínimo 4.5:1)
- Texto secundario con opacidad reducida para jerarquía

#### Iconografía
- Librería recomendada: Lucide Icons, Material Icons o FontAwesome
- Usar íconos solo cuando aporten valor visual o mejoren comprensión
- Tamaños consistentes y alineados con el texto
- NUNCA usar emojis en contenido corporativo

### Paleta de Colores

#### Colores Primarios (Azules)
Configura en `tailwind.config.mjs` la familia "primary" con estos valores:
- 50: #e6f4fb (azul muy claro, fondos sutiles)
- 100: #cce9f7 (azul claro)
- 200: #99d3ef (azul medio-claro)
- DEFAULT: #0399de (azul interactivo principal, para enlaces y elementos destacados)
- light: #02aeec (azul claro brillante, variaciones hover)
- dark: #053f74 (azul corporativo oscuro, fondos hero, textos fuertes)

#### Colores de Marca (Brand)
- orange: #bb4119 (naranja acento para CTAs primarios y elementos destacados)
- orangeLight: #d95a32 (naranja claro para estados hover)
- surface: #F8FAFC (gris muy claro, fondos alternativos)

#### Guía de Uso
**Fondos:**
- Secciones principales claras: blanco o surface
- Secciones de impacto: primary-dark con degradados
- Fondos alternativos: grises claros (gray-50, gray-100)

**Textos:**
- Títulos sobre fondo claro: primary-dark
- Títulos sobre fondo oscuro: blanco
- Párrafos sobre claro: grises oscuros (gray-700, gray-800)
- Párrafos sobre oscuro: grises claros (gray-100) o blanco

**Botones:**
- CTA principal: fondo naranja (orange), hover naranja claro (orangeLight)
- CTA secundario: fondo azul (primary), hover azul oscuro
- CTA outline: borde azul, hover con relleno azul

**Acentos:**
- Enlaces: primary (azul interactivo)
- Iconos destacados: orange
- Bordes sutiles: grises claros

## ARQUITECTURA DEL PROYECTO

### Estructura de Archivos
Organiza el proyecto con separación clara de responsabilidades. NO coloques todo el código en un solo archivo.

#### `/src/layouts/Layout.astro`
**Responsabilidades:**
- Estructura HTML5 base completa (doctype, html, head, body)
- Meta tags SEO: title, description, Open Graph, Twitter Cards
- Enlaces a fuentes de Google (Poppins, Roboto) con preconnect
- Configuración de viewport para responsive
- Favicon y app icons
- Schema.org JSON-LD para datos estructurados de organización
- Atributo lang dinámico según idioma activo

#### `/src/components/Navbar.astro`
**Diseño y Comportamiento:**
- Posición sticky en la parte superior (z-index alto)
- Efecto backdrop-blur con fondo semi-transparente blanco
- Al hacer scroll, añadir sombra sutil para profundidad
- Logo clickeable que lleva al inicio
- Enlaces de navegación: Inicio, Módulos, Precios, Contacto
- Selector de idioma (banderas o texto ES/EN)
- Responsive:
  - Desktop: navegación horizontal completa
  - Mobile: menú hamburguesa con slide-in desde lateral
  - Overlay oscuro al abrir menú mobile
  - Transiciones suaves en apertura/cierre

#### `/src/components/Hero.astro`
**Diseño Visual:**
- Altura mínima de viewport completo, contenido centrado verticalmente
- Fondo: degradado azul oscuro (from primary-dark via primary-900 to primary-800)
- Elementos decorativos: patrón de grid sutil o partículas con baja opacidad
- Contenido:
  - Título principal H1 grande y impactante
  - Subtítulo descriptivo breve
  - Dos CTAs: primario (naranja, "Solicitar Demo") y secundario (outline, "Ver Módulos")
- Animación de fade-in al cargar la página
- Opcional: ilustración o mockup de dashboard a un lado

#### `/src/components/BentoGrid.astro`
**Estructura:**
- Grid responsivo de tarjetas para módulos de ASAIE
- Layout: 1 columna mobile, 2 columnas tablet, 3 columnas desktop
- Cada tarjeta debe incluir:
  - Ícono representativo del módulo (arriba o lateral)
  - Título del módulo en negritas
  - Descripción breve de 2-3 líneas
  - Badge de estado: "Disponible" o "Próximamente"
- Efectos hover: elevación (translate-y negativo), sombra más pronunciada
- Fondo blanco con bordes sutiles, bordes redondeados grandes
- Módulos a mostrar: extraer de documentación en /docs (Rectoría, Docentes, Biblioteca, etc.)

#### `/src/components/Pricing.astro`
**Estructura de Precios:**
- Tres planes en columnas: Básico, Profesional, Enterprise
- Grid responsivo: 1 columna mobile, 3 columnas desktop
- Plan destacado (Profesional): borde naranja, badge "Más Popular", sombra elevada
- Cada tarjeta incluye:
  - Nombre del plan
  - Precio mensual grande y destacado
  - Lista de características con checkmarks
  - Botón CTA: "Contratar Plan" o "Contactar Ventas"
- Nota al pie: "Todos los planes incluyen soporte técnico"
- Enlace opcional: "Ver comparativa completa"

#### `/src/components/Footer.astro`
**Secciones:**
- Logo y tagline/descripción breve de ASAIE
- Navegación rápida (enlaces principales)
- Información de contacto: email, teléfono, dirección
- Iconos de redes sociales con enlaces
- Copyright con año dinámico
- Enlaces legales: Política de Privacidad, Términos de Servicio
- Diseño: fondo oscuro (gray-900), texto claro, grid de 3-4 columnas en desktop, stack en mobile

#### `/src/pages/index.astro`
**Ensamblaje:**
- Importar Layout y todos los componentes
- Definir título y descripción de página para SEO
- Estructura: Navbar → Hero → BentoGrid → Pricing → Footer
- Lang="es" para versión en español

### Estilos y Efectos Visuales

#### Sombras
- Tarjetas en reposo: sombra suave y difusa
- Tarjetas hover: sombra más pronunciada y elevada
- Botones: sombra sutil, incrementa en hover
- Navbar con scroll: sombra media para separación del contenido

#### Bordes Redondeados
- Tarjetas y secciones grandes: muy redondeados (12-16px)
- Botones: redondeados medianos (8px)
- Elementos pequeños: ligeramente redondeados (4-6px)

#### Transiciones
- Todos los elementos interactivos con transición suave (300ms)
- Easing: ease-in-out para naturalidad
- Propiedades animadas: transform, shadow, colors, opacity

#### Degradados
- Hero: degradado diagonal oscuro con variaciones de azul
- Botones premium: degradado horizontal naranja
- Overlays de imagen: degradado vertical desde transparente a oscuro

### Internacionalización (i18n)

#### Idiomas Soportados
- Español (es): idioma por defecto
- Inglés (en): idioma secundario

#### Implementación
- Crear archivos JSON en `/src/i18n/es.json` y `/src/i18n/en.json`
- Estructura JSON por secciones: nav, hero, modules, pricing, footer, etc.
- Crear helper en `/src/utils/i18n.ts` para gestionar traducciones
- Rutas separadas: `/` para español, `/en/` para inglés
- Selector de idioma en Navbar con banderas o códigos (ES/EN)
- Detectar idioma del navegador como preferencia inicial
- Cambio de idioma redirige a la página equivalente
- URLs amigables SEO en ambos idiomas

#### Contenido Traducible
- Todos los textos visibles deben venir de archivos de traducción
- Meta tags SEO también traducidos
- Alt texts de imágenes
- Etiquetas de formularios y botones

## GESTIÓN DE CONTENIDO

### Imágenes y Assets

#### Logotipos
**Ubicación actual:** Carpeta `/docs` en la raíz del proyecto
**Destino:** Copiar a `/public/` con nombres estandarizados:
- `logotipo.png`: Logo completo con texto (usar en Navbar y Footer)
- `logo-icon.png`: Isotipo/ícono solo (usar para favicon y vista mobile)

**Optimización de imágenes:**
- Especificar width y height para evitar layout shift
- Loading eager para logos en above-the-fold
- Loading lazy para imágenes en secciones inferiores
- Alt text descriptivo para accesibilidad
- Considerar formato WebP con fallback PNG para imágenes decorativas

**Generación de favicon:**
- Crear favicon.svg y favicon.ico desde logo-icon.png
- Incluir múltiples tamaños para diferentes dispositivos (16x16, 32x32, 180x180, 192x192, 512x512)

### Extracción de Contenido

#### Fuentes de Información
Buscar y leer archivos en la carpeta `/docs` para extraer:
- Descripción de módulos académicos
- Características y beneficios de ASAIE ÉXODO
- Información de precios y planes (si está disponible)
- Misión, visión y valores corporativos
- Información de contacto

#### Procesamiento
- Identificar secciones clave en los documentos
- Estructurar información en formato JSON organizado
- Crear archivo `/src/data/content.json` con toda la información
- Importar y usar este archivo en los componentes correspondientes

#### Contenido Requerido por Sección
**BentoGrid (Módulos):**
- Nombre de cada módulo
- Descripción breve (2-3 líneas)
- Funcionalidades principales
- Estado (disponible/próximamente)

**Pricing:**
- Nombres de planes
- Precios mensuales
- Lista de características por plan
- Diferenciadores del plan destacado

**Footer:**
- Email de contacto
- Teléfono
- Dirección física (si aplica)
- Enlaces a redes sociales

### Interactividad y Experiencia de Usuario

#### Efectos Hover
**Botones:**
- Cambio de color de fondo (más oscuro o brillante)
- Ligero incremento de escala (1.05x)
- Sombra más pronunciada
- Transición suave de 300ms

**Tarjetas:**
- Elevación vertical ligera (translate hacia arriba)
- Sombra más intensa y difusa
- Opcional: cambio sutil de color de borde
- Mantener suavidad en la transición

**Enlaces:**
- Cambio de color
- Subrayado animado (desde centro o izquierda)
- Mantenimiento de contraste para accesibilidad

#### Navegación Responsive
**Desktop (>= 768px):**
- Navbar con logo a la izquierda
- Enlaces horizontales visibles
- Selector de idioma a la derecha

**Mobile (< 768px):**
- Logo centrado o a la izquierda
- Botón hamburguesa a la derecha
- Al tocar hamburguesa: menú desliza desde el lado
- Overlay oscuro semi-transparente detrás del menú
- Botón X o icono de cierre dentro del menú
- Click en overlay cierra el menú
- Enlaces en stack vertical con espaciado cómodo

#### Smooth Scroll
- Configurar scroll suave en HTML
- Enlaces internos con navegación animada a secciones
- Opcional: botón "volver arriba" que aparece tras scroll > 300px

#### Feedback Visual
- Estados focus visibles para accesibilidad de teclado
- Loading states en botones de formulario
- Cambios de cursor apropiados (pointer en clickeables)
- Animaciones de entrada sutiles en secciones (scroll reveal)

## PLAN DE EJECUCIÓN

### Fase 1: Configuración Base
1. Inicializar proyecto Astro con TypeScript
2. Instalar y configurar Tailwind CSS v3+
3. Configurar `tailwind.config.mjs` con la paleta de colores completa especificada
4. Configurar fuentes Poppins y Roboto en Tailwind config
5. Añadir sombras personalizadas en Tailwind config

### Fase 2: Layout y Estructura
6. Crear `/src/layouts/Layout.astro` con meta tags SEO, fuentes y estructura base
7. Buscar y copiar logotipos desde `/docs` a `/public/`
8. Generar favicons en múltiples tamaños

### Fase 3: Componentes Principales
9. Desarrollar `Navbar.astro` con sticky positioning y responsive menu
10. Desarrollar `Hero.astro` con degradado, textos impactantes y CTAs
11. Leer documentación en `/docs` y extraer información de módulos
12. Desarrollar `BentoGrid.astro` con grid responsivo y tarjetas de módulos
13. Desarrollar `Pricing.astro` con tres planes y diseño de tarjetas
14. Desarrollar `Footer.astro` con información de contacto y enlaces

### Fase 4: Internacionalización
15. Crear archivos de traducción `/src/i18n/es.json` y `/src/i18n/en.json`
16. Crear helper `/src/utils/i18n.ts` para gestión de traducciones
17. Implementar selector de idioma en Navbar
18. Crear página `/src/pages/en/index.astro` para versión en inglés

### Fase 5: Página Principal y Optimización
19. Ensamblar `/src/pages/index.astro` importando todos los componentes
20. Verificar responsive en diferentes breakpoints
21. Optimizar imágenes y assets
22. Validar accesibilidad y contraste de colores
23. Test de rendimiento con Lighthouse (objetivo: 100/100)

### Criterios de Éxito
- Diseño transmite: **Tecnología, Solidez y Modernidad**
- Experiencia visual coherente y profesional
- Navegación fluida e intuitiva
- Tiempo de carga < 2 segundos
- Responsive perfecto en mobile, tablet y desktop
- Accesibilidad WCAG AA
- SEO optimizado con meta tags completos

---

**PRINCIPIOS DE DISEÑO:**
Cada decisión visual debe reforzar la percepción de ASAIE ÉXODO como una solución moderna, confiable y profesional para gestión académica.

---

## INSTRUCCIONES PARA EL AGENTE EJECUTOR

Analiza los documentos PDF en la carpeta /docs para extraer toda la información necesaria del contenido: módulos académicos, características del producto, información de contacto, precios y planes. Asegura que esta información esté correctamente integrada en las secciones correspondientes del sitio web.

Crea un plan de ejecución detallado por sprints para el desarrollo del proyecto, dividiendo las tareas en sprints manejables con objetivos claros y entregables definidos para cada fase, este plan de tabajo debes crearlo en un archivo markdown en el directorio docs y solo debes iniciar a construir cuanto lo apruebe.

Al final de cada sprint, realiza una revisión para asegurar que los objetivos se han cumplido antes de avanzar al siguiente sprint y actualizar el % de avance del proyecto.