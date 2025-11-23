<template>
  <div class="q-pa-md" style="max-width: 400px">

    <q-form
      @submit="onSubmit"
      @reset="onReset"
      class="q-gutter-md"
    >
      <q-input
        filled
        v-model="ime"
        label="Ime"
        
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Molimo da unesete ime']"
      />

      <q-input
        filled
        type="Prezime"
        v-model="Prezime"
        label="Prezime"
        lazy-rules
        :rules="[
          val => val !== null && val !== '' || 'Molimo da unesete prezime',
          
        ]"
      />

      <q-input
        filled
        type="Email adresa"
        v-model="email"
        label="Email adresa"
        lazy-rules
        :rules="[
          val => val !== null && val !== '' || 'Molimo da unesete email adresu',
         
        ]"
      />

      <q-input
        filled
        type="Lozinka"
        v-model="lozinka"
        label="Lozinka"
        lazy-rules
        :rules="[
          val => val !== null && val !== '' || 'Molimo da kreirate lozinku',
          val => val > 0 && val < 100 || 'Molimo da unesete lozinku'
        ]"
      />

      

      <div>
        <q-btn label="Registriraj se" type="registracija" color="primary"/>
       
      </div>
    </q-form>

  </div>
</template>


<script>
import { useQuasar } from 'quasar'
import { ref } from 'vue'

export default {
  setup () {
    const $q = useQuasar()

    const name = ref(null)
    const age = ref(null)
    const accept = ref(false)

    return {
      name,
      age,
      accept,

      onSubmit () {
        if (accept.value !== true) {
          $q.notify({
            color: 'red-5',
            textColor: 'white',
            icon: 'warning',
            message: 'You need to accept the license and terms first'
          })
        }
        else {
          $q.notify({
            color: 'green-4',
            textColor: 'white',
            icon: 'cloud_done',
            message: 'Submitted'
          })
        }
      },

      onReset () {
        name.value = null
        age.value = null
        accept.value = false
      }
    }
  }
}
</script>