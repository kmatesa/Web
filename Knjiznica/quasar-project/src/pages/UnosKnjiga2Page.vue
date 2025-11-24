<template>
  <q-page padding>
    <!-- content -->
     <q-form class="q-gutter-md">

     </q-form>
  </q-page>
</template>

<script setup>
import {re} from 'vue'
import axios from 'axios'

async function insertBook(){
  let formData = {
    "naslov": naslov.value,
    "autor": autor.value,
    "opis": opis.value,
    "slika":slika.value,
    "stanje": stanje.value
  }

  console.log("test"+formData.autor)
  await axios.post('http://localhost:3000/api/unos/knjige/id', formData)
  .then(result => {
    console.log(result)
  })
  .catch(error => {
    console.log(error)
  })
}
</script>
