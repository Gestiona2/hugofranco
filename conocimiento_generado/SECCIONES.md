# Inventario de secciones — Hugo Franco Ingeniería

Qué hay en cada página, dónde vive su texto, y qué se puede cambiar sin romper nada.

> **Lo primero y más importante: TODO el texto vive en `src/datos/`.** Un archivo por
> página, más `sitio.json` para lo que se repite. Los archivos `.astro` tienen el diseño y
> **ni una sola frase escrita a mano**. Si crees que hay que tocar un `.astro` para cambiar
> un texto, vuelve a mirar el JSON: el campo existe.

## Los archivos de contenido

| Archivo | Qué controla |
|---|---|
| `src/datos/sitio.json` | Menú, teléfonos, correo, dirección, horario, redes, pie. **Se ve en todas las páginas.** |
| `src/datos/inicio.json` | Toda la página de inicio |
| `src/datos/servicios.json` | Los 4 servicios (los usa `/servicios`, el inicio y el pie) |
| `src/datos/mantesep.json` | La página de Mantesep |
| `src/datos/proyectos.json` | La galería: filtros, fotos y textos del visor |
| `src/datos/certificaciones.json` | La página de certificaciones |
| `src/datos/contacto.json` | Formulario, rótulos y ubicación |
| `src/datos/legal.json` | Política de privacidad y tratamiento de datos (borradores) |
| `src/datos/pagina-404.json` | La página de "no encontrada" |

---

## Lo que se repite en todas las páginas (`sitio.json`)

### Menú de arriba
- **Dónde:** lista `menu`. Cabe bien de 5 a 7 ítems.
- **Cuidado:** el campo `id` debe coincidir con el `activa="..."` de la página, o no marca
  dónde está el visitante.
- El botón "Cotizar" sale de `ctaPrincipal`.

### Teléfonos, correo y dirección
- **Dónde:** `whatsapp`, `telefonoTexto`, `telefonoFijo`, `correo`, `direccion`, `ciudad`,
  `horario`. Se cambian una vez y quedan en el pie, contacto, botón flotante y datos de
  Google.
- **Cuidado:** `whatsapp` va **sin espacios, sin + y sin guiones**, empezando por 57.

### Pie de página (el "cajetín")
- Cuatro columnas: marca y redes, navegación, servicios (lee `servicios.json`) y contacto.
  No hay que editarlo aparte.

---

## Inicio (`inicio.json`)

Las secciones, en el orden en que aparecen.

### 1. Portada — bloque `hero`
Tres piezas:
- **Titular, texto, botones y cuatro cifras** (`titulo`, `sub`, `acciones`, `datos`).
  El titular es texto plano, sin etiquetas.
- **La prueba hidrostática** (`hero.prueba`): el gráfico animado. Se editan los textos
  (`titulo`, `subtitulo`, `pie`, `sello`). **No se cambia el 200 psi ni las 2 horas** sin
  consultar: son la prueba que exige NFPA 13 y el gráfico dibuja justamente eso.
- **La lámina de la red** (`hero.lamina`): la foto con cuatro marcadores numerados y su
  leyenda. Los marcadores (`x` e `y` son porcentajes de la imagen) apuntan a partes de la
  foto actual; **si se cambia la foto, hay que recolocarlos**.
- **Cuidado con las cifras:** cada una debe poder demostrarse en el sitio (hoy: NFPA,
  4 frentes, 8 entidades = logos de la cinta, 5 obras = las de la galería). Si cambia el
  número de logos u obras, actualizar la cifra.

### 2. Cinta de logos de clientes — bloque `clientes`
- 6 a 10 logos. PNG/WebP con fondo transparente, ~110 px de alto. En tema oscuro se
  muestran sobre una pastilla blanca.

### 3. Sobre nosotros — bloque `nosotros`
- Dos párrafos, cuatro puntos, un botón y **dos fotos verticales** (3:4).

### 4. Los cuatro frentes — bloque `servicios` (+ `servicios.json`)
- El título e introducción están en `inicio.json`; **las tarjetas salen de `servicios.json`**
  y se ven también en `/servicios`.
- A la izquierda hay un índice que queda fijo mientras se baja y marca el frente activo.

### 5. Protocolo de certificación — bloque `certificacion`
- Dos párrafos arriba. **Los cuatro pasos de la línea salen de `certificaciones.json` →
  `servicio.pasos`** (no de este archivo). Exactamente 4.

### 6. Obra construida — bloque `obra`
- Los títulos están en `inicio.json`; **las tarjetas salen solas de `proyectos.json`**
  (una por proyecto, con su primera foto y cuántas fotos tiene). Un proyecto nuevo en la
  galería aparece aquí sin tocar nada más.

### 7. Mantesep — bloque `mantesep`
- Cuatro tarjetas (`items`: `t` título, `img` foto) y un botón.

### 8. Testimonio — bloque `testimonio`
- **Cuidado:** hoy dice "Cliente de proyecto hidráulico" porque **no se ha confirmado quién
  lo dijo**. Ver `PENDIENTES.md`. No inventar un nombre.

### 9. Llamado final — bloque `ctaFinal` (+ `CtaFinal.astro`)
- El bloque azul oscuro que cierra casi todas las páginas. Los textos de los botones salen
  de `inicio.json`; el título y la bajada de cada página, del JSON de esa página (`cta`).

---

## Servicios (`servicios.json`)

- **`lista`:** cada servicio tiene `id` (el ancla: `/servicios#incendios`), `num`, `titulo`,
  `icono`, `linea` (color: `azul`, `verde`, `rojo`, `lima`), `resumen`, `texto`, `tags` e
  `imagen`.
- **Cuidado con `id`:** si se cambia, se rompen los enlaces del pie y del inicio.
- **Cuidado con `icono`:** solo funcionan los de `STACK.md`.
- **`proceso`:** los 4 pasos de "cómo trabajamos". **`cta`:** el llamado final.

## Mantesep (`mantesep.json`)

- **`servicios`:** cinco tarjetas con foto, ícono, título y texto (3 por fila: 6 se ve
  mejor que 5, pero 5 es aceptable).
- **`certificacion`:** el bloque azul del final. Dice que Mantesep está certificada por la
  Corporación Autónoma Regional. **Falta el número de resolución** (ver `PENDIENTES.md`).

## Proyectos (`proyectos.json`)

- **`filtros`** (botones) e **`items`** (fotos). Cada foto tiene un `cliente` que debe
  coincidir con el `id` de un filtro; si no, solo se ve en "Todo".
- Al hacer clic en una foto se abre un **visor** con flechas y teclado (←, →, Esc). Los
  textos del visor están en `interfaz`.
- **Para agregar un proyecto:** subir fotos a `public/img/proyectos/`, agregar un filtro y
  una entrada por foto. Aparece también en el riel "Obra construida" del inicio.
- Fotos 4:3, máximo 1200 px de ancho.

## Certificaciones (`certificaciones.json`)

- **`marcos`:** tres tarjetas con sigla (NFPA, CAR, NAL). Sigla de máximo 5 letras.
- **`servicio`:** texto y los 4 pasos (los mismos que el protocolo del inicio).
- **`documentos`:** hoy dice que los certificados se envían a solicitud, porque
  **todavía no hay PDF**. Cuando lleguen, listarlos aquí.

## Contacto (`contacto.json`)

- **`formulario.servicios`:** opciones de la lista desplegable; que digan lo mismo que los
  servicios reales.
- **`formulario.aviso`:** texto legal junto a la casilla. **No cambiarlo sin consultar.**
- **`rotulos`:** los nombres de cada dato (WhatsApp, Correo…).
- **`mapa`:** no hay mapa incrustado a propósito (enviaría la IP de cada visitante a
  Google). Hay un botón que lo abre en otra pestaña. **Si piden "poner el mapa", explicar
  esto antes.**

## Textos legales (`legal.json`)

- Dos páginas, **borradores sin revisión de abogado**. Los marcadores `{razonSocial}`,
  `{direccion}`, `{ciudad}`, `{correo}` y `{telefono}` se reemplazan con los datos de
  `sitio.json`. No cambiar sin consultar.
