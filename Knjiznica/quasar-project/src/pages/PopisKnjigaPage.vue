<template>
  <div class="q-pa-md">
    <q-table
      title="Popis svih knjiga"
      :rows="rows"
      :columns="columns"
      row-key="name"
    />
  </div>

</template>

<script>
const columns = [
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

export default {
  setup () {
    return {
      columns,
      rows
    }
  }
}
</script>