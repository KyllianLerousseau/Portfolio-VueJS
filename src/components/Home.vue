<template>
    <div class="split">
        <div class="card-01">
            <h1>01</h1>
        </div>
        <div class="contenu-01">
            <div class="photo-container">
            </div>
                <div class="title">
                    <h1>Kyllian Lerousseau</h1>
                    <h2>Concepteur Développeur d'Applications en formation</h2>
                    <p class="description">
                        Passionné par le développement web et mobile, je crée des applications interactives et
                        responsives.
                        Je maîtrise React, JavaScript, PHP et Symfony et je suis à la recherche d’un stage pour mettre
                        mes
                        compétences en pratique.
                    </p>
                </div>
            </div>
    </div>
    <div class="split">
        <div class="contenu-02">
            <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quo reprehenderit quis aliquid vero eaque,
                suscipit delectus quam quisquam cumque officia atque voluptates accusamus sapiente voluptas saepe
                perspiciatis numquam, similique dolor.</p>
        </div>
        <div class="card-02">
            <h1>02</h1>
        </div>
    </div>
    <div class="split">
        <div class="card-03">
            <h1>03</h1>
        </div>
        <div class="contenu-03">

        </div>
    </div>
</template>
<script setup>
</script>
<style scoped>
.card-01 {
    flex: 1;
    background: rgba(255, 255, 255, 0.1);
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 8em;
    border-right: 8px solid var(--primary-dark);
    border-bottom: 8px solid var(--primary-dark);
}

.card-01 h1 {
    text-align: center;
    opacity: 0.6;
    color: var(--text-dark);
    font-weight: bold;
}

.contenu-01 {
    flex: 1;
    padding: 1.5rem;
    display: flex;
    width: 100%;
    color: var(--text-light);
}

.split {
    display: flex;
    height: 80vh;
    width: 100%;
}

.photo-container {
    padding-top: 5px;
    display: flex;
    width: 150px;
    height: 150px;
    background: rgba(255, 255, 255, 0.1);
    border: 3px solid var(--primary-dark);
}

.title {
    flex: 1;
    text-align: center;
    padding-top: 8px;
}

.description {
    padding-left: 20px;
    text-align: left;
}

.contenu-02 {
    flex: 1;
    padding: 1.5rem;
    display: flex;
    width: 100%;
    color: var(--text-light);
}

.card-02 {
    flex: 1;
    background: rgba(255, 255, 255, 0.1);
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 3rem;
    font-size: 8em;
    border-left: 8px solid var(--primary-dark);
    border-top: 8px solid var(--primary-dark);
    border-bottom: 8px solid var(--primary-dark);
}

.card-02 h1 {
    text-align: center;
    opacity: 0.6;
    color: var(--text-dark);
    font-weight: bold;
}

.card-03 {
    flex: 1;
    background: rgba(255, 255, 255, 0.1);
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 8em;
    border-right: 8px solid var(--primary-dark);
    border-top: 8px solid var(--primary-dark);
}

.card-03 h1 {
    text-align: center;
    opacity: 0.6;
    color: var(--text-dark);
    font-weight: bold;
}

.contenu-03 {
    flex: 1;
    padding: 1.5rem;
    display: flex;
    width: 100%;
    color: var(--text-light);
}
</style>