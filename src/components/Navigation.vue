<template>
    <header>
        <nav>
            <a href="#" class="navLinks" :class="{ active: composantActif === 'home' }"
                @click.prevent="composantActif = 'home'">Accueil</a>
            <a href="#" class="navLinks" :class="{ active: composantActif === 'about' }"
                @click.prevent="composantActif = 'about'">A propos</a>
            <a href="#" class="navLinks" :class="{ active: composantActif === 'contact' }"
                @click.prevent="composantActif = 'contact'">Contact</a>
            <a href="#" class="navLinks" :class="{ active: composantActif === 'projectList' }"
                @click.prevent="composantActif = 'projectList'">Projets</a>
            <a href="#" class="navLinks" :class="{ active: composantActif === 'skills' }"
                @click.prevent="composantActif = 'skills'">Compétences</a>
        </nav>
    </header>
    <div class="container">
        <component :is="onglets[composantActif]" />
    </div>

</template>
<script setup>

import Skills from './Skills.vue';
import Home from './Home.vue';
import Contact from './Contact.vue';
import ProjectList from './ProjectList.vue';
import AboutSection from './AboutSection.vue';

import { ref, watch } from 'vue';

const onglets = {
    home: Home,
    about: AboutSection,
    contact: Contact,
    projectList: ProjectList,
    skills: Skills
}

const composantActif = ref('home');

watch(composantActif, (oldValue, newValue) => {

});
</script>
<style scoped>
@import "../assets/main.css";

header {
    height: 10vh;
}

nav {
    padding: 20px 15px;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 25px;
    border-bottom: 10px solid var(--primary-dark);
}

.navLinks {
    font-size: 2rem;
    text-decoration: none;
    color: var(--text-light);
}

.navLinks:hover {
    color: var(--accent);
}

.navLinks.active {
    color: var(--accent);
    border-bottom: 2px solid var(--primary-dark);
}

.container {
    height: 100vh;
}
</style>