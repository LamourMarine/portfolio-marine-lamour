<template>
  <nav>
    <ul>
      <li v-if="currentSection !== 'Home'">
        <a href="#" @click.prevent="changeSection('Home')">Accueil</a>
      </li>
      <li v-if="currentSection !== 'About'">
        <a href="#" @click.prevent="changeSection('About')">À propos</a>
      </li>
      <li v-if="currentSection !== 'Projects'">
        <a href="#" @click.prevent="changeSection('Projects')">Projets</a>
      </li>
      <li v-if="currentSection !== 'Contact'">
        <a href="#" @click.prevent="changeSection('Contact')">Contact</a>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  props: ['currentSection'],
  methods: {
    changeSection(section) {
      this.$emit('change-section', section)
    }
  }
}
</script>

<style scoped>
nav {
  position: fixed;
  top: 35%;
  left: 20px;
}

ul {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

a {
  color: white;
  text-decoration: none;
  font-weight: 600;
  font-size: 1.2rem;
  transition: color 0.3s ease;
  cursor: pointer;
}

a:hover {
  color: #42b883;
}
</style>
