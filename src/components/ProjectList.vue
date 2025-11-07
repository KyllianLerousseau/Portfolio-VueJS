<template>
    <div class="responsive">
        <select v-model="selectedCategory">
            <option value="">Toutes les catégories</option>
            <option v-for="category in categories" :key="category" :value="category">
                {{ category }}
            </option>
        </select>

        <div class="cards">
            <ProjectCard v-for="(project, index) in filteredProjects" :key="project.title" :project="project"
                :isVisible="activeIndexes.includes(index)" @openModal="openModal" />
        </div>

        <div v-if="selectedProject" class="modal-backdrop" @click.self="closeModal">
            <div class="modal">
                <button class="close-btn" @click="closeModal">×</button>
                <div class="modal-image-container">
                    <img :src="selectedProject.image" :alt="selectedProject.title" class="modal-image" />
                </div>
                <h2>{{ selectedProject.title }}</h2>
                <p class="category">{{ selectedProject.category }}</p>
                <p>{{ selectedProject.description }}</p>

                <div class="tech-container" v-if="selectedProject.technologies?.length">
                    <h3>Technologies utilisées</h3>
                    <div class="tech-list">
                        <span v-for="(tech, index) in selectedProject.technologies" :key="index" class="tech-badge">
                            {{ tech }}
                        </span>
                    </div>

                    <a :href="selectedProject.link" target="_blank" class="detailsBtn">
                        Voir sur GitHub
                    </a>
                </div>
            </div>
        </div>
    </div>
</template>
<script setup>
import ProjectCard from "./ProjectCard.vue";
import { computed, onMounted, reactive, ref, watch } from 'vue';

const projects = reactive([
    {
        title: "Mini-Twitter",
        category: "Web App / Backend",
        description: "Application web simulant un réseau social type Twitter avec publications et abonnements.",
        date: "23-10-2025",
        technologies: ["PHP", "Symfony", "MySQL", "HTML", "CSS", "JavaScript"],
        link: "https://github.com/KyllianLerousseau/mini-twitter",
        image: "img/Mini-Twitter.png",
    },
    {
        title: "Projet-React",
        category: "Frontend / React",
        description: "Application développée avec React comme base de projet front-end moderne.",
        date: "06-11-2025",
        technologies: ["React", "JavaScript", "HTML", "CSS", "Expo"],
        link: "https://github.com/KyllianLerousseau/projet-react",
        image: "img/Projet-React.png"
    },
    {
        title: "Projet-MVC",
        category: "Backend / MVC",
        description: "Projet utilisant une architecture MVC pour structurer une application web.",
        date: "15-10-2025",
        technologies: ["PHP", "MySQL", "HTML", "CSS", "JavaScript"],
        link: "https://github.com/KyllianLerousseau/projet-MVC",
        image: "img/E-commerce.png"
    },
    {
        title: "Site de recettes",
        category: "Web / Frontend",
        description: "Site de recettes de cuisine listant des recettes avec filtrage et affichage d’articles.",
        date: "03-10-2025",
        technologies: ["HTML", "CSS", "JavaScript", "PHP"],
        link: "https://github.com/KyllianLerousseau/Site-recettes",
        image: "img/Site-recettes.png"
    },
    {
        title: "Horloge Javascript",
        category: "Frontend / JavaScript",
        description: "Horloge numérique en JavaScript permettant d’afficher l'heure en temps réel.",
        date: "04-03-2025",
        technologies: ["JavaScript", "HTML", "CSS"],
        link: "https://github.com/KyllianLerousseau/javascript-horloge",
        image: "img/Horloge.png"
    },
    {
        title: "Calculatrice Javascript",
        category: "Frontend / JavaScript",
        description: "Calculatrice simple implémentée en JavaScript pour les opérations de base.",
        date: "04-03-2025",
        technologies: ["JavaScript", "HTML", "CSS"],
        link: "https://github.com/KyllianLerousseau/javascript-calculatrice",
        image: "img/Calculatrice.png"
    }
]);


const selectedCategory = ref("");
const selectedProject = ref(null);

const categories = computed(() => [...new Set(projects.map((p) => p.category))]);

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

function openModal(project) {
    selectedProject.value = project;
    document.body.style.overflow = "hidden";
}

function closeModal() {
    selectedProject.value = null;
    document.body.style.overflow = "auto";
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

@media (max-width: 1200px) {
    .cards {
        grid-template-columns: repeat(3, 1fr);
    }
}

@media (max-width: 900px) {
    .cards {
        grid-template-columns: repeat(2, 1fr);
        gap: 10px;
    }

    .responsive {
        margin-top: 35%;
        padding-right: 20px;
    }
}

@media (max-width: 600px) {
    .cards {
        grid-template-columns: 1fr;
        gap: 10px;
    }

    .responsive {
        margin-top: 40%;
        padding-right: 20px;
    }
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

.modal-backdrop {
    position: fixed;
    inset: 0;
    background-color: rgba(15, 23, 42, 0.9);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 50;
    backdrop-filter: blur(4px);
}

.modal {
    background-color: #1e293b;
    border: 2px solid var(--neutral-light);
    color: var(--text-light);
    border-radius: 12px;
    max-width: 600px;
    width: 90%;
    padding: 25px;
    position: relative;
    animation: appear 0.4s ease forwards;
}

.modal-image-container {
    padding-top: 5px;
    width: 100%;
    display: flex;
    justify-content: center;
    margin-bottom: 15px;
}

.modal-image {
    width: 100%;
    max-height: 250px;
    object-fit: cover;
    border-radius: 8px;
}

.close-btn {
    background-color: var(--secondary);
    border: 2px solid var(--neutral-light);
    color: var(--text-light);
    border-radius: 8px;
    border: none;
    padding: 6px 10px;
    outline: none;
    font-size: 18px;
    cursor: pointer;
}

.close-btn:hover {
    background-color: var(--accent);
    color: var(--text-dark);
}

.tech-container {
    margin-top: 1rem;
    text-align: center;
}

.tech-container h3 {
    font-size: 1.1rem;
    margin-bottom: 0.5rem;
    color: var(--text-light);
    padding: 8px;
}

.tech-list {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 0.5rem;
    padding-bottom: 16px;
}

.tech-badge {
    background-color: var(--primary-dark);
    color: var(--accent);
    padding: 5px 10px;
    border-radius: 20px;
    font-size: 0.9rem;
    font-weight: 500;
    cursor: default;
}

.detailsBtn {
    text-decoration: underline;
    color: var(--accent);
    padding-top: 10px;
    font-weight: bold;
    font-size: 1.5rem;
}

.detailsBtn:hover {
    color: var(--text-light);
}

@media (max-width: 600px) {
    .modal {
        width: 90%;
        padding: 15px;
    }

    .project-card {
        max-width: 100%;
        padding: 12px;
    }

    .detailsBtn {
        font-size: 0.9rem;
        padding: 6px 8px;
    }

    .tech {
        font-size: 0.7rem;
        padding: 2px 6px;
    }
}
</style>
