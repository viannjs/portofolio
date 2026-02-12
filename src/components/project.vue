<template>
  <section id="project" class="relative py-20 bg-transparent overflow-hidden">
    <div class="max-w-7xl mx-auto px-6 w-full">
      
      <div class="flex items-center gap-4 mb-12 transition-all duration-700"
           :class="isVisible ? 'translate-x-0 opacity-100' : '-translate-x-10 opacity-0'">
        <h2 class="text-xl md:text-2xl font-black uppercase italic text-white tracking-tighter">
          Featured <span class="text-indigo-500">Projects</span>
        </h2>
        <div class="h-[1px] w-12 bg-zinc-800"></div>
      </div>

      <div class="max-w-5xl transition-all duration-1000 delay-300"
           :class="isVisible ? 'translate-y-0 opacity-100' : 'translate-y-10 opacity-0'">
        
        <div class="space-y-6"> 
          <div v-for="project in projectList" :key="project.id" 
               class="group relative flex flex-col md:flex-row w-full bg-white/[0.02] border border-white/5 rounded-[2.5rem] overflow-hidden hover:bg-white/[0.04] hover:border-indigo-500/30 transition-all duration-500 backdrop-blur-md">
            
            <div class="w-full md:w-2/5 h-64 md:h-auto relative overflow-hidden bg-zinc-950 flex-shrink-0">
              
              <div class="absolute top-4 left-4 z-20 flex gap-2">
                <div v-for="tech in project.techStack" :key="tech.name"
                  class="group/badge flex items-center bg-black/80 backdrop-blur-xl border border-white/10 rounded-full h-9 px-2 overflow-hidden transition-all duration-500 max-w-[36px] hover:max-w-[140px]"
                >
                  <img :src="tech.logoUrl" :alt="tech.name" class="w-5 h-5 object-contain flex-shrink-0" />
                  <span class="ml-2 text-[10px] font-black text-white whitespace-nowrap opacity-0 group-hover/badge:opacity-100 uppercase tracking-widest">
                    {{ tech.name }}
                  </span>
                </div>
              </div>

              <div class="absolute inset-0 bg-gradient-to-b from-black/40 via-transparent to-transparent z-10 opacity-60"></div>

              <img :src="project.image" 
                   class="w-full h-full object-cover grayscale group-hover:grayscale-0 group-hover:scale-110 transition-all duration-[1.5s] opacity-40 group-hover:opacity-100" />
            </div>

            <div class="w-full md:w-3/5 p-8 md:p-10 flex flex-col justify-between">
              <div>
                <a :href="project.projectUrl" target="_blank" class="inline-block group/title mb-4"> 
                  <h3 class="text-2xl md:text-3xl font-black text-white uppercase italic tracking-tighter group-hover/title:text-indigo-400 transition-colors flex items-center gap-3">
                    {{ project.title }}
                    <svg class="opacity-0 -translate-x-2 group-hover/title:opacity-100 group-hover/title:translate-x-0 transition-all duration-300 text-indigo-500" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3">
                      <line x1="7" y1="17" x2="17" y2="7"></line>
                      <polyline points="7 7 17 7 17 17"></polyline>
                    </svg>
                  </h3>
                </a>
                <p class="text-zinc-400 text-base md:text-lg leading-relaxed font-medium line-clamp-3">
                  {{ project.description }}
                </p>
              </div>

              <div class="flex items-center justify-between pt-6 mt-8 border-t border-white/5">
                <span class="text-[10px] font-black tracking-[0.3em] text-zinc-500 uppercase italic">
                  {{ project.date }}
                </span>
                
                <div class="flex gap-2">
                  <div class="w-1.5 h-1.5 rounded-full bg-indigo-500"></div>
                  <div class="w-1.5 h-1.5 rounded-full bg-zinc-800"></div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <div class="pt-12 flex items-center gap-4">
          <div class="h-[1px] w-20 bg-zinc-800"></div>
          <div class="w-2 h-2 rotate-45 border border-indigo-500/50"></div>
        </div>

      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue';

const isVisible = ref(false);

const projectList = [
  {
    id: 1,
    title: "E-Commerce Re-design",
    projectUrl: "#",
    description: "Membangun ulang antarmuka toko online dengan fokus pada performa tinggi dan UX yang intuitif.",
    date: "JAN 2024",
    image: "https://images.unsplash.com/photo-1557821552-17105176677c?q=80&w=1632",
    techStack: [
      { name: "Vue.js", logoUrl: "https://v2.vuejs.org/images/logo.png" },
      { name: "Tailwind", logoUrl: "https://upload.wikimedia.org/wikipedia/commons/d/d5/Tailwind_CSS_Logo.svg" }
    ]
  },
  {
    id: 2,
    title: "SaaS Dashboard UI Kit",
    projectUrl: "#",
    description: "Sistem desain modern untuk aplikasi manajemen data perusahaan dengan visualisasi data kompleks.",
    date: "DES 2023",
    image: "https://images.unsplash.com/photo-1460925895917-afdab827c52f?q=80&w=1615",
    techStack: [
      { name: "React", logoUrl: "https://upload.wikimedia.org/wikipedia/commons/a/a7/React-icon.svg" },
      { name: "Firebase", logoUrl: "https://www.vectorlogo.zone/logos/firebase/firebase-icon.svg" }
    ]
  }
];

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    if (entries[0].isIntersecting) isVisible.value = true;
  }, { threshold: 0.1 });
  
  const target = document.querySelector('#project');
  if (target) observer.observe(target);
});
</script>k