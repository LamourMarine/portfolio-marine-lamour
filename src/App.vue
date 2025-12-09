<template>
  <div class="frame">
    <div id="app">
      <!-- Hamburger menu button (mobile only) -->
      <button
        class="hamburger"
        @click="mobileMenuOpen = !mobileMenuOpen"
        :class="{ active: mobileMenuOpen }"
        aria-label="Toggle menu"
      >
        <span></span>
        <span></span>
        <span></span>
      </button>

      <!-- Header visible sur toutes les pages en mobile -->
      <header class="mobile-header" v-if="isMobile">
        <div class="header-names-mobile">
          <h1><span>Marine</span> <span>Lamour</span></h1>
        </div>
        <p class="tagline">Développeuse web et web mobile</p>
      </header>

      <aside class="sidebar" :class="{ open: mobileMenuOpen }">
        <header class="desktop-header">
          <div class="header-names">
            <h1><span>Marine</span> <span>Lamour</span></h1>
          </div>
          <p class="tagline">Développeuse web et web mobile</p>
        </header>
        <Navbar
          :current-section="currentSection"
          @change-section="handleSectionChange"
        />
      </aside>

      <!-- Overlay pour fermer le menu mobile -->
      <div
        v-if="mobileMenuOpen"
        class="overlay"
        @click="mobileMenuOpen = false"
      ></div>

      <main>
        <transition name="fade" mode="out-in">
          <component
            :is="currentSectionComponent"
            :key="currentSection"
            @change-section="handleSectionChange"
          />
        </transition>
      </main>
    </div>
  </div>
</template>

<script>
import Navbar from "./components/Navbar.vue";
import Home from "./components/Home.vue";
import StackTechnique from "./components/StackTechnique.vue";
import About from "./components/About.vue";
import Projects from "./components/Projects.vue";
import Contact from "./components/Contact.vue";

export default {
  components: { Navbar, Home, StackTechnique, About, Projects, Contact },
  data() {
    return {
      currentSection: "Home",
      mobileMenuOpen: false,
      isMobile: false,
    };
  },
  computed: {
    currentSectionComponent() {
      return this.currentSection;
    },
  },
  watch: {
    currentSection() {
      // Attendre que le DOM soit mis à jour
      this.$nextTick(() => {
        const mainElement = document.querySelector("main");
        if (mainElement) {
          mainElement.scrollTo({
            top: 0,
            behavior: "smooth",
          });
        }
      });
    },
  },
  methods: {
    handleSectionChange(section) {
      this.currentSection = section;
      this.mobileMenuOpen = false;
    },
    checkMobile() {
      this.isMobile = window.innerWidth <= 768;
    },
  },
  mounted() {
    this.checkMobile();
    window.addEventListener("resize", this.checkMobile);
  },
  beforeUnmount() {
    window.removeEventListener("resize", this.checkMobile);
  },
};
</script>

<style scoped>
html,
body {
  margin: 0;
  padding: 0;
  height: 100%;
  background-color: #111;
  color: white;
  font-family: "Inter", sans-serif;
}

.frame {
  background-color: #1a1a1a;
  background: radial-gradient(ellipse at top right, #4c4c4cd6 0%, #111 100%);
  position: fixed;
  inset: 1cm;
  border: 1px solid white;
  box-sizing: border-box;
  z-index: 0;
  display: flex;
}

#app {
  display: flex;
  padding: 20px;
  width: 100%;
  text-align: left;
  position: relative;
  z-index: 1;
}

/* Header mobile (affiché uniquement sur mobile) */
.mobile-header {
  display: none;
}

/* Header desktop (dans la sidebar) */
.desktop-header {
  z-index: 10;
  margin-bottom: 40px;
}

.header-names,
.header-names-mobile {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  align-items: center;
}

h1 {
  font-weight: 100;
  font-size: 85px;
  font-family: "Inter", sans-serif;
  margin: 0;
  padding: 0;
  display: flex;
  flex-wrap: wrap;
}

.tagline {
  margin-top: 5px;
  font-weight: 400;
  font-size: 20px;
}

.sidebar {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 80px;
  color: white;
  width: 240px;
  flex-shrink: 0;
}

main {
  padding: 20px;
  flex-grow: 1;
  overflow-y: auto;
}

/* Hamburger menu (hidden on desktop) */
.hamburger {
  display: none;
  flex-direction: column;
  justify-content: space-around;
  width: 30px;
  height: 25px;
  background: transparent;
  border: none;
  cursor: pointer;
  padding: 0;
  z-index: 1001;
  position: fixed;
  top: 30px;
  right: 30px;
}

.hamburger span {
  width: 30px;
  height: 3px;
  background: white;
  border-radius: 10px;
  transition: all 0.3s ease;
}

.hamburger.active span:nth-child(1) {
  transform: rotate(45deg) translate(8px, 8px);
}

.hamburger.active span:nth-child(2) {
  opacity: 0;
}

.hamburger.active span:nth-child(3) {
  transform: rotate(-45deg) translate(7px, -7px);
}

/* Overlay pour mobile */
.overlay {
  display: none;
}

/* Transition fade douce */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

/* ==================== RESPONSIVE ==================== */

/* Tablette */
@media (max-width: 1024px) {
  .frame {
    inset: 0.5cm;
  }

  h1 {
    font-size: 60px;
  }

  .sidebar {
    gap: 50px;
  }
}

/* Mobile */
@media (max-width: 768px) {
  .frame {
    inset: 0px;
    border: none;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    width: 100vw;
    overflow-x: hidden;
  }

  #app {
    flex-direction: column;
    padding: 0px;
    width: 100vw;
    max-width: 100vw;
    box-sizing: border-box;
  }

  .hamburger {
    display: flex;
  }

  /* Afficher le header mobile */
  .mobile-header {
    display: block;
    text-align: center;
    margin-bottom: 20px;
    padding: 20px 15px 0 15px;
    width: 100%;
    box-sizing: border-box;
  }

  .header-names-mobile {
    justify-content: center;
  }

  .mobile-header h1 {
    font-size: 40px;
  }

  .mobile-header .tagline {
    font-size: 16px;
  }

  /* Cacher le header dans la sidebar sur mobile */
  .desktop-header {
    display: none;
  }

  .sidebar {
    position: fixed;
    top: 0;
    left: -100%;
    width: 70%;
    max-width: 300px;
    height: 100vh;
    background: #1a1a1a;
    z-index: 1000;
    padding: 30px;
    transition: left 0.3s ease;
    overflow-y: auto;
    gap: 40px;
  }

  .sidebar.open {
    left: 0;
  }

  .overlay {
    display: block;
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background: rgba(0, 0, 0, 0.7);
    z-index: 999;
  }

  main {
    padding: 0px;
    width: 100%;
    max-width: 100vw;
    box-sizing: border-box;
  }
}

/* Très petits mobiles */
@media (max-width: 480px) {
  .mobile-header h1 {
    font-size: 32px;
  }

  .mobile-header .tagline {
    font-size: 14px;
  }

  .sidebar {
    width: 80%;
  }
}

/* Petits mobiles comme iPhone 11 (375px) */
@media (max-width: 400px) {
  .mobile-header h1 {
    font-size: 32px; /* Plus petit pour iPhone 11 */
  }

  .mobile-header .tagline {
    font-size: 14px;
  }

  .sidebar {
    width: 85%; /* Plus large sur petit écran */
    padding: 20px;
  }

  #app {
    padding: 0px; /* Encore moins de padding */
  }

  main {
    padding: 0px;
  }
}
</style>
