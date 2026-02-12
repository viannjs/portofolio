<template>
  <section class="relative min-h-[90vh] flex items-center bg-transparent">
    <div class="max-w-7xl mx-auto px-6 w-full">
      <div class="grid md:grid-cols-2 grid-cols-1 items-center gap-10">
        <div class="order-2 md:order-1 transition-all duration-1000 ease-out"
             :class="mounted ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-10'">
          <h1 class="text-5xl md:text-8xl font-black text-white leading-none tracking-tighter uppercase italic mb-6">
            <span class="text-indigo-500 not-italic font-light block text-2xl tracking-[0.3em] mb-2">Portfolio 2024</span>
            Benediktus <br />
            <span class="text-transparent" style="-webkit-text-stroke: 1px white;">Jovian</span>
          </h1>
          <p class="max-w-md text-zinc-500 text-lg leading-relaxed mb-10 border-l-2 border-indigo-500/30 pl-6">
            Creative Developer & UI Designer. Berfokus pada pembangunan pengalaman digital yang sinematik dan minimalis.
          </p>
          <div class="flex items-center gap-6">
            <button class="group relative px-8 py-4 bg-white text-black font-black uppercase tracking-widest text-sm transition-all duration-300 hover:bg-indigo-500 hover:text-white rounded-full overflow-hidden">
              <span class="relative z-10">Follow Me</span>
              <div class="absolute inset-0 bg-indigo-600 translate-y-full group-hover:translate-y-0 transition-transform duration-300"></div>
            </button>
            <div class="h-[1px] w-20 bg-zinc-800"></div>
          </div>
        </div>

        <div class="order-1 md:order-2 flex justify-center md:justify-end transition-all duration-1000 delay-300"
             :class="mounted ? 'opacity-100 scale-100 blur-0' : 'opacity-0 scale-90 blur-xl'">
          
          <div class="relative group p-8">
            
            <div class="absolute inset-0 z-0 opacity-0 group-hover:opacity-100 transition-opacity duration-500 pointer-events-none">
              <div class="flame blue-flame-1"></div>
              <div class="flame blue-flame-2"></div>
              <div class="flame blue-flame-3"></div>
              <div class="absolute inset-10 bg-blue-600/20 blur-[80px] rounded-full group-hover:animate-pulse"></div>
            </div>

            <div class="relative z-10 p-2 bg-[#050505] rounded-full border border-white/10 group-hover:border-blue-500/50 transition-all duration-500">
              <img 
                :src="profileImg" 
                alt="Profile" 
                class="w-64 h-64 md:w-80 md:h-80 rounded-full object-cover grayscale group-hover:grayscale-0 transition-all duration-700 shadow-2xl" 
              />
            </div>
            
            <div class="absolute -inset-2 border border-indigo-500/10 rounded-full animate-spin-slow group-hover:border-blue-400/30 group-hover:scale-110 transition-all duration-700"></div>
          </div>

        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import profileImg from '../assets/minju.jpg'

const mounted = ref(false)
onMounted(() => { mounted.value = true })
</script>

<style scoped>
@keyframes spin-slow {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}
.animate-spin-slow {
  animation: spin-slow 20s linear infinite;
}

/* BASE STYLE API */
.flame {
  @apply absolute rounded-full;
  background: radial-gradient(circle at center, #3b82f6 0%, #1d4ed8 40%, transparent 70%);
  filter: blur(20px);
  mix-blend-mode: screen;
  bottom: 10%;
  left: 50%;
  transform: translateX(-50%);
  width: 100px;
  height: 100px;
}

/* API 1: Melingkar lewat KIRI ke Atas */
.blue-flame-1 {
  animation: orbit-left 2s infinite linear;
}

/* API 2: Melingkar lewat KANAN ke Atas */
.blue-flame-2 {
  animation: orbit-right 2.5s infinite linear;
  animation-delay: 0.7s;
}

/* API 3: Sumbu Tengah (Inti) */
.blue-flame-3 {
  width: 150px;
  height: 150px;
  animation: orbit-center 1.8s infinite ease-in-out;
  animation-delay: 0.3s;
}

/* KEYFRAMES UNTUK EFEK MELINGKAR (ORBITING) */
@keyframes orbit-left {
  0% { transform: translate(-50%, 0) scale(0.5); opacity: 0; }
  30% { opacity: 0.8; }
  /* Bergerak melengkung ke kiri (-150px) dan naik (-200px) */
  100% { transform: translate(-180%, -280px) scale(1.5); opacity: 0; }
}

@keyframes orbit-right {
  0% { transform: translate(-50%, 0) scale(0.5); opacity: 0; }
  30% { opacity: 0.8; }
  /* Bergerak melengkung ke kanan (150px) dan naik (-200px) */
  100% { transform: translate(120%, -320px) scale(1.2); opacity: 0; }
}

@keyframes orbit-center {
  0% { transform: translate(-50%, 0) scale(1); opacity: 0; }
  30% { opacity: 0.5; }
  100% { transform: translate(-50%, -350px) scale(2); opacity: 0; }
}
</style>