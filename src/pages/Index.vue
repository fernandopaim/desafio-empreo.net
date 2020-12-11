<template>
  <q-page class="row bg-grey-1">
    <div class="left-bar desktop-only hidden-xs hidden-sm col-md-3 col-lg-2 body-height bg-secondary">
      <h3 class="left-bar-title q-mb-xs text-primary">Cadastro recrutador</h3>
      <q-stepper v-model="step" class="styled-stepper"
        done-color="primary"
        active-color="primary"
        inactive-color="primary"
        vertical animated flat>
        <q-step :name="1" prefix="1" title="Dados pessoais"
          caption="1 min" :done="step > 1" />
        <q-step :name="2" prefix="2" title="Organização"
          caption="1 min" :done="step > 2" />
        <q-step :name="3" prefix="3" title="Detalhes da vaga"
          caption="1 min" :done="step > 3" />
      </q-stepper>
    </div>
    <div class="col-sm-12 col-md-10 body-height">

    </div>
    <!-- <example-component
      title="Example component"
      active
      :todos="todos"
      :meta="meta"
    ></example-component> -->
  </q-page>
</template>

<script lang="ts">
import { Todo, Meta } from 'components/models'
import ExampleComponent from 'components/CompositionComponent.vue'
import { defineComponent, ref } from '@vue/composition-api'

export default defineComponent({
  name: 'PageIndex',
  components: { ExampleComponent },
  data () {
    return {
      step: 1
    }
  },
  setup () {
    const todos = ref<Todo[]>([
      {
        id: 1,
        content: 'ct1'
      }
    ])
    const meta = ref<Meta>({
      totalCount: 1200
    })
    return { todos, meta }
  }
})
</script>

<style lang="sass" scoped>
  .body-height
    height: calc(100vh - 55px)

  .left-bar
    padding-left: 3vw
    // max-width: max(16vw, 24em)
    padding-top: 0.6em

  .left-bar-title
    font-family: 'Poppins', sans-serif
    font-weight: 600
    font-size: 1.65em
    line-height: 150%

  .styled-stepper::v-deep
    background: transparent

    .q-stepper__tab
      padding: 0
      margin-bottom: 2.2em
      opacity: 0.6

    .q-stepper__step-content
      display: none

    .q-stepper__tab.q-stepper__tab--active
      opacity: 1
</style>
