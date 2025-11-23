<template>
  <div class="q-pa-md" style="max-width: 400px">

    <q-form
      @submit="onSubmit"
      @reset="onReset"
      class="q-gutter-md"
    >
      <q-input
        filled
        v-model="name"
        label="email"
        hint="email adresa"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Molimo da unesete svoju email adresu']"
      />

      <q-input
        filled
        type="lozinka"
        v-model="age"
        label="lozinka"
        lazy-rules
        :rules="[
          val => val !== null && val !== '' || 'Molimo da unesete svoju lozinku',
          val => val > 0 && val < 100 || 'Molimo da unesete svoju lozinku'
        ]"
      />

      

      <div>
        <q-btn label="Prijavi se" type="Prijavi se" color="primary"/>
        
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

