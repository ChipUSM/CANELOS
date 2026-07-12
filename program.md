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
</style>

<div class="reveal">

	<h3 align="justify" style="font-size: 1.2em; line-height: 1.6; max-width: 1200px; margin: 0;">
			La asignación de horarios para cada charlista se encuentra sujeta a disponibilidad de los mismos pero la posible asignación de bloques es la siguiente:
	</h3>

	<p align="center" style="margin-top: 40px;"> <img src="..\assets\img\material26\iterinario_preventivo.png" alt="Descripción de la imagen" width="600" style="max-width: 100%"/>
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

	<p align="center" style="margin-top: 40px;"> <img src="../assets/img/canelos_poster_brilloso.jpg" alt="Descripción de la imagen" width="600" style="max-width: 100%"/> </p>

</div>

<br>
<hr>
<br>

<div class="reveal" style="font-weight: bold;">

	<h2 align="left" style="font-weight: bold;">Talleres</h2>

	<h3 align="center" style="font-weight: bold; margin-top: 40px; margin-bottom: 40px;">Próximamente...</h3>

</div>

<br>
<hr>
<br>

<div class="reveal" style="font-weight: bold;">

	<h2 align="left" style="font-weight: bold;">Charlas plenarias</h2>

	<h3 align="center" style="font-weight: bold; margin-top: 40px; margin-bottom: 40px;">Próximamente...</h3>

</div>

<br>
<hr>
<br>

<div class="reveal" style="font-weight: bold;">

	<h2 align="left" style="font-weight: bold;">Sesión de Posters</h2>

	<h3 align="center" style="font-weight: bold; margin-top: 40px; margin-bottom: 40px;">Próximamente...</h3>

</div>

<script>
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