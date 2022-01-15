<template>
  <div class="q-pa-md q-gutter-sm">
    <q-btn outline rounded color="primary" label="Elija - piedra, papel o tijera" />
    <br>
    <q-btn @click="piedra" class="glossy" round color="primary" icon="las la-hand-rock" size="xl" />
    <q-btn @click="papel" class="glossy" round color="secondary" icon="las la-hand-paper" size="xl"/>
    <q-btn @click="tijera" class="glossy" round color="deep-orange" icon="las la-hand-scissors" size="xl"/>
    <br>
    <h6>Usuario: </h6>
    <h6>Máquina: </h6>

    <q-btn outline rounded color="primary" label="Máquina elije " />
    <q-btn v-show="show" class="glossy" round :icon="icono" size="xl" />

    <h4 id="resultado" ></h4>

    <q-dialog v-model="alert">
      <q-card>
        <q-card-section>
          <div class="text-h6">Alert</div>
        </q-card-section>

        <q-card-section class="q-pt-none">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Rerum repellendus sit voluptate voluptas eveniet porro. Rerum blanditiis perferendis totam, ea at omnis vel numquam exercitationem aut, natus minima, porro labore.
        </q-card-section>

        <q-card-actions align="right">
          <q-btn flat label="OK" color="primary" v-close-popup />
        </q-card-actions>
      </q-card>
    </q-dialog>
  </div>
</template>

<script>
import { defineComponent } from 'vue'
// import { mdiAbTesting } from '@quasar/extras/mdi-v6'

export default defineComponent({
  name: 'PageIndex',
  alert: false,
  // show: 'false',
  created () {
    // this.icono = 'las la-hand-scissors'
    const pc = parseInt(Math.random() * (4 - 1) + 1)
    let pcmano = 0
    switch (pc) {
      case 1:
        pcmano = 'piedra'
        this.icono = 'las la-hand-rock'
        break
      case 2:
        pcmano = 'papel'
        this.icono = 'las la-hand-paper'
        break
      case 3:
        pcmano = 'tijera'
        console.log(pcmano)
        this.show = 'true'
        this.icono = 'las la-hand-scissors'
        break
      default:
        alert('falla')
        break
    }
    console.log(pcmano)
  },
  computed () {
    console.log('a')
  },
  setup () {
    return {
      piedra () {
        let show = 'false'
        console.log(show)
        document.getElementById('resultado').innerHTML = ''
        console.log('piedra')
        const mano = 'piedra'
        const pc = parseInt(Math.random() * (4 - 1) + 1)
        let pcmano = 0
        switch (pc) {
          case 1:
            pcmano = 'piedra'
            break
          case 2:
            pcmano = 'papel'
            break
          case 3:
            pcmano = 'tijera'
            break
          default:
            alert('falla')
            break
        }
        console.log(pc)
        console.log('maquina saca', pcmano)
        show = 'true'
        show = this.show
        console.log(show)
        if (pcmano === mano) {
          console.log('empate')
        }
      },
      papel () {
        document.getElementById('resultado').innerHTML = ''
        console.log('papel')
        const mano = 'papel'
        const pc = parseInt(Math.random() * (4 - 1) + 1)
        let pcmano = 0
        let icono = ''
        switch (pc) {
          case 1:
            pcmano = 'piedra'
            break
          case 2:
            pcmano = 'papel'
            break
          case 3:
            pcmano = 'tijera'
            icono = 'las la-hand-scissors'
            console.log(icono)
            break
          default:
            alert('falla')
            break
        }
        console.log(pc)
        console.log('maquina saca', pcmano)
        if (pcmano === mano) {
          console.log('empate')
          document.getElementById('resultado').innerHTML = 'empate'
        }
      },
      tijera () {
        document.getElementById('resultado').innerHTML = ''
        console.log('tijera')
        const mano = 'tijera'
        const pc = parseInt(Math.random() * (4 - 1) + 1)
        let pcmano = 0
        switch (pc) {
          case 1:
            pcmano = 'piedra'
            break
          case 2:
            pcmano = 'papel'
            break
          case 3:
            pcmano = 'tijera'
            break
          default:
            alert('falla')
            break
        }
        console.log(pc)
        console.log('maquina saca', pcmano)
        if (pcmano === mano) {
          console.log('empate')
        }
      },
      computador () {
        console.log('computador')
        if (this.computador.value !== true) {
          console.log('computador')
        }
      }
    }
  }
})
</script>
