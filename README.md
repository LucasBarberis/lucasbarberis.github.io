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

## Estructura del sitio

```
index.md                 Portada: quién soy en 3 líneas, hoja de ruta, temas y contacto
├── quien-soy.md         Trayectoria breve, links a perfiles (Scholar, ORCID), lo personal
├── en-que-ando.md       Resumen de cada línea de investigación con link a su página
│   ├── tumoresferas.md  Células madre tumorales y tumoresferas
│   ├── streams.md       Oncostreams (autoorganización en gliomas)
│   ├── spp.md           Materia activa / interacciones no recíprocas
│   └── conducta.md      Conducta de aves de corral
└── trabajemos-juntos.md Cómo es trabajar conmigo, temas posibles y cómo contactarme
```

### Plantilla de cada página de línea de investigación

Cada página temática (`tumoresferas.md`, `streams.md`, etc.) sigue el mismo esquema:

1. **La pregunta** — 2 o 3 oraciones, entendibles por alguien de tercer año de la licenciatura.
2. **Cómo la atacamos** — experimentos, simulaciones, teoría (lista corta).
3. **Resultados** — galería de imágenes y videos, cada uno con un epígrafe de 1 o 2 líneas y, si corresponde, el link al paper.
4. **Qué se podría hacer** — temas abiertos para trabajos finales o doctorado.
5. **Gente involucrada** — colaboradores y estudiantes.
6. **Publicaciones** — 2 a 5 trabajos clave, con link.

## Organización de archivos

```
_config.yml              Configuración de Jekyll (título, tema)
assets/
├── css/                 Hojas de estilo
├── images_personal/     Fotos personales (portada, quién soy)
└── images_work/         Figuras y videos de investigación
```

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

## Cómo verla localmente

Requiere Ruby y Bundler.

```bash
gem install bundler jekyll
bundle init && bundle add github-pages --group jekyll_plugins   # solo la primera vez
bundle exec jekyll serve
```

Después abrir http://localhost:4000.

## Cómo publicar

GitHub Pages compila el sitio solo a partir de la rama `main`:

```bash
git add .
git commit -m "Descripción del cambio"
git push
```

Los cambios aparecen en https://lucasbarberis.github.io en uno o dos minutos.

## Pendientes

Lo que quedó a medio hacer de la primera versión (hecha con DeepSeek) y lo que falta:

### Limpieza

- [x] `trabajemos-juntos.md`: sacar las becas con fechas y requisitos y el teléfono de ejemplo. Reemplazarlo por "temas posibles" de cada línea y cómo contactarme.
- [x] Revisar los bloques comentados de publicaciones y premios en `en-que-ando.md` y `quien-soy.md`: parecen inventados. Borrarlos o reemplazarlos por datos reales.
- [x] `tumoresferas.md`: cambiar las rutas `/home/lucas/devel/personal_page/assets/...` por `/assets/...`. El video referenciado (`ps_0.7_24_tsteps_c.mp4`) en realidad se llama `sphere_ps_0.7_24_tsteps_c.mp4`.
- [x] `tumoresferas.md`: arreglar el link roto `<a href "...">` (falta el `=`), cerrar los `<div>` de la galería, sacar el `<img src="">` vacío y agregar el front matter (`---`).
- [x] Links "← Volver al inicio": apuntan a `index.md`; deberían apuntar a `/`.
- [ ] Unificar estilos: hoy conviven el tema `jekyll-theme-cayman`, `style.css` y `style_dark.css`. Elegir uno y sacar los estilos inline repetidos de cada página.
- [x] `assets/formularioLicencia.pdf`: borrado.
- [ ] `assets/pdf.jpeg`: no se usa en ninguna página. Confirmar y borrarlo.

### Contenido

- [ ] Completar `streams.md`, `spp.md` y `conducta.md` con más resultados.
- [ ] Hielo es un proyecto en preparación: no hay página todavía. Cuando haya algo, crear `hielo.md`.
- [x] Descomentar los links "Ver más →" de `en-que-ando.md` a medida que estén las páginas.
- [ ] Agregar en `quien-soy.md` los links a Google Scholar, ORCID y CVar.
- [x] Llevar al sitio el contenido del primer borrador en Google Sites.
