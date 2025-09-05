<template>
  <section class="about">
    <div class="section-content">
      <h1 class="title">À propos de moi</h1>
        <div class="about-text">
        Je m'appelle Marine, développeuse web passionnée par la création d'expériences utilisateurs performantes et esthétiques.
      Après une formation en développement web, je me spécialise aujourd'hui dans le front-end avec Vue.js et TypeScript, tout en ayant acquis des bases en développement backend.
      Je suis particulièrement intéressée par la conception d'API et la gestion de bases de données, et je continue à approfondir mes compétences dans ce domaine.
      Je suis constamment en apprentissage, motivée par la résolution de problèmes techniques et la création de solutions durables.
      N'hésitez pas à me contacter ou à découvrir mes projets dans la section dédiée.
        </div>
          <div class="contact-links">
            <div class="card" v-for="link in links" :key="link.name">
              <a :href="link.url" target="_blank" rel="noopener noreferrer" class="card-link">
                <img :src="link.icon" :alt="link.name" />
                <p class="card-name">{{ link.name }}</p>
              </a>
            </div>
  </div>
    </div>
  </section>
</template>

<script lang="ts" setup>
import logoLinkedin from '../assets/logoLinkedin.png'
import logoGithub from '../assets/logoGithub.png'
import logoResume from '../assets/logoResume.png'

const links = [
  { name: 'Linkedin', icon: logoLinkedin, url: 'https://www.linkedin.com/in/marine-lamour-8a1747278/'},
  { name: 'Github', icon: logoGithub, url: 'https://github.com/LamourMarine'},
  { name: 'Resume', icon: logoResume, url: '/CV.pdf' }
]

</script>

<style scoped>

section {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-left: 0;
  padding-left: 120px;
}

.section-content {
  width: 100%;
  max-width: 800px;
  text-align: center;
}

.title {
  display: flex;
  flex-direction: column;
  justify-content: center;
  font-weight: 100; 
  font-size: 2.5rem;
  padding: 20px 40px 0 40px;
  margin-top: 10px;
  margin-left: 215px;
  margin-bottom: 125px;
  font-family: 'Inter', sans-serif;
  text-decoration: underline; 
  color: white;
}

.about-text {
  line-height: 2;
  width: 69%;
  margin-left: auto;
  margin-bottom: 150px;
}

.contact-links {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 30px;
  width: 130%;
}

img {
  width: 50px;
  height: 50px;
}

.links {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  justify-content: center;
}

.contact-links {
  display: flex;
  gap: 40px;
  justify-content: center;
  flex-wrap: wrap;
}

.card {
  width: 120px;
  padding: 20px 10px;
  text-align: center;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  cursor: pointer;
  position: relative;
}

.card-link {
  text-decoration: none;
  color: white;
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
}

.card img {
  max-width: 80%;
  max-height: 80%;
  display: block;
  margin: 0 auto;
  transition: transform 0.3s ease;
  border-radius: 6px;
}

.card-name {
  opacity: 0;
  margin-top: 10px;
  font-weight: 600;
  font-size: 1rem;
  text-decoration: none;
  transition: opacity 0.3s ease, border-bottom-color 0.3s ease;
  border-bottom: 2px solid transparent;
}

/* Au hover */
.card:hover {
  transform: scale(1.1);
}

.card:hover .card-name {
  opacity: 1;
  border-bottom: 2px solid white; /* soulignement */
}

</style>