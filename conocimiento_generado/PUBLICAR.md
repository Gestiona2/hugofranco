# Cómo se publica este sitio

## Estado actual

⚠️ **La publicación todavía no está configurada.** El sitio está construido y compila
bien, pero no se ha decidido con el cliente dónde vive ni se ha conectado nada.

Hoy el dominio `hugofrancoingenieria.com` apunta al WordPress anterior. Ese cambio se hace
**con el cliente presente**, con sus cuentas, y es el último paso.

Ver `PENDIENTES.md`.

## Lo que hay que decidir con el cliente

1. **Dónde se aloja.** El sitio es estático: sirve cualquier hosting. Las cuatro rutas
   soportadas son el hosting que ya tenga, Cloudflare Pages, Netlify o GitHub Pages.
2. **A nombre de quién.** El dominio, la cuenta de GitHub y el hosting van **a nombre del
   cliente**, creados con él presente. El proveedor no conserva credenciales ajenas.
3. **Qué pasa con el WordPress viejo.** Conviene dejarlo apagado pero respaldado durante
   unas semanas antes de borrarlo.

## Cómo funcionará una vez configurado

1. Se hace el cambio en el texto o la foto
2. Se ve en la vista previa (`npm run dev`)
3. El cliente aprueba
4. Se guarda y se publica
5. **Tarda de 2 a 4 minutos.** Si no lo ve, recargar con Ctrl+F5

**El compilado se hace en la nube.** El cliente nunca compila para publicar.

## Si la publicación falla

El sitio **sigue mostrando la versión anterior**. No se rompe, no se cae, no se pierde
nada. Avisar al proveedor y esperar.

## Cómo deshacer

Cada publicación queda guardada. Se puede volver a la anterior sin perder nada. Si el
cliente dice "quedó mal, devuélvelo", se puede: díselo, porque es lo que hace que se
atreva a pedir cambios.

## Guardar el compilado

Al cerrar la entrega hay que archivar también la carpeta `dist/` compilada, no solo el
código. Es lo que mantiene el sitio recuperable dentro de diez años, aunque las
herramientas de hoy ya no existan.
