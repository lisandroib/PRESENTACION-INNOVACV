<template>
  <div class="ats-scanner-container relative w-[320px] h-[390px] bg-white border border-slate-200/60 rounded-xl shadow-xl overflow-hidden my-auto mx-auto select-none">
    <!-- Scanner Line -->
    <div class="scanner-bar absolute left-0 right-0 h-[3px] bg-gradient-to-r from-transparent via-violet-600 to-transparent z-30 shadow-[0_0_10px_#7c3aed]"></div>
    
    <!-- Document Container (Scaled down for mockup) -->
    <div class="cv-document w-[800px] absolute top-0 left-1/2 transform -translate-x-1/2 scale-[0.38] origin-top text-left p-6" style="color: #1e293b; background: white;">
      <!-- Harvard CV Layout -->
      <div style="font-family: 'Inter', sans-serif; color: #1e293b; max-width: 800px; margin: 0 auto; padding: 20px;">
        <!-- Header -->
        <h1 style="text-align: center; font-size: 2.5em; font-weight: 800; margin-bottom: 5px; color: #1e293b; text-transform: uppercase;">nombre y apellido</h1>
        <p style="text-align: center; margin-bottom: 30px; font-size: 11px; color: #475569;">Yerba Buena, Tucumán | +543815999159 | ibarra.lisandro@gmail.com</p>

        <!-- Profile -->
        <h2 style="font-size: 14px; font-weight: 700; color: #1e293b; text-transform: uppercase; border-bottom: 2px solid #e2e8f0; padding-bottom: 4px; margin-top: 25px; margin-bottom: 15px; letter-spacing: 1px;">Perfil Profesional</h2>
        <p style="text-align: justify; font-size: 11px; line-height: 1.5;">Soy un desarrollador apasionado y orientado a resultados, dedicado a construir soluciones innovadoras y eficientes. Mi enfoque se centra en escribir código limpio y escalable, priorizando la calidad y el rendimiento. Disfruto resolviendo problemas complejos y aplicando nuevas tecnologías para impulsar el éxito de los proyectos.</p>

        <!-- Skills -->
        <h2 style="font-size: 14px; font-weight: 700; color: #1e293b; text-transform: uppercase; border-bottom: 2px solid #e2e8f0; padding-bottom: 4px; margin-top: 25px; margin-bottom: 15px; letter-spacing: 1px;">Habilidades</h2>
        <ul style="margin: 0 0 15px 0; padding-left: 15px; font-size: 11px; list-style-type: disc; line-height: 1.4;">
          <li style="margin-bottom: 2px;">Python</li>
          <li style="margin-bottom: 2px;">JavaScript</li>
          <li style="margin-bottom: 2px;">SQL</li>
          <li style="margin-bottom: 2px;">Git</li>
          <li style="margin-bottom: 2px;">APIs REST</li>
          <li style="margin-bottom: 2px;">Desarrollo Web</li>
        </ul>

        <!-- Education -->
        <h2 style="font-size: 14px; font-weight: 700; color: #1e293b; text-transform: uppercase; border-bottom: 2px solid #e2e8f0; padding-bottom: 4px; margin-top: 25px; margin-bottom: 15px; letter-spacing: 1px;">Educación</h2>
        <p style="display: flex; justify-content: space-between; margin: 0 0 2px 0; align-items: baseline;">
          <strong style="font-size: 13px; text-transform: uppercase;">Bachiller en informática</strong>
          <strong style="font-size: 12px; color: #475569;">-</strong>
        </p>
        <p style="margin: 0 0 15px 0; font-size: 12px;">Colegio del Sol</p>

        <p style="display: flex; justify-content: space-between; margin: 0 0 2px 0; align-items: baseline;">
          <strong style="font-size: 13px; text-transform: uppercase;">Ingeniería Informática</strong>
          <strong style="font-size: 12px; color: #475569;">2021 - 2026</strong>
        </p>
        <p style="margin: 0 0 15px 0; font-size: 12px;">Universidad del Norte Santo Tomás de Aquino</p>

        <!-- Experience -->
        <h2 style="font-size: 14px; font-weight: 700; color: #1e293b; text-transform: uppercase; border-bottom: 2px solid #e2e8f0; padding-bottom: 4px; margin-top: 25px; margin-bottom: 15px; letter-spacing: 1px;">Experiencia</h2>
        <p style="display: flex; justify-content: space-between; margin: 0 0 2px 0; align-items: baseline;">
          <strong style="font-size: 13px; text-transform: uppercase;">La Mascotera</strong>
          <strong style="font-size: 12px; color: #475569;">MARZO 2025 - SEPTIEMBRE 2025</strong>
        </p>
        <p style="margin: 0 0 6px 0; font-size: 12px; color: #475569;">Rol: Pasante de IT</p>
        <ul style="margin: 0 0 15px 0; padding-left: 15px; font-size: 11px; list-style-type: disc; line-height: 1.5;">
          <li style="margin-bottom: 4px;">Colaboré en la resolución de incidencias de software, optimizando el rendimiento de las aplicaciones internas y la experiencia del usuario.</li>
          <li style="margin-bottom: 4px;">Configuré y desplegué herramientas de software en estaciones de trabajo, asegurando la funcionalidad y compatibilidad de los sistemas.</li>
          <li style="margin-bottom: 4px;">Desarrollé y mantuve scripts básicos en Python para la automatización de tareas administrativas, mejorando la eficiencia operativa.</li>
          <li style="margin-bottom: 4px;">Brindé soporte técnico de primer nivel, diagnosticando problemas de software y hardware, y escalando los casos complejos al equipo superior.</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<style>
.ats-scanner-container {
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.12), inset 0 0 10px rgba(0, 0, 0, 0.02);
}

.scanner-bar {
  top: 0;
  animation: scanEffect 4s ease-in-out infinite;
}

/* Evitar que Slidev aplique animaciones de revelación o transición a las viñetas del CV */
.cv-document li {
  animation: none !important;
  transition: none !important;
  opacity: 1 !important;
  transform: none !important;
}

@keyframes scanEffect {
  0% {
    top: 0%;
    opacity: 0;
  }
  10% {
    opacity: 1;
  }
  90% {
    opacity: 1;
  }
  100% {
    top: 100%;
    opacity: 0;
  }
}
</style>
