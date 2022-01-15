<template>
  <q-page padding class="q-ml-xs">
    <h4 class="q-ml-xl q-pl-xl">Juegos</h4>
    <q-btn
    label="Cachipún"
    color="secondary"
    outline
    class="q-ml-xs"
    to="/cachipun"
    icon="content_cut"
    />
    <q-btn
    label="Gato"
    color="secondary"
    outline
    class="q-ml-xs"
    to="/gato"
    icon="highlight_off"
    />
    <q-btn
    label="Puzzle"
    color="secondary"
    outline
    class="q-ml-xs"
    to="/puzzle"
    icon="exit_to_app"
    />
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'PageIndex',
  setup () {
    return {
      piedra () {
        console.log('piedra')
      },
      papel () {
        console.log('papel')
      },
      tijera () {
        console.log('tijera')
      },
      computador () {
        console.log('computador')
      }
    }
  }
})
</script>
