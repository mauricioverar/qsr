<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          Quasar App
        </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
    >
      <q-list>
        <q-item-label
          header
        >
        <q-item clickable v-ripple to="/" active-class="my-menu-link">
          Juegos
          </q-item>
        </q-item-label>
        <q-item clickable v-ripple to="/cachipun" active-class="my-menu-link">
          <q-item-section avatar>
            <q-icon name="content_cut"/>
          </q-item-section>

          <q-item-section>Cachipún</q-item-section>
        </q-item>

        <q-item clickable v-ripple to="/gato" active-class="my-menu-link">
          <q-item-section avatar>
            <q-icon name="highlight_off"/>
          </q-item-section>

          <q-item-section>Gato</q-item-section>
        </q-item>

        <!-- <q-item clickable v-ripple to="/puzzle" active-class="my-menu-link">
          <q-item-section avatar>
            <q-icon name="exit_to_app"/>
          </q-item-section>

          <q-item-section>Puzzle</q-item-section>
        </q-item>

        <q-item clickable v-ripple to="/laberinto" active-class="my-menu-link">
          <q-item-section avatar>
            <q-icon name="sync_alt"/>
          </q-item-section>

          <q-item-section>Laberinto</q-item-section>
        </q-item>

        <q-item clickable v-ripple to="/laberinto" active-class="my-menu-link">
          <q-item-section avatar>
            <q-icon name="sync_alt"/>
          </q-item-section>

          <q-item-section>Zener</q-item-section>
        </q-item> -->
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>

import { defineComponent, ref } from 'vue'
import { useQuasar } from 'quasar' // importar $q

export default defineComponent({
  name: 'MainLayout',

  setup () { // composition API
    const leftDrawerOpen = ref(false)
    const $q = useQuasar()

    return {
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      },
      $q // exportar $q
    }
  }
})
</script>
