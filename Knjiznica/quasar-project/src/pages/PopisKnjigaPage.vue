<template>
  <div class="q-pa-md">
   
    
    <q-table
      flat bordered
      :rows="books"
      :columns="columns"
      row-key="name"
      :wrap-cells="true"
    >
   
    </q-table>
  </div>

</template>

<script setup>

import {ref, onMounted} from 'vue'
import axios from 'axios';
let books = ref([])
onMounted(() => {
  loadBooks()
})
async function loadBooks(){
  await axios.get('http://localhost:3000/api/knjige/')
  .then(result => {
    console.log(result.data)
    books.value = result.data
    console.log(books.value[0].naslov)
  })
  .catch(error => {
    console.error(error)
  })
}

const columns =[
  {name: 'id', label: 'id', field: 'id'},
  {name: 'naslov', aligin: 'centar', label: 'naslov', filed: 'naslov', sortable: true},
  {name: 'autor', label: 'autor', filed:'autor', sortable:true},
  {name:'opis', label:'opis',field:'opis'},
  {name:'slika', label:'slika', field:'slika'},
    {name:'stanje', label:'stanje', field:'stanje'},
  {name:'status', label: 'status',field:'status'}
]

/*const columns = [
  {
    name: 'Knjiga',
    required: true,
    label: 'Knjiga',
    align: 'left',
    field: row => row.name,
    format: val => `${val}`,
    sortable: true,
    style: {
      fontSize:'14px'
    },
    headerStyle: {
      fontSize: '18px'
    }
  },
  { name: 'ID',
    
   label: 'ID', 
   field: 'ID', 
   sortable: true, 
  style: {
      fontSize:'14px'
    },
    headerStyle: {
      fontSize: '18px'
    }
 },
  { name: 'Naslov',
   
   label: 'Naslov',
    field: 'Naslov', 
    sortable: true,
    style: {
      fontSize:'14px'
    },
    headerStyle: {
      fontSize: '18px'
    }
  },
  { name: 'Autor',
   
   label: 'Autor',
    field: 'Autor',
  style: {
      fontSize:'14px'
    },
    headerStyle: {
      fontSize: '18px'
    } },

  { name: 'Opis', 
   
  label: 'Opis',
   field: 'Opis',
  style: {
      fontSize:'14px'
    },
    headerStyle: {
      fontSize: '18px'
    }

  },
  { name: 'Slika',
   
   label: 'Slika',
    field: 'Slika',
  style: {
      fontSize:'14px'
    },
    headerStyle: {
      fontSize: '18px'
    } },

  { name: 'Status',
  
   label: 'Status',
    field: 'Status',
     sortable: true, sort: (a, b) => parseInt(a, 10) - parseInt(b, 10),
    style: {
      fontSize:'14px'
    },
    headerStyle: {
      fontSize: '18px'
    } }
]

const rows = [
  {
    name:'Mali princ',
    ID:'234',
    Naslov:'Mali princ',
    Autor:'jk',
    Opis:'krk',
    Slika:'da',
    Status:'zauzeta'


    
  },
  {
    name: 'Lovac u žitu',
     ID:'234',
    Naslov:'Lovac u zitu',
    Autor:'j.s',
    Opis:'k',
    Slika:'ne',
    Status:'zauzeta'
    
  },
  {
    name: 'Preobrazba',
     ID:'234',
    Naslov:'Preobrazba',
    Autor:'fk',
    Opis:'k',
    Slika:'da',
    Status:'slobodna'

   
  }
  
]
*/
</script>