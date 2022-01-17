<template>
  <q-page padding>
    <div class="q-pa-md q-gutter-sm">
    <q-btn outline rounded color="primary" label="Elija - piedra, papel o tijera" />
    <br>
    <q-btn @click="rock" :id="piedra" round color="primary" :icon="piedra" size="xl" />
    <q-btn @click="paper" class="glossy" round color="secondary" :icon="papel" size="xl"/>
    <q-btn @click="scissors" class="glossy" round color="deep-orange" :icon="tijera" size="xl"/>
    <br>
    <br>
    <br>

    <h6>Usuario: {{us}}</h6>
    <h6>Máquina: {{mak}}</h6>
    <!-- <pre>{{icono}}</pre> -->

    <q-btn outline rounded color="primary" label="Máquina elije " />
    <q-btn v-if="computa" class="glossy" round :icon="icono" size="xl" />

    <h4 id="resultado" ></h4>
  </div>
  </q-page>
</template>

<script>
import { ref } from 'vue'
export default {
  setup () {
    const piedra = 'las la-hand-rock'
    const papel = 'las la-hand-paper'
    const tijera = 'las la-hand-scissors'
    const icono = ref(null)
    const us = ref(null)
    const mak = ref(null)

    const computa = () => {
      const pc = parseInt(Math.random() * (4 - 1) + 1)

      switch (pc) {
        case 1:
          icono.value = piedra // usar .value
          break
        case 2:
          icono.value = papel
          break
        case 3:
          icono.value = tijera
          break
        default:
          break
      }
    }

    const rock = () => {
      computa()

      if (icono.value === papel) {
        mak.value += 1
      } else if (icono.value === tijera) {
        us.value += 1
      }
    }

    const paper = () => {
      computa()

      if (icono.value === tijera) {
        mak.value += 1
      } else if (icono.value === piedra) {
        us.value += 1
      }
    }

    const scissors = () => {
      computa()

      if (icono.value === piedra) {
        mak.value += 1
      } else if (icono.value === papel) {
        us.value += 1
      }
    }

    return {
      computa,
      icono,
      piedra,
      papel,
      tijera,
      rock,
      paper,
      scissors,
      us,
      mak
    }
  }
}
</script>
