<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn flat dense round icon="menu" aria-label="Menu" @click="toggleLeftDrawer" />

        <q-toolbar-title> Quasar aplikacija Knjiznica </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <q-item-label header> Essential Links </q-item-label>

        <EssentialLink v-for="link in linksList" :key="link.title" v-bind="link" />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [


  {
    title: 'Knjižnica',
    caption: 'Knjižnica - početna stranica',
    icon: 'local_library',
    link: '#/',
  },
  {
    title: 'Knjižnica - nove knjige',
    caption: 'Popis novih dostupnih knjiga u knjižnici',
    icon: 'library_books',
    link: '#/PopisNovihKnjiga',
  },

  {
    title: 'Knjižnica - popis knjiga',
    caption: 'Popisdostupnih knjiga u knjižnici',
    icon: 'book',
    link: '#/PopisKnjiga',
  },

  {
    title: 'Pretraživanje',
    caption: 'Pretraživanje knjiga',
    icon: 'search',
    link: '#/Pretrazivanje',
  },
  {
    title: 'Lokacija',
    caption: 'Lokacija',
    icon: 'location_on',
    link: '#/Lokacija',
  },
  {
    title: 'Login',
    caption: 'Login',
    icon: 'person',
    link: '#/Login',
  },
  {
    title: 'Registracija',
    caption: 'Registracija',
    icon: 'person',
    link: '#/Registracija',
  },

  {
    title: 'TEST',
    caption: 'Test',
    icon: 'person',
    link: '#/Test',
  },
{
    title: 'TEST1',
    caption: 'Test1',
    icon: 'person',
    link: '#/Test1',
  },
  {
    title: 'Unos knjiga',
    caption: 'Unos novih knjiga',
    icon: 'book',
    link: '#/UnosKnjiga',
  },
  {
    title: 'Unos knjiga2',
    caption: 'Unos novih knjiga',
    icon: 'book',
    link: '#/UnosKnjiga2',
  },


  {
    title: 'Docs',
    caption: 'quasar.dev',
    icon: 'school',
    link: 'https://quasar.dev',
  },
  {
    title: 'Github',
    caption: 'github.com/quasarframework',
    icon: 'code',
    link: 'https://github.com/quasarframework',
  },
  {
    title: 'Discord Chat Channel',
    caption: 'chat.quasar.dev',
    icon: 'chat',
    link: 'https://chat.quasar.dev',
  },
  {
    title: 'Forum',
    caption: 'forum.quasar.dev',
    icon: 'record_voice_over',
    link: 'https://forum.quasar.dev',
  },
  {
    title: 'Twitter',
    caption: '@quasarframework',
    icon: 'rss_feed',
    link: 'https://twitter.quasar.dev',
  },
  {
    title: 'Facebook',
    caption: '@QuasarFramework',
    icon: 'public',
    link: 'https://facebook.quasar.dev',
  },
  {
    title: 'Quasar Awesome',
    caption: 'Community Quasar projects',
    icon: 'favorite',
    link: 'https://awesome.quasar.dev',
  },
  {
    title: 'GitHub knjiznica',
    caption: 'GitHub projekt knjiznica',
    icon: 'library_books',
    link: 'https://github.com/kmatesa/Knjiznica.git',
  },
  {
    title: 'Veleuciliste u Rijeci',
    caption: 'Poveznica za web stranicu VeleRi',
    icon: 'school',
    link: 'https://veleri.hr/hr',
  },
]

const leftDrawerOpen = ref(false)

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value
}
</script>
