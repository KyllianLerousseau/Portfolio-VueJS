<template>
    <h1>Niveau de compétences</h1>
    <div class="skills">
        <SkillBadge v-for="(skill, index) in skills" :title="skill.title" :img="skill.img" :key="index"
            :class="{ on: activeIndexes.includes(index) }"
            :progress="skill.progress" />
    </div>

</template>
<script setup>
import { onMounted, ref } from 'vue';
import SkillBadge from './SkillBadge.vue';

const skills = ref([
    { title: 'HTML', progress: 90, img: '/img/HTML.png' },
    { title: 'CSS', progress: 60, img: '/img/CSS.png' },
    { title: 'Javascript', progress: 50, img: '/img/Javascript.png' },
    { title: 'VueJS', progress: 40, img: '/img/VueJS.png' },
    { title: 'NodeJS', progress: 30, img: '/img/NodeJS.png' },
    { title: 'PHP', progress: 55, img: '/img/PHP.png' },
    { title: 'Symfony', progress: 60, img: '/img/Symfony.png' },
    { title: 'ReactJS & React-Native', progress: 50, img: '/img/ReactJS.png' },
    { title: 'MySQL', progress: 70, img: '/img/MySQL.png' }
]);

const activeIndexes = ref([]);

function animationCards() {
    activeIndexes.value = [];

    skills.value.forEach((_, index) => {
        setTimeout(() => {
            activeIndexes.value.push(index);
        }, (index + 1) * 100)
    })
}

onMounted(() => {
    animationCards();
});
</script>
<style scoped>
.skills {
    display: grid;
    padding: 10px 20px;
    grid-template-columns: repeat(4, 1fr);
    gap: 20px 0px;

}

h1 {
    text-align: center;
    color: var(--text-light);
    font-weight: bold;
}

@media (max-width: 1200px) {
    h1 {
        margin-top: 40%;
    }
    .skills {
        grid-template-columns: repeat(3, 1fr);
    }
}

@media (max-width: 600px) {
    .skills {
        grid-template-columns: 1fr;
        gap: 15px;
        padding: 10px;
    }
}

@media (max-width: 600px) {
    .skills {
        grid-template-columns: 1fr;
        gap: 15px;
        padding: 10px;
    }
}

</style>