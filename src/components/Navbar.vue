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

<script  lang="ts" setup>
import { defineProps, defineEmits, ref } from 'vue'

//Définir les types de props
interface Section {
  name: string
  label: string
}

const { currentSection } = defineProps<{
  currentSection: string
}>()


//Définir les événements émis
const emit = defineEmits<{
  (e: 'change-section', section: string): void
}>()

//Définir les données internes (équivalent data)
const sections = ref<Section[]>([
  { name: 'Home', label: 'Home' },
  { name: 'StackTechnique', label: 'Stack Technique' },
  { name: 'About', label: 'A propos' },
  { name: 'Projects', label: 'Projets' },
  { name: 'Contact', label: 'Contact' },
])

//Méthode pour changer la section (équivalent methods)
function changeSection(section: string) {
  emit('change-section', section)
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
  line-height: 1.3;
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
