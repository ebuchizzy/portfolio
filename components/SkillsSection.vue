<template>
    <section id="skills" class="py-16 sm:py-24 px-4 sm:px-6 md:px-12 lg:px-48 bg-dark text-white">
      <div class="w-full flex justify-center items-center flex-col mb-8 sm:mb-16">
        <h2 class="text-primary text-2xl sm:text-4xl font-bold relative pb-8 text-center" data-aos="fade-up">
          My Skills
          <span class="absolute w-24 sm:w-36 h-1 bg-primary bottom-4 left-1/2 transform -translate-x-1/2"></span>
          <span class="absolute w-3 h-3 bg-primary rounded-full bottom-3 left-1/2 transform -translate-x-1/2"></span>
        </h2>
      </div>
      
      <div class="flex flex-col lg:flex-row justify-between items-center">
        <div class="w-full lg:w-5/12 mb-8 sm:mb-10 lg:mb-0">
          <h2 class="text-xl sm:text-3xl font-bold mb-4 sm:mb-6 text-center lg:text-left" data-aos="fade-right" data-aos-delay="200">My Skills and Experiences</h2>
          <p class="mb-6 sm:mb-8 text-sm sm:text-base" data-aos="flip-down" data-aos-delay="300">
            I specialize in crafting visually appealing and highly functional digital experiences. As a web designer, I use Canva, Figma, Framer, and Spline to create sleek, user-friendly interfaces that enhance engagement and usability. My graphic design expertise, powered by Adobe Creative Suite, allows me to develop compelling visuals that strengthen brand identity and communication. Whether it's web design or branding, I ensure every project is both aesthetically striking and strategically effective.
          </p>

          <p class="mb-6 sm:mb-8 text-sm sm:text-base" data-aos="flip-down" data-aos-delay="300">
            On the development side, I build dynamic and scalable web applications using HTML, CSS, JavaScript, Python, SQL, and PHP, leveraging frameworks like Vue.js, Nuxt.js, and Tailwind CSS for modern front-end solutions. My backend expertise includes Node.js, Express.js, Django, MongoDB, and mySQL, enabling me to create seamless, high-performance applications. From concept to deployment, I provide full-stack solutions that merge creativity with functionality to bring ideas to life.
          </p>

          <div class="flex justify-center lg:justify-start">
            <NuxtLink to="#" 
              class="inline-block px-4 sm:px-6 py-2 sm:py-3 bg-primary text-white uppercase text-sm sm:text-base font-semibold tracking-wider rounded transition-colors duration-500 hover:bg-blue-600"
              data-aos="zoom-in-right" data-aos-delay="400">
              See More
            </NuxtLink>
          </div>
        </div>
        
        <div class="w-full lg:w-1/2">
          <div class="mb-4 sm:mb-6" v-for="(skill, index) in skills" :key="index">
            <div class="flex justify-between items-center mb-2 text-sm sm:text-base" data-aos="flip-up" :data-aos-delay="100 + (index * 100)">
              <span>{{ skill.name }}</span>
              <span>{{ skill.percentage }}%</span>
            </div>
            <div class="w-full h-3 sm:h-4 bg-gray-300 rounded-md relative" data-aos="zoom-in-right" :data-aos-delay="140 + (index * 100)">
              <div class="absolute top-0 left-0 h-full rounded-md" 
                   :style="{ width: skill.percentage + '%', backgroundColor: skill.color }"></div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </template>
  
  <script setup>
  const skills = [
    { name: 'HTML', percentage: 95, color: '#e45126' },
    { name: 'CSS', percentage: 90, color: '#0c73b8' },
    { name: 'Javascript', percentage: 80, color: '#e3a324' },
    { name: 'Python', percentage: 85, color: '#e45126' },
    { name: 'PHP', percentage: 65, color: '#0c73b8' },
    { name: 'SQL', percentage: 70, color: '#e3a324' }
  ];
  </script>