---
layout: default
title: Células madre tumorales
description: Modelos y simulaciones del crecimiento de tumoresferas y del papel de las células madre tumorales, en colaboración con el IBYME.
---

<div class="back-link">
    <a href="/en-que-ando">← Volver a proyectos</a>
</div>

<div class="section">
    <div class="section-title">
        <h2>Células Madre Tumorales</h2>
        <img src="/assets/images_work/sphere_ibyme.png" alt="Logo de CONICET, IFEG e IBYME" class="logo del IBYME" height="40">
    </div>
    
    <div class="intro-with-image">
        <div class="intro-text">
            <p>Estudiamos cómo la existencia de células cancerosas con propiedades de célula madre impulsa el crecimiento de un tumor. Tomamos como referencia experimentos en tumoresferas que se hacen en el IBYME, Buenos Aires, en colaboración con el Dr. Luciano Vellón.</p>
            <p>Para esto trabajamos con tres herramientas:</p>
            <ul>
                <li><strong>Modelos de dinámica de poblaciones:</strong> ecuaciones diferenciales y sistemas dinámicos.</li>
                <li><strong>Simulaciones con agentes:</strong> simulamos muchas partículas que interactúan para modelar el crecimiento de las tumoresferas. Así medimos propiedades físicas del crecimiento y obtenemos resultados sin hacer cada experimento en el laboratorio.</li>
                <li><strong>Análisis de imágenes de laboratorio:</strong> usamos ciencia de datos para segmentar las imágenes, identificar cada célula y validar nuestros modelos [1].</li>
            </ul>
        </div>
        <div class="intro-figures">
            <img src="/assets/images_work/sphere_ps_0.7_slice_perspective.png" alt="Tumoresfera simulada con agentes">
        </div>
    </div>
</div>

<div class="section">
    <h2>Resultados</h2>
    <div class="gallery-container">
        <div class="gallery-item">
            <video controls class="gallery-video">
                <source src="/assets/images_work/sphere_ps_0.7_24_tsteps_web.mp4" type="video/mp4">
                <source src="/assets/images_work/sphere_ps_0.7_24_tsteps_web.webm" type="video/webm">
            </video>
            <div class="gallery-description">
                <p>Simulmos crecimieto de tumoresferas. En el video las células madre se grafican en rojo y las diferenciadas en azul. Las celulas más claras estan quiescents, es decir, no proliferan en este caso por falta de espacio. A partir de la estadística de su distribucion construimos modelos físicos y matemáticos.</p>
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
        <div class="gallery-item">
            <img src="/assets/images_work/sphere_network.webp" alt="Distribución no aleatoria de CMT" class="gallery-image">
            <div class="gallery-description">
                <p>Analizamos las propiedade de las redes que forman la células madre. En este cao, mostramos que la sCMT no pueden estar distribuidas al azar .</p>
            </div>
        </div>
        <div class="gallery-item">
            <img src="/assets/images_work/sphere_tree.png" alt="Distribución no aleatoria de CMT" class="gallery-image">
            <div class="gallery-description">
                <p>Representamos las tumoresferas en un Grafo Espacio Temporal. Algo asi como un cono de luz pero para el crecimiento de la tumoresfera. Esto nos permite estudiar la dinámica como un problema de percolación. </p>
            </div>
        </div>
        <div class="gallery-item">
            <p>Utilizamos modelos de dinámica de poblaciones para entender el crecimiento tumoral desde el análisis de bifurcaiocnes. </p>
            <img src="/assets/images_work/sphere_equations.png" alt="Modelo de Lotka-Volterra para clulas. Los linces a vece engendran liebres. " class="gallery-image">
            <p>Modelo de Lotka-Volterra para células. Los linces a vece engendran liebres.  </p>
            <img src="/assets/images_work/sphere_ajuste2.png" alt="Ajuste a datos experimetales predicen la frecuencia de las subpoblaciones." class="gallery-image">
            <p>"Ajustamos datos experimetales para predecir la frecuencia de las subpoblaciones celulares. </p>
            <img src="/assets/images_work/sphere_bifurcationXY.png" alt="Dinmica subyacente" class="gallery-image">
            <div class="gallery-description">
            <p>Analizamos la dinámica subyacente. </p>       
        </div>  
    </div>
</div>

<div class="section">
    <h2>Qué hay para hacer</h2>
    <ul>
        <li><strong>Pregrado.</strong> Medir diámetros de tumoresferas experimentales, compactación, grados de diferenciación. Ajustar datos experimentales.</li>
        <li><strong>Trabajo final.</strong> Modelo mínimo de dinámica de poblaciones. Mediciones sobre experimentos con SOX2, abundancia relativa, grado de diferenciacion. Reprogramación celular. </li>
        <li><strong>Doctorado.</strong> Implementar  efectos espaciales, difusión de nutrientes y oxigeno, microambiente tumoral, señalización, reprogramación, terapias (inmuno, quimio, radio) y su impacto sobre el tejido sano. Modelos en PDE de dinámica de poblaciones. Modelos estocasticos sobre el Grafo Espacio Temporal. </li>
    </ul>
    <p><a href="/trabajemos-juntos">Ver propuestas →</a></p>
</div>

<div class="section">
    <h2>Gente involucrada</h2>
    <div class="card-container">
           <div class="card">
            <h3>Dr. Luciano Vellón</h3>
            <p>Genetista. Director del Laboratorio de Células Madre del IBYME-CONICET, donde se realizan los experimentos.</p>
        </div>
             <div class="card">
            <h3>Dr. Carlos Condat</h3>
            <p>Investigador superior de CONICET en el IFEG. Director de mi doctorado.</p>
        </div>
        <div class="card">
            <h3>Lic. Jerónimo Fotinós</h3>
            <p>Físico, con diploma en Ciencia de Datos. Becario doctoral a punto de recibirse. Realizó los códigos de simulación y segmentación en las imágenes. Ideaó el Grafo Espacio Temporal. Demostró teóricamente el límite de percolación. Ideó una forma termodínamica de medir propiedades mecánicas. </p>
        </div>
               <div class="card">
            <h3>Ing. Jeremías Castro Romero</h3>
            <p>Bioingeneiero en el IBYME recién recibido cultivando esferoides y , tomando imágenes y procesándolas. </p>
        </div>
    </div>
</div>

<div class="section">
    <h2>Publicaciones</h2>
    <p>[1] <a href="https://www.nature.com/articles/s41598-024-61558-6">Artículo en <em>Scientific Reports</em> (2024)</a>.</p>
</div>
