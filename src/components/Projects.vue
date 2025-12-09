<template>
  <section class="project-container">
    <h1 class="title">Projets</h1>

    <!-- Projet phare : Cantine Verte -->
    <div class="featured-project">
      <div class="featured-wrapper">
        <a :href="featuredProject.link" target="_blank" rel="noopener noreferrer" class="featured-card">
          <img :src="featuredProject.image" :alt="featuredProject.name" class="featured-image" />
        </a>

        <div class="featured-info">
          <div class="featured-header">
            <h2 class="featured-title">{{ featuredProject.name }}</h2>
          </div>

          <div class="tech-badges">
            <span class="badge" v-for="tech in featuredProject.technologies" :key="tech">
              {{ tech }}
            </span>
          </div>

          <ul class="featured-desc">
            <li v-for="(item, index) in featuredProject.description" :key="index">
              {{ item }}
            </li>
          </ul>

<div class="project-links">
  <a :href="featuredProject.githubFront" target="_blank" rel="noopener noreferrer" class="link-button">
    <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
      <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
    </svg>
    Code Frontend
  </a>
  <a :href="featuredProject.githubBack" target="_blank" rel="noopener noreferrer" class="link-button">
    <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
      <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
    </svg>
    Code Backend
  </a>
  <a :href="featuredProject.link" target="_blank" rel="noopener noreferrer" class="link-button primary">
    <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
      <path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"></path>
      <polyline points="15 3 21 3 21 9"></polyline>
      <line x1="10" y1="14" x2="21" y2="3"></line>
    </svg>
    Voir le site
  </a>
</div>        </div>
      </div>
    </div>

    <!-- Autres projets -->
    <h3 class="section-subtitle">Autres projets</h3>
    <div class="projects-grid">
      <div
        v-for="project in otherProjects"
        :key="project.name"
        class="project-wrapper"
      >
        <a :href="project.link" target="_blank" rel="noopener noreferrer" class="project-card">
          <img :src="project.image" :alt="project.name" class="card-image" />
        </a>

        <div class="project-info">
          <h2 class="project-title">{{ project.name }}</h2>

          <div class="tech-badges">
            <span class="badge" v-for="tech in project.technologies" :key="tech">
              {{ tech }}
            </span>
          </div>

          <ul class="project-desc">
            <li v-for="(item, index) in project.description" :key="index">
              {{ item }}
            </li>
          </ul>

          <div class="project-links">
            <a v-if="project.github" :href="project.github" target="_blank" rel="noopener noreferrer" class="link-icon" title="Voir le code">
              <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
              </svg>
            </a>
            <a :href="project.link" target="_blank" rel="noopener noreferrer" class="link-icon" title="Voir le site">
              <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"></path>
                <polyline points="15 3 21 3 21 9"></polyline>
                <line x1="10" y1="14" x2="21" y2="3"></line>
              </svg>
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script lang="ts" setup>
import mockupPokedex from "@/assets/MockupPokedex.jpg";
import duSolAuPlafond from "@/assets/Du_sol_au_plafond.png";
import cantineVerte from "@/assets/Cantine_Verte.png";

const featuredProject = {
  name: "Cantine Verte",
  description: [
    "Plateforme connectant cantines et producteurs locaux en Hauts-de-France",
    "Architecture full-stack avec authentification par rôles (producteurs, structures, admin)",
    "Système complet de gestion : validation des producteurs, catalogue produits, panier et commandes",
    "Upload d'images avec gestion des URLs en production",
    "Déploiement : Frontend (Netlify), Backend (Render), Database (Supabase)"
  ],
  technologies: ["React", "TypeScript", "Symfony", "PostgreSQL", "Docker"],
  image: cantineVerte,
  link: "https://cantineverte.netlify.app",
  githubFront: "https://github.com/LamourMarine/app-mla-frontend",
  githubBack: "https://github.com/LamourMarine/app-mla-backend"
};

const otherProjects = [
  {
    name: "Du Sol Au Plafond",
    description: [
      "Site vitrine moderne et responsive",
      "Formulaire de contact avec EmailJS",
      "Déploiement sur Netlify"
    ],
    technologies: ["React", "Tailwind CSS", "Vite"],
    image: duSolAuPlafond,
    link: "https://du-sol-au-plafond.netlify.app/",
    github: "https://github.com/LamourMarine/du-sol-au-plafond"
  },

  {
    name: "Pokédex App",
    description: [
      "Consommation d'API externe PokéAPI",
      "Intégration HTML / CSS responsive",
      "Logique JavaScript vanilla"
    ],
    technologies: ["JavaScript", "HTML", "CSS"],
    image: mockupPokedex,
    link: "https://lamourmarine.github.io/test-technique/",
    github: "https://github.com/LamourMarine/test-technique"
  }
];
</script>

<style scoped>
.project-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-left: 120px;
  padding: 40px 20px;
  color: white;
}

.title {
  font-weight: 100;
  font-size: 2.5rem;
  margin: 0 0 60px 0;
  font-family: "Inter", sans-serif;
  text-decoration: underline;
  text-align: center;
}

/* ============ FEATURED PROJECT ============ */
.featured-project {
  width: 100%;
  max-width: 1000px;
  margin-bottom: 80px;
}

.featured-wrapper {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 3rem;
  align-items: start;
  background: rgba(26, 26, 26, 0.5);
  border-radius: 16px;
  padding: 2rem;
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.featured-card {
  display: block;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.4);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.featured-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 32px rgba(0, 0, 0, 0.5);
}

.featured-image {
  width: 100%;
  height: 320px;
  object-fit: cover;
  display: block;
}

.featured-info {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.featured-header {
  display: flex;
  align-items: center;
  gap: 1rem;
  flex-wrap: wrap;
}

.featured-title {
  font-size: 1.8rem;
  font-weight: 600;
  margin: 0;
  color: white;
}

.featured-badge {
  background: linear-gradient(135deg, #1B998B, #17a085);
  color: white;
  padding: 0.4rem 1rem;
  border-radius: 20px;
  font-size: 0.85rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.featured-desc {
  font-size: 1rem;
  color: #d4d4d4;
  line-height: 1.7;
  margin: 0;
  padding: 0 0 0 1.5rem;
  list-style: disc;
}

.featured-desc li {
  margin-bottom: 0.6rem;
}

.featured-desc li:last-child {
  margin-bottom: 0;
}

/* ============ TECH BADGES ============ */
.tech-badges {
  display: flex;
  gap: 0.5rem;
  flex-wrap: wrap;
}

.badge {
  background: #1B998B;
  color: white;
  padding: 0.35rem 0.9rem;
  border-radius: 16px;
  font-size: 0.8rem;
  font-weight: 500;
}

/* ============ PROJECT LINKS ============ */
.project-links {
  display: flex;
  gap: 1rem;
  margin-top: 0.5rem;
}

.link-button {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.7rem 1.2rem;
  border-radius: 8px;
  font-size: 0.95rem;
  font-weight: 500;
  text-decoration: none;
  transition: all 0.3s ease;
  border: 1px solid rgba(255, 255, 255, 0.2);
  color: white;
}

.link-button:hover {
  transform: translateY(-2px);
  border-color: rgba(255, 255, 255, 0.4);
}

.link-button.primary {
  background: #1B998B;
  border-color: #1B998B;
}

.link-button.primary:hover {
  background: #17a085;
  border-color: #17a085;
}

.link-icon {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 36px;
  height: 36px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.1);
  color: white;
  transition: all 0.3s ease;
  text-decoration: none;
}

.link-icon:hover {
  background: #1B998B;
  transform: scale(1.1);
}

/* ============ OTHER PROJECTS ============ */
.section-subtitle {
  font-size: 1.8rem;
  font-weight: 300;
  margin: 0 0 40px 0;
  color: white;
  text-align: center;
  width: 100%;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 2.5rem;
  max-width: 1000px;
  width: 100%;
}

.project-wrapper {
  display: flex;
  flex-direction: column;
}

.project-card {
  display: block;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  overflow: hidden;
  text-decoration: none;
}

.project-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 24px rgba(0, 0, 0, 0.4);
}

.project-card:focus {
  outline: 2px solid #1B998B;
  outline-offset: 4px;
}

.card-image {
  width: 100%;
  height: 220px;
  object-fit: cover;
  display: block;
}

.project-info {
  margin-top: 1rem;
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.project-title {
  font-size: 1.3rem;
  font-weight: 600;
  margin: 0;
  color: white;
}

.project-desc {
  font-size: 0.95rem;
  color: #c7c7c7;
  line-height: 1.6;
  margin: 0;
  padding: 0 0 0 1.2rem;
  list-style: disc;
}

.project-desc li {
  margin-bottom: 0.4rem;
}

.project-desc li:last-child {
  margin-bottom: 0;
}

/* ==================== RESPONSIVE ==================== */

/* Tablette large */
@media (max-width: 1200px) {
  .project-container {
    margin-left: 60px;
  }

  .featured-wrapper {
    gap: 2rem;
    padding: 1.5rem;
  }

  .featured-image {
    height: 280px;
  }
}

/* Tablette */
@media (max-width: 1024px) {
  .featured-wrapper {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .featured-image {
    height: 320px;
  }

  .projects-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 2rem;
  }

  .card-image {
    height: 200px;
  }
}

/* Mobile */
@media (max-width: 768px) {
  .project-container {
    margin: 0;
    padding: 20px 15px;
    width: 100%;
    max-width: 100vw;
    box-sizing: border-box;
  }

  .title {
    font-size: 1.8rem;
    margin-bottom: 40px;
  }

  .featured-project {
    margin-bottom: 60px;
  }

  .featured-wrapper {
    padding: 1.5rem;
    gap: 1.5rem;
  }

  .featured-image {
    height: 240px;
  }

  .featured-title {
    font-size: 1.5rem;
  }

  .featured-badge {
    font-size: 0.75rem;
    padding: 0.3rem 0.8rem;
  }

  .featured-desc {
    font-size: 0.9rem;
  }

  .link-button {
    padding: 0.6rem 1rem;
    font-size: 0.9rem;
  }

  .section-subtitle {
    font-size: 1.5rem;
    margin-bottom: 30px;
  }

  .projects-grid {
    grid-template-columns: 1fr;
    gap: 2rem;
    max-width: 500px;
  }

  .card-image {
    height: 220px;
  }

  .project-title {
    font-size: 1.2rem;
  }

  .project-desc {
    font-size: 0.9rem;
  }
}

/* Petits mobiles */
@media (max-width: 480px) {
  .project-container {
    padding: 20px 10px;
  }

  .title {
    font-size: 1.5rem;
    margin-bottom: 30px;
  }

  .featured-wrapper {
    padding: 1rem;
    gap: 1rem;
  }

  .featured-image {
    height: 200px;
  }

  .featured-title {
    font-size: 1.3rem;
  }

  .featured-desc {
    font-size: 0.85rem;
    padding-left: 1rem;
  }

  .tech-badges {
    gap: 0.4rem;
  }

  .badge {
    font-size: 0.75rem;
    padding: 0.3rem 0.7rem;
  }

  .link-button {
    padding: 0.5rem 0.8rem;
    font-size: 0.85rem;
    gap: 0.4rem;
  }

  .link-button svg {
    width: 16px;
    height: 16px;
  }

  .section-subtitle {
    font-size: 1.3rem;
  }

  .projects-grid {
    gap: 1.5rem;
  }

  .card-image {
    height: 180px;
  }

  .project-title {
    font-size: 1.1rem;
  }

  .project-desc {
    font-size: 0.85rem;
    padding-left: 1rem;
  }

  .link-icon {
    width: 32px;
    height: 32px;
  }

  .link-icon svg {
    width: 16px;
    height: 16px;
  }
}
</style>