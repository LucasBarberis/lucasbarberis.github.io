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
- Videos `.mp4` (H.264), cortos (≤ 30 s) y de menos de ~10 MB. GitHub rechaza archivos de más de 100 MB.
- Usar **rutas relativas a la raíz del sitio** (`/assets/images_work/...`), nunca rutas locales de la máquina (`/home/lucas/...`).
- Las fotos personales se publican sin pie: el texto alternativo describe la foto y la historia queda en el autor.

## Cómo verla localmente

Hace falta Ruby. Los pasos son para Ubuntu/Debian.

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

y después seguir los pasos de "Cómo verla localmente". Las notas de trabajo que quedan en la sesión de Claude Code de una computadora no viajan: todo lo que haya que recordar tiene que estar en este README o en los commits.

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
- [ ] Sacar los estilos inline repetidos de cada página y pasarlos a `style_dark.css`.
- [ ] `assets/pdf.jpeg`: no se usa en ninguna página. Confirmar y borrarlo.
- [ ] `assets/images_work/stream_10K-03-10-03.mp4` pesa ~75 MB. GitHub avisa por encima de 50 MB: comprimirlo o dejar solo un fragmento.
- [ ] `assets/images_work/spp_cergy.png` es el logo de Cergy-Paris Université. Decidir si se muestra como colaboración.
- [ ] Confirmar en el sitio publicado que el diseño se vea bien en teléfono.

### Contenido

- [x] Descomentar los links "Ver más →" de `en-que-ando.md`.
- [x] Llevar al sitio el contenido del primer borrador en Google Sites.
- [x] Fotos personales y figuras de investigación con pie confirmado.
- [ ] Completar `streams.md`, `spp.md` y `conducta.md` con más resultados.
- [ ] Hielo es un proyecto en preparación: no hay página todavía. Cuando haya algo, crear `hielo.md`.
- [ ] Agregar en `quien-soy.md` los links a Google Scholar, ORCID y CVar.
- [ ] Revisar con Lucas el texto de "Acerca de mí" (los datos vienen del Google Site).
