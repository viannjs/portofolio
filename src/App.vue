<template>
  <div class="relative min-h-screen w-full bg-[#050505] text-zinc-100 overflow-x-hidden selection:bg-indigo-500/30">
    
    <div class="fixed inset-0 z-0 pointer-events-none">
      <div class="absolute inset-0 opacity-[0.1]" 
           style="background-image: linear-gradient(#1e1e1e 1px, transparent 1px), linear-gradient(90deg, #1e1e1e 1px, transparent 1px); background-size: 50px 50px;">
      </div>
      <div class="absolute inset-0 opacity-[0.03] mix-blend-overlay bg-[url('https://grainy-gradients.vercel.app/noise.svg')]"></div>
      <div class="absolute top-0 left-1/2 -translate-x-1/2 w-full h-full bg-[radial-gradient(circle_at_50%_0%,rgba(67,56,202,0.1),transparent_70%)]"></div>
    </div>

    <div class="relative z-10 px-6 md:px-20 lg:px-56 flex flex-col gap-20">
      <Navbar />
      <Hero />
      <About />
      <Education />
      <Skills />
      <Project />
    </div>
  </div>
</template>

<script setup>
import Navbar from './components/navbar.vue';
import Hero from './components/hero.vue';
import About from './components/about.vue';
import Skills from './components/skills.vue';
import Education from './components/education.vue';
import Project from './components/project.vue';
</script>

<style>
body { background-color: #050505; margin: 0; font-family: 'Inter', sans-serif; }
section { background-color: transparent !important; }
</style>