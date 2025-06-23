<template>
    <div class="stack-container">
        <h1 class="title">Stack Technique</h1>
        <div class="icons-container">
             <!-- icônes -->
        </div>
    </div>
</template>

<script>
export default {
  name: 'StackTechnique'
}
</script>

<style scoped>

.stack-container {
  display: flex;
  flex-direction: column;
  color: white;
}

.title {
  display: flex;
    flex-direction: column;
    justify-content: center;
  font-weight: 100;  /* même style que ton nom par ex */
  font-size: 2.5rem;
  padding: 20px 40px 0 40px; /* un peu d'espace en haut et sur les côtés */
  margin: 0;
  font-family: 'Inter', sans-serif; /* ou ta police principale */
}

</style>