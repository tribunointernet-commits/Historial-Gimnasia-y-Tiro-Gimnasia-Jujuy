# Infografía interactiva: clásico norteño

## Qué se corrigió en esta versión
- **Registro AFA:** 19 partidos, con **4 victorias de Gimnasia y Tiro**, **9 empates** y **6 victorias de Gimnasia de Jujuy**.
- **Torneo Confraternidad:** 16 partidos, con **6 victorias de Gimnasia y Tiro**, **3 empates** y **7 victorias de Gimnasia de Jujuy**.
- Se incorporó el **logo SVG original de El Tribuno** (archivo `logo.svg`, proporcionado por el usuario) y escudos representativos de ambos clubes.
- Se reforzó el comportamiento **responsive** para móvil, tablet y desktop.

## Publicarla en GitHub Pages
1. Crear un repositorio público en GitHub (por ejemplo `clasico-norteno`).
2. Subir los archivos `index.html` y `logo.svg` a la raíz de la rama `main`. **Se necesitan ambos** para visualizar el logo oficial.
3. Ir a **Settings > Pages**.
4. En **Build and deployment**, elegir **Deploy from a branch**.
5. Seleccionar la rama **main** y la carpeta **/(root)**.
6. Guardar. GitHub Pages generará una URL similar a:
   `https://USUARIO.github.io/clasico-norteno/`

## Insertarla en una nota web
```html
<iframe
  id="clasico-frame"
  src="https://USUARIO.github.io/clasico-norteno/"
  title="Infografía interactiva: historial del clásico norteño"
  width="100%"
  height="1280"
  style="border:0;display:block;width:100%;max-width:100%;"
  loading="lazy"
  referrerpolicy="strict-origin-when-cross-origin">
</iframe>
```

Cambiá `USUARIO` por tu usuario real de GitHub.

## Altura automática opcional
Si tu CMS permite JavaScript junto al iframe, agregá además este bloque:

```html
<script>
window.addEventListener('message', (event) => {
  if (event.origin !== 'https://USUARIO.github.io') return;
  if (event.data?.type !== 'clasicoNortenoHeight') return;
  const frame = document.getElementById('clasico-frame');
  if (frame && event.source === frame.contentWindow) {
    frame.style.height = `${Math.ceil(event.data.height)}px`;
  }
});
</script>
```

## Responsive
La pieza:
- usa `width: 100%` para adaptarse al ancho del contenedor;
- reorganiza el hero, los escudos y las tarjetas cuando baja el ancho de pantalla;
- convierte algunos bloques a una sola columna en celular;
- mantiene la interacción con mouse y con toque en dispositivos táctiles.
