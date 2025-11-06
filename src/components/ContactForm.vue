<template>
    <div class="formContainer">
        <form class="formContact" @submit.prevent="validationMessage">
            <h1>Formulaire de contact</h1>
            <div class="nomForm">
                <label>Nom </label>
                <input v-model="name" type="text">
                <span v-if="!isNameValid && name" class="error-msg">Nom invalide</span>
            </div>
            <div class="emailForm">
                <label>Email</label>
                <input v-model="email" type="email" :class="{ error: !isEmailValid && email }">
                <span v-if="!isEmailValid && email" class="error-msg">Email invalide</span>
            </div>
            <div class="textForm">
                <label for="Message">Message</label>
                <textarea v-model="message"></textarea>
                <span v-if="!isMessageValid && message" class="error-msg">Message invalide</span>
            </div>
            <button class="sumbitBtn" type="submit" :disabled="!isFormValid">Envoyer</button>
        </form>
        <p class="validationMessage"> {{ validation }}</p>
    </div>
</template>
<script setup>
import { computed, ref, watch } from 'vue';

const name = ref("");
const email = ref("");
const message = ref("");
const validation = ref("");

const isEmailValid = ref(false);
const isNameValid = ref(false);
const isMessageValid = ref(false);

watch(email, (email) => {
    if (email.includes("@" && ".com")) {
        isEmailValid.value = true;
    }
});

watch(name, (name) => {
    if (name.length > 0) {
        isNameValid.value = true;
    }
});

watch(message, (message) => {
    if (message.length > 0) {
        isMessageValid.value = true;
    }
});

const isFormValid = computed(() => isEmailValid.value && isNameValid.value && isMessageValid.value);

function validationMessage() {
    validation.value = `${name.value}, votre message a bien été envoyé !`;

    name.value = '';
    email.value = '';
    message.value = '';
    isEmailValid.value = false;
    isNameValid.value = false;
    isMessageValid.value = false;

    setTimeout(() => {
        validation.value = ''
    }, 3000)
}
</script>
<style scoped>
@import '../assets/main.css';

.error {
    border: 2px solid red;
}

.error-msg {
    color: red;
    font-size: 0.8em;
}

.validationMessage {
    font-size: 18px;
    font-weight: bold;
    color: green;
    text-align: center;
}

.sumbitBtn:disabled {
    opacity: 0.4;
    cursor: default;
}

.sumbitBtn:disabled:hover {
    transform: none;
    background-color: var(--secondary);
    color: var(--text-light);
}

.sumbitBtn {
    background-color: var(--secondary);
    border: 2px solid var(--neutral-light);
    color: var(--text-light);
    padding: 8px 10px;
    border-radius: 8px;
    cursor: pointer;
}

.sumbitBtn:hover {
    background-color: var(--neutral-light);
    color: var(--text-dark);
    transform: translateY(-6px);
}

.textForm {
    display: flex;
    flex-direction: column;
    gap: 5px;
}

.textForm label {
    margin-left: 5px;
}

.textForm textarea {
    resize: none;
    width: 400px;
    height: 150px;
    padding: 10px 12px;
    border: 2px solid var(--neutral-light);
    outline: none;
    border-radius: 12px;
    margin-left: 5px;
    background-color: var(--neutral-dark);
    color: var(--text-light);
}

.emailForm {
    display: flex;
    flex-direction: column;
    gap: 5px;
}

.emailForm label {
    margin-left: 5px;
}

.emailForm input {
    padding: 10px 12px;
    border: 2px solid var(--neutral-light);
    outline: none;
    border-radius: 12px;
    margin-left: 5px;
    background-color: var(--neutral-dark);
    color: var(--text-light);
    width: 200px;
}

.nomForm {
    display: flex;
    flex-direction: column;
    gap: 5px;
}

.nomForm label {
    margin-left: 5px;
}

.nomForm input {
    padding: 10px 12px;
    border: 2px solid var(--neutral-light);
    outline: none;
    border-radius: 12px;
    margin-left: 5px;
    background-color: var(--neutral-dark);
    color: var(--text-light);
    width: 200px;
}

.formContact {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    color: var(--accent);
    gap: 10px;
}

.formContainer {
    margin: 10% auto;
    width: 500px;
    padding: 15px;
    background-color: var(--neutral-dark);
    border-radius: 8px;
}
</style>