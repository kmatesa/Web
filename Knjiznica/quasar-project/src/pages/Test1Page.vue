<template>
  <q-page padding>
    <div class="q-pa-md q-gutter-sm">
    <q-btn push color="white" text-color="primary" label="Unread Mails">
      <q-badge color="orange" v-model="unread" floating>{{ unread }}</q-badge>
    </q-btn>

    <q-btn dense color="purple" round icon="email" class="q-ml-md">
      <q-badge color="red" v-model="open" floating>{{ open }}</q-badge>
    </q-btn>

     <q-card class="my-card bg-secondary text-white" v-for="item in msg" :key="item">
      <q-card-section>
        <div class="text-h6"> {{ item.title }}</div>
        <div class="text-subtitle2">by {{item.author}}</div>
      </q-card-section>

      <q-card-section>
        {{item.text }}
      </q-card-section>

      <q-separator dark />

      <q-card-actions>
        <q-btn flat @click="openMsg()">Open</q-btn>
        <q-btn flat @click="deleteMsg()">Delete</q-btn>
      </q-card-actions>
    </q-card>
  </div>
 <div class="q-gutter-md" style="max-width: 300px">
   <q-input v-model="title" label="Title" />
    <q-input v-model="author" label="Author" />
     <q-input v-model="text" label="Text" />
     <q-btn flat @click="save()">Save</q-btn>
</div>
  </q-page>
</template>

<script setup>
//

import {ref} from 'vue'

const msg = [
  {
    title:'Changing planet',
    author:'John Doe',
    text:'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.'
  },
   {
    title:'New planet',
    author:'Johnny Doe',
    text:'Lorem ipsum.'
  }, 
  {
    title:'New update',
    author:'Doe',
    text:'Lorem.'
  }
]

let unread = ref(22)
let open = ref(4)
let title=ref('')
let author=ref('')
let text=ref('')

function openMsg(){
  open.value -= 1 


console.log("Open "+open.value)


}

function deleteMsg(){
  unread.value -= 1 
console.log("Delete "+unread.value)

}

function save(){
 
  msg.push({title:title.value, author:author.value, text:text.value})
   console.log(msg)
}

</script>

<style lang="sass" scoped>
.my-card
  width: 100%
  max-width: 250px
</style>