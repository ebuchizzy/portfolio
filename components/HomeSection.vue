<template>
  <section id="main" class="relative flex items-center justify-center w-full h-screen bg-dark px-4 sm:px-6 md:px-12 lg:px-48 overflow-hidden">
    
    <div class="relative z-10 text-center max-w-4xl">
      <h2 class="text-white text-2xl sm:text-3xl md:text-3xl lg:text-4xl font-medium" data-aos="fade-right" data-aos-delay="800">
        Hello, I'm <br>
        <span class="text-3xl sm:text-4xl md:text-5xl lg:text-6xl font-semibold">
          <span>{{ typedText }}</span>
          <span class="typing-cursor">|</span>
        </span>
      </h2>
      
      <div class="mt-8 relative h-24 sm:h-28 md:h-36 overflow-hidden mt-4" data-aos="fade-left" data-aos-delay="900">
        <transition-group name="slide-fade" class="animated-text">
          <h3 :key="currentText"
              class="text-3xl sm:text-4xl md:text-4xl lg:text-6xl font-bold text-primary absolute left-1/2 transform -translate-x-1/2">
            {{ currentText }}
          </h3>
        </transition-group>
      </div>
      
      <NuxtLink to="#work" 
         class="inline-block mt-8 sm:mt-10 px-6 sm:px-8 py-3 sm:py-4 bg-primary text-white uppercase text-base sm:text-lg font-semibold tracking-wider rounded transition-colors duration-500 hover:bg-blue-600" 
         data-aos="zoom-out" data-aos-delay="1000">
        See My Works
      </NuxtLink>
      
      <div class="mt-10 pl-6 sm:mt-14 flex justify-center" data-aos="fade-in" data-aos-delay="1200">
        <a v-for="(icon, index) in socialIcons" :key="index" 
           :href="icon.link" 
           class="text-white text-2xl sm:text-3xl mr-6 sm:mr-8 hover:text-primary transition-colors duration-300"
           :data-aos="'fade-in'"
           :data-aos-delay="1200 + (index * 100)">
          <i :class="icon.class"></i>
        </a>
      </div>
    </div>
  </section>
</template>
  
<script setup>
import { ref, onMounted, onUnmounted, computed } from 'vue';

const fullName = "Chukwuebuka Akpuofoba";
const typedText = ref('');
const typingComplete = ref(false);
let typingTimer = null;

const animatedTexts = [
  'Web Developer',
  'UI/UX Designer',
  'Graphic Designer',
];

const socialIcons = [
  { class: 'fab fa-behance', link: 'https://www.behance.net/ebukaakpuofoba'},
  { class: 'fab fa-linkedin', link: 'https://www.linkedin.com/in/chukwuebuka-akpuofoba-675b77369'},
  { class: 'fab fa-github', link: 'https://github.com/ebuchizzy?tab=repositories' }
];

const currentTextIndex = ref(0);
const currentText = computed(() => animatedTexts[currentTextIndex.value]);
let textRotationInterval = null;

const startTypingAnimation = () => {
  let currentIndex = 0;
  typingTimer = setInterval(() => {
    if (currentIndex < fullName.length) {
      typedText.value += fullName.charAt(currentIndex);
      currentIndex++;
    } else {
      clearInterval(typingTimer);
      typingComplete.value = true;
      
      // Start the role text rotation after name typing is complete
      startTextRotation();
    }
  }, 100); // Adjust speed of typing here (milliseconds)
};

const startTextRotation = () => {
  textRotationInterval = setInterval(() => {
    currentTextIndex.value = (currentTextIndex.value + 1) % animatedTexts.length;
  }, 3000);
};

onMounted(() => {
  // Start typing animation when component mounts
  startTypingAnimation();
});

onUnmounted(() => {
  // Clean up intervals when component unmounts
  if (typingTimer) clearInterval(typingTimer);
  if (textRotationInterval) clearInterval(textRotationInterval);
});
</script>
  
<style scoped>
.slide-fade-enter-active {
  transition: all 0.3s ease;
}
.slide-fade-leave-active {
  transition: all 0.3s ease;
}
.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateY(20px);
  opacity: 0;
}

.typing-cursor {
  animation: blink 0.7s infinite;
}

@keyframes blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0; }
}

@media (max-width: 1300px) {
  .three-d {
    scale: 0.7;
    top: 0%;
    right: -20%;
  }
}

@media (max-width: 768px) {
  .three-d {
    scale: 0.5;
    top:-50%;
    right: -20;
  }
}
</style>