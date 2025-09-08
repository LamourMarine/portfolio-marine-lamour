<template>
  <section class="project-container">
    <h1 class="title">Projets</h1>
    <div class="projects-grid">
      <div v-for="project in projects" :key="project.name" class="project-wrapper">
        <!-- Card cliquable uniquement -->
        <a :href="project.link" target="_blank" class="project-card">
          <img :src="project.image" :alt="project.name" class="card-image" />
        </a>

        <!-- Titre et description sous la card -->
        <div class="project-info">
          <h2 class="project-title">{{ project.name }}</h2>
          <ul v-if="Array.isArray(project.description)" class="project-desc">
            <li v-for="(item, index) in project.description" :key="index">{{ item }}</li>
          </ul>
          <p v-else class="project-desc">{{ project.description }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script lang="ts" setup>
import mockupPokedex from '@/assets/MockupPokedex.jpg'

const projects = [
  {
    name: 'Pokédex App',
    description: [
      'Consommer une API externe',
      'Travailler l’intégration HTML / CSS',
      'Gérer de la logique en JS'
    ],
    image: mockupPokedex,
    link: 'https://lamourmarine.github.io/test-technique/'
  },
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
  align-items: stretch;
}

.project-card {
  display: block;
  /*flex-direction: column;
  background: white;*/
  border-radius: 12px;
  /*padding: 1rem;*/
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  color: inherit;
  overflow: hidden;
}

.project-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 20px rgba(0,0,0,0.15);
}

.card-image {
  width: 100%;
  height: 200px;
  object-fit: cover;
  border-radius: 8px;
  /*margin-bottom: 1rem;*/
}

.project-info {
  text-align: center; 
  margin-top: 0.5rem; 
}

.project-title {
  font-size: 1.2rem; 
  font-weight: bold;
  margin-bottom: 0.25rem;
}

.project-desc {
  font-size: 0.95rem;
  color: #c7c7c7;
  line-height: 1.4;
  margin: 0;
  padding: 0;
  list-style: disc inside;
}

</style>
