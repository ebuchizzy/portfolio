<template>
    <section id="work" class="py-24 px-4 sm:px-6 md:px-12 lg:px-48 bg-dark">
      <div class="w-full flex justify-center items-center flex-col mb-8 sm:mb-16">
        <h2 class="text-primary text-2xl sm:text-4xl font-bold relative pb-8 text-center" data-aos="fade-up">
          My Works
          <span class="absolute w-24 sm:w-36 h-1 bg-primary bottom-4 left-1/2 transform -translate-x-1/2"></span>
          <span class="absolute w-3 h-3 bg-primary rounded-full bottom-3 left-1/2 transform -translate-x-1/2"></span>
        </h2>
      </div>
      
      <div class="flex flex-wrap justify-center">
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
  import image1 from '@/assets/Image/Desktop - 1.png'
  import image2 from '@/assets/Image/Desktop - 2.png'
  import image3 from '@/assets/Image/Desktop - 11.png'
  import image4 from '@/assets/Image/Desktop - 14.png'
  import image5 from '@/assets/Image/SupportUsPage.png'
  import image6 from '@/assets/Image/Desktop - 111.png'
  import image7 from "@/assets/Image/Desk - saint.png"


  const works = [
    { image: image1, animation: 'fade-right', delay: '200', link: 'https://www.behance.net/gallery/220607569/JSPARKS-branding' },
    { image: image2, animation: 'fade-up', delay: '200', link: 'https://www.behance.net/gallery/220607569/JSPARKS-branding' },
    { image: image3, animation: 'fade-left', delay: '200', link: 'https://www.behance.net/gallery/217027223/Lanraj-Product-Design' },
    { image: image4, animation: 'fade-right', delay: '400', link: 'https://www.behance.net/gallery/217018213/Car-Flyer-Design-with-Figma' },
    { image: image5, animation: 'fade-up', delay: '400', link: 'https://www.behance.net/gallery/221056145/SupportPage-Design-and-Dev' },
    { image: image6, animation: 'fade-left', delay: '400', link: 'https://www.behance.net/gallery/217018213/Car-Flyer-Design-with-Figma' },
    { image: image7, animation: 'fade-right', delay: '400', link: 'https://www.behance.net/gallery/222712327/Design-and-Deveopment-of-an-HR-website' }
  ];
  </script>