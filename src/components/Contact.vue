<template>
  <section class="contact-container">
    <h1 class="title">Contact</h1>
    
    <div class="contact-content">
      <div class="contact-intro">
        <p>
          Vous avez un projet, une question ou simplement envie d'échanger ? 
          N'hésitez pas à me contacter via ce formulaire ou directement sur 
          <a href="https://www.linkedin.com/in/marine-lamour-8a1747278/" target="_blank" rel="noopener noreferrer">LinkedIn</a>.
        </p>
        <p class="response-time">Je réponds généralement sous 24-48h 📧</p>
      </div>

      <form @submit.prevent="submitForm" class="contact-form">
        <div class="form-group">
          <label for="name">Nom *</label>
          <input
            type="text"
            id="name"
            v-model="form.name"
            required
            placeholder="Votre nom"
            :disabled="isSubmitting"
          />
        </div>

        <div class="form-group">
          <label for="email">Email *</label>
          <input
            type="email"
            id="email"
            v-model="form.email"
            required
            placeholder="votre.email@exemple.com"
            :disabled="isSubmitting"
          />
        </div>

        <div class="form-group">
          <label for="message">Message *</label>
          <textarea
            id="message"
            v-model="form.message"
            required
            placeholder="Votre message..."
            ref="messageTextarea"
            @input="adjustHeight"
            :disabled="isSubmitting"
          ></textarea>
        </div>

        <!-- Message de succès -->
        <div v-if="showSuccess" class="alert alert-success">
          <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <path d="M22 11.08V12a10 10 0 1 1-5.93-9.14"></path>
            <polyline points="22 4 12 14.01 9 11.01"></polyline>
          </svg>
          Message envoyé avec succès ! Je vous réponds très vite.
        </div>

        <!-- Message d'erreur -->
        <div v-if="showError" class="alert alert-error">
          <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <circle cx="12" cy="12" r="10"></circle>
            <line x1="15" y1="9" x2="9" y2="15"></line>
            <line x1="9" y1="9" x2="15" y2="15"></line>
          </svg>
          Une erreur est survenue. Veuillez réessayer.
        </div>

        <div class="button-wrapper">
          <button type="submit" :disabled="isSubmitting" class="submit-button">
            <span v-if="!isSubmitting">Envoyer</span>
            <span v-else class="loading">
              <svg class="spinner" xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <line x1="12" y1="2" x2="12" y2="6"></line>
                <line x1="12" y1="18" x2="12" y2="22"></line>
                <line x1="4.93" y1="4.93" x2="7.76" y2="7.76"></line>
                <line x1="16.24" y1="16.24" x2="19.07" y2="19.07"></line>
                <line x1="2" y1="12" x2="6" y2="12"></line>
                <line x1="18" y1="12" x2="22" y2="12"></line>
                <line x1="4.93" y1="19.07" x2="7.76" y2="16.24"></line>
                <line x1="16.24" y1="7.76" x2="19.07" y2="4.93"></line>
              </svg>
              Envoi en cours...
            </span>
          </button>
        </div>
      </form>
    </div>
  </section>
</template>

<script lang="ts" setup>
import { reactive, ref } from 'vue'
import emailjs from '@emailjs/browser'

const serviceID = import.meta.env.VITE_EMAILJS_SERVICE_ID;
const templateID = import.meta.env.VITE_EMAILJS_TEMPLATE_ID;
const publicKey = import.meta.env.VITE_EMAILJS_PUBLIC_KEY;

// États du formulaire
const isSubmitting = ref(false)
const showSuccess = ref(false)
const showError = ref(false)

const submitForm = async () => {
  isSubmitting.value = true
  showSuccess.value = false
  showError.value = false

  const templateParams = {
    name: form.name,
    email: form.email,
    message: form.message,
  }

  try {
    const response = await emailjs.send(serviceID, templateID, templateParams, publicKey)
    console.log('SUCCESS!', response.status, response.text)
    
    // Afficher message de succès
    showSuccess.value = true
    
    // Réinitialiser le formulaire
    form.name = ''
    form.email = ''
    form.message = ''
    
    // Masquer le message après 5 secondes
    setTimeout(() => {
      showSuccess.value = false
    }, 5000)
    
  } catch (error) {
    console.error('FAILED...', error)
    showError.value = true
    
    // Masquer le message d'erreur après 5 secondes
    setTimeout(() => {
      showError.value = false
    }, 5000)
  } finally {
    isSubmitting.value = false
  }
}

// Définition d'un type pour le formulaire
interface ContactForm {
  name: string
  email: string
  message: string
}

// Création d'un objet réactif avec valeurs initiales
const form = reactive<ContactForm>({
  name: '',
  email: '',
  message: ''
})

const messageTextarea = ref<HTMLTextAreaElement | null>(null)

function adjustHeight() {
  if (!messageTextarea.value) return
  messageTextarea.value.style.height = '200px' // reset la hauteur
  if (messageTextarea.value.scrollHeight > 200) {
    messageTextarea.value.style.height = messageTextarea.value.scrollHeight + 'px';
  }
}
</script>

<style scoped>
.contact-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-left: 120px;
  padding: 40px 20px;
  color: white;
}

.title {
  font-weight: 100;
  font-size: 2.5rem;
  margin: 0 0 40px 0;
  font-family: "Inter", sans-serif;
  text-decoration: underline;
  text-align: center;
}

.contact-content {
  width: 100%;
  max-width: 600px;
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.contact-intro {
  text-align: center;
  color: #d4d4d4;
  line-height: 1.6;
}

.contact-intro p {
  margin: 0 0 1rem 0;
}

.contact-intro a {
  color: #1B998B;
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s ease;
}

.contact-intro a:hover {
  color: #17a085;
  text-decoration: underline;
}

.response-time {
  font-size: 0.95rem;
  color: #aaa;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

label {
  font-size: 1rem;
  font-weight: 500;
  color: white;
}

input,
textarea {
  padding: 0.9rem;
  background-color: rgba(255, 255, 255, 0.95);
  color: #222;
  border: 2px solid transparent;
  border-radius: 8px;
  font-size: 1rem;
  font-family: 'Inter', sans-serif;
  transition: all 0.3s ease;
  width: 100%;
  box-sizing: border-box;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #1B998B;
  background-color: white;
  box-shadow: 0 0 0 3px rgba(27, 153, 139, 0.1);
}

input:disabled,
textarea:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

input::placeholder,
textarea::placeholder {
  color: #999;
}

textarea {
  min-height: 200px;
  resize: vertical;
  line-height: 1.5;
}

/* Alerts */
.alert {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 1rem;
  border-radius: 8px;
  font-size: 0.95rem;
  animation: slideIn 0.3s ease;
}

.alert-success {
  background-color: rgba(27, 153, 139, 0.15);
  border: 1px solid #1B998B;
  color: #1B998B;
}

.alert-error {
  background-color: rgba(239, 68, 68, 0.15);
  border: 1px solid #ef4444;
  color: #ef4444;
}

@keyframes slideIn {
  from {
    opacity: 0;
    transform: translateY(-10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Button */
.button-wrapper {
  display: flex;
  justify-content: center;
  margin-top: 0.5rem;
}

.submit-button {
  padding: 1rem 3rem;
  background: linear-gradient(135deg, #1B998B, #17a085);
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 1.1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  min-width: 160px;
  justify-content: center;
}

.submit-button:hover:not(:disabled) {
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(27, 153, 139, 0.3);
}

.submit-button:active:not(:disabled) {
  transform: translateY(0);
}

.submit-button:disabled {
  opacity: 0.7;
  cursor: not-allowed;
}

.loading {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.spinner {
  animation: spin 1s linear infinite;
}

@keyframes spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

/* ==================== RESPONSIVE ==================== */

/* Tablette */
@media (max-width: 1024px) {
  .contact-container {
    margin-left: 60px;
  }
}

/* Mobile */
@media (max-width: 768px) {
  .contact-container {
    margin-left: 0;
    padding: 20px 15px;
  }

  .title {
    font-size: 1.8rem;
    margin-bottom: 30px;
  }

  .contact-content {
    max-width: 100%;
  }

  .contact-intro {
    font-size: 0.95rem;
  }

  input,
  textarea {
    padding: 0.8rem;
    font-size: 0.95rem;
  }

  textarea {
    min-height: 150px;
  }

  .submit-button {
    padding: 0.9rem 2.5rem;
    font-size: 1rem;
    width: 100%;
  }
}

/* Petits mobiles */
@media (max-width: 480px) {
  .contact-container {
    padding: 20px 10px;
  }

  .title {
    font-size: 1.5rem;
    margin-bottom: 25px;
  }

  .contact-intro {
    font-size: 0.9rem;
  }

  .response-time {
    font-size: 0.85rem;
  }

  input,
  textarea {
    padding: 0.75rem;
    font-size: 0.9rem;
  }

  label {
    font-size: 0.95rem;
  }

  .submit-button {
    padding: 0.85rem 2rem;
    font-size: 0.95rem;
  }

  .alert {
    font-size: 0.85rem;
    padding: 0.85rem;
  }
}
</style>