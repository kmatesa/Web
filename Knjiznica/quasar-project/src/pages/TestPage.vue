<template>
  <q-page padding>
    <!-- content -->
     <h1>{{ poruka }}</h1>
     <p v-html="tijelo"></p>
     <p v-html="htmlText"></p>
     <p v-text="htmlText"></p>

     <p v-for="item in days" :key="item">
        <button v-if="item=='Ponedeljak'">
          {{ item }}*
       </button>
       <button v-else-if="item=='Srijeda'" v-show="false">
          {{ item }}
       </button>
          <button v-else>
        {{ item }}
          </button>

          <a :href="link.url" :target="link.target"> {{link.text}} </a>
          <q-input color="purple-12" v-model="text" label="Item name" @keyup="log()"> </q-input>
           <q-input color="pink-12" v-model="text" label="Item name"> </q-input>

     </p>

  </q-page>
</template>

<script setup>

//
const poruka = "Test page"
const tijelo = "Tekst na stranici"
const htmlText="<p><b>Formatirani tekst</b> na stranici </p>"
const days = ['Ponedeljak', 'Utorak', 'Srijeda', 'Cetvrtak', 'Petak', 'Subota', 'Nedelja']

const link = {
url: 'http://www.google.com',
target: '_blank',
text: 'Google'
}

import { ref } from 'vue'
const text = ref('')

text.value = "Hello"


function log(){
  console.log(text.value)
}

</script>
