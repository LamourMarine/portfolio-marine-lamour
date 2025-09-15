<template>
  <div class="container">
    <h2>Contact</h2>
    <form @submit.prevent="submitForm">
      <div class="form-group">
        <label for="name">Nom</label>
        <input
        type="text"
        id="name"
        v-model="form.name"
        required
        title="Merci de renseigner votre nom."
        />
      </div>

      <div class="form-group">
        <label for="email">Email</label>
        <input
        type="email"
        id="email"
        v-model="form.email"
        required
        title="Merci de renseigner votre email."
        />
      </div>

      <div class="form-group">
        <label for="message">Message</label>
        <textarea
        id="message"
        v-model="form.message"
        required
        title="Merci d'écrire votre message."
        ref="messageTextarea"
        @input="adjustHeight"
        ></textarea>
      </div>

      <div class="button-wrapper">
      <button type="submit">Envoyer</button>
      </div>
    </form>
  </div>
</template>

<script lang="ts" setup>
import { reactive, ref } from 'vue'
import emailjs from '@emailjs/browser'

const serviceID = import.meta.env.VITE_EMAILJS_SERVICE_ID;
const templateID = import.meta.env.VITE_EMAILJS_TEMPLATE_ID;
const publicKey = import.meta.env.VITE_EMAILJS_PUBLIC_KEY;

const submitForm = () => {
  const templateParams = {
    name: form.name,
    email: form.email,
    message: form.message,
  }

  emailjs
    .send(serviceID, templateID, templateParams, publicKey)
    .then((response) => {
      console.log('SUCCESS!', response.status, response.text)
      alert('Message envoyé avec succès !')
    })
    .catch((error) => {
      console.error('FAILED...', error)
      alert('Une erreur est survenue.')
    })
}

//Définition d'un type pour le formulaire
interface ContactForm {
  name: string
  email: string
  message: string
}

//Creation d'un ojet reactif avec valeurs initiales
const form = reactive<ContactForm>({
  name: '',
  email: '',
  message: ''
})

const messageTextarea = ref<HTMLTextAreaElement | null>(null)

function adjustHeight(){
  if (!messageTextarea.value) return
  messageTextarea.value.style.height = '200px' //reset la hauteur
  if (messageTextarea.value.scrollHeight > 200) {
    messageTextarea.value.style.height = messageTextarea.value.scrollHeight + 'px';
  }
}

</script>

<style scoped>
h2 {
  font-size: 2.25rem;
  text-decoration: underline;
  font-weight: 100;
  font-size: 2.5rem;
}
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 118%;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  width: 400px;
}

.form-group input {
  width: 100%;
  box-sizing: border-box;
}

label {
  margin-top: 1rem;
}

.button-wrapper {
  margin-top: 1rem;
  display: flex;
  justify-content: center;
}
input {
  padding: 0.8rem;
  justify-content: center;
  align-items: center;
  background-color: azure;
  color: #222;
}

textarea {
  background-color: azure;
  color: #222;
  height: 200px;
}
</style>

