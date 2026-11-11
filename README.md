# 🎟️ Cierre de Caja · Puesto de Lotería

Aplicación web de una sola página (SPA) para que el dependiente haga el cierre de caja al final del día:

- Caja inicial + **ventas** − **premios** = **caja final esperada**
- Una fila por sorteo, en cualquier orden: se agregan, quitan o repiten según el día
- **Nica** y **Tica** se marcan por turno (Día, Tarde, Noche; la Nica además tiene **Extra**). **La Primera** y **Honduras** no llevan turno y pueden tener uno o varios sorteos al día
- La plantilla carga las filas habituales según el día de la semana (la Nica Extra aparece los martes, sábados y domingos)
- Subtotal por **lotería**, con desglose por turno
- Fotos de los apuntes: se ven en grande para digitar, o se leen automáticamente con IA (Claude)
- Revisa que la suma coincida con el *Total* escrito en la hoja
- Arqueo opcional (billetes, monedas, SINPE Móvil, créditos, otros) → **sobrante / faltante**
- Historial, compartir por WhatsApp, imprimir/PDF, exportar CSV, respaldo y restauración
- "Nuevo día": guarda el cierre y usa la caja final como caja inicial del día siguiente
- Las loterías, sus turnos y la plantilla de cada día se configuran desde ⚙️ Ajustes

Todo funciona en el navegador. No hay servidor ni base de datos: los datos se guardan en el propio teléfono (localStorage).

## Publicar en GitHub Pages

1. Creá un repositorio nuevo en GitHub (por ejemplo `cierre-caja`).
2. Subí los archivos `index.html`, `README.md` y `.nojekyll` (botón **Add file → Upload files**).
3. Andá a **Settings → Pages**. En *Source* elegí **Deploy from a branch**, rama `main`, carpeta `/ (root)` y guardá.
4. En uno o dos minutos la app queda en `https://TU-USUARIO.github.io/cierre-caja/`.
5. En el teléfono, abrí el enlace y usá **Agregar a pantalla de inicio** para tenerla como app.

## Lectura de fotos con IA (opcional)

1. Sacá una clave de API en <https://console.anthropic.com> (necesita saldo; cada lectura cuesta unos pocos centavos de dólar).
2. En la app: ⚙️ → pegá la clave → **Guardar ajustes**.
3. Agregá las fotos → **✨ Leer fotos con IA**. Los montos leídos quedan en azul: revisalos contra la foto. Al editar un monto, deja de estar en azul.

La IA lee solo la jornada que corresponde al día de la semana de la fecha elegida (por ejemplo, el bloque "Martes").

**Seguridad:** la clave queda guardada en el navegador del dispositivo. Usala solo en teléfonos del negocio, y ponele un límite de gasto en la consola de Anthropic. Si un teléfono se pierde, revocá la clave desde la consola.

Sin clave, la app funciona igual: los montos se digitan mirando la foto.
