# Página personal — Lucas Barberis

Página web personal publicada en **https://lucasbarberis.github.io** (GitHub Pages + Jekyll).

## Para qué es esta página

El objetivo es tener un lugar al que pueda mandar a **potenciales estudiantes de grado (trabajo final) y de doctorado** para que vean, rápido y de forma visual:

1. **En qué trabajo**: mis líneas de investigación.
2. **Qué resultados obtuvimos**: mostrados sobre todo con **imágenes y videos** (simulaciones, experimentos, análisis de datos), con poco texto.
3. **En qué podrían trabajar ellos**: temas abiertos dentro de cada línea.

No busca ser un CV completo ni una lista exhaustiva de publicaciones. Para eso están Google Scholar, ORCID y el CVar.

### Qué *no* va en la página

- Ofrecimientos de becas con fechas, requisitos o promedios (se desactualizan enseguida).
- Datos inventados o de relleno (publicaciones, premios, teléfonos de ejemplo).
- Texto largo: si algo se puede mostrar con una figura o un video, va la figura o el video.
- Proyectos que todavía no están en marcha (por ahora, hielo).

## Estructura del sitio

```
index.md                 Portada: quién soy, hoja de ruta, temas, herramientas y contacto
├── quien-soy.md         Trayectoria, lo personal y fotos
├── en-que-ando.md       Resumen de cada línea de investigación con link a su página
│   ├── tumoresferas.md  Células madre tumorales y tumoresferas
│   ├── streams.md       Oncostreams (autoorganización en gliomas)
│   ├── spp.md           Materia activa / interacciones no recíprocas
│   └── conducta.md      Conducta de aves de corral
└── trabajemos-juntos.md Propuestas para pregrado, trabajo final y doctorado; contacto
```

### Plantilla de cada página de línea de investigación

Cada página temática (`tumoresferas.md`, `streams.md`, etc.) sigue el mismo esquema:

1. **La pregunta**: 2 o 3 oraciones, entendibles por alguien de tercer año de la licenciatura.
2. **Cómo la atacamos**: experimentos, simulaciones, teoría (lista corta).
3. **Resultados**: galería de imágenes y videos, cada uno con un epígrafe de 1 o 2 líneas y, si corresponde, el link al paper.
4. **Qué se podría hacer**: temas abiertos para trabajos finales o doctorado.
5. **Gente involucrada**: colaboradores y estudiantes.
6. **Publicaciones**: 2 a 5 trabajos clave, con link.

## Organización de archivos

```
_config.yml              Título del sitio y archivos que no se publican
_layouts/default.html    Estructura HTML común a todas las páginas (carga style_dark.css)
assets/
├── css/style_dark.css   Estilos (único modo: oscuro)
├── images_personal/     Fotos personales
└── images_work/         Figuras y videos de investigación
```

El sitio no usa ningún tema de GitHub: el diseño está en `_layouts/default.html` y `assets/css/style_dark.css`.

Convención para nombres en `assets/images_work/`: el prefijo indica la línea de investigación.

| Prefijo    | Línea                        |
|------------|------------------------------|
| `sphere_`  | Tumoresferas                 |
| `stream_`  | Oncostreams                  |
| `spp_`     | Materia activa               |
| `quail_`   | Conducta de aves             |

Recomendaciones para los medios:

- Imágenes en `.webp` o `.png`, de menos de ~1 MB.
- Usar **rutas relativas a la raíz del sitio** (`/assets/images_work/...`), nunca rutas locales de la máquina (`/home/lucas/...`).
- Las fotos personales se publican sin pie: el texto alternativo describe la foto y la historia queda en el autor.
- Cada imagen lleva texto alternativo (`alt`). Si es un logo, el `alt` dice qué institución es.

### Videos

Cada video se publica en **dos formatos**, para que se reproduzca en cualquier navegador (incluido Chromium en Linux, que a veces no trae H.264):

| Archivo                          | Codec            | Para qué                              |
|----------------------------------|------------------|---------------------------------------|
| `nombre_web.mp4`                 | H.264 (High)     | Fuente principal (Safari, Chrome, Firefox) |
| `nombre_web.webm`                | VP9              | Respaldo para navegadores sin H.264   |

En la página, el MP4 va primero y el WebM después:

```html
<video controls class="gallery-video">
    <source src="/assets/images_work/nombre_web.mp4" type="video/mp4">
    <source src="/assets/images_work/nombre_web.webm" type="video/webm">
</video>
```

**Parámetros de compresión** (los del video de la tumoresfera, que se reproduce bien en la página):

- MP4: `libx264`, perfil High, preset medium, CRF 30, `-g 250 -keyint_min 1 -bf 3`, formato `yuv420p`, sin audio, `-movflags +faststart` (el índice al principio del archivo; sin esto el video puede quedar trabado).
- WebM: `libvpx-vp9`, CRF 36 (o 46 si pesa más de ~10 MB), `-b:v 0`, sin audio.

Comandos (en PowerShell o bash, con ffmpeg instalado):

```bash
ffmpeg -i original.mp4 -c:v libx264 -preset medium -crf 30 -profile:v high \
  -pix_fmt yuv420p -g 250 -keyint_min 1 -bf 3 -an -movflags +faststart nombre_web.mp4

ffmpeg -i original.mp4 -c:v libvpx-vp9 -crf 36 -b:v 0 -deadline good -cpu-used 4 \
  -an nombre_web.webm
```

Tamaños: el objetivo es que cada archivo quede por debajo de ~10 MB. GitHub rechaza archivos de más de 100 MB y avisa por encima de 50 MB.

**Los originales no van al repo.** Están en la carpeta `lucasbarberis_archivos_fuera_del_repo` (en la carpeta `G:\Mi unidad\datos\devel`, al lado del repo). Si hay que volver a comprimir un video, se parte de ahí.

## Cómo verla localmente

Hace falta Ruby con Jekyll. Hay pasos para Windows y para Ubuntu. Las dos máquinas tienen que dar el mismo resultado, porque el repo no tiene nada específico de un sistema operativo.

### Windows

```powershell
# Solo la primera vez: Ruby 3.3 con DevKit
winget install RubyInstallerTeam.RubyWithDevKit.3.3
# Cerrar y volver a abrir VS Code para que tome el PATH.
# Si el instalador pregunta por ridk install, elegir 3 (MSYS2 + MINGW).

# Solo la primera vez: Jekyll
gem install jekyll webrick

# Cada vez: desde la carpeta del proyecto
jekyll serve
```

### Ubuntu / Debian

```bash
# Solo la primera vez: herramientas para compilar extensiones de Ruby
sudo apt install ruby-dev build-essential

# Solo la primera vez: Jekyll, instalado en tu usuario (sin sudo)
gem install --user-install jekyll webrick

# Cada vez: levantar el sitio desde la carpeta del proyecto
export PATH="$(ruby -e 'print Gem.user_dir')/bin:$PATH"
jekyll serve
```

Después abrir http://127.0.0.1:4000. Jekyll recarga la página al guardar cambios. Si el puerto está ocupado, agregar `--port 4001`.

**Notas para Windows:**

- La primera compilación tarda varios minutos (la carpeta está en Google Drive y el antivirus revisa los archivos). Las siguientes son más rápidas.
- Si los cambios no se actualizan al guardar, usar `jekyll serve --force_polling`.
- Con el servidor corriendo, `Ctrl+Shift+P` → **Simple Browser: Show** en VS Code abre el sitio en un panel. Para los videos conviene usar Chrome o Edge en vez del Simple Browser.
- Si un video se traba en la página pero se reproduce al arrastrarlo a Chrome, probar con **F12 → Network → Disable cache** y recargar. Jekyll responde `304` (usa la caché) y eso puede romper la reproducción de videos; con la caché desactivada se ve bien.

**Videos (ffmpeg):** para comprimir videos hace falta ffmpeg. En Windows: `winget install Gyan.FFmpeg`. En Ubuntu: `sudo apt install ffmpeg`.

La carpeta `_site/` que genera Jekyll no se versiona (está en `.gitignore`).

## Cómo publicar

GitHub Pages compila el sitio solo a partir de la rama `main`:

```bash
git add -A
git commit -m "Descripción del cambio"
git push origin main
```

Los cambios aparecen en https://lucasbarberis.github.io en uno o dos minutos. Se puede seguir el avance en la pestaña **Actions** del repositorio.

## Trabajar desde otra computadora

El repositorio es la única fuente de verdad. Para seguir en otra máquina:

```bash
git clone git@github.com:LucasBarberis/lucasbarberis.github.io.git
cd lucasbarberis.github.io
```

y después seguir los pasos de "Cómo verla localmente" del sistema que corresponda. Antes de empezar, `git pull` para traer los cambios de la otra máquina.

Las notas de trabajo que quedan en la sesión de Claude Code de una computadora no viajan: todo lo que haya que recordar tiene que estar en este README o en los commits.

Los originales de los videos y las imágenes que no están en el sitio no viajan con el repo. Si hace falta alguno, está en `lucasbarberis_archivos_fuera_del_repo`, que solo existe en la computadora donde se hizo el trabajo.

## Notas para retomar el trabajo con Claude

Para que otra sesión de Claude Code (en esta u otra computadora) siga sin preguntar lo mismo:

- **Idioma y tono:** el sitio y las conversaciones son en español rioplatense (voseo).
- **Commits:** no hacer commit ni push sin pedirlo. Antes de tocar `main`, confirmar el cambio.
- **Qué se verificó:** en la computadora Windows, el sitio se compila con `jekyll build` sin errores y se sirve en http://127.0.0.1:4000. Los videos se verificaron con Chrome sin interfaz (cargan y son H.264 High).
- **Antes de borrar archivos:** revisar que no estén referenciados en `.md`, `.html`, `.css` o `_config.yml` (buscar la ruta completa).
- **Cambios sin commitear que quedaron de la última sesión:** títulos con logo y subrayado de sección (`.section-title` en `style_dark.css`), figuras de la introducción de `tumoresferas.md` (`.intro-with-image`), galería sin recorte (`height: auto`).

## Pendientes

Lo que quedó a medio hacer de la primera versión (hecha con DeepSeek) y lo que falta:

### Limpieza

- [x] `trabajemos-juntos.md`: sacar las becas con fechas y requisitos y el teléfono de ejemplo.
- [x] Revisar los bloques comentados de publicaciones y premios: parecían inventados y se borraron.
- [x] `tumoresferas.md`: rutas, link roto, `<div>` sin cerrar, imagen vacía y front matter arreglados.
- [x] Links "← Volver" apuntan a `/`.
- [x] Unificar estilos: solo modo oscuro (`style_dark.css`), con layout propio sin tema de GitHub.
- [x] `assets/formularioLicencia.pdf`: borrado.
- [x] `_site/` fuera del repo y excluido con `.gitignore`.
- [x] `assets/pdf.jpeg`: borrado (no se usaba).
- [x] Videos grandes: los originales (75 MB y 22 MB) salieron del repo; el sitio usa las versiones comprimidas.
- [ ] Sacar los estilos inline repetidos de cada página y pasarlos a `style_dark.css`.
- [ ] `assets/images_work/spp_cergy.png` es el logo de Cergy-Paris Université. Decidir si se muestra como colaboración.
- [ ] Confirmar en el sitio publicado que el diseño se vea bien en teléfono.
- [ ] Probar que los videos se reproduzcan en el sitio publicado (en GitHub Pages el servidor maneja mejor los rangos que Jekyll local).

### Contenido

- [x] Descomentar los links "Ver más →" de `en-que-ando.md`.
- [x] Llevar al sitio el contenido del primer borrador en Google Sites.
- [x] Fotos personales y figuras de investigación con pie confirmado.
- [x] Videos de oncostreams (nemático y 10K) y de tumoresferas en la galería.
- [ ] Completar `streams.md`, `spp.md` y `conducta.md` con más resultados.
- [ ] Hielo es un proyecto en preparación: no hay página todavía. Cuando haya algo, crear `hielo.md`.
- [ ] Agregar en `quien-soy.md` los links a Google Scholar, ORCID y CVar.
- [ ] Revisar con Lucas el texto de "Acerca de mí" (los datos vienen del Google Site).
- [ ] Pie de foto para el video de 10K en `streams.md` (hoy la tarjeta no tiene descripción).
