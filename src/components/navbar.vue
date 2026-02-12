<template>
  <div class="fixed bottom-6 right-6 z-[999] flex flex-col md:flex-row items-center md:items-end justify-end gap-3 font-sans">
    
    <div 
      class="flex bg-black p-2 rounded-full gap-3 relative transition-all duration-500 shadow-2xl border border-white/10"
      :class="[
        isOpen ? 'opacity-100 scale-100 translate-y-0' : 'opacity-0 pointer-events-none scale-90 translate-y-10 md:translate-y-0 md:translate-x-10',
        'flex-col md:flex-row' 
      ]"
    >
      <div
        class="absolute w-12 h-12 rounded-full bg-[#373737] transition-all duration-500 ease-[cubic-bezier(0.68,-0.55,0.27,1.55)] z-0"
        :style="selectorStyle"
      ></div>

      <div
        :ref="el => { if (el) itemRefs['home'] = el }"
        class="w-12 h-12 flex justify-center items-center rounded-full z-10 cursor-pointer transition-all duration-500 hover:scale-110"
        @mouseenter="selected = 'home'"
        @click="handleHomeClick"
      >
        <box-icon name="home-alt" 
          :class="selected === 'home' ? 'fill-white' : 'fill-[#75747A]'"
          class="transition-colors duration-300 w-6 h-6">
        </box-icon>
      </div>

      <div class="flex items-center justify-center pointer-events-none z-10 px-1">
        <div class="bg-white/20 transition-all duration-500"
             :class="isMobile ? 'h-[1px] w-8' : 'h-6 w-[1px]'">
        </div>
      </div>

      <a v-for="platform in platforms" :key="platform.id"
        :href="platform.url"
        target="_blank"
        rel="noopener noreferrer"
        :ref="el => { if (el) itemRefs[platform.id] = el }"
        class="w-12 h-12 flex justify-center items-center rounded-full z-10 cursor-pointer transition-all duration-500 hover:scale-110"
        @mouseenter="selected = platform.id"
      >
        <box-icon :name="platform.icon" type="logo" 
          :class="selected === platform.id ? 'fill-white' : 'fill-[#75747A]'"
          class="transition-colors duration-300 w-6 h-6">
        </box-icon>
      </a>
    </div>

    <button 
      @click="isOpen = !isOpen"
      class="w-14 h-14 bg-black rounded-full flex items-center justify-center shadow-lg border border-white/10 text-white transition-all active:scale-90 z-[1000]"
    >
      <transition name="fade" mode="out-in">
        <box-icon v-if="!isOpen" name="menu" color="white" key="menu"></box-icon>
        <div v-else key="arrow" class="flex items-center justify-center">
          <box-icon :name="isMobile ? 'chevron-down' : 'chevron-right'" color="white"></box-icon>
        </div>
      </transition>
    </button>
  </div>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue';

const isOpen = ref(false);
const selected = ref('home');
const itemRefs = ref({});
const isMobile = ref(false);

// Platform List - Facebook is Back!
const platforms = [
  { id: 'facebook', icon: 'facebook-circle', url: 'https://facebook.com/username' },
  { id: 'instagram', icon: 'instagram-alt', url: 'https://instagram.com/username' },
  { id: 'github', icon: 'github', url: 'https://github.com/username' },
  { id: 'twitter', icon: 'twitter', url: 'https://twitter.com/username' }
];

const checkMobile = () => {
  isMobile.value = window.innerWidth < 768;
};

const handleHomeClick = () => {
  window.scrollTo({ top: 0, behavior: 'smooth' });
  setTimeout(() => { isOpen.value = false; }, 300);
};

onMounted(() => {
  checkMobile();
  window.addEventListener('resize', checkMobile);
});

onUnmounted(() => {
  window.removeEventListener('resize', checkMobile);
});

const selectorStyle = computed(() => {
  const activeEl = itemRefs.value[selected.value];
  if (!activeEl) return {};

  return {
    transform: isMobile.value 
      ? `translateY(${activeEl.offsetTop - 8}px)` 
      : `translateX(${activeEl.offsetLeft - 8}px)`,
    opacity: isOpen.value ? 1 : 0
  };
});
</script>

<style scoped>
.fade-enter-active, .fade-leave-active { transition: all 0.3s ease; }
.fade-enter-from, .fade-leave-to { opacity: 0; transform: scale(0.5); }
</style>