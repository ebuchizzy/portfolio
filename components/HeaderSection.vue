<template>
  <header class="fixed top-0 left-0 z-50 w-full">
    <div
      :class="[
        'relative flex items-center justify-between overflow-hidden px-4 py-4 transition-all duration-300 sm:px-6 md:px-12 lg:px-48',
        isSticky || isMenuOpen ? 'bg-primary shadow-lg shadow-black/10' : 'bg-transparent'
      ]"
    >
      <div
        v-if="isSticky || isMenuOpen"
        class="pointer-events-none absolute inset-0 opacity-[0.08] [background-image:linear-gradient(rgba(255,255,255,0.34)_1px,transparent_1px),linear-gradient(90deg,rgba(255,255,255,0.34)_1px,transparent_1px)] [background-size:84px_84px]"
      ></div>

      <NuxtLink
        to="/"
        class="relative z-10 text-xl font-bold uppercase text-white sm:text-2xl"
        data-aos="zoom-in"
        @click.prevent="goHome"
      >
        CEA
      </NuxtLink>

      <div class="lg:hidden">
        <button
          type="button"
          @click.stop="toggleMenu"
          :aria-expanded="isMenuOpen"
          aria-label="Toggle navigation menu"
          class="relative z-[60] flex h-11 w-11 items-center justify-center rounded-full border border-white/20 bg-white/10 backdrop-blur-sm transition-colors duration-300 focus:outline-none"
        >
          <span
            :class="[
              'absolute h-0.5 w-5 transform rounded-full bg-white transition-all duration-300 ease-in-out',
              isMenuOpen ? 'translate-y-0 rotate-45' : '-translate-y-1.5'
            ]"
          ></span>
          <span
            :class="[
              'absolute h-0.5 w-5 transform rounded-full bg-white transition-all duration-300 ease-in-out',
              isMenuOpen ? 'translate-y-0 -rotate-45' : 'translate-y-1.5'
            ]"
          ></span>
        </button>
      </div>

      <nav class="hidden lg:flex lg:items-center">
        <a
          v-for="(link, index) in navLinks"
          :key="index"
          :href="link.to"
          @click="handleLinkClick(link.to)"
          :class="[
            'relative z-10 mx-2 text-sm font-medium text-white transition-colors duration-300 sm:mx-3 sm:text-base',
            isSticky ? 'hover:text-black' : 'hover:text-primary'
          ]"
        >
          {{ link.text }}
        </a>
      </nav>
    </div>

    <Transition
      enter-active-class="transition duration-300 ease-out"
      enter-from-class="-translate-y-6 opacity-0"
      enter-to-class="translate-y-0 opacity-100"
      leave-active-class="transition duration-200 ease-in"
      leave-from-class="translate-y-0 opacity-100"
      leave-to-class="-translate-y-4 opacity-0"
    >
      <div v-if="isMenuOpen" class="lg:hidden">
        <button
          aria-label="Close navigation menu"
          class="fixed inset-0 top-[72px] z-30 bg-black/40 backdrop-blur-[2px]"
          @click="closeMenu"
        ></button>

        <nav
          class="absolute top-full left-0 right-0 z-40 mx-4 mt-2 overflow-hidden rounded-[28px] border border-white/15 bg-white/95 p-4 shadow-2xl shadow-black/25 backdrop-blur xl:hidden"
        >
          <a
            v-for="(link, index) in navLinks"
            :key="`mobile-${index}`"
            :href="link.to"
            @click="handleLinkClick(link.to)"
            :class="[
              'mb-2 flex items-center justify-between rounded-2xl px-4 py-3 text-base font-medium transition-all duration-300 last:mb-0',
              activeLink === link.to
                ? 'bg-primary text-white shadow-lg shadow-primary/30'
                : 'bg-black/[0.03] text-black hover:bg-primary hover:text-white'
            ]"
          >
            <span>{{ link.text }}</span>
            <span class="text-lg leading-none">&rarr;</span>
          </a>
        </nav>
      </div>
    </Transition>
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

const closeMenu = () => {
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
  document.body.classList.remove('overflow-hidden');
});

const goHome = () => {
  closeMenu();
  
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
  closeMenu();
};
</script>
