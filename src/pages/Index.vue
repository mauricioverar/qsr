<template>
  <div class="q-pa-md q-gutter-sm">
    <q-btn outline rounded color="primary" label="Elija - piedra, papel o tijera" />
    <br>
    <q-btn @click="piedra" class="glossy" round color="primary" icon="las la-hand-rock" size="xl" />
    <q-btn @click="papel" class="glossy" round color="secondary" icon="las la-hand-paper" size="xl"/>
    <q-btn @click="tijera" class="glossy" round color="deep-orange" icon="las la-hand-scissors" size="xl"/>
  </div>
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
