<template>
    <div class="container">
        <div class="text-container">
            <h2>A propos de moi</h2>
            <p class="text">je suis Kyllian Lerousseau, développeur full-stack en formation de Concepteur Développeur
                d’Applications.</p>


            <p class="text">Passionné par le développement web et mobile, j'aime créer des applications interactives et
                responsives
                qui
                offrent une expérience utilisateur fluide et intuitive.</p>

            <p class="text">
                Je travaille principalement avec React et JavaScript pour le front-end, et PHP avec Symfony pour le
                back-end, tout en maîtrisant les bases de données MySQL et les architectures MVC.
            </p>

            <p class="text">
                Au fil de mes projets personnels et professionnels: mini-réseaux sociaux, sites de recettes,
                calculatrices
                et horloges interactives, j’ai renforcé ma créativité, ma rigueur et ma capacité à résoudre des
                problèmes
                techniques concrets.
            </p>

            <p class="text">
                Je suis à la recherche d’un stage ou d’opportunités stimulantes pour mettre mes compétences en pratique,
                contribuer à des projets concrets et continuer à apprendre en tant que développeur.
            </p>

        </div>
    </div>
</template>
<script setup>
</script>
<style scoped>
.container {
    display: flex;
    align-items: center;
    justify-content: center;

}

.text-container {
    padding: 10px;
    width: 100%;
    height: 400px;
    border: 2px solid var(--neutral-light);
    color: var(--accent);
}

.text-container h2 {
    text-decoration: underline;
}

.text {
    font-size: 22px;
}
</style>