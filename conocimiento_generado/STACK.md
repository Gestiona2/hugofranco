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
│   ├── components/     ← Piezas que se repiten (encabezado, llamado final, formulario)
│   ├── layouts/        ← Layout.astro: menú, pie, botón de tema. Se ve en todas.
│   └── styles/
│       └── global.css  ← Colores, tipografías y todos los estilos
├── public/
│   ├── img/            ← Fotos del sitio
│   │   ├── clientes/   ← Logos de la cinta
│   │   └── proyectos/  ← Galería
│   ├── brand/          ← Logotipo y favicon
│   ├── fonts/          ← Las dos tipografías, guardadas aquí
│   └── vendor/         ← Librerías guardadas aquí (GSAP y los íconos)
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

Para una página nueva basta con crear el archivo. La dirección sale del nombre.

## Nada se pide a servidores ajenos

Las tipografías, los íconos y la librería de animación **están guardados dentro del
sitio**. No se cargan desde Google ni desde un CDN. Dos razones: la privacidad del
visitante (nadie externo se entera de quién entró) y que el sitio siga funcionando dentro
de diez años sin depender de que un servicio ajeno siga vivo.

## Los íconos

Están en `public/vendor/lucide/lucide.min.js`. **No es la librería completa** — son solo
los que el sitio usa, para no cargar 368 KB por 24 dibujos.

Los que hay hoy:

```
arrow-right   arrow-up      arrow-up-right  check-circle-2  circle-check-big
clipboard-check  clock      droplets        facebook        filter
flame         instagram     layout-grid     leaf            mail
map-pin       message-circle  moon          phone           settings-2
spray-can     sun           toilet          waves
```

**Si pones un `icono` que no está en esa lista, no sale nada** (y queda un aviso en la
consola del navegador). Para agregar uno: bajar su SVG de
`unpkg.com/lucide-static@0.544.0/icons/<nombre>.svg`, quitarle el comentario de licencia y
la etiqueta `<svg>` de afuera, y sumar el interior al objeto `ICONOS` de ese archivo. Las
instrucciones están escritas ahí mismo, al principio.

## Las animaciones

GSAP con ScrollTrigger, guardado en `public/vendor/gsap/`. Un elemento con la clase
`reveal` aparece al llegar a él. Los que tienen `data-parallax` se mueven un poco más
lento que el resto.

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
