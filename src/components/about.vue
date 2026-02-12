<template>
  <section id="about" class="relative -mt-32 pt-0 pb-20 bg-transparent">
    <div class="max-w-7xl mx-auto px-6 w-full">
      
      <div class="max-w-4xl transition-all duration-1000 delay-300"
           :class="isVisible ? 'translate-y-0 opacity-100' : 'translate-y-10 opacity-0'">
        
        <div class="flex items-center gap-4 mb-8">
          <h2 class="text-xl md:text-2xl font-black uppercase italic text-white tracking-tighter">
            About <span class="text-indigo-500">Me</span>
          </h2>
          <div class="h-[1px] w-12 bg-zinc-800"></div>
        </div>

        <div class="space-y-6">
          <h3 class="text-4xl md:text-6xl font-black text-white tracking-tighter italic uppercase leading-[0.85]">
            Halo, Saya <span class="text-indigo-500">Alex.</span>
          </h3>

          <div class="grid grid-cols-1 md:grid-cols-2 gap-8 md:gap-12 text-zinc-400 font-medium leading-relaxed">
            <div class="space-y-4 text-lg md:text-xl">
              <p>
                Saya adalah seorang <span class="text-white">Frontend Developer</span> yang mendedikasikan waktu untuk merakit antarmuka digital yang tidak hanya berfungsi, tapi juga berbicara secara visual.
              </p>
              <p>
                Fokus utama saya adalah menciptakan pengalaman pengguna yang mulus menggunakan ekosistem <span class="text-white">Vue.js</span> dan <span class="text-white">Tailwind CSS</span>. Bagi saya, menulis kode adalah tentang memecahkan masalah kompleks menjadi solusi yang elegan.
              </p>
            </div>

            <div class="space-y-4 text-base md:text-lg border-l border-zinc-800/50 pl-6 md:pl-8">
              <p>
                Di luar pekerjaan teknis, saya adalah penikmat desain minimalis dan penganut prinsip <span class="italic text-indigo-400">"less is more"</span>. Saya percaya bahwa teknologi terbaik adalah yang memudahkan hidup manusia.
              </p>
              <p>
                Saat ini, saya terbuka untuk kolaborasi pada proyek-proyek inovatif. Jika Anda memiliki ide yang ingin diwujudkan menjadi kenyataan digital, mari kita bicara dan buat sesuatu yang luar biasa.
              </p>
              
              <div class="pt-4 flex gap-2">
                <div class="w-1.5 h-1.5 rounded-full bg-indigo-500"></div>
                <div class="w-1.5 h-1.5 rounded-full bg-zinc-800"></div>
                <div class="w-1.5 h-1.5 rounded-full bg-zinc-800"></div>
              </div>
            </div>
          </div>
        </div>

      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue';

const isVisible = ref(false);

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    if (entries[0].isIntersecting) isVisible.value = true;
  }, { threshold: 0.1 });
  
  const target = document.querySelector('#about');
  if (target) observer.observe(target);
});
</script>