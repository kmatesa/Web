<template>

   <q-toolbar class="bg-blue-9 text-white">
      <q-toolbar-title>Pretraživanje knjiga</q-toolbar-title>
     </q-toolbar>

<div class="q-pa-md">
    <div class="q-gutter-md" style="max-width: 300px">
      <q-input v-model="text" label="Pretraživanje" />

    
  <div class="q-pa-md">
    <div class="q-gutter-sm">
      <q-checkbox dense v-model="teal" label="po nalov" color="teal" />
       <q-checkbox dense v-model="teal" label="po autoru" color="teal" />
 </div>
  </div>
      <div class="q-pa-md q-gutter-sm">
    <q-btn color="blue" text-color="white" label="Traži" />
 </div>

 
      </div>
        </div>
 
</template>


<script>
import { ref } from 'vue'

export default {
  setup () {
    return {
      teal: ref(true)}}}
</script>