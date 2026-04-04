<template>
  <header :class="[
    'fixed top-0 left-0 w-full z-50 flex justify-between items-center transition-all duration-200 py-4 px-4 sm:px-6 md:px-12 lg:px-48',
    isSticky ? 'bg-primary' : 'bg-dark'
  ]">
    <NuxtLink 
  to="/" 
  class="text-white text-xl sm:text-2xl font-bold uppercase" 
  data-aos="zoom-in"
  @click.prevent="goHome"
>CEA</NuxtLink>
   
    <div class="lg:hidden">
      <button @click="toggleMenu" class="w-8 h-8 relative focus:outline-none z-[60]">
  <span :class="[
    'block absolute h-0.5 w-6 transform transition-all duration-300 ease-in-out origin-center left-1',
    isMenuOpen ? 'rotate-45 top-[15px] bg-black' : 'top-[10px] bg-white'
  ]"></span>
  <span :class="[
    'block absolute h-0.5 w-6 transform transition-all duration-300 ease-in-out origin-center left-1',
    isMenuOpen ? '-rotate-45 top-[15px] bg-black' : 'top-[21px] bg-white'
  ]"></span>
</button>
    </div>
   
    
    <nav :class="[
       'transition-all duration-300',
  isMenuOpen 
    ? 'fixed top-0 right-0 w-64 h-screen bg-white flex flex-col justify-center items-center shadow-lg z-50 overflow-y-auto' 
    : 'hidden lg:flex lg:items-center lg:relative'
    ]">
   
      
      <a v-for="(link, index) in navLinks" :key="index"
   :href="link.to"
   @click="handleLinkClick(link.to)"
   :class="[
     'font-medium mx-2 sm:mx-3 text-sm sm:text-base transition-colors duration-300',
     isMenuOpen 
       ? `my-2 sm:my-3 py-1.5 sm:py-2 px-4 sm:px-6 ${activeLink.value === link.to ? 'bg-primary text-white' : 'text-black hover:bg-primary hover:text-white'}`
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

const goHome = () => {
  isMenuOpen.value = false;
  document.body.classList.remove('overflow-hidden');
  
  const el = document.getElementById('main');
  if (el) {
    el.scrollIntoView({ behavior: 'smooth' });
  } else {
    window.scrollTo({ top: 0, behavior: 'smooth' });
  }
};

const activeLink = ref('#main');

const handleLinkClick = (linkTo) => {
  activeLink.value = linkTo;
  setTimeout(() => {
    isMenuOpen.value = false;
    document.body.classList.remove('overflow-hidden');
  }, 300);
};
</script>