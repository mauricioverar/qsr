<template>
  <div class="margen">
      <q-btn label="seleccione: " color="accent" size="md" />
      <q-btn v-if="fichaX" @click="x" color="accent" icon="close" size="md" />
      <q-btn v-if="fichaO" @click="o" color="accent" icon="radio_button_unchecked" size="md" />
      <q-btn @click="refresh" color="accent" icon="refresh" size="md" />

      <h6>Máquina: {{mak}} <span>Usuario: {{us}}</span></h6>

      <!-- desaparecer boton -->
      <br>
      <br>
      <br>

    <div class="">
        <q-btn v-if="computa" @click="uno" color="accent" :icon="icono1" size="30px" />
        <q-btn @click="dos" color="accent" :icon="icono2" size="30px" />
        <q-btn @click="tres" color="accent" :icon="icono3" size="30px" />
      </div>
      <div class="">
        <q-btn @click="cuatro" color="accent" :icon="icono4" size="30px" />
        <q-btn @click="cinco" color="accent" :icon="icono5" size="30px" />
        <q-btn @click="seis" color="accent" :icon="icono6" size="30px" />
      </div>
      <div class="">
        <q-btn @click="siete" color="accent" :icon="icono7" size="30px" />
        <q-btn @click="ocho" color="accent" :icon="icono8" size="30px" />
        <q-btn @click="nueve" color="accent" :icon="icono9" size="30px" />
      </div>

      <!-- <q-btn label="Confirm" color="primary" @click="confirm" /> -->

  </div>
</template>

<script>
import { ref } from 'vue'
// import { Dialog } from 'quasar'
import { useQuasar } from 'quasar'

export default {
  setup () {
    const $q = useQuasar()
    let ficha = ''
    const game = false
    let fichaO = ref(null)
    fichaO = true
    let fichaX = true
    const icono9 = ref(null)
    const icono8 = ref(null)
    const icono7 = ref(null)
    const icono6 = ref(null)
    const icono5 = ref(null)
    const icono4 = ref(null)
    const icono3 = ref(null)
    const icono2 = ref(null)
    const icono1 = ref(null)
    let turno = ''
    let cont = 0
    const us = ref(null)
    const mak = ref(null)

    const refresh = () => {
      icono9.value = null
      icono8.value = null
      icono7.value = null
      icono6.value = null
      icono5.value = null
      icono4.value = null
      icono3.value = null
      icono2.value = null
      icono1.value = null
      ficha = ''
      turno = ''
      cont = 0
    }

    const inicio = () => {
      console.log('elija X ó O')
      confirm()
      // alert('inicio')
    }
    const confirm = () => {
      $q.dialog({
        title: 'Confirm',
        message: 'Otra partida?',
        cancel: true,
        persistent: true
      }).onOk(() => {
        console.log('>>>> OK')
        refresh()
      }).onOk(() => {
        // console.log('>>>> second OK catcher')
      }).onCancel(() => {
        // to = "/"
      }).onDismiss(() => {
        // console.log('I am triggered on both OK and Cancel')
      })
    }
    // gana**************************************
    const gana = () => {
      console.log('gana')
      cont += 1
      console.log('cont ', cont)
      if (
        (icono1.value === ficha && icono2.value === ficha && icono3.value === ficha) ||
        (icono4.value === ficha && icono5.value === ficha && icono6.value === ficha) ||
        (icono7.value === ficha && icono8.value === ficha && icono9.value === ficha) ||
        (icono1.value === ficha && icono4.value === ficha && icono7.value === ficha) ||
        (icono2.value === ficha && icono5.value === ficha && icono8.value === ficha) ||
        (icono3.value === ficha && icono6.value === ficha && icono9.value === ficha) ||
        (icono1.value === ficha && icono5.value === ficha && icono9.value === ficha) ||
        (icono3.value === ficha && icono5.value === ficha && icono7.value === ficha)
      ) {
        if (turno === 'pc') {
          console.log('gana usuario')
          us.value += 1
        } else {
          console.log('gana makina')
          mak.value += 1
        }
        inicio()
      }
      if (cont === 9) {
        console.log('fin')
      } else {
        if (turno === 'pc') {
          if (ficha === 'close') {
            ficha = 'radio_button_unchecked'
            console.log('ficha pc o')
          }
          computa()
        } else {
          // ficha = 'close'
          console.log('continua')
        }
      }
    }

    const computa = () => {
      console.log('computa')
      const pc = parseInt(Math.random() * (10 - 1) + 1)
      console.log('pc ', pc)
      switch (pc) {
        case 1:
          if (icono1.value !== null) {
            // ficha = 'close'
            computa()
          } else {
            icono1.value = ficha // usar .value
            turno = 'us'
            gana()
          }
          break
        case 2:
          if (icono2.value !== null) {
            // ficha = 'close'
            computa()
          } else {
            icono2.value = ficha // usar .value
            turno = 'us'
            gana()
          }
          break
        case 3:
          if (icono3.value !== null) {
            // ficha = 'close'
            computa()
          } else {
            icono3.value = ficha // usar .value
            turno = 'us'
            gana()
          }
          break
        case 4:
          if (icono4.value !== null) {
            // ficha = 'close'
            computa()
          } else {
            icono4.value = ficha // usar .value
            turno = 'us'
            gana()
          }
          break
        case 5:
          if (icono5.value !== null) {
            // ficha = 'close'
            computa()
          } else {
            icono5.value = ficha // usar .value
            turno = 'us'
            gana()
          }
          break
        case 6:
          if (icono6.value !== null) {
            // ficha = 'close'
            computa()
          } else {
            icono6.value = ficha // usar .value
            turno = 'us'
            gana()
          }
          break
        case 7:
          if (icono7.value !== null) {
            // ficha = 'close'
            computa()
          } else {
            icono7.value = ficha // usar .value
            turno = 'us'
            gana()
          }
          break
        case 8:
          if (icono8.value !== null) {
            // ficha = 'close'
            computa()
          } else {
            icono8.value = ficha // usar .value
            turno = 'us'
            gana()
          }
          break
        case 9:
          if (icono9.value !== null) {
            // ficha = 'close'
            computa()
          } else {
            icono9.value = ficha // usar .value
            turno = 'us'
            gana()
          }
          break
        default:
          break
      }
    }
    // *********** usuario **************
    const x = () => {
      fichaO = false
      console.log('x')
      console.log(fichaO)
      ficha = 'close'
    }
    const o = () => {
      fichaX = false
      console.log('radio_button_unchecked')
      ficha = 'radio_button_unchecked'
    }
    const uno = () => {
      console.log('uno')
      ficha = 'close'
      icono1.value = ficha
      turno = 'pc'
      gana()
    }
    const dos = () => {
      console.log('dos')
      ficha = 'close'
      icono2.value = ficha
      turno = 'pc'
      gana()
    }
    const tres = () => {
      console.log('tres')
      ficha = 'close'
      icono3.value = ficha
      turno = 'pc'
      gana()
    }
    const cuatro = () => {
      console.log('cuatro')
      ficha = 'close'
      icono4.value = ficha
      turno = 'pc'
      gana()
    }
    const cinco = () => {
      console.log('cinco')
      ficha = 'close'
      icono5.value = ficha
      turno = 'pc'
      gana()
    }
    const seis = () => {
      console.log('seis')
      ficha = 'close'
      icono6.value = ficha
      turno = 'pc'
      gana()
    }
    const siete = () => {
      console.log('siete')
      ficha = 'close'
      icono7.value = ficha
      turno = 'pc'
      gana()
    }
    const ocho = () => {
      console.log('ocho')
      ficha = 'close'
      icono8.value = ficha
      turno = 'pc'
      gana()
    }
    const nueve = () => {
      console.log('nueve')
      ficha = 'close'
      icono9.value = ficha
      turno = 'pc'
      gana()
    }

    return {
      x,
      o,
      uno,
      dos,
      tres,
      cuatro,
      cinco,
      seis,
      siete,
      ocho,
      nueve,
      icono1,
      icono2,
      icono3,
      icono4,
      icono5,
      icono6,
      icono7,
      icono8,
      icono9,
      computa,
      turno,
      ficha,
      cont,
      us,
      mak,
      refresh,
      confirm,
      game,
      fichaX,
      fichaO
    }
  }
}
</script>

<style lang="sass" scoped>
.o
  font-size: 200%
.margen
  margin: 8% 18%
</style>
