<template>
    <section
      id="work"
      class="relative isolate overflow-hidden bg-[#000716] px-4 py-24 sm:px-6 md:px-12 lg:px-48"
    >
      <div class="pointer-events-none absolute inset-0 bg-[radial-gradient(circle_at_top_left,rgba(255,255,255,0.08),transparent_22%),radial-gradient(circle_at_bottom_right,rgba(58,108,244,0.1),transparent_30%),linear-gradient(145deg,#000512_10%,#020a18_52%,#050d1a_100%)]"></div>
      <div class="pointer-events-none absolute inset-0 opacity-[0.04] [background-image:linear-gradient(rgba(255,255,255,0.26)_1px,transparent_1px),linear-gradient(90deg,rgba(255,255,255,0.26)_1px,transparent_1px)] [background-size:80px_80px]"></div>

      <div class="relative z-10 mb-8 flex w-full flex-col items-center justify-center sm:mb-16">
        <h2 class="text-primary text-2xl sm:text-4xl font-bold relative pb-8 text-center" data-aos="fade-up">
          My Works
          <span class="absolute w-24 sm:w-36 h-1 bg-primary bottom-4 left-1/2 transform -translate-x-1/2"></span>
          <span class="absolute w-3 h-3 bg-primary rounded-full bottom-3 left-1/2 transform -translate-x-1/2"></span>
        </h2>
      </div>
      
      <div class="relative z-10 flex flex-wrap justify-center">
        <div v-for="(work, index) in works" :key="index"
             class="w-full min-[280px]:w-64 sm:w-80 mx-2 sm:mx-4 mb-4 sm:mb-6 overflow-hidden rounded-lg"
             :data-aos="work.animation" :data-aos-delay="work.delay">
          <div class="relative w-full h-48 sm:h-64 overflow-hidden">
            <a :href="work.link" target="_blank">
              <img :src="work.image" :alt="'Project ' + (index + 1)" 
                   class="absolute top-0 left-0 w-full h-full object-cover transition-transform duration-300 hover:scale-110">
            </a>
          </div>
        </div>
      </div>
    </section>
  </template>
  
  <script setup>
  import image5 from '@/assets/Image/img.png'
  import image7 from "@/assets/Image/Desk - saint.png"
  import image1 from '@/assets/Image/Desktop - 1.png'
  import image2 from '@/assets/Image/Desktop - 2.png'
  import image3 from '@/assets/Image/Desktop - 11.png'
  import image4 from '@/assets/Image/Frame 4.png'
  import image6 from '@/assets/Image/Desktop - 111.png'
  import image8 from "@/assets/Image/MacBook Air - 1.png"
  import image9 from "@/assets/Image/Flux.png"
  import image10 from "@/assets/Image/Nex.png"
  import image11 from "@/assets/Image/Vert.png"
  import image12 from "@/assets/Image/Cryenix.png"


  const works = [
    { image: image5, animation: 'fade-up', delay: '400', link: 'https://www.fortrez.io/' },
    { image: image7, animation: 'fade-right', delay: '400', link: 'https://hrsolutions.framer.website/' },
    { image: image1, animation: 'fade-right', delay: '200', link: 'https://www.behance.net/gallery/220607569/JSPARKS-branding' },
    { image: image2, animation: 'fade-up', delay: '200', link: 'https://www.behance.net/gallery/220607569/JSPARKS-branding' },
    { image: image3, animation: 'fade-left', delay: '200', link: 'https://www.behance.net/gallery/217027223/Lanraj-Product-Design' },
    { image: image4, animation: 'fade-right', delay: '400', link: 'https://www.behance.net/gallery/236087981/Petrofa' },
    { image: image6, animation: 'fade-left', delay: '400', link: 'https://www.behance.net/gallery/230989255/Metro-Electric-Flyer-1' },
    { image: image8, animation: 'fade-up', delay: '200', link: 'https://www.behance.net/gallery/228935409/Jumaphad-2' },
    { image: image9, animation: 'fade-up', delay: '400', link: 'https://www.behance.net/gallery/235036049/FluxenX-Landing-page' },
    { image: image10, animation: 'fade-left', delay: '400', link: 'https://www.behance.net/gallery/234986329/Nexora-ai-3d-design' },
    { image: image11, animation: 'fade-right', delay: '400', link: 'https://www.behance.net/gallery/234988367/Virtara-3d-design' },
    { image: image12, animation: 'fade-up', delay: '200', link: 'https://www.behance.net/gallery/235035961/Cryenix-Landing-page' }
  ];
  </script>
