<template>
  <q-page padding>
    <h1 class="text-h2">Lista de compras</h1>
    <q-form
      class="row q-col-gutter-md"
      @reset="onReset"
      @submit.prevent="onSubmit"
      ref="myForm"
    >
      <q-input
        label="Producto"
        class="col-12 col-sm-6"
        v-model.trim="producto"
        lazy-rules
        :rules="[(val) => (val && val.length > 0) || 'Campo vacío']"
      />
      <q-select
        label="Prioridad"
        class="col-12 col-sm-6"
        :options="opciones"
        v-model="seleccion"
        lazy-rules
        :rules="[(val) => (val && val.length > 0) || 'Campo vacío']"
      />
      <q-toggle
        label="Aceptar los las condiciones super bknes"
        v-model="condiciones"
        class="col-12"
      />
      <div class="col-12">
        <q-btn label="submit" type="submit" color="primary" />
        <q-btn
          label="reset"
          type="reset"
          color="primary"
          flat
          class="q-ml-sm"
        />
      </div>
    </q-form>
    <!-- <pre>{{productos}}</pre> -->

    <lista-productos :productos="productos" class="q-mt-xl" />
  </q-page>
</template>

<script>
import { useQuasar } from 'quasar'
import ListaProductos from 'src/components/ListaProductos.vue'
import { ref } from 'vue'
export default {
  components: { ListaProductos },
  setup () {
    const $q = useQuasar()
    const myForm = ref(null)

    const productos = ref([])

    const producto = ref(null)
    const seleccion = ref(null)
    const opciones = ['Máxima', 'Moderada', 'Mínima']
    const condiciones = ref(false)

    const onSubmit = () => {
      if (condiciones.value === false) {
        $q.notify({
          color: 'red-5',
          textColor: 'white',
          icon: 'warning',
          message: 'You need to accept the license and terms first'
        })
      } else {
        $q.notify({
          color: 'green-4',
          textColor: 'white',
          icon: 'cloud_done',
          message: 'Submitted'
        })

        myForm.value.resetValidation()

        // procesar el formulario
        // empujar datos(push)
        productos.value = [
          ...productos.value,
          {
            producto: producto.value,
            prioridad: seleccion.value
          }
        ]
        onReset()
      }
    }

    const onReset = () => {
      producto.value = null
      seleccion.value = null
      condiciones.value = false
    }

    return {
      producto,
      seleccion,
      opciones,
      condiciones,
      onSubmit,
      onReset,
      myForm,
      productos
    }
  }
}
</script>
