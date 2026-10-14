# Con qué está hecho y dónde está cada cosa

## En una línea

Astro 7 + Tailwind 4, sitio estático. No hay base de datos, ni servidor, ni panel de
administración. Se compila a archivos HTML que cualquier hosting puede servir.

## El mapa de carpetas

```
web-hugofranco/
├── src/
│   ├── datos/          ← TODO EL TEXTO DEL SITIO. Un archivo por página.
│   ├── pages/          ← Una página por archivo. La dirección sale del nombre.
│   ├── components/     ← Piezas que se repiten: encabezado de página, llamado final,
│   │                     formulario, Protocolo (la línea de pasos animada), Legal
│   ├── layouts/        ← Layout.astro: SEO, menú, pie (cajetín), botón de tema. En todas.
│   └── styles/
│       └── global.css  ← Colores, tipografías y todos los estilos
├── public/
│   ├── img/            ← Fotos del sitio
│   │   ├── clientes/   ← Logos de la cinta
│   │   └── proyectos/  ← Galería
│   ├── brand/          ← Logotipo y favicon
│   ├── fonts/          ← Archivo y Public Sans, guardadas aquí
│   ├── vendor/         ← Los íconos, guardados aquí
│   ├── sitemap.xml     ← A mano: agregar cada página nueva
│   └── robots.txt
└── dist/               ← Lo que se publica. Se genera solo; no editar.
```

## Las páginas y sus direcciones

| Archivo | Dirección |
|---|---|
| `src/pages/index.astro` | `/` |
| `src/pages/servicios.astro` | `/servicios` |
| `src/pages/mantesep.astro` | `/mantesep` |
| `src/pages/proyectos.astro` | `/proyectos` |
| `src/pages/certificaciones.astro` | `/certificaciones` |
| `src/pages/contacto.astro` | `/contacto` |
| `src/pages/politica-privacidad.astro` | `/politica-privacidad` |
| `src/pages/tratamiento-datos.astro` | `/tratamiento-datos` |
| `src/pages/404.astro` | cualquier dirección que no exista |

Para una página nueva basta con crear el archivo. La dirección sale del nombre.

## Nada se pide a servidores ajenos

Las tipografías y los íconos **están guardados dentro del sitio** (las animaciones son
código propio, sin librerías). No se cargan desde Google ni desde un CDN. Dos razones: la privacidad del
visitante (nadie externo se entera de quién entró) y que el sitio siga funcionando dentro
de diez años sin depender de que un servicio ajeno siga vivo.

## Los íconos

Están en `public/vendor/lucide/lucide.min.js`. **No es la librería completa** — son solo
los que el sitio usa, para no cargar 368 KB por 24 dibujos.

Los que hay hoy:

```
arrow-right  arrow-up  arrow-up-right  badge-check  check-circle-2  circle-check-big
clipboard-check  clock  droplets  facebook  filter  flame  instagram  layout-grid
leaf  mail  map-pin  message-circle  moon  phone  settings-2  spray-can  sun
toilet  waves
```

**Si pones un `icono` que no está en esa lista, no sale nada** (y queda un aviso en la
consola del navegador). Para agregar uno: bajar su SVG de
`unpkg.com/lucide-static@0.544.0/icons/<nombre>.svg`, quitarle el comentario de licencia y
la etiqueta `<svg>` de afuera, y sumar el interior al objeto `ICONOS` de ese archivo. Las
instrucciones están escritas ahí mismo, al principio.

## Las animaciones

Código propio (sin GSAP ni otras librerías), en la propia página que las usa:

- **La prueba hidrostática** de la portada (`src/pages/index.astro`, script del final): dibuja
  la curva con el tiempo, mueve el punto, cuenta el reloj y pone el sello. Empieza cuando se
  ve en pantalla.
- **El índice de frentes**: marca el frente que se está viendo.
- **El protocolo** (`src/components/Protocolo.astro`): la línea de pasos se llena al bajar.
- **Transición entre páginas:** una línea de CSS (`@view-transition`), la hace el navegador.

Con "reducir movimiento" activado en el sistema, todo aparece terminado, sin animar.

## El formulario

**No hay servidor.** El formulario arma el texto del mensaje y lo abre en WhatsApp o en el
correo del visitante. Está todo en `src/components/Formulario.astro`. Por eso funciona en
cualquier hosting, sin configurar nada y sin costo mensual.

Si algún día se quiere envío real por correo, hay que agregar una función serverless —
está anotado en `PENDIENTES.md`.

## Ver el sitio mientras se edita

```
npm run dev
```
Abre `http://localhost:4321`. Los cambios se ven al instante.

## Compilar

```
npm run build
```
Deja el sitio listo en `dist/`. **No hace falta hacerlo para publicar**: eso lo hace solo
el servidor de publicación.
