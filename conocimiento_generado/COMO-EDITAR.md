# Recetas — los cambios que se piden más seguido

Todas las rutas salen de la carpeta del sitio.

## Cambiar el teléfono, el WhatsApp o el correo

`src/datos/sitio.json`. Se cambia **una sola vez** y queda cambiado en el pie, en la
página de contacto, en el formulario y en el botón flotante.

```json
"whatsapp": "573219803291",
"telefonoTexto": "+57 321 980 3291",
"correo": "auxiliar@hugofrancoingenieria.com",
```

⚠️ `whatsapp` va **sin espacios, sin + y sin guiones**, empezando por 57. Si se escribe
con espacios, el botón de WhatsApp deja de abrir la conversación.

## Cambiar el texto de la portada

`src/datos/inicio.json`, bloque `hero`. La palabra en verde se marca con `<em>`:

```json
"titulo": "Ingeniería que <em>protege</em> la vida y el agua",
```

## Cambiar el texto de un servicio

`src/datos/servicios.json`, dentro de `lista`. **Aparece en dos páginas a la vez**
(en `/servicios` y en el inicio); casi siempre es lo que se quiere.

## Agregar un servicio

1. Copiar un bloque entero de `lista` en `servicios.json` y pegarlo debajo
2. Cambiarle `id`, `num`, `titulo`, `resumen`, `texto` y `tags`
3. Poner un `icono` **de la lista que está en `STACK.md`** — si no está, no sale nada
4. Poner una `imagen` que exista en `public/img/`

## Agregar fotos a un proyecto

1. Guardar las fotos en `public/img/proyectos/`, nombradas `proyecto-6.webp`,
   `proyecto-7.webp`…
2. En `src/datos/proyectos.json`, agregar una entrada por foto dentro de `items`:

```json
{
  "cliente": "club-manizales",
  "nombre": "Club Manizales",
  "descripcion": "Humedal artificial para tratamiento de agua residual",
  "src": "/img/proyectos/club-manizales-10.webp",
  "alt": "Humedal artificial para tratamiento de agua residual — Club Manizales"
}
```

El `cliente` tiene que ser igual al `id` de un filtro, o la foto solo se verá en "Todo".

## Agregar un proyecto nuevo a la galería

Igual que arriba, pero antes hay que agregar el botón del filtro en `filtros`:

```json
{ "id": "nombre-corto", "texto": "Nombre visible" }
```

## Cambiar una foto

Guardar la nueva en `public/img/` **con el mismo nombre** que la vieja. No hay que tocar
ningún otro archivo. Medidas recomendadas:

| Dónde | Medida | Proporción |
|---|---|---|
| Portada del inicio | 1920 px de ancho | Panorámica y **oscura** (lleva texto blanco encima) |
| Encabezado de página interior | 1600 px de ancho | Panorámica |
| Fotos de "sobre nosotros" | 900 px de ancho | Vertical, 3:4 |
| Tarjetas de Mantesep | 1200 px de ancho | 4:3 |
| Galería de proyectos | 1200 px de ancho | 4:3 |
| Logos de clientes | 110 px de alto | Fondo transparente |

Guardar siempre en **WebP** si se puede: pesa la mitad que un JPG y se ve igual.

## Agregar un logo a la cinta de clientes

1. Guardar el logo en `public/img/clientes/`, en PNG o WebP con fondo transparente
2. Agregarlo a `clientes.logos` en `src/datos/inicio.json`

La cinta los muestra en gris y los colorea al pasar el mouse; funciona mejor con logos de
un solo color o con buen contraste.

## Cambiar un ítem del menú

`src/datos/sitio.json`, lista `menu`. Si se agrega una página nueva, hay que ponerle
también un `id`, y en el archivo `.astro` de esa página escribir `activa="ese-id"` para
que el menú marque dónde está el visitante.

## Cambiar los colores

`src/styles/global.css`, al principio del archivo. Están todos juntos y comentados.
⚠️ Afecta a **todo** el sitio y a los dos temas (claro y oscuro). Avisar antes de hacerlo.

## Lo que NO se hace desde aquí

- **Los textos legales** (`/politica-privacidad`, `/tratamiento-datos`) son borradores sin
  revisión de abogado. No cambiarlos sin consultar.
- **El aviso de aceptación del formulario** (`contacto.json`, campo `aviso`) también es
  legal.
- **El texto sobre la certificación de la Corporación Autónoma Regional** afirma algo
  verificable ante una autoridad. No adornarlo.
