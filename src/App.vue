<template>
  <div class="frame">
    <div id="app">
      <aside class="sidebar">
        <header>
          <h1>Marine Lamour</h1>
          <p class="tagline">Développeuse web et web mobile</p>
        </header>
        <Navbar 
          :current-section="currentSection" 
          @change-section="currentSection = $event" 
        />
      </aside>

      <main>
        <transition name="fade" mode="out-in">
          <component :is="currentSectionComponent" :key="currentSection" />
        </transition>
      </main>
    </div>
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue'
import Home from './components/Home.vue'
import StackTechnique from './components/StackTechnique.vue'
import About from './components/About.vue'
import Projects from './components/Projects.vue'
import Contact from './components/Contact.vue'

export default {
  components: { Navbar, Home, StackTechnique, About, Projects, Contact },
  data() {
    return {
      currentSection: 'Home', // section par défaut
    }
  },
  computed: {
    currentSectionComponent() {
      // renvoie le composant à afficher selon la section active
      return this.currentSection
    }
  }
}
</script>

<style scoped>

html, body {
  margin: 0;
  padding: 0;
  height: 100%;
  background-color: #111; 
  color: white;
  font-family: 'Inter', sans-serif;
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
  height: 100vh;
  width: 100vw; 
  text-align: left;
  position: relative;
  z-index: 1;

}


header {
  top: 40px;
  left: 20px;
  z-index: 10;
  margin-bottom: 40px;
}

 h1 {
  font-weight: 100;
  font-size: 60px;
  font-family: 'Inter', sans-serif;  margin: 0;
  padding: 0;
}

.tagline {
  margin-top: 5px;
  font-weight: 400;
}

.sidebar {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 80px;
  color: white;
}


main {
  margin-left: 240px;
  padding: 20px;
  flex-grow: 1;
  overflow-y: auto;
}

/* Transition fade douce */
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s ease;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
}
</style>
