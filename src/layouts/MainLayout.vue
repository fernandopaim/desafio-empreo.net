<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-toolbar-title>
          <div class="text-logo" @click="confirm">
            emprego<span>.</span>net
          </div>
        </q-toolbar-title>

        <q-btn dense flat icon="close" v-close-popup @click="confirm">
          <q-tooltip>Sair</q-tooltip>
        </q-btn>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script lang="ts">
import { defineComponent, ref } from '@vue/composition-api'

export default defineComponent({
  name: 'MainLayout',
  components: {},
  setup () {
    const leftDrawerOpen = ref(false)

    return { leftDrawerOpen }
  },
  methods: {
    confirm () {
      this.$q.dialog({
        title: 'Cancelar registro?',
        message: 'Tem certeza de que deseja sair do cadastro?',
        ok: {
          label: 'Continuar cadastro',
          push: true
        },
        cancel: {
          label: 'Sair',
          flat: true
        },
        persistent: true
      }).onOk(() => {
        // console.log('>>>> OK')
      }).onCancel(() => {
        // return this.$router.push('/recruiter')
        window.location.href = 'https://uat.emprego.net/recruiter'
      }).onDismiss(() => {
        // console.log('I am triggered on both OK and Cancel')
      })
    }
  }
})
</script>

<style lang="sass" scoped>
  @import 'https://fonts.googleapis.com/css2?family=Open+Sans&family=Poppins:wght@600&display=swap'

  .text-logo
    display: inline-block
    margin: 4px 4px 4px 24px
    padding: 4px 0
    font-family: 'Poppins', sans-serif
    font-weight: 600
    cursor: pointer

    > span
      font-family: 'Open Sans', sans-serif
      font-size: 125%
</style>
