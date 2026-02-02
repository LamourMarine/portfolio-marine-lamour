<template>
  <section class="home-content">
    <div class="home-center">
      <h1 class="home-headline">
        Développeuse
        <span class="gradient-text">Backend</span>
      </h1>

        <div class="home-intro">
          <p>
            Développeuse backend spécialisée en Java/Spring Boot et PHP/Symfony, je 
            conçois des API REST robustes et des architectures logicielles performantes. 
            Mon expertise couvre la gestion de bases de données relationnelles (PostgreSQL), 
            l'authentification sécurisée (JWT), et le déploiement d'applications en production. 
            Compétente également en React/TypeScript pour l'intégration frontend.
          </p>

          <p>
            Rigoureuse et méthodique, j'accorde une attention particulière à la qualité du 
            code, aux tests unitaires (JUnit, Mockito), et aux bonnes pratiques de développement. 
            Mes projets déployés témoignent de ma capacité à concevoir des solutions backend 
            complètes, de la modélisation des données au déploiement sur des environnements cloud.
          </p>
        </div>
        
      <div class="home-cta">
        <a
          href="#"
          @click.prevent="$emit('change-section', 'Projects')"
          class="cta-link primary"
        >
          → Découvrir mes projets
        </a>

        <a
          href="#"
          @click.prevent="$emit('change-section', 'Contact')"
          class="cta-link secondary"
        >
          Me contacter
        </a>
      </div>

      <!-- Liens directs vers CV, LinkedIn, GitHub -->
      <div class="social-links">
        <a
          href="https://www.linkedin.com/in/marine-lamour-8a1747278/"
          target="_blank"
          rel="noopener noreferrer"
          class="social-link"
          title="LinkedIn"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24"
            fill="currentColor"
          >
            <path
              d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"
            />
          </svg>
        </a>
        <a
          href="https://github.com/LamourMarine"
          target="_blank"
          rel="noopener noreferrer"
          class="social-link"
          title="GitHub"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24"
            fill="currentColor"
          >
            <path
              d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"
            />
          </svg>
        </a>
        <a
          href="/CV.pdf"
          target="_blank"
          rel="noopener noreferrer"
          class="social-link"
          title="Télécharger mon CV"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
          >
            <path
              d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"
            ></path>
            <polyline points="14 2 14 8 20 8"></polyline>
            <line x1="16" y1="13" x2="8" y2="13"></line>
            <line x1="16" y1="17" x2="8" y2="17"></line>
            <polyline points="10 9 9 9 8 9"></polyline>
          </svg>
        </a>
      </div>
    </div>
  </section>
</template>

<style scoped>
.home-content {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100%;
  padding: 40px;
}

.home-center {
  max-width: 800px;
  text-align: center;
  display: flex;
  flex-direction: column;
  gap: 32px;
  animation: fadeIn 0.8s ease-in;
}

.home-headline {
  font-size: 3.5rem;
  font-weight: 300;
  line-height: 1.2;
  margin: 0;
  color: white;
}

.gradient-text {
  background: linear-gradient(135deg, #1b998b, #4de6d1);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  font-weight: 600;
  display: inline-block;
}

.home-intro {
  display: flex;
  flex-direction: column;
  gap: 1.2em;
  text-align: left;
  max-width: 700px;
  margin: 0 auto;
}

.home-intro p {
  font-size: 1.1rem;
  color: #d4d4d4;
  line-height: 1.7;
  margin: 0;
}

.home-cta {
  display: flex;
  justify-content: center;
  gap: 16px;
  flex-wrap: wrap;
  margin-top: 16px;
}

.cta-link {
  color: white;
  text-decoration: none;
  font-size: 1.05rem;
  font-weight: 500;
  transition: all 0.3s ease;
  padding: 12px 28px;
  border-radius: 8px;
  display: inline-flex;
  align-items: center;
  gap: 8px;
}

.cta-link.primary {
  background: linear-gradient(135deg, #1b998b, #17a085);
  border: none;
}

.cta-link.primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(27, 153, 139, 0.3);
}

.cta-link.secondary {
  background: transparent;
  border: 2px solid rgba(255, 255, 255, 0.3);
}

.cta-link.secondary:hover {
  border-color: #1b998b;
  color: #1b998b;
}

.social-links {
  display: flex;
  justify-content: center;
  gap: 24px;
  margin-top: 16px;
}

.social-link {
  width: 44px;
  height: 44px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.1);
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  transition: all 0.3s ease;
  text-decoration: none;
}

.social-link:hover {
  background: #1b998b;
  transform: scale(1.1);
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
    padding: 20px 15px;
  }

  .home-headline {
    font-size: 2.5rem;
  }

  .home-intro {
    text-align: justify;
  }

  .home-intro p {
    font-size: 1rem;
  }

  .home-center {
    max-width: 100%;
    gap: 24px;
  }

  .cta-link {
    font-size: 1rem;
    padding: 10px 24px;
  }

  .social-links {
    gap: 20px;
  }

  .social-link {
    width: 40px;
    height: 40px;
  }
}

@media (max-width: 480px) {
  .home-headline {
    font-size: 2rem;
  }

  .home-intro p {
    font-size: 0.95rem;
  }

  .home-center {
    gap: 20px;
  }

  .cta-link {
    font-size: 0.95rem;
    padding: 10px 20px;
  }
}
</style>
