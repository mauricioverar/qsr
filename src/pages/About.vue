<template>
  <div class="q-pa-md" style="max-width: 400px">

      <pre>{{name}} - {{seleccion}} - {{accept}}</pre>

    <!-- <q-form
      @submit="onSubmit"
      @reset="onReset"
      class="q-gutter-md"
    > -->
    <q-form
      @submit="onSubmit"
      @reset="reset"
      class="q-gutter-md"
      ref="myForm"
    >
      <q-input
        filled
        v-model="name"
        label="Nombre *"
        hint="Nombre"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Ingresar nombre']"
      />

      <div class="col-12 col-sm-6">
          <q-select
          v-model="seleccion"
          label="Prioridad"
          :options="opciones"
          lazy-rules
          :rules="[ val => val && val.length > 0 || 'seleccionar']"
          ></q-select>
      </div>

      <q-input
        filled
        type="number"
        v-model="age"
        label="Edad *"
        lazy-rules
        :rules="[
          val => val !== null && val !== '' || 'Ingresar edad',
          val => val > 0 && val < 100 || 'Ingresar edad real'
        ]"
      />

      <q-toggle v-model="accept" label="Acepto términos y licencia" />

      <div>
        <q-btn label="Submit" type="submit" color="primary"/>
        <q-btn label="Reset" type="reset" color="primary"
        outline
        class="q-ml-sm" />
      </div>
    </q-form>
    <tabla-datos />

  </div>
</template>

<script>
import { useQuasar } from 'quasar'
import { ref } from 'vue'
import TablaDatos from 'src/components/TablaDatos.vue'

export default {
  components: { TablaDatos },
  setup () {
    const $q = useQuasar()

    const name = ref(null)
    const age = ref(null)
    const accept = ref(false)
    const seleccion = ref(null)
    const opciones = ['max', 'med', 'min']
    // const productos = ref([])
    const reset = () => { // forma es6
      name.value = null
      age.value = null
      accept.value = false
      seleccion.value = null
    }
    const myForm = ref(null)

    return {
      name,
      age,
      accept,
      seleccion,
      opciones,
      reset,
      myForm,

      onSubmit () {
        if (accept.value !== true) {
          $q.notify({
            color: 'red-5',
            textColor: 'white',
            icon: 'warning',
            message: 'Aceptar términos'
          })
        } else {
          $q.notify({
            color: 'green-4',
            textColor: 'white',
            icon: 'cloud_done',
            message: 'Ingresado'
          })
          myForm.value.resetValidation()
          reset()
          // procesar fomulario
        //   productos.value = [...productos.value, {
        //     producto: producto.value
        //   }]
        }
      }
    /*
    },

      onReset () {
        name.value = null
        age.value = null
        accept.value = false
      }
     */
    }
  }
}
</script>
