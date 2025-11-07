<template>
    <div class="project-card" :class="{ filtre: isVisible }">
        <div class="project-content">
            <h3>{{ project.title }}</h3>
            <p class="category">{{ project.category }}</p>
            <p class="description">{{ project.description }}</p>

            <button class="detailsBtn" @click="$emit('openModal', project)">
                Voir détails
            </button>
        </div>
    </div>
</template>
<script setup>
defineProps({
    project: Object,
    isVisible: Boolean,
});
</script>
<style scoped>
.project-card {
    width: 100%;
    max-width: 300px;
    height: auto;
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

.project-content {
    padding: 15px;
    display: flex;
    flex-direction: column;
    gap: 6px;
}

.category {
    font-weight: bold;
    color: var(--secondary);
}

.tech-list {
    display: flex;
    flex-wrap: wrap;
    gap: 5px;
    margin-top: 8px;
}

.tech {
    background: var(--secondary);
    color: var(--text-dark);
    padding: 2px 8px;
    border-radius: 5px;
    font-size: 0.8rem;
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