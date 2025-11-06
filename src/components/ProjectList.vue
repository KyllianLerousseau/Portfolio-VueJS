<template>
    <select v-model="selectedCategory">
        <option value="">Toutes les catégories</option>
        <option v-for="category in categories" :key="category" :value="category">
            {{ category }}
        </option>
    </select>

    <div class="cards">
        <div v-for="(project, index) in filteredProjects" :key="project.id" class="project-card"
            :class="{ filtre: activeIndexes.includes(index) }">
            <h3>{{ project.title }}</h3>
            <p>{{ project.category }}</p>
            <p> {{ project.description }}</p>
            <p> {{ project.date }}</p>
            <button class="detailsBtn">Voir détails</button>
        </div>
    </div>
</template>
<script setup>
import { computed, onMounted, reactive, ref, watch } from 'vue';

const projects = reactive([
    {
        title: "mini-twitter",
        category: "Web App / Backend",
        description: "Application web simulant un réseau social type Twitter avec publications et abonnements.",
        date: "23-10-2025",
        technologies: ["PHP", "Symfony", "MySQL", "HTML", "CSS", "JavaScript"],
        link: "https://github.com/KyllianLerousseau/mini-twitter"
    },
    {
        title: "projet-react",
        category: "Frontend / React",
        description: "Application développée avec React comme base de projet front-end moderne.",
        date: "06-11-2025",
        technologies: ["React", "JavaScript", "HTML", "CSS", "Vite"],
        link: "https://github.com/KyllianLerousseau/projet-react"
    },
    {
        title: "projet-MVC",
        category: "Backend / MVC",
        description: "Projet utilisant une architecture MVC pour structurer une application web.",
        date: "15-10-2025",
        technologies: ["PHP", "MySQL", "HTML", "CSS", "JavaScript"],
        link: "https://github.com/KyllianLerousseau/projet-MVC"
    },
    {
        title: "Site-recettes",
        category: "Web / Frontend",
        description: "Site de recettes de cuisine listant des recettes avec filtrage et affichage d’articles.",
        date: "03-10-2025",
        technologies: ["HTML", "CSS", "JavaScript"],
        link: "https://github.com/KyllianLerousseau/Site-recettes"
    },
    {
        title: "javascript-horloge",
        category: "Frontend / JavaScript",
        description: "Horloge numérique en JavaScript permettant d’afficher l'heure en temps réel.",
        date: "04-03-2025",
        technologies: ["JavaScript", "HTML", "CSS"],
        link: "https://github.com/KyllianLerousseau/javascript-horloge"
    },
    {
        title: "javascript-calculatrice",
        category: "Frontend / JavaScript",
        description: "Calculatrice simple implémentée en JavaScript pour les opérations de base.",
        date: "04-03-2025",
        technologies: ["JavaScript", "HTML", "CSS"],
        link: "https://github.com/KyllianLerousseau/javascript-calculatrice"
    }
]);


const selectedCategory = ref("");

const categories = computed(() => {
    const allCategories = projects.map(project => project.category);
    const uniqueCategories = allCategories.filter((category, index) => {
        return allCategories.indexOf(category) === index;
    });
    return uniqueCategories;
});

const filteredProjects = computed(() => {

    let listFiltree = projects;

    if (selectedCategory.value !== "") {
        listFiltree = listFiltree.filter(project => project.category === selectedCategory.value);
    }

    return listFiltree;
});

const activeIndexes = ref([]);

function animationCards() {
    activeIndexes.value = [];

    filteredProjects.value.forEach((_, index) => {
        setTimeout(() => {
            activeIndexes.value.push(index);
        }, (index + 1) * 100)
    })
}

onMounted(() => {
    animationCards();
});

watch(filteredProjects, () => {
    animationCards();
});

</script>
<style scoped>
.cards {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-template-rows: auto;
    gap: 15px 0px;
    padding: 10px;
}

.project-card {
    width: 300px;
    height: 300px;
    background-color: #0f172ad0;
    border: 2px solid var(--neutral-light);
    color: var(--text-light);
    padding: 15px;
    border-radius: 8px;
    opacity: 0;
    transform: translateY(10px) scale(0.7);
    transition: opacity 0.4s ease, transform 0.7s ease;
}

.project-card.filtre {
    transform: translate(0) scale(1);
    opacity: 1;
}

select {
    background-color: var(--secondary);
    color: var(--text-dark);
    font-weight: bold;
    cursor: pointer;
    border: none;
    outline: none;
    padding: 10px 10px;
    margin: 10px 15px;
    border-radius: 6px;
}

.detailsBtn {
    background-color: var(--secondary);
    border: 2px solid var(--neutral-light);
    color: var(--text-light);
    padding: 8px 10px;
    border-radius: 8px;
    cursor: pointer;
}

.detailsBtn:hover {
    background-color: var(--neutral-light);
    color: var(--text-dark);
    transform: translateY(-6px);
}
</style>