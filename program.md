---
layout: page
title: Programa
short_title: Programa
permalink: /programa/
img_link: ../assets/img/charla.jpg
---

<style>
  .reveal {
    opacity: 0;
    transform: translateY(40px);
    transition: opacity 0.7s ease-out, transform 0.7s ease-out;
  }
  .reveal.active {
    opacity: 1;
    transform: translateY(0);
  }
  
  /* Efecto hover para las tarjetas de charla */
  .charla-card {
    transition: transform 0.2s ease, box-shadow 0.2s ease;
    cursor: pointer;
  }
  .charla-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 20px rgba(0,0,0,0.12) !important;
  }

  /* Estilos del Modal (Minipage) */
  .charla-modal-overlay {
    display: none;
    position: fixed;
    z-index: 9999;
    top: 0; left: 0; width: 100%; height: 100%;
    background: rgba(0, 0, 0, 0.7);
    backdrop-filter: blur(5px);
    justify-content: center;
    align-items: center;
    opacity: 0;
    transition: opacity 0.3s ease;
  }
  .charla-modal-overlay.show {
    display: flex;
    opacity: 1;
  }
  .charla-modal-content {
    background: #ffffff;
    width: 90%;
    max-width: 850px;
    max-height: 90vh;
    overflow-y: auto;
    padding: 40px;
    border-radius: 16px;
    box-shadow: 0 10px 40px rgba(0,0,0,0.3);
    position: relative;
    transform: translateY(20px);
    transition: transform 0.3s ease;
  }
  .charla-modal-overlay.show .charla-modal-content {
    transform: translateY(0);
  }
  .cerrar-modal-btn {
    position: absolute;
    top: 20px;
    right: 25px;
    font-size: 35px;
    color: #444;
    cursor: pointer;
    line-height: 1;
    text-decoration: none;
    font-weight: bold;
  }
  .cerrar-modal-btn:hover { color: #47001e; }

  /* Estructura interior del modal */
  .modal-layout-top {
    display: flex;
    flex-wrap: wrap;
    gap: 30px;
    margin-bottom: 20px;
  }
  
  /* =========================================
     DISEÑO CREDENCIAL (MARCO FOTO + SUBMARCO)
     ========================================= */
  
  .modal-marco-foto {
    width: 240px;
    height: 240px;
    background-color: #47001e; 
    padding: 6px; 
    clip-path: polygon(30px 0%, calc(100% - 30px) 0%, 100% 30px, 100% calc(100% - 30px), calc(100% - 30px) 100%, 30px 100%, 0% calc(100% - 30px), 0% 30px);
    z-index: 2;
    position: relative;
  }
  
  .modal-foto-recorte {
    width: 100%;
    height: 100%;
    object-fit: cover;
    background-color: #fff;
    clip-path: polygon(24px 0%, calc(100% - 24px) 0%, 100% 24px, 100% calc(100% - 24px), calc(100% - 24px) 100%, 24px 100%, 0% calc(100% - 24px), 0% 24px);
  }

  .modal-submarco {
    width: 210px; 
    background-color: #47001e; 
    padding: 0 3px 3px 3px; 
    clip-path: polygon(0% 0%, 100% 0%, 100% calc(100% - 15px), calc(100% - 15px) 100%, 15px 100%, 0% calc(100% - 15px));
    margin-top: -15px; 
    z-index: 1;
    position: relative;
  }

  .modal-submarco-interno {
    background-color: #fff;
    height: 100%;
    padding: 25px 10px 15px 10px; 
    text-align: center;
    display: flex;
    flex-direction: column;
    justify-content: center;
    clip-path: polygon(0% 0%, 100% 0%, 100% calc(100% - 12px), calc(100% - 12px) 100%, 12px 100%, 0% calc(100% - 12px));
  }

  /* Cajas de la derecha */
  .modal-boxes-right {
    flex: 1;
    min-width: 250px;
    display: flex;
    flex-direction: column;
    gap: 15px;
  }
  .caja-1 {
    border: 2px solid #47001e;
    padding: 20px;
    border-radius: 8px;
    background-color: #fff;
  }
  .caja-2 {
    border: 1px solid #ddd;
    padding: 20px;
    border-radius: 8px;
    background-color: #f7f9fc;
    flex-grow: 1;
  }
  .caja-3 {
    border: 1px solid #ddd;
    padding: 25px;
    border-radius: 8px;
    background-color: #f7f9fc;
  }

  /* =========================================
     ESTILOS LÍNEA DE TIEMPO (TIMELINE POSTERS)
     ========================================= */
  .timeline-container {
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    position: relative;
    margin: 80px auto 50px auto; 
    width: 100%;
    max-width: 1000px;
  }
  
  /* Línea gris base (Ajustada matemáticamente para 4 puntos) */
  .timeline-line {
    position: absolute;
    top: 24px; 
    left: 12.5%; 
    width: 75%; 
    height: 4px;
    background-color: #e2e8f0; 
    z-index: 1;
    border-radius: 2px;
  }
  
  /* ========================================================
     LA LÍNEA DE PROGRESO BURDEOS
     Cambia el "width: 0%;" a "33%", "66%" o "100%" 
     según vayan avanzando las fechas.
     ======================================================== */
  .timeline-line::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    height: 100%;
    width: 0%; /* <-- CAMBIA ESTE PORCENTAJE PARA AVANZAR LA LÍNEA */
    background-color: #47001e;
    border-radius: 2px;
    transition: width 0.5s ease;
  }

  .timeline-step {
    position: relative;
    z-index: 2;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    flex: 1;
  }
  
  .timeline-bg-number {
    position: absolute;
    top: -45px;
    font-size: 4.5em;
    font-weight: 900;
    color: #47001e;
    opacity: 0.08; 
    z-index: -1;
    line-height: 1;
    user-select: none;
  }
  
  .timeline-dot {
    width: 24px;
    height: 24px;
    background-color: #ffffff;
    border: 5px solid #47001e;
    border-radius: 50%;
    margin-bottom: 20px;
    box-shadow: 0 0 0 5px rgba(71, 0, 30, 0.1);
    transition: transform 0.3s ease, box-shadow 0.3s ease, background-color 0.3s ease;
  }
  
  /* Clase especial para el punto "activo" o rellenado */
  .timeline-dot.active {
    background-color: #47001e;
    box-shadow: 0 0 0 5px rgba(71, 0, 30, 0.25);
  }

  .timeline-step:hover .timeline-dot {
    transform: scale(1.2);
    box-shadow: 0 0 0 8px rgba(71, 0, 30, 0.15);
  }
  
  .timeline-date {
    font-size: 0.9em;
    color: #47001e;
    font-weight: 800;
    margin-bottom: 8px;
    text-transform: uppercase;
    letter-spacing: 1px;
  }
  
  .timeline-text {
    font-size: 1.05em;
    color: #333;
    font-weight: 600;
    line-height: 1.3;
  }
  
  @media (max-width: 768px) {
    .timeline-container {
      flex-direction: column;
      gap: 50px;
    }
    .timeline-line { display: none; }
    .timeline-step {
      flex-direction: row;
      text-align: left;
      gap: 20px;
      align-items: flex-start;
      width: 100%;
    }
    .timeline-bg-number {
      top: -20px;
      left: 30px;
      font-size: 3.5em;
    }
    .timeline-dot {
      margin-bottom: 0;
      margin-top: 5px;
    }
    .timeline-content {
      padding-top: 5px;
    }
  }

  /* Botón Inscripción */
  .btn-inscripcion {
    background-color: #47001e;
    color: #ffffff !important;
    padding: 15px 35px;
    border-radius: 30px;
    text-decoration: none;
    font-weight: 700;
    font-size: 1.1em;
    box-shadow: 0 6px 15px rgba(71,0,30,0.25);
    display: inline-block;
    transition: all 0.3s ease;
  }
  .btn-inscripcion:hover {
    background-color: #63002a;
    transform: translateY(-3px);
    box-shadow: 0 8px 20px rgba(71,0,30,0.35);
  }
</style>

<div class="reveal">
	<h3 align="justify" style="font-size: 1.2em; line-height: 1.6; max-width: 1200px; margin: 0;">
			La asignación de horarios para cada charlista se encuentra sujeta a disponibilidad de los mismos pero los horarios tentativos para el evento son los siguientes:
	</h3>
	<p align="center" style="margin-top: 40px;"> <img src="{{ "/assets/img/material26/iterinario_preventivo.png" | relative_url }}" alt="Itinerario" width="600" style="max-width: 100%"/>
	</p>
</div>

<br>
<hr>
<br>

<div class="reveal">
	<h2 align="left" style="font-weight: bold;">Actividades</h2>
	<h3 align="justify" style="font-size: 1.2em; line-height: 1.6; max-width: 1200px; margin: 0;">
		La edición 2026 de CANELOS tendrá lugar los días 8 y 9 de Octubre, de forma presencial. 
		Serán dos días llenos de charlas plenarias técnicas y presentaciones de empresas, 
		con participación de destacados invitados de la academia e industria microelectrónica, tanto de Chile como del extranjero.
		Además, se incluyen instancias de networking y un foro para cerrar el seminario discutiendo sobre el futuro de la microelectrónica en nuestro país.
	</h3>
	<p align="center" style="margin-top: 40px;"> <img src="{{ "/assets/img/canelos_poster_brillante.jpg" | relative_url }}" alt="Poster CANELOS" width="600" style="max-width: 100%"/> </p>
</div>

<br>
<hr>
<br>

<div class="reveal">
	<h2 align="left" style="font-weight: bold;">Talleres</h2>
	<h3 align="center" style="font-weight: bold; margin-top: 40px; margin-bottom: 40px;">Próximamente...</h3>
</div>

<br>
<hr>
<br>

<div class="reveal">
	<h2 align="left" style="font-weight: bold; margin-bottom: 40px; display: flex; align-items: center; flex-wrap: wrap; gap: 12px;">
	    Charlas plenarias
	    <span style="font-size: 0.55em; font-weight: 500; color: #777; font-style: italic; letter-spacing: 0.5px; padding-top: 4px;">
	        (Haz clic en cada charla para más detalles)
	    </span>
	</h2>

    <!-- LISTA PRINCIPAL (TARJETAS SIMPLES - TODOS CON BURDEOS) -->
    <div style="display: flex; flex-direction: column; align-items: center; gap: 20px; width: 100%;">

        <!-- Charla 1 -->
        <div class="charla-card reveal" onclick="abrirCharla('pedro')" style="display: flex; align-items: center; gap: 25px; width: 100%; background-color: #f7f9fc; padding: 20px 30px; border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.05); border-left: 5px solid #47001e;">
            <img src="{{ "/assets/img/material26/pedro_toledo.png" | relative_url }}" alt="Pedro Toledo" style="width: 90px; height: 90px; border-radius: 10px; object-fit: cover;">
            <div style="text-align: left;">
                <h3 style="margin: 0 0 5px 0; font-size: 1.4em; color: #222; font-weight: 700;">Pedro Toledo</h3>
                <h4 style="margin: 0; font-size: 1.1em; color: #47001e; font-weight: 600; font-style: italic; line-height: 1.3;">"Nanoscale Digital-Based Analog Processing: Circuits and Systems Solutions..."</h4>
            </div>
        </div>
        
        <!-- Charla 2 -->
        <div class="charla-card reveal" onclick="abrirCharla('joel')" style="display: flex; align-items: center; gap: 25px; width: 100%; background-color: #f7f9fc; padding: 20px 30px; border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.05); border-left: 5px solid #47001e;">
            <img src="{{ "/assets/img/material26/joel_gak.jpg" | relative_url }}" alt="Joel Gak" style="width: 90px; height: 90px; border-radius: 10px; object-fit: cover;">
            <div style="text-align: left;">
                <h3 style="margin: 0 0 5px 0; font-size: 1.4em; color: #222; font-weight: 700;">Joel Gak</h3>
                <h4 style="margin: 0; font-size: 1.1em; color: #47001e; font-weight: 600; font-style: italic; line-height: 1.3;">"Desafíos y técnicas de diseño en implantables"</h4>
            </div>
        </div>

        <!-- Charla 3 -->
        <div class="charla-card reveal" onclick="abrirCharla('exp3')" style="display: flex; align-items: center; gap: 25px; width: 100%; background-color: #f7f9fc; padding: 20px 30px; border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.05); border-left: 5px solid #47001e;">
            <img src="https://placehold.co/300x300/eeeeee/999999?text=Foto+3" alt="Expositor 3" style="width: 90px; height: 90px; border-radius: 10px; object-fit: cover;">
            <div style="text-align: left;">
                <h3 style="margin: 0 0 5px 0; font-size: 1.4em; color: #222; font-weight: 700;">Expositor 3</h3>
                <h4 style="margin: 0; font-size: 1.1em; color: #47001e; font-weight: 600; font-style: italic; line-height: 1.3;">"Por Anunciar"</h4>
            </div>
        </div>

        <!-- Charla 4 -->
        <div class="charla-card reveal" onclick="abrirCharla('exp4')" style="display: flex; align-items: center; gap: 25px; width: 100%; background-color: #f7f9fc; padding: 20px 30px; border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.05); border-left: 5px solid #47001e;">
            <img src="https://placehold.co/300x300/eeeeee/999999?text=Foto+4" alt="Expositor 4" style="width: 90px; height: 90px; border-radius: 10px; object-fit: cover;">
            <div style="text-align: left;">
                <h3 style="margin: 0 0 5px 0; font-size: 1.4em; color: #222; font-weight: 700;">Expositor 4</h3>
                <h4 style="margin: 0; font-size: 1.1em; color: #47001e; font-weight: 600; font-style: italic; line-height: 1.3;">"Por Anunciar"</h4>
            </div>
        </div>

        <!-- Charla 5 -->
        <div class="charla-card reveal" onclick="abrirCharla('exp5')" style="display: flex; align-items: center; gap: 25px; width: 100%; background-color: #f7f9fc; padding: 20px 30px; border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.05); border-left: 5px solid #47001e;">
            <img src="https://placehold.co/300x300/eeeeee/999999?text=Foto+5" alt="Expositor 5" style="width: 90px; height: 90px; border-radius: 10px; object-fit: cover;">
            <div style="text-align: left;">
                <h3 style="margin: 0 0 5px 0; font-size: 1.4em; color: #222; font-weight: 700;">Expositor 5</h3>
                <h4 style="margin: 0; font-size: 1.1em; color: #47001e; font-weight: 600; font-style: italic; line-height: 1.3;">"Por Anunciar"</h4>
            </div>
        </div>

    </div>
</div>

<br>
<hr>
<br>

<!-- ========================================== -->
<!-- SECCIÓN: SESIÓN DE POSTERS                 -->
<!-- ========================================== -->
<div class="reveal">
	<h2 align="left" style="font-weight: bold; margin-bottom: 20px;">Sesión de Posters</h2>
	
    <p style="font-size: 1.1em; line-height: 1.6; color: #444; max-width: 1000px; margin-bottom: 30px;">
        La Sesión de Posters de CANELOS 2026 es el espacio ideal para que estudiantes, investigadores y profesionales presenten sus últimos trabajos e innovaciones en microelectrónica. Durante esta instancia, los autores podrán interactuar directamente con expertos de la industria y la academia en un ambiente colaborativo y cercano.
    </p>

    <!-- Línea de Tiempo Profesional -->
    <div class="timeline-container">
        <div class="timeline-line"></div>
        
        <!-- Paso 00 (Punto inicial / Actual) -->
        <div class="timeline-step">
            <div class="timeline-bg-number">00</div>
            <!-- Nota que este punto tiene la clase "active" para verse relleno -->
            <div class="timeline-dot active"></div>
            <div class="timeline-content">
                <div class="timeline-date">xx de xx, 2026</div>
                <div class="timeline-text">Inicio de<br>Postulaciones</div>
            </div>
        </div>

        <!-- Paso 01 -->
        <div class="timeline-step">
            <div class="timeline-bg-number">01</div>
            <!-- Cuando llegue este paso, puedes agregarle la clase "active" al div de abajo -->
            <div class="timeline-dot"></div>
            <div class="timeline-content">
                <div class="timeline-date">xx de xx, 2026</div>
                <div class="timeline-text">Cierre de<br>Postulaciones</div>
            </div>
        </div>
        
        <!-- Paso 02 -->
        <div class="timeline-step">
            <div class="timeline-bg-number">02</div>
            <div class="timeline-dot"></div>
            <div class="timeline-content">
                <div class="timeline-date">xx de xx, 2026</div>
                <div class="timeline-text">Notificación de<br>Resultados</div>
            </div>
        </div>
        
        <!-- Paso 03 -->
        <div class="timeline-step">
            <div class="timeline-bg-number">03</div>
            <div class="timeline-dot"></div>
            <div class="timeline-content">
                <div class="timeline-date">08 de octubre, 2026</div>
                <div class="timeline-text">Inicio del<br>Evento</div>
            </div>
        </div>
    </div>

    <!-- Botón de Inscripción -->
    <div style="text-align: center; margin-top: 50px; margin-bottom: 30px;">
        <a href="https://chipusm.github.io/CANELOS/registro/" class="btn-inscripcion">
            Haz clic aquí para ir a la inscripción
        </a>
    </div>

</div>


<!-- ========================================== -->
<!-- EL MODAL (MINIPAGE QUE SE ABRE AL HACER CLIC) -->
<!-- ========================================== -->
<div id="modalCharlas" class="charla-modal-overlay" onclick="cerrarCharlaFuera(event)">
  <div class="charla-modal-content">
    <a href="#!" class="cerrar-modal-btn" onclick="cerrarCharla()">&times;</a>
    
    <div class="modal-layout-top">
      
      <!-- DISEÑO CREDENCIAL -->
      <div style="display: flex; flex-direction: column; align-items: center; filter: drop-shadow(0 10px 16px rgba(0,0,0,0.25)); flex-shrink: 0; margin: auto;">
        
        <!-- PARTE SUPERIOR -->
        <div class="modal-marco-foto">
            <img id="m-foto" src="" class="modal-foto-recorte" alt="Foto">
        </div>
        
        <!-- PARTE INFERIOR -->
        <div class="modal-submarco">
            <div class="modal-submarco-interno">
                <h3 id="m-nombre-badge" style="margin: 0; font-size: 1.3em; font-weight: 800; color: #222;">Nombre</h3>
                <p id="m-cargo-badge" style="margin: 6px 0; font-size: 0.9em; color: #555; line-height: 1.2;">Cargo / Trabajo</p>
                <p id="m-afiliacion-badge" style="margin: 0; font-size: 0.9em; color: #47001e; font-weight: 700;">Institución / País</p>
            </div>
        </div>

      </div>
      
      <div class="modal-boxes-right">
        <!-- Caja 1: Título -->
        <div class="caja-1" style="display: flex; flex-direction: column; justify-content: center;">
            <h4 id="m-titulo" style="margin: 0; font-size: 1.35em; color: #47001e; font-style: italic; line-height: 1.4; font-weight: 800;">"Título de la charla"</h4>
        </div>
        <!-- Caja 2: Biografía -->
        <div class="caja-2">
            <p id="m-bio" style="margin: 0; font-size: 1em; color: #444; line-height: 1.6;">Texto de la biografía...</p>
        </div>
      </div>
    </div>

    <!-- Caja 3: Descripción de la Charla -->
    <div class="caja-3">
        <h4 style="margin: 0 0 12px 0; font-size: 1.2em; color: #47001e; font-weight: bold;">Sobre la charla</h4>
        <p id="m-desc" style="margin: 0; font-size: 1em; color: #444; line-height: 1.6;">Descripción...</p>
    </div>

  </div>
</div>

<!-- ========================================== -->
<!-- SCRIPTS (Animaciones y Lógica del Modal)   -->
<!-- ========================================== -->
<script>
  // 1. BASE DE DATOS DE LOS CHARLISTAS
  const datosCharlas = {
    'pedro': {
      foto: '{{ "/assets/img/material26/pedro_toledo.png" | relative_url }}',
      nombre: 'Pedro Toledo',
      cargo: 'Director / Investigador',
      afiliacion: 'CASS iDL / País',
      titulo: '"Nanoscale Digital-Based Analog Processing: Circuits and Systems Solutions for Emerging Applications and Technologies"',
      bio: 'Pedro Toledo es un reconocido investigador enfocado en el procesamiento analógico digital. [Añade aquí más detalles sobre su experiencia, estudios y aportes a la industria].',
      desc: 'En esta presentación se abordarán los desafíos actuales del procesamiento analógico en escalas nanométricas. Se presentarán soluciones a nivel de circuitos y sistemas que habilitan nuevas aplicaciones tecnológicas, optimizando el consumo energético y mejorando el rendimiento en arquitecturas modernas.'
    },
    'joel': {
      foto: '{{ "/assets/img/material26/joel_gak.jpg" | relative_url }}',
      nombre: 'Joel Gak',
      cargo: 'Profesor Titular',
      afiliacion: 'Universidad Católica del Uruguay',
      titulo: '"Desafíos y técnicas de diseño en implantables"',
      bio: 'Joel Gak es un destacado investigador invitado, experto en el desarrollo de tecnologías biomédicas y sistemas de bajo consumo de potencia para aplicaciones en salud.',
      desc: 'El diseño de dispositivos médicos implantables requiere técnicas de vanguardia para asegurar miniaturización extrema, biocompatibilidad y un consumo ultra bajo de potencia. En esta charla exploraremos las metodologías y barreras actuales que enfrenta la industria microelectrónica en el campo de la biomedicina.'
    },
    'exp3': {
      foto: 'https://placehold.co/300x300/eeeeee/999999?text=Foto+3',
      nombre: 'Expositor 3',
      cargo: 'Cargo por confirmar',
      afiliacion: 'Institución',
      titulo: '"Por Anunciar"',
      bio: 'Pronto revelaremos la biografía de nuestro próximo expositor destacado. Mantente atento a nuestras actualizaciones.',
      desc: 'Pronto revelaremos la información detallada sobre esta charla plenaria y las temáticas específicas que nuestro expositor compartirá con los asistentes del evento.'
    },
    'exp4': {
      foto: 'https://placehold.co/300x300/eeeeee/999999?text=Foto+4',
      nombre: 'Expositor 4',
      cargo: 'Cargo por confirmar',
      afiliacion: 'Institución',
      titulo: '"Por Anunciar"',
      bio: 'Pronto revelaremos la biografía de nuestro próximo expositor destacado. Mantente atento a nuestras actualizaciones.',
      desc: 'Pronto revelaremos la información detallada sobre esta charla plenaria y las temáticas específicas que nuestro expositor compartirá con los asistentes del evento.'
    },
    'exp5': {
      foto: 'https://placehold.co/300x300/eeeeee/999999?text=Foto+5',
      nombre: 'Expositor 5',
      cargo: 'Cargo por confirmar',
      afiliacion: 'Institución',
      titulo: '"Por Anunciar"',
      bio: 'Pronto revelaremos la biografía de nuestro próximo expositor destacado. Mantente atento a nuestras actualizaciones.',
      desc: 'Pronto revelaremos la información detallada sobre esta charla plenaria y las temáticas específicas que nuestro expositor compartirá con los asistentes del evento.'
    }
  };

  // 2. FUNCIONES DEL MODAL
  function abrirCharla(id) {
    const data = datosCharlas[id];
    if(!data) return;

    // Rellenamos la credencial
    document.getElementById('m-foto').src = data.foto;
    document.getElementById('m-nombre-badge').innerText = data.nombre;
    document.getElementById('m-cargo-badge').innerText = data.cargo;
    document.getElementById('m-afiliacion-badge').innerText = data.afiliacion;

    // Rellenamos las Cajas limpias
    document.getElementById('m-titulo').innerText = data.titulo;
    document.getElementById('m-bio').innerText = data.bio;
    document.getElementById('m-desc').innerText = data.desc;

    // Mostramos el modal
    document.getElementById('modalCharlas').classList.add('show');
    document.body.style.overflow = 'hidden';
  }

  function cerrarCharla() {
    document.getElementById('modalCharlas').classList.remove('show');
    document.body.style.overflow = 'auto'; // Devolvemos el scroll
  }

  function cerrarCharlaFuera(event) {
    if (event.target === document.getElementById('modalCharlas')) {
      cerrarCharla();
    }
  }

  // 3. ANIMACIÓN REVEAL AL HACER SCROLL
  document.addEventListener('DOMContentLoaded', function () {
    const items = document.querySelectorAll('.reveal');
    const observer = new IntersectionObserver((entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add('active');
          observer.unobserve(entry.target);
        }
      });
    }, { threshold: 0.15 });

    items.forEach((item) => observer.observe(item));
  });
</script>
