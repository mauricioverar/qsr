<template>
<pre>{{productos}} </pre>
  <q-table
    title="Productos"
    :columns="columns"
    :rows="productos"
    no-data-label="Sin productos para mostrar"
  />
  <!-- <pre>{{productos}}</pre> -->
</template>

<script>
const columns = [
  {
    name: 'producto',
    align: 'left',
    label: 'Producto',
    field: 'producto',
    sortable: true
  },
  { name: 'prioridad', label: 'Prioridad', field: 'prioridad', sortable: true }
]

const row = [
  {
    producto: 'fsad',
    prioridad: 'Máxima'
  }
]
export default {
  props: {
    productos: Array
  },
  setup () {
    return {
      columns,
      row
    }
  }
}
</script>
