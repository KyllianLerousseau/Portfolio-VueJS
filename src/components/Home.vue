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
                    responsives.<br>
                    <br>
                    Je maîtrise VueJs, JavaScript, PHP, MySQL et Symfony et je suis à la recherche d’un stage pour mettre
                    mes
                    compétences en pratique.<br>
                </p>
            </div>
        </div>
    </div>
    <div class="split">
        <div class="contenu-02">
        </div>
        <div class="card-02">
            <h1>02</h1>
        </div>
    </div>
</template>
<script setup>
</script>
<style scoped>
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
    flex-direction: column;
    width: 100%;
    color: var(--text-light);
}

.split {
    display: flex;
    height: 80vh;
    width: 100%;
    margin-top: 20px;
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
    text-align: left;
    padding-top: 18px;
}

.description {
    text-align: left;
    font-size: 22px;
}

.contenu-02 {
    flex: 1;
    padding: 1.5rem;
    display: flex;
    width: 100%;
    color: var(--text-light);
}

.card-01,
.card-02 {
    flex: 1;
    background: rgba(255, 255, 255, 0.1);
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 8em;
    border: 8px solid var(--primary-dark);
    padding: 2rem;
    box-sizing: border-box;
}

.card-02 h1 {
    text-align: center;
    opacity: 0.6;
    color: var(--text-dark);
    font-weight: bold;
}

@media (max-width: 768px) {
    .split {
        flex-direction: column;
        gap: 1.5rem;
        margin-top: 40%;
        width: 100%;
    }

    .card-01,
    .card-02 {
        font-size: 4em;
        padding: 1.5rem;
        width: 100%;
        border-left: none;
        border-right: none;
        border: 8px solid var(--primary-dark);
    }

    .contenu-01,
    .contenu-02 {
        flex-direction: column;
        padding: 1rem;
        width: 100%;
        box-sizing: border-box;
    }

    .description {
        padding-left: 0;
        padding-right: 0;
        text-align: center;
        word-wrap: break-word;
    }

    .photo-container {
        width: 100px;
        height: 100px;
        margin-bottom: 1rem;
    }
}
</style>