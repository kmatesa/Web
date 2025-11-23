<template>
  <div class="q-pa-md">
    
    <q-input v-model="textID" label="ID" readonly />
    <q-input v-model="textKnjiga" label="Knjiga" />
    <q-input v-model="textAutor" label="Autor" />
    <q-input v-model="textOpis" label="Opis" />

    
    <q-file
      v-model="file"
      label="Pick one file"
      filled
      style="max-width: 300px"
      @update:model-value="handleFileChange"
    />
 
    <div v-if="imagePreview" style="margin-top:10px; display:flex; justify-content:flex-start;">
      <img :src="imagePreview" alt="Preview" style="max-width:100px; max-height:100px;" />
    </div>

    
    <q-checkbox
      v-model="valSlobodna"
      label="Slobodna"
      inline
      class="q-mr-md"
      @update:model-value="onStatusChange('slobodna')"
    />
    <q-checkbox
      v-model="valZauzeta"
      label="Zauzeta"
      inline
      @update:model-value="onStatusChange('zauzeta')"
    />

    <br />

    <q-btn color="blue" text-color="white" label="Spremi" class="q-mr-sm q-mb-lg" @click="dodajKnjigu" />
    <q-btn color="blue" text-color="white" label="Odustani" class="q-mb-lg" @click="resetirajFormu" />

    
    <div class="q-gutter-md q-mt-lg row wrap">
      <q-card v-for="row in rows" :key="row.ID" class="col-12 col-md-4">
        <q-card-section>
          <div><strong>ID:</strong> {{ row.ID }}</div>
          <div><strong>Knjiga:</strong> {{ row.Naslov }}</div>
          <div><strong>Autor:</strong> {{ row.Autor }}</div>
          <div><strong>Opis:</strong> {{ row.Opis }}</div>
          <div><strong>Slika:</strong></div>
          

          <div class="q-mt-sm" style="display:flex; justify-content:center;">
            <img v-if="row.Slika" :src="row.Slika" alt="Slika" style="max-width:80px; max-height:80px;" />
            <span v-else>-</span>
          </div>
          <div><strong>Status:</strong> {{ row.Status }}</div>
        </q-card-section>
      </q-card>
    </div>

   
    <q-table
      title="Popis svih knjiga"
      :rows="rows"
      :columns="columns"
      row-key="ID"
      class="q-mt-lg"
    >
      <template v-slot:body-cell-Slika="props">
        <q-td style="text-align:center;">
          <img v-if="props.row.Slika" :src="props.row.Slika" alt="Slika" style="max-width:50px; max-height:50px;" />
          <span v-else>-</span>
        </q-td>
      </template>
    </q-table>
  </div>
</template>

<script>
import { ref, reactive } from 'vue'

export default {
  setup() {
    
    const columns = [
      { name: 'ID', label: 'ID', field: 'ID', sortable: true },
      { name: 'Naslov', label: 'Knjiga', field: 'Naslov', sortable: true },
      { name: 'Autor', label: 'Autor', field: 'Autor' },
      { name: 'Opis', label: 'Opis', field: 'Opis' },
      { name: 'Slika', label: 'Slika', field: 'Slika' },
      { name: 'Status', label: 'Status', field: 'Status' }
    ]

    
    const rows = reactive([])

  
    const textID = ref(1)
    const textKnjiga = ref('')
    const textAutor = ref('')
    const textOpis = ref('')
    const file = ref(null)
    const imagePreview = ref(null)

    
    const valSlobodna = ref(false)
    const valZauzeta = ref(false)
    const status = ref('slobodna') 

    const onStatusChange = (selected) => {
      if (selected === 'slobodna') {
        valSlobodna.value = true
        valZauzeta.value = false
        status.value = 'slobodna'
      } else if (selected === 'zauzeta') {
        valSlobodna.value = false
        valZauzeta.value = true
        status.value = 'zauzeta'
      }
    }

    
    const handleFileChange = (f) => {
      if (!f) {
        imagePreview.value = null
        return
      }
      if (f.type.startsWith('image/')) {
        imagePreview.value = URL.createObjectURL(f)
      } else {
        imagePreview.value = null
      }
    }

    const dodajKnjigu = () => {
      rows.push({
        ID: textID.value,
        Naslov: textKnjiga.value,
        Autor: textAutor.value,
        Opis: textOpis.value,
        Slika: imagePreview.value, 
        Status: status.value
      })
      textID.value++
      resetirajFormu()
    }

    const resetirajFormu = () => {
      textKnjiga.value = ''
      textAutor.value = ''
      textOpis.value = ''
      file.value = null
      imagePreview.value = null
      valSlobodna.value = false
      valZauzeta.value = false
      status.value = 'slobodna'
    }

    return {
      columns,
      rows,
      textID,
      textKnjiga,
      textAutor,
      textOpis,
      file,
      imagePreview,
      valSlobodna,
      valZauzeta,
      status,
      onStatusChange,
      handleFileChange,
      dodajKnjigu,
      resetirajFormu
    }
  }
}
</script>
