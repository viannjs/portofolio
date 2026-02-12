<template>
  <section class="py-16 bg-white text-zinc-900">
    <div class="max-w-3xl mx-auto px-6">
      <h2 class="text-2xl font-bold mb-10 tracking-tight border-b pb-4 border-zinc-100">
        Education
      </h2>

      <div class="space-y-12">
        <div v-for="edu in educationList" :key="edu.school" class="flex items-start gap-4">
          
          <div class="flex-shrink-0 mt-1">
            <div class="w-12 h-12 rounded-lg bg-zinc-100 border border-zinc-200 flex items-center justify-center overflow-hidden">
              <img v-if="edu.logo" :src="edu.logo" :alt="edu.school" class="w-full h-full object-cover" />
              <span v-else class="text-zinc-400 font-bold text-xs uppercase">{{ edu.school.substring(0,2) }}</span>
            </div>
          </div>

          <div class="flex-grow flex justify-between items-start">
            <div>
              <h3 class="text-lg font-bold leading-none text-zinc-900">{{ edu.school }}</h3>
              <p class="text-zinc-500 mt-2 font-medium">{{ edu.major }}</p>
              <p v-if="edu.description" class="text-sm text-zinc-400 mt-1">{{ edu.description }}</p>
            </div>

            <div class="text-right">
              <span class="text-sm font-mono font-medium text-zinc-400 bg-zinc-50 px-3 py-1 rounded-full border border-zinc-100">
                {{ edu.year }}
              </span>
            </div>
          </div>

        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const educationList = [
  {
    school: 'Universitas Indonesia',
    major: 'Teknik Informatika',
    year: '2020 — 2024',
    logo: 'https://upload.wikimedia.org/wikipedia/id/thumb/0/00/Lambang_Universitas_Indonesia.svg/1200px-Lambang_Universitas_Indonesia.svg.png',
    description: 'Fokus pada Pengembangan Web dan Kecerdasan Buatan. IPK: 3.9/4.0'
  },
  {
    school: 'SMKN 1 Jakarta',
    major: 'Rekayasa Perangkat Lunak',
    year: '2017 — 2020',
    logo: '', // Jika kosong akan muncul inisial sekolah
    description: 'Mempelajari dasar-dasar pemrograman algoritma dan basis data.'
  }
]
</script>