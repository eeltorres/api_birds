<template>
  <body>
    <h1 class="title">Inicio</h1>
    <h3 class="carne">Carne: 23002910</h3>
    <button class="btn" @click="nextPage">Cargar</button>
  </body>
</template>

<script setup>
import { useRouter } from 'vue-router';

const router = useRouter()
//Función para ir a la siguiente página
const nextPage = () => {
  router.push('/Birds')
}

</script>

<style>
body {
  font-family: 'Lucida Sans';
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
}

.title{
  padding: 50px;
  margin: 80px;
}

.carne{
  padding: 20px;
}

.btn{
  margin: 140px;
  height: 50px;
  width: 100px;
  padding: 10px;
  cursor: pointer;
}
</style>