# Inventario de secciones — Hugo Franco Ingeniería

Qué hay en cada página, dónde vive su texto, y qué se puede cambiar sin romper nada.

> **Lo primero y más importante de este sitio: TODO el texto vive en `src/datos/`.**
> Un archivo por página, más `sitio.json` para lo que se repite. Los archivos `.astro`
> tienen el diseño y **ni una sola frase escrita a mano**. Si crees que hay que tocar un
> `.astro` para cambiar un texto, vuelve a mirar el JSON: el campo existe.

## Los archivos de contenido

| Archivo | Qué controla |
|---|---|
| `src/datos/sitio.json` | Menú, teléfonos, correo, dirección, horario, redes, pie. **Se ve en todas las páginas.** |
| `src/datos/inicio.json` | Toda la página de inicio |
| `src/datos/servicios.json` | Los 4 servicios (los usa `/servicios` **y también el inicio**) |
| `src/datos/mantesep.json` | La página de Mantesep |
| `src/datos/proyectos.json` | La galería: filtros y fotos |
| `src/datos/certificaciones.json` | La página de certificaciones |
| `src/datos/contacto.json` | Formulario y ubicación |

---

## Lo que se repite en todas las páginas (`sitio.json`)

### Menú de arriba
- **Cómo lo llama el cliente:** "el menú", "los botones de arriba"
- **Dónde:** lista `menu` en `sitio.json`
- **Cuántos caben bien:** 5 a 7. Con más de 7 se amontona en pantallas medianas.
- **Cuidado:** el campo `id` de cada ítem debe coincidir con el `activa="..."` de la
  página, o el subrayado verde no marca dónde está el visitante.

### Teléfonos, correo y dirección
- **Dónde:** `whatsapp`, `telefonoTexto`, `telefonoFijo`, `correo`, `direccion`, `ciudad`,
  `horario` en `sitio.json`
- **Cambiarlos aquí los cambia en el pie, en la página de contacto y en el botón flotante
  de WhatsApp, todo de una vez.**
- **Cuidado:** `whatsapp` va **sin espacios, sin + y sin guiones**, empezando por 57
  (ejemplo: `573219803291`). Si se escribe con espacios, el botón de WhatsApp deja de
  funcionar. `telefonoTexto` sí es para leer, ahí van los espacios.

### Pie de página
- Se arma solo con el menú, los datos de contacto y la lista `legales`. No hay que
  editarlo aparte.

---

## Página de inicio (`src/datos/inicio.json`)

Ocho secciones, en este orden.

### 1. Portada
- **Cómo la llama el cliente:** "la portada", "lo primero que se ve"
- **Dónde:** bloque `hero`
- **Qué contiene:** línea pequeña de arriba (`eyebrow`), titular, párrafo, dos botones y
  cuatro cifras.
- **El titular admite una palabra en verde:** se marca con `<em>`, así:
  `"Ingeniería que <em>protege</em> la vida y el agua"`. Es el único lugar del sitio donde
  se escribe una etiqueta dentro del texto.
- **Imagen:** `/img/hero-incendios.webp` — 1920 px de ancho, se recorta a pantalla
  completa. Debe ser una foto **oscura**: encima va texto blanco.
- **Cuidado:** el titular está pensado para 3 líneas en computador. Mucho más largo empuja
  las cifras fuera de la pantalla.

### 2. Cinta de logos de clientes
- **Cómo la llama el cliente:** "los logos que se mueven"
- **Dónde:** bloque `clientes`
- **Cuántos caben bien:** 6 a 10. Con menos de 5 se nota la repetición.
- **Imagen:** PNG o WebP con fondo transparente, 110 px de alto. Se muestran en gris y se
  colorean al pasar el mouse.

### 3. Sobre nosotros
- **Dónde:** bloque `nosotros` — dos párrafos, cuatro puntos con visto, un botón y dos fotos
- **Imágenes:** `/img/nosotros-1.webp` y `/img/nosotros-2.webp` — verticales, 3:4
  (la segunda va desfasada hacia abajo, es a propósito)

### 4. Los cuatro servicios
- **Dónde:** ¡ojo! el título y la entrada están en `inicio.json` (bloque `servicios`),
  pero **la lista sale de `servicios.json`**. Se escribe una sola vez y se ve en dos
  páginas.
- **Cuidado:** cambiar un servicio aquí lo cambia también en `/servicios`. Es lo que se
  quiere casi siempre.

### 5. Inspección y certificación (bloque negro)
- **Dónde:** bloque `certificacion` — dos párrafos y cuatro pasos numerados
- **Cuántos pasos caben bien:** exactamente 4. Con 3 o 5 la cuadrícula queda coja.

### 6. Mantesep
- **Dónde:** esta sección es la excepción — las cuatro tarjetas están escritas dentro de
  `src/pages/index.astro`, en una lista corta al inicio de la sección `MANTESEP`. Son solo
  título e imagen; el texto de verdad está en `/mantesep`.

### 7. Testimonio
- **Dónde:** bloque `testimonio`
- **Cuidado:** hoy dice "Cliente de proyecto hidráulico" porque **no se ha confirmado
  quién lo dijo**. Ver `PENDIENTES.md`. No inventar un nombre.

### 8. Llamado final
- **Dónde:** bloque `ctaFinal`. El mismo bloque negro cierra casi todas las páginas, pero
  con texto propio escrito en cada `.astro` (es corto y cambia por página).

---

## Servicios (`src/datos/servicios.json`)

### La lista de servicios
- **Dónde:** lista `lista`
- **Cada servicio tiene:** `id` (el ancla de la dirección: `/servicios#incendios`), `num`,
  `titulo`, `icono`, `resumen`, `texto`, `tags` e `imagen`.
- **Cuántas etiquetas (`tags`) caben bien:** 3 a 5. Con más se van a tres renglones.
- **Cuidado con `icono`:** solo funcionan los íconos que estén en
  `public/vendor/lucide/lucide.min.js`. Si pones uno que no está, **no sale nada**. La
  lista de los que hay está al principio de ese archivo, y en `STACK.md`.
- **Cuidado con `id`:** si lo cambias, se rompen los enlaces del pie de página.

### Los cuatro pasos de "cómo trabajamos"
- **Dónde:** bloque `proceso`. Exactamente 4 pasos.

---

## Mantesep (`src/datos/mantesep.json`)

- **Dónde:** lista `servicios` — cinco tarjetas con foto, ícono, título y texto
- **Cuántas caben bien:** múltiplos de 3 se ven mejor (van de a 3 por fila). Con 5, la
  segunda fila queda con dos. Es aceptable, pero 6 se ve mejor.
- **Imágenes:** 4:3, mínimo 800 px de ancho
- **Bloque `certificacion`:** el texto negro del final. Dice que Mantesep está certificada
  por la Corporación Autónoma Regional. **El número de resolución todavía falta** —
  ver `PENDIENTES.md`.

---

## Proyectos (`src/datos/proyectos.json`)

- **Dónde:** `filtros` (los botones de arriba) e `items` (las fotos)
- **Cómo se conectan:** cada foto tiene un campo `cliente` que debe coincidir con el `id`
  de un filtro. Si no coincide, la foto solo se ve en "Todo".
- **Para agregar un proyecto:**
  1. Sube las fotos a `public/img/proyectos/` con nombres como `nombre-1.webp`
  2. Agrega un filtro nuevo a `filtros`
  3. Agrega una entrada por foto en `items`, con el mismo `cliente`
- **Imagen:** 4:3, máximo 1200 px de ancho. Más grande solo pesa, no se ve mejor.
- **Cuántas caben bien:** de 3 a 12 por proyecto.

---

## Certificaciones (`src/datos/certificaciones.json`)

- **`marcos`:** las tres tarjetas con sigla (NFPA, CAR, NAL). La sigla debe ser corta —
  máximo 5 letras — o rompe el recuadro.
- **`servicio`:** el bloque negro con los cuatro pasos
- **`documentos`:** el cierre. Hoy dice que los certificados se envían a solicitud, porque
  **todavía no tenemos los PDF**. Cuando lleguen, esta sección debería listarlos.

---

## Contacto (`src/datos/contacto.json`)

- **`formulario.servicios`:** las opciones de la lista desplegable. Conviene que digan lo
  mismo que los servicios reales.
- **`formulario.aviso`:** el texto junto a la casilla de aceptación. **Es un texto legal:
  no cambiarlo sin consultar.**
- **`mapa`:** no hay mapa incrustado a propósito — un mapa de Google dentro de la página le
  enviaría la dirección IP de cada visitante a Google sin que la persona lo pida. En su
  lugar hay un botón que abre el mapa en otra pestaña. **Si alguien pide "poner el mapa",
  explicar esto antes de cambiarlo.**
