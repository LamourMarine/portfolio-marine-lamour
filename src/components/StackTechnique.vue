<template>
    <div class="stack-container">
        <h1 class="title">Stack Technique</h1>
        <div class="tech-icons">
          <div class="tech-wrapper" v-for="tech in technologies" :key="tech.name">
            <div class="tech">
              <div class="card">
                <div class="card-inner">
                  <div class="card-front">
                    <img :src="tech.icon" :alt="tech.name" />
                  </div>
                  <div class="card-back">
                    <p>{{ tech.name }}</p>
                  </div>
                </div>
              </div>
            </div>
            <!-- Nom affiché directement sur mobile (en dehors du .tech) -->
            <p class="tech-name-mobile">{{ tech.name }}</p>
          </div>
        </div>
    </div>
</template>

<script lang="ts" setup>
import vueLogo from '@/assets/Vue.js_Logo_2.svg.png'
import tsLogo from '@/assets/typescript.svg'
import cssLogo from '@/assets/css3.png'
import tailwindLogo from '@/assets/tailwind-css-logo-png_seeklogo-354675-removebg-preview.png'
import phpLogo from '@/assets/kisspng-web-development-php-software-developer-web-applica-create-5ad11121794b05.5974879215236508494968-removebg-preview.png'
import symfonyLogo from '@/assets/symfony-badge-icon-lg.png'
import mysqlLogo from '@/assets/images-removebg-preview.png'
import postgresLogo from '@/assets/PostgreSQL-Logo.wine.png'

const technologies = [
  { name: 'Vue.js', icon: vueLogo },
  { name: 'TypeScript', icon: tsLogo },
  { name: 'CSS', icon: cssLogo },
  { name: 'Tailwind', icon: tailwindLogo },
  { name: 'PHP', icon: phpLogo },
  { name: 'Symfony', icon: symfonyLogo },
  { name: 'MySQL', icon: mysqlLogo },
  { name: 'PostgreSQL', icon: postgresLogo }
]
</script>

<style scoped>
.stack-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-left: 120px;
  color: white;
  padding: 20px;
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
  gap: 100px 40px;
  justify-content: center;
  margin-top: 7rem;
  max-width: 800px;
}

/* Wrapper pour contenir la card ET le nom mobile */
.tech-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
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

/* Nom mobile caché par défaut */
.tech-name-mobile {
  display: none;
  margin: 0;
}

.card {
  width: 120px;
  height: 120px;
  perspective: 1000px;
}

.card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  transform-style: preserve-3d;
  transition: transform 0.6s;
}

.tech:hover .card-inner {
  transform: rotateY(180deg);
}

.card-front,
.card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  border-radius: 8px;
  overflow: hidden;
}

.card-front {
  background: #1a1a1a;
  display: flex;
  justify-content: center;
  align-items: center;
}

.card-front img {
  max-width: 80%;
  max-height: 80%;
}

.card-back {
  background: #333;
  color: white;
  transform: rotateY(180deg);
  display: flex;
  justify-content: center;
  align-items: center;
  font-weight: bold;
}

/* ==================== RESPONSIVE ==================== */

/* Tablette */
@media (max-width: 1024px) {
  .stack-container {
    margin-left: 60px;
  }

  .title {
    font-size: 2rem;
    padding: 15px 30px 0 30px;
  }

  .tech-icons {
    gap: 60px 30px;
    margin-top: 5rem;
  }

  .tech {
    width: 130px;
    height: 130px;
  }

  .card {
    width: 100px;
    height: 100px;
  }
}

/* Mobile */
@media (max-width: 768px) {
  .stack-container {
    margin-left: 0;
    padding: 10px;
  }

  .title {
    font-size: 1.8rem;
    padding: 10px 20px 0 20px;
    text-align: center;
  }

  .tech-icons {
    gap: 40px 20px;
    margin-top: 3rem;
    max-width: 100%;
  }

  .tech-wrapper {
    gap: 10px;
  }

  .tech {
    width: 110px;
    height: 110px;
    background-color: #1a1a1a;
    opacity: 1;
  }

  .card {
    width: 90px;
    height: 90px;
  }

  /* Désactiver le flip sur mobile */
  .card-inner {
    transform: none !important;
  }

  .card-back {
    display: none;
  }

  .card-front {
    background: transparent;
  }

  /* Afficher le nom sous l'icône */
  .tech-name-mobile {
    display: block;
    font-size: 0.9rem;
    font-weight: 500;
    color: white;
    text-align: center;
  }
}

/* Petits mobiles */
@media (max-width: 480px) {
  .title {
    font-size: 1.5rem;
    padding: 10px 10px 0 10px;
  }

  .tech-icons {
    gap: 30px 15px;
    margin-top: 2rem;
  }

  .tech {
    width: 90px;
    height: 90px;
  }

  .card {
    width: 75px;
    height: 75px;
  }

  .tech-name-mobile {
    font-size: 0.85rem;
  }
}

/* Très petits écrans */
@media (max-width: 360px) {
  .tech-icons {
    gap: 20px 10px;
  }

  .tech {
    width: 80px;
    height: 80px;
  }

  .card {
    width: 65px;
    height: 65px;
  }

  .tech-name-mobile {
    font-size: 0.8rem;
  }
}
</style>