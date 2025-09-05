<template>
  <section class="project-container">
    <h1 class="title">Projets</h1>
    <div class="projects-grid">
            <a 
        v-for="project in projects" 
        :key="project.name" 
        :href="project.link" 
        target="_blank" 
        class="project-card"
      >
        <div class="card-content">
          <img :src="project.image" :alt="project.name" class="card-image" />
          <h2 class="card-title">{{ project.name }}</h2>
          <p class="card-desc">{{ project.description }}</p>
        </div>
      </a>
    </div>
  </section>
</template>

<script lang="ts" setup>

const projects = [
  {name: 'Projet 1', description: '', image: '', link: ''},
  {name: 'Projet 2', description: '', image: '', link: ''},
  {name: 'Projet 3', description: '', image: '', link: ''},
  {name: 'Projet 4', description: '', image: '', link: ''},
  {name: 'Projet 5', description: '', image: '', link: ''},
  {name: 'Projet 6', description: '', image: '', link: ''}
]
</script>

<style scooped>

.project-container {
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

.projects-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.5rem;
  margin-top: 2rem;
}

.project-card {
  display: block;
  background: white;
  border-radius: 12px;
  padding: 1rem;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  text-decoration: none;
  color: inherit;
}

.project-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 20px rgba(0,0,0,0.15);
}
</style>
