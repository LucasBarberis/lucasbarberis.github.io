---
layout: default
title: Células madre tumorales - Lucas Barberis
---

<link rel="stylesheet" href="/assets/css/style_dark.css">

<div class="back-link">
    <a href="/en-que-ando">← Volver a proyectos</a>
</div>

<div class="section">
    <h2>Células madre tumorales</h2>
    <p>Estudiamos cómo la existencia de células cancerosas con propiedades de célula madre impulsa el crecimiento de un tumor. Tomamos como referencia experimentos en tumoresferas que se hacen en el IBYME, Buenos Aires, en colaboración con el Dr. Luciano Vellón.</p>
    <p>Para esto trabajamos con tres herramientas:</p>
    <ul>
        <li><strong>Modelos de dinámica de poblaciones:</strong> ecuaciones diferenciales y sistemas dinámicos.</li>
        <li><strong>Simulaciones con agentes:</strong> simulamos muchas partículas que interactúan para modelar el crecimiento de las tumoresferas. Así medimos propiedades físicas del crecimiento y obtenemos resultados sin hacer cada experimento en el laboratorio.</li>
        <li><strong>Análisis de imágenes de laboratorio:</strong> usamos ciencia de datos para segmentar las imágenes, identificar cada célula y validar nuestros modelos [1].</li>
    </ul>
</div>

<div class="section">
    <h2>Resultados</h2>
    <div class="gallery-container">
        <div class="gallery-item">
            <video controls class="gallery-video">
                <source src="/assets/images_work/sphere_ps_0.7_24_tsteps_c.mp4" type="video/mp4">
            </video>
            <div class="gallery-description">
                <p>Las células se muestran en colores según su estado de proliferación. A partir de su distribución estadística se pueden construir modelos matemáticos.</p>
            </div>
        </div>
        <div class="gallery-item">
            <img src="/assets/images_work/sphere_nuclei_processing_horizontal.png" alt="Procesamiento de imagen de una tumoresfera" class="gallery-image">
            <div class="gallery-description">
                <p>Procesamos la imagen original (arriba a la izquierda) para identificar cada célula (segmentación).</p>
            </div>
        </div>
        <div class="gallery-item">
            <img src="/assets/images_work/sphere_tessellation_to_csc_recognition.png" alt="Identificación de células madre" class="gallery-image">
            <div class="gallery-description">
                <p>Identificamos, por ejemplo, qué células son madre en una tumoresfera experimental.</p>
            </div>
        </div>
    </div>
</div>

<div class="section">
    <h2>Qué se podría hacer</h2>
    <ul>
        <li><strong>Pregrado:</strong> medir diámetros de tumoresferas con Fiji y ajustar datos experimentales.</li>
        <li><strong>Trabajo final:</strong> efectos del medio ambiente, senescencia, quimioterapia y radioterapia, la transición de percolación y la optimización del código de simulación.</li>
        <li><strong>Doctorado:</strong> efectos espaciales, difusión de nutrientes, terapias y su impacto sobre el tejido sano.</li>
    </ul>
    <p><a href="/trabajemos-juntos">Ver propuestas →</a></p>
</div>

<div class="section">
    <h2>Gente involucrada</h2>
    <div class="card-container">
        <div class="card">
            <h3>Dr. Carlos Condat</h3>
            <p>Investigador superior de CONICET en el IFEG. Director de mi doctorado.</p>
        </div>
        <div class="card">
            <h3>Dr. Luciano Vellón</h3>
            <p>Genetista. Director del Laboratorio de Células Madre del IBYME-CONICET, donde se realizan los experimentos.</p>
        </div>
        <div class="card">
            <h3>Lic. Jerónimo Fotinós</h3>
            <p>Físico, con diploma en Ciencia de Datos. Becario doctoral.</p>
        </div>
    </div>
</div>

<div class="section">
    <h2>Publicaciones</h2>
    <p>[1] <a href="https://www.nature.com/articles/s41598-024-61558-6">Artículo en <em>Scientific Reports</em> (2024)</a>.</p>
</div>
