<script setup>
import { ref } from 'vue';

let arrayImagenes = ref([])
let buscar = ref()

const accesKey = 'tDmWuSHock3LaL3PHw3p260slWA-Rf5PPVTWa913kEY'
const endPoint = 'https://api.unsplash.com/search/photos'

async function getImages(query) {
  let response = await fetch(endPoint + '?query=' + query + '&client_id=' + accesKey)

  let jsonResponse = await response.json()
  let imagesList = await jsonResponse.results
  createImages(imagesList)
}

function createImages(imagesList) {
  if(arrayImagenes.value !==""){
    arrayImagenes.value = [];
    for (let i = 0; i < imagesList.length; i++) {
    const image = { nombre: null }
    image.nombre = imagesList[i].urls.thumb
    arrayImagenes.value.push(image)
  }
}
  }


</script>

<template>
  <main>
    <p>Numero de imagenes {{ arrayImagenes.length }}</p>
    <input type="text" v-model="buscar" @keyup="getImages(buscar)" />
    <div v-for="(imagen, id) in arrayImagenes" :key="id" class="col-12 col-md-6 col-lg-4">
        <img :src="imagen.nombre" width="300" height="300" alt="Imagen del artista" />
      </div>
  </main>
</template>
