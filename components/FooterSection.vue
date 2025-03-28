<template>
    <footer class="py-8 bg-dark text-white text-center">
      <h3 class="text-xl font-semibold mb-2">Chukwuebuka Akpuofoba</h3>
      <p>Copyright @{{ currentYear }} <a href="#" class="text-primary font-semibold">CEA</a>. All Rights Reserved.</p>
    </footer>
  </template>
  
  <script setup>
  const currentYear = new Date().getFullYear();
  </script>