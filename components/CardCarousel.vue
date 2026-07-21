<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const activeIndex = ref(0);
let timer = null;

const cards = [
  { src: './demostracion_landing.png', alt: 'Editor de CV', title: 'Editor Principal' },
  { src: './educacion.png', alt: 'Sección Educación', title: 'Formación Académica' },
  { src: './perfil.png', alt: 'Sección Perfil', title: 'Perfil Profesional' },
  { src: './mis_curriculums.png', alt: 'Mis Currículums', title: 'Panel de Currículums' },
  { src: './datos personales.png', alt: 'Datos Personales', title: 'Datos de Contacto' },
  { src: './habilidades.png', alt: 'Sección Habilidades', title: 'Habilidades y Aptitudes' }
];

// Iniciar la rotación automática (cada 1.5 segundos)
const startAutoPlay = () => {
  stopAutoPlay();
  timer = setInterval(() => {
    activeIndex.value = (activeIndex.value + 1) % cards.length;
  }, 1500);
};

// Detener la rotación
const stopAutoPlay = () => {
  if (timer) {
    clearInterval(timer);
    timer = null;
  }
};

const nextCard = (e) => {
  e.stopPropagation();
  activeIndex.value = (activeIndex.value + 1) % cards.length;
  // Reiniciamos el temporizador al hacer click manual para evitar saltos bruscos
  startAutoPlay();
};

onMounted(() => {
  startAutoPlay();
});

onUnmounted(() => {
  stopAutoPlay();
});

const getCardStyle = (index) => {
  const total = cards.length;
  const diff = (index - activeIndex.value + total) % total;

  if (diff === 0) {
    // Carta al frente
    return {
      zIndex: 30,
      opacity: 1,
      transform: 'translate(0px, 30px) scale(1) rotate(0deg)',
      pointerEvents: 'auto'
    };
  } else if (diff === 1) {
    // Segunda carta (detrás a la derecha)
    return {
      zIndex: 20,
      opacity: 0.65,
      transform: 'translate(20px, -5px) scale(0.92) rotate(3deg)',
      pointerEvents: 'none'
    };
  } else if (diff === 2) {
    // Tercera carta (más atrás a la izquierda)
    return {
      zIndex: 10,
      opacity: 0.35,
      transform: 'translate(-20px, -35px) scale(0.84) rotate(-3deg)',
      pointerEvents: 'none'
    };
  } else {
    // Cartas en cola (ocultas tras la tercera carta)
    return {
      zIndex: 0,
      opacity: 0,
      transform: 'translate(-30px, -50px) scale(0.75) rotate(-5deg)',
      pointerEvents: 'none'
    };
  }
};
</script>

<template>
  <div 
    class="card-carousel-container relative w-full max-w-[400px] h-[320px] mx-auto mt-4 flex items-center justify-center cursor-pointer select-none"
    @click="nextCard"
    @mouseenter="stopAutoPlay"
    @mouseleave="startAutoPlay"
    title="Haz clic para pasar de carta (se pausa al pasar el cursor)"
  >
    <div 
      v-for="(card, index) in cards" 
      :key="index"
      class="card-carousel-item absolute w-[90%] max-h-[220px] rounded-xl shadow-xl border border-gray-200/20 dark:border-gray-700/20 bg-white dark:bg-slate-800 p-2 transition-all duration-500 ease-out"
      :style="getCardStyle(index)"
    >
      <img :src="card.src" :alt="card.alt" class="w-full h-full object-contain rounded-lg pointer-events-none" />
      
      <!-- Tag de título flotante en la carta activa -->
      <div 
        v-if="index === activeIndex"
        class="absolute bottom-4 left-4 bg-violet-600/90 backdrop-blur-sm text-white text-[10px] px-2.5 py-0.5 rounded-full font-bold shadow-md tracking-wide"
      >
        {{ card.title }}
      </div>
    </div>
  </div>
</template>

<style scoped>
.card-carousel-container:hover .card-carousel-item {
  box-shadow: 0 20px 40px rgba(139, 92, 246, 0.15);
}

.card-carousel-item {
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
  backface-visibility: hidden;
}
</style>
