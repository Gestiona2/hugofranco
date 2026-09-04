# Qué no tocar, y cuándo llamar al proveedor

## Nunca, sin consultar

**Los textos legales.** `/politica-privacidad` y `/tratamiento-datos` son **borradores
sin revisión de abogado**, y también lo es el aviso junto a la casilla del formulario
(`contacto.json`, campo `aviso`). Cambiarlos por cuenta propia puede dejar a la empresa
expuesta ante la Superintendencia de Industria y Comercio.

**Las afirmaciones sobre certificaciones.** El sitio dice que Mantesep está certificada
por la Corporación Autónoma Regional y que se certifica ante las autoridades competentes.
Eso es verificable y alguien lo puede exigir. No adornarlo, no ampliarlo, no agregar
certificaciones que no existan.

**Las cifras.** Las cuatro de la portada (NFPA, 4 frentes, +8 entidades, 100% certificados)
se pueden sostener. **No agregar años de experiencia, obras entregadas ni clientes
satisfechos sin que el cliente entregue el dato.**

**El nombre del testimonio.** Hoy dice "Cliente de proyecto hidráulico" porque no está
confirmado quién lo dijo. Poner un nombre inventado sería atribuirle a una persona real
palabras que quizá no dijo.

**Los colores y las tipografías.** Vienen del logotipo y afectan a todo el sitio y a los
dos temas. Si lo piden, avisar el alcance antes de hacerlo.

## Cosas que se ven fáciles y no lo son

**Poner el mapa de Google dentro de la página.** Se quitó a propósito: un mapa incrustado
le envía la dirección IP de cada visitante a Google sin que la persona lo pida. Por eso
hay un botón que lo abre en otra pestaña. Si lo piden, explicar esto primero.

**Cargar tipografías o íconos desde internet.** Todo está guardado dentro del sitio, por
privacidad y para que siga funcionando en diez años. No reemplazar por enlaces a Google
Fonts ni a un CDN.

**Escribir un color directamente en un estilo.** Todo usa variables que cambian según el
tema. Un color escrito a mano se ve bien en tema claro y se rompe en tema oscuro.

**Poner un ícono que no existe.** Solo funcionan los 24 que están guardados (lista en
`STACK.md`). Cualquier otro nombre deja el espacio vacío, sin ningún aviso en la página.

**Escribir texto dentro de un archivo `.astro`.** El texto va en `src/datos/`. Si parece
que no hay campo para lo que se pide, casi siempre sí lo hay: revisar `SECCIONES.md`.

## Llamar al proveedor cuando

- La publicación falla dos veces seguidas
- Hay que cambiar dónde está alojado el sitio o a dónde apunta el dominio
- Se necesita que el formulario envíe correos de verdad (hoy abre WhatsApp o el correo)
- Se quiere agregar un blog, una tienda o algo que guarde datos
- Algo se ve roto en celular y no se sabe por qué
- Alguien pide cambiar un texto legal
