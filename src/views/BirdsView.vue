<template>
  <main>
    <h1 class="title-bird">Aves de Guatemala</h1>
    <div class="content">
      <Box v-for="(item, index) in data" :key="index" 
      :family="item.sp"
      :name="item.gen + ' '+item.sp"
      :explorer="item.rec"
      :location="item.loc"
      :linkImage="item.sono.small"
      :audioSrc="item.file"
      />
    </div>
  </main>
</template>

/*************** SCRIPT ******************/
<script setup>
import { ref, onMounted } from 'vue';
import Box from '@/components/Box.vue';

// URL de la API
const API_URL = 'https://xeno-canto.org/api/2/recordings?query=cnt:guatemala';

// Datos reactivos
const data = ref([]);

// Función para obtener los datos
async function fetchData() {
  try {
    const response = await fetch(API_URL);
    if (!response.ok) {
      throw new Error('Error en la respuesta del servidor');
    }
    const jsonData = await response.json();
      data.value = jsonData.recordings; 
    } catch (error) {
    console.error('Se produjo el siguiente error: ', error);
  }
}


onMounted(async () => {
  await fetchData();
  console.log('Datos después de la asignación:', data.value); // Ver los datos después de la asignación
}); 
</script>

<style>
main {
  margin: 0;
  padding: 0;
}

.title-bird {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  background-color: lightgray;
  color: black;
  text-align: center;
  padding: 10px;
  margin: 0;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
  z-index: 1000;
  height: 30px;
  font-size: x-large;
}

.content{
  margin-top: 60px;
  padding: 20px;
}

</style>