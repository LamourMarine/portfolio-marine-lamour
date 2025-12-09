<template>
  <section class="about">
    <div class="section-content">
      <h1 class="title">À propos de moi</h1>
      <div class="about-text">
        <p>Je m'appelle Marine, développeuse web passionnée par la création d'expériences utilisateurs performantes et esthétiques.</p>
        
        <p>Après une formation en développement web, je me spécialise aujourd'hui dans le front-end avec Vue.js et TypeScript, tout en ayant acquis des bases en développement backend. Je suis particulièrement intéressée par la conception d'API et la gestion de bases de données, et je continue à approfondir mes compétences dans ce domaine.</p>
        
        <p>Je suis constamment en apprentissage, motivée par la résolution de problèmes techniques et la création de solutions durables.</p>
        
        <p>N'hésitez pas à me contacter ou à découvrir mes projets dans la section dédiée.</p>
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
  { name: 'LinkedIn', icon: logoLinkedin, url: 'https://www.linkedin.com/in/marine-lamour-8a1747278/'},
  { name: 'GitHub', icon: logoGithub, url: 'https://github.com/LamourMarine'},
  { name: 'CV', icon: logoResume, url: '/CV.pdf' }
]
</script>

<style scoped>
section {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 40px 20px;
  margin-left: 120px;
}

.section-content {
  width: 100%;
  max-width: 800px;
}

.title {
  font-weight: 100; 
  font-size: 2.5rem;
  margin: 0 0 60px 0;
  font-family: 'Inter', sans-serif;
  text-decoration: underline; 
  color: white;
  text-align: center;
}

.about-text {
  line-height: 1.8;
  margin-bottom: 80px;
  text-align: left;
  color: white;
}

.about-text p {
  margin-bottom: 1.2em;
}

.about-text p:last-child {
  margin-bottom: 0;
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
  transition: transform 0.3s ease;
  cursor: pointer;
}

.card-link {
  text-decoration: none;
  color: white;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.card img {
  width: 60px;
  height: 60px;
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
  transition: opacity 0.3s ease, border-bottom-color 0.3s ease;
  border-bottom: 2px solid transparent;
}

/* Au hover */
.card:hover {
  transform: scale(1.1);
}

.card:hover .card-name {
  opacity: 1;
  border-bottom: 2px solid white;
}

/* Focus pour accessibilité */
.card-link:focus {
  outline: 2px solid #1B998B;
  outline-offset: 4px;
  border-radius: 8px;
}

/* ==================== RESPONSIVE ==================== */

/* Tablette */
@media (max-width: 1024px) {
  section {
    margin-left: 60px;
    padding: 30px 20px;
  }

  .title {
    font-size: 2rem;
    margin-bottom: 50px;
  }

  .about-text {
    margin-bottom: 60px;
  }

  .contact-links {
    gap: 30px;
  }
}

/* Mobile */
@media (max-width: 768px) {
  section {
    margin-left: 0;
    padding: 20px 15px;
  }

  .section-content {
    max-width: 100%;
  }

  .title {
    font-size: 1.8rem;
    margin-bottom: 40px;
  }

  .about-text {
    line-height: 1.7;
    margin-bottom: 50px;
    text-align: justify;
  }

  .about-text p {
    margin-bottom: 1em;
  }

  .contact-links {
    gap: 25px;
  }

  .card {
    width: 100px;
    padding: 15px 8px;
  }

  .card img {
    width: 50px;
    height: 50px;
  }

  .card-name {
    font-size: 0.9rem;
  }

  /* Afficher les noms directement sur mobile */
  .card-name {
    opacity: 1;
    border-bottom: 2px solid transparent;
  }

  .card:active .card-name {
    border-bottom: 2px solid white;
  }
}

/* Petits mobiles */
@media (max-width: 480px) {
  .title {
    font-size: 1.5rem;
    margin-bottom: 30px;
  }

  .about-text {
    font-size: 0.95rem;
    line-height: 1.6;
    margin-bottom: 40px;
  }

  .contact-links {
    gap: 20px;
  }

  .card {
    width: 85px;
  }

  .card img {
    width: 45px;
    height: 45px;
  }

  .card-name {
    font-size: 0.85rem;
    margin-top: 8px;
  }
}
</style>