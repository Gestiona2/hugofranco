# Marca — Hugo Franco Ingeniería

## De dónde salen estos colores

Del logotipo existente y del sitio anterior. **No se inventó una paleta nueva**: el verde
lima ya era el color de la empresa y el azul viene del propio logo. Lo que cambió es cómo
se usan: antes el verde era un acento decorativo sobre blanco; ahora la autoridad la pone
el fondo casi negro y el verde es la señal que marca lo importante.

## Colores

| Nombre | Valor | Para qué |
|---|---|---|
| Verde profundo | `#5f8a0d` | Botones y texto verde sobre fondo claro. **Es el lima oscurecido** para que se lea bien sobre blanco; el lima puro no alcanza el contraste. |
| Lima de marca | `#abca1e` | El color de la empresa. Acentos, subrayados, botones sobre fondo oscuro. |
| Azul del logo | `#1b4fa8` | Está declarado pero hoy solo vive dentro del logotipo. Disponible si se necesita un segundo acento. |
| Negro verdoso | `#101410` | Portadas, bloques oscuros, pie de página |
| Fondo claro | `#f6f7f2` | El fondo general. No es blanco puro: es un hueso muy leve, más amable a la vista. |
| Gris de marca | `#414141` | Texto secundario |

**Dónde se cambian:** `src/styles/global.css`, bloques `@theme` y `:root`, al principio
del archivo. Están todos juntos y comentados.

> **Regla de contraste:** el lima `#abca1e` **nunca** va como texto sobre fondo blanco —
> no se lee. Sobre fondo oscuro sí, y ahí es donde brilla. Para fondo claro está el verde
> profundo.

## Tema claro y tema oscuro

El sitio tiene los dos, y el visitante elige con el botón de la luna/sol. La preferencia
se guarda en su navegador.

**Cómo funciona, y por qué importa al editar:** ninguna sección usa un color escrito a
mano. Todas usan variables (`var(--text)`, `var(--bg)`, `var(--marca)`…) que cambian de
valor según el tema. **Si alguna vez se escribe un color directo en un estilo, ese punto
se rompe en tema oscuro.** Es el error más fácil de cometer en este sitio.

## Tipografías

| Uso | Fuente | Dónde |
|---|---|---|
| Títulos | **Space Grotesk** | Titulares, botones, números, etiquetas |
| Textos | **Inter** | Párrafos y listas |

Las dos están **guardadas dentro del sitio** (`public/fonts/`), no se piden a Google. Es a
propósito: así el sitio no le pasa la IP de cada visitante a un servidor ajeno, y sigue
funcionando aunque Google cambie algo. Son fuentes variables: un solo archivo cubre todos
los grosores.

## Tono de los textos

- **Trato de usted.** Es una empresa de ingeniería que le habla a constructoras y
  entidades públicas, no a consumidores.
- **Concreto, sin adjetivos de más.** "Probamos el sistema y lo certificamos" pesa más que
  "soluciones de la más alta calidad".
- **La norma se nombra.** NFPA, Corporación Autónoma Regional, S.T.A.R. Es lo que separa a
  esta empresa de un instalador cualquiera, y el cliente que la busca reconoce las siglas.
- **Nunca prometer lo que no se puede probar.** Sin cifras inventadas de años de
  experiencia, obras entregadas o clientes satisfechos. Todas las cifras del sitio salen
  de algo verificable.

## Movimiento

Las secciones aparecen suavemente al bajar. Es discreto a propósito. Si alguien tiene
activado "reducir movimiento" en su sistema, todo se muestra de una vez, sin animación —
eso no se debe quitar.
