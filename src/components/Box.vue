<template>
    <div class="main-content">
        <div class="head">
            <img :src=linkImage alt="Aves de Guatemala" @click="playAudio">
        </div>
        <div class="body">
            <p><strong>Familia: </strong>{{ family }}</p>
            <p><strong>Nombre: </strong>{{ name }}</p>
            <p><strong>Ubicación: </strong>{{ location }}</p>
            <p><strong>Descubridor: </strong>{{ explorer }}</p>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        family: String,
        name: String,
        location: String,
        explorer: String,
        linkImage: String,
        audioSrc: String
    },
    methods: {
        playAudio() {
            if (this.audioSrc) {
                const audio = new Audio(this.audioSrc);
                audio.play();
            } else {
                console.warn('No se proporcionó una fuente de audio.');
            }
        },
    },
};

</script>

<style>
.main-content {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    /* height: 120px; */
    width: 92%;
    /* padding: 40px; */
    border: double;
    padding: 5px;
    margin: 4%;
}

.head {
    height: 60%;
}
</style>