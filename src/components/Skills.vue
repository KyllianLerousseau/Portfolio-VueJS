<template>
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
    { title: 'CSS', progress: 80, img: '/img/CSS.png' },
    { title: 'Javascript', progress: 70, img: '/img/Javascript.png' },
    { title: 'VueJS', progress: 32, img: '/img/VueJS.png' },
    { title: 'NodeJS', progress: 20, img: '/img/NodeJS.png' },
    { title: 'PHP', progress: 65, img: '/img/PHP.png' },
    { title: 'PHP Symfony', progress: 60, img: '/img/Symfony.png' },
    { title: 'ReactJS & React-Native', progress: 30, img: '/img/ReactJS.png' },
    { title: 'MySQL', progress: 60, img: '/img/MySQL.png' }
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


</style>