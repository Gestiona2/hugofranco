# Marca — Hugo Franco Ingeniería

## La idea de diseño: "el plano certificado"

Esta empresa **prueba y certifica** sistemas. Por eso el sitio se lee como una lámina de
ingeniería: papel de plano con cuadrícula, líneas de cota, tuberías con su color de línea,
y un sello de "acta emitida". Cada decisión visual sale de ahí, no de una plantilla.

**Lo memorable es una sola cosa:** la curva de **prueba hidrostática** de la portada. La
presión sube, se sostiene en 200 psi durante 2 horas y cae el sello "Acta emitida". Todo lo
demás es sobrio a propósito, para que esa pieza destaque.

## Colores

Salen del logotipo y de las convenciones de los planos. **No se inventó una paleta
decorativa.**

| Nombre | Valor | Para qué |
|---|---|---|
| Tinta de plano | `#0b1730` | Texto principal en tema claro, botones, bloques oscuros |
| Azul del logo | `#1b4fa8` | Enlaces, líneas de cota, el frente de "Diseño hidráulico" |
| Rojo de línea de incendio | `#d1352a` | La curva de la prueba, el frente de incendios, la línea del menú activo |
| Verde ambiental | `#25763f` | El frente de ingeniería ambiental, Mantesep |
| Lima de marca | `#abca1e` | **Solo lo aprobado y certificado:** el sello, los marcadores, el botón sobre fondo oscuro. Nunca como texto sobre claro. |
| Papel de plano | `#eef2f7` | Fondo del tema claro |

> **Regla del lima:** es el color de la empresa, pero se reserva para "aprobado". Si se usa
> en todas partes deja de significar algo. Sobre fondo claro **nunca** va como texto: no se
> lee. Para texto verde sobre claro existe `--lima-texto`.

**Dónde se cambian:** `src/styles/global.css`, bloques `:root` (tema claro) y
`:root[data-theme="dark"]` (cianotipo), al principio del archivo.

### Color de línea de cada frente

Como en los planos, cada frente lleva el color de su tubería: hidráulico = azul,
ambiental = verde, incendios = rojo, inspección y certificación = lima. Se define con el
campo `linea` de cada servicio en `servicios.json` (`azul`, `verde`, `rojo`, `lima`).

## Dos temas

| Tema | Qué es | Fondo |
|---|---|---|
| Claro | Papel de plano | `#eef2f7` con cuadrícula azul tenue |
| Oscuro | **Cianotipo** (azul de plano con trazos claros) | `#0a1c45` |

El visitante elige con el botón de la luna/sol; se guarda en su navegador.

**Cómo funciona, y por qué importa al editar:** ninguna sección usa un color escrito a
mano. Todas usan variables (`var(--text)`, `var(--bg)`, `var(--azul)`…) que cambian según
el tema. **Si alguna vez se escribe un color directo en un estilo, ese punto se rompe en el
otro tema.** Es el error más fácil de cometer.

Los bloques "cianotipo" (certificación, Mantesep, llamado final, pie) son azul oscuro en los
dos temas: son la parte "plano" del sitio.

## Tipografías

| Uso | Fuente | Por qué |
|---|---|---|
| Títulos, botones, cifras | **Archivo** (variable: peso 100–900 y ancho 62–125 %) | Tiene ancho variable: se usa ancho para titulares y condensado para rótulos tipo cajetín de plano |
| Textos | **Public Sans** (variable) | Legible, neutra, pensada para texto largo y documentos |

Las dos están **guardadas dentro del sitio** (`public/fonts/`), no se piden a Google:
privacidad del visitante y que el sitio funcione dentro de diez años.

## Tono de los textos

- **Trato de usted.** Le habla a constructoras y entidades públicas, no a consumidores.
- **Concreto, sin adjetivos de más.** "Probamos el sistema y lo certificamos" pesa más que
  "soluciones de la más alta calidad".
- **La norma se nombra.** NFPA, Corporación Autónoma Regional, S.T.A.R.
- **Nunca prometer lo que no se puede probar.** Sin cifras inventadas. Las cuatro de la
  portada salen de algo verificable en el propio sitio: NFPA (estándar usado), 4 frentes,
  8 entidades (los logos de la cinta) y 5 obras (las de la galería).

## Movimiento

Hay poco y con intención:
1. La curva de prueba de la portada (se dibuja una vez, al verla).
2. El índice de "frentes" que marca el activo mientras se baja.
3. La línea de pasos del protocolo que se va llenando al bajar.
4. Transición suave entre páginas (nativa del navegador, donde exista).

Si alguien tiene activado "reducir movimiento" en su sistema, todo se muestra ya terminado,
sin animar. **Eso no se debe quitar.**
