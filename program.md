---
layout: page
title: Actividades
short_title: Actividades
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
  
  /* Tarjetas genéricas */
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
    z-index: 10;
  }
  .cerrar-modal-btn:hover { color: #0284c7; }

  /* CAJAS GENERALES PARA EL MODAL */
  .caja-1 {
    border: 2px solid #ddd;
    padding: 20px;
    border-radius: 8px;
    background-color: #fff;
    transition: border-color 0.3s ease;
  }
  .caja-2 {
    border: 1px solid #ddd;
    padding: 20px;
    border-radius: 8px;
    background-color: #f7f9fc;
  }
  .caja-3 {
    border: 1px solid #ddd;
    padding: 25px;
    border-radius: 8px;
    background-color: #f7f9fc;
  }

  /* ESTRUCTURA MODAL CHARLAS (Diseño Credencial) */
  #layout-charlas .modal-layout-top {
    display: flex;
    flex-wrap: wrap;
    gap: 30px;
    margin-bottom: 20px;
    align-items: center;
  }
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
  .modal-boxes-right {
    flex: 1;
    min-width: 250px;
    display: flex;
    flex-direction: column;
    gap: 15px;
  }

  /* ESTRUCTURA MODAL TALLERES (Columnas completas) */
  #layout-talleres {
    display: none; /* Se activa mediante JS */
    flex-direction: column;
    gap: 15px;
  }
  #layout-talleres #m-taller-logo-box {
    text-align: left;
    margin-bottom: 5px;
  }
  #layout-talleres #m-taller-logo-img {
    max-width: 220px;
    height: auto;
    object-fit: contain;
  }
  #m-taller-logo-placeholder {
    width: 180px; 
    height: 60px; 
    background: #f7f9fc; 
    border: 2px dashed #cbd5e1; 
    display: flex; 
    align-items: center; 
    justify-content: center; 
    color: #94a3b8; 
    font-weight: 800; 
    font-size: 1.2em; 
    border-radius: 6px; 
    letter-spacing: 2px;
  }
  
  /* TEMAS DE COLOR PARA TALLERES */
  /* Tema Celeste (Taller 4) */
  #layout-talleres.tema-celeste .caja-1 { border-color: #0284c7; }
  #layout-talleres.tema-celeste #m-taller-titulo { color: #0284c7; }
  #layout-talleres.tema-celeste #m-taller-desc-titulo { color: #0284c7; }
  
  /* Tema Rojo (Talleres 1, 2 y 3) */
  #layout-talleres.tema-rojo .caja-1 { border-color: #47001e; }
  #layout-talleres.tema-rojo #m-taller-titulo { color: #47001e; }
  #layout-talleres.tema-rojo #m-taller-desc-titulo { color: #47001e; }

  /* =========================================
     ESTILOS LÍNEA DE TIEMPO
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
  .timeline-line {
    position: absolute;
    top: 24px; left: 12.5%; width: 75%; height: 4px;
    background-color: #e2e8f0; z-index: 1; border-radius: 2px;
  }
  .timeline-line::before {
    content: ''; position: absolute; top: 0; left: 0;
    height: 100%; width: 0%; background-color: #47001e;
    border-radius: 2px; transition: width 0.5s ease;
  }
  .timeline-step {
    position: relative; z-index: 2; display: flex; flex-direction: column;
    align-items: center; text-align: center; flex: 1;
  }
  .timeline-bg-number {
    position: absolute; top: -45px; font-size: 4.5em; font-weight: 900;
    color: #47001e; opacity: 0.08; z-index: -1; line-height: 1; user-select: none;
  }
  .timeline-dot {
    width: 24px; height: 24px; background-color: #ffffff;
    border: 5px solid #47001e; border-radius: 50%; margin-bottom: 20px;
    box-shadow: 0 0 0 5px rgba(71, 0, 30, 0.1);
    transition: transform 0.3s ease, box-shadow 0.3s ease, background-color 0.3s ease;
  }
  .timeline-dot.active {
    background-color: #47001e; box-shadow: 0 0 0 5px rgba(71, 0, 30, 0.25);
  }
  .timeline-step:hover .timeline-dot {
    transform: scale(1.2); box-shadow: 0 0 0 8px rgba(71, 0, 30, 0.15);
  }
  .timeline-date {
    font-size: 0.9em; color: #47001e; font-weight: 800;
    margin-bottom: 8px; text-transform: uppercase; letter-spacing: 1px;
  }
  .timeline-text {
    font-size: 1.05em; color: #333; font-weight: 600; line-height: 1.3;
  }
  @media (max-width: 768px) {
    .timeline-container { flex-direction: column; gap: 50px; }
    .timeline-line { display: none; }
    .timeline-step { flex-direction: row; text-align: left; gap: 20px; align-items: flex-start; width: 100%; }
    .timeline-bg-number { top: -20px; left: 30px; font-size: 3.5em; }
    .timeline-dot { margin-bottom: 0; margin-top: 5px; }
    .timeline-content { padding-top: 5px; }
  }

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


<div class="reveal" style="display: flex; flex-wrap: wrap; justify-content: center; gap: 50px; margin-bottom: 20px; width: 100%;">
    <p style="font-size: 1.2em; line-height: 1.6; max-width: 1200px; margin: 0 auto;">
        CANELOS 2026 se desarrollará entre el 5 y el 9 de octubre, en dos etapas complementarias. Los tres primeros días (5 al 7 de octubre) están dedicados a talleres prácticos en distintas áreas del diseño de circuitos integrados, cada uno con horario e inscripción propios. Los dos días finales (8 y 9 de octubre) corresponden al seminario central, el corazón del evento.
    </p>
    <p style="font-size: 1.2em; line-height: 1.6; max-width: 1200px; margin: 0 auto;">
        El seminario está dividido en dos jornadas, cada una con un enfoque particular. El primer día está dedicado a charlas de carácter académico y educativo, e incluye la sesión de student posters, donde estudiantes seleccionados mediante convocatoria presentarán sus proyectos e investigaciones ante la comunidad, optando a becas de transporte y alojamiento. El segundo día contempla bloques que buscan exponer al público las distintas facetas y personas involucradas en este rubro a lo largo de Latinoamérica —empresas de diseño de microchips, centros de investigación y la comunidad local—, cerrando con un panel compuesto por profesionales y docentes prominentes de nuestro país.
    </p>
    <p style="font-size: 1.2em; line-height: 1.6; max-width: 1200px; margin: 0 auto;">
        Cada transición entre bloques incluirá un coffee break libre de costo para los asistentes (el almuerzo corre por cuenta de cada participante). Durante estos recesos podrás además recorrer las exhibiciones y stands anexos a CANELOS.
    </p>
</div>
<div class="reveal">
	<p align="center" style="margin-top: 40px;"> <img src="{{ "/assets/img/material26/CANELOS26_A_section.png" | relative_url }}" alt="Poster CANELOS" width="600" style="max-width: 100%"/> </p>
</div>

<div class="reveal">
  <h2 align="left" style="font-weight: bold;">Programa</h2>
	<h3 align="justify" style="font-size: 1.2em; line-height: 1.6; max-width: 1200px; margin: 0;">
			La asignación de horarios para cada charlista se encuentra sujeta a disponibilidad de los mismos pero los horarios tentativos para el evento son los siguientes:
	</h3>
	<p align="center" style="margin-top: 40px;"> <img src="{{ "/assets/img/material26/horario_v6.jpeg" | relative_url }}" alt="Itinerario" width="600" style="max-width: 100%"/>
	</p>
</div>

<div class="reveal">
	<h2 align="left" style="font-weight: bold; margin-bottom: 40px; display: flex; align-items: center; flex-wrap: wrap; gap: 12px; color: #47001e;">
	    Talleres
	    <span style="font-size: 0.55em; font-weight: 500; color: #777; font-style: italic; letter-spacing: 0.5px; padding-top: 4px;">
	        (Haz clic en cada taller para más detalles)
	    </span>
	</h2>

    <div style="display: flex; flex-direction: column; align-items: center; gap: 20px; width: 100%;">
        
        <!-- Taller 1 (Rojo) -->
        <div class="charla-card reveal" onclick="abrirTaller('taller1')" style="display: flex; align-items: center; gap: 25px; width: 100%; background-color: #f7f9fc; padding: 20px 30px; border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.05); border-left: 5px solid #47001e;">
            <div style="text-align: left;">
                <span style="font-size: 0.85em; font-weight: 700; color: #47001e; text-transform: uppercase; letter-spacing: 1px;">Taller 1</span>
                <h3 style="margin: 2px 0 5px 0; font-size: 1.4em; color: #222; font-weight: 700;">Diseño de Chips Implantables</h3>
                <h4 style="margin: 0; font-size: 1.1em; color: #555; font-weight: 600; font-style: italic; line-height: 1.3;">Joel Gak</h4>
            </div>
        </div>

        <!-- Taller 2 (Rojo) -->
        <div class="charla-card reveal" onclick="abrirTaller('taller2')" style="display: flex; align-items: center; gap: 25px; width: 100%; background-color: #f7f9fc; padding: 20px 30px; border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.05); border-left: 5px solid #47001e;">
            <div style="text-align: left;">
                <span style="font-size: 0.85em; font-weight: 700; color: #47001e; text-transform: uppercase; letter-spacing: 1px;">Taller 2</span>
                <h3 style="margin: 2px 0 5px 0; font-size: 1.4em; color: #222; font-weight: 700;">Taller Tiny TapeOut</h3>
                <h4 style="margin: 0; font-size: 1.1em; color: #555; font-weight: 600; font-style: italic; line-height: 1.3;">ChipUSM</h4>
            </div>
        </div>

        <!-- Taller 3 (Rojo) -->
        <div class="charla-card reveal" onclick="abrirTaller('taller3')" style="display: flex; align-items: center; gap: 25px; width: 100%; background-color: #f7f9fc; padding: 20px 30px; border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.05); border-left: 5px solid #47001e;">
            <div style="text-align: left;">
                <span style="font-size: 0.85em; font-weight: 700; color: #47001e; text-transform: uppercase; letter-spacing: 1px;">Taller 3</span>
                <h3 style="margin: 2px 0 5px 0; font-size: 1.4em; color: #222; font-weight: 700;">Taller ACATEC</h3>
                <h4 style="margin: 0; font-size: 1.1em; color: #555; font-weight: 600; font-style: italic; line-height: 1.3;">Academias de Tecnologías</h4>
            </div>
        </div>

        <!-- Taller 4 (Celeste, Celero) -->
        <div class="charla-card reveal" onclick="abrirTaller('taller4')" style="display: flex; align-items: center; gap: 25px; width: 100%; background-color: #f7f9fc; padding: 20px 30px; border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.05); border-left: 5px solid #0284c7;">
            <div style="text-align: left;">
                <span style="font-size: 0.85em; font-weight: 700; color: #0284c7; text-transform: uppercase; letter-spacing: 1px;">Taller 4</span>
                <h3 style="margin: 2px 0 5px 0; font-size: 1.4em; color: #222; font-weight: 700;">Digital Design for DSP Applications</h3>
                <h4 style="margin: 0; font-size: 1.1em; color: #0284c7; font-weight: 600; font-style: italic; line-height: 1.3;">Celero Communications Inc</h4>
            </div>
        </div>

    </div>
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

    <!-- LISTA PRINCIPAL CHARLAS -->
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
        <div class="charla-card reveal" onclick="abrirCharla('alba')" style="display: flex; align-items: center; gap: 25px; width: 100%; background-color: #f7f9fc; padding: 20px 30px; border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.05); border-left: 5px solid #47001e;">
            <img src="../assets/img/material26/alba_avila.jpg" alt="Alva Avila" style="width: 90px; height: 90px; border-radius: 10px; object-fit: cover;">
            <div style="text-align: left;">
                <h3 style="margin: 0 0 5px 0; font-size: 1.4em; color: #222; font-weight: 700;">Alba Avila</h3>
                <h4 style="margin: 0; font-size: 1.1em; color: #47001e; font-weight: 600; font-style: italic; line-height: 1.3;">"Materiales de Transistores Avanzados de Extracción a Fabricación"</h4>
            </div>
        </div>

        <!-- Charla 4 -->
        <div class="charla-card reveal" onclick="abrirCharla('carlos')" style="display: flex; align-items: center; gap: 25px; width: 100%; background-color: #f7f9fc; padding: 20px 30px; border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.05); border-left: 5px solid #47001e;">
            <img src="../assets/img/material26/carlos_silva.jpeg" alt="Expositor 4" style="width: 90px; height: 90px; border-radius: 10px; object-fit: cover;">
            <div style="text-align: left;">
                <h3 style="margin: 0 0 5px 0; font-size: 1.4em; color: #222; font-weight: 700;">Carlos Silva</h3>
                <h4 style="margin: 0; font-size: 1.1em; color: #47001e; font-weight: 600; font-style: italic; line-height: 1.3;">"Introducción al Diseño de Circuitos Integrados Digitales"</h4>
            </div>
        </div>

        <!-- Charla 5 -->
        <div class="charla-card reveal" onclick="abrirCharla('peter')" style="display: flex; align-items: center; gap: 25px; width: 100%; background-color: #f7f9fc; padding: 20px 30px; border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.05); border-left: 5px solid #47001e;">
            <img src="../assets/img/material26/peter_kinget.png" alt="Expositor 5" style="width: 90px; height: 90px; border-radius: 10px; object-fit: cover;">
            <div style="text-align: left;">
                <h3 style="margin: 0 0 5px 0; font-size: 1.4em; color: #222; font-weight: 700;">Peter R. Kinget</h3>
                <h4 style="margin: 0; font-size: 1.1em; color: #47001e; font-weight: 600; font-style: italic; line-height: 1.3;">"Circuit Labs at the Lunch Table with MOSbius"</h4>
            </div>
        </div>

        <!-- Charla 6 -->
        <div class="charla-card reveal" onclick="abrirCharla('kai')" style="display: flex; align-items: center; gap: 25px; width: 100%; background-color: #f7f9fc; padding: 20px 30px; border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.05); border-left: 5px solid #47001e;">
            <img src="../assets/img/material26/kai_ni.jpg" alt="Expositor 6" style="width: 90px; height: 90px; border-radius: 10px; object-fit: cover;">
            <div style="text-align: left;">
                <h3 style="margin: 0 0 5px 0; font-size: 1.4em; color: #222; font-weight: 700;">Kai Ni</h3>
                <h4 style="margin: 0; font-size: 1.1em; color: #47001e; font-weight: 600; font-style: italic; line-height: 1.3;">"A New Look at Charge-Based Memories for Storage and Computing"</h4>
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

	<div class="page-col-wrapper">        
		<div class="page-col page-col-3">
			<p align="center"> <img src="../assets/img/material26/CANELOS26_D2.png" alt="Afiche poster sesion 1" width="400" style="max-width: 100%"/> </p>
		</div>
		<div class="page-col page-col-3">
			<p align="center"> <img src="../assets/img/material26/CANELOS26_E.jpeg" alt="Afiche poster sesion 1" width="400" style="max-width: 100%"/> </p>
		</div>
	</div>

    <!-- Línea de Tiempo Profesional -->
    <div class="timeline-container">
        <div class="timeline-line"></div>
        <div class="timeline-step"><div class="timeline-bg-number">00</div><div class="timeline-dot active"></div><div class="timeline-content"><div class="timeline-date">23 de Julio, 2026</div><div class="timeline-text">Inicio de<br>Postulaciones</div></div></div>
        <div class="timeline-step"><div class="timeline-bg-number">01</div><div class="timeline-dot"></div><div class="timeline-content"><div class="timeline-date">31 de Agosto, 2026</div><div class="timeline-text">Cierre de<br>Postulaciones</div></div></div>
        <div class="timeline-step"><div class="timeline-bg-number">02</div><div class="timeline-dot"></div><div class="timeline-content"><div class="timeline-date">03-07 de Septiembre, 2026</div><div class="timeline-text">Notificación de<br>Resultados</div></div></div>
        <div class="timeline-step"><div class="timeline-bg-number">03</div><div class="timeline-dot"></div><div class="timeline-content"><div class="timeline-date">08 de octubre, 2026</div><div class="timeline-text">Inicio del<br>Evento</div></div></div>
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
  <div class="charla-modal-content" id="m-content-box">
    <a href="#!" class="cerrar-modal-btn" onclick="cerrarCharla()">&times;</a>
    
    <!-- CONTENEDOR 1: PARA CHARLAS PLENARIAS -->
    <div id="layout-charlas">
        <div class="modal-layout-top">
          <!-- DISEÑO CREDENCIAL -->
          <div id="m-credencial-box" style="display: flex; flex-direction: column; align-items: center; filter: drop-shadow(0 10px 16px rgba(0,0,0,0.25)); flex-shrink: 0; margin: auto;">
            <div class="modal-marco-foto">
                <img id="m-foto" src="" class="modal-foto-recorte" alt="Foto">
            </div>
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
            <div class="caja-1" style="display: flex; flex-direction: column; justify-content: center; border-color: #47001e;">
                <h4 id="m-titulo" style="margin: 0; font-size: 1.35em; color: #47001e; font-style: italic; line-height: 1.4; font-weight: 800;">"Título"</h4>
            </div>
            <!-- Caja 2: Biografía -->
            <div class="caja-2">
                <p id="m-bio" style="margin: 0; font-size: 1em; color: #444; line-height: 1.6;">Texto...</p>
            </div>
          </div>
        </div>

        <!-- Caja 3: Descripción -->
        <div class="caja-3">
            <h4 id="m-desc-titulo" style="margin: 0 0 12px 0; font-size: 1.2em; color: #47001e; font-weight: bold;">Sobre la actividad</h4>
            <p id="m-desc" style="margin: 0; font-size: 1em; color: #444; line-height: 1.6;">Descripción...</p>
        </div>
    </div>

    <!-- CONTENEDOR 2: PARA TALLERES -->
    <div id="layout-talleres">
        <!-- Esquina Superior Izquierda: LOGO -->
        <div id="m-taller-logo-box">
            <img id="m-taller-logo-img" src="" alt="Logo Taller" style="display: none;">
            <div id="m-taller-logo-placeholder" style="display: none;">LOGO</div>
        </div>

        <!-- Caja 1: Título completo e impartido por -->
        <div class="caja-1" style="display: flex; flex-direction: column; align-items: center; justify-content: center; gap: 8px;">
            <h4 id="m-taller-titulo" style="margin: 0; font-size: 1.6em; font-weight: 800; font-style: italic; text-align: center;">Título del Taller</h4>
            <div style="font-size: 1em; color: #222; font-weight: 700; text-align: center;">
                Impartido por: <span id="m-taller-instructor" style="font-weight: 500; color: #555;"></span>
            </div>
        </div>
        
        <!-- Caja 2: Descripción Introductoria -->
        <div class="caja-2">
            <p id="m-taller-bio" style="margin: 0; font-size: 1em; color: #444; line-height: 1.6;">Introducción...</p>
        </div>
        
        <!-- Caja 3: Contenido / Sobre el taller -->
        <div class="caja-3">
            <h4 id="m-taller-desc-titulo" style="margin: 0 0 12px 0; font-size: 1.25em; font-weight: bold;">Sobre el taller y el contenido</h4>
            <p id="m-taller-desc" style="margin: 0; font-size: 1em; color: #444; line-height: 1.6;">Contenido del taller...</p>
        </div>
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
      afiliacion: 'Synopsys Portugal',
      titulo: '"Nanoscale Digital-Based Analog Processing: Circuits and Systems Solutions for Emerging Applications and Technologies"',
      bio: 'Pedro Toledo is a Staff Analog Design at Synopsys, Lisbon, where he works in the development of high-speed SerDes and equalization circuits in advanced CMOS technologies, including nanosheet, GAA, and FinFET. His work focuses on PHY building blocks for PCIe, USB, and MPHY interfaces, covering CTLE, DFE, CDR, LDO, and signaldetection circuits...',
      desc: 'While digital Integrated Circuits (IC) have been reaping the benefits of CMOS technology scaling in terms of speed, power consumption, and area, the techniques used for analog signal processing have not progressed at the same rate. It is evident that there have been substantial and ongoing improvements in the performance of digital circuits when compared to analog building blocks...'
    },
    'joel': {
      foto: '{{ "/assets/img/material26/joel_gak.jpg" | relative_url }}',
      nombre: 'Joel Gak',
      cargo: 'Profesor Titular',
      afiliacion: 'Universidad Católica del Uruguay',
      titulo: '"Desafíos y técnicas de diseño en implantables"',
      bio: 'Dr. Ing. Joel Gak is an engineer and holds a PhD in Engineering, specializing in analog and mixed-signal integrated circuit design. He has more than 20 years of experience in ASIC development...',
      desc: 'The Adventure of Designing a Pacemaker ASIC<br><br>This talk tells the story behind the development of a complete pacemaker ASIC, following the project from the initial product requirements through circuit design, simulation, layout, fabrication, and finally silicon testing...'
    },
    'alba': {
      foto: '../assets/img/material26/alba_avila.jpg',
      nombre: 'Alba Avila',
      cargo: 'Profesora Titular',
      afiliacion: 'Universidad de los Andes, Colombia',
      titulo: 'Materiales de Transistores Avanzados de Extracción a Fabricación',
      bio: 'Alba Avila es la directora del centro de microelectrónica (CMUA) y Profesora e investigadora del departamento de Ingeniería Eléctrica y Electrónica de la Universidad de los Andes...',
      desc: 'Pronto revelaremos la información detallada sobre esta charla plenaria y las temáticas específicas que nuestro expositor compartirá con los asistentes del evento.'
    },
    'carlos': {
      foto: '../assets/img/material26/carlos_silva.jpeg',
      nombre: 'Carlos Silva',
      cargo: 'Profesor Titular',
      afiliacion: 'Pontificia Universidad Católica del Perú',
      titulo: 'Introducción al Diseño de Circuitos Integrados Digitales',
      bio: 'Es doctor por la Universidad Autónoma de Barcelona. Ha realizado estancias de Posdoc en el Instituto Nacional Politécnico de Grenoble, Grenoble-Francia y en Texas A&M University...',
      desc: 'La charla provee los conceptos básicos para realizar el diseño de circuitos integrados digitales por medio de varios métodos de integración como la lógica complementaria MOS (CMOS) y lógica dinámica que permitan realizar el diseños de circuitos integrados de aplicación específica (ASIC)...'
    },
    'peter': {
      foto: '../assets/img/material26/peter_kinget.png',
      nombre: 'Peter R. Kinget',
      cargo: 'Profesor Titular',
      afiliacion: 'Columbia University',
      titulo: 'Circuit Labs at the Lunch Table with MOSbius',
      bio: 'Peter Kinget is the Bernard J. Lechner Professor of Electrical Engineering at Columbia University in New York. His research group focusses on the design of analog and RF integrated circuits...',
      desc: 'Learning integrated circuit design requires gaining a broad range of skills and knowledge including circuit analysis and design, signals & systems, applied electro-magnetics, and semiconductor physics...'
    },
    'kai': {
      foto: '../assets/img/material26/kai_ni.jpg',
      nombre: 'Kai Ni',
      cargo: 'Profesor Titular',
      afiliacion: 'University of Notre Dame',
      titulo: 'A New Look at Charge-Based Memories for Storage and Computing',
      bio: 'Kai Ni received the B.S. degree in Electrical Engineering from University of Science and Technology of China, Hefei, China in 2011, and Ph.D. degree of Electrical Engineering from Vanderbilt University...',
      desc: 'Charge-based memories, including SRAM, DRAM, and Flash, form the backbone of modern memory systems. Decades of technology scaling have enabled tremendous improvements in memory density, performance, and energy efficiency...'
    }
  };

  // 1.5 BASE DE DATOS DE LOS TALLERES 
  const datosTalleres = {
    'taller1': {
      logo: '', // Vacío para que active el placeholder
      titulo: 'Diseño de Chips Implantables',
      instructor: 'Joel Gak',
      bio: 'Los detalles específicos sobre los requisitos y la dinámica de este taller se revelarán de manera oficial próximamente.',
      desc: 'Estamos trabajando para brindarte el mejor contenido. Pronto publicaremos el programa detallado y los módulos que se abordarán.'
    },
    'taller2': {
      logo: '', // Vacío para que active el placeholder
      titulo: 'Taller Tiny TapeOut',
      instructor: 'ChipUSM',
      bio: 'Los detalles específicos sobre los requisitos y la dinámica de este taller se revelarán de manera oficial próximamente.',
      desc: 'Estamos trabajando para brindarte el mejor contenido. Pronto publicaremos el programa detallado y los módulos que se abordarán.'
    },
    'taller3': {
      logo: '', // Vacío para que active el placeholder
      titulo: 'Taller ACATEC',
      instructor: 'Academias de Tecnologías',
      bio: 'Los detalles específicos sobre los requisitos y la dinámica de este taller se revelarán de manera oficial próximamente.',
      desc: 'Estamos trabajando para brindarte el mejor contenido. Pronto publicaremos el programa detallado y los módulos que se abordarán.'
    },
    'taller4': {
      logo: '{{ site.baseurl }}/assets/img/logo_celero_color.png',
      titulo: 'Digital Design for DSP Applications',
      instructor: 'Celero Communications Inc',
      bio: 'This course introduces the fundamental concepts of digital design with a specific focus on implementing Digital Signal Processing (DSP) algorithms in FPGA-based systems.<br><br>The learning process is organized into three progressive phases. First, students learn the fundamentals of digital hardware design and HDL-based development. Next, they explore the basic concepts of DSP and fixed-point arithmetic. Finally, they apply these concepts to the implementation of DSP blocks on FPGAs.',
      desc: `
        The course emphasizes that a successful digital design must be correct not only from a logical perspective, but also from a timing perspective. Students will learn how propagation delays, setup and hold times, clock frequency, and signal timing affect the performance and reliability of a digital circuit.<br><br>
        
        <strong>Course Learning Path:</strong><br><br>
        <strong>Part 1 — Digital Design Fundamentals</strong><br>
        The first part introduces the Verilog HDL language and the fundamental building blocks of digital systems. Students will study both combinational and sequential circuits and learn how to describe, simulate, and synthesize them using HDL.<br><br>
        
        <strong>Part 2 — DSP Fundamentals and Fixed-Point Implementation</strong><br>
        The second part introduces fundamental DSP building blocks and the principles required to implement DSP algorithms in hardware.<br><br>
        
        <strong>Part 3 — FPGA Implementation of DSP Blocks</strong><br>
        The third part focuses on translating DSP algorithms into practical FPGA implementations.<br><br>
        
        <strong>Minimum Course Content:</strong>
        <ul style="padding-left: 20px; margin-top: 5px;">
          <li>Introduction to Verilog HDL</li>
          <li>Combinational and sequential digital circuits</li>
          <li>Binary, fixed-point, and floating-point number representations</li>
          <li>Timing diagrams for combinational and sequential circuits</li>
          <li>Gate and signal propagation delays</li>
          <li>Basic hierarchical design and synthesis</li>
          <li>Introduction to FIR and IIR filters</li>
          <li>Fixed-point implementation of DSP algorithms</li>
          <li>FPGA implementation of FIR and IIR filters</li>
          <li>Timing and resource considerations in FPGA-based DSP designs</li>
        </ul><br>
        
        <strong>Course Materials:</strong> Students are required to bring their own laptop for the practical exercises and laboratory activities.
      `
    }
  };

  // 2. FUNCIONES DEL MODAL PARA CHARLAS
  function abrirCharla(id) {
    const data = datosCharlas[id];
    if(!data) return;

    // Intercambiar visibilidad de layouts
    document.getElementById('layout-talleres').style.display = 'none';
    document.getElementById('layout-charlas').style.display = 'block';

    // Rellenar datos
    document.getElementById('m-foto').src = data.foto;
    document.getElementById('m-nombre-badge').innerText = data.nombre;
    document.getElementById('m-cargo-badge').innerText = data.cargo;
    document.getElementById('m-afiliacion-badge').innerText = data.afiliacion;
    document.getElementById('m-titulo').innerText = data.titulo;
    document.getElementById('m-bio').innerHTML = data.bio;   
    document.getElementById('m-desc').innerHTML = data.desc; 

    document.getElementById('modalCharlas').classList.add('show');
    document.body.style.overflow = 'hidden';
  }

  // 3. FUNCIONES DEL MODAL PARA TALLERES 
  function abrirTaller(id) {
    const data = datosTalleres[id];
    if(!data) return;

    // Intercambiar visibilidad de layouts
    document.getElementById('layout-charlas').style.display = 'none';
    
    // Mostrar layout de talleres
    const layoutTalleres = document.getElementById('layout-talleres');
    layoutTalleres.style.display = 'flex';

    // Aplicar temas de color (Taller 4: Celeste, Resto: Rojo)
    if(id === 'taller4') {
        layoutTalleres.classList.remove('tema-rojo');
        layoutTalleres.classList.add('tema-celeste');
    } else {
        layoutTalleres.classList.remove('tema-celeste');
        layoutTalleres.classList.add('tema-rojo');
    }

    // Gestionar si tiene logo o necesita placeholder
    const logoImg = document.getElementById('m-taller-logo-img');
    const logoPlaceholder = document.getElementById('m-taller-logo-placeholder');
    
    if (data.logo && data.logo.trim() !== '') {
        logoImg.src = data.logo;
        logoImg.style.display = 'block';
        logoPlaceholder.style.display = 'none';
    } else {
        logoImg.style.display = 'none';
        logoPlaceholder.style.display = 'flex'; // Muestra la cajita punteada "LOGO"
    }

    // Rellenar el resto de los datos
    document.getElementById('m-taller-titulo').innerText = data.titulo;
    document.getElementById('m-taller-instructor').innerText = data.instructor;
    document.getElementById('m-taller-bio').innerHTML = data.bio;   
    document.getElementById('m-taller-desc').innerHTML = data.desc; 

    document.getElementById('modalCharlas').classList.add('show');
    document.body.style.overflow = 'hidden';
  }

  // 4. FUNCIONES GLOBALES DEL MODAL
  function cerrarCharla() {
    document.getElementById('modalCharlas').classList.remove('show');
    document.body.style.overflow = 'auto'; 
  }

  function cerrarCharlaFuera(event) {
    if (event.target === document.getElementById('modalCharlas')) {
      cerrarCharla();
    }
  }

  // 5. ANIMACIÓN REVEAL AL HACER SCROLL
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
