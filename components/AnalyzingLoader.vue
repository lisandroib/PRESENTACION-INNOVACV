<template>
  <div class="analyzing-loader-container is-comparing w-full flex flex-row items-center justify-center gap-6">
    <div class="relative flex items-center justify-center w-[60px] h-[60px] flex-shrink-0">
      <svg viewBox="0 0 36 36" class="circular-progress-svg absolute inset-0 w-full h-full">
        <circle cx="18" cy="18" r="15.9155" class="circular-progress-bg" />
        <circle cx="18" cy="18" r="15.9155" class="circular-progress-fill" />
      </svg>
    </div>
    
    <div class="flex flex-col items-start justify-center">
      <div class="analyzing-loader-text text-xl">
        <span v-for="(letter, i) in 'Analizando...'.split('')" :key="i" class="analyzing-letter" :style="{ animationDelay: `${i * 0.1}s` }">{{ letter }}</span>
      </div>
      <span class="text-[10px] font-bold uppercase tracking-wider text-slate-400 mt-0.5">Compatibilidad IA</span>
    </div>
  </div>
</template>

<style scoped>
.analyzing-loader-container {
  padding: 8px 16px;
  background: transparent;
}

.circular-progress-svg {
  transform: rotate(-90deg);
}

.circular-progress-bg {
  fill: none;
  stroke: rgba(167, 139, 250, 0.1);
  stroke-width: 2.5;
}

.circular-progress-fill {
  fill: none;
  stroke: #8b5cf6;
  stroke-width: 2.5;
  stroke-linecap: round;
  stroke-dasharray: 100;
  stroke-dashoffset: 100;
}

.is-comparing .circular-progress-fill {
  animation: dashSpin 2s ease-in-out infinite, colorSpin 4s linear infinite;
}

@keyframes dashSpin {
  0% {
    stroke-dasharray: 1, 200;
    stroke-dashoffset: 0;
  }
  50% {
    stroke-dasharray: 89, 200;
    stroke-dashoffset: -35px;
  }
  100% {
    stroke-dasharray: 89, 200;
    stroke-dashoffset: -100px;
  }
}

@keyframes colorSpin {
  0% { stroke: #8b5cf6; }
  50% { stroke: #c084fc; }
  100% { stroke: #8b5cf6; }
}

.analyzing-loader-text {
  display: flex;
  font-weight: 800;
  color: #8b5cf6;
  letter-spacing: 1px;
}

.analyzing-letter {
  animation: glowBounce 1.4s infinite ease-in-out both;
}

@keyframes glowBounce {
  0%, 80%, 100% { 
    transform: translateY(0); 
    opacity: 0.5;
    text-shadow: none;
  }
  40% { 
    transform: translateY(-4px); 
    opacity: 1;
    text-shadow: 0 0 12px rgba(139, 92, 246, 0.6);
  }
}
</style>
