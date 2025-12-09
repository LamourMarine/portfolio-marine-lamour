<template>
  <section class="home-content"> 
    <div class="home-center">
      <p class="home-aboutme">
        Développeuse web en apprentissage constant, je m'appuie sur mon esprit logique et ma persévérance pour résoudre des problèmes, progresser chaque jour et créer des solutions durables.
      </p>
      
      <div class="home-cta">
        <a href="#" @click.prevent="$emit('change-section', 'Projects')" class="cta-link">
          → Découvrir mes projets
        </a>
      </div>

      <p class="home-availability">
        Recherche alternance CDA • Septembre 2025
      </p>
    </div>
  </section>
</template>


<style scoped>
.home-content {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  padding: 40px;
}

.home-center {
  max-width: 600px;
  text-align: center;
  display: flex;
  flex-direction: column;
  gap: 32px;
  animation: fadeIn 0.8s ease-in;
}

.home-aboutme {
  font-size: 1.5rem;
  color: white;
  line-height: 1.6;
  margin: 0;
}

.home-cta {
  display: flex;
  justify-content: center;
}

.cta-link {
  color: white;
  text-decoration: none;
  font-size: 1.1rem;
  font-weight: 500;
  transition: all 0.3s ease;
  padding: 8px 0;
  border-bottom: 1px solid transparent;
}

.cta-link:hover {
  color: #1B998B;
  border-bottom-color: #1B998B;
  transform: translateX(4px);
}

.home-availability {
  font-size: 0.95rem;
  color: #aaa;
  margin: 0;
  font-weight: 400;
}

.cta-link:focus {
  outline: 2px solid #1B998B;
  outline-offset: 4px;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@media (max-width: 768px) {
  .home-aboutme {
    font-size: 1.2rem;
  }
  
  .home-center {
    max-width: 90%;
    gap: 24px;
  }
}

</style>