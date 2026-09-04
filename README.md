# Sitio web de Hugo Franco Ingeniería S.A.S.

Ingeniería hidráulica, sanitaria, ambiental y redes de protección contra incendios.
Manizales, Caldas.

## Para el dueño del sitio

No hace falta leer esto. Abre `TUTORIAL.md`: explica cómo pedirle cambios al asistente
hablándole en español normal.

## Para quien edite el sitio

Lee `AGENTS.md` y después `conocimiento_generado/` completo.

**La regla que ordena todo:** el texto vive en `src/datos/`, un archivo por página. Los
archivos `.astro` tienen el diseño y ninguna frase escrita a mano.

## Ver el sitio mientras se edita

```bash
npm install     # solo la primera vez
npm run dev     # abre http://localhost:4321
```

## Compilar

```bash
npm run build   # deja el sitio listo en dist/
```

Hecho con Astro 7 y Tailwind 4. Sitio estático: sin base de datos ni servidor.
