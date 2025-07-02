<template>
    <div class="stack-container">
        <h1 class="title">Stack Technique</h1>
        <div class="tech-icons">
            <div class="tech" v-for="tech in technologies" :key="tech.name">
                <img :src="tech.icon" alt="tech.name" />
            </div>
        </div>
    </div>
</template>

<script lang="ts" setup>
const technologies = [
    { name: 'Vue.js', icon: 'src/assets/Vue.js_Logo_2.svg.png' },
    { name: 'TypeScript', icon: 'src/assets/typescript.svg' },
    { name: 'CSS', icon: 'src/assets/css3.png' },
    { name: 'Tailwind', icon: 'src/assets/tailwind-css-logo-png_seeklogo-354675-removebg-preview.png' }, 
    { name: 'PHP', icon: 'src/assets/kisspng-web-development-php-software-developer-web-applica-create-5ad11121794b05.5974879215236508494968-removebg-preview.png' }, 
    { name: 'Symfony', icon: 'src/assets/symfony-badge-icon-lg.png' },
    { name: 'MySQL', icon: 'src/assets/images-removebg-preview.png' },
    { name: 'PostgreSQL', icon: 'src/assets/PostgreSQL-Logo.wine.png' }
]

</script>

<style scoped>

.stack-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-left: 120px;
  color: white;
}

.title {
  display: flex;
    flex-direction: column;
    justify-content: center;
  font-weight: 100; 
  font-size: 2.5rem;
  padding: 20px 40px 0 40px;
  margin: 0;
  font-family: 'Inter', sans-serif;
  text-decoration: underline;
}

.tech-icons {
  display: flex;
  flex-wrap: wrap;
  gap: 40px;
  justify-content: center;
  margin-top: 5rem;
}

.tech {
  background-color: #1a1a1a; 
  opacity: 0.8;
  border-radius: 8px;
  padding: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 150px;
  height: 150px;
  transition: opacity 0.3s ease;
}

.tech:hover {
  opacity: 1;
}

.tech img {
  max-width: 190px;
  max-height: 125px;
}
</style>