<template>
  <header :class="[
    'fixed top-0 left-0 w-full z-50 flex justify-between items-center transition-all duration-200 py-4 px-4 sm:px-6 md:px-12 lg:px-48',
    isSticky ? 'bg-primary' : 'bg-dark'
  ]">
    <NuxtLink to="/" class="text-white text-xl sm:text-2xl font-bold uppercase" data-aos="zoom-in">CEA</NuxtLink>
   
    <div class="lg:hidden">
      <button @click="toggleMenu" class="w-8 sm:w-10 h-8 sm:h-10 relative focus:outline-none">
        <span :class="[
          'block absolute h-0.5 w-5 sm:w-6 bg-white transform transition duration-300 ease-in-out',
          isMenuOpen ? 'rotate-45 translate-y-0' : '-translate-y-1.5'
        ]"></span>
        <span :class="[
          'block absolute h-0.5 w-5 sm:w-6 bg-white transform transition duration-300 ease-in-out',
          isMenuOpen ? 'opacity-0' : 'opacity-100'
        ]"></span>
        <span :class="[
          'block absolute h-0.5 w-5 sm:w-6 bg-white transform transition duration-300 ease-in-out',
          isMenuOpen ? '-rotate-45 translate-y-0' : 'translate-y-1.5'
        ]"></span>
      </button>
    </div>
   
    
    <nav :class="[
       'transition-all duration-300',
  isMenuOpen 
    ? 'fixed top-0 right-0 w-64 h-screen bg-white flex flex-col justify-center items-center shadow-lg z-50 overflow-y-auto' 
    : 'hidden lg:flex lg:items-center lg:relative'
    ]">
      <button v-if="isMenuOpen"
              @click="toggleMenu"
              class="absolute top-4 right-4 text-black hover:text-primary">
        <i class="fas fa-times text-xl sm:text-2xl"></i>
      </button>
      
      <a v-for="(link, index) in navLinks" :key="index"
         :href="link.to"
         @click="handleLinkClick"
         :class="[
           'font-medium mx-2 sm:mx-3 text-sm sm:text-base transition-colors duration-300',
           isMenuOpen ? 'text-black my-2 sm:my-3 py-1.5 sm:py-2 px-4 sm:px-6 hover:bg-primary hover:text-white'
           : `text-white ${isSticky ? 'hover:text-black' : 'hover:text-primary'}`,
         ]">
        {{ link.text }}
      </a>
    </nav>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const isSticky = ref(false);
const isMenuOpen = ref(false);

const navLinks = [
  { text: 'Home', to: '#main' },
  { text: 'About', to: '#about' },
  { text: 'Skills', to: '#skills' },
  { text: 'Services', to: '#services' },
  { text: 'Work', to: '#work' },
  { text: 'Contact', to: '#contact' }
];

const handleLinkClick = () => {
  isMenuOpen.value = false;
  document.body.classList.remove('overflow-hidden');
};

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
  if (isMenuOpen.value) {
    document.body.classList.add('overflow-hidden');
  } else {
    document.body.classList.remove('overflow-hidden');
  }
};

const handleScroll = () => {
  isSticky.value = window.scrollY > 0;
};

onMounted(() => {
  window.addEventListener('scroll', handleScroll);
});

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll);
});
</script>