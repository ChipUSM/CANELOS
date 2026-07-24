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
	<p align="center" style="margin-top: 40px;"> <img src="{{ "/assets/img/canelos_poster_brillante.jpg" | relative_url }}" alt="Poster CANELOS" width="600" style="max-width: 100%"/> </p>
</div>

<div class="reveal">
  <h2 align="left" style="font-weight: bold;">Programa</h2>
	<h3 align="justify" style="font-size: 1.2em; line-height: 1.6; max-width: 1200px; margin: 0;">
			La asignación de horarios para cada charlista se encuentra sujeta a disponibilidad de los mismos pero los horarios tentativos para el evento son los siguientes:
	</h3>
	<p align="center" style="margin-top: 40px;"> <img src="{{ "/assets/img/material26/horario_v3.jpeg" | relative_url }}" alt="Itinerario" width="600" style="max-width: 100%"/>
	</p>
</div>

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
        <div class="charla-card reveal" onclick="abrirCharla('alva')" style="display: flex; align-items: center; gap: 25px; width: 100%; background-color: #f7f9fc; padding: 20px 30px; border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.05); border-left: 5px solid #47001e;">
            <img src="../assets/img/material26/alva_avila.jpg" alt="Alva Avila" style="width: 90px; height: 90px; border-radius: 10px; object-fit: cover;">
            <div style="text-align: left;">
                <h3 style="margin: 0 0 5px 0; font-size: 1.4em; color: #222; font-weight: 700;">Alva Avila</h3>
                <h4 style="margin: 0; font-size: 1.1em; color: #47001e; font-weight: 600; font-style: italic; line-height: 1.3;">"Por Anunciar"</h4>
            </div>
        </div>

        <!-- Charla 4 -->
        <div class="charla-card reveal" onclick="abrirCharla('carlos')" style="display: flex; align-items: center; gap: 25px; width: 100%; background-color: #f7f9fc; padding: 20px 30px; border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.05); border-left: 5px solid #47001e;">
            <img src="../assets/img/material26/carlos_silva.jpeg" alt="Expositor 4" style="width: 90px; height: 90px; border-radius: 10px; object-fit: cover;">
            <div style="text-align: left;">
                <h3 style="margin: 0 0 5px 0; font-size: 1.4em; color: #222; font-weight: 700;">Expositor 4</h3>
                <h4 style="margin: 0; font-size: 1.1em; color: #47001e; font-weight: 600; font-style: italic; line-height: 1.3;">"Introducción al Diseño de Circuitos Integrados Digitales"</h4>
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

	  <p align="center" style="margin-top: 40px;"> <img src="{{ "/assets/img/material26/CANELOS26_D.png" | relative_url }}" alt="Poster CANELOS" width="600" style="max-width: 100%"/> </p>

    <!-- Línea de Tiempo Profesional -->
    <div class="timeline-container">
        <div class="timeline-line"></div>
        
        <!-- Paso 00 (Punto inicial / Actual) -->
        <div class="timeline-step">
            <div class="timeline-bg-number">00</div>
            <!-- Nota que este punto tiene la clase "active" para verse relleno -->
            <div class="timeline-dot active"></div>
            <div class="timeline-content">
                <div class="timeline-date">20 de Julio, 2026</div>
                <div class="timeline-text">Inicio de<br>Postulaciones</div>
            </div>
        </div>

        <!-- Paso 01 -->
        <div class="timeline-step">
            <div class="timeline-bg-number">01</div>
            <!-- Cuando llegue este paso, puedes agregarle la clase "active" al div de abajo -->
            <div class="timeline-dot"></div>
            <div class="timeline-content">
                <div class="timeline-date">20 de Agosto, 2026</div>
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
      bio: 'Pedro Toledo is a Staff Analog Design at Synopsys, Lisbon, where he works in the development of high-speed SerDes and equalization circuits in advanced CMOS technologies, including nanosheet, GAA, and FinFET. His work focuses on PHY building blocks for PCIe, USB, and MPHY interfaces, covering CTLE, DFE, CDR, LDO, and signaldetection circuits. He received the Ph.D. degree in Microelectronics from Politecnico di Torino, Italy, and the Federal University of Rio Grande do Sul (UFRGS), Brazil, where he graduated Summa Cum Laude. His research interests include DIGOTA architectures, ZTC/GZTC MOSFET modeling, low-voltage analog design, and digital-based analog processing. Dr. Toledo has authored numerous papers in IEEE journals and conferences and serves as reviewer for several IEEE Transactions and Letters. He is the recipient of multiple awards, including the SBMicro Best PhD Thesis Award, the IEEE ICECS Best Student Paper Award, and the YEF-ECE Best Paper Award.',
      desc: 'While digital Integrated Circuits (IC) have been reaping the benefits of CMOS technology scaling in terms of speed, power consumption, and area, the techniques used for analog signal processing have not progressed at the same rate. It is evident that there have been substantial and ongoing improvements in the performance of digital circuits when compared to analog building blocks. To address this disparity, there is a growing trend towards exploring alternative IC design strategies that leverage digital-in-concept methodologies to implement analog functions. By capitalizing on the well-established fullyautomated EDA digital tools, reimagining analog functions in digital terms holds the promise of making Analog IC blocks more conducive to achieving energy efficiency and adapting to the shrinking feature sizes of new technologies. This presentation aims to showcase the current state-of-the-art digital-based analog building blocks, such as OTA, comparators, and converters, along with their impact on emerging applications and technologies. This shift in approach has the potential to revolutionize the field of analog signal processing and pave the way for undefined advancements in IC design.'
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
    'alva': {
      foto: '../assets/img/material26/alva_avila.jpg',
      nombre: 'Alva Avila',
      cargo: 'Cargo por confirmar',
      afiliacion: 'Universidad de los Andes',
      titulo: '"Por Anunciar"',
      bio: 'Alba Avila es la directora del centro de microelectrónica (CMUA) y Profesora e investigadora del departamento de Ingeniería Eléctrica y Electrónica de la Universidad de los Andes. Es física, ingeniera eléctrica, máster en ingeniera eléctrica de la Universidad de los Andes y doctora de la Universidad de Cambridge en el Reino Unido. Es una apasionada investigadora interdisciplinaria en la ciencia e ingeniería de materiales. Ha trabajado en nanomateriales para aplicaciones en energía y sensado, también ha desarrollado tecnologías humanitarias para monitoreo de agua, almacenamiento de enrgía y alfabetización tecnológica. Así mismo, ha estudiado propiedades de materiales a diferentes escalas y generados kits educativos para la enseñanza de nanotecnología y nuevos materiales. Además, ha promovido programas de inclusión y vocaciones científico-técnicas en colaboración con proyectos de EU y LATAM. Es fellow del resilence center del imperial college, Distinguished lecturer of EDS IEEE y miembro de WIE.',
      desc: 'Pronto revelaremos la información detallada sobre esta charla plenaria y las temáticas específicas que nuestro expositor compartirá con los asistentes del evento.'
    },
    'carlos': {
      foto: '../assets/img/material26/carlos_silva.jpeg',
      nombre: 'Carlos Silva',
      cargo: 'Cargo por confirmar',
      afiliacion: 'Universidad Autónoma de Barcelona',
      titulo: 'Introducción al Diseño de Circuitos Integrados Digitales',
      bio: 'Es doctor por la Universidad Autónoma de Barcelona. Ha realizado estancias de Posdoc en el Instituto Nacional Politécnico de Grenoble, Grenoble-Francia y en Texas A&M University. Actualmente es Profesor titular de la PUCP. Director-Fundador del Grupo de Investigación en Microelectrónica. Desde 2019-2024 fue director de la Dirección de Fomento de la Investigación de la PUCP. Silva-Cárdenas es autor del primer circuito integrado digital peruano que logró su fabricación y cuenta con más de 80 publicaciones, es autor de un libro, tres capítulos de libros y coeditor de dos libros. Ha impartido cursos de posgrado en las universidades: Complutense de Madrid, Valencia y Autónoma de Barcelona, y en la Universidad Nacional de Tucumán en Argentina. Ha sido General Chair de una docena de congresos internacionales y del evento flagship de latinoamérica LASCAS2026 realizado en Arequipa-Peru en febrero de 2026.. Ha recibido premios, como el Premio de RECONOCIMIENTO A LA INVESTIGACIÓN de la PUCP durante los últimos 9 años, el Premio al Ingeniero Eminente de la Región 9 de IEEE Latinoamérica en 2019 y el Premio ELEKTRON en 2025 por su “liderazgo en Microelectrónica, su rol clave en la regulación de las telecomunicaciones y su aporte decisivo a la formación e investigación en ingeniería en el Perú”. Es miembro del Board of Goverment de CASS-IEEE desde 2024-2026.',
      desc: 'La charla provee los conceptos básicos para realizar el diseño de circuitos integrados digitales por medio de varios métodos de integración como la lógica complementaria MOS (CMOS) y lógica dinámica que permitan realizar el diseños de circuitos integrados de aplicación específica (ASIC).Los temas cubren: Conceptos y funcionamiento del MOSFET, Regiones de funcionamiento, Voltaje umbral, Efecto de cuerpo, Ecuaciones de diseño MOS y Curvas Características, Nivel de Inversión, Efecto de Modulación de Canal. Métodos de implementación de circuitos digitales tanto combinacional como secuencial. Latches y registros estáticos y dinámicos. Flip flop. Diagrama de máscaras, layout y reglas de diseño, simulación y caracterización de dispositivos.'
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
