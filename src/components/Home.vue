<template>
  <section class="home-content">
    <div class="home-center">
      <h1 class="home-headline">
        Développeuse web en
        <span class="gradient-text">apprentissage continu</span>
      </h1>
      <p class="home-aboutme">
        Développeuse web en apprentissage constant, je m'appuie sur mon esprit
        logique et ma persévérance pour résoudre des problèmes, progresser
        chaque jour et bâtir des applications modernes.
      </p>

      <div class="home-cta">
        <a
          href="#"
          @click.prevent="$emit('change-section', 'Projects')"
          class="cta-link"
        >
          → Découvrir mes projets
        </a>
      </div>

      <p class="home-availability">
        <span class="availability-dot"></span>
        Recherche alternance CDA • Decembre 2025
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
  max-width: 700px;
  text-align: center;
  display: flex;
  flex-direction: column;
  gap: 32px;
  animation: fadeIn 0.8s ease-in;
}

.home-headline {
  font-size: 3rem;
  font-weight: 300;
  line-height: 1.2;
  margin: 0 0 10px 0;
  color: white;
}

.gradient-text {
  background: linear-gradient(135deg, #1b998b, #4de6d1);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  font-weight: 600;
  display: inline-block;
  animation: gradientShift 3s ease infinite;
}

@keyframes gradientShift {
  0%,
  100% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
}

.home-aboutme {
  font-size: 1.3rem;
  color: #d4d4d4;
  line-height: 1.7;
  margin: 0;
}

.home-cta {
  display: flex;
  justify-content: center;
}

.cta-link {
  color: white;
  text-decoration: none;
  font-size: 1.2rem;
  font-weight: 500;
  transition: all 0.3s ease;
  padding: 12px 0;
  border-bottom: 2px solid transparent;
  position: relative;
}

.cta-link::before {
  content: "";
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 2px;
  background: linear-gradient(90deg, #1b998b, #4de6d1);
  transition: width 0.3s ease;
}

.cta-link:hover::before {
  width: 100%;
}

.cta-link:hover {
  color: #1b998b;
  transform: translateX(8px);
}

.home-availability {
  font-size: 1rem;
  color: #aaa;
  margin: 0;
  font-weight: 400;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
}

.availability-dot {
  width: 10px;
  height: 10px;
  background: #1b998b;
  border-radius: 50%;
  display: inline-block;
  animation: pulse 2s ease-in-out infinite;
}

@keyframes pulse {
  0%,
  100% {
    opacity: 1;
    transform: scale(1);
  }
  50% {
    opacity: 0.6;
    transform: scale(1.2);
  }
}

.cta-link:focus {
  outline: 2px solid #1b998b;
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

/* Responsive */
@media (max-width: 768px) {
  .home-content {
    padding: 20px;
  }

  .home-headline {
    font-size: 2.2rem;
  }

  .home-aboutme {
    font-size: 1.1rem;
  }

  .home-center {
    max-width: 100%;
    gap: 24px;
  }

  .cta-link {
    font-size: 1.1rem;
  }

  .home-availability {
    font-size: 0.9rem;
  }
}

@media (max-width: 480px) {
  .home-headline {
    font-size: 1.8rem;
  }

  .home-aboutme {
    font-size: 1rem;
  }

  .home-center {
    gap: 20px;
  }

  .cta-link {
    font-size: 1rem;
  }
}
</style>
