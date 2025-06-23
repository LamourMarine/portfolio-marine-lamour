<template>
        <nav>
            <ul>
                <li v-for="section in sections" :key="section.name">
                <a href="#" @click.prevent="changeSection(section.name)">
                <span v-if="currentSection === section.name" class="dot"></span>
                    <span v-else>{{ section.label }}</span>
                </a>
                </li>
            </ul>
        </nav>
</template>

<script>
export default {
  props: ['currentSection'],
  emits: ['change-section'],
  data() {
    return {
        sections: [
            { name: 'Home', label:'Home'},
            { name: 'StackTechnique', label: 'Stack Technique'},
            { name: 'About', label: 'A propos'},
            { name: 'Projects', label: 'Projets'},
            { name: 'Contact', label: 'Contact'},
        ],
    }
  },
  methods: {
    changeSection(section) {
      this.$emit('change-section', section)
    }
  }
}
</script>

<style scoped>
.dot {
  display: inline-block;
  width: 10px;
  height: 10px;
  background-color: white;
  border-radius: 50%;
}

nav ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

nav li {
  margin: 5px 0;
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
  color: #1B998B;
}
</style>
