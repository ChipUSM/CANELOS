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
  }
  .cerrar-modal-btn:hover { color: #0284c7; }

  /* Estructura interior del modal */
  .modal-layout-top {
    display: flex;
    flex-wrap: wrap;
    gap: 30px;
    margin-bottom: 20px;
    align-items: flex-start; /* Alineación superior para dejar el logo en la esquina */
  }

  /* Contenedor de Logo para Talleres (Esquina superior izquierda) */
  .modal-logo-container {
    display: flex;
    justify-content: flex-start;
    align-items: flex-start;
    width: 100%;
    max-width: 250px;
    padding: 0;
    flex-shrink: 0;
  }
  .modal-logo-container img {
    max-width: 100%;
    height: auto;
    object-fit: contain;
    border-radius: 8px;
  }
  
  /* DISEÑO CREDENCIAL PARA CHARLAS */
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

  /* Cajas del modal (Lado derecho del logo para talleres) */
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
    transition: border-color 0.3s ease;
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

  /* Estilos dinámicos SOLO para el Taller 4 (Celeste) */
  .modal-taller-theme .caja-1 {
    border-color: #0284c7 !important;
  }
  .modal-taller-theme #m-titulo {
    color: #0284c7 !important;
  }
  .modal-taller-theme #m-desc-titulo {
    color: #0284c7 !important;
  }

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
    top: 24px; 
    left: 12.5%; 
    width: 75%; 
    height: 4px;
    background-color: #e2e8f0; 
    z-index: 1;
    border-radius: 2px;
  }
  
  .timeline-line::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    height: 100%;
    width: 0%; 
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
        
        <!-- Paso 00 -->
        <div class="timeline-step">
            <div class="timeline-bg-number">00</div>
            <div class="timeline-dot active"></div>
            <div class="timeline-content">
                <div class="timeline-date">23 de Julio, 2026</div>
                <div class="timeline-text">Inicio de<br>Postulaciones</div>
            </div>
        </div>

        <!-- Paso 01 -->
        <div class="timeline-step">
            <div class="timeline-bg-number">01</div>
            <div class="timeline-dot"></div>
            <div class="timeline-content">
                <div class="timeline-date">31 de Agosto, 2026</div>
                <div class="timeline-text">Cierre de<br>Postulaciones</div>
            </div>
        </div>
        
        <!-- Paso 02 -->
        <div class="timeline-step">
            <div class="timeline-bg-number">02</div>
            <div class="timeline-dot"></div>
            <div class="timeline-content">
                <div class="timeline-date">03-07 de Septiembre, 2026</div>
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
  <div class="charla-modal-content" id="m-content-box">
    <a href="#!" class="cerrar-modal-btn" onclick="cerrarCharla()">&times;</a>
    
    <div class="modal-layout-top">
      
      <!-- CONTENEDOR LOGO (Para Talleres) -->
      <div id="m-logo-box" class="modal-logo-container" style="display: none;">
        <a id="m-logo-link" href="#" target="_blank" rel="noopener noreferrer">
            <img id="m-logo-img" src="" alt="Logo" width="430">
        </a>
      </div>

      <!-- DISEÑO CREDENCIAL (Para Charlas Plenarias) -->
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
        <div class="caja-1" style="display: flex; flex-direction: column; justify-content: center;">
            <h4 id="m-titulo" style="margin: 0; font-size: 1.35em; color: #47001e; font-style: italic; line-height: 1.4; font-weight: 800;">"Título"</h4>
        </div>
        <!-- Caja 2: Biografía / Presentación / Instructor -->
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
      bio: 'Pedro Toledo is a Staff Analog Design at Synopsys, Lisbon, where he works in the development of high-speed SerDes and equalization circuits in advanced CMOS technologies, including nanosheet, GAA, and FinFET. His work focuses on PHY building blocks for PCIe, USB, and MPHY interfaces, covering CTLE, DFE, CDR, LDO, and signaldetection circuits. He received the Ph.D. degree in Microelectronics from Politecnico di Torino, Italy, and the Federal University of Rio Grande do Sul (UFRGS), Brazil, where he graduated Summa Cum Laude. His research interests include DIGOTA architectures, ZTC/GZTC MOSFET modeling, low-voltage analog design, and digital-based analog processing. Dr. Toledo has authored numerous papers in IEEE journals and conferences and serves as reviewer for several IEEE Transactions and Letters. He is the recipient of multiple awards, including the SBMicro Best PhD Thesis Award, the IEEE ICECS Best Student Paper Award, and the YEF-ECE Best Paper Award.',
      desc: 'While digital Integrated Circuits (IC) have been reaping the benefits of CMOS technology scaling in terms of speed, power consumption, and area, the techniques used for analog signal processing have not progressed at the same rate. It is evident that there have been substantial and ongoing improvements in the performance of digital circuits when compared to analog building blocks. To address this disparity, there is a growing trend towards exploring alternative IC design strategies that leverage digital-in-concept methodologies to implement analog functions. By capitalizing on the well-established fullyautomated EDA digital tools, reimagining analog functions in digital terms holds the promise of making Analog IC blocks more conducive to achieving energy efficiency and adapting to the shrinking feature sizes of new technologies. This presentation aims to showcase the current state-of-the-art digital-based analog building blocks, such as OTA, comparators, and converters, along with their impact on emerging applications and technologies. This shift in approach has the potential to revolutionize the field of analog signal processing and pave the way for undefined advancements in IC design.'
    },
    'joel': {
      foto: '{{ "/assets/img/material26/joel_gak.jpg" | relative_url }}',
      nombre: 'Joel Gak',
      cargo: 'Profesor Titular',
      afiliacion: 'Universidad Católica del Uruguay',
      titulo: '"Desafíos y técnicas de diseño en implantables"',
      bio: 'Dr. Ing. Joel Gak is an engineer and holds a PhD in Engineering, specializing in analog and mixed-signal integrated circuit design. He has more than 20 years of experience in ASIC development, with a particular focus on low-power systems, implantable medical devices, analog interfaces, and power management. He is an Associate Professor at Universidad Católica del Uruguay, where he conducts research and teaches in the areas of microelectronics, ASICs, and IoT. He has participated in numerous research and development projects and has extensive experience across the complete integrated circuit design cycle, from system architecture and transistor-level design to tape-out, silicon validation, and transfer to real-world applications.',
      desc: 'The Adventure of Designing a Pacemaker ASIC<br><br>This talk tells the story behind the development of a complete pacemaker ASIC, following the project from the initial product requirements through circuit design, simulation, layout, fabrication, and finally silicon testing.<br><br>Rather than focusing on circuit equations or detailed transistor-level design, I will share the engineering challenges, unexpected problems, difficult decisions, and lessons learned along the way. Designing a medical chip is not only about making each block work—it is about making the entire system work reliably together, while dealing with real-world constraints and, above all, safety.'
    },
    'alba': {
      foto: '../assets/img/material26/alba_avila.jpg',
      nombre: 'Alba Avila',
      cargo: 'Profesora Titular',
      afiliacion: 'Universidad de los Andes, Colombia',
      titulo: 'Materiales de Transistores Avanzados de Extracción a Fabricación',
      bio: 'Alba Avila es la directora del centro de microelectrónica (CMUA) y Profesora e investigadora del departamento de Ingeniería Eléctrica y Electrónica de la Universidad de los Andes. Es física, ingeniera eléctrica, máster en ingeniera eléctrica de la Universidad de los Andes y doctora de la Universidad de Cambridge en el Reino Unido. Es una apasionada investigadora interdisciplinaria en la ciencia e ingeniería de materiales. Ha trabajado en nanomateriales para aplicaciones en energía y sensado, también ha desarrollado tecnologías humanitarias para monitoreo de agua, almacenamiento de enrgía y alfabetización tecnológica. Así mismo, ha estudiado propiedades de materiales a diferentes escalas y generados kits educativos para la enseñanza de nanotecnología y nuevos materiales. Además, ha promovido programas de inclusión y vocaciones científico-técnicas en colaboración con proyectos de EU y LATAM. Es fellow del resilence center del imperial college, Distinguished lecturer of EDS IEEE y miembro de WIE.',
      desc: 'Pronto revelaremos la información detallada sobre esta charla plenaria y las temáticas específicas que nuestro expositor compartirá con los asistentes del evento.'
    },
    'carlos': {
      foto: '../assets/img/material26/carlos_silva.jpeg',
      nombre: 'Carlos Silva',
      cargo: 'Profesor Titular',
      afiliacion: 'Pontificia Universidad Católica del Perú',
      titulo: 'Introducción al Diseño de Circuitos Integrados Digitales',
      bio: 'Es doctor por la Universidad Autónoma de Barcelona. Ha realizado estancias de Posdoc en el Instituto Nacional Politécnico de Grenoble, Grenoble-Francia y en Texas A&M University. Actualmente es Profesor titular de la PUCP. Director-Fundador del Grupo de Investigación en Microelectrónica. Desde 2019-2024 fue director de la Dirección de Fomento de la Investigación de la PUCP. Silva-Cárdenas es autor del primer circuito integrado digital peruano que logró su fabricación y cuenta con más de 80 publicaciones, es autor de un libro, tres capítulos de libros y coeditor de dos libros. Ha impartido cursos de posgrado en las universidades: Complutense de Madrid, Valencia y Autónoma de Barcelona, y en la Universidad Nacional de Tucumán en Argentina. Ha sido General Chair de una docena de congresos internacionales y del evento flagship de latinoamérica LASCAS2026 realizado en Arequipa-Peru en febrero de 2026.. Ha recibido premios, como el Premio de RECONOCIMIENTO A LA INVESTIGACIÓN de la PUCP durante los últimos 9 años, el Premio al Ingeniero Eminente de la Región 9 de IEEE Latinoamérica en 2019 y el Premio ELEKTRON en 2025 por su “liderazgo en Microelectrónica, su rol clave en la regulación de las telecomunicaciones y su aporte decisivo a la formación e investigación en ingeniería en el Perú”. Es miembro del Board of Goverment de CASS-IEEE desde 2024-2026.',
      desc: 'La charla provee los conceptos básicos para realizar el diseño de circuitos integrados digitales por medio de varios métodos de integración como la lógica complementaria MOS (CMOS) y lógica dinámica que permitan realizar el diseños de circuitos integrados de aplicación específica (ASIC).Los temas cubren: Conceptos y funcionamiento del MOSFET, Regiones de funcionamiento, Voltaje umbral, Efecto de cuerpo, Ecuaciones de diseño MOS y Curvas Características, Nivel de Inversión, Efecto de Modulación de Canal. Métodos de implementación de circuitos digitales tanto combinacional como secuencial. Latches y registros estáticos y dinámicos. Flip flop. Diagrama de máscaras, layout y reglas de diseño, simulación y caracterización de dispositivos.'
    },
    'peter': {
      foto: '../assets/img/material26/peter_kinget.png',
      nombre: 'Peter R. Kinget',
      cargo: 'Profesor Titular',
      afiliacion: 'Columbia University',
      titulo: 'Circuit Labs at the Lunch Table with MOSbius',
      bio: 'Peter Kinget is the Bernard J. Lechner Professor of Electrical Engineering at Columbia University in New York. His research group focusses on the design of analog and RF integrated circuits and the novel systems or applications they enable in communications, sensing, computing, and power management. He also devotes a lot of his energy to teaching initiatives like https://mosbius.org and https://vlsidesignlab.org He received his engineering and Ph.D. degrees in electrical engineering from the Katholieke Universiteit in Leuven (Belgium). He has worked in industrial research and development at Bell Laboratories, Broadcom, Celight and Multilink before joining the faculty of the Department of Electrical Engineering, Columbia University, NY in 2002. He served as Department Chair from 2017 to 2020. He is also a consulting expert on patent litigation and a technical consultant to industry. Peter is a Fellow of the IEEE and is widely published. He received several awards including the "IEEE Solid-State Circuits Society 2020 Innovative Education Award and the “2011 IEEE Communications Society Award for Advances in Communication” (for an outstanding paper in any IEEE Communications Society publication in the past 15 years). He is a “Distinguished Lecturer” for the IEEE Solid-State Circuits Society (SSCS), and has been an Associate Editor of the IEEE Journal of Solid State Circuits (2003-2007) and the IEEE Transactions on Circuits and Systems II (2008-2009). He has served on the program committees of many of the major solid-state circuits conferences and has been an elected member of the IEEE SSCS Adcom (2011-2013 & 2014-2016).',
      desc: 'Learning integrated circuit design requires gaining a broad range of skills and knowledge including circuit analysis and design, signals & systems, applied electro-magnetics, and semiconductor physics. Learning theory has always been most accessible through books or now the internet. Simulation tools are now also widely available on personal computers, including open-source versions. But, learning measurements so far has been mostly confined to school or industry laboratories. Yet, physical intuition and practical experience keeps playing a significant role in the development of successful, high performance integrated circuits. We will present the MOSbius platform that allows a student or designer to experiment with IC-style, analog, CMOS circuits at the lunch table. This unique platform uses a custom chip with CMOS building blocks that can be wired on a breadboard or with a programmable on-chip switch matrix. Measurements can be conducted using an affordable, all-in-one, USB lab instrument. Ready-to-go experiments are provided to learners and instructors on https://mosbius.org. Nothing can substitute for the aha moment when you observe a circuit finally working. The debugging process to bring-up the circuit teaches the designer essential lessons that carry over to high performance circuits in highly scaled technologies. The MOSbius platform aims to make lab experience widely accessible and affordable to learners.'
    },
    'kai': {
      foto: '../assets/img/material26/kai_ni.jpg',
      nombre: 'Kai Ni',
      cargo: 'Profesor Titular',
      afiliacion: 'University of Notre Dame',
      titulo: 'A New Look at Charge-Based Memories for Storage and Computing',
      bio: 'Kai Ni received the B.S. degree in Electrical Engineering from University of Science and Technology of China, Hefei, China in 2011, and Ph.D. degree of Electrical Engineering from Vanderbilt University, Nashville, TN, USA in 2016 by working on characterization, modeling, and reliability of III-V MOSFETs. Since then, he became a postdoctoral associate at University of Notre Dame, working on ferroelectric devices for nonvolatile memory and novel computing paradigms. He is now an associate professor in University of Notre Dame since 2023 after joining Rochester Institute of Technology as an assistant professor. He has around 200 publications in top journals and conference proceedings, including Nature Electronics, IEDM, VLSI Symposium, IRPS, EDL, etc. His current interests lie in nanoelectronic devices empowering unconventional computing, domain-specific accelerator, and memory technology.',
      desc: 'Charge-based memories, including SRAM, DRAM, and Flash, form the backbone of modern memory systems. Decades of technology scaling have enabled tremendous improvements in memory density, performance, and energy efficiency, supporting the storage and processing of data being generated at an unprecedented rate. The availability of these advanced memory technologies has also been a key enabler of the rapid growth of artificial intelligence. However, continued scaling is pushing conventional memory technologies toward their physical and geometric limits, creating an increasing need for new device concepts and architectures that can provide sustainable scaling paths toward higher density, improved performance, and greater energy efficiency.\n\n In this talk, we will discuss two representative emerging memory technologies: HfO₂-based ferroelectric memories and oxide-semiconductor-channel-based monolithic 3D DRAM. We will highlight recent advances in these technologies, examine their key device and integration challenges, and discuss their potential for future high-density memory systems. Beyond conventional data storage, we will further explore how these emerging memory technologies can enable compute-in-memory architectures to address the growing memory wall in AI computing. In particular, we will present their applications to key computational primitives, including matrix–vector multiplication accelerators and associative memories, illustrating opportunities to extend emerging memory technologies from high-density storage toward energy-efficient computing.'
    }
  };

  // 1.5 BASE DE DATOS DE LOS TALLERES
  const datosTalleres = {
    'taller1': {
      logo: 'https://via.placeholder.com/350x150/eeeeee/888888?text=LOGO',
      link: '#',
      titulo: 'Diseño de Chips Implantables',
      bio: '<strong>Impartido por: Joel Gak</strong><br><br>Información detallada próximamente...',
      desc: 'Pronto se anunciarán los requisitos, fechas exactas y contenidos específicos para este taller.'
    },
    'taller2': {
      logo: 'https://via.placeholder.com/350x150/eeeeee/888888?text=LOGO',
      link: '#',
      titulo: 'Taller Tiny TapeOut',
      bio: '<strong>Impartido por: ChipUSM</strong><br><br>Información detallada próximamente...',
      desc: 'Pronto se anunciarán los requisitos, fechas exactas y contenidos específicos para este taller.'
    },
    'taller3': {
      logo: 'https://via.placeholder.com/350x150/eeeeee/888888?text=LOGO',
      link: '#',
      titulo: 'Taller ACATEC',
      bio: '<strong>Impartido por: Academias de Tecnologías</strong><br><br>Información detallada próximamente...',
      desc: 'Pronto se anunciarán los requisitos, fechas exactas y contenidos específicos para este taller.'
    },
    'taller4': {
      logo: '{{ site.baseurl }}/assets/img/logo_celero_color.png',
      link: 'https://celero.inc',
      titulo: 'Digital Design for DSP Applications',
      bio: '<strong>Impartido por: Celero Communications Inc</strong><br><br>This course introduces the fundamental concepts of digital design with a specific focus on implementing Digital Signal Processing (DSP) algorithms in FPGA-based systems.<br><br>The learning process is organized into three progressive phases. First, students learn the fundamentals of digital hardware design and HDL-based development. Next, they explore the basic concepts of DSP and fixed-point arithmetic. Finally, they apply these concepts to the implementation of DSP blocks on FPGAs.',
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

    // Quitar tema de taller y restaurar alineación original (centrado)
    document.getElementById('m-content-box').classList.remove('modal-taller-theme');
    document.querySelector('.modal-layout-top').style.alignItems = 'center';

    // Mostrar Credencial y ocultar Logo
    document.getElementById('m-logo-box').style.display = 'none';
    document.getElementById('m-credencial-box').style.display = 'flex';

    document.getElementById('m-foto').src = data.foto;
    document.getElementById('m-nombre-badge').innerText = data.nombre;
    document.getElementById('m-cargo-badge').innerText = data.cargo;
    document.getElementById('m-afiliacion-badge').innerText = data.afiliacion;
    document.getElementById('m-titulo').innerText = data.titulo;
    document.getElementById('m-bio').innerHTML = data.bio;   
    
    document.getElementById('m-desc-titulo').innerText = "Sobre la charla";
    document.getElementById('m-desc').innerHTML = data.desc; 

    document.getElementById('modalCharlas').classList.add('show');
    document.body.style.overflow = 'hidden';
  }

  // 3. FUNCIONES DEL MODAL PARA TALLERES
  function abrirTaller(id) {
    const data = datosTalleres[id];
    if(!data) return;

    // Solo el Taller 4 usa el tema visual Celeste (modal-taller-theme)
    if(id === 'taller4') {
        document.getElementById('m-content-box').classList.add('modal-taller-theme');
    } else {
        document.getElementById('m-content-box').classList.remove('modal-taller-theme');
    }

    // Alinear layout en "flex-start" para que el logo se mantenga en la esquina superior izquierda
    document.querySelector('.modal-layout-top').style.alignItems = 'flex-start';

    // Mostrar Logo y ocultar marco de Credencial
    document.getElementById('m-credencial-box').style.display = 'none';
    document.getElementById('m-logo-box').style.display = 'flex';

    if(data.logo) {
      document.getElementById('m-logo-img').src = data.logo;
    }
    if(data.link) {
      document.getElementById('m-logo-link').href = data.link;
    }

    document.getElementById('m-titulo').innerText = data.titulo;
    document.getElementById('m-bio').innerHTML = data.bio;   
    
    document.getElementById('m-desc-titulo').innerText = "Sobre el taller y el contenido";
    document.getElementById('m-desc').innerHTML = data.desc; 

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
</script>---
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

  /* Tarjetas de Talleres (Tema Celeste) */
  .taller-card {
    border-left: 5px solid #0284c7 !important;
  }
  .taller-card:hover {
    box-shadow: 0 8px 20px rgba(2, 132, 199, 0.2) !important;
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
  .cerrar-modal-btn:hover { color: #0284c7; }

  /* Estructura interior del modal */
  .modal-layout-top {
    display: flex;
    flex-wrap: wrap;
    gap: 30px;
    margin-bottom: 20px;
    align-items: center;
  }

  /* Contenedor de Logo para Talleres */
  .modal-logo-container {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    max-width: 280px;
    margin: 0 auto;
    padding: 15px;
  }
  .modal-logo-container img {
    max-width: 100%;
    height: auto;
    object-fit: contain;
  }
  
  /* DISEÑO CREDENCIAL PARA CHARLAS */
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

  /* Cajas del modal */
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
    transition: border-color 0.3s ease;
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

  /* Estilos dinámicos cuando es Taller (Celeste) */
  .modal-taller-theme .caja-1 {
    border-color: #0284c7 !important;
  }
  .modal-taller-theme #m-titulo {
    color: #0284c7 !important;
  }
  .modal-taller-theme #m-desc-titulo {
    color: #0284c7 !important;
  }

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
    top: 24px; 
    left: 12.5%; 
    width: 75%; 
    height: 4px;
    background-color: #e2e8f0; 
    z-index: 1;
    border-radius: 2px;
  }
  
  .timeline-line::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    height: 100%;
    width: 0%; 
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
	<h2 align="left" style="font-weight: bold; margin-bottom: 40px; display: flex; align-items: center; flex-wrap: wrap; gap: 12px; color: #0284c7;">
	    Talleres
	    <span style="font-size: 0.55em; font-weight: 500; color: #777; font-style: italic; letter-spacing: 0.5px; padding-top: 4px;">
	        (Haz clic en cada taller para más detalles)
	    </span>
	</h2>

    <div style="display: flex; flex-direction: column; align-items: center; gap: 20px; width: 100%;">
        
        <!-- Taller 1 -->
        <div class="charla-card taller-card reveal" onclick="abrirTaller('taller1')" style="display: flex; align-items: center; gap: 25px; width: 100%; background-color: #f7f9fc; padding: 20px 30px; border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.05);">
            <div style="text-align: left;">
                <span style="font-size: 0.85em; font-weight: 700; color: #0284c7; text-transform: uppercase; letter-spacing: 1px;">Taller 1</span>
                <h3 style="margin: 2px 0 5px 0; font-size: 1.4em; color: #222; font-weight: 700;">Diseño de Chips Implantables</h3>
                <h4 style="margin: 0; font-size: 1.1em; color: #555; font-weight: 600; font-style: italic; line-height: 1.3;">Joel Gak</h4>
            </div>
        </div>

        <!-- Taller 2 -->
        <div class="charla-card taller-card reveal" onclick="abrirTaller('taller2')" style="display: flex; align-items: center; gap: 25px; width: 100%; background-color: #f7f9fc; padding: 20px 30px; border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.05);">
            <div style="text-align: left;">
                <span style="font-size: 0.85em; font-weight: 700; color: #0284c7; text-transform: uppercase; letter-spacing: 1px;">Taller 2</span>
                <h3 style="margin: 2px 0 5px 0; font-size: 1.4em; color: #222; font-weight: 700;">Taller Tiny TapeOut</h3>
                <h4 style="margin: 0; font-size: 1.1em; color: #555; font-weight: 600; font-style: italic; line-height: 1.3;">ChipUSM</h4>
            </div>
        </div>

        <!-- Taller 3 -->
        <div class="charla-card taller-card reveal" onclick="abrirTaller('taller3')" style="display: flex; align-items: center; gap: 25px; width: 100%; background-color: #f7f9fc; padding: 20px 30px; border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.05);">
            <div style="text-align: left;">
                <span style="font-size: 0.85em; font-weight: 700; color: #0284c7; text-transform: uppercase; letter-spacing: 1px;">Taller 3</span>
                <h3 style="margin: 2px 0 5px 0; font-size: 1.4em; color: #222; font-weight: 700;">Taller ACATEC</h3>
                <h4 style="margin: 0; font-size: 1.1em; color: #555; font-weight: 600; font-style: italic; line-height: 1.3;">Academias de Tecnologías</h4>
            </div>
        </div>

        <!-- Taller 4 (Celero) -->
        <div class="charla-card taller-card reveal" onclick="abrirTaller('taller4')" style="display: flex; align-items: center; gap: 25px; width: 100%; background-color: #f7f9fc; padding: 20px 30px; border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.05);">
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
        
        <!-- Paso 00 -->
        <div class="timeline-step">
            <div class="timeline-bg-number">00</div>
            <div class="timeline-dot active"></div>
            <div class="timeline-content">
                <div class="timeline-date">23 de Julio, 2026</div>
                <div class="timeline-text">Inicio de<br>Postulaciones</div>
            </div>
        </div>

        <!-- Paso 01 -->
        <div class="timeline-step">
            <div class="timeline-bg-number">01</div>
            <div class="timeline-dot"></div>
            <div class="timeline-content">
                <div class="timeline-date">31 de Agosto, 2026</div>
                <div class="timeline-text">Cierre de<br>Postulaciones</div>
            </div>
        </div>
        
        <!-- Paso 02 -->
        <div class="timeline-step">
            <div class="timeline-bg-number">02</div>
            <div class="timeline-dot"></div>
            <div class="timeline-content">
                <div class="timeline-date">03-07 de Septiembre, 2026</div>
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
  <div class="charla-modal-content" id="m-content-box">
    <a href="#!" class="cerrar-modal-btn" onclick="cerrarCharla()">&times;</a>
    
    <div class="modal-layout-top">
      
      <!-- CONTENEDOR LOGO (Para Talleres) -->
      <div id="m-logo-box" class="modal-logo-container" style="display: none;">
        <a id="m-logo-link" href="https://celero.inc" target="_blank" rel="noopener noreferrer">
            <img id="m-logo-img" src="{{ site.baseurl }}/assets/img/logo_celero_color.png" alt="Logo" width="430">
        </a>
      </div>

      <!-- DISEÑO CREDENCIAL (Para Charlas Plenarias) -->
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
        <div class="caja-1" style="display: flex; flex-direction: column; justify-content: center;">
            <h4 id="m-titulo" style="margin: 0; font-size: 1.35em; color: #47001e; font-style: italic; line-height: 1.4; font-weight: 800;">"Título"</h4>
        </div>
        <!-- Caja 2: Biografía / Presentación -->
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
      bio: 'Pedro Toledo is a Staff Analog Design at Synopsys, Lisbon, where he works in the development of high-speed SerDes and equalization circuits in advanced CMOS technologies, including nanosheet, GAA, and FinFET. His work focuses on PHY building blocks for PCIe, USB, and MPHY interfaces, covering CTLE, DFE, CDR, LDO, and signaldetection circuits. He received the Ph.D. degree in Microelectronics from Politecnico di Torino, Italy, and the Federal University of Rio Grande do Sul (UFRGS), Brazil, where he graduated Summa Cum Laude. His research interests include DIGOTA architectures, ZTC/GZTC MOSFET modeling, low-voltage analog design, and digital-based analog processing. Dr. Toledo has authored numerous papers in IEEE journals and conferences and serves as reviewer for several IEEE Transactions and Letters. He is the recipient of multiple awards, including the SBMicro Best PhD Thesis Award, the IEEE ICECS Best Student Paper Award, and the YEF-ECE Best Paper Award.',
      desc: 'While digital Integrated Circuits (IC) have been reaping the benefits of CMOS technology scaling in terms of speed, power consumption, and area, the techniques used for analog signal processing have not progressed at the same rate. It is evident that there have been substantial and ongoing improvements in the performance of digital circuits when compared to analog building blocks. To address this disparity, there is a growing trend towards exploring alternative IC design strategies that leverage digital-in-concept methodologies to implement analog functions. By capitalizing on the well-established fullyautomated EDA digital tools, reimagining analog functions in digital terms holds the promise of making Analog IC blocks more conducive to achieving energy efficiency and adapting to the shrinking feature sizes of new technologies. This presentation aims to showcase the current state-of-the-art digital-based analog building blocks, such as OTA, comparators, and converters, along with their impact on emerging applications and technologies. This shift in approach has the potential to revolutionize the field of analog signal processing and pave the way for undefined advancements in IC design.'
    },
    'joel': {
      foto: '{{ "/assets/img/material26/joel_gak.jpg" | relative_url }}',
      nombre: 'Joel Gak',
      cargo: 'Profesor Titular',
      afiliacion: 'Universidad Católica del Uruguay',
      titulo: '"Desafíos y técnicas de diseño en implantables"',
      bio: 'Dr. Ing. Joel Gak is an engineer and holds a PhD in Engineering, specializing in analog and mixed-signal integrated circuit design. He has more than 20 years of experience in ASIC development, with a particular focus on low-power systems, implantable medical devices, analog interfaces, and power management. He is an Associate Professor at Universidad Católica del Uruguay, where he conducts research and teaches in the areas of microelectronics, ASICs, and IoT. He has participated in numerous research and development projects and has extensive experience across the complete integrated circuit design cycle, from system architecture and transistor-level design to tape-out, silicon validation, and transfer to real-world applications.',
      desc: 'The Adventure of Designing a Pacemaker ASIC<br><br>This talk tells the story behind the development of a complete pacemaker ASIC, following the project from the initial product requirements through circuit design, simulation, layout, fabrication, and finally silicon testing.<br><br>Rather than focusing on circuit equations or detailed transistor-level design, I will share the engineering challenges, unexpected problems, difficult decisions, and lessons learned along the way. Designing a medical chip is not only about making each block work—it is about making the entire system work reliably together, while dealing with real-world constraints and, above all, safety.'
    },
    'alba': {
      foto: '../assets/img/material26/alba_avila.jpg',
      nombre: 'Alba Avila',
      cargo: 'Profesora Titular',
      afiliacion: 'Universidad de los Andes, Colombia',
      titulo: 'Materiales de Transistores Avanzados de Extracción a Fabricación',
      bio: 'Alba Avila es la directora del centro de microelectrónica (CMUA) y Profesora e investigadora del departamento de Ingeniería Eléctrica y Electrónica de la Universidad de los Andes. Es física, ingeniera eléctrica, máster en ingeniera eléctrica de la Universidad de los Andes y doctora de la Universidad de Cambridge en el Reino Unido. Es una apasionada investigadora interdisciplinaria en la ciencia e ingeniería de materiales. Ha trabajado en nanomateriales para aplicaciones en energía y sensado, también ha desarrollado tecnologías humanitarias para monitoreo de agua, almacenamiento de enrgía y alfabetización tecnológica. Así mismo, ha estudiado propiedades de materiales a diferentes escalas y generados kits educativos para la enseñanza de nanotecnología y nuevos materiales. Además, ha promovido programas de inclusión y vocaciones científico-técnicas en colaboración con proyectos de EU y LATAM. Es fellow del resilence center del imperial college, Distinguished lecturer of EDS IEEE y miembro de WIE.',
      desc: 'Pronto revelaremos la información detallada sobre esta charla plenaria y las temáticas específicas que nuestro expositor compartirá con los asistentes del evento.'
    },
    'carlos': {
      foto: '../assets/img/material26/carlos_silva.jpeg',
      nombre: 'Carlos Silva',
      cargo: 'Profesor Titular',
      afiliacion: 'Pontificia Universidad Católica del Perú',
      titulo: 'Introducción al Diseño de Circuitos Integrados Digitales',
      bio: 'Es doctor por la Universidad Autónoma de Barcelona. Ha realizado estancias de Posdoc en el Instituto Nacional Politécnico de Grenoble, Grenoble-Francia y en Texas A&M University. Actualmente es Profesor titular de la PUCP. Director-Fundador del Grupo de Investigación en Microelectrónica. Desde 2019-2024 fue director de la Dirección de Fomento de la Investigación de la PUCP. Silva-Cárdenas es autor del primer circuito integrado digital peruano que logró su fabricación y cuenta con más de 80 publicaciones, es autor de un libro, tres capítulos de libros y coeditor de dos libros. Ha impartido cursos de posgrado en las universidades: Complutense de Madrid, Valencia y Autónoma de Barcelona, y en la Universidad Nacional de Tucumán en Argentina. Ha sido General Chair de una docena de congresos internacionales y del evento flagship de latinoamérica LASCAS2026 realizado en Arequipa-Peru en febrero de 2026.. Ha recibido premios, como el Premio de RECONOCIMIENTO A LA INVESTIGACIÓN de la PUCP durante los últimos 9 años, el Premio al Ingeniero Eminente de la Región 9 de IEEE Latinoamérica en 2019 y el Premio ELEKTRON en 2025 por su “liderazgo en Microelectrónica, su rol clave en la regulación de las telecomunicaciones y su aporte decisivo a la formación e investigación en ingeniería en el Perú”. Es miembro del Board of Goverment de CASS-IEEE desde 2024-2026.',
      desc: 'La charla provee los conceptos básicos para realizar el diseño de circuitos integrados digitales por medio de varios métodos de integración como la lógica complementaria MOS (CMOS) y lógica dinámica que permitan realizar el diseños de circuitos integrados de aplicación específica (ASIC).Los temas cubren: Conceptos y funcionamiento del MOSFET, Regiones de funcionamiento, Voltaje umbral, Efecto de cuerpo, Ecuaciones de diseño MOS y Curvas Características, Nivel de Inversión, Efecto de Modulación de Canal. Métodos de implementación de circuitos digitales tanto combinacional como secuencial. Latches y registros estáticos y dinámicos. Flip flop. Diagrama de máscaras, layout y reglas de diseño, simulación y caracterización de dispositivos.'
    },
    'peter': {
      foto: '../assets/img/material26/peter_kinget.png',
      nombre: 'Peter R. Kinget',
      cargo: 'Profesor Titular',
      afiliacion: 'Columbia University',
      titulo: 'Circuit Labs at the Lunch Table with MOSbius',
      bio: 'Peter Kinget is the Bernard J. Lechner Professor of Electrical Engineering at Columbia University in New York. His research group focusses on the design of analog and RF integrated circuits and the novel systems or applications they enable in communications, sensing, computing, and power management. He also devotes a lot of his energy to teaching initiatives like https://mosbius.org and https://vlsidesignlab.org He received his engineering and Ph.D. degrees in electrical engineering from the Katholieke Universiteit in Leuven (Belgium). He has worked in industrial research and development at Bell Laboratories, Broadcom, Celight and Multilink before joining the faculty of the Department of Electrical Engineering, Columbia University, NY in 2002. He served as Department Chair from 2017 to 2020. He is also a consulting expert on patent litigation and a technical consultant to industry. Peter is a Fellow of the IEEE and is widely published. He received several awards including the "IEEE Solid-State Circuits Society 2020 Innovative Education Award and the “2011 IEEE Communications Society Award for Advances in Communication” (for an outstanding paper in any IEEE Communications Society publication in the past 15 years). He is a “Distinguished Lecturer” for the IEEE Solid-State Circuits Society (SSCS), and has been an Associate Editor of the IEEE Journal of Solid State Circuits (2003-2007) and the IEEE Transactions on Circuits and Systems II (2008-2009). He has served on the program committees of many of the major solid-state circuits conferences and has been an elected member of the IEEE SSCS Adcom (2011-2013 & 2014-2016).',
      desc: 'Learning integrated circuit design requires gaining a broad range of skills and knowledge including circuit analysis and design, signals & systems, applied electro-magnetics, and semiconductor physics. Learning theory has always been most accessible through books or now the internet. Simulation tools are now also widely available on personal computers, including open-source versions. But, learning measurements so far has been mostly confined to school or industry laboratories. Yet, physical intuition and practical experience keeps playing a significant role in the development of successful, high performance integrated circuits. We will present the MOSbius platform that allows a student or designer to experiment with IC-style, analog, CMOS circuits at the lunch table. This unique platform uses a custom chip with CMOS building blocks that can be wired on a breadboard or with a programmable on-chip switch matrix. Measurements can be conducted using an affordable, all-in-one, USB lab instrument. Ready-to-go experiments are provided to learners and instructors on https://mosbius.org. Nothing can substitute for the aha moment when you observe a circuit finally working. The debugging process to bring-up the circuit teaches the designer essential lessons that carry over to high performance circuits in highly scaled technologies. The MOSbius platform aims to make lab experience widely accessible and affordable to learners.'
    },
    'kai': {
      foto: '../assets/img/material26/kai_ni.jpg',
      nombre: 'Kai Ni',
      cargo: 'Profesor Titular',
      afiliacion: 'University of Notre Dame',
      titulo: 'A New Look at Charge-Based Memories for Storage and Computing',
      bio: 'Kai Ni received the B.S. degree in Electrical Engineering from University of Science and Technology of China, Hefei, China in 2011, and Ph.D. degree of Electrical Engineering from Vanderbilt University, Nashville, TN, USA in 2016 by working on characterization, modeling, and reliability of III-V MOSFETs. Since then, he became a postdoctoral associate at University of Notre Dame, working on ferroelectric devices for nonvolatile memory and novel computing paradigms. He is now an associate professor in University of Notre Dame since 2023 after joining Rochester Institute of Technology as an assistant professor. He has around 200 publications in top journals and conference proceedings, including Nature Electronics, IEDM, VLSI Symposium, IRPS, EDL, etc. His current interests lie in nanoelectronic devices empowering unconventional computing, domain-specific accelerator, and memory technology.',
      desc: 'Charge-based memories, including SRAM, DRAM, and Flash, form the backbone of modern memory systems. Decades of technology scaling have enabled tremendous improvements in memory density, performance, and energy efficiency, supporting the storage and processing of data being generated at an unprecedented rate. The availability of these advanced memory technologies has also been a key enabler of the rapid growth of artificial intelligence. However, continued scaling is pushing conventional memory technologies toward their physical and geometric limits, creating an increasing need for new device concepts and architectures that can provide sustainable scaling paths toward higher density, improved performance, and greater energy efficiency.\n\n In this talk, we will discuss two representative emerging memory technologies: HfO₂-based ferroelectric memories and oxide-semiconductor-channel-based monolithic 3D DRAM. We will highlight recent advances in these technologies, examine their key device and integration challenges, and discuss their potential for future high-density memory systems. Beyond conventional data storage, we will further explore how these emerging memory technologies can enable compute-in-memory architectures to address the growing memory wall in AI computing. In particular, we will present their applications to key computational primitives, including matrix–vector multiplication accelerators and associative memories, illustrating opportunities to extend emerging memory technologies from high-density storage toward energy-efficient computing.'
    }
  };

  // 1.5 BASE DE DATOS DE LOS TALLERES
  const datosTalleres = {
    'taller1': {
      logo: '{{ site.baseurl }}/assets/img/logo_celero_color.png',
      link: 'https://celero.inc',
      titulo: 'Diseño de Chips Implantables',
      bio: 'Impartido por: Joel Gak<br><br>Información detallada próximamente...',
      desc: 'Pronto se anunciarán los requisitos, fechas exactas y contenidos específicos para este taller.'
    },
    'taller2': {
      logo: '{{ site.baseurl }}/assets/img/logo_celero_color.png',
      link: 'https://celero.inc',
      titulo: 'Taller Tiny TapeOut',
      bio: 'Impartido por: ChipUSM<br><br>Información detallada próximamente...',
      desc: 'Pronto se anunciarán los requisitos, fechas exactas y contenidos específicos para este taller.'
    },
    'taller3': {
      logo: '{{ site.baseurl }}/assets/img/logo_celero_color.png',
      link: 'https://celero.inc',
      titulo: 'Taller ACATEC',
      bio: 'Impartido por: Academias de Tecnologías<br><br>Información detallada próximamente...',
      desc: 'Pronto se anunciarán los requisitos, fechas exactas y contenidos específicos para este taller.'
    },
    'taller4': {
      logo: '{{ site.baseurl }}/assets/img/logo_celero_color.png',
      link: 'https://celero.inc',
      titulo: 'Digital Design for DSP Applications',
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

    // Cambiar al tema visual de Charlas (Burdeos)
    document.getElementById('m-content-box').classList.remove('modal-taller-theme');

    // Mostrar Credencial y ocultar Logo
    document.getElementById('m-logo-box').style.display = 'none';
    document.getElementById('m-credencial-box').style.display = 'flex';

    document.getElementById('m-foto').src = data.foto;
    document.getElementById('m-nombre-badge').innerText = data.nombre;
    document.getElementById('m-cargo-badge').innerText = data.cargo;
    document.getElementById('m-afiliacion-badge').innerText = data.afiliacion;
    document.getElementById('m-titulo').innerText = data.titulo;
    document.getElementById('m-bio').innerHTML = data.bio;   
    
    document.getElementById('m-desc-titulo').innerText = "Sobre la charla";
    document.getElementById('m-desc').innerHTML = data.desc; 

    document.getElementById('modalCharlas').classList.add('show');
    document.body.style.overflow = 'hidden';
  }

  // 3. FUNCIONES DEL MODAL PARA TALLERES
  function abrirTaller(id) {
    const data = datosTalleres[id];
    if(!data) return;

    // Aplicar tema visual Celeste para Talleres
    document.getElementById('m-content-box').classList.add('modal-taller-theme');

    // Mostrar Logo y ocultar marco de Credencial
    document.getElementById('m-credencial-box').style.display = 'none';
    document.getElementById('m-logo-box').style.display = 'flex';

    if(data.logo) {
      document.getElementById('m-logo-img').src = data.logo;
    }
    if(data.link) {
      document.getElementById('m-logo-link').href = data.link;
    }

    document.getElementById('m-titulo').innerText = data.titulo;
    document.getElementById('m-bio').innerHTML = data.bio;   
    
    document.getElementById('m-desc-titulo').innerText = "Sobre el taller y el contenido";
    document.getElementById('m-desc').innerHTML = data.desc; 

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
