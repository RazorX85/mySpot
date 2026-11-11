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

## Lectura de fotos con IA (gratis)

La app usa un servicio gratis del puesto (Cloudflare Workers AI). No hace falta clave de API.

1. En la app: ⚙️ → **PIN del puesto** (se lo da el dueño) → **Guardar ajustes**.
2. Tomá la foto con la hoja **derecha**, de frente y con buena luz.
3. La app te muestra cada foto y pregunta **"¿Se lee derecha?"**. Si está de lado o de cabeza, tocá **↻ Girar** hasta que los títulos se lean bien. Si la foto parecía de lado, la app ya la giró sola: revisá que no haya quedado de cabeza.
4. Tocá **✨ Leer fotos con IA**. Los montos leídos quedan **en azul**: revisalos uno por uno contra la foto. Al editar un monto, deja de estar en azul.
5. Mirá los avisos del consolidado: si la suma no coincide con el **Total** escrito en la hoja, hay un monto mal leído.

La IA lee solo la jornada del día de la semana de la fecha elegida (por ejemplo, el bloque "Martes"). Se equivoca a veces con la letra a mano (un 7 que parece 1, por ejemplo), por eso **siempre hay que revisar**. Hay un máximo de 60 lecturas por día para todo el puesto.

Sin PIN o sin internet, la app funciona igual: los montos se digitan mirando la foto.

**Para el dueño — cómo funciona el PIN:** el PIN se guarda en dos lados y tienen que coincidir. (1) En el **servidor** (Cloudflare), una sola vez, con `npx wrangler secret put SHOP_PIN`; ahí queda secreto y **nunca** va en el código publicado. (2) En **cada teléfono**, en ⚙️ → PIN del puesto. Si el servidor no tiene PIN, la app dice "Falta configurar el PIN del puesto en el servidor". Para cambiar el PIN, se repite el paso 1 y se actualiza en los teléfonos.

**Opción avanzada:** en ⚙️ → *Avanzado* se puede usar Claude con una clave de API propia de Anthropic (lee mejor, pero cuesta unos centavos por lectura y la clave queda en el teléfono).
