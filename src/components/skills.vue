<template>
  <section id="skills" class="relative py-20 bg-transparent overflow-hidden">
    <div class="max-w-7xl mx-auto px-6 w-full">
      
      <div class="max-w-5xl transition-all duration-1000 delay-150"
           :class="isVisible ? 'translate-y-0 opacity-100' : 'translate-y-10 opacity-0'">
        
        <div class="flex items-center gap-4 mb-8">
          <h2 class="text-xl md:text-2xl font-black uppercase italic text-white tracking-tighter">
            Technical <span class="text-indigo-500">Skills</span>
          </h2>
          <div class="h-[1px] w-12 bg-zinc-800"></div>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-x-16 gap-y-6">
          <div v-for="skill in skills" :key="skill.name" class="group">
            
            <div class="flex justify-between items-end mb-3">
              <div class="flex items-center gap-4">
                <div class="relative p-2 bg-zinc-900/50 rounded-xl border border-white/5 group-hover:border-indigo-500/50 transition-all duration-500">
                  <img :src="skill.logo" :alt="skill.name" class="w-5 h-5 object-contain grayscale group-hover:grayscale-0 transition-all" />
                </div>
                
                <div class="flex flex-col">
                  <span class="text-[10px] font-black tracking-[0.2em] text-zinc-500 uppercase leading-none mb-1">Stack</span>
                  <span class="text-lg font-bold text-white tracking-tight uppercase italic group-hover:text-indigo-400 transition-colors">
                    {{ skill.name }}
                  </span>
                </div>
              </div>

              <span class="text-xs font-mono font-bold text-indigo-400/70 group-hover:text-indigo-400 transition-colors">
                {{ skill.percentage }}%
              </span>
            </div>
            
            <div class="relative w-full h-2 bg-zinc-900 rounded-full overflow-hidden border border-white/5">
              <div 
                class="h-full rounded-full transition-all duration-[2500ms] ease-[cubic-bezier(0.34,1.56,0.64,1)] relative overflow-hidden"
                :style="{ 
                  width: isVisible ? skill.percentage + '%' : '0%', 
                  background: 'linear-gradient(90deg, #4f46e5 0%, #818cf8 100%)',
                  boxShadow: '0 0 20px rgba(79, 70, 229, 0.2)'
                }"
              >
                <div class="absolute inset-0 bg-gradient-to-r from-transparent via-white/20 to-transparent animate-shine"></div>
              </div>
            </div>
          </div>
        </div>

        <div class="pt-12 flex items-center gap-3">
          <div class="h-[1px] w-20 bg-zinc-800"></div>
          <div class="flex gap-1.5">
            <div class="w-1.5 h-1.5 rounded-full bg-indigo-500/50"></div>
            <div class="w-1.5 h-1.5 rounded-full bg-zinc-900"></div>
          </div>
        </div>

      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const isVisible = ref(false)

const skills = [
  { name: 'Vue.js / Vite', percentage: 90, logo: 'https://v2.vuejs.org/images/logo.png' },
  { name: 'Tailwind CSS', percentage: 95, logo: 'https://upload.wikimedia.org/wikipedia/commons/d/d5/Tailwind_CSS_Logo.svg' },
  { name: 'JavaScript', percentage: 85, logo: 'https://upload.wikimedia.org/wikipedia/commons/6/6a/JavaScript-logo.png' },
  { name: 'UI Design', percentage: 70, logo: 'https://upload.wikimedia.org/wikipedia/commons/3/33/Figma-logo.svg' },
]

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    if (entries[0].isIntersecting) isVisible.value = true
  }, { threshold: 0.1 })
  const target = document.querySelector('#skills')
  if (target) observer.observe(target)
})
</script>

<style scoped>
@keyframes shine {
  0% { transform: translateX(-100%) skewX(-20deg); }
  100% { transform: translateX(200%) skewX(-20deg); }
}
.animate-shine { animation: shine 4s infinite; }
section { font-family: 'Inter', sans-serif; }
</style>