# Pendientes — Hugo Franco Ingeniería

Lo que quedó a medias, en orden de importancia. Actualizado el 3 de septiembre de 2026.

## Bloquean la salida a producción

### 1. Publicación sin configurar
El sitio compila y funciona, pero **no está publicado en ninguna parte**. Falta decidir
con el cliente dónde se aloja y hacer el cambio de dominio, con sus cuentas y él presente.
Ver `PUBLICAR.md`.

### 2. Textos legales sin revisión de abogado
`/politica-privacidad` y `/tratamiento-datos` son borradores razonables, redactados sobre
la Ley 1581 de 2012, pero **nadie con título los ha revisado**. Ambas páginas lo dicen en
la primera línea; ese aviso hay que quitarlo cuando estén revisadas.

### 3. NIT de la empresa
`src/datos/sitio.json` tiene `"nit": "PENDIENTE"`. Hoy no se muestra en ninguna parte,
pero debería aparecer en el pie y en los textos legales.

## Contenido que falta pedirle al cliente

### 4. Los certificados de verdad
La página `/certificaciones` existe y explica los marcos normativos, pero **no tiene un
solo documento**. En el sitio anterior ese enlace del menú no llevaba a ninguna parte, así
que no había de dónde sacarlo. Falta pedir:
- Número de resolución de la certificación de Mantesep ante la Corporación Autónoma
  Regional, y el PDF
- Matrículas profesionales del equipo, si las quieren mostrar
- Cualquier otra certificación vigente

### 5. Autor del testimonio
El testimonio de la página de inicio es real (viene del sitio anterior) pero **no se sabe
quién lo dijo**. Hoy aparece como "Cliente de proyecto hidráulico". Falta el nombre, el
cargo y la empresa, **con autorización de esa persona**.

### 6. Confirmar dos fotos de Mantesep
Las fotos de "Mantenimiento de pozos sépticos" y "Trampas de grasa" salieron del sitio
anterior con esos nombres de archivo, pero **lo que se ve en cada una no parece
corresponder**: la de pozos muestra un canal con rejillas y la de trampas muestra los
vehículos. Puede que los archivos originales estuvieran mal nombrados. Hay que
confirmarlo con el cliente antes de que alguien lo note.

### 7. Redes sociales
Las direcciones de Facebook e Instagram en `sitio.json` **están adivinadas** a partir del
nombre de la empresa. El sitio anterior tenía los íconos pero sin enlace útil. Confirmar
las direcciones reales o quitar los íconos.

### 8. Cifras de la portada
Hoy dicen NFPA, 4 frentes, 8 entidades y 5 obras. Cada una se demuestra con algo del propio
sitio (la cinta de logos y la galería), pero son tibias. Si el cliente entrega **años de
operación, número de obras o metros de red instalados**, esas cifras venden mucho más. No
inventarlas.

### 9. Horario
`"Lunes a viernes, 8:00 a.m. – 6:00 p.m."` es una suposición razonable: el sitio anterior
no lo decía. Confirmar.

## Mejoras que se pueden hacer después

### 10. Formulario con envío real por correo
Hoy el formulario abre WhatsApp o el cliente de correo del visitante. Funciona siempre y
no cuesta nada, pero **no queda registro del lado de la empresa** y en un computador sin
cliente de correo configurado el botón de correo no hace nada visible. Si se quiere envío
real, hay que agregar una función serverless — depende de dónde se aloje el sitio.

### 11. Analítica
No hay ninguna. Si el cliente quiere saber cuánta gente entra, hay que elegir una
herramienta que respete la privacidad y avisarlo en la política.

### 12. Foto de portada propia
La portada usa una imagen de renderizado de una red contra incendios que venía del sitio
anterior. Funciona muy bien, pero **es un render, no una obra suya**. Una foto real de un
cuarto de bombas de ellos sería más fuerte.

### 13. Página 404
Hecha (`src/pages/404.astro`).

### 14. Confirmar la "prueba hidrostática" con el cliente
La portada tiene un gráfico animado de una prueba hidrostática a **200 psi durante 2 horas**
(el criterio de NFPA 13 para redes de rociadores). Está rotulado como "esquema ilustrativo",
no como resultado de una obra suya. Hay que confirmar con el cliente que **así es como
prueban** sus redes (o los valores que usan) y que está de acuerdo con mostrarlo. Si usan
otros valores, se cambian en `inicio.json` (`hero.prueba`) y en la curva de `index.astro`.

### 15. Posición de los marcadores de la foto de la portada
Los cuatro números sobre la foto de la red (manómetro, válvula, montante, colector) están
puestos a mano sobre la foto actual. Si se cambia la foto, recolocarlos (ver `COMO-EDITAR.md`).
