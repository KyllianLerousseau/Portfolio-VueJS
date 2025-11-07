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
    <Transition name="slide-fade" mode="out-in">
        <div class="container" :key="composantActif">
            <component :is="onglets[composantActif]" />
        </div>
    </Transition>

</template>
<script setup>
import Skills from './Skills.vue';
import Home from './Home.vue';
import Contact from './Contact.vue';
import ProjectList from './ProjectList.vue';
import AboutSection from './AboutSection.vue';

import { ref, shallowRef, Transition } from 'vue';


const onglets = {
    home: Home,
    about: AboutSection,
    contact: Contact,
    projectList: ProjectList,
    skills: Skills
}

const composantActif = shallowRef('home');

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
    flex-wrap: wrap;
    height: auto;
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
    width: 100%;
    min-height: 100vh;
    max-height: 100%;
    padding: 2rem 1rem;
    box-sizing: border-box;
}
.slide-fade-enter-from {
    transform: translateX(20px);
    opacity: 0;
}

.slide-fade-enter-to {
    transform: translateX(0);
    opacity: 1;
}

.slide-fade-leave-from {
    transform: translateX(0);
    opacity: 1;
}

.slide-fade-leave-to {
    transform: translateX(20px);
    opacity: 0;
}

.slide-fade-enter-active {
    transition: all 0.3s ease-out;
}

.slide-fade-leave-active {
    transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
}

@media (max-width: 768px) {
    nav {
        flex-direction: column;
        gap: 15px;
    }

    .navLinks {
        font-size: 1.5rem;
    }
}
</style>