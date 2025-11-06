<template>
    <div class="skill-badge">
        <h3>{{ title }}</h3>
        <img :src="img" :alt="title" class="skill-icon">
        <div class="progress-bar">
            <div class="progress" :style="{ width: progress + '%' }"></div>
        </div>
    </div>
</template>
<script setup>

defineProps({
    title: String,
    img: String,
    progress: Number,
});

</script>
<style scoped>
.skill-badge {
    width: 250px;
    height: 200px;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1rem;
    padding: 12px;
    background-color: #0f172ad0;
    color: var(--text-light);
    border-radius: 8px;
    opacity: 0;
    transform: translateY(10px) scale(0.7);
    transition: opacity 0.4s ease, transform 0.7s ease;
}

.skill-badge.on {
    transform: translate(0) scale(1);
    opacity: 1;
}

.skill-icon {
    height: 80px;
    object-fit: contain;
}

.progress-bar {
    width: 100%;
    height: 12px;
    background-color: #eee;
    border-radius: 5px;
    overflow: hidden;
}

.progress {
    height: 100%;
    background-image: linear-gradient(to top, #30cfd0 0%, #330867 100%);
    background-repeat: no-repeat;

}
</style>